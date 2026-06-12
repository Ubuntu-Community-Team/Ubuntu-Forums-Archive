---
title: "HOW-TO Install VAG-COM using Wine"
date: 2006-07-21
forum: Tutorials
---

### Post by palladium on 2006-07-21
Background
VAG-COM ([www.ross-tech.com](www.ross-tech.com)) is an on-board diagnostic (OBD) scanner for Volkswagen Audi Group vehicles. Ross-Tech explicitly state that it is only supported running under Windows. However, others (with more experience than I) have used wine to get it working under Linux in the past. For example:

This post ([http://forums.vwvortex.com/zerothread?id=2698219](http://forums.vwvortex.com/zerothread?id=2698219)) states VAG-COM works under SUSE Linux but provides no description as to how to install it. 
This HOW-TO ([http://autos.groups.yahoo.com/group/VAG-COM/message/4440](http://autos.groups.yahoo.com/group/VAG-COM/message/4440)) from 2001 is too old so I don’t know if it still works. VAG-COM has undergone many updates since then.
This HOW-TO ([http://www.ubuntuforums.org/showthread.php?t=102885](http://www.ubuntuforums.org/showthread.php?t=102885)) from 2005 requires mozactivex and a couple of DLLs. It was probably based on version 504 of VAG-COM but provided me with hope that I could get it to work. 

I have installed the recently released version 607.0 of VAG-COM under Ubuntu Linux. This is how.

System used
VAG-COM Cable = HEX-COM+CAN cable from Ross-Tech. IMPORTANT: This is the serial port version (not USB). I believe that the USB version will not work with Linux because Wine only supports USB devices that are supported by the Linux kernel. 
VAG-COM software = Release 607.0 from Ross-Tech.
Computer = Toshiba 8100 laptop with a Pentium 3 processor and 196 Mb RAM.
OS = Ubuntu (Dapper Drake 6.06 release) freshly installed and updated on 16/7/06. Linux kernel 2.6.15-25-386. 
Wine = Version 0.9.9-0Ubuntu2 from Universe repository. 

Conventions
Text like this:
```
$ cd vag-com
```
Means that you type "cd vag-com", without the quotes or the $ sign, at the prompt of the command-line interface in the user's home directory. That is, just open the terminal and type the command because you should automatically be in the home directory. 
"=>" means this results in …
"->" means the next step is …

HOW-TO Install VAG-COM
1.Install Wine from Universe repository using Synaptic.
2.Create the wine directories and open a configuration window by typing at the command prompt:
```
$ winecfg
```
-> click OK to close the window as no changes are required. 
3.Download Vag-Com-Release-6070-Installer.exe from [www.ross-tech.com](www.ross-tech.com). This is the version of the software for the serial cable. 
4.Move the downloaded file to ~/.wine/drive_c. Tip: If using Nautilus file manager to do this, you have to press Ctrl-H to show the hidden /.wine directory in your user’s home directory.  
5.Run the VAG-COM setup wizard by typing:
```
$ wine c:\vagcom-release-6070-installer.exe
```
=> Setup Wizard should open and behave as if it is a Windows program 
-> Choose to Install to c:\Program Files\VAG-COM.
=> Creates a desktop icon called "VAG-COM Release 607.lnk" on the desktop. 
-> When the installation is complete simply delete this desktop icon as it does not work in linux.
6.Run VAG-COM by typing at the terminal either: 
```
$ cd ".wine/drive_c/Program Files/VAG-COM" && wine vagcom.exe 
```
Or
```
$ sh –c cd ".wine/drive_c/Program Files/VAG-COM" && wine vagcom.exe
```
This can be simplified by optionally creating a desktop icon below.

Create a desktop icon to run VAG-COM 
Unfortunately, running VAG-COM is not as simple as just typing: "wine vagcom.exe" at the home directory command prompt. Even if you have added the VAG-COM path to the wine windows registry, so that it can find the executable, it will not work properly. You need to issue the command from within the VAG-COM directory or VAG-COM will give the error "Can’t Open Codes File: CODES.DAT". The program will then continue but does not work very well. 
The simplest way that I found around this problem (using my very limited knowledge) was to change to the VAG-COM directory before running it. This is effectively what the commands above do but these are a nuisance to type. 
A simple solution is to use a script that performs the change of directory and then runs VAG-COM. Such a script can then be called by a desktop icon. 
7.Create a text file called vagcom.sh which contains the following:
```
cd ~/.wine/drive_c/"Program Files"/VAG-COM
wine vagcom.exe
cd ~
```
8.You can then create a launcher on your desktop by right clicking the desktop 
-> Create Launcher…
-> Name = VAG-COM
-> Command = sh vagcom.sh
9.I believe that those who use a KDE environment may simply be able to add "~/.wine/drive_c/"Program Files"/VAG-COM" to the working directory of a desktop launcher without needing to write a script. Unfortunately, I could not find an equivalent in Gnome. 
Tips:
Linux directory and file names are case sensitive while windows ones are not. Therefore if the name is being used by wine the case does not matter but if used by Linux it does. If you have trouble, pay strict attention to case. 
I have limited experience with Linux and VAG-COM so don’t rely on anything I say.

---

### Post by pat2man on 2006-12-10
I have an older generic USB interface that works with the 311 version, works fine as long as you run:

ln -s /dev/usbTTY0 ~/.wine/dosdevices/com1

Which links the device to the com1 port.

---

### Post by lespedeza on 2006-12-17
Anyone have any luck getting Vag-Com to work under Wine with the Ross-Tech USB interfaces?  

Vag-Com is the only thing I need to use Windows for and it would be nice if I didn't have to boot into Windows to use it.

Any help would be appreciated.

Thanks,

JMK

---

### Post by smitty5533 on 2007-01-23
great guide!  i'm going to try that right-click line when i get home tonight on my tablet pc

---

### Post by triple7 on 2007-07-16
I was able to successfully install my old "ISO-COM" serial VAG-COM in WINE without issue. Here are my stats:

Ubuntu Fiesty Fawn
Wine version: 0.9.41
VAGCOM version: 311.2n
Computer: Dell Latitude D800 Laptop w/built in serial port
Car: 96 VW Passat TDI

I just followed all the default prompts in Wine and VAG-COM. Hooked up the OBD-II connector to the car and was able to connect to the Engine controller and the Air Bag controller. 

Now it's time to completely get ride of my windows partition!

-illya

---

### Post by darrenm on 2007-07-29
> **pat2man said:**
> I have an older generic USB interface that works with the 311 version, works fine as long as you run:

ln -s /dev/usbTTY0 ~/.wine/dosdevices/com1

Which links the device to the com1 port.

I have a 3rd party USB VAG-COM cable which worked fine with VAG-COM in Windows but I can't get it to work with wine. The device gets recognised and the kernel loads the FTDI driver but I get "interface status :3 - not found or not ready" when I try to test the port in VAG-COM. Has anyone seen this? I have /dev/ttyUSB0 symlinked to ~/.wine/dos_devices/com1 and chmodded 777. I'm using VAG-COM 311.2 - N

---

### Post by StarryTripper on 2007-10-08
I'm running 7.10 Beta & VAG-COM 311.2 & 3rd Party serial cable off eBay

Installed Wine with Wine-Doors deb

[http://www.wine-doors.org/wordpress/?page_id=3]("http://www.wine-doors.org/wordpress/?page_id=3")

That was it! Just worked!

md5 of my VAG-COM installer is 1944dd042b7fb754703a9e0967ff48b2

It's not the one currently available on their website, not sure if that makes a difference

---

### Post by darrenm on 2007-10-09
After my post above I got it to work and see the USB device through the serial>USB driver but it wouldnt actually talk to the car.

Are you using a USB or serial cable?

---

### Post by jaripetteri on 2007-10-15
Ross-Tech uses FTDI USB-serial port -chip on they USB adapters and there is support for that on most newer kernels. not sure when it game but should be on 6.10+.

But they use their own pid's on windows drivers so there might be the reason why HEX-USB is not working. I'll do some testing for this asap.

---

### Post by darrenm on 2007-10-16
I'll have another good go too. I had to remove brltty to get the ftdi module to work correctly, now looks like it should work, haven't tried for a while though.

---

### Post by jago25_98 on 2008-08-27
Another trick:
#ln -sf /dev/ttyUSB0 /dev/ttyS0

Also check out **freediag** (remember to try $set interface and scan).
Personally I can't connect to the ECU in Windows or anything. Not sure if it's software, cable or actual ECU.

---

### Post by jaripetteri on 2008-08-27
I might be able to help on that one. What kind of cable you are using and what is your car model and motor type?

---

### Post by jago25_98 on 2008-08-27
ooh, ohh! 
It's:

- VW T4 2.5tdi

- Interface is a cheap Chinese copy, blue with OBD-II written on it. lsusb says `Bus 002 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC` and it was advertised with `FTDI Chip` mentioned, which is the same as the Ross-tech cables from VAGCOM 4-ish

to be exact:
[http://cgi.ebay.co.uk/KKL-VAG-VW-AUDI-OBD2-OBD-USB-CABLE-Diagnose-interface-2_W0QQitemZ320290020369QQcmdZViewItem?hash=item320290020369&_trkparms=72%3A12|39%3A1|66%3A2|65%3A12|240%3A1318&_trksid=p3911.c0.m14](http://cgi.ebay.co.uk/KKL-VAG-VW-AUDI-OBD2-OBD-USB-CABLE-Diagnose-interface-2_W0QQitemZ320290020369QQcmdZViewItem?hash=item320290020369&_trkparms=72%3A12|39%3A1|66%3A2|65%3A12|240%3A1318&_trksid=p3911.c0.m14)

UK ebay item  320290020369

---

### Post by jaripetteri on 2008-08-27
Problem is that V6 engine. Some of theses are a bit tricky and you might not be able to connect on that engine anyway. Problem lies behind the fact that PC serial port is not capable exact 10400 baud speed which is what OBD uses but just very close. Those V6 ECU:s are not that tolerant than most of the ECU:s are.

There are still something you might try. On Windows (sorry) you might drop baud rate from 9600 to 4800 and/or change latency time from 16ms to e.g. 8ms. Those are under USB-serial port setting. Same tricks might work on Ubuntu to.

You also should try to get connect engine running/not running. And putting laptop on charger is also sometimes helped. Warning do not use any inverter but real car laptop charger!

On VAG-COM settings try start baud as 9600 but if not helping put it back what ever the was.

Also you could try with VAG-COM version 311.2. If these are not working you need to get Ross-Techs HEX-series adapter. Those have MCU inside helping to get connected.

---

### Post by jago25_98 on 2008-08-27
Thanks. Tried all that. Tried with freediag scantool (set interfaces tried all), ODBii `Vehicle Explorer` (freeware) and VAGCOM. Vagcom is the only one that makes the car dash audiably tick.

Funny thing is, I had it working before. It's not a V6 engine but a Turbo Diesel. (Transporter campervan)

---

### Post by KamakazieX on 2008-10-22
In lou to my vortex post and being a heavy tester here for the 2681 thinkpad I got a new toy my eee 901. Trying to get Vag Com 311.2 working under wine, i symlinked the usbdev to com1 as everyone else, it works effectively, however, after the first communication with the car is severed, the interface is dead until a reboot. I have also removed the tty package as stated in the earlier post.

Running Ubuntu-Eee 8.04.1 *current

Using Generic FTDI cable

Even if the cable is unplugged and replugged it does not interface with the dongle until a reboot.

Vortex post: [http://forums.vwvortex.com/zeropost?cmd=fshow&id=510](http://forums.vwvortex.com/zeropost?cmd=fshow&id=510)

---

### Post by darrenm on 2008-10-25
I found the same with my EEE 701. Worked for a while, would stop and wouldn't work until a reboot. Never found a solution.

---

### Post by KamakazieX on 2009-01-27
Bump.

Has anyone fixed the buggy ftdi module it is most definitely the issue. If you link it properly it communicates for sure the first handshake (when it pulls the green vin/serial) After that the connection is severed until a reboot, even if the machine is rebooted.

Haven't seen any progress in the couple kernel updates since my last post.

I dont have a windows laptop.. so it would be nice to know where this is heading, or if the genuine hardware is supported and not buggy.

---

### Post by darrenm on 2009-01-27
I doubt it will be fixed to be honest. I think the best way forward is to file a bug and try to contact the original developer. If you can find out what changed a few revisions ago then perhaps the regression can be fixed. It may be something to do with the tickless kernel stuff that was done for power saving a while back. Have you tried the server or i386 kernel?

---

### Post by Purple8 on 2009-02-15
Hi ive got vag com all installed, but it has one major flaw the buttons are all garbled and are a differant size to those in windows. I am running 409.1
Can :confused:anybody help. I am still new to the linux world but finding it great so far.

---

### Post by tamashumi on 2011-07-11
Hi,

I just want to report that for me USB VAG KKL 3rd party cable works under Ubuntu 10.04 and VAG 311.2

Linking the device under ~/.wine/dosdevices does the trick. However the device is /dev/ttyUSB0 in my case. Not /dev/usbTTY0 like writen in previous posts.

EDIT: not for long however. I was able to get info about modules, check errors, etc for a while... During usage however I got communication errors. Linked com1 port become inaccessible every time I tried to use VAG-COM. At the beginning re-connecting usb cable results with another device like /dev/ttyUSB1, ttyUSB2 and so on. I had to link again and it worked for about a minute.

---

### Post by johnrunsubntlnx on 2012-08-31
Hi Guys, I'm trying to get VCDS-Lite with a FT232R generic cable to work on Mac OS X.

I've been following this thread and trying out a lot of different things and I still can't get it to work properly.


Right now VCDS-Lite via Wine can detect the cable and the car when using the "Test" button under Options. But once I try to go into one of the controllers, it gives me a message saying "Cannot connect to the Controller"

Not sure if this matters but when I use the "Test" button, it does say that the latency is poor, so I'm thinking the cable is responding slower that it needs to.

I tried setting the Baud Rate and Latency Timer using this:
[http://www.ftdichip.com/Support/Docu...c%20Driver.pdf](http://www.ftdichip.com/Support/Docu...c%20Driver.pdf)

I'm running out of ideas. Any suggestions on what I can try?

Thanks

---

### Post by jaripetteri on 2012-09-01
> **johnrunsubntlnx said:**
> Hi Guys, I'm trying to get VCDS-Lite with a FT232R generic cable to work on Mac OS X.

I've been following this thread and trying out a lot of different things and I still can't get it to work properly.


Right now VCDS-Lite via Wine can detect the cable and the car when using the "Test" button under Options. But once I try to go into one of the controllers, it gives me a message saying "Cannot connect to the Controller"

Not sure if this matters but when I use the "Test" button, it does say that the latency is poor, so I'm thinking the cable is responding slower that it needs to.

I tried setting the Baud Rate and Latency Timer using this:
[http://www.ftdichip.com/Support/Docu...c%20Driver.pdf](http://www.ftdichip.com/Support/Docu...c%20Driver.pdf)

I'm running out of ideas. Any suggestions on what I can try?

Thanks

What is the car you are trying to connect?

---

### Post by johnrunsubntlnx on 2012-09-01
> **jaripetteri said:**
> What is the car you are trying to connect?

it's a 2003 Audi A4.  And I know both my car and my cable works since I have VCDS working on an older winxp laptop that I have.  But that laptop is so old and so slow so I'd like to use my macbook air instead.

---

### Post by jaripetteri on 2012-09-01
> **johnrunsubntlnx said:**
> it's a 2003 Audi A4.  And I know both my car and my cable works since I have VCDS working on an older winxp laptop that I have.  But that laptop is so old and so slow so I'd like to use my macbook air instead.

If its V6 engine those are sometimes difficult to get connected. Since OBD is using non standard baud rate (10400) it is not possible to make exact that via serial port but very close. So we are playing with tolerances. If you have working environment and you change something it may not work any more. 

There are couple thing you may try thought. You could try older VAG-COM v.311.2 its a bit slower and more tolerant. Put latency on 6ms or even to 0ms.

Another, try to put start baud to 9600 on VCDS/VAG-COM setting.

Try connection while your car engine is running.

Or its something else you are facing there... :)

---

