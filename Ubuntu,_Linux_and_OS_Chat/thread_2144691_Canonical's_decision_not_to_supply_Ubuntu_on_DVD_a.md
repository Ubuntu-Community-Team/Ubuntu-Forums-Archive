---
title: "Canonical's decision not to supply Ubuntu on DVD anymore"
date: 2013-05-13
forum: Ubuntu, Linux and OS Chat
---

### Post by tonybsa on 2013-05-13
Over the last 6  years I have worked as a VSA (Volunteer Services Abroad) volunteer from New Zealand in developing countries, helping with setting up small networks and tutoring people on the use of software.
I  have recently installed Ubuntu & LibreOffice in Tonga for the ministry of tourism and New Ireland (PNG) for the Community Development division of the Provincial Administration.
In both cases I have installed small LANs with a Ubuntu Server (12.04) and approximately 70 desktop & laptop PC running Ubuntu 11.10.
I have been able to do this as I could "purchase" the systems on DVD and install the OS on all machines from DVDS.
The reason to use DVDs is the lack of internet connections. Oh we do have one, but to download Ubuntu 13.04 will take approximately 4 DAYS!. That is if the ISP stays operational for that time and if the PNG power company manage to generate power for longer that a few hours.
The situation was or is the same in Tonga.
Now I am a great advocate of Open source software, especially in developing countries that do not have access to computer shops or internet.
The Community Development had 4 desktop PCs and several laptops, with a variety of unlicensed Microsoft OSs (XP, Vista, Windows 7). They were running variations of Microsoft Office (2003, 2007 &  2010). There was not a central server.
My task was to install a server and LAN, plus design a database for the division to maintain a complex pension scheme.

How am I to "update" the systems?

Bring back the DVDs :)

Don't forget more than half the worlds population does NOT have internet access!

Tony Bray

---

### Post by Lars Noodén on 2013-05-13
One option, which might not fit here because it still requires some connectivity, would be to set up a local mirror repository.  The local machines on the same LAN could then point to that repository instead of Ubuntu's.  That might work if you can have it try to update at night and on weekends when no one is around but the net is still available.  You can do that with rsync, which will minimize the downloads.  But there is still the issue of initial population of the repository.

[https://help.ubuntu.com/community/Rsyncmirror](https://help.ubuntu.com/community/Rsyncmirror)

It would take a little extra setup to make it recover from power failures, but it can be done.  

There is also APT-on-CD which is a smaller solution:

[https://wiki.ubuntu.com/APTonCD](https://wiki.ubuntu.com/APTonCD)

---

### Post by 3rdalbum on 2013-05-13
You can still buy Ubuntu on DVD or even on USB. It's just that Canonical only sells 12.04. If you want a later version, try eBay.

---

### Post by ibjsb4 on 2013-05-13
You could get the entire software repository on dvd.

[http://www.osdisc.com/products/linux/ubuntu/ubuntu-1304-software-repository-pc.html](http://www.osdisc.com/products/linux/ubuntu/ubuntu-1304-software-repository-pc.html)

But wouldn't you be better off with 12.04 and five years of support?

---

### Post by mastablasta on 2013-05-13
> **ibjsb4 said:**
> But wouldn't you be better off with 12.04 and five years of support?

i don't think connecting to internet in search of repositories is the issue here... ;-) very slow internet, power supply problematic... 

though probably 12.04 desktop is more polished than 11.10.

> **tonybsa said:**
> Don't forget more than half the worlds population does NOT have internet access!


so, they went from CD dispenser maschines in rural africa countryside, to shipping for free, to not shipping at all. Ubuntu? no not really.

not all is lost though. there are some places/shops selling the DVD. there are also other Ubuntu based distros that sell DVDs (e.g. Linux mint: [http://www.linuxmint.com/store.php](http://www.linuxmint.com/store.php)). finally you could have someone download it on a USB stick for you and send it to you.


curious though why you went with Ubutnu and not with Kubuntu desktop. surely it would have been more familiar to Windows users. oh well...

i think another issue in these countries is if they do have internet that it is slow (especially on these islands) and then the updates are quite big for those connecitons. i don't think Debian stable updates are as big. maybe that's why Debian got on ISS :-P debian's updates also don't mess up the sound, GPU  and mouse drivers or time  as they did in my case. standard is dropping...

---

### Post by grahammechanical on 2013-05-14
Ah, I see your problem. No one sells blank re-writeable DVD disks! Computers only have DVD reader drives that cannot copy a DVD. 

[http://www.webupd8.org/2011/03/ubuntu-live-cd-will-let-you-upgrade-to.html](http://www.webupd8.org/2011/03/ubuntu-live-cd-will-let-you-upgrade-to.html)

I expect that the provincial administration is spending all its money on sea defences due to rising sea levels caused by Global warming. I bet that there are those in the provincial administration with broadband Internet connection. 

At least with Ubuntu they will not be using pirated software. And we can set update notification to Never. With such a problematic Internet connection risk of malware infection would be reduced due to the malware not being fully downloaded by the time the mains power goes off.

---

### Post by cariboo on 2013-05-14
DVD's are still available to Loco Teams, so that may be the way to get the disks, usually you have to pay the shipping, but otherwise the disks themselves are free.

---

### Post by mamamia88 on 2013-05-14
Um buy a dvd from another source?   5 bucks or so is dirt cheap for installing on a crap load of pcs like you. [http://www.osdisc.com/products/linux/ubuntu](http://www.osdisc.com/products/linux/ubuntu)

---

### Post by andrew.46 on 2013-05-18
I had almost forgotten about the *CDs* from shipit.com, gave Ubuntu a decent legup in the old days :)

---

### Post by Perfect Storm on 2013-05-18
Properly if people didn't shipit ridicules amount of CDs/DVDs when they only needed 1 or a couple to give away or started donating in the past. We won't have this problem.

---

### Post by prusswan on 2013-05-18
Local institutions should be the ones responsible for physical distribution, which was never cheap in the first place.

---

