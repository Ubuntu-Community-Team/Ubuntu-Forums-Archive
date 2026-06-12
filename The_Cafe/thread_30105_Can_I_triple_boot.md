---
title: "Can I triple boot?"
date: 2005-04-27
forum: The Cafe
---

### Post by tommyr on 2005-04-27
My system has WinXP, Suse 9.1 already. Can I install Ubuntu as well and will it allow me to boot either of the 3 for now?  

I need XP for my zen Xtra 30g MP3player, that's the only reason I use that, normally I use SUSE but I really LOVE the Ubuntu Live CD and want to install Ubuntu and switch. 

Any answers appreciated. 

Tom

---

### Post by Leif on 2005-04-27
Yes, it shouldn't be a problem. Just check the grub feedback during the installation process. As far as I remember it does inform you of what other OSs it found.

---

### Post by jerome bettis on 2005-04-27
i actually quadruple boot ... ubuntu, gentoo, windows xp, and i just installed free bsd.

i guess i'm an operating systems whore

---

### Post by defkewl on 2005-04-27
Of course you can. I even install three Linux onced: FC3, Debian sarge and Gentoo.

Grub will detect if there are any other OS exists. But if it didn't do the job well, you'll have to edit the grub menu.lst (which will be located in /boot/grub if you install it with Ubuntu) by yourself.

---

### Post by TravisNewman on 2005-04-27
heh- some may remember my setup from a while back-- Ubuntu, Gentoo, Debian, Fedora, SuSE, Another Ubuntu for testing, Windows, Solaris, and FreeBSD. So I was nine-tuple booting.

---

### Post by seven on 2005-04-27
Well, I won't repeat the others but i'll add:
be very cautious when you apply the partition, so you won't delete important data

---

### Post by az on 2005-04-27
Try this:
[http://packages.ubuntu.com/hoary/x11/gnomad2](http://packages.ubuntu.com/hoary/x11/gnomad2)

"I need XP for my zen Xtra 30g MP3player, that's the only reason I use that"

You may not need windows anymore...  

gnomad2 is in Hoary.   

Answer back if it works.  I am at work, waiting for my wife to pick me up and I had nothing to do but google around for a few minutes.

---

### Post by TravisNewman on 2005-04-27
gnomad2 will require some further configuration from the way that hoary installs it, from my experience anyway. gnomad2.sourceforge.net has all the instructions for that.

---

### Post by primeirocrime on 2005-04-27
[QUOTE=panickedthumb]heh- some may remember my setup from a while back-- Ubuntu, Gentoo, Debian, Fedora, SuSE, Another Ubuntu for testing, Windows, Solaris, and FreeBSD. So I was nine-tuple booting.[/QUOTE]

what???? let me just ask if you have diferent passwords for all of that:)

---

### Post by TravisNewman on 2005-04-27
Well, it was only temporary-- I'm back to JUST having one Ubuntu and one SuSE that I'm only keeping around for trying 9.3 whenever I get the motivation. But at the time, no I didn't have different passwords.

---

### Post by DoubleDangerClub on 2005-04-28
I'm still waiting for the vaporware CherryOS to make up for all their crap and make it possible for me to have Ubuntu, Mac OSX, and Windows XP as my boot setup.  Ah well...dreams are good to have...

:)

DDC

---

### Post by KiwiNZ on 2005-04-28
[QUOTE=panickedthumb]heh- some may remember my setup from a while back-- Ubuntu, Gentoo, Debian, Fedora, SuSE, Another Ubuntu for testing, Windows, Solaris, and FreeBSD. So I was nine-tuple booting.[/QUOTE]

Nine Os's , we really do need to do that collection so we can get you into that clinic:):):razz:

---

### Post by TravisNewman on 2005-04-28
Naaaahhhh I was just doing it to see if I COULD do it ;)
No need to TDO me.

(TDO=temporary detainment order-- for people who aren't safe for others or themselves, or both)

---

### Post by poofyhairguy on 2005-04-28
[QUOTE=panickedthumb]heh- some may remember my setup from a while back-- Ubuntu, Gentoo, Debian, Fedora, SuSE, Another Ubuntu for testing, Windows, Solaris, and FreeBSD. So I was nine-tuple booting.[/QUOTE]


Poor hard drives...

---

### Post by TravisNewman on 2005-04-28
heh-- I forgot about Slackware. That's 10 ;)

---

### Post by Fintan on 2005-07-15
[QUOTE=panickedthumb]heh-- I forgot about Slackware. That's 10 ;)[/QUOTE]

Hi mr. 10 systems. I don't think anyone is going to TDO you just yet. But seriously. I have xp (for macromedia), vectorlinux(don't like), pclinuxos(mucho like), ubuntu (mainOS) and freeBSD(don't know because can't boot).

How can i point grub to BSD AND make it boot?
I installed free bsd without installing boot manager to mbr. 
I have tried some of the suggestions here but none have worked.
Since you are obviously an expert i am turning to you.

Any help would be great.
Cheers
Fintan

---

### Post by azurehi on 2007-02-20
Presently I have xp and ubuntu 6.10m about 115gb each.  I want to add pclinuxos 2007 when it's out at the end of 2/07.  think this is possible?  Sounds like it from discussion in 4/05.  Would I just install pclinux and let its partition manager resize or should I do that beforehand w/gparted?  Any help/suggestions appreciated.  
PS - I've had 6.10 for a week and am learning each day - my first installed linux distro.:)

---

