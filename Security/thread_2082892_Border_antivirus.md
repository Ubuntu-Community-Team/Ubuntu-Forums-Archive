---
title: "Border antivirus"
date: 2012-11-10
forum: Security
---

### Post by inspiteofmyself on 2012-11-10
I am curious because I know some Debian-based commercial products like Untangle offer border-based antivirus protection. I would not mind if I only got detection for that matter...

I am not opposed to running a full web-based firewall suite, provided it will run under Ubuntu and not "be" the operating system so to speak.

---

### Post by LordXandor on 2012-11-10
Do you have an objection with an client-side firewall?

[Firestarter Howto]("http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/")

And as far as anti-virus. There are not too many viruses for linux, in general I feel it's not a huge concern as it is extremely unlikely to get a virus (the majority of viruses are designed for Windows and cannot affect linux).
But just in case it is a concern for you:
[Top 5 Anti-viruses]("http://opensource-sidh.blogspot.com/2011/10/top-5-anti-virus-for-ubuntu-free.html")

---

### Post by cariboo on 2012-11-10
> **LordXandor said:**
> Do you have an objection with an client-side firewall?

[Firestarter Howto]("http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/")

And as far as anti-virus. There are not too many viruses for linux, in general I feel it's not a huge concern as it is extremely unlikely to get a virus (the majority of viruses are designed for Windows and cannot affect linux).
But just in case it is a concern for you:
[Top 5 Anti-viruses]("http://opensource-sidh.blogspot.com/2011/10/top-5-anti-virus-for-ubuntu-free.html")

Please don't recommend Firestarter, as it hasn't been updated except for a few bug fixes, in several years. Using firestarter itself isn't much of a problem, but if you use it to monitor incoming connections, it has to be run with escalated privileges, which may lead to security problems.

I'd much rather see the op use ufw/gufw to set up the firewall. In most cases, the default rules are enough for a standard desktop system. You can start the firewall (iptables/netfilter) using the following commands, In a gui, press Alt-F2 and type:

```
gksu ufw enable
```

or from the command line:

```
sudo ufw enable
```

As far as an anti-virus program is concerned, if you aren't sharing files with Windows or Mac systems, there really isn't a need for it, as there aren't, as stated previously any Linux viruses in the wild.

A much bigger problem in my eyes, is social engineering, and the only thing to prevent that is education, so spend some time learning the differences between the previous operating system you used and Ubuntu, and remember that most of what you know about your previous operating won't transfer to Ubuntu or any other Linux distribution.

---

### Post by inspiteofmyself on 2012-11-10
i am more interested in virus detection and blocking at the border (my linux server). i know i can install snort with an inline addon for clamav to handle virus activity. looking for something similar if there is anything else.

inside of our home network are multiple windows machines for the wife, kids, etc... they all have antivirus installed, but wouldnt it be nice to stop them before they ever entered our network? :)

---

### Post by offgridguy on 2012-11-10
> **inspiteofmyself said:**
> 

inside of our home network are multiple windows machines for the wife, kids, etc... they all have antivirus installed, but wouldnt it be nice to stop them before they ever entered our network? :)

I am curious, is this even possible?

---

### Post by LordXandor on 2012-11-10
Theoretically speaking a custom route or hub might be able to do this.

---

### Post by Ms. Daisy on 2012-11-10
Beyond snort I don't know how you'd accomplish that without having a  dedicated machine to filter incoming traffic.   I suppose you could  create a series of virtual machines on one dedicated machine (or maybe  even on your linux server if it's beefy enough) to run all the  individual Tangle appliances. No idea how that would work in terms of  bandwidth and unacceptable delays to users.

Other options: you  could have the linux server function as a proxy for all web traffic on  the windows machines. You could apply rules & blacklist/whitelist  websites- use dansguardian or something similar. It's not what you're  asking for but I guess it's kind of an alternative.

---

### Post by inspiteofmyself on 2012-11-11
i am really just somewhat interested in what untangle does with their products. they are able to offer border-antivirus on some relatively meager hardware. my linux server acts as little more than a router/firewall, and its a quad core machine with 6gigs of ram... pretty sure it would be up to the task of packet filtering.

---

### Post by OpSecShellshock on 2012-11-11
With any in-line IPS there is a greater chance of false positives disrupting legitimate/intended activity than there is of threats being prevented. And with AV solutions of any kind it's important to keep in mind that all it's doing is matching against signatures based on known malware, which is always pretty far behind the malware itself. I wouldn't personally trust any vendor making the claim that they can stop malware at the premise of the network, especially if they make the claim without demonstrating it. Malware is more of a local system problem than a network problem. Until it runs on a target machine it's just a file. It's easy to make files appear harmless right up until the moment they actually do their damage.

---

