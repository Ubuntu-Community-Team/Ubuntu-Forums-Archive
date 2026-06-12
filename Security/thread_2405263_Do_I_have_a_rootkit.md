---
title: "Do I have a rootkit?"
date: 2018-11-03
forum: Security
---

### Post by feliixx on 2018-11-03
Hi,

I found out some unexpected connections on my desktop ubuntu. I have some https connections every hour at 30 minutes to this IP : 145.14.145.231. This happens without my browser being running. 
I was playing Mame with etherape running in the background when these strange connections came up, even though I was not browsing the Internet. From time to time I have some connections to cannonical for instance, which are normal, but I can't figure out what those are.

I was wondering if I could have been infected with a rootkit or something. I only use programs from the ubuntu repositories and even if I shut down Mame, these connections are still occurring every hour at 30 minutes.

Any info? Thanks in advance!

---

### Post by TheFu on 2018-11-03
Doubtful.

Time servers? What port and protocol(s)?  netstat or lsof can help determine those.

But if you have any concerns, wipe the system and reload from fresh and be careful in the programs you load and run.

---

### Post by feliixx on 2018-11-03
Thank you for your reply. Do you have any command lines to run netstat or lsof? 
I read an older topc advising to try lynis, which I did but it gave me nothing really wrong.

I assume I have to run them at 30 minutes?

---

### Post by TheFu on 2018-11-03
> **feliixx said:**
> Thank you for your reply. Do you have any command lines to run netstat or lsof? 
I read an older topc advising to try lynis, which I did but it gave me nothing really wrong.

I assume I have to run them at 30 minutes?

I'd have to google or read the manpage for the specific options. You can do that just as easily. "*find port netstat*" would be my search term.  You can also use **grep** to look only for the specific IP you are concerned about in the output.  I'd redirect all of the output into a file around the time I expected it.  Something like this:
$ netstat {options, whatever they are} | grep {that IP address} | tee  /tmp/outputfile

But this is just one method. There are 50+ others.  Whatever works is what you should use.  The **lsof** would work similarly, but I'd restrict it to just IPv4 "files" because my network doesn't support IPv6 and I specifically disable all IPv6 across all my systems.

It is probably just trying to keep the clock correct using NTP. The only way to be certain is to check the protocol used.

---

### Post by feliixx on 2018-11-03
Thanks, I will try all this.

Etherape reported me that there were HTTPS connections.

---

### Post by TheFu on 2018-11-03
Any issues if you visit the same IP/domain with a browser?  

Some programs will check for updates incessantly. Don't forget that if you use RSS, feed updates will happen based on those settings.

I'd disable javascript before doing that, but I disable JS by default and only enable it for trusted sites that DEMAND it.  I've stopped visiting some media sites because they started requiring JS for functionality.  Nothing is more important than being able to trust my system.

And as a last effort, you could just block outbound to it with a system firewall setting.

---

### Post by feliixx on 2018-11-07
If I visit the same domains with my browser (found on whois and google), it doesn't behave the same way (I mean the same connection every 30' from my browser), even though the connections remain  identical otherwise.

However I used nethogs to record these connections and got this:

```

NetHogs version 0.8.1

    PID USER     PROGRAM                                                              DEV        SENT      RECEIVED       
  31812 user     wget                                                                 wls2       0.291       0.984 KB/sec
  31809 user     wget                                                                 wls2       0.292       0.984 KB/sec
  31801 user     wget                                                                 wls2       0.275       0.926 KB/sec
  31798 user     wget                                                                 wls2       0.261       0.868 KB/sec
  13015 user     /usr/lib/firefox/firefox                                             wls2       0.000       0.000 KB/sec
      ? root     unknown TCP                                                                     0.000       0.000 KB/sec

  TOTAL                                                                                          1.119       3.761 KB/sec 
```

And here is my sudo netstat :

```

Connexions Internet actives (serveurs et établies)
Proto Recv-Q Send-Q Adresse locale          Adresse distante        Etat       User       Inode       PID/Program name
tcp        0      0 127.0.2.1:domain        *:*                     LISTEN      root       35581       1/init          
tcp        0      0 laptop:domain           *:*                     LISTEN      root       28278       1833/dnsmasq    
tcp        0      0 localhost:ipp           *:*                     LISTEN      root       40109       5639/cupsd      
tcp        0      0 192.168.43.162:38306    coptere.infra.ubu:https ESTABLISHED user       642223      1884/firefox    
tcp        0      0 192.168.43.162:38308    coptere.infra.ubu:https TIME_WAIT   root       0           -               
udp        0      0 *:mdns                  *:*                                 avahi      21305       1018/avahi-daemon: 
udp        0      0 127.0.2.1:domain        *:*                                 root       35582       1/init          
udp        0      0 laptop:domain           *:*                                 root       28277       1833/dnsmasq    
udp        0      0 *:bootpc                *:*                                 root       593389      458/dhclient    
udp        0      0 *:59559                 *:*                                 _dnscrypt-proxy 38935       4794/dnscrypt-proxy
udp        0      0 *:53544                 *:*                                 nobody     590800      1833/dnsmasq    
udp        0      0 *:45356                 *:*                                 avahi      21307       1018/avahi-daemon:  
udp        0      0 *:ipp                   *:*                                 root       37783       5641/cups-browsed
udp6       0      0 [::]:mdns               [::]:*                              avahi      21306       1018/avahi-daemon: 
udp6       0      0 [::]:52872              [::]:*                              avahi      21308       1018/avahi-daemon: 
```

And this loop, using lsof:

```
user@laptop:~$ while true; do VAR=$(lsof -i | sed '1d'); echo "$VAR" | grep -v "$VAR1" >> log; VAR1=$VAR; sleep 1; done
```

gave me this:

```
firefox 1884 user   96u  IPv4 1008169      0t0  TCP 192.168.43.162:39054->marula.canonical.com:https (ESTABLISHED)
firefox  1884 user   96u  IPv4 1008169      0t0  TCP 192.168.43.162:39054->marula.canonical.com:https (ESTABLISHED)
wget    20386 user    3u  IPv4 1011824      0t0  TCP 192.168.43.162:42686->145.14.144.41:https (SYN_SENT)
firefox 1884 user   96u  IPv4 1008169      0t0  TCP 192.168.43.162:39054->marula.canonical.com:https (ESTABLISHED)
firefox  1884 user   96u  IPv4 1008169      0t0  TCP 192.168.43.162:39054->marula.canonical.com:https (ESTABLISHED)
wget    20412 user    3u  IPv4 1009659      0t0  TCP 192.168.43.162:42692->145.14.144.41:https (ESTABLISHED)
firefox 1884 user   96u  IPv4 1008169      0t0  TCP 192.168.43.162:39054->marula.canonical.com:https (ESTABLISHED)
```

And finally, rkhunter and chkrootkit gave me nothing but false positives. After having checked every warning, there is nothing to worry from these 2 programs. However, the connections remain...

---

### Post by TheFu on 2018-11-08
What are the arguments to wget? The process table has those.  You can even find the entire environment based on the PID, if you need. It is in /proc/{PID}/

**ps -eaf|grep wget**

---

### Post by feliixx on 2018-11-08
Thank you for your help. Here is what gives me "**ps -eaf | grep wget" inside a loop:**

```
user     13042 13053  0 23:30 ?        00:00:00 wget -S --spider https://blogbird.000webhostapp.com/forwarder
user     13054 13053  0 23:30 ?        00:00:00 wget -S --spider https://blogbird.000webhostapp.com
user     13063 11565  2 23:30 ?        00:00:00 wget -O - https://blogbird.000webhostapp.com
```

Edit: one line was missing

---

### Post by TheFu on 2018-11-08
If you aren't using blogbird, then your machine is being used to increase their clicks.  Check the wget manpage.  If you don't use wget, move the binary for a few days, see what happens.

Not a rootkit, just a simple hack.   If you have versioned backups, go through those to see when the compromise happened and which new files were added to your box under what userid. 

For example, I can't tell if "user" is the real values above or if you are hiding some username. Find all the processes running under that userid and figure out where they are getting started.  ptree might be helpful.

 When you are ready to move on, wipe the system, reinstall fresh, using more secure methods this time around.  The OS on this machine can not be trusted anymore.

---

### Post by feliixx on 2018-11-09
Thank you. Yes "user@latop" are my real ids. I wanted something neutral.

OK, I will process these further checks and see what happens. I understand the best would be to wipe the system.It's probably time to move to Ubuntu 18.04 as I was still on the 16.04.

---

### Post by TheFu on 2018-11-09
I'm on 16.04.  18.04 just isn't ready for my needs yet.  Support for 16.04 has 3 more years. No hurry.

I'm not gonna try to figure out that command. Sorry.

Did you check the different crontab locations?  There are 6+ places that a task can be started by cron or anacron.

---

### Post by feliixx on 2018-11-09
Thanks. Anyway I'm going to reinstall everything. Unfortunately, I'm on Kubuntu, so it is only supported for 3 years. I will check these contrabs but I'd like to try first something on ufw before wiping the system.

Do you have any rule to suggest to add to ufw? 

It is probably my last message here so thanks for your help!

---

### Post by cam17 on 2018-11-21
I have noticed that my /tmp directory has the following files, note the highlight red. This file occurs after a reboot.
[COLOR=#000000][FONT=-webkit-standard]
-rw------- 1 mac mac 0 Nov 21 06:53 config-err-W58x71[/FONT][/COLOR][COLOR=#000000][FONT=-webkit-standard]drwx------ 2 mac mac 4096 Nov 21 06:53 ssh-YMOUArFgSVPF[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]drwx------ 3 root root 4096 Nov 21 06:52 systemd-private-d2c674aa69a948ec8a8a3d39aaeca4bf-bolt.service-YjdSfv[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]drwx------ 3 root root 4096 Nov 21 06:52 systemd-private-d2c674aa69a948ec8a8a3d39aaeca4bf-colord.service-aXkyZU[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]drwx------ 3 root root 4096 Nov 21 06:52 systemd-private-d2c674aa69a948ec8a8a3d39aaeca4bf-[COLOR=#ff0000]**rtkit-daemon.service**[/COLOR]-eoSBC4[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]drwx------ 3 root root 4096 Nov 21 06:53 systemd-private-d2c674aa69a948ec8a8a3d39aaeca4bf-systemd-hostnamed.service-4as32V[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]drwx------ 3 root root 4096 Nov 21 06:53 systemd-private-d2c674aa69a948ec8a8a3d39aaeca4bf-systemd-localed.service-03Rqrv[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]drwx------ 3 root root 4096 Nov 21 06:52 systemd-private-d2c674aa69a948ec8a8a3d39aaeca4bf-systemd-resolved.service-2UKwWN[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]drwx------ 3 root root 4096 Nov 21 06:52 systemd-private-d2c674aa69a948ec8a8a3d39aaeca4bf-systemd-timesyncd.service-4SLui4[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]drwx------ 2 mac mac 4096 Nov 21 06:54 Temp-4d891332-0501-4a43-bf11-9c68a50bfae1[/FONT][/COLOR]

---

### Post by howefield on 2018-11-21
> ....rtkit-daemon.service...

[https://www.mankier.com/package/rtkit](https://www.mankier.com/package/rtkit)
[https://www.mankier.com/8/rtkitctl](https://www.mankier.com/8/rtkitctl)

---

### Post by jay-marm on 2018-11-21
A quick check on that address via virus total: [https://www.virustotal.com/#/ip-address/145.14.145.231](https://www.virustotal.com/#/ip-address/145.14.145.231) Lots of hits detected.

---

