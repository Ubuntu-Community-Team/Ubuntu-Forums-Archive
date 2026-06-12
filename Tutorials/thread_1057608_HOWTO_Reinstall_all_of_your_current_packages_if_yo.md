---
title: "HOWTO Reinstall all of your current packages if you do a fresh Ubuntu install"
date: 2009-02-02
forum: Tutorials
---

### Post by dcstar on 2009-02-02
People sometimes have to do a reinstall of their Ubuntu system for various reasons (been playing/experimenting with configuration/drivers/other packages or just because something is badly broken) but remembering all the extra packages you have installed can be a chore - but here is the simple solution:


On your old system (assuming it is still working), start up **Synaptic** and go:

[INDENT]**File-Save Markings** and choose a file name along with a location (like a USB drive) that you can use when you have installed your new system)[/INDENT]

This file contains a list of all your currently installed packages, and when you have installed and booted up your new system (and configured your repositories to the best for your location - as we all do, don't we?) then start up **Synaptic** and go:

[INDENT]**File-Read Markings** and point it at your saved file, and after that has completed then select **Apply** to kick off the download & installation of all of those packages you had installed previously![/INDENT]


There are also apt-get command line functions that achieve the same outcome, so those who don't have/use Synaptic can still do this.

You will still have to do any special configuration changes that you had on the old system, but at least all of the packages are now in the new system.

This is also very handy for moving to new hardware/duplicating setups etc.

Be aware that doing this between different Ubuntu versions may cause complications because some packages may not be in a later version or have different names.

---

### Post by wersdaluv on 2009-02-04
Wow. Already on Lifehacker.com but still got no reply. 

Great points! Took note of 'em. Thanks!

[http://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallatoin](http://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallatoin)

---

### Post by iwfur25 on 2009-02-04
/var/cache/apt/archives contains the downloaded packages. Back it up (if you have the space) and restore it along with the markings and apt won't have to re-download all (or maybe most?) of the packages.

---

### Post by inod3 on 2009-02-04
> On your old system (assuming it is still working), start up **Synaptic** and go:

[INDENT]**File-Save Markings** and choose a file name along with a location (like a USB drive) that you can use when you have installed your new system)[/INDENT]

This file contains a list of all your currently installed packages

Sorry, but its not working for me:

Ubuntu 8.10

System -> administration -> synaptic package manager *click*
File -> Save Marking As... *click*
$ cat <filename>
$

Nothingness. Same for option 'Save Markings'.

---

### Post by dazzlindonna on 2009-02-04
Wow, great tip. I had not noticed that option in Synaptic. Thanks!

---

### Post by MayOne.Net on 2009-02-04
Don't forget to backup your sources before you reinstall. 

 ```
sudo cp /etc/apt/sources.list ~/sources.list.backup
```

Otherwise if you have added any PPAs or other sources, this tip won't work.

---

### Post by obscur156 on 2009-02-04
Hi all,i was doing something look a like but via the terminal.
With one command you can install all your apps in one shot.

Example:

sudo aptitude install firestarter krusader amsn  ktorrent amarok devede k3b vlc  ksnapshot netspeed audacity timer-applet convertall gtkhash bleachbit

You can install as much as you want,it makes no difference.
You save your command with openoffice word or what ever to a USB KEY (drive) and copy and paste to the terminal on the next install.

Voila,Best regards.

---

### Post by ZungBang on 2009-02-04
According to section [6.4.9]("http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-record") of the [Debian Reference Manual]("http://www.debian.org/doc/manuals/reference/"), the following will save both the list of packages installed and their debconf configuration:
 
```
     # dpkg --get-selections "*" >myselections   # or use \*
     # debconf-get-selections > debconfsel.txt

```and the following will reinstall and reconfigure them:

```
     # dselect update
     # debconf-set-selections < debconfsel.txt
     # dpkg --set-selections <myselections
     # apt-get -u dselect-upgrade    # or dselect install

```

---

### Post by johnjohn2 on 2009-02-04
Thanks dude worked like a charm

---

### Post by kevmaster on 2009-02-05
If you run a server, and don't have a graphical interface, you can still do it with apt:

[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by obscur156 on 2009-02-05
Ok ,one question? 
When i make an install ,i remove a lot too.So when i save my marking ,does it remove things that i removed before  i saved my marking???

Thanks for your reply,Best regards.

---

### Post by MGStreak on 2009-02-05
> **dcstar said:**
> On your old system (assuming it is still working), start up **Synaptic** and go:

[INDENT]**File-Save Markings** and choose a file name along with a location (like a USB drive) that you can use when you have installed your new system)[/INDENT]

This file contains a list of all your currently installed packages, and when you have installed and booted up your new system (and configured your repositories to the best for your location - as we all do, don't we?) then start up **Synaptic** and go:


> **inod3 said:**
> Sorry, but its not working for me:

Ubuntu 8.10

System -> administration -> synaptic package manager *click*
File -> Save Marking As... *click*
$ cat <filename>
$

Nothingness. Same for option 'Save Markings'.

This is because the 'Save Markings' only saves the markings you have *currently* made for installation/upgrading.  *NOT* packages you have already installed!  This tutorial is a little unclear.

---

### Post by juanbretti on 2009-02-07
> **MGStreak said:**
> This is because the 'Save Markings' only saves the markings you have *currently* made for installation/upgrading.  *NOT* packages you have already installed!  This tutorial is a little unclear.

I might add that you need to check on the bottom: "Save full state, not only changes"
Check the attach.

BTW, great tip!

---

### Post by MGStreak on 2009-02-08
> **pepemosca said:**
> I might add that you need to check on the bottom: "Save full state, not only changes"

*facepalm*

THANK YOU!!!

---

### Post by statmonkey on 2009-02-09
> **obscur156 said:**
> Ok ,one question? 
When i make an install ,i remove a lot too.So when i save my marking ,does it remove things that i removed before  i saved my marking???

Thanks for your reply,Best regards.

OK, not specifically what you have asked but I have the same issues and work around it using APTonCD.  It is in the repos  - 
*sudo apt-get install aptoncd*

The value of it is it allows you to keep a CD copy of what you have installed for safe keeping, you can add or deselect packages as you see fit.  I actually just use it for archving/safekeeping and use the command line along with a Quickstart backup of my home environment.  It really makes a clean install a snap or setting up a new box as well.

Great thread btw.

---

### Post by Clancy_s on 2009-02-10
Nice tip, thanks.

---

### Post by kazemizuhi on 2009-02-10
While this is all well and good, is it possible to backup all of the installation files? Or in plain english, I do not always have the privelage to be connected to the internet with the PC ubuntu is installed on. Unfortunately, I have been forced to reinstall an unreasonable number of times as I migrated from Windows XP environment to a dual-boot XP/Ubuntu setup.

The most fustrating thing with this process is the fact that I have to download Nvidia display drivers everytime I reinstall. There is a bug with Ubuntu's live CD where it defaults to 740x400 when it cannot recognise your monitor (in my experience). The dialog boxes one uses during installation have a vertical resolution larger than this making it impossible to run through the installation process. I have to carry my PC over to the family PC to use it's monitor for install, then download and istall the Nvidia drivers before I can even begin using the OS with my monitor. Not to mention all the 'sudo apt-get' updates.

I have yet to find a tutorial or instructions for downloading an installation file to one's drive, then proceeding to install said file as one is wont to do in a Windows environment. Everything I have seen thus far has required sudo apt-get or use of synaptic. As far as I know these methods do not provide me with an installation file which I can re-use at a later date. This leads me to believe that it may not be possible. Yet my better judgement tells me otherwise; for how did the average linux user get-by prior to the prevalence of the internet?

Is there a way to backup everything (mainly display drivers and sudo apt-get updates) one has downloaded to save one having to download again after re-install? I ask, because Ubuntu (crunchbang distro) has decided to die on me again. Basically, all elements (icons, text, etc...) are displayed as if the resolution were 740x400 (read: ridiculously large). The resolution is 1440x900 so everything is crisp and sharp, but the text and icons being the size they are, dialog boxes are not fitting within the screen bounds again. I have never seen or heard of such an error before, but that's a discussion for another thread.

I believe I may have to reinstall and would like to do so without connecting to the internet. Any help would be very much appreciated.

Thanks, in advance.

---

### Post by obscur156 on 2009-02-11
Thanks you very much statmonkey.  :)

---

### Post by KenLazlo on 2009-02-11
to fix your graphic installation problem you can use the alternate installation cd which has a text based installation [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

to avoid downloading all updates after a reinstall:  
ubuntu stores downloaded packages in /var/cache/apt/archives
save these files and after a new installation copy them to the same location. 
after that do a   apt-get update and apt-get upgrade

I save my home-directory and directory /etc and subdirectories, cause they contain most configuration files

another solution is to save the entire linux partition. I prefer using the program partimage, but there are some other live-cds around.

---

### Post by dsm iv tr on 2009-02-12
> 
I have yet to find a tutorial or instructions for downloading an installation file to one's drive, then proceeding to install said file as one is wont to do in a Windows environment. Everything I have seen thus far has required sudo apt-get or use of synaptic. As far as I know these methods do not provide me with an installation file which I can re-use at a later date. This leads me to believe that it may not be possible. Yet my better judgement tells me otherwise; for how did the average linux user get-by prior to the prevalence of the internet? Is there a way to backup everything (mainly display drivers and sudo apt-get updates) one has downloaded to save one having to download again after re-install?


You can install .deb files (of which the entire OS is comprised) (give or take a few files) individually with dpkg -i <file.deb>, or use gdebi-gtk, which is installed by default.

Check /var/cache/apt/archives for the packages you've downloaded; you'll find their .deb files there unless you've explicitly removed them.

For your historical reference, people actually used to distribute things, even entire operating systems, on floppies. :P

> 
I ask, because Ubuntu (crunchbang distro) has decided to die on me again. Basically, all elements (icons, text, etc...) are displayed as if the resolution were 740x400 (read: ridiculously large). The resolution is 1440x900 so everything is crisp and sharp, but the text and icons being the size they are, dialog boxes are not fitting within the screen bounds again. I have never seen or heard of such an error before, but that's a discussion for another thread.

This sounds like a problem with your Xorg configuration, or the nVidia binary driver. If it's the binary driver, I can't be much help to you. If it's Xorg, you might try making sure the DPI is set properly for your system. If that yields nothing, you can try moving /etc/X11/xorg.conf out of the way, perhaps to your home directory, and restarting X so that it uses a default configuration.

For changing your DPI, check this thread:
[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)

---

### Post by kazemizuhi on 2009-02-18
Thanks for the responses. That was a great help. I don't know how my Nvidia driver became faulty (if that is where the issue lies), as I had not even booted into the Ubuntu partition since I got it working. I'm copying all this down and going to see if it works.

Thanks once again.

---

### Post by anextx on 2009-04-24
hey, i'm getting ready to upgrade to 9.04.  I got everything backed up fine, except for the 'lock' file in my /var/cache/apt/archives folder.  it says i don't have permission to copy/paste it.  is this file necessary? 

i moved all of the other files successfully and also saved my packages with synaptic.  are these the only things i will need to do before upgrading (my home directory is in its own partition, so no need to back it up)?

---

### Post by markitoxs on 2009-04-26
This was extremely useful, managed to reinstall everything effortless.

---

### Post by Mr Surbade on 2009-07-07
> **obscur156 said:**
> 
With one command you can install all your apps in one shot :

sudo aptitude install firestarter krusader amsn  ktorrent amarok devede k3b vlc  ksnapshot netspeed audacity timer-applet convertall gtkhash bleachbit


Damn ! That is clever !!

I've been digging up the whole wide web searching informations about backing up packages. All I found was complicated solutions. Thanks mate, we all need to learn from you simplicity.

---

### Post by MadBillyGoat on 2009-07-07
Hello, 
     I am new to linux and wiped windows clean off all my pcs and just did it.  All is well, I have been watching my used space on my hardrive. I have noticed that the archives in var is freaking huge and growing I found it was the archive.thanks to this post I know how to backup my install and tanks to a different build a live cd. Im all over it and can hardly wait.

Thanks,

The Questions,

Can I remove the archived files?
If not, can I relocate files?
If possible is there a way to make the os archive somewhare else by defalt?

Thanks,

MadBillyGoat

---

### Post by NTolerance on 2009-07-07
> **MadBillyGoat said:**
> Hello, 
     I am new to linux and wiped windows clean off all my pcs and just did it.  All is well, I have been watching my used space on my hardrive. I have noticed that the archives in var is freaking huge and growing I found it was the archive.thanks to this post I know how to backup my install and tanks to a different build a live cd. Im all over it and can hardly wait.

Thanks,

The Questions,

Can I remove the archived files?
If not, can I relocate files?
If possible is there a way to make the os archive somewhare else by defalt?

Thanks,

MadBillyGoat

Yes, you can safely delete the files in /var/cache/apt/archives if you wish.

---

### Post by blur xc on 2009-07-08
What about programs installed in wine?  How do you go about putting those back?  Do you have to go back and do all that the hard way?

Thanks,
BM

---

### Post by NTolerance on 2009-07-08
> **Barna Madau said:**
> What about programs installed in wine?  How do you go about putting those back?  Do you have to go back and do all that the hard way?

Thanks,
BM

You probably can just back up your ~/.wine directory.  If you're making backups of your home directory as everyone should, you can simply copy it back over if you need to restore.

---

### Post by MadBillyGoat on 2009-07-14
Hell again, 
Thank you for the information it was most helpful. I do have another question, Somehow The archives changed I did nothing, but there are packages missing. Are the archives deleted automatically after a set time or size? Or are only the essential packages kept forever? Because the dir went from over 2 gigs to under 600mgs.  I thought it was kid of odd.

Thanks

MadBillyGoat

---

### Post by grkuntzmd on 2009-08-25
> **inod3 said:**
> Sorry, but its not working for me:

Ubuntu 8.10

System -> administration -> synaptic package manager *click*
File -> Save Marking As... *click*
$ cat <filename>
$

Nothingness. Same for option 'Save Markings'.

Same thing happened to me until I clicked the "save full state, not only changes" checkbox in the File-Save Marking As... dialog (near the bottom).

-Ralph

---

### Post by fela on 2009-08-25
Another tip is that if you have a download cap/slow connection, and are duplicating a system, you can move all the .deb packages that you want from /var/cache/apt/archives on the source system to the same place on the target system. Apt (or synaptic) will automatically detect that it has them and not bother downloading them all over again.

---

### Post by xeolhades on 2009-08-29
Well, the way below is so more simple.

In older system do:

# dpkg -l|grep ii|cut -d ' ' -f 3 > /media/<ANYTHING>/packages_`date +"%Y%m%d"`.txt
# cp /etc/apt/sources.list /media/<ANYTHING>/sources_`date +"%Y%m%d"`.list

In the new system:

# cp /media/<ANYTHING>/sources_<DATE>.list  /etc/apt/sources.list
# apt-get updade; apt-get install -y `cat /media/<ANYTHING>/packages_<DATE>.txt`

:popcorn:

---

### Post by SaintDanBert on 2009-11-01
This entire thread is smokin' cool. That said, why is this issue so bloody arcane? Why isn't this "common knowledge" and built into the update/upgrade processing that synaptic and apt and dpkg try to accomplish?

For example, 
[list]
[*]when I select upgrade within synaptic, maybe it could tell me, "Saving list of added and removed packages..." and  "Please provide a path and file name ..."
[*]when I first boot after an upgrade, maybe something could ask me, "Do you have a record of added and removed packages..." and "Please provide a path and file name ..."
[/list]
It is this sort of "I know a secret..." about accomplishing important, common tasks that discourages plain folks from approaching linux.

---

### Post by MountainX on 2009-11-01
I would like to do something like this with KDE. In particular, I want to make Kubuntu as close to openSUSE 11.2 as possible. Does anyone know an ***easy*** way to get all the settings, installed apps, themes and other stuff from openSUSE KDE and replicate it in Kubuntu?

I want everything from the grub and boot splash screens to the same list of default apps to the default plasma configuration. Of course, that's just a starting point. I will change the branding and stuff, but for starters, I want everything from openSUSE because it is a much more polished setup and almost everything works better for me.

I am willing to install openSUSE. From there, I need to know what to copy and how to save it so it can be imported into Kubuntu after a fresh install. Is this possible in a manner as easy as what is described in this thread?

I know there may be issues related to KDE-base versions being slightly different, so if any experts can suggest how to do this I will be extremely happy.

References:
[http://forums.opensuse.org/applications/423797-suse-would-perfect-if-used-debian-package-mangement.html](http://forums.opensuse.org/applications/423797-suse-would-perfect-if-used-debian-package-mangement.html)
[http://ubuntuforums.org/showthread.php?t=1308011](http://ubuntuforums.org/showthread.php?t=1308011)

---

### Post by fela on 2009-11-02
> **SaintDanBert said:**
> This entire thread is smokin' cool. That said, why is this issue so bloody arcane? Why isn't this "common knowledge" and built into the update/upgrade processing that synaptic and apt and dpkg try to accomplish?

For example, 
[list]
[*]when I select upgrade within synaptic, maybe it could tell me, "Saving list of added and removed packages..." and  "Please provide a path and file name ..."
[*]when I first boot after an upgrade, maybe something could ask me, "Do you have a record of added and removed packages..." and "Please provide a path and file name ..."
[/list]
It is this sort of "I know a secret..." about accomplishing important, common tasks that discourages plain folks from approaching linux.

If you really wanted to fix all of these minor little naggings (that often only newbies would need), then feel free to add them in. But once you've learned how to do something, you don't need a useless little bit of driftwood telling you how to do it. That's why most Linux developers concentrate on the more pressing issues.

Anyway, Linux isn't Windows and it has to be admitted that a fair amount of 'computer literacy' is assumed in most if not all distros - it's just one of those things you need if you're to use Linux. Mark Shuttleworth might disagree all he likes but yeah, you do need to know a fair amount about computers to use Linux to its full advantage. If you don't, then Linux distros such as Ubuntu and the like will appear as cheap Windows knock offs that lack features, and that's sadly what's happened with alot of people. If everyone knew how to use the command line there wouldn't be half the anti-linux rants that there are now.

---

### Post by ronewolf on 2009-11-02
yes, a good thread with most content well written and understandable. but don't think that this addresses the full range of concerns for those of us who want to re-install or update a customized and functional system.

as most do, i have not only changed from the default package list (for instance removing most games and adding some useful apps....), but i have also made various config changes (such as the hack to disable the touchpad when keying). and i am on 8.04 but want to get to 9.10 (don't i?).

so seem to be two paths to do this. one is to do 4(!) updates 8.04->8.10->9.04-.9.10. ugg, seems like a risky and time consuming path. also, i have poulsboro drivers to bring along.

so maybe better to do a fresh install. in that case, what i'd like to do is to create a fresh 9.10 system on a usb device, apply all of my changes to that stick (packages, configs, ...), try it out for bit, and then bring all of that back onto my hard drive as my standard boot. isn't this what 99% of end users would want?

so i can create the 9.10 usb install and with this thread can bring over my package list (mostly), but what about the configs and other files that are in various system folders? how do i get those to the new system? right, i don't have a list of those changes made over the past year.... and then, once happy with the new system, how to get it back to my hard drive.

am i right that this procedure doesn't exist? i hear linux guys talk about doing something like this, but don't find the tools or clear instructions anywhere.

i'll post this question elsewhere as a fresh question, but thought i might get some answers here as this thread is at least close to what i want to do.

---

### Post by COKEDUDE on 2010-11-08
Great guide. Thank you for this.

---

### Post by SaintDanBert on 2010-11-09
> **kazemizuhi said:**
> 
...
I have yet to find a tutorial or instructions for downloading an installation file to one's drive, then proceeding to install said file as one is wont to do in a Windows environment. Everything I have seen thus far has required sudo apt-get or use of synaptic. As far as I know these methods do not provide me with an installation file which I can re-use at a later date. This leads me to believe that it may not be possible. Yet my better judgement tells me otherwise; for how did the average linux user get-by prior to the prevalence of the internet?
...


Find the raw package files of your choice. They need to be *.DEB format packages. (There are ways to convert from other package formation into *.DEB format, but I won't go there.) You fetch the packages into a folder on your local computer, say "$HOME/myPackages"
Then:
```

prompt$ cd $HOME/myPackages
prompt$ sudo  dpkg --install  pack1.deb
prompt$ sudo  dpgh --install  pack2a.deb pack2b.deb ... pack2z.deb
...
prompt$ sudo  dpkg --install  packLast.deb

```

The first example is for a package that stands alone.
The second example is for a package with dependencies. Yes, you need to manage these on your own.

COMMENTARY:  I know that there are ways to run apt against local copies of package files. I've never done it. Maybe someone else can contribute that.

~~~ 0;-Dan

---

### Post by PayPaul on 2011-10-09
> **SaintDanBert said:**
> Find the raw package files of your choice. They need to be *.DEB format packages. (There are ways to convert from other package formation into *.DEB format, but I won't go there.) You fetch the packages into a folder on your local computer, say "$HOME/myPackages"
Then:
```

prompt$ cd $HOME/myPackages
prompt$ sudo  dpkg --install  pack1.deb
prompt$ sudo  dpgh --install  pack2a.deb pack2b.deb ... pack2z.deb
...
prompt$ sudo  dpkg --install  packLast.deb

```

The first example is for a package that stands alone.
The second example is for a package with dependencies. Yes, you need to manage these on your own.

COMMENTARY:  I know that there are ways to run apt against local copies of package files. I've never done it. Maybe someone else can contribute that.

~~~ 0;-Dan
Most of the Deb packages I've installed have only required opening up Software Manager to do it. For some programs I have found with dependencies it's best to use Synaptic. On occasion and I suspect it will be more so I've had to use the command lines I either find in the site for the program to add repositories or use the get-apt command to make certain the program installs.

I have a similar question: As I understand it the markings file I created in Synaptic will allow me to reinstall all the packages/programs currently on my system when I go to a clean install of the new release. Does that markings file also take into account dependencies? I did also discover on my own the need to check the box involving installs as well as changes. I'm hoping that the dependencies of these packages/programs will resolve themselves as well.

---

### Post by PayPaul on 2011-10-09
> **iwfur25 said:**
> /var/cache/apt/archives contains the downloaded packages. Back it up (if you have the space) and restore it along with the markings and apt won't have to re-download all (or maybe most?) of the packages.

I looked into that folder and found very little in it. In fact it's listed as having files with 0 bytes and in the Apt folder there are two bin files, pkgcache.bin and srcpkgcache.bin. What are those? I've backed up the markings but do wonder about what will happen when I attempt to reinstall these packages. It's been indicated that a new installation of the upcoming release may cause compatibility problems. Will there be any kind of messages during the reinstall which will help out in the proper install of my present packages?

---

