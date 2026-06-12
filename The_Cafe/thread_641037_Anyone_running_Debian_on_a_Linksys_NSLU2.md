---
title: "Anyone running Debian on a Linksys NSLU2?"
date: 2007-12-14
forum: The Cafe
---

### Post by 23meg on 2007-12-14
The [NSLU2]("http://en.wikipedia.org/wiki/NSLU2") is a NAS (network attached storage) interface for USB disks. It's actually a minuscule computer that runs on an ARM-compatible 266MHz Intel processor, and has 32MB of RAM. 

The nice thing is: it can do way more than make disks available on a network, because [it can run Debian]("http://www.nslu2-linux.org/"). Since it has very low power consumption and is fanless, it's optimal for tasks that require little computing power, but need the computer to be on all the time. 

It's cheap, so I'm planning to get at least one, to use as a web server and torrent machine. Anyone with experiences to share?

---

### Post by 23meg on 2007-12-18
Nobody?

---

### Post by smartboyathome on 2007-12-18
I had never heard about that before, but this could definately help me since my server died recently and I am having to use my friend's server for now. :)

---

### Post by dreyergustav on 2007-12-18
I have a slug running Debian Etch and are very pleased with it. I'm using it to to share files using NFS and Samba. As you said it doesn't use much power (I think about 5 watt) which is nice when you live in Denmark where electricity is very expensive :).

If you are thinking about getting one I would recommend that you run your root file system and swap off a flash drive and keep larger files on an attached hard drive. This way the hard drive will only be active when you need the files.

---

### Post by smartboyathome on 2007-12-18
> **dreyergustav said:**
> If you are thinking about getting one I would recommend that you run your root file system and swap off a flash drive and keep larger files on an attached hard drive. This way the hard drive will only be active when you need the files.

That I can already do, since I have a spare one I can use.

---

### Post by armalite on 2007-12-21
Me too I have a NSLU2 with debian stable (etch?), I tried some things with this little "pc". :) 

I have bought it last summer to test it, my idea was to set a backup box in case the primary home server goes offline for whatever reason. I used until october 2007, after that i gone busy with other projects and had no time to give to my little nslu2.

So I installed in there apache, php, lighttpd, mysql, dhcpd, radius, courier suite, openvpn, powerdns and heartbeat. 

From my experience with nlsu2 i can say this:
- heartbeat v2 isn't well supported, at least until version 2.0.7 (the last i tried). It caused memory leaks and put the slug to overload till no usability. I had to use only heartbeat v1. Maybe with hb 2.1.x problems could be resolved, i don't know;

- mysql is very slow, it really can't be used apart simple (very simple) queries; 

- that said, a Joomla website over apache+mysql+php takes forever to load a page. If you put static pages, it works quite well given the cpu power. I installed some php accelerators but no change in speed. This let me think that mysql is the bottleneck in this setup;

- lighttpd is really faster than apache on nslu2, so if you have to use a web server, lighttpd should be your preferred choice;

- courier smtp/pop/imap works good, and it has also a web frontend. nslu2 as a little mail server is a nice thing;

- speed transfer via ftp/samba/scp isn't very speedy on nslu2. Expect to have 2000Kbytes/s;

- dhcp, freeradius and also powerdns (with mysql backend, which is weird, i know) work good, at least in little environments like could be a "normal" home;

- LVM, raid works out of the box, and so reiserfs. However, be aware not to use chmod/chgrp/chown on large directories because it will overload the nslu2 till manual reboot. You can attach as many disks as you want, in /etc/fstab use UUID to let partitions be recognized correctly;

- I bought also a little usb phidget to watchdog (read: reboot) the dlink router when it hangs and i wrote a little c code. I used the original phidget libraries and  it worked as intended.

Anyway I'm satisfied with what the nslu2 can do. Since it is ARM based, don't expect to have every application found on i386 (i miss ebox for nslu2!).

Power consumption is really low, maybe a Soekris board suits best some network needs, but AFAIK nslu2 setup is way easier than soekris board.

---

### Post by AndyCooll on 2007-12-21
I recently bought one of these with the intention of installing Debian on it. Unfortunately a Debian kernel update broke the NSLU2 Debian Installer, and at the time it didn't seem as if this had been fixed. 

And I haven't had the time to attempt to manual install Debian. So mine is still sitting around at the moment doing very little. However as a result of this thread perhaps I'll have another go over the Christmas break.

:cool:

---

### Post by AndyCooll on 2007-12-29
It seems the new Debian installer is available. 

So I've downloaded it and tried flashing my slug with it. However I'm not getting very far. I've tried this using both the original Linksys web app and Upslug2) . It seems to work, no errors are reported. It then reboots, I attach my USB HDD ...and wait ...and wait ...a couple of hours etc

It goes no further, I'm left with an orange "Ready/Status" light, a green "Ethernet" light, and no lights against the disks. And when I try SSH'ing into it I get the error message "ssh: connect to host 192.168.0.3 port 22: No route to host". 192.168.0.3 is the static IP address I gave it. And it hasn't got the default IP address because that doesn't report back anything at all.

I know it's possible for these methods to work, I've successfully used both of them to upgrade the original firmware.

So where am I going wrong? What else might I try doing to get Debian on it? I'm thinking I might have to try manually installing Debian on it, however before I resort to that I thought I should seek some ideas from you lot first.

:cool:

---

### Post by popch on 2007-12-29
> **AndyCooll said:**
> I(...) when I try SSH'ing into it I get the error message "ssh: connect to host 192.168.0.3 port 22: No route to host". 192.168.0.3 is the static IP address I gave it. And it hasn't got the default IP address because that doesn't report back anything at all.

The message 'no route to host' seems to indicate that your slug is not on the same subnet as your PC. Since your slug is at 192.168.0.3, your PC should have an IP adress like 192.168.0.n, where 0 < n < 255.

---

### Post by AndyCooll on 2007-12-29
> **popch said:**
> The message 'no route to host' seems to indicate that your slug is not on the same subnet as your PC. Since your slug is at 192.168.0.3, your PC should have an IP adress like 192.168.0.n, where 0 < n < 255.

Thanks for your reply. I can confirm that in actual fact all my pc's are on the 192.168.0.x/255.255.255.0 subnet.

:cool:

---

### Post by gn2 on 2007-12-29
> **AndyCooll said:**
> I get the error message "ssh: connect to host 192.168.0.3 port 22: No route to host". 192.168.0.3 is the static IP address I gave it. And it hasn't got the default IP address because that doesn't report back anything at all.

Have you tried 192.168.1.77 ?

---

### Post by IgnacioMiller on 2007-12-29
I run Debian on my NSLU2!!!

---

### Post by popch on 2007-12-30
Try the following commands

***ping 192.168.0.3***

Should tell you if your slug is there and responding. Press control-c when you have received several replies.

***arp***

This takes a while to respond (several seconds until first reaction). When entered without any arguments it should answer the IP and MAC addresses of all devices connected to your LAN segment.

***route***

Displays the routing table. Since ssh says that there was no route to the slug, it seems worthwile to check this one.

---

### Post by xoai on 2007-12-30
I set up Debian, nginx, PHP and MySQL on a  VPS and the whole system just takes around 22-28mb memory. I think nginx is better than Apache and Lighttpd in this case. I am going to buy a NSLU2. It's really impressed

---

### Post by AndyCooll on 2007-12-30
Thanks guys for your replies. Here are my results:
```
root@snoopy:~/share/software/nslu2# ping 192.168.0.3
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Host Unreachable
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable
From 192.168.0.2 icmp_seq=5 Destination Host Unreachable
From 192.168.0.2 icmp_seq=6 Destination Host Unreachable
From 192.168.0.2 icmp_seq=7 Destination Host Unreachable
From 192.168.0.2 icmp_seq=9 Destination Host Unreachable
From 192.168.0.2 icmp_seq=10 Destination Host Unreachable
From 192.168.0.2 icmp_seq=11 Destination Host Unreachable

--- 192.168.0.3 ping statistics ---
12 packets transmitted, 0 received, +9 errors, 100% packet loss, time 11009ms
, pipe 3
root@snoopy:~/share/software/nslu2# arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.3                      (incomplete)                              eth0
192.168.0.1              ether   00:11:50:4E:31:6A   C                     eth0
root@snoopy:~/share/software/nslu2# route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

```

As I mentioned I can flash the nslu2 with the original Linksys firmware and within minutes its working fine again. I can then type 192.168.0.3 in to a web-browser and everythings works. I just can't seem to get it up and running with Debian ...

:confused:

PS. I seem to hit the same block with a manual install. AFAI I'm following Martin Michlmayr's original instructions. In effect I'm using Upslug2 and doing the same type of flash process for Debian that I do when installing the original Linksys firmware. Am I missing something obvious?

---

### Post by popch on 2007-12-30
From the results above you can clearly see that there is no response from 192.168.0.3. You can also see that there has not recently been any device on the LAN using that address.

In short: the slug does not think it has the address 192.168.0.3. I have no idea what address it might have when running Debian.

Perhaps you should consult the documentation which you used for installing Debian on your slug. On the other hand, you could use an IP scanner and have it search for the slug's address.

Sorry, I can not recommend an IP scan program as I have no experience in using one of those. The last time I needed that done, I had my son do it for me on his Windows box, because that was much faster.:)

---

### Post by gn2 on 2007-12-30
Have you looked here: [http://www.nslu2-linux.org/wiki/Debian/TroubleShooting](http://www.nslu2-linux.org/wiki/Debian/TroubleShooting) ?

---

### Post by AndyCooll on 2007-12-30
Yay!!! Finally got the little blighter working.

Not really sure why it suddenly started working.. I re-read the Troubleshooting FAQ (thanks gn2, yes I'd read it, but I read it again anyway). In the default Linksys config I already had IP address, netmask, default gateway etc set up. I added the DNS Server too. I then tried (yet again) the manual configuration and yet again it failed. So I gave it one last try with the new Debian installer. And this time I had an SSH connection!

The install then went smoothly and I can now connect to it fine.

One minor thing. It's working fine, but blinking orange/green all the time. Is this correct?

:cool:

---

### Post by 23meg on 2008-01-16
Thanks everyone for your replies. I'm probably buying two. 

Does anyone have experience with running rtorrent or Transmission (CLI version) on it? I wonder if they'll perform reliably.

---

### Post by macogw on 2008-01-16
At LUG today a guy was talking about Asterisk.  He said NSLU2's are actually pretty crappy when it comes to serving the "network storage" purpose, but they're great to use as your Asterisk server, once you flash them with OpenWRT.

---

### Post by AndyCooll on 2008-01-17
> **23meg said:**
> Thanks everyone for your replies. I'm probably buying two. 

Does anyone have experience with running rtorrent or Transmission (CLI version) on it? I wonder if they'll perform reliably.

I'm running rTorrent (and Screen) on mine. It installed no problem (as you'd expect) and seems to run fine. As far as I can tell I get the same sort of download rates that I was getting when using Azureus or Deluge.

:cool:

---

### Post by N6546R on 2008-02-27
Thought I'd check in on this one, I'm also running a Slug with Etch. It has tow medium-sized hard drives (300G) attached, and I use it to do remote backups with rsync-based scripts of a few of my websites. transfer rate is a bit slow, as has been mentioned, but I'm not looking for speed, just something cheap and quiet to suck down files every night.

For a while it was running unSlung and serving up music to several Netgear MP101 wireless music boxes, using the Twonkyvision media server. I've since moved Twonky to a different box due to some performance issues with the Slug. 

I've had the thing for a couple of years now and it's always been a treat to work on.

Perry
[www.kidpub.com](www.kidpub.com)

---

### Post by armalite on 2008-02-28
I'm in the way of fattening the ram on NSLU2. Too bad it will take a lot of time since I had to ask a local electronic store to unsolder the memory chips from an old PC133 SODIMM of mine. Unfortunately, it will take some weeks because they're too busy.
Anyway, they asked a little too much to piggyback solder the memory on NSLU2, so i'll try to do it myself, one way or another. :)
I'll hope that with 64Mb, nslu2 will no more panic on heartbeat v2.

In the meanwhile I upgraded to Debian Sid, kernel seems stable but pay attention to ethernet driver that doesn't get loaded at boot on kernels <2.6.24-4, you have to load it manually.

---

### Post by discontentment68 on 2008-03-09
I'm running rtorrent with dtach on mine and it seems fine with only a few torrents.  I also run vsftpd with ssl and it runs just as expected.  This is all without de-underclocking the device.  I love this thing.  5 watts of love.
It is problematic to attempt to compile anything on the slug.  I had attempted to get rtorrent with scgi interface but the compiling was taking more than two days.  ... anyone had any luck cross compiling for it?

---

### Post by armalite on 2008-03-10
I never found a complete (and relatively easy) howto on crosscompile. The ones i found were always too vague, things like "install the target toolchain" is a little cryptic to me on how to do that.

Last time I had to compile for NSLU2 i did the following: I installed Debian ARM on Qemu on my pc and compiled the package in it... not the best solution, i think.

---

### Post by anjelika on 2008-03-11
Hello,
Anyone can confirm that running mysql on this device is not a good ideea?
I was interested in purchasing one in the near future but was looking to use it primary as a web server (apache, lighthttpd, maybe something even lighter) , a subversion server and a database server (not for production use, only development).
If Mysql is too heavy for this, then maybe Sqlite?
Anyone got any experiences with that configuration or what are you guys using this device for?
Thanks

---

### Post by faheyd on 2008-04-17
> **anjelika said:**
> Hello,
Anyone can confirm that running mysql on this device is not a good ideea?
I was interested in purchasing one in the near future but was looking to use it primary as a web server (apache, lighthttpd, maybe something even lighter) , a subversion server and a database server (not for production use, only development).
If Mysql is too heavy for this, then maybe Sqlite?
Anyone got any experiences with that configuration or what are you guys using this device for?
Thanks

I'm running sqlite3, mt-daapd, samba, on a 500GB ext usb drive with a 18GB debian root partition with 512mb tmp, and a 512mb swap partition (I use the rest of the drive for a media partition).
I also loaded up webmin to make things easier.  I'm still finding things to do with it as I've only had it for 2 weeks.

---

### Post by CADutch on 2008-11-14
Try this... I have not tried this myself, but it seems to work for this guy.

[http://www.cyrius.com/debian/nslu2/install.html](http://www.cyrius.com/debian/nslu2/install.html)

---

### Post by saarakura on 2009-04-03
people, i need a help... how can i see the temperature of processor ?

---

