---
title: "Linux as a firewall - where to start"
date: 2010-08-26
forum: Security
---

### Post by chrisbay90 on 2010-08-26
Hi,
 
I work at a PC repairs shop and we recently had a malware infested machine use our network to send large volumes of spam. We have plugged up that hole but are looking to segment off our repairs network as securly as we can.
 
The lan is now in two subnets (only by use of VLANS, not physically) one for repair machines and one for everything else. With the linux server (octopus) on both.
 
The plan is to have two network adapters on octopus, one for either network. Octopus should be the default gateway for the repairs LAN, with no other route out. Install squid on it to cache all the downloads/updates/drivers always needed in the repairs area. And to use octopus as an inbetween. The repairs machines do need access to a select amount of resources (mostly file shares) on the normal LAN, and some net access (probably nothing outside of squid)
 
What tools should i be looking at to acheive this. Basically blacklist all trafic from the repairs lan but allow SOME traffice to certain resources on the lan.
 
```

         {nastie sick computers}
                   |
              -------------
              |REPAIRS LAN|
              | 10.1.1.x  |
              -------------
                   | 
                   |
               [OCTOPUS]
                   |
                   |
              -----------
              |SAFE LAN |
              |10.1.69.x|
              -----------
                   |
                   |
{Demo PC's, Internet Gateway, fileshares, Important resources}
                   |
{The interwebs, ubuntuforums.org}

```
A crude network diagram incase my description was lacking.

---

### Post by cariboo on 2010-08-26
I know this doesn't answer your question but, personally, I don't connect a customer computer to the network unless I know it is clean. I always install anti-malware programs via a usb thumb drive and scan it, before a network cable even gets near it. If the system is unclean-able using the regular tools, I resort to up-to-date live CD virus scanners. There is a list available [here]("http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/").

I use CDR/Ws as the Live CDs are updated quite often.

---

### Post by TNT1 on 2010-08-26
I'd use a simple box as a gateway to your lan. Something running SELinux, but with an easy GUI, maybe a Fedora distro. That will give you all the options you need.

---

### Post by TwoEars on 2010-08-26
All tools, taking into account you already have this server(I think) setup with Linux installed, I suggest you look into iptables. This will allow you to do what you want, fairly easily.

---

### Post by cariboo on 2010-08-26
Have a look at arno's ipttables firewall, it's in the repositories. I used it when I had a separate subnet in my shop. It's a pretty comprehensive script, and it is well commented.

---

### Post by chrisbay90 on 2010-08-28
Thanks guys. That should be enough to get me started.

I'll look into iptables or arno's ipttables firewall if i need a hand.

---

