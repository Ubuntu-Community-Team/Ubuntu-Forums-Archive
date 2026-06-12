---
title: "Juju EC2 error - ERROR SSH forwarding error: bind: Cannot assign requested address"
date: 2013-08-24
forum: Ubuntu Cloud and Juju
---

### Post by thaidog on 2013-08-24
I keep getting this error where I cannot access my new instance:

```

$ juju status
2013-08-24 11:58:20,879 INFO Connecting to environment...
2013-08-24 11:58:21,407 ERROR juju environment not found: is the environment bootstrapped?

$ juju bootstrap --constraints "instance-type=t1.micro"
2013-08-24 11:58:35,597 INFO Bootstrapping environment 'wordpress' (origin: distro type: ec2)...
2013-08-24 11:58:38,488 INFO 'bootstrap' command finished successfully

$ juju status
2013-08-24 12:01:16,940 INFO Connecting to environment...
The authenticity of host 'ec2-xxxx.compute-1.amazonaws.com (xxxxx)' can't be established.
ECDSA key fingerprint is xxxxxxxxxx.
Are you sure you want to continue connecting (yes/no)? yes
2013-08-24 12:01:21,018 ERROR SSH forwarding error: bind: Cannot assign requested address

2013-08-24 12:01:48,837 ERROR SSH forwarding error: bind: Cannot assign requested address

2013-08-24 12:02:19,544 ERROR SSH forwarding error: bind: Cannot assign requested address

```

I generated a a .pem key and tried to manaully ssh to the instance but I still cannot. Any ideas?

---

