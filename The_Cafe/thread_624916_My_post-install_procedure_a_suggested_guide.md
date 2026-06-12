---
title: "My post-install procedure: a suggested guide"
date: 2007-11-27
forum: The Cafe
---

### Post by roazena on 2007-11-27
This is what *I* do when setting up an Ubuntu box (Gutsy) for friends new to Linux. Please, keep the flaming to a minimum.

If there was a way to automate some of this with scripts I could keep on a thumbdrive or website, I'd be grateful for info.

* Estimated time: 1 hour on fast DSL connection*
**[SIZE=3]Software Sources:[/SIZE]**[LIST]
[*]**Ubuntu Software** tab: Remove CD as a source
[*]Tick all other sources
[*]**Third Party** tab: Add partner
[*]**Updates** tab: change *Automatic updates* to *Download all updates in the background*
[*]**Statistics** tab: tick *Submit statistical information*[/LIST]**[SIZE=3]Add/Remove:[/SIZE]**[LIST]
[*]ubuntu-restricted-extras
[*]kubuntu-restricted-extras
[*]streamcast
[*]DeVeDe
[*]Amarok
[*]Xine
[*]VLC
[*]Flickr Uploader
[*]Gmail notifier
[*]Audacity
[*]Bluefish *(Quanta Plus installs confusing extras into other menus)*
[*]Mplayer
[*]Scite text editor
[*]KmyMoney
[*]Inkscape
[*]Scribus
[*]Dia
[*]Wine[/LIST]The above will take care of multimedia plugins, KDE, msttcorefonts, and enabling any other necessary repositories beyond Canonical.
[B][SIZE=3]
Medibuntu:[/SIZE][/B]
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs
```[B][SIZE=3]
Peripherals:[/SIZE][/B][LIST]
[*]**System &#8594; Administration &#8594; Restricted Drivers Manager**
[*]Check monitor settings in **System &#8594; Administration &#8594; Screens and Graphics**
[*]Check wireless if applicable
[*]Set up any nearby printers, print test page
[*]test nearby USB devices
[*]Make sure **System &#8594; Preferences &#8594; Keyboard** is configured for proper keyboard[/LIST]**[SIZE=3]Themes:[/SIZE]**
```
sudo apt-get install blubuntu-look peace-look tropic-look
```[B][SIZE=3]
Appearance:[/SIZE][/B][LIST]
[*]Change **Theme** to Blubuntu (note ramifications below for OpenOffice)
[*]Change **Application/Document/Desktop/Window title** fonts to DejaVu Sans Condensed (it renders more smoothly and reverses the unfortunate x-width trend Verdana started)
[*]If monitor known, alter **Rendering** accordingly
[*]Test **Visual Effects**[/LIST]**[SIZE=3]Time and Date Settings:[/SIZE]**[LIST]
[*]  Set **Time Zone**
[*]** Configuration**: *Keep synchronized with Internet servers* (install NTP)[/LIST]**[SIZE=3] Wine:[/SIZE]**[LIST]
[*] In Firefox, find vcredist_x86.exe on microsoft.com and install (this supplies C libraries needed by many Windows apps)[/LIST]**[SIZE=3] OpenOffice:[/SIZE]**[LIST]
[*]** View**: change icon set back to Human
[*]** Java**: make sure OOo finds JVM
[*]** Fonts**: substitute the following:[LIST]
[*] Helvetica &#8594; FreeSans
[*] Bookman &#8594; URW Bookman L
[*] Avant Garde &#8594; URW Gothic L
[*] Century Gothic &#8594; URW Gothic L
[*] Optima &#8594; MgOpen Cosmetica
[*] Zapf Chancery &#8594; URW Chancery L
[*] Palatino &#8594; URW Palladio L
[*] Palatino Linotype &#8594; URW Palladio L
[*] Book Antiqua &#8594; URW Palladio L[/LIST] [/LIST]**[SIZE=3] GRUB:[/SIZE]**[LIST]
[*] If dualboot, edit menu.list accordingly to correct default boot, hiddenmenu on[/LIST]**[SIZE=3] File Sharing:[/SIZE]**[LIST]
[*] Create temp folder on desktop, turn on sharing and install both NFS/Samba sharing[/LIST]**[SIZE=3] Passing it on:[/SIZE]**[LIST]
[*] Go to ubuntuforums.org and bookmark it to toolbar
[*] Use CD burning app to copy install disc to desktop, check MD5 sum:
```
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
```[/LIST]**[SIZE=3] Final checklist:[/SIZE]**[LIST]
[*] GRUB behaves properly
[*] Firefox (internet) works
[*] Sound card plays
[*] Audio CDs autoplay in correct player
[*] Audio CD burning app works
[*] DVDs autoplay in correct player (may have to be changed to VLC)
[*] Trash emptied[/LIST]

---

### Post by StooJ on 2007-12-17
No one else has posted yet, so I thought I'd throw in my two cents.

Brilliant guide! As a relative newcomer to Ubuntu I've not got my plan of campaign quite perfected yet, it's incredibly useful for me to see someone else's roadmap clearly.

I wish there were more of these threads around to compare & contrast.

The only thing I'm not sure about yet is where to find Streamcast, unless I'm missing a source.

---

### Post by fatality_uk on 2007-12-17
Very Nice :) > Please, keep the flaming to a minimum. Why would you assume anyone would flame? Great post!!
My roadmap consists of 173 scraps of paper, with things like "http://apt.wicd.net fiesty" scribbled on it. I still have no idea what "http://squirrel. gusty" does or why I wrote it down

---

### Post by Lord_Dicranius on 2007-12-17
Great list.  Subscribed for future reference :)

---

### Post by Sukarn on 2007-12-18
roazena was asking whether anything could be automated. To that end, I can provide no help.
Other than that, good guide.

---

### Post by PrimoTurbo on 2007-12-18
A couple of interested things I do is edit xorg.conf and remove any high resolutions that have a low refresh rates, essentially my max resolutio becomes 1024x768 @ 85.. That way my refresh rate/resolution is the same as on desktop and GDM (login), and all full screen games.

I also simply use Automatix to install most things, I've never had a problem with it.

---

### Post by peitschie on 2007-12-18
Hi roazena,

From a quick glance, I would say that a lot of that can be easily automated.  I don't have a script to give you yet (may look at it tonight for fun though), but here is what I can see:

The following can be quite easily automated:
[LIST]
[*]Software sources simply requires editing sources.lst
[*]Add/remove can be duplicated using apt-get & aptitude commands
[*]Medibuntu already a "script" so can be easily incorporated into a larger one
[*]themes already a "script"
[*]Wine installer could easily be done.  vcredist_x86 can also be installed silently according to [http://blogs.msdn.com/astebner/archive/2006/08/23/715755.aspx](http://blogs.msdn.com/astebner/archive/2006/08/23/715755.aspx)
[*]File sharing easily scriptable.  Modification of smb.conf file, and aptitude/apt-get to install samba & nfs
[*]Copying cd to disc & checking md5 sum also quite straight forward using shell commands
[*]Time zone needs to be set manually, but installing ntp and selecting servers could be done easily using aptitude/apt-get
[/LIST]

More difficult to automate or unsure:
[LIST]
[*] OpenOffice modifications would require more extensive knowledge of where these settings are stored
[*] Bookmarking something in the toolbar might be easily done by replacing the bookmark file for firefox...?  Do the users have any other bookmarks before this modification is done?
[*] checking for a dualboot system, and selecting proper system... this is probably best left a manual task simply as there is a large amount of overhead in parsing the config file (as it can't just be replaced)
[*] changes to Appearence are probably best left a manual task due to the complexity of some of the changes (i.e., the number of other programs that need to be run etc., finding the appropriate config files & keys etc.)
[*] Peripherals is the same as appearence.  Needs too much user-interaction to make scripting a very useful task
[/LIST]

I may post some code snippets later if you're interested in having a go yourself :)

---

### Post by picpak on 2007-12-18
> **fatality_uk said:**
> My roadmap consists of 173 scraps of paper, with things like "http://apt.wicd.net fiesty" scribbled on it. I still have no idea what "http://squirrel. gusty" does or why I wrote it down

Someone needs to start using Tomboy. :)

Great guide. I'm doing some of the steps right now.

---

### Post by Mateo on 2007-12-18
I turn off the tray icon for the update-manager.  that thing annoyed me the way it would appear twice a week.  I prefer to upgrade on my time, which is 2 or 3 times a month.

---

### Post by LaRoza on 2007-12-18
I do most of that to some degree, but also add the Ubuntu SE repository to my sources, and use:
```

wget -q http://ubuntusatanic.org/ubuntu-se-key.gpg -O- | sudo apt-key add -

```

Add:

```

deb http://ubuntusatanic.org/hell gutsy main

```

```

sudo aptitude install ubuntu-satanic

```

But not everyone will want that I imagine.

---

### Post by as0l0 on 2007-12-18
so why isn't a lot of this stuff done by default?

---

### Post by macogw on 2007-12-18
> **roazena said:**
> This is what *I* do when setting up an Ubuntu box (Gutsy) for friends new to Linux. Please, keep the flaming to a minimum.

If there was a way to automate some of this with scripts I could keep on a thumbdrive or website, I'd be grateful for info.
I've written simple scripts to do some of this for myself before.  To avoid having to use a lot of echos to put all the sources in the sources.list, though, make a copy of the final sources.list and put that on your flash drive with it, in the same directory as the script, so it can just replace it with the new one.

This:
```

#!/bin/bash

# replaces /etc/apt/sources.list
# with the one in current directory
sudo cp ./sources.list /etc/apt/sources.list
# make sure root owns it
sudo chown root:root /etc/apt/sources.list
# and that no one else can touch it
sudo chmod 755 /etc/apt/sources.list
# get the medibuntu key and add it
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 

sudo apt-get update

# install packages
# i'm assuming "Flickr uploader" means kflickr?
# here's 2 methods, delete whichever you dislike

# method number 1
# list all of the packages in the script (requires finding this line in the script and editing it)
sudo apt-get install ubuntu-restricted-extras kubuntu-restricted-extras streamcast devede amarok xine vlc kflickr gmail-notify audacity bluefish mplayer scite kmymoney inkscape scribus dia wine blubuntu-look peace-look tropic-look ntp

# method number 2
# list the packages, one on each line, in a file in the same directory as the script...benefit is it's easier to modify that file to do slightly different installations per person since you're not sorting through the script.  This assumes the file listing the packages is called "debs"...modify as you see fit
cat debs | xargs sudo apt-get install

# turn on popularity contest
sudo sed -i -e 's/PARTICIPATE="no"/PARTICIPATE="yes"/' popularity-contest.conf

# create temp dir on desktop
mkdir ~/Desktop/temp

# copy install disc to iso on desktop
dd if=/dev/cdrom of=~/Desktop/ubuntu_install_disc.iso
# create MD5sum of iso and check against textfile on flash drive named md5.txt
diff `md5sum ~/Desktop/ubuntu_install_disc.iso` md5.txt
# if that spits out any diff output with +++ and --- kind of lines, you know it failed the md5sum



```
Will do this:
> 
**[SIZE=3]Software Sources:[/SIZE]**[LIST]
[*]**Ubuntu Software** tab: Remove CD as a source
[*]Tick all other sources
[*]**Third Party** tab: Add partner
[*]**Statistics** tab: tick *Submit statistical information*[/LIST]**[SIZE=3]Add/Remove:[/SIZE]**[LIST]
[*]ubuntu-restricted-extras
[*]kubuntu-restricted-extras
[*]streamcast
[*]DeVeDe
[*]Amarok
[*]Xine
[*]VLC
[*]Flickr Uploader
[*]Gmail notifier
[*]Audacity
[*]Bluefish *(Quanta Plus installs confusing extras into other menus)*
[*]Mplayer
[*]Scite text editor
[*]KmyMoney
[*]Inkscape
[*]Scribus
[*]Dia
[*]Wine[/LIST]The above will take care of multimedia plugins, KDE, msttcorefonts, and enabling any other necessary repositories beyond Canonical.
[B][SIZE=3]
Medibuntu:[/SIZE][/B]
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs
```
```
sudo apt-get install blubuntu-look peace-look tropic-look
```
**[size=3]Other[/size]**
[list]
[*] Use CD burning app to copy install disc to desktop, check MD5 sum:
```
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
```
[*] Create temp folder on desktop
[*]  (install NTP)[/list]



Shouldn't be too hard to write, just don't know it off the top of my head.
> 
**[SIZE=3]Time and Date Settings:[/SIZE]**[LIST]
[*]  Set **Time Zone**
[*]** Configuration**: *Keep synchronized with Internet servers*[/LIST][B][SIZE=3] 
Wine:[/SIZE][/B][LIST]
[*] In Firefox, find vcredist_x86.exe on microsoft.com and install (this supplies C libraries needed by many Windows apps)[/LIST]
turn on sharing and install both NFS/Samba sharing[/LIST]



What do you mean by this?  Do you rename them to the old Windows names or do you do this somewhere in OOo?
> 
** Fonts**: substitute the following:[LIST]
[*] Helvetica &#8594; FreeSans
[*] Bookman &#8594; URW Bookman L
[*] Avant Garde &#8594; URW Gothic L
[*] Century Gothic &#8594; URW Gothic L
[*] Optima &#8594; MgOpen Cosmetica
[*] Zapf Chancery &#8594; URW Chancery L
[*] Palatino &#8594; URW Palladio L
[*] Palatino Linotype &#8594; URW Palladio L
[*] Book Antiqua &#8594; URW Palladio L[/LIST]

---

### Post by vishzilla on 2007-12-18
Great guide...was looking for the OO.org Icon set fix!

---

### Post by Tundro Walker on 2007-12-18
I created a cheat-sheet, too, after I started using Ubuntu.  Kept notes on various tweaks & fixes (which has been getting smaller and smaller as they fix them with each distro).

Add this to your list...[LIST]
[*]Install localepurge (purges language files for langauges you're not using, EG: man pages, etc .. only do this for a comp where you know everyone's going to use the same language)[/LIST][LIST]
[*]For Nvidia users, run "nvidia-settings" and set them up.  Then, add "nvidia-settings --load-config-only" to your startup programs so it'll auto-load your settings on each boot (not sure if they fixed it where it'll autoload, so I just always add this)[/LIST][LIST]
[*]Google "AutoFsck" and install (Musther's script that makes Fsck run when you shutdown instead of on boot up)[/LIST][LIST]
[*]Open up Open Office (Write or Spreadsheet), and go to Tools > Options.  Under OpenOffice.org > Memory, set the following then click "OK".  This will let OOo use more memory, making startup and operation much faster.[LIST]
[*]Undo down to 20-30 steps
[*]Graphics Cache for OO.org = 64mb+ (with 1gb RAM, I set mine to 256mb)
[*]Memory per object = 5mb+[/LIST] [/LIST][LIST]
[*]There's a Trash Applet for the panel, but you can get rid of it (and reclaim the 2mb it uses) by enabling a desktop Trash icon instead.  Main > System Tools > Configuration Editor.  Apps > nautilus > desktop.  Checkmark "trash_icon_visible".  You can also check boxes to make the network, home, "my computer", etc icons visible.  (Gnome devs wanted a clean, no-icon look to the desktop, so this is usually switched off by default).[/LIST][LIST]
[*]Gutsy Gibbon introduced some screen issues for some folks, where the desktop gets loaded in "virtual" mode, which means the desktop is larger than the screen can show (like it's zoomed in), and your mouse can pan the screen around the desktop.  This is really annoying.  You hard-fix this by doing the following...[LIST]
[*]open "gksudo gedit /etc/X11/xorg.conf" in a terminal
[*]look for "Section 'Screen'"
[*]" Change the "Virtual" size to be exactly what your desktop is set to (IE: the size you'd like)
[*]this will force virtual mode to be the same size as normal mode[/LIST] [/LIST][B]
For Xubuntu [/B](not sure if this is an issue anymore)[LIST]
[*]sudo apt-get install gnome-utils (installs file searcher and other useful utils)[/LIST][LIST]
[*]Fix "fonts getting smaller" issue:[/LIST][INDENT][LIST]
[*]sudo mousepad ~/.config/xfce4/Xft.xrdb[/LIST][/INDENT][LIST]
[*]...add "Xft.dpi: 96" on last line and add blank line on end. Save.  This forces the window manager to keep 96 dpi, preventing the fonts from shrinking ever smaller.[/LIST]For games where the gamma is really dark, even when maxed out in the game (*cough* Tremulous *cough*)
[LIST]
[*]"xgamma -gamma <0.0 to 10.0>" can brute-set the gamma.  Make 2 launchers...[/LIST][INDENT][LIST=1]
[*]"xgamma -gamma 2" called "Xgamma Up" to increase for playing games
[*]"xgamma -gamma 1" called "Xgamma Down" to lower after playing[/LIST][/INDENT]When using WiFi with WPA encryption, I noticed Network Manager and Wicd would force me to re-login each time it booted (even when I checked to make it auto-login...it would still force me to manually connect every time).

So, the following I found online to force auto-connection at boot...[LIST]
[*]Open a terminal and do "gksudo nautilus", then surf to /etc/network/[/LIST][LIST]
[*]create a "New document" file called "wpa.conf", and toss the following in it and save (adjusting the settings as needed)...[/LIST]ctrl_interface=/var/run/wpa_supplicant

network={
ssid="<your network name>"
psk=<your psk key>
    }
[LIST]
[*]Open the "interfaces" file, and comment out (IE: put # in front of) the wpa-ssid & wpa-psk lines, then add...[/LIST]    wpa-conf /etc/network/wpa.conf
[INDENT]...to it (this points the WPA to the WPA supplicant file you created to look up the network and password.
[/INDENT][INDENT]NOTE: you can get the psk from the wpa-psk line on your "interfaces" file, and just copy/paste that to your wpa.conf file.
[/INDENT]I've got other stuff, too, but it's mostly just stripping out very specific things per my preferences or minimalist setup (EG: I get rid of gparted, because I don't repartition my drive at all, I bumped off artwork, mouse icons, bluetooth tools, etc).  I always bump off main packages, then after unistalling them (in Synaptic), I see if it recommends auto-removing any lib files and such, and remove those, too.

Good post, Dude!

EDIT:

Should also mention that when you upgrade Ubuntu using Update Manager (EG: from Feisty to Gutsy), it likes to re-install all the default packages and overwrite any setup files you might have changed.  This is really for reliance issues, since it helps put the upgrade on a "clean slate", guaranteeing necessary things (which you may have removed) will be there when needed during the upgrade.  You'll probably have to tweak some things and uninstall stuff after an upgrade.  But, you shouldn't have to install stuff...as long as it's in the default Repo's.  EG: I installed Gnomad 2, and the upgrade process didn't uninstall it.  However, I also installed WICD from the 3rd party repo, and the upgrade DID uninstall that.  So, I had to jack around with that again after upgrading to Gutsy.  (But after using the WPA supplicant trick, I haven't needed WICD.)

Likewise, if you're doing a fresh install, always get and burn the latest distro to CD, and use it to install.  It really sucks using an old distro copy, and after 30 minutes of install, the first thing it needs to do is spend 5 hours updating.  By using the latest distro, you know it's the most up-to-date, and should require little if any updating after installation.

---

### Post by andhar on 2007-12-19
Very nice post , I have it bookmarked but do you know of any other good themes and backgrounds the ones you pointed out are pretty nice.

sudo apt-get install blubuntu-look peace-look tropic-look  <--- Nice

---

### Post by picpak on 2007-12-19
> **Tundro Walker said:**
> 
[LIST][*]sudo apt-get install gnome-utils (installs file searcher and other useful utils)[/LIST]

If you want a file searcher why not do

```
sudo apt-get install catfish
```

?

---

### Post by Tundro Walker on 2007-12-19
> **andhar said:**
>  ... do you know of any other good themes and backgrounds ...

Check out "gnome-art" in Synaptic, Adept, Apt-get (whatever you use).

It lets you pull in a preview of all the themes posted at [http://art.gnome.org/](http://art.gnome.org/) through a GUI, then you pick-n-choose the ones you like and it'll download them for use.  There's pre-packaged themes, but also modular ones, like for toolbar/button , wallpapers, window themes, etc, so you can mix and match as you like.  I thought it was pretty slick when I used it.

---

### Post by macogw on 2007-12-19
> **Tundro Walker said:**
> Check out "gnome-art" in Synaptic, Adept, Apt-get (whatever you use).

It lets you pull in a preview of all the themes posted at [http://art.gnome.org/](http://art.gnome.org/) through a GUI, then you pick-n-choose the ones you like and it'll download them for use.  There's pre-packaged themes, but also modular ones, like for toolbar/button , wallpapers, window themes, etc, so you can mix and match as you like.  I thought it was pretty slick when I used it.

neat!

For a file searcher, why not just use the included Tracker?

---

### Post by el_ricardo on 2007-12-19
i don't have a routine, i can never remember everything, so i just get the internet working and install other stuff as i realise that i need it lol

---

### Post by roazena on 2007-12-24
Thanks for all of the positive feedback. What I mean by "no flaming" was the inclusion of Wine upsetting purists. I rehabilitate older PCs and put them up on the local Freecycle for needy people, and part of my goal is to make simple desktop systems that are user friendly and as outside-world compatible as possible from the get-go. I don't want to burden new users with cookbook instructions.

> **macogw said:**
> What do you mean by this?  Do you rename them to the old Windows names or do you do this somewhere in OOo?

The latter. If I knew where OOo keeps its font substitution table I'd put a revised version somewhere that could be wgetted.


Thanks to everyone who offered advice. I'll be experimenting with wrapping these up into an installer.

---

### Post by castoroil97 on 2007-12-24
thanks for the guide

---

### Post by KoolBeans on 2008-01-06
What is synaptic and how do I use it? Why should I use it?
I have Ubuntu Studio, I don't see that listed? I have the Studio Package, right?

As to the Main menu>Trash I cant find anything. In the right pane when I select/check System for view, it unchecks itself. In the left pane, I select System, no Trash.

I can't install specific programs from the add/remove menu my settings>all applications. Specifically, Wine. Will not let me check it.

Still no sound.

Oh yea. I am running the Ubuntu Studio AMD64 Version.

---

### Post by Lostincyberspace on 2008-01-06
are you 64 bit if you are then you need to go to the wine site to be able to use wine.

---

### Post by KoolBeans on 2008-01-06
I tried to do it through add/remove. It is not accessable to me from there.

---

### Post by KoolBeans on 2008-01-06
> By far the easiest method for installing Wine is to use a prepackaged version of Wine. These packages contain ready-to-run Wine binary files specifically compiled for your distribution, and they are tested regularly by the packagers for both functionality and completeness.
Packages are the recommended method for installing Wine. from [WineHQ](http://www.winehq.org/site/docs/wineusr-guide/getting-wine)

---

### Post by KoolBeans on 2008-01-06
Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
Freezes terminal.
I loose the ~$ thingy.

---

### Post by KoolBeans on 2008-01-07
Funny, I just tried installing it from The WineHQ .deb packages archive, .0.9.52 amd64.
After downloading, installing, it stated-same package already installed. If it is, Where?

---

### Post by CheeseEatingBulldog on 2008-01-07
Hi, 
I install ubuntu for the company I work for and made a wiki for my collegues on what I did on a standard install, so for the interested, here it is:

**Standard Ubuntu Install: Alex' method**

Here I will explain a standard install of an Ubuntu machine. This includes all extra software that is needed by common users.
[B]
Dual Boot Install:[/B]
If you want to make your machine dual boot, then use the guides at: [http://apcmag.com/node/5162/]("http://apcmag.com/node/5162/")  which will explain an install of the base system.
[B]
Get the ISO:[/B]
You can either get the ISO from [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") or select a different version from [http://releases.ubuntu.com/]("http://releases.ubuntu.com/"). The latter has the 'Alternate CD' and '64-Bit' as well as the DVD version of Ubuntu.
[B]
Installing base system:[/B]
Set the option 'boot from CD' in your BIOS if that isn't already the case, and boot the Live CD. If you experience problems like a hang or it just takes for ever to load, try adding irqpoll to the grub boot line (last option in Live CD boot menu). This sorts out various irq conflicts you might have, from experience some hard drives need this option.

Once you are loaded into the Live CD environment, click the 'Install' option from the desktop and run through the installation. It will then prompt for a reboot, so remove CD and boot.
[B]
Checking DRI (direct rendering)[/B]
For newer machines this is usually on by default, but older machines with old video cards this is not the case. To check, open a terminal and type:
 
```
glxinfo
```

Right at the top you will see:

```
name of display: :0.0
display: :0 screen: 0
direct rendering: Yes
```

or "no" if that is the case. You can also check by typing 

```
glxgears
```

which will load some 3d gears in a window, if dri is enabled this will work smoothly, otherwise, not.

Many old cards require that you put video depth to 16-bit instead of the default 24-bit to get dri to work. To do this open a terminal and type: 

```
sudo gedit /etc/X11/xorg.conf 
```

this will open a text editor and your X-config file. Look for defaullt depth and change it to 16.

To be on the safe side also add this section to your xorg.conf:

```
Section "Module"
Load "dbe"
Load "dri"
Load "extmod"
Load "glx"
Load "record"
Load "xtrap"
Load "freetype"
Load "type1"
EndSection
```

Which will load the kernel modules needed for dri. Save the file and reboot X by pressing ctrl+alt+backspace.
[B]
Adding the extras - graphics, the cube and other effects:[/B]
Now that you have the base system installed you can start to tweak it. First off check that you have the propriatory driver running for your video card, a message will normaly prompt you of the existence of a propriatory driver upon first boot. If not, then go to the System menu and select 'Restricted driver manager' and check the box next to your video driver (You may have to enable extra software sources from the 'Software sources' option in the system menu). This will download and install the driver for you from the repositories.

NOTE: If you want to customise your sources list, you can generate one online at [http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/"). Once generated open the file /etc/aptitude/sources.list as root (for example, open a terminal and type):

```
sudo gedit /etc/aptitude/sources/list
```

This will open the file in a text editor. Select all and delete. Select and copy the generated text from the ubuntu-nl site and paste it into the open file and save. Close the text editor and from the command line type: 

```
sudo aptitude update 
```

to update your sources list.

The driver will be installed and to enable it simply log out and log back in (or press Ctrl + Alt + Backspace to reload GDM). If you have problems, as in gdm won't load and you are stuck on the command line, you can reconfigure gdm manually with:

```
sudo dpkg-reconfigure xorg-xserver 
```

which will start the command line config tool, afterwhich you can reload gdm by typing: 

```
sudo gdm
```

If you can't install the propriatory driver from the ubuntu sources you can alternatively grab the driver from the manufacturers site. For example for NVIDIA cards go to: 

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

this will give you a NVIDIAXXX.run file.

Place this on your Desktop and goto the command line (crtl + alt + F1).
Kill GDM by typing:
```

sudo killall gdm
```

Change directories to your Desktop:
 
```
cd /home/YOURNAME/Desktop
```

Start installer by typing:
 
```
sudo sh NVIDIAXXX.run
```

This should launch the installer, if the installer gives you and error about headers you will need to install the Linuxheaders and buildessetial packages: sudo aptitude search headers / buildessential look for the right package and install them sudo aptitude install PACKAGE NAMES
Now reload installer 

```
sudo sh NVIDIAXXX.run

```
This will make a custom kernel module (driver), once it is finished reload GDM by typing sudo gdm

NOTE:If you install the driver with the .run installer you will have to rerun the installer each time there is a kernel update (and after such an update your gdm WILL NOT LOAD on boot and leave you at the command line.

You can also use ENVY which is a script written to install ATI / NVIDIA drivers, you can get it from: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Once you have succesfully loaded into GDM, you can install the compiz manager to customize your desktop effects by typing:

```
sudo aptitude install compizconfig-settings-manager
```

 which will add the settings manager to your system menu (you can enable the cube and various effects from this menu).
[B]
Install all you can:[/B]
First off goto the add software option under the ubuntu logo in the top-left and select all the stuff you want (install all video players and apps you want). Then download AUTOMATIX from [http://www.getautomatix.com/wiki/index.php?title=Installation ]("http://www.getautomatix.com/wiki/index.php?title=Installation")(which is .deb file that you can double click) and run Automatix. Here you can install all the codecs, java runtime and other software you need (such as the flash plugin).Note than automatix now uses ubuntu repositories, and thus does not screw your install as it did in the past with third party software.

Lastly you can install some packages from either Synaptic (via the system menu) or just open a terminal and install them by hand a list of what I normally install is:

vlc
kino
audacity
avidemux
xine
k3B
gparted
hardinfo
softinfo
samba
inkscape
bum
thunderbird

To install them simply type:

```
sudo aptitude install PACKAGE NAME PACKAGE NAME PACKAGE NAME 

```
(you can install multiple packages at the same time by putting a space between each package name).

For more software ideas (and windows equivalents) see this list: [https://help.ubuntu.com/community/WindowsApplicationsEquivalents]("https://help.ubuntu.com/community/WindowsApplicationsEquivalents")

**Windows software and Wine:**
To be able to install and run windows applications you need to install wine. Don't get the one from the repositories, but goto [http://www.wine-doors.org/wordpress/]("http://www.wine-doors.org/wordpress/") and download [http://www.wine-doors.org/releases/wine-doors_0.1.1-1_all.deb]("http://www.wine-doors.org/releases/wine-doors_0.1.1-1_all.deb") which is a debian file you can double click to install. Once installed select wine doors from the ubuntu menu. This opens the wine package manager. Create a new install by typing a name. Then select all windows core packages to install and let wine doors set up wine.

To tweak the install open a terminal and type:

```
winecfg 
```

Here you can change the emulation version (win98/2000/xp) and set a virtual desktop size for windows applications running on your ubuntu desktop.

**Cusomising the look:**
Some people don't like brown, and want to have different icons and such. Goto: [http://gnome-look.org/ ]("http://gnome-look.org/")to see what you can have.

For a different look (I like the OSX blue/white look) click on the GTK 2.X link in the menu and chose a different look. Download the subsiquent files to your Desktop and open the 'Appearence' option from the System menu. Drag and drop downloaded files into window, this will install the theme, and can then be chosen from the list. Alternatively you can chose different window borders, control colours and background seperately by clicking the 'customise option under the theme.

For icons chose the 'Icon Themes' option in gnome-look.org and drag and drop downloaded icon themes into the 'appearence' menu like the theme.

For a different login screen chose 'GDM Themes in gnome-look.org and chose a login screen. Then open the 'login screen' option from the system menu, and drag and drop downloaded files into the window.
[B]
Menu editing:[/B]
Some usefull tools are hidden in the menus by default, so the see them right-click on the ubuntu menu icon (top left) and chose the edit menus option. Go through the menus and check the boxes of the applications you want to be able to see in the menus. Some must haves are gconfig-editor, pdfview and various system-tools which are hidden on default.
[B]
Adding Desktop Icons to Desktop:[/B]
If you want the icons for Home, Network Places and Trash launch gconf-editor via terminal and select applications then nautilus and desktop. Check the boxes of the icons you want to have shown on your dekstop.
[B]
System Monitor and other menu bar stuff:[/B]
You can add an assortment of applets to your gnome-panels by right clicking either of them and selecting 'add to panel'. Select for example the system monitor and click add. Now right click on system monitor to add displays for cpu usage, memory usage, load and disk activity.
[B]
Keep your system up to date:[/B]
After installing everything check for updates if they are not prompted straight away by opening a terminal and typing:

```
sudo aptitude update 
```

and then

```
sudo aptitude upgrade
```

**Extra Stuff:**
One application that is handy for downloading stuff is Azureus (Bittorrent client). Goto [http://azureus.sourceforge.net/ ]("http://azureus.sourceforge.net/")and download the azureus tarball. Make a directory in your /home directory and unzip all files to that directory. Then simply run the Azureus file. For future ease open a torrent and select Azureus as the application to open it with and tick the box that says to this in the future as well.

Another extra is an application to mount iso images as drives (like deamon tools). The howto page is [http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html]("http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html") but to install the application simply open a terminal and type sudo aptitude install gmountiso. The application will be added to your ubuntu menus.

---

### Post by Trail on 2008-01-07
Sorry, but... eh. While I do understand that it's nice to see what other people do with their machine, I fail to see why something like that would need to be automated or so.

I like to customize most things I can, and my desktop (and laptop) look differently on a monthly basis. (Gnome, KDE, compiz, awn, screenlets, superekaramba, whatever). And, apart from that, I have a set of applications I frequently use that I prefer, and I'm sure it quite differs from anyone else's.

So, since I believe each installation is probably unique, why bother with a script? :)

I do feel that a list such as this, though, is useful for inspiration and comparison purposes though.

---

### Post by StooJ on 2008-01-14
> **Trail said:**
> So, since I believe each installation is probably unique, why bother with a script? :)

The OP isn't dealing with unique installations. He's recycling old PCs for charity, and rather than uniquely tailoring each computer, or providing a virgin Ubuntu installation, he has a set routine that will result in a rather nice, ready-to-go box for end-users.

Sounds like a great idea to me, and well worth scripting.

I've personally found the thread useful because I follow the guide for a new installation now. It's a better set up than I've come up with, everyone prefers the blue theme and it gives them a nicer starting point to customize as they wish.

---

### Post by koenn on 2008-01-14
> **macogw said:**
> I've written simple scripts to do some of this for myself before.  To avoid having to use a lot of echos to put all the sources in the sources.list, though, make a copy of the final sources.list and put that on your flash drive with it, in the same directory as the script, so it can just replace it with the new one.

I do that too, but I prefer keeping data inside the script, but in a manageable way, so i do things like

```

# replace sources.list with custom list
cp /etc/apt/sources.list /etc/apt/sources.list.orig
cat > /etc/apt/sources.lst << EOF

deb http:// ...
deb http:// ...
EOF

```
this replaces sources list with whatever is between <<EOF and EOF

```

#install extra packages

PKGS="ubuntu-restricted-extras kubuntu-restricted-extras"
PKGS="$PKGS treamcast devede amarok xine vlc kflickr"
PKGS="$PKGS gmail-notify audacity bluefish mplayer scite" 



for ITEM in $PKGS; do
    apt-get -y install $ITEM
done

```
the PKGS declaration can be at the top of the script so it's easy to edit. I do apt-get install in a loop ; you could just do
apt-get -y install $PKGS
but then the entire statement fails if one of the packages is not found or causes trouble

instead of using sudo in the script, you can just run the whole script with sudo (eg sudo ./post-install.sh)


time zone can be called like this : (might require sudo)
```
tzconfig
```

you can also try to automate it like this :
```
tzconfig << EOF
y
8
Brussels
EOF

```
i.e. you provide all answers in the list :
modify timezone : y
part of the world: 8   (=Europe)
nearest city : Brussels

for ntp, try
```

	echo "server 192.168.0.2" > /etc/ntp.conf

```
replace with a valid ip address or ntp server name. I'm not sure you'd still have to enable ntp, need to check that.

---

### Post by maechismo on 2008-01-15
Hi Roazena,

I am completely new to the Linux world and to Ubuntu. After struggling for couple of days finally I installed Ubuntu onto my Laptop which runs XP on another partition. 

I was following through your steps and I copied and pasted the mediabuntu code on my terminal and hit return thats it, it came up with an error as "---19:12:02-----" line is not not known in the source.list.d???

and it does not let me to work on Synaptic Packet manager as well:

I looked into the etc/apt/source.lit.d and tried to change the line 1
"19:12:02" but it says I dont have permission......

I am stuck here..Could you please give some advise hot to resolve this?......this error doesn't me to do anything on my PC....

anyone much appreciated!

thanks

---

### Post by StooJ on 2008-01-29
You'll need to attach those screenshots, maechismo, or upload them to a webpage before we can view them. At the moment they are pointing to your own computer's hard drive.

Did you paste the lines in one at a time?

---

