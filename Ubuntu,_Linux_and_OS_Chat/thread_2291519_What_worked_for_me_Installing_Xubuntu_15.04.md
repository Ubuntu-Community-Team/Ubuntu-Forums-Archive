---
title: "What worked for me: Installing Xubuntu 15.04"
date: 2015-08-20
forum: Ubuntu, Linux and OS Chat
---

### Post by Deep_Peasant on 2015-08-20
Just to say hi & thanks, don't know where to post, can find spoiler tags so here it is,

XUBUNTU 15.04 August 2015.

Coming from the dark ages of DOS up to Windows 10 and the implications of installing the later I decided it was time to move to another operating system. Having tried Ubuntu in the past the choice was made. Alas, the Unity interface did not appeal to me and XFCE, Xubuntu had my preference. Switching from Windows to (X)ubuntu has been made easier and the installation is fairly straightforward. That is, when you don’t horse around too much with different HDD/SSD OS combo’s like I did. Then the adaptation challenges kick in, can’t find this, what does that do, how do I fix this and that. So I started to make notes of things I found out. Here’s the “list” so far,

GET XUBUNTU:
[http://xubuntu.org/](http://xubuntu.org/)

GET A INSTALLER:
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

    Install the Xubuntu ISO. 
    Use a USB stick, don’t use front panel USB ports.
    Get your PC to boot from USB, press Del, F2, F12, whatever gets you into your BIOS or bootmenu. 
    Boot your PC with the installation USB Stick.

DUAL-BOOT:
Do not install a fresh or new Windows version AFTER dual-boot installation. It breaks the boot loader. Yes, you can repair it but it gave me a headache, thats how I found BOOT REPAIR and again GPARTED.

TERMINAL:
The command line interface, you can’t do anything serious without administrator permission.
How do you get that? 
    sudo
then type your password, you won’t see what you are typing!
After putting in a command, hit enter and let each command run before entering another.
So don’t copy and paste multiple commands and expect them to run all in one enter!

DISK MANAGEMENT:
Always missing after system install,
Software Center:
    GPARTED
Get program,
Terminal:
    sudo apt-get install gparted

BOOT REPAIR:
Run from live cd/usb!
Get program,
Terminal:
    sudo add-apt-repository ppa:yannubuntu/boot-repair
    sudo apt-get update
    sudo apt-get install -y boot-repair && boot-repair

Run program GUI, Menu/Setting/Boot Repair

FIREWALL:
Software Center:
    UFW / GUFW GUI for UFW

VIRUSSCAN:
Software Center:
    CLAMAV

GUI SYSTEM CLEANER:
Software Center:
    BLEACHBIT
(Carefull now!)

CLEANUP UBUNTU SYSTEM:
Terminal:

What autoclean does is remove partial packages from the system.
    sudo apt-get autoclean
What this command does is to clean remove .deb packages that apt caches when you install/update programs.
    sudo apt-get clean
What the autoremove command does is to remove packages installed as dependencies after the original package is removed from the system.
    sudo apt-get autoremove
Then the last one, is a little too dangerous to my taste, keep it OPTIONAL!
What gtkorphan does is to find packages that were once used but no longer have any purpose.
Be careful as to not remove the Gstreamer packages as they are for mp3 encoder/decoding and DVD playback. Do not remove them.
    sudo apt-get install gtkorphan
System/Administration/Remove orphaned packages.

Now for a few programs I installed that might be useful to former Windows users:

SYSTEM TEMPERATURES
Software Center:
    PSENSOR

DISK MONITORING
Software Center:
    GSMARTCONTROL

PASSWORD SAFE
Software Center:
    KEEPASSX

CD AUDIO EXTRACT/MP3
Software Center:
    ASUNDER CD RIPPER
Don’t forget to install the LAME mp3 encoder.

Last note, these tips & tricks worked for me. I found out installing on my own PC with it’s hardware quirks, searching for answers around the net, mostly ending up with results from the Ubuntu forums.
I don’t have any interest or gain by saying you should use these tips or programs, there are dozens of options and programs. Still there are many more things that I came across and forgot or got deleted as I (re)installed for the X time (thanks to myself messing around and a little ‘help’ from windows....). 
So far so good, big thanks to all the (X)ubuntu/linux people out there. :)

---

### Post by Bucky Ball on 2015-08-20
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Better here. You won't get any feedback on the intro thread as it is a non-support or chat thread in a non-support area and is thousands of posts deep. :)

The intro thread is for a quick 'hi, I'm here, how ya doin' post, and you're still welcome to post one of those.

I'm sure you'll get a few responses to your ideas here. For all the forum categories see [HERE]("http://ubuntuforums.org/forum.php"). 

PS: I've changed the title to reflect your post. You can change it to something other by editing the first post and hitting 'Go Advanced'.

---

### Post by Bashing-om on 2015-08-20
Deep_Peasant; Hello;

What an odyssey . Press on pays off !

[INDENT][INDENT]testimony that 'buntu
[INDENT][INDENT][INDENT][INDENT]can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

