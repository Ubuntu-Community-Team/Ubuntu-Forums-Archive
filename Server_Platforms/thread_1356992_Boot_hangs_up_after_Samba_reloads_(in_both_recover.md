---
title: "Boot hangs up after Samba reloads (in both recovery/normal boot)"
date: 2009-12-16
forum: Server Platforms
---

### Post by mogie on 2009-12-16
Hi,

Got a problem at bootup with my server. It may be related to an apt-get update && upgrade which I've made sereval of recently... I'm not sure.

I've tried both Recovery and normal startup mode. I'm currently running Karmic Koala kernel 2.6.31-16 x64.

The last line showing (in both recovery and "splash quiet") is
""Reloading /etc/samba/smb.conf" "smdb only"
...done

And here it hangs.

Maybe it would helpful to know what daemon is initiating after the samba-daemon. (just suggesting..I dont really know)

I've been checking some /var/log/samba/log.smbd files, but I don't find anything because the root-system is in permanent read-only.
I forgot to mention that I'm able to go into "maintenance mode" with root login just by typing it then.
It is of course read-only mode then. 
And I'm not ever sure how to get the system writeable if I need to do some configuration to fix this boot-up issue.

Thanks for all advices! I'm a bit newbie at debugging this since I can't see any output on the screen, nor dmesg.

---

### Post by volkswagner on 2009-12-17
Did you change smbd.conf, if so did you make a backup?

If you have a backup you can boot a live cd and copy smbd.conf to a new backup, then copy your fist backup to smbd.conf.

I will try to attach an unaltered smbd.conf from my 8.04 server 64bit.

Just realized, I don't seem to have smbd.conf.  I have smb.conf.  Is your original post a typo or am I missing something?

---

### Post by mogie on 2009-12-17
As I predicted, there is nothing related to smb.conf. I really think it may have something with the initializing of programs/daemons AFTER the samba-daemon. I've now set the smb.conf to default using the Live-CD to write the file. No difference..

Is there any way to find out which order the startup programs are loading in Ubuntu?

---

### Post by mogie on 2009-12-18
Solved!

Changes in /etc/fstab was the cause, and some problems with ext4/quota program. I'm not sure yet.

---

