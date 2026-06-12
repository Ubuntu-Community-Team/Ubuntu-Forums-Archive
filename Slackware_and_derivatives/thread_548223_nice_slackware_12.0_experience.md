---
title: "nice slackware 12.0 experience"
date: 2007-09-11
forum: Slackware and derivatives
---

### Post by Pancetilla on 2007-09-11
Hi, everyone, just wanted to share my Slackware experience.

I just installed Slackware 12.0 2 days ago and, surprisingly enough, everything went fine. I've been using Debian/ubuntu for three or so years, but I consider myself a "newbie". I'm not afraid of command line (in fact, I don't like using GUIs for doing what I can do just using nano and root passwd), but I wanted some challenge, so I went for Slacware.

It installs OK, everything is clear and well explained. You know what to do at every moment. I went for the "full" install, which copies about 4 GB of packages to my HD. I think this may be the key for a painless installation. It ships with LILO by default, but I chose to reinstall GRUB from my Debian etch install and modified it, don't ask me why. I feel more comfortable using GRUB. 

Ok. Boot-loader is configured. Next: adduser and configure X. I did startx and it was all fine, except the mouse, the wheel was not working. It's a Logitech MX518, so I basically checked if evdev was installed. With a 4 GB install, the answer is "yes", as I expected. So I brought my mouse settings from Debian's xorg.conf and it worked!. Back/forward buttons worked on firefox, not on konqueror, so a little more tweak was necessary. Installed imwheel from linux-packages using Kpackage (it's a breeze to install packages) and using it I was able to use my side buttons.

Nvidia drivers: just download the official drivers from nvidia, sh ./NVIDIA as root, edit manually your xorg.conf and there you go. It can't get easier than that (Windows install is tougher, actually!)

I only miss my apt-get (or pacman, from Arch...a good CL package manager). I think there's one thing called slapt-get, but you've got 4 Gb of installed software, so probably there is an app for everything. I had to ./configure, make, make install libdvdcss too, but it gave me no pain. I also prefer Gnome to KDE, but I already have Gnome in my debian box and I wanted to try something different. But if you like Gnome, my advice is to look somewhere else (although it's possible to install gnome using some .tgz). It comes with fluxbox, xfce...if you are into light desktop/window managers.

The thing is I was expeting a challenge and, surprise, everything went OK right from the start. Very pleased with Slackware 12.0. It is not a beginner distro, but considering my skill level, it is nice enough to give it a try even if you are unsure about your linux knowledge and the install//config is painless, from my point of view. Kudos for Slackware, a pretty nice distro!

---

### Post by tommcd on 2007-09-11
Yeah, slackware 12 is excellent. I've been using zenwalk for a while now and that got me interested in slackware so I put slack12 on my laptop and it runs great. I installed everything from the first 2 CDs so I can boot KDE or XFCE (I prefer XFCE, but I can still use k3b and amarok from XFCE).
Instead of compiling all programs from source you can get ready to install apps as .tgz packages (like libdvdcss and libdvdread) from:
[http://linuxpackages.net/](http://linuxpackages.net/)
[http://www.slacky.eu/](http://www.slacky.eu/)
and slackbuild scripts from:
[http://slackbuilds.org/](http://slackbuilds.org/)

---

### Post by Pancetilla on 2007-09-14
I have to add that I found [slacky]("http://www.slacky.eu/") very helpful and with TONS of packages...it's in italian, but since I'm spanish, i haven't had problems at all...thanks for the links

My Slackware 12.0 is taking shape at full speed. I only have to include some DVD encoder (transcode?) and then try to compile iriverter; after that, it will be perfect (for my needs).

---

### Post by andrew.46 on 2007-10-05
Hi,

 Must say I had a similar experience with Slackware 12. I downloaded the DVD (using the work connection) and installed the Full package. An incredible amount of software, all beautifully integrated. And although a Gnome fan I was blown away by the beautiful KDE desktop.

 Compiling any software I could throw at it was an absolute breeze for the few extra packages that I required. My secret is that I suspect I will more than likely change to Slackware 12 after uni exams.

 Anybody else tempted to change?

                   Andrew

---

### Post by Pancetilla on 2007-10-05
Just a little update, because I'm sticking with Slackware, where other have disappeared from my HD.

I'm doing things that I never thought of in Ubuntu/Debian, playing a lot with the conf files, removing services form the boot-up, etc. I'm not afraid of breaking something, because I always have Debian to go back, but Slackware has resisted all my "hacking" attempts without complain. I found the package system (or the lack of it) strange at first, coming from Ubuntu/debian and their powerful apt-get, but I'm not missing any of these tools. 

Debian/Ubuntu is still my OS of choice, but Slackware has come to stay. I even like KDE :confused: :lolflag:

---

### Post by danny joe ritchie on 2007-10-05
I've been thinking about giving Slack 12 a try! Debian will stil my main OS so I can experiment a little!

---

### Post by tommcd on 2007-10-06
> **Pancetilla said:**
> I have to add that I found [slacky]("http://www.slacky.eu/") very helpful and with TONS of packages...it's in italian, but since I'm spanish, i haven't had problems at all...thanks for the links

My Slackware 12.0 is taking shape at full speed. I only have to include some DVD encoder (transcode?) and then try to compile iriverter; after that, it will be perfect (for my needs).

If you need a dvd encoder just get mplayer (and the codecs) and dvdauthor from slackbuilds:
[http://slackbuilds.org/repository/12.0/multimedia/MPlayer/](http://slackbuilds.org/repository/12.0/multimedia/MPlayer/)
[http://slackbuilds.org/repository/12.0/multimedia/mplayer-codecs-all/](http://slackbuilds.org/repository/12.0/multimedia/mplayer-codecs-all/)
[http://slackbuilds.org/repository/12.0/multimedia/dvdauthor/](http://slackbuilds.org/repository/12.0/multimedia/dvdauthor/)
just read the slackbuilds how to first:
[http://slackbuilds.org/howto/](http://slackbuilds.org/howto/)
I am using mplayer from slackbuilds and it compiled and installed fine. Then read this tutorial for dvd encoding from the command line:
[http://unix-tutorials.com/go.php?id=549](http://unix-tutorials.com/go.php?id=549)
I use this method for dvd encoding on zenwalk. Just make a folder in your home directory called Mencoder-DVDauthor (or what ever). Inside it place 2 files, one for the mencoder commands and one for the dvd.xml file. Edit the mencoder commands for NTSC compatabilty if you need to as explained in the article. Then when I want to encode a video I just place it in the Mencoder folder and copy and paste the commands right into the terminal (just replace your_video.avi with the name of your video). It may not be as easy a GUI tool like Devede, but it works great.
One small thing: the chapters part of the dvd.xml file from the article is wrong. The correct chapter time format is h:mm:ss. Just read "man dvdauthor".

---

### Post by angryfirelord on 2007-10-07
Slapt-get: [http://software.jaos.org/#slapt-get]("http://software.jaos.org/#slapt-get")
Gslapt: [http://software.jaos.org/#gslapt]("http://software.jaos.org/#gslapt")
Makes your life easier. :)

---

### Post by tommcd on 2007-10-07
> **angryfirelord said:**
> Slapt-get: [http://software.jaos.org/#slapt-get]("http://software.jaos.org/#slapt-get")
Gslapt: [http://software.jaos.org/#gslapt]("http://software.jaos.org/#gslapt")
Makes your life easier. :)


Have slpat-get and gslapt been reliable for you? From hanging out at the slackware forums on linuxquestions.org it seems that most of the longtime slackware users just download the updates manually and use upgradepkg to upgrade them, so that is what I've been doing. It is said to be more reliable that way.

---

### Post by angryfirelord on 2007-10-07
> **tommcd said:**
> Have slpat-get and gslapt been reliable for you? From hanging out at the slackware forums on linuxquestions.org it seems that most of the longtime slackware users just download the updates manually and use upgradepkg to upgrade them, so that is what I've been doing. It is said to be more reliable that way.
I've never had any major issues with it. slapt-get is just a front end to slackware's package management, so all it's doing is fetching and doing some dependency resolving, just like how apt-get does the same for dpkg. The worst case scenario I got was it didn't download all the dependencies & even then, I was able to determine what wasn't there and download those packages.

Unless of course, you're one of "1337 slack0rs" who enjoy spending 3 hours trying to figure out why your app isn't working. :) For the "sane" users, there's slapt-get.

---

### Post by lucidapparition on 2007-10-18
I also, have had a similar Slacktackular experience with 12.0. Everything works OK out of the box, and after I recompile the kernel it should work great.

I'm not sure how slackware does it, but the default theme is wonderful. I was bored, and switched the color scheme to browns and oranges and I actually liked it! That never happened for me with the default ubuntu theme.

---

### Post by Whiffle on 2007-10-18
I might have to give slackware another go, I have a special place in my heart for that distro.

If you want gnome, give Dropline gnome or Freerock Gnome a shot, they're easy to install.

---

### Post by digger95 on 2007-10-21
Slackware 12 is great!

I started out on Ubuntu several weeks ago as my very first Linux distro ever (which I highly recommend for any new Windows to Linux convert like me).  But after a week or two with that I decided I wanted to jump into Slackware and get really down and dirty with Linux.  

People thought I was nuts... being a Linux newbie and trying to tackle Slackware, but honestly it has not been bad and I've learned so much already.  I've had some challenging moments to be sure, but the important thing is that my internet worked right out of the box and that's all I need to learn the rest.

I'm very glad I switched now.  I really do feel like I'm actually learning Linux, and not just another point-and-click operating system.  Kinda takes me back to my college computing days (early eighties).

I'll always recommend Ubuntu for my friends getting into Linux for the first time.  It's a sweet distro.  But I don't see myself using anything but Slackware from now on.

Dig

---

### Post by FredB on 2007-10-21
I hope that slamd64 ([http://slamd64.com/](http://slamd64.com/)) will be great too ;)

---

### Post by toasty_ghosty on 2007-10-22
Before 7.10 came out I was using Slackware 12.0 since it was released and I must say, Slackware is completely different but is amazing in its own way. And now that I just got 7.10 working and since I just read digger95's post it makes me want to go back...sometimes a distro just fits you.

---

### Post by FredB on 2007-10-22
My first preview of linux was back in 1997 a slacky...

---

### Post by digger95 on 2007-10-22
> **toasty_ghosty said:**
> Slackware is completely different but is amazing in its own way... sometimes a distro just fits you.
I couldn't agree more.

Slackware just 'fits' me and I can safely say that I'm a slacker for life now.  It's the first distro to make me never want to go back to windows again, and it's also the first to get me to stop distro-hopping.  Good grief I was such a distro-hoe there for a while.  I don't even want to think about how many times I've reformatted my hard drive this past month.   LoL.  Slackware stopped that insanity.

But I have tremendous respect for Ubuntu.  It's a wonderful gateway distro that's getting a LOT of windows folks through the door.  If it weren't for Ubuntu, I'd not be using Linux at all right now, much less Slackware.  Many thanks to Ubuntu.

Dig

---

### Post by g2g591 on 2007-12-23
hmm (Ubuntu, check, Kubuntu, check, Opensuse, check, Debian, check, Gentoo, check, Arch, check) I think its time I give Slackware a try

---

### Post by LaRoza on 2007-12-23
> **g2g591 said:**
> hmm (Ubuntu, check, Kubuntu, check, Opensuse, check, Debian, check, Gentoo, check, Arch, check) I think its time I give Slackware a try

You'll find it very nice.

---

### Post by bebop_tango on 2008-01-10
From all the experience I"ve adquired from Ubuntu/Debian, Slackware 12 was a breeze.

:)

I liked very much the selection of software... there's even an povray modeler (although I had to install povray myself... it's weird it's not included on the DVD)!

I also got a whole bunch of cool software from slacky.eu, like Kaffeine and KFTPGrabber.

It also learned how to install the NVIDIA drivers and modules from the CLI installer...

The slmodem installation didn't work also... but I'm planning to buy a hardmodem and stop having "linux-internet headaches".

The only thing I didn't like was the X font rendering in X. But that's talk for another topic...

---

### Post by andrew.46 on 2008-01-13
Hi,

 Saw you mention fonts:

> **bebop_tango said:**
>  [...] The only thing I didn't like was the X font rendering in X. But that's talk for another topic...

Have you tried adding a windows fontpack to /usr/share/fonts/TTF/ ? Makes a big difference.

           Andrew

---

### Post by Hevoos on 2008-02-06
I installed Slackware 12.0 some months ago, and I don't think I'm going to remove it! It's so fast, clean and stable and easy to configure, I'm starting to get hold of the package management aswell.

As someone said, if I screw up I can always go back to Debian. ;)



A good tutorial for those using Slackware as their desktop distro: [http://www.howtoforge.com/the_perfect_desktop_slackware12](http://www.howtoforge.com/the_perfect_desktop_slackware12)

---

### Post by lespaul_rentals on 2008-02-06
> **digger95 said:**
> 

People thought I was nuts... being a Linux newbie and trying to tackle Slackware, but honestly it has not been bad and I've learned so much already.  I've had some challenging moments to be sure, but the important thing is that my internet worked right out of the box and that's all I need to learn the rest.

I'm very glad I switched now.  I really do feel like I'm actually learning Linux, and not just another point-and-click operating system.  Kinda takes me back to my college computing days (early eighties).

I agree!  Slackware is a great distro.  I heard that it's one of the most advanced and elite of all distros, and a good number of people were like "OMG it's so hard!" but I really didn't feel that way.  It's very customizable, very complex, but in a good way.  Compiling the software doesn't increase the perfomance too much on modern hardware, but hey, 2 seconds cut from the starting time isn't bad.  Plus, compiling from source is fun.  I like to put my terminal fullscreen while running make, it looks like something from a hacker movie.  :lolflag:

---

