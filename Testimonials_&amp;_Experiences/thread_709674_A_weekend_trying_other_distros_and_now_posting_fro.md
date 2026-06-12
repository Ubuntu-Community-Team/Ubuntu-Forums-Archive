---
title: "A weekend trying other distros and now posting from Ubuntu"
date: 2008-02-27
forum: Testimonials &amp; Experiences
---

### Post by jucas_lo on 2008-02-27
Well, I decided to put on good use the 60 GB of free space I had on my external HD to try a couple of linux distros to see if I could find anything that made me turn to something different than the Ubuntu I've been using since version 5.10.....if I remember well.....

first of all I would like to say that I'm not a programmer/developer or anything, in fact I study Electronic Engineering and I get on the "linux thing" a few years ago first with Mandrake 9.2 (now Mandriva) I stick to it until Mandrake 10 and then I had like a break from linux until I decided to try out Ubuntu (hey they're even giving me a free cd, so what the heck!!) and I've been a fan ever since....

well now I thought...if ubuntu is based on debian, shouldn't be debian the first thing to try, right??....well so here are my impressions....

Debian

Installation extremely easy and speedy...but it is still text based!!! it is 2008!!!! (ubuntu gives us a live CD to try it before installing and it is a lot easier and prettier!!!) It tried to get some packages over internet but it didn't support my Wifi card, (Intel 2200BG completely linux compatible)....

After the install which was pretty quick I got an ugly GRUB prompt, I choose Debian, then the loading / splash thing also very ugly all text based....and finally when it was about to start I got nothing but a blank screen......sad really....i tried to modify the xorg.conf file to use the free ati driver with the proper resolution for my monitor....but i got nothing, i wanted to download ati drivers to get it working but since i didn't have an internet connection working on debian, i had to restart and use ubuntu to download the driver and then install it.....

so finally i got a window manager working...but.....my internet connection wasn't working yet.....I tried to find anything graphical to set it up....but I found nothing!!!! so I gave up!!!

I was really disappointed...I mean if my network card is completely supported in the linux kernel, and my video card should be supported with the open drivers (at least in 2D) why the hell debian wants me to install every single thing manually and edit every config file by hand.....I found it really stupid....and i thing it is not about making things user friendly....it is about saving precious time ...if something is widely supported debian should install it by itself or at least a text based configuration should be available...

openSUSE

Then I decided to try openSUSE since it is acclaimed to be one of the most user friendly distros.....so I downloaded an ISO with KDE just to make it different from Ubuntu...the install was extremely slow!!!! even though the graphic installer was really beautiful!! it kinda recognized my Wifi card but it couldn't resolve a DHCP issue....but at least it tried and after installation the network set up work with just a few clicks...very similar to Ubuntu...

but again it didn't get my video settings right away...I got the same blank screen that I had with debian....this time after some googling...i use a great utility sax2 that gave me a basic config of my video driver and get my to the desktop!!

overall really polished distro..!!! the graphical grub is just fantastic!!! (I'm gonna stick to it)...
then i tried to use amarok to play some songs ....it gave me like 10 crash reports in 2 minutes of playing with it....and obviously as in ubuntu it didn't have the mp3 libraries to play the songs....so i search the net...and I found a very nice thing called 1-Click install...it is a good idea...but it is not as good as it sounds.....SUSE uses the rpm package manager ....and I have to say that it is really the worst thing I've ever seen, it couldn't even manage well the dependency hell of the packages!!! and I was using only the official repositories and the Packman repository which is the most widely used Suse repository..!!! it gave 5 errors and i was just installing one codec!!!

then I tried to install the Ati drivers.....also with the one click thing....it installed supposedly well,  I had to modify  the xorg.conf file, using aticonfig --initial....even though after restarting I got no direct rendering and I culdn't use any 3d app......a shame

In conclusion I have to say that the way debian handles thing instead of helping the users gets in their way by not offering automated things to do very basic stuff....
and openSUSE well I think it is pretty good but it is still  way behind compared to ubuntu...and I think that if it had the apt package manager it would be a real competitor for ubuntu....even though the support in the forums is very limited compared to ubuntus....

Si here I am with ubuntu that since 6.10 has always detected my monitor correctly the same that both distros I tried failed to even get a compatible resolution.....I love ubuntu!!!

well sorry for the long post....but i just feel like sharing....


cya

---

### Post by amd-64 on 2008-02-27
nice and informative ... thanks

---

### Post by Riffer on 2008-02-28
[SIZE="2"]I tried a bunch of distros too (mostly debian based) and I have to agree about SUSE.  I found it to be more a business distro, suitable for workstations.  Haven't tried Debian but I have tried LinuxMint which I would recommend.  Since its based on Ubuntu it installs the same way.  Their software installer works well and software installer is nicer then the add/remove in Ubuntu.  

I have also tried distros designed for older or for machiness with less system resources, (puppy, elive, Xbuntu etc).  While they seem to be good distros, I found them harder to install and set up.  

At the moment I found Ubuntu and LinuxMint to be good distros for beginner Linux users.  I look forward to when I'm more competent with Linux so I can try some of the other Distros.

[/SIZE]

---

### Post by Cresho on 2008-02-28
ubuntu is built towards making it more user friendly and they throw in a community forum to help out (in a community way!). WAY TO GO! :popcorn:

:KS :KS :KS :KS :KS :KS

---

### Post by MONODA on 2008-02-28
> Installation extremely easy and speedy...but it is still text based!!! it is 2008!!!!
thes reason for it to be text based is for it to be fast and simple, not because they cant implement it.

---

### Post by jucas_lo on 2008-02-29
Yeah that's true MONODA, it is in fact very easy to install and as I said before it was really fast....but after thinking about it some time I've found that Debian is not meant for the desktop at all.....I think that what you get with Debian is a clean and fast OS, that I think will be better suited in a server system in which there is just an initial configuration of hardware and services and then you just let the machine do it's job....and you don't have to worry about installing new drivers for a new video card or connecting your PDA, or connecting a camera...(it's not that you can't do it, it is just that it's more difficult than the regular user friendly distro)....and in that case I think Debian will be the best distro....

but if you're like me and like to try new hardware, new drivers and new stuff....it will make your life a lot harder...,you will learn a lot but it will be an incredibly time consuming process.....

 but that's linux right, you can choose whatever suits your needs......

---

