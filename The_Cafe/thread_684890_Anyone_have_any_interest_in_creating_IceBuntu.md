---
title: "Anyone have any interest in creating IceBuntu?"
date: 2008-02-01
forum: The Cafe
---

### Post by aysiu on 2008-02-01
I know [Fluxbuntu](http://fluxbuntu.org/js.html) is already in production and is at Release Candidate instead of 1.0

Both Damn Small Linux (Fluxbox) and Puppy Linux (IceWM) are excellent choices for people with low specs, but if someone wants something Ubuntu-based (with the same software repositories, release cycle, and *sudo* implementation) for an older computer, the only choices right now are Xubuntu, Fluxbuntu, or manual installation and configuration of IceWM (or some other window manager) manually.

If the forums' user base is any indication, Fluxbox is very popular among Ubuntu users, but there should be a significant enough number of us IceWM users to be able to put together a low-spec-friendly Ubuntu for IceWM users--IceBuntu.

I'm thinking it'd be an Alternate CD, since 64 or 128 MB of RAM may not be enough to run a live session and Ubiquity at the same time. Here's the problem: I don't know how to do it, so I'm asking the community to help out.

I've taken a look at Reconstructor, and as far as I can tell, it doesn't let you truly modify the installation the Alternate CD sets up--only add and remove packages. I wouldn't want IceBuntu to just be IceWM installed. It would be great to have some sensible configuration choices, a good default theme ([ThinBlack](http://ubuntuforums.org/showthread.php?t=321994), for example), and launcher icons for popular applications.

If you're interested in creating a IceBuntu disk or even, if it's easier, an IceBuntu metapackage, please post in this thread and let me know what you're willing to contribute and what you think IceBuntu should be like.

My technical know-how is a little weak, so I can contribute trying to coordinate people's efforts and maybe publicizing IceBuntu a bit on my Psychocats website.

Others?

**Edit**: It looks as if other people are much better at figuring out this ISO-remastering thing than I am. If you have torrents or other ideas you want to post up, please post them on the Ubuntu Wiki, since this thread is now becoming quite long.
[https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu)

---

### Post by gn2 on 2008-02-01
Sounds like a very worthwhile project.

Perhaps [these instructions]("http://www.linuxscrew.com/2007/07/31/how-to-create-custom-linux-iso-image/") might help.

Maybe start with the Xubuntu Alternate CD and strip out the XFCE bits and replace them with the required packages to create IceBuntu.

---

### Post by aysiu on 2008-02-01
> **gn2 said:**
> Sounds like a very worthwhile project.

Perhaps [these instructions]("http://www.linuxscrew.com/2007/07/31/how-to-create-custom-linux-iso-image/") might help.

Maybe start with the Xubuntu Alternate CD and strip out the XFCE bits and replace them with the required packages to create IceBuntu.
So if I start with the Xubuntu Alternate CD, take out all the Xfce packages, replace them with IceWM packages, and then modify the configuration files in /tmp/newiso and create the new ISO from that, it should work?

---

### Post by gn2 on 2008-02-01
There's one easy way to find out, I've never tried, it just looks like a simple method.

---

### Post by aysiu on 2008-02-01
> **gn2 said:**
> There's one easy way to find out, I've never tried, it just looks like a simple method.
I'll give it a shot and report back. Then the problem would be seeding the torrent. I guess I could just put it up on Psychocats as straight download for those who know how to seed torrents...

One step at a time, though...

---

### Post by RAV TUX on 2008-02-01
> **aysiu said:**
> I know [Fluxbuntu]("http://fluxbuntu.org/js.html") is already in production and is at Release Candidate instead of 1.0

Both Damn Small Linux (Fluxbox) and Puppy Linux (IceWM) are excellent choices for people with low specs, but if someone wants something Ubuntu-based (with the same software repositories, release cycle, and *sudo* implementation) for an older computer, the only choices right now are Xubuntu, Fluxbuntu, or manual installation and configuration of IceWM (or some other window manager) manually.

If the forums' user base is any indication, Fluxbox is very popular among Ubuntu users, but there should be a significant enough number of us IceWM users to be able to put together a low-spec-friendly Ubuntu for IceWM users--IceBuntu.

I'm thinking it'd be an Alternate CD, since 64 or 128 MB of RAM may not be enough to run a live session and Ubiquity at the same time. Here's the problem: I don't know how to do it, so I'm asking the community to help out.

I've taken a look at Reconstructor, and as far as I can tell, it doesn't let you truly modify the installation the Alternate CD sets up--only add and remove packages. I wouldn't want IceBuntu to just be IceWM installed. It would be great to have some sensible configuration choices, a good default theme ([ThinBlack]("http://ubuntuforums.org/showthread.php?t=321994"), for example), and launcher icons for popular applications.

If you're interested in creating a IceBuntu disk or even, if it's easier, an IceBuntu metapackage, please post in this thread and let me know what you're willing to contribute and what you think IceBuntu should be like.

My technical know-how is a little weak, so I can contribute trying to coordinate people's efforts and maybe publicizing IceBuntu a bit on my Psychocats website.

Others?

Actually this already exist, it's called LinuxICE and it is based on Ubuntu.

The Distropedia article on LinuxICE is [here]("http://cafelinux.org/distropedia/?q=node/25").

The LinuxICE website is [here]("http://linuxice.com/index.php").

While LinuxICE has what you desire, IceWM based on Ubuntu it is made for in car computers I am almost certain it would work on old PC's.

Also these LinuxICE guys I am sure would welcome any DEV help to come out with a community version that is just what you want.

The LinuxICE forum is [here]("http://www.nextabyte.com/nanonymous/forum/viewforum.php?f=6").

Instead of reinventing the wheel swing over to LinuxICE and offer to help. ;)

RAV TUX

---

### Post by RAV TUX on 2008-02-01
Also LinuxICE Torrent and download mirrors are here:

[Torrent]("http://www.nextabyte.com/nanonymous/forum/download.php?id=167")          

Mirrors:
        
 [Mirror 1]("http://student.ccbcmd.edu/%7Ejyav/linuxICE/LinuxICE-Beta1-2.iso")
        
 [Mirror 2]("http://spuzzdawg.net/linuxice/LinuxICE-Beta1-2.iso")
        
 [Mirror 3]("http://nextabyte.com/nanonymous/downloads/LinuxICE-Beta1-2.iso")
        
 [Mirror 4]("http://mitchp.homedns.org/LinuxICE-Beta1-2.iso")
        
 [Mirror 5]("http://66.135.41.165/linuxice/LinuxICE-Beta1-2.iso")

I hope this helps, if LinuxICE is not what you were thinking and you still want to make a ICEbuntu, I am sure many here including myself would enjoy an aysui version of an IceWM/Ubuntu distro. 

Having witnessed first hand Rui Pais building the Oz OS RC I would consult Rui for a quick HOWTo, somewhere Rui posted a helpful post on this, if I find it I will let you know.

---

### Post by aysiu on 2008-02-01
> **RAV TUX said:**
> Actually this already exist, it's called LinuxICE and it is based on Ubuntu.

The Distropedia article on LinuxICE is [here]("http://cafelinux.org/distropedia/?q=node/25").

The LinuxICE website is [here]("http://linuxice.com/index.php").

While LinuxICE has what you desire, IceWM based on Ubuntu it is made for in car computers I am almost certain it would work on old PC's.

Also these LinuxICE guys I am sure would welcome any DEV help to come out with a community version that is just what you want.

The LinuxICE forum is [here]("http://www.nextabyte.com/nanonymous/forum/viewforum.php?f=6").

Instead of reinventing the wheel swing over to LinuxICE and offer to help. ;)

RAV TUX
Thanks for that link, RAV TUX. You know more about distro availability than anyone else here probably.

While I would love to avoid "reinventing the wheel," it may actually be more work to modify LinuxICE than to modify normal Ubuntu: > Kernel:
-2.6.20
-Suspend2 built in
-touchscreen support
-support for common usb->serial devices

Packages:
-GPS support
-NavIt GPS application
-Carman ODB-II statistics monitoring
-Samba
-SSH

Light Window Manager:
-MatchBox

xorg:
-evtouch driver built in with calibrator

front-end:
-nGhost Media Center Beta 0.95

codecs (possibly included proprietary codecs):
-dvd support It looks as if they've highly customized the kernel and xorg specifically for an in-car interface.

I'm going to start off with gn2's suggestion, but I'll keep LinuxICE in mind.

---

### Post by RAV TUX on 2008-02-01
Glad to help please see my edit to my second post, I believe Rui ran into time consuming problems with reconstructor, it may not be the right direction. 

I believe Rui built Oz OS by "hand" using the terminal which is less constricting then other ways.

...but before I mis-represent let me contact Rui and see if he can help with a proper response.

Edit to second post:
> **RAV TUX said:**
> 
I hope this helps, if LinuxICE is not what you were thinking and you still want to make a ICEbuntu, I am sure many here including myself would enjoy an aysui version of an IceWM/Ubuntu distro. 

Having witnessed first hand Rui Pais building the Oz OS RC I would consult Rui for a quick HOWTo, somewhere Rui posted a helpful post on this, if I find it I will let you know.

---

### Post by Mateo on 2008-02-01
Not interested personally, but if you go this route I would suggest looking to the Eee source code for some ideas on how to make IceWM more attractive.  It's the only instance of IceWM that I've really liked.

One good feature of IceWM that isn't in Gnome or (to my knowledge) KDE is built-in minimize to tray capabilities for every application.

---

### Post by aysiu on 2008-02-01
I tried gn2's suggestion, and I end up with a bunch of files: ```
boot.cat  f1.txt  f4.txt  f7.txt  initrd.gz     linux
boot.txt  f2.txt  f5.txt  f8.txt  isolinux.bin  splash.rle
f10.txt   f3.txt  f6.txt  f9.txt  isolinux.cfg
``` The text files are the F-keys at boot time that tell you about the different boot flags. The boot.txt is the text that appears when you first boot up. The rest of the files are binaries.

I'm not sure how to modify those files to make the ISO include different files.

---

### Post by zmjjmz on 2008-02-01
Although I can't contribute any programming work, I'd be glad to test it when it comes out.

---

### Post by Vadi on 2008-02-01
Not interested, partially because my computer isn't *that* old. I'm not sure many people use a computer below Xubuntu/Fluxbuntu's standards either (just installed Xubuntu on a really, really old Dell laptop).

---

### Post by aysiu on 2008-02-01
> **Vadi said:**
> Not interested, partially because my computer isn't *that* old. I'm not sure many people use a computer below Xubuntu/Fluxbuntu's standards either (just installed Xubuntu on a really, really old Dell laptop).
It wouldn't really be *below* Fluxbuntu's standards. Both Fluxbox and IceWM are lightweight window managers. It's just a matter of preference. Some of us prefer IceWM to Fluxbox.

---

### Post by Vadi on 2008-02-01
Oh go ahead :)

(-sigh-).

---

### Post by aysiu on 2008-02-01
> **zmjjmz said:**
> Although I can't contribute any programming work, I'd be glad to test it when it comes out.
Thanks. Let's see *if* it comes out. But if I can get something out, I'd love to have testers!

---

### Post by markp1989 on 2008-02-01
> **aysiu said:**
> Thanks. Let's see *if* it comes out. But if I can get something out, I'd love to have testers!

i can help test if you like aswell

i thought u mite find this like interesting, i have used it to create custom live cds, and i found it usefull, i used it to create a live cd, for browsing hte web on my sisters computer, all it had was ubuntu base xfce and firefox, but it did what i wanted it to 
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by aysiu on 2008-02-01
I appreciate the links people are providing, and I *am* looking at them as well as trying to find some on my own.

They all look very intimidating to me. I don't know what *chroot* means. I have never remastered an .ISO, created Linux from scratch, or done anything along those lines.

---

### Post by markp1989 on 2008-02-01
i have had a go at creating a CD, it runs from the CD fine, but i currently have no way of testing the installation, does any one have a test system they can use, or somewhere for me to upload a 263mb iso?

currently all that is installed is:
icewm
gdm
dillo
xfe
synaptic

i have not installed other programs yet as i want to keep the size of the iso down.

---

### Post by zmjjmz on 2008-02-01
I have three possible test systems.
is 160M RAM  and a 400Mhz Celeron enough?

---

### Post by Dr Small on 2008-02-01
I'd help test it if you made it :D

---

### Post by markp1989 on 2008-02-01
> **zmjjmz said:**
> I have three possible test systems.
is 160M RAM  and a 400Mhz Celeron enough?

should be, im not 100% sure what the requirements will be, im currently installing it on a virtual machine with 128mb ram.


i just spoke to my friend who said he will let me test it on his old computer, which has a 500mhz cpu and 512mb of ram 

i will post back how i get on,

---

### Post by markp1989 on 2008-02-01
> **Dr Small said:**
> I'd help test it if you made it :D

i have the iso, i have only just started doing it today.

i just need some way of getting the iso out to people.

---

### Post by K.Mandla on 2008-02-01
> **Dr Small said:**
> I'd help test it if you made it :D
I was going to say, I know Dr Small would be on board. :)
> **aysiu said:**
> I appreciate the links people are providing, and I *am* looking at them as well as trying to find some on my own.

They all look very intimidating to me. I don't know what *chroot* means. I have never remastered an .ISO, created Linux from scratch, or done anything along those lines.
There's a wiki page somewhere about remastering the live CD. I'll have to search around for it though. 

There's also [isomaster]("http://packages.ubuntu.com/gutsy/otherosfs/isomaster") if you want to just tamper with a standing installation ISO and see if that yields any results.

---

### Post by markp1989 on 2008-02-01
> **markp1989 said:**
> should be, im not 100% sure what the requirements will be, im currently installing it on a virtual machine with 128mb ram......i will post back how i get on,

the install works well on teh virtual machine,the install was a tad slow, but after that it runs very well, the install takes up 887mb on the hard disk.

---

### Post by markp1989 on 2008-02-01
i just finished installing it on my friends old computer, and it runs well.

cpu: AMD-K6  450mhz
ram: 512mb

results were similar to the virtual machine, install was abit slow, but after that it ran well

---

### Post by markp1989 on 2008-02-01
> **zmjjmz said:**
> I have three possible test systems.
is 160M RAM  and a 400Mhz Celeron enough?

i think that should be fine.

does any one know any free hosting sites, that will accept a 265mb iso

EDIT: there is a torrent here (my first attempt at making a torrent, so  can some one test it and tell me if it downloads, when you have finished please seed it for a while) 
[http://www.2shared.com/file/2793710/a283f4ed/iceubuntualpha1.html](http://www.2shared.com/file/2793710/a283f4ed/iceubuntualpha1.html)

torrent will be slow for a bit, as i am the only person uploading

Instalation instructions: 
when the live CD boot, click on the debian (Start) button and open the terminal, then type "ubiquity" and press enter, and the ubuntu installer will run

---

### Post by phrostbyte on 2008-02-01
Correction aysiu (I don't know if someone said this already), Puppy Linux uses jwm as it's WM.

Why not use Ubuntu's build system (Soyuz) to make this distro?

---

### Post by phrostbyte on 2008-02-01
system can be composed of two major metapackages

ubuntu-minimal - same as in all ubuntu versions
icebuntu-desktop - all the packages specific to icebuntu

---

### Post by RAV TUX on 2008-02-01
aysiu, I almost forgot...

The easiest way that I have made a Ubuntu based CD/DVD ISO was with [remastersys]("http://www.remastersys.klikit-linux.com/"), you can use this to develop your ISO in approximately under 10 minutes.

I used this to make an Oz OS DVD ISO based on Ubuntu Hebrew Remix(unreleased to public).

I have yet to find anything easier. (...but Rui Pais' way is still probably even better)
> 
[SIZE=4][COLOR=#000099]**What is remastersys?**[/COLOR][/SIZE]                      [LEFT]   [COLOR=#000099]**Remastersys**[/COLOR] is a tool that can be used to do 2 things with an existing Klikit or Ubuntu or derivative installation.[/LEFT]
[LIST]
[*]It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
[*]It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.[/LIST][LEFT][SIZE=4][COLOR=#000099]**How did it come to be?**[/COLOR][/SIZE][/LEFT]
        [LEFT]   It was initially created by my desire to be able to easily backup or create a distributable copy of an Ubuntu or derivative installation.  Inspiration for this tool came from the mklivecd script that Mandriva uses and the remasterme script that is in PCLinuxOS.  I had originally looked at some way to port these over to Ubuntu but that proved to be way too much work as it wasn't compatible with casper and ubiquity and used too many Mandriva specific things,  so I set out to create remastersys from scratch.[/LEFT]
        [LEFT]   After studying casper and ubiquity along with some wikis on the internet,  I created the first version of remastersys.  The biggest problem had to do with the making of the live cd user.  I had initially made a small workaround that created the livecd user during the building of the livecd system but that wasn't always consistent and became a showstopper with Feisty.  I took a few months off from working on it to enjoy the summer with my family.[/LEFT]
        [LEFT]   I was about to give up on it until I received a nice message from Chris of Klikit who informed me he had used remastersys to create Klikit.  After taking a look at Klikit and seeing how great it was, I decided to push the rest of the way and finish it.  I ironed out the last few bugs and remastersys 2.0 was born.  It should be released shortly as I am also working on a gui frontend for it for the folks that aren't comfortable enough to use the command line interface.[/LEFT]
                [LEFT][COLOR=#000099]**[SIZE=4]How do you use it?[/SIZE]**[/COLOR][/LEFT]
        [LEFT]   At the command line, you simply run "sudo remastersys backup" to make a full system backup,  or "sudo su" to become root and then run "remastersys dist" to make a distributable copy to share with friends.  
    There is a configuration file - /etc/remastersys.conf where you can set things like the name of the livecd/dvd, the live session username, other files to exclude from the cd/dvd, etc.[/LEFT]
        [LEFT]   If you are a gui person, simply click on the "Remastersys Backup" icon on the desktop and you can select which option you want to run.[/LEFT]
        [LEFT]  There is also a gui now and it is called Remastersys Backup.  You can find the icon on your desktop once you install remastersys. [/LEFT]
        [LEFT][COLOR=#000099]**[SIZE=4]Some notes about using the dist option[/SIZE]**[/COLOR][/LEFT]
        [LEFT]   You should start with a clean install of Klikit, Ubuntu or variant and use a single user to make all changes.  You should not install any proprietary video drivers like the nvidia or ati drivers as they will not be used on the livecd and users will have to reinstall them after installation.  Clean up history and cache and copy over the contents to /etc/skel but be sure to change the ownership of everything in /etc/skel to root.  While the livecd/dvd is being created, you will not be able to open any other apps or windows.  It is highly recommended to become root to do this by issuing "sudo su" in a terminal window and then running "remastersys dist".  The reason for this is that the uid for the users on the system have to be changed to be below 1000 or the casper livecd scripts will not create the live session user properly.  Remastersys will restore the UID's back to their original values once it is finished.[/LEFT]
        
        [LEFT][COLOR=#000099]**[SIZE=4]Some notes about the backup option[/SIZE]**[/COLOR][/LEFT]
        [LEFT]   You can log into the livecd/dvd with any valid user that was on the system on the hard drive but it is recommended to log into the first one created during the initial installation as that is the user that can sudo.  When you come to install this back to a hard drive, the user setup portion of ubiquity (the install program) is just a placeholder other than the system name.  The username and password set here will not be used but must be created in order to continue with the installation.  Part of the reason for this is that your users are already created so you don't need to create them again,  but more importantly because user setup is an integral part of the install program and cannot be removed or bypassed easily.  If you were using proprietary video drivers like the nvidia or ati ones, you will need to reinstall them.  The Ubuntu livecd scripts prevent these from running properly but reinstalling them after installation will make them work again.[/LEFT]
                [LEFT][COLOR=#000099]**[SIZE=4]Where to go to ask questions, report bugs, request features or make recommendations?[/SIZE]**[/COLOR][/LEFT]
        [LEFT]The main support area is on the [Klikit User Forum]("http://loscompanion.com/forums/index.php?board=58.0")[/LEFT]
        
       [LEFT][COLOR=#000099]**[SIZE=4]What license is remastersys covered by?[/SIZE]**[/COLOR][/LEFT]
        [LEFT]It is released under the [GNU GPL Version 2]("http://www.gnu.org/licenses/old-licenses/gpl-2.0.html")[/LEFT]
        
        [LEFT][COLOR=#000099]**[SIZE=4]Where can I get remastersys?[/SIZE]**[/COLOR][/LEFT]
        The Remastersys repository needs to be added to your /etc/apt/sources.list
       
 Paste the following into the sources.list:
       
 # Remastersys
 deb [http://www.remastersys.klikit.org/repository](http://www.remastersys.klikit.org/repository) remastersys/
       
 Then simply either reload in Synaptic or you can "sudo apt-get update" and install remastersys.[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by RRS on 2008-02-01
> **markp1989 said:**
> ......a torrent here (my first attempt at making a torrent, so  can some one test it and tell me if it downloads, when you have finished please seed it for a while) 

Torrent file downloaded fine, opened with Deluge no problem. 

The tracker does seem to have a hard time establishing/maintaining connections though. Occasionally will show 1 seeder and 1 peer available but won't maintain a connection. 
Not that savvy to the ways of torrents though so could be ISP related or ??? No matter, I'll just leave it open and wait, I've got time. And I'll keep seeding when done.

Aysiu; my skills are also quite limited beyond testing but if I find anything usefull I'll let you know. Played with Ice a bit in the past and it looked promising but I'd welcome something a bit more "pre-packaged"

BTW, I'm also seeding the OZ-OS torrent RavTux mentioned in case anyone's interested.
Lokks like I'm gonna be busy w/installs Sunday :popcorn:

---

### Post by markp1989 on 2008-02-01
> **RRS said:**
> Torrent file downloaded fine, opened with Deluge no problem. 

The tracker does seem to have a hard time establishing/maintaining connections though. Occasionally will show 1 seeder and 1 peer available but won't maintain a connection. 
Not that savvy to the ways of torrents though so could be ISP related or ??? No matter, I'll just leave it open and wait, I've got time. And I'll keep seeding when done.

Aysiu; my skills are also quite limited beyond testing but if I find anything usefull I'll let you know. Played with Ice a bit in the past and it looked promising but I'd welcome something a bit more "pre-packaged"

BTW, I'm also seeding the OZ-OS torrent RavTux mentioned in case anyone's interested.
Lokks like I'm gonna be busy w/installs Sunday :popcorn:

ok, thankyou, are there any better trackers i could use? dont think it helps that my internet is not all that fast

---

### Post by RAV TUX on 2008-02-01
> **RRS said:**
> 

BTW, I'm also seeding the OZ-OS torrent RavTux mentioned in case anyone's interested.
Lokks like I'm gonna be busy w/installs Sunday :popcorn:

RRS Thanks for seeding the Oz OS Torrent, I hope you enjoy it! ;)

Remember to post at the[ CafeLinux Forum]("http://www.cafelinux.org/forum/") for support if needed.

aysui do you have any screenshots?

---

### Post by markp1989 on 2008-02-01
i give up with torrents, there getting on my nervs, im going to see if i can find any were to upload it

---

### Post by RRS on 2008-02-01
> **RAV TUX said:**
> RRS Thanks for seeding the Oz OS Torrent, I hope you enjoy it! ;)

Remember to post at the[ CafeLinux Forum]("http://www.cafelinux.org/forum/") for support if needed.

No problem to seed, do have to limit upload rate though or it kills my browsing speed.
Have E17 CVS running on an old Dell thanks to Rui Pais' thread currently but I'll have to make room on my 64bit machine before I can try Oz OS.

> **markp1989 said:**
> the tracker i was using in the first torrent didnt seem that good, so i have created a new torrent using a different tracker 

sorry to anyone who had difficulties with the other 1

No problem.
Deluge offered to merge the trackers so I let it. If someone doesn't think that's best, let me know.

My weekend project list just keeps growing, supposed to play with some cars too. Oh well, maybe I can wait 'till Monday to sleep @ work........

Aysiu: If I get time to install something I'll give Remastersys a try per Rav Tux's advice, looks promising.

---

### Post by RRS on 2008-02-01
> **markp1989 said:**
> i give up with torrents, there getting on my nervs, im going to see if i can find any were to upload it
Don't worry, I don't even know how to create a torrent file, just download and reseed.....

I'll go ahead and leave it open overnight in case you have some luck :)

---

### Post by aysiu on 2008-02-02
Klikit seems a bit more up my alley (I am a point-and-click guy, after all). Unfortunately, the download page appears not to be working right now. Maybe I'll try it again later.

---

### Post by TeaSwigger on 2008-02-02
What is your idea / policy regarding apps? Do you have a list? All it takes is one hefty app to bring an otherwise lithe setup to its knees.

---

### Post by markp1989 on 2008-02-02
[http://www.2shared.com/file/2794682/15a7c06/icebuntualpha.html](http://www.2shared.com/file/2794682/15a7c06/icebuntualpha.html)

tried making another torrent, sorry bout the other 2 trys, was very late.

as for applications, currently al that are installed is:
dillo
xfe
synaptic

i have not installed many things as i want to keep the size of the iso down, and i am not sure what apps would be best.

---

### Post by sagarhshah on 2008-02-02
Am downloading it,

Have an old pc lying in the basement. Have been looking to try and do something with it. Now I have an excuse to bring it out.

Will seed torrent once it downloads.

Sagar

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> Am downloading it,

Have an old pc lying in the basement. Have been looking to try and do something with it. Now I have an excuse to bring it out.

Will seed torrent once it downloads.

Sagar

thankyou, is it downloading ok?

---

### Post by sagarhshah on 2008-02-02
> **markp1989 said:**
> thankyou, is it downloading ok?

Unfortunately it is not.
It shows that there is one seeder in the swarm but it doesn't want to connect to it :S

---

### Post by RAV TUX on 2008-02-02
> **RRS said:**
> No problem to seed, do have to limit upload rate though or it kills my browsing speed.
Have E17 CVS running on an old Dell thanks to Rui Pais' thread currently but I'll have to make room on my 64bit machine before I can try Oz OS.Any little bit helps.

Rui is ahead of his time with releasing a 64bit version first; as Rui and I are both 64bit users it makes perfect sense also.

I look forward to your feedback as I am sure you will love Oz OS.

> **RRS said:**
> 
Aysiu: If I get time to install something I'll give Remastersys a try per Rav Tux's advice, looks promising.
Remastersys is just plain easy and a joy to use.

> **aysiu said:**
> Klikit seems a bit more up my alley (I am a point-and-click guy, after all). Unfortunately, the download page appears not to be working right now. Maybe I'll try it again later.

It was working for me earlier, I hope it is back up for you soon.

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> Unfortunately it is not.
It shows that there is one seeder in the swarm but it doesn't want to connect to it :S

hmm, im new to creating torrents, anyone have any ideas that could help me?

thankyou

---

### Post by sagarhshah on 2008-02-02
> **markp1989 said:**
> hmm, im new to creating torrents, anyone have any ideas that could help me?

thankyou

It seems you are using ktorrent. Am i right? I don't have any experience with it.
All I could probably ask is.
Is your torrent client pointing to the right folder where the iso is stored?


What does it show on your side in ktorrent?
sagar

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> It seems you are using ktorrent. Am i right? I don't have any experience with it.
All I could probably ask is.
Is your torrent client pointing to the right folder where the iso is stored?


What does it show on your side in ktorrent?
sagar

yes i am using ktorrent (how do u know that), attached a screen print of it.


tried making one with deluge [http://www.mininova.org/tor/1145655](http://www.mininova.org/tor/1145655) 

i dont know if it will be any better. any one experienced with torrents, got any tips they could give?

---

### Post by p_quarles on 2008-02-02
I don't have any experience creating new torrents, but here's the error message I'm getting from that file:
```
An error occurred while loading the torrent. The torrent is probably corrupt or is not a torrent file.
```
The only thing I can think of here would be to try placing the torrent file on a different tracker.

---

### Post by bufsabre666 on 2008-02-02
i think linuxtracker.org might be a good choice

---

### Post by K.Mandla on 2008-02-02
> **RAV TUX said:**
> Actually this already exist, it's called LinuxICE and it is based on Ubuntu. ...

While LinuxICE has what you desire, IceWM based on Ubuntu ...
Pardon me, but the specs page for LinuxICE says Matchbox is the window manager. Am I mistaken in that?
[QUOTE=LinuxICE site]Light Window Manager:
-MatchBox[/QUOTE]

---

### Post by Rui Pais on 2008-02-02
Hi,
only now i could give a word here (only this morning i read RAV TUX mail, but i have to go out...)

aysiu, if you need any specific help, just say.

usually (for my limited knowledge) livecd, go in 2 different categories.
Those who creates a live system on a squashfs file and those who seems to install from scripts from a much more minimal livecd (on an initird basic system i suppose), and it's much more difficult to deal.

Typical of the first are Ubuntu and X/K/Edu/Ge... variations.
Fluxbuntu it's an example of the second.

I have some experience with creating squashfs, but almost none in the other...

Another possible way, i think, it's just remake the fluxbuntu, replacing at pressed file the installation of fluxbuntu-desktop by icewm or some more elaborated meta-package that would install icewm+extras+config.

---

### Post by aysiu on 2008-02-02
Thanks for coming in to this thread, Rui Pais. If I do have specific help, I'll definitely ask for it.

Unfortunately, I have *no* experiencing remastering CDs at all. I don't even know what *squashfs* is!

---

### Post by aysiu on 2008-02-02
> **TeaSwigger said:**
> What is your idea / policy regarding apps? Do you have a list? All it takes is one hefty app to bring an otherwise lithe setup to its knees. I don't know. I'm trying to take it one step at a time. I guess once I know it can be made/easily made, it would make sense to start discussing what apps to put in. Speaking as someone who has had low-spec'ed PCs I've put Ubuntu on (one was a 766 MHz PC with 128 MB of RAM), I'd say having one or two heavy apps isn't so bad. Even Damn Small Linux has Firefox in it.

> **phrostbyte said:**
> Correction aysiu (I don't know if someone said this already), Puppy Linux uses jwm as it's WM. Wow! I'm not keeping up with the times. You're right. Puppy does use JWM. And, as a matter of fact, I just checked the DSL site, and DSL *also* now uses JWM instead of Fluxbox.

> Why not use Ubuntu's build system (Soyuz) to make this distro? Maybe because I don't know what Soyuz is?

---

### Post by sagarhshah on 2008-02-02
> **markp1989 said:**
> yes i am using ktorrent (how do u know that), attached a screen print of it.


tried making one with deluge [http://www.mininova.org/tor/1145655](http://www.mininova.org/tor/1145655) 

i dont know if it will be any better. any one experienced with torrents, got any tips they could give?

Sorry for the late reply went down to watch a bit of football.

tried the one you have put up on mininova.
still no dice!!
it still uses the the piratebay tracker.

Maybe you should try another public tracker...

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> Sorry for the late reply went down to watch a bit of football.

tried the one you have put up on mininova.
still no dice!!
it still uses the the piratebay tracker.

Maybe you should try another public tracker...

maybe, are there any trackers that you would recommend ?

---

### Post by init1 on 2008-02-02
> **aysiu said:**
> I tried gn2's suggestion, and I end up with a bunch of files: ```
boot.cat  f1.txt  f4.txt  f7.txt  initrd.gz     linux
boot.txt  f2.txt  f5.txt  f8.txt  isolinux.bin  splash.rle
f10.txt   f3.txt  f6.txt  f9.txt  isolinux.cfg
``` The text files are the F-keys at boot time that tell you about the different boot flags. The boot.txt is the text that appears when you first boot up. The rest of the files are binaries.

I'm not sure how to modify those files to make the ISO include different files.
The filesystem on the disk is compressed in "initrd.gz". Gunzip it, 
```

gunzip initrd.gz

```
and run "file" on it. 
```

file initrd

```
If "file" tells you it's a ext2 filesystem, mount it with
```

mount -o loop initrd /somemountpoint

```
If it tells you it's a cpio archieve, extract it with
```

cpio -id<initrd

```
If cpio complains, it's either not a cpio or it wants you to rename it to
```

mv initrd initrd.cpio

```
And then run the cpio command again
This should give you the contents of "/" in your current directory.
In either case, this will give you a chance to edit the contents
When you're done, if it was a ext2 filesystem, just umount it
```

umount /somemountpoint

```
If it was a cpio archeive, rebuild it
```

cpio -H newc -o > initrd

```
In either case, recompress it with
```

gzip initrd

```

---

### Post by sagarhshah on 2008-02-02
> **markp1989 said:**
> maybe, are there any trackers that you would recommend ?

Check your inbox.
Have sent you some public trackers on there.

Hopefully they will work

I'll look for more and send them as I come across any.

Sagar

---

### Post by Mazza558 on 2008-02-02
I made a logo for your project. 

If you want any changes, just ask. :)

EDIT: forgot the Ubuntu logo. I'll add it in later, methinks.

---

### Post by markp1989 on 2008-02-02
tried a torrent using a different tracker [http://www.mininova.org/tor/1145865](http://www.mininova.org/tor/1145865)

im sorry about the torrents, i have never tried to make a torrent before

---

### Post by sagarhshah on 2008-02-02
> **markp1989 said:**
> tried a torrent using a different tracker [http://www.mininova.org/tor/1145865](http://www.mininova.org/tor/1145865)

im sorry about the torrents, i have never tried to make a torrent before


both trackers are connecting and seem to update fine.
So it might be something on your side.
anybody else got much experience with torrents?

maybe you can transfer the iso to someone who might have better knowledge with torrents.

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> both trackers are connecting and seem to update fine.
So it might be something on your side.
anybody else got much experience with torrents?

maybe you can transfer the iso to someone who might have better knowledge with torrents.

that would probably be best, would any one be willing to create teh torrent for me if i can find a way to get the iso to you?

---

### Post by sagarhshah on 2008-02-02
> **markp1989 said:**
> that would probably be best, would any one be willing to create teh torrent for me if i can find a way to get the iso to you?

Upload to rapidshare/megaupload or some other download website.
You will need to split the files into three equal part so as to keep them under 100MB limit.

I have a premium account with rapidshare so I can download all parts immediately. Those who might not have a premium account will have to wait between downloading each part of the iso.

Any other ideas anyone else?

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> Upload to rapidshare/megaupload or some other download website.
You will need to split the files into three equal part so as to keep them under 100MB limit.

I have a premium account with rapidshare so I can download all parts immediately. Those who might not have a premium account will have to wait between downloading each part of the iso.

Any other ideas anyone else?

how do i break the iso up?

---

### Post by sagarhshah on 2008-02-02
> **markp1989 said:**
> how do i break the iso up?

I believe it should work something like this.

split -b90m filename.iso

to join them i believe it would be like this

cat filename.isoaa filename.isoab  filename.isoac >> filename.iso

oh yeah don't forget to also md5sum on the iso before you split it and post it here.

Sagar

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> I believe it should work something like this.

split -b90m filename.iso

to join them i believe it would be like this

cat filename.isoaa filename.isoab  filename.isoac >> filename.iso

oh yeah don't forget to also md5sum on the iso before you split it and post it here.

Sagar


mark@mark-desktop:~/Desktop$ md5sum '/home/mark/Desktop/icebuntualpha.iso' 92bac66f1a0f24dbc66bd77fae6ad0a2  /home/mark/Desktop/icebuntualpha.iso
 check sum is there now im about to upload the files to rapid share

---

### Post by koenn on 2008-02-02
I don't have any interest in an IceBuntu (and shouldn't that be Ubuntu, Icewm Edition ?) but I've been playing with preseeds and metapackages before, so I had a look at it. 

It shouldn't be that hard. 
I think you are going to need a metapackage. Ubuntu install CD's just call a metapackage so you can quite easily replace that with one you made, and you don't have to worry about how the installer goes about installing all that software. 

You do, however, need to add any new package (eg the icemw packages) to your remastered CD, remove other packages (eg xubuntu*), and update the packages file (an index of packages on the CD)

To make the installer use the new metapackage, there are some minor changes to config files.

From the looks of it, that's all.

Any other customization can be done by  
- customized config files in the icebuntu metapackage, or
- adding customozed config files to the relevant packages.

The first option might require the relevant packages to be installed in advance, so that their config can be overwritten - if not, you'll be installing 2 packages with different versions of the same config file. You might be able to work around that with "Pre-Depends"

The second method is cleaner, but requires you maintain cusomized versions of the packages you've modified, i.e. you need a naming scheme that doesn't conflict with the original packages, and you have to add your modifications to new versions when the're released/

I'll have a go at it and see if my assumptions are correct

---

### Post by markp1989 on 2008-02-02
Putting the iso on rapid share because for some reason i couldnt get a torrent to work

Part 1: [http://rapidshare.com/files/88658430/xaa.html](http://rapidshare.com/files/88658430/xaa.html)
part 2: [http://rapidshare.com/files/88671547/xab.html](http://rapidshare.com/files/88671547/xab.html)
Part 3 [http://rapidshare.com/files/88682191/xac.html](http://rapidshare.com/files/88682191/xac.html)




when you have all 3 parts cd to the folder they are in and

```
cat xaa xab xac >> icebuntualpha.iso
```

```
md5sum '/path/to/icebuntualpha.iso' 
```
and the output should match 

```
92bac66f1a0f24dbc66bd77fae6ad0a2
```

to install , boot from the cd, then open the terminal and type ubiquity

---

### Post by sagarhshah on 2008-02-02
where are the other files?

theres a link for only the first file

Sagar

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> where are the other files?

theres a link for only the first file

Sagar

still uploading, i currently only have an upload speed of around 30kbs , i will post them as soon as they  finish

---

### Post by picpak on 2008-02-02
This is impressive, and I have to say I'm surprised that nobody thought of making an "IceBuntu" earlier.

Are there any metapackages ready? I'd like to try it out, but I don't want to download and join together iso's.

---

### Post by markp1989 on 2008-02-02
the other 2 rapid share are up now

---

### Post by hellion0 on 2008-02-02
I might be willing to test this one on my older laptop. (300MHz PII, 352MB RAM) I just hope it'll still pick up the wireless card like vanilla Ubuntu does.

As for what should go in, maybe start by focusing on compiling a "icebuntu-desktop" package with all the essentials needed for this Ubuntu flavour? I'm only guessing, I've never tried modifying a distro before.

---

### Post by markp1989 on 2008-02-02
> **hellion0 said:**
> I might be willing to test this one on my older laptop. (300MHz PII, 352MB RAM) I just hope it'll still pick up the wireless card like vanilla Ubuntu does.

i havnt tested it with wireless, only wired. and it detected both network cards i have tried

---

### Post by graabein on 2008-02-02
Anyone put up a blog/homepage on some free hosting site? Just to say what's on the ISO, default applications and provide links for download etc? Maybe some screenshots if the default theme looks good?

---

### Post by sagarhshah on 2008-02-02
> **markp1989 said:**
> the other 2 rapid share are up now

almost done...
will try it out in vmware first.
Then tomorrow will bring out the old tower from the basement!!

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> almost done...
will try it out in vmware first.
Then tomorrow will bring out the old tower from the basement!!

cool, thanks:D

---

### Post by bruce89 on 2008-02-02
What I'd like to see would be a Ubuntu netinst CD like Debian's one which is about 150 MB for one architecture. It would install the base and you could select which DE you want (if any).

---

### Post by markp1989 on 2008-02-02
> **bruce89 said:**
> What I'd like to see would be a Ubuntu netinst CD like Debian's one which is about 150 MB for one architecture. It would install the base and you could select which DE you want (if any).

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by sagarhshah on 2008-02-02
I tried it in vmware but it does not like it.
Guess I will have to wait till tomorrow.

Anyways in the meantime I have created a torrent here :

[http://thepiratebay.org/tor/4009431](http://thepiratebay.org/tor/4009431)

hopefully this one will work

---

### Post by markp1989 on 2008-02-02
> **sagarhshah said:**
> I tried it in vmware but it does not like it.
Guess I will have to wait till tomorrow.

Anyways in the meantime I have created a torrent here :

[http://thepiratebay.org/tor/4009431](http://thepiratebay.org/tor/4009431)

hopefully this one will work

thanks, i tried it in virtual box and it worked fine. and i tested it on m8 mys old pc

this torrent works, im seeding it now , can only upload about 25kbs

---

### Post by bruce89 on 2008-02-02
> **markp1989 said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Nice.

---

### Post by zmjjmz on 2008-02-02
Downloading it now...

---

### Post by sagarhshah on 2008-02-02
good to know that the torrent works :)
will leave it to seed for everyone!!

night

Sagar

---

### Post by Frem on 2008-02-02
I note that noone had mentioned [UbuntuLite]("http://ubuntulite.tuxfamily.org/") yet. They're talking about doing all sorts of interesting things, like TinyX. I believe they used to be using IceWM as the default, it might be Openbox now.

I used to have a few pretty flipping sweet IceWM configs. My original website died, but I might still have some links to good themes. Why is it that 90% of IceWM themes look like the author was blind?

Edit: Looked around, the only themes I used to use that still have a website up are [here]("http://www.varlock.com/").

Editedit: I also note that noone has mentioned GTK themes. These can make a large difference in performance on old machines. Murrine themes can be pretty zippy, as is ThinIce, and BlueCurve. Bluecurve has the added advantage of being available for almost every window manager, GTK1, GTK2, and QT.

---

### Post by sagarhshah on 2008-02-02
> **Frem said:**
> I note that noone had mentioned [UbuntuLite]("http://ubuntulite.tuxfamily.org/") yet. They're talking about doing all sorts of interesting things, like TinyX. I believe they used to be using IceWM as the default, it might be Openbox now.


yup they use openbox

> **Frem said:**
> 
I used to have a few pretty flipping sweet IceWM configs. My original website died, but I might still have some links to good themes. Why is it that 90% of IceWM themes look like the author was blind?

It would always be nice to get some decent themes in there.
haven't seen many decent themes out there yet.

---

### Post by RAV TUX on 2008-02-02
> **K.Mandla said:**
> Pardon me, but the specs page for LinuxICE says Matchbox is the window manager. Am I mistaken in that?

Wow,...you may be right, I must have missed that one. 

I'll have to correct the Distropedia page.

Thanks for the heads up.

> **Rui Pais said:**
> Hi,
only now i could give a word here (only this morning i read RAV TUX mail, but i have to go out...)

aysiu, if you need any specific help, just say.

usually (for my limited knowledge) livecd, go in 2 different categories.
Those who creates a live system on a squashfs file and those who seems to install from scripts from a much more minimal livecd (on an initird basic system i suppose), and it's much more difficult to deal.

Typical of the first are Ubuntu and X/K/Edu/Ge... variations.
Fluxbuntu it's an example of the second.

I have some experience with creating squashfs, but almost none in the other...

Another possible way, i think, it's just remake the fluxbuntu, replacing at pressed file the installation of fluxbuntu-desktop by icewm or some more elaborated meta-package that would install icewm+extras+config.

Thanks for the input Rui and taking the time to help  aysiu.

> **aysiu said:**
> Thanks for coming in to this thread, Rui Pais. If I do have specific help, I'll definitely ask for it.

Unfortunately, I have *no* experiencing remastering CDs at all. I don't even know what *squashfs* is!
[http://en.wikipedia.org/wiki/SquashFS](http://en.wikipedia.org/wiki/SquashFS)

---

### Post by RAV TUX on 2008-02-03
> **K.Mandla said:**
> Pardon me, but the specs page for LinuxICE says Matchbox is the window manager. Am I mistaken in that?

> **RAV TUX said:**
> Wow,...you may be right, I must have missed that one. 

I'll have to correct the Distropedia page.

Thanks for the heads up.
  

Actually going back to the original Distropedia article about the original Linux ICE it was based on ICE WM:

>  Light Window Manager:
  
 -ICEwm (seems appropriate for Linux ICE [IMG]http://www.nextabyte.com/nanonymous/forum/images/smiles/icon_wink.gif[/IMG] )qouted from the Linux ICE website on 06/26/2007

They may have changed the WM since then but it would be surprising.

---

### Post by RAV TUX on 2008-02-03
> **RAV TUX said:**
> Actually going back to the original Distropedia article about the original Linux ICE it was based on ICE WM:

qouted from the Linux ICE website on 06/26/2007

They may have changed the WM since then but it would be surprising.

It appears they have changed the WM from it's original ICEwm to Matchbox so k.mandla you are correct...

I will update the Distropedia page.
>  Kernel:
-2.6.20
-Suspend2 built in
-touchscreen support
-support for common usb->serial devices

Packages:
-GPS support
-NavIt GPS application
-Carman ODB-II statistics monitoring
-Samba
-SSH

Light Window Manager:
-MatchBox

xorg:
-evtouch driver built in with calibrator

front-end:
-nGhost Media Center Beta 0.95

codecs (possibly included proprietary codecs):
-dvd support[http://linuxice.com/features.php](http://linuxice.com/features.php)

Makes me wonder why this Distro which has been around for  a while changed from ICEwm to Matchbox...

perhaps they ran into trouble and perhaps ICEwm is not a good choice, I don't know? but it is worth looking into...maybe [RatPoison]("http://www.nongnu.org/ratpoison/")  would be worth looking into or...[Golem.]("http://golem.sourceforge.net/")

(makes me wonder what you would call a ubuntu distro based on the [RatPoison]("http://www.nongnu.org/ratpoison/") WM or the [Golem]("http://golem.sourceforge.net/") WM?)

---

### Post by LaRoza on 2008-02-03
> **RAV TUX said:**
> 
(makes me wonder what you would call a ubuntu distro based on the [RatPoison]("http://www.nongnu.org/ratpoison/") WM?)

Ratbuntu

(No, that doesn't work...)

---

### Post by RAV TUX on 2008-02-03
> **LaRoza said:**
> Ratbuntu

(No, that doesn't work...)No...but [CrackBuntu]("http://ubuntuforums.org/showpost.php?p=4259279&postcount=19") works.

---

### Post by hellion0 on 2008-02-03
Lol. That's almost scary.

As for one built around Golem, all I can think of is Zombuntu (going off of "zombi" or "zombie", synonyms for "golem") or Robuntu (another synonym for "golem", in this case "robot".) "Golbuntu" makes me think less of a window manager and more on football or hockey.

---

### Post by nikoPSK on 2008-02-03
> **RAV TUX said:**
> No...but [CrackBuntu]("http://ubuntuforums.org/showpost.php?p=4259279&postcount=19") works.

sounds fun :shock:

---

### Post by Lostincyberspace on 2008-02-03
could some one just upload it at upload hut they allow up to 1 gig I think for free I use it all the time to send iso's to people.

---

### Post by lespaul_rentals on 2008-02-04
Great idea, I will help beta-test and seed/host whatever I can.

If you can't figure out how to get torrents working, you could make a 3-part RAR archive and upload the pieces to Mediafire.

---

### Post by quinnten83 on 2008-02-04
> **markp1989 said:**
> i have had a go at creating a CD, it runs from the CD fine, but i currently have no way of testing the installation, does any one have a test system they can use, or somewhere for me to upload a 263mb iso?

currently all that is installed is:
icewm
gdm
dillo
xfe
synaptic

i have not installed other programs yet as i want to keep the size of the iso down.

you might try with a virtual machine.
try virtualbox in the repos.

---

### Post by hellion0 on 2008-02-04
Well, I downloaded the iso, tried burning it to a CD, and it doesn't boot from the CD. I know the machine can boot from a burned disc, so is anyone else having issues?

Edit: Figured out the CD drive's acting up on that machine.

---

### Post by nikoPSK on 2008-02-04
> **quinnten83 said:**
> you might try with a virtual machine.
try virtualbox in the repos.

although I do not want to seem rude, there is VMware as well. :)

---

### Post by markp1989 on 2008-02-04
> **quinnten83 said:**
> you might try with a virtual machine.
try virtualbox in the repos.

i have tested it on virtualbox, works


tested it on friends old pc (512mb 500mhz) works, but install is a bit slow, after that its fine 

tested on my sisters old computer (1ghz 256mb ram) runs well from cd and hard drive

---

### Post by Odd-rationale on 2008-02-04
Subscribed!

I know this question was asked in the making of fluxbuntu, but how is icebuntu going to be different from Ubuntu CLI + iceWM?

Another question is icebuntu going to feature rox-filer as well? (I like rox btw.)

In any case, I would love to help in any way I can.

P.S. Could you update the first post to provide links to the download? That way people don't have to go through the entire tread. Thanks!

---

### Post by sagarhshah on 2008-02-04
Hi,
tried it out on a 1 Ghz with 256 ram pc and it seems to work pretty well.
I'll be trying it out with a 128 mb ram to see how well it works.

Oh yeah btw theres some project on freshmeat thats called icebuntu
[http://freshmeat.net/projects/icebuntu/](http://freshmeat.net/projects/icebuntu/)

so another name might have to be chosen.

Download Links(all 3 parts need to be downloaded and joined using cat or a similar tool)
Part 1: [http://rapidshare.com/files/88658430/xaa.html](http://rapidshare.com/files/88658430/xaa.html)
part 2: [http://rapidshare.com/files/88671547/xab.html](http://rapidshare.com/files/88671547/xab.html)
Part 3 [http://rapidshare.com/files/88682191/xac.html](http://rapidshare.com/files/88682191/xac.html)

or download the whole thing in a torrent
[http://thepiratebay.org/tor/4009431](http://thepiratebay.org/tor/4009431)

md5 sum
`92bac66f1a0f24dbc66bd77fae6ad0a2`

if people are serious about doing this it might be worth having a mini-site hosted on [http://www.tuxfamily.org](http://www.tuxfamily.org)
I would do it but I'm in my final year of uni and need to concentrate on passing my finals but would love to help in any way I can.

Sagar

---

### Post by zmjjmz on 2008-02-04
How about Icedbuntu?
I have yet to try it though...

---

### Post by sagarhshah on 2008-02-04
> **sagarhshah said:**
> Hi,

Oh yeah btw theres some project on freshmeat thats called icebuntu
[http://freshmeat.net/projects/icebuntu/](http://freshmeat.net/projects/icebuntu/)

so another name might have to be chosen.



read up on the icedbuntu project on freshmeat.
Its a theme for IceWM based on the gnome dapper drake look!

---

### Post by zmjjmz on 2008-02-04
I guess we should use it then...

---

### Post by johnraff on 2008-02-05
lxde 
[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)
is a collection of lightweight apps based around IceWM.
I've used pcmanfm and gpicview  and they're nice.
Some of the other stuff might be useful too.

---

### Post by sagarhshah on 2008-02-05
> **johnraff said:**
> lxde 
[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)
is a collection of lightweight apps based around IceWM.
I've used pcmanfm and gpicview  and they're nice.
Some of the other stuff might be useful too.

had a brief look at it. It seems something worth looking at in detail.

I have updated the wiki with a download link for the torrent [https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu)

---

### Post by K.Mandla on 2008-02-07
Can anyone post the complete ISO somewhere? I'm behind a proprietary router, so I can't use torrent files. And Rapidshare wants me to wait three hours before I can get the other two parts.

---

### Post by hellion0 on 2008-02-07
> **K.Mandla said:**
> Can anyone post the complete ISO somewhere? I'm behind a proprietary router, so I can't use torrent files. And Rapidshare wants me to wait three hours before I can get the other two parts.Give me a few minutes and I can have a HTTP link going.

---

### Post by sagarhshah on 2008-02-08
bump

---

### Post by markp1989 on 2008-02-10
i have just made a new cd, with some changes:

iceBuntu theme installed by default, need to contact the developer of this theme,  to ask permission, but the email address on the site doesn't work.

network manager on the panel, with support for connecting to wireless networks

auto mount usb drives, camera cards etc automaticaly in /media

conky starts every boot to display important hardware information, such as used ram, etc

Pidgin installed for msn aim etc

support for restricted drivers 

icewm configured, different theme, panel neatened and all of the menus are neatened up.

---

### Post by zmjjmz on 2008-02-10
Sounds great, can't wait for a torrent.

---

### Post by markp1989 on 2008-02-10
il start a torrent soon, im trying to think of any changes that may be needed

---

### Post by zmjjmz on 2008-02-10
Actually, can you put in a light browser.
Not Dillo, but maybe Kazehakase?

---

### Post by nikoPSK on 2008-02-10
> **zmjjmz said:**
> Actually, can you put in a light browser.
Not Dillo, but maybe Kazehakase?

epiphany?

---

### Post by zmjjmz on 2008-02-10
Hv3?

/off topic
I got rid of Firefox and installed Epiphany once, and what did Synaptic do?
Reinstall firefox...

---

### Post by nikoPSK on 2008-02-10
> **zmjjmz said:**
> Hv3?

/off topic
I got rid of Firefox and installed Epiphany once, and what did Synaptic do?
Reinstall firefox...

lol, dunno why

---

### Post by markp1989 on 2008-02-11
> **zmjjmz said:**
> Actually, can you put in a light browser.
Not Dillo, but maybe Kazehakase?

i have never used  Kazehakase, does any one have any opinions they could give me about  Kazehakase or other light browsers

---

### Post by seshomaru samma on 2008-02-11
As a main browser for a light distro - I would choose Opera , though I understand that because it is not free as in freedom it will cannot be the default browser.
Kazehakase is a good light browser, I am currently running Damn Small Linux -N with SeaMonkey as the main browser and I think I would prefer Kazehakase- its main panel seems to have more options.

---

### Post by markp1989 on 2008-02-11
im thinking of adding a media player, any sugestions on a light weight player, that can play many file types?

---

### Post by p_quarles on 2008-02-11
> **markp1989 said:**
> im thinking of adding a media player, any sugestions on a light weight player, that can play many file types?
Audacious? Not the lightest, but the lightest that's also easy for the inexperienced user. Similar to Winamp.

---

### Post by meborc on 2008-02-11
> **zmjjmz said:**
> Hv3?

/off topic
I got rid of Firefox and installed Epiphany once, and what did Synaptic do?
Reinstall firefox...

well... epiphany is still dependent on firefox :) so it is not a wise choice... i also recommend opera as it is the fastest of the mentioned browsers on my crappy lappy

for music player - cmus - play your music from a terminal window... who actually looks at the music player when they are listening to the music anyway? 

cmus is what i use... simple and easy

---

### Post by zmjjmz on 2008-02-11
Why not XMMS?
I'ved used it in DSL, and I can say that it's rather light...

---

### Post by djbsteart1 on 2008-02-11
dream linux has xmms so it will be fine for formats, and i recall it being light aswell.

---

### Post by markp1989 on 2008-02-11
i have just made a new cd, with some changes:

iceBuntu theme installed by default, need to contact the developer of this theme, to ask permission, but the email address on the site doesn't work.

network manager on the panel, with support for connecting to wireless networks

auto mount external automaticaly in /media

conky starts every boot to display important hardware information, such as used ram, etc

Pidgin installed for msn aim etc

support for restricted drivers

icewm configured, different theme, panel neatened and all of the menus are neatened up.

dillo replaced with kazehakase 

audacious installed for music play back

have not added any office processing software yet. 

im posting this from my live cd now, runs extreamly well. i will upload the iso some time tomorrow

---

### Post by zmjjmz on 2008-02-11
As for office stuff, OO.o is out.
Abiword for Word Processing
Gnumeric for Spreadsheets would be good...
Anyone have a liight standalone presentation software thingie they'd recommend?

---

### Post by markp1989 on 2008-02-12
installed on to a 1gb CF card, and it runs well, just after booting around 50-60 mb of ram used up (havnt set a swap partition on the CF for obvious reasons).

posting from it now, have spent most of the morning listening to music in audacious, browsing the internet with Kazehakase, and chatting to people usign Pidgen, and have had no problems atal, runs stable, and fast.

---

### Post by Dr Small on 2008-02-12
Sweet :)
What default theme does it have? ... for IceWM.

---

### Post by markp1989 on 2008-02-12
> **Dr Small said:**
> Sweet :)
What default theme does it have? ... for IceWM.

[http://freshmeat.net/projects/icebuntu/](http://freshmeat.net/projects/icebuntu/) i tried contacting the developer , but the email address on the site doesnt work

---

### Post by aimran on 2008-02-12
If you used ThinBlack like Aysiu suggested then I might be interested ;)!

[http://ubuntuforums.org/showthread.php?t=321994](http://ubuntuforums.org/showthread.php?t=321994)


Also, Wbar for dock? :P

---

### Post by markp1989 on 2008-02-12
> **aimran said:**
> If you used ThinBlack like Aysiu suggested then I might be interested ;)!

[http://ubuntuforums.org/showthread.php?t=321994](http://ubuntuforums.org/showthread.php?t=321994)


Also, Wbar for dock? :P

i chose the icebuntu theme, because it made it "feel" like ubuntu still.

i have attached a screen print of how it looks on first boot

---

### Post by daulex on 2008-02-12
> **markp1989 said:**
> il start a torrent soon, im trying to think of any changes that may be needed

go to the ubuntu suggestions forum and just pick the "easy ones to do" :D:lolflag:

---

### Post by markp1989 on 2008-02-12
any one know any light weight office software?

---

### Post by zmjjmz on 2008-02-12
Abiword Word Processor; Gnumeric Spreadsheet.
As for presentation software...

---

### Post by p_quarles on 2008-02-12
[Siag Office](http://siag.nu/)

(joking -- it is lightweight, but pretty ancient)

---

### Post by daulex on 2008-02-12
> **markp1989 said:**
> i chose the icebuntu theme, because it made it "feel" like ubuntu still.

i have attached a screen print of how it looks on first boot

*slap* preinstall firefox dammit

looks great though, cant wait to give it a try :)

---

### Post by zmjjmz on 2008-02-12
Here's something for Presentation Stuffs.

[http://member.wide.ad.jp/wg/mgp/](http://member.wide.ad.jp/wg/mgp/)
Ok.
So it hasn't been updated in a year...

---

### Post by markp1989 on 2008-02-12
> **daulex said:**
> *slap* preinstall firefox dammit

looks great though, cant wait to give it a try :)

firefox is a memory hog, so i am trying to avoid it. synaptic is installed  by default so it is easy to install if you want

---

### Post by markp1989 on 2008-02-12
just installed it on the "media pc" in my sig, without a swap partition, and it runs well, install takes up 745mb of the hard disk.

i had trouble creating a torrent last time, does any one know where i can host a 275mb is for free? preferably without having to break it up in to separate parts

---

### Post by Dr Small on 2008-02-12
> **markp1989 said:**
> just installed it on the "media pc" in my sig, without a swap partition, and it runs well . i had trouble creating a torrent last time, does any one know where i can host a 275mb is for free? preferably without having to break it up in to separate parts
I would suggest smoothing out the wrinkles of the torrent problem, because I can't download 275MBs in one clip.

---

### Post by zmjjmz on 2008-02-12
[http://www.filefactory.com/](http://www.filefactory.com/)
"Upload up to 25 files at once. 300MB per file."

---

### Post by markp1989 on 2008-02-12
> **zmjjmz said:**
> [http://www.filefactory.com/](http://www.filefactory.com/)
"Upload up to 25 files at once. 300MB per file."

thankyou, i will upload the file at about 11:30 -12, because if i do it any earlier my sisters will complain that the internet is being slow

---

### Post by zmjjmz on 2008-02-12
Found another place that will take up to 1GB
[http://uploadhosted.filefront.com/](http://uploadhosted.filefront.com/)

---

### Post by markp1989 on 2008-02-12
> **Dr Small said:**
> I would suggest smoothing out the wrinkles of the torrent problem, because I can't download 275MBs in one clip.

[http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/) have tried making a torrent, but im not sure how well it will work.

if any one trys it tell me if it works or not.

Please seed it for a bit after downloading

---

### Post by p_quarles on 2008-02-12
Downloading, albeit slowly with just 1 peer (presumably markp1989).

And yes, I'll continue to seed this to at least a 1.5 ratio.

---

### Post by markp1989 on 2008-02-12
> **p_quarles said:**
> Downloading, albeit slowly with just 1 peer (presumably markp1989).

And yes, I'll continue to seed this to at least a 1.5 ratio.

thankyou. yes, i am currently the only seed, and my connections is not all that fast.

---

### Post by aimran on 2008-02-12
I'll seed for a few days... at least till the next version comes up :)

Oh wait it gives me an invalid URL for the tracker

---

### Post by p_quarles on 2008-02-12
> **markp1989 said:**
> thankyou. yes, i am currently the only seed, and my connections is not all that fast.
It's a bit faster than mine, actually. It was 40 k/s for a bit, and my upload speed maxes out at 36 or so. I can't seed at that speed if I want to do anything else, of course.

---

### Post by K.Mandla on 2008-02-12
> **p_quarles said:**
> [Siag Office](http://siag.nu/)

(joking -- it is lightweight, but pretty ancient)
I've used that in Arch before -- it's actually not as dysfunctional as it might appear. It's very lightweight too. I've tried compiling it in Ubuntu but I ran into problems. Maybe I'll try it again. 
> **markp1989 said:**
> i chose the icebuntu theme, because it made it "feel" like ubuntu still.

i have attached a screen print of how it looks on first boot
Very sharp!
> **zmjjmz said:**
> Found another place that will take up to 1GB
[http://uploadhosted.filefront.com/](http://uploadhosted.filefront.com/)
I've used them before and they're okay, I got a lot of ads and stuff on the download pages though. Very fast speeds from my experience though.

---

### Post by p_quarles on 2008-02-12
> **K.Mandla said:**
> I've used that in Arch before -- it's actually not as dysfunctional as it might appear. It's very lightweight too. I've tried compiling it in Ubuntu but I ran into problems. Maybe I'll try it again.
I might give that a try too. I understand that the word processor (called "Pathetic Writer") is actually decent. But, I don't think there's a spreadsheet tool for the suite at all, and the most recent release was November 2006. 

Oh, what the heck, I'm going to see if I can compile it. I'll let you know how it works.

---

### Post by K.Mandla on 2008-02-12
> **p_quarles said:**
> I might give that a try too. I understand that the word processor (called "Pathetic Writer") is actually decent. But, I don't think there's a spreadsheet tool for the suite at all, and the most recent release was November 2006. 

Oh, what the heck, I'm going to see if I can compile it. I'll let you know how it works.
Sounds good. If you want to see the problems I ran into and the possible solutions, I left a note to myself about it [here]("http://kmandla.wordpress.com/2007/09/19/compiling-siag-is-driving-me-nuts/"). I haven't had a chance to try it again since then, but I think that last comment by Christian might be the winner (I believe the developer's name is Christian, isn't it? coincidence? Hmm :-k ).

---

### Post by p_quarles on 2008-02-12
> **K.Mandla said:**
> Sounds good. If you want to see the problems I ran into and the possible solutions, I left a note to myself about it [here]("http://kmandla.wordpress.com/2007/09/19/compiling-siag-is-driving-me-nuts/"). I haven't had a chance to try it again since then, but I think that last comment by Christian might be the winner (I believe the developer's name is Christian, isn't it? coincidence? Hmm :-k ).
For me, it's hanging at trying to find the Xpm libs. They're installed, but it's either the wrong version or it's in the wrong place. I'm continuing to investigate.

---

### Post by p_quarles on 2008-02-12
Very odd -- I've downloaded 91% of the torrent, and still haven't sent a single byte up. Am I the only one downloading?

---

### Post by markp1989 on 2008-02-12
> **p_quarles said:**
> Very odd -- I've downloaded 91% of the torrent, and still haven't sent a single byte up. Am I the only one downloading?

now you download has finished, its not uploading any, so i gues you were the only person downloading , i will still leave the torrent up. 

post back on here how you get on with it.

---

### Post by Albi on 2008-02-12
If people are really serious about making such a distribution, then PM me and I'll gladly make a suitable theme.

Just tell me if you want it to stick true to the Ubuntu brown or what color pallete.  I don't think my Thinblack theme would go that well as a default.

Edit: Should have read through the entire thread rather than the last two pages.  I'll try to make a new ubuntu-like theme based from several Hardy mockups and if you want it you can use it for your ISO.  Should be ready in a few days seeing as school isn't giving me too hard a time these past few days and there's 50cm of snow outside.

---

### Post by p_quarles on 2008-02-12
> **markp1989 said:**
> now you download has finished, its not uploading any, so i gues you were the only person downloading , i will still leave the torrent up. 

post back on here how you get on with it.
Well, it looks good and is definitely lightweight. I installed it on a VM with 256 MB of RAM. The live CD used about 100 MB, and the installed version ate up all of 50 MB. 

The only thing I saw that was off was in the menu: the "Programs" entry basically recapitulates all the other menu items.

---

### Post by seshomaru samma on 2008-02-13
please keep seeding - i'm downloading

---

### Post by p_quarles on 2008-02-13
> **seshomaru samma said:**
> please keep seeding - i'm downloading
I'm not planning on stopping the seed any time soon, so no worries. My upload speed isn't that great, though, as you can probably see.

---

### Post by seshomaru samma on 2008-02-13
got it...
will test it when i have time

---

### Post by markp1989 on 2008-02-13
> **seshomaru samma said:**
> got it...
will test it when i have time

cool, post on here what you think of it

---

### Post by urukrama on 2008-02-13
> **markp1989 said:**
> i chose the icebuntu theme, because it made it "feel" like ubuntu still.

i have attached a screen print of how it looks on first boot

Why don't you use the human Gtk theme with that? It shouldn't slow the system down, but gives it a much nicer look, especially since you are using a human-like icewm theme.

---

### Post by ezphilosophy on 2008-02-13
I'm trying to download the torrent file hosted on filefront and the tracker is seemingly the pirate bay.  Is that the right one?  ktorrent says there are a couple of seeders but I have yet to download anything.

EDIT: It started after 12 min.  Getting 1.1 Kb/s!

EDIT #2: Yeah, that's what I meant.  I must have been looking at that IceWM Thin Ice black theme hosted on imageshack when I was typing

---

### Post by markp1989 on 2008-02-13
> **ezphilosophy said:**
> I'm trying to download the torrent file hosted on imageshack and the tracker is seemingly the pirate bay.  Is that the right one?  ktorrent says there are a couple of seeders but I have yet to download anything.

EDIT: It started after 12 min.  Getting 1.1 Kb/s!

[http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/)  torrent is hosted there.

---

### Post by zmjjmz on 2008-02-13
I tried out the alpha1 on the plane in Vbox- very nice.
I'm going to download the alpha2 now.

---

### Post by markp1989 on 2008-02-13
could someone update the wiki ([https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu)) for me please? 

Changes 
1) IceBuntu theme installed by default 
2) Network manager on the panel, with support for connecting to wireless networks
3) Auto mount external automaticaly in /media
4) Conky starts every boot to display important hardware information, such as used ram, etc
5) Pidgin installed for msn aim irc etc [http://www.pidgin.im/](http://www.pidgin.im/)
6) Support for restricted drivers
7) Icewm configured, different theme, panel neatened and all of the menus are neatened up.
8) Dillo replaced with kazehakase
9) Audacious installed for music play back

New torrent [http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/)

---

### Post by zmjjmz on 2008-02-13
Oh, I'm going to create a forum...
like, now.
icebuntu.6.forumer.com

---

### Post by markp1989 on 2008-02-13
> **zmjjmz said:**
> Oh, I'm going to create a forum...
like, now.
icebuntu.6.forumer.com

excellent, i just signed up

---

### Post by zmjjmz on 2008-02-13
I'm kinda working on it being usable first...

---

### Post by markp1989 on 2008-02-13
> **zmjjmz said:**
> I'm kinda working on it being usable first...

lol, ok, im just gona leave it for now, tell me when it is ready :D

---

### Post by K.Mandla on 2008-02-13
If you ask ubuntu-geek, I'm sure he would open a forum for the project here. 

[http://ubuntuforums.org/forumdisplay.php?f=249](http://ubuntuforums.org/forumdisplay.php?f=249)

It would save you the trouble of managing it yourself. Is that a good idea at all?

---

### Post by zmjjmz on 2008-02-13
I'm already quite into it, (have most of the things set up) and I need something to do now and then...

---

### Post by K.Mandla on 2008-02-13
> **markp1989 said:**
> [http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/)  torrent is hosted there.
Was an HTTP or FTP link ever posted? I weep for the loss of torrent traffic on my connection. :(

---

### Post by markp1989 on 2008-02-13
> **K.Mandla said:**
> Was an HTTP or FTP link ever posted? I weep for the loss of torrent traffic on my connection. :(

just started uploading the ISO to [http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/)
will take a few hours

---

### Post by markp1989 on 2008-02-13
> **K.Mandla said:**
> Was an HTTP or FTP link ever posted? I weep for the loss of torrent traffic on my connection. :(

just started uploading the ISO to [http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/)
will take a few hours

---

### Post by zmjjmz on 2008-02-13
Ok, the forums are ready for postage.
Go crazy.
(not too crazy)
(follow the guidelines/rules)

---

### Post by K.Mandla on 2008-02-13
> **markp1989 said:**
> just started uploading the ISO to [http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/)
will take a few hours
Right on. I'll watch for it. Thanks. ;)

---

### Post by zmjjmz on 2008-02-13
I just finished the torrent, so I'm going to restart (kernel headers update or something) and put the new one in VBox.

---

### Post by markp1989 on 2008-02-13
[http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/) ths iso is also up.

---

### Post by zmjjmz on 2008-02-13
Actually, shouldn't we start posting these in the forums?

icebuntu.6.forumer.com

---

### Post by markp1989 on 2008-02-13
> **zmjjmz said:**
> Actually, shouldn't we start posting these in the forums?

icebuntu.6.forumer.com

yes we should, but im not sure what section to put the links and stuff like that in

---

### Post by zmjjmz on 2008-02-13
Oh...
I'll be on that soon.
Fix'd

---

### Post by K.Mandla on 2008-02-14
> **markp1989 said:**
> [http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/) ths iso is also up.
Got it. Thanks. :)

---

### Post by K.Mandla on 2008-02-14
This looks pretty good. The only things I noticed at this point is that the GTK2 theme still seemed to be set to Raleigh. I installed the ubuntulooks theme and it looked fine after that.

---

### Post by markp1989 on 2008-02-14
just updated the wiki [https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu)

---

### Post by secdroid on 2008-02-14
Kudos for creating this variant 'buntu!

I'm an Ubuntu fan, but have been wishing for something lighter than Xubuntu.  Tried Fluxbuntu, but didn't really care for it.

Booted icebuntutest2.1 from CD on a Pentium III 500, 368 MB, 3Dfx video.  Only issue was screen resolution (more later).  Edited xorg.conf, restarted X, and installed to HD.  Cannot comment on speed of LiveCD because test box has very slow CD drive.  Everything worked as LiveCD.

Booted off hard disk and everything worked fine.  I love the tiny memory footprint -- 52 MB at idle.

I'm new to Ice, but find it very pleasing.  The default theme is quite satisfactory.  To my taste, it is minimal, but not too minimal.

As to applications for the distro, I'm of two minds.  On the one hand, we have Synaptic.  That, plus a list of suggested apps in a help file would be fine.  Some of us prefer to choose our own and would rather not have to uninstall defaults.

OTOH, most folks like pre-installed apps.  Zenwalk 5.0 and Antix (Mepis) are lightweight distros with (IMHO) excellent lightwight apps.  They might inspire the choice of apps for Icebuntu.

I'd suggest the addition of some IceWM control panel goodies, as well as printer and wireless admin apps.

I'm not sure that I understand the rationale for the program menu structure.  To me, it is confusing and seems to be redundant.  YMMV.

As for the screen resolution issue, it appears to be endemic to all 'buntus, but no other distros.  I have the test box on a Belkin KVM switch which causes 'buntu hardware config checkers to screw up.  Not an Icebuntu issue.

One question: Why create another 'buntu variant? You could create a package in the Ubuntu repository to add  Icewm (and apps) on top of Ubuntu Server.  Is there really that much interest in another LiveCD?  You could concentrate your efforts on the desktop and application issues and defer a lot of packaging and hosting issues until later.  Just a thought...

---

### Post by zmjjmz on 2008-02-14
Nice to hear you liked it!
As for the Server + IceWM repo, I don't think it's a good idea because it's supposed to be good for beginners.  
Also, this would require internet access, and some older computers (such as mine) aren't yet connected to the internet, so it just wouldn't be feasible.
Anyways, if you're now an IceBuntu user you should join the forums
icebuntu.6.forumer.com
Oh, and the Control panel thing is already being looked into.

---

### Post by secdroid on 2008-02-14
> **zmjjmz said:**
> 
Anyways, if you're now an IceBuntu user you should join the forums
icebuntu.6.forumer.com

Can't register.  Confirmation code rejected six times in a row.  Never had this problem on any other board.

---

### Post by zmjjmz on 2008-02-14
Really?
That's a problem...
Are you sure you're copying it right?
Maybe there's a character your e-mail viewer doesn't recognize?
(It's really a problem with forumer though...)

---

### Post by urukrama on 2008-02-14
> **zmjjmz said:**
> Oh, and the Control panel thing is already being looked into.

Would that be the [Icewm Control Panel]("http://www.phrozensmoke.com/projects/icewmcp/"), or something else?

This is looking promising. I might install this soon :-)

---

### Post by zmjjmz on 2008-02-14
Yes, it would be the IceWMCP.
A suggestion was made here: [http://icebuntu.6.forumer.com/viewtopic.php?t=10](http://icebuntu.6.forumer.com/viewtopic.php?t=10)

---

### Post by markp1989 on 2008-02-14
anyone who tries it i would be gratefull if you could post how you got on in the experience section of [http://icebuntu.6.forumer.com](http://icebuntu.6.forumer.com)

---

### Post by secdroid on 2008-02-14
> **zmjjmz said:**
> 
Are you sure you're copying it right?
Maybe there's a character your e-mail viewer doesn't recognize?
(It's really a problem with forumer though...)
Tried again 2x.  No go.  Using Firefox/1.5.0.13pre on Dapper.

No problems with other PHP-based forums.  No problem with other CAPTCHAs.

Doesn't appear to be an admin email contact.  I give up.

---

### Post by zmjjmz on 2008-02-14
Sorry to hear that.
Everybody else seems to be getting in fine though...

---

### Post by secdroid on 2008-02-14
> **secdroid said:**
> Tried again 2x.  No go.  Using Firefox/1.5.0.13pre on Dapper.

No problems with other PHP-based forums.  No problem with other CAPTCHAs.

Doesn't appear to be an admin email contact.  I give up.

Found workaround.  Disabled all extensions in Firefox and tried again.  Worked.

Don't know which extension was the fault, 'cause I nuked them all at once.  Suspect that it was noscript, even though flash and javascript were enabled.  

FWIW, the extensions were noscript, mediaplayerconnectivity, netcrafttoolbar, adblock, and videodownloader.

---

### Post by zmjjmz on 2008-02-14
Well, not sure about it what happened, but welcome to the forums!

---

### Post by seshomaru samma on 2008-02-15
My first impressions:
it booted smoothly on my desktop and looked very cool - I decide to give it a try on my very old laptop ([here]("http://page7.auctions.yahoo.co.jp/jp/auction/g55384846")- scroll down to see the pix, 128MB Celeron, 500Mhz)
I encountered some problems - first it took 25 minutes to boot, which is strange cause Knoppix which I assume is heavier took only 7 or so. Next I tried to install but the install application windows opened in the  wrong resolution and it was very difficult to reach the "forward" button . 
Since this version of Ubuntu caters mostly to low-specs machines , I think that some sort of CLI type install option is advisable. The installation application became unresponsive in the partitioner part - I tried to resize the Damn Small Linux partition to allow space for Linux. I should have done that through DSL...
Finally it didn't recognise my network card . I have a rather exotic external network card ([here ]("http://page16.auctions.yahoo.co.jp/jp/auction/u19210098")) which until now only Knoppix recognised. 
I will try installing it again so I can play with it more. 
All in all very impressive work there!

---

### Post by zmjjmz on 2008-02-15
I agree with you about the install thing, but a CLI option may be bad for novices...
Maybe a lightweight graphical one, or maybe a very guided CLI one...

---

### Post by stevejesus on 2008-02-15
Use Iceape instead of Firefox.  I use it on my PII Lappy.

---

### Post by uberlube on 2008-02-15
> **markp1989 said:**
> any one know any light weight office software?
LAMO!! I wish :)

---

### Post by markp1989 on 2008-02-15
> **zmjjmz said:**
> I agree with you about the install thing, but a CLI option may be bad for novices...
Maybe a lightweight graphical one, or maybe a very guided CLI one...

i agree that an alternative install disk would be better, but i have no idea how to do that, any one want to help out?

---

### Post by Dr Small on 2008-02-15
> **zmjjmz said:**
> I agree with you about the install thing, but a CLI option may be bad for novices...
Maybe a lightweight graphical one, or maybe a very guided CLI one...
Although CLI could potentially be bad for novices, I don't forsee many novices using Icebuntu, for the simple reason is IceWM is generally for geeks with low specs and are CLI junkies anyhow.

---

### Post by zmjjmz on 2008-02-15
A guided CLI one then?

---

### Post by markp1989 on 2008-02-15
> **Dr Small said:**
> Although CLI could potentially be bad for novices, I don't forsee many novices using Icebuntu, for the simple reason is IceWM is generally for geeks with low specs and are CLI junkies anyhow.


i was thinking of having it done similar to how Geexbox does, its a live cd, but at syslinux prompt if you type install then it launches the text based installer, and if you press enter then it boots the live cd, im not sure how i would go about doing this

---

### Post by zmjjmz on 2008-02-15
Just so long as we remember to have it say "type install and then hit enter to go to a text installer, or just hit enter to run the OS without touching your hard drive."

---

### Post by markp1989 on 2008-02-15
> **zmjjmz said:**
> Just so long as we remember to have it say "type install and then hit enter to go to a text installer, or just hit enter to run the OS without touching your hard drive."
i was planing to have it like this?
> Welcome to IceBuntu

For the default live system, enter "live" or press enter 
For safe graphics mode, enter "vesa". 
To run the text based installer type "install"
To verify the CD for errors, enter "check". 
To run memtest86+, enter "memtest"



just not sure what options i will have to pass  to the kernel, and how i will install the alternative installer

im sure google will hold the answer

---

### Post by zmjjmz on 2008-02-15
Bump.

---

### Post by markp1989 on 2008-02-16
bump

---

### Post by zmjjmz on 2008-02-16
Actually, I'm going to put IceBuntu in my sig...

---

### Post by Dr Small on 2008-02-16
> **markp1989 said:**
> i was planing to have it like this?




just not sure what options i will have to pass  to the kernel, and how i will install the alternative installer

im sure google will hold the answer
Sorry, I don't know hardly anything about the boot process, so I can't be of much help. :(

---

### Post by zmjjmz on 2008-02-17
Bump.

The Wiki page was improved, thanks to Dr Small.

---

### Post by markp1989 on 2008-02-17
> **zmjjmz said:**
> Bump.

The Wiki page was improved, thanks to Dr Small.

nice job Dr small, it looks good:D

---

### Post by Dr Small on 2008-02-17
No problem, guys. Glad I could help out there ;)

---

### Post by ayenack on 2008-02-18
This isn't just good for old PC it's also good for USB Pendrive installs. I've just installed it onto a 1GB USB Pendrive. Work very well. Was thinking about putting up a Howto but not sure if this is the right place or not. Might be better suited to the wiki or Icebuntu forums.

Thoughts?

---

### Post by zmjjmz on 2008-02-18
Post it in the Support section of the forums at [http://icebuntu.6.forumer.com](http://icebuntu.6.forumer.com)
A good idea for the title would be "HOWTO: IceBuntu on a Pen Drive"

---

### Post by ayenack on 2008-02-18
I'm not going to have that much time to post support if people can't get it to work or hose there systems. So unless you or someone else can help people who run into problems might not be such a good idea. I will help when I can but this will only be intermittently.

---

### Post by zmjjmz on 2008-02-18
Huh?
I meant to make a HOWTO and post it in the support section of the IceBuntu forums...

---

### Post by ayenack on 2008-02-18
OK. I'm doing that right now.

EDIT: It's now on the IceBuntu forums in the Support channel under the name HOWTO: IceBuntu on a Pen Drive.

---

### Post by markp1989 on 2008-02-20
bump

---

### Post by Dr Small on 2008-02-23
Bump :)

---

### Post by zmjjmz on 2008-02-23
Should someone PM the OP and tell him his IceBuntu is almost ready?

---

### Post by ayenack on 2008-02-24
> **zmjjmz said:**
> Should someone PM the OP and tell him his IceBuntu is almost ready?

I think so. Should be either you or markp1989 seeing as you've done all the work.

BTW do you think there should be a link to the IceBuntu .iso download on IceBuntu Forums?

---

### Post by Dr Small on 2008-02-24
> **ayenack said:**
> I think so. Should be either you or markp1989 seeing as you've done all the work.

BTW do you think there should be a link to the IceBuntu .iso download on IceBuntu Forums?
There is one on the Wiki Page:
[https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu)

---

### Post by ayenack on 2008-02-24
> **Dr Small said:**
> There is one on the Wiki Page:
[https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu)

Forgot about that. :oops:

---

### Post by zmjjmz on 2008-02-24
> **ayenack said:**
> I think so. Should be either you or markp1989 seeing as you've done all the work.

Nah, mark did all the work.
[SIZE="1"]I'm too lazy[/SIZE]

---

### Post by zmjjmz on 2008-02-29
bump.
2.2 is out.

---

### Post by seshomaru samma on 2008-03-01
downloading...
a torrent would be nice..

---

### Post by K.Mandla on 2008-03-01
Aha! I was wondering when this thread would pop back up again. Trying now. ...

---

### Post by tdrusk on 2008-03-01
> **aysiu said:**
> I know [Fluxbuntu](http://fluxbuntu.org/js.html) is already in production and is at Release Candidate instead of 1.0

Both Damn Small Linux (Fluxbox) and Puppy Linux (IceWM) are excellent choices for people with low specs, but if someone wants something Ubuntu-based (with the same software repositories, release cycle, and *sudo* implementation) for an older computer, the only choices right now are Xubuntu, Fluxbuntu, or manual installation and configuration of IceWM (or some other window manager) manually.

If the forums' user base is any indication, Fluxbox is very popular among Ubuntu users, but there should be a significant enough number of us IceWM users to be able to put together a low-spec-friendly Ubuntu for IceWM users--IceBuntu.

I'm thinking it'd be an Alternate CD, since 64 or 128 MB of RAM may not be enough to run a live session and Ubiquity at the same time. Here's the problem: I don't know how to do it, so I'm asking the community to help out.

I've taken a look at Reconstructor, and as far as I can tell, it doesn't let you truly modify the installation the Alternate CD sets up--only add and remove packages. I wouldn't want IceBuntu to just be IceWM installed. It would be great to have some sensible configuration choices, a good default theme ([ThinBlack](http://ubuntuforums.org/showthread.php?t=321994), for example), and launcher icons for popular applications.

If you're interested in creating a IceBuntu disk or even, if it's easier, an IceBuntu metapackage, please post in this thread and let me know what you're willing to contribute and what you think IceBuntu should be like.

My technical know-how is a little weak, so I can contribute trying to coordinate people's efforts and maybe publicizing IceBuntu a bit on my Psychocats website.

Others?

**Edit**: It looks as if other people are much better at figuring out this ISO-remastering thing than I am. If you have torrents or other ideas you want to post up, please post them on the Ubuntu Wiki, since this thread is now becoming quite long.
[https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu)

I would love it. Perfect for my Pentium 1 64 mb of ram laptop.

---

### Post by seshomaru samma on 2008-03-01
download froze at 83%
can't start again
it could be that this site blocks IPs from China
most of them do

> There was an error processing your request; it appears to be invalid or there was an error with your conection. Please wait while your request is retried...

If you need further help with a download, please contact FileFront support.

hopefully it will work later...

---

### Post by zmjjmz on 2008-03-01
Sorry about that.
I don't think we have the server power to host the downloads ourselves (or servers at all)

---

### Post by K.Mandla on 2008-03-02
This looks pretty good. I like the addition of the ThinBlack theme, although to be honest, if you're shipping with Raleigh and Human as the only options for the GTK2 theme, you might want to add a darkish one to complement ThinBlack. The other two are a little ... odd with it.

I'd say it's almost perfect as it is. Don't go adding ridiculous packages or productivity suites. Keep it small and light and let people add to it as they wish. It'll keep your workload from spiraling out of control too. ...

(One peeve is the weird nested Programs menu that comes from the menu package. I know it's not your fault, but if you have a predetermined list of software that will be available, you might want to sculpt the default menu to include only those programs. It's an idea, but definitely not required. :D )

---

### Post by zmjjmz on 2008-03-02
> **K.Mandla said:**
> you might want to add a darkish one to complement ThinBlack
I'm using SlicknesS right now, and it would go great with it.

---

### Post by zmjjmz on 2008-03-04
Another bump.
Mark and I have agreed that Ubiquity has to go.
Does anyone know of a good text based installer that is available (preferrably) through synaptic? Maybe the alternate-install CD one?

---

### Post by K.Mandla on 2008-03-05
I know the text installer is debian-installer, but I can't say much else about it.

[https://launchpad.net/ubuntu/+source/debian-installer](https://launchpad.net/ubuntu/+source/debian-installer)

:D

---

### Post by zmjjmz on 2008-03-05
Debian-installer in synaptic is 'just a bunch of documents'
Not an installer as far as I could tell...
EDIT: This looks right.
Funny.

---

### Post by K.Mandla on 2008-03-05
Is that helpful then? The only reason I know that is because a bug in the installation process for the alternate CD is filed against debian-installer (I think). So I might be way off track with that.

---

### Post by zmjjmz on 2008-03-05
Yeah, it is.
It's already on the IceBuntu forums now...

---

### Post by MattBD on 2008-03-05
I think IceBuntu is a great idea. I don't know if I'd be able to help much, but I'd certainly be willing to help test it.

I did actually have a bit of a tinker with IceWM over the weekend. I installed a command-line install of Ubuntu in VirtualBox, then added IceWM and several applications, and I thought I'd share my opinions as to which of those I think worked best.

File Manager - PCManFM - fast but the tabbed interface means it's powerful.
Browser - Kazehakase as it's faster than Firefox and does well in Fluxbuntu. Dillo was a bit too spartan for my taste.
IM client - AYTTM, just about the only multi-protocol client I could find that was smaller than Pidgin.
E-mail - Thunderbird, couldn't really find anything I liked that was smaller, but since many people use webmail anyway you might be able to get away without one at all.
Terminal - A no-brainer, XTerm.
Word processor - Has to be AbiWord, there's not really anything smaller.
Spreadsheet - Gnumeric

These are just suggestions which worked for me. If anyone else can suggest alternatives I'd be interested to hear them

---

### Post by zmjjmz on 2008-03-05
You can use the forums to post suggestions regarding applications.
[http://icebuntu.6.forumer.com](http://icebuntu.6.forumer.com)
As for file managers, we currently use Xfe.  PCmanFM is probably better, but we're only on our third preprerelease.
AYTTM looks good, maybe we can offer Pidgin as an 'Enhancement?' (lack of Gtalk support though is a real downer, especially since XMPP is an OSP)
The other applications are already being used (not so sure about Xterm, but we use Sylpheed for e-mail).

In unrelated news, I set up and registered an IRC channel!
#icebuntu at the Ubuntu Servers.

---

### Post by MattBD on 2008-03-06
Have been giving IceBuntu 2.2 a try in VirtualBox, and with hindsight Sylpheed is absolutely the right e-mail client - I'd not tried it myself and it does seem to be ideal for a lightweight distro.

---

### Post by zmjjmz on 2008-03-06
Why do you think it was chosen ;)

Anyways, the only problem with Sylpheed is that it doesn't support HTML, but...

---

### Post by ayenack on 2008-03-09
It'd be cool if IceBuntu was on the users OS list in user profiles. I'd put it up instead of Arch.

---

### Post by zmjjmz on 2008-03-09
I'd think it'd have to be more or less complete as Fluxbuntu first...
I mean, we don't even have a website for it.
And why isn't anyone on the IRC chan...

---

### Post by zmjjmz on 2008-03-10
Bump...
EDIT: Does anyone have any experience remastering an alternate install CD?

---

### Post by markp1989 on 2008-03-14
bump

---

### Post by Omnios on 2008-03-14
[http://ubuntuhomeserver.org/](http://ubuntuhomeserver.org/)> **aysiu said:**
> I know [Fluxbuntu]("http://fluxbuntu.org/js.html") is already in production and is at Release Candidate instead of 1.0
 
I'm thinking it'd be an Alternate CD, since 64 or 128 MB of RAM may not be enough to run a live session and Ubiquity at the same time. Here's the problem: I don't know how to do it, so I'm asking the community to help out.
 
My technical know-how is a little weak, so I can contribute trying to coordinate people's efforts and maybe publicizing IceBuntu a bit on my Psychocats website.
 
Others?
 
**Edit**: It looks as if other people are much better at figuring out this ISO-remastering thing than I am. If you have torrents or other ideas you want to post up, please post them on the Ubuntu Wiki, since this thread is now becoming quite long.
[https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu](https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu)
 
Hi aysiu. Some times you come up with some really neet stuff. I find this ice thing interesting as it may solve some problems pertaining to Ubuntu Home Servers wich in affect may help this project by attracting attention and hopefully developers. 
 
To start off a few months ago there was a post abut a new Ubuntu Home Server project. Here is a link to that thread.
 
[http://ubuntuforums.org/showthread.php?t=671746&highlight=Home+server](http://ubuntuforums.org/showthread.php?t=671746&highlight=Home+server)
 
Also there home page is here.
 
[http://ubuntuhomeserver.org/](http://ubuntuhomeserver.org/)
 
 There forum is here.
 
[http://ubuntuhomeserver.org/phpbb3/](http://ubuntuhomeserver.org/phpbb3/)
 
 K now the thing here is that it may be possible to co-develop a Ubuntu-ice release as well as have it worked into a graphical front end for the server version. This GUI issue is where a lot of people are butting heads where the hard core base users state a web interface is needed and others wanting a win-nt/2000 like interface. It may be possible to have both with the server base and possibly a script command to start X and ice when needed. This may also allow for a GUI based Ubuntu server that can rock the GUI server world. I think that this has a lot of potential and should be discused.

---

### Post by zmjjmz on 2008-03-14
If it's a light GUI you need for the UHS, I'd recommend JWM.  It has that same look, but it's much lighter... (It's included with DSL as the default WM)

---

### Post by markp1989 on 2008-03-16
Good news, I finished the Decorating, so I can be able to start working on Icebuntu 2.3! 

join  the IRC/post on the icebuntu forum, do discuss the next release ([http://icebuntu.6.forumer.com/](http://icebuntu.6.forumer.com/)) <---- that link will change soon

---

### Post by zmjjmz on 2008-03-16
Just to remind everyone, the IRC channel is #icebuntu on irc.freenode.net

---

### Post by Lord DarkPat on 2008-03-17
By looking at the screeny's I can safely say that this redefines elegance!!
Sadly I own a P4 and Centrino

---

### Post by zmjjmz on 2008-03-17
New forums!
[http://icebuntuforums.grubbn.com](http://icebuntuforums.grubbn.com)

---

### Post by Lostincyberspace on 2008-03-17
One problem there are no forums their so nothing can happen.

---

### Post by zmjjmz on 2008-03-17
...
Weird...
hold on...

Ok, I got it to work.

---

### Post by Lostincyberspace on 2008-03-17
Now there are two support forums? you might want to remove one.

---

### Post by zmjjmz on 2008-03-17
I could of sworn that wasn't there when I last checked, but who knows?
Anyways, the deformation is gone now.  Does anyone know how to get smiles in phpbb3?

---

### Post by zmjjmz on 2008-03-26
Bump.
The forums are now using MyBB, and I have some configurin' to do.
After the homework...

---

### Post by markp1989 on 2008-03-26
> **zmjjmz said:**
> Bump.
The forums are now using MyBB, and I have some configurin' to do.
After the homework...

cool, new forums looking good

---

### Post by zmjjmz on 2008-03-26
Would you mind populating releases?

---

### Post by notwen on 2008-04-02
You guys may want to look into this guy's script which sets up a very nice IceWM/XFCE gui in a minimal cli install.

[Thread here]("http://ubuntuforums.org/showthread.php?t=741631"). =]

---

### Post by zmjjmz on 2008-04-02
I'll talk to Mark about it, consider posting it as a suggestion on icebuntuforums.grubbn.com

---

### Post by markp1989 on 2008-04-05
Icebuntu 2.3 

Changes

installer (not text based, uses ubiquity-only)
clean up the menus, using menu maker
Install ndiswrapper, to help support more network adapters
SlicknesS GTK theme for use with Thinblack
vmware mousedriver
Tango icon theme default
installed xzgv - image viewer
install menu maker
replace GDM with slim

Md5sum Icebuntu2.3.iso
```
48835fcde81770e01dc1a4cc57a022e5
```


iso hosted here [http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/)

---

### Post by PissedApache on 2008-04-10
Sweet!

Gonna try it out on the old lappy i picked up;  Panasonic CF-27, Pentium II 300MHz, 128MB, 6.1Gb

\\:D/

---

### Post by zmjjmz on 2008-04-15
Bump

---

### Post by Yitram on 2008-04-24
> **markp1989 said:**
>  im posting this from my live cd now, runs extreamly well. i will upload the iso some time tomorrow

I seem to have missed something.  When I try to use the live cd part, it asks for a username and password, but everything i've thought of to try doesn't work.

EDIT: I'll just install it and hope I don't lose the disk.  It already has an Ubuntu partition on it, so as long as I just reformat that, It should work fine.

---

### Post by zmjjmz on 2008-04-24
Have you tried 'ubuntu' 'ubuntu' ?
I dunno, it logs in automatically for me.

---

### Post by Yitram on 2008-04-24
> **zmjjmz said:**
> Have you tried 'ubuntu' 'ubuntu' ?
I dunno, it logs in automatically for me.

Just tried it...and no good.  Doesn't make sense that it should make me log in.  Let me try it here on my desktop.

Ditto on my desktop, wants me to login

---

### Post by markp1989 on 2008-04-24
oh yeah i was sposed to write that on the wiki,

the username is "ubuntu"
and the password is blank ""

---

### Post by Yitram on 2008-04-24
> **markp1989 said:**
> oh yeah i was sposed to write that on the wiki,

the username is "ubuntu"
and the password is blank ""

LMAO.  I'm surprised that I'm the first to ask that, considering that 2.3 has been out for a couple of weeks now.  I guess most ppl who have been following this started at the beginning and haven't needed the LiveCD part.  I've actually been following it, but I've only just now gotten around to trying it on my laptop.  

My only complaint so far is that in the menus, when I mouse over something thats like a directory that has things under it, like 'Editors' or 'Internet' or the like, that it doesn't automatically expand, and I actually have to click it to get it to expand.  Maybe this is something that can be fixed via settings somewhere.

---

### Post by zmjjmz on 2008-04-24
That's an IceWM thing I believe.

---

### Post by Dr Small on 2008-04-24
> **Yitram said:**
> LMAO.  I'm surprised that I'm the first to ask that, considering that 2.3 has been out for a couple of weeks now.  I guess most ppl who have been following this started at the beginning and haven't needed the LiveCD part.  I've actually been following it, but I've only just now gotten around to trying it on my laptop.  

My only complaint so far is that in the menus, when I mouse over something thats like a directory that has things under it, like 'Editors' or 'Internet' or the like, that it doesn't automatically expand, and I actually have to click it to get it to expand.  Maybe this is something that can be fixed via settings somewhere.
That is a setting that can be edited in the ~/.icewm/preferences
It is called, ClickToFocus.
That should be set to 0.

Dr Small

---

### Post by MattBD on 2008-04-25
Has anyone tried IceBuntu on an Asus Eee PC?

I've got a 2GB Surf and I'm not too keen on the existing Xandros OS, so I was thinking about using IceBuntu instead. Any comments?

---

### Post by markp1989 on 2008-04-25
> **MattBD said:**
> Has anyone tried IceBuntu on an Asus Eee PC?

I've got a 2GB Surf and I'm not too keen on the existing Xandros OS, so I was thinking about using IceBuntu instead. Any comments?

i use it on my eee pc , and it works fine, using the ubuntu script pack [http://ubuntu-eee.tuxfamily.org/inde...itle=Main_Page](http://ubuntu-eee.tuxfamily.org/inde...itle=Main_Page)

i use the icebuntu 2.2 release on mine because the 2.3 release has problems with the network manager

sorry double post

---

### Post by markp1989 on 2008-04-25
> **MattBD said:**
> Has anyone tried IceBuntu on an Asus Eee PC?

I've got a 2GB Surf and I'm not too keen on the existing Xandros OS, so I was thinking about using IceBuntu instead. Any comments?

i use it on my eee pc , and it works fine, using the ubuntu script pack [http://ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page](http://ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page)

[http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_use_the_ubuntu-eee_script](http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_use_the_ubuntu-eee_script)

i use the icebuntu 2.2 release on mine because the 2.3 release has problems with the network manager

---

### Post by MattBD on 2008-04-25
Cool, in that case I'll have to give it a try sometime. The Xandros install is seriously lacking under the hood.

---

### Post by markp1989 on 2008-05-08
bump

---

### Post by tdrusk on 2008-05-10
I'm going to start working on a version of this. I am using Hardy as a base. Is there still an active development?

---

### Post by markp1989 on 2008-05-10
> **tdrusk said:**
> I'm going to start working on a version of this. I am using Hardy as a base. Is there still an active development?

im planing on making a new version that will be based on Gusty still, i havnt got any feed back from the last version, so im not sure what i will change.

you can make one using hardy if you want, any information you want from me about doing it then just pm me

---

### Post by tdrusk on 2008-05-10
> **markp1989 said:**
> im planing on making a new version that will be based on Gusty still, i havnt got any feed back from the last version, so im not sure what i will change.

you can make one using hardy if you want, any information you want from me about doing it then just pm me
Awesome. I think if we both work without knowing what the other is doing we can generate new ideas and make something good.

---

### Post by zmjjmz on 2008-05-10
> **tdrusk said:**
> Awesome. I think if we both work without knowing what the other is doing we can generate new ideas and make something good.

Wait what?
Do we really need two Icebuntus?

---

### Post by tdrusk on 2008-05-10
> **zmjjmz said:**
> Wait what?
Do we really need two Icebuntus?

no no. We both will finish our versions, then bounce ideas off each other. It can all combine as one later.

That way new ways of doing things are being done by both creators.

---

### Post by zmjjmz on 2008-05-10
Ah, a merger. Ok.

---

### Post by agim on 2008-05-10
Keep us all posted. I would be very interested as a tester.

---

### Post by tdrusk on 2008-05-11
> **agim said:**
> Keep us all posted. I would be very interested as a tester.

Okay. I am still working on it, obviously haha.

I rarely use icewm, but I think this will turn out pretty good. My goal is to give it the main functionality of Ubuntu, only with lighter programs. 

Does anyone have any good ideas for a network manager, or should I just use network-manager-gnome?

---

### Post by zmjjmz on 2008-05-11
nm-applet fails in SLiM, but we can't find much else...
In development is lxnm (nm for LXDE), that looks promising.

---

### Post by agim on 2008-05-11
I have used wicd. It worked well. I have heard other people use it in lighter systems and when network manager isn't doing its job.

edit:
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by songshu on 2008-05-11
do you guys have a project page?
can people team up?

i want in on the fun, i'm working on my own custom project but there should be plenty of overlap to be usefull.

---

### Post by songshu on 2008-05-11
still need help remastering the alternate?

i just did the mini.iso and its really simple.

```
Hacking the installer

first we need to get the mini.iso from here https://help.ubuntu.com/community/Installation/MinimalCD

no need to burn it to cd first, just mount it

mount -o loop /path/to/iso /some/mountpoint

after its mounted, copy the content to a folder

mkdir -p /opt/cd-image
rsync -av /some/mountpoint/ /opt/cd-image

since the content of is now copied to /opt/cd-image this would be the place to make the needed changes.

nano /opt/cd-image/isolinux.cfg

all i've added is the laoshu part

DISPLAY boot.txt



F1 f1.txt

F2 f2.txt

F3 f3.txt

F4 f4.txt

F5 f5.txt

F6 f6.txt

F7 f7.txt

F8 f8.txt

F9 f9.txt

F0 f10.txt



DEFAULT laoshu



LABEL laoshu

	kernel linux

	append vga=normal debian-installer/locale=en_US console-setup/layoutcode=us netcfg/get_hostname=unassigned-hostname preseed/url=http://192.168.1.12/laoshu-preseed.cfg initrd=initrd.gz --



LABEL install

	kernel linux

	append vga=normal initrd=initrd.gz -- 

LABEL linux

	kernel linux

	append vga=normal initrd=initrd.gz -- 

LABEL cli

	kernel linux

	append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=normal initrd=initrd.gz -- 



LABEL expert

	kernel linux

	append priority=low vga=normal initrd=initrd.gz -- 

LABEL cli-expert

	kernel linux

	append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low vga=normal initrd=initrd.gz -- 



LABEL rescue

	kernel linux

	append vga=normal initrd=initrd.gz rescue/enable=true -- 



PROMPT 1

TIMEOUT 0


after the changes are made we can make a fresh new .iso image

IMAGE=laoshu.iso

BUILD=/opt/cd-image

mkisofs -r -V "LaoShu Install CD" \
            -cache-inodes \
            -J -l -b isolinux.bin \
            -c boot.cat -no-emul-boot \
            -boot-load-size 4 -boot-info-table \
            -o $IMAGE $BUILD


```

---

### Post by tdrusk on 2008-05-11
I am having trouble getting the background image to load. It shows for a split second, then goes gray. I do not have nautilus install or Rox, so I can't use the rox trick.

If I go into another theme the background image changes to the one I want it to, but that's not the way it should work. It should load at startup.

What am I doing wrong?

EDIT: I figured it out.

The creator of the Thin Black theme set the background as something on his computer, thus making it look for that.

---

### Post by zmjjmz on 2008-05-11
Just gonna remind people that the forums are at [http://icebuntu.6.forumer.com](http://icebuntu.6.forumer.com)
or
[http://icebuntuforums.grubbn.com/forums/](http://icebuntuforums.grubbn.com/forums/)
and the IRC channel is #icebuntu on irc.freenode.net

---

### Post by MattBD on 2008-05-18
> **tdrusk said:**
> no no. We both will finish our versions, then bounce ideas off each other. It can all combine as one later.

That way new ways of doing things are being done by both creators.

Mind if I make my own as well? I'm interested in creating a version that's designed with things like the Eee PC in mind, and possibly includes out-of-the-box support for mobile broadband by including Vodafone's mobile broadband driver (and possibly UMTSmon, but I'd have to compile that myself) but is better suited for more advanced users.

---

### Post by angryfirelord on 2008-05-18
If GUI tools such as network-manager or wicd don't work, one could use th CLI tool ceni from Sidux. I head that anticapitalista (creator of antiX) was considering using it in his distro, which uses fluxbox.

---

### Post by MattBD on 2008-05-18
> **angryfirelord said:**
> If GUI tools such as network-manager or wicd don't work, one could use th CLI tool ceni from Sidux. I head that anticapitalista (creator of antiX) was considering using it in his distro, which uses fluxbox.

I found Knetworkmanager to work OK, but network-manager wasn't too hot.

---

### Post by zmjjmz on 2008-05-18
What was the resource usage of Knetworkmanager?
EDIT: This seems to only happen with SLiM btw.

---

### Post by MattBD on 2008-05-19
> **zmjjmz said:**
> What was the resource usage of Knetworkmanager?
EDIT: This seems to only happen with SLiM btw.

Not sure, I'll have to check it when I get the chance, but it did seem pretty low when I ran top in Kubuntu. I couldn't get network-manager to work at all in IceWM.

---

### Post by p_quarles on 2008-05-19
> **angryfirelord said:**
> If GUI tools such as network-manager or wicd don't work, one could use th CLI tool ceni from Sidux. I head that anticapitalista (creator of antiX) was considering using it in his distro, which uses fluxbox.
I second the suggestion of Ceni. It's a very easy-to-use application, and uses ncurses, so will bring only very light dependencies. Using knetworkmanager in a primarily Gtk+ environment could be a bit problematic in that regard.

---

### Post by davidsj888 on 2008-05-19
eBay Selling has become the home based business of choice for tens of thousands of people. To sell on eBay successfully, you need real wholesale suppliers of products to sell.Right now you also can be ebay selling without any worry about the supplier.If you sell the garment such as the sexy lingerie,you can click [china sexy lingerie wholesale](http://www.china-sexy-lingerie.com).They were supported by the [china sexy lingerie supplier](http://www.bestoplingerie.com).If you dont like the sexy lingerie,you can sell the Usb flash drives.Also i have one site from [china usb flash drives manufacturer](http://www.chinausbflashdrives.com/).If your wife or your friend like dance,so this place is good place.they can make the custom dance dress,you will see some style in the party.They have many nice and fashion dance dress,[latin dance dress](http://www.smartsgarment.com/catalogue).anything else?! of course,maybe you have the garden.you need the [garden tools](http://www.chinabestop.com) and hand tools.anwer is correction.you will like this cute and pretty tools,it is floral tools.Hope those info can help you.enjoy them!

---

### Post by Mark76 on 2008-06-03
If anyone's interested I threw this Icebuntu logo together in Inkscape.  Sadly I seem to have run out of talent, so if you like it and want to use it let me know.

---

### Post by kevdog on 2008-06-03
Is the Ceni source available for download?  Where do I get the sources?  Id like to try it on Ubuntu if possible.  It does look quite easy.

---

### Post by qazwsx on 2008-06-03
> **kevdog said:**
> Is the Ceni source available for download?  Where do I get the sources?  Id like to try it on Ubuntu if possible.  It does look quite easy.
ceni seems to be perl script. Like everyting in sidux it is free.
deb package and tar
[ftp://debian.tu-bs.de/project/sidux/debian/pool/main/c/ceni](ftp://debian.tu-bs.de/project/sidux/debian/pool/main/c/ceni)

---

### Post by zmjjmz on 2008-06-03
> **Mark76 said:**
> If anyone's interested I threw this Icebuntu logo together in Inkscape.  Sadly I seem to have run out of talent, so if you like it and want to use it let me know.

Sorry, but we already have one in the attached zip.
Thanks for that though.

---

### Post by Aliby on 2008-06-11
I must say that the contribution by Mark76 looks more attractive
:KS
> **zmjjmz said:**
> Sorry, but we already have one in the attached zip.
Thanks for that though.

---

### Post by Mark76 on 2008-06-11
Thanks Aliby :D

I just thought the warm, cosy colours of the standard Ubuntu logo look a bit odd in a distro called *Ice*buntu.  So I had a go at making an alternative ;)

---

### Post by Mark76 on 2008-06-11
Actually, I'm thinking of the other Icebuntu :oops:

---

### Post by zmjjmz on 2008-06-11
Although I haven't been able to contact Markp1989 for sometime (partially my own fault.), we've already started worrying about the "buntu" part of the trademark.
No offense, but that logo looks quite like the Kubuntu logo, which is a registered trademark by Canonical...

---

### Post by Mark76 on 2008-06-11
Yeah. I was hoping someone with more artistic skill could make it look... *icier*.  That'd go some way to making it look less KDE-ey.

But if the project is going to have to drop the buntu tag, then I guess neither design would be appropriate.

Maybe it's time to start lobbying to get Ice made a quasi official member of the Buntu family. Like Cousin Flux.

---

### Post by zmjjmz on 2008-06-11
We really need to get any trademakr issues worked out before we hit Distrowatch.

---

### Post by markp1989 on 2008-06-11
I haven't been thinking about Icebuntu for a  while, I plan to start working on a new version some time this month,

I was planning to email Ubuntu about the trademark issue, but i have not done it yet, i think it would be better to rename Icebuntu to something different, I'm just not sure what to call it, any suggestions?  

zmjjmz: Sorry I haven't replied to your msn messages, recently I havnt been on the computer as much as usual

---

### Post by Mark76 on 2008-06-11
Are you still allowed to use the Ubuntu repositories or will you have to switch to Debian?

How about DebIce?

Or Frosty The Distro :D

---

### Post by zmjjmz on 2008-06-11
Why wouldn't we be allowed to use the Ubuntu repositories?

---

### Post by Robux the great on 2008-06-11
This sounds like a worthwhile project

If it gets going let me know and I will test it on my hardware and report back.

Regards

Rob

---

### Post by Mark76 on 2008-06-11
How would I know?

---

### Post by zmjjmz on 2008-06-11
I dunno, you suggested that we wouldn't be able to :confused:

Anyways, we already have some artwork for icebuntu, but that could be changed to...
:/
t3h l337 1c3wm di57r0?
:D
EDIT: Robux, just remember to post at the forums at
[http://icebuntu.6.forumer.com](http://icebuntu.6.forumer.com) (sorry nathangrubb, it's just that I got adblock and the ads don't bother me anymore).

---

### Post by Mark76 on 2008-06-11
Did I suggest that?

Oops :oops:

---

### Post by markp1989 on 2008-06-11
> **zmjjmz said:**
> I dunno, you suggested that we wouldn't be able to :confused:

Anyways, we already have some artwork for icebuntu, but that could be changed to...
:/
t3h l337 1c3wm di57r0?
:D
EDIT: Robux, just remember to post at the forums at
[http://icebuntu.6.forumer.com](http://icebuntu.6.forumer.com) (sorry nathangrubb, it's just that I got adblock and the ads don't bother me anymore).

for some reason i cant access that forum, just get the sever not fount message

---

### Post by zmjjmz on 2008-06-11
How completely odd.
It loads fine for me.
It's in the US though, maybe a cable was cut or something?
EDIT: You were able to get there fine a few hours ago...

---

### Post by markp1989 on 2008-06-11
> **zmjjmz said:**
> How completely odd.
It loads fine for me.
It's in the US though, maybe a cable was cut or something?
EDIT: You were able to get there fine a few hours ago...

im able to access it now, dont know why i couldnt

---

### Post by zmjjmz on 2008-06-11
Guess it doesn't matter then :/
Anyways, our IRC channel is #icebuntu on irc.freenode.net
(I'm going to keep saying that until we have more than one [me] regular...)

---

### Post by Dr.Ninethousand on 2008-06-28
is there a torrent anywhere for 2.3?

I've downloaded the iso several times from the couple of sources I could find, but the md5sum never matches and is always different..

(I always have that problem with downloaded .iso files from sources other than torrents..  is that abnormal? do I have some kind of issue?)

---

### Post by zmjjmz on 2008-06-28
I think Mark tried to make a torrent earlier, and failed.
EDIT: You may want to ask your ISP about the corruption though.

---

### Post by Dr.Ninethousand on 2008-06-28
lol, pretty sure my ISP would just go "uhhhhhhh.. you should probably be using Windows shouldn't you?..  uhhhhhh..."

---

### Post by markp1989 on 2008-07-02
I am thinking of stepping down as lead developer, is there anyone who will be willing to take my place.

I am doing this because I think this project has gone as far as I can take it with my current ability, however, i believe that Icebuntu has a lot of potential, if a good developer takes over.

I would like to make it clear that I'm not going to completely abandon the project, I am still willing to help with testing and other stuff as and when i can.

Sorry

MarkP1989

EDIT: this is the link i got most of the information from when i was working on Icebuntu  [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by Dr.Ninethousand on 2008-07-02
well hopefully it continues..

there are other tiny distros, but I would definitely prefer to use ubuntu repos and resources, and I don't really like fluxbox..

---

### Post by Mark76 on 2008-07-03
Has anyone ever managed to install icedock on a Debian/Ubuntu machine?

---

### Post by graabein on 2008-07-03
How does this compare to [LXDE]("http://lxde.org/about.html")? Even lighter? 

I'd like to see a screenshot of the latest version.


Is this image below something that's possible in icewm?
[IMG]http://puppyfiles.org/dotpupsde/dotpups/WindowManagers/Muppy-icedock.jpg[/IMG]
[http://puppyfiles.org/dotpupsde/dotpups/WindowManagers/Muppy-icedock.jpg]("http://puppyfiles.org/dotpupsde/dotpups/WindowManagers/Muppy-icedock.jpg")

---

### Post by zmjjmz on 2008-07-07
Icedock looks pretty cool.
I'm going to try and get on making some LiveCD's, but it may take a  while for me to get it working.

EDIT: LXDE uses Openbox, so it's slightly heavier.

---

### Post by Mark76 on 2008-07-07
Does it?

I can't get the darn thing to work. Care to give me a few pointers?

---

### Post by zmjjmz on 2008-07-07
LXDE?
I just followed the guide on their website, it worked fine.

---

### Post by Mark76 on 2008-07-07
No, icedock.  I downloaded the src code but I can't figure out how to compile it.

---

### Post by zmjjmz on 2008-07-07
Well someone got it working, I haven't had the chance unfortunately.

---

### Post by joninkrakow on 2008-07-08
> **zmjjmz said:**
> Icedock looks pretty cool.
I'm going to try and get on making some LiveCD's, but it may take a  while for me to get it working.

EDIT: LXDE uses Openbox, so it's slightly heavier.

I'm typing this from LXDE using icewm as my window manager. I forgot to set icewm to not load its dock when I set it up, however, so I can hit the Windows key and get the icewm dock's menu. :-)

In any case, you don't need to use Openbox with LXDE. It is possible to change that. BTW, I switched to icewm so I could use the thinblack them. It looks good with the LXpanel. 

-Jon

---

### Post by hellomoto on 2008-07-14
how is the production of this getting on?

I would love to be able to help but i really wouldn't be any use.

I would love to get my hands of a copy, one of my PCs is so old that even xubuntu runs slow! However I know what im doing with ubuntu and I don't really want to try puppylinux or damn small linux so please get out this flavor!

---

### Post by zmjjmz on 2008-07-14
It's out already.
In IceBuntu link in my sig, go to the section labeled Releases, and go to Icebuntu 2.3
There's a download link in that post.

---

### Post by zmjjmz on 2008-07-19
Ok, so I've gone ahead and modded Thinblack and Icebuntu to use the logo attached, and I put the logo on the wallpaper.

---

### Post by MattBD on 2008-07-19
That's a really cool logo.

---

### Post by zmjjmz on 2008-07-19
> **MattBD said:**
> That's a really cool logo.

Credit goes to David Nuon, Nathan Grubb's friend.

---

### Post by zmjjmz on 2008-07-23
Ok guys, I'm going on a two week bike trip come friday, so don't expect anything for a while.

---

### Post by markp1989 on 2008-09-25
bump

---

### Post by brack on 2009-03-02
Is this projct stil alive? Is it possible to upgrade IceBuntu till 8.10 or it is too late?

---

### Post by zmjjmz on 2009-03-02
It will be soon, expect something before May.

---

### Post by aysiu on 2009-06-06
I don't know if the proper IceBuntu is still going on or not, but I did a quick Ubuntu IceWM Remix if people are interested.

You can download it [here](http://www.2shared.com/file/6145764/1542fa50/ubuntuicewmremix.html).

If you want to do an *md5sum -c* on the integrity of the download, here is what the ubuntuicewmremix.iso.md5 file should look like: ```
e5a1d9687a1a8a104c4edfbec5626131 *ubuntuicewmremix.iso
``` Screenshots attached.

I started with the mini.iso and installed Synaptic, Firefox, Thunar, AbiWord, aumix, WICD, and that's about it. It's very barebones. You can use Synaptic to add more as you see fit. The .iso is 253 MB. The installed size is just a little over 800 MB.

Hope you like it.

---

### Post by gn2 on 2009-06-06
Was that a Remastersys job?

You wouldn't happen to know if Remastersys only works if you have originally installed from a Live CD?

---

### Post by pookiebear on 2009-06-06
cool downloading now.

---

### Post by pookiebear on 2009-06-06
download page from that link won't feed the file, just a bunch of ads.

---

### Post by Mark76 on 2009-06-06
I can't find a download link on that page

Does it not work with webkit browsers?

---

### Post by markp1989 on 2009-06-06
hey, nice to see this project doing something again, sorry i had to drop out before. 

i will download the iso , and make a torrent that i will seed. as soon as i can work out how to download from that website.

edit: found the download button , bottom right, says "Save file to your PC: click here"



edit: heres a new torrent the other 1 didnt work [http://www.mininova.org/tor/2663836](http://www.mininova.org/tor/2663836)

---

### Post by aysiu on 2009-06-06
> **gn2 said:**
> Was that a Remastersys job?

You wouldn't happen to know if Remastersys only works if you have originally installed from a Live CD? It is a Remastersys job. And, no, it doesn't have to be originally installed from the live CD. I installed this from the mini.iso, in fact (the one that's about 10 MB).

> **pookiebear said:**
> download page from that link won't feed the file, just a bunch of ads. > **Mark76 said:**
> I can't find a download link on that page

Does it not work with webkit browsers? Sorry. It's a file hosting site full of ads. It helps if you have NoScript on (of course, that's a Firefox extension, so it probably doesn't work with a webkit browser). The file download link is at the very bottom of the page.

I also have it available on another file hosting site that may have fewer ads:
[http://files.filefront.com/ubuntuicewmremixiso/;13864261;/fileinfo.html](http://files.filefront.com/ubuntuicewmremixiso/;13864261;/fileinfo.html)

---

### Post by zmjjmz on 2009-06-06
Yeah, sorry. I didn't realize how much work I would have during school. I should start working on it in August.

---

### Post by aysiu on 2009-06-06
> **markp1989 said:**
> hey, nice to see this project doing something again, sorry i had to drop out before. 

i will download the iso , and make a torrent that i will seed. as soon as i can work out how to download from that website.

edit: found the download button , bottom right, says "Save file to your PC: click here"

edit: i just attached the torrent file. i had to add .doc to the end of it, otherwise ubuntuforums wouldnt let me upload it, remove the .doc and it should work ok. 

tell me if it works .
Thanks for doing that. I won't have my netbook on all the time, but when it is, I'll be a peer seeder for that torrent (hope I'm using the right terminology).

---

### Post by zmjjmz on 2009-06-06
I'm going to host it at mhscc.ath.cx
I'll post a link when it's ready.

---

### Post by aysiu on 2009-06-06
Awesome.

By the way, I went for what I consider the bare minimum in terms of what's installed. If anyone wants to tweak it and make available a new one, Remastersys is dead-easy to use to create an .iso.

---

### Post by gn2 on 2009-06-06
> **aysiu said:**
> It is a Remastersys job. And, no, it doesn't have to be originally installed from the live CD. I installed this from the mini.iso, in fact (the one that's about 10 MB).

Excellent, that's very helpful information, thanks Aysiu :)
I have an old P3 unit with low RAM that gets used as a dedicated music jukebox and I can't find a distro that suits both me and it.
Now I will be able to create my own.

---

### Post by aysiu on 2009-06-06
> **gn2 said:**
> Excellent, that's very helpful information, thanks Aysiu :)
I have an old P3 unit with low RAM that gets used as a dedicated music jukebox and I can't find a distro that suits both me and it.
Now I will be able to create my own.
The only caveat I would throw in is that, as far as I know, the remastered .iso will always include Remastersys and its dependencies (since it is an installed application at the time the .iso is made, by definition).

Nevertheless, I was able to create a relatively slim Ubuntu remix even with Remastersys installed (253 MB for a live CD isn't so bad).

The one thing I would advise is that you change your APT preferences to not install recommended dependencies (against the 9.04 default). Otherwise, Remastersys will bring in half the *ubuntu-desktop* metapackage during its first run.

---

### Post by Sublime Porte on 2009-06-06
> The only caveat I would throw in is that, as far as I know, the remastered .iso will always include Remastersys and its dependencies (since it is an installed application at the time the .iso is made, by definition).

Check in /etc/remastersys.conf (from memory is the configuration file for remastersys), there's an option to disclude files, you'd just need to get a list of files (from the deb package) that remastersys installs, and then put them in the discluded files list.

Just out of curiousity, did you install gnome-network-manager? Because I've been playing with remastersys, but unless I install gnome-network-manager (I want to use wicd instead), the LiveCD I create freezes on boot up when trying to configure the network interface. I've asked the remastersys author, but he was unable to assist.

---

### Post by aysiu on 2009-06-06
> **Sublime Porte said:**
> Check in /etc/remastersys.conf (from memory is the configuration file for remastersys), there's an option to disclude files, you'd just need to get a list of files (from the deb package) that remastersys installs, and then put them in the discluded files list.

Just out of curiousity, did you install gnome-network-manager? Because I've been playing with remastersys, but unless I install gnome-network-manager (I want to use wicd instead), the LiveCD I create freezes on boot up when trying to configure the network interface. I've asked the remastersys author, but he was unable to assist.
Yeah, I thought about using the exclude option, but that would entail me finding every instance of Remastersys, and I just couldn't be bothered. I kind of think it should be a default setting to exclude Remastersys from the remastered .iso.

And, no, I didn't include Network Manager, and I didn't have any freeze-ups. I put in WICD instead.

---

### Post by zmjjmz on 2009-06-06
In addition to having the downloads mirrored, I think it should be an official website for icebuntu. Obviously, this aspect will have to be taken up in August, but if anyone wants to submit CSS designs and such (I am **not** an artist) it would be nice.

---

### Post by Sublime Porte on 2009-06-07
> Yeah, I thought about using the exclude option, but that would entail me finding every instance of Remastersys, and I just couldn't be bothered.

If you installed Remastersys by deb package then just do: dpkg -L remastersys >filelist.txt
And it'll create a text file listing all the files remastersys installs.

> And, no, I didn't include Network Manager, and I didn't have any freeze-ups. I put in WICD instead.

Just to confirm, you're using jaunty?

---

### Post by aysiu on 2009-06-07
It's not just Remastersys. It's all the Remastersys dependencies as well: casper, ubiquity, etc.

And, yes, it's Jaunty.

---

### Post by Sublime Porte on 2009-06-07
Well since they're all installed by deb, then you can repeat the same process, but use >> instead of > so it appends to the filelist.txt

But I would've thought you'd want ubiquity installed, no? Since it is required if you want to let users install.

---

### Post by zmjjmz on 2009-06-07
The problem with Ubiquity is that it is rather resourse intensive, and requires at least 256MB RAM. I would suggest that you modify inxtaller.

---

### Post by markp1989 on 2009-06-07
edit: heres a new torrent the other 1 didnt work [http://www.mininova.org/tor/2663836](http://www.mininova.org/tor/2663836)

tell me if you have any problems with it.

---

### Post by ayenack on 2009-06-15
Someone needs to update the [Derivative Team page]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu"). The download is still pointing to:

[http://hosted.filefront.com/markp1989/](http://hosted.filefront.com/markp1989/)

There's no download there.

---

### Post by wlake on 2009-07-31
I have played around with this and I like the speed and responsiveness of the desktop. I think this is quicker than LXDE. I had to remove wicd and install network manager because wicd did not pick up my wireless (iwl3945).

I also had a hard time installing the nvidia drivers, but that was probably due to my lack of expertise.

I would like to see icebuntu continue.

---

### Post by Johnny K on 2009-08-10
Not many (or any) of the download links that are available are currently working. We need to get this software out there somehow.

With the help of markp1989, I got a copy of the official ISO and created a torrent. A link to the torrent is available below.

I know that markp1989 is seeding, and I will try to as well. Can we get 10 people to promise to seed it as well? We need some support to spread this iso on the internet again.

Torrent: [http://www.filedropper.com/ubuntuicewmremixiso](http://www.filedropper.com/ubuntuicewmremixiso)

---

### Post by Mark76 on 2009-08-10
I'll seed it if you like

---

### Post by jaxxstorm on 2009-08-10
Hello everyone. Hows the making of Icebuntu going?

I'm interested in getting involved. Have we got anywhere with it. Is there anyone actively developing it?

---

### Post by Johnny K on 2009-08-10
> **Mark76 said:**
> I'll seed it if you like

Great, thank you! I just don't want people to be stuck without a download like I was...

---

### Post by Mark76 on 2009-08-10
I'll need a torrent file first though

---

### Post by jaxxstorm on 2009-08-10
**EDIT: in the process of researching the situation etc, it seems this thread has sprung back to life and mark is now re seeding the torrent. Fiar play, and i'll let him to continue as it is**

Ok, from what I can see, this doesn't seem to have progressed anywhere. I'm thinking about making a new thread, but here is my idea at the moment.

IceWM seems to play nice with GTK, so I'm going to include some GTk apps to make it familiar to those who already use Ubuntu. I'm going for a distro that is INCREDIBLY lightweight, it will include the very minimal software available, and the lightest software I can find, unless functionality means it isn't viable to be used.

So, without further ado. Some ideas.

I'll be building from an Ubuntu minimal CD. Inistally, it'll just be a remastersys'd iso thats available. Once I'm happy with the way things are, I'll look into making it a fully featured distro with repos and everything, but that'll be a fair way off.

Obviously, The default Window Manager will be IceWM, as up to date as possible. I'll definitely, definitely need help with the themes however, as graphical design is NOT my strong point. I know there is an icebuntu theme, but its old and deprecated.

I'm figuring the best login manager will be SLiM. Lightweight, configurable, and it'll give a bit of distinction from standard Ubuntu. 
Web browser - I can't really look past firefox here unfortunately. I'd like to be able to use either kazehekase or Midori, but as far as I'm aware, they don't support flash and therefore can;t really be considered usable. Opera is out because its no open source.

Email client - I'm not going to include one. As far as I can gather, webmail is taking off too much to include one.

Message client - pidgin, I'll include the facebook chat plugin too, because I can imagine LOTS of people use it.

Music player - Sonata is my first choice at the moment. I'll consider other ideas if anyone fancies suggesting any.

File manager - Can't see past PCManFm
 here really.

Finally, for terminal emulation I'll probably go for Sakura. if not it'll be terminator.

I think that'll be it for applications. Anything else will be system tools etc.

What does everyone think? is anyone willing to help with graphic design etc?

---

### Post by Johnny K on 2009-08-10
> **Mark76 said:**
> I'll need a torrent file first though

Does this link, from my previous post, work?

[http://www.filedropper.com/ubuntuicewmremixiso](http://www.filedropper.com/ubuntuicewmremixiso)

---

### Post by Mark76 on 2009-08-10
Yeah the link works

---

### Post by Jesus_Valdez on 2009-08-10
Midori supports flash.

What about Arora for web browser?

[http://code.google.com/p/arora/](http://code.google.com/p/arora/)

but perhaps** Ice**weasel is more theme-related :P

---

### Post by Johnny K on 2009-08-10
> **Mark76 said:**
> Yeah the link works

That link should allow you to download the .torrent file. Are you having any issues?

---

### Post by jaxxstorm on 2009-08-10
> **Jesus_Valdez said:**
> Midori supports flash.

What about Arora for web browser?

[http://code.google.com/p/arora/](http://code.google.com/p/arora/)

but perhaps** Ice**weasel is more theme-related :P

Midori is buggy as hell as I remember correctly, I could be wrong.

I'd be interested in using Arora for a web browser but as far as I can tell its not near completion. Theres also the fact it uses QT and I'd prefer to stick to gtk if possible.

I'm trying to decide what to do about a theme. Crunchbang, my current distro of choice using an all black theme, and corenominal seems to have done that because its easier to just turn things black than to actually think about theming etc. I definitely don't want to go for a black theme, but perhaps a uniform colour? Icy coloured? I'll have a think.

---

### Post by markp1989 on 2009-08-10
> **jaxxstorm said:**
> **EDIT: in the process of researching the situation etc, it seems this thread has sprung back to life and mark is now re seeding the torrent. Fiar play, and i'll let him to continue as it is**

Ok, from what I can see, this doesn't seem to have progressed anywhere. I'm thinking about making a new thread, but here is my idea at the moment.

IceWM seems to play nice with GTK, so I'm going to include some GTk apps to make it familiar to those who already use Ubuntu. I'm going for a distro that is INCREDIBLY lightweight, it will include the very minimal software available, and the lightest software I can find, unless functionality means it isn't viable to be used.

So, without further ado. Some ideas.

I'll be building from an Ubuntu minimal CD. Inistally, it'll just be a remastersys'd iso thats available. Once I'm happy with the way things are, I'll look into making it a fully featured distro with repos and everything, but that'll be a fair way off.

Obviously, The default Window Manager will be IceWM, as up to date as possible. I'll definitely, definitely need help with the themes however, as graphical design is NOT my strong point. I know there is an icebuntu theme, but its old and deprecated.

I'm figuring the best login manager will be SLiM. Lightweight, configurable, and it'll give a bit of distinction from standard Ubuntu. 
Web browser - I can't really look past firefox here unfortunately. I'd like to be able to use either kazehekase or Midori, but as far as I'm aware, they don't support flash and therefore can;t really be considered usable. Opera is out because its no open source.

Email client - I'm not going to include one. As far as I can gather, webmail is taking off too much to include one.

Message client - pidgin, I'll include the facebook chat plugin too, because I can imagine LOTS of people use it.

Music player - Sonata is my first choice at the moment. I'll consider other ideas if anyone fancies suggesting any.

File manager - Can't see past PCManFm
 here really.

Finally, for terminal emulation I'll probably go for Sakura. if not it'll be terminator.

I think that'll be it for applications. Anything else will be system tools etc.

What does everyone think? is anyone willing to help with graphic design etc?

For terminal you can just use xterm,as it is included in the xorg package (i think)  

are you planing to bother with any networking/power management programs, if so i would recommend wicd, which i use on my laptop

it would be nice to have a program to change gtk themes, icons, fonts etc, [http://wiki.lxde.org/en/LXAppearance](http://wiki.lxde.org/en/LXAppearance) works rather well, i use it on my desktop. 

for some light programs look here [http://wiki.lxde.org/en/Main_Page](http://wiki.lxde.org/en/Main_Page) , obviously dont install them all or it will just end up becoming lxubuntu, but it can give you a few ideas.

---

### Post by Mark76 on 2009-08-10
> **Johnny K said:**
> That link should allow you to download the .torrent file. Are you having any issues?

Well. Nothing's coming down the pipe so far.

Regarding browsers. How about Seamonkey (or IceApe. If you prefer :D)?

---

### Post by markp1989 on 2009-08-10
I have just been speaking with jaxxstorm , as i havnt done any work on this project, we have aggred that he will be taking over development.

He is looking for sugestions for software / setup ideas any one has, so any suggestions are welcome :)

It is very nice to see this project starting up again, as the last version i did was based on ubuntu 8.04. 

 
Thanks Markp1989

---

### Post by Johnny K on 2009-08-10
> **Mark76 said:**
> Well. Nothing's coming down the pipe so far?

I believe I am sharing it, but I am very new to torrents so it's very likely that I'm wrong.

Could it has something to do with the fact that The Pirate Bay is down?

---

### Post by markp1989 on 2009-08-10
just a thought: in the old versions jockey-gtk (restricted drivers manager) was installed, so after first boot, the user could set up there video drivers etc easily.

edit:im seeding the torrent, but so far, i have not had any people connecting to me,

---

### Post by jaxxstorm on 2009-08-10
> **markp1989 said:**
> For terminal you can just use xterm,as it is included in the xorg package (i think)  

are you planing to bother with any networking/power management programs, if so i would recommend wicd, which i use on my laptop

it would be nice to have a program to change gtk themes, icons, fonts etc, [http://wiki.lxde.org/en/LXAppearance](http://wiki.lxde.org/en/LXAppearance) works rather well, i use it on my desktop. 

for some light programs look here [http://wiki.lxde.org/en/Main_Page](http://wiki.lxde.org/en/Main_Page) , obviously dont install them all or it will just end up becoming lxubuntu, but it can give you a few ideas.

Thanks mark.

I'm going to avoid using xterm as its lack of GTK-ness will make it look quite ugly against the rest of the apps. I'm sure I'll find a terminal emulator that works and looks right with the rest of the apps. Thanks for the lxde links, they look really useful. Hopefully I'll produce something worthy of the work you started.

---

### Post by jaxxstorm on 2009-08-10
I've updated the [wiki page]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu") a little bit, changing the links etc. I noticed that the links to the old releases were dead, so I haven't saved them, although they will be in the page edit history should you need to re acquire them.

I've left a link to this thread in on the [Wiki page]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu") - I think I'm going to create a new thread, unless anyone has any objections? it'll allow me to ask for help and update people on the progress.

EDIT - New thread started here - [http://ubuntuforums.org/showthread.php?t=684890&page=38](http://ubuntuforums.org/showthread.php?t=684890&page=38)

---

### Post by ksennin on 2009-08-10
> **jaxxstorm said:**
> I've updated the [wiki page]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu") a little bit, changing the links etc. I noticed that the links to the old releases were dead, so I haven't saved them, although they will be in the page edit history should you need to re acquire them.

I've left a link to this thread in on the [Wiki page]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu") - I think I'm going to create a new thread, unless anyone has any objections? it'll allow me to ask for help and update people on the progress.

EDIT - New thread started here - [http://ubuntuforums.org/showthread.php?t=684890&page=38](http://ubuntuforums.org/showthread.php?t=684890&page=38)
That link takes me back to this very same page.

---

### Post by jaxxstorm on 2009-08-11
> **ksennin said:**
> That link takes me back to this very same page.

Oooops,

sorry, this is the thread link!

[http://ubuntuforums.org/showthread.php?t=1236897](http://ubuntuforums.org/showthread.php?t=1236897)

---

### Post by Johnny K on 2009-08-11
TPB seems to be back up. The current IceBuntu torrent ([http://www.filedropper.com/ubuntuicewmremixiso](http://www.filedropper.com/ubuntuicewmremixiso)) should now be working. Would anyone be able to verify?

---

### Post by #11u-max on 2009-08-11
jaxxstorm, should i post up new artwork here?

---

### Post by Ibidem on 2010-04-20
Well, looks like Spri has switched to JWM (what Puppy uses).
That leaves "Icebuntu" pretty much dead unless someone starts it back up...:(

I'd suggest a new project, the "Ubuntu IceWM Remix"/UIR

Working on getting Icedock packaged (first try at packaging; I have a tarball here)
It takes Ocaml; I have the full source (attached).  If it just supported transparency!
(It does work with xcompmgr +transset)

What I've got now is close to LXDE, but no lxpanel/openbox.

What desktop/file manager is preferred:
1.  Rox
2.  PCManFM (LXDE)
3.  Thunar (XFCE)
4.  idesk + whatever file manager
   a. MC
   b. xfe
   c. xfm
DFM (unmaintained since ~2000), while I've compiled it on Lucid, has some CPU race issue that completely hogs one core.

---

### Post by Mark76 on 2010-04-20
I'd go with Rox.

But you knew that already ;)

---

### Post by Ibidem on 2010-04-21
I've been pretty happy with PCManFM myself; the main thing with ROX is that I haven't seen a "tree view".

---

### Post by Ibidem on 2010-05-02
Rox will be default, if I build it.  I'd like to add roxterm (features like gnome-terminal, but light enough to go w/ Rox) too.

Now, web browser? or
1. Firefox (compatible/supported, huge, a little slow)
2. Chromium (fastest, but uses ram & cpu)--default on latest Spri, IIRC
3. Seamonkey (supposed to be faster & lighter than Firefox, less well supported, extras)
4. Netsurf ("runs on a 16 MB system", though Ubuntu requires 64 to boot; HTML5, no plugins)
--replaces dillo
5. w3m (included anyhow, not used as x-www-browser?; text-mode)
6. Links (not default, text-mode browser)
7. Epiphany (gnome-webkit)
Opera is good, but proprietary-->no-go on here
No KDE stuff, no Konqueror; Midori is too buggy for a default, IMHO.

Mail client-
Claws, Sylpheed, Seamonkey, alpine, mutt, or none?
(omitting Thunderbird & Evolution as I doubt they'd work with this).

I'll say +1 for Claws; it's a decent GUI, lightweight, etc.
I use Firefox all the time, but am open to alternatives that don't crash too much (i.e. NOT Midori, which I have tried and rejected).

---

### Post by murderslastcrow on 2010-05-02
You know, these are all great ideas, but I think a good idea would be to create the most minimal Ubuntu possible, and preload it with a lot of different WMs. Since the three heaviest (Gnome, KDE, Xfce) all have their own distro, why not just pile the rest of the memorable WMs into an ISO with lightweight software? Then let people remove the .desktop entries or packages they don't want?

There's no way any of this stuff is too large to fit on a CD together. Wouldn't this decrease the amount of reproduced effort? No use in being lightweight if you're only a few loops/megabytes less memory than Xubuntu.

If someone could make a Damn Small Linux that offered more advanced DEs just in case, and a simpler way to install new software, we'd have something really unique, there.

Either way, I really like the ideas here, and I plan on placing this on an old desktop soon. ROX is fine, although PCManFM is a bit more user-friendly. If it's lighter, go with it.

---

### Post by zmjjmz on 2010-05-02
> **murderslastcrow said:**
> 
If someone could make a Damn Small Linux that offered more advanced DEs just in case, and a simpler way to install new software, we'd have something really unique, there.

Eh, DSL does have apt and MyDSL, but it is kinda dead.


I would recommend using the latest Dillo with the option to install any browser given in a nice little script (I would be willing to write it, just need to know some environmental variables). Basically, it would display a bunch of options for a browser, with recommended specs next to them. Selecting an option would have it download and install the browser. We could do the same with mail clients.

---

### Post by Mark76 on 2010-05-03
ROX has the advantage over PCManFM that the icons can be arranged any way the user wishes. It's also a more mature project.

---

### Post by zmjjmz on 2010-05-03
> **Mark76 said:**
> ROX has the advantage over PCManFM that the icons can be arranged any way the user wishes. It's also a more mature project.

Well there's also iDesk for that, though I haven't measured its resource usage.

---

### Post by zmjjmz on 2010-05-04
> **zmjjmz said:**
> 
I would recommend using the latest Dillo with the option to install any browser given in a nice little script (I would be willing to write it, just need to know some environmental variables). Basically, it would display a bunch of options for a browser, with recommended specs next to them. Selecting an option would have it download and install the browser. We could do the same with mail clients.

So here's the browser select script (in perl). It's a first draft, I haven't had a chance to test it (AP exams), so I may have gotten something horribly, horribly wrong.

[http://pastebin.ca/1871439](http://pastebin.ca/1871439)

---

### Post by Ibidem on 2010-05-04
Big problem with using dillo:

ibid@newbook:~$ aptitude show dillo
No current or candidate version found for dillo
Package: dillo
State: not a real package

ibid@newbook:~$ aptitude show dillo2
E: Unable to locate package dillo2

(Lucid Lynx does not have any dillo versions; see [https://bugs.launchpad.net/ubuntu/+source/dillo/+bug/428529](https://bugs.launchpad.net/ubuntu/+source/dillo/+bug/428529)--apparently dillo required gtk1 and dillo2 requires FLTK2, and there have been license issues with fltk2)

BUT, Netsurf has almost the same system requirements, while rendering a whole lot better (HTML5, CSS; no js or plugins)--I'd say that dillo vs Netsurf would be pretty obvious.

As far as "why not use a different version of Ubuntu" goes, Lucid is the latest, fastest booting (except for a few computers), and longest supported (to 2013 on desktop, 2015 on server) version of Ubuntu.
The main advantage to an older version is if we dig up the pre-Hardy Heron versions that will work on <64 MB of ram.

---

### Post by Ibidem on 2010-05-04
OK, Dillo 2 (SSL enabled, rudimentary CSS) is in this ppa:
[**ppa:d.filoni/dillo+ssl**]("https://launchpad.net/%7Ed.filoni/+archive/dillo+ssl")
But it isn't in the standard repos (main, universe, restricted, multiverse), and Netsurf does a lot more with the same resources.

---

### Post by zmjjmz on 2010-05-04
> **Ibidem said:**
> Big problem with using dillo:


Oh, eh, I really just threw dillo out there. Any browser could be used, and I suppose I could try and get dillo working on lucid somehow and host it for the script.

---

### Post by Ibidem on 2010-05-05
> **zmjjmz said:**
> Well there's also iDesk for that, though I haven't measured its resource usage.
If you add another running program, you use more resources.  iDesk+any file manager will probably be heavier than just a file manager.

As far as browser goes, if you're fine with no javascript, netsurf + the script should work.
Dillo from the PPA would be possible, but I prefer to stick with the repositories when possible.
If Opera were DFSG-free, I'd use it.

---

### Post by Mark76 on 2010-05-05
If you do go with Netsurf as the default browser be aware that the version in the Ubuntu repositories is way out of date. They're currently on 2.5 for the stable version and 3.0 is available through Subversion.

---

### Post by sudoer541 on 2010-05-05
Can anyone help me? 
I would like to create the following versions of ubuntu:

Ububntu fire RED
Ubuntu Leaf GREEN
Ubuntu Gold
Ubuntu Emerald and Saffire
Ubuntu Pikachu edition
Ubuntu Charmander Edition
Ubuntu Bulbasar Edition
Ubuntu Crystal 
Ubuntu Mystery gudgeon and rescue 
Ubuntu Dash
Ubuntu Trozeil
Ubuntu Ranger
Ubuntu Diamond and Pearl
Ubuntu platinum 
Ubuntu Balck and White
Ubuntu Stadium 
Ubuntu Snap
Ubuntu Puzzle league 
Ubuntu Hacker edition
Ubuntu Criminal edition
Ubuntu astronomers Edition
Ubuntu Electricians edition
Ubuntu Lucifer Edition
Ubuntu Recycling edition
Ubuntu Rap Edition
Ubuntu classic edition
Ubuntu Milly Cyrus Edition
Ubuntu Justin Bieber Edition
Ubuntu Jonas Brothers Edition
Ubuntu Flo-Rida Edition
Ubuntu Judge Judy Edition (Dangerous)
Ubuntu 69 Edition
Ubuntu Mark Shuttleworth Edition
Ubuntu Keyboard only Edition
Ubuntu mouse only Edition
Ubuntu Monitor Only Edition
Ubuntu facebook Edition
Ubuntu Tweeter Edition
Ubuntu cloud edition
Ubuntu Thunder edition
Ubuntu Sun edition
Ubuntu Science edition
Ubuntu RFID edition
Ubuntu Linux Edition
Ubuntu Zelda Edition
Ubuntu Super Mario Edition
Ubuntu LOL Edition
Ubuntu iPad Edition (May void warranty)
Ubuntu iPod/iPhone edition
Ubuntu Girls dition
Ubuntu Pink Edition
Ubuntu Barbie
Ubuntu Make-up Edition
Ubuntu Boys Edition
Ubuntu car Edition
Ubuntu Business Edition
Ubuntu for Small business edition
Ubuntu for Tiny business edition
Ubuntu for corporations edition
Ubuntu for pre-school edition
Ubuntu elementary school edition
Ubuntu middle school edition 
Ubuntu High school edition
Ubuntu college edition
Ubuntu university edition
Ubuntu street edition 
Ubuntu gang edition
Ubuntu for Nokia
Ubuntu for Motorola 
Ubuntu for samsung
Ubuntu Athletes edition
Ubuntu Gaga edition 
Ubuntu Adam Lambert edition
Ubuntu cops edition
Ubuntu Nurse edition
Ubuntu doctors edition
Ubuntu motorists edition 
Ubuntu  youtube edition
Ubuntu  digg edition
Ubuntu  X rated edition
Ubuntu rich edition
Ubuntu  lawyers edition 
Ubuntu Sharia edition
Ubuntu for panasonic 
Ubuntu DIY edition
Ubuntu for dummies (book)
Ubuntu Microwave edition
Ubuntu sudeor541 edition(some restrictions may apply+ $150 fee is required to use ubuntu sudoer541 edition)

Btw I am serious!!! I want to create as many ubuntu variants as possible. 
Anyone wanna help?

---

### Post by Ylon on 2010-05-05
> **sudoer541 said:**
> Can anyone help me? 
I would like to create the following versions of ubuntu:
[...]
Ubuntu Nurse edition
[...]
Ubuntu  X rated edition


I am for a fork between these two edition :lolflag:

---

### Post by RiceMonster on 2010-05-05
> **sudoer541 said:**
> Can anyone help me? 
I would like to create the following versions of ubuntu:

Btw I am serious!!! I want to create as many ubuntu variants as possible. 
Anyone wanna help?

lol

---

### Post by zmjjmz on 2010-05-05
> **Ibidem said:**
> If you add another running program, you use more resources.  iDesk+any file manager will probably be heavier than just a file manager.

As far as browser goes, if you're fine with no javascript, netsurf + the script should work.
Dillo from the PPA would be possible, but I prefer to stick with the repositories when possible.
If Opera were DFSG-free, I'd use it.

That's fine, because I think the idea is that we get them to run the script first thing, if they have a net connection. The _only_ issue I see with this is that netsurf, being without Javascript, won't work with certain router web interfaces (*ahem* DD-WRT), and this may be an issue in a small proportion of really unfortunate cases.

---

### Post by Ibidem on 2010-05-15
> **zmjjmz said:**
> That's fine, because I think the idea is that we get them to run the script first thing, if they have a net connection. The _only_ issue I see with this is that netsurf, being without Javascript, won't work with certain router web interfaces (*ahem* DD-WRT), and this may be an issue in a small proportion of really unfortunate cases.
Perhaps also some redirect-based open wireless networks...
The question now--Do we want to make it work for these people?
If so, that limits our browser selection some; dillo and netsurf won't work:
Kazehake--http://kazehakase.sourceforge.jp/
Web (GTKhtml2) [http://chrislord.net/blog/Software/Web/](http://chrislord.net/blog/Software/Web/) (old)
Midori
Arora
Atlantis, which is ancient (gtk-webcore)
Orygin Web Browser ([http://www.sand-labs.org/owb](http://www.sand-labs.org/owb)) might be worth trying...perhaps.

---

### Post by zmjjmz on 2010-05-15
> **Ibidem said:**
> Perhaps also some redirect-based open wireless networks...
The question now--Do we want to make it work for these people?
If so, that limits our browser selection some; dillo and netsurf won't work:
Kazehake--http://kazehakase.sourceforge.jp/
Web (GTKhtml2) [http://chrislord.net/blog/Software/Web/](http://chrislord.net/blog/Software/Web/) (old)
Midori
Arora
Atlantis, which is ancient (gtk-webcore)
Orygin Web Browser ([http://www.sand-labs.org/owb](http://www.sand-labs.org/owb)) might be worth trying...perhaps.

You should try and test them out on a minimal machine, maybe like 128MB RAM, 400MHz proc (I have some celeries), and an integrated POS graphics card. I have a bunch if you don't, but I'm a bit busy at the moment.

---

### Post by Ibidem on 2010-06-04
I only have a PIII/800mhz with 256 MB RAM and a Pentium/166 with 160 MB RAM  (and then qemu, which does a good job of emulating a slow-as-molasses PC :-P ).
I've been looking and testing, and have concluded that Ubuntu (8.04+) is perhaps not the best platform for IceWM--which is part of what drove me to run Scientific Linux, where it's an official package with a mini-livecd.
Icebuntu may be swapping to disk if you use it on less than 128+ MB of ram, except for single-tasking with Abiword or Midori.
Dapper ran perhaps a little better on 64 MB of RAM.

But here's a tentative lineup for lowram systems, with approximate RSS:
Icewm+menu --13 MB for GUI
lxdm/wdm/slim/nodm (autologin)--~10-14 MB extra for login
X takes 18 MB
Rox takes 14 MB, managing desktop; PCManFM is 15 MB, and Xfe uses 4-8 MB while not managing the desktop.
And that's ~60 MB for a desktop.
Abiword is perhaps 21 MB, and Gnumeric is 16 MB.
Midori is ~11 MB, while Seamonkey would require 36 MB of RAM.
Xpdf takes just shy of 3 MB, in contrast to the ~5 MB for evince/epdfview (viewing small PDFs).
So 160 MB would be just enough for comfortable multitasking--barely.

Ibidem

---

### Post by Mark76 on 2010-06-04
IceWM can set the desktop background (icewmbg), but it doesn't allow for icons and there's no graphical interface, so you have to edit the ~/.icewm/preferences file everytime you want to set a new wallpaper.

---

### Post by zmjjmz on 2010-06-05
> **Mark76 said:**
> IceWM can set the desktop background (icewmbg), but it doesn't allow for icons and there's no graphical interface, so you have to edit the ~/.icewm/preferences file everytime you want to set a new wallpaper.

Not that hard to do in a script, actually.

So, let's think of some alternatives. There was the Pathetic Writer and the Siag suite for office. Pathetic Writer supports old, old, old, old RTF, but it should work if you really can't do much else.
If you don't mind doing more testing, do you think you can look into the resource usage of Hv3 or Uzbl?
I don't really know of any light file managers besides those mentioned and mc. (Xfe looks good though?) 
Should desktop file access be considered important?
I don't know what to say about the login -- I remember DeLi Linux 
basically had X startup and just have a terminal for you to login. I can see if I can get my DeLi computer running again to test this.

---

### Post by Mark76 on 2010-06-05
I've never been able to get Siag to work.

Is it cause I is 64 bit? :confused:

---

### Post by zmjjmz on 2010-06-06
> **Mark76 said:**
> I've never been able to get Siag to work.

Is it cause I is 64 bit? :confused:

This is possible. It worked for me on a 32-bit system.

---

### Post by Ibidem on 2010-06-06
Hv3 looked good at first (low ram, tabs, Javascript, etc.) and is pretty fast.  But it failed the biggest test: it wouldn't login.  That's due to some bug deep in the code, so I guess it's a no-go--especially since it hasn't been maintained since 2003.
Uzbl looks like it probably isn't worth the few MB of RAM that might be saved over Midori, unless you actually prefer a browser that has no features and requires configuration. And the current Midori is better than previously: it is now usable (still not ideal) as a browser, not just for testing.
If Xfe is used as file manager, there should be a shortcut on the taskbar.  Otherwise I'd use ROX.
But I'm tempted to just go ahead with IceWM, Midori, Rox & Xfe, Abiword, Gnumeric, and so on--possibly including MC, since it's on most other light IceWM distros.  We might make it a hair more usable on 128 MB PCs by paring the selection down and using outdated software, but it won't be that much gain and they may not boot from livecd.
Absolute minimum: IceWM with Links2/Chimera2, MC, Siag, Xterm & urxvt, ubiquity-frontend-debconf (text installer), getty (console login) + startx for login and GUI.  But that's a barely usable system that fits DeLi better than Ubuntu.  We should remember that Ubuntu probably will never work as well on the sort of system that requires this selection as other distros (DeLi, puplets, Grey Cat Linux...), due to its bloat and such.

If you doubt that Ubuntu is bloated, I don't know where you've been.  In all honesty, I have seen no reports of Ubuntu on IBM PS/2 systems, but the kernel still supports MCA buses.

---

### Post by zmjjmz on 2010-06-07
Sad to hear that about Hv3 -- It looked really, really promising.

I'm sure that if we can manage to spin out an Icebuntu distro with the stuff for 160MB and above, we can offer an even lighter version with the outdated stuff. Obviously the main one should be a priority.

---

### Post by Slug71 on 2010-06-07
**Spri**????

[http://www.sprilinux.com/?q=node/55](http://www.sprilinux.com/?q=node/55)

---

### Post by Mark76 on 2010-06-07
Which is moving over to JWM, according to the website.

So still no icelinux

---

### Post by Slug71 on 2010-06-07
> **Mark76 said:**
> Which is moving over to JWM, according to the website.

So still no icelinux

Yeh because its no longer being maintained and therefore makes sense. 
Could always fork Spri though.

---

### Post by anticapitalista on 2010-06-07
> **Mark76 said:**
> Which is moving over to JWM, according to the website.

So still no icelinux

There are a few outside of Ubuntu.

antiX, Absolute

---

### Post by Ibidem on 2010-06-07
Well, it looks like a few people may be working on Hv3.  But I tried building it from source and it is a mess--manually set up the makefile, etc.  The results I had were from the 2003 nightly, sources from "alpha 16", and I found mentions of alpha 11 from late 2006.  So I've  no idea what the latest is like.

EDIT:Last nightly is 08_0203, or "early in 2008". All those numbers had me confused for a bit

---

### Post by Ibidem on 2010-06-10
I've installed Midori on here, and found this (thanks to Google and the Puppy forums):
```
$ ls -l /usr/lib/webkit-1.0-2/libexec
total 132
-rwxr-xr-x 1 root root 116560 2010-04-08 19:00 DumpRenderTree
-rwxr-xr-x 1 root root  13896 2010-04-08 19:00 GtkLauncher

```
The second of the two is the interesting part--it's a very light, extremely minimal Webkit browser, with Javascript.
Be warned, however! It does not support tabs or have a search box, or any sort of intelligent URL handling.
All there is, is the back & forwards buttons, the URL bar, and "Load/Reload".
Downloading is hypothetically possible; I don't know what happens, since it has no dialog or such.
It will get you around the web and logged in to websites.  It will NOT do much of anything for you.
This is in the package libwebkit-1.0-2 
A launcher:
`dlocate -L libwebkit-1.0-2|head -n -1|tail -n -1` 
OR
/usr/lib/webkit-*/libexec/GtkLauncher

---

### Post by Ibidem on 2010-06-15
A few questions on software-
I've dug up the dillo2, gtk1.2, and "off-stable" (GCC3.x, filezilla, etc.) ppas.
I'll enable at least off-stable (ppa:yofel/off-ppa) and gtk1.2 (ppa:adamkoczur/gtk1.2), since gtk1.2 stuff has been used with IceWM for a long time and icecc requires libstdc++5, from off-stable.
Should I have some of these libraries preinstalled?
Should I preinstall icecc, with python-qt and gvim (to make it work)?
Would gtk 1.2-based packages that aren't in the Lucid repos be off-limits (ie, xdialog, geg, danpei from Jaunty)?

Right at the moment I have an extracted SFS (from Lubuntu) that I chrooted into and installed rox-filer, icewm, and a few other things in, while removing LXDE; UCK has a habit of failing to work here, since ubuntu-standard doesn't depend on dialog. 

Ibidem

---

### Post by Ibidem on 2010-06-20
If anyone wants GTK1.2 stuff, I've built 15 packages so far: 
```
$ ls|grep deb
gcrontab_0.8.0-4_i386.deb
geg_1.0.2-6build1_i386.deb
gman_0.9.3-5.1_i386.deb
gtkboard_0.11pre0-11_i386.deb
gtkedit_1.0-0ubuntu1_i386.deb
gtkpool_0.5.0-9_i386.deb
gtranscode_0.3-0.1build1_i386.deb
jscalibrator_1.5.6-0ubuntu3_i386.deb
libjsw2_1.5.6-0ubuntu3_i386.deb
libjsw-dev_1.5.6-0ubuntu3_i386.deb
linpopup_1.2.0-8.3_i386.deb
manedit_0.8.1-4_i386.deb
predict_2.2.3-2ubuntu2_i386.deb
predict-gsat_2.2.3-2ubuntu2_i386.deb
xmms_1.2.11-1_i386.deb

```
The easy way to do it (PROPERLY, NOT INSTALLING BINARIES FROM THE WRONG VERSION) is add the GTK1 PPA, add a "deb-src ....<version> <sections>" line to /etc/apt/sources.list that points to the right version (Dapper, Hardy, Intrepid (for now), or Jaunty), run apt-get update, and then 
```
sudo apt-get build-dep <package short name>
sudo apt-get source --compile <package name>

```
Anyhow, that includes the classic music player XMMS, two games packages (gtkboard is  dozens of games in one package), the fastest GUI editor in Notepad layout (gtkedit), a GUI for controlling cron, a good grapher (geg) (something I had some trouble finding for Linux at first, though there are a number), and manedit, the easiest manpage editor I've seen (But that was last found in Intrepid).

Does anyone else want any of these packages?
I might include xmms, gtkedit, gcrontab, & gtkpool.

---

### Post by MichealH on 2010-06-21
I am interested in making Icebuntu again and maintaining it.

---

### Post by Ibidem on 2010-06-21
Sounds better than I can do.  I am working on a one-shot remix, but...
First, please note Canonical's trademark policy.  To name a derivative *buntu (eg, Icebuntu, Lubuntu, Minibuntu) requires getting permission.  That's why the old Icebuntu became Spri, and Minibuntu became Ubuntu Mini Remix ( or such).  The only way to use "Ubuntu" in the name is by naming it a "Remix."
I suggest the name "UIR"--Ubuntu IceWM Remix.

Additionally, I suggest sticking with fairly standard selections (for IceWM users), and targeting the lighter end of the spectrum.  E.g., rox-filer, Abiword+Gnumeric/Siag, Mtpaint (the Gimp is nice, but heavy).  Don't go to short on features though; xterm is needed, but you might include roxterm or rxvt or the like.

---

### Post by MichealH on 2010-06-21
Yup to what you said, Maybe Ubuntu Ice Remix or is it better to have Ubuntu ICEWM Remix?

When I have it ready to customize then I will start :D

---

### Post by MichealH on 2010-06-23
I have made a Aubergine theme for the Window Decoration... Now I need things to take the GTK theme or... How do i make those themes for Ice WM?

Just because I am building it on The Lucid Lynx I might as well put the new branding in.

---

### Post by Ibidem on 2010-06-23
Take a look at [http://www.icewm.org/themes/index.html](http://www.icewm.org/themes/index.html), and at /usr/share/icewm/themes; each subfolder contains a theme (Theme name is folder name).  It's easiest to start with an existing theme and modify it.
I'm uploading my favorite theme, which I tweaked a bit (IceXimian3, based on IceXimian2 by Hetdegon, which was a copy of the Ximian/Novell default desktop for GNOME from ages back).  It is designed for small screens.  Feel free to examine, rename, and modify; it's GPL thanks to the original being GPL.  (To reduce confusion, please rename any derivatives).
You may prefer to start by digging up one of the other IceWM themes that have been posted here (Icebuntu, [IceGil Grey]("http://ubuntuforums.org/showthread.php?t=323274"), or such) or on the [Puppy IceWM Themes Exchange]("http://www.murga-linux.com/puppy/viewtopic.php?t=20702")  (note that a *.pet is a modified .tar.gz archive, and Puppy's standard package format--open with tar -xzf <name.pet> and ignore errors).
Something similar to Lucid's themes and backgrounds would be acceptable.
But please do not copy Ubuntu's backwards buttons.  Those are  Canonical's error, and should not be inflicted upon IceWM users.

Ibidem

---

### Post by Ibidem on 2010-06-25
I'm thinking about playing around and doing a second version:
UIR Retro edition: Dapper/6.06.1_updated, alternate install.  I'd aim that at the legacy machines that 8.04+ may be too much for.  Dapper still has a year before the repos shut down, and it's the only supported version that will boot in under 64 MB of ram.  It performs decently with that, running IceWM.
Dapper is best for IceWM, with 4 config apps in the repos while 8.04+ has none.
I also know Dapper best, having run it until a year ago.
Of course, a live cd would never boot in 32 MB of ram.  So I'd try an alternate install cd, with a selection of light software...x-window-system-core, dillo, chimera2 (the joys of redundancy--the lightest and ugliest GUI browser in the world), siag, rxvt, links, Mozilla or Firefox 1.5 as backup browser (NOT auto-installed, but on CD), idesk, xfe, emelfm...
Target: Install, boot, & use swap on a Pentium/32M ram/1.5 GB HD.  It'll be slow as molasses on that, but should run quite happily in 64 MB on a PIII@~500 mhz.

Does this sound interesting to anyone?  It'll be "the last shot" for ancient machines, especially the Pentiums.
Ibidem

---

### Post by Ibidem on 2010-07-01
Well, I compiled Siag on here; one of the two libraries it allegedly requires is a replacement for Xaw3d, so I just built everything with the --with-xaw3d=Xaw3d option.  Doesn't quite work right, though... Here's what happens when saving a 
"test" doc:
```
ibid@newbook:~/misc/src$ pw
BadAccess (attempt to access private resource denied)
BadAccess (attempt to access private resource denied)
BadAccess (attempt to access private resource denied)
*** buffer overflow detected ***: pw terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x299390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x2982ca]
/lib/tls/i686/cmov/libc.so.6(+0xe19e8)[0x2989e8]
/usr/local/lib/libMowitz.so.0(+0x14d19)[0x6bfd19]
/usr/lib/libXt.so.6(+0x454cb)[0x16c4cb]
/usr/lib/libXt.so.6(+0x45618)[0x16c618]
/usr/lib/libXt.so.6(_XtTranslateEvent+0x59c)[0x16cecc]
/usr/lib/libXt.so.6(XtDispatchEventToWidget+0x46a)[0x142d2a]
/usr/lib/libXt.so.6(+0x1c56b)[0x14356b]
/usr/lib/libXt.so.6(XtDispatchEvent+0xad)[0x1423fd]
/usr/local/lib/libMowitz.so.0(MwFileselInput+0x41c)[0x6beadc]
pw[0x8054369]
pw[0x8062876]
pw[0x807615b]
pw[0x8079f31]
pw[0x807a052]
pw[0x805fada]
/usr/lib/libXt.so.6(XtCallCallbackList+0x11c)[0x13454c]
/usr/local/lib/libMowitz.so.0(+0x2d8ed)[0x6d88ed]
/usr/local/lib/libMowitz.so.0(+0x2f96c)[0x6da96c]
/usr/lib/libXt.so.6(+0x454cb)[0x16c4cb]
/usr/lib/libXt.so.6(+0x45618)[0x16c618]
/usr/lib/libXt.so.6(_XtTranslateEvent+0x59c)[0x16cecc]
/usr/lib/libXt.so.6(XtDispatchEventToWidget+0x46a)[0x142d2a]
/usr/lib/libXt.so.6(+0x1c56b)[0x14356b]
/usr/lib/libXt.so.6(XtDispatchEvent+0xad)[0x1423fd]
/usr/lib/libXt.so.6(XtAppMainLoop+0x54)[0x1425c4]
pw[0x804f4dd]
pw[0x805a05c]
pw[0x805a16b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x1cdbd6]
pw[0x804da41]
======= Memory map: ========
00110000-00125000 r-xp 00000000 08:0d 298054     /usr/lib/libXmu.so.6.2.0
00125000-00126000 r--p 00014000 08:0d 298054     /usr/lib/libXmu.so.6.2.0
00126000-00127000 rw-p 00015000 08:0d 298054     /usr/lib/libXmu.so.6.2.0
00127000-00176000 r-xp 00000000 08:0d 298048     /usr/lib/libXt.so.6.0.0
00176000-00177000 r--p 0004e000 08:0d 298048     /usr/lib/libXt.so.6.0.0
00177000-0017a000 rw-p 0004f000 08:0d 298048     /usr/lib/libXt.so.6.0.0
0017a000-0018d000 r-xp 00000000 08:0d 792430     /lib/tls/i686/cmov/libnsl-2.11.1.so
0018d000-0018e000 r--p 00012000 08:0d 792430     /lib/tls/i686/cmov/libnsl-2.11.1.so
0018e000-0018f000 rw-p 00013000 08:0d 792430     /lib/tls/i686/cmov/libnsl-2.11.1.so
0018f000-00191000 rw-p 00000000 00:00 0 
00191000-001b5000 r-xp 00000000 08:0d 792427     /lib/tls/i686/cmov/libm-2.11.1.so
001b5000-001b6000 r--p 00023000 08:0d 792427     /lib/tls/i686/cmov/libm-2.11.1.so
001b6000-001b7000 rw-p 00024000 08:0d 792427     /lib/tls/i686/cmov/libm-2.11.1.so
001b7000-0030a000 r-xp 00000000 08:0d 792420     /lib/tls/i686/cmov/libc-2.11.1.so
0030a000-0030b000 ---p 00153000 08:0d 792420     /lib/tls/i686/cmov/libc-2.11.1.so
0030b000-0030d000 r--p 00153000 08:0d 792420     /lib/tls/i686/cmov/libc-2.11.1.so
0030d000-0030e000 rw-p 00155000 08:0d 792420     /lib/tls/i686/cmov/libc-2.11.1.so
0030e000-00311000 rw-p 00000000 00:00 0 
00311000-00329000 r-xp 00000000 08:0d 268984     /usr/lib/libxcb.so.1.1.0
00329000-0032a000 r--p 00017000 08:0d 268984     /usr/lib/libxcb.so.1.1.0
0032a000-0032b000 rw-p 00018000 08:0d 268984     /usr/lib/libxcb.so.1.1.0
0032b000-0032d000 r-xp 00000000 08:0d 792426     /lib/tls/i686/cmov/libdl-2.11.1.so
0032d000-0032e000 r--p 00001000 08:0d 792426     /lib/tls/i686/cmov/libdl-2.11.1.so
0032e000-0032f000 rw-p 00002000 08:0d 792426     /lib/tls/i686/cmov/libdl-2.11.1.so
0032f000-00331000 r-xp 00000000 08:0d 297755     /usr/lib/libXau.so.6.0.0
00331000-00332000 r--p 00001000 08:0d 297755     /usr/lib/libXau.so.6.0.0
00332000-00333000 rw-p 00002000 08:0d 297755     /usr/lib/libXau.so.6.0.0
00333000-00337000 r-xp 00000000 08:0d 297761     /usr/lib/libXdmcp.so.6.0.0
00337000-00338000 r--p 00003000 08:0d 297761     /usr/lib/libXdmcp.so.6.0.0
00338000-00339000 rw-p 00004000 08:0d 297761     /usr/lib/libXdmcp.so.6.0.0
00339000-00356000 r-xp 00000000 08:0d 784954     /lib/libgcc_s.so.1
00356000-00357000 r--p 0001c000 08:0d 784954     /lib/libgcc_s.so.1
00357000-00358000 rw-p 0001d000 08:0d 784954     /lib/libgcc_s.so.1
003b6000-003cb000 r-xp 00000000 08:0d 298036     /usr/lib/libICE.so.6.3.0
003cb000-003cc000 r--p 00014000 08:0d 298036     /usr/lib/libICE.so.6.3.0
003cc000-003cd000 rw-p 00015000 08:0d 298036     /usr/lib/libICE.so.6.3.0
003cd000-003cf000 rw-p 00000000 00:00 0 
004a9000-004c4000 r-xp 00000000 08:0d 784953     /lib/ld-2.11.1.so
004c4000-004c5000 r--p 0001a000 08:0d 784953     /lib/ld-2.11.1.so
004c5000-004c6000 rw-p 0001b000 08:0d 784953     /lib/ld-2.11.1.so
00681000-00685000 r-xp 00000000 08:0d 301409     /usr/lib/libXfixes.so.3.1.0
00685000-00686000 r--p 00003000 08:0d 301409     /usr/lib/libXfixes.so.3.1.0
00686000-00687000 rw-p 00004000 08:0d 301409     /usr/lib/libXfixes.so.3.1.0
006ab000-006f5000 r-xp 00000000 08:0d 263043     /usr/local/lib/libMowitz.so.0.3.1
006f5000-006f6000 ---p 0004a000 08:0d 263043     /usr/local/lib/libMowitz.so.0.3.1
006f6000-006f7000 r--p 0004a000 08:0d 263043     /usr/local/lib/libMowitz.so.0.3.1
006f7000-006ff000 rw-p 0004b000 08:0d 263043     /usr/local/lib/libMowitz.so.0.3.1
006ff000-00710000 rw-p 00000000 00:00 0 
007c2000-008db000 r-xp 00000000 08:0d 302727     /usr/lib/libX11.so.6.3.0
008db000-008dc000 r--p 00118000 08:0d 302727     /usr/lib/libX11.so.6.3.0
008dc000-008de000 rw-p 00119000 08:0d 302727     /usr/lib/libX11.so.6.3.0
008de000-008df000 rw-p 00000000 00:00 0 
00922000-00925000 r-xp 00000000 08:0d 785065     /lib/libuuid.so.1.3.0
00925000-00926000 r--p 00002000 08:0d 785065     /lib/libuuid.so.1.3.0
00926000-00927000 rw-p 00003000 08:0d 785065     /lib/libuuid.so.1.3.0
00976000-009b9000 r-xp 00000000 08:0d 319054     /usr/lib/libXaw3d.so.6.1
009b9000-009ba000 r--p 00042000 08:0d 319054     /usr/lib/libXaw3d.so.6.1
009ba000-009c0000 rw-p 00043000 08:0d 319054     /usr/lib/libXaw3d.so.6.1
009c0000-009d2000 rw-p 00000000 00:00 0 
00a14000-00a1d000 r-xp 00000000 08:0d 792423     /lib/tls/i686/cmov/libcrypt-2.11.1.so
00a1d000-00a1e000 r--p 00008000 08:0d 792423     /lib/tls/i686/cmov/libcrypt-2.11.1.so
00a1e000-00a1f000 rw-p 00009000 08:0d 792423     /lib/tls/i686/cmov/libcrypt-2.11.1.so
00a1f000-00a46000 rw-p 00000000 00:00 0 
00b89000-00b97000 r-xp 00000000 08:0d 265095     /usr/lib/libXext.so.6.4.0
00b97000-00b98000 r--p 0000d000 08:0d 265095     /usr/lib/libXext.so.6.4.0
00b98000-00b99000 rw-p 0000e000 08:0d 265095     /usr/lib/libXext.so.6.4.0
00bfe000-00bff000 r-xp 00000000 00:00 0          [vdso]
00c5e000-00c65000 r-xp 00000000 08:0d 298042     /usr/lib/libSM.so.6.0.1
00c65000-00c66000 r--p 00006000 08:0d 298042     /usr/lib/libSM.so.6.0.1
00c66000-00c67000 rw-p 00007000 08:0d 298042     /usr/lib/libSM.so.6.0.1
00cb8000-00cc0000 r-xp 00000000 08:0d 306093     /usr/lib/libXcursor.so.1.0.2
00cc0000-00cc1000 r--p 00007000 08:0d 306093     /usr/lib/libXcursor.so.1.0.2
00cc1000-00cc2000 rw-p 00008000 08:0d 306093     /usr/lib/libXcursor.so.1.0.2
00d03000-00d0b000 r-xp 00000000 08:0d 301434     /usr/lib/libXrender.so.1.3.0
00d0b000-00d0c000 r--p 00007000 08:0d 301434     /usr/lib/libXrender.so.1.3.0
00d0c000-00d0d000 rw-p 00008000 08:0d 301434     /usr/lib/libXrender.so.1.3.0
00e15000-00e24000 r-xp 00000000 08:0d 298060     /usr/lib/libXpm.so.4.11.0
00e24000-00e25000 r--p 0000e000 08:0d 298060     /usr/lib/libXpm.so.4.11.0
00e25000-00e26000 rw-p 0000f000 08:0d 298060     /usr/lib/libXpm.so.4.11.0
08048000-0808a000 r-xp 00000000 08:0d 293646     /usr/local/bin/pw
0808a000-0808b000 r--p 00041000 08:0d 293646     /usr/local/bin/pw
0808b000-0808d000 rw-p 00042000 08:0d 293646     /usr/local/bin/pw
0808d000-08091000 rw-p 00000000 00:00 0 
09431000-097c8000 rw-p 00000000 00:00 0          [heap]
b7628000-b7662000 rw-p 00000000 00:00 0 
b76df000-b76e0000 rw-p 00000000 00:00 0 
b76e0000-b771f000 r--p 00000000 08:0d 291777     /usr/lib/locale/en_US.utf8/LC_CTYPE
b771f000-b783d000 r--p 00000000 08:0d 292474     /usr/lib/locale/en_US.utf8/LC_COLLATE
b783d000-b787d000 rw-p 00000000 00:00 0 
b787e000-b787f000 r--p 00000000 08:0d 272687     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b787f000-b7880000 r--p 00000000 08:0d 292476     /usr/lib/locale/en_US.utf8/LC_TIME
b7880000-b7881000 r--p 00000000 08:0d 292478     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7881000-b7882000 r--p 00000000 08:0d 292480     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7882000-b7883000 r--p 00000000 08:0d 272693     /usr/lib/locale/en_US.utf8/LC_PAPER
b7883000-b7884000 r--p 00000000 08:0d 272694     /usr/lib/locale/en_US.utf8/LC_NAME
b7884000-b7885000 r--p 00000000 08:0d 292482     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7885000-b7886000 r--p 00000000 08:0d 292484     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7886000-b7887000 r--p 00000000 08:0d 272697     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7887000-b788e000 r--s 00000000 08:0d 310099     /usr/lib/gconv/gconv-modules.cache
b788e000-b788f000 r--p 00000000 08:0d 292486     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b788f000-b7891000 rw-p 00000000 00:00 0 
bfe03000-bfe18000 rw-p 00000000 00:00 0          [stack]
Aborted

```
The rest are similar.  This is compiling 3.6.1 on Lucid--it seems that the developer has an ancient system.

Ted, the old RTF editor, is solid on Jaunty.  I also dug up a light spreadsheet that acts (SOMEWHAT) like Excel: [ABS]("http://home.scarlet.be/%7Epin01858/download.html") (used in Puppy 1.0.x).  It's from 2001, GPL, Athena widget set.  Cannot compile on Lucid, after changing -lXaw to -lXaw3d it gets further, but fails.  The binary (ELF for Linux 2.2) fails at first, but the solution is ```
sudo ln -s /usr/lib/*libXaw3d*.*so*.*6* /usr/lib/*libXaw*.*so*.*6*
```.
Then it runs pretty well.  I'd say it's light, at  800 KB - 2.5 MB RSS and VM-Size under 15 MB, when using the heaviest demos.  It does not have the standard shortcut keys.

---

### Post by Tech2077 on 2010-07-11
Is this project actually moving forward. The ppa is empty and i can't find anything other than a few obscure small projects that seem to be ubuntu mini remix put through uck with a few extra applications installed. And for the original concept, i can't find anything newer than 2008.

---

### Post by Ibidem on 2010-07-12
Well, it's perhaps creeping forwards--but not very quick.

As far as "a few extra applications installed", that is the primary difference between my standard base system and ubuntu-standard (which is what Ubuntu Mini Remix includes).  So it's not absurd to use that sort of configuration.
The original concept is "Ubuntu with IceWM included as default WM, and a light, minimal set of apps".
If it drops the IceWM part, it ceases to be "Icebuntu".  
The "light, minimal set of apps" part is the only sensible course for a remix/distro aimed at IceWM users.  I don't think that most IceWM users would appreciate having Nautilus, Audacity, OpenOffice, the Gimp, Gedit, Evolution, and every other piece of bloatware that Canonical or the Gnome developers think should be a default.  IceWM is my own WM of choice because it is light, fast, and minimal.  I add what I want, rather than trying to figure out what bloat can be removed.  Most other IceWM users, from all I understand, have similar preferences.
(You seem to have missed Spri, and the special repository for it.  Although current development is based on JWM, they had a Jaunty version with IceWM, the IceWM control panel, and such.)

---

### Post by Ibidem on 2010-08-23
Well, a little news:
Lucid Puppy 5.1 includes IceWM as alternate window manager; it's almost what I'd hope for with an "IceBuntu".
JWM/IceWM (just delete JWM, IMHO)
Rox-filer
urxvt
Abiword, Gnumeric, Mtpaint
Mhwaveedit (audio editor), Gnucash, Homebank (remove these?)
etc.

Browser chooser, Netsurf as standard browser.

---

### Post by Mark76 on 2010-11-22
Sorry to be a thread resurrector, but seeing as how the project website is dead I assume Spri is too.

---

### Post by PissedApache on 2010-11-22
I use slitaz on my old pentium II 300Mhz toughbook now :D

---

### Post by Ibidem on 2011-03-17
Well, I'm back...or my computer that had everything is, rather.
In ~/misc/src/ubuntu-icewm-remix/DEBIAN/control:
```
Package: ubuntu-icewm-remix-desk
Version: 0.10
Section: universe
Priority: optional
Architecture: all
Depends: icewm, xinit, menu, gvim, rxvt-unicode, seamonkey-browser, cups, hplip
Installed-Size:
Maintainer: Ibidem
Description: A light IceWM desktop (metapackage)
 Ubuntu-icewm-remix-desk provides a core, semi-functional desktop.  Office suite is not provided--alternatives include OpenOffice, "Gnome Office", or Softmaker (proprietary).

```Please note that this is FOR REVIEW.  Hammer on app choice all you want, that's the purpose.

In my own PPA ([https://launchpad.net/~ibid-ag/+archive/oldgtk1]("https://launchpad.net/%7Eibid-ag/+archive/oldgtk1")), I've got nextaw, oleo (a Lesstif/X/curses spreadsheet), xmms, a slightly changed icewm-themes package, and a few more things (mostly gtk1.2).
nextaw is needed for Siag to work right--it compiles with other Xaw* variants, but the clipboard handling is particular to nextaw, presumably causing the crash I found. 
I might try getting Oleo+Ted for office, depend on geg  & xcalc (calculators: one graphing, one scientific), 
( wvware || catdoc) && o3read, 
Sylpheed || Claws || Mutt, 
Xpaint || mtpaint
xpdf || mupdf
xli || xloadimage || danpei
gv
suggest abiword, gnumeric

etc.
What would you like to see?
Ibidem

---

### Post by markp1989 on 2011-06-07
I know this is an old thread.


today I was tidying  and I found a 512mb usb drive with a bootable image of Icebuntu 2.2 on it from 2007 when I was working on it. 

I just took a DD of it and uploaded it to my dropbox, a share link is here if any one wants to copy it to a usb drive to give it a go for nostalgia. 

just gave it a go on my Asus UL30A and was surprised that it worked mostly, Wifi wasn't working, but I cant remember if wireless networking was implemented in that release or not. 

Dropbox Link : [http://db.tt/6LXoBb7](http://db.tt/6LXoBb7)

---

