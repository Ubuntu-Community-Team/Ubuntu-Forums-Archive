---
title: "Headless server / VNC"
date: 2009-10-22
forum: Server Platforms
---

### Post by can2002 on 2009-10-22
Hi all,

I've been meaning for ages to sort out a problem where I want to connect to my MythTV backend server via VNC.  The problem I've encountered like many others is that the box doesn't have a monitor attached and therefor my X session has not successfully started.  I've finally got round to sorting it and thought I'd post here in case it was of use.  

I'm running Karmic; however I'm reasonably sure the solution should work in Jaunty too (where I first noticed the problem).  Create a file called [FONT="Courier New"]xorg.conf[/FONT] in [FONT="Courier New"]/etc/X11/[/FONT] and paste the following:

[INDENT][FONT="Courier New"][COLOR="Red"]
Section "Device"
        Identifier      "VNC Device"
        Driver          "vesa"
EndSection

Section "Screen"
        Identifier      "VNC Screen"
        Device          "VNC Device"
        Monitor         "VNC Monitor"
                SubSection "Display"
                        Modes   "1024x768"
                EndSubSection
EndSection

Section "Monitor"
        Identifier      "VNC Monitor"
        HorizSync       30-70
        VertRefresh     50-75
EndSection
[/COLOR][/FONT][/INDENT]

Thanks to the various posts here that have provided pointers...

Regards,
Chris

---

### Post by druhboruch on 2009-10-22
Have you considered freenx?
It is fast and very easy to setup.

---

### Post by benbrookshire on 2009-11-04
I think this is just what I needed! I had this same problem in 9.04, but for some reason it eventually stopped happening.

I upgraded to 9.10 Monday of this week and after ssh'ing in and restarting I was dead in the water. Plugging in a monitor and rebooting allowed me to get back online.

I haven't tested this yet, but I have already put it in place. Wanted to note that the xorg.conf file already existed, I just made a backup and edited the existing.

I didn't see what the screen was showing when I was hung, but previously in 9.04 it said something like "low graphics mode", and wouldn't boot.

Thanks!

---

### Post by windependence on 2009-11-04
> **druhboruch said:**
> Have you considered freenx?
It is fast and very easy to setup.

+1 for freenx.

You could also export X in an ssh session and just run the app on the client machine.

OR, you could admin the box via command line which is the best way IMHO.

-Tim

---

### Post by benbrookshire on 2009-11-05
I agree, for the most part I try to admin via command line. But I like having the GUI to fall back on. I'm not an expert, so some things are beyond me if I don't have the GUI.

The problem prevents accessing the command-line as Ubuntu doesn't even boot. I realize this problem may be non-existent if you just run Ubuntu without a GUI, but like I said...

---

### Post by redrockts on 2009-11-08
Thank you for sharing, can2002!

This is _**EXACTLY**_ what I have been looking for and needed. So many other posts attempting to solve the headless startup issue have recommend other VNC servers or other more invasive solutions. I knew proper settings in the xorg.conf file would fix it, but I am just not fluent enough in the xorg.conf file to have figure this out. I implemented your file and it works like a dream.

Thanks again!

---

### Post by mr_snarf on 2009-11-18
I was having the same problem with 64-bit version of Ubuntu 9.10 (desktop). I wanted to use it headless, and VNC into it, but it wouldn't work. Repeately checking calling "tail /var/log/syslog" found errors occuring every few seconds: gdm wasn't successfully starting, and thus kept respawning. I could VNC in, but couldn't get past the login screen (was using xdmcp to bring up the gdm login screen (not sure if thats the correct terminology)).

Putting your lines of code in /etc/X11/xorg.conf fixed the problem! Thanks!

---

### Post by MadhaviPrem on 2009-12-26
Worked like charm on Linux Mint Helena HTPC to control via VNC 
Great Tip
Thanks[Smile]("http://ubuntuforums.org/images/smilies/icon_smile.gif")

---

### Post by xTkAx on 2010-01-09
My resolution is 800x600 when connected via VNC on the headless server, and i wanted to have a larger screen to view.  The server is Karmic 9.10 and xorg.conf  was empty, but i added all the lines you marked in red, and rebooted.

After it came online, the VNC connection wouldn't let me connect at all, so i ssh'd back to the server, and rm'd /etc/X11/xorg.conf, rebooted, and now it works again. So just adding those lines to that file didn't work for me.  I'll be sticking with 800x600 for a bit until i find some other workaround or dedicate more time to it.  For now though, ssh -x user@server works good enough.

---

### Post by produnis on 2010-01-24
> **can2002 said:**
> 
[INDENT][FONT=Courier New][COLOR=Red]
Section "Device"
        Identifier      "VNC Device"
        Driver          "vesa"
EndSection

Section "Screen"
        Identifier      "VNC Screen"
        Device          "VNC Device"
        Monitor         "VNC Monitor"
                SubSection "Display"
                        Modes   "1024x768"
                EndSubSection
EndSection

Section "Monitor"
        Identifier      "VNC Monitor"
        HorizSync       30-70
        VertRefresh     50-75
EndSection
[/COLOR][/FONT][/INDENT]
Regards,
Chris

Thank Chris!!! This solved [my problem]("http://ubuntuforums.org/showthread.php?p=8711723")....
Works like charm on Karmic!

---

### Post by fboecom on 2010-02-28
I[FONT="Arial"]t did not work for me at all. Probably because of the changed behaviour of X11 in 9.10.
However, there is a better solution and it is described here:
[http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx](http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx) .
I am quite a newbie, so as much in newbie talk and to state it even a bit more explicit:

0. It is easier or even necessary to allow remote connections by one time hooking up a monitor and keyboard and set the necessary things using the logged in (sudo) user. Such as the vnc password. Also how the box behaves during shutdown is easy using the GUI. 
sudo apt-get install vncserver and openssh as well.
1. 'SSH into the box' means for instance using Putty, also from Windows. use putty to connect (using ssh) to the server in command line form. Login with Putty also works with no monitor and not keyboard to the server.
2. accessing the server with Putty,after logging in, you would type in:
[FONT="Courier New"]nano ~/.vnc/xstartup[/FONT]
and there:
[FONT="Courier New"]#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid black
gnome-session &[/FONT]
and ^X out.
after that I created a shell script:
[FONT="Courier New"]nano ~/.vnc/vnc.sh[/FONT]
and in there:
[FONT="Courier New"]#!/bin/sh
vncserver &#8211;geometry widthxheight &#8211;depth 24[/FONT]
and ^X out.
then 
[FONT="Courier New"]chmod +x ~/.vnc/vnc.sh[/FONT]
so, after logging in you would type ./.vnc/vnc.sh 
and the box would resond that it has created the Xsession as well as its version (typically:1).
From the client machine start the VNCclient, with
<hostname>:1
where <hostname> is the name of the ubuntu server and the number is the number of the X session.
Enter the password and off you go![/FONT]

---

### Post by fboecom on 2010-03-01
[FONT="Arial"]Too bad I found out that VNC completely shifts my keys.. In my previous post, disregard the xstartup editing. Luckily I found the solution(s) 
1. **vnc solution** from
[COLOR="Blue"][http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html](http://blog.yclian.com/2007/12/3-solutions-to-gnomevnc-keyboard.html)[/COLOR]
Wolfgang Schnerring said...

I have created a file called **vncstart **in my home directory. It contains:

[FONT="Courier New"]#!/bin/sh
echo resetting keyboard..
gconftool --set /desktop/gnome/peripherals/keyboard/kbd/layouts --type List --list-type String [aa]
echo starting vnc X session
vncserver -geometry 1024x768 -depth 24[/FONT]

then 
[FONT="Courier New"]chmod +x vncstart[/FONT] 

and the next time in putty issue:

[FONT="Courier New"]./vncstart[/FONT]

then in the vncviewer access the [FONT="Courier New"]**<host>:<x_server_number>**r[/FONT] (eg: **via-c7-uu:1**) and we are all set.
dammit for the time needed.

2. **install FreeNX**, a better solution and forget all about VNC.[/FONT]

---

### Post by NeddyDownUnder on 2010-04-01
Thanks for all the help in this post. It helped alot. 

After many many hours of fumbling through my Linux machine I have been able to get my headless  Ubuntu Desktop machine to consistently display at 1680x1050. I thought I would make a post as I couldn't get this resolution with just what has been posted so far in this post.

I am very new to Linux and I have been on a mission for a few days now trying to get the resolution on my headless Ubuntu desktop system to display correctly. I am running Karmic, and I'm using an onboard graphics card(sorry I don't know what mobo it is) with no monitor conected...

Anyway I wanted to display at 1680x1050, and as far as I can tell (and I could be wrong..) but vesa does not support that resolution, and I kept just getting a few different, lower resolutions assigned each time I started up, I solved my problem by just taking out the top section of the suggested xorg.conf file at the start of the post so that the system would automatically fill in the blanks. It works a treat, now every time I reboot or shut down and I reconnect over VNC through my Mac the resolution is set at 1680x1050. I don't know how correct this method is, as I said I'm very new to Linux, but it worked for me and I thought I would pass it on.

Here is what my whole xorg.conf file looks like now:

Section "Screen"
Identifier "VNC Screen"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1680x1050"
EndSubSection
EndSection

Section "Monitor"
Identifier "VNC Monitor"
HorizSync 31-101
VertRefresh 60-160
EndSection

Maybe this will help someone. :)

---

### Post by Malac on 2010-05-10
I posted my idea on brainstorm.ubuntu.com here is the link if you want to comment or help promote it.
[[IMG]http://brainstorm.ubuntu.com/idea/24380/image/2/[/IMG]]("http://brainstorm.ubuntu.com/idea/24380/")

---

### Post by alexand&#305;r on 2010-05-10
Thanks for the information :)

---

### Post by knowram on 2010-05-13
> **xTkAx said:**
> My resolution is 800x600 when connected via VNC on the headless server, and i wanted to have a larger screen to view.  The server is Karmic 9.10 and xorg.conf  was empty, but i added all the lines you marked in red, and rebooted.

After it came online, the VNC connection wouldn't let me connect at all, so i ssh'd back to the server, and rm'd /etc/X11/xorg.conf, rebooted, and now it works again. So just adding those lines to that file didn't work for me.  I'll be sticking with 800x600 for a bit until i find some other workaround or dedicate more time to it.  For now though, ssh -x user@server works good enough.

I am having the same problem. Tried adding the xorg.conf file to /etc/X11 and now VNC will not connect at all.

---

### Post by gggie on 2010-06-11
The solution in the OP was working perfectly for me in 9.10 - but I upgraded to 10.04 and it's not working anymore.

Is there a solution to this problem that works with 10.04?  

(I can't believe there isn't just a simple option a user can toggle to tell the OS you want to be in headless/VNC mode and don't want the monitor check to happen... :-s)

---

### Post by Enthrall on 2010-06-13
> **gggie said:**
> The solution in the OP was working perfectly for me in 9.10 - but I upgraded to 10.04 and it's not working anymore.

Is there a solution to this problem that works with 10.04?  

(I can't believe there isn't just a simple option a user can toggle to tell the OS you want to be in headless/VNC mode and don't want the monitor check to happen... :-s)

Im frantically looking for a solution myself.

---

### Post by HermanAB on 2010-06-14
Well, actually there is a very simple solution - don't use VNC.

You guys have basically rediscovered most of the reasons why greybeard sysadmins that manage remote servers do not use VNC, but rather use SSH.  The remaining reason that you haven't discovered yet, is that VNC is insecure and will sooner or later cause your machine to get hacked.

Rather install openssh-server and connect to it like this:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or even
$ ssh -X -C -c blowfish user@server "gnome-panel"

and go click happy.

That works from Windows too, if you install Cygwin.

In a nutshell, VNC is a POS and is almost always the wrong solution.  The exception is training.  VNC is sometimes good for training.

---

### Post by Malac on 2010-06-14
^^ 
I don't want to ssh into it that adds a whole layer of complication and isn't required in a simple home setup.

_**A quickish solution for anyone tearing their hair out:**_
You can build a dummy vga load for about £5-00 max with parts from maplins or other electronic suppliers. Google "dummy vga load" and there are loads of sites with diagrams and howtos. It's a bit fiddly but a kid could do it. 
Here's the directions I used:
[http://soerennielsen.dk/mod/VGAdummy/index_en.php](http://soerennielsen.dk/mod/VGAdummy/index_en.php)
and another good one:
[http://www.geeks3d.com/20091230/vga-hack-how-to-make-a-vga-dummy-plug/](http://www.geeks3d.com/20091230/vga-hack-how-to-make-a-vga-dummy-plug/)

**Also please see my earlier post with a link to brainstorm.ubuntu.com where I have an idea for a simple option to ignore missing monitor as suggested, that needs promoting. :)**

Hope this helps.

---

### Post by CharlesA on 2010-06-14
I've been forwarding X over ssh for a while now and it totally rocks compared to VNC. It's secure and you don't need to have an extra service running on your machine.

If you are just using a server locally and don't need any access from the internet, I guess you could use VNC, but it wouldn't be that secure. To use the builtin vino server, you would need to set the machine to autologin and then set the server to use a password or whatnot.

If it doesn't have access to the internet, you should be "ok" but I'd not use VNC on a server I could just SSH into.

@HermanAB: I use XMing on Windows machines along with Putty to forward X over SSH. Works fine so far. :)

---

### Post by gggie on 2010-08-22
For anyone still looking for a 10.04 solution to this, see posts # 21 and 24 in this thread:
[http://ubuntuforums.org/showthread.php?t=1452600&page=3](http://ubuntuforums.org/showthread.php?t=1452600&page=3)

Using the xorg.conf in # 21 and the grub edit in # 24 worked for me.  I can now (finally!) boot the system without a monitor attached.

---

### Post by =ChAoS= on 2010-08-22
> **benbrookshire said:**
> I agree, for the most part I try to admin via command line. But I like having the GUI to fall back on. I'm not an expert, so some things are beyond me if I don't have the GUI.
 
 
I use freenx and the no machines client on my windows desktop for that very reason. :lolflag:

---

### Post by mtbsoft on 2010-12-18
> **HermanAB said:**
> Rather install openssh-server and connect to it like this:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or even
$ ssh -X -C -c blowfish user@server "gnome-panel"

and go click happy.
Thanks for this, helped me out no end.  In case anyone needs to know, adding the -t argument to the ssh ***mand create a pseudo-terminal which enables you to run sudo ***mands if necessary.

---

### Post by manuel.flury on 2011-03-26
Create this /etc/X11/xorg.conf

> Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib64/xorg/modules"
        FontPath     "catalogue:/etc/X11/fontpath.d"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "vnc"
        Load  "extmod"
        Load  "dbe"
        Load  "glx"
        Load  "record"
        Load  "dri2"
        Load  "dri"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "HWcursor"                  # [<bool>]
        #Option     "Xinerama"                  # [<bool>]
        #Option     "StaticXinerama"            # <str>
        Identifier  "Card0"
        Driver      "vmwlegacy"
        BusID       "PCI:0:15:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
        Option "SecurityTypes" "VncAuth"
        Option "UserPasswdVerifier" "VncAuth"
EndSection
check you have the extension available :

# ls -l /usr/lib64/xorg/modules/extensions/*vnc*
-rw-r--r-- 1 root root 619600 2011-03-26 23:24 /usr/lib64/xorg/modules/extensions/libvnc.so


I copied it from another linux (fedora) after spending too much time to find the package, if somebody knows the name of the package that would be great

I use this config in VMWare VM and it works like a charm

---

### Post by Champilion on 2011-03-29
Hello everyone,

I was really frustrated trying to setup a headless Ubuntu server through VNC as most of the solutions mentioned in number of forums has not worked for me, Messing with [FONT=Courier New]xorg.conf file in every possible way and not being satisfied with the results, i decided to post my version of how to setup a headless ubuntu server through VNC.

Instead of messing around with the the [/FONT][FONT=Courier New]xorg.conf file i decided to use the "xrandr" command and hard code it into /etc/gdm/Init/Default so this is what i have done
[/FONT]
[FONT=Courier New]note: im no expert in linux, so test these settings before applying them also some of my comments are coming out of guessing more than true facts. 
[/FONT][FONT=Courier New]note: always keep a backup copy of the  Init/Default file in case anything goes wrong you can start the server  in recovery mode and overwrite the corrupted file with the backup.[/FONT]
[FONT=Courier New]xrandr referenc[/FONT][FONT=Courier New]e: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)[/FONT]
[FONT=Courier New]
-In a terminal run: gksudo gedit /etc/gdm/Init/Default
which opens the Init/Default file

-I've inserted right below the "OLD_IFS=$IFS" line:
 [/FONT]> xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync

xrandr --addmode CRT1 1280x768_60.00

xrandr --output CRT1 --mode 1280x768note: i have tested these commands first in terminal before pasting them into the Init file.
note: running xrandr command alone should give u info about which display options u have also the "virtual screen" info u need which in my case was CRT1 connected to the VNC X display

-also because i wanted for the x11vnc to auto start and be running even if i logoff my session i have added these lines after the "/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm" line:

> /usr/bin/x11vnc -rfbauth /home/[COLOR=Red]myaccount[/COLOR]/.vnc/passwd -o /tmp/x11vnc.log -bg -shared -forever -noxdamage -progressive 256 -xrandr "resize" -rfbport 5905note: i have added the -xrandr "resize" command which allows x11vnc screen to be resized without giving a blackscreen or crashing the server

- Then saved my file and restarted

Hope this info be much of a help for some of you as this has worked great for me without having to change anything in the [FONT=Courier New]xorg.conf file.
[/FONT][FONT=Courier New]




[/FONT]

---

### Post by a904guy on 2011-06-12
I've found a solution to the 800x600 resolution issues.

[http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/]("http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/")

---

### Post by kriegaex on 2012-02-23
This is my solution for bigger resolutions. VESA only seems to support max. 1600x1200.

```

# Driver "dummy" needs package xserver-xorg-video-dummy.
# If resolutions up to 1600x1200 are enough for you, you may use driver "vesa".
# VideoRam needs to be big enough (8192 or 16384), otherwise there might be error messages in /var/log/Xorg.0.log.

Section "Device"
    Identifier  "Headless x11vnc Video Device"
    Driver      "dummy"
#   Driver      "vesa"
	VideoRam    16384
EndSection


# Modelines calculated at http://www.arachnoid.com/modelines/index.html (removed trailing "_60.00" in mode names).
# HorizSync, VertRefresh ranges need to be big enough, otherwise there might be error messages in /var/log/Xorg.0.log.

Section "Monitor"
    Identifier  "Headless x11vnc Monitor"
    HorizSync 22 - 83
    VertRefresh 50 - 76
    # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
    Modeline "1024x768" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
    # 1152x864 @ 60.00 Hz (GTF) hsync: 53.70 kHz; pclk: 81.62 MHz
    Modeline "1152x864" 81.62 1152 1216 1336 1520 864 865 868 895 -HSync +Vsync
    # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
    Modeline "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync
    # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
    Modeline "1280x1024" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
    # 1360x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 116.01 MHz
    Modeline "1360x1024" 116.01 1360 1448 1592 1824 1024 1025 1028 1060 -HSync +Vsync
    # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
    Modeline "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
    # 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
    Modeline "1600x1200" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 -HSync +Vsync
    # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
    Modeline "1680x1050" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -HSync +Vsync
    # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
    Modeline "1920x1080" 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -HSync +Vsync
    # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
    Modeline "1920x1200" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -HSync +Vsync
EndSection


# Use modes defined in "Modeline" entries above.

Section "Screen"
    Identifier  "Headless x11vnc Screen"
    Monitor     "Headless x11vnc Monitor"
    Device      "Headless x11vnc Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1024x768" "1152x864" "1280x800" "1280x1024" "1360x1024" "1440x900" "1600x1200" "1680x1050" "1920x1080" "1920x1200"
    EndSubSection
EndSection

```

---

