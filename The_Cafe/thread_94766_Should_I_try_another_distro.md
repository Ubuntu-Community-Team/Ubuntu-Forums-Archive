---
title: "Should I try another distro?"
date: 2005-11-24
forum: The Cafe
---

### Post by Hygelac on 2005-11-24
Hello.  I'm fairly new to Linux and have recently installed Ubuntu on one of my computers, but have had a lot of hardware problems with it (No need to go into details here; but the floppy drive, floppy controller, and dial-up modem don't work at all; and the mouse, keyboard, and graphics card work only occasionally and/or partially.  There may be other things that don't work too that I haven't tested yet.  Also, the monitor only loaded in 640x480 at first, but I fixed that).  

I am wondering if, in your opinion(s), I should do everything I possibly can to get this hardware working with Ubuntu, or if I should try a different distro first and see how it handles out-of-the-box.  

For reference, the computer is relatively old (Compaq Presario with an AMD K6 processor of about 300MHz, 188Mb RAM, 15Gb and 4Gb hardrives), if that could make a difference.  I also run Damn Small Linux on this computer as a LiveCD (most of the hardware works out-of-box, except for the modem, USB pendrive, and possibly ethernet card and graphics card), and ran it from the hard drive prior to installing Ubuntu.

Of course, for those who may think that I should try another distro, I'm quite interested to know your suggestions, especially if you're familiar with this kind of situation.

---

### Post by dolson on 2005-11-24
I would try to work with someone here to get things working and submit the problem reports to make things better in the future of Ubuntu.

I came from Debian, where I had to do everything myself, to Ubuntu, and it is very slick, and I think that finally there is a distro that is doing everything right for the desktop. I believe in Ubuntu.

To deal with your hardware, you should tackle each item one at a time, starting with your most important part, whichever that is. I would boot DSL and do an lsmod and then make a note of all the modules that are loaded; do an lspci as well. Go back to Ubuntu and do the same, and see what's missing. That's a good place to start, IMHO.

---

### Post by corvax on 2005-11-24
As for the floppy drive / controller first thing i would do is make sure the floppy isnt disabled in the bios.. The second is id make sure the cable was seated correctly on the mobo and the floppy. You say you have a problem with keyboard graphics and mouse sounds like you need to reconfigure x.... Try sudo dpkg-reconfigure xserver-xorg from the command line The modem i would hazard to guess is a W I N modem and they are tricky to get to work in linux.

---

### Post by aysiu on 2005-11-24
I think you should try another computer.

Ordinarily, I would tell someone who's had that many problems to try another distro (Mepis, Blag, SuSE), but if your computer's that old, it may just not work.

Linux is generally pretty good at hardware detection, amazingly good. But it has trouble with extremely new and extremely old hardware. Luckily, the extremely new ones won't be so extremely new in a few months. The extremely old hardware will always be extremely old and get only older with time.

Is your modem a WinModem? If so, it'll work with Windows, but it probably won't work with Linux.

---

### Post by Hygelac on 2005-11-24
Thank you to those who have responded thus far.
 
aysiu:
My plan has actually been to get a new computer (Athlon64 notebook of some sort, probably). I have been using this old one to try out and learn about Linux, which I want to put on the new one. This one had Win98 on it, until a virus gutted its drivers and left most of its hardware in shambles. I decided to try something different instead of reinstalling Windows and all the relevent software and drivers for the 5th time on it, so here I am. I've been learning a lot and it has all been rather fun and interesting. I want to compare several distros too to see what I prefer, though in practice I am limited by the fact that I have to download them at 5Kb/s (Ubuntu took about 34 hours; and the only other one I've downloaded, Damn Small, was a mere 50Mb). Recently a friend has offered me the use of her high-speed for this, so maybe I can try others after all. Despite the fact I will probably have hardware trouble on them too, I can still learn a lot, and get to compare distros for my new computer in the process.
 
aysiu & corvax:
Since your posts I have done a bit of research, and am now fairly certain that I have a winmodem of an especially hopeless type! I guess I'll have to use the USB pendrive to transfer files and get compiling code if I want to install new applications, since I cannot run Synaptic. I may as well learn how to do so at some point.
 
corvax:
The floppy is connected and enabled, demonstrated by its operation in Damn Small. Thanks for the xorg configurer path. When I fixed the screen earlier I edited the xorg.conf in gedit to do so, but now I see that this program is used for that and other things, and it provides information on them as well. Unfortunately, I wasn't able to fix anything with it this time, but it could come in handy on a later computer.
 
dolson:
I'm interested by the fact that you say you had to do everything in Debian by yourself, but I'm not sure what you mean. Do you mean that there is better tech-support for Ubuntu? I don't know if I can devote that much time to getting the hardware working on this machine though, I'm pretty busy with exams and such right now. From what I have been able to do with Ubuntu, it has generally been quite nice, though slow on an AMD K6. The one issue I have with it right now is the GNOME desktop itself. I'm not sure if I like it that much, I want to compare it to KDE. I have nothing to compare it to in Linux except the wee Fluxbox desktop that came with Damn Small (which was pretty cool actually, though very limited in some ways which I don't know if were due to it or the distro it came with).

---

### Post by towsonu2003 on 2005-11-25
here's my 2 cents:

never ever give up. looking at your specifications, I would say: try slackware... 

now, it is hard to use, but it will TEACH you linux for sure :)

What I would do is: first read tutorials about slackware; install slackware; as the above poster said, get yourself a relatively thick notebook (writing notes), make a list of problems, from most important to least important; and start... everytime you are stuck for sure, try another distro. distrowatch.com is a good resource for that.

it took me about 6 months to solve all my problems, which were similar but more numerous than yours, with a better computer, using about 10 distros in total. (yes, first one was slackware :) )

for the winmodem, start reading linmodem.org and download and read and run scanModem tool in there and, if you can't figure out what to do with the output of scanmodem, email their discussion group... excellent people, very helpful, as long as you read stuff...

PS; here is what I learned 6 months ago: linux=reading...

---

### Post by Hygelac on 2005-11-25
Alright, thanks for the suggestions.  Alas, I accidentally made X inoperative whilst configuring it from xorg at some point.  At least the keyboard seems to work properly now (and with no GUI everything runs much faster right now too), which will be nice once I get X and the GUI running again.  I'll try to figure out what I did wrong in xorg that made X inoperative, and then fix it.  If I can't, I'll just reinstall Ubuntu and try to figure it out from the restored system.

---

### Post by Ozitraveller on 2005-11-25
Hi have Xubuntu running on an old Dell 300, PII/300 with ati 32mb video, 128mb ram and 2 x 8gb IDE HDD. All I did was to do a Ubuntu server install and added the rest.
 
Xubuntu:
[https://wiki.ubuntu.com/Xubuntu]("https://wiki.ubuntu.com/Xubuntu")
 
InstallingXubuntu:
[https://wiki.ubuntu.com/InstallingXubuntu]("https://wiki.ubuntu.com/InstallingXubuntu")
 
Ubuntu Mini-RAM HOWTO:
[http://ubuntuforums.org/showthread.php?t=8338&page=1&pp=10]("http://ubuntuforums.org/showthread.php?t=8338&page=1&pp=10")

HOWTO Ubuntu mini ram:
 [http://ubuntuforums.org/showthread.php?t=42873&highlight=low+ram]("http://ubuntuforums.org/showthread.php?t=42873&highlight=low+ram")

And I have tried this (below) on both Dabian and Ubuntu, and it works well with both.
 
Ubuntu/Debian-Sarge Mini-RAM HOWTO:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html]("http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html")
 
Currently I am running Breezy on a PII/400 with nvidia 64 mb video, 389 mb ram and 2 x 10gb IDE HDD. A little bit slow but still useable!
 
I hope this helps!
 
Good luck.

---

### Post by corvax on 2005-11-25
Since this inst really the help forum id suggest you post there.  Or if you want REALTIME help using your favorite irc client login to irc.freenode.net and join #ubuntu im sure someone with more knowledge and experience can get you going :D

---

### Post by Hygelac on 2005-11-26
Good point, I'll stop posting in this thread.  Besides, I got the winmodem working and things are now under control.  :mrgreen:

---

### Post by Specialsauce on 2005-11-26
[QUOTE=Hygelac]Hello.  I'm fairly new to Linux and have recently installed Ubuntu on one of my computers, but have had a lot of hardware problems with it (No need to go into details here; but the floppy drive, floppy controller, and dial-up modem don't work at all; and the mouse, keyboard, and graphics card work only occasionally and/or partially.  There may be other things that don't work too that I haven't tested yet.  Also, the monitor only loaded in 640x480 at first, but I fixed that).  

I am wondering if, in your opinion(s), I should do everything I possibly can to get this hardware working with Ubuntu, or if I should try a different distro first and see how it handles out-of-the-box.  

For reference, the computer is relatively old (Compaq Presario with an AMD K6 processor of about 300MHz, 188Mb RAM, 15Gb and 4Gb hardrives), if that could make a difference.  I also run Damn Small Linux on this computer as a LiveCD (most of the hardware works out-of-box, except for the modem, USB pendrive, and possibly ethernet card and graphics card), and ran it from the hard drive prior to installing Ubuntu.

Of course, for those who may think that I should try another distro, I'm quite interested to know your suggestions, especially if you're familiar with this kind of situation.[/QUOTE]
try

-mepis
-slackware
-gentoo
-slax
-suse 10.0 

but especially try gentoo.

---

### Post by YourSurrogateGod on 2005-11-26
[QUOTE=Hygelac]Thank you to those who have responded thus far.
 
aysiu:
My plan has actually been to get a new computer (Athlon64 notebook of some sort, probably). I have been using this old one to try out and learn about Linux, which I want to put on the new one. This one had Win98 on it, until a virus gutted its drivers and left most of its hardware in shambles. I decided to try something different instead of reinstalling Windows and all the relevent software and drivers for the 5th time on it, so here I am. I've been learning a lot and it has all been rather fun and interesting. I want to compare several distros too to see what I prefer, though in practice I am limited by the fact that I have to download them at 5Kb/s (Ubuntu took about 34 hours; and the only other one I've downloaded, Damn Small, was a mere 50Mb). Recently a friend has offered me the use of her high-speed for this, so maybe I can try others after all. Despite the fact I will probably have hardware trouble on them too, I can still learn a lot, and get to compare distros for my new computer in the process.[/quote]
You can always order a CD if you don't want to spend the time downloading the image.

---

### Post by YourSurrogateGod on 2005-11-26
[QUOTE=Specialsauce]try

-mepis
-slackware
-gentoo
-slax
-suse 10.0 

but especially try gentoo.[/QUOTE]
NO! Hygelac is new to linux (I've been new to Linux before and made the stupid decision of installing gentoo, big mistake), the last thing that you want is a distro such as gentoo, which would take hours to install and configure and might not work after that's done. If someone is new to Linux, the *last* distro to recommend to someone is Gentoo. New folks would become frustrated with the install process and ditch Linux for good without exploring options that are easier to install (Suse and Ubuntu come to mind.)

Personally, I'd recommend Suse if Ubuntu didn't work. It has decent hardware support and is easy to install.

---

