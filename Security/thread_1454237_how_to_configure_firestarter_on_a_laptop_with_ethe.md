---
title: "how to configure firestarter on a laptop with ethernet or wireless connection"
date: 2010-04-14
forum: Security
---

### Post by tanoloco on 2010-04-14
Hi guys,

I've got a laptop which can use both ethernet OR wireless connection.
Problem:
1. the laptop is used by several users and some of them are very basic user, so they need the icon of firestarter to be visible on the tray to know what's goin' on, and that's mean they need to see the red  stopped icon of firestarter to know they have to switch from ethernet to wireless or viceversa to activate the firewall.

2. It's impossible to know in advance if the laptop will connect through ethernet or wireless
and firestarter can only be set to work over one or the other but not both as far as I know.

What I want:
- to have the icon of firestarter automatically shown on the tray so users can change something if they notice that something goes wrong with the firewall. I can teach all the user to change firestarter preferences in order to change eth0 to wlan0 or viceversa if they see the red point - stopped icon of firestarter.

Solutions:
a. I've configured firestarter to start on startup: this works good but on every startup if there's no connection it shows an alert saying that networking is not ready.
Is there a way to avoid this annoying alert? Users will be scared if they see this.

b. Otherwise is there a way to start firestarter only when a networking start instead of on startup? This would avoid the startup message of firestarter and let the user automatically see the icon on the tray if everything is going right.

c. Otherwise is there a way I miss to configure firestarter in order to work over both ethernet AND wireless? In this way I will avoid to start firestarter at all because (hopefully) it would work on any case.

Any help would be appreciated
Thanks

---

### Post by bodhi.zazen on 2010-04-14
Your users do not "need" the firestarter icon to show them what's "going on".

Firstarter, or any tool, should be used to set your firewall, then it should be closed. It runs as root and should NOT be used to monitor network traffic.

IMO, by far, the easiest solution is to remove - purge firestarter and use ufw.

```
sudo apt-ger purge firestarter
sudo ufw enable
```

Those commands will remove firestarter and enable your firewall.

---

### Post by tanoloco on 2010-04-15
Hi bodhi.zazen,

wow! Are you always there to answer questions??? Is it a job for you???
Very good! Thank you for this!

Thank you for your suggestion: it solved my problems!
Now I have a firewall which is enabled on startup and working automatically on any available interface.

Just to share my experience which might help someone else who could read this thread in the future:
1. I found this very good manual on ufw syntax and usage:
[http://manpages.ubuntu.com/manpages/karmic/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/ufw.8.html)

2. I prefered to install a gui, as well, to make its configuration easier to those people scared of using a shell. This is gufw but somehow the version on the repository doesn't work properly on my system and I download its new version from here:
[https://launchpad.net/gui-ufw](https://launchpad.net/gui-ufw)

Everything is working nice here:
ufw version: 0.29-4ubuntu1
gufw version: 10.04.3-0ubuntu2
kernel: 2.6.31-20-generic (karmic)

Now I've got a couple of things left:
a. How can I put the label [solved] on this thread? Never done before
b. The problem of a monitoring applet still remains: I will open a new thread on this.

Thank you!!! :)

---

### Post by LeeDaugherty on 2010-04-15
Firestarter was truly a one-of-a-kind program.  Unfortunately, it is seriously outdated and hasn't been developed in awhile.  Why it keeps getting brought into new versions, I don't know.  The real-time monitoring of firestarter was neat, but that really sums it up.  Now, I even feel akward saying this, but don't get to wrapped up and spend too much time regarding firewalls with Ubuntu.  Unless you live in public-wifi spots and have plenty of intelligent enemies, the ability to remote-exploit a Linux box takes some serious talent, and the best ways to do it, a firewall isn't going to help.  UFW is fine, if you like the peace of mind, it is the best in simply configuring iptables.  And the best thing you can ever do (I wish the world would do), if you want protection on any PC, pay careful attention to your ICMP section of your firewall setup.  If on first glance you aren't seen on the network, you can avoid the rabid port-scan onslaught.

---

### Post by tanoloco on 2010-04-15
Here is my post mentioned before
[http://ubuntuforums.org/showthread.php?p=9125704]("http://ubuntuforums.org/showthread.php?p=9125704#post9125704")

in which I ask for a network applet or I explain how to turn firestarter into it.

Hey Lee thanks for your comment! :)
If you have a look at the above link (long) you can see how I discovered how to keep using firestarter features as a network applet while using ufw as a firewall.

Maybe I'm a paranoid but I prefer to set a firewall on a laptop and on any pc with 24 h open connection .. especially if there are data I don't want to loose stored in them :)

Thank you for your suggestion: I've never checked ICMP section while setting a firewall.
Never heard about it at all .. sorry :( I'm still a learner 

I'll try to read more about it ... in the meanwhile, for example, using ufw what must I check according to your suggestion?

Thank you!!!

BTW: how can I put the prefix [solved] on this thread?

---

### Post by LeeDaugherty on 2010-04-15
Once again, Firestarter when ran initiate iptables and runs a script against it to create rules.  It's scripts are very good, but very dated, and no longer accurate for performance reasons.  UFW does the same, whichever one you run last, is the one that actually has updated the iptables the last.  You don't need a firewall.  I don't care what you are doing or what information you have, I'm just being honest.  If you want to be paranoid, great, I think that is a great quality to have when anyone's on the internet.  But a firewall isn't going to help.  Let me explain how every compromise happens.  I will start by port-scanning a bunch of ips looking for victims.  I (for simplicity) ping you, you respond (ICMP).  That tells me I found a computer (now you get why I say turn them off).  Since I found you, I then run a more intrusive port-scan identifying what kind of computer you are, what os you are running, what services you are running (what ports you have open).  With this information, I load up a program (they all use the same one) and I see if there are any known exploits for your OS, with your version, software, running the services you have.  Take for example, I scanned you, and cups (the printer program responded), I know a couple months ago, there was a bug in that program that could allow someone remote to hijack it (I know...I'm tying to keep this simple, if anyone actually read the cups exploit).  I target my program, to do exactly what causes cups to break.  I break it, the program hangs, and when it does, I send it more code, but this time, code that tells your computer to give me a command prompt.  Your computer does, and I start poking around, escalate my priveleges, and steal all your porn.  Ok...hopefully you followed that.  That is how one-on-one hacking is done-99% of the time.  Long story short--that does NOT happen!  Even on Windows machines, I mean technically yes it does happen.  But it happens to the VP of Google, it happens to a server that holds 50,000 credit card numbers.  If you have an arch-enemy, it could happen to you.  But it doesn't happen.  Botnets...are simply that, bots.  They aren't people.  It's drones of machines.  Uninstall your firewalls, turn off ICMP replies the handful of them, and go back to checking downloading music, checking Facebook, balancing your checkbook.  I don't make light of internet security, I have literally worked it for 15 years, but one-on-one attacks don't happen, and definately not on Ubuntu.  You should have a router anyway :)  That is your firewall.

---

### Post by cdenley on 2010-04-15
> **tanoloco said:**
> 
Maybe I'm a paranoid but I prefer to set a firewall on a laptop and on any pc with 24 h open connection .. especially if there are data I don't want to loose stored in them :)

Does your firestarter applet run with root privileges? If you're paranoid, then this should really worry you.
> **tanoloco said:**
> 
Thank you for your suggestion: I've never checked ICMP section while setting a firewall.
Never heard about it at all .. sorry :( I'm still a learner


Whether dropping pings (ICMP echo) actually make you safer is debatable. It may reduce the number of port scans, but if port scans can't succeed in finding a vulnerable service, why does it matter?

---

### Post by LeeDaugherty on 2010-04-15
I'm not saying turning off ICMP replies will keep you safe, but it's the most important (in my mind) and most often overlooked step.  Being silent on the network is the best defense.  (Next to keeping your system up to date and not thinking ftp and telnet are safe because no one is going to guess wizard is your password).  The funniest thing, in the Firestarter manual I remember, in order to fix the issue of it popping up asking for su auth, the manual tells you to modify sudoers to always allow Firestarter.  Always thought that was funny for a "security" program to offer that as a workaround to an annoyance that is supposed to be there.  True story!  Look it up!

---

### Post by tanoloco on 2010-04-15
Hey Lee,

once again thanks for your brilliant explanation and for sharing your long experience :)

A few things:
1. I'm not worried about porno thieves :)
2. I removed definetely firestarter and enabled ufw
3. I use grep /var/log/syslog to check if something goes wrong
4. How can I turn off ICMP replies? I don' know if it is so important according to cdenley advice (thank you for your post!!) but it seems to me a good idea as you explained it.

Great help!!!

Cheers
T

pd: No idea on how to put the [solved] prefix uh??? :confused:

---

### Post by LeeDaugherty on 2010-04-15
I don't know about solved, figued admins did that.  CDenley is completely right, it is very debateable.  In internet security everyone has what's important to them, and honestly we are all wrong, cause poo still hits the fan sometimes.  But one reason I explained myself, is mitigating the interest of the intruder should be a top-priority.  One can spend all their time building thousands of lines of firewall rules, but if they would have just not replied to the ICMP request to begin with and gotten passed over, the whole thing seems kind of silly.  And it's a 30 second process.  And if you don't believe me, ping microsoft.com.  ICMP was ordered suspended throughout the entire company public and private LANs several years ago.  So hey what do I know...look it up.  ICMP replay attacks, redirects, next to ARP it's the biggest security hole there is.  And unlike ARP, it can be stopped.  So maybe one-day when ISPs decide that no net-neutrality snafus are going to bitch when they stop routing ICMP, the world would be a better place.

---

### Post by bodhi.zazen on 2010-04-15
> **LeeDaugherty said:**
> I'm not saying turning off ICMP replies will keep you safe, but it's the most important (in my mind) and most often overlooked step.  Being silent on the network is the best defense.  (Next to keeping your system up to date and not thinking ftp and telnet are safe because no one is going to guess wizard is your password).  The funniest thing, in the Firestarter manual I remember, in order to fix the issue of it popping up asking for su auth, the manual tells you to modify sudoers to always allow Firestarter.  Always thought that was funny for a "security" program to offer that as a workaround to an annoyance that is supposed to be there.  True story!  Look it up!

If you monitor such port scans they do not typically start with a ping, why would they ? Most scripts simply scan an IP range looking for OS and open ports (ie they start with a port scan).

IMO people who deploy such tools became wise to hosts not responding to a pind many years ago, so while this advice may have been good at one time, IMO it is very much out dated.

If a port is "closed" it is closed (secured), there is no convincing argument that DROP is any more or less secure then REJECT, both are secure.

So turn off ping replies if you wish, but be sure to secure any open ports you may have.

---

### Post by LeeDaugherty on 2010-04-15
I have to disagree.  Port scans are ICMP based almost all of the time.  It's the best way to travel great distances with the least chance of detection.  Whether it's the actual ping utility no, even nmap uses hping.  ICMP's are key in transversing firewalls for appropriate OS detection and network mapping.  And blocks are scanned at once, and the most popular blocks to scan are blocks of cable/dsl users.  They are always on, and offer the best chance to get beginner users.  Here in Dallas, Time Warner hands out strictly cable modems, no nat no routers, nothing.  Alot of people plug in and go with a public ip.  I have it very well documented, while Time Warner in this area is the oldest ISP (and IMO not the best in keeping up with their network), their network withstands a great deal more of scans than my at&t and fios connections (which can be explained due to DSL infrastructure), but another point I think people need to remember, is more often than not, port scans aren't done by people.  These are bots setup to gather information, like the old war dialing days.  Compromised PCs are fetching anywhere from 0.05 up to as high as 0.20.  Unfortunately because of the downturn world-wide captcha breaking, information gathering, and even script writing are becoming money makers of course for the people that run them, but for the people they farm out the grunt work too.  ICMP (again along with ARP) is old, but since it mostly is ignored and a very good protocol to map with, it is used the most in first stage network discovery.  Drop, is definately more secure than reject.  Reject sends back a reply, and if ICMPs are non-responsive, and you reply a reject, you haven't accomplished stealth-i-ness.  The word sounded good at the time.  By dropping, you maintain non-responsiveness, which is very important in the first stage.  Second, OS fingerprinting which leads directly into vulnerabilty assesment, yes, is equally important.  I'd just not rather spark anyone's interest by answering the doorbell.

---

### Post by bodhi.zazen on 2010-04-15
> **LeeDaugherty said:**
> I have to disagree.  Port scans are ICMP based almost all of the time.  It's the best way to travel great distances with the least chance of detection.  Whether it's the actual ping utility no, even nmap uses hping.  ICMP's are key in transversing firewalls for appropriate OS detection and network mapping.  And blocks are scanned at once, and the most popular blocks to scan are blocks of cable/dsl users.  They are always on, and offer the best chance to get beginner users.  Here in Dallas, Time Warner hands out strictly cable modems, no nat no routers, nothing.  Alot of people plug in and go with a public ip.  I have it very well documented, while Time Warner in this area is the oldest ISP (and IMO not the best in keeping up with their network), their network withstands a great deal more of scans than my at&t and fios connections (which can be explained due to DSL infrastructure), but another point I think people need to remember, is more often than not, port scans aren't done by people.  These are bots setup to gather information, like the old war dialing days.  Compromised PCs are fetching anywhere from 0.05 up to as high as 0.20.  Unfortunately because of the downturn world-wide captcha breaking, information gathering, and even script writing are becoming money makers of course for the people that run them, but for the people they farm out the grunt work too.  ICMP (again along with ARP) is old, but since it mostly is ignored and a very good protocol to map with, it is used the most in first stage network discovery.  Drop, is definately more secure than reject.  Reject sends back a reply, and if ICMPs are non-responsive, and you reply a reject, you haven't accomplished stealth-i-ness.  The word sounded good at the time.  By dropping, you maintain non-responsiveness, which is very important in the first stage.  Second, OS fingerprinting which leads directly into vulnerabilty assesment, yes, is equally important.  I'd just not rather spark anyone's interest by answering the doorbell.

No, that is not correct.

nmap is a complex tool ...

Let me show you an example :

iptables :

Chain INPUT (policy ACCEPT 2004 packets, 84176 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    **0     0 ACCEPT     icmp --  any     anywhere             anywhere**            
    0     0 DROP       all  -f   any     anywhere             anywhere            
    0     0 DROP       all  --   any     anywhere             anywhere            state INVALID 
    0     0 ACCEPT     all  --  any     anywhere             anywhere            state RELATED,ESTABLISHED 
 2310  102K **REJECT**       all  --  any     anywhere             anywhere            

As you can see ping (all icmp in fact) is accepted :

root@lucid:~# ping -c 1 ip_address
PING host_name (ip_address) 56(84) bytes of data.
64 bytes from host_name (ip_address): icmp_seq=1 ttl=64 time=0.109 ms (aye, it's a LAN)

as is reflected in iptables :

Chain INPUT (policy ACCEPT 2009 packets, 84648 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    **6   504 ACCEPT     icmp --  any     anywhere             anywhere**

Aslo, note REJECT rather then DROP !!!

Now let us try nmap (it takes a long time to run):

root@lucid:~# nmap -p1-65535 -sS -sV -O hostname

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-04-15 11:28 MDT

[B]All 65535 scanned ports on host_name (ip_address) are filtered
Too many fingerprints match this host to give specific OS details[/B]

OS and Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 11.92 seconds

So accepting icmp and REJECT as opposed to DROP did not affect the results of nmap and OS detection (or a lack of it).

Also look at the numbers in my first post, you can see nmap does NOT use imcp.

Hopefully this little exercise clears up REJECT vs DROP and icmp traffic :twisted:

---

### Post by uRock on 2010-04-15
Wireshark is in the ubuntu repositories as is Zenmap, which is a GUI front end for NMAP. I have scanned a few servers to help test people's NIDS and ran Wireshark at the same time. Zenmap uses TCP scan unless instructed otherwise. Port scans do not use ICMP to find ports, though if the scanner receives an ICMP packet, it will process it. A good firewall will block ICMP responses. Here is a screenshot of wireshark while running a port scan. In wireshark, all grayed out entries are port scan packets. This portscan used TCP and a few ARP packets. This scan was done on a local network without the filtering support of the router's NAT. A scan from outside my network will not see any of my PCs.

---

### Post by Jive Turkey on 2010-04-16
AFAIK the concept of ports does not apply to the ICMP protocol.

---

### Post by uRock on 2010-04-16
Correct, ICMP does not use ports and cannot be used for a port scan. That is part of the reason I gave the visual of a port scan. Some people don't believe until they see it.

Most server operators have a Network Intrusion Detection System (NIDS) that will detect the port scan and blacklist the scanner's IP.

For more info on NIDS please see Bodhi's [Ubuntu Intrusion Detection]("http://ubuntuforums.org/showthread.php?t=919472") thread.

Cheers,
Ronnie

---

### Post by node8472 on 2010-04-16
[solved] is under your thread tools at the top of your thread! "mark thread as solved" 
And you all need to chill, we're all in this community to help each other and peacefully co-exist not bag on another!

peace

---

### Post by tanoloco on 2010-04-16
> **node8472 said:**
> [solved] is under your thread tools at the top of your thread! "mark thread as solved" 
And you all need to chill, we're all in this community to help each other and peacefully co-exist not bag on another!

peace

Hey node! thanks for having pointed me to the right place: I have looked under thread tools before while searching the [solved] tag but I haven't noticed it!
Maybe it would be more visible as first line or [COLOR=SeaGreen]with a different color [/COLOR](green?).


Anyhow guys: thank you for all your comments!! I apologize I cannot really understand you: I switched from windows only since a few months (first year on summer!) and I think I'm a little paranoid because I realized how windows is unsecure ... I might say that ubuntu seems to me a very secure place: for example I could drop anti-virus apps and this is still unbellievable !!!

I read somewhere that maybe a firewall is a good choise to install though not needed and now I discovered ufw it's enough for my needs.

Now I can understand better about ICMP (thank you all) and what I can say is that wiith gufw is very easy to select "deny" (which I think is wht you call drop) "reject" and "pemit" both on incoming and outcoming traffic.

deny is colored in red, while reject in blue and permit in red.
this suggests me that deny is considered more safe than reject, at least by the developers of gufw.

I'm not a guru, very far away to be, I can understand that a closed door is safe because it's close .. but I think that closed and silent is safer!!
It's only an opinion I don't have any argument on that: I only think that if I was a hacker I would keep on trying to search an access from a responding ip if I really want to force a network.

But I'm no a hacker :(

Anyhow I think that ubuntu (linux more generally) is a safe place because there is a lot of people  like you who keep on discussing about security staff. So thank you for all your efforts which can offer to people like me, who cannot understand deeper, a safer place

:)

I put solved on that thread because my original question was answered: you better open a new thread if you want to keep on discussing on ICMP or whatever because in the future will come here people googling for "how to configure firestarter on a laptop with ethernet or wireless connection" I suppose ...

:lolflag:

---

### Post by node8472 on 2010-04-16
ubuntu has a firewall (iptables) built into the background, by default ubuntu doesn't have any open ports for the public to see. Even if you get some kind of mal-ware you must give it root auth. inorder for it to run. but so long as you and your users continue safe-surfing practices you'll be fine.

---

### Post by d3v1150m471c on 2010-07-14
> **bodhi.zazen said:**
> 
If a port is "closed" it is closed (secured), there is no convincing argument that DROP is any more or less secure then REJECT, both are secure.


While both are secure, drop takes an extra step in defense by saying to the attacker, "This host doesn't exist so don't bother." If they see a host is up it's feasible they may look for other routes of intrusion.

---

### Post by bodhi.zazen on 2010-07-14
> **d3v1150m471c said:**
> While both are secure, drop takes an extra step in defense by saying to the attacker, "This host doesn't exist so don't bother." If they see a host is up it's feasible they may look for other routes of intrusion.

I have to disagree, that concept is sooo .... 1990's era. =)

First most automated attacks or so called script kiddies do not care, they simply scan because they can.

Second, unless you take additional steps in your firewall configuration, "DROP" does not fool anyone (hint - take a look at the tcp protocol and capabilities of nmap).

So DROP does not deter either the script kiddies or the "pros".

Here is what you get with "DROP"

> sudo nmap 192.168.0.19

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-07-14 22:00 MDT
All 1000 scanned ports on 192.168.1.19 are filtered
MAC Address: 52:54:00:56:69:C1 (QEMU Virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.75 secondsThis is with two rules

The first is to accept ONLY related and established packets[INDENT]sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT[/INDENT]The second rule is to DROP everything else.[INDENT]sudo iptables -A INPUT -j DROP[/INDENT]As you can see, the host is up. You can even see I am testing a VM and the "MAC Address" :twisted:

---

### Post by d3v1150m471c on 2010-07-15
I think our rules are different. My ip currently will not drop all packets, however, on my old setup I was never able to even detect if my ip was up, let alone port statuses. This was the same with my audits and audits from shields-up and nmap.org.

---

### Post by bodhi.zazen on 2010-07-15
> **d3v1150m471c said:**
> I think our rules are different. My ip currently will not drop all packets, however, on my old setup I was never able to even detect if my ip was up, let alone port statuses. This was the same with my audits and audits from shields-up and nmap.org.

I was responding to your claim that DROP was somehow better then REJECT. 

You claimed > drop takes an extra step in defense by saying to the attacker, "This  host doesn't exist so don't bother."

So I posted a demonstration that that claim is not accurate ^^

As I indicated, you need more then "DROP" (vs REJECT).

---

