---
title: "HOWTO: Epson Perfection 1670 Scanner (and other SnapScan scanners)"
date: 2005-04-14
forum: Tutorials
---

### Post by Remix_88 on 2005-04-14
**HOWTO: Epson Perfection 1670 Scanner**

The scanner firmware comes in a file called ESFW30.BIN, which apparently is only available if you install the software on the CD-ROM provided with the scanner. Unfortunately, the software only installs under Windows and then you have to copy the software from the Windows machine to the linux machine. Or you can follow this simple process to download the firmware (provided by Jeff Silverman) and then update your /etc/sane/saned.conf 

```
$ wget http://www.commercialventvac.com/~jeffs/ESFW30.BIN
$ sudo cp ESFW30.BIN /etc/sane.d
```

Edit /etc/saned.d/snapscan.conf and change the line...

firmware /path/to/your/firmware/file.bin

...to point to /etc/sane.d/ESFW30.BIN

```
$ scanimage -L
```

You should see that your scanner is now detected. If so, you can now scan using XSane.

**Other Similar Scanners - [http://snapscan.sourceforge.net](http://snapscan.sourceforge.net)**

The process should be the very similar (you should just need to appropriate firmware) for other snapscan scanners. See the SnapScan Backend for SANE page for more details about the following scanners...

Acer / Benq	300f	SCSI	
Acer / Benq	310s	SCSI	
Acer / Benq	610s	SCSI	
Acer / Benq	620S	SCSI	
Acer / Benq	620ST	SCSI	
Acer / Benq	620+	SCSI	
Acer / Benq	640s	SCSI	
Acer / Benq	310U	USB
Acer / Benq	320U	USB	
Acer / Benq	340U	USB	
Acer / Benq	620U	USB	
Acer / Benq	620UT	USB	
Acer / Benq	640U	USB	
Acer / Benq	640UT	USB	
Acer / Benq	640BU	USB	
Acer / Benq	640BT	USB
Acer / Benq	1240	USB	
Acer / Benq	3300	USB
Acer / Benq	4300	USB	
Acer / Benq	5000	USB
Acer / Benq	5300	USB	
Agfa	SnapScan 300	SCSI	
Agfa	SnapScan 310s	SCSI	
Agfa	SnapScan 600	SCSI	
Agfa	SnapScan 1236s	SCSI	
Agfa	SnapScan 1236u	USB	
Agfa	SnapScan 1212U	USB	
Agfa	SnapScan e10	USB
Agfa	SnapScan e20	USB	
Agfa	SnapScan e25	USB	
Agfa	SnapScan e26	USB	
Agfa	SnapScan e40	USB	
Agfa	SnapScan e42	USB	
Agfa	SnapScan e50	USB	
Agfa	SnapScan e52	USB	
Agfa	Arcus 1200	SCSI
Epson	Perfection 660	USB
Epson	Perfection 1270	USB
Epson	Perfection 1670	USB
Epson	Perfection 2480	USB
Epson	Perfection 2580	USB
Guillemot / Hercules	MaxiScan A4 Deluxe	SCSI	
Guillemot / Hercules	Scan @home Touch 1248	USB
Guillemot / Hercules	Maxi A4 36bit		USB
Mitsubishi 		Diamondview 648UT	USB
Mitsubishi		Diamondview 650U	USB

**Reference**

 - [http://www.commercialventvac.com/~jeffs/epson1670andFedora.html](http://www.commercialventvac.com/~jeffs/epson1670andFedora.html)
 - [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

---

### Post by chunk on 2006-02-06
[QUOTE=Remix_88]http://www.commercialventvac.com/~jeffs/ESFW30.BIN[/QUOTE]

Mirrored here:
[http://leroybrown.glassmelter.com/binaries/ESFW30.BIN](http://leroybrown.glassmelter.com/binaries/ESFW30.BIN)

---

### Post by bernardfrancois on 2006-03-20
[QUOTE=Remix_88]
Edit /etc/saned.d/snapscan.conf and change the line...
[/quote]
Little typo: it should be **sane.d**

I just successfully installed my Agfa Snapscan e25 with this howto. Thanks a lot!
I found my specific firmware at [http://drivermagic.co.nz/p/nph-detail.php?a=1221](http://drivermagic.co.nz/p/nph-detail.php?a=1221)
This site also includes firmware for other snapscan versions.

I also uploaded the files to my webspace on my ISP. You can find it here:
[http://www.evonet.be/~bfran/extern/snapscan-firmware/](http://www.evonet.be/~bfran/extern/snapscan-firmware/)
It includes the following files:
```

snap1212p.bin
snap1212u.bin
Snape10.bin
snape20.bin
Snape22.bin
Snape25.bin
snape26.bin
Snape40.bin
Snape42.bin
Snape50.bin
Snape52.bin
SnapScan 1212P_2.bin
SnapScan1212P_2.bin
SnapScan 1212U_2.bin
SnapScan1212U_2.bin

```
If you read this and you need one of these files and none of the above links work any more, and using a search engine to look for them doesn't give any results, then please contact me.

Am I violating copyright by distributing this firmware? If so, I'll remove it.

---

### Post by edopizza on 2006-03-24
I have an Agfa Snapscan e40 that is not working. 

lsusb says: 
Bus 001 Device 002: ID 06bd:208d AGFA-Gevaert NV Snapscan e40
Bus 001 Device 001: ID 0000:0000

I tried 2 configuations: 

First: 
cp ESFW30.BIN in /etc/sane/saned.conf 

and edited the line 
firmware /etc/sane/ESFW30.BIN 
in /etc/saned.d/snapscan.conf 

Second: 
cp Snape40.bin in /etc/sane/saned.conf 

and edited the line 
firmware /etc/sane/Snape40.bin 
in /etc/saned.d/snapscan.conf 

scanimage -L just returns to a new line and the cursor blinks without showing the path for a couple of seconds and after reports that no scanner was found. 

On x, xsane reports "no device available". 

The strange thing is that just after the first ubuntu 5.10 installation the scanner use to work properly. The problem started after the reboot of the first update/upgrade. 

Do I need to configure something more? 





[QUOTE=bernardfrancois]Little typo: it should be **sane.d**

I just successfully installed my Agfa Snapscan e25 with this howto. Thanks a lot!
I found my specific firmware at [http://drivermagic.co.nz/p/nph-detail.php?a=1221](http://drivermagic.co.nz/p/nph-detail.php?a=1221)
This site also includes firmware for other snapscan versions.

I also uploaded the files to my webspace on my ISP. You can find it here:
[http://www.evonet.be/~bfran/extern/snapscan-firmware/](http://www.evonet.be/~bfran/extern/snapscan-firmware/)
It includes the following files:
```

snap1212p.bin
snap1212u.bin
Snape10.bin
snape20.bin
Snape22.bin
Snape25.bin
snape26.bin
Snape40.bin
Snape42.bin
Snape50.bin
Snape52.bin
SnapScan 1212P_2.bin
SnapScan1212P_2.bin
SnapScan 1212U_2.bin
SnapScan1212U_2.bin

```
If you read this and you need one of these files and none of the above links work any more, and using a search engine to look for them doesn't give any results, then please contact me.

Am I violating copyright by distributing this firmware? If so, I'll remove it.[/QUOTE]

---

### Post by bernardfrancois on 2006-03-24
You will have to do it with the Snape40.bin firmware, not the one of the epson scanner (it might work with that one as well, but it's better and safer to use the one made for your scanner).

> 
Second: 
cp Snape40.bin in /etc/sane/saned.conf


You should do this:
**sudo cp Snape40.bin /etc/sane/sane.d**

Then run **sudo gedit /etc/sane.d/snapscan.conf**

Then you change the following line:
*firmware /path/to/your/firmware/file.bin*
to
*firmware /etc/sane.d/Snape40.bin*

---

### Post by edopizza on 2006-03-25
Hi BernardFrancois! You must have eagle eyes. 

It was just a typing error in my previous post, I don't even have a folder called "snapscan.conf". 

It means that I already did what you suggested but without managing to make it work. 

WaaaaaaaaaaaaaaaaH! :-(

---

### Post by bernardfrancois on 2006-03-26
When I'm back at the computer where I made it to work I'll give you a script that will set it up.

---

### Post by edopizza on 2006-03-28
Ok, many thanks!

---

### Post by joey111 on 2006-03-31
i can get the ESFW41.BIN for epson perfection 2480 from nowhere and my cd is not readable anymore!
has anybody a download location??
thx

---

### Post by bernardfrancois on 2006-04-02
[QUOTE=edopizza]Ok, many thanks![/QUOTE]

I already wrote the script, but at that moment my Internet connection didn't work. Now I don't have acces to that computer till tomorow... Then I'll post the script. It will be able to set up every snapscan scanner that works with sane.

---

### Post by bernardfrancois on 2006-04-02
[QUOTE=joey111]i can get the ESFW41.BIN for epson perfection 2480 from nowhere and my cd is not readable anymore!
has anybody a download location??
thx[/QUOTE]

You could try to find it on the website of [epson](http://www.epson.com), and if you can't find it there you could contact them about it.

[edit]
I already found it [here](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&oid=41623&prodoid=46048265&infoType=Downloads&platform=Windows). Just download the windows driver and try to see what's inside. It should contain the firmware file.

Maybe it even contains firmware of multiple scanners, this was the case with the scanner I have.
If you found it, please tell me how you did it. Then I'll put it online so my script can use it.
[/edit]

---

### Post by joey111 on 2006-04-03
I will tell, but I just downloaded the epson11373.exe and how should I open it in Linux?

---

### Post by bernardfrancois on 2006-04-04
[QUOTE=joey111]I will tell, but I just downloaded the epson11373.exe and how should I open it in Linux?[/QUOTE]

Maybe you can try with rar (you can download it from rarlabs.com I guess). After installing, try **man rar** and see if you can get some more information.
When I have some more time I might check it myself.

In the meantime I finished the script. [Here](http://www.evonet.be/~bfran/extern/snapscan-firmware/snapscan.sh) you can download it.
Note that I didn't test it thouroughly, so it might not work. Please tell me if it worked.

Note that I forgot to add the line to restart the sane service. You should do this after running the script as root.

[edit]
I wil update the script as soon as possible. It doesn't work yet for any other but agfa snapscan scanners.
[/edit]

[edit2]
**NOTE:**
The url in the link above ([http://www.evonet.be/~bfran/extern/snapscan-firmware/snapscan.sh](http://www.evonet.be/~bfran/extern/snapscan-firmware/snapscan.sh)) will always point to the latest version of the script.
[/edit]

---

### Post by edopizza on 2006-04-05
WE WON!!!!! 
Many thanks bernardfrancois!!!! 

The script you posted above seems to work. If I am not wrong, it copies the choosed .bin in /etc/sane.d/ and edit the snapscan.conf. 
After that, the scanner didn't still working. I checked the time and date of the new snape40.bin and snapscan.conf to see if the script really overwrote them. Everyting was ok, with new date and time. But there was also a surprise: the other .conf had a normal text file icon, the icon beside snapscan.conf was different, something like a red box and the rights were -rw--------. 

**SOLUTION:** 
I just changed the owner in -rw-r--r-- to let the normal user read the snapscan.conf file with this command: 

 **sudo chmod 644 snapscan.conf**

That's it! 

By the way, the .bin file has an icon similar to the gnome foot, but it doesn't create problems. 



(OT: now I can finally scan the documents that the tax administration is waiting with joy...)

---

### Post by bernardfrancois on 2006-04-06
> **edopizza]
Many thanks bernardfrancois!!!!
[/quote]
The pleasure was mine said:**
> 
If I am not wrong, it copies the choosed .bin in /etc/sane.d/ and edit the snapscan.conf.

Yep. Actually, the editing of snapscan.conf is done in an awk script, which I wrote first in a seperate file, then I pushed the whole thing in an echo command:
**echo -e "{\n\tfound = \"false\"\n}\n\n/^firmware.*$/ {\n\tprint \"firmware \" firmware\n\tfound = \"true\"\n}\n\n{\n\tif( found == \"false\" ){\n\t\tprint\n\t}\n}"**
If you execute the line above, you'll see the awk script.
Making the menu to choose from was very easy, there's a built-in command **select** (more info: **help select**, **man bash**).

> 
I just changed the owner in -rw-r--r-- to let the normal user read the snapscan.conf file with this command: 
 **sudo chmod 644 snapscan.conf**

Ok, I'll add it to the script.

> 
By the way, the .bin file has an icon similar to the gnome foot, but it doesn't create problems.

File types unknown by nautilus always show such a foot icon. However, you might still see differneces between those files if you examine them with the **file** command.

---

### Post by maximo_it on 2006-10-21
Hi all,

i tried the 3d procedure to fix detection of my EPSON USB scanner 1670 perfection but ...this is the result

```
maximo@maximo-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
maximo@maximo-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x011f [EPSON Scanner]) at libusb:004:006
found USB scanner (vendor=0x046d, product=0x092e) at libusb:003:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
maximo@maximo-desktop:~$

```

and if i try to run xsane i get error...

Can you help me?

---

### Post by dief-eh? on 2006-11-16
hello!
i just successfully installed my saved-from-the-dump Snapscan 1212 scanner on my ubuntu edgy machine using the instructions found here. thanks to bernardfrancois and remix_88. if anyone's interested in my notes, i can add them to this thread.

---

### Post by matchstich on 2006-12-16
i have a file called snapscan.conf. is there any way i can over write what's in it. i mistakenly put an empty folder in it and want to put the bin in it, thanks

---

### Post by edopizza on 2006-12-17
You would like to put the .bin path in the snapscan.conf, is it correct? 
If you would like to edit or overwrite that file you need to add sudo in front of the command. 

First make a backup of the original file "sudo cp /whateveryourpathis/snapscan.conf /whateveryourpathis/snapscan.conf_backup" 

Open a console window, type "sudo gedit /whateveryourpathis/snapscan.conf" 

Now you should be able to edit and save the file.

---

### Post by matchstich on 2006-12-17
> **bernardfrancois said:**
> Little typo: it should be **sane.d**

I just successfully installed my Agfa Snapscan e25 with this howto. Thanks a lot!
I found my specific firmware at [http://drivermagic.co.nz/p/nph-detail.php?a=1221](http://drivermagic.co.nz/p/nph-detail.php?a=1221)
This site also includes firmware for other snapscan versions.

I also uploaded the files to my webspace on my ISP. You can find it here:
[http://www.evonet.be/~bfran/extern/snapscan-firmware/](http://www.evonet.be/~bfran/extern/snapscan-firmware/)
It includes the following files:
```

snap1212p.bin
snap1212u.bin
Snape10.bin
snape20.bin
Snape22.bin
Snape25.bin
snape26.bin
Snape40.bin
Snape42.bin
Snape50.bin
Snape52.bin
SnapScan 1212P_2.bin
SnapScan1212P_2.bin
SnapScan 1212U_2.bin
SnapScan1212U_2.bin

```
If you read this and you need one of these files and none of the above links work any more, and using a search engine to look for them doesn't give any results, then please contact me.

Am I violating copyright by distributing this firmware? If so, I'll remove it.

you have to join that site to get the driver. i have a acer 620U.  but don't want to sign up. have no credit cards. thanks

---

### Post by changlinn on 2007-04-09
I have the epson 2480
I found the bin file I needed on the driver disc and copied it to my webspace below [http://www.morganstorey.com/stuff/Esfw41.bin](http://www.morganstorey.com/stuff/Esfw41.bin)
I have followed the instructions and get the below

[I]# scanimage -L
device `snapscan:libusb:005:003' is a EPSON EPSON Scanner flatbed scanner[/I]

I can now get xsane working, and scanimage -T seems to work, but it doesn't scan. Xsane just shows a slightly bluey blurred page as a preview and a finished product.

---

### Post by changlinn on 2007-04-14
anyone know how to fix the above? My wife's desperate to scan some pictures, has even suggested I reinstall windows.

---

### Post by matthoffman on 2007-04-25
Have you tried the other firmware file (ESFW30.BIN) posted above?  Perhaps your firmware doesn't play nice...a known-working firmware is worth a shot. 

I have an Epson 1670; I'll give it a shot in a minute.

---

### Post by matthoffman on 2007-04-25
> **matthoffman said:**
> Have you tried the other firmware file (ESFW30.BIN) posted above?  Perhaps your firmware doesn't play nice...a known-working firmware is worth a shot. 

I have an Epson 1670; I'll give it a shot in a minute.


Hmm...odd.  I can't scan, either.  With Kooka, preview works, but the full scan doesn't -- it just hangs.  With scanimage on the command line, it warms up the scanner and then says, 

scanimage: sane_start: Error during device I/O

The scanner light starts doing a funky red-green-blink dance, and scanning hangs.  Hmmm... perhaps my scanner is a revision that isn't compatible with the posted firmware?  But the preview scan worked...

I tried in 2 hubs, in case that was the issue; I may try plugging it directly into the motherboard to rule it out further.

---

### Post by matthoffman on 2007-04-26
well, for the record, the firmware for Epson scanners is packaged in the driver that you can download from Epson -- use unzip to open the .exe file, and then cabextract to open the ModUsd.cab file.  You'll find the two .bin options inside.   
Interestingly, the esfw30.bin file inside there is different than the one posted on this thread.  But it doesn't solve my problem -- scanner detected, then "Error during device I/O".   
Alas...

---

### Post by Thingymebob on 2007-05-03
Having the same problems as matthoffman with my 1670 perfection using esfw30.bin,
xsane opens, previews ok - dies on scan
Result of scanimage -Tv
```

[snapscan] Scanner warming up - waiting 9 seconds.
[snapscan] Scanner warming up - waiting 35 seconds.
scanimage: scanning image of size 2552x3507 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 7656 bytes...  PASS
scanimage: reading one byte...          PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...    PASS
scanimage: stepped read, 32 bytes...    PASS
scanimage: stepped read, 64 bytes...    PASS
scanimage: stepped read, 128 bytes...   PASS
scanimage: stepped read, 256 bytes...   PASS
scanimage: stepped read, 512 bytes...   PASS
scanimage: stepped read, 1024 bytes...  PASS
scanimage: stepped read, 2048 bytes...  PASS
scanimage: stepped read, 4096 bytes...  PASS
scanimage: stepped read, 8192 bytes...  PASS
scanimage: stepped read, 8191 bytes...  PASS
scanimage: stepped read, 4095 bytes...  PASS
scanimage: stepped read, 2047 bytes...  PASS
scanimage: stepped read, 1023 bytes...  PASS
scanimage: stepped read, 511 bytes...   PASS
scanimage: stepped read, 255 bytes...   PASS
scanimage: stepped read, 127 bytes...   PASS
scanimage: stepped read, 63 bytes...    PASS
scanimage: stepped read, 31 bytes...    PASS
scanimage: stepped read, 15 bytes...    PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS

```
Last time I used this scanner was on Dapper, Just plugged it in and it worked - What Happened?

---

### Post by Thingymebob on 2007-05-03
I got an Image:
[IMG]http://www.aircooled.info/images/out.jpg[/IMG]
Scanner will only complete one pass, then requires restart / xsane restart
Don't do the preview scan just select the whole area and then scan........What a pain!

The result of scanimage -Tv after the first scanned image (scanimage -p > img1.ppm)
```

scanimage: open of device snapscan:libusb:003:003 failed: Error during device I/O

```

dmesg:
```

[  172.217525] usb 3-7: new high speed USB device using ehci_hcd and address 3
[  172.288914] usb 3-7: configuration #1 chosen from 1 choice

```

---

### Post by Thingymebob on 2007-05-03
I've set sane to debug and attached is a diff of the successful and failed scan passes if anyone can do anything with them

---

### Post by ttread on 2007-05-24
I am experiencing the same problems with my Epson Perfection 1670.  This appears to be a kernel bug in Feisty: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/94226](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/94226)   I used this scanner for a long time on Edgy and it worked beautifully.

It does one scan ok and then just gives I/O error repeatedly, with red blinking light.  I found that I could reset the scanner by disconnecting/reconnecting the power cable, but it's very difficult to use for productive work.  I have tried both firmware files available with the same result.

---

### Post by glennric on 2007-05-24
This bug has been around since Feisty was released.  It has to do with the experimental feature
"USB selective suspend/resume and wakeup (EXPERIMENTAL) (USB_SUSPEND)" that is enabled in the Feisty kernel.  If you recompile the kernel with this option disabled then you will be able to scan normally again.  Even better, if you compile the 2.6.21 vanilla kernel with this enabled things will work as they should.  There was a bug in the 2.6.20 kernel that has been fixed.

---

### Post by Franko30 on 2007-06-25
Hi,

I'm having the same 'Epson Perfection 1670' problem since using Feisty. It worked with Edgy and the ESFW30.BIN file.

> **glennric said:**
> This bug has been around since Feisty was released.  (...)  Even better, if you compile the 2.6.21 vanilla kernel with this enabled things will work as they should.  There was a bug in the 2.6.20 kernel that has been fixed.

Unfortunately, recompiling the Kernel is not an option for me - seems that I can't use the scanner until Gutsy is out...

What a pain in the ***! Hey the forum forum censors the swearword with a... That is just so US-American.

Franko30

---

### Post by gmolleda on 2007-07-30
I have a scanner Epson Perfection 1670.
I have Ubuntu Feisty Fawn: kernel 2.6.20

I have compiled two kernel:
2.6.20 without option "USB selective suspend/resume and wakeup (EXPERIMENTAL) (USB_SUSPEND)": I now can scan 1 page, but finish scan and the scan is halt with red led (if I switch off and later switch on the scanner and restart xsane then I can scan other one page).

2.6.21 with option "USB selective suspend/resume and wakeup (EXPERIMENTAL) (USB_SUSPEND)": I can scan 1 page too, but no more: switch and restart=1 page.

Sorry my english (I'm Spanish).
Bye.

---

### Post by matew on 2007-08-03
> **ttread said:**
> I am experiencing the same problems with my Epson Perfection 1670.  This appears to be a kernel bug in Feisty: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/94226](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/94226)   I used this scanner for a long time on Edgy and it worked beautifully.

[...] I found that I could reset the scanner by disconnecting/reconnecting the power cable, [...].

Same problem here with a AGFA Snapscan e20 which worked perfectly when I used Debian Unstable. Thanks for hinting me to the kernel bug, guys ... this made it possible to develop the following crazy workaround:

All we have to do is to prevent the USB port from being suspended once the scanner is used for the first time after scanner power-on. To this end, use the following command in a separate terminal window just after scanner power-on, before doing anything else to the scanner:

```
while [ true ]; do sleep 0.3; lsusb; done
```

As long as this command is running, you can use the scanner just as you are used to: xsane, preview scanning, scanimage and so on all work perfectly again.

Details: This is an infinite command, so end it with Ctrl+C but remember that you need to power your scanner off and on to use the scanner again after that. As long as this command is running, the USB port is accessed every 0.3 seconds, so is never suspended. You can tweak the sleep delay to lower CPU consumption if desired. But it cannot be longer than approx 1 or 2 seconds as this is the "timeout" for an idle USB port before being suspended, as you can see from the time left for the scanner to partially move to zero position after a scanimage command ended.

If you want to see the command working (as I do), use the following command instead:

```
a=0; while [ true ]; do sleep 0.3; lsusb; ((a++)); echo iteration $a; done
```

hope this helps someone else,
matew

---

### Post by holch on 2007-10-28
Ohh, I experienced the same problem (only one scan possible).

Is this problem solved in the new version of Ubuntu (7.10)?

---

### Post by Franko30 on 2007-10-28
Hi,

for me - on one machine so far - scanning is possible in 7.10

But not out of the box - I still have to use the procedure explained in post 1 of this thread.

Cheers

Franko30

---

### Post by holch on 2007-10-28
Thank you Franko30,

I can live with the procedure of the first post in the thread. You do that once and that's it.

But it is annoying to disconnect the scanner and shut down Xsane after each scan (you can't even do a preview scan + the normal scan).

OK, I have to fix the problem with my external hard disk (doesn't allow me to write on it) so I can make my back-up. Then I will update to 7.10.

Regards,
Holch

---

### Post by Conquestor1 on 2007-10-30
How do I get Ubuntu to find the downloaded files. I cannot seem to get a straight link to the Epson files using wget. I do hava Windows laptop I can install to/ Where would I find the bin file. Can I simply copy it and then where would I copy it to?
:(

---

### Post by dentament on 2007-11-08
try this workaround, for some scanners it works (with epson perfection 2480 it does)
install scanbuttond
run scanbuttond (as user) before running xsane / xscanimage

> But what is going on?
> the daemon always watches for the scanner and the usb did not suspend.
> the real function of this software is to look for the buttons on the scanner and do something usefull lke
> scanning -> printing - scanning -> email

see here for details: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

---

### Post by cchevy on 2007-11-11
I have a agfa snapscan e20 and it could not be recognized in 7.10. I did what was suggested in the first post but still no luck.

i have the original intallation cd and several bin files on it:

snape20.bin
Snape40.bin
Snape50.bin
SnapScan 1212P_2.bin
SnapScan 1212U_2.bin

i have tried to place some of them in etc/sane.d and changing the firmware path on snapscan.conf but still no result. what .bin file do i need?

can somebody help me on this?

---

### Post by bernardfrancois on 2008-07-05
I've updated the script to install agfa snapscan scanners. It now includes the fix mentioned by edopizza.

You can download it here: [http://www.evonet.be/~bfran/extern/snapscan-firmware/snapscan.sh](http://www.evonet.be/~bfran/extern/snapscan-firmware/snapscan.sh)

Note that you must execute it as root.

I used the script today to install my agfa snapscan e25 scanner in ubuntu 7.10.

---

### Post by nyagol on 2008-07-07
:(Hi i have a benq 5000 on Ubuntu Hardy Heron & have followed all this instructions succefully but I have this problem : xsane identifies the scanner alright but crashes in the middle of the scanning process sometimes it restarts my system. any help there?

---

### Post by megahertz on 2008-11-03
I finally have Xsane working with my Epson Perfection 2580 (it should work with Perfection 2480).
- Epson Perfection 2480 and Perfection 2580 are driven by snapscan backend, so libsane should be installed (use Synaptic Package Manager to see if it is installed and/or to install it).
- Two files are needed to be edited with root privileges: /etc/sane.d/dll.conf and /etc/sane.d/snapscan.conf.
- Open /etc/sane.d/dll.conf and put a # at the beginning of ALL lines Except the Snapscan

#sm3600

#sm3840

snapscan

#sp15c

#st400

#stv680

- Open etc/sane.d/snapscan.conf and edit the forth line (firmware)

#Change to the fully qualified filename of your firmware file, if

# firmware upload is needed by the scanner

firmware /etc/sane.d/esfw41.bin


- Put the CD that came with your scanner and open /media/Epson/ESCAN/ModUsd.cab . Extract esfw41.bin to the etc/sane.d folder.

- Copy dll.conf, snapscan.conf and esfw41.bin
 from folder /etc/sane.d to folder /etc/sane.d/dll.d

Now Xsane should find and open your  Epson Perfection 2580 scanner.
:p

---

### Post by Tuxi on 2008-11-25
I've tried the above to try to get an Epson Perfection V300 to work without success.  I found the corresponding firmware file from a Windows install and from cabextract.  When I run 'scanimage -L' I get
```

[sanei_debug] Setting debug level of snapscan to 2.
[snapscan] add_usb_device: error opening device libusb:002:011: Access to resource has been denied

```

Any suggestions?  Thanks.

**Additional Information**
For me the firmware file appears to be Esfw8B.bin which was found in "/media/cdrom0/Common/EPSON Scan/ModUsd.cab".  This is the same file as was being used in a Windows install.

"sudo scanimage -L" gives no message about the V300.  lsusb returns (in part) "Bus 002 Device 006: ID 04b8:0131 Seiko Epson Corp."

---

### Post by kaibob on 2008-11-26
> **Tuxi said:**
> I've tried the above to try to get an Epson Perfection V300 to work without success....

Tuxi,

Please let us know if you get the V300 working. I need a new scanner and want to buy the V300. I checked the Avasys site, but it doesn't show support for the V300 as of yet. 

[http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm)

kaibob

---

### Post by Tuxi on 2008-11-26
kaibob,

It's beginning to look like I'll have to wait for the avasys driver.  It seems as though they're updating about twice a month.  In the meantime, if I figure something out, I'll post it here.

---

### Post by Jonam on 2009-01-01
Tuxi,

I have a V300 working fine under iscan though causing difficulties with transparencies under Xsane. Refer to my post that outlines installation here:

[http://ubuntuforums.org/showthread.php?p=6297403](http://ubuntuforums.org/showthread.php?p=6297403)

It's not too difficult to get going.

Jonam

---

### Post by Tuxi on 2009-01-04
Jonam,

Thanks.  I've got the V300 working in 64-bit thanks to the link.  I too am having issues with the transparency unit under xsane.

---

### Post by bernardfrancois on 2009-04-13
The script I made is no longer online, because I now have a different internet provider. If anyone would still want to use it to make his or her scanner work, please send me a PM and I'll try to find it and get it online somewhere.

---

### Post by nebhead77 on 2009-04-17
I was able to resolve the issue with my Epson Perfection 1670 on my install of Intrepid (Intel 32-Bit) by installing the deb files from the following website: [http://www.arakhne.org/epson/index.html]("http://www.arakhne.org/epson/index.html")

More specifically from here: [http://download.tuxfamily.org/arakhne/pool/l/libsane-epson-perfection/]("http://download.tuxfamily.org/arakhne/pool/l/libsane-epson-perfection/")

Good luck!

---

### Post by bernardfrancois on 2009-04-18
Note that some acer scanners also use the snapscan backend. Firmware for them can be found here:
[http://outlands.ca/linux/snapscan-firmware.html](http://outlands.ca/linux/snapscan-firmware.html)

These are the scanners for which firmware is provided on that page:
[list]
[*]Acer/Benq 310U, 320U, 340U
[*]Acer/Benq 620U, 640U, Guillemot/Hercules Maxi A4 36bit
[*]Acer/Benq 620UT, 640UT
[*]Acer/Benq 640BU
[*]Acer/Benq 640BT
[*]Acer/Benq 1240
[*]Acer/Benq 3300/4300
[*]Guillemot/Hercules Scan @home Touch 1248
[/list]

I also attached the script I made earlier. Note that it will not work any more as it is now, so don't try executing it without any modifications. 
Basically, the script just copies the firmware file to the **/etc/sane.d/** directory and modifies the **/etc/sane.d/snapscan.conf** configuration file (as described earlier in this thread).

---

### Post by malahavock on 2009-05-02
Re: scanner script
I found the script and attached it here:
[http://ubuntu-utah.ubuntuforums.org/...06#post7093606](http://ubuntu-utah.ubuntuforums.org/...06#post7093606)

Note that it won't work any more, but I guess you can figure out how to install the firmware for your scanner. I also posted a link where you can get the right firmware. The instructions how to install it can be found in the thread.

Can you post something in the thread to let everyone know if it worked or not?

Greetz,

Bernard

Quote:
Originally Posted by malahavock
I'm pretty sure it is.

Quote:
Originally Posted by bernardfrancois
Quote:
Originally Posted by malahavock
I would like to take you up on the offer of a scanner script. I am new to ubuntu and am at a loss as to how to get my Acer 3300u to work. any help would be greatly appreciated.
Do you know if it's a snapscan-type scanner? Otherwise it may not work...

I'll check this evening if I can find the script.


Greetz,

Bernard



I personally could not get this to work, but i found a great deal on a hp AIO officejet 6500. Which works like a champ, by the way.

---

### Post by CDrewing on 2009-10-11
Crazy behaviour of my EPSON Perfection 2580 PHOTO. FYI, I did it the same way as described in the first post of this thread.

My lsusb says: 

```
Bus 001 Device 003: ID 04b8:011f Seiko Epson Corp. Perfection 1670

```

**But it's a 2580 PHOTO!**

The rest is working. xsane is finding my scanner, the scanner is even reacting when I try to scan a preview, but it remains empty. So does a full scanned image.

This happens with esfw30 and esfw41.

Ideas? Anyone?

---

### Post by Gnu.Linux.Revolution on 2009-10-22
Thank you, Remix_88!
Another Epson Perfection 1670 is now working OK, under Debian Lenny.

-------------------------------------------------------------------------------------------------------------
[quote=Remix_88;131852]**HOWTO: Epson Perfection 1670 Scanner**

The scanner firmware comes in a file called ESFW30.BIN, which apparently is only available if you install the software on the CD-ROM provided with the scanner. Unfortunately, the software only installs under Windows and then you have to copy the software from the Windows machine to the linux machine. Or you can follow this simple process to download the firmware (provided by Jeff Silverman) and then update your /etc/sane/saned.conf 

```
$ wget http://www.commercialventvac.com/~jeffs/ESFW30.BIN
$ sudo cp ESFW30.BIN /etc/sane.d
```Edit /etc/saned.d/snapscan.conf and change the line...

firmware /path/to/your/firmware/file.bin

...to point to /etc/sane.d/ESFW30.BIN

```
$ scanimage -L
```You should see that your scanner is now detected. If so, you can now scan using XSane.

---

### Post by pluseagle on 2009-11-29
Hi
i have agfa snapscan 1212u scanner. i installed ubuntu 9.10 on my laptop. at first i used my scanner ( i scanned 50 pages. but after i restarted my laptop, it didn't work. When i want to open xscane, it shows this screen 
[[IMG]http://img163.imageshack.us/img163/6550/98012443.th.jpg[/IMG]]("http://img502.imageshack.us/img502/254/74265618.jpg")

pls help

---

### Post by ndaneau on 2010-01-14
Hi,

I'm using a Epson Perfection 1670 under Ubuntu 9.10.

I didn't made any special trick to install it, it was working out of the box! Almost magic!
BUT... after that the first use, got some issue... I'm actually in dual-boot with Windows XP (where the scanner work too). 
When booting Ubuntu after using Windows, the scanner is OK. 
When booting Ubuntu after using Ubuntu (what i do most of the time), the scanner doesn't work, Xsane can't find it.

Thanks for any help as this is one of the last thing i need to fix before deleting the Windwos partition! :KS

Nico

---

### Post by amiroff on 2010-05-01
Ubuntu 10.04 here. Recognized Epson 1670 scanner when I plugged in (appears in simple scan settings) but refused to scan. After applying steps in first post I can now enjoy my scanner. Thank you very much!

---

### Post by GH68 on 2010-11-23
I have the same problem as ndaneau with my Epson Perfection 660 - it works if I first run Windows XP but otherwise not. I think it used to work perfectly a few Ubuntu versions ago, but since I'm not using the scanner frequently I don't know when I lost the functionality. Any advice from anyone?

---

### Post by Grafen on 2011-02-16
> **GH68 said:**
> I have the same problem as ndaneau with my Epson Perfection 660 - it works if I first run Windows XP but otherwise not. I think it used to work perfectly a few Ubuntu versions ago, but since I'm not using the scanner frequently I don't know when I lost the functionality. Any advice from anyone?
I've got exactly the same problem! But I don't have win anymore :( Please, someone, help!

---

### Post by GH68 on 2011-02-16
I obviously forgot to post my solution, probably because it seemed unrelated to the actual topic. It turned out that Linux was more picky with the USB interface and did not work when using my USB hub. When connecting the scanner directly to a USB port on the PC, everything works fine. I don't know if more recent versions are more picky or if my hardware degenerated over time.

---

### Post by Franko30 on 2011-02-17
> **GH68 said:**
> When connecting the scanner directly to a USB port on the PC, everything works fine


Hi,

this doesn't work for me since 9.04 or so - I'm now on 10.04

Cheers

Franko30

---

### Post by GH68 on 2011-02-17
I'm on 10.10 and I suspected that my solution was unlikely to be the solution for others, which was the reason for not posting it in the first place. Finally I decided to post it anyway since it may help someone. Checking the hardware may be the first thing to do, but I was completely misled by the behaviour of the scanner working flawlessly in Ubuntu after having run Windows. Obviously, the USB communication in Ubuntu was good enough for the scanning process but not for loading scanner firmware. Difficult to say if Franko30 or Grafen even have the same problem, i.e. that it is the firmware upload that fails. At least ndaneau seems to have the firmware upload issue, would be interesting to hear of any progress from you?

---

### Post by Grafen on 2011-02-18
Well, connecting directly, without hub, didn't work. I've also wasted enough time on this issue googling some solution, so I've decided just to get rid of this not linux-friendly piece of hardware. Never will buy anything Epson-branded anymore.

---

### Post by OMAR5363 on 2012-04-02
**thank you sir i dowloaded a driver for windows intalled scanner then copied the driver dowloaded (18 mo) on the partition with ubuntu i restarted the computer in ubuntu (i have dual boot w7and ubuntu)** [B]and now the scanner epson perfection 1670 is working thank you for your help.

[/B]

---

### Post by mikey on 2012-06-09
> **nebhead77 said:**
> I was able to resolve the issue with my Epson Perfection 1670 on my install of Intrepid (Intel 32-Bit) by installing the deb files from the following website: [http://www.arakhne.org/epson/index.html]("http://www.arakhne.org/epson/index.html")

More specifically from here: [http://download.tuxfamily.org/arakhne/pool/l/libsane-epson-perfection/]("http://download.tuxfamily.org/arakhne/pool/l/libsane-epson-perfection/")

Good luck!
worked for me as well on natty.

---

