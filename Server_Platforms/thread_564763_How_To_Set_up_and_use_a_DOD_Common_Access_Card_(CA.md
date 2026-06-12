---
title: "How To: Set up and use a DOD Common Access Card (CAC) for Army Knowledge Online (AKO)"
date: 2007-10-01
forum: Server Platforms
---

### Post by psyopper on 2007-10-01
With the growing usage of Ubuntu and the requirement in the US Army to use your Common Access Card (CAC) to log in to AKO there have been a lot of questions asked about getting these to work under Ubuntu.

Some caveats: Red Hat Fedora 6 supports the CAC on an out of the box installation. Ubuntu does not. There are several different tutorials on how to install a CAC reader and log in to AKO. It is a combination of these that this tutorial is built upon:

[http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/]("http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/")
[http://ubuntuforums.org/showthread.php?t=457084]("http://ubuntuforums.org/showthread.php?t=457084")
On AKO there is also a thread easily found by searching "linux cac" in AKO Public.

Many thanks to MrFSL for finding the majority of the packages necessary.

**[SIZE="4"]Step 1 : Get a USB card reader[/SIZE]**

Specifically, you wan to get the SCM Microsystems SCR331 Smart Card Reader. [These can be had on eBay for about $20 to $35]("http://search.ebay.com/scr331_W0QQfrppZ50QQfsopZ1QQmaxrecordsreturnedZ300") (including shipping). There are several different part numbers for this card reader. One of them works right out of the box, the others require reflashing the bios.

PN: 904622 - this is the newer part number and does NOT need to be reflashed, it will work right out of the box.

All other part numbers PRIOR to 904622 WILL require reflashing the BIOS. 

You may be able to contact the seller in advance of the sale and have them verify the part number if you don't want to reflash the BIOS. [If you get a card reader that requires reflashing, visit this web site for instructions]("http://symbolik.wordpress.com/2007/02/26/scm-scr-331-usb-smartcard-reader-firmware-upgrade/"). **You will need to reflash these readers in Windows**.


**[SIZE="4"]Step 2 : Install the packages (Part 1)[/SIZE]**

Most of the packages are present in the Ubuntu repositories and can be installed by running the following command in a terminal window:

```

sudo apt-get install libusb-0.1-4 libpcsclite1 libpcsclite-dev pcscd pcsc-tools build-essential autoconf xlibs-dev libccid

```

Once they are installed you can plug in your card reader and test to see if it's working properly. It is NOT yet ready for logging in to AKO though so sit tight. 

First we need to initialize PCSC to get the security system started:
```
sudo /etc/init.d/pcscd restart
```

Then we will see if it is actually reading your card (go ahead and insert your card in the card reader):
```
pcsc_scan
```

If it is reading your card correctly you should see something like this:
```
~$ pcsc_scan
PC/SC device scanner
V 1.4.8 (c) 2001-2006, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.3.2
Scanning present readers
0: SCM SCR 331 (21120717207407) 00 00

Mon Oct  1 11:52:50 2007
 Reader 0: SCM SCR 331 (21120717207407) 00 00
  Card state: Card inserted, 
  ATR: XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX 

ATR:  XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX 
+ TS = 3B --> Direct Convention
+ T0 = 6B, Y(1): 0110, K: 11 (historical bytes)
  TB(1) = 00 --> VPP is not electrically connected
  TC(1) = 00 --> Extra guard time: 0
+ Historical bytes: XX XX XX XX XX XX XX XX XX XX
  Category indicator byte: 80 (compact TLV data object)
    Tag: 6, len: 5 (pre-issuing data)
      Data: XX XX XX XX XX
    Tag: 8, len: 3 (status indicator)
      LCS (life card cycle): 00 (No information given)
      SW: 9000 (Normal processing.)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
 XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX 
        Gemplus GXP3 64V2N
        U.S. Department of Defense Common Access Card (DoD CAC)

```

**[SIZE="4"]Step 3 : Install the packages (Part 2)[/SIZE]**

There is one more package we need to install. Most of the tutorials out there have you [installing Coolkey from source]("http://directory.fedoraproject.org/wiki/CoolKey") but that is not necessary and will alleviate some of the headaches for new Ubuntu/Linux users and possible dependency issues. Fortunately the good folks over at Debian (the big brother to Ubuntu) have [Coolkey packaged for installation]("http://packages.debian.org/unstable/admin/coolkey").

Download the coolkey package appropriate for your installation:

[i386 for 32 bit Ubuntu]("http://packages.debian.org/sid/coolkey/i386/download")

[ia64 for 64 bit Ubuntu]("http://http.us.debian.org/debian/pool/main/c/coolkey/coolkey_1.1.0-3_ia64.deb")

[For other versions of coolkey available, click here]("http://packages.debian.org/unstable/admin/coolkey")

All it takes is downloading the appropriate package, and once complete, opening the download and allowing GDebbie Package Manager to install it for you.

**[SIZE="4"]Step 4 : Installing the authentication tool for Firefox[/SIZE]**

Next we need to set up Firefox to use your CAC/Reader as an authentication tool for websites. In Firefox go to:

Edit-> Preferences -> Advanced -> Encryption --
[IMG]http://www.pbupload.com/data/500/preferences1.jpg[/IMG]

Click on the Security Devices button --
[IMG]http://www.pbupload.com/data/500/devices1.jpg[/IMG]

Click the Load button to load a new module. Name it CAC Module and either type in or browse to /usr/local/lib/pkcs11/libcoolkeypk11.so --
[IMG]http://www.pbupload.com/data/500/cacmodule.jpg[/IMG]

Click OK and the CAC Module should now appear on the left side of the screen, like in the screen shots above. If you insert your CAC it will show your name under the CAC Module, and if you click on it ti should appear in the right hand pane with more detail.

**[SIZE="4"]Step 5 : Installing the DOD Security Certificates[/SIZE]**

This is probably the easiest step of the bunch. And it's almost the last... Simply go to the following web site:

[http://dodpki.c3pki.chamb.disa.mil/rootca.html]("http://dodpki.c3pki.chamb.disa.mil/rootca.html")

Once there click on each of the three links, you will need to install all three certificates to get AKO/CAC working correctly. On each link, when you click it, Firefox will prompt you to install the certificate. Click Yes to each one.

**[SIZE="4"]Step 6 : Log in to AKO/DKO [/SIZE]**

Go to [https://www.us.army.mil]("https://www.us.army.mil") and click the CAC login button. You will be prompted for your CAC password/PIN. This is the 6 - 12 digit pin they had you enter when you had your ID made. You may be prompted with "This site has requested that you identify yourself with a certificate". Verify that your name is highlighted and click OK. You may be prompted several times for this, just keep ensuring your name is selected and clicking OK.

---

### Post by MrFSL on 2008-01-11
I mentioned this on another post but just wanted to update - the firmware now is flash-able from Linux using the manufacturers new utility:
[http://www.scmmicro.com/security/view_product_en.php?PID=2](http://www.scmmicro.com/security/view_product_en.php?PID=2)

As it is - you have to download the Windows firmware update to get the bin file first. You also must stop your pscsd service first:
```
sudo /etc/init.d/pcscd stop
```

After flash:
```
sudo /etc/init.d/pcscd start
```

---

### Post by jsh-hk on 2008-01-19
Thank you for this post.  I had some issues at first getting my card to be properly read, but a restart, for whatever reason, seems to have fixed it.  D'oh!

Also, good news for Gutsy users: Coolkey now appears to be in the Ubuntu repo's, so no need to go grab the debian package.

Thanks again!

---

### Post by jsh-hk on 2008-01-20
Also, the Ubuntu community has released a guide:

[https://help.ubuntu.com/community/CommonAccessCard]("https://help.ubuntu.com/community/CommonAccessCard")

---

### Post by joeprelude on 2008-01-23
it worked for a day then wouldn't work the next, i keep gettin an error when trying to sign in and tried to see if the system would read the card, with the [COLOR="Red"]pcsc_scan[/COLOR] command, and this is what the terminal said

[COLOR="Blue"]PC/SC device scanner
V 1.4.11 (c) 2001-2007, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.99
winscard_clnt.c:3471:SCardCheckDaemonAvailability() PCSC Not Running
SCardEstablishContext: Cannot Connect to Resource Manager: Service not available. (0x8010001D)
[/COLOR]

i have the latest feisty

---

### Post by MrFSL on 2008-01-23
It looks like the server is not running try:

```
sudo /etc/init.d/pcscd restart
```

---

### Post by joeprelude on 2008-03-03
still getting that error, also opened the firefox preference to look at the module lit and the one i loaded for the cac is no longer on there. and it won't let me reload it

---

### Post by MrFSL on 2008-03-03
> also opened the firefox preference to look at the module lit and the one i loaded for the cac is no longer on there. and it won't let me reload it

First things first - I would get your CAC card showing using pcsc_scan first - then worry about firefox.

If you have the appropriate **hardware** (**NOTE** - not all CAC card readers have shown to work in Linux) and you have followed the necessary steps to install and configure the appropriate software - then things should work.

I would retrace your steps from the top. Perhaps you overlooked something.

Sorry. :(

---

### Post by joeprelude on 2008-03-03
ok i have p/n 904850,
scr3310 v2.0

tried from the begining but still not working

---

### Post by MrFSL on 2008-03-03
Alright. 

I personally have a SCR331 P/N 90533 rev. 1.0

Regardless the output of pcsc_scan being:
> PC/SC device scanner
V 1.4.11 (c) 2001-2007, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.99
winscard_clnt.c:3471:SCardCheckDaemonAvailability() PCSC Not Running
SCardEstablishContext: Cannot Connect to Resource Manager: Service not available. (0x8010001D)

Means the daemon... the service is not running.
So lets do some testing...
1) Lets see if the pcscd daemon is running using:
```
ps -e | grep -i pcsc
```
If you don't get anything but a new line then it is not running

2) Since I am about 99% positive that it is not running lets go ahead and find out why if we can. Lets start the daemon process in the foreground and check the output:
```
sudo pcscd -f
```
Post the output back on this forum please. -- Now, if there is no real errors then (while leaving that terminal open) connect your cac card reader, (if it isn't already connected) and run pcsc_scan again - and please post the output.

Hope this helps.

---

### Post by barret on 2008-03-06
```
cw@ubuntu:~$ sudo pcscd -f
[sudo] password for cw:
pcscdaemon.c:294:main() pcscd set to foreground with debug send to stderr
configfile.l:108:evaluatetoken() Error with device /dev/SCR24x0: No such file or directory
configfile.l:109:evaluatetoken() You should use 'DEVICENAME /dev/null' if your driver does not use this field
pcscdaemon.c:532:at_exit() cleaning /var/run
pcscdaemon.c:551:clean_temp_files() Cannot unlink /var/run/pcscd.comm: No such file or directory

```

I'm getting the same error as joeprelude and that is the error above that I get when I run pcscd -f.

---

### Post by tubasoldier on 2008-03-06
This would have been good information about six months ago before I decided the National Guard was no longer fun....

---

### Post by MrFSL on 2008-03-07
> **barret said:**
> ```
cw@ubuntu:~$ sudo pcscd -f
[sudo] password for cw:
pcscdaemon.c:294:main() pcscd set to foreground with debug send to stderr
configfile.l:108:evaluatetoken() Error with device /dev/SCR24x0: No such file or directory
configfile.l:109:evaluatetoken() You should use 'DEVICENAME /dev/null' if your driver does not use this field
pcscdaemon.c:532:at_exit() cleaning /var/run
pcscdaemon.c:551:clean_temp_files() Cannot unlink /var/run/pcscd.comm: No such file or directory

```

I'm getting the same error as joeprelude and that is the error above that I get when I run pcscd -f.

Odd. What reader are you attempting to use. What instructions did you follow so far to get this working?

---

### Post by warpasylum on 2008-03-08
Thanks, I'm trying to make the complete switch from windows to linux and this will definitely help:)

---

### Post by Vinnie_Fits on 2008-04-06
[FONT="Lucida Sans Unicode"][SIZE="4"]**Quick and Dirty CAC install on Gutsy Gibbon**[/SIZE][/FONT]

I had to mix directions from two webpages I found by googling.

[http://ubuntuforums.org/showthread.php?t=564763&highlight=cac%20reader%20install](http://ubuntuforums.org/showthread.php?t=564763&highlight=cac%20reader%20install)
 and
[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard) 

These worked for the most part but there were some minor things which caused frustration (like locating the libcoolkeypk11.so file in Firefox. I couldn't find the file where it was supposed to be, so I had to hunt). Anyway, I made this document up for my future reference but decided to slap it up here in case it helps anyone else. The full directions aren't here, I highly recommend clicking on and reading both the above links thoroughly before using my directions so you can understand better the issues I was having and maybe then it will make some sense to you. However, if you have the SCR 331 USB smart card reader with part no. 904622 (and not an earlier part number), these directions below will probably work just fine for you. Remember, it doesn't have all the inf you might need but serves well as a checklist for me for future installation on another Ubuntu box.

**Install pcscd from terminal**
```
sudo apt-get install pcscd pcsc-tools libccid libpcsclite-dev
```

**Plug SCR 331 USB card reader in USB port and put in your CAC**

**Initialize pcsc from terminal**
```
sudo /etc/init.d/pcscd restart
```

Light on reader should be flashing now if not, try scan anyway and see what's wrong

**Run the pcsc scan from terminal**
```
pcsc_scan
```

You should now see the results and at the bottom you'll see something like this:
```
Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
 XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX 
        Gemplus GXP3 64V2N
        U.S. Department of Defense Common Access Card (DoD CAC)
```
 
If your card is not identified, you will see something like this:
```
Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
        NONE
Your card is not present in the database.You can get the latest version of the database from  [http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt](http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt)
or use: wget [http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt](http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt) --output-document=/home/gniibe/.smartcard_list.txt

If your ATR is still not in the latest version then please send a mail
to <ludovic.rousseau@free.fr> containing:
- your ATR
- a card description
```

**If you do see the latter result from above than copy the text **

```
wget http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt &#8211;output-document=/home/gniibe/.smartcard_list.txt
```
 
into your terminal and it will get the latest card info. Then run the pcsc scan again. If your card is in the updated list, you should see something akin to the first result above when doing the scan (I had this problem with a CAC and this worked for me).

**Install Coolkey from Synaptic**
My recommendation is don't bother trying to install it manually through the terminal or getting the deb package. It's in the Gutsy repository so just install it in that manner. Open System > Administration > Synaptic Package manager. Search for coolkey. Mark it for upgrade and apply. It will download one additional dependency. Close out Synaptic after installation.

**Install authentication for Firefox**
From within Firefox, Edit-> Preferences -> Advanced -> Encryption.
Click Advanced Tab
Click &#8220;Security Devices&#8221; button
Click &#8220;Load&#8221; button
Type &#8220;CAC Module&#8221; in module name
Browse to the file &#8220;/usr/lib/pkcs11/libcoolkeypk11.so&#8221; and click OK and OK again. (File might also be in /usr/**local**/lib/pkcs11/libcoolkeypk11.so).

**Install DOD Root Certificates**
Go here [http://dodpki.c3pki.chamb.disa.mil/rootca.html](http://dodpki.c3pki.chamb.disa.mil/rootca.html) and click on the links to install the root certificates. Check all three boxes and click &#8220;Install&#8221;. You may get some error on the first one about not being able to install it because it's not signed. Just keep clicking Yes (about 4 times I think). The other two links shouldn't give you a problem.

**Check certificates install in Firefox**
Edit > Preferences > Advanced > &#8220;View Certificates&#8221;. ***WARNING! IT MAY ASK YOU FOR YOUR CAC PIN. Don't make the mistake of typing in your Firefox main password (if you use one) or you may lock out your CAC!*** You should see a bunch of certificates now under U.S. Government. I would specifically for the three you just installed, but you should see all the common ones you see on a windows machine.

**Verify CAC works**
Browse to the site you need to login with your CAC and try it out! Or go to [https://www.us.army.mil/](https://www.us.army.mil/) and do the CAC login option. It should popup a little window and ask you to pick the certificate. Don't change it, just click OK and you should be logged in. It may or may not ask for your PIN (probably not if you bother to check to see if the certificates were loaded/installed in Firefox per the Check certificate install in Firefox directions in the above paragraph.

ATTACH: Zipped doc file containing above for your printing pleasure!

---

### Post by Vinnie_Fits on 2008-04-06
Now I'm trying to get Evolution to work with DOD email account. Evolution only supports OWA access (which I can do now in FF :) but I don't think it supports a certificate login with a CAC. I'll post any results here if I have success (or even if I don't so people can troubleshoot as well).

Tags: DOD CAC OWA RPC Evolution PKI SCR331 Exchange

More information in this thread: [http://ubuntuforums.org/showthread.php?p=4667676#post4667676](http://ubuntuforums.org/showthread.php?p=4667676#post4667676)

---

### Post by Vinnie_Fits on 2008-04-06
I'm going to attempt this install using an SCM SCR243 PCMCIA smart card reader/writer as well. I bought this for my own personal laptop to access my DOD email account rather than having to drag that USB SCR331 reader around with me. It works in windows very well on my laptop. I haven't tried to install Ubuntu on the laptop to try it there (afraid of hosing my data in a dual boot setup). I'll either do the dual boot on the laptop or get a USB to PCMCIA adapter of some sort so I can test it on my Ubuntu desktop machine. 

Why do you care? Well just in case someone is trying to do the same thing, they might benefit and in the meantime at least they'll have a thread to search for! :) 

By the way, it seems the SCM brand readers work the best with the DOD CACs. I've bought and set back a myriad of them which wouldn't work in windows.

Be aware also that SCM is an OEM seller so you may have to get one off eBay (where I found mine). It was relatively inexpensive at around $35USD I think.

---

### Post by tmaleshafske on 2008-04-13
Has anyone had any luck with the DELL texas instrument internal card reader?

---

### Post by joeprelude on 2008-05-06
ok so i got my reader to work and be recognized, by using the firfox addon, but now it asks for a master password, i used my pin but doesnot work as password. anyway to figure this out

---

### Post by ZanexGt on 2008-05-14
Thanks Vinnie_Fits, your [guide](http://ubuntuforums.org/showpost.php?p=4666212&postcount=15) above also works in Hardy. 
I used the directions to install a SCR331 on my laptop which has Ubuntu 08.04 Hardy Heron and the included Firefox 3 Beta 5 installed. Everything works perfectly.

---

### Post by bone2006 on 2008-07-14
For another model

Cherry Model ST-1000U
[http://www.barcoding.com/prodpages/Cherry/st1000ulores.gif](http://www.barcoding.com/prodpages/Cherry/st1000ulores.gif)


Installing the drivers/software needed to scan the card
****************************************************************
open up the terminal -> Applications-> Accesories -> Terminal


$ sudo apt-get install libusb-0.1-4 libpcsclite1 libpcsclite-dev pcscd pcsc-tools build-essential autoconf libccid subversion coolkey
//installs all the applications/dependencies that are needed

$ cd && mkdir card && cd card
// takes you to your home directory, creates a directory called card and then takes you to that directory

$ svn co [http://svn.gula.es/cm2020](http://svn.gula.es/cm2020) 
//Checking outthe source code from subversion repository, when it's dnoe it will say: Checked out revision 12

$ cd cm2020 && sudo sh ./install
// changes to directory cm2020 and the runs the install script, when it's done it's going to say: Installation finished 

$ lsmod | grep cardman 
cardman                42116  0
usbcore               146028  5 cardman,usb_storage,libusual,uhci_hcd
// see if you get something similar to what's above to see if it's worknig

$ sudo /etc/init.d/pcscd restart
// restart pcscd (daemon program for smart card reader - PCSC Lite resource manager)

$ pcsc_scan
// now your scanning the card you sould se something like what I have below

//Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
 XX XX XX XX XX XX XX XX XX XX XX XX XX XX XX 
        Gemplus GXP3 64V2N
        U.S. Department of Defense Common Access Card (DoD CAC)

****************************************************************

FIREFOX SETUP INSTRUCTIONS.

1) Edit-> Preferences -> Advanced -> Encryption
2) Click on the Security Devices button
3) Click the Load button to load a new module. Name it CAC Module and either type in or browse to /usr/lib/pkcs11/libcoolkeypk11.so
4) Install all three DOD certificates and put a checkmark on all of them.  Just click on each one and firefox will ask you if it's ok
[http://dodpki.c3pki.chamb.disa.mil/rootca.html](http://dodpki.c3pki.chamb.disa.mil/rootca.html)

---

### Post by JohnDeCarlo on 2008-07-21
> **tmaleshafske said:**
> Has anyone had any luck with the DELL texas instrument internal card reader?

I actually had some good luck with this with Ubuntu Gutsy, but now that I have installed Hardy, I have not been able to get it to work again.

I did the install using apt-get (aptitude, actually), rather than compiling from source, as indicated above.

Here is the information I have collected.

When I run "pcscd -f", it seems to identify the reader and card just fine:

00000000 pcscdaemon.c:295:main() pcscd set to foreground with debug send to stderr
00000734 pcscdaemon.c:513:main() pcsc-lite 1.4.99 daemon ready.
00369999 hotplug_libusb.c:478:HPAddHotPluggable() Adding USB device: 002:003
00000059 readerfactory.c:1116:RFInitializeReader() Attempting startup of O2 Micro Oz776 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so.1.3.1
00000235 readerfactory.c:983:RFBindFunctions() Loading IFD Handler 3.0
00000471 ifdhandler.c:1239:init_driver() LogLevel: 0x0003
00000344 ifdhandler.c:1249:init_driver() DriverOptions: 0x0000
00000015 ifdhandler.c:77:IFDHCreateChannelByName() lun: 0, device: usb:0b97/7762:libusb:002:003
00001184 ccid_usb.c:233:OpenUSBByName() Manufacturer: Ludovic Rousseau (ludovic.rousseau@free.fr)
00000331 ccid_usb.c:243:OpenUSBByName() ProductString: Generic CCID driver v1.3.1
00000339 ccid_usb.c:249:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
00046942 ccid_usb.c:397:OpenUSBByName() Found Vendor/Product: 0B97/7762 (O2 Micro Oz776)
00000020 ccid_usb.c:399:OpenUSBByName() Using USB bus/device: 002/003
00002406 ccid_usb.c:788:get_data_rates() declared: 9600 bps
00007998 ifdhandler.c:841:IFDHPowerICC() lun: 0, action: PowerUp
01148142 Card ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
01148154 ifdhandler.c:271:IFDHGetCapabilities() lun: 0, tag: 0xFAE
00000379 ifdhandler.c:313:IFDHGetCapabilities() Reader supports 1 slot(s)
191438487 eventhandler.c:365:EHStatusHandlerThread() Card Removed From O2 Micro Oz776 00 00
01614088 ifdhandler.c:841:IFDHPowerICC() lun: 0, action: PowerUp
01149083 eventhandler.c:438:EHStatusHandlerThread() Card inserted into O2 Micro Oz776 00 00
00000038 Card ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1


But when I run pcsc_scan, nothing happens:

PC/SC device scanner
V 1.4.11 (c) 2001-2007, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.4
Scanning present readers
Waiting for the first reader...

If I run ATR_analysis on what pcscd -f displays:

ATR_analysis 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
+ TS = 3B --> Direct Convention
+ T0 = DB, Y(1): 1101, K: 11 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU (223200 bits/s at 3.57 MHz)
  TC(1) = 00 --> Extra guard time: 0
  TD(1) = 80 --> Y(i+1) = 1000, Protocol T = 0
-----
  TD(2) = 1F --> Y(i+1) = 0001, Protocol T = 15 - Global interface bytes following
-----
  TA(3) = 03 --> Clock stop: not supported - Class accepted by the card: (3G) A 5V B 3V
+ Historical bytes: 00 31 C0 64 77 E3 03 00 82 90 00
  Category indicator byte: 00 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: C0
        - Application selection: by full DF name
        - Application selection: by partial DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 4 (pre-issuing data)
      Data: 77 E3 03 00
    Mandatory status indicator (3 last bytes)
      LCS (life card cycle): 82 (Proprietary)
      SW: 9000 (Normal processing.)
+ TCK = C1 (correct checksum)

Possibly identified card (using /home/jdecarlo/.smartcard_list.txt):
3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
        CAC (Common Access Card)

Any thoughts?

Thank you.

---

