
### Minimum RTO for a single AZ outage
|Time |Step Description  |
|--|--|
| 00:00 |Problem happens  |
|00:05|Failure alert triggers|
|00:15|Automatic switchover to standby replica DB|

**Minimum RTO ~20 mins**

### Minimum RTO for a single region outage
|Time |Step Description  |
|--|--|
| 00:00 |Problem happens  |
|00:05|Failure alert triggers|
|00:07|Alert triggers on-all support team(1 mins)
|00:17|On-call support team may need to get out of bed, get to a computer, log in, log onto VPN (10 mins)
|00:27|On-call support team starts diagnosing the issue (10 mins)
|00:37|Root cause is discovered (10 mins)
|00:47|Remediation started (1 hr)- promoting replica DB etc
|01:47|Issue fixed (5 mins)

**Minimum RTO ~120 mins**

### Minimum RPO for a single AZ outage

In case of recoverable instance failure RPO can be zero but RTO may be around 30 mins as per AWS documentation.
When instance cannot be recovered and requires to pull point in time recovery. We can calculate RPO from RDS:describe-db-instances:LatestRestorableTime but we need to add additional human factors , size of the DB and other steps with respect to application

### Minimum RPO for a single region outage

This is similar to AZ. considering the network latency,  replica promotion and other things, RPO of 60-90 min can be considered. 