---
title: "New Hoary install - strange IP address in 'last -aix' output"
date: 2005-07-13
forum: Server Platforms
---

### Post by jcook713 on 2005-07-13
Hi,

Just did a fresh install on a brand new harddrive on my laptop using the newest Hoary disks(got in mail). I checked the output from 'last -aix' and I get:

justin   :0           Wed Jul 13 09:43   still logged in    194.135.4.8
runlevel (to lvl 2)   Wed Jul 13 09:39 - 12:11  (02:32)     0.0.0.0
reboot   system boot  Wed Jul 13 09:39          (02:32)     0.0.0.0
shutdown system down  Tue Jul 12 22:35 - 12:11  (13:35)     0.0.0.0
runlevel (to lvl 0)   Tue Jul 12 22:35 - 22:35  (00:00)     0.0.0.0
justin   :0           Tue Jul 12 22:13 - down   (00:22)     194.135.4.8
runlevel (to lvl 2)   Tue Jul 12 22:12 - 22:35  (00:22)     0.0.0.0
reboot   system boot  Tue Jul 12 22:12          (00:22)     0.0.0.0
shutdown system down  Tue Jul 12 22:10 - 22:35  (00:25)     0.0.0.0
runlevel (to lvl 6)   Tue Jul 12 22:09 - 22:10  (00:00)     0.0.0.0
justin   :0           Tue Jul 12 20:38 - 22:09  (01:31)     194.135.4.8
runlevel (to lvl 2)   Tue Jul 12 20:35 - 22:09  (01:34)     0.0.0.0
reboot   system boot  Tue Jul 12 20:35          (01:34)     0.0.0.0
justin   :0           Tue Jul 12 09:29 - crash  (11:06)     194.135.4.8
runlevel (to lvl 2)   Tue Jul 12 09:29 - 20:35  (11:06)     0.0.0.0
reboot   system boot  Tue Jul 12 09:29          (12:40)     0.0.0.0
shutdown system down  Mon Jul 11 17:39 - 22:09 (1+04:29)    0.0.0.0
runlevel (to lvl 0)   Mon Jul 11 17:39 - 17:39  (00:00)     0.0.0.0
justin   :0           Mon Jul 11 09:28 - down   (08:11)     194.135.4.8
runlevel (to lvl 2)   Mon Jul 11 09:27 - 17:39  (08:11)     0.0.0.0
reboot   system boot  Mon Jul 11 09:27          (08:11)     0.0.0.0
shutdown system down  Sun Jul 10 16:19 - 17:39 (1+01:20)    0.0.0.0
runlevel (to lvl 0)   Sun Jul 10 16:18 - 16:19  (00:00)     0.0.0.0
justin   :0           Sun Jul 10 04:17 - down   (12:01)     194.135.4.8
runlevel (to lvl 2)   Sun Jul 10 04:16 - 16:18  (12:01)     0.0.0.0
reboot   system boot  Sun Jul 10 04:16          (12:01)     0.0.0.0
justin   tty2         Sat Jul  9 17:41 - crash  (10:35)     0.0.0.0
justin   :0           Sat Jul  9 14:48 - crash  (13:27)     194.135.4.8
runlevel (to lvl 2)   Sat Jul  9 14:45 - 04:16  (13:31)     0.0.0.0
reboot   system boot  Sat Jul  9 14:45         (1+01:33)    0.0.0.0
shutdown system down  Sat Jul  9 14:42 - 16:18 (1+01:35)    0.0.0.0
runlevel (to lvl 6)   Sat Jul  9 14:42 - 14:42  (00:00)     0.0.0.0
justin   :0           Sat Jul  9 13:28 - 14:42  (01:14)     194.135.4.8
runlevel (to lvl 2)   Sat Jul  9 13:27 - 14:42  (01:15)     0.0.0.0
reboot   system boot  Sat Jul  9 13:27          (01:15)     0.0.0.0
shutdown system down  Sat Jul  9 13:24 - 14:42  (01:17)     0.0.0.0
runlevel (to lvl 6)   Sat Jul  9 13:24 - 13:24  (00:00)     0.0.0.0
justin   :0           Sat Jul  9 13:19 - down   (00:04)     194.135.4.8
runlevel (to lvl 2)   Sat Jul  9 13:19 - 13:24  (00:05)     0.0.0.0
reboot   system boot  Sat Jul  9 13:19          (00:05)     0.0.0.0
justin   :0           Sat Jul  9 19:00 - crash  (-5:-41)    194.135.4.8
runlevel (to lvl 2)   Sat Jul  9 18:56 - 13:19  (-5:-37)    0.0.0.0
reboot   system boot  Sat Jul  9 18:56          (-5:-31)    0.0.0.0
shutdown system down  Sat Jul  9 14:28 - 13:24  (-1:-3)     0.0.0.0
runlevel (to lvl 6)   Sat Jul  9 14:27 - 14:28  (00:00)     0.0.0.0
justin   :0           Sat Jul  9 14:05 - down   (00:22)     194.135.4.8
runlevel (to lvl 2)   Sat Jul  9 14:04 - 14:27  (00:23)     0.0.0.0
reboot   system boot  Sat Jul  9 14:04          (00:23)     0.0.0.0
shutdown system down  Sat Jul  9 14:02 - 14:27  (00:25)     0.0.0.0
runlevel (to lvl 0)   Sat Jul  9 14:02 - 14:02  (00:00)     0.0.0.0
justin   :0           Sat Jul  9 13:48 - down   (00:13)     194.135.4.8
runlevel (to lvl 2)   Sat Jul  9 13:47 - 14:02  (00:14)     0.0.0.0
reboot   system boot  Sat Jul  9 13:47          (00:14)     0.0.0.0
shutdown system down  Sat Jul  9 13:45 - 14:02  (00:16)     0.0.0.0
runlevel (to lvl 6)   Sat Jul  9 13:44 - 13:45  (00:00)     0.0.0.0
justin   :0           Sat Jul  9 13:22 - down   (00:22)     194.135.4.8
runlevel (to lvl 2)   Sat Jul  9 12:46 - 13:44  (00:58)     0.0.0.0
reboot   system boot  Sat Jul  9 12:46          (00:58)     0.0.0.0

I have never logged on remotely to this laptop and I got these IP addresses here even when I was not on the internet. Have I been compromised? I was just on a Ubuntu irc channel and someone else who had just done a fresh install had the same IP address in his/her 'last -aix' output. 
The IP address resolves to a bank in Russia. :? 

Can anyone help me out on this issue?

---

### Post by jcook713 on 2005-07-13
Was poking around alittle on the forums here and found the following thread:

 [http://ubuntuforums.org/showthread.php?t=47778](http://ubuntuforums.org/showthread.php?t=47778)

It seems like my problem exactly.

There was no response to this posting but I am assuming until I hear otherwise that this is a bug as mentioned in the linked post above, --correct?

---

### Post by msh on 2005-07-19
What IP adress are you reffering to?

---

### Post by LordHunter317 on 2005-07-19
Is your internet address 194.135.4.8?  If so, nothing to worry about.

---

### Post by ArBaDaCarBa on 2005-07-20
Yep, I also have 194.135.4.8 as IP for every user logged from :0
But the IP is correct for everything else... weird bug.

---

