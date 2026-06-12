---
title: "Request OpenOffice.org2 1.9.m100"
date: 2005-05-08
forum: Ubuntu Backports
---

### Post by Gnobody on 2005-05-08
I have a request for OpenOffice.org2 1.9.m100, is there a Debianized ver. out?

---

### Post by MadMan2k on 2005-05-09
you can alienize the rpm packages as a hotfix

---

### Post by makhand on 2005-05-10
I would also like to request this. If not 2.0m100 then at least 1.1.4. In my experience, 1.1.3 has some very basic functionality bugs ( try inserting an image and then moving it around, putting text below/above it, moving it around some more, etc). I've had some real problems with it. When I went to the 2.0m79(?) one (which is in synaptic), well, it crashed my system -- though I'm not sure about that, it could be that my computer got owned at that time because I subsequently had all kinds of trouble recovering the files and then my XP, which shares some of the same files basically deleted the entire directory (which i was very angry about).  ](*,)  ](*,)

---

### Post by jdong on 2005-05-11
Openoffice is always a beast to compile -- I want to see Sid or Breezy to try to get it to compile before I waste my time doing so.

I've spent at least 48 hours before trying to backport Openoffice, and gave up.

---

### Post by gugus on 2005-05-22
There is a debian version here, included all localized packages:
[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)

---

### Post by jdong on 2005-05-22
I have started to offer torrents of large packages not worthy of being in the Backports repos.


One of these packages is Openoffice.org2 (currently m104), which is converted using the script at [http://www.piai.it/Alberto/doc/ooo-debianize-en.html](http://www.piai.it/Alberto/doc/ooo-debianize-en.html)

You can find the torrents at [http://backports.ubuntuforums.org/ubp/torrents/](http://backports.ubuntuforums.org/ubp/torrents/) or from the tracker at [http://backports.ubuntuforums.org:6969/](http://backports.ubuntuforums.org:6969/)


Please **uninstall ALL CURRENT VERSIONS OF OPENOFFICE** before installing this package -- there is a high risk of conflicts.

On my system, OOo 1.9.m104 is stable enough to be used on a daily basis. I've yet to see it crash, even though I use it very heavily (lots of multimedia Powerpoints)



**Please help seed this torrent**, at least till ratio 1.000. Thanks to people currently seeding this.

---

### Post by thegnark on 2005-05-23
[QUOTE=gugus]There is a debian version here, included all localized packages:
[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)[/QUOTE]
 I have been using debs from here for a while. I haven't gone to update in a couple weeks, and now I get a problem when I "sudo apt-get install *"

Couldn't find package openofficeorg-calc-1.9.104.1-linux-2.6-intel.deb

The package DEFINATELY exists. Also, I tried doing this with an old version (that I removed prior to installing latest version) and I get the problem (where I did not before). I tried just sudo apt-get install openofficeorg-core01-1.9.104.1-linux-2.6-intel.deb, with no avail. Similar problems anyone? Possible solutions?

---

### Post by jdong on 2005-05-23
You must use **dpkg -i *.deb** -- apt-get only operates with APT repositories.

---

### Post by thegnark on 2005-05-23
[QUOTE=jdong]You must use **dpkg -i *.deb** -- apt-get only operates with APT repositories.[/QUOTE]

WHOA! super brain-fart. I knew that, but for some reason I forgot.

As I side note, I use Ubuntu on my laptop, but not my desktop. As it works out, I don't usemy laptop at home - only when classes are in session (and it so happens that summer session just begun again).

I'm such a dope.

---

### Post by Gnobody on 2005-05-24
it doesn't take on my gtk theme?

---

### Post by jdong on 2005-05-24
Weird... it takes on mine fine.

---

### Post by jdong on 2005-05-24
**Could people who've download this package please help seed it?** I'm down to two seeds right now.

I don't care if you rate limit it to 5KB/s or 15KB/s... I'm asking for any contribution. There are times when I'm not online, and I don't want the torrent to die.


Thanks.

---

### Post by dodongo on 2005-05-24
I'm 75% there and will be more than happy to leave it going for some time, just as a heads-up.

---

### Post by cRoMo on 2005-05-30
Torrent isn't downloadable anymore, and there also is newer build (106) available.

---

### Post by jasplund on 2005-05-30
Version 106: [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m106/Build-1/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m106/Build-1/)

---

### Post by jdong on 2005-05-30
Yeah, new server; haven't stuck on a tracker yet :)

106: I'll build it later this week.

---

### Post by jasplund on 2005-05-30
I wonder if the 104 languagepacks would work for version 106 as well. It's worth a try I guess.


Johan

---

### Post by cRoMo on 2005-06-04
Another build (m107) has showed up.

---

### Post by crvendramini on 2005-06-04
I'm making download via the torrent, thank you very much.  :) 

One question: when I ask to desintall all current openoffice.org packages, synaptic tell me that "ubuntu-desktop" also will be deinstalled. No problem here???? 

thanks

---

### Post by jdong on 2005-06-04
[QUOTE=crvendramini]I'm making download via the torrent, thank you very much.  :) 

One question: when I ask to desintall all current openoffice.org packages, synaptic tell me that "ubuntu-desktop" also will be deinstalled. No problem here???? 

thanks[/QUOTE]

No prob.

---

### Post by crvendramini on 2005-06-05
[QUOTE=jdong]No prob.[/QUOTE]

Thank you...  ;-)

---

### Post by crvendramini on 2005-06-05
Apologize me about flood but the package works great. A breeze install , starts so fast, really amazing...

thank you very much...

 :grin:

---

### Post by Farhad on 2005-06-11
The torrent no longer has any seeds - is there another package i can install?

---

### Post by jasplund on 2005-06-11
[QUOTE=Farhad]The torrent no longer has any seeds - is there another package i can install?[/QUOTE]


Yes you can find 108 here [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m108/Build-1/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m108/Build-1/)

As well as several language packs

---

### Post by Farhad on 2005-06-11
I have now installed from the ftp server - how do I actually open the applications?  There are no entries in my XFCE menu for Openoffice after restarting.

---

### Post by dodongo on 2005-06-11
[QUOTE=Farhad]I have now installed from the ftp server - how do I actually open the applications?  There are no entries in my XFCE menu for Openoffice after restarting.[/QUOTE]
 IIRC, the path to the executable is /usr/bin/soffice

You can (I've used XFCE but don't recall the specifics) create a launcher which points to that file, and it will start OpenOffice for you in its "bare" form (i.e., it won't open Writer, just the main OOo window).

lol  Sorry if that's vague -- was that helpful at all?

---

### Post by jasplund on 2005-06-11
[QUOTE=dodongo]IIRC, the path to the executable is /usr/bin/soffice

You can (I've used XFCE but don't recall the specifics) create a launcher which points to that file, and it will start OpenOffice for you in its "bare" form (i.e., it won't open Writer, just the main OOo window).

lol  Sorry if that's vague -- was that helpful at all?[/QUOTE]

If you want to open writer you should use /usr/bin/soffice -writer

or -calc if you want to open calc

---

### Post by dodongo on 2005-06-11
Thanks, jasplund :)

---

### Post by Farhad on 2005-06-11
[QUOTE=dodongo]IIRC, the path to the executable is /usr/bin/soffice

You can (I've used XFCE but don't recall the specifics) create a launcher which points to that file, and it will start OpenOffice for you in its "bare" form (i.e., it won't open Writer, just the main OOo window).

lol  Sorry if that's vague -- was that helpful at all?[/QUOTE]
 I found the path - its /opt/openoffice.org1.9.108/program/soffice

Thanks for all the help!

---

