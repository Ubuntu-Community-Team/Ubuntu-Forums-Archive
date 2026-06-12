---
title: "Backports server being switched to FreeBSD?"
date: 2005-04-20
forum: Ubuntu Backports
---

### Post by angrykeyboarder on 2005-04-20
[-X

Um..... I can't hlpe but find that amusing. :)

Hopefully the switch will be soon.  I've been trying to update for hours now.

---

### Post by RastaMahata on 2005-04-20
[QUOTE=angrykeyboarder][-X

Um..... I can't hlpe but find that amusing. :)

Hopefully the switch will be soon.  I've been trying to update for hours now.[/QUOTE]
 arg, I need j2sdk :( asap

---

### Post by mrbass on 2005-04-20
I keep getting errors myself like so:

```

Ign http://backports.ubuntuforums.org hoary-backports Release.gpg
Ign http://backports.ubuntuforums.org hoary-extras Release.gpg
Ign http://backports.ubuntuforums.org hoary-backports Release
Ign http://backports.ubuntuforums.org hoary-extras Release
Ign http://backports.ubuntuforums.org hoary-backports/main Packages
Ign http://backports.ubuntuforums.org hoary-backports/universe Packages
Ign http://backports.ubuntuforums.org hoary-backports/multiverse Packages
Ign http://backports.ubuntuforums.org hoary-backports/restricted Packages
Ign http://backports.ubuntuforums.org hoary-extras/main Packages
Ign http://backports.ubuntuforums.org hoary-extras/universe Packages
Ign http://backports.ubuntuforums.org hoary-extras/multiverse Packages
Ign http://backports.ubuntuforums.org hoary-extras/restricted Packages
Err http://backports.ubuntuforums.org hoary-backports/main Packages
  500 Internal Server Error
Err http://backports.ubuntuforums.org hoary-backports/universe Packages
  500 Internal Server Error
Err http://backports.ubuntuforums.org hoary-backports/multiverse Packages
  500 Internal Server Error
Err http://backports.ubuntuforums.org hoary-backports/restricted Packages
  500 Internal Server Error
Err http://backports.ubuntuforums.org hoary-extras/main Packages
  500 Internal Server Error
Err http://backports.ubuntuforums.org hoary-extras/universe Packages
  500 Internal Server Error
Err http://backports.ubuntuforums.org hoary-extras/multiverse Packages
  500 Internal Server Error
Err http://backports.ubuntuforums.org hoary-extras/restricted Packages
  500 Internal Server Error
Fetched 17.0kB in 16s (1061B/s)
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz  500 Internal Server Error
Reading package lists... Done
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by RastaMahata on 2005-04-20
same for me, errors 500 :(

---

### Post by cka on 2005-04-20
Yep, this thread just answered my question about the http 500 errors.

---

### Post by ubuntu-geek on 2005-04-20
[QUOTE=angrykeyboarder][-X

Um..... I can't hlpe but find that amusing. :)

Hopefully the switch will be soon.  I've been trying to update for hours now.[/QUOTE]
 Costs $150 for a custom OS install.. If you would like to donate I will get backports on an Ubuntu server :)

---

### Post by ubuntu-geek on 2005-04-20
Ok the repo is fixed on the old server :) happy leeching..

---

### Post by MaX on 2005-04-21
[QUOTE=ubuntu-geek]Ok the repo is fixed on the old server :) happy leeching..[/QUOTE]
 backports still gives me Failed

---

### Post by A-star on 2005-04-22
same problem here

---

### Post by ubuntu-geek on 2005-04-23
how about now?

---

### Post by NaplesBill on 2005-04-23
I just tried the backports repo and they are not working.  I also tried to browse from [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)  by clicking on the line "You may browse the entire repository here."  This is the message I get:

> <D:error>
<C:error/>
<m:human-readable errcode="160029">
Could not open the requested SVN filesystem
</m:human-readable>
</D:error>

---

### Post by frankzen on 2005-04-23
14:00 esdst and freebsd is still down. :roll:

---

### Post by KroniX on 2005-04-23
eta on when it will be up?

---

### Post by plockery on 2005-04-24
I am getting this 500 error still on all backports addresses.

---

### Post by oracledarren on 2005-04-24
16:20 GMT UK Still down

---

### Post by frankzen on 2005-04-24
14:37 eastern daylight saving time Sunday April 24 2005  ](*,) and still down

---

### Post by TravisNewman on 2005-04-24
jdong is away tending to his life away from the backports for now. He may have a better idea of what's going on, since he deals with it on a regular basis. So on behalf of jdong, I say please be patient while he's away, and everything will get fixed as soon as possible.

ubuntu-geek is working on trying to get things going, but this is jdongs baby, and he knows what the baby needs when it starts to cry :)

---

### Post by ubuntu-geek on 2005-04-24
[QUOTE=frankzen]14:00 esdst and freebsd is still down. :roll:[/QUOTE]
 Hello, the server actually hasn't been switched it still on the old server. The repo is currently working on the old server.. If it proved stable on the new server for the next 12 hours i'll switch it over..

---

### Post by Trab on 2005-04-24
[QUOTE=ubuntu-geek]Hello, the server actually hasn't been switched it still on the old server. The repo is currently working on the old server.. If it proved stable on the new server for the next 12 hours i'll switch it over..[/QUOTE]
 everything is hunky dorrie now.... the 500 error is gone for me as of 12:36pm PST
thanks mate

---

### Post by jtopping on 2005-04-24
ditto...i'm so happy to have w32codecs now :)

---

### Post by jdong on 2005-04-24
Hey everyone,

I was in Atlanta at the US FIRST robotics competition's international championship event for the past few days. As a result, I was unable to have any internet contact for the past few days (too tired!)

I'm sorry to hear about the downtime, and I'd like to thank Ubuntu-geek for stepping in to bring the server back online.


P.S: In case we're wondering, we placed 1st in our division (there were 4 divisions, ~400 teams in total), and 3rd overall, an unprecedented event on our team!

---

### Post by TravisNewman on 2005-04-24
Congrats jdong! Welcome back!

---

### Post by angrykeyboarder on 2005-04-24
[QUOTE=ubuntu-geek]Costs $150 for a custom OS install.. If you would like to donate I will get backports on an Ubuntu server :)[/QUOTE]

What costs $150.00 (for a cutsom install)? Ubutu or FreeBSD?

At the very least you could have gone with 
**any** Linux distro rather than FreeBSD. ;-)

On the other hand, FreeBSD does not seem to be working either.  I have not been able to access your archive for a few weeks now...

---

### Post by TravisNewman on 2005-04-24
Can you not access it now? Do you have the correct entries in your sources.list? Things were fixed earlier, and I've had no problems since.

FreeBSD, for a server, is better than most Linux distributions. And it's Ubuntu that costs extra.

---

### Post by ubuntu-geek on 2005-04-24
[QUOTE=angrykeyboarder]What costs $150.00 (for a cutsom install)? Ubutu or FreeBSD?

At the very least you could have gone with 
**any** Linux distro rather than FreeBSD. ;-)

On the other hand, FreeBSD does not seem to be working either.  I have not been able to access your archive for a few weeks now...[/QUOTE]
 It costs $150 for my provider to install a custom OS. Fedora was not a option and FreeBSD is the next best to Ubuntu.

---

### Post by desheikh on 2005-04-25
Hey guys,

Is the backports server up yet or not  ? 

I cant seem to access it :S

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

Ali

---

### Post by ubuntu-geek on 2005-04-25
How about now?

---

### Post by desheikh on 2005-04-25
Woooohoooo!!!.. J2re for me finally!! 
Thanks :D

---

### Post by dreadnought on 2005-04-25
Welcome back I missed you\\:D/

---

### Post by jdong on 2005-04-25
Ok, I'm glad we're all settled down.

I'll be back to writing an English paper.

---

### Post by gbusse on 2005-04-25
Thanks alot jdong and ubuntu-geek for all your work on the server. Unfortunately though there seems to be a problem. Apt-get takes forever to connect to the server then once it has finally connected it crawls along at a snails pace. Apparently it is going to take 45 minutes to download an 864K upgrade to GAIM. I know it is not my connection as I have tested it with other servers.

Hopefully the server will stabilize soon. I would help but unfortunately when it comes to Linux based servers I am not really that qualified (yet) and when it comes to BSD based servers, forget it.

Thanks again,
Gord

---

