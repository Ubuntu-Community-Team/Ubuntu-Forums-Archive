---
title: "VirtualBox Screen Resolution - Ubuntu 11.04 Alpha2"
date: 2011-02-16
forum: Virtualisation
---

### Post by vivimonkey on 2011-02-16
Apparently, xorg.conf has been deprecated. Is there any other screen resolution config file in the file system?

---

### Post by franco67 on 2011-02-17
Vivimonkey, you are true: I've complete the upgrade (of my 10.10 into VirtualBox) a few hours ago and the settings into xorg.conf are completely ignored.

now it's running with a ridiculous 800x600 in a full HD screen. It's impossible to work.

other ideas for manually bypassing auto-detected screen capacity?


f.

---

### Post by insane_alien on 2011-02-17
install guest additions.

---

### Post by franco67 on 2011-02-17
it's not my firs use of VitualBox... I've already done it.

the same problem appears on v10.10: the installation of VB Guest Additions does not solve the problem... ubuntu is unable to detect the screen correctly but a manual update of xorg.conf allowed to use the correct resolution.

maybe, in the 11.04 there is a bug into xrandr that does not load xorg.conf.

I'm trying to update the configuration of xrandr manually...

I'll keep you informed.

f.

---

### Post by franco67 on 2011-02-17
type the command:
>cvt 1920 1004
you will obtain something similar:

# 1920x1004 59.89 Hz (CVT) hsync: 62.40 kHz; pclk: 159.75 MHz
Modeline "1920x1004_60.00"  159.75  1920 2040 2240 2560  1004 1007 1017 1042 -hsync +vsync

>xrandr
you will obtain something similar:

Screen 0: minimum 640 x 480, current 800 x 600
**default** connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
   1920x1004_60.00   59.9  

the bold word is the output name
if you type this command:
>xrandr --newmode default "1920x1004_60.00"  159.75  1920 2040 2240 2560  1004 1007 1017 1042 -hsync +vsync
and then
>xrandr --addmode default 1920x1004_60.00

  and the new mode will be inserted into available list... you can easily see it in the screen settings.
but if you select it it doesn't work anyway.

when you try to apply the High res config, the system tell you an error...
maybe the "*Failed to get* size of *gamma* for output default" message the xrandr tells you every times means something...
 
funny!!!

you can try to make this configuration as default but, on the next start-up, the new configuration disappears.


no more ideas.

for insane_alien...
really... the compilation of Guest Addictions fails... I've see only the last line: "installation of... something...done."
maybe the detection of the screen (and the use of xorg.conf) fails for this reason.

I've try to follow the wiki for the installation of the guest addictions but noting to do.

it tells that the right headers for the kernel are unavailable. strange: they are correctly installed.

---

### Post by franco67 on 2011-02-17
with a downgrade of the kernel to 2.6.35, the compilation of guest addiction works.

this is the output:
VirtualBox Guest Additions installer
Removing installed version 4.0.2 of VirtualBox Guest Additions...
Removing existing VirtualBox DKMS kernel modules ...done.
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modulesDoing non-kernel setup of the Guest Additions ...done.
You should restart your guest to make sure the new modules are actually used

Installing the Window System drivers
Warning: unsupported pre-release version of X.Org Server installed.  Not
installing the X.Org drivers.
Installing graphics libraries and desktop services components ...done.

after this I've try to reboot, re-apply the schema for creating a new high res config for xrandr but...
](*,)

---

### Post by vivimonkey on 2011-02-28
Hello?:confused:

---

### Post by foyb on 2011-03-01
> **franco67 said:**
> type the command:
>cvt 1920 1004
you will obtain something similar:

# 1920x1004 59.89 Hz (CVT) hsync: 62.40 kHz; pclk: 159.75 MHz
Modeline "1920x1004_60.00"  159.75  1920 2040 2240 2560  1004 1007 1017 1042 -hsync +vsync

>xrandr
you will obtain something similar:

Screen 0: minimum 640 x 480, current 800 x 600
**default** connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
   1920x1004_60.00   59.9  

the bold word is the output name
if you type this command:
>xrandr --newmode **default** "1920x1004_60.00"  159.75  1920 2040 2240 2560  1004 1007 1017 1042 -hsync +vsync
and then
>xrandr --addmode default 1920x1004_60.00


hi,

i tried your approach, how ever the --newmode param does not expect the screenname as first value;

the first value is the name for the new mode, it will be added to the list of all known modes;

the --addmode command adds the new mode to the list of modes available for your screen, and thats why the first value here is the screenname (in your example, *default*, i get **VBOX0** as the screenname).

After the Guest Additions have been installed, i applied this list of commands to get an acceptable screen resolution for my natty guest (hosted on a maverick installation):


```
$ cvt 1360 640
# 1360x640 59.93 Hz (CVT) hsync: 39.85 kHz; pclk: 69.50 MHz
Modeline "1360x640_60.00"   *69.50  1360 1416 1552 1744  640 643 653 665 -hsync +vsync*

# the italic text is what we actually need for xrandr...

# then add the new mode to the list of available resolutions:
$ xrandr --newmode betterResolution *69.50  1360 1416 1552 1744  640 643 653 665 -hsync +vsync*

# check if the new resolution has been accepted:
$ xrandr
Screen 0: minimum 64 x 64, current 1360 x 640, maximum 32000 x 32000
*VBOX0* connected 1360x640+0+0 0mm x 0mm
   1360x640       60.0*+
   800x600        60.0  
   640x480        60.0  
  [B]betterResolution (0x119)   69.5MHz
        h: width  1360 start 1416 end 1552 total 1744 skew    0 clock   39.9KHz
        v: height  640 start  643 end  653 total  665           clock   59.9Hz[/B]

# since "betterResolution" is shown here, you can proceed with 
# assigning this resolution to the screen
$ xrandr --addmode VBOX0 betterResolution

# after this is done, check if this setting has been accepted:
$ xrandr
Screen 0: minimum 64 x 64, current 1360 x 640, maximum 32000 x 32000
VBOX0 connected 1360x640+0+0 0mm x 0mm
   1360x640       60.0*+
   800x600        60.0  
   640x480        60.0  
   **betterResolution   59.9**

```


after this is done you should be able to set your screen via display properties. In my setup this resolution has survived a reboot.

---

### Post by rubytester on 2011-05-12
I tried the above procedure and got an error when I did xrandr --addmode and I am not sure how to decipher the errors at the end (I am on lenovo w500 laptop running win7 as host, vbox 4.06 and 11.04 as guest. My max win7 resolution is 1680x1050 and I wanted to match that on a guest)
here is my output

[FONT="Courier New"]
cvt 1680 1050
gives me the following entries
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

xrandr --newmode foobar 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr now shows this
Screen 0: minimum 64 x 64, current 1280 x 960, maximum 32000 x 32000
VBOX0 connected 1280x960+0+0 0mm x 0mm
   1024x768       60.0 +
   1280x960       60.0*+
   800x600        60.0  
   640x480        60.0  
  foobar (0x120)  146.2MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz

xrandr --addmode VBOX0 foobar

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  20
  Current serial number in output stream:  21
[/FONT]

---

### Post by ekool on 2011-05-12
Had the same issue as you guys.... 

Followed the instructions at this URL and it's all good... despite the fact it says it's for 10... works on my 11 as well.

[http://scottlinux.com/2010/09/05/ubuntu-10-10-in-virtualbox-resolution-fix/](http://scottlinux.com/2010/09/05/ubuntu-10-10-in-virtualbox-resolution-fix/)

---

### Post by mpollmeier on 2011-09-03
maybe a bit late now, but for other users: the xorg config  files are now located in /usr/share/X11/xorg.conf.d

also see [http://askubuntu.com/questions/37761/xorg-conf-in-ubuntu-natty-11-04](http://askubuntu.com/questions/37761/xorg-conf-in-ubuntu-natty-11-04)

---

### Post by steve7777777 on 2012-05-07
Thanks! This worked for me! Ubuntu 12.04 running in VB, 10.10 is the host system.

---

