---
title: "Appropriate defense against port scan?"
date: 2012-11-13
forum: Security
---

### Post by Dirich on 2012-11-13
Hello, I am in need to check whether or not someone is doing a port scan of the ports of my work desktop pc (static IP, I am not one of the network admin, and we seem not to have a firewall or any kind of defense...).

What I need is just to check the requests and log them (and understand if there's a port scan going on or not).

A friend talked about snort, and I started to check a couple of related threads in here, but I am not totally sure if I am doing something disproportionate or not.

I mean, is some sort of "standard firewall" enough for my purpose (identify a portscan and identify the IP scanning me)?
Also, I kind of have a time problem, as I have to be able to register potential port scans asap, since I have reason to fear that something is going to happen in the very near future). This is why I would really like something basic and with almost no config to do, so that I can take my time studying how to do stuff properly without having to be worried to much.


EDIT: actually, I trust my friend but the more I read the more it seems like I don't need a NIDS tool...

---

### Post by Lars Noodén on 2012-11-13
A firewall won't identify attacks by itself.  It can log incoming traffic and then let you identify an attack either through manual analysis of the logs or with the help of an IDS like Snort.  You can use the firewall to block hosts that have attacked you.  

You can also use rate limiting in the firewall to slow down or cap the rate of incoming connections.  Here is one example for ICMP:

```

iptables -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

```

However, if the scan is distributed and comes from many source hosts then limiting won't help.

---

### Post by thnewguy on 2012-11-13
It might help if we knew why you want to do these things, what you are hoping to accomplish. It might also be a good idea to check if there is a firewall on your organixation's network and, if not, why. A machine on the network shouldn't be reacting to port scans, those should be stopped prior to reaching the LAN.

---

### Post by Dirich on 2012-11-14
I don't know why, but I know that it was chosen to leave the responsibility of protecting a PC to the PC user.

The situation is, I know someone did a suspicious portscan on my PC at work, and I fear he may do more than it.

Originally I wanted to be able to gather proofs against him, in case he attempted something illegal, so that I could ask help to the police. But for the time being I have no time and I'll just try to configure iptables to block him.

Thanks Lars for the iptables suggestion.

---

### Post by mikewhatever on 2012-11-14
I don't think port scanning is illeal, also, you might not even have any open ports.

---

### Post by Ms. Daisy on 2012-11-16
Is this a school wifi network? If you're on a network with a bunch of other people, then you want to run a personal firewall. People could be scanning you from inside the network and a firewall would help.   Gufw might have a simpler interface if you aren't familiar with firewalls.  Check out this tutorial.

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

The reason you would be concerned about a port scan is that someone is looking at your open ports. If you don't run any services (like ssh, vnc, ftp, blah blah), then you don't have open ports and there's not much for them to do.  I would want to make sure I had all the security updates installed in all my software & operating system if I knew I were being scanned. The less vulnerabilities the better.

---

