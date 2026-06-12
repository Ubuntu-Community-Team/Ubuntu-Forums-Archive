---
title: "cannot change system date of EC2 instance"
date: 2009-05-28
forum: Server Platforms
---

### Post by meonkeys on 2009-05-28
I'm unable to change the system date of an EC2 instance of 8.04 (Hardy) x86_64 (ami-e257b08b from [http://alestic.com/](http://alestic.com/)).

```
$ date
Thu May 28 13:07:01 UTC 2009
$ sudo date 05110000
Mon May 11 00:00:00 UTC 2009
$ date
Thu May 28 13:07:10 UTC 2009
```

Anyone know what might, in general, prevent the system date from being changed? Or perhaps this is a Xen issue?

Thank you,
-Adam

(crossposted here: [http://groups.google.com/group/ec2ubuntu/](http://groups.google.com/group/ec2ubuntu/) ... If this functionality has been explicitly disabled in their EC2 image, I imagine someone in that forum would know)

---

### Post by meonkeys on 2009-05-28
Aha! This does the trick:

```
echo 1 > /proc/sys/xen/independent_wallclock
```

mentioned by a coworker, then found [on the xen-users mailing list](http://lists.xensource.com/archives/html/xen-users/2009-02/msg00488.html).

---

