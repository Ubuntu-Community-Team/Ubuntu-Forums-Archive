---
title: "[SOLVED] Adding block lists to IPBlock stops internet"
date: 2008-08-09
forum: Security
---

### Post by rbjscv on 2008-08-09
Hi all,  I'm still just a 2 month old Ubunty.

Using IpBlock along with kTorrent 3.1.1.  The problem is that if I add another one of IpBlocks's lists to IpBlock it knocks my internet off every time.  As long as I leave the defaults running everything is fine.  I've been trying to figure this out for a few weeks now but its beyond my elementary abilities.

OH yes I also have it set for autostart, but it never does.  And also, it only seems to be blocking schools, yet it is supposed to be blocking ads, bogon, level 1,spyware, and edu.  I just have never seen that happening.  OK and sometimes it just simply doesn't work at all.  I've removed removing the program and all the lists and still Nada.


 Not to make a comparison but I will. Peer guardian was always busting away blocking all sorts of bad guys.  IPBlock seems laid back in comparision.

Any help/insights?  I'm also running firestarter, but that doesn't seem to be causing any problems.

Confused @ 2 months

Oh, yeah, running Hardy

And now I realized this is probably in the wrong forums.  Most sincere apologies

---

### Post by uljanow on 2008-08-10
Which additional list are you trying to use ? I'd check the logs whether there are entries of your ISP or DNS-Servers.

You can check if IPs are blocked with the following (replace level1.gz with the lists you use):
```
ping $(zcat /var/cache/iplist/level1.gz | grep -o -E "([0-9.]+){4}" | head -n1)
```


How does firestarter start ? IPblock needs to be started after other apps that change iptables-rules. 

And the output of 
```
sudo egrep "iplist|ipblock" /var/log/syslog*
``` would be useful, too.

---

### Post by rbjscv on 2008-08-10
Firstly, thank you.  Secondly, I'm not trying to add my own lists - that is beyond me.  I just wanted to add some of the programs other lists to the default ones.  So here comes the answers.


Ping command yielded this:

PING 3.0.0.0 (3.0.0.0) 56(84) bytes of data.


--- 3.0.0.0 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5008ms


Firestarter always starts in the background.  I rarely open it up unless I want to look at traffic while downloading.


2nd output below:

/var/log/syslog.0:Aug  9 19:46:57 radium iplist[6869]: error: iplist is already running. Try --insert (-i) option. 
/var/log/syslog.0:Aug  9 19:47:20 radium iplist[6877]: error: can't find stop 
/var/log/syslog.0:Aug  9 19:49:06 radium ipblock[6984]: error: can't access /var/cache/iplist
/var/log/syslog.0:Aug  9 19:49:13 radium iplist[7009]: error: can't find ads-trackers-and-bad-pr0n.gz 
/var/log/syslog.0:Aug  9 19:49:13 radium ipblock[6989]: error: failed to start, cleaning up
/var/log/syslog.0:Aug  9 19:49:33 radium iplist[7034]: error: can't find ads-trackers-and-bad-pr0n.gz 
/var/log/syslog.0:Aug  9 19:49:33 radium ipblock[7023]: error: failed to start, cleaning up
/var/log/syslog.0:Aug  9 19:49:37 radium ipblock[7044]: error: can't access /var/cache/iplist
/var/log/syslog.0:Aug  9 19:49:45 radium ipblock[7053]: error: can't access /var/cache/iplist
/var/log/syslog.0:Aug  9 19:49:48 radium iplist[7070]: error: can't find ads-trackers-and-bad-pr0n.gz 
/var/log/syslog.0:Aug  9 19:49:48 radium ipblock[7059]: error: failed to start, cleaning up
/var/log/syslog.0:Aug  9 19:50:07 radium ipblock[7088]: error: can't access /var/cache/iplist
/var/log/syslog.0:Aug  9 19:50:13 radium iplist[7105]: error: can't find ads-trackers-and-bad-pr0n.gz 
/var/log/syslog.0:Aug  9 19:50:13 radium ipblock[7094]: error: failed to start, cleaning up


Finally does one put their output text in a separate scroll down box within the msg?

---

### Post by rbjscv on 2008-08-10
Alright now, after I posted the requested output I got to thinking.  You jogged my memory (what's left of it) when you asked about firestarter.  I realized that what was happening was that IpBlock was cranking up before firestarter.  Changed line in usr/sbin/ipblock to 'sleep 2'.  line 133 to be exact.

So now everything starts in background as desired.

Now onward to:  Why doesn't kTorrent forward ports correctly.  Port on firewall is forwarded.  Port in Firestarter can be open or closed seems to make no dif.

---

### Post by rbjscv on 2008-08-10
Well I posted too soon.  I can start IpBlock manually after Firestarter is going, but I only have output blocked and no blocked input.

IpBlock is now @ sleep 2 but it still doesn't always autostart.  So I'm as confused as can be.

---

### Post by uljanow on 2008-08-12
If you add a list (URL) an update is required to download that list.

The directory **/var/cache/iplist** can't be accessed. Is /var read-only or mounted as tmpfs ?

To fix the problem with firestarter, I'd start firestarter at runlevel (during boot) compared to gdm sessions. This conflict is probably the reason why the internet doesn't work.

---

