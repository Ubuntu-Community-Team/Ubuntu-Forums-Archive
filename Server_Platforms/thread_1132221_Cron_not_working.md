---
title: "Cron not working"
date: 2009-04-21
forum: Server Platforms
---

### Post by EoinDu on 2009-04-21
I am fairly new to Linux in general but have been in IT in Novell and wondows environments for 20+ years. Our environment is mostly Windows but we have a few Red Hat and Debain servers for external use (name servers, etc.) and a couple of Unduntu 6.0.6.2 LTS Subversion source control servers running as VMs on a HP C7000 blade system on the inside. The people who installed and maintained the Linux machines are all gone and the IT department has shrunk to just me so I am going through a steep learning curve at the moment.

My current problem is that I am trying to get regular backups of the SVN servers. In the past a combination of bash scripts and Mondo were used and the backups were FTPed to the FTP server of one of the IT guys. I have re-written the scripts to send the backups to a Samba share on another server that is backed up. The script was working fine. I added it to crontab and it backed up for 2 days.

Yesterday it did not run at all and when I ran it manually the script failed because /tmp was read only. Today crontab is RO as is just about everything else in the system. As this is a production server holding some of our source control files I have to get this fixed as guickly as I can without messing anything up. 

Does anyone have any ideas about what could be causing this RO status? The / partition is 81% used and the others are 1% or less. Is this a matter of scheduling a reboot and it should come up as RW or is this type of thing more ofter corruptinn or something like that?

Thanks for any pointers.

---

### Post by geoffjay on 2009-04-21
did you try the obvious?
$ sudo mount -n -o remount rw /

---

### Post by EoinDu on 2009-04-21
Yes I did try it. It does not run because it wants the filesystem type. How do I fine that info?

---

### Post by anderswestrup on 2009-04-21
Is it only /tmp that is read-only, or is it all files on the system?

If /tmp have been changed somehow you can set back the permissions:
sudo chmod 1777 /tmp

But if it is the filesystem that is mounted read-only the other suggested fix may work. I think geoffjay forgot a ',' in his command, it should be:
sudo mount -n -o remount,rw /

---

### Post by EoinDu on 2009-04-21
/tmp shows 776 as do several other directories. I cannot chmod any of them. I cannot delete files marked 777. I did run the mount -n -o remount,rw / (with the comma) while logged in as root. No change - everything is still RO.

---

### Post by EoinDu on 2009-04-21
It got late enough that everyone was off the system so I rebooted it and it came back up as RW. I still do not know what put it into a RO state in the first place.:D

---

