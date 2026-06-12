---
title: "DNS Bind9 with pbx server, and samba woes"
date: 2011-12-08
forum: Server Platforms
---

### Post by richrock on 2011-12-08
Hi all,

I was in the process of changing our Windows SBS2003 server to Ubuntu, we'd bought a new hdd and was able to access all our old data from the RAID setup (1, I think) to copy over.  All well and good, but I have two problems.

1.  Windows 7 and Samba shares.  This may be related to the DNS issue below, but I could not get Win 7 Home, or Win 7 Pro to see the Samba shares.  My laptop with Win 7 Enterprise did, although with some difficulty.  Is this fixable?  Point 2 may have a solution, possibly.

2.  I booted our server, everything running smoothly (we don't need exchange anymore, just a fileserver - or so I thought) - until my boss comes up and says 'the phones aren't working'.  A panicked rebuild using the original drives showed me that the DNS settings in SBS were pointing to the phone system too.  We're using Asterisk, and the guy who set it all up has moved on since. :(

So...

I figured I need to install Bind9, something I'll do tonight when everyone's gone and we don't need the phones/server.

But:

Can I simply put the Forward Lookup and Reverse Lookups into the same conf file, even if the IP range is different?

IE:  Our server 'serves' on 192.168.168.xxx - that was working fine.  The phones are served on 192.168.167.xxx - and these weren't working.  I read this for Bind8 - [http://www.troubleshooters.com/linux/dns.htm](http://www.troubleshooters.com/linux/dns.htm) which seemed to make me think it could.  I'm not a DNS/Network Guru, but I can figure and understand a lot of the principles.  Which stops my boss employing a proper sysadmin, I guess  :rolleyes:

Any helpful pointers would be well appreciated and stop this poor developer slipping back into alcoholism (again).

---

### Post by jonobr on 2011-12-08
Hey there


On the voip side, if you want to run a trace on the server to see if the phones are tyrong to register I can help on that.

If you do a trace assuming your doing standard voip.


in a terminal type

```
sudo tcpdump -w trace.pcap -i any -s 1600 port 5060 
```
Run the trace for a few minutes , then control c and send to me.

You can send the trace.pcap to me and ill look,


It may be worth it to run a trace of a test call,


Run the trace again, give it a different name
```
sudo tcpdump -w call1.pcap -i any -s 1600 port 5060 
```
 place the call,
send me the results, I canm look at them for you.


If you dont want to post on the forums, just send to me in a provate message.

On the zone files for bind 9, your just mapping a name to an Ip, so it should matter, unless I'm misreading your question.

On the alchaholism, I cant help too much, but just think of how marketable you are becoming.....

---

### Post by richrock on 2011-12-08
Odd, running the tcpdump (even as root) gives permission denied.  I'm just trying to figure out how to point 192.168.168.2 ip address to the server (ie, itself) and 192.168.167.xxx to an Asterisk server.  Like I said, this was configured by someone long left (and probably not the best way either)...

I've tried a few tutorials now, partly scared I could really screw up the server, but also not getting anywhere.

---

### Post by jonobr on 2011-12-08
Hi there


Getting a tcpdump will really help on the asterisk side,.

I do a lot of telecom voip mostly on the debugging of asterisk so I can help. ( I promise I will overlook wales knocking ireland out of the world cup)


Tell me what your getting when your running sudo tcpdump

if you cant run sudo , you have big problems.
Have you changed /etc/sudoers ?

---

### Post by richrock on 2011-12-08
tcpdump:  verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes


it paused there before I hit Ctrl-C to quit, and is gave me:

19:39:13.979402 IP 192.168.168.200.netbios-ns > 192.168.168.255.netbios-ns:  NBT UP PACKET(137): QUERY; REQUEST; BROADCAST

1 packets captured
44 packets received by filter
0 packets dropped by kernel.

BTW - think I sorted the Win 7 Samba issue - just a typo in the conf, altered a setting.  Just need to route phone IP addresses back.

---

### Post by richrock on 2011-12-08
Right - managed to run tcpdump on the server.   Didn't get anything through, as Asterisk server decided to go straight to voicemail - no IP addresses to assign for the call.  There is my problem.  :-(

---

### Post by jonobr on 2011-12-08
Hey

I may be a bit confused.

Im guessing your phones have an ip address and are trying to connect to your asterisk server,


They do this on port 5060, looking at those registration attempts may show something, 
thats waht the trace would capture.

Am I missing something in the setup?
Also glad to hear samba shares are ok

---

### Post by richrock on 2012-02-27
Sorry it's been a while, but I've started trying to tackle this again.  It seems our old windows SBS2003 server has a number of Forward and Reverse lookup zones for each phone.  

Asterisk seems to reset the nameserver to the IP address of the server, which is incredibly annoying.

Would there be anything on the phones to set up?  Or could I effectively copy the DNS settings from Windows server to Ubuntu server?

---

