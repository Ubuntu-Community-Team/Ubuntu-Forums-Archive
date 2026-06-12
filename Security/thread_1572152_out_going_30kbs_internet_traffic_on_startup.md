---
title: "out going 30kb/s internet traffic on startup"
date: 2010-09-10
forum: Security
---

### Post by Manolicious on 2010-09-10
I've noticed a few time when starting up my computer that before I open any browsers or torrenting programs there's about 30kb/s of outgoing internet traffic from my computer that last for a minute or two.  Is this ubuntu's update manager or the [tracker people have been talking about]("http://linux.slashdot.org/story/10/08/10/0319243/Canonical-Begins-Tracking-Ubuntu-Installations")(slashdot.org)?  Is this tracker still installed on some versions and how can i deactivate it?  I believe I had turned off the upgrade managers auto check earlier, it wouldn't have turned itself back on with some latter update, would it have?

Is there any way I can observe what programs are using my internet connection, say in much the same way I can use the system monitor to find what programs are using such and such % of my processor?

---

### Post by uRock on 2010-09-10
I'd say it is Update Manager checking for updates.

---

### Post by BkkBonanza on 2010-09-11
As a test you could add a tcpdump line to your startup that would log the traffic. 
This would allow seeing what it is and to whom it's going.

Adding a simple script into /etc/network/if-up.d would achieve this. 
Something like,

```
#!/bin/bash
tcpdump -i eth0 -w /tmp/test -c 500 tcp or udp
```
(assuming eth0 is your interface)
(this captures first 500 tcp/udp packets)

To read the capture use,

**sudo tcp -r /tmp/test |less -S**

You'll see right away what IP that initial traffic is to.

Use **nslookup IP** to try to locate the reverse name.

BTW I don't see any canonical-census package in the repos. Not sure if that article is baloney or they've hidden it or it's only for some installations. Ah, reading the source article I see it is only for some OEM installs. So if you aren't using one of those then it's not even present.

---

### Post by OpSecShellshock on 2010-09-11
Have you ruled out DHCP and/or NTP requests?

---

### Post by Manolicious on 2010-09-12
> **uRock said:**
> I'd say it is Update Manager checking for updates.

Currently I don't have Submit Statistical Information on and I only have it set to notify me of available updates (according to my update manager), specifically important security and recommended.  Would these constitute 1.8mb of outgoing data?

> **OpSecShellshock said:**
> Have you ruled out DHCP and/or NTP requests?

No, how would I?  I thought only using the commands ifconfig and dhclient would mess with that stuff, commands I haven't used for a while (at least +4 months)

Thanks BkkBonaza, I'll try that out.

---

### Post by uRock on 2010-09-13
> **Manolicious said:**
> No, how would I?  I thought only using the commands ifconfig and dhclient would mess with that stuff, commands I haven't used for a while (at least +4 months)

Thanks BkkBonaza, I'll try that out.
Depending on you network, running Wireshark from on a different machine while booting this one will tell what is going on as the packets mentioned by BkkBonanza will show up as ARP, CUPS, or one of many other protocols that will be directed to the local LAN's addressing scheme instead of connecting to the outside world. If they are TCP /UDP packets, then you'll be able to use whois to track what website your system is connecting to and then if it is showing the IP for the ubuntu servers, then all is good.

If you know your way around snort, then you can use it to capture the packets as well.

---

### Post by BkkBonanza on 2010-09-13
Ah, my example command only captures tcp and udp packets. 
It should provide a simple and effective amount of info.

---

### Post by Manolicious on 2010-10-29
all right BkkBonanza, I believe i got a read out from the command you suggested.  Assuming I used it correctly, would it be safe to post the output here, or should I consult it with my ISP or some security service?

---

### Post by BkkBonanza on 2010-10-30
I couldn't say for sure that it would be "safe". I doubt your ISP would have any interest or be helpful, and a security consultant of some sort is going to cost a lot. 

I would start by trying to undertsand it yourself, and browse it to determine if any logins/passwords may be logged in the data. As far as just trying to understand what is happening you are looking for only a few things. First, what protocols are in play? You would want to look at port numbers and make a list of which ones are being used. Then look at actual destination IP values and again make a list.

Those items alone should tell you a lot about what's going on. You could post that info here unless you think it looks "sensitive" (unlikely). If you do decide to post the packet dump then post it as an attachment not as pasted text. 

As soon as your interface is brought up there will be traffic for DHCP and likely some DNS too. Maybe other stuff. DHCP uses ports 68 and 67 between your IP and the gateway (DHCP server). DNS is port 53 and could be to your gateway or to some other DNS server outside your network.

---

### Post by cariboo on 2010-10-30
> **Manolicious said:**
> I've noticed a few time when starting up my computer that before I open any browsers or torrenting programs there's about 30kb/s of outgoing internet traffic from my computer that last for a minute or two.  Is this ubuntu's update manager or the [tracker people have been talking about]("http://linux.slashdot.org/story/10/08/10/0319243/Canonical-Begins-Tracking-Ubuntu-Installations")(slashdot.org)?  Is this tracker still installed on some versions and how can i deactivate it?  I believe I had turned off the upgrade managers auto check earlier, it wouldn't have turned itself back on with some latter update, would it have?

Is there any way I can observe what programs are using my internet connection, say in much the same way I can use the system monitor to find what programs are using such and such % of my processor?

What the slashdot article was talking about was an applet that phones home that is installed on OEM versions of Ubuntu. If you didn't purchase a system with Ubuntu pre-installed, you have nothing to worry about.

---

### Post by Manolicious on 2010-12-05
BkkBonanza, describing the output of your tcp command in abstract, there's a lot of chatter, but it mainly occurs between me and usually one particular ip address.  This "particular" ip address can vary depending on the moment I used your command when seeing an outgoing connection, which doesn't happen often now (weekly to monthly).  Since learning your command I used it (in bash, can't get a handle of scripts) whenever I saw this weird outgoing connection, looking for the major (or most occurring) offender's site name in their ip address, and then I would add it to my firewall.  So far it has worked, but now it's coming back again so I figure I'd look into the readout I saved after the first few times I tried the command.

In the particular read out I have, my computer is sending something through what I'm guessing is port 47### (### being a set of numbers, at the end of my ip address and site name) to some other guy's port numbered 25###, then something is sent back from guy's 25### to my 47###, with the exact same port numbers (###) as before.  So far I can't pin down what kind of program uses these ports.

When you say actual destination IP values, you mean the ip address followed by their site name, right?  And what do you mean by logins and passwords?  Would I see someone login into my computer with this command?  If so I didn't see anything in the output that looked like a login.  

Also a few questions about the command you gave me.  In the readout, what's the stuff after the colon (: ) on each line?  Would the tcpdump man file tell me about this readout?  Also is there a specific man page for the tcp bash command?  That seems to be a program that can read the readout of a tcpdump.  Could I just write it to /tmp/test.txt so I can read it without the tcp command?  I seem to be having trouble with tcp in bash, I think.

---

### Post by BkkBonanza on 2010-12-05
It's been a while so I went back tor ead the old posts here.

That **tcp** command is a typo and should be **tcpdump**. tcpdump can be used to both capture and write traffic and also read it and format it for viewing. 

**sudo tcpdump -r /tmp/test | less -S**

just reads the dump file and formats it, then pipes it to the less command to allow scrollable viewing. The -S flag makes it easier to view by preventing line wrapping.

**man tcpdump** may help with options and has some useful info on output format.

The stuff listed after the : on output is usually packet flags info, sequence numbers etc. This can be ignored (or -q added to command to prevent detailed info).

Once you find the suspicious IP address you are connecting to you can give that to nslookup to try and find a reverse name lookup. This sometimes tells you something useful but not always. Some addresses don't have reverse records and some have records that aren't very useful. (If tcpdump has reverse name lookup on by default then the reverse names may already be in the dumped data - to see actual ip address add -n to the tcpdump read command to stop name lookup, maybe that is confusing you.)

When a connection is "live" you can use the command, 

sudo netstat -ntup

to provide a list of open connections and see which process has them open. This will help detect which program is makign that connection to your suspicious IP.

The port numbers are not very useful as they are usually random high ports and even when they appear to be "standard" ones they can easily be otherwise. Judging by your info showing high ports 48xxx 25xxx it initially seems like peer-to-peer traffic that you're seeing. An exmaple might be Skype or Bittorrent but that's just a guess really. The most useful thing to find out is what process is opening the connection at your end.

You won't see user login info in the dump unless you use the -A option to output packet data in ascii format. Even then how much actuall packet contents are captured depends on options during the capture phase (if I recall correctly).

---

