---
title: "Has my machine been compromised?"
date: 2005-04-27
forum: Server Platforms
---

### Post by theplatypus on 2005-04-27
I woke up this morning to a couple of widgets on my desktop.

#1  "Warning Could not grab your mouse. A malicious client may be eavesdropping on your session."

#2 " Changing user Please enter your password to run /usr/sbin/firestarter"

Firestarter was running when I went to sleep.

---

### Post by nocturn on 2005-04-27
[QUOTE=theplatypus]I woke up this morning to a couple of widgets on my desktop.

#1  "Warning Could not grab your mouse. A malicious client may be eavesdropping on your session."

#2 " Changing user Please enter your password to run /usr/sbin/firestarter"

Firestarter was running when I went to sleep.[/QUOTE]

You will need to check the rest of your logs, /var/log/messages is the most obvious one to start on.

Additionally, download and run rkhunter to check for rootkits or changes.

---

### Post by theplatypus on 2005-04-27
/var/og/messages


```
Apr 24 06:47:03 localhost syslogd 1.4.1#16ubuntu6: restart.
Apr 24 07:07:03 localhost -- MARK --
Apr 24 07:27:03 localhost -- MARK --
Apr 24 07:47:03 localhost -- MARK --
Apr 24 08:07:03 localhost -- MARK --
Apr 24 08:27:03 localhost -- MARK --
Apr 24 08:47:03 localhost -- MARK --
Apr 24 09:07:03 localhost -- MARK --
Apr 24 09:27:03 localhost -- MARK --
Apr 24 09:47:03 localhost -- MARK --
Apr 24 10:07:03 localhost -- MARK --
Apr 24 10:27:03 localhost -- MARK --
Apr 24 10:47:03 localhost -- MARK --
Apr 24 11:07:03 localhost -- MARK --
Apr 24 11:27:03 localhost -- MARK --
Apr 24 11:47:03 localhost -- MARK --
Apr 24 12:07:03 localhost -- MARK --
Apr 24 12:27:03 localhost -- MARK --
Apr 24 12:47:03 localhost -- MARK --
Apr 24 13:07:03 localhost -- MARK --
Apr 24 13:27:03 localhost -- MARK --
Apr 24 13:47:03 localhost -- MARK --
Apr 24 14:07:04 localhost -- MARK --
Apr 24 14:27:04 localhost -- MARK --
Apr 24 14:47:04 localhost -- MARK --
Apr 24 15:07:04 localhost -- MARK --
Apr 24 15:27:04 localhost -- MARK --
Apr 24 15:47:04 localhost -- MARK --
Apr 24 16:07:04 localhost -- MARK --
Apr 24 16:27:04 localhost -- MARK --
Apr 24 16:47:04 localhost -- MARK --
Apr 24 17:07:04 localhost -- MARK --
Apr 24 17:27:04 localhost -- MARK --
Apr 24 17:47:04 localhost -- MARK --
Apr 24 18:07:04 localhost -- MARK --
Apr 24 18:27:04 localhost -- MARK --
Apr 24 18:47:04 localhost -- MARK --
Apr 24 19:07:04 localhost -- MARK --
Apr 24 19:27:04 localhost -- MARK --
Apr 24 19:47:04 localhost -- MARK --
Apr 24 20:07:04 localhost -- MARK --
Apr 24 20:27:04 localhost -- MARK --
Apr 24 20:47:04 localhost -- MARK --
Apr 24 21:07:04 localhost -- MARK --
Apr 24 21:27:04 localhost -- MARK --
Apr 24 21:47:04 localhost -- MARK --
Apr 24 22:07:04 localhost -- MARK --
Apr 24 22:27:04 localhost -- MARK --
Apr 24 22:47:04 localhost -- MARK --
Apr 24 23:07:04 localhost -- MARK --
Apr 24 23:27:04 localhost -- MARK --
Apr 24 23:47:04 localhost -- MARK --
Apr 25 00:07:04 localhost -- MARK --
Apr 25 00:27:04 localhost -- MARK --
Apr 25 00:47:04 localhost -- MARK --
Apr 25 01:07:04 localhost -- MARK --
Apr 25 01:27:04 localhost -- MARK --
Apr 25 01:47:04 localhost -- MARK --
Apr 25 02:07:04 localhost -- MARK --
Apr 25 02:27:04 localhost -- MARK --
Apr 25 02:47:04 localhost -- MARK --
Apr 25 03:07:04 localhost -- MARK --
Apr 25 03:27:04 localhost -- MARK --
Apr 25 03:47:04 localhost -- MARK --
Apr 25 04:07:04 localhost -- MARK --
Apr 25 04:27:04 localhost -- MARK --
Apr 25 04:47:04 localhost -- MARK --
Apr 25 05:07:04 localhost -- MARK --
Apr 25 05:27:04 localhost -- MARK --
Apr 25 05:47:04 localhost -- MARK --
Apr 25 06:07:04 localhost -- MARK --
Apr 25 06:25:16 localhost exiting on signal 15
Apr 25 06:25:17 localhost syslogd 1.4.1#16ubuntu6: restart.
Apr 25 06:45:17 localhost -- MARK --
Apr 25 07:05:17 localhost -- MARK --
Apr 25 07:25:17 localhost -- MARK --
Apr 25 07:45:17 localhost -- MARK --
Apr 25 08:05:17 localhost -- MARK --
Apr 25 08:25:17 localhost -- MARK --
Apr 25 08:45:17 localhost -- MARK --
Apr 25 09:05:17 localhost -- MARK --
Apr 25 09:25:17 localhost -- MARK --
Apr 25 09:45:17 localhost -- MARK --
Apr 25 10:05:17 localhost -- MARK --
Apr 25 10:25:17 localhost -- MARK --
Apr 25 10:45:17 localhost -- MARK --
Apr 25 11:05:17 localhost -- MARK --
Apr 25 11:25:17 localhost -- MARK --
Apr 25 11:45:17 localhost -- MARK --
Apr 25 12:05:17 localhost -- MARK --
Apr 25 12:25:17 localhost -- MARK --
Apr 25 12:45:17 localhost -- MARK --
Apr 25 13:05:17 localhost -- MARK --
Apr 25 13:25:17 localhost -- MARK --
Apr 25 13:45:17 localhost -- MARK --
Apr 25 14:05:17 localhost -- MARK --
Apr 25 14:25:17 localhost -- MARK --
Apr 25 14:45:17 localhost -- MARK --
Apr 25 15:05:17 localhost -- MARK --
Apr 25 15:25:17 localhost -- MARK --
Apr 25 15:45:17 localhost -- MARK --
Apr 25 16:05:17 localhost -- MARK --
Apr 25 16:25:17 localhost -- MARK --
Apr 25 16:45:17 localhost -- MARK --
Apr 25 17:05:17 localhost -- MARK --
Apr 25 17:25:17 localhost -- MARK --
Apr 25 17:40:00 localhost kernel: Inbound IN=eth0 OUT= MAC=00:0c:6e:ae:5f:81:00:60:0f:9e:e9:ae:08:00 SRC=72.29.75.11 DST=192.168.1.96 LEN=44 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=40374 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Apr 25 17:40:45 localhost last message repeated 6 times
Apr 25 17:41:43 localhost last message repeated 5 times
Apr 25 18:05:17 localhost -- MARK --
Apr 25 18:25:17 localhost -- MARK --
Apr 25 18:45:17 localhost -- MARK --
Apr 25 19:05:17 localhost -- MARK --
Apr 25 19:25:17 localhost -- MARK --
Apr 25 19:30:22 localhost kernel: Inbound IN=eth0 OUT= MAC=00:0c:6e:ae:5f:81:00:60:0f:9e:e9:ae:08:00 SRC=72.25.72.102 DST=192.168.1.96 LEN=44 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=80 DPT=40982 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Apr 25 19:31:07 localhost last message repeated 7 times
Apr 25 19:31:56 localhost last message repeated 3 times
Apr 25 19:45:17 localhost -- MARK --
Apr 25 20:05:17 localhost -- MARK --
Apr 25 20:25:17 localhost -- MARK --
Apr 25 20:32:21 localhost kernel: Inbound IN=eth0 OUT= MAC=00:0c:6e:ae:5f:81:00:60:0f:9e:e9:ae:08:00 SRC=72.25.72.102 DST=192.168.1.96 LEN=44 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=80 DPT=41538 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Apr 25 20:33:06 localhost last message repeated 7 times
Apr 25 20:33:55 localhost last message repeated 2 times
Apr 25 20:45:17 localhost -- MARK --
Apr 25 21:05:17 localhost -- MARK --
Apr 25 21:25:17 localhost -- MARK --
Apr 25 21:45:17 localhost -- MARK --
Apr 25 22:05:17 localhost -- MARK --
Apr 25 22:25:17 localhost -- MARK --
Apr 25 22:25:24 localhost kernel: Inbound IN=eth0 OUT= MAC=00:0c:6e:ae:5f:81:00:60:0f:9e:e9:ae:08:00 SRC=72.25.72.102 DST=192.168.1.96 LEN=44 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=80 DPT=42041 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Apr 25 22:26:10 localhost last message repeated 5 times
Apr 25 22:26:15 localhost kernel: Inbound IN=eth0 OUT= MAC=00:0c:6e:ae:5f:81:00:60:0f:9e:e9:ae:08:00 SRC=72.25.72.102 DST=192.168.1.96 LEN=44 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=80 DPT=42052 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Apr 25 22:26:37 localhost last message repeated 3 times
Apr 25 22:26:58 localhost kernel: Inbound IN=eth0 OUT= MAC=00:0c:6e:ae:5f:81:00:60:0f:9e:e9:ae:08:00 SRC=72.25.72.102 DST=192.168.1.96 LEN=44 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=80 DPT=42041 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Apr 25 22:27:01 localhost kernel: Inbound IN=eth0 OUT= MAC=00:0c:6e:ae:5f:81:00:60:0f:9e:e9:ae:08:00 SRC=72.25.72.102 DST=192.168.1.96 LEN=44 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=80 DPT=42052 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Apr 25 22:27:49 localhost kernel: Inbound IN=eth0 OUT= MAC=00:0c:6e:ae:5f:81:00:60:0f:9e:e9:ae:08:00 SRC=72.25.72.102 DST=192.168.1.96 LEN=44 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=80 DPT=42052 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Apr 25 22:45:17 localhost -- MARK --
Apr 25 23:05:18 localhost -- MARK --
Apr 25 23:25:18 localhost -- MARK --
Apr 25 23:45:18 localhost -- MARK --
Apr 26 00:05:18 localhost -- MARK --
Apr 26 00:25:18 localhost -- MARK --
Apr 26 00:45:18 localhost -- MARK --
Apr 26 01:05:18 localhost -- MARK --
Apr 26 01:25:18 localhost -- MARK --
Apr 26 01:45:18 localhost -- MARK --
Apr 26 02:05:18 localhost -- MARK --
Apr 26 02:25:18 localhost -- MARK --
Apr 26 02:45:18 localhost -- MARK --
Apr 26 03:05:18 localhost -- MARK --
Apr 26 03:25:18 localhost -- MARK --
Apr 26 03:45:18 localhost -- MARK --
Apr 26 04:05:18 localhost -- MARK --
Apr 26 04:25:18 localhost -- MARK --
Apr 26 04:45:18 localhost -- MARK --
Apr 26 05:05:18 localhost -- MARK --
Apr 26 05:25:18 localhost -- MARK --
Apr 26 05:45:18 localhost -- MARK --
Apr 26 06:05:18 localhost -- MARK --
Apr 26 06:25:15 localhost exiting on signal 15
Apr 26 06:25:16 localhost syslogd 1.4.1#16ubuntu6: restart.
Apr 26 06:45:16 localhost -- MARK --
Apr 26 07:05:16 localhost -- MARK --
Apr 26 07:25:16 localhost -- MARK --
Apr 26 07:45:16 localhost -- MARK --
Apr 26 08:05:16 localhost -- MARK --
Apr 26 08:25:17 localhost -- MARK --
Apr 26 08:45:17 localhost -- MARK --
Apr 26 09:05:17 localhost -- MARK --
Apr 26 09:25:17 localhost -- MARK --
Apr 26 09:45:17 localhost -- MARK --
Apr 26 10:05:17 localhost -- MARK --
Apr 26 10:25:17 localhost -- MARK --
Apr 26 10:45:17 localhost -- MARK --
Apr 26 11:05:17 localhost -- MARK --
Apr 26 11:25:17 localhost -- MARK --
Apr 26 11:45:17 localhost -- MARK --
Apr 26 12:05:17 localhost -- MARK --
Apr 26 12:25:17 localhost -- MARK --
Apr 26 12:45:17 localhost -- MARK --
Apr 26 13:05:17 localhost -- MARK --
Apr 26 13:25:17 localhost -- MARK --
Apr 26 13:45:17 localhost -- MARK --
Apr 26 14:05:17 localhost -- MARK --
Apr 26 14:25:17 localhost -- MARK --
Apr 26 14:45:17 localhost -- MARK --
Apr 26 15:05:17 localhost -- MARK --
Apr 26 15:25:17 localhost -- MARK --
Apr 26 15:45:17 localhost -- MARK --
Apr 26 16:05:17 localhost -- MARK --
Apr 26 16:25:17 localhost -- MARK --
Apr 26 16:45:17 localhost -- MARK --
Apr 26 17:05:17 localhost -- MARK --
Apr 26 17:25:17 localhost -- MARK --
Apr 26 17:45:17 localhost -- MARK --
Apr 26 18:05:17 localhost -- MARK --
Apr 26 18:25:17 localhost -- MARK --
Apr 26 18:45:17 localhost -- MARK --
Apr 26 19:05:17 localhost -- MARK --
Apr 26 19:25:17 localhost -- MARK --
Apr 26 19:45:17 localhost -- MARK --
Apr 26 20:05:17 localhost -- MARK --
Apr 26 20:25:17 localhost -- MARK --
Apr 26 20:45:17 localhost -- MARK --
Apr 26 21:05:17 localhost -- MARK --
Apr 26 21:25:17 localhost -- MARK --
Apr 26 21:45:17 localhost -- MARK --
Apr 26 22:05:17 localhost -- MARK --
Apr 26 22:25:17 localhost -- MARK --
Apr 26 22:45:17 localhost -- MARK --
Apr 26 23:05:17 localhost -- MARK --
Apr 26 23:25:17 localhost -- MARK --
Apr 26 23:45:17 localhost -- MARK --
Apr 27 00:05:17 localhost -- MARK --
Apr 27 00:25:17 localhost -- MARK --
Apr 27 00:45:17 localhost -- MARK --
Apr 27 01:05:17 localhost -- MARK --
Apr 27 01:25:18 localhost -- MARK --
Apr 27 01:45:18 localhost -- MARK --
Apr 27 02:05:18 localhost -- MARK --
Apr 27 02:25:18 localhost -- MARK --
Apr 27 02:45:18 localhost -- MARK --
Apr 27 03:05:18 localhost -- MARK --
Apr 27 03:25:18 localhost -- MARK --
Apr 27 03:45:18 localhost -- MARK --
Apr 27 04:05:18 localhost -- MARK --
Apr 27 04:25:18 localhost -- MARK --
Apr 27 04:45:18 localhost -- MARK --
Apr 27 05:05:18 localhost -- MARK --
Apr 27 05:25:18 localhost -- MARK --
Apr 27 05:45:18 localhost -- MARK --
Apr 27 06:05:18 localhost -- MARK --
Apr 27 06:25:14 localhost exiting on signal 15
Apr 27 06:25:15 localhost syslogd 1.4.1#16ubuntu6: restart.
Apr 27 06:45:15 localhost -- MARK --
Apr 27 07:05:15 localhost -- MARK --
Apr 27 07:25:15 localhost -- MARK --
Apr 27 07:45:15 localhost -- MARK --
Apr 27 08:05:15 localhost -- MARK --
```

---

### Post by theplatypus on 2005-04-27
I ran chkrootkit, the only thing that looks off to me is

```
eth0: PACKET SNIFFER(/sbin/dhclient3[5967])
```

---

### Post by nocturn on 2005-04-27
[QUOTE=theplatypus]I ran chkrootkit, the only thing that looks off to me is

```
eth0: PACKET SNIFFER(/sbin/dhclient3[5967])
```[/QUOTE]

Hmm, when did it output this? (can you post the lines before and after)?
Are you using dhcp to get an IP address?

Do what package does the file /sbin/dhclient3 belong (use dpkg to get that info).

Try rkhunter anyway, it is better then chkrootkit, and in any case the combination of both is the safest.

BTW, does ifconfig report any interface in promiscueus mode?

---

### Post by nocturn on 2005-04-27
Some additional questions:
How is your system connected to the internet?  (direct, local firewall, hardware firewall?)

Did you open any services for external access?
Do you have SSH (server) installed?

---

### Post by theplatypus on 2005-04-28
Thanks for the help Nocturne. Rkhunter found some suspicious files. At one point this morning mp3's started playing on their own. So I'm going to do a fresh install and change all of my passwords. It may be drastic. But I'll sleep better.

---

### Post by nocturn on 2005-04-28
[QUOTE=theplatypus]Thanks for the help Nocturne. Rkhunter found some suspicious files. At one point this morning mp3's started playing on their own. So I'm going to do a fresh install and change all of my passwords. It may be drastic. But I'll sleep better.[/QUOTE]

Don't do that just yet.  Unless you know how they got in, it may happen again.
You can take an image of your partitions using dd from the livecd, it is identical to your real HD (you can even mount it).

If you have been compromised, a complete reinstall and rotating passwords is a very good procedure.
If you are connected to the net directly, consider installing firestarter, or buying a cheap hardware firewall (30-100 €).

Good luck.

---

### Post by theplatypus on 2005-04-28
I'm still not positive that anyone compromised the machine. But, I've been meaning to ugrade my windows drive anyway (2000-> xp pro). So I'll just install and tweak 2 os's. After an offline istallation I'll hook up my router and all should be fine. 

  I removed my router a few weeks ago so my isp could run some line tests. They assured me that the provided dsl modem  had a built in firewall. I had a friend run some port scans and everything seemed cool. But, I installed Firestarter as well just to be safe. A few days later I got the messages from my first post. I'm probably fine. But, I would rather be safe than sorry.

---

### Post by LordHunter317 on 2005-05-05
[QUOTE=theplatypus]I'm still not positive that anyone compromised the machine. But, I've been meaning to ugrade my windows drive anyway (2000-> xp pro). So I'll just install and tweak 2 os's. After an offline istallation I'll hook up my router and all should be fine. 

  I removed my router a few weeks ago so my isp could run some line tests. They assured me that the provided dsl modem  had a built in firewall. I had a friend run some port scans and everything seemed cool. But, I installed Firestarter as well just to be safe. A few days later I got the messages from my first post. I'm probably fine. But, I would rather be safe than sorry.[/QUOTE]
 If you ran rkhunter locally, you didn't learn a damn thing.

You must run it off an uncompromised source, meaning a rescue CD downloaded from an untainted machine.

---

