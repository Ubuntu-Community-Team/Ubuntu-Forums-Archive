---
title: "Am I being hacked"
date: 2009-11-27
forum: Security
---

### Post by Xog on 2009-11-27
There's hundreds of lines of this in my messages system log viewer. including when I was sleeping.
```
Nov 27 17:50:50 logan-laptop kernel: [53920.243308] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=88.233.63.108 DST=me.me.me.me LEN=60 TOS=0x00 PREC=0x00 TTL=47 ID=21334 DF PROTO=TCP SPT=47813 DPT=58535 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 27 17:50:59 logan-laptop kernel: [53929.014396] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=88.233.63.108 DST=me.me.me.me LEN=60 TOS=0x00 PREC=0x00 TTL=47 ID=21336 DF PROTO=TCP SPT=47813 DPT=58535 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 27 17:51:11 logan-laptop kernel: [53941.131929] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=88.233.63.108 DST=me.me.me.me LEN=60 TOS=0x00 PREC=0x00 TTL=47 ID=21337 DF PROTO=TCP SPT=47813 DPT=58535 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 27 17:51:35 logan-laptop kernel: [53965.077043] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=88.233.63.108 DST=me.me.me.me LEN=60 TOS=0x00 PREC=0x00 TTL=47 ID=21338 DF PROTO=TCP SPT=47813 DPT=58535 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov 27 17:51:45 logan-laptop kernel: [53974.718641] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=32051 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 27 17:51:46 logan-laptop kernel: [53975.652074] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=32187 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 27 17:51:47 logan-laptop kernel: [53976.651962] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=32321 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 27 17:51:48 logan-laptop kernel: [53977.657952] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=32431 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 27 17:51:49 logan-laptop kernel: [53978.665084] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=32596 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 27 17:51:50 logan-laptop kernel: [53979.668581] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=32829 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 27 17:51:52 logan-laptop kernel: [53981.683505] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=33208 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 27 17:52:04 logan-laptop kernel: [53993.718460] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=48 TOS=0x00 PREC=0x00 TTL=45 ID=35414 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 27 17:52:20 logan-laptop kernel: [54009.756340] Inbound IN=eth0 OUT= MAC=00:15:c5:1e:d4:ce:00:05:00:e7:14:b7:08:00 SRC=71.80.210.189 DST=me.me.me.me LEN=48 TOS=0x00 PREC=0x00 TTL=45 ID=37552 DF PROTO=TCP SPT=12221 DPT=58535 WINDOW=65535 RES=0x00 SYN URGP=0
```

Also in my 'messages' Log it says,
/var/log/btmp
The file is not a regular file or is not a text file.

What does this mean?

---

### Post by Xog on 2009-11-27
I looked up one of the IP addresses on the list ( 88.233.63.108 ) and it says it's located in Istanbul, Turkey :O

General Information

      Hostname:	dsl88-233-16236.ttnet.net.tr
      ISP:	Turk Telekom
      Organization:	Turk Telekom
      Proxy:	None detected
      Type:	Cable/DSL
      Blacklist:	

Geo-Location Information

      Country:	Turkey
      State/Region:	34
      City:	Istanbul
      Latitude:	41.0186
      Longitude:	28.9647
      Area Code:	


:|

another one's in china
and another one's in castro valley, california ( 24.4.193.8 )

General Information

      Hostname:	c-24-4-193-8.hsd1.ca.comcast.net
      ISP:	Comcast Cable
      Organization:	Comcast Cable
      Proxy:	None detected
      Type:	Cable/DSL
      Blacklist:	

Geo-Location Information

      Country:	United States
      State/Region:	CA
      City:	Castro Valley
      Latitude:	37.709
      Longitude:	-122.0885
      Area Code:	510

---

### Post by cariboo on 2009-11-27
btmp a log file that contains all the last bad login attempts. More info is available by running man lastb.

---

### Post by Xog on 2009-11-27
> **cariboo907 said:**
> btmp a log file that contains all the last bad login attempts. More info is available by running man lastb.
```

logan@logan-laptop:~$ lastb
UNKNOWN  tty1                          Fri Nov 27 02:50 - 02:50  (00:00)    

btmp begins Fri Nov 27 02:50:33 2009
logan@logan-laptop:~$ 

```
firewall + messages
[http://img513.imageshack.us/img513/807/screenshot2tv.png](http://img513.imageshack.us/img513/807/screenshot2tv.png)

These are all the logins from nov. 21st to now.
```

logan@logan-laptop:~$ last
logan    pts/1        :0.0             Fri Nov 27 18:15   still logged in   
logan    pts/0        :0.0             Fri Nov 27 18:12   still logged in   
logan    pts/0        :0.0             Fri Nov 27 17:10 - 17:50  (00:40)    
logan    pts/0        :0.0             Fri Nov 27 05:45 - 06:48  (01:02)    
logan    pts/0        :0.0             Fri Nov 27 04:23 - 04:23  (00:00)    
logan    pts/0        :0.0             Fri Nov 27 04:12 - 04:20  (00:08)    
logan    pts/0        :0.0             Fri Nov 27 04:09 - 04:09  (00:00)    
logan    pts/0        :0.0             Fri Nov 27 02:58 - 02:58  (00:00)    
logan    tty7         :0               Fri Nov 27 02:53   still logged in   
reboot   system boot  2.6.31-15-generi Fri Nov 27 02:53 - 18:21  (15:28)    
logan    tty1                          Fri Nov 27 02:50 - down   (00:01)    
logan    tty1                          Fri Nov 27 02:50 - 02:50  (00:00)    
logan    pts/0        :0.0             Fri Nov 27 02:43 - down   (00:08)    
logan    pts/2        :0.0             Fri Nov 27 02:35 - 02:40  (00:05)    
logan    tty7         :0               Fri Nov 27 02:18 - down   (00:33)    
reboot   system boot  2.6.31-15-generi Fri Nov 27 02:18 - 02:51  (00:33)    
logan    pts/0        :0.0             Fri Nov 27 02:08 - 02:15  (00:07)    
logan    pts/0        :0.0             Fri Nov 27 00:53 - 00:57  (00:04)    
logan    pts/0        :0.0             Thu Nov 26 22:17 - 22:19  (00:01)    
logan    pts/0        :0.0             Thu Nov 26 20:34 - 20:36  (00:01)    
logan    pts/0        :0.0             Thu Nov 26 20:28 - 20:33  (00:04)    
logan    pts/0        :0.0             Thu Nov 26 20:20 - 20:26  (00:05)    
logan    tty7         :0               Thu Nov 26 19:56 - down   (06:21)    
reboot   system boot  2.6.31-15-generi Thu Nov 26 19:56 - 02:17  (06:21)    
logan    pts/0        :0.0             Thu Nov 26 19:10 - 19:12  (00:01)    
logan    tty7         :0               Thu Nov 26 18:55 - 19:24  (00:29)    
reboot   system boot  2.6.31-15-generi Thu Nov 26 18:55 - 19:24  (00:29)    
logan    tty7         :0               Thu Nov 26 14:49 - crash  (04:05)    
reboot   system boot  2.6.31-15-generi Thu Nov 26 14:49 - 19:24  (04:35)    
logan    tty7         :0               Wed Nov 25 19:05 - 14:22  (19:16)    
reboot   system boot  2.6.31-15-generi Wed Nov 25 19:05 - 14:22  (19:17)    
logan    pts/0        :0.0             Tue Nov 24 19:18 - 19:19  (00:01)    
logan    pts/1        :0.0             Tue Nov 24 19:01 - 19:02  (00:01)    
logan    pts/0        :0.0             Tue Nov 24 18:58 - 19:01  (00:02)    
logan    tty7         :0               Tue Nov 24 18:52 - down   (14:54)    
reboot   system boot  2.6.31-15-generi Tue Nov 24 18:52 - 09:46  (14:54)    
logan    pts/0        :0.0             Tue Nov 24 03:00 - 03:00  (00:00)    
logan    tty7         :0               Tue Nov 24 02:54 - down   (05:38)    
reboot   system boot  2.6.31-15-generi Tue Nov 24 02:54 - 08:33  (05:38)    
logan    tty7         :0               Tue Nov 24 02:45 - down   (00:07)    
reboot   system boot  2.6.31-15-generi Tue Nov 24 02:45 - 02:53  (00:07)    
logan    pts/0        :0.0             Tue Nov 24 01:41 - 01:41  (00:00)    
logan    tty7         :0               Mon Nov 23 21:03 - down   (05:41)    
reboot   system boot  2.6.31-15-generi Mon Nov 23 21:02 - 02:44  (05:41)    
logan    tty7         :0               Mon Nov 23 06:10 - down   (00:03)    
reboot   system boot  2.6.31-15-generi Mon Nov 23 06:10 - 06:13  (00:03)    
logan    tty7         :0               Mon Nov 23 05:30 - 05:36  (00:05)    
reboot   system boot  2.6.31-15-generi Mon Nov 23 05:30 - 05:36  (00:05)    
logan    pts/0        :0.0             Mon Nov 23 02:04 - 02:07  (00:02)    
logan    tty7         :0               Mon Nov 23 01:25 - down   (01:49)    
reboot   system boot  2.6.31-15-generi Mon Nov 23 01:25 - 03:15  (01:49)    
logan    tty7         :0               Mon Nov 23 00:39 - crash  (00:45)    
reboot   system boot  2.6.31-15-generi Mon Nov 23 00:39 - 03:15  (02:35)    
logan    pts/0        :0.0             Mon Nov 23 00:37 - crash  (00:01)    
logan    tty7         :0               Mon Nov 23 00:05 - crash  (00:33)    
reboot   system boot  2.6.31-15-generi Mon Nov 23 00:05 - 03:15  (03:09)    
logan    tty7         :0               Sun Nov 22 22:52 - down   (01:12)    
reboot   system boot  2.6.31-15-generi Sun Nov 22 22:52 - 00:05  (01:12)    
logan    pts/1        :0.0             Sun Nov 22 22:45 - 22:48  (00:02)    
logan    pts/0        :0.0             Sun Nov 22 22:25 - 22:51  (00:25)    
logan    pts/0        :0.0             Sun Nov 22 22:24 - 22:24  (00:00)    
logan    pts/0        :0.0             Sun Nov 22 17:37 - 18:29  (00:51)    
logan    pts/0        :0.0             Sun Nov 22 17:26 - 17:27  (00:00)    
logan    tty7         :0               Sun Nov 22 17:25 - down   (05:25)    
reboot   system boot  2.6.31-15-generi Sun Nov 22 17:25 - 22:51  (05:25)    
logan    pts/0        :0.0             Sun Nov 22 17:22 - 17:23  (00:01)    
logan    pts/0        :0.0             Sun Nov 22 16:51 - 16:51  (00:00)    
logan    tty7         :0               Sun Nov 22 16:09 - down   (01:15)    
reboot   system boot  2.6.31-15-generi Sun Nov 22 16:08 - 17:24  (01:16)    
logan    pts/2        :0.0             Sun Nov 22 15:51 - 15:51  (00:00)    
logan    pts/0        :0.0             Sun Nov 22 15:51 - down   (00:16)    
logan    pts/0        :0.0             Sat Nov 21 18:03 - 18:39  (00:35)    
logan    tty7         :0               Sat Nov 21 17:59 - down   (22:07)    
reboot   system boot  2.6.31-15-generi Sat Nov 21 17:59 - 16:07  (22:08)    
logan    tty7         :0               Sat Nov 21 17:07 - down   (00:51)    
reboot   system boot  2.6.31-14-generi Sat Nov 21 17:07 - 17:58  (00:51)    
logan    tty7         :0               Sat Nov 21 12:11 - crash  (04:56)    
reboot   system boot  2.6.31-14-generi Sat Nov 21 12:11 - 17:58  (05:47)    
logan    tty7         :0               Sat Nov 21 01:20 - down   (02:39)    
reboot   system boot  2.6.31-14-generi Sat Nov 21 01:20 - 04:00  (02:40)    

```
I'm also beginning to get red messages in the firewall from blocked connections. Service is Telnet. ??

[http://img522.imageshack.us/img522/7302/screenshot3rq.png](http://img522.imageshack.us/img522/7302/screenshot3rq.png)

and im getting these in my auth:
```

Nov 27 11:17:01 logan-laptop CRON[5542]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 27 11:17:01 logan-laptop CRON[5542]: pam_unix(cron:session): session closed for user root
Nov 27 12:17:01 logan-laptop CRON[5553]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 27 12:17:01 logan-laptop CRON[5553]: pam_unix(cron:session): session closed for user root
Nov 27 13:17:01 logan-laptop CRON[5570]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 27 13:17:01 logan-laptop CRON[5570]: pam_unix(cron:session): session closed for user root
Nov 27 14:17:01 logan-laptop CRON[5583]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 27 14:17:01 logan-laptop CRON[5583]: pam_unix(cron:session): session closed for user root
Nov 27 15:17:01 logan-laptop CRON[5602]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 27 15:17:01 logan-laptop CRON[5602]: pam_unix(cron:session): session closed for user root
Nov 27 16:17:01 logan-laptop CRON[5624]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 27 16:17:01 logan-laptop CRON[5624]: pam_unix(cron:session): session closed for user root
Nov 27 17:05:40 logan-laptop sudo:    logan : TTY=unknown ; PWD=/home/logan ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817411 --update-at-startup
Nov 27 17:08:00 logan-laptop sudo:    logan : TTY=unknown ; PWD=/home/logan ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817411 --update-at-startup
Nov 27 17:09:51 logan-laptop sudo:    logan : TTY=unknown ; PWD=/home/logan ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Nov 27 17:10:39 logan-laptop sudo:    logan : TTY=pts/0 ; PWD=/home/logan ; USER=root ; COMMAND=/usr/bin/apt-key add -
Nov 27 17:10:59 logan-laptop sudo:    logan : TTY=unknown ; PWD=/home/logan ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Nov 27 17:11:17 logan-laptop sudo:    logan : TTY=unknown ; PWD=/home/logan ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817445 --update-at-startup
Nov 27 17:11:43 logan-laptop sudo:    logan : TTY=unknown ; PWD=/home/logan ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817411 --update-at-startup
Nov 27 17:11:53 logan-laptop sudo:    logan : TTY=unknown ; PWD=/home/logan ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817411 --set-selections-file /tmp/tmp0J4dWG
Nov 27 17:17:01 logan-laptop CRON[6087]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 27 17:17:01 logan-laptop CRON[6087]: pam_unix(cron:session): session closed for user root
Nov 27 18:09:13 logan-laptop sudo:    logan : TTY=unknown ; PWD=/home/logan ; USER=root ; COMMAND=/usr/sbin/firestarter
Nov 27 18:17:01 logan-laptop CRON[7341]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 27 18:17:01 logan-laptop CRON[7341]: pam_unix(cron:session): session closed for user root
```

---

### Post by Xog on 2009-11-27
nothing

---

### Post by OpSecShellshock on 2009-11-27
There seems to be some port scanning going on at the very least. Some of the more obvious stuff (telnet, ssh, http) looks like it's not being allowed or that it's just unsuccessful password guessing.

How do you have iptables configured? You can go to the Policy tab in Firestarter and check to see what your inbound and outbound settings look like. Outbound should be set to "restrictive by default." Then you try the network applications you need to use and see which ones break because they can't establish connections. Once you know that, you can add rules (and be sure to activate them) to allow for those ports for specific applications.

Once that's done, there should be no reason to open any inbound ports since you won't want any connections coming in until you've sent a request out. To ensure this, select "inbound policy" from the drop down menu and make sure everything is blank. At the moment I'd guess that you have inbound traffic to port 55835 allowed for some reason.

Also you'll want to be sure and disable VNC. I can't remember how to do that off the top of my head, but it should be easy to find. If you can afford it, I'd suggest looking into getting a hardware router/firewall to put between your computer and your modem.

---

### Post by Xog on 2009-11-28
thanks

---

### Post by The Cog on 2009-11-29
It looks to me like your firewall is logging lots of blocked incoming connection attempts. Firewalls are supposed to block incoming connection attempts though, so I don't see a problem with that. 

Unless you install a service or enable remote desktop viewing then even without a firewall to block incoming connections, there wouldn't be anything running to accept those connection attempts. My advice is to do 4 things:
1) Disable remote desktop if it's enabled
2) Don't install any servers (ssh, http etc.) without very good reason
3) Make sure the firewall is configured to drop incoming connections
4) Stop looking at the firewall logs - they'll keep you awake at night

---

### Post by Beverly Roberts on 2009-11-29
Clearly, from the log files. There are numerous failed intrusion attempts. 

Beverly Roberts

---

### Post by u.b.u.n.t.u on 2009-11-30
Xog you didn't state, but in instances where file sharing was enabled over a period of time, and then stopped, continued attempts to create a connection may continue for some time.

---

