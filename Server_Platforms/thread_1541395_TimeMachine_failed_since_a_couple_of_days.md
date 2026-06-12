---
title: "TimeMachine failed since a couple of days"
date: 2010-07-29
forum: Server Platforms
---

### Post by emma_peel on 2010-07-29
Hello.

My macbook is backed up using timemachine on a samba drive. I used this hack for months :

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

This tuto is based on Netatalk, but works perfectly with Samba (or used to), as described in many others blogs.

A couple of days ago, I had a strange message from timemachine, like the backup should be reconstructed to improve the security. The sparsebundle has been deleted, and timemachine try to create a new one now. This step fails.

I tried to create manually a new sparsebundle, using the tuto. It does not work.

I have a backup of the sparsebundle ... I can navigate into it ("enter timemachine"), but I cannot backup anymore.

Does anyone face the same issue ?

Thanks in advance for your support.

---

### Post by regala on 2010-07-29
> **emma_peel said:**
> Hello.

TimeMachine ate itself.

Thanks in advance for your support.

TimeMachine is an Apple product. You should ask them.

---

### Post by DrMelon on 2010-07-29
Yeah, a Linux forum won't be able to provide the same amount of support as an Apple technician - this is because if it were an Open-Source project, we would know exactly how it worked, but since TimeMachine is closed-source and belongs to Apple, only they know its inner workings. :(
Good luck!

---

### Post by emma_peel on 2010-07-29
Hum, this functionality is not officially supported. No help could be expected from them.

---

### Post by emma_peel on 2010-07-29
Looks related to the last macos update (10.6.4).

---

### Post by arrrghhh on 2010-07-29
> **emma_peel said:**
> Looks related to the last macos update (10.6.4).

Hence it's their problem.  For whatever reason, for all OSS has done for Apple, they really do NOT seem to like working with them in any way shape or form.  They'll steal code from them all day long, but won't give a scrap back.  It's unfortunate the BSD license allows them to commit such crime...

Shame really, I'm sure some of their code would be very useful...

I'll still try to throw you a bone tho.  Can you still connect to the samba share?  Have you considered NFS?  (I have no clue how supported NFS is on OSX however...)

---

### Post by wmgries on 2010-07-29
That tutorial has you use Netatalk, not Samba. If you are using Samba to connect (I believe that's possible) you should go back and re-read the tutorial and set it up with Netatalk. Works great with 10.6.4.

---

### Post by emma_peel on 2010-08-02
Hello all.

Thank you for your support. I finally apply again the hack. The first back-up took a longer time to mount the SMB partition. I guess that the sparsebundle has been update some how.

Anyway, it worked. I just lost the history.

Thanks again.

---

