---
title: "can i check if ive been port scanned?"
date: 2011-10-13
forum: Security
---

### Post by mushy365 on 2011-10-13
i'm on my lan and doing an nmap tutorial to scan machines on my lan, to get the hang of nmap. The scans are running fine and brining back results. 

The thing that struck me tho was, if someone was scanning me, like i am scanning myself how would i be able to tell. 

Is there anywhere evidence of being scanned might show up. In the tutorial for nmap you can spoof the ip address. So would be interesting to be able to check if there was a log to see what ip address it thought it came from.

---

### Post by Jonathan L on 2011-10-13
> **mushy365 said:**
> i'm on my lan and doing an nmap tutorial to scan machines on my lan, to get the hang of nmap. The scans are running fine and brining back results. 

The thing that struck me tho was, if someone was scanning me, like i am scanning myself how would i be able to tell. 

Is there anywhere evidence of being scanned might show up. In the tutorial for nmap you can spoof the ip address. So would be interesting to be able to check if there was a log to see what ip address it thought it came from.

Hi Mushy

Have you tried tcpdump/wireshark on machine A and scan it from machine B ?

Kind regards,
Jonathan.

---

### Post by OpSecShellshock on 2011-10-13
The simplest way to tell is just to understand that everybody gets port scanned.

If you actually want to see it, you can install something like PSAD which looks for port scans. Most likely you'll have to be connected to the Internet directly in order to see much activity though. If you've got a router between your connection and LAN then most of the port scanning will probably stop there, since that's one of the things that routers are for. There may be evidence of scanning on the router itself, but it will vary by brand probably. Check the administration console.

---

### Post by mushy365 on 2011-10-13
i'll look into the wireshark thing, as ive used it before. However ive always thought of it as something you turn on and turn off again. Does it have a use as an IDS? And can be let run constantly?

---

### Post by CharlesA on 2011-10-13
> **mushy365 said:**
> i'll look into the wireshark thing, as ive used it before. However ive always thought of it as something you turn on and turn off again. Does it have a use as an IDS? And can be let run constantly?
Wireshark only reads packets, I don't think it does IDS.

Check out these two threads:
[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

---

### Post by Dangertux on 2011-10-13
> **mushy365 said:**
> i'm on my lan and doing an nmap tutorial to scan machines on my lan, to get the hang of nmap. The scans are running fine and brining back results. 

The thing that struck me tho was, if someone was scanning me, like i am scanning myself how would i be able to tell. 

Is there anywhere evidence of being scanned might show up. In the tutorial for nmap you can spoof the ip address. So would be interesting to be able to check if there was a log to see what ip address it thought it came from.


In regards to spoofing ip addresses , if you enable tcp_syncookies in your firewall script as such

```

echo "1" > /proc/sys/net/ipv4/tcy_syncookies

```

it will cut down alot on IP spoofing.

That being said if you're looking to determine if someone is using reflective or a spoofed IP address to scan your machine you can do the following

```

grep /var/log/syslog martian

```

Additionally it's important to understand with nmap spoof scanning with the -S option that they will not receive results if the IP address they are "spoofing" is not an actual interface on their machine. Since the returned packets will essentially go nowhere.

Also I don't recommend PSAD - it's people's gut reaction to enable automatic port scan blocking which can be used by an attacker to create a denial of service condition (for instance if I port scan you and spoof google's ip)

Wireshark can help you analyze a port scan in real time but is not an IDS, if you're looking for something along those lines I would recommend Snort.

Hope this helps

---

### Post by Lars Noodén on 2011-10-13
You could look at Snort if you want an IDS running.  Just be sure that you budget the time to go through the logs and reports.  Otherwise, there is no point in running it.   Also, as mentioned above before, everyone connected to the net gets scanned.

---

### Post by Dangertux on 2011-10-13
> **Lars Noodén said:**
> You could look at Snort if you want an IDS running.  Just be sure that you budget the time to go through the logs and reports.  Otherwise, there is no point in running it.   Also, as mentioned above before, everyone connected to the net gets scanned.

BASE is also a decent graphical presentation of the logs snort generates that is relatively quick to check on too. If that's something OP is interested in.

---

### Post by bodhi.zazen on 2011-10-13
You can try PSAD

[http://bodhizazen.net/Tutorials/psad](http://bodhizazen.net/Tutorials/psad)

It is safe to assume you have been and are being scanned ;)

A better question is what to do about it. to answer that question, what services are you running and what have you done to secure them ? Do you have a router ? etc, etc.

Snort is a fantastic tool and will alert you to more significant traffic, but it is not specific to Linux, and you will get a number of "false positives" from snort.

---

### Post by Jonathan L on 2011-10-13
> **mushy365 said:**
> i'll look into the wireshark thing, as ive used it before. However ive always thought of it as something you turn on and turn off again. Does it have a use as an IDS? And can be let run constantly?

Hi Mushy

No, my suggestion about wireshark was purely so you can understand what happens in the scanning.  It's no use to you in protecting your machine directly: for that, as you say, you want something which does detection and logging.  But for education about how attacks happen, it's invaluable.

Kind regards,
Jonathan.

---

### Post by mushy365 on 2011-10-13
Thanks guys, alot to think about. Im using wireshark now to see what a port scan looks like and it does look pretty obvious, at least the ones that my limitied knowledge knows how to do. Slightly disappointed with wireshark tho, and i said it on another thread. 

I thought i would be able to use it to sniff all traffic on my lan, even if it was from my cousins laptop to the internet and didnt have anything to do with my machine, but it seems i can only capture traffic either sent to and from the machine running wireshark

---

### Post by bodhi.zazen on 2011-10-13
> **mushy365 said:**
> Thanks guys, alot to think about. Im using wireshark now to see what a port scan looks like and it does look pretty obvious, at least the ones that my limitied knowledge knows how to do. Slightly disappointed with wireshark tho, and i said it on another thread. 

I thought i would be able to use it to sniff all traffic on my lan, even if it was from my cousins laptop to the internet and didnt have anything to do with my machine, but it seems i can only capture traffic either sent to and from the machine running wireshark

Wireshark will sniff all your traffic on a LAN, you just need to learn to use it.

Look at the snort documentation ;)

[img]http://www.digitalundercurrents.com/blog/wp-content/uploads/2011/02/snort_topology.png[/img]

[http://www.digitalundercurrents.com/blog/?p=82](http://www.digitalundercurrents.com/blog/?p=82)

substitute wireshark, tcpdump, etc for snort, it is all about location of your sniffer.

See also info on routers, hubs, switches, monitoring ports, etc (network architecture). You can not sniff others on your LAN as you are on a switch.

---

### Post by mushy365 on 2011-10-13
in those diagrams is snort ment to be a computer running snort and all internet data is routed through that computer?

At the minute i have 


cousins laptop when she comes down wireless connection
|
|

router  -------------------------------- Wireless connection to windows laptop
|
|

my ubuntu computer with snort



the router is a self contained unit i got from my isp, but ive no idea how to install snort to read traffic from all three machines.

anyone got a good install tutorial for snort btw?

---

### Post by Dangertux on 2011-10-13
> **mushy365 said:**
> in those diagrams is snort ment to be a computer running snort and all internet data is routed through that computer?

At the minute i have 


cousins laptop when she comes down wireless connection
|
|

router  -------------------------------- Wireless connection to windows laptop
|
|

my ubuntu computer with snort



the router is a self contained unit i got from my isp, but ive no idea how to install snort to read traffic from all three machines.

anyone got a good install tutorial for snort btw?

It's best to use snort on either a gateway, or at the gateway in a data management zone on a mirrored port. This allows you to see all traffic going into and out of the network.

Using Snort ad-hoc inside of the network greatly limits its functionality, and usefulness. 

As far as the tutorial for installing it goes this is for the version in the repos , which is a little bit out of date at this point. However, for the most current version you will have to compile from source which is kind of a pain if you're new to it.

[https://help.ubuntu.com/community/SnortIDS](https://help.ubuntu.com/community/SnortIDS)

Hope this helps.

---

### Post by Jonathan L on 2011-10-13
> **mushy365 said:**
> Thanks guys, alot to think about. Im using wireshark now to see what a port scan looks like and it does look pretty obvious, at least the ones that my limitied knowledge knows how to do. Slightly disappointed with wireshark tho, and i said it on another thread. 

I thought i would be able to use it to sniff all traffic on my lan, even if it was from my cousins laptop to the internet and didnt have anything to do with my machine, but it seems i can only capture traffic either sent to and from the machine running wireshark

... as the others have said, it's about whether the packets are arriving on the computer doing the packet sniffing, not about the sniffer.  For these purposes a good ethernet switch will be able to help a lot, as you can put a port into diagnostic mode; obviously wifi is public; and I keep a box of old 10baseT ethernet hubs for this exact purpose.

Look for broadcasts too, of course.

Hope that helps.

Kind regards,
Jonathan.

---

### Post by SparTacux on 2011-10-14
> **mushy365 said:**
> i'm on my lan and doing an nmap tutorial to scan machines on my lan, to get the hang of nmap. The scans are running fine and brining back results. 

The thing that struck me tho was, if someone was scanning me, like i am scanning myself how would i be able to tell. 

Is there anywhere evidence of being scanned might show up. In the tutorial for nmap you can spoof the ip address. So would be interesting to be able to check if there was a log to see what ip address it thought it came from.


If you nip over to GRC.COM and select Shields up it will do a port scan for you. I tried it out myself the other day & it scanned my Router Wan IP address. The Router logs showed consecutive port scans starting at port zero and progressing upwards in sequential steps of one. Some Routers  have some sort of firewall log than can be viewed via a browser and sometimes the logs can be sent via email to an email address of your choice. My wireless router allows it to send syslog data on port 514 which can be picked up by a computer on my network. If you have a dongle you can port scan your router from outside your network.

If you use nmap from within your network then you can see the scan logs by enabling logging in GUFW and view the UFW log files on the machine you are scanning. Be warned - it generates lots of logs to various log files. You can make changes to some configuration file so that UFW only writes to the UFW logs.  

Try nmap and scan the LAN side of your router by typing the target address as the gateway to your router.

For example try nmap -p- 192.168.0.1

port 80 will probably show up as open since the router uses a web browser to configure its settings.

---

