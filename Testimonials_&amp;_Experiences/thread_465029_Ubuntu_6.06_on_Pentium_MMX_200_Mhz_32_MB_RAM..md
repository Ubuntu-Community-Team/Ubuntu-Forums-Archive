---
title: "Ubuntu 6.06 on Pentium MMX 200 Mhz 32 MB RAM."
date: 2007-06-05
forum: Testimonials &amp; Experiences
---

### Post by kagashe on 2007-06-05
Hi,

I am thrilled and excited to report that I am posting this thread on Opera browser from a machine of Pentium MMX 200 Mhz 32 MB RAM on which Ubuntu 6.06 with WDM Display Manager and JWM Window Manager is installed. This is how I did the installation.

This machine has Windows 98 with two partitions c: and d:. I emptied partition d: while in Windows. Although the machine has CD-R it could not boot from CD. I copied the SmartBootManager (sbm.bin) file from Ubuntu CD and used RawWrite utility to make the SBM floppy. I put the floppy and Ubuntu 6.06 Alternate Install CD in the drives and rebooted.

I proceeded to install the "server". I got a warning that the RAM was too low and atleast 36 MB was required but I ignored it. The machine hanged at Networking stage. I decided to make another attempt and pressed "Esc" key at Networking stage. I resized hda2 (d: of Windows) partition to create swap partition.

The installation took lot of time but I could install the server.

Then I looked at the Ethernet card. It was Intel card which is suppossed to have problems in Linux. After reading a few posts on this forum (while in Windows) I decided to try the following command:
> sudo dhclient eth0
I got success in connecting to the router.

I decided to go for UbuntuLite desktop (from [http://blueeyedcreature.net](http://blueeyedcreature.net) repository) through apt-get. Th downloading of packages was smooth since it is 2 Mbps connection but installation took a few hours.

I got flickering screen (which I was expecting). I switched to terminal and reconfigured X through:
> sudo dpkg-reconfigure xserver-xorg
I selected the least resolution 640x480 with 16 color depth. I entered the horizontal and vertical frequency range for the monitor. I restarted WDM through:
> sudo /etc/init.d/ wdm restart

The display was OK but the mouse was not working. Then I discovered that the mouse was connected to serial (COM 2) port. Since there was no provision to configure the mouse in dpkg-reconfigure I had to edit the configuration file through:
> sudo nano /etc/X11/xorg.conf
with the following:
Mouse "Device" "/dev/ttyS1"
             "Protocol" "auto"

I could login through WDM to IceWM window manager. I tried Dillo and Firefox but was not satisfied with the speed. Then I installed Fluxbox window manager and got almost the same results. I downloaded and installed Opera and found it faster than Firefox.

Next day I tried Puppy Linux Live CD and was impressed with the speed with Dillo. Seamonky (the other web browser in Puppy) took lot of time to load and I killed the process. I found that the speed was due to the Window Manager (JWM).

I installed JWM and found a small Start Menu, opened terminal and typed "Opera" and entered.

I am now posting this thread from Opera and very happy.

Now how do I add the menu items like they are appearing in IceWM and Fluxbox?

kagashe

---

### Post by patrick295767 on 2007-06-05
(I would recommand you just sarge for such machine)
(Dont try to use ubuntu with such configuration, Id advice you)
  
or damn small linux
or delilinux

---

### Post by jgrabham on 2007-06-05
Stand outside my window - A 700mhz P3 pc might be flying out of it in a minute!  :]

---

### Post by forcesofhabit on 2007-06-05
I too would recommend DeliLinux or Damn Small Linux.
I'm not too familiar with JWM, but you may want to try DWM which I think is a little more light weight.
Good luck!

---

### Post by dimeotane on 2007-10-15
Great work Kagashe!   I'm following in your footsteps.  I've put Ubuntu 7.04 feisty on an dell inspiron 3000 notebook.  It's a Pentium 200 with 64mb ram and 4 gig hard drive. 

I'm trying out openbox as the window manager.  I wasn't sure what browser to try other than elinks, or links2.  I've used dillo before on legacy systems.  I will try your suggestion for opera using  JWM. 

I'd like to find a list of packages in ubuntu that work on low end systems.  Know of any?  Perhaps we can put one together if it still hasn't been done yet.

---

### Post by kagashe on 2007-10-16
> **dimeotane said:**
> Great work Kagashe!   I'm following in your footsteps.  I've put Ubuntu 7.04 feisty on an dell inspiron 3000 notebook.  It's a Pentium 200 with 64mb ram and 4 gig hard drive. 

I'm trying out openbox as the window manager.  I wasn't sure what browser to try other than elinks, or links2.  I've used dillo before on legacy systems.  I will try your suggestion for opera using  JWM. 

I'd like to find a list of packages in ubuntu that work on low end systems.  Know of any?  Perhaps we can put one together if it still hasn't been done yet.
There are two groups working on making Ubuntu work on low end systems.
[Ubuntulite]("http://groups.google.co.in/group/ubuntulite?hl=en")
[Fluxbuntu]("http://www.google.co.in/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Ffluxbuntu.org%2F&ei=0FQUR9GwA52UswLhnJTSCQ&usg=AFQjCNFVbQVIdSzCAp3lMIdGJpbzt42_aA&sig2=j2p2trqM6fmIvK6dZKJUGA")

You will find the list on [ubuntulite]("http://groups.google.co.in/group/ubuntulite?hl=en") which is a Google group.
Fluxbuntu site is going to launch version 7.10 immediately after the launch of Gutsy.

You should also try Puppy.

You have nice blog at wordpress,

kagashe

---

### Post by Kowalski_GT-R on 2007-10-16
Always a great read when you post, kagashe,

good job, very interesting.

I ,myself, am waiting for Fluxbox. Installation on a 233Mhz/64Mb pc.

ciao,


Andre

---

### Post by dimeotane on 2007-10-17
> Now how do I add the menu items like they are appearing in IceWM and Fluxbox?
have you tried installing the package "menu" or "menu-xdg" someone suggested that installed with blackbox.  I find new menu items show up in the blackbox menu after installing a new package.  

Although it has a minimalist look, last I checked into the fluxbuntu distro (spring 07) it didn't seem very lite for legacy systems.  I thought the requirements were 128meg or more. 

> 
 Welcome to Fluxbuntu!
 Minimum Requirements:
 CPU: Pentium 2 233MHz (maybe less)
 RAM: 128 MB
 HardDrive Space: 2GB (1.2GB Installed)


I'm so happy to cram a basic ubuntu system into less than 1 gig on the hard drive, and running at a nice speed with only 64mb on a 200mhz pentium.   

It's taking me a while to learn how to configure openbox into a nice gui though.    I wish there was a package that would set up a basic openbox system which is preconfigured.

I'm also wishing there was a list somewhere that has all the main packages which will run on older legacy systems.

I started to install the ubuntu-lite desktop package until I read that it would take another 400 meg + for a few dozen more packages I don't really want or need.    I want ultra lite!

Right now the base Ubuntu is only a half gig...  and openbox is adding only a few more megs.   

 some good and lightweight packages for a Pentium 200mhz are:

** file managers:**
  pcmanfm
  thunar
  rox-filer
  xfe

**editors:**
leafpad or mousepad 

**IRC chat:**
weechat-curses
irssi

**messenger:**
centericq

**system stats:**
htop
conky

[B]games:
[/B] (for the kids & young at heart)
xscavenger
circuslinux

**RSS News reader**
raggle

**webbrowser**
links2
elinks
dillo


(more to follow)...

---

### Post by eeried on 2007-11-08
What a good job you've done, Kagashe! 

Is JWM lighter than Fluxbox?

---

### Post by kagashe on 2007-11-08
> **eeried said:**
> What a good job you've done, Kagashe! 

Is JWM lighter than Fluxbox?Yes.

---

### Post by eeried on 2007-11-09
Sorry I forgot to ask in my previous post: 
Which is lighter: JMW or openbox?

BTW I once used PuppyLinux on an AMDk6-2 300MHZ, 64Mo RAM and it was very slow: Seamonkey would crawl along. I think it needs installing so it runs on a swap partition.

Dillo is no longer maintained, I've read, and doesn't support CSS. I like lynx but people don't usually, understandably.

Unfortunately, UbuntuLite nor Fluxbox seem really the right solution.

I'll try installing light-weight versions of Ubuntu as some of you have done. Up to now I've managed to get old memory sticks, which is a quick solution when you can grab some, and I've been running Puppy.

Now for the less easy way!

---

### Post by kerry_s on 2007-11-09
you should try debian etch/lenny base install jwm build up. debian is way faster on the old stuff.

for jwm menu, copy /etc/jwm/jwmrc to your ~/.jwmrc and modify as needed/wanted. jwm is very flexable, there are a lot of different ways to go with the menu, once your understand the xml format.

i'm running version 2..0.1-1 on debian lenny/sid.

my menu->

```

<?xml version="1.0"?>

<JWM>

<StartupCommand>
xset dpms 0 0 300
xrdb -merge ~/.Xdefaults
conky
</StartupCommand>

   <IconPath>
      $HOME/.icons
   </IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops count="4">
      <!-- <Background type="command">eval `cat $HOME/.fehbg`</Background> -->
      <Background type="solid">black</Background>
   </Desktops>

   <!-- The root menu, if this is undefined you will not get a menu. -->
   <!-- Additional RootMenu attributes: onroot, labeled, label -->
   <RootMenu height="48" onroot="3">
      <Program icon="term.png" label="Terminal">xterm -rv -fn 9x15</Program>
      <Program icon="home.png" label="File Manager">emelfm</Program>
      <Program icon="www.png" label="Web Browser">iceweasel</Program>
      <Separator/>
       <Program icon="synaptic.png" label="Synaptic">xterm -g 50x0+350+350 -e sudo synaptic</Program>
      <Separator/>
      <Restart label="Restart" icon="restart.png"/>
   </RootMenu>

   <RootMenu height="32" onroot="1">
      <Exit label="Exit" confirm="false" icon="exit.png"/>
         <Program icon=".png" label="Reboot">sudo reboot</Program>
         <Program icon=".png" label="Shutdown">sudo halt</Program>
   </RootMenu>

   <RootMenu height="32" onroot="2">
      <Desktops label="Desktops"/>
   </RootMenu>

   <!-- Additional tray attributes: autohide, width, border, layer, layout -->
   <Tray  x="0" y="-1" height="32">
      <TrayButton label="Menu">root:3</TrayButton>
      <TrayButton icon="desktop.png">showdesktop</TrayButton>
      <TrayButton label="D#">root:2</TrayButton>
      <TaskList/>
      <Dock/>
     <TrayButton icon="mute.png">exec:amixer sset PCM toggle > /dev/null</TrayButton>
     <TrayButton icon="zero.png">exec:amixer sset PCM 3%- > /dev/null</TrayButton>
      <TrayButton icon="max.png">exec:amixer sset PCM 3%+ > /dev/null</TrayButton>
   </Tray>

   <Tray layer="0" x="10" y="10" layout="vertical" width="128" height="0">
      <TrayButton label="Programs">exec:</TrayButton>
      <TrayButton icon="term.png">exec:xterm -rv -fn 9x15</TrayButton>
      <TrayButton icon="home.png">exec:emelfm</TrayButton>
      <TrayButton icon="www.png">exec:iceweasel</TrayButton>
   </Tray>

   <Tray layer="0" x="140" y="10" layout="vertical" width="128" height="0">
      <TrayButton label="Adminastrator">exec:</TrayButton>
      <TrayButton icon="synaptic.png">exec:xterm -g 50x0+350+350 -e sudo synaptic</TrayButton>
   </Tray>

   <Tray layer="0" layout="vertical" x="611" y="400" halign="right" width="0">
      <Pager/>
     <TrayButton label="Screen Off">exec:sleep 3;xset dpms force off</TrayButton>
   </Tray>

   <!-- Visual Styles -->
   <WindowStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
         <Text>white</Text>
         <Title>#70849d:#2e3a67</Title>
         <Corner>white</Corner>
         <Outline>black</Outline>
      </Active>

      <Inactive>
         <Text>#aaaaaa</Text>
         <Title>#808488:#303438</Title>
         <Corner>#aaaaaa</Corner>
         <Outline>black</Outline>
      </Inactive>
   </WindowStyle>

   <TaskListStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <ActiveForeground>black</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>gray70:gray90</Background>
   </TaskListStyle>

   <TrayStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Background>gray90</Background>
      <Foreground>black</Foreground>
   </TrayStyle>

   <PagerStyle>
      <Outline>black</Outline>
      <Foreground>gray90</Foreground>
      <Background>#808488</Background>
      <ActiveForeground>#70849d</ActiveForeground>
      <ActiveBackground>#2e3a67</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Foreground>black</Foreground>
      <Background>gray90</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
   </MenuStyle>

   <PopupStyle enabled="false">
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <!-- Double click speed (in milliseconds) -->
   <DoubleClickSpeed>400</DoubleClickSpeed>

   <!-- Double click delta (in pixels) -->
   <DoubleClickDelta>2</DoubleClickDelta>

   <!-- The focus model (sloppy or click) -->
   <FocusModel>click</FocusModel>

   <!-- The snap mode (none, screen, or border) -->
   <SnapMode distance="10">border</SnapMode>

   <!-- The move mode (outline or opaque) -->
   <MoveMode>outline</MoveMode>

   <!-- The resize mode (outline or opaque) -->
   <ResizeMode>outline</ResizeMode>

   <!-- Key bindings -->
   <Key key="Up">up</Key>
   <Key key="Down">down</Key>
   <Key key="Right">right</Key>
   <Key key="Left">left</Key>
   <Key key="h">left</Key>
   <Key key="j">down</Key>
   <Key key="k">up</Key>
   <Key key="l">right</Key>
   <Key key="Return">select</Key>
   <Key key="Escape">escape</Key>

   <Key mask="A" key="Tab">nextstacked</Key>
   <Key mask="A" key="F4">close</Key>
   <Key mask="A" key="#">desktop#</Key>
   <Key mask="A" key="F1">root:1</Key>
   <Key mask="A" key="F2">exec:gmrun</Key>
   <Key mask="" key="Print">exec:scrot %T.jpg</Key>
</JWM>

pic->


```

---

### Post by eeried on 2007-11-09
> debian is way faster on the old stuff.
it certainly is, but making ubuntu speed on old machines is a challenge. But yes, i thought I would install Debian  though it's less easy to install a printer, mount stuff -- the command line's allright but some people may not like it. It all depends who uses the old computer.

I use debian Etch + flubox and a rather basic install,  on a PII 400MHZ, 256Mo RAM, and Iceweasel never flinches even with many tabs open, while Ubuntu Dapper was rather slow. But that's a luxury machine.

---

### Post by kerry_s on 2007-11-09
> **eeried said:**
> it certainly is, but amking ubuntu speed on old machines is a challenge. But yes, i thought I would install Debian  though it's less easy to install a printer, mount stuff -- the command line's allright but some people may not like it. It all depends who uses the old computer.

I use debian Etch + flubox and a rather basic install,  on a PII 400MHZ, 256Mo RAM, and Iceweasel never flinches even with many tabs open, while Ubuntu Dapper was rather slow. But that's a luxury machine.

printer just install cups. for auto-mounting install ivman. it's as easy or hard as you make it. ubuntu and debian have the same applictions, ubuntu is just a snap shot of sid, which gets really old fast, with debian you just upgrade.

mines a 450mhz 256ram, nothing is slow on mine. i'm just running it as basic internet with iceweasel and all the stuff i need to watch vids and movies, but i can easily run heavier apps like open office, acroread(aka:adobe reader8) ), etc...

---

### Post by kagashe on 2007-11-09
> **eeried said:**
> Sorry I forgot to ask in my previous post: 
Which is lighter: JMW or openbox?I have not tried openbox but my guess is JWM would be lighter..
> BTW I once used PuppyLinux on an AMDk6-2 300MHZ, 64Mo RAM and it was very slow: Seamonkey would crawl along. I think it needs installing so it runs on a swap partition.Puppy boots on less than 128 MB RAM but you are not supposed to run Seamonkey till you save the Puppy files somewhere on hard disc for which installation is not necessary. You just reboot once again after saving your session. While you save Puppy automatically creates swap which is used on next reboot and you can now run Seamonkey and see the difference.

kagashe

---

### Post by eeried on 2008-01-11
I run Puppy 2.17 the way Kagashe describes (minimal install on the HDD), end it does make a difference from running on RAM. But this machine has 128MO RAM which is a lot really. It'es an AMD-K6 230MHZ which I have boosted with more RAM, a PCI video card (no AVG slot) to replace the original onboard card, an ISA sound Card (Puppy configures it on its own), and a  PCI  ethernet card.

So I suppose I could install either Debian or Ubuntu (I just need to make a note of the sound card ID to make it work with Debian or Ubuntu).

We've been given a Pentium 150, though I haven't looked at it much there's probably 32MO RAM and it's probably going to be difficult to install anything else than Puppy. there's no ethernet card which is the main problem for a customized install. If the CD-drive works I'll make do with what's available on the CD (Debian or Ubuntu).

What we would really need is a libre light browser -- Opera may be lighter than firefox or Seamonkey but I won't install it. Dillo is abandoned, and lynks however good it is may not be a pleasant experience for most people.

cheers,

---

### Post by K.Mandla on 2008-01-11
Moved to Testimonials and Experiences.

---

### Post by armandh on 2008-01-11
there is an alt DSL linux distro for older equipment 
that I booted and ran live on a 166 MHZ IBM thinkpad 
I cant remember if the mem was 24 or 32
I did it just to test

---

### Post by eeried on 2008-01-21
> alt DSL linux distro for older equipment 

I'll have a go when I can find the download link.

What I've just done, after finding some doc on the French-speaking wiki, is install a minimal Feisty from the alternate CD, You choose "install a command-line system", and when it's done, you can install the following:

 ```
 sudo apt-get install wdm jwm xfonts-base xserver-xorg
```

Now I have to learn how to fill in the JWM menu which doesn't even have vim, so I can't install anything else from X at least.

Here are the specs of this luxury retro-computer (Compaq Deskpro):

- RAM about 64MB
- Proc': celeron 300 MHZ 
there's an audio PCI card and an Nvidia Video VGA card.

I might even get away with Xfce!

---

### Post by eeried on 2008-01-22
Can't find seamonkey in the repos...

True, it's much better to install a minimal version of Debian on old machines because you have a better choice of software (iceape, probably, a lighter terminal than xterm though it is fast on JWM, etc.).

However what we need is a browser as light as Sylpheed-claws (email)

---

### Post by eeried on 2008-02-14
Hello,

Following some sound advice in this thread I've installed Debian Etch from the first CD, and Xfce and apps runs pretty well.

I was a bit disappointed no to get a screen where you can choose what to install, so  that you can install nothing, just the base system and then install exactly what you want. Instead of that, Debian-installer ran into low memory mode and installed XFCE, of its own accord.

However I'm getting rid of many things, like all print-related apps, and I'm installing Fluxbox and JWM, and uninstalling XFCE. Then I'll upgrade to lenny.

I tried installing a basic Ubuntu (from the menu install a command-line system or sth like that) with JWM, but the WDM login screen would fail to appear once and again, so I gave up on Ubuntu.

---

### Post by kerry_s on 2008-02-14
> **eeried said:**
> Hello,

Following some sound advice in this thread I've installed Debian Etch from the first CD, and Xfce and apps runs pretty well.

I was a bit disappointed no to get a screen where you can choose what to install, so  that you can install nothing, just the base system and then install exactly what you want. Instead of that, Debian-installer ran into low memory mode and installed XFCE, of its own accord.

However I'm getting rid of many things, like all print-related apps, and I'm installing Fluxbox and JWM, and uninstalling XFCE. Then I'll upgrade to lenny.

I tried installing a basic Ubuntu (from the menu install a command-line system or sth like that) with JWM, but the WDM login screen would fail to appear once and again, so I gave up on Ubuntu.


use the net installer, i always use it for custom installs->
[http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso)

when it comes to package selection, just uncheck both of them.

do you really need a login screen? i don't use 1, mine goes straight to the desktop.

**apt-get install rungetty**

edit your /etc/inittab
**1:2345:respawn:/sbin/rungetty tty1 --autologin user**
"user" is the log in name, example: --autologin bill

add a script to startx in ~/.bash_profile

[B]```
if [ `tty` = "/dev/tty1" ]; then
startx
fi
```[/B]


i also run etch/lenny custom, i do mine this way:
install etch base install with net installer
login as root
**apt-get install mc**
then i just change the etch src repos to lenny, i don't build anything so don't need them.
looks like this:
```
deb http://ftp.debian.org/debian/ etch main contrib non-free
deb http://ftp.debian.org/debian/ lenny main contrib non-free

deb http://security.debian.org/ etch/updates main contrib non-free
deb http://security.debian.org/ lenny/updates main contrib non-free

```

[B]apt-get update
apt-get dist-upgrade
[/B]

**apt-get install xorg synaptic jwm rox-filer leafpad**
reboot(ctrl+alt+delete)

log in as my user and do a little setup, set a solid background, the auto login, open synaptic and remove some stuff i don't want, etc...

then i start installing what i want.

currently working on what i call "the many faces of jwm", doing different setups that i can change to with a click and a restart.

i haven't done the gnome 1 yet, i only just came up with this idea yesterday, so i'm just getting the basics setup, later they will all look completely different, more to what those setups look like. it's a project. :lolflag:

i'm going to replace the openbox screen shot with the gnome 1, since there's nothing to see on the openbox 1 anyway, it's just rox pinboard with no icons.

---

### Post by eeried on 2008-02-15
Many thanks kerry_s for this how-to.

Yes, the net installer is precisely what I had in mind last night after wasting so much time removing this, adding this and so on.

For those who can read French there's an excellent step-by-step howto to understand and install only what you want in Debian, and reconfigure things as you like: [http://formation-debian.via.ecp.fr/](http://formation-debian.via.ecp.fr/) (updated 2007)

> do you really need a login screen? i don't use 1, mine goes straight to the desktop.

On that computer this will be a good idea not to bother with a login screen or login in at all. WDM doesn't allow me to shutdown as a simple user though there must be some way of changing this behaviour.

> add a script to startx in ~/.bash_profile
```
if [ `tty` = "/dev/tty1" ]; then
startx
fi
```


In Ubuntu Gutsy (I'm not near the old machine at the moment), I can see the file .profile, and a few .bash* files; one of them is ".bash_logout". Can I make a new file called "bash_login", or should I use one that already exists, like .profile?

On that old machine, I think I'd better stick with Etch, and just upgrade Iceweasel to Lenny, because updates and upgrades take a long time. That computer will be used for surfing, and writing a bit with Abiword and Geany -- which is I think better than leafpad.

I'll stick to free software only and install Gnash-plugin instead of Flash, or no falsh plugin at all if Gnash is still buggy.

BTW I installed rxvt-unicode-lite (much lighter than xterm) on both Gutsy and Debian, but I can't find an entry in the menus nor in /usr/bin. I'd like to make an icon in the Gusty taskbar.

The problem with synaptic is that it's very slow on that machine but Aptitude is a bit confusing to me. 

Lastly I'll have to install the language packages for French, and make sure all the software are in French. I seem to remember from my Libranet days there's a "locale" tool that should do the trick.

---

### Post by kerry_s on 2008-02-15
> In Ubuntu Gutsy (I'm not near the old machine at the moment), I can see the file .profile, and a few .bash* files; one of them is ".bash_logout". Can I make a new file called "bash_login", or should I use one that already exists, like .profile?

gutsy's different those won't work for gutsy, debian only.

> 
I'll stick to free software only and install Gnash-plugin instead of Flash, or no falsh plugin at all if Gnash is still buggy.


if it's that slow, i'd go without.


> BTW I installed rxtv-unicode-lite (much lighter than xterm) on both Gutsy and Debian, but I can't find an entry in the menus nor in /usr/bin. I'd like to make an icon in the Gusty taskbar.


it should be> rxvt <just put that for the command.

> The problem with synaptic is that it's very slow on that machine but Aptitude is a bit confusing to me.

Lastly I'll have to install the language packages for French, and make sure all the software are in French. I seem to remember from my Libranet days there's a "locale" tool that should do the trick.

ditto, synaptic is the best, i always uninstall aptitude, hate it.
yep, just grab the french versions of what you want.
example: instead of getting the regular iceweasel, grab the iceweasel-I10n-fr

debian is very multilingual, you should be able to find the application in french or the program can choose the language.

---

### Post by eeried on 2008-02-19
hello,

I've installed a very bare Debian on that old machine and I think it's easier than trying to install a bare version of Ubuntu.

I've installed through net install: the CD is about 150MB. When the screen gives you the choice of choosing various installations (standard, desktop, server, etc), I simply made sure to unchecked any installation at all so that the installer installs only the base system.

After rebooting, I removed the "non-free" repos, changed etch to lenny, and updated and upgarded then did a dist-upgradeI installed a few packages, and configured what was necessary. I did this bit by bit because it takes too much resources if you install several packages at one go.

I removed the old kernel (linux-image that is)

I installed vim and lynx, and exim, and postfix (not sure it's useful, as I won't install a mail-client and  mail will be read, etc on webmails only). I removed nano and w3m. Then after installing xorg, and configuring it, I installed JWM, firefox, geany, rxvt.

Just make sure you empty  /var/cache/apt/archives : ```
# apt-get clean
``` if your HDD is small (ours is 4GB).

JWM is fun to modifiy (I've got nice colours on the windows now) though I still have to add icons (I suppose I ought to type the full path like /usr/share...), and some background color, and get familiar with JWM generally.

kerry_s, you were right about Flash: no use adding a plugin (I chose Gnash), since Flash makes Iceweasel very slow.

df -h outputs less than 600MB. very satisfactory!

However, Iceweasel is still in English.

I'll probably add Abiword, and Gcompris and Tuxtype, unless that's too big. In that case, we can use a version of puppy-Linux Live-CD  that comes with both packages (Toutou-Edux 2.17.1).

I hope to add more RAM  if I can find some but still Debian makes a good job. I really like the way Debian installs a sound base system and then enables you to add just what you want. ubuntu seems to have more fluff and floatsam.

Next step is to try and make a CD out of this installation so I can install this customized version on another computer if necessary.

BTW is it possible to remove some bits of Xorg like wacom?

---

### Post by kerry_s on 2008-02-19
yeah, just consider the first couple of times as practice. once you get use to the surroundings it gets easier. you'll figure out ways to trim even more. i'm at 490mb without firefox cache, i've dropped my boot up ram usage from just under 24mb to just under 19mb.

> BTW is it possible to remove some bits of Xorg like wacom?

yes, i remove alot of xorg stuff, vid drivers, 100,75,cyrillic fonts, even xorg went. lol

pic->

---

### Post by eeried on 2008-02-19
Your JWM desktop looks very nice, kerry_s! Congratulations! and many thanks for the info about how to trim Xorg.

---

### Post by kerry_s on 2008-02-19
> **eeried said:**
> Your JWM desktop looks very nice, kerry_s! Congratulations! and many thanks for the info about how to trim Xorg.

thanks, that's my jwm apple style setup, kept 4 and dropped 2, i had rox pinboard with icons and without icons.

let me know if you need help with yours, sometimes the xml setup can be tricky.

here's what i call kde style & gnome style, the jwm style is pretty much the stock, so you already know what that looks like. :)

i'll attach my 4 jwm setups, just to let you know i've already taken out the spaces and compressed some down to single lines,also removed comments, so it may look a bit confusing to you, the quest for speed, what can i say? 
:lolflag:

---

### Post by kerry_s on 2008-02-21
ooh, i just figured out jwm supports debian menu, so you can> apt-get install menu <then run> update-menus <and it will create the menu entries in /etc/jwm/jwmrc, then you just copy that menu(cp /etc/jwm/jwmrc ~/.jwmrc) and tweak it as you see fit. makes it easier at install time, since you can start with menu entries for what you have installed.

if you run> update-menus <as a regular user it will create a folder "jwmrc" in your home folder, that has the "jwmrc".

so for a clean install, we can do this->

apt-get install xorg jwm menu synaptic rox-filer leafpad
update-menus
reboot
log in as user
startx

and you should have jwm with a menu of what you have so far.
i wonder if we can just use the <Include> tag in .jwmrc?
i'll try it later, should be easy enough->

<JWM>
<Include>/home/user/jwmrc/jwmrc</Include>
</JWM>

something like that. :)

---

### Post by eeried on 2008-02-21
Many thanks kerry_s for the files which help me learn how to make menus. I've made  2 root menus, one with restart and exit, and a floating one with some apps and icons. It's real fun!

If I understand right you need feh just as in fluxbox if you want some background, don't you? 

i installed leafpad which is lighter than geany.

Still, kagashe made a  better job than I did because his machine is much less powerful than the one I have installed debian on: Kgashe's is 200MHZ, mine is 300MHZ, his has 32MB RAM, mine has 64MB RAM, and I can't say mine speeds really :-\

Well, I'm not finshed with it yet. So I'll report later :-)

Oh I knew about menu but it's nice editing a file. Well I'll try using menu then.

cheers

---

### Post by kerry_s on 2008-02-21
no you don't need feh for the background.
change this->
```
<Background type="solid">black</Background>
```
to
```
<Background type="image">whatever.png</Background>
```

this part tells it were to look
```
<IconPath>$HOME/.backgrounds</IconPath>
```

by default, it's only setup to look in "~/ .icons", i added "~/.backgrounds". you can change it to what ever you want though.

nice huh, jwm can do backgrounds and icons, without adding anything else to do it. :)

also if you want to use feh, you can change it like this->
```
<Background type="command">eval 'cat $HOME/.fehbg'</Background>
```

then just open your image up in feh and use feh's set background function.

feh will use resources though, jwm won't, with jwm no matter how many icon's/taskbars/backgrounds you add it uses the same amount of resources.

you can even set different backgrounds for each virtual desk and it won't use more resources, but it's a bit annoying to me. :)

```

<Background name="1" type="image">whatever.png</Background>
<Background name="2" type="image">whatever.png</Background>
<Background name="3" type="image">whatever.png</Background>
<Background name="4" type="image">whatever.png</Background>

```

look over the man pages, you might want some of things that i don't use->

```
jwm(1)                                                                  jwm(1)



NAME
       JWM - Joeâ€™s Window Manager


SYNOPSIS
       jwm [options]

DESCRIPTION
       JWM is a window manager for the X11 Window System.


OPTIONS
       -display display
              This option specifies the display to use; see X(1).

       -exit
              Exit JWM by sending _JWM_EXIT to the root window.

       -h
              Display a help message and exit.

       -p
              Parse the configuration file and exit.  It is a good idea to use
              this after making modifications to  the  configuration  file  to
              ensure there are no errors.

       -restart
              Restart JWM by sending _JWM_RESTART to the root window.

       -v
              Display version information and exit.


FILES
       /etc/jwm/jwmrc
              The default JWM configuration file.

       ~/.jwmrc
              Local configuration file. Copy the default configuration file to
              this location to make user-specific changes.


CONFIGURATION
       OVERVIEW
              Configuration of JWM is done by editing ".jwmrc".  This file  is
              XML  making it easy to edit, either by hand or programmatically.
              The example.jwmrc gives an example configuration  file.   Before
              restarting  JWM,  it is a good idea to run "jwm -p" to make sure
              the configuration file is free of errors.  Otherwise you may end
              up without a root menu.

       ROOT MENU
              The  root  menu  in JWM is the primary way of starting programs.
              It also provides a way to restart or exit  the  window  manager.
              The  outer  most  tag  is RootMenu. The following attributes are
              supported:

              onroot list
                     Determine which buttons on the root window  activate  the
                     menu.  This is a list of integers specifying buttons. The
                     default is "123".  Note that multiple root menus  may  be
                     specified by using different buttons for different menus.
                     The range of possible button values is 0 to 9  inclusive.

              height int
                     Height  of  each  menu  item  in  pixels. 0 indicates the
                     largest menu item will determine the height. The  default
                     is 0.

              labeled bool
                     Determines  if  a  label  appears at the top of the menu.
                     Default is false.

              label string
                     The label to display at the top of the menu.  Default  is
                     "JWM".

              Within the RootMenu tag, the following tags are supported:

              Menu
                     This  tag creates a submenu item. Any of the tags allowed
                     within the RootMenu  tag,  including  the  Menu  tag  are
                     allowed within this element. The following attributes are
                     supported:

                     height int
                             Height of each menu item in pixels.  0  indicates
                             the  largest menu item will determine the height.
                             The default is inherited from the parent menu.

                     label string
                             The label to use. No default.

                     icon string
                             The icon to use for this menu. No default.

                     labeled bool
                             Determines if a label appears at the top  of  the
                             menu. Default is false.

              Include
                     Include  the  contents of a file into the menu structure.
                     The file must start with a "JWM" tag. The file is  speciâ€
                     fied  by  the  text  of the tag.  If the text starts with
                     "exec:" then the output of a program is used.

              Program
                     The Program tag provides a way to start an external  proâ€
                     gram.  The  text in this tag is the command used to start
                     he program.  The following attributes are supported:

                     label string
                             The label to display. Default is the text of  the
                             tag.

                     icon string
                             The icon to use. No default.

              Separator
                     This  tag  simply  puts  a line in the menu allowing menu
                     divisions.  No text or attributes are used.

              Desktops
                     Add a desktop menu. This will add a submenu with  a  list
                     of  desktops that can be used to change the current deskâ€
                     top.  The following attributes are supported:

                     label string
                             The label to use for the  menu.  The  default  is
                             "Desktops".

                     icon string
                             The icon to use for this item. No default.

              SendTo
                     Add a "send to" menu to the menu. After selecting an item
                     from this menu, a window may be  selected  to  send  that
                     window to the selected desktop.  The following attributes
                     are supported

                     label string
                             The label to use. The default is "SendTo".

                     icon string
                             The icon to use for this item. No default.

              Stick
                     Add a stick/unstick window operation to the  menu.  After
                     selecting  this  item  a window may be selected to toggle
                     the  sticky  state  of  that   window.    The   following
                     attributes are supported

                     label string
                             The label to use. The default is "Stick".

                     icon string
                             The icon to use for this item. No default.

              Maximize
                     Add  a  maximize  window  operation  to  the  menu. After
                     selecting this item a window may be  selected  to  toggle
                     the  maximized  state  of  that  window.   The  following
                     attributes are supported

                     label string
                             The label to use. The default is "Maximize".

                     icon string
                             The icon to use for this item. No default.

              Minimize
                     Add a  minimize  window  operation  to  the  menu.  After
                     selecting  this item a window may be selected to minimize
                     that window.  The following attributes are supported

                     label string
                             The label to use. The default is "Minimize".

                     icon string
                             The icon to use for this item. No default.

              Shade
                     Add a shade/unshade window operation to the  menu.  After
                     selecting  this  item  a window may be selected to toggle
                     the  shaded  status  of  that  window.    The   following
                     attributes are supported

                     label string
                             The label to use. The default is "Shade".

                     icon string
                             The icon to use for this item. No default.

              Move
                     Add  a move window operation to the menu. After selecting
                     this item a window may be selected to move  that  window.
                     The following attributes are supported

                     label string
                             The label to use. The default is "Move".

                     icon string
                             The icon to use for this item. No default.

              Resize
                     Add  a resize window operation to the menu. After selectâ€
                     ing this item a window may be  selected  to  resize  that
                     window.  The following attributes are supported

                     label string
                             The label to use. The default is "Resize".

                     icon string
                             The icon to use for this item. No default.

              Kill
                     Add  a kill window operation to the menu. After selecting
                     this item a window may be selected to kill  that  window.
                     The following attributes are supported

                     label string
                             The label to use. The default is "Kill".

                     icon string
                             The icon to use for this item. No default.

              Close
                     Add a close window operation to the menu. After selecting
                     this item a window may be selected to close that  window.
                     The following attributes are supported

                     label string
                             The label to use. The default is "Close".

                     icon string
                             The icon to use for this item. No default.

              Restart
                     This  tag adds a menu item to restart the window manager.
                     The following attributes are supported:

                     label string
                             The label to use. The default is "Restart".

                     icon string
                             The icon to use. No default.

              Exit
                     This tag adds a menu item to exit the window manager.  If
                     text  is  present within this tag, it is interpreted as a
                     command to run when JWM exits. This can be used to  start
                     another  window  manager.   The  following attributes are
                     supported:

                     label string
                             The label to use. The default is "Exit".

                     icon string
                             The icon to use. No default.

                     confirm bool
                             Determine if  a  confirm  dialog  appears  before
                             exiting. Default is true.

                     Note  that  confirm dialogs can be disabled completely at
                     the compile-time.

       TRAYS
              One or more trays may be created via the  Tray  tag.   This  tag
              supports the following attributes:

              autohide bool
                     Allows  this  tray  to  hide  itself  when not activated.
                     Default is false.

              x int
                     The x-coordinate of the tray. This  may  be  negative  to
                     indicate an offset from the right of the screen.

              y int
                     The  y-coordinate  of  the  tray. This may be negative to
                     indicate an offset from the bottom of the screen.

              width int
                     The width of the tray. 0 indicates that the  tray  should
                     compute  an  optimal  width depending on what it contains
                     and the layout. 0 is the default.

              height int
                     The height of the tray. 0 indicates that the tray  should
                     compute  an  optimal height depending on what it contains
                     and the layout. 0 is the default.

              border int
                     The width of the border. The default is 1.  Valid  values
                     are between 0 and 32 inclusive.

              layer int
                     The layer of the tray. The default is 8. Valid values are
                     between 0 and 12 inclusive.

              layout { vertical | horizontal }
                     The layout of the tray. The default is horizontal.

              valign { fixed | top | center | bottom }
                     The vertical alignment of the tray. The default is fixed.

              halign { fixed | left | center | right }
                     The  horizontal  alignment  of  the  tray. The default is
                     fixed.

              Within this tag the following tags are supported:

              Clock
                     Add a clock to the tray. The text of this tag is  a  comâ€
                     mand  to run when the clock is clicked. This tag supports
                     the following attributes:

                     format string
                             The format of the clock. See strftime(3).

                     width int
                             The width of the  clock.  0  indicates  that  the
                             width should be determined from the length of the
                             text to be displayed.

                     height int
                             The height of the clock.  0  indicates  that  the
                             height should be determined from the font used.

              Dock
                     Add  a dock for system notifications. This can be used by
                     those programs that use  the  _NET_SYSTEM_TRAY_Sn  selecâ€
                     tion.  The  size of the Dock is dynamic based on the size
                     of the tray and the number of items contained.  Only  one
                     Dock is allowed per instance of JWM.

              Pager
                     Add  a pager to the tray. This tag supports the following
                     attributes:

                     width int
                             The width of the  pager.  0  indicates  that  the
                             width  should  be  determined from the tray. 0 is
                             the default.

                     height int
                             The height of the pager.  0  indicates  that  the
                             height  should  be determined from the tray. 0 is
                             the default.

              Swallow
                     Swallow a program into the tray. The  text  of  this  tag
                     gives  the command to run.  This tag supports the followâ€
                     ing attributes:

                     name string
                             The  name  of  the  program  to   swallow.   This
                             attribute is required.

                     width int
                             The  width  of the swallowed program. 0 indicates
                             that the width should be determined from the tray
                             and  size  requested  from  the program. 0 is the
                             default.

                     height int
                             The height of the swallowed program. 0  indicates
                             that  the  height  should  be determined from the
                             tray and the size requested from the  program.  0
                             is the default.

              TaskList
                     Add  a task list to the tray.  This tag supports the folâ€
                     lowing attribute:

                     maxwidth int
                             The maximum width of an item in the task list.  0
                             indicates no maximum.  The default is 0.

              TrayButton
                     Add a button to the tray. The text of this tag determines
                     what action to take when the button is clicked. The  folâ€
                     lowing actions are supported:

                     root:n
                             Show root menu n.  Note that the default TrayButâ€
                             ton action is root:1.

                     exec: string
                             Execute a command.

                     showdesktop
                             Minimize all windows on the current desktop.

                     This tag supports the following attributes:

                     label string
                             A label to display. No default.

                     popup string
                             A string to be displayed for a popup.  This  will
                             default to the value specified for label, if proâ€
                             vided. If neither popup nor label  are  specified
                             no popup will be shown.

                     icon string
                             An icon to display. No default.

       INCLUDES
              Other  configuration files may be included under the JWM tag via
              the Include tag.  The text of this tag specifies the location of
              an  additional  configuration  file. The path may be relative to
              the loacation JWM was started, an absolute path, or a path  refâ€
              erencing  an environment variable (using â€™$â€™). The format of the
              configuration file is the same as the main configuration file.

       GROUP SETTINGS
              Program groups allow one to specify options  which  apply  to  a
              group  of programs by name and/or class. A program group is creâ€
              ated with the Group tag. As many program groups can  be  created
              as  desired.  Within  the  Group tag the following tags are supâ€
              ported:

              Name
                     The title of a program to match to be in this group. This
                     field is case sensitive. a wild card, *, may be used.
              Class
                     The  window  class  for  a program to match to be in this
                     group. This field is case sensitive. A wild card, *,  may
                     be used.
              Option
                     An  option  for  this  group.  Possible options are given
                     below:

                     border
                             Causes windows in this group to have a border.

                     desktop:#
                             The desktop on which windows in this  group  will
                             be started.

                     icon:string
                             The icon to be used for windows in this group.

                             The  layer on which windows in this group will be
                             started.

                     maximized
                             Make windows in this group initially maximized.

                     hmax
                             Make windows in this group maximize horizontally.

                     vmax
                             Make windows in this group maximize vertically.

                     minimized
                             Make windows in this group initially minimized.

                     noborder
                             Causes  windows  in  this  group  to be displayed
                             without a border.

                     nolist
                             Causes the tray to ignore windows in this  group.

                     notitle
                             Causes  windows  in  this  group  to be displayed
                             without a title bar.

                     pignore
                             Ignore initial window position requested by  proâ€
                             gram.

                     shaded
                             Make windows in this group initially shaded.

                     sticky
                             Make windows in this group sticky.

                     title
                             Causes windows in this group to have a title bar.

       WINDOW STYLE
              The WindowStyle tag controls the look of window borders.  Within
              this tag, the following tags are supported:

              Font
                     The  font  used for title bars. See the FONTS section for
                     more information.

              Width
                     The width of window borders in pixels. The default is  4,
                     the minimum is 1, and the maximum is 32.

              Height
                     The height of window title bars in pixels. The default is
                     20, the minimum is 2, and the maximum is 64.

              Active
                     The colors used for the active  window.  See  the  COLORS
                     section  for  more  information  on colors. The following
                     tags are supported:

                     Text
                             The color of text on the title bar.

                     Title
                             The color of the title bar  (gradients  are  supâ€
                             ported).

                     Corner
                             The color of the corner handles.

                     Outline
                             The color of the window outline.

              Inactive
                     The colors used for inactive windows. See the COLORS secâ€
                     tion for more information on colors. The  following  tags
                     are supported:

                     Text
                             The color of text on the title bar.

                     Title
                             The  color  of  the title bar (gradients are supâ€
                             ported).

                     Corner
                             The color of the corner handles.

                     Outline
                             The color of the window outline.

       TRAY STYLE
              The TrayStyle tag controls the look of trays.  Within  this  tag
              the following tag is supported:

              Font
                     The  default  tray font to use. See the FONTS section for
                     more information.

              Foreground
                     The default foreground color. See the COLORS section  for
                     more information.

              Background
                     The  default background color. See the COLORS section for
                     more information.

       TASK LIST STYLE
              The TaskListStyle tag controls the look of task lists.  This tag
              supports the following attribute:

              insert mode
                     This determines how new items are added to the task list.
                     Valid options are left and right. The default is right.

              Within this tag the following tags are supported:

              Font
                     The font used for program names. See  the  FONTS  section
                     for more information.

              Foreground
                     The  foreground  color  of  the task list items.  See the
                     COLORS section for more information.

              Background
                     The background color of the task  list  items  (gradients
                     are supported).  See the COLORS section for more informaâ€
                     tion.

              ActiveForeground
                     The foreground color of an active item on the task  list.
                     See the COLORS section for more information.

              ActiveBackground
                     The  background  color of an active item on the task list
                     (gradients are supported). See  the  COLORS  section  for
                     more information.

       CLOCK STYLE
              The  ClockStyle  tag  controls  the look of clocks.  Within this
              tag, the following tags are supported.

              Font
                     The  font  used.  See  the   FONTS   section   for   more
                     information.

              Foreground
                     The  color  of  the text. See the COLORS section for more
                     information.

              Background
                     The background color. See the  COLORS  section  for  more
                     information.

       PAGER STYLE
              The  PagerStyle  tag  controls  the look of pagers.  Within this
              tag, the following tags are supported:

              Outline
                     The color of the outline  around  windows  shown  in  the
                     pager. See the COLORS section for more information.

              Foreground
                     The color of inactive windows shown in the pager. See the
                     COLORS section for more information.

              Background
                     The background color of inactive desktops  shown  in  the
                     pager. See the COLORS section for more information.

              ActiveForeground
                     The  color  of active windows shown in the pager. See the
                     COLORS section for more information.

              ActiveBackground
                     The color of active desktops shown in the pager. See  the
                     COLORS section for more information.

       MENU STYLE
              The  MenuStyle  tag  controls the look of the menus in JWM (this
              includes the root menu and window menus).  Within this  tag  the
              following tags are supported:

              Font
                     The  font  used  on  menus See the FONTS section for more
                     information.

              Foreground
                     The text color of inactive menu  items.  See  the  COLORS
                     section for more information.

              Background
                     The background color of inactive menu items. See the COLâ€â€
                     ORSsection for more information.

              ActiveForeground
                     The text color of active menu items.  See the COLORS secâ€
                     tion for more information.

              ActiveBackground
                     Text background color of active menu items (gradients are
                     supported).  See the COLORS section for more information.

       POPUP STYLE
              The  PopupStyle  tag  controls the look of popup windows such as
              those shown when the mouse sits over a task list item.  This tag
              supports the following attributes:

              delay int
                     The  delay  in  milliseconds before popups activate.  The
                     default is 600.

              enabled bool
                     Determine if popups are shown. Default is true.

              Within this tag the following tags are supported:

              Font
                     The font to use. See the FONTS section for more  informaâ€
                     tion.

              Outline
                     The  color  of the window outline. See the COLORS section
                     for more information.

              Foreground
                     The text color. See the COLORS section for more  informaâ€
                     tion.

              Background
                     The  background  color.  See  the COLORS section for more
                     information.

       FONTS
              Fonts for various parts of JWM are specified within a Font  tag.
              The  text  of  this tag determines the font to use.  This can be
              either a standard X font string or, if compiled  with  XFT  supâ€
              port, an XFT font string.

       COLORS
              Colors  for  various  parts of JWM are specified within specific
              tags (discribed above). Colors may either be hex triplets in RGB
              format  (for example, #FF0000 is red) or by a name recognized by
              the X server.  For components that support gradients, two colors
              may be specified separated by a colon.

       ICONS
              Icons for windows that donâ€™t supply an icon via the _NET_WM_ICON
              hint are located by searching the icon  search  path(s)  for  an
              icon  whose  name (minus the ".xpm" or ".png" extension) matches
              the instance name of the window  as  returned  in  the  WM_CLASS
              hint.  If  this  lookup  fails, a default icon is supplied. This
              icon will be displayed for the window on itâ€™s title bar  and  on
              the  task  list.  Icons that are not an appropriate size will be
              scaled. Square icons work best.

              For menu items, the icon path is searched for a match. the  icon
              specified  for  a  menu  item must be the exact name of the icon
              file with the extension.  If no match is  found,  a  blank  area
              will  appear  where  the  icon should appear.  If an icon is not
              specified for any menu item in a menu, no space  will  be  alloâ€
              cated for icons.

              Zero  or  more  IconPath tags may be specified. The text of this
              tag is assumed to be an absolute directory path to  a  directory
              containing  XPM,  PNG,  and/or  JPEG  icons.  When searching for
              icons, if multiple paths are provided, they will be searched  in
              order until a match is made.  Note that icon, PNG, JPEG, and XPM
              support are compile-time options.

       KEY BINDINGS
              Keyboard bindings in JWM are specified in Key tags.  Either  the
              key  or  keycode attributes must be specified to determine which
              key will cause an action. The optional attribute,  mask,  speciâ€
              fies what key mask, if any, must be in effect for the binding to
              match. Finally, the text  of  the  Key  tag  is  the  action  to
              perform.

              One  or  more  of  the  following key masks may be specified for
              mask:

                      A      The "Alt" key.

                      C      Control

                      S      Shift

                      H      Hyper

                      M      Meta

                      P      Super

              The key specified in the key attribute must contain a valid  key
              string for XStringToKeysym(3). These values are usually what one
              would expect (for example, the escape key is called "Escape").

              Valid actions for a key binding are:

                      up     Move up. Not grabbed.

                      down   Move down. Not grabbed.

                      right  Move right. Not grabbed.

                      left   Move left. Not grabbed.

                      escape Stop a move/resize or exit a menu. Not grabbed.

                      select Make a menu selection. Not grabbed.

                      next   Move  to  the  next  window  in  the  task  list.
                             Grabbed.

                     nextstacked
                             Move  to  the  next window in the stacking order.
                             Grabbed.

                      close  Close the active window. Grabbed.

                     minimize
                             Minimize the active window. Grabbed.

                     maximize
                             Maximize the active window. Grabbed.

                      shade  Shade the active window. Grabbed.

                      move   Move the active window. Grabbed.

                      resize Resize the active window. Grabbed.

                      root:n Show root menu n. Grabbed.

                      window Show the  window  menu  for  the  active  window.
                             Grabbed.

                     desktop
                             Switch to the next desktop. Grabbed.

                     desktop#
                             Switch  to  a  specific desktop. To use this, "#"
                             must be specified in the key section. The  number
                             1  to  the number of desktops configured are then
                             substituted for "#". Grabbed.

                     exec:command
                             Execute command. Grabbed.

                     restart
                             Restart JWM. Grabbed.

              Note that keys that are grabbed will not be available to  appliâ€
              cations other than JWM since JWM will interpret these. Also note
              that there are no default key bindings. Finally, it is  possible
              to bind multiple key combinations to the same action.

       MOUSE BINDINGS
              Any button (other than the scroll wheel) on the root window will
              bring up the root  menu  unless  otherwise  specified   via  the
              onroot  attribute  of  RootMenu. Scrolling up on the root window
              switches to the previous desktop and scrolling down switches  to
              the next desktop.

              The right button will show the window menu on the frame.

              The  left  button will resize if on the border or move if in the
              title bar.

              The middle button will move anywhere on the frame.

              A double click on the title bar of a window will toggle the maxâ€
              imized state of the window. Scrolling up over the title bar will
              shade the window and scrolling down  will  unshade  the  window.
              When  a  menu is open, the scroll wheel will move through menus.
              When over the pager, the  scroll  wheel  will  switch  desktops.
              When over a task list, the scroll wheel will switch windows.

       DESKTOPS
              Virtual  desktops  are controlled with the Desktops tag.  Within
              this tag the following attribute is supported:

              count int
                     The number of virtual desktops. The default is  4.  Valid
                     values are between 1 and 8 inclusive.

              Within the Desktops tag the following tags are supported:

              Background
                     The  default  background for desktops. The type attribute
                     determines the type of background and the text  contained
                     within this tag is the value. Valid types are:

                     solid
                             A  solid  color.  See the COLORS section for more
                             information.  This is the default.
                     gradient
                             A gradient color. See the COLORS section for more
                             information.
                     image
                             A  stretched  image.  This may be an XPM, PNG, or
                             JPEG image. Note that support for XPM,  PNG,  and
                             JPEG  images must be compiled in and icon support
                             is required.
                     tile
                             A tiled image. Like image, but the image is tiled
                             instead of stretched.
                     command
                             A command to run for setting the background.

              Desktop
                     Desktop-specific  data.  The name attribute may be speciâ€
                     fied to name the desktop (the default is the desktop numâ€
                     ber).  Within  this tag a Background tag may be specified
                     for a desktop-specific background.  See Background  above
                     for more information.

       OTHER SETTINGS

              The following tags may also be supplied:

              DoubleClickDelta
                     The  number  of pixels the mouse can move during a double
                     click.  The default is 2. Valid values are between 0  and
                     32 inclusive.

              DoubleClickSpeed
                     The  maximum  number of milliseconds between clicks for a
                     double click.  The  default  is  400.  Valid  values  are
                     between 1 and 2000 inclusive.

              FocusModel
                     The  focus  model  to  be  used. The default is "sloppy".
                     Valid values are "click" (click to  focus)  and  "sloppy"
                     (focus follows mouse).

              MoveMode
                     The  move mode. The default is "opaque". Valid values are
                     "opaque"  and   "outline".   The   optional   coordinates
                     attribute determines the location of the move status winâ€
                     dow. Possible values are:

                             off
                                    Disable the status window.

                             corner
                                    Place the status window in the  corner  of
                                    the screen.

                             window
                                    Center  the  status  window  on the window
                                    being moved.

                             screen
                                    Center the status window on the screen.

              ResizeMode
                     The resize mode. The default is  "opaque".  Valid  values
                     are  "opaque"  and  "outline".  The  optional coordinates
                     attribute determines the location of the move status winâ€
                     dow. Possible values are:

                             off
                                    Disable the status window.

                             corner
                                    Place  the  status window in the corner of
                                    the screen.

                             window
                                    Center the status  window  on  the  window
                                    being resized.

                             screen
                                    Center the status window on the screen.

              SnapMode
                     The  snap mode. The default is "border". Valid values are
                     "none" (for no snapping), "screen" (for snapping  to  the
                     edge  of  the  screen), and "border" (for snapping to the
                     borders  of  windows  and  the  screen).    An   optional
                     attribute, distance, specifies the distance for snapping.
                     The default is 5. Valid  values  are  between  1  and  32
                     inclusive.

              StartupCommand
                     A command to run when JWM starts.

              ShutdownCommand
                     A command to run when JWM exits.

              RestartCommand
                     A command to run when JWM restarts.



AUTHOR
       Joe Wingbermuehle <joewing@joewing.net>


SEE ALSO
       X(1)




v2.0.1                            2007-09-17                            jwm(1)
```

---

### Post by kerry_s on 2008-02-23
hey, i been thinking about flash and i looked at the requirements, which i don't even meet for flash9.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60515&stc=1&d=1203766358[/IMG]

so what i did was drop down to flash7, which seems to play nicely compared to flash9. you might want to give that a try.

i attached it, just unpack and put it in ~/.mozilla/plugins or copy to the main plugins folder.

---

