---
title: "Checking logs"
date: 2012-07-20
forum: Server Platforms
---

### Post by MockY on 2012-07-20
My web/ftp server has started to shut down on me unexpectedly. I tested all hardware and they all pass with flying colors (hard drives, motherboard, memory). I checked specific ftp logs and nothing stands out. The machine runs 11.10 and is behaving as someone is sending a halt command, shutting the machine down but leaving it running (11.10 and later ridiculously requires *sudo poweroff* in order to fully turn it off). I want to check whether my machine is compromised in any way (any php scripts running amok, or someone actively attacking the server with whatever method).

With that in mind, what logs should I look through.

---

### Post by LHammonds on 2012-07-20
If you suspect somebody is accessing your system or possibly hacked root, take a look at the authentication log to see who is accessing your system and when.

/var/log/auth.log

[Log files in Ubuntu and how to view them]("http://forum.zentyal.org/index.php?topic=4321.0")

Something else to check, if you think your account was compromised is your command history.   Simply press the up arrow and see if there are any commands that were issued that you did not type.  Can also see them by typing **vi ~/.bash_history**

Not sure if this would be helpful (I have not used it yet), there is a [LogWatch]("https://help.ubuntu.com/community/Logwatch") utility.

When I login to my 12.04 server (not as root) and issue the **shutdown -P now** command without using **sudo** it simply ignores me and says I must be root to issue the command.  It does not partially takedown my server and decide to stop at some arbitrary point.  It does not issue any kind of shutdown at all.

I don't use 11.xx simply because it is considered an "in-between" development platform.  I've only used the Long Term Support (LTS) versions which are 10.04 and 12.04.  If your version has the root account disabled by default, make sure it is still disabled or has not been logged into directly.  Look at /home/.bash_history for a hint as well as the datestamp of that file.

Take a look at sudoers and make sure there are no users listed in there that are not supposed to be there.

LHammonds

---

### Post by MockY on 2012-07-23
Thank you for your informative post. I checked all the logs mentioned in the link you provided and nothing stands out. I suspect that the OS got corrupted along the way after an update, but I could not find any proof of such.

I can't have this server offline for much longer, so I'm simply switching motherboard and hard drive and installing 12.04, and hoping that this mystical issue goes away.

---

