---
title: "/etc/fstab modified &amp; borked"
date: 2012-06-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dino99 on 2012-06-27
was having a very simple minimalistic fstab and was running fine.
but recently (since a couple of weeks) 2 new lines entry have been added related to non existant floppy drive (/dev/fd0)
of course the system try to mount that stupid hardware ghost.

Wonder which package upgrade have modified this fstab .:confused:

---

### Post by ronacc on 2012-06-27
thats an old bug that seems to have crept back in . IIRC it was back around gutsy that it first showed up .

---

### Post by dino99 on 2012-06-27
> **ronacc said:**
> thats an old bug that seems to have crept back in . IIRC it was back around gutsy that it first showed up .

thanks but have you an idea of the package to blame ?
on my side i was thinking about some wine updates, as i've not seen package changelog talking about fstab tweaked by upstream.

---

### Post by ronacc on 2012-06-27
no Idea what package caused it then or now , I'm not seeing it on my sys either on my updated precise or my couple day old daily install , I'll check the daily again after the update  now in progress completes .

---

### Post by dino99 on 2012-06-27
i'm only doing upgrades, no daily install here. Googling around it seems that util-linux is the right package to report against. The wrong fstab entry even does not match with blkid.

Reported
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1018385](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1018385)

---

### Post by ronacc on 2012-06-27
still not seeing it on my sys after todays update , my util-linux version is 2.20.1-1ubuntu3 .

---

### Post by dino99 on 2012-06-27
> **ronacc said:**
> still not seeing it on my sys after todays update , my util-linux version is 2.20.1-1ubuntu3 .

have the same one here too. well i'm not sure its the right package to report against anyway, dev will switch to an other one in case. But i've seen this error for the first time a while back (couple of weeks)

---

### Post by Elfy on 2012-06-27
not a rolling upgrade here, but a daily on i386 with nouveau :all fine

):P

---

