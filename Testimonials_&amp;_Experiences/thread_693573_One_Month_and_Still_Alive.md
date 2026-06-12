---
title: "One Month and Still Alive"
date: 2008-02-11
forum: Testimonials &amp; Experiences
---

### Post by galeg on 2008-02-11
Firstly I am retired Senior IT Project Manager (retired after managing most IT departments in an Australian Bank - then moving to the departure lounge as a Senior Project Manager)

I run a desktop (originally XP now dual), and a new laptop with Vista (not sure with running Ubuntu on the laptop as Toshiba advise that they modify the bios specifically for Vista)..

Its been about 2 weeks since I built a dual boot XP box and installed Ubuntu on a secondary HDD.

At times very frustrating, with some late nights, but believe that I have a system that is quicker in many respects than XP, and as my knowledge grows, the frustrations reduce.

A few major bugbears I have are:

1. Lack of formal documentation for many applications (although I understand that many are written by people that are doing the programming in the spare time, and do not have training in documentation).

2. The confusion with forum support entries (mainly external to Ubuntu) that refer to previous versions, and do not contain dates. I have just installed uTorrent, (and Wine) and finished up with approx 6 sets of instructions from various sources, from which I picked bits and pieces to get it going (one hell of a learning experience)  during which I somehow managed to lose the Wine icon group, but what the heck, I still have the Terminal command line capability.

3. The use of Jargon. As an ex IT manager it was a full time job to train techos to reduce the amount of jargon, and apart from UNIX techos, we were reasonably successful. Now UNIX being (in my view) the commercial brother of Linux, maybe jargon goes with the territory. In my view the use of large amounts of jargon is common with techos who appear to have difficulties relating to people with lesser knowledge, and therefore make assumptions that everybody knows what they are referring too.

4. Driver support for Canon scanners (specifically D1250U2 models). Unfortunately this is a legacy problem, but it is disappointing to note that Canon openly state that they do not support Linux. Canon printers generally seem covered by outside people / groups writing drivers. (although I have not looked at trying to activate my High Definition digital TV card as yet, this may be a future challenge).

5. The need to run XP programs under Wine. I suspect that migration from XP programs is directly linked to attained skills in Linux, as I found when trying to run rTorrent, then needing to back off to uTorrent under Wine. 

6. The Ubuntu documentation. I find this document hard to follow, and believe that it would be very beneficial if a volunteer coordinator (with previous technical documentation) could be found to maintain the documentation, and build into a down loadable PDF..

In summary, I would give Ubuntu a B+ and am running about 75%+ of my day to day effort on Ubuntu. I will probably increase usage when I have confidence in backing up / recovery of the Ubuntu data files (more a procedural issue than a technical one), and have the knowledge to move away from some of the XP applications (currently running under Wine).

---

### Post by ukripper on 2008-02-11
there are plenty of ways to backup your system in linux:
Any strategy you would like can be used:

i believe you might be currently using tar backups or sbackup.

if you need more comprehensive type of backups which include incremental, cloning, system recovery there are many apps available.

accross network and incremental support - rsync (GUI version Grsync) [http://packages.ubuntu.com/edgy/net/rsync](http://packages.ubuntu.com/edgy/net/rsync)

Cloning - Clonezilla [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)
or partimage to copy partitions [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

there are many more....depends on your backuop strategy

---

### Post by armandh on 2008-02-11
can't directly help on the cannon scanner but I can tell you about my similar problem, a data products DDS-32 printer. it has been running in XP on a win 2K beta driver. data products was sold to Hitachi and disappeared. I suspected the printer would never run on Linux. but I was wrong! a fellow who knew much more than I about the printer suggested the linux generic postscript driver. WOW it worked! including duplex!  the fancy printer monitoring was absent but I got my high quality 32 ppm printing.  no need to buy a large used HP. you need to find someone who is expert in the guts of your scanner. they would know if there is a generic driver or if the software is a totally home grown cluster F.

---

### Post by hyper_ch on 2008-02-11
> **galeg said:**
> 1. Lack of formal documentation for many applications (although I understand that many are written by people that are doing the programming in the spare time, and do not have training in documentation).
What is not documented?

> **galeg said:**
> 
2. The confusion with forum support entries (mainly external to Ubuntu) that refer to previous versions, and do not contain dates. I have just installed uTorrent, (and Wine) and finished up with approx 6 sets of instructions from various sources, from which I picked bits and pieces to get it going (one hell of a learning experience)  during which I somehow managed to lose the Wine icon group, but what the heck, I still have the Terminal command line capability.
Why not running a native linux bittorrent client?

> **galeg said:**
> 
3. The use of Jargon. As an ex IT manager it was a full time job to train techos to reduce the amount of jargon, and apart from UNIX techos, we were reasonably successful. Now UNIX being (in my view) the commercial brother of Linux, maybe jargon goes with the territory. In my view the use of large amounts of jargon is common with techos who appear to have difficulties relating to people with lesser knowledge, and therefore make assumptions that everybody knows what they are referring too.
Well, if you want to make sure what the other is talking about you have to use jargon... I bet you've learned a lot of windows jargon over time. More than you might think... it's just like a new language... in the beginning it sounds all weird but with time you'll get fluent in it...

> **galeg said:**
> 
4. Driver support for Canon scanners (specifically D1250U2 models). Unfortunately this is a legacy problem, but it is disappointing to note that Canon openly state that they do not support Linux. Canon printers generally seem covered by outside people / groups writing drivers. (although I have not looked at trying to activate my High Definition digital TV card as yet, this may be a future challenge).
Not much to be done here... you could stop supporting Canon ;)

> **galeg said:**
> 
5. The need to run XP programs under Wine. I suspect that migration from XP programs is directly linked to attained skills in Linux, as I found when trying to run rTorrent, then needing to back off to uTorrent under Wine. 
For most programs there are good alternative. If you list what you need, I bet we can point out alternatives for you.

> **galeg said:**
> 
6. The Ubuntu documentation. I find this document hard to follow, and believe that it would be very beneficial if a volunteer coordinator (with previous technical documentation) could be found to maintain the documentation, and build into a down loadable PDF.. 
Which Ubuntu documentation are you talking about?

> **galeg said:**
> 
In summary, I would give Ubuntu a B+ and am running about 75%+ of my day to day effort on Ubuntu. I will probably increase usage when I have confidence in backing up / recovery of the Ubuntu data files (more a procedural issue than a technical one), and have the knowledge to move away from some of the XP applications (currently running under Wine).
Well, once you get used to it you'll have far less problems ;)

As said, when you're having problems, all it takes is to ask here in the forum.

---

### Post by hyperair on 2008-02-11
My Canon IP1000 has a driver for Linux thankfully, but it sucks big time. >< Can't even print grayscale.

Then there's the Canon scanner... D646U EX or something of that sort. No drivers. I'm annoyed at Canon. They either do a lousy job or don't do it at all.

---

### Post by ukripper on 2008-02-11
Go for Brother all in one, they mostly work

---

### Post by hyperair on 2008-02-11
Well at least now I know what to go for the next time I go shopping for printers/scanners, but they still work fine for now. So I use Virtualbox to handle my scanner, and cups-pdf to handle printing.

---

### Post by galeg on 2008-02-12
Thanks for your replies

Primarily in response to hyper_ch, some of the answers are:

1. The lack of formal documentation was primarily aimed at Sourceforge application solutions. But from memory, the disaster I had with rTorrent was partly as I was unable to locate comprehensive documentation. I suspect that some doco could be difficult for developers when they need to cater for a number of Linux distributions, each with their own requirements.

2. Native bittorrent, was an issue as I was unable to find a comparable GUI driven Linux bittorrent client. I looked at rTorrent, but with my current skill base, it was not practical. Would be happy if somebody could recommend a good GUI (as against a cmd line entry) bittorrent client for Linux, which works similar to uTorrent. Another example of one requirement I have is for synCE (to connect my IPAQ). This package looks like a minefield, with the developers stating that people should wait until somebody in Linux land builds an installation package for their brand of Linux. I bet their were a few Valium taken by people trying to get this running, without a Ubuntu package being built.

3. Agreed to a certain extent, but if you are talking to someone who is either new to the OS, or the OS is only one of a number actively dealt with (e.g. as with project management teams / change administration teams / documentation teams), then an assessment should be briefly made as to the suitability of systems jargon.

4. Unfortunately when one owns a brand of scanner, for financial reasons, they may need to hold that scanner until it leaves its mortal world for the old scanner home in the sky.

5. Noted, and I will request forum feedback in the future.

6. The documentation mentioned is available under the Ubuntu Support site. It is not searchable or have a comprehensive index that would be available under, say, a PDF. For example, where in the doco would I find the options available with the apt-get command, would the options in fact be in the doco. Most current IT doco that I have dealt with is now on line with key word search functionality, that allows for quick accurate reference. This is why I have suggested the document be made available in a PDF format (a quick way out without resorting to a formal DMS (document management system)).

Undoubtedly as skills increase, heartaches / frustrations will reduce.

---

### Post by NightwishFan on 2008-02-12
I use Deluge Bittorrent Client.

---

### Post by hyperair on 2008-02-12
#1. Don't use sourceforge.net applications unless you know what you're doing or Ubuntu's repository doesn't have it (at the version you want) already. Even then, most applications have an interface that's easy enough to figure out. 

#2. I use KTorrent. No doubt requires the installation of KDE libraries on my GNOME system, but I find it really good. CPU usage's a lil higher than Deluge's, but otherwise it's good. More features, more stable, and such.

#4. I agree with you on this, but I must say that the USB scanners can be virtualized pretty well. =) That's how I handle mine. 

#6. Try using your system's documentation as well. System->Help and Support. As for stuff like rtorrent, which are all command line, it helps to use this command: "man <program>" where <program> is rtorrent, or apt-get or anything else under the sun. You'll find that the documentation here is usually very detailed, especially for command line apps like rtorrent and apt-get.

---

### Post by hyper_ch on 2008-02-12
with regard to rtorrent: Why not using the official homepage?

[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

[http://libtorrent.rakshasa.no/rtorrent/rtorrent.1.html](http://libtorrent.rakshasa.no/rtorrent/rtorrent.1.html)

[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

[http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest)

CLI based torrent client is something you first ahve to get used to a bit (I remember I had to)... but the power of screen and rtorrent on a linux box are amazing :)

---

### Post by mivo on 2008-02-12
I'd also suggest Deluge. You can see some screenshots at the homepage:

[http://deluge-torrent.org/screenshots.php](http://deluge-torrent.org/screenshots.php)

---

### Post by hyperair on 2008-02-12
I still believe in the GUI torrent clients, even though I'm quite well versed with the command line already. Perhaps rtorrent would be useful if I didn't have an X session running, say.. an Ubuntu server installation or an Arch default installation.

---

### Post by hyper_ch on 2008-02-12
well, there are also a couple of WUIs available for rtorrent.

The screen and ncurses handling of rtorrent just makes it perfectly controlable from anywhere you can use SSH.

---

### Post by hyperair on 2008-02-12
Agree with that, but I usually do my torrent controlling via SSH+VNC. Slightly more complex, but does the job just as well. Then there's the WebUI also, which works well for controlling the torrent program. Exists for both KTorrent and Deluge.

---

### Post by HappyFeet on 2008-02-12
> 2. Native bittorrent, was an issue as I was unable to find a comparable GUI driven Linux bittorrent client. I looked at rTorrent, but with my current skill base, it was not practical. Would be happy if somebody could recommend a good GUI (as against a cmd line entry) bittorrent client for Linux, which works similar to uTorrent.

+1 for Deluge Bittorrent. [http://deluge-torrent.org/](http://deluge-torrent.org/) it's a .deb file, so just click to install. has many features of utorrent, and the ability to import peerguardian blocklists.

---

### Post by waspbr on 2008-02-13
I can relate, in my windows partition I still use utorrent, and when I started using ubuntu, I was a little disappointed at the native BT client. So I tried out Deluge and azureous. They are great but at the time they had a bug that affected me, so tried out Ktorrent and haven't looked back. The interface is quite similar to utorrent.

---

### Post by djbsteart1 on 2008-02-13
to go back to printers, my hp all in one is great. and since there is hplip nearly all of there products are supported.

---

