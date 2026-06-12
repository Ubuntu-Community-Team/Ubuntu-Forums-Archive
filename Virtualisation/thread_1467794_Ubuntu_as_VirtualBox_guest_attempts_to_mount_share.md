---
title: "Ubuntu as VirtualBox guest attempts to mount shared folders twice at startup"
date: 2010-05-01
forum: Virtualisation
---

### Post by jlebar on 2010-05-01
(Moved from main forum: [http://ubuntuforums.org/showthread.php?t=1467757](http://ubuntuforums.org/showthread.php?t=1467757))

I just upgraded my Ubuntu VirtualBox guest to Lucid.

My host machine shares two folders with the guest.  I have them listed in my /etc/fstab so they're automatically mounted:

share /mnt/share vboxsf defaults 0 0

For some reason, it looks like Ubuntu attempts to mount these shared folders twice.  The first time, the mount doesn't succeed, but the second time, it does, so by the time I actually log in, the shares work properly.

Karmic would just print an error message at boot, but now Lucid makes me press a key to continue booting when the mount fails.

Ideally, I'd like to figure out how to make the first mount attempt work properly.  But if that's complicated, just disabling Lucid's prompt would make me happy.

Any ideas how I can go about accomplishing this?

Thanks.

---

### Post by kc109 on 2010-05-03
I have had the same problem and came across these two threads:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/530179](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/530179)
[http://ubuntuforums.org/showthread.php?t=1440320&](http://ubuntuforums.org/showthread.php?t=1440320&)

I found the following steps worked well for me.
1)comment out the share mounting lines in /etc/fstab
2)edit the /etc/rc.local file [not the /etc/init.d/rc.local file] to add the mount points in the form of: mount.vboxsf -w HOST_FOLDER /MOUNT_POINT

e.g. my original  /etc/rc.local file contained the following
 
	#!/bin/sh -e
	#
	# rc.local
	#
	# This script is executed at the end of each multiuser runlevel.
	# Make sure that the script will "exit 0" on success or any other
	# value on error.
	#
	# In order to enable or disable this script just change the execution
	# bits.
	#
	# By default this script does nothing.
	#
	exit 0

It now looks like this

	#!/bin/sh -e
	#
	# rc.local
	#
	# This script is executed at the end of each multiuser runlevel.
	# Make sure that the script will "exit 0" on success or any other
	# value on error.
	#
	# In order to enable or disable this script just change the execution
	# bits.
	#
	# By default this script does nothing.
	# auto mount VirtualBox shared folders
	mount.vboxsf -w vm-share-work /media/share
	mount.vboxsf -w sdb8 /media/prog-lib
	mount.vboxsf -w apt-store-10.04-LTS /media/aptoncd
	# end of VirtualBox shared folders
	#
	exit 0

---

### Post by jlebar on 2010-05-03
Thanks, kc109; that worked great.

---

### Post by k00lman on 2010-05-05
Worked for me, too!

---

### Post by abdusamed on 2010-05-18
in my case it's the other way arount.. i can't access my shared folder in ubuntu from xp guest machine.. like how to?

---

### Post by jlebar on 2010-05-18
abdusamed, you should create a new forum topic if you're having a different problem.

---

### Post by raisinman on 2011-01-08
Superb! Thanks.

---

### Post by Advice Pro on 2011-09-23
> **jlebar said:**
> (Moved from main forum:  I have them listed in my /etc/fstab so they're automatically mounted

Why did you choose /ect/fstab?  What did you mean by automatically mounted?

---

### Post by huyhoang3673 on 2012-06-27
I did exactly like what kc109 mentioned. Remove the entries in /etc/sftab and add the following lines to /etc/rc.local:

mount.vboxsf -w work /home/my_user/work
mount.vboxsf -w ws /home/my_user/ws

But after rebooting, I still didn't see these folders mounted. If I mounted manually, I got:
$ sudo mount -t vboxsf ws ~/ws
/sbin/mount.vboxsf: mounting failed with the error: No such device

Can someone help me how to fix this issue and automount those 2 directories after booting up? I already set work and ws to point to a folder on my laptop via Virtual Box Shared Folder option.

Thanks,

---

### Post by huyhoang3673 on 2012-06-27
I figured out why it doesn't work for me. I just recently updated my Virtual Box to 4.1.18, but I didn't re-update my Guest Addition accordingly. After updating Guest Addition, I was able to auto-mount using rc.local file as mentioned earlier. However, either /etc/rc.local or /etc/init.d/rc.local works for me.

---

