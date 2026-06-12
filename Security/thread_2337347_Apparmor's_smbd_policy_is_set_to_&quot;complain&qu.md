---
title: "Apparmor's smbd policy is set to &quot;complain&quot;.  Still in development?"
date: 2016-09-16
forum: Security
---

### Post by gbell12 on 2016-09-16
Hi All,

I installed apparmor-profiles.  Now my syslog's polluted with:

```
Sep 17 11:22:38 server kernel: [50129.596576] audit: type=1400 audit(1474075358.485:5208783): 
apparmor="**ALLOWED**" operation="mknod" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/32489" pid=32489 
comm="smbd" requested_mask="c" denied_mask="c" fsuid=0 ouid=0

```

Being an "allowed" message, I wanted to shut it up, so I went digging into /etc/apparmor.d/usr.sbin.smbd, only to find 

```
/usr/sbin/smbd flags=(complain) {
```

My reading of the docs leads me to understand that it's not enforcing any rules, just complaining.  Is that right?  

Almost all the profiles in /etc/apparmor.d/ are set to just complain.   Does this mean that apparmor isn't really doing much?

---

### Post by Seb_Boffen on 2016-09-28
If an directory is not listed within a apparmor profile access will be denied, as far as I know, but my log was filling up due to the samba update (4.3.11-Ubuntu)

With:

Sep 29 01:03:12 servername kernel: [37737.425293] type=1400 audit(1475103792.835:444): apparmor="ALLOWED" operation="mknod" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/2015" pid=2015 comm="smbd" requested_mask="c" denied_mask="c" fsuid=0 ouid=0

And:

Sep 29 01:27:09 servername kernel: [39174.102830] type=1400 audit(1475105229.511:546): apparmor="ALLOWED" operation="mknod" profile="/usr/sbin/nmbd" name="/var/lib/samba/private/msg.sock/18522" pid=18522 comm="nmbd" requested_mask="c" denied_mask="c" fsuid=0 ouid=0

So to stop the log updates I've updated the apparmor profile: /etc/apparmor.d/usr.sbin.nmbd
With: 
 
/var/lib/samba/private/msg.sock/ rw,
/var/lib/samba/private/msg.sock/[0-9]* rwk,

And I've updated the apparmor profile: /etc/apparmor.d/usr.sbin.smbd
With:

/{,var/}run/samba/msg.lock/ rw,
/{,var/}run/samba/msg.lock/[0-9]* rwk, 
/{var/,}run/samba/winbindd.pid rwk,
/{var/,}run/samba/winbindd/ rw,
/{var/,}run/samba/winbindd/pipe w,

than ran: [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]init.d[COLOR=#000000]**/**[/COLOR]apparmor restart

---

### Post by gbell12 on 2016-09-29
Thanks for that, Seb.  Hopefully your reply will help attract attention for my main question!

---

### Post by fenyx on 2017-05-04
Thank you so much Seb_Boffen, I had the same "access denied" issue than gbell12 and your precise and accurate description helped me to resolve the problem. Noobs will always need experts sharing their knowledge to progress until they become experts and continue the job ;)

---

