---
title: "Mount partiton without enter password"
date: 2009-11-01
forum: Security
---

### Post by bangrobe on 2009-11-01
Everytime enter a partition on my harddisk, I must enter password. Is there a way to skip that step?

---

### Post by Citadel1980 on 2009-11-01
When you enter your password, you need to see if you have and option that allows you to authenticate for just that particular time or for a session (time you are currently logged in or to allow authentication permanently.) You can also download via apt-get or synaptic a utility called NTFS-config that will help you configure which hard drives you wish to auto mount without issusing a password each time.

This feature is a security measure that is usually set by default. If you are the lone user of this computer or no one else has physical access to the computer/or you don't care then use the auto mount feature.

I'm not physically present at a Linux computer but if you look for info pertaining to what I stated you will find additional info.

I hope this helps.

---

### Post by Lars Noodén on 2009-11-02
What kind of partition and what kind of device is it on?  

For many kinds you can set /etc/fstab to allow users to mount or unmount a partition.  The [mount option](http://manpages.ubuntu.com/manpages/karmic/en/man8/mount.8.html) 'user' allows that.  
(Be sure to make a back up copy first: cp /etc/fstab /etc/fstab.orig)
You can also take advantage of the UUID to ensure that *only* that partition is mounted.  

Is the partition encrypted or unencrypted?

---

### Post by Darce on 2009-11-02
Hi bangrobe,

I used the solution here :

[http://ubuntuforums.org/showthread.php?t=1308528](http://ubuntuforums.org/showthread.php?t=1308528)

as posted by [pjomega]("http://ubuntuforums.org/member.php?u=412800")

Worked a treat for me, hopefully you to.

Cheers,

Tim

---

