---
title: "Can't attach volumes to my instance"
date: 2010-10-18
forum: Ubuntu Cloud and Juju
---

### Post by Ohm's Lawyer on 2010-10-18
Hello again,
I've hit the next snag in my adventure in UEC cloud computing. I can't seem attach volumes to my instance. I can create the volume, and I can run my instance, but when I run the command:

euca-attach-volume -i i-xxxxxxxx -d /dev/sdb  vol-xxxxxxxx

[FONT=Verdana]it will change the status of the volume from "available" to "in use" for about 3 seconds, then change back to "available". All the while the instance never sees the volume.

Any one have any ideas?

Thanks in advance.
[/FONT]

---

### Post by marrusl on 2010-10-19
Hi OL,

In /var/log/eucalyptus/ on the front end machine, take a look through the most recent cloud-error.log, cloud-debug.log, and cloud-output.log.  You should find a related error there.  You also should check the nc.log on the Node Controller.

Post the errors here or if they are way to long use [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/)

Also, check the  VNET_INTERFACE in eucalyptus.conf on your CLC/SC and make sure it's correct.

Regards,
Mark

---

### Post by Ohm's Lawyer on 2010-10-24
Hi Mark,
Thanks for replying. The specific error I'm getting is:

DoAttachVolume failed error=1 (code=9)

Otherwise my VNET_INTERFACE settings look correct.

Thanks again

---

