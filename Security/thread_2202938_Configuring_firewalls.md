---
title: "Configuring firewalls"
date: 2014-01-31
forum: Security
---

### Post by baguahsing2 on 2014-01-31
I know this will be a loaded question, but here it goes. I have been trying to learn how to properly configure a firewall in order to stealth ports and to prevent traffic on ports I do not use either by the os or installed programs.  I have a hardware firewall on my router and a software firewall my pc, laptop, and tablet.  Do I stealth ports on the router, the pc, or both?  If you want to block outgoing traffic, where is the best place to do that, hardware or software?  Some devices will not work on my wifi unless I broadcast my ssid.  Is mac id a good alternative to prevent unwanted access (I live next door to a public library).  I have found the master list of all 65k ports and what they are used for, but is there a readers' digest version that lists ports used by Linux, windows, android, and the like?  What are some good resources to learn about firewalls and how to configure them.  Do the ps3 and xbox use ports other than the ones for http?  This is a lot, I know, but my googling is making me feel like I am running around in circles.  I mainly surf the net, email, ps3, xbox, play lotro, Netflix thru ps3, and iTunes is about 95% of what me and my family do online, it that helps.

---

### Post by TheFu on 2014-01-31
> **baguahsing2 said:**
> I know this will be a loaded question, but here it goes. I have been trying to learn how to properly configure a firewall in order to stealth ports and to prevent traffic on ports I do not use either by the os or installed programs.  I have a hardware firewall on my router and a software firewall my pc, laptop, and tablet.  Do I stealth ports on the router, the pc, or both?  If you want to block outgoing traffic, where is the best place to do that, hardware or software?  Some devices will not work on my wifi unless I broadcast my ssid.  Is mac id a good alternative to prevent unwanted access (I live next door to a public library).  I have found the master list of all 65k ports and what they are used for, but is there a readers' digest version that lists ports used by Linux, windows, android, and the like?  What are some good resources to learn about firewalls and how to configure them.  Do the ps3 and xbox use ports other than the ones for http?  This is a lot, I know, but my googling is making me feel like I am running around in circles.  I mainly surf the net, email, ps3, xbox, play lotro, Netflix thru ps3, and iTunes is about 95% of what me and my family do online, it that helps.

That is a bunch of questions. I certainly do not know all the answers, but I'll "inflict" you with some and a few opinions.

Stealth is a made up term that means dropping packets. This is security by obscurity. That is usually not much security at all and makes troubleshooting issues harder.  So, if you don't want people to see that your public IP has anything there, then have the router drop all inbound packets.  You'd want to do this on portable devices too, since that router won't always be in front of you.

Blocking outbound traffic works the same way. Both, since if one part of your network has a failure, then the other will still work.

Don't worry about broadcasting the SSID. Anyone trying to hack your wifi will see it anyway.
MAC filtering is useless. Don't bother. Here's a [wifi security checklist.]("http://blog.jdpfu.com/pages/wifi-security")

The list of "ports" is also called services is stored in /etc/services on every UNIX/Linux machine. These are guidelines only. The admin for the machine/service can elect to use a different port.

I don't know ANYTHING about the PS3/xbox ... other than that UPnP needs to be disabled on your router if you care at all about security.

As a beginner trying to learn more grc.com/sn is a good place to start. They ramble a bunch and don't always get the details 100% correct, but overall Steve does more good than harm.  A warning - the more they hype anything, the less you should pay attention.

About firewalls and learning more ... on Linux there is only 1 firewall - iptables. Everything else is just an interface to iptables - PERIOD.  It is really impressive what can be accomplish with this tool alone, but a tiny mistake can lock you out of your own machine or allow all traffic access. Do not just copy rules from websites without understanding. It is probably best to keep it simple and use ufw or gufw to start. That front-end is limited, but will also keep you out of too much trouble.

Anyway - hope that helps.

---

### Post by ian-weisser on 2014-02-01
> **baguahsing2 said:**
> I have been trying to learn how to properly configure a firewall in order to stealth ports and to prevent traffic on ports I do not use either by the os or installed programs.

I completely agree with TheFu on "stealthing." It sounds cool and helpful...but it's usefulness is limited.
Packets arriving on ports that have no application listening are discarded by the kernel anyway.
Packets arriving on ports that do have listening applications will be processed by those applications.
One strategy is to limit the number of listening applications to those you are actually using. If you have no need for anyone to remotely login to a system, then remove it's listening ssh daemon.
Another strategy is to limit the permissions and access of listening applications, usually by running them as a system user (instead of as a human user), and properly using built-in security. If you expose ssh over the internet, use keys instead of passwords.

  > **baguahsing2 said:**
> I have a hardware firewall on my router and a software firewall my pc, laptop, and tablet.
Many consumer routers are linux-based, and use the same iptables as your Ubuntu system. Just another "software" firewall, though an excellent firewall if you use it properly.

  > **baguahsing2 said:**
> Do I stealth ports on the router, the pc, or both?
If you really want to stealth, do it on the router. That's all the testing website will see anyway.

> **baguahsing2 said:**
> If you want to block outgoing traffic, where is the best place to do that, hardware or software?
Why would you install applications that create undesired outbound traffic?
If  you discover an program in the Ubuntu repositories that makes network  connections outside of it's purpose, please file a bug report.


> **baguahsing2 said:**
> Some devices will not work on my wifi unless I broadcast my ssid.  Is mac id a good alternative to prevent unwanted access (I live next door to a public library).
If you like the administrative overhead, sure it can be effective.
Or you can use a key.
Or you can reduce the power from 802.11n to g or b to reduce the wifi range
Or you can use a directional antenna or reflector (a few centimeters of cardboard and aluminum foil).

  
> **baguahsing2 said:**
> is there a readers' digest version that lists ports used by Linux, windows, android, and the like?
No.
There is also no list of all the aftermarket products available for bicycles. And for the same reason - too many possible applications, and no central registry, and no need for one.


> **baguahsing2 said:**
> What are some good resources to learn about firewalls and how to configure them.
To understand firewalls, you must first understand what a port really is.
To understand ports, you must first understand what a socket really is.
To understand sockets, you must first understand pipes and file descriptors.
Once you understand what a socket and port are, what they do, and how they do it, then you will have a much better understanding of what you need your firewalls to do.

---

### Post by bashiergui on 2014-02-02
First understand why a port is needed at all. Services listen on ports and clients use random high-number ports to connect to the servers. If you aren't running any services then there's no reason any ports would be open.

I wouldn't recommend you start with writing rules to deny outbound connections. You have to keep certain ports open to function, and the ephemeral ports are tricky to configure properly. The reason to have outbound rules would be to prevent an attacker from beaconing out on some weird port. That has some value but attackers often just use common ports like 80 (http) that you can't block without making your computer useless.

No, there's no master list of ports. You have to read the documentation for each service you install to know what ports it uses. A decent general reference is here: [http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)
> I mainly surf the net, email, ps3, xbox, play lotro, Netflix thru ps3, and iTunes is about 95% of what me and my family do online, it that helps. All that sounds like the basic rules of deny all in and allow all out would suffice.

> I live next door to a public library Use a long complex password to connect to the wifi. Also use a strong password for your router, you could disable remote management of the router over wifi and require an ethernet connection. Enable the strongest encryption your router can handle, should be WPA2

---

