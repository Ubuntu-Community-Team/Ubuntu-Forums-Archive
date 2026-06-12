---
title: "Utilility of tcpdump-like tools and switches?"
date: 2010-09-09
forum: Security
---

### Post by wkulecz on 2010-09-09
I see a lot of discussions about tools like tcpdump and the like and paranoia about plain-text passwords.  I can see how this is still a problem with public wifi networks and other wireless ethernet, but these days even the cheapest "home routers" are actually switches so tcpdump only seems to see traffic to/from the machine it is running on.

Actually for some code I'm developing, it would be very helpful to have tcpdump on a third machine "eavesdrop" on the communication between two others, but it doesn't seem to work.

I have a four computer network connected to our real network using a cheap Linksys home router box and get net access (like posting here) on these four machines via NAT through the router. But my local applications are isolated from the real network so any bugs I develop doesn't get off my local 192.168.1.0 network to cause other problems.  I've used this setup for years.

As I said, am I missing something about tcpdump?  I'd like to run tcpdump on my Ubuntu box and monitor the communication from the Windows setup utility to a small embedded device so I can figure out how to set it up using a Linux program instead of the Windows utility it comes with (documentation is worse than poor)

If I give sudo tcpdump -net 192.168.1.0/24 I only see traffic to/from the box tcpdump is running on.  Short of trying to find an old passive ethernet hub (10BaseT will kill my app for lack of bandwidth), is there something I'm missing about tcpdump and the like that would make them helpful here?

Is tcpdump available for Windows? That would solve the immediate problem.  Time to Google.


Edit:

WinDump was very easy to find, should solve my immediate problem.

---

### Post by HermanAB on 2010-09-09
Also have a look at ngrep.  It is trivially easy to use ngrep to look for user names, passwords and CC numbers.

---

### Post by anomie on 2010-09-09
[QUOTE=wkulecz]Is tcpdump available for Windows? That would solve the immediate problem.[/QUOTE]

For a pretty GUI, see wireshark.

---

### Post by BkkBonanza on 2010-09-09
You can get other LAN users traffic by enabling forwarding on your machine and run an arp spoof attack. This allows you to redirect other IP traffic thru your machine on the way to a third machine.

---

### Post by leonbravo on 2011-04-08
Hi there,

I'm working on a sort of similar thing...

anyways, windump is the utility for windown. Check 

[http://www.winpcap.org/windump/](http://www.winpcap.org/windump/)

cheers.

---

### Post by bodhi.zazen on 2011-04-08
The traffic you capture will depend on where you listen.

I use a switch with a monitoring port, there are several available in a variety of price ranges with a variety of features. If you put the switch outside your router you will capture a lot of noise, better put it inside your router. You can monitor the entire LAN or a segment, again depending on where you put the switch.

tcdump will capture the raw packets (better then snort), snort will filter through the sheer volume of packets for potential problems.

So it sort of depends on what you are wanting to do exactly.

---

### Post by njdove on 2011-04-08
> **anomie said:**
> For a pretty GUI, see wireshark.

I concur - your easiest solution will be to capture your desired traffic by installing Wireshark on the Windows machine. If you'd rather analyze the file on your Ubuntu machine, Wireshark uses the same libpcap format on all platforms so you can save the file and open it on your Ubuntu machine with Wireshark (or tcpdump).

---

### Post by HermanAB on 2011-04-10
Howdy,

Note that you can get all the standard Linux tools on Windows through Cygwin.
[http://cygwin.org](http://cygwin.org)

---

