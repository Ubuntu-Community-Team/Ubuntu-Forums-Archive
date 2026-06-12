---
title: "harddrive wipe on restart"
date: 2012-11-03
forum: Security
---

### Post by nwalkey on 2012-11-03
I'm working at a community access site and we are getting new computers soon. We are planning on running a mix of some ubuntu release and windows 7. We already have a solution or will find a solution for clearing all data created during a session but are looking for the best solution for ubuntu. I personally have used ubuntu in the past and have just recently switch(for good I think) on my home computers. 
     Here is what our setup is like and what is needed:
-6 computers that will be capable of dual booting ubuntu/windows

-each computer is going to be set up to automatically log in to a customer account

-there will be a staff/admin account

-the customer account needs to not suffer from any loss of functionality but needs to 
be secure in a way that they cannot damage the computers accidentally

-we have the computers set to restart after 15 minutes of idle and upon restart, all changes that were made during the session need to be permanently deleted

-the solution needs to be relatively easy to implement and fix if errors occur

-we need to be capable of imaging both partitions using FOG(hopefully)

I know there are ways to do this and hopefully I can be pointed in the right way. I haven't done much research into doing this but thought this would be the right place to get pointed in the right direction.

Long post for a first post but I'll hopefully be capable of contributing to the community and to this forum :)

---

### Post by HermanAB on 2012-11-03
Simple really.  Install a virtualizer such as Vmware or Virtualbox and upon logout, use tar to unarchive and overwrite the VM with a fresh copy.

---

### Post by nwalkey on 2012-11-03
Sounds interesting but then I would need to set up scripts or something to do it automatically. I don't know if vbox will work for this but I'll look into it because that would make managing images really simple.

---

### Post by Ms. Daisy on 2012-11-03
That sounds a lot like the Ubuntu guest account. Have you looked at its capabilities? 

Also I would disable the usb ports & CD drive. Give people an option to share/move their files via email or dropbox or some other cloud method.

---

### Post by nwalkey on 2012-11-03
Unfortunately I can't disable usb ports and cd drives as they are one of the most used file transfer solutions at the site. I'll look into guest account forsure though. It would be awesome if that can do everything I need. I was thinking maybe have a read only partition and then all written files be written to a temp file on another partition that gets erased everytime the computer is restarted. There really can't be any files from the user remaining in any form after restart.

---

### Post by Ms. Daisy on 2012-11-04
Hmm. 

Your thread seems to have evolved into something similar to this thread:
[http://ubuntuforums.org/showthread.php?t=2079725](http://ubuntuforums.org/showthread.php?t=2079725)

---

### Post by SeijiSensei on 2012-11-04
Another solution might be to create a copy of /home somewhere in the file system.  Then at boot, you could run a script from /etc/rc.local that would copy this image to a [ramdisk]("http://www.cyberciti.biz/faq/howto-create-linux-ram-disk-filesystem/") and mount the ramdisk as /home.  Upon reboot the ramdisk will vanish and be created anew.

---

### Post by nwalkey on 2012-11-05
So /home being mounted to ram disk or getting over written is all that needs to be done?
That sounds like an easy solution. I'll check that out.

---

