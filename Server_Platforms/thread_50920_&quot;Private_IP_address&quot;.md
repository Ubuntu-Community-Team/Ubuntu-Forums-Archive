---
title: "&quot;Private IP address&quot;"
date: 2005-07-21
forum: Server Platforms
---

### Post by lsg on 2005-07-21
Hi, i am kinda new to linux 6 montswith ubuntu. I was checking to see who was logged on with the last-i command and i found a private ip address 194.135.4.8 logged on, so i disable internet access and rebooted but the same ip address was there logged in.

Is this something i should be worried about? any help would be appreciated.
This is a partial result of the last -i command.

administ pts/0        192.168.*.*     Thu Jul 21 16:16   still logged in   
administ pts/0        192.168.*.*     Wed Jul 20 20:15 - 20:20  (00:05)    
administ pts/0        192.168.*.*     Wed Jul 20 19:57 - 20:14  (00:16)    
administ pts/1        192.168.*.*     Wed Jul 20 19:53 - 19:53  (00:00)    
administ pts/0        0.0.0.0          Wed Jul 20 19:32 - 19:56  (00:24)    
administ pts/0        192.168.*.*     Wed Jul 20 19:26 - 19:32  (00:05)    
administ pts/0        192.168.*.*     Wed Jul 20 19:16 - 19:25  (00:09)    
administ pts/0        192.168.*.*     Wed Jul 20 18:50 - 18:51  (00:00)    
administ pts/0        192.168.*.*     Wed Jul 20 18:49 - 18:50  (00:00)    
administ pts/1        192.168.*.*     Wed Jul 20 17:47 - 17:48  (00:01)    
administ pts/0        0.0.0.0          Wed Jul 20 17:45 - 17:54  (00:08)    
administ pts/0        0.0.0.0          Wed Jul 20 17:36 - 17:42  (00:06)    
administ :0           194.135.4.8      Wed Jul 20 17:35   still logged in   
reboot   system boot  0.0.0.0          Wed Jul 20 17:34          (23:54)    
administ pts/0        0.0.0.0          Wed Jul 20 16:09 - 16:42  (00:32)    
administ pts/1        0.0.0.0          Wed Jul 20 06:08 - 06:08  (00:00)    
administ pts/0        0.0.0.0          Wed Jul 20 06:07 - 06:11  (00:04)    
administ pts/0        0.0.0.0          Tue Jul 19 23:40 - 23:41  (00:00)    
administ :0           194.135.4.8      Tue Jul 19 23:39 - 16:42  (17:03)    
reboot   system boot  0.0.0.0          Tue Jul 19 23:38          (17:04)    
administ pts/0        0.0.0.0          Tue Jul 19 23:21 - 23:36  (00:15)    
administ pts/0        0.0.0.0          Tue Jul 19 23:13 - 23:14  (00:01)    
administ pts/0        0.0.0.0          Tue Jul 19 23:07 - 23:13  (00:05)    
administ pts/0        0.0.0.0          Tue Jul 19 22:57 - 22:59  (00:01)    
administ :0           194.135.4.8      Tue Jul 19 22:55 - 23:37  (00:42)    
reboot   system boot  0.0.0.0          Tue Jul 19 22:54          (00:43)    
administ pts/0        0.0.0.0          Tue Jul 19 22:42 - 22:49  (00:06)    
administ pts/0        0.0.0.0          Tue Jul 19 22:15 - 22:38  (00:22)    
administ pts/0        0.0.0.0          Tue Jul 19 22:05 - 22:11  (00:05)    
administ :0           194.135.4.8      Tue Jul 19 22:02 - 22:49  (00:47)    
reboot   system boot  0.0.0.0          Tue Jul 19 22:01          (00:48)    
administ pts/0        0.0.0.0          Tue Jul 19 21:53 - 21:56  (00:03)    
administ pts/0        0.0.0.0          Tue Jul 19 21:48 - 21:52  (00:04)    
administ pts/0        192.168.*.*     Tue Jul 19 21:25 - 21:47  (00:22)    
administ pts/1        192.168.*.*     Tue Jul 19 21:12 - 21:23  (00:10)    
administ pts/0        192.168.*.*     Tue Jul 19 20:45 - 21:23  (00:38)    
administ pts/0        0.0.0.0          Sat Jul 16 17:11 - 17:11  (00:00)    
administ pts/0        192.168.*.*     Sat Jul 16 14:37 - 15:21  (00:44)    
administ pts/0        192.168.*.*     Sat Jul 16 13:26 - 13:51  (00:24)    
administ pts/1        0.0.0.0          Sat Jul 16 09:16 - 11:54  (02:37)    
administ pts/0        192.168.*.*     Sat Jul 16 09:15 - 12:23  (03:08)    
administ pts/0        0.0.0.0          Sat Jul 16 09:06 - 09:07  (00:00)    
administ :0           194.135.4.8      Sat Jul 16 07:52 - 21:56 (3+14:04)   
reboot   system boot  0.0.0.0          Sat Jul 16 07:48         (3+14:08)   
administ :0           194.135.4.8      Sat Jul 16 07:38 - crash  (00:10)    
reboot   system boot  0.0.0.0          Sat Jul 16 05:37         (3+16:18)   
administ pts/0        192.168.*.*     Sat Jul 16 02:42 - 02:56  (00:14)    
administ pts/0        0.0.0.0          Sat Jul 16 02:37 - 02:38  (00:00)    
administ pts/1        192.168.*.*     Sat Jul 16 02:35 - 02:38  (00:03)    
administ pts/0        0.0.0.0          Sat Jul 16 02:27 - 02:37  (00:09)    
administ pts/0        0.0.0.0          Sat Jul 16 02:26 - 02:27  (00:00)    
administ pts/0        192.168.*.*     Sat Jul 16 02:18 - 02:24  (00:05)    
administ pts/0        192.168.*.*     Sat Jul 16 02:09 - 02:11  (00:02)    
administ pts/0        192.168.*.*     Sat Jul 16 02:02 - 02:08  (00:05)    
administ pts/1        0.0.0.0          Sat Jul 16 01:33 - 01:34  (00:00)    
administ pts/1        0.0.0.0          Sat Jul 16 01:23 - 01:25  (00:01)    
administ pts/0        192.168.*.*     Sat Jul 16 01:22 - 01:37  (00:15)

---

### Post by jasmuz on 2005-07-21
Buddy read this: [http://en.wikipedia.org/wiki/Private_IP_address](http://en.wikipedia.org/wiki/Private_IP_address)

Those IP addresses are local, wich means there is no security risk because they are from your own machine.

---

### Post by crashtest on 2005-07-21
[QUOTE=jasmuz]Buddy read this: [http://en.wikipedia.org/wiki/Private_IP_address](http://en.wikipedia.org/wiki/Private_IP_address)

Those IP addresses are local, wich means there is no security risk because they are from your own machine.[/QUOTE]

The 192.168.*.* addresses in the log are private addresses, and are on his local network.  However, the 194.135.4.8 IP which he mentions is a public address, not private.  I would say this needs a little further investigation.  Any security experts out there?

---

### Post by souki on 2005-07-21
what the hell is that?

I have the same thing !!!!

```
souki    :0           194.135.4.8      Wed Jul 20 18:40   still logged in
souki    tty1         0.0.0.0          Wed Jul 20 18:39   still logged in
reboot   system boot  0.0.0.0          Wed Jul 20 18:33         (1+09:45)
```
I've found [this link](http://lists.ubuntu.com/archives/kubuntu-users/2005-July/001247.html)  on google, it says it is a bug

---

### Post by crashtest on 2005-07-21
[QUOTE=souki]what the hell is that?

I have the same thing !!!!

```
souki    :0           194.135.4.8      Wed Jul 20 18:40   still logged in
souki    tty1         0.0.0.0          Wed Jul 20 18:39   still logged in
reboot   system boot  0.0.0.0          Wed Jul 20 18:33         (1+09:45)
```
I've found [this link](http://lists.ubuntu.com/archives/kubuntu-users/2005-July/001247.html)  on google, it says it is a bug[/QUOTE]

OK, that's good.  Clearly a bug, and it is fixed in breezy.  Nice.

---

### Post by lsg on 2005-07-21
[QUOTE=crashtest]OK, that's good.  Clearly a bug, and it is fixed in breezy.  Nice.[/QUOTE]
 Did someone find a fix? Is it a bug? I hope that`s what it is!

---

