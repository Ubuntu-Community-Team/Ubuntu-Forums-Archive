---
title: "Headless server won't load GUI..."
date: 2010-05-03
forum: Server Platforms
---

### Post by michaelslarsen on 2010-05-03
I have an Dell 755, and I have installed Ubuntu 10.4 server+Gnome on it, everything works fine.  I have it auto login, and run Azureus/Vuse at startup (so it can be a headless Bit Torrent server), it works perfectly.  As soon as I try to go headless (no keyboard/mouse/monitor) the machine boots fine (I can SSH / FreeNX to the machine) but none of the GUI/apps load.  What I think is happening is that when it boots without a monitor attached it does not load any of the X11 stuff.  I need it to.  It worked in Ubuntu 9.04 just fine, but now with 10.4 it is a no-go.  Does anyone know how to force the X11/GUI to load when there are no monitors/hardware attached?  This is the one thing standing in my was of getting Windows out of my house.

Any help would be greatly appreciated!

---

### Post by Proudly Dutch on 2010-05-03
I ran into the same problem after upgrading from 9.10 Server to 10.4 Server.  Tried evey trick or possible solution I could find but in the end none of them worked.

I just gave up in the end (because I needed the monitor for a desktop machine) and reinstalled 9.10 last night.
Server is running headless again.

Ubuntu developers: FIX THIS!   A Server should be able to run headless!!!!

I like 10.4 a lot, but not be able to run headless with GNOME just put me of.

---

### Post by windependence on 2010-05-04
Headless would imply GUIless also. Learn the CLI <flame on>

-Tim

---

### Post by Drenriza on 2010-05-04
Why not use the server with pure Command line commands?
 
Thats how i maintain my
 
apache2.
Mysql.
Joomla.
php5.
dhcp3.
 
services.

---

### Post by tgalati4 on 2010-05-04
You just need the xserver-xorg libraries, you don't really need the xserver running.  Perhaps there was a meta-package change from Karmic to Lucid so that you didn't get all of the xorg libraries loaded during install.

Try the following on Karmic server:

cd
locate xorg
locate xorg > files_needed.txt

Now boot into Lucid
locate xorg

Compare the files_needed.txt list with Lucid and determine what is missing.

I agree that commandline server management is not difficult.  Most services also have web-based management pages as well.  But everyone uses servers differently.  I still have a Dapper Drake desktop machine running 24/7 that I use for several services.  It's handy to have remote xsessions to do things like play last.fm music with gui, feed photoframes with webilder (you need a desktop for that), xload displays, etherape and other graphical network monitoring.  So it's nice to have the gui, for the cost of several hundred megabytes of libraries and 9% CPU cycles if you have to run the desktop locally.  For a headless server, you just need the xorg libraries to get remote gui capability.

---

### Post by Bob P on 2010-05-04
I agree with the opinion that a server should be able to run headless.  Even though headless operation is a common objective, its uncommon to find headless configuration as an install option ... even on the enterprise class products like RHEL.  To perform a headless install everyone makes you jump through some hoops.

I agree that a server doesn't necessarily require a GUI.  I do all of my server administration via the CLI.  But to be fair, headless doesn't necessarily force you to be GUI less.  Its entirely possible to have a GUI by running the X11 client on the headless server and X11 server on the remote terminal.  X11 does that sort of thing quite well,  although most people don't think of using X11 that way.

WRT having a GUI interface in the absence of X11, the web browser based solutions immediately come to mind.  Have you looked into Webmin?

---

### Post by ghost_ryder35 on 2010-05-04
> **michaelslarsen said:**
> I have an Dell 755, and I have installed Ubuntu 10.4 server+Gnome on it, everything works fine.  I have it auto login, and run Azureus/Vuse at startup (so it can be a headless Bit Torrent server), it works perfectly.  As soon as I try to go headless (no keyboard/mouse/monitor) the machine boots fine (I can SSH / FreeNX to the machine) but none of the GUI/apps load.  What I think is happening is that when it boots without a monitor attached it does not load any of the X11 stuff.  I need it to.  It worked in Ubuntu 9.04 just fine, but now with 10.4 it is a no-go.  Does anyone know how to force the X11/GUI to load when there are no monitors/hardware attached?  This is the one thing standing in my was of getting Windows out of my house.

Any help would be greatly appreciated!

are you sure its not loading?  when you freenx in you are connecting to a different X11 session, therefore Azureus and whatever else wont be running in that instance.  You can ps -ef | grep -i azureus to see if it is running

---

### Post by Groodles on 2010-05-04
I had the same problem, and it was because of my Intel grfx card not being able to detect a monitor and therefore not being able to pick a screen resolution to use.  The result was that X would default to failsafe mode and wait for keyboard input.

My solution was to force (via xorg.conf) the X11 session to use the "vesa" driver.  To do that I also had to disable KMS support (which is on by default in Lucid) because KMS does not support the vesa driver.

Here's how to disable KMS:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

And here's a copy of my xorg.conf
```
Section "Device"
        Identifier      "Onboard Intel Graphics"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       31-101
        VertRefresh     60-160
EndSection

Section "Screen"
        Identifier      "Basic Screen"
        Monitor         "Generic Monitor"
        Device          "Onboard Intel Graphics"
        SubSection "Display"
            Modes		"1024x768"
        EndSubSection
EndSection

```

---

### Post by tgalati4 on 2010-05-04
That's an edge case that I hadn't thought of:  kernel-mode-setting.

You need VESA for low-level graphics, but VESA is not supported by KMS!

So that makes perfect sense:  turn off KMS then use VESA.

That's regression.

---

### Post by arrrghhh on 2010-05-04
Again, why are we running GUI's on our so-called "headless" servers?  Not very headless with a GUI...

---

### Post by tgalati4 on 2010-05-04
There are lots of reasons for a home server.  Say you want to update your podcast feeds using gpodder (a graphical podcast downloader).  You have your mp3 player plugged into your headless server via USB so it charges.  You are on a laptop somewhere else in the house, you can open a terminal, ssh -2 -Y and have gpodder running remotely on your laptop.  Update feeds, download podcasts, sync to your player, and unmount it.  

If your headless server is hooked to your home stereo system, you can bring up vagalume (remotely) and stream last.fm.  

You can even bring up gnome-panel remotely and have an almost-complete desktop experience.  It's faster and more secure than VNC.

For business/enterprise services, a headless server is just that--headless and management though the web or through the commandline is more common.

---

### Post by arrrghhh on 2010-05-04
I do pretty much all of those things without a GUI.  That's my point.  I have a home server that's headless - but no X no Gnome, none of that bloat.

I guess I think headless I think no GUI.  But it's probably just more meaning that there's no keyboard/mouse/monitor hooked up.  Same as in my case, just network and power.

---

### Post by Groodles on 2010-05-04
> **arrrghhh said:**
> I do pretty much all of those things without a GUI.  That's my point.  I have a home server that's headless - but no X no Gnome, none of that bloat.

I guess if you're worried about "bloat" it's because you're running on limited resources.  However if you have plenty of resources then it's not a problem.

Someone also once said that unused resources are wasted resources.

> I guess I think headless I think no GUI. But it's probably just more meaning that there's no keyboard/mouse/monitor hooked up. Same as in my case, just network and power.

I take "headless" to mean lack of keyboard/mouse/monitor.  GUI doesn't come into the description.

---

### Post by tgalati4 on 2010-05-04
Yea, but you can't see album art when you are streaming through a remote connection, or see podcast descriptions when updating.  Certainly there are commandline ways to do anything in linux, but when you are remotely logged into a server, it's nice to have most of your apps available as well.  It's nice to have xload running when you are loading up your server with video transcoding or music processing.  I still have a Dapper Drake desktop machine running 24/7 because it works and I have set up several useful services on it.  I only run the xserver when I need to, but otherwise I can bring up graphical apps remotely and that I find is quite helpful.  Want to read a pdf remotely?  View a picture remotely?  Certainly you can set up a mount point and do those things through the commandline, but from a workflow standpoint, a familiar gui rocks.

---

### Post by Revelator7MD on 2010-05-04
Just confirming that this indeed worked for me as well. Upgraded from 9.10 to 10.4, but then VNC with GDM stopped working. Suspecting GDM wasn't loading properly, I followed [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting), where I ran the command:

```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
```(in my case I have a Radeon card)
then rebooted. Worked! :D

---

### Post by arrrghhh on 2010-05-04
> **tgalati4 said:**
> Yea, but you can't see album art when you are streaming through a remote connection, or see podcast descriptions when updating.  Certainly there are commandline ways to do anything in linux, but when you are remotely logged into a server, it's nice to have most of your apps available as well.  It's nice to have xload running when you are loading up your server with video transcoding or music processing.  I still have a Dapper Drake desktop machine running 24/7 because it works and I have set up several useful services on it.  I only run the xserver when I need to, but otherwise I can bring up graphical apps remotely and that I find is quite helpful.  Want to read a pdf remotely?  View a picture remotely?  Certainly you can set up a mount point and do those things through the commandline, but from a workflow standpoint, a familiar gui rocks.

I guess you've never used a web interface or used fstab to mount NFS shares?!?

If you guys want to use a GUI, by all means use the crutch.  I really wanted to learn how to administer a system without a GUI (I always depended on one before...) and it taught me a TON about command-line administration.  So I don't have to depend on a GUI to do anything any longer!!  The server is a server, I see GUI's as a thing client machines need.

To each his own, just seems silly to me.  Install ubuntu-desktop if you want a GUI, ubuntu-server is supposed to be just that, for servers.

For me, the knowledge I gained by forcing myself to setup the server without a GUI is priceless.  Now I don't need to depend on something that I (and others, obviously) have had break on them.

---

### Post by windependence on 2010-05-04
> **arrrghhh said:**
> I guess you've never used a web interface or used fstab to mount NFS shares?!?

If you guys want to use a GUI, by all means use the crutch.  I really wanted to learn how to administer a system without a GUI (I always depended on one before...) and it taught me a TON about command-line administration.  So I don't have to depend on a GUI to do anything any longer!!  The server is a server, I see GUI's as a thing client machines need.

To each his own, just seems silly to me.  Install ubuntu-desktop if you want a GUI, ubuntu-server is supposed to be just that, for servers.

For me, the knowledge I gained by forcing myself to setup the server without a GUI is priceless.  Now I don't need to depend on something that I (and others, obviously) have had break on them.
100% agree here. Think security. Think power consumption. I'm sure there are more reasons I forgot. 

If you really want to set up a home server, then Ubuntu Desktop is your product. There is nothing in the server kernel that will help you download torrents or stream media or anything else you want to do unless you are running your server in a virtualized environment which you haven't stated. The desktop product will do everything you need without skipping a beat and will probably hardly even use any CPU. The server distro is for production environments and is tuned to that goal. This is why a GUI is NOT included with the server product. Canonical specifically touts it as a security advantage and I agree. 

It would not hurt you to learn how things work under the hood though, in case your GUI crutch doesn't work and you end up reformatting because you don't know how to recover the GUI from the command line. You'll feel better about it too having learned something new!

-Tim

---

### Post by Bob P on 2010-05-04
i guess i'm an old fart in that i remember the days before the first GUI.  but then i remember the days before DOS and CP/M too.  having cut my teeth on the CLI, I've never used a GUI for server administration.  I'm not too proud to say that using a CLI just for the sake of saying that you know enough to use a CLI is synonymous to saying that you want to do things the hard way just because you can.

I've been doing GUI-less servers for a long, long time.  I've never used a GUI because I was always one of the people who thought that GUIs were crutches for wimps.  Then I learned how wrong I was.

Last weekend I was setting up a new SMB server on our protected LAN.  Other SMB servers are already there that exist as PDCs, and adding additional SMB servers to that type of environment can be a little tricky -- especially if the servers are running different versions of Samba, as the configuration file syntax changes from version to version.  So there I was, beating my head against the wall in text mode, trying to configure a new SMB server that didn't want to play nicely with everyone else because I wasn't aware of a new syntax change.  Of course, I was doing this via a CLI text editor and progress was slow.

When I was chatting with a sysadmin friend at Bank of America he asked me why I wasn't using the SMB configuration tool that's built into Red Hat's minimal server GUI.  So I gave it a try -- BAM!  A few mouse clicks to set up the configuration and the GUI app generated the proper config files using the proper syntax for that SMB version.  The server was up and running in less than 5 minutes.  It was fast, it was painless, and with the GUI tool I got the config right on its first attempt.  All that I had to do was check some boxes.  Wow.

There are good reasons to use some of the GUI-based tools that come with some of the enterprise class server packages.  They do make your life easier by improving your productivity.  You're not a wimp on crutches if you use them.

---

### Post by arrrghhh on 2010-05-05
> **Bob P said:**
> There are good reasons to use some of the GUI-based tools that come with some of the enterprise class server packages.  They do make your life easier by improving your productivity.  You're not a wimp on crutches if you use them.

I agree with this as well.  I use Webmin to setup things like Samba, it makes things go much, much faster.

However, for day-to-day stuff, I like the CLI better.  Plus, the knowledge it afforded me is amazing because I was always used to a GUI - I was tired of clicking on buttons, not knowing what they were changing, and sometimes misbehaving.  I just feel much more confident that the command I'm submitting is actually doing what I want it to, as opposed to a button that does who knows what.

I equate it to knowing how to drive a manual or not knowing how to drive a manual.  Either way, you can drive a car that's an automatic, but if you don't know how to drive a manual and your buddy is drunk... you're screwed.  If your X blows up from an update, and you don't know some CLI commands... You're screwed :D

---

### Post by ricardoph on 2010-07-24
For those who are afraid of command lines... and want their server to run like a regular desktop, you may wann try this (copied from a topic I started)

1) Connect a monitor for the booting in case you're sure you won't have any power issues during operation...
2) A little more complex, but the solution that works under any  conditions, is to create a dummy monitor, with a few resistance and a  female DB25 connector, you can fool the video card and tell it a SVGA  monitor is hooked up. I took the instructions from this post [http://www.xtremesystems.org/forums/showthread.php?t=200444 ]("http://www.xtremesystems.org/forums/showthread.php?t=200444")

The thing worked like a charm, and it only costs less than a dollar.....

:grin:

So, yes, the people afraid of command lines, can still have their server and manage it like a regular desktop....

---

### Post by milksop on 2010-08-02
> **Groodles said:**
> I had the same problem, and it was because of my Intel grfx card not being able to detect a monitor and therefore not being able to pick a screen resolution to use.  The result was that X would default to failsafe mode and wait for keyboard input.

My solution was to force (via xorg.conf) the X11 session to use the "vesa" driver.  To do that I also had to disable KMS support (which is on by default in Lucid) because KMS does not support the vesa driver.

Here's how to disable KMS:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

And here's a copy of my xorg.conf
```
Section "Device"
        Identifier      "Onboard Intel Graphics"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       31-101
        VertRefresh     60-160
EndSection

Section "Screen"
        Identifier      "Basic Screen"
        Monitor         "Generic Monitor"
        Device          "Onboard Intel Graphics"
        SubSection "Display"
            Modes		"1024x768"
        EndSubSection
EndSection

```

Just wanted to confirm that this worked for me. Kind of a pain for servers that have been happily running headless for a long time though.

Thanks Groodles! Much appreciated.

---

### Post by arrrghhh on 2010-08-03
Not sure why a 'headless' server would have a GUI in the first place...

Yet another reason I like running without a GUI!  Less headaches (once everything is setup), whew.

---

### Post by erk on 2010-08-03
Normally all that's required is to plug some sort of adapter into the video card to make it think it has a monitor. I use something like a DVI -> VGA converter that often comes with the video card and that seems to work.

There are also some tricks linking a couple of pins together on the video socket to fool the card. Just google on it, not a new problem, and not specific to Ubuntu.

---

### Post by Chunder on 2010-08-03
There seem to be a lot of experienced folk out there who are pooh-pooing running a "headless" machine (be it a server or not) with a GUI, so I'd just like to wade in with a "real world" reason why people (me! my wife!) have a need to do this. Note in both cases I'm talking about 10.04

1) I have a Mythbuntu server upstairs that I'm trying to get set up so that it can sleep and wake up on demand - either upon a connection from a remote frontend, or when a recording is due. I want to have access to the GUI so that I can (occasionally) get in and see what's going on - I've tried ssh-ing (ssh -X user@server) from my Mac mini, and although this mostly works, I can't run things like mythtv-setup or some of the more familiar Mythbuntu applications (graphical corruption mostly).
Sure, I can do some (or perhaps most) of the things by command line, but that means relearning a whole bunch of stuff - and ignoring all the great stuff that the Mythbuntu team have done in making the system easy to use.
VNC seems like the only sensible solution (it's only accessed from the local network) but trying to boot into a GUI when the monitor is disconnected has been the devil's own job.

2) The Mythfrontend is an Acer Revo 3610 in the lounge, hooked up by HDMI to a TV via an amplifier/receiver. If the frontend is booted before the amplifier is switched on, then no monitor is detected and I get no display (presumably the failsafe mode either doesn't operate over HDMI or is in a resolution unsupported by the TV).
Unfortunately this kind of thing happens a lot - all of the devices are controlled by a Logitech Harmony remote, where selecting the "Watch MythTV" activity should start all the devices in the correct order automatically... unless the remote is blocked or isn't quite pointing at a device, in which case the IR signal is missed, and the device doesn't switch on. 
In this situation, it is imperative that the Mythfrontend continues to boot into the GUI - using the normal 1920x1080@50hz resolution - so that when the amp is switched on, the usual MythTV interface is displayed.
As it stands, this has caused so many problems already that I've disabled the option to shut the frontend down. Small power wastage vs wifely ire isn't really much contest!

Hopefully this gives a bit more clarity on why this may be needed - the GUI isn't always just a crutch; yes, no a true server machine you may be able to do everything by command line or remote X login, but it's not always the right solution.

Personally, I've waded through all sorts of options - including everything in this thread - but I still can't get it to work. Fortunately (?!) my years of fiddling with Myth/Ubuntu has inured me to the sheer frustration of not being able to get things done that should - on the face of it - be simple. 
I'll keep plugging away and researching more - seemingly the only recommended course of action whenever you hit a problem; eventually you'll find one small cryptic reference that makes it all work - but if anyone has any bright ideas (and can get over their deep-seated loathing of having a "headless" server that still runs a GUI!) then pleasepleasepleasehelp!

---

### Post by arrrghhh on 2010-08-03
LOL I do have a strange hatred for 'headless' servers running a GUI.  I still don't get why on the myth backend you need to run a GUI... I understand on the frontend why you need a GUI tho.

Have you considered an IR blaster/UHF setup for your Harmony?  I know it's not really the solution you're looking for, but those pretty much eliminate issues with the remote being blocked, etc.  I'm just not sure how to 'trick' the video card into thinking there's always something plugged in with the correct resolution... perhaps a custom x11 configuration file?

Also, I haven't done a myth backend only setup, does that not include a GUI out-of-the-box?  I thought they ran XFCE, but maybe that's only on the frontend...

---

### Post by NTolerance on 2010-08-05
This thread disappoints.  Seriously.

I've got a Ubuntu 10.04 desktop system connected to my HDTV.  I maintain it remotely mainly through SSH and the CLI.  

This includes things like upgrading to new kernels with apt-get.  When you upgrade the kernel you need to reboot.  So I issue a "shutdown -r now" via the CLI and my system reboots and then fails to start X because my HDTV is being used to play back video from one of several other devices connected to it.

A user should be able to reboot via the CLI with no monitor connected, then connect a monitor after the fact and watch a video with XBMC/MythTV/etc.

Don't think for a second that you can anticipate all use cases.  It's not cool to tell people how to use their systems.  Give people the benefit of the doubt.

---

### Post by arrrghhh on 2010-08-05
> **NTolerance said:**
> Don't think for a second that you can anticipate all use cases.  It's not cool to tell people how to use their systems.  Give people the benefit of the doubt.

Not tryin to second guess anyone, it's just when most people run into problems trying to put X and Gnome in pieces onto a server-based distro, it just seems silly.  Run Ubuntu-Desktop, like you do.

> **NTolerance said:**
> This includes things like upgrading to new kernels with apt-get. When you upgrade the kernel you need to reboot. So I issue a "shutdown -r now" via the CLI and my system reboots and then fails to start X because my HDTV is being used to play back video from one of several other devices connected to it.

Yea, that is a little disappointing that something like this would happen.  That begs the question, can you boot the system at all without a monitor "plugged in"?  There's gotta be a way in xorg.conf or something to trick it into thinking there's always a monitor plugged in with a certain resolution...

---

### Post by PushinNshovinMe on 2010-08-06
[rant] I am new to Linux and have found the Ubuntu forums to be largely unhelpful.  Most posters seem to only have one thing in mind at anytime and provide terribly shallow answers.  It seems like you pretty much just have to learn everything on your own, using those vague answers as direction to go in.  I do hope to create a guide on how I created my media server with more specifics of my system and an easier to follow step-by-step for people like me who really don't know enough command-line to understand most vague answers on here. [/rant]
 
 
To have a GUI that you want to monitor from a Remote Desktop connection, I just used Webmin 1.510.
 
sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.510_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.510_all.deb)
 
sudo dpkg -i webmin_1.510_all.deb
 
sudo apt-get install -f
 
I have had trouble with this not downloading the required : libmd5-perl_2.03-1_all.deb file, here is a working address: 
 
sudo wget [http://ftp.debian.org/debian/pool/main/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb](http://ftp.debian.org/debian/pool/main/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb)
 
 
Once installed you can access it in your browser: [https://*ip.of.your.server*:10000/]("https://ip.of.your.server:10000/")
Log in with your server user and password, Go to >System, then 'Bootup and Shutdown', then check off the 'x11-common' action and Click the [Start On Boot] button at the bottom of the page.
 
 
Hope that helps, it's what worked for me.

---

### Post by Chunder on 2010-08-06
> **arrrghhh said:**
> That begs the question, can you boot the system at all without a monitor "plugged in"?  There's gotta be a way in xorg.conf or something to trick it into thinking there's always a monitor plugged in with a certain resolution...

That's all that we want (well, all that I want. For now. :) ) - something that's not a hardware hack that can tell X (or gdm, or whatever) not to bother looking for a monitor, but to just go away and create the X screen as defined in the xorg.conf regardless... kind of an "I know there's no monitor so override the warnings automatically" switch.

---

### Post by arrrghhh on 2010-08-06
> **Chunder said:**
> That's all that we want (well, all that I want. For now. :) ) - something that's not a hardware hack that can tell X (or gdm, or whatever) not to bother looking for a monitor, but to just go away and create the X screen as defined in the xorg.conf regardless... kind of an "I know there's no monitor so override the warnings automatically" switch.

I'll see what I can drum up.  Unfortunately my best experience always comes when I run into an issue... and I've never had this issue :P

PushinNshovinMe, I guess you had a LOT of bad experiences in the forums.  That's unfortunate... I have had fairly good experience in here as far as helpful individuals.  There will always people that say something you feel is out of line, but just ignore them.  Welcome to the internet :D

---

### Post by NTolerance on 2010-08-06
> **PushinNshovinMe said:**
> [rant] I am new to Linux and have found the Ubuntu forums to be largely unhelpful.  Most posters seem to only have one thing in mind at anytime and provide terribly shallow answers.  It seems like you pretty much just have to learn everything on your own, using those vague answers as direction to go in.  I do hope to create a guide on how I created my media server with more specifics of my system and an easier to follow step-by-step for people like me who really don't know enough command-line to understand most vague answers on here. [/rant]
 
To be fair, while I did rant a bit myself, this thread is an exception IMHO.  In particular, the Tutorials & Tips subforum has some very good and well-documented step-by-step instructions.

---

### Post by Chunder on 2010-08-14
OK - just a quick update; I've got my mythbuntu-desktop-running-server (so not really a server installation in the strictest sense) to boot up without the monitor connected and to continue to use the normal 1920x1080 display that it would use if the monitor was plugged in.
Most of the stuff out there - disabling KMS, Nouveau, etc. didn't help; ultimately it came down to spotting in the /var/log/Xorg.0.log file that it was failing the EDID check, which gave me some more terms to google.
Cobbling together advice from a number of sites, I added the following lines to my xorg.conf "Device" section:
```

Option "ConnectedMonitor" "CRT-1"
Option "IgnoreEDID" "TRUE"
Option "UseEDID" "FALSE"
Option "UseEDIDFreqs" "FALSE"
Option "UseEDIDDPi" "FALSE"
Option "ModeValidation" "NoEdidModes"

```

I also had to manually play around with the HorizSync and VertRefresh ranges until the nvidia-settings program would let me select the right mode.

For reference, I also tried using get-edid/parse-edid and ddccontrol in order to find the monitor's EDID (the option doesn't appear in nvidia-settings for some reason, so the advice provided by some sites to save the EDID and use the CustomEDID option wouldn't work) but unfortunately they wouldn't work either. 

I'm going to have a play around with my frontend now (and no, that's not a euphemism for anything! :) ) in order to try and achieve the same result; hopefully this will help somebody out there?

Linux is such a roller-coaster of emotion: hours (days? weeks?) of frustration, a brief glimmer of hope, then a shower of elation... which only lasts until you hit the next problem. Rinse. Repeat. :P

---

### Post by nshiell on 2010-09-21
arrrghhh: I like/need to use a GUI as well as the CLI, i.e. now as I'm at a client and I need to use some GUI things

I'm seriously shocked that this bug made it's way to release!
10.04 can't be used as a home server OS!

---

### Post by arrrghhh on 2010-09-21
> **nshiell said:**
> arrrghhh: I like/need to use a GUI as well as the CLI, i.e. now as I'm at a client and I need to use some GUI things

I'm seriously shocked that this bug made it's way to release!
10.04 can't be used as a home server OS!

Dude, if you need a GUI, use the desktop version.  You're trying to fit a square peg into a round hole by adding a GUI to the server edition...

Besides, I can administer anything on my system from the cli.  I sometimes cheat and use Webmin, but that just makes things easier to see sometimes...

---

### Post by Groodles on 2010-09-23
> **arrrghhh said:**
> Dude, if you need a GUI, use the desktop version. 

I think the real point is that this problem (not being able to load X without a monitor attached) will affect the desktop version as well.

Therefore harping on about GUI vs CLI on a "server" is pointless.

Some people like CLI, some want something more.  Horses for courses.

---

### Post by arrrghhh on 2010-09-23
> **Groodles said:**
> I think the real point is that this problem (not being able to load X without a monitor attached) will affect the desktop version as well.

Therefore harping on about GUI vs CLI on a "server" is pointless.

Some people like CLI, some want something more.  Horses for courses.

Indeed, but if you want a GUI, use the desktop edition.  I'm betting some custom x11 stuff will be needed, I've just never done it/never needed to do it so unfortunately I'm not sure how it would be done... Never been very savvy with xorg.conf anyways... Also considering how it seems to be getting 'phased out' it may not work at all...

Kinda stupid if you ask me, it seems like there should be a way to trick it.  But I still stand by the belief that if you want a GUI, use the desktop edition :D

I can't really test this guys, but I found some dudes in the archlinux forums that were having similar issues with dual monitor setups... they used a combination of some xorg.conf tweaks, and .xinitrc stuff.  [Thread](https://bbs.archlinux.org/viewtopic.php?pid=795399#p795399).  Hopefully it helps.

---

### Post by Groodles on 2010-09-23
lol Dude.  You quote my post but it's obvious from your comment that you didn't read it. :)

---

### Post by arrrghhh on 2010-09-23
> **Groodles said:**
> lol Dude.  You quote my post but it's obvious from your comment that you didn't read it. :)

Uh, yea I did and actually did quite a bit of leg work trying to find something... even asked around on IRC.  So whatever your deal is, I don't really care, but I'm done helping if that's your reaction.

---

### Post by Groodles on 2010-09-24
Ok, so NONE of your posts in this thread have been helpful in regard to the question that raised the thread in the first place.

All you've done is go on about how servers should not have GUIs installed, and you're still doing it.

If you're not going to help, please don't dilute a thread by posting unhelpful opinions.

---

### Post by zmiq2 on 2010-10-01
Hi,

1) I think anything can be done via the CLI, and that should be the way to go for server headless systems. But I also think freedom comes first, and some at first strange procedures may have their reasoning too, and that just happened to me, so I'll post what worked for me

2) for my asus b202 (eeebox), with ubuntu 10.04, the solution it this thread worked very well:

- deactivate kms (I have an intel card)

# echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf 
- new /etx/X11/x.conf file

Section "Device"         Identifier      "Onboard Intel Graphics"         Driver          "vesa" EndSection  Section "Monitor"         Identifier      "Generic Monitor"         HorizSync       31-101         VertRefresh     60-160 EndSection  Section "Screen"         Identifier      "Basic Screen"         Monitor         "Generic Monitor"         Device          "Onboard Intel Graphics"         SubSection "Display"             Modes		"1024x768"         EndSubSection EndSection
Then I rebooted, and gnome autostart launched perfectly, even the screensaver launched as expected.

HTH

---

### Post by vof on 2010-10-01
Many thanks groodles for the hints which allowed me to fix the basic problem - that naked grey screen background.  And I agree with your comments about the unnecessary OT discussions about the principles underlying headless server sysadmin tasks diluting the valuable bits. I too am happy to ssh in but prefer to use VNC, X and synaptic for e.g. package management stuff.

It took me some time (a day or two) to find this thread and fix the problem so I have modified the title of my post to help fellow sufferers get here quicker (I hope).

And also for fellow sufferers, the key actions (from groodles post #8 ) to make it work are:

1. Use the vesa driver.
2. Disable kernel mode setting.

Now I see the gdm greeter screen and can login, I am finding that the X VNC combination is using 100% of one of the dual core cpus. So I've just moved the problem, not fixed it completely;)

What did not help:

1. adding Option "NoDDC" ["True"] to Device section of /etc/X11/xorg.conf

2. adding the following lines to the [xdmcp] section of /etc/gdm/custom.conf:
MaxSessions=16
DisplaysPerHost=2

3. adding the following lines to the end of xorg.conf as suggested in Novell SLE11 document 7005704 to fix the 100% cpu problem:
Section "Extensions"
    Option "SYNC" "off"
EndSection 

My problem started immediately after I moved my server system disk from an old 600MHz Pentium 2 with i810 graphics to a new dual core E1200 Celeron with G33 graphics. The system had no complaints on the earlier headless system and started up fine on the new system with a screen attached but as soon as I put it back in its cupboard without a screen, Xvnc generated the very common grey background in the client window.

And finally, some versions in case that helps:

vince@uranus:/proc$ lsb_release -rd
Description: Ubuntu 10.04.1 LTS
Release: 10.04

vince@uranus:/proc$ uname -a
Linux uranus 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

xserver-xorg 1:7.5+5ubuntu1
xserver-xorg-core 2:1.7.6-2ubuntu7.3
xserver-xorg-video-intel 2:2.9.1-3ubuntu5
xserver-xorg-video-vesa 1:2.3.0-1ubuntu1
vnc4server 4.1.2
vnc4-common 4.1.2

---

### Post by recluce on 2010-10-03
> **arrrghhh said:**
> Uh, yea I did and actually did quite a bit of leg work trying to find something... even asked around on IRC.  So whatever your deal is, I don't really care, but I'm done helping if that's your reaction.

You have NOT been helping anybody. You have just hijacked this thread to preach your believe that a GUI on a server is evil. We know your opinion now. Go away.

---

### Post by Derspankster on 2010-10-25
> **recluce said:**
> You have NOT been helping anybody. You have just hijacked this thread to preach your believe that a GUI on a server is evil. We know your opinion now. Go away.

I agree. Hit the road jackass. I too have a valid reason to run a GUI with my headless server. I may end up going back to 8.04.

---

### Post by HermanAB on 2010-10-26
Howdy,

The important thing to note is that you do not need to run Xorg, VNC, Nomachine or any other GUI environment on a server in order to use graphical programs on the server. 

The solution used by all large institutions that use tens of thousands of headless servers (Google, Amazon, Yahoo, Rackspace...) is SSH with X forwarding.

What you need to do, is install your GUI programs on the server and make sure it works, then turn X off.  From then on, simply log in with SSH (you should configure it to use X forwarding by default) like this:
$ ssh -X -C -c blowfish user@server guiprogram

You can even run a Gnome panel and go click happy:
$ ssh -X -C -c blowfish user@server gnome-panel

All your graphical programs will then run transparently on the local desktop.

This even works from Windows, if you have Cygwin installed.

---

### Post by arrrghhh on 2010-10-26
> **HermanAB said:**
> Howdy,

The important thing to note is that you do not need to run Xorg, VNC, Nomachine or any other GUI environment on a server in order to use graphical programs on the server.

This even works from Windows, if you have Cygwin installed.

Yes, thank you for pointing this out to these... people.

Such a level-headed post, I appreciate it.

You can also use xming on Windows if you don't want to deal with cygwin.

Thanks again, I didn't think there was anyone reasonable left in this whole GUI server argument :p

---

### Post by wjamoore on 2011-08-27
Ok for the benefit of Arrrggg

I put ubuntu 10.04 DESKTOP on a headless PC to be a music server.  Of course I end up with the same problem.  Can't view remote desktop if monitor is not attached.

As for CLI..  Do you seriously think my wife /brother/ father / friends etc are going to learn to use the command line to play some music?  We're talking about home PC stuff that anyone can use.  It really bugs me when people start spouting terminology that the non unix/linux person has no idea about and further bugs me when you don't accpet that the point of Ubuntu (if I'm not hugely misstaken) was to make a plug and play system that anyone can use. (almost)

So.. Does anyone know if there is any real defined fix for this.  If not does Ubuntu plan to do anything about it?   I mean it should be possible to set an option under monitors to allow no monitor GUI

thanks

wjam

---

### Post by arrrghhh on 2011-08-27
> **wjamoore said:**
> Ok for the benefit of Arrrggg

I put ubuntu 10.04 DESKTOP on a headless PC to be a music server.  Of course I end up with the same problem.  Can't view remote desktop if monitor is not attached.

As for CLI..  Do you seriously think my wife /brother/ father / friends etc are going to learn to use the command line to play some music?  We're talking about home PC stuff that anyone can use.  It really bugs me when people start spouting terminology that the non unix/linux person has no idea about and further bugs me when you don't accpet that the point of Ubuntu (if I'm not hugely misstaken) was to make a plug and play system that anyone can use. (almost)

So.. Does anyone know if there is any real defined fix for this.  If not does Ubuntu plan to do anything about it?   I mean it should be possible to set an option under monitors to allow no monitor GUI

thanks

wjam

My girlfriend / mother /friend / whatever plays music thru a CLIENT interface which controls the SERVER.  No one ever interacts with the cli except me.  That's the whole point of the server - you build/use front-ends to get the job done for you.  So I use MPD to play music - there's a plethora of front-ends that you can use to control it, my personal favorite is MPM - a FireFox addon.  There's plenty of others.  For torrents, I use rtorrent + rutorrent - a web interface, so again no one actually interacts with the cli.

Didn't mean to start a war, it's just how servers are built.  Without a GUI, that's how it should be.  A truly headless machine should only be ssh'd into when there's a problem or something needs to be updated/installed/otherwise managed.  Other than that, use front-ends!!

---

### Post by wjamoore on 2011-08-28
I get the whole point of the GUI less server.  I fully understand.  the point is I'm an electro mechanical engineer.. Not SW.  I can, and do have to, work in the HP Unix world from time to time, but I do it so infrequently that it's a very long slow process. (mostly cos I need to get that big brick of a Unix book out).

All I'm saying is that there is a tendency on these forums to assume everyone has the time and patience to start to learn all the file structures of Linux in order to build something that should be simple.  All i want is a PC that boots normally without it's screen attached.  Should be absolutely a piece of cake.  But it's not.

By the way if someone can point me at a definitive how to guide to set up a real server where the remote user can call up movies internet and music applications, I'd be delighted.  But in layman's terms.  I don't mind doing CLI but I want (need) to know what the steps accomplish (in layman's terms again).  Oh and I don't want to see a CLI when the projector is switched on...

I just tried 11.04.  Plus point - it's graphics drivers are OK for my MB now (although for some reason it refuses to recognize my monitor brand - as my desk PC does) ... and once I figured out how to get rid of that new GUI it seems it might be working quite well but I still can't disconnect the damn monitor and boot properly.  So I'll try the procedures again and see what happens.

thanks in advance for any info

wjam

---

### Post by wjamoore on 2011-08-28
well..  I'll be damned.  I got rid of the ATI drivers and used the native...  Because a weird thing was going on with 2 resolutions showing up at the same time... and 11.04 works!

Nothing to do.. just set up the network for autologon, set up the startup apps.. and restart.

No problem.  Although it's not that fast a boot considering I have a SSD.  Slower than my laptop with 10.04

The question is.  Why?  Almost certainly something to do with improved video default drivers as 10.04 could not find the native resolution of my monitor with  the ASUS E35M1 I- Deluxe ATI VGA hardware (9802)...  but no problem with my "lower tech" desktop  ATI Radeon 3200.  So I'm assuming the newer ATI stuff is not quite fully supported.

wjam

---

### Post by arrrghhh on 2011-08-28
> **wjamoore said:**
> well..  I'll be damned.  I got rid of the ATI drivers and used the native...  Because a weird thing was going on with 2 resolutions showing up at the same time... and 11.04 works!

The question is.  Why?  Almost certainly something to do with improved video default drivers as 10.04 could not find the native resolution of my monitor with  the ASUS E35M1 I- Deluxe ATI VGA hardware (9802)...  but no problem with my "lower tech" desktop  ATI Radeon 3200.  So I'm assuming the newer ATI stuff is not quite fully supported.

> **wjamoore said:**
> All I'm saying is that there is a tendency on these forums to assume everyone has the time and patience to start to learn all the file structures of Linux in order to build something that should be simple.  All i want is a PC that boots normally without it's screen attached.  Should be absolutely a piece of cake.  But it's not.

By the way if someone can point me at a definitive how to guide to set up a real server where the remote user can call up movies internet and music applications, I'd be delighted.  But in layman's terms.  I don't mind doing CLI but I want (need) to know what the steps accomplish (in layman's terms again).  Oh and I don't want to see a CLI when the projector is switched on...

I just tried 11.04.  Plus point - it's graphics drivers are OK for my MB now (although for some reason it refuses to recognize my monitor brand - as my desk PC does) ... and once I figured out how to get rid of that new GUI it seems it might be working quite well but I still can't disconnect the damn monitor and boot properly.  So I'll try the procedures again and see what happens.

I think your setup is going to require the Desktop Edition.  I agree that it should be easy to boot the machine without a monitor attached, but I would say that's not "normal", and perhaps the hardware or software doesn't handle it so well.  I'm not sure what the culprit is for you, but you have to agree most machines either have a DE and always have a monitor plugged in, or are servers and never have a monitor plugged in.

It seems like you want to play movies and search the internet directly on the "server".  This is obviously not orthodox for a server, and completely breaks the whole server/client setup that I was describing earlier.  The server edition is really setup to be a server - not a machine that you directly surf the internet on, but a machine that for example serves up pages to the internet.

I wish you well in your efforts.  If you want to use the machine to watch movies directly on and surf the internet directly on, you're obviously going to need some sort of DE.  I know as well as you do it's pretty impossible to search the internet on a machine that's cli only.

So the Server Edition, while it sounds great on paper (and is great if you want a server) is not for you.  You'll need the Desktop Edition, and hopefully you can sort out the issues with the no monitor condition.  It certainly does seem like a software issue, and hopefully you can resolve it.  I've never attempted such a thing, and I'm not sure what section of the forums it belongs in...

Good luck!

---

### Post by wjamoore on 2011-08-28
Dude!  It is desktop and (as mentioned) everything works in 11.04.  Including no monitor.

Only problem now is making realplayer work in 64 bit.

 I can't force it as per the Ubuntu instructions here:

[https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods)

Seems it doesnt like lsb4

Anyway i can live without 1 radio stream

wjam

---

### Post by mathew7 on 2011-10-18
> **arrrghhh said:**
> I think your setup is going to require the Desktop Edition.  I agree that it should be easy to boot the machine without a monitor attached, but I would say that's not "normal", and perhaps the hardware or software doesn't handle it so well.  I'm not sure what the culprit is for you, but you have to agree most machines either have a DE and always have a monitor plugged in, or are servers and never have a monitor plugged in.

It seems like you want to play movies and search the internet directly on the "server".  This is obviously not orthodox for a server, and completely breaks the whole server/client setup that I was describing earlier.  The server edition is really setup to be a server - not a machine that you directly surf the internet on, but a machine that for example serves up pages to the internet.

I wish you well in your efforts.  If you want to use the machine to watch movies directly on and surf the internet directly on, you're obviously going to need some sort of DE.  I know as well as you do it's pretty impossible to search the internet on a machine that's cli only.

So the Server Edition, while it sounds great on paper (and is great if you want a server) is not for you.  You'll need the Desktop Edition, and hopefully you can sort out the issues with the no monitor condition.  It certainly does seem like a software issue, and hopefully you can resolve it.  I've never attempted such a thing, and I'm not sure what section of the forums it belongs in...

Good luck!

But what is the difference between the 2 editions? Except maybe for some kernel parameters, only the CD bundled packages. The common packages from the server and desktop editions are identical. They take the updates from the same repositories. You won't see the "apache-server" and "apache-desktop" packages. You only have "apache". A server edition can be turned into a desktop just like an Ubuntu can be turned into Xubuntu.

My setup is a home server in my living room, where my HDMI-passthrough-amplifier and HDTV are also.
So I'm using my server, which already has a standalone VNC daemon  running, to also stream youtube, motogp, ALMS etc. to the HDTV (note: intel G43  IGP).
So my problem is that any restart of the server due to "upgrades" will  never start my "streaming" session, because when my amp and TV are off,  no EDID comes though HDMI. So when I do turn on the TV+amp, I have to  login to a text session and start GDM3 again (which defeats the  autologin). I never do the upgrades while "watching" the TV. When I'm  there, I'm there to watch+listen (so don't even think of telling me to do the upgrades at  the console)

So:
- server/desktop does not matter (it's the GPU driver that aborts)
- HDTV does not send EDID when off (so techincally monitor is plugged)
- remote restart will fail preparing the "ready for streaming" session
- using vesa driver defeats the purpose of having video streaming (I've seen that "guide" 3 times in this topic)

How would you like to have you STB box to "power on" each time you  "wake" your TV? That would mean after you turn on your TV, you will wait  1-2 minutes for STB to show something.

So (to everyone) stop debating "why" it's a problem and start telling "how" to fix it.

I saw a post about nvidia driver, and some of those options I will try now. But I wanted to post "why" I (and others may) need it.

---

### Post by arrrghhh on 2011-10-18
> **mathew7 said:**
> So (to everyone) stop debating "why" it's a problem and start telling "how" to fix it.

I think the main source of the problem is you're not using a server how they are traditionally used.  I think Linux can be customized to anyone's needs.  Sometimes it's difficult to figure out how to customize it to meet those needs.

I have a server that's always on too with lots of shows, movies, etc.  But I stream all this media to another system - after all I want surround sound to work!  Right now it's a PS3, but I want to setup an XBMC system.

Good luck.  I'd say you'll have to trick the card into thinking there's always a monitor there - which I don't know how you can do... xorg.conf really isn't used anymore, otherwise I'd say you could statically configure something in there and *maybe* it'll work.

Again, I don't think most people have their servers plugged into their TV's.  My server is plugged into my amp to play music thru mpc/mpd - people told me the same thing "no one hooks a server up to an amp", but I figured out how to make it work.  I'm sure there's a way...  Hopefully someone chimes in that knows how.

---

### Post by mathuin on 2011-10-18
> **arrrghhh said:**
> I think the main source of the problem is you're not using a server how they are traditionally used.  I think Linux can be customized to anyone's needs.  Sometimes it's difficult to figure out how to customize it to meet those needs.

It's funny, but this is exactly how servers are used many, many places and have been for many, many years.  ssh in, vncserver out, get your graphical interface where you need it instead of where the machine is -- and when the machine is in a colocation facility in California and you are accessing it remotely from a hotel in New York, it's nice to be able to access it graphically if that's what you need to do what you need to do.

I have a need for VNC because it's "screen for X": I can start a graphical program on a VNC server session then detach that server session and the graphical program will continue to run.  I can reconnect to that server session from work or home (modulo certain tunneling) and check on that program.  I have done this for a long, long time on multiple operating systems.  It is a very good way for me to work.  It is in fact the only way for me to work on this project, because that is the only tool available.

I just upgraded a lucid lynx box to oneiric ocelot by multiple release updates.  Now VNC does not work, so my work flow is dead in the water.  There was no documentation warning that VNC would break.  There is just the unrealistic, unjustified, and unwise assumption that if I wish to use a GUI on a system, I must do it locally at least once.  I hope that anyone still reading can see how that assumption does not apply for me at the least and others as well.

Please.  Someone tell us how to get back to work.  Reverting to lucid lynx, or to FreeBSD, or goodness help me Windows, is not desirable -- but each of those platforms can do this simple obvious common thing, so I am sure that oneiric ocelot can, once people who understand the changes can help us figure out what we need.

Thank you in advance to those who can actually help.

Jack.

---

### Post by arrrghhh on 2011-10-18
> **mathuin said:**
> It's funny, but this is exactly how servers are used many, many places and have been for many, many years.  ssh in, vncserver out, get your graphical interface where you need it instead of where the machine is -- and when the machine is in a colocation facility in California and you are accessing it remotely from a hotel in New York, it's nice to be able to access it graphically if that's what you need to do what you need to do.

No, I'd say an extremely small section of servers that people actually want a UI on.  I know every single Linux server I've come across (that's being used as a server) has no UI and SSH only...

If it works fine in Lucid, why not run Lucid?  I keep my servers on LTS releases anyways...  You seem to do a lot of things that server people don't do, but yet you claim they do.

---

### Post by Smokabowl on 2011-10-26
Argh is a troll. I'm surprised everybody hasn't ignored him by now.

I want a headless server with VNC, and I am going to get it. I know how to use the CLI and I just DGAF.

---

### Post by Steve54 on 2011-10-31
> **Smokabowl said:**
>  I want a headless server with VNC, and I am going to get it.
 
Agreed, I used 10.4LTS and added Gnome core, Gnome utilities, VNC and Webmin. I followed a tutorial that I found on the net. Using Gnome core I've had no problems with it booting without a monitor attached. I didn't have to fiddle with any graphics settings other than setting the screen size parameters in VNC. I didn't want the desktop version because of all the extras that would have been installed.
 
I do some of the admin by the GUI via VNC and some via either a terminal in the GUI or through PUTTY.
 
I am new to Ubuntu and it's taken me a month so far and I'm still struggling to get one device to connect to the Samba shares. 
 
For the purpose I'm using it for I could have it all done and sorted in XP in a day but I wanted the stability that hopefully Ubuntu will give. If it wasn't for a semi-familiar GUI I would have had to give up long ago and used Windows.

---

### Post by arrrghhh on 2011-10-31
> **Steve54 said:**
> If it wasn't for a semi-familiar GUI I would have had to give up long ago and used Windows.

So glad you all are willing to step outside your bubble and learn something new :rolleyes:.

Good luck in your useless pursuit of bloating up your server install!

---

### Post by Steve54 on 2011-10-31
> **arrrghhh said:**
> So glad you all are willing to step outside your bubble and learn something new :rolleyes:.
 
Unless the server needs rebuilding then I will be back in my "bubble", the server is purely a tool.
 
> **arrrghhh said:**
> Good luck in your useless pursuit of bloating up your server install!
 
Unless you include filling the HDD with files then hardly bloating seeing as the GUI doesn't run unless I login. The server runs quite happily at the login prompt.

---

### Post by Smokabowl on 2011-11-14
> **Steve54 said:**
> Unless the server needs rebuilding then I will be back in my "bubble", the server is purely a tool.
 

 
Unless you include filling the HDD with files then hardly bloating seeing as the GUI doesn't run unless I login. The server runs quite happily at the login prompt.Oh noes my dual Xeon processors are going to need another cycle to complete a users request.

---

