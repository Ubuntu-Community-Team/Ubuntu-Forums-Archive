---
title: "Low Power Home Server - full solution"
date: 2010-03-01
forum: Server Platforms
---

### Post by steev182 on 2010-03-01
I've been running my Dell SC440 as a home server/workstation for about a year now and whilst it can cope with both roles, it is power hungry, loud and does get a little slow down sometimes. What I am looking to do is create a home server to take away the need of it to be on 24x7.

My requirements in a home server would include:

- Media Server (using TwonkyMedia or uShare)
- NZB Downloader (hellaNZB or sabNZB)
- AFP + NFS file serving
- rsync/unison for Linux backups and N900 media sync and backup
- Email/Calendar/Contacts hosting and sync (zimbra or zarafa?)

I would like to achieve this with an Acer Revo and a couple of 1 or 1.5TB external hard disks, I'm unsure if the Atom processor would be strong enough for all of these services, although I could test it using my netbook, if that can cope, the Revo would be able to easily.

Has anyone done something like this?

---

### Post by matchett808 on 2010-03-01
well i am currently running rtorrent, ushare, ssh, cups and vsftpd from a 630mhz EEE pc, so I reckon It would easily handle most of it....
....word of the wise, I have email and file sync hooked up through the ftp server (and its ran from a script on my local machine) although this isn't what you are looking for it may provide another idea (its kinda slow, about 3-4mbp/s on wireless N from a new 64bit dual core laptop thingmy.....my server is under powered but a revo has a clear gig over mine....)


Also...my server is running a gui desktop version of ubuntu and I have a number of extra (small) programmes running (like one that checks a site once/second...)

---

### Post by solitaire on 2010-03-01
i'm running an intel 330 ATOM ION board and that only pulls in 55w with a Sata and IDE drive.
it's just a XBMC media center for now, but it should be more than enough to run the serivces you require. 

Make sure you get a Dual Core it's worth the extra few $
If you get a Atom Motherboard then fit it with a micro PSU, it's then virtually silent.

---

### Post by windependence on 2010-03-01
The atom would be my recommendation also, however, Zimbra wants it's own box. I have not tried VMware ESXi on the atom, but that could be a solution to that problem also, however, you are limited to 2 GB RAM so no GUI here.

-Tim

---

### Post by tgalati4 on 2010-03-01
plugcomputer.org

---

### Post by oldfred on 2010-03-01
See these links:

Server with extras
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

Thread on servers
[http://ubuntuforums.org/archive/index.php/t-1286445.html](http://ubuntuforums.org/archive/index.php/t-1286445.html)
See this post for an interesting low power version: I use/sold a lot of linux home servers

---

### Post by solitaire on 2010-03-01
Most ATOM Motherboards handle 4Gb of RAM (well my ZOTAC board does, well it can handle 2x4Gb sticks in dual channel mode)

---

### Post by DesG on 2010-03-01
I find your opening post strange!

I have a SC440 with a Quad Core cpu and 8GB ram with a couple of TB drives, and it runs at 72W at idle, its so quiet, I can't tell if its still on if I visit it.

Mine is running VMWare Server with lots of VM's, performance is blistering.

What cpu and ram do you have in your SC440, also have you done any tuning of the fans, iirc the default install of Ubuntu had the fans going full tilt, which is noisy, but after 5 minutes adjusting the fans etc, it was whisper quiet.

Just giving you options :)

Cheers, Des.

---

### Post by steev182 on 2010-03-01
It isn't that quiet in my room, but maybe adding some ram could help...

---

### Post by nerr on 2010-03-01
[http://www.newegg.com/Product/Product.aspx?Item=N82E16859321013&cm_re=Acer_easyStore-_-59-321-013-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16859321013&cm_re=Acer_easyStore-_-59-321-013-_-Product)

Here's my low-power, quiet solution. :) Does the job wonderfully, that's for sure.  It runs the following services with ease:

- Samba (SMB)
- OpenSSH Server (SSH/SFTP)
- CUPS (IPP)
- NFS
- Apache2 (HTTP/HTTPS)
- Subsonic (streaming music)
- DHCP
- rtorrent
- ClamAV

These require a little more beef, but still perform admirably on the Atom:
          - Network boot Linux (pxelinux) (PXE/DCHP/TFTP)
- Virtualbox

Needless to say, I am thoroughly impressed with the Atom's excellent performance.  I would love to upgrade to a dual-core Atom, but it's simply not feasible right now, so my Atom 230 will continue to serve me for now.

---

### Post by steev182 on 2010-03-02
So you can run VMs on Atoms nerr?

---

### Post by snowpine on 2010-03-02
> **steev182 said:**
> So you can run VMs on Atoms nerr?

Yes but don't expect good performance! :)

I have Windows XP in VirtualBox on my dual core Atom 330. It is just enough that I can open the occasional file in Photoshop. But for example I cannot watch Netflix Streaming (framerate painfully low).

The Atom does *not* have KVM capabilities.

---

### Post by nerr on 2010-03-02
> **steev182 said:**
> So you can run VMs on Atoms nerr?

Believe it or not, yeah.  I have a Windows XP VM that performs fairly well for basic tasks such as web browsing, but it's more of a gimmick than anything.  I just wanted to see how well it would run, but it's useful for when I'm not on my own LAN and I'd like to adjust my router settings or test out some kind of LAN networking service.  Obviously it would run a great deal better on a stronger processor, but the Atom 230 does work surprisingly well.

---

### Post by volkswagner on 2010-03-02
> **snowpine said:**
> Yes but don't expect good performance! :)

I have Windows XP in VirtualBox on my dual core Atom 330. It is just enough that I can open the occasional file in Photoshop. But for example I cannot watch Netflix Streaming (framerate painfully low).

The Atom does *not* have KVM capabilities.

Nor will the Atom 330 run Windows inside XenServer, but Linux VMs work fine.

---

