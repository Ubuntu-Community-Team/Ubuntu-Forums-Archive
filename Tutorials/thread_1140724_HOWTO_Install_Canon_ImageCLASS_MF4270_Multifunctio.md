---
title: "HOWTO: Install Canon ImageCLASS MF4270 Multifunction driver"
date: 2009-04-27
forum: Tutorials
---

### Post by Francewhoa on 2009-04-27
[COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=4]**Requirements**[/SIZE][/FONT][/COLOR]
 
[LIST]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Ubuntu     8.04 the Hardy Heron[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Printer     must be connected via USB cable.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Printer must be power on.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Gnome     interface[/SIZE][/FONT][/COLOR]
[/LIST]
 

[COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=4]**Note**[/SIZE][/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]The current driver doesn't support all features. But you will be able to print.
[/SIZE][/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]
[/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=4]**Steps**[/SIZE][/FONT][/COLOR]
 
[LIST=1]
[*][FONT=Nimbus Sans L, sans-serif][SIZE=3][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Go     to [URL="http://support-au.canon.com.au/contents/AU/EN/0100270808.html"]http://support-au.canon.com.au/contents/AU/EN/0100270808.html
[/URL][/SIZE][/FONT][/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]If above link doesn't work try the following alternative link [http://support-au.canon.com.au/EN/search?v%3Aproject=ABS-EN&binning-state=model%3D%3DimageCLASS%20MF4270%0Amenu%3D%3DDownload%0Aos%3D%3DLinux&](http://support-au.canon.com.au/EN/search?v%3Aproject=ABS-EN&binning-state=model%3D%3DimageCLASS%20MF4270%0Amenu%3D%3DDownload%0Aos%3D%3DLinux&)[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Scroll     down the page and click on DOWNLOAD link.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Save     the file to a temporary location. Such as DESKTOP
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Right     click on file     'UFR_II_Printer_Driver_for_Linux_Driver_V180_uk_EN'
Select     EXTRACT HERE
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]A     new folder will be created     'UFR_II_Printer_Driver_for_Linux_Driver_V180_uk_EN'
Open this     folder.
Open appropriate folder. If unsure open '32-bit_Driver'     folder.
Open DEBIAN Folder
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Right     click on 'cndrvcups-common_1.80-1_i386.deb' file
Select 'OPEN     WITH GDEBI PACKAGE INSTALLER'
Click on INSTALL PACKAGE button
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Go     back to the same folder.
Right click on     'cndrvcups-ufr2-uk_1.80-1_i386.deb' file
Select 'OPEN WITH GDEBI     PACKAGE INSTALLER'
Click on INSTALL PACKAGE button[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Make sure the printer is connected via USB and power on.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]On     Ubuntu panel/menu. Click on SYSTEM > ADMINISTRATION >     PRINTING
On the left side under LOCAL PRINTERS delete any already     existing Canon printer.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on NEW PRINTER button.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Select     CANON MF4200 SERIES USB #1
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on FORWARD button
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Select     radio button PROVIDE PDD FILE
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on (NONE) drop down menu.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]A     new window will open. 
In the left side column click on FILE     SYSTEM
In the right side column navigate to USR > SHARE >     CUPS > MODEL > Scroll down and select 'CNCUPSMF4200ZK.ppd'
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on OPEN button
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on FORWARD button
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Leave     the PRINTER NAME as is.
Type in a DESCRIPTION. Such as 'Canon     ImageCLASS MF4270 Multifunction'.
Leave the LOCATION as is.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on APPLY button.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Make     sure the printer is connected via a USB cable.
Make sure the     printer is power up.
Under the SETTINGS tab click on PRINT TEST     page.
[/SIZE][/FONT][/COLOR]
[*][LEFT][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]That's     it. You're done. Enjoy
[/SIZE][/FONT][/COLOR]
    [/LEFT]
[/LIST]
 

 [LEFT][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]------------------------------------------------------------------[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT][FONT=Nimbus Sans L, sans-serif][SIZE=3][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]**Most recent Linux drivers for Canon ImageCLASS MF4270 can be found here:**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]
[http://support-au.canon.com.au/EN/search?v%3Aproject=ABS-EN&binning-state=model%3D%3DimageCLASS%20MF4270%0Amenu%3D%3DDownload%0Aos%3D%3DLinux&](http://support-au.canon.com.au/EN/search?v%3Aproject=ABS-EN&binning-state=model%3D%3DimageCLASS%20MF4270%0Amenu%3D%3DDownload%0Aos%3D%3DLinux&)[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/LEFT]
 

 [COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]**How-to source: **[http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html](http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html)[/SIZE][/FONT][/COLOR]

---

### Post by lekifsirk on 2009-06-29
Onopoc,
You are my hero!  Thank you a million times!:KS

---

### Post by rwigle on 2009-07-16
One MINOR edit suggested and one issue:

After 7, the printer needs to be connected and power on. I know that the requirements say printer must be connected via USB cable, but most users will have a new machine with a plug in the USB socket and a big card saying "Do not plug USB cable in until software is installed."

The installation worked fine (as does the printer and copy function).

I have an issue with scanning: XSane doesn't recognize that a scanner is connected, even if I have pushed the scan button before I open XSane. The error message is "no devices available" Did I miss something?

---

### Post by trungd_t on 2009-07-21
> **lekifsirk said:**
> Onopoc,
You are my hero!  Thank you a million times!:KS

I 2nd this. 

I just installed the 64-bit version of the driver, and it too is working. The download package only had 32-bit version for Deb. I installed "alien" and used it to converted the 64-bit rpm to deb with the following commands.

sudo alien --to-deb --scripts cndrvcups-common-1.80-1.x86_64.rpm
sudo alien --to-deb --scripts cndrvcups-ufr2-uk-1.80-1.x86_64.rpm

Files generated: 

cndrvcups-common_1.80-2_amd64.deb
cndrvcups-ufr2-uk_1.80-2_amd64.deb

After installation of the driver, plugged in the USB and powered on the printer, then automatically a "new printer" dialog popup. Just followed the rest of the instructions and finish.

Cheerios,
Trung

---

### Post by quackeroni_pizza on 2009-08-22
This does not work with Jaunty. Any ideas?

---

### Post by onthenarrowpath on 2009-09-02
For me, it neither worked with hardy (or maybe I messed it up). Anyways, [this]("https://answers.launchpad.net/ubuntu/+question/79913") one did it for me, finally, after 4 months of trying and failing.

Hope it helps!

---

### Post by UbunteroTKT on 2010-01-06
Do you have a procedure for Canon ImageCLASS D340?

Thanks.

---

### Post by Papabravo on 2010-01-09
The above procedure worked on my system wtith
Ubuntu 9.04
MF4270 connected via ethernet to my router

just by following the directions after selecting New Printer

---

### Post by Francewhoa on 2010-02-06
Thanks rwigle :) for your comment #3. I updated the how-to.

---

### Post by jonibo on 2010-02-12
With a USB-connected MF4270 and Ubuntu 9.10, I had to make sure that the usblp module was present in order to have the printer detected.  This is contrary to everything else that I've found that claims that Cups 1.4 requires that this module _NOT_ be present.

Additionally, the above-mentioned packages from the Canon site fail to install because they depend on libcupsys2 which has been renamed in Ubuntu/Debian.  The instructions at the following link were sufficient to get around this issue:

[http://ubuntuforums.org/showpost.php?p=8337773&postcount=15](http://ubuntuforums.org/showpost.php?p=8337773&postcount=15)

Perhaps this info can be useful to someone else.  Other than that, the above instructions worked perfectly for me.  Thanks.

---

### Post by buzink on 2010-02-23
better link to download driver:

[http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One%20Printers&series=Laser%20Multifunction&model=imageCLASS%20MF4270&menu=Download](http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One%20Printers&series=Laser%20Multifunction&model=imageCLASS%20MF4270&menu=Download)

---

### Post by 1clue on 2010-04-07
This same exact driver and same exact process works with the Canon MF8050Cn running on Ubuntu 9.10 Karmic Koala 64-bit.

I had some problems because I didn't understand that "alien" is a command which converts an RPM (or whatever) to a Debian package.  However, I used the 2 64-bit RPMs in the archive mentioned in this thread and got the printer going after a bit of fumbling around.

Thanks.

---

### Post by arh1 on 2010-07-30
thanks, Onopoc!

this approach worked for me with 9.04 / Jaunty, and an ImageCLASS MF4690

---

### Post by moffa on 2011-03-28
Got it working with Ethernet as well following the same instructions.  Thank you

---

### Post by millerwjr on 2011-04-03
You are awesome!

I was totally able to get my Canon ImageCLASS MF8050Cn to install and print _***via ethernet***_ with no problems, thanks to your walkthrough!

In fact, I didn't even need anything past step #12. The Printer  Configuration tool was able to find the printer over the network (had to wait a minute for the list to populate) and the drivers were auto-detected after installing  the packages via GDEBI.

Thank you so very much! You saved me a *huge* headache...  :P

Now if I can just get it to scan over the network...

   ... That was a joke. Are you laughing, yet?  :lolflag:

(I'm running Ubuntu 10.04 LTS)

---

### Post by Baji P. on 2011-06-06
The instructions worked great on Ubuntu 10.10 (Meerkat) x86_64 connecting to the printer via ethernet, even though at present time Canon has not offered .deb pkgs for 64-bit.

I used the alien command, posted by Trung on this thread, to create the necessary .deb pkgs from .rpm pkgs

Current Linux driver version is 2.2, the ppd file to be selected is now CNCUPSMF4200ZS.ppd  under  /usr/share/cups/model/

Canon now offers the Linux drivers under their USA support site :

[http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_mf4270](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_mf4270)

thnx => Onopoc !

---

### Post by Baldone on 2011-11-11
> **Onopoc said:**
> [COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=4]**Requirements**[/SIZE][/FONT][/COLOR]
 
[LIST]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Ubuntu     8.04 the Hardy Heron[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Printer     must be connected via USB cable.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Printer must be power on.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Gnome     interface[/SIZE][/FONT][/COLOR]
[/LIST]
 

[COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=4]**Note**[/SIZE][/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]The current driver doesn't support all features. But you will be able to print.
[/SIZE][/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]
[/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=4]**Steps**[/SIZE][/FONT][/COLOR]
 
[LIST=1]
[*][FONT=Nimbus Sans L, sans-serif][SIZE=3][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Go     to [URL="http://support-au.canon.com.au/contents/AU/EN/0100270808.html"]http://support-au.canon.com.au/contents/AU/EN/0100270808.html
[/URL][/SIZE][/FONT][/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]If above link doesn't work try the following alternative link [http://support-au.canon.com.au/EN/search?v%3Aproject=ABS-EN&binning-state=model%3D%3DimageCLASS%20MF4270%0Amenu%3D%3DDownload%0Aos%3D%3DLinux&](http://support-au.canon.com.au/EN/search?v%3Aproject=ABS-EN&binning-state=model%3D%3DimageCLASS%20MF4270%0Amenu%3D%3DDownload%0Aos%3D%3DLinux&)[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Scroll     down the page and click on DOWNLOAD link.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Save     the file to a temporary location. Such as DESKTOP
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Right     click on file     'UFR_II_Printer_Driver_for_Linux_Driver_V180_uk_EN'
Select     EXTRACT HERE
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]A     new folder will be created     'UFR_II_Printer_Driver_for_Linux_Driver_V180_uk_EN'
Open this     folder.
Open appropriate folder. If unsure open '32-bit_Driver'     folder.
Open DEBIAN Folder
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Right     click on 'cndrvcups-common_1.80-1_i386.deb' file
Select 'OPEN     WITH GDEBI PACKAGE INSTALLER'
Click on INSTALL PACKAGE button
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Go     back to the same folder.
Right click on     'cndrvcups-ufr2-uk_1.80-1_i386.deb' file
Select 'OPEN WITH GDEBI     PACKAGE INSTALLER'
Click on INSTALL PACKAGE button[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Make sure the printer is connected via USB and power on.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]On     Ubuntu panel/menu. Click on SYSTEM > ADMINISTRATION >     PRINTING
On the left side under LOCAL PRINTERS delete any already     existing Canon printer.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on NEW PRINTER button.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Select     CANON MF4200 SERIES USB #1
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on FORWARD button
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Select     radio button PROVIDE PDD FILE
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on (NONE) drop down menu.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]A     new window will open. 
In the left side column click on FILE     SYSTEM
In the right side column navigate to USR > SHARE >     CUPS > MODEL > Scroll down and select 'CNCUPSMF4200ZK.ppd'
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on OPEN button
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on FORWARD button
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Leave     the PRINTER NAME as is.
Type in a DESCRIPTION. Such as 'Canon     ImageCLASS MF4270 Multifunction'.
Leave the LOCATION as is.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Click     on APPLY button.
[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]Make     sure the printer is connected via a USB cable.
Make sure the     printer is power up.
Under the SETTINGS tab click on PRINT TEST     page.
[/SIZE][/FONT][/COLOR]
[*][LEFT][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]That's     it. You're done. Enjoy
[/SIZE][/FONT][/COLOR]
    [/LEFT]
[/LIST]
 

 [LEFT][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]------------------------------------------------------------------[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT][FONT=Nimbus Sans L, sans-serif][SIZE=3][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]**Most recent Linux drivers for Canon ImageCLASS MF4270 can be found here:**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]
[http://support-au.canon.com.au/EN/search?v%3Aproject=ABS-EN&binning-state=model%3D%3DimageCLASS%20MF4270%0Amenu%3D%3DDownload%0Aos%3D%3DLinux&](http://support-au.canon.com.au/EN/search?v%3Aproject=ABS-EN&binning-state=model%3D%3DimageCLASS%20MF4270%0Amenu%3D%3DDownload%0Aos%3D%3DLinux&)[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/LEFT]
 

 [COLOR=#000000][FONT=Nimbus Sans L, sans-serif][SIZE=2]**How-to source: **[http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html](http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html)[/SIZE][/FONT][/COLOR]
Hi, when I try to open with GDEBI it gives me the following info: Error: Dependency is not satisfiable: cndrvcups-common (>= 2.30).
What can I do about it?

---

### Post by bakinsoda on 2011-11-14
Does anyone know how to get this to work with a Canon ImageClass D860?  Tried it and had little success.  Thanks.

---

### Post by seajayf on 2012-03-17
works for ubuntu 11.10! Thank you! Thank you! Thank you! Thank you! Thank you! :KS

---

### Post by jirbas on 2012-04-29
just managed to install Canon Imageclass mf4570dn, the driver files goes like Linux_UFRII_PrinterDriver_V240_us_EN, it works both thru usb and over the wireless network, no problems :):)

---

### Post by MishMich on 2012-08-21
Hi,

thanks for taking the trouble to do this. I've been hunting for a driver for my Laserbase MF3220 to do this for a couple of years, but no luck. I contacted Canon, and they said a linux driver was low priority for them, and nor were they prepared to release the proprietary information necessary to write one. So, it is encouraging to see they are releasing for some models. I tried the MF3010, MF4010, and MF4200, in case any of those work with the 3200 series, but no joy.

I wondered if anybody else had had any luck?

I'm stuck with the MF3220 until the two spare laser toner cartridges run out, which at my present rate of consumption will be around 2015! And I really want to hang this off an atom-based file-&-print-server I'm putting together to run this and my Pixma 4000 (which works fine under linux).

---

### Post by omegamormegil on 2012-11-24
Just in case these instructions don't work for someone, I found another thread which resolved my issue with an imageCLASS D420.  According to the thread, this works on Ubuntu 12.04 and 11.10 using the instructions in the first post:

[http://ubuntuforums.org/showthread.php?t=1427330](http://ubuntuforums.org/showthread.php?t=1427330)

---

