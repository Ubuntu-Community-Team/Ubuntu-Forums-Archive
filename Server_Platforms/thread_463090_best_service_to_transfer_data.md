---
title: "best service to transfer data"
date: 2007-06-03
forum: Server Platforms
---

### Post by rziraschi on 2007-06-03
Hello all,
I am relatively new to linux so please forgive the length of this post. I want to create a dedicated backup server preferably a linux box. I would like to use ubuntu server 6.06.

Here is my network layout.. 3 windows xp desktops running through a linksys router. 2 workstations are hardwired one is a wireless laptop. 

I have a windows xp pro box (hardwired to linksys router) that i am currently using to store about 40gig of backed up data (mp3, movie files etc) from our 3  destops. The data is backed up on an NTFS partition.

I built an ubuntu server using the ubuntu 6.06 server iso. I was able to install Samba on it and I could then connect to it from the windows workstations. I built the ubuntu server using the default file system (ext 3 I believe it was)

I tried a small data transfer of 1.3gig and it took over 2hrs to copy over. I put another hd in the ubuntu box, installed windows 2000 server and the same data took 50 minutes to transfer. I figured this is normal going native from NTFS to NTFS..

I then installed  another hard drive in the same ubuntu box and setup the box as a freenas server, enabled rsync service and using a program called Deltacopy from a windows box, it took 1.5hrs to transform the same data. When I tried to transfer using CIFS (samba service) it again took over 2 hours to transfer the same data.

My question is this... I would like to have the backup server running lnux but I need to at least come close to the transfer rate of going from xp to a windows server. Can anyone recommend what i  may have overlooked that would cause such a delay in the data transfer to a non windows partition? 

I know there must be some way to match the data transfer speed of ntfs to ntfs, when I was working as a system admin at a bank, we used network appliance boxes running CIFS services and there was no change in the data transfer speeds. (Yes, I know I am using non enterprise hardware at home, but in theory it should be something I can accomplish.) 

Most posts I see on the ubuntu forums state that Samba is either impossible to install and configure.(I find this hard to believe, it is not point and click but if you try, it does work, even I got it working :)  or they complain that samba is slow. 

Thank you in advance for any input you have.

Regards,
Ron

---

### Post by kidders on 2007-06-04
Hi there,

The source and destination filesystems make absolutely no difference (at least not in the way you think they do) over a network, since they are both interfaced by whatever filesharing protocol you happen to be using. Your problem is probably a network performance issue ... it would be worth looking over your Samba configuration for any corrections or optimisations you might be able to make. Samba+Linux should be well able to match (or outdo) Win2k's performance.

In general terms however, Windows filesharing is quite a slow way of exchanging data. If all you want is to back up large volumes of stuff quickly, something with a little less overhead might be worth looking into. Of course, there's no harm in tweaking your Linux box's networking & Samba config to try to get as much speed out of them as you can!

---

### Post by trak87 on 2007-06-04
Even 1.3 gig in 50 minutes is extraordinarily slow. Sounds like an old fashioned 10 mb network or a setting is wrong somewhere. I had similar slowness with moving files from Windows to Linux via ssh in the past. Darned if I can remember what fixed it.

---

### Post by kidders on 2007-06-04
> **trak87 said:**
> Even 1.3 gig in 50 minutes is extraordinarily slow. Sounds like an old fashioned 10 mb network or a setting is wrong somewhere. I had similar slowness with moving files from Windows to Linux via ssh in the past. Darned if I can remember what fixed it.

Perhaps you fiddled with your buffering or something? SSH tunnels will (obviously) be a whole lot slower than Samba, but you're right ... 50 minutes is disastrously slow ... I seem to be able to copy 1.3GiB in about 1:45 with scp!

---

### Post by rziraschi on 2007-06-07
Hello Kidders and Trak87,
I agree that the transfer rate is very slow. All nics are set to 100/full but the data transfer does seem more like 10mb speed. 
As per your comments, what would you use to transfer the data? (I know scp was mentioned).

I have an ubuntu 7.04 desktop up and running (to poke around with) and I went into system>admin>network tools and I noticed that next to network speed, there was no speed shown (blank space) Is this something that I need to set from a terminal?
Again I appologize for all the questions. This is new to me and i will learn it. I am googling how to set nic speed now.

Thanks again for your help.
Regards,
Ron

---

### Post by kidders on 2007-06-07
Hey again,

> **rziraschi said:**
> As per your comments, what would you use to transfer the data? (I know scp was mentioned).That very much depends on your environment, and what you think you might like to do in the future. Some choices include ... (I've tried to add a "pro" and a "con" for each one, without getting too long-winded) ...

[LIST]
[*]ATA over Ethernet - File*system* (ie not file) sharing for extremely large data volumes on very fast networks. Very low overhead. Not routable.
[*]FTP - Again, suitable for very large data volumes. Low overhead. Not for use on untrusted networks.
[*]HTTP, WebDAV - Platform independent & very easy to wrap in SSL on an "as required" basis. Reflects advanced filesystem features poorly.
[*]NFS, AFP, Samba - Run-of-the-mill filesharing protocols. Familiar & feature-rich, but relatively high overhead. Not safe for use in untrusted environments.
[/LIST]Of course, you can wrap almost all of these in SSH tunnels or SSL (making them more computationally intensive) to secure them.

> **rziraschi said:**
> I noticed that next to network speed, there was no speed shownYou can find out how fast your network card is operating with commands like **ethtool** (assuming you have it installed). Example...
```
$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        **Speed: 100Mb/s**
        **Duplex: Full**
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes
```
Linux *should* select the maximum possible speed supported by your network link automatically. If it doesn't appear to, you may have a problem with a switch/hub/cable/etc. If your network is being slow for no apparent reason, you might also like to take a look at things like **iftop** (sort of like top for network interfaces), **wireshark** (also called ethereal), **tcpdump** (basically a text-based version of wireshark), etc. There are lots and lots of networking problems these won't help you detect though.

I hope that's of some help.

---

