---
title: "First things YOU do with your new Ubuntu OS!"
date: 2006-06-08
forum: The Cafe
---

### Post by Patrick-Ruff on 2006-06-08
hey all, stay you've just freshly installed Ubuntu, or a new version or whatever, either way your hard drive is completely clear, system is fresh, what do YOU do from there? What programs do YOU install? what things do YOU do to your fresh Ubuntu system?

fun thread


my being new to linux, I don't have a routine to getting a new system set up. unlike what I did with Windows...but I'm done with that, so, Post away!

---

### Post by Patrick-Ruff on 2006-06-08
I just realized that this is the Support category, feel free to move this thread if you feel the need to admins.

---

### Post by Turin Turambar on 2006-06-08
The first thing I do is setup my modem. I'm still on Dial-up and I have to compile ltmodem modules. :) Once on the internet, I slowly download everything and within day or two, I have a fresh, but fully functional system. :)

Oh yeah, I pretty much try not to spoil the virginity of the new system... so I try the default values... if it works, I leave it as it is, if not, I modify. ;)

---

### Post by nix4me on 2006-06-08
Install build-essential, thunderbird, sun-java, mplayer, mozilla-mplayer, proftpd, flash, 686 kernel, etc.

nix4me

---

### Post by Patrick-Ruff on 2006-06-08
right on, how would you go about doing this 'The first thing I do is setup my modem. I'm still on Dial-up and I have to compile ltmodem modules.' ltmodem? I can never get other drivers working correctly, the only ones I have are Linuxant drivers..ugh I hate those with a passon, 20 bucks for full support..ugh, are there alternatives to these drivers? I'de rather not be having my desktop on the internet and then my laptop getting internet from my desktop via ICS lol.

---

### Post by rickyjones on 2006-06-08
Mplayer. GNUCash. NetworkManager. Most other things are already setup because I keep my /home in it's own partition.

I try to keep a clean system when I can.

-Richard

---

### Post by ????? on 2006-06-08
I would get my Broadcom Wireless working, and then customize firefox, and get everything configured and install some extra packages (like Thunderbird)

---

### Post by Patrick-Ruff on 2006-06-08
my wireless worked right out of the box :).

---

### Post by grsing on 2006-06-08
First thing, run Automatix and get all the multimedia codecs and such set up.  Then customize the desktop (make it more functional for me, no big changes, just moving icons around, adding some, deleting some).  Then get Firefox all set up (extensions, bookmarks, themes, etc).  Then make Ubuntu all pretty (screensaver, desktop background, theme, etc.).  Wireless in there somewhere if it's my laptop.  That's about it, I think.

---

### Post by onesojourner on 2006-06-09
install compiz.

look it up on google video if you dont know what it is.

---

### Post by Brando569 on 2006-06-09
[QUOTE=grsing]First thing, run Automatix and get all the multimedia codecs and such set up.  Then customize the desktop (make it more functional for me, no big changes, just moving icons around, adding some, deleting some).  Then get Firefox all set up (extensions, bookmarks, themes, etc).  Then make Ubuntu all pretty (screensaver, desktop background, theme, etc.).  Wireless in there somewhere if it's my laptop.  That's about it, I think.[/QUOTE]

same here! :D i download automatix and run it then customize kde to my liking and installed needed apps from there

---

### Post by Zerocool10482 on 2006-06-09
These are my steps

1. Setup internet.
2.sudo apt-get update, sudo apt-get upgrade
3.test all the new features and programs. (about a week)
4.Install VLC, PenguinTV, XMMS, and anything else I see in the package manager.
5.Copy DVD backup to /home
6.Check out the forums for new updates

---

### Post by jaapd on 2006-06-09
I installed the new version of FireFox, OpenOffice 2 (not the beta on) and NetBeans.
All this without missing windows.

---

### Post by angkor on 2006-06-09
First thing is to enable the universe / multiverse repositories. After that it's time for a new kernel:

```
sudo apt-get install linux-image-k7
```

reboot and then I install the nvidia drivers:

```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
sudo nvidia-xconfig
```

and restart X.

After that I install a bunch off apps I always use. Among others: Azureus, thunderbird, mplayer, vlc, nicotine, gdesklets, engage, gnomebaker, amarok etc.

---

### Post by anaconda on 2006-06-09
Interesting that no-one mentioned this yet.. Or is this thought to be part of installing ubuntu?

The absolutely first thing I do is to enable all the repositories I want! So that apt-get and synaptic can find all the programs that I need..

Then I would install mplayer, azureus, a few games, f-spot,  different window managers, wine, 

Then I would adjust the look of ubuntu.. I hate the 2 (gnome)panels on top and bottom taking too much space on my monitor..

---

### Post by Klaidas on 2006-06-09
Hmm, let's see.
First, I change the wallpapper.
Then, change the defautl OS in grub
Then, enable extra resposities.
After that install codecs, XMMS, Xchat, Firestarter, Skype, gFTP, a buch of other things:)

---

### Post by angkor on 2006-06-09
[QUOTE=anaconda]Interesting that no-one mentioned this yet.. Or is this thought to be part of installing ubuntu?

The absolutely first thing I do is to enable all the repositories I want! So that apt-get and synaptic can find all the programs that I need..
[/QUOTE]

No one?

[quote=angkor]first thing is to enable the universe / multiverse repositories.[/quote]

:p

---

### Post by anaconda on 2006-06-09
Oh.
sorry angkor, I must have missed your post the first time.

You were the first.

---

### Post by someusernoob on 2006-06-09
1. install nvidia-glx
2. install codecs etc. with Bumps
3. instal Xgl/compiz
4. install some programs like par2, rar,cksfv, thunderbird, xchat
5. play with ubuntu, coz everything else i use works out-of-the-box.

/edit: i forgot, somewhere between those actions i change my fstab file for the right mounting.

---

### Post by hw-tph on 2006-06-09
I enable the universe and multiverse repositories, install build-essential, some utilities (svn, cvs, etc). Add some gstreamer plugins. Then I restore my $HOME backup (dotfiles, documents, etc) and then I'm pretty much done.

This last install (Dapper) I got the quodlibet svn sources, got the requirements for building it (**apt-get build-dep quodlibet**) and then installed quodlibet-svn. Nice. :)

---

### Post by ramcosca on 2006-06-09
Tried a couple times to connect it my home network, wired. When I did, I downoaded the recommended updates and logged in here... lol

---

### Post by msv240586 on 2006-06-09
Hey guys this might sound like a stupid question to you guys but i've just freshly just installed ubuntu 5.10 and i've got no idea on how to install any softwear. I follow the readme instructions but i'm finding it so difficult! I haven't been able to install anything

---

### Post by Patrick-Ruff on 2006-06-09
installing stuff is  quite different from windows..it requires alot more interaction with the terminal. heres some examples of installing

```

sudo dpkg -i /media/cdrom/install.deb
sudo sh /media/cdrom/install.sh

```

stuff like that. I remember seeing a Terminal tuturial somewhere, I suggest you search and find that, its the basis of the Linux OS.

---

### Post by Patrick-Ruff on 2006-06-09
whoops, forgot to mention, theres also the package manager, and the apt-get command

for example: 
```

sudo apt-get install yabasic
*note:this requires the internet as expected*
sudo apt-get update
sudo apt-get upgrade

```
etc.

---

### Post by christhemonkey on 2006-06-09
From your desktop select Computer > System Configuration > Synaptic Package Manager, you will be asked to enter your password.



You then add extra repositories.

Goto Settings > Repositories you will see (2) grayed out boxes click both of them, then click the Reload button.

Then select what you want to install!

---

### Post by xXx 0wn3d xXx on 2006-06-09
I usually install Automatix and use that to do everything for me. I could install everything myself, but nothing gets the job done quicker then automatix.

---

### Post by msv240586 on 2006-06-09
[QUOTE=christhemonkey]From your desktop select Computer > System Configuration > Synaptic Package Manager, you will be asked to enter your password.



You then add extra repositories.

Goto Settings > Repositories you will see (2) grayed out boxes click both of them, then click the Reload button.

Then select what you want to install![/QUOTE]


Yeah thats good and nice but i can't connect to the internet from ubuntu becuase i cannot seem to install the driver. it always keeps on telling me "Not a valid command" or "Location doesn't exist" and stuff like that

---

### Post by Jagot on 2006-06-09
I usually use a script I have written and add to occasionally to set my new installation up as I want:

```
#!/bin/bash

## updating
sudo aptitude update
sudo aptitude -f -y upgrade
sudo aptitude -f -y dist-upgrade

## compilers

sudo aptitude -f -y install build-essential

## ndiswrapper & 915resolution
sudo aptitude -f -y install ndiswrapper-utils 915resolution

## setting up ndiswrapper

sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

sudo rmmod bcm43xx

sudo rmmod ndiswrapper

sudo modprobe ndiswrapper

## fonts

sudo mv ~/Desktop/My\ Fonts /usr/share/fonts/truetype/
sudo aptitude -f -y install xfonts-intl-arabic xfonts-intl-asian xfonts-intl-chinese xfonts-intl-chinese-big xfonts-intl-european xfonts-intl-japanese xfonts-intl-japanese-big xfonts-intl-phonetic gsfonts-x11 msttcorefonts

## configure fonts

sudo fc-cache -f -v

## mp3

sudo aptitude -f -y install gstreamer0.10-plugins-ugly mpg321 vorbis-tools

## other non-free

sudo aptitude -f -y install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-main1 libxine-extracodecs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse 

## windows codecs

wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb 
sudo dpkg -i w32codecs_20050412-0.4_i386.deb

## media players

sudo aptitude -f -y install totem-xine xine-ui mplayer vlc totem-xine-firefox-plugin gxine

## dvd

sudo aptitude -f -y install libdvdread3 
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

## flash

sudo aptitude -f -y install flashplugin-nonfree
sudo update-flashplugin

## java

sudo aptitude -f -y install sun-java5-jdk
sudo update-alternatives --config java

mkdir -p /home/jagot/.mozilla/plugins

cd ~/.mozilla/plugins

ln -s /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

sudo ln -s /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/

## samba

sudo aptitude -f -y install samba smbfs

## gparted

sudo aptitude -f -y install gparted ntfsprogs gksu

## splash screen manager

sudo aptitude -f -y install gnome-splashscreen-manager

## change gtk themes & icons for root applications

sudo ln -s /home/jagot/.themes /root/.themes
sudo ln -s /home/jagot/.icons /root/.icons
sudo ln -s /home/jagot/.fonts /root/.fonts

## epiphany

sudo aptitude -f -y install epiphany-browser epiphany-extensions

## rar support

sudo aptitude -f -y install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar

## gnomebaker

sudo aptitude -f -y install gnomebaker

## restart
sudo shutdown -r now
```

---

### Post by J0E0NE on 2006-06-09
Id install nvidia glx drivers + java sun + spend a couple of hours puttin all those gd's of music back on and also getting frostwire back :p

---

### Post by fluffington on 2006-06-09
Here's what I do. Might be missing a thing or two.

[list=1]
[*]Install nvidia-glx, rewrite xorg.conf from memory (I've reconfigured X on this box so many times throughout the Dapper testing cycle that I've memorized it)
[*]Compile & install nVidia chipset drivers (why aren't these in the repos)
[*]Enable universe/multiverse repositories
[*]Install optomized kernel and headers
[*]Install gstreamer plugins and fonts
[*]Install blender, inkscape, xchat, abiword, gnumeric, and bluefish
[*]Install lots of -dev packages
[*]Setup my printer
[*]Move the panels around and add launchers for gedit and terminal
[*]Configure Firefox, Nautulus, and a couple things in System > Preferences
[*]Done! Time to read the forums.
[/list]

---

### Post by u.b.u.n.t.u on 2006-06-09
I am actually compiling a mini install manual/tutorial for myself. It covers areas such as synaptic, video card drivers, HDD file format and mounting, links, security, messenging and networking.

I may create a wiki for myself and add it to my signature when I am finished.

I am only in my 2nd week of using ubuntu but have already installed it many times, on many computers and basically spent whole days learning it. I need to get proficient with ubuntu fast as I no longer want to deal with XP (which I knew very well).

I will also be testing 6.10 and may seek to join the beta testing team. I have a box that can be used for dedicated testing. Creating faults and solving them, so that will be fun.

All of my friends use XP. I will be the person to help them make the move - so that gives you an idea of the skills with ubuntu I need to develop.

The first thing I do when I install a vanilla ubuntu - I feel happy. \\:D/ 

lol :D

---

### Post by TOPPEL on 2006-06-09
[QUOTE=grsing]First thing, run Automatix and get all the multimedia codecs and such set up.  Then customize the desktop (make it more functional for me, no big changes, just moving icons around, adding some, deleting some).  Then get Firefox all set up (extensions, bookmarks, themes, etc).  Then make Ubuntu all pretty (screensaver, desktop background, theme, etc.).  Wireless in there somewhere if it's my laptop.  That's about it, I think.[/QUOTE]

i am very weary of a script doing things for me seeing as the ubuntu wiki is periodically updated as well as the operating system some things like easyubuntu script wont run for some people and i personally want to know what i have on my system i dont want to not have a clue of what all is in my windows/system directory because if you've used windows long enough they are easily seen as a operating system that is setup so you dont know anything and that you have to get help just because of design flaws (such as desktop cleanup) -- things that are not so obvious.  anyway i'm into doing things myself and not letting anyone elses script setup what may damage my system and if i'm in linux for the long haul i want to have a clue about what i'm doing so i can learn about it more later. 

:rolleyes:

---

### Post by AndyCooll on 2006-06-09
First thing I do is install openssh-server and give the box a fixed IP address. I then reboot.

I can then control the box from my main machine. I then add additional users (the missus), install nfs-common, edit fstab, sources.list, ssh_config, network_interfaces, hosts etc.

After that I'll install kubuntu-desktop followed by Automatix, and finally a host of other software I like to have on my system.

:cool:

---

### Post by namelessted on 2006-06-09
I get my wireless working. Then i configure the video card to work properly with my laptop widescreen. Then i go on to automatix, and customizing some of my programs like firefox

---

### Post by r3st on 2006-06-09
usualy repositories and change the theme
then restricted formats

---

### Post by grsing on 2006-06-09
[QUOTE=TOPPEL]i am very weary of a script doing things for me seeing as the ubuntu wiki is periodically updated as well as the operating system some things like easyubuntu script wont run for some people and i personally want to know what i have on my system i dont want to not have a clue of what all is in my windows/system directory because if you've used windows long enough they are easily seen as a operating system that is setup so you dont know anything and that you have to get help just because of design flaws (such as desktop cleanup) -- things that are not so obvious.  anyway i'm into doing things myself and not letting anyone elses script setup what may damage my system and if i'm in linux for the long haul i want to have a clue about what i'm doing so i can learn about it more later. 

:rolleyes:[/QUOTE]

Not sure how EasyUbuntu works, but with Automatix, you can pick pretty much exactly what it's going to install (with a few exceptions), just saving a lot of apt-get install typing.  And it serves as a bit of a checklist for me.  Of course, everyone is different, which is part of what's great about Ubuntu (many different ways to do what you want).

---

### Post by karlsson88 on 2006-06-13
The first thing i did was to install XGL ....

---

### Post by ubnoobie on 2006-06-13
my current dapper desktop is a mix of ubuntu and xubuntu; starting with a bare (console) install off an alternate install cd.

the very first thing done was switch to the k7 kernel.

i left the cd in (to use as a repository), enabled universe & multiverse, and then installed the bits and pieces of those two desktops environments i wanted. i went slow, taking in one or two major components at a time.

i installed the nvidia-glx restricted driver, enabled it; reconfigured xorg to specify display resolutions; then a quick manual edit to xorg.conf to get my mouse buttons working. 

installed the rest of the desktop apps i wanted (openoffice, gnomebaker, abiword, gnumeric, editors, media players, etc)...

configure themes & desktop in the desktop environments

went through the restricted formats wiki page and installed the multimedia codecs and other non-free format support that i wanted --- manually.

set up my primary printer --- an hp laser that's connected to a windows system. connect to a few windows shares, install samba & smbfs (for future use)

install the parts of a LAMP server that i want for testing and home lan use (will be a media server). install vsftpd & ssh server.

install a few must-have extensions for firefox, configure xchat (non-gnome version), gaim (for non-irc protocols). set up epiphany for use with gmail only (firefox for everything else), configure thunderbird for certain accounts (will use evolution for others).

and that's where i'm at currently -- still have to set up the web-based jukebox (ampache or similar), migrate data over from several pc's & an external drive, set up a scanner & two other printers, configure mail services (fetchmail, mta, spamassassin, etc), vnc, and a few other things. those will be done as-needed and as time permits.

---

### Post by KarmaKing on 2006-06-13
log-in

---

### Post by Patrick-Ruff on 2006-06-13
nice, this thread is continueing, well...I can't seem to get Gnome working perfectly, lack of graphics accelleration towards it and all that..ugh

---

### Post by jimcooncat on 2006-06-13
[QUOTE=AndyCooll]First thing I do is install openssh-server and give the box a fixed IP address. I then reboot. [/QUOTE]

Me too. I might get a chance to play with my home machine while I'm at work, or install a machine in the basement. After all, there's only so much free time, and a new distro has lots of stuff to explore!

---

### Post by sherlock-holmes on 2006-06-13
i set the keyboard shortcut for the terminla to alt+F3.

edit source.list and update, dist-upgrade

install thunderbird, vpnc, kile, and other applications i need for school

etc...

---

### Post by muzakman on 2006-06-13
Couple of n00b things...

How do you get the broadcom working? everything i try stops at the modprobe command with ndiswrapper, im stuck

I also need to know how to install the multimeda codecs i need (dvd, mp3, etc.)

i saw some reference to something called Automatix, but i dunno what that is...

Help?


Cheers,
Will

---

### Post by fluffington on 2006-06-13
[QUOTE=muzakman]I also need to know how to install the multimeda codecs i need (dvd, mp3, etc.)[/QUOTE]

Check out the [Restricted Formats](https://wiki.ubuntu.com/RestrictedFormats) wiki page.

[QUOTE=muzakman]i saw some reference to something called Automatix, but i dunno what that is...[/QUOTE]

It's a script that automatically installs some useful stuff, like Flash, video drivers, etc. Check out [ths thread](http://www.ubuntuforums.org/showthread.php?t=177646).

Edit: stupid grammatical errors

---

### Post by Patrick-Ruff on 2006-12-26
lets pull a thread back from the dust . . . heres some new things I do now.

set up a static IP for my WiFi (also configure the proxy use)
set up my ATI drivers (which really suck, and don't work well)
install many, many, many programs.
and continue tweaking it to get it the way I want it (still haven't quite accomplished that yet . . . )

---

### Post by macogw on 2006-12-26
apt-get install msttcorefonts gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs libdvdread3 libdvdcss2 totem-xine dpkg-dev fakeroot debhelper vlc vlc-plugin-* mozilla-plugin-vlc
avahi-daemon avahi-utils totem-gstreamer-firefox-plugin realplay cowbell easytag banshee dvdrip vcdimager cdrdao subtitleripper acidrip goobox gnomebaker gdesklets gdesklets-data build-essential alien planetpenguin-racer planetpenguin-racer-data planetpenguin-racer-extras frozen-bubble flashplugin-nonfree alsa-oss  sun-java5-jre sun-java5-plugin
^^^^^^^^^^^^^^
All that stuff that I copied from ubuntuguide and then smooshed into one long apt-get instead of 30 of them.

Oh, and add beryl and Tilda (with the key mapped to F2)

---

### Post by Griffongob on 2006-12-26
so if I had a desktop with a pci wireless card how would I set that up?

---

### Post by bodhi.zazen on 2006-12-26
1. Security: I like to do a few security tweaks first thing.
2. Setup internet/firefox
3. Update, including kernel (reboot)
4. Setup my dual monitors & beryl (just for the fun of it)
5. Setup multimedia
6. Setup local networking/printing
7. Install fluxbox
8. Remove unnecessary packages.

---

### Post by NeoLithium on 2006-12-26
Well, once I get my internet up (takes like 20 seconds for me max anyway); the first thing I do, is compile a new kernel that's configured to my specs; or if I'm lazy at that point, I'll skip it and download the things that I want, like Opera, TinyFugue, as well as transfer my files from my backup disks onto my HD while the updates are running.

From inserting the install disk, to having the system up to what I want with my files transferred from backup, usually only takes me about 2 hours, if I include time compiling a kernel.

---

### Post by keithpeter on 2006-12-26
Xubuntu 6.06 install on a Dell L400 goes like this (but hopefully not too often :) ) 

[LIST]
[*]Get the USB ADSL modem working using [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)
[*]Do most of [http://ubuntuforums.org/showthread.php?t=186792](http://ubuntuforums.org/showthread.php?t=186792) to get flash, MP3 and other stuff working, and to change the sources.list
[*]Install openoffice using sudo apt-get install openoffice2
[*]Change the panel widths in xfce4 to 24px each and set autohide. Set the right margin on the screen to 5px so I can always get to menu even with apps maximised
[*]Dowload the Agualemon theme for xfce4 - nice and neat
[*]Add some wallpaper
[*]Try to get some work done ;) 
[/LIST]

All of this takes about 90 minutes. I've been playing with various versions of Ubuntu and various desktops and have decided to stick with Xubuntu on the P3 700MHz with 256Mb of RAM. OpenOffice is essential as I produce handouts with diagrams and formulas and need to produce presentations.

---

### Post by Patrick-Ruff on 2006-12-26
> **Griffongob said:**
> so if I had a desktop with a pci wireless card how would I set that up?

so long as it was detected and is working, you would go into the networking settings and set it up to use a certain network and all that.  I'm not sure what the deal is with edgy, the network settings no longer automatically uses gksudo, making it basically useless.

I guess a programmer started drinking at some point? or what?

---

### Post by TooRight on 2006-12-26
The first thing I do is install the drivers I need for my ATI graphic card, then I enable the respositories, update, install Kubuntu, then automatix to install flash and java, when that's done I set automatix to install everything else i want, audio and video codecs, programs and utilities etc, and while that's happening I head over to kde-look.org to grab my usual icons and my superkaramba and it's various karambas, when that's done i head over to youtube to kill some time while automatix finishes up :D

---

### Post by Patrick-Ruff on 2006-12-26
ati graphics drivers . . . . eww. I wish they would do something about that.

---

### Post by TooRight on 2006-12-26
Yeah, those drivers sure are a source of contention around here... it's amazing how many threads are dedicated to sorting it all out.

---

### Post by Lost Traveler on 2006-12-26
Patrick-Ruff,  I know next to nothing and so I downloaded a book, _Ubuntu Linux For Non-Geeks[U] and the author guided me through the install and with a series of little lessons you would learn what and how to do what needs to be done.  Good luck._[/U]

---

### Post by Andreas93 on 2006-12-26
Set up my folders in home to make it look more like Windows (which is a bit sad) and add my data

---

### Post by qalimas on 2006-12-26
If I am on my desktop, I start with the nVidia drivers.  On my laptop, the ATI OSS by default works fine.  After that, on any system, I continue with mp3 playback, Flash, Java, that sort of thing.  Skype usually follows and then I'll theme up KDE and change a bunch of settings.

---

### Post by xpod on 2006-12-26
Im one of the lucky ones that thankfully dont have much i really need to do in the way of hardware configuration.
Everything just works apart from the nvidia card which takes all of 2 minutes now to set up or 5 mabey seeing as beryl is usually installed at the same time on this pc.Printer is but a click or 2 away and practically every mobile phone,camera and mp3 player in the house shows up automatically.

Java,flash,codecs etc .Most times from automatix but i went without AX on a more recent ubu install on another pc of ours and did things the "proper" way instead:rolleyes: 
Change browser preferences and add extensions......the ubuntu one being the first one usually :D 

All in all the whole thing from blank cd to fully set up os takes 40 or 50 minutes.....if that?
It does now anyway.

After the few months i had previously on a pc someone was looking down on me when i found ubuntu me thinks..........mabey i`ll get myself over to the "which religon" thread after all:twisted:

---

### Post by Stemp on 2006-12-26
1. pppoeconf for my dsl modem
2. universe/multiverse repos
3. updates
4. libdvdcss, mp3 and w32codecs
5. ati/radeon free driver (my ati 9600 is recognized as a vesa card)
6. mplayer, vlc and BMP
7. Flash player
8. epiphany and thunderbird (can't handle spams with evolution)
9. LAMP and others things to learn

---

### Post by Patrick-Ruff on 2006-12-27
nvidia, you have no idea how lucky you are.    I still don't thikn my ubuntu setup in my laptop is quite complete, probably because of the bloody ATI card . . .

---

### Post by tom1979 on 2006-12-27
Hmmm well as this was my first install, a duel boot with xp, i checked xp was still there! then run ubunto on a lan cable, setup gaim, annoyed a few contacts with the auto reply settings(easy to please!), then left the updates running, installing every package, and automatix, again adding every extra bit of software! my 2Gb install is now nearly 10Gb!

now im back on xp as the wifi wont work... :( once this is fixed ill sit back and enjoy it!

---

### Post by Patrick-Ruff on 2006-12-27
what wifi card do you have?

---

### Post by ashleycrue on 2006-12-27
I add my essentials
-exaile
-skype
-thunderbird
-gstreamer formp3,etc
-streamtuner and xmms so I can listen to live365.com (this time it doesn't show up)
-aMSN
-change the wall paper,screener saver (I like the ant) and the theme.
-reskin firefox and thunderbird and then add the add-ons
  I had to reinstall a couple of days ago cos I messed up so this time easy ubuntu was added as well but still no dvd.

---

### Post by NT4usB on 2006-12-27
first, first, first... fix the damn mouse so it moves at a reasonable rate. The default setting is so slow I don't have a free space big enough on my desk to get across the screen without pumping the mouse a couple times.
Then configure the buttons in xorg.conf so tabs open and close with the thumb instead of the scroll wheel.
Only then can I proceed with borking up the new install, fixing it, and borking it again...

---

### Post by d3v1ant_0n3 on 2006-12-27
I only have a dapper disc (for some reason, Edgy's live cd won't start up right for me). So the first thing I do is upgrade to edgy.

Uncomment repos.

update & upgrade

Then install Automatix and use it to install codecs and a few apps.

Install Beryl

Install comix

Install gimp 2.3

Tweak everything visually.

---

### Post by SAGEv4.5 on 2006-12-27
install flash, mp3s, and ad blocker for firefox. get new wallpaper

---

### Post by Patrick-Ruff on 2006-12-27
> 
I only have a dapper disc (for some reason, Edgy's live cd won't start up right for me). So the first thing I do is upgrade to edgy.

Uncomment repos.

update & upgrade

Then install Automatix and use it to install codecs and a few apps.

Install Beryl

Install comix

Install gimp 2.3

Tweak everything visually.


if you want edgy really badly, download the alternate CD and do a text install.

---

### Post by Elrohir on 2006-12-29
not exactly in this order but here is what I install:

- Java 1.5.0 (latest update from []("http://java.sun.com/javase/downloads/index.jsp"))
- OpenOffice (latest release from [the official site]("http://www.openoffice.org"))
- [Mercury]("http://mercury.to") Messenger
- Mozilla Firefox (latest release from [http://www.mozilla.com](http://www.mozilla.com))
- Mozilla Thunderbird ([http://www.mozilla.com](http://www.mozilla.com))
- GnomeBaker
- XMMS
- VLC
- Wifi-Radar
- Google Earth ([http://earth.google.com](http://earth.google.com))

that's it I guess... those are the apps I use the most...

---

### Post by confusimo on 2006-12-29
Thankfully Ubuntu 6.06DD 64 bit is pretty stable so I haven't needed to reinstall sinse I first set it up.

But when I first did I needed 32 bit Seamonkey browser for flash cuz 64bit doesn't support flash yet.  And TVtime, Jalbum, RadFtp, Gnome Radio, Wifi-Radar, XMMS for MP3s, and K3B for burning DVDs. all make good additions.

The internet wifi was auto detect and so was my tv card so nothing to setup.  On the internet right away with Comcast Cable Modem and a Router.  Nothing to setup in ubuntu.

Thnaks
Confusimo

---

### Post by hyper_ch on 2006-12-29
--> Running Xubuntu Edgy

(1) Change my /etc/apt/sources.list to this:
> 
# deb cdrom:[Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
# deb cdrom:[Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe


deb  [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free


(2) Execute the following command
sudo apt-get update && sudo apt-get upgrade

(3) Run the follwing install.sh file by this command:
sudo sh install.sh
> 
#!/bin/bash

#KDE Appz
apt-get -y install kopete konversation konqueror k3b amarok krfb ktorrent kftpgrabber
apt-get -y install kontact kdepim-kio-plugins kgpg

# IMs
apt-get -y install skype amsn

# IRSSI / OpenSSH
apt-get -y install irssi openssh-server

# GnuMP3d
apt-get -y install gnump3d

# OTR
apt-get -y install python-glade-1.2 python-gtk-1.2

# VmWare
apt-get -y install linux-headers-`uname -r` build-essential xinetd

# Browsers
apt-get -y install kazehakase mozilla-browser opera flashplugin-nonfree

# Codecs
apt-get -y install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs

# Samba
apt-get -y install samba

# Midnight Commander
apt-get -y install mc

# GParted
apt-get -y install gparted

# Java
apt-get -y install j2re1.4


And then I do that:
cp -Rp /media/sda1/current/home/USER/ ~/

---

### Post by Asham on 2006-12-29
First things I do

1. Tweak the user interface of the OS
2. Install Java 5 (I can't get Java 6 to work)
3. Install Opera
4. Setup all the Firefox extensions needed in order to make the app usable ;)
5. Copy the login and logout sound clips from Dapper

---

### Post by stalker145 on 2006-12-29
I try to remember any changes I made to the theme and then add my backed-up bookmarks to FireFox and finish it all up with updates... that's it... all my programs I use (including Beryl, Sudoku, Conky, and a rash of others) are already installed and set up since I have a disk image that I reinstall from... heinously easy... takes about 4-6 minutes :D

---

### Post by benuski on 2006-12-29
The first things I always do are get the Mozilla manually installed versions of Firefox and Thunderbird(They run faster for me), install MPlayer and VLC(MPlayer for the firefox plugin and VLC because it rocks), get either Banshee or now Exaile for my media player, and of course install all of the necessary codecs and get flash.  And update to the newest version of Gaim.

---

### Post by kevinlang21 on 2006-12-30
easy ubuntu
usp
kiba
beryl
wallpaper

---

### Post by lucky_chouhan on 2006-12-30
When i installed fresh ubuntu first thing i am configure my adsl then add some programs for my my audio and video, desklet, themes etc.

---

### Post by redDEADresolve on 2006-12-30
stay up for 8 hours getting everything you guys mentioned setup and enjoying every minute of it.

---

### Post by Atomic Dog on 2006-12-30
Remove ipv6
setup the UI thye way I want it.
install wifiRadar
install automatix2

---

### Post by DJ_Peng on 2006-12-31
My first things once I got Ubuntu reinstalled after I accidentally FUBAR'd it was to install Firefox 2 and the Thunderbird 2 beta from Mozilla and point them to my profiles which I store on a separate drive. Of course since I store my custom set up page via a web server to be able to use the same file in both Ubuntu and Windows I have to get Apache set up next. Then I grab Amarok (and MySQL to hold the library database) and go for my multimedia codecs. After that I grab Wine (from the host, not the repository) and IEs4Linux to get my Dreamweaver and Fireworks available for working on a couple websites I manage.

---

### Post by handy on 2006-12-31
I set up the partitions how I want them, they stay that way now:

**/ = 10Gb** the rest of this 80Gb drive is a scratch disk.

**/home = 34Gb** it's own high speed drive.

**/var = 3.9Gb** a different drive too (I don't really need a seperate **/var**, but I have other drives & plenty of space so it protects me if something goes really strange; logs & tmp files can't fill up my **/** partition... )

**/swap = 2Gb** which is never used, I have 2Gb of RAM.  /swap is on the same drive as /var, the rest or this 34Gb Raptor is for storage too.

**After install:**

Do the about:config thing & kill IPv6 in Firefox, or I can't browse.

Then prepend my DNS server's addresses in;

**/etc/dhcp3/dhclient.conf**

or I can't access the repo's or Automatix.

Then I enable all the repo's in Synaptic, Reload & update all.

Then install Automatix, & add some bits & pieces the easy way. (Including the nVidia drivers)

Edit xorg.conf so my monitor's refresh rates are correct, & add some screen resolutions; I like to run at 1600x1200 & 1280x1024.

Check that Alsa is default sound manager, then run AlsaMixer & configure, also add AslaMixer to the Menu.

Tweak the GUI a little, adding things like UT2k4 to the menu if I have to...

So that I can manually use CPU frequency scaling, via the *CPU Monitor Preferences* display which I place in the top Panel, I enter the following in the Terminal:

**sudo chmod +s /usr/bin/cpufreq-selector**

Reinstall Cedega from the latest install files that I keep in /home, (as well as backed up) & get Guild Wars running.

Now life is good... :KS


All of the above is as easy as pie ***_now_***.  It took months to garner the above meager amount of knowledge!  True I have learned more than just that, but I have put a lot of time in on these forums.  It is so often quite difficult for new user's to setup Ubuntu, & if they don't have a technical bent it must feel very frustrating for many of them.  I'm glad I don't use wireless... :rolleyes:

---

### Post by karachuonyo on 2007-01-08
First thing enable the universe and multiverse repo's, apt-get update and upgrade. install automatix then install the nvidia drivers, codecs,flash plugins, google earth an a few games. log into forum and enjoy my freedom from gates. Takes normally 1 hour from inserting the install cd to have my system as i like :D

---

### Post by firezip on 2007-01-08
Steps of an Ubuntu

[LIST=1]
[*]Partition 
[*]Install
[*]Update Ubuntu
[*]Install Automatix and Automatix Bleeder
[*]Install Nvidia drivers & reboot
[*]Install software
[*]Transfer Files
[*]Customise Ubuntu look and feel
[*]Sit back & relax :)
[/LIST]

---

### Post by rbhigday on 2007-01-08
Jump up and down and be happy cause it installed!!!!

Hey I'm a newbie, sometime it desn't work :)

---

### Post by abijah on 2007-01-08
Lay down in the fetal position and cry!

I have a love – hate relationship with Ubuntu/Linux.

I really don’t want to do all this hacking and installing crap.

Somebody said
> stay up for 8 hours getting everything you guys mentioned setup and enjoying every minute of it. 

Well I don’t love it! 

Now wait, I’m using this VistaCrap and I’m pissed that I still have to bend over backwards to get my devices/drivers to work with it.  I mean, ppl are going to be paying money for that OS.

Then, there’s Ubuntu, it’s free and you can’t really complain to anyone about what’s been handed to you.

I’m sick of these OS.  When are these developers going to really keep the novice users in mind?

I wish I could afford an Apple.

---

### Post by doobit on 2007-01-08
It took me 25 minutes the last time to do a complete Xubuntu install using the alternate install CD. When my wife's XP machine threw a disk it took me around 8 hours over three days, to format, install, and install software and drivers.

---

### Post by CCBalla10 on 2007-01-10
Install Automatix2

---

### Post by Iyatos on 2007-01-10
install xmms, then check for python updates

---

### Post by richpor_1 on 2007-01-10
Installed Beryl - love the eye candy! 
Gdeslkets
Automatix
Restricted Formats (DVD,MP3)

and most of the other goodies to get the system to "functional level"

Then gave up and went back to XP cause' no matter what I do, I can't get my ATI TV (](*,) ](*,) ) to work and can't seem to scan and fax...

Aside from that, it's okay and still on my pc as a dual-boot!

---

### Post by glabouni on 2007-01-12
1st thing I do is editing apt repositories and running apt-update
while this is in progress, I'm getting opera web browser and removing firefox icons and any references from menus and preferred applications.
now that I have my favorite web browser at hands, I usually surf the web while apt-getting packages, and bitching about not knowing how to remove firefox without breaking ubuntu-desktop package. 

once I got all safe and stable packages I want, and am done with bitching I reboot using sysrescuecd and partimage my brand new installation, then reboot into ubuntu and start apt-getting all those not so safe packages, and surf the web (bitching once per install is enough) looking for way to fix any problem or for specific documentation. 

when I'm happy with this I do a another sysrescue reboot and partimage, and I'm now ready to use my brand new installation.


> **abijah said:**
> I really don&#8217;t want to do all this hacking and installing crap.
(...)
Then, there&#8217;s Ubuntu, it&#8217;s free and you can&#8217;t really complain to anyone about what&#8217;s been handed to you.

I&#8217;m sick of these OS.  When are these developers going to really keep the novice users in mind?

I wish I could afford an Apple.

for those who don't want to do installing crap, then a console is gonna suit you, no installing required !
the other way around is to have someone do it for you, my guess is there are many youngsters who would be happy to do it for a little something in return.

ubuntu is not the one and only linux flavour around, feel free to try another one. btw complaining is always possible, but it's definitely not the best way to be heared and obtain what you want.

Computers were never made nor intended for people who don't intend to learn how to use it and invest personal effort into it. 
For those who are not ready to do this, my advice would be: don't fall for marketing crap, you can live a happy and fulfilling life *without* a computer.
An OS that would be usable out of the box by anyone to do anything doesn't exist (yet), bear that in mind, and if you do decide to buy your own computer anyway, you are now part of the consumer force, make wise use of your consumer power to make things evolve the right way.

---

### Post by Patrick-Ruff on 2007-03-20
automatix isn't the solution for everything. I recently replaced windows with ubuntu on my main OS . . . I'm just waiting for feisty now. Edgy has a lot of glitches in network related things that just irritate the hell out of me.


on this one I set up beryl, wine, my fonts (omg, took soo long) 


and a ton of programs that I'd rather not type out.  


oh and . . . I'm still not happy with it ;).

---

### Post by karellen on 2007-03-20
setup my pppoe network connection :)

---

### Post by RandomJoe on 2007-03-20
First thing I do after the base system is installed is to enable "Focus Follows Mouse"!

Otherwise I start cursing shortly after opening more than one window... ;)

---

### Post by Adamant1988 on 2007-03-20
Install all of my apps and then start importing my backed up data and songs.

---

### Post by Motoxrdude on 2007-03-20
Download 600mb of updates, install my favorite apps, mount my drives to the home folder, import my music, and enjoy.

---

### Post by Patrick-Ruff on 2007-03-20
I wish I didn't like games at all . . . the only game I really enjoy is Warcraft 3 and it /really/ sucks to play under cedega . . . wine is alright but there are many issues I have that nobody seems to have answered. 

guess I have a weekend of tweaking comming up . . . I wish feisty was out.

---

### Post by Kingsley on 2007-03-20
I found myself in this situation a few days ago. The first thing I do is fix my repositories to my liking and then download tons of updates/programs, especially KDE 3.5.6, Firefox, and ntfs-3g. Then I install my favorite icons set theme and change the system colors.

---

### Post by qalimas on 2007-03-20
knetworkmanager, kdewebdev, codecs, koffice

Then I update everything, then theme it the way I want.

---

### Post by beercz on 2007-03-20
Restore my previously backed up data

---

### Post by Frak on 2007-03-20
Install Crossover, then MS Office.

---

### Post by noneofthem on 2007-03-20
First I do a system update. Then I normally install all the essential stuff like multimedia codecs, my everyday applications and everything else I need to have everything working. While everything is downloading and installing I change the look of the desktop (wallpaper, theme, move icons around etc.. That's basically it. This normally doesn't take longer than 30 or 40 minutes.

---

