---
title: "System Mode, Avalibility Zone Problem (suspect NC connection issue)"
date: 2012-01-15
forum: Ubuntu Cloud and Juju
---

### Post by The Cheat on 2012-01-15
Hi,

Just getting a eucalyptus cloud running and run into a few issues. We are using UEC from 10.10, so eucalyptus 2.0.0.

We have everything registered including the node but it seems to not want to give us any available hardware to create VM's with.

Below is an output of the avalibility zone verbose and attached are a few relevant log files. Any help would be greatly appreciated.

project@APs3:/var/log/eucalyptus$ euca-describe-availability-zones verbose
AVAILABILITYZONE	cluster1	134.117.89.147
AVAILABILITYZONE	|- vm types	free / max cpu ram disk
AVAILABILITYZONE	|- m1.small	0000 / 0000 1 192 10
AVAILABILITYZONE	|- c1.medium	0000 / 0000 1 256 10
AVAILABILITYZONE	|- m1.large	0000 / 0000 2 512 10
AVAILABILITYZONE	|- m1.xlarge	0000 / 0000 2 1024 20
AVAILABILITYZONE	|- c1.xlarge	0000 / 0000 4 2048 20

BTW we have no control over IP's in the system because the school wont assign any to us. Hence System mode. The cc.log seems to indicate closed port of 8775 on the NC but it is open and listening. We have moved the credential files to .euca on the NC as well.

---

