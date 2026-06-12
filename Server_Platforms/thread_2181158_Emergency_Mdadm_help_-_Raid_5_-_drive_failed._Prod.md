---
title: "Emergency Mdadm help - Raid 5 - drive failed. Production server"
date: 2013-10-16
forum: Server Platforms
---

### Post by collisionystm on 2013-10-16
Hey guys,

Been a while since I posed but I could use some help.

I have a debian production server ( did not set up )that is using mdadm and has lost a drive. I dont know alot about software raid because I dont use it and I am looking for some help.

I found this to be helpful but I feel a little lost and I am looking for guidance. [http://ubuntuforums.org/showthread.php?t=1639651](http://ubuntuforums.org/showthread.php?t=1639651)

I cant post the exact output because the system seems to have lost its network function with the failure. It boots to a prompt for maintenance mode and I hit CTRL +D to continue.

cat /proc/mdstat shows md1 as inactive and md0 as active.

mdadm.conf has md1 as raid 5 and md0 as raid 1.

Is it possible to activate the md1 temporarily until I get a replacement drive, or do I risk doing damage? If its possible, what do I need to do?

Sorry for being vague. Im not sure where to start. Mdadm is new to me.

---

### Post by lingpanda on 2013-10-16
Maybe this can assist you?  [http://globalblindspot.blogspot.com/2011/06/how-to-replace-failed-disk-of-raid-5.html](http://globalblindspot.blogspot.com/2011/06/how-to-replace-failed-disk-of-raid-5.html)

---

### Post by collisionystm on 2013-10-16
That page helped me so much and I was able to get the system up and running! Thank you, thank you, thank you!

---

### Post by lingpanda on 2013-10-16
> **collisionystm said:**
> That page helped me so much and I was able to get the system up and running! Thank you, thank you, thank you!
You're welcome.

---

