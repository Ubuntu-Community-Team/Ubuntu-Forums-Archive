---
title: "HOWTO: setup the VFD &amp; IR of Zalman HD160 case"
date: 2006-11-22
forum: Tutorials
---

### Post by falela on 2006-11-22
I have recently built my MythTV on Kubuntu Edgy (my first ever linux) in a Zalman HD160 enclosure. This case comes with a VFD/IR module made by IRTrans. I have been googling on how to enable this little piece of hardware, and the only info I found is [this]("http://www.mythtvtalk.com/forum/viewtopic.php?t=3367").
 IRTrans provides linux drivers on [their website]("http://www.irtrans.de/en/download/linux.php"). Base on the info from the mythtvtalk forum, and a little bit of messing around with the source code, I finally get the hardwares to work. 
**note:** all the commands below are for Debian based distro . If you are using other distro, you are on your own, as I don't know anything about their commands. 

[SIZE="3"]**Prerequisite**[/SIZE]

If you are using a 64 bit system, download the 32 to 64 bit compatibility libraries:
```
sudo apt-get install ia32-libs libc6-i386 libc6-dev-i386
```
Get the checkinstall package:
```
sudo apt-get install checkinstall
```

[SIZE="3"]**Install the softwares**[/SIZE]

[SIZE="2"]**IR Server**[/SIZE]
This is the daemon for receiving the IR signal. According to the README, it replaces the lirc daemon, so you can stop the lircd daemon. Since I don't have other IR device, I don't have any issue stopping it.  If that is not the case for you, you need to check if this irserver is compatible. The last command below pevents lircd from autostart on boot up.
```
cd /etc/init.d
sudo lirc stop
sudo update-rc.d -f lirc remove
```
Don't uninstall it, as the extra tools offered by lirc, e.g. irw, irexec, are quite useful.

Download the compiled version of the server. Decompress the package and copy the program (irserver) to /usr/sbin/ directory:
```
tar -xvzf irserver.tar.gz
chmod 766 ***/path to irserver/***irserver
sudo cp ***/path to irserver/***irserver /usr/sbin
```

Create a 'remotes' directory, this is where the server stores the remote control configuration:
```
sudo mkdir -p /usr/local/share/irtrans/remotes
```
You can create this remotes directory in several other places: **/etc/irserver/remotes**, **/usr/share/irtrans/remotes**, or **~/.irtrans/remotes**. Putting it where is up to you, but I don't recommend putting it in **~/.irtrans/remotes** as the server has no access right to your home during system bootup. Thus, making auto-start fails.
**Note:** Make sure you have only one remotes directory (out of the 4 options above) in your system.

To test run the server, do the following but substitute x with the correct usb port #:
```
irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB*x*
```
Press any button on the remote, you should see some printout on the terminal. Now it is time to setup the remote control.

[SIZE="2"]**Learning the remote control**[/SIZE]
Download the ASCII client off the IRTrans website. The executable is already included in the zip. With the irserver running, run the irclient:
```
cp ***/path to irclient/***
sudo chmod +x irclient
sudo ./irclient localhost
```
The steps to learn the remote are: 
[LIST=1]
[*]Select "2 - Learn" to start learning.
[*]Select "1 - Select remote", I enter 'Zalman' for mine.
[*]Select "2 - Learn Timing". Just press any button on the remote.(note: I am not sure if this step is necessary.)
[*]For each button on the remote, do "3 - Learn Command [Based on timing]". Enter the command name, then press the button on the remote that maps to this name.
**Note:** The server treats the volume knob on your case as 2 IR codes, so you need to learn those as well
[*]After you finish, select "99 - Exit" twice to exit
[/LIST]

**Note:** I have yet to find out the difference between item 3 (Based on timing) and 4 (Command with timing). If someone know, please drop me a note.

A Zalman.rem file is created in /usr/local/share/irtrans/remotes/ directory.  I include a copy of my Zalman.rem config here, in case you don't want to mess with this learning part. I also have a lircrc to use with MythTV. I grabbed this off the web, and make some changes to match my button names. (thanks Jarod Wilson and Hugo van der Kooij for the config file). Copy the lircrc to ~/.mythtv/ directory.
These configs are by no mean perfect.  You certainly need to tweak it to suit your need.

Remove the .txt extension from these files before using them.
[ATTACH]19804[/ATTACH]
[ATTACH]19805[/ATTACH]

[SIZE="2"]**LCD daemon**[/SIZE]
This is actually a forked version of the lcdProc package, so uninstall lcdproc if you have it:
```
sudo apt-get uninstall lcdproc
```
Download the IRTrans lcdproc driver source code and untar it:
```
tar -xvzf ***/path to saved tar/***lcdproc.tar.gz
```
Configure with the irtrans driver, compile and install: 
```
cd ***/path to saved tar/***lcdproc
./configure --enable-drivers=irtrans
make
sudo checkinstall
```
*checkinstall* will ask you some questions about the package (lcdproc). Just enter **lcdproc** in the description field. The default version number is messed up (don't know why), change it back to **0.4.3**.

The daemon *LCDd* is installed in /usr/local/sbin, and the client lcdproc is in /usr/local/bin

Using *checkinstall* to install giving you the ability to uninstall it with your distribution's standard package management utilities(Adept or Synaptic).

Modify the LCD configuration file, it is in the same directory you type checkinstall in. Use your favorite editor, I use nano here:
```
nano LCDd.conf
```
Find this entry in the [server] section and make the change:
```
Foreground=no
```
Chnage other settings (Heartbeat, backlight) according to your preference.

Copy this file to the /etc directory:
```
sudo cp ***/path to saved tar/***lcdproc/LCDd.conf /etc
```
[B][SIZE="3"]
Make the servers autostart[/SIZE][/B]

You can auto start modules by putting the sysV init script in /etc/init.d directory. Use /etc/init.d/skeleton as a template. Here are the 2 scripts I use, remove the .txt extension and copy them to /etc/inid.d/.
[ATTACH]19808[/ATTACH]
[ATTACH]19807[/ATTACH]

```
sudo cp irserver /etc/init.d
sudo cp LCDd /etc/init.d

``` 
Make the scripts executable: 
```
sudo chmod 766 /etc/init.d/irserver
sudo chmod 766 /etc/init.d/LCDd

```
Make them autorun when boot up: 
```
sudo update-rc.d -f irserver start 97 2 3 4 5 .
sudo update-rc.d -f LCDd start 98 2 3 4 5 . 

```
Notes the . at the end. I set the scripts with sequence codes 97 and 98, so that irserver script starts before LCDd script (LCDd depends on irserver).

Reboot and check if these 2 daemons start:
```
ps -e | grep LCDd
ps -e | grep irserver

```
**[SIZE="3"]MythTV[/SIZE]**

Run mythfrontend, go to Setup > Apperance > LCD device display. Enable LCD device. That's it

Enjoy!

---

### Post by timothyp on 2007-04-04
Hi,

I'm using an ASUS EPC945-m8 Barbone system as a MythTV front end.
I can't seem to configure LCDProc to use the built in VFD (what is the meaning of VFD btw?) LCD display.

I think the LCD belongs to a company called Weltrend
The usb id is 040b:7000  as shown by lsusb
```
Bus 005 Device 003: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 040b:7000 Weltrend Semiconductor 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0471:0815 Philips 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:0024 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

```

As always when you try to get help, their forum is offline:
[http://club.aopen.com.tw/forum/](http://club.aopen.com.tw/forum/)

In ubuntu 6.10 I was also able to configure the IR module using Lirc
and mceusb2, but in 7.04 (which I'm using) I cannot compile Lirc nor is the mceusb2 driver included, even though the version of Lirc is correct.

Anyway I'm mostly interested in the LCD, how to get it working.

Oh and for more information about my front-end, check out my bookmarks on the subject: [http://del.icio.us/delegatevoid/mythtv](http://del.icio.us/delegatevoid/mythtv)

---

### Post by El_Matthews on 2007-04-26
Hello, 

Great guide, just what I was lookinf for except that my case is an origenae X10 but the VFD is the same.

Everything works except the remote. when I start the with ```
irserver -codedump -loglevel 4 /dev/ttyUSB0
```the serial number of the VFD appears etc. but when I press a command on my remote nothing appears. The time appears correctly on my VFD so communication to the VFD works correctly.

Any idea where or what I have to look for?

---

### Post by jpgscca on 2007-04-27
Hi,

New to the Ubuntu Forums but here goes...

I'm having the same problem. Mythtv is setup and running but the remote doesn't work. I was able to see the commands by using the "-debug_code" command option to see the commands from the remote.
try this:
```
irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB0
```
Hope this helps.
Still not sure why I can't use the remote.

---

### Post by falela on 2007-05-17
sorry for the late reply.
Did you apt-get mythtv or compile from source.  apt-get should include lircd support.  And remember to copy the renamed lircrc to ~/.mythtv/ directory.
and finally, what did it say when you **ps -e**.  If you follow the steps, it should show irserver, LCDd and mythlcdserver

cheers

---

### Post by timothyp on 2007-05-17
I got lirc-modules or so using apt, compiled the mceusb2 driver 
and the missing step was to copy that file to ~/mythtv/...

Done that now and everything is working :)

(With the exception of the VFD but there seems to be an update lcdproc which I will give a try

---

### Post by El_Matthews on 2007-06-02
everything worked correctly until I updated my system this friday.

Now I have no remote control anymore. even ```
irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB0
``` gives all the info of the ```
IRTRans Send Done: 1
Name   : 
Version: D5.03.08
FW SNo : 20897
Capab  : Power On; 
FW Cap : 3964953
USB SNo: 
Node   : /dev/ttyUSB0

IRServer Version 5.8.04

```
but when I press a button on my remote nothing appears. Anybody the same problem?

PS: I already re-downloaded the src files and recompiled the irserver but same problem. Please help because a mythbox without remote isn't very ussefull.

---

### Post by El_Matthews on 2007-06-05
I don't know how but it works again so you can ignore my question

---

### Post by davidgardner on 2007-07-01
Just wanted to mention, that I couldn't find out how to get LCDd working until I found this post, and I'm not even running Ubunto. The in order to get the LCDd script working for Gentoo I commented out the LSB function include on line 40, and replaced the log_* functions with a call to logger. Hope this will help non-Ubuntu users who stumble upon this post.

---

### Post by BatPenguin on 2007-08-20
Hello everybody,

Great to see a how-to for this case, I'm considering upgrading my system and using this one. Could you answer a very newbie-ish question about the LCD for me, though: what information does it show / what can you set it up to show there? For example: can you show something like "upcoming recordings" etc?

I've been using Mythtv for a year or so now, but I've never had (or seen) a system setup with one of these screens, so I'd be interested to know what it is that you can see from it and how useful you think it is.

Around next month I'll be upgrading pretty much everything in my system (currently Athlong XP 2800, looking at quad cores now) and I'd very much appreciate comments on this case. Also: can you disable the volume knob controls without it affecting the screen? I have a 2-year old daughter who enjoys touching all sorts of volume controls and such...:) Thanks!

---

### Post by rbsdude on 2007-08-20
Hello falela,

Great tute .

I have been trying the Myth tv guide and getting nowhere . So this was a great help . I have the remote working ok , but just need to config the LCD . 

I am going to compile the lcdproc on another machine as my mythbox does not have the right environment , then copy the individual files to the mythbox . After a stab at compiling and making , I noticed that 3 files are created : lcdproc , LCDd and LCDd.conf . I was expecting that there was going to be a forth file : irtrans.so , but did not see it amongst the other files . I thought it would be needed in  /usr/lib/lcdproc/ which is the driver path normally . 

When you compiled yours how many files were created , and where did they get installed ? Much appreciate your help .


RD

---

### Post by rbsdude on 2007-08-21
Its ok . Got it all working now . Was having trouble compiling the lcdproc . It looked like nothing was happening when doping the make . That is resolved by doing a make clean before the make . Now I have all 3 files done ( does not need 4th file irtrans.so if using compiled LCDd and lcdproc) and display is working . When scrolling through myth menus the little display mimics what is being selected on the screen . When watching tv it shows the tv channel info .  All good .

P.S One question , how is the stability of the system when using these compiled binaries from irtrans ? any lockups, freezes or crashes ?


Best regards 

RD

---

### Post by Cuppa-Chino on 2007-10-17
just to ask the question from BatPenguin again, is it possible to use the screen for all types of info:

ie 

* cd track
* tv station
* radio station
* random myth plugins like weather 

thx

---

### Post by BatPenguin on 2007-10-20
> **Cuppa-Chino said:**
> just to ask the question from BatPenguin again, is it possible to use the screen for all types of info:
thx

Hi there, seems like not too many people are reading this thread anymore =).

In any case, I did order the case and just got it the other day with all my new components. So I'll be starting installing and configuring everything possibly as early as tonight. Getting the screen going isn't exactly a top priority at the moment but once I have myth running otherwise and other important stuff like Vmware setup and running, I'll be sure to see just exactly what I can do with the screen.

Depending on how smoothly everything goes, it might take anywhere from a few days to a couple of weeks until I get to it (plenty of things to setup here...), but I'll let you know how it goes.

---

### Post by BatPenguin on 2007-10-27
OK; I got this to work now. For those interested in what this is good for: Myth shows channel information and the menus as you're navigating through them. If the frontend is not active but the backend is recording (back and frontends are on the same machine for me), the display will show "Recording..." and the program information. Pretty neat.

I'm also using Lirc to handle a PVR-150 IR blaster for channel changes so it works fine with Lirc active as well. 

Anyway, I have a question: when myth is not doing anything, the text shown is:

LCDproc Server
Clients: 0

How do I change this? I'd like it to say something, ummm, more interesing =) Didn't see a line for that in the config file.

Also, is there a way to change what the display says when the computer is OFF. As I remember it, it used to be the clock...now it's nothing before I boot up. I'd appreciate some tips on how to change these things. Thanks!

---

### Post by BatPenguin on 2007-11-17
Haven't seen any replies so I'll try again: has anybody managed to customize the settings any more? Like print stuff from other programs / scrpts besides Myth to the screen? My hope is to get the screen to (upon shutdown) print the name and time of the next recording on the LCD. Anybody have any idea how this could be done? At the moment I have a mythshutdown scrip that writes the wake-up time to the system BIOS, I'd just like to add to that so that it also prints the time to the screen (and leaves it there). The whole point being that even when the box is turned off I could still see when and what is the next recording - and yeah, not exactly curing cancer this trick but I think it'd be neat :)

Any ideas? Thanks.

---

### Post by orasetaina on 2007-11-19
hi.
i have a thermaltake mozart sx and was wondering if this method would on it?

Also is there anyway of making the vfd work without mythbuntu..im running normal gutsy!!!

appreciate your replies! 
:)

---

### Post by BatPenguin on 2007-12-08
> **orasetaina said:**
> 
Also is there anyway of making the vfd work without mythbuntu..im running normal gutsy!!!


Hi there. I'm running normal Gutsy as well, no mythbuntu, and this works fine.

I'm still hoping that someone would give me a tip on how to print stuff on the screen manually / via a script so I could use it more. The default myth support is very nice, though.

---

### Post by straightv6 on 2007-12-24
When I run ```
irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB0
```

I get "Could not open IP socket"

Can anyone tell me why this is happening?

---

### Post by luckyfourleaf on 2007-12-31
> **straightv6 said:**
> When I run ```
irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB0
```

I get "Could not open IP socket"

Can anyone tell me why this is happening?

I had the same problem, but also noticed ttyUSB0 did not exist in /dev. Someone pointed out through their site that they solved this issue by taking a closer look at the USB connection to the mother board... turns out they had it plugged in wrong, and so did I.

  Now I have a new problem: I've installed all of the 32 - 64 compatibility packages as instructed in this thread (Mythbuntu 7.10), but I continually get a new error when running the command ```
irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB0
```. It throws out ```
Error executing the 64Bit IRServer
```. Really irritating, especially because searches on this error return NOTHING.  Perhaps it is something simple...  someone help! I need my remote to work, or my wife will continue to call my MythTV box the "I Told You So".  Good times :oops:

---

### Post by joe_user on 2008-02-04
I have the same thing going on... I am using Fedora 8. AMD x86_64
I have noticed a couple things...

1)  If I am in the /usr/local/irtrans dir and exec the startup script (/etc/init.d/irserver64)  or exec the irserver or irserver64 script it will work perfect

[dagon] /usr/local/irtrans 135> p irserver64
UID        PID  PPID  C STIME TTY          TIME CMD
root      4215     1  0 18:06 ?        00:00:00 /usr/local/irtrans/irserver64 -daemon -pidfile /var/run/irserver64 -loglevel 2 -logfile /var/log/irserver64.log /dev/ttyUSB0


2) If I am not in the directory and exec the irserver cmd it will throw this error:  (irserver is able to detect platforms and automajically call on irserver64... or so it says...)

[dagon] /usr/local 119> sudo /usr/local/irtrans/irserver -daemon -pidfile /var/run/irserver -loglevel 2 -logfile /var/log/irserver64.log /dev/ttyUSB0
Error executing the 64Bit IRServer

3) If I am not in the directory and exec the irserver64 cmd it will appear to start, but really does nothing... if you look at the logs dir it complains about not seeing the remotes dir

[dagon] /usr/local 131> cat /var/log/irserver64.log
IRServer Version 5.9.07
[ 0]:                      D5.03.08     SN: 18706
Could not open Remote Database (No folder 'remotes' / Access rights ?)



....so I am pretty much stuck with trying to figure out how to code my startup script to see the remotes dir to it can startup on reboot....  and suggestions?

---

### Post by bau on 2008-02-13
Hi,
I followed also the instruction, but the RC does not work. I dicovered the following:
with ps -ef | grep irserver it is running, but with my login. when I stop the service and start it with sudo comand again it is running as root. When I start now the frontend of mythtv again it works!
I have tried the start as mentioned with update-rc and also to edit the rc.local but both times the service is started under my login and not as root.
My question is where to put the shell script or the start command of irserver to be run on root level.
I am running Mythbuntu 7.10

---

### Post by karlec on 2008-04-07
Good tutorial, worked as advertised!:)
Has anyone been able to get the MCE keyboard to work ?  The download comes with a mce-keyboard.rem in the remotes db, the multimedia keys work but not the regular keys.

---

### Post by muppet(au) on 2008-08-02
G'day all,

Totally new to linux and have just crossed to "the dark side" from mce2005.
I am running Mythbuntu 8.0.4.1 i386 version.
After 3 days of endless googling and reading up on what the hell I am doing in terminal, I purchased this case based on this howto.

Very impressed so far:)

I have the remote working fine and the lcd has suddenly changed from "welcome to htpc" to the correct date and time etc after doing all the steps.

My 1st question is, should the lcd show anything else other than the date and time?? (and yes, I have done the lcd thing in mythtv frontend)

2nd question, mythbuntu wants to install a newer version of lcdproc.....should I do it or not and where would I find it after it installs???? I am worried I will bork what good I have done so far.

Please remember I am using mythbuntu 8.0.4.1 , not ubuntu or kubuntu.

Thanks.

---

### Post by BatPenguin on 2008-08-02
> **muppet(au) said:**
> G'day all,

Totally new to linux and have just crossed to "the dark side" from mce2005.
I am running Mythbuntu 8.0.4.1 i386 version.
After 3 days of endless googling and reading up on what the hell I am doing in terminal, I purchased this case based on this howto.

Very impressed so far:)

I have the remote working fine and the lcd has suddenly changed from "welcome to htpc" to the correct date and time etc after doing all the steps.

My 1st question is, should the lcd show anything else other than the date and time?? (and yes, I have done the lcd thing in mythtv frontend)

2nd question, mythbuntu wants to install a newer version of lcdproc.....should I do it or not and where would I find it after it installs???? I am worried I will bork what good I have done so far.

Please remember I am using mythbuntu 8.0.4.1 , not ubuntu or kubuntu.

Thanks.

Hi Muppet, welcome to Ubuntu :)

I wouldn't update lcdproc since I believe the IRtrans version is different from the normal, at least these instructions at the beginning of the thread say so (not 100% sure about this though, it might work just fine now). Anyway, updating might force you to reinstall the package from the web site. Actually: If your machine is a Myth server and you don't have any issues with any of these remote/lcd things, I wouldn't update Lirc, Lcdproc etc. unless you know what the update is going to do/fix. I at least try to usually avoid unnecessary hassle when it comes to Myth. I have some of these (lirc etc.) actually locked to current versions because of this, I've had to recompile modules too many times before because of updates. The new versions of Ubuntu come every 6 months so that's a nice time interval for recompiling lirc etc. modules, in my mind :) 

The LCD should be showing the names of menus when you navigate through them and the names of programs when watching TV. Does yours not do this? The Setup->Appereance menu in the frontend has all the options for what to show, you should be seeing whatever you've setup there when using Myth.

---

### Post by Jpps on 2008-08-27
Hi,

I'm trying to setup HTPC with Zalmans HD160Plus, but I'm having trouble at getting the remote and VDF to work.

The How-to posted on this thread is a little old and apparently some things have changed since.

1st, IRTrans provides their own 64bit binaries from their site: [http://www.irtrans.de/en/download/linux.php](http://www.irtrans.de/en/download/linux.php)

So I skipped straight to the install part. But when I tried to test/run the irserver I found out that my system is missing /dev/ttyUSBx !!

lsusb shows this:
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 15c2:0038 SoundGraph Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 0000:0000  
So it should be properly connected as SoundGraph shows in the list.

Mouse and Canon digital camera work perfectly with the USB.

I'm running 2.6.24-19-generic Ubuntu. I tried a fresh install from the CD, but still no luck at finding /dev/ttyUSBx.

Could someone who have succeeded at getting Z160 to work please give me some poitters what could be the problem?

---

### Post by Mattias on 2008-09-07
I also have a Zalman 160 plus and using Hardy
Has anybody succeeded in making the irtrans work. I don seem to be having a /dev/ttyUSB0 device. As far as i can tell I have made all the necessary connections ....
Thank you in advance to any help 
/Mattias

EDIT: I´m closer now that I´ve realised that the plus version uses imonlcd driver not irtrans, this has been changed for the plus version. I´ve so far gotten the LCD display to work, still some work left on the lirc functionality. A quick google on the lsusb identity of 15c2:0038 SoundGraph Inc
gives some insight to how to get it working. e.g. [http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html](http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html)

---

### Post by Bloemetjesgordijn on 2008-11-03
Can you please help me??


> **falela said:**
> 
Reboot and check if these 2 daemons start:
```
ps -e | grep LCDd
ps -e | grep irserver

```


If I enter the above mentioned commands nothing happens

And when I enter in my terminal:
sudo LCDd of LCDd

It replies: "Error connecting to irtrans server localhost"

I am lost here...

Any help is appreciated


Kind regards,

Bloemetjesgordijn

---

### Post by BatPenguin on 2008-11-04
> **Bloemetjesgordijn said:**
> Can you please help me??




If I enter the above mentioned commands nothing happens

And when I enter in my terminal:
sudo LCDd of LCDd

It replies: "Error connecting to irtrans server localhost"

I am lost here...

Any help is appreciated


Kind regards,

Bloemetjesgordijn

Looks like the irserver daemon is not starting. Try:

```
sudo /etc/init.d/irserver start
```

and see if that starts it. My guess is your init scripts are not set up properly or starting for some reason.

---

### Post by Bloemetjesgordijn on 2008-11-04
Nope didnt work

It says "Error executing the 64Bit IRServer"

Furthermore date & time on the display are gone now *Bummer*

Pretty expensive stuff for an LCD with only "Welcome to HTPC" :lolflag:


It works !!!!!!!
I had to start Irserver 64 bits instead of irserver


Great  thx "BatPenguin"

---

### Post by Orfeous on 2009-01-27
i cant get the irserver working for my case :(
this is whats happen...

```
xbmc@xbmc:/usr/local/share/irtrans$ sudo ./irserver -codedump -loglevel 4 -logfile irserver.log /dev/ttyUSB0

Init Server Socket done
Init Events done
IRTRans Send status: 0 - 0
IRTRans Send status: 0 - 0
IRTRans Send status: 1 - 11
IRTRans Send status: 0 - 0
IRTRans Send Done: 4
Init communication ...
Error opening COM/USB Port / LAN Device
```

dmesg output..

```
[   14.268039] USB Serial support registered for FTDI USB Serial Device
[   14.268118] ftdi_sio 6-1:1.0: FTDI USB Serial Device converter detected
[   14.268159] usb 6-1: Detected FT232BM
[   14.268219] usb 6-1: FTDI USB Serial Device converter now attached to ttyUSB0
[   14.268232] usbcore: registered new interface driver ftdi_sio
[   14.268235] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver

```


lsusb output for the irtrans device
```
Bus 006 Device 002: ID 0403:fc60 Future Technology Devices International, Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0xfc60
  bcdDevice            4.00
  iManufacturer           1 MConsult
  iProduct                2 IRTrans USB
  iSerial                 3 MMUN0000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 IRTrans USB
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)
```

lsusb finds the device and uses ftdio_serial module and assigns it to /dev/ttyUSB0 as i can see in kernel boot.

but it seems that i cant access it.. what can i try?

---

### Post by aynema on 2009-03-30
I'm having an issue with a Origin X10 case which uses the same VFD & IR module.
I previously had it working fine but its now stopped working. I've also tried re-installing Mythbuntu and even tried Mythdora.
Pretty much every thing appears to work and the VFD does work fine and shows what's happening in mythtv etc but the Remote doesn't work at all.
I've run both irw and irclient and pressing buttons on the remote show nothing. Thinking it may be a broken remote I've tried a different one but still nothing.
Any idea's

---

### Post by Bloemetjesgordijn on 2009-03-31
sorry guys,

I cant help you, I am in over my head

I got it working with help of the folowing treads/forums
[http://www.distantlogic.com/zalman.html](http://www.distantlogic.com/zalman.html)

and
[http://spawn.sin.khk.be/public/htpc/](http://spawn.sin.khk.be/public/htpc/)

Good luck

Bloemetjesgordijn

---

### Post by zdessa on 2009-09-18
> **BatPenguin said:**
> Looks like the irserver daemon is not starting. Try:

```
sudo /etc/init.d/irserver start
```and see if that starts it. My guess is your init scripts are not set up properly or starting for some reason.

 I am having the same problem. The LCDdproc script executes at login because i can see the screen change then quickly shuts off. I f i manually enter the command ```
 sudo /etc/init.d/LCDd start
``` then it works. Anyone know how i should modify the script so it automatically starts during startup? 

Thanks

---

### Post by gregms on 2009-10-12
I'm trying to use the Hulu Desktop client for linux but it requires that lircd be ran with the -r (--release) switch. It suggests adding the line REMOTE_LIRCD_ARGS="-r" to the hardware.conf file, but I don't use a hardware.conf file with the IRTrans setup.

Any idea on how to add in the -r into this setup?
-Greg

---

### Post by GoMad on 2009-11-13
Batpenguin / falele -  what motherboard did you use ?  I was looking at the msi media diva board that takes the AM2+ AMD chips (AM3 with bios upgrade).
 
I also read these are primarily for Windowms, did you get dual dispalys to work, ie tv on tv, with the lcd display showing status etc. ?
 
Also, the ase build quality, is it all metal ?  
 
My main concern is the depth of it :-(  Micro AT would be better. I have a separate mythtv backend so might stick a 32GB SSD disk in it as it won't be storing much.
 
Thanks - if you are still reading.
 
GoMad.

---

### Post by BatPenguin on 2009-11-13
> **GoMad said:**
> Batpenguin / falele -  what motherboard did you use ?

Hi there,

Yes, I still read this at least, have it subscribed :)

I have the Abit AB9 QuadGT LGA775 ATX with the Intel Core 2 Quad Q6700 2.66GHz in it. It's been really good. I think it's actually a pretty roomy case, I haven't had that much trouble with it, I have a Geforce 8800GT in it, it's not the smallest card available.

If you're just building a frontend for Myth, I'd go with something smaller and a micro-at, yes. I use this as a combined backend/frontend + general living room computer, connected to an LCD tv. For just a frontend, I think this would be mighty big+noisy, I'd go for something smaller.

---

### Post by Veabers on 2009-11-27
Orfeous,

Did you solve your problem? I am having the exact same problem when I run the server it exits with the error Error opening COM/USB Port / LAN Device.

---

### Post by Veabers on 2009-11-28
> **Veabers said:**
> Orfeous,

Did you solve your problem? I am having the exact same problem when I run the server it exits with the error Error opening COM/USB Port / LAN Device.


As an update in case anyone else find this post I solved my problem.

I found the following set of instructions. [http://ubuntuforums.org/showthread.php?p=835460]("http://ubuntuforums.org/showthread.php?p=8354600")

This stopped the "Error opening COM/USB Port / LAN Device." error from displaying when starting the server.

The last change I had to make was in the mythfrontend under the general setting in the Remote Control section change the LIRCD Daemon Socket path from /var/run/lirc/lircd to /dev/lircd.

---

### Post by barroj on 2010-05-17
Excuse me for not posting in the right place, but I have the same case - Zalman HD160XT case.  I believe mine is revision 3, but it is not the "Plus" version.  

I'm at a loss because I don't seem to have a /dev/ttyUSBx device.  When I issue the lsusb command, it only shows the following:

```
root@htpc:~# lsusb
Bus 008 Device 002: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 154b:000f PNY 
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

When I issue the cat /proc/usb/devices, I receive the message "no such file or directory."  When I attempt to issue the "mount -t usbfs none /proc/bus/usb" I receive the message "/proc/bus/usb does not exist".

I'm also using an ASUS P5P43TD motherboard with an Intel Core 2 Quad Q9400 Processor BX80580Q9400 - 2.66GHz with 4GB of RAM and an nVidia GeForce GTS 250 video card.  I am using mythbuntu version 10.04 installed as a new mythbuntu install with all updates applied.

I've checked my connections, and it appears I have everything connected properly.  The 7" LCD screen works with the touch screen, the card reader works, the USB devices work, the power switch and power LED work, CD/DVD player, SATA hard drives, etc. all work.

I'm hoping that someone else out there with this same type of case can help me - anything I can look for to determine that it is not a defective cable somewhere?  Any help is appreciated. 

If you require additional information, I would most gladly submit it.

Cheers,
John

---

### Post by lpt2007 on 2011-05-29
> **falela said:**
> I have recently built my MythTV on Kubuntu Edgy (my first ever linux) in a Zalman HD160 enclosure. This case comes with a VFD/IR module made by IRTrans. I have been googling on how to enable this little piece of hardware, and the only info I found is [this]("http://www.mythtvtalk.com/forum/viewtopic.php?t=3367").
 IRTrans provides linux drivers on [their website]("http://www.irtrans.de/en/download/linux.php"). Base on the info from the mythtvtalk forum, and a little bit of messing around with the source code, I finally get the hardwares to work. 
**note:** all the commands below are for Debian based distro . If you are using other distro, you are on your own, as I don't know anything about their commands. 

[SIZE="3"]**Prerequisite**[/SIZE]

If you are using a 64 bit system, download the 32 to 64 bit compatibility libraries:
```
sudo apt-get install ia32-libs libc6-i386 libc6-dev-i386
```
Get the checkinstall package:
```
sudo apt-get install checkinstall
```

[SIZE="3"]**Install the softwares**[/SIZE]

[SIZE="2"]**IR Server**[/SIZE]
This is the daemon for receiving the IR signal. According to the README, it replaces the lirc daemon, so you can stop the lircd daemon. Since I don't have other IR device, I don't have any issue stopping it.  If that is not the case for you, you need to check if this irserver is compatible. The last command below pevents lircd from autostart on boot up.
```
cd /etc/init.d
sudo lirc stop
sudo update-rc.d -f lirc remove
```
Don't uninstall it, as the extra tools offered by lirc, e.g. irw, irexec, are quite useful.

Download the compiled version of the server. Decompress the package and copy the program (irserver) to /usr/sbin/ directory:
```
tar -xvzf irserver.tar.gz
chmod 766 ***/path to irserver/***irserver
sudo cp ***/path to irserver/***irserver /usr/sbin
```

Create a 'remotes' directory, this is where the server stores the remote control configuration:
```
sudo mkdir -p /usr/local/share/irtrans/remotes
```
You can create this remotes directory in several other places: **/etc/irserver/remotes**, **/usr/share/irtrans/remotes**, or **~/.irtrans/remotes**. Putting it where is up to you, but I don't recommend putting it in **~/.irtrans/remotes** as the server has no access right to your home during system bootup. Thus, making auto-start fails.
**Note:** Make sure you have only one remotes directory (out of the 4 options above) in your system.

To test run the server, do the following but substitute x with the correct usb port #:
```
irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB*x*
```
Press any button on the remote, you should see some printout on the terminal. Now it is time to setup the remote control.

[SIZE="2"]**Learning the remote control**[/SIZE]
Download the ASCII client off the IRTrans website. The executable is already included in the zip. With the irserver running, run the irclient:
```
cp ***/path to irclient/***
sudo chmod +x irclient
sudo ./irclient localhost
```
The steps to learn the remote are: 
[LIST=1]
[*]Select "2 - Learn" to start learning.
[*]Select "1 - Select remote", I enter 'Zalman' for mine.
[*]Select "2 - Learn Timing". Just press any button on the remote.(note: I am not sure if this step is necessary.)
[*]For each button on the remote, do "3 - Learn Command [Based on timing]". Enter the command name, then press the button on the remote that maps to this name.
**Note:** The server treats the volume knob on your case as 2 IR codes, so you need to learn those as well
[*]After you finish, select "99 - Exit" twice to exit
[/LIST]

**Note:** I have yet to find out the difference between item 3 (Based on timing) and 4 (Command with timing). If someone know, please drop me a note.

A Zalman.rem file is created in /usr/local/share/irtrans/remotes/ directory.  I include a copy of my Zalman.rem config here, in case you don't want to mess with this learning part. I also have a lircrc to use with MythTV. I grabbed this off the web, and make some changes to match my button names. (thanks Jarod Wilson and Hugo van der Kooij for the config file). Copy the lircrc to ~/.mythtv/ directory.
These configs are by no mean perfect.  You certainly need to tweak it to suit your need.

Remove the .txt extension from these files before using them.
[ATTACH]19804[/ATTACH]
[ATTACH]19805[/ATTACH]

[SIZE="2"]**LCD daemon**[/SIZE]
This is actually a forked version of the lcdProc package, so uninstall lcdproc if you have it:
```
sudo apt-get uninstall lcdproc
```
Download the IRTrans lcdproc driver source code and untar it:
```
tar -xvzf ***/path to saved tar/***lcdproc.tar.gz
```
Configure with the irtrans driver, compile and install: 
```
cd ***/path to saved tar/***lcdproc
./configure --enable-drivers=irtrans
make
sudo checkinstall
```
*checkinstall* will ask you some questions about the package (lcdproc). Just enter **lcdproc** in the description field. The default version number is messed up (don't know why), change it back to **0.4.3**.

The daemon *LCDd* is installed in /usr/local/sbin, and the client lcdproc is in /usr/local/bin

Using *checkinstall* to install giving you the ability to uninstall it with your distribution's standard package management utilities(Adept or Synaptic).

Modify the LCD configuration file, it is in the same directory you type checkinstall in. Use your favorite editor, I use nano here:
```
nano LCDd.conf
```
Find this entry in the [server] section and make the change:
```
Foreground=no
```
Chnage other settings (Heartbeat, backlight) according to your preference.

Copy this file to the /etc directory:
```
sudo cp ***/path to saved tar/***lcdproc/LCDd.conf /etc
```
[B][SIZE="3"]
Make the servers autostart[/SIZE][/B]

You can auto start modules by putting the sysV init script in /etc/init.d directory. Use /etc/init.d/skeleton as a template. Here are the 2 scripts I use, remove the .txt extension and copy them to /etc/inid.d/.
[ATTACH]19808[/ATTACH]
[ATTACH]19807[/ATTACH]

```
sudo cp irserver /etc/init.d
sudo cp LCDd /etc/init.d

``` 
Make the scripts executable: 
```
sudo chmod 766 /etc/init.d/irserver
sudo chmod 766 /etc/init.d/LCDd

```
Make them autorun when boot up: 
```
sudo update-rc.d -f irserver start 97 2 3 4 5 .
sudo update-rc.d -f LCDd start 98 2 3 4 5 . 

```
Notes the . at the end. I set the scripts with sequence codes 97 and 98, so that irserver script starts before LCDd script (LCDd depends on irserver).

Reboot and check if these 2 daemons start:
```
ps -e | grep LCDd
ps -e | grep irserver

```
**[SIZE="3"]MythTV[/SIZE]**

Run mythfrontend, go to Setup > Apperance > LCD device display. Enable LCD device. That's it

Enjoy!

Can I use this HOWTO for Vlsys M-PLAY 202 Plus?

LINK: [http://www.vlsys.co.kr/English/product_mplay202plus.php](http://www.vlsys.co.kr/English/product_mplay202plus.php)

---

### Post by mstrommer on 2012-08-26
Thank you very much for this very useful tutorial.

I am using XBMC and the only step to complete to make the remote work with XMBC was to update the  /usr/share/xbmc/system/Lircmap.xml file.

I have used your sample Zalman.rem file for irtrans configuration. Copied the remote section for mediacenter remote and changed the device to zalman. 

```
<remote device="mediacenter"> ... </remote>
```

```
<remote device="zalman"> ... </remote>
```

I also enabled "remote sends keyboard presses"  in XBMC -> System -> System -> Input settings.

Works like a charm. Ubuntu 12.4, XMBC 11 and Zalman 160 with irtrans.

---

