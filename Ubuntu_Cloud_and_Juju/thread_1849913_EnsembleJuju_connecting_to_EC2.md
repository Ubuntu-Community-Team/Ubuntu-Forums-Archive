---
title: "Ensemble/Juju connecting to EC2"
date: 2011-09-25
forum: Ubuntu Cloud and Juju
---

### Post by jrings on 2011-09-25
I'm trying to connect to EC2 via Juju, and I am following the simple instructions.

*juju bootstrap*
works and gives me a new instance

but 
*juju status*
gives me

[I]
2011-09-25 10:24:05,028 INFO Connecting to environment.
2011-09-25 10:24:11,882 ERROR SSH forwarding error: bind: Cannot assign requested address

Cannot connect to machine i-c80a91a8 (perhaps still initializing): could not connect before timeout after 2 retries
2011-09-25 10:24:35,446 ERROR Cannot connect to machine *** (perhaps still initializing): could not connect before timeout after 2 retries[/I]


I don't know where to start looking for a solution.

---

### Post by jrings on 2011-09-25
I can connect manually to EC2 via
*ssh -v -i tmp/mykey.pem [email]ubuntu@ec2-50-19-42-6.compute-1.amazonaws.com[/email]*

But how do I tell Juju about the key and the username it's supposed to use?

---

### Post by castrojo on 2011-09-25
Look at the log in the instance, I had an issue last week where the instance was trying to install the ensemble ppa, which is now 404 so my instances would just sit there. 

I think this week the rename issues should be sorted out.

---

### Post by kim0 on 2011-09-26
There was a bug that prevented the juju ec2 instance from bootstrapping completely. Upgrade juju to latest and try again. If it doesn't work, visit #juju on irc and shout :)

---

