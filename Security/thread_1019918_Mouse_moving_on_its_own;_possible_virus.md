---
title: "Mouse moving on its own; possible virus"
date: 2008-12-23
forum: Security
---

### Post by jrc27 on 2008-12-23
i run ubuntu and windows xp on my comp and I notice that when i run ubuntu, from time to time the cursor will move on its own and even click on things.  for ex.: 
i was on facebook and it opened someones profile twice
it also moved violently across my desktop screen and made a new folder

now i've looked at other forum posts about this talking about joysticks and othr stuff that doesn't help me.  Does anyone have an explanation for my cursor moving on its own other than someone remote controlling it to mess with me.  If it is someone messing w/ me, can u suggest any good anti-virus software to use.

Thanks.

---

### Post by lykwydchykyn on 2008-12-23
It could be a bad spot in the mouse cable; does it look like a person moving the mouse, or does it look like the mouse just freaking out and doing random things?

Is it actually a mouse or a laptop touchpad?

If someone is remoting in and messing with you, and antivirus is not the solution.  You need to look at what remote services are activated on your system (like vnc, ssh, xdmcp, etc) and lock them down.

---

### Post by jrc27 on 2008-12-23
its a hp desktop w/ hp optical mouse, but i've had this comp for years and this only happens in ubuntu never windows

as for the remote login, i've disable remote login and removed the remote login application

when it moves, it does look a bit frantic, but there are times when it just scrolls down when i'm on firefox and then it'll flail around for a while and then i'll get back control

---

### Post by davec64 on 2008-12-23
I had a similar problem. 

It turned out the graphics tablet I had installed caused a similar reaction if I left it's mouse on it! I moved the mouse well away from it and all is well!

I know it's silly but you haven't got a secondary pointing device attached have you?

---

### Post by melojo on 2008-12-23
As far as I know there are no known Linux Virus in the wild.  Could be some kind of conflict.  Have you installed any new hardware or software lately?

---

### Post by jrc27 on 2008-12-23
nope, the only hardware i have attached are a mouse, keyboard, speakers, printer, and modem

---

### Post by melojo on 2008-12-23
> **jrc27 said:**
> nope, the only hardware i have attached are a mouse, keyboard, speakers, printer, and modem

Do you have another mouse you could try?

---

### Post by jrc27 on 2008-12-23
> **melojo said:**
> As far as I know there are no known Linux Virus in the wild.  Could be some kind of conflict.  Have you installed any new hardware or software lately?

yea, but this has been going on since i very first installed ubuntu, though when i installed it i did have like 210 updates, but its way to deliberate to be anything like that

---

### Post by lykwydchykyn on 2008-12-23
Post the output of these commands:

```

sudo netstat -tunap
sudo iptables -l
last
who

```

That should help us determine if anyone has been remoting in to mess with you.  Also check /var/log/auth.log and see if there are user names other than yours in there (there will be a number of root logins attributed to the cron daemon, that's normal).

---

### Post by jrc27 on 2008-12-23
> **lykwydchykyn said:**
> Post the output of these commands:

```

sudo netstat -tunap
sudo iptables -l
last
who

```

That should help us determine if anyone has been remoting in to mess with you.  Also check /var/log/auth.log and see if there are user names other than yours in there (there will be a number of root logins attributed to the cron daemon, that's normal).



a@ubuntu-a:~$ sudo netstat -tunap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *************           0.0.0.0:*               LISTEN      5212/cupsd      
tcp        0      0 *************      66.151.149.78:80        ESTABLISHED 6072/firefox    
tcp        0      0 *************     81.18.240.138:80        ESTABLISHED 6072/firefox    
tcp        0      0 2*************8      66.151.149.78:80        ESTABLISHED 6072/firefox    
tcp        0      0 2*************505      66.151.149.78:80        ESTABLISHED 6072/firefox    
tcp        0      0 *************75      66.151.149.74:80        ESTABLISHED 6072/firefox    
tcp        1      0 *************11      91.189.94.12:80         CLOSE_WAIT  6072/firefox    
tcp        1      0 2*************210      91.189.94.12:80         CLOSE_WAIT  6072/firefox    
tcp        1      0 *************      91.189.94.12:80         CLOSE_WAIT  6072/firefox    
tcp        0      0 2*************07      66.151.149.78:80        ESTABLISHED 6072/firefox    
tcp        1      0 *************13      91.189.94.12:80         CLOSE_WAIT  6072/firefox    
tcp        0      0 *************04      66.151.149.78:80        ESTABLISHED 6072/firefox    
tcp        0      0 2*************13      66.151.149.78:80        ESTABLISHED 6072/firefox    
tcp        1      0 2*************2      91.189.94.12:80         CLOSE_WAIT  6072/firefox    
tcp        0      0 2*************06      66.151.149.78:80        ESTABLISHED 6072/firefox    
tcp        1      0 2*************215      91.189.94.12:80         CLOSE_WAIT  6072/firefox    
tcp        0      0 24*************336      74.125.45.83:80         ESTABLISHED 6072/firefox    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           5566/dhclient   
udp        0      0 0.0.0.0:51045           0.0.0.0:*                           5071/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5071/avahi-daemon:


a@ubuntu-a:~$ sudo iptables -l
iptables v1.3.8: Unknown arg `-l'
Try `iptables -h' or 'iptables --help' for more information.



a@ubuntu-a:~$ last
a        pts/0        :0.0             Tue Dec 23 17:39   still logged in   
a        tty7         :0               Tue Dec 23 17:37   still logged in   
reboot   system boot  2.6.24-22-generi Tue Dec 23 17:36 - 17:41  (00:04)    
a        pts/0        :0.0             Tue Dec 23 12:15 - 12:15  (00:00)    
a        pts/0        :0.0             Tue Dec 23 12:02 - 12:05  (00:03)    
a        pts/0        :0.0             Tue Dec 23 11:46 - 11:56  (00:09)    
a        tty7         :0               Tue Dec 23 08:31 - 12:25  (03:53)    
reboot   system boot  2.6.24-22-generi Tue Dec 23 08:31 - 12:25  (03:53)    
a        tty7         :0               Mon Dec 22 22:43 - 22:59  (00:16)    
reboot   system boot  2.6.24-22-generi Mon Dec 22 22:43 - 22:59  (00:16)    
a        pts/0        :0.0             Mon Dec 22 22:40 - 22:41  (00:01)    
a        pts/0        :0.0             Mon Dec 22 22:29 - 22:39  (00:10)    
a        pts/0        :0.0             Mon Dec 22 22:23 - 22:26  (00:03)    
a        tty7         :0               Mon Dec 22 22:21 - 22:42  (00:20)    
reboot   system boot  2.6.24-22-generi Mon Dec 22 22:21 - 22:42  (00:20)    
a        tty7         :0               Mon Dec 22 08:18 - 08:46  (00:27)    
reboot   system boot  2.6.24-22-generi Mon Dec 22 08:18 - 08:46  (00:27)    
a        tty7         :0               Sat Dec 20 22:52 - 23:43  (00:50)    
reboot   system boot  2.6.24-22-generi Sat Dec 20 22:52 - 23:43  (00:51)    
a        tty7         :0               Sat Dec 20 11:04 - 11:04  (00:00)    
reboot   system boot  2.6.24-22-generi Sat Dec 20 11:04 - 11:04  (00:00)    
a        tty7         :0               Fri Dec 19 14:49 - 14:55  (00:06)    
reboot   system boot  2.6.24-22-generi Fri Dec 19 14:49 - 14:55  (00:06)    
a        tty7         :0               Wed Dec 17 16:23 - 18:43  (02:20)    
reboot   system boot  2.6.24-22-generi Wed Dec 17 16:23 - 18:43  (02:20)    
a        tty7         :0               Mon Dec 15 15:57 - 16:20  (00:22)    
reboot   system boot  2.6.24-22-generi Mon Dec 15 15:57 - 16:20  (00:23)    
a        tty7         :0               Sun Dec 14 14:28 - 14:28  (00:00)    
reboot   system boot  2.6.24-22-generi Sun Dec 14 14:28 - 14:28  (00:00)    
a        tty7         :0               Sun Dec 14 14:26 - 14:26  (00:00)    
reboot   system boot  2.6.24-22-generi Sun Dec 14 14:25 - 14:26  (00:00)    
a        tty7         :0               Sun Dec 14 14:23 - 14:23  (00:00)    
a        tty7         :0               Sun Dec 14 12:11 - 14:23  (02:11)    
reboot   system boot  2.6.24-22-generi Sun Dec 14 12:10 - 14:23  (02:12)    
a        tty7         :0               Sat Dec 13 15:08 - 23:03  (07:55)    
reboot   system boot  2.6.24-22-generi Sat Dec 13 15:08 - 23:03  (07:55)    
a        tty7         :0               Sat Dec 13 14:59 - 15:06  (00:06)    
reboot   system boot  2.6.24-22-generi Sat Dec 13 14:59 - 15:07  (00:07)    
a        tty7         :0               Fri Dec 12 15:25 - 16:08  (00:43)    
reboot   system boot  2.6.24-22-generi Fri Dec 12 15:25 - 16:08  (00:43)    
a        tty7         :0               Fri Dec 12 14:46 - 15:24  (00:37)    
reboot   system boot  2.6.24-22-generi Fri Dec 12 14:46 - 15:24  (00:37)    
a        pts/0        :0.0             Thu Dec 11 18:15 - 18:17  (00:02)    
a        pts/0        :0.0             Thu Dec 11 18:12 - 18:13  (00:00)    
a        pts/1        :0.0             Thu Dec 11 18:09 - 18:19  (00:10)    
a        pts/0        :0.0             Thu Dec 11 18:09 - 18:12  (00:02)    
a        tty7         :0               Thu Dec 11 17:56 - 19:07  (01:10)    
reboot   system boot  2.6.24-22-generi Thu Dec 11 17:55 - 19:07  (01:11)    
a        tty7         :0               Wed Dec 10 17:44 - crash (1+00:11)   
reboot   system boot  2.6.24-22-generi Wed Dec 10 17:43 - 19:07 (1+01:24)   
a        tty7         :0               Tue Dec  9 16:23 - 16:32  (00:08)    
reboot   system boot  2.6.24-22-generi Tue Dec  9 16:22 - 16:32  (00:09)    
a        pts/0        :0.0             Mon Dec  8 21:57 - 21:57  (00:00)    
a        tty7         :0               Mon Dec  8 17:41 - 21:59  (04:18)    
reboot   system boot  2.6.24-22-generi Mon Dec  8 17:41 - 21:59  (04:18)    
a        tty7         :0               Mon Dec  8 17:12 - 17:33  (00:20)    
reboot   system boot  2.6.24-19-generi Mon Dec  8 12:12 - 17:33  (05:20)    

wtmp begins Mon Dec  8 12:12:28 2008


a@ubuntu-a:~$ who
a        tty7         2008-12-23 17:37 (:0)
a        pts/1        2008-12-23 17:45 (:0.0)

---

### Post by lykwydchykyn on 2008-12-24
Oops, should have been iptables -L.  Based on the other data, though, I don't think anyone is in there messing with you, unless they're REALLY clever.  If you still aren't sure, try disconnecting the network for a bit and see if it happens then.

If you can borrow a different mouse, see if that helps any.

---

### Post by hyper_ch on 2008-12-24
it's no virus.

---

### Post by cariboo on 2008-12-24
To get a listing of your firewall rules you need to type:

```
sudo iptables -L
```

The command posted above was a typo.

Jim

---

### Post by NoBugs! on 2009-01-06
Sounds like it's most likely a software bug or problem with the mouse. Some mouse pads will cause optical mice to jump around, have you tried a different surface/mousepad?

---

### Post by jrusso2 on 2009-01-06
Sounds like it might be some kind of trojan or malware since you were on myspace which is known for this and you said its making its own directory and clicking profiles.  You should have the most recent browser and most recent flash.  You should also run the newest Java and VLC or you will be vulerable. You should also get the no script plugin for firefox I would not go near myspace without it.

---

### Post by Chayak on 2009-01-06
> **jrusso2 said:**
> Sounds like it might be some kind of trojan or malware since you were on myspace which is known for this and you said its making its own directory and clicking profiles.  You should have the most recent browser and most recent flash.  You should also run the newest Java and VLC or you will be vulerable. You should also get the no script plugin for firefox I would not go near myspace without it.

I seriously doubt it.  I see malware samples every day, it's my job and I've yet to see a sample that will infect Linux.  If it is I want a copy because no one I work with would believe it.

A malware author wants distribution.  Why waste the time and effort developing something that will run on a very small percentage of Linux users coming to a site when you can put less effort into writing something for windows and get magnitudes more hosts hooked?

---

### Post by jrusso2 on 2009-01-06
> **Chayak said:**
> I seriously doubt it.  I see malware samples every day, it's my job and I've yet to see a sample that will infect Linux.  If it is I want a copy because no one I work with would believe it.

A malware author wants distribution.  Why waste the time and effort developing something that will run on a very small percentage of Linux users coming to a site when you can put less effort into writing something for windows and get magnitudes more hosts hooked?

It could still be malware but related to flash or java or java script not Linux.  I have done flash tests that crashed my browser on both Windows and Linux.

It does not mean its a virus.  How would a bug make directory?

---

### Post by teddks on 2009-01-06
To my knowledge there are no GNU/Linux viruses in the wild as of now. It's incredibly more likely it's just a buggy mouse driver.

---

### Post by landerblonde on 2009-03-14
I have the same problem with my mouse moving on it's own.  It runs across the page like someone is controlling and trying to access info.  Hard to even restart computer.  I believe there is a virus or someone hacking into my computer but not sure what to do.  Checked for virus and added firestarter application on my laptop.  Any ideas on how to fix?

---

### Post by bodhi.zazen on 2009-03-14
I am going to close this thread now as it seems to be spreading FUD.

As has been stated, there are no known viruses in Linux that would do anything like this.

It is sad that viruses are such a problem in other OS that users assume any and every problem is due to a virus.

Although I do not know the problem, I suggest you post in general help.

---

