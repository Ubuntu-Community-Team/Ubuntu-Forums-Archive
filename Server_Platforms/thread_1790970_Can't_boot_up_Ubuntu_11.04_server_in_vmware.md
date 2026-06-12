---
title: "Can't boot up Ubuntu 11.04 server in vmware"
date: 2011-06-25
forum: Server Platforms
---

### Post by xbfish on 2011-06-25
Hi guys,

I just installed Ubuntu 11.04 server edition into vmware workstation. Everything works well and I can even set-up a LAMP server. 

Next, I issue a reboot or shutdown to my ubuntu server.

The next time I want to start up my ubuntu server, it won't boot up. There is only a black screen with no flickering cursors. 

Anyone knows what happen? :(

---

### Post by doas777 on 2011-06-25
the possibilities are legion. 
to start tracking down the issue, boot in [Recovery Mode]("https://wiki.ubuntu.com/RecoveryMode"), or off a live 
CD, and look at the file /var/log/dmesg.0 . it is a log of your last boot. post any errors you see.

---

### Post by xbfish on 2011-06-26
Attached screenshots are the log of /var/log/dmesg.0 

Can't seem to find any critical errors :(

---

### Post by doas777 on 2011-06-26
so you log ends after the entry "USB Hub Found" about 2.8 seconds in?
that doesn;t seem to match the mention of the file being 1200 lines long.

what is at the bottom of the file?

---

### Post by doas777 on 2011-06-26
> **jarryslink said:**
> About this problem I think need more information to   consult!
Edit: sry, thought you were the op. my bad. disregard.

---

### Post by xbfish on 2011-06-26
hi guys, 

the file is indeed 1200++ lines long.

I do know how I can copy the whole ling to display it here.

If I shutdown or reboot the server again, I will be faced with the black screen.  But if I boot in recovery mode and select resume to resume normal boot, I can login to the server.

Any idea?

---

### Post by doas777 on 2011-06-26
> **xbfish said:**
> hi guys, 

the file is indeed 1200++ lines long.

I do know how I can copy the whole ling to display it here.

If I shutdown or reboot the server again, I will be faced with the black screen.  But if I boot in recovery mode and select resume to resume normal boot, I can login to the server.

Any idea?
well you could attach it. in the end, all we really need to see is the last bit, so try:

```
cat /var/log/dmesg.0 | tail
```

---

### Post by xbfish on 2011-06-26
now there is 0 lines in the log file. I am getting confused.

---

### Post by doas777 on 2011-06-26
@op, 
this may help give us sufficient info as well:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by xbfish on 2011-06-26
> **doas777 said:**
> @op, 
this may help give us sufficient info as well:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

sorry, quite a noob here. How do i download and install the script into vmware?

---

### Post by doas777 on 2011-06-26
> **xbfish said:**
> sorry, quite a noob here. How do i download and install the script into vmware?
I would boot off a live cd. just mount the iso while the server is off, and boot it up. you may have to quickly hit the key to enter bios set up to set the cdrom to the first boot device.

then mount your system partiton, and copy the file to /root/Desktop, and set the ownership and permissions to root:root 770. 
then shutdown, "eject" the livecd, and reboot into recovery mode again.
then run:
```
sudo bash ~/Desktop/boot_info_script*.sh

```then boot to live cd again, mount the sys partition, and post back the \root\Desktop\RESULTS.TXT file.

I know, it sucks, but at least its tractable.

---

### Post by xbfish on 2011-06-26
this is the tail for the log...

---

### Post by doas777 on 2011-06-26
so it appears to be hanging while applying an apparmor profile to mysqld (or it is breaking in the next loaded item. hopefully its the aa profile).

from recovery mode, try running this command to disable your profile temporarilly:
```
aa-disable /user/sbin/mysqld
```

---

### Post by xbfish on 2011-06-26
It says the path does not exist. :confused:

---

### Post by doas777 on 2011-06-26
> **xbfish said:**
> It says the path does not exist. :confused:
sorry, typo on my part:
```
aa-disable /usr/sbin/mysqld
```

---

### Post by xbfish on 2011-06-26
Did that and when I boot into ubuntu again, it is still a black screen with a cursor freeze over there.

---

### Post by doas777 on 2011-06-26
> **xbfish said:**
> Did that and when I boot into ubuntu again, it is still a black screen with a cursor freeze over there.
any change in the dmesg tail?

see if you can get the bootscript to run

---

### Post by xbfish on 2011-06-26
I do not know what is the error. But i can always boot into recovery mode and then resume boot to boot in ubuntu server.

Hmm.. I am downloading ubuntu 10.04. Trying to see if I have this problem. 

Will post an update. :)

---

### Post by xbfish on 2011-06-26
Apprently, I don't have this problem with Ubuntu 10.04. :P

Don't know what is happening in 11.04... :confused:

---

