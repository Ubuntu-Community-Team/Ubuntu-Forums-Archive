---
title: "help with email spamming."
date: 2021-11-24
forum: Security
---

### Post by ulao3 on 2021-11-24
I know I have a pc on my network that is spamming emails as evidence by a few black list sites. Also yahoo keeps rate limiting me. Though I do not see any evidence on the PC's I have running. I have a few PC's and a few android devices. It is rather hard to turn one off at a time and the end results is not easy to detect. Thus its hard to troubleshoot that way.  So I want to intercept and use linux to hunt it down. Every thing goes out of my ubuntu server, all traffic. but I'm not a security guru by any means. 

I thought maybe I could use iptables like

iptables -A INPUT -p tcp -s 192.168.0.0/25 --dport 25 -j LOG --log-level debug

and tail -f /var/log/kern.log

and there I see a few messages once a second but it looks like my FW is blocking it. 
 
```

Nov 24 14:38:48 ubuntuspawn kernel: [6630908.886197] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=185.219.52.172 DST=[myIP] LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=38447 DF PROTO=TCP SPT=41304 DPT=5927 WINDOW=0 RES=0x00 RST URGP=0
Nov 24 14:38:54 ubuntuspawn kernel: [6630915.201554] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=46.232.211.193 DST=[myIP] LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=24534 DF PROTO=TCP SPT=37905 DPT=40945 WINDOW=64240 RES=0x00 SYN URGP=0
Nov 24 14:39:11 ubuntuspawn kernel: [6630931.733367] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=185.219.52.172 DST=[myIP] LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=38801 DF PROTO=TCP SPT=48692 DPT=5927 WINDOW=0 RES=0x00 RST URGP=0
Nov 24 14:39:15 ubuntuspawn kernel: [6630935.532012] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=172.98.68.19 DST=[myIP] LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=55084 DF PROTO=TCP SPT=55145 DPT=40945 WINDOW=64860 RES=0x00 SYN URGP=0
Nov 24 14:39:33 ubuntuspawn kernel: [6630953.568650] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=61.177.173.11 DST=[myIP] LEN=67 TOS=0x00 PREC=0x00 TTL=47 ID=1181 DF PROTO=TCP SPT=12671 DPT=22 WINDOW=229 RES=0x00 ACK PSH URGP=0
Nov 24 14:39:35 ubuntuspawn kernel: [6630956.301506] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=187.189.88.168 DST=[myIP] LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=17182 PROTO=UDP SPT=10700 DPT=40945 LEN=28
Nov 24 14:39:49 ubuntuspawn kernel: [6630969.761855] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=185.219.52.172 DST=[myIP] LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=39389 DF PROTO=TCP SPT=7954 DPT=5927 WINDOW=0 RES=0x00 RST URGP=0
Nov 24 14:39:54 ubuntuspawn kernel: [6630975.263547] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=37.146.57.182 DST=[myIP] LEN=132 TOS=0x00 PREC=0x00 TTL=108 ID=52386 PROTO=UDP SPT=22879 DPT=40945 LEN=112
Nov 24 14:40:15 ubuntuspawn kernel: [6630996.279388] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=185.159.156.3 DST=[myIP] LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=61920 DF PROTO=TCP SPT=48280 DPT=40945 WINDOW=64240 RES=0x00 SYN URGP=0
Nov 24 14:40:32 ubuntuspawn kernel: [6631012.854881] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=31.13.65.36 DST=[myIP] LEN=40 TOS=0x0C PREC=0x60 TTL=87 ID=0 DF PROTO=TCP SPT=443 DPT=62644 WINDOW=0 RES=0x00 RST URGP=0
Nov 24 14:40:32 ubuntuspawn kernel: [6631012.854945] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=31.13.65.36 DST=[myIP] LEN=40 TOS=0x0C PREC=0x60 TTL=87 ID=0 DF PROTO=TCP SPT=443 DPT=62644 WINDOW=0 RES=0x00 RST URGP=0
Nov 24 14:40:38 ubuntuspawn kernel: [6631018.779255] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=95.192.81.202 DST=[myIP] LEN=52 TOS=0x00 PREC=0x00 TTL=238 ID=23544 DF PROTO=TCP SPT=61805 DPT=40945 WINDOW=64240 RES=0x00 SYN URGP=0

```

other then that I only see this

Nov 24 14:30:47 ubuntuspawn kernel: [6630427.637180] CIFS VFS: Free previous auth_key.response = 0000000048575e17


Is there a better way to go about this?

---

### Post by TheFu on 2021-11-24
Block all outbound 25/tcp and 465/tcp and 587/tcp from the LAN.  Then check which devices are trying to access those ports one at a time and add them to a white list.

I'm lazy and only allow 1 MTA to email outbound. All LAN clients must use my LAN email gateway to send anything.  Typical home users should just know exactly which IP addresses are tied to each device on the LAN, then trace the offender.  This means that either static IPs need to be setup or DHCP reservations for all devices, then you can have a "guest" IP range for unknown stuff.  When people visit, their wifi stuff gets put on that guest range outside my normal LAN.  If there is any abuse, blocking everything for that range is easy.

If your router is also your DHCP server handing out IPs, then it probably can also provide DHCP reservations - which is a MAC to IP allocation method.  Based on the MAC address, when a known client makes a DHCP request, the IP in that table would be provided every time.  [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tries to explain - but don't worry. The old way as that article outlines is mostly gone. Current routers have a table with separate fields.  The only trick is to reserve IPs for devices you know in a different IP range than for devices you don't know.
For example, I handle IPs from .90 - .99 for devices I know on my LAN, but guest devices get .240-.250 IPs <--- that's the normal DHCP IP range.  For LAN static IPs, I use .1 - .89.  
On IPv4 LANs, use the '**arp**' command get get all the current MACs. Run that command from a system they all use.  **ip neigh** is another command that shows MAC-to-IP relations.

---

### Post by Doug S on 2021-11-24
I'm not sure you will catch what you are looking for via the INPUT chain. I would log it, and/or block it, via the FORWARD chain, and with unique log prefixes, for extracting and sorting later on.

I would also, at least temporarily, monitor all packets using tcpdump (or wireshark, if you prefer). I have been logging every external and most internal packet to and from my main gateway router server for many many years, giving me the ability to back and look at event details after the fact. Here are example commands (modified for herein). External:

```
sudo tcpdump -i enp1s0 -w 'ext-%F-%H-%M-%S.bin' -G 601 -Z doug
```
I do 10 minutes per raw file, with the extra second so that the files do not clobber themselves upon the switch between daylight saving time and standard time, although I do still get an interleaved mess.Internal:
```
sudo tcpdump -i enp3s0 not port 22 and not port 445 and not port 139 and not port 5001 -w 'int-%F-%H-%M-%S.bin' -G 601 -Z doug
```
Where I do not want to capture packets related to high volume internal traffic to/from the server itself, so I exclude some ports.

Use caution, as this can use a lot of disk space quickly. I have a 1TB HDD dedicated to this.

EDIT: Oh, and as TheFu suggests, internally I use a DHCP server, but via MAC, so I know the LAN computer for all packets.

---

### Post by ulao3 on 2021-11-25
I do use a DCHP on my linux server, and disable all DHCP on routers. 

I'm not very well versed with tcpdump, but that would be my goto... MY disk space is small so I'd need a way to log only the last X hours. 

can any one explain to me what this means?
sudo tcpdump -i enp1s0 -w 'ext-%F-%H-%M-%S.bin' -G 601 -Z doug
I'm not find anything helpful on the net for a z option. I'm guessing 'doug' is a file name? What is it doing with bin files? Do I listen on my out facing or inward facing nic?

---

### Post by TheFu on 2021-11-25
ALWAYS, ALWAYS, ALWAYS, check the manpages on your local system before running complex commands.  The internet has whatever version it likes.  Your system has the documentation delivered WITH the exact version of the tool.

```
       -Z user
       --relinquish-privileges=user
              If tcpdump is running as root, after opening the capture device or  input  savefile,
              change the user ID to user and the group ID to the primary group of user.

              This behavior is enabled by default (-Z tcpdump), and can be disabled by -Z root.
```

That's from the tcpdump manpage on my system.  Yours could be different.

---

### Post by Doug S on 2021-11-25
> **ulao3 said:**
> can any one explain to me what this means?
sudo tcpdump -i enp1s0 -w 'ext-%F-%H-%M-%S.bin' -G 601 -Z doug
Means to run tcpdump on my external network interface card, automatically naming each file with the date and time, 10 minutes and 1 second per file, and root won't own the binary files but doug will. Example:

```
doug@s15:/media/sdb1/tcpdump/019$ [COLOR="#FF0000"]ls -l ext*.bin | tail -4[/COLOR]
-rw-r--r-- 1 [COLOR="#FF0000"]doug doug[/COLOR]  496623580 Nov 25 10:47 ext-2021-11-25-10-37-43.bin
-rw-r--r-- 1 [COLOR="#FF0000"]doug doug[/COLOR]  395349090 Nov 25 10:57 ext-2021-11-25-10-47-47.bin
-rw-r--r-- 1 [COLOR="#FF0000"]doug doug[/COLOR]    2369897 Nov 25 11:07 ext-2021-11-25-10-57-48.bin
-rw-r--r-- 1 [COLOR="#FF0000"]doug doug[/COLOR]    1056768 Nov 25 11:15 ext-2021-11-25-11-07-51.bin
```

It is sometimes more than 601 seconds between file names, because it'll only do the file rotation upon the next need to write after the time expires.
Now, and based on other log files, say I wanted to investigate in detail something at some specific time. I don't have a specific good example, but say someone trying to access SSH, port 22, (which I picked because I know it is so common):

```
doug@s15:/media/sdb1/tcpdump/019$ tcpdump -n -tttt -r ext-2021-11-25-10-47-47.bin port 22
reading from file ext-2021-11-25-10-47-47.bin, link-type EN10MB (Ethernet), snapshot length 262144
2021-11-25 10:47:52.233181 IP 45.144.225.175.38729 > my ip.22: Flags [S], seq 1571753640, win 65535, length 0
```

> **ulao3 said:**
> What is it doing with bin files?Creating them.

> **ulao3 said:**
> Do I listen on my out facing or inward facing nic?I was suggesting both, but maybe internal would be good enough for your use case.

---

### Post by ulao3 on 2021-11-25
well my case "should" be rather obvious. I think its spamming quite a bit.

I ran this for a few hours. Didnt understated the user thing so left it out. 
 sudo tcpdump -i enp2s0 -w 'ext-%F-%H-%M-%S.bin' -G 601

tcpdump: listening on enp3s5, link-type EN10MB (Ethernet), capture size 262144 bytes
nothing ever displayed on the console. 

> Creating them.
 so it logs to a bin file? That just seems strange if so, I see over 30 files logged in that time and as suggested they are binary file, how do I read that?

thx for the help do far...

---

### Post by Doug S on 2021-11-25
> **ulao3 said:**
> well my case "should" be rather obvious. I think its spamming quite a bit.

I ran this for a few hours. Didnt understated the user thing so left it out. 
 sudo tcpdump -i enp2s0 -w 'ext-%F-%H-%M-%S.bin' -G 601

tcpdump: listening on enp3s5, link-type EN10MB (Ethernet), capture size 262144 bytes
nothing ever displayed on the console. 

 so it logs to a bin file? That just seems strange if so, I see over 30 files logged in that time and as suggested they are binary file, how do I read that?

thx for the help do far...O.K. without any other insight into where or what file to specifically look at in detail, let's just mindlessly process everything into a reduced information text file. We can always go back later and post process again if needed.

```
for f in ext*.bin; do tcpdump -n -tttt -r $f >>alle.txt
for f in int*.bin; do tcpdump -n -tttt -r $f >>alli.txt

```Note: you might have to run it as root, because you left out the user thing.

Now start looking at those text files for whatever, probably packets to/from specific ports. grep will be very handy at this point.

---

### Post by ulao3 on 2021-11-26
I'm ssh'd in as root, and I only have ext files, no int's but when I run the first command I just a singe > prompt. 


root@ubuntuspawn:~# for f in ext*.bin; do tcpdump -n -tttt -r $f >>alle.txt;
>

---

### Post by Doug S on 2021-11-26
Sorry, poorly done on my part:

```
for f in ext*.bin; do tcpdump -n -tttt -r $f >>alle.txt; done
```

---

### Post by ulao3 on 2021-11-26
ahh, yes much better. so I have a lot of activity to look at here but not a clue what it means.

This one bothers me a bit.
2021-11-25 18:52:23.195285 IP 68.94.156.1.53 > 192.168.0.25.56740: 62415 3/0/0 CNAME [www.glb.paypal.com]("http://www.glb.paypal.com")., CNAME www-fastly.glb.paypal.com., A 151.101.193.21 (95)

but I may have made a paypal purchase at that time.

I do see a lot of large ports but figure maybe I should look for mail stuff

```


2021-11-25 19:36:25.420502 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [.], ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 0
2021-11-25 19:36:25.420549 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [.], seq 1:1419, ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 1418
2021-11-25 19:36:25.420600 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [.], seq 1419:2837, ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 1418
2021-11-25 19:36:25.420723 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [.], seq 2837:4255, ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 1418
2021-11-25 19:36:25.420730 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [P.], seq 4255:4277, ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 22

2021-11-25 19:44:40.246956 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [.], ack 204, win 15, length 0
2021-11-25 19:44:40.250097 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [.], seq 1:1461, ack 204, win 15, length 1460
2021-11-25 19:44:40.250361 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [.], seq 1461:2921, ack 204, win 15, length 1460
2021-11-25 19:44:40.250527 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [P.], seq 2921:4341, ack 204, win 15, length 1420
2021-11-25 19:44:41.459477 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [P.], seq 4461:4570, ack 332, win 15, length 109

2021-11-25 20:00:41.290829 IP 80.12.24.12.993 > 192.168.0.31.51664: Flags [.], ack 515, win 4893, length 0
2021-11-25 20:00:50.617010 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], ack 208, win 60, length 0
2021-11-25 20:00:50.621489 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 1:1461, ack 208, win 60, length 1460
2021-11-25 20:00:50.621759 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 1461:2921, ack 208, win 60, length 1460
2021-11-25 20:00:50.621998 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 2921:4381, ack 208, win 60, length 1460
2021-11-25 20:00:50.622223 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 4381:5841, ack 208, win 60, length 1460
2021-11-25 20:00:50.622523 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 5841:7301, ack 208, win 60, length 1460
2021-11-25 20:00:50.622745 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 7301:8761, ack 208, win 60, length 1460
2021-11-25 20:00:50.622778 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 8761:10221, ack 208, win 60, length 1460
2021-11-25 20:00:50.622804 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 10221:11681, ack 208, win 60, length 1460
2021-11-25 20:00:50.622853 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 11681:13141, ack 208, win 60, length 1460
2021-11-25 20:00:50.622904 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 13141:14601, ack 208, win 60, length 1460

2021-11-25 20:00:55.595947 IP 1.1.1.1.53 > 192.168.0.31.53561: 27833 1/0/0 A 104.100.154.143 (54)
2021-11-25 20:01:18.501763 IP 1.1.1.1.53 > 192.168.0.31.55394: 56497 1/0/0 A 104.100.154.143 (52)

```

Strange ports range all over the place
65215
2021-11-25 20:02:10.442216 IP 192.168.0.104.64248 > 151.106.6.79.65215: UDP, length 105

53120 
2021-11-25 20:02:12.105529 IP 192.168.0.27.53120 > 104.244.42.194.443: Flags [.], ack 2372, win 16494, length 0

61995
2021-11-25 20:02:10.445756 IP 192.168.0.104.61995 > 18.67.0.77.443: Flags [P.], seq 1310:1334, ack 21516, win 4320, length 24

saw this - Is this a vnc probe?
2021-11-25 20:02:10.446044 IP 95.143.179.195.27677 > 192.168.0.25.5900: Flags [P.], seq 1:13, ack 13, win 64228, length 12

The files is large (1 meg) but this form will not let me attach it compressed 100k. So much in here to look at.

---

### Post by Doug S on 2021-11-27
> **ulao3 said:**
> This one bothers me a bit.
2021-11-25 18:52:23.195285 IP 68.94.156.1.53 > 192.168.0.25.56740: 62415 3/0/0 CNAME [www.glb.paypal.com]("http://www.glb.paypal.com")., CNAME www-fastly.glb.paypal.com., A 151.101.193.21 (95)

but I may have made a paypal purchase at that time.That is a DNS lookup response. You can tell by the use of port 53 on the DNS server end.

> **ulao3 said:**
> I do see a lot of large ports but figure maybe I should look for mail stuff

```


2021-11-25 19:36:25.420502 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [.], ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 0
2021-11-25 19:36:25.420549 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [.], seq 1:1419, ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 1418
2021-11-25 19:36:25.420600 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [.], seq 1419:2837, ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 1418
2021-11-25 19:36:25.420723 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [.], seq 2837:4255, ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 1418
2021-11-25 19:36:25.420730 IP 142.250.9.109.465 > 192.168.0.111.42034: Flags [P.], seq 4255:4277, ack 261, win 261, options [nop,nop,TS val 2323951554 ecr 3637127513], length 22

2021-11-25 19:44:40.246956 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [.], ack 204, win 15, length 0
2021-11-25 19:44:40.250097 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [.], seq 1:1461, ack 204, win 15, length 1460
2021-11-25 19:44:40.250361 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [.], seq 1461:2921, ack 204, win 15, length 1460
2021-11-25 19:44:40.250527 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [P.], seq 2921:4341, ack 204, win 15, length 1420
2021-11-25 19:44:41.459477 IP 87.248.97.12.995 > 192.168.0.31.49653: Flags [P.], seq 4461:4570, ack 332, win 15, length 109

2021-11-25 20:00:41.290829 IP 80.12.24.12.993 > 192.168.0.31.51664: Flags [.], ack 515, win 4893, length 0
2021-11-25 20:00:50.617010 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], ack 208, win 60, length 0
2021-11-25 20:00:50.621489 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 1:1461, ack 208, win 60, length 1460
2021-11-25 20:00:50.621759 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 1461:2921, ack 208, win 60, length 1460
2021-11-25 20:00:50.621998 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 2921:4381, ack 208, win 60, length 1460
2021-11-25 20:00:50.622223 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 4381:5841, ack 208, win 60, length 1460
2021-11-25 20:00:50.622523 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 5841:7301, ack 208, win 60, length 1460
2021-11-25 20:00:50.622745 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 7301:8761, ack 208, win 60, length 1460
2021-11-25 20:00:50.622778 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 8761:10221, ack 208, win 60, length 1460
2021-11-25 20:00:50.622804 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 10221:11681, ack 208, win 60, length 1460
2021-11-25 20:00:50.622853 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 11681:13141, ack 208, win 60, length 1460
2021-11-25 20:00:50.622904 IP 77.238.185.51.993 > 192.168.0.31.51804: Flags [.], seq 13141:14601, ack 208, win 60, length 1460

2021-11-25 20:00:55.595947 IP 1.1.1.1.53 > 192.168.0.31.53561: 27833 1/0/0 A 104.100.154.143 (54)
2021-11-25 20:01:18.501763 IP 1.1.1.1.53 > 192.168.0.31.55394: 56497 1/0/0 A 104.100.154.143 (52)

```
O.K. so you have identified 192.168.0.111 as the source in the  first example; 192.168.0.31 in the second and third examples. The 4th example are more DNS packets. Which sessions might be bad and which legitimate, I don't know, but assume you can correlate with expected email activity to deduce.

> **ulao3 said:**
> Strange ports range all over the place
65215
2021-11-25 20:02:10.442216 IP 192.168.0.104.64248 > 151.106.6.79.65215: UDP, length 105

53120 
2021-11-25 20:02:12.105529 IP 192.168.0.27.53120 > 104.244.42.194.443: Flags [.], ack 2372, win 16494, length 0

61995
2021-11-25 20:02:10.445756 IP 192.168.0.104.61995 > 18.67.0.77.443: Flags [P.], seq 1310:1334, ack 21516, win 4320, length 24

saw this - Is this a vnc probe?
2021-11-25 20:02:10.446044 IP 95.143.179.195.27677 > 192.168.0.25.5900: Flags [P.], seq 1:13, ack 13, win 64228, length 12

The files is large (1 meg) but this form will not let me attach it compressed 100k. So much in here to look at.

I do not know why 192.168.0.104 might be communicating with 151.106.79 on high port numbers.
192.168.0.27 has a HTTPS session going with 18.67.0.77. The source port number is meaningless, and is used just for traffic control for the session.
Yes, 192.168.0.25 might have a VNC session going. Port 5900 is typically a default 1st VNC session port. You would have to extract more packets to know more, but it isn't a SYN packet, so has the appearance of an in progress tcp session. If it was the session initiator, I do not know how 95.143.179.195 might have become FORWARDed to 192.168.0.25 in the first place.

---

### Post by SeijiSensei on 2021-11-27
> **ulao3 said:**
> I thought maybe I could use iptables like
```
iptables -A INPUT -p tcp -s 192.168.0.0/25 --dport 25 -j LOG --log-level debug
```
and tail -f /var/log/kern.log and there I see a few messages once a second but it looks like my FW is blocking it.[/code]


No, it's not blocking anything of the sort. Look at the destination ports "DPT" in the log file. None of them are 25, or 465, or 587. 
 
```

Nov 24 14:38:48 ubuntuspawn kernel: [6630908.886197] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=185.219.52.172 DST=[myIP] LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=38447 DF PROTO=TCP SPT=41304 **DPT=5927** WINDOW=0 RES=0x00 RST URGP=0
Nov 24 14:38:54 ubuntuspawn kernel: [6630915.201554] [UFW BLOCK] IN=enp2s0 OUT= MAC=00:26:18:92:60:c7:4c:12:65:64:39:50:08:00 SRC=46.232.211.193 DST=[myIP] LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=24534 DF PROTO=TCP SPT=37905 **DPT=40945** WINDOW=64240 RES=0x00 SYN URGP=0

```

You had the glimmerings of a good idea by trying to block outbound traffic to port 25.  The problem is where is the rule placed. Do you have a Linux box running as your router where you can add iptables rules that apply to the entire network?  If all the clients talk to an ordinary router, then you'd need to be able to add the rule there.  Depends on the brand and model.

BTW, the "--log-prefix" parameter to iptables lets you label specific rules in the log.

---

### Post by ulao3 on 2021-11-27
yeah my linux server is my router with two nics...

I use iptable and have routs for my vnc like so.
```


iptables -t nat -A PREROUTING -i enp0s2 -p tcp --dport 5925 -j DNAT --to-destination 192.168.0.25:5900


```

and I used to do my blocking in there but moved to ufw, I have a few choice blocking going on. 

```

To                         Action      From
--                         ------      ----
443/tcp                    ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
21/tcp                     ALLOW       Anywhere
Samba                      ALLOW       Anywhere
Apache                     ALLOW       Anywhere
Apache Full                ALLOW       Anywhere
5919                       ALLOW       Anywhere
5901                       DENY        Anywhere
5904                       DENY        Anywhere
5902                       DENY        Anywhere
5903                       DENY        Anywhere
5905                       DENY        Anywhere
5906                       DENY        Anywhere
5907                       DENY        Anywhere
5910:5931/tcp              ALLOW       Anywhere
443/tcp (v6)               ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
21/tcp (v6)                ALLOW       Anywhere (v6)
Apache (v6)                ALLOW       Anywhere (v6)
Apache Full (v6)           ALLOW       Anywhere (v6)
Samba (v6)                 ALLOW       Anywhere (v6)
5919 (v6)                  ALLOW       Anywhere (v6)
5901 (v6)                  DENY        Anywhere (v6)
5904 (v6)                  DENY        Anywhere (v6)
5902 (v6)                  DENY        Anywhere (v6)
5903 (v6)                  DENY        Anywhere (v6)
5905 (v6)                  DENY        Anywhere (v6)
5906 (v6)                  DENY        Anywhere (v6)
5907 (v6)                  DENY        Anywhere (v6)
5910:5931/tcp (v6)         ALLOW       Anywhere (v6)

53,113,123/udp             ALLOW OUT   Anywhere
53,113,123/udp (v6)        ALLOW OUT   Anywhere (v6)

```


> O.K. so you have identified 192.168.0.111 as the source in the  first example You mean the source of the mail issue?

---

### Post by Doug S on 2021-11-27
> **ulao3 said:**
>  You mean the source of the mail issue?I have no way of knowing. I'll rephrase: It is email traffic involving 192.168.0.111. You will have to determine is it legitimate email or bad guy 
stuff.

---

### Post by ulao3 on 2021-11-28
ahh, then maybe I need to close email clients, and or do not do email activity for x hours, and run this again.

is there a way to use the commands above filter 192.168.0.31 and port 993 ?
and woudl there be a way to echo these details to the screen so I can see it live?

UPDATE using this** tcpdump -n -tttt  -i enp3s5 port 993**


seem to do what I need to investigate with this pc

---

### Post by Doug S on 2021-11-28
> **ulao3 said:**
> is there a way to use the commands above filter 192.168.0.31 and port 993 ?
and woudl there be a way to echo these details to the screen so I can see it live?

UPDATE using this** tcpdump -n -tttt  -i enp3s5 port 993**Yes, exactly. Once things get narrowed down and we have some idea what we are looking for, then yes the next step is exactly what you have done.

EDIT: You could also run multiple tcpdump sessions, one per terminal, watching other ports at the same time:
```
 tcpdump -n -tttt  -i enp3s5 port 465
```

you could also re-process the previously captured data with increased focus:```
$ for f in int*.bin; do tcpdump -n -tttt -r $f port 993 >>port993.txt; done
```

---

### Post by SeijiSensei on 2021-11-29
> **ulao3 said:**
> and I used to do my blocking in there but moved to ufw, I have a few choice blocking going on.
There are no rules in the list you presented that block outbound traffic to TCP ports 25, 465, and 587.

---

### Post by ulao3 on 2021-11-29
Doug, thx for all the help, its 
[https://en.wikipedia.org/wiki/Trojan:Win32/Agent](https://en.wikipedia.org/wiki/Trojan:Win32/Agent)
and  its all over the place... A rely nasty one to remove. KS is able to  find it but it likes to come back. I think I got it from here, this all  really helped allot thx!

---

### Post by Doug S on 2021-11-29
> **ulao3 said:**
> Doug, thx for all the help, its 
[https://en.wikipedia.org/wiki/Trojan:Win32/Agent](https://en.wikipedia.org/wiki/Trojan:Win32/Agent)
and  its all over the place... A rely nasty one to remove. KS is able to  find it but it likes to come back. I think I got it from here, this all  really helped allot thx!Thanks for reporting back.

When you say you "got it from here" what do you mean? Do you mean from these forums? If yes, I don't think so.
Also, what is "KS"?

---

### Post by ulao3 on 2021-11-30
nono, As in I got it from here on out... Spent the day over this one, some clever whatnot's, to remove it.

 KS - KasperSky.

---

### Post by ulao3 on 2021-12-02
just one small other thing I see here,
```

2021-12-02 15:09:43.879437 IP 192.168.0.25.53630 > 192.168.0.19.22: Flags [.], ack 346472688, win 63104, length 0
2021-12-02 15:09:43.879452 IP 192.168.0.19.22 > 192.168.0.25.53630: Flags [P.], seq 346472880:346473072, ack 512001, win 65535, length 192
2021-12-02 15:09:43.879495 IP 192.168.0.19.22 > 192.168.0.25.53630: Flags [P.], seq 346473072:346473248, ack 512001, win 65535, length 176
2021-12-02 15:09:43.879524 IP 192.168.0.19.22 > 192.168.0.25.53630: Flags [P.], seq 346473248:346473440, ack 512001, win 65535, length 192
2021-12-02 15:09:43.879580 IP 192.168.0.19.22 > 192.168.0.25.53630: Flags [P.], seq 346473440:346473824, ack 512001, win 65535, length 384
2021-12-02 15:09:43.879641 IP 192.168.0.19.22 > 192.168.0.25.53630: Flags [P.], seq 346473824:346474016, ack 512001, win 65535, length 192
2021-12-02 15:09:43.879691 IP 192.168.0.19.22 > 192.168.0.25.53630: Flags [P.], seq 346474016:346474208, ack 512001, win 65535, length 192
2021-12-02 15:09:43.879741 IP 192.168.0.19.22 > 192.168.0.25.53630: Flags [P.], seq 346474208:346474400, ack 512001, win 65535, length 192


```

What could this be, its spamming really fast. I have no idea what 192.168.19.22 is but I see its a private IP. it does not reply to a ping or nslookup. 

update: oh I think its my ssh connection. as a result of running tcpdump -n -tttt  -i enp3s5


[COLOR=#D8D8D8][/COLOR]

---

### Post by Doug S on 2021-12-02
> **ulao3 said:**
> What could this be, its spamming really fast. I have no idea what 192.168[COLOR="#FF0000"].0[/COLOR].19.22 is but I see its a private IP. it does not reply to a ping or nslookup. 
You don't know what 192.168.0.19 is? I can not help with that, because as you say it is on your LAN. The port involved is SSH, port 22.

Just a guess below:
Might you just so happen to have an SSH session open between 192.168.0.25 (client) and 192.168.0.19 (server)? And are you running tcpdump via a terminal on 192.168.0.25? If yes, then you are flooding yourself as tcpdump captures the traffic and then sends it to the client, creating an infinite loop.
I always communicate with my servers via ssh, and have to make sure to avoid this situation via a "not host". Example:

```
doug@s19:~/temp-k-git/linux$ sudo tcpdump -n -tttt -i br0 not host 192.168.111.122
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on br0, link-type EN10MB (Ethernet), capture size 262144 bytes
2021-12-02 07:33:18.529276 ARP, Request who-has 192.168.111.4 (ff:ff:ff:ff:ff:ff) tell 192.168.111.58, length 46
2021-12-02 07:33:19.705503 ARP, Request who-has 192.168.111.136 (ff:ff:ff:ff:ff:ff) tell 192.168.111.58, length 46
2021-12-02 07:33:19.705555 ARP, Reply 192.168.111.136 is-at 3c:7c:3f:0d:99:83, length 28
^C
3 packets captured
3 packets received by filter
0 packets dropped by kernel
```

otherwise (very fast):

```
2021-12-02 07:34:17.745493 IP 192.168.111.122.53781 > 192.168.111.136.22: Flags [.], ack 1378048, win 8209, length 0
2021-12-02 07:34:17.745525 IP 192.168.111.136.22 > 192.168.111.122.53781: Flags [P.], seq 1378220:1378548, ack 757, win 501, length 328
2021-12-02 07:34:17.745573 IP 192.168.111.136.22 > 192.168.111.122.53781: Flags [P.], seq 1378548:1378720, ack 757, win 501, length 172
2021-12-02 07:34:17.745621 IP 192.168.111.136.22 > 192.168.111.122.53781: Flags [P.], seq 1378720:1378892, ack 757, win 501, length 172
2021-12-02 07:34:17.745719 IP 192.168.111.136.22 > 192.168.111.122.53781: Flags [P.], seq 1378892:1379064, ack 757, win 501, length 172
2021-12-02 07:34:17.745731 IP 192.168.111.122.53781 > 192.168.111.136.22: Flags [P.], seq 757:793, ack 1378048, win 8209, length 36
2021-12-02 07:34:17.745731 IP 192.168.111.122.53781 > 192.168.111.136.22: Flags [.], ack 1378720, win 8212, length 0
^C
8335 packets captured
8337 packets received by filter
0 packets dropped by kernel
```

EDIT: or:```
$ sudo tcpdump -n -tttt -i br0 not port 22
```

---

### Post by ulao3 on 2021-12-02
> You don't know what 192.168.0.19 is?  Of course I know what that is. 

I said 

> I have no idea what 192.168.19.22 is

> Might you just so happen to have an SSH session open between 192.168.0.25 (client) and 192.168.0.19 (server)?
did you miss my update :) ?

> update: oh I think its my ssh connection. as a result of running tcpdump -n -tttt  -i enp3s5

---

### Post by Doug S on 2021-12-02
> **ulao3 said:**
> Of course I know what that is. 

I said 




did you miss my update :) ?Yes, I guess I was already writting my reply when you updated.

I had assumed 192.168.19.22 was a typo and you had meant to write 192.168.0.19.

---

