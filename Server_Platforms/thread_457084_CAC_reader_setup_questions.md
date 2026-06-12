---
title: "CAC reader setup questions"
date: 2007-05-28
forum: Server Platforms
---

### Post by captkirk on 2007-05-28
I am trying to setup a CAC reader for some work related items.  I am following the directions on [http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/](http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/) and I seem to be having a problem.  I used synaptic to install the first four packages, namely libusb, pcsc-lite, pcsc-tools, and ccid.  There is not a package for coolkey listed in synaptic.  I have found other links to the package, but when I try to install them, I get no libc6 installed, even though I can see it.  I would follow the directions and build coolkey, but I don't seem to have everything installed I need to build and I can't get enough information to tell me what needs to be installed to build coolkey.  Can someone point me in the direction of figuring out what my next step should be?

Thanks!

---

### Post by psyopper on 2007-06-03
Well...

I've been working on the same thing, and quite possibly for the same reasons! I decided to do it as the web page describes but I keep getting stuck at installing pcsc-tools. When I run "make install" it tells me it can't find pcsc-lite even though I set the environment variables myself.

Try downloading coolkey from the site listed and following the directions for the make.

---

### Post by captkirk on 2007-06-13
Well, your hint helped a little.  I download the coolkey and looked at what I needed to build it.  It took a while, but I was able to get it installed by installing the dependent packages.  I then installed coolkey and it already had what I needed, without a rebuild.  I then reflashed my reader and I was up and running!

---

### Post by contemno on 2007-06-14
i have a cac card as well, i followed the instructions on this page [http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/](http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/)
and it works excellent. i did it so i wouldnt have to type in a long password into ako, just login with my pin.

---

### Post by Alterios on 2007-07-06
I was searching for a way to get my cac card running and came across this thread. I went to the page and  can not make heads or tails of it. Can someone translate it into kindergarten level please. The first part I'm having trouble with is:
 "Set the build variable - “declare -x PKG_CONFIG_PATH=/usr/cac/lib/pkgconfig” - this is only needed for building, not later using these tools."
How do I do that?

The next thing I'm having problems with it that everytime I type: "cd libusb*0.1.12 && ./configure –prefix=/usr/cac && make && make install" it tells me; configure: error: invalid variable name: –prefix.

Please help. I have very easily set it up on both my wife's XP based comps and it is irking the hell out of me that it's so hard to do it in Ubuntu. I don't mind using the command line to install something as long as I can have a coherent non-uberuser set of instructions to follow. P.S. I have also tried the Gentoo guide as well. Thanks in advance.

---

### Post by captkirk on 2007-07-12
Go back to [http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/](http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/) and look at the last comment (it was posted yesterday).  Perhaps you posted it?  It gives the details I think you are looking for to install and build what you need to get cac support working under ubuntu 7.04

---

### Post by MrFSL on 2007-09-20
Had an opportunity to look into this DoD CAC card business recently and here is what I found:

First I was supplied with a Model SCR331 CAC card reader, P/N 903533 rev.1.0. First I visited [THIS WEBSITE]("http://www.txsystems.com/scm.html") and installed the latest firmware (using Windows).

Next I installed the following on feisty:
```
sudo apt-get install libusb-0.1-4 libpcsclite1 libpcsclite-dev pcscd pcsc-tools build-essential autoconf xlibs-dev libccid
```

I plugged the card reader into my Feisty laptop.

Restarted the pcsc daemon:
```
sudo /etc/init.d/pcscd restart
```

Made sure that the card reader was functioning using:
```
pcsc_scan
```

Next I downloaded coolkeys from [HERE.]("http://directory.fedora.redhat.com/download/coolkey/coolkey-1.1.0.tar.gz")

Extracted it to my desktop, changed directory, and compiled:
```
tar xvzf coolkey-1.1.0.tar.gz
cd coolkey-1.1.0
autoconf
./configure
make
sudo make install
```

I installed all the correct certificates and configured firefox/mozilla using the tail end of [THIS]("http://www7320.nrlssc.navy.mil/pubs/2006/CommonAccessCardLinux.pdf") paper.

Everything works as expected.

Make sure to check out the following resources:
[https://www.us.army.mil/suite/thread/37814](https://www.us.army.mil/suite/thread/37814) (DoD Employees Only)


[http://symbolik.wordpress.com/?s=cac+linux](http://symbolik.wordpress.com/?s=cac+linux)


[http://gentoo-wiki.com/HOWTO_DoD_CAC](http://gentoo-wiki.com/HOWTO_DoD_CAC)



And definitely check out the following:
[http://ossg.disa.mil/projects/linuxcac/](http://ossg.disa.mil/projects/linuxcac/)

---

### Post by EricBaenen on 2007-10-11
Some consolidated instructions for using a CAC card for machine login, screensaver, Firefox, etc. at [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

---

### Post by troxy18 on 2007-11-26
Just my experience getting a CAC reader to work in Linux.

MY system specs, Lenovo Thinkpad T61 with built in lenovo integrated smartcard reader.  Running Ubuntu 7.10 Gutsy Gibbon for x86-64 processor.

The Lenovo card reader was not supported in the version of libccid supported by Synaptic.  a quick google search revealed that version 1.3.1-1 in the Hardy Heron repository does support my reader. ([http://packages.ubuntu.com/hardy/libs/libccid](http://packages.ubuntu.com/hardy/libs/libccid)) That required some newer versions of other dependencies than the 7.10 repositories had.  I ended up pulling off a few other new versions of related packages.

Here are links to all the packages I installed
[http://mirror.clarkson.edu/pub/ubuntu/pool/universe/c/ccid/libccid_1.3.1-1_amd64.deb](http://mirror.clarkson.edu/pub/ubuntu/pool/universe/c/ccid/libccid_1.3.1-1_amd64.deb)
[http://mirror.clarkson.edu/pub/ubuntu/pool/universe/p/pcsc-lite/libpcsclite1_1.4.4-2_amd64.deb](http://mirror.clarkson.edu/pub/ubuntu/pool/universe/p/pcsc-lite/libpcsclite1_1.4.4-2_amd64.deb)
[http://mirror.clarkson.edu/pub/ubuntu/pool/universe/p/pcsc-lite/pcscd_1.4.4-2_amd64.deb](http://mirror.clarkson.edu/pub/ubuntu/pool/universe/p/pcsc-lite/pcscd_1.4.4-2_amd64.deb)
[http://mirror.clarkson.edu/pub/ubuntu/pool/universe/p/pcsc-tools/pcsc-tools_1.4.11-1_amd64.deb](http://mirror.clarkson.edu/pub/ubuntu/pool/universe/p/pcsc-tools/pcsc-tools_1.4.11-1_amd64.deb)
[http://mirror.clarkson.edu/pub/ubuntu/pool/universe/c/coolkey/coolkey_1.1.0-3_amd64.deb](http://mirror.clarkson.edu/pub/ubuntu/pool/universe/c/coolkey/coolkey_1.1.0-3_amd64.deb)

Installing those 5 packages got the card reader working so where I could run pcsc_scan and get results and recognition when I plugged my cac card in.  I set the security device in Firefox to be /usr/lib/pkcs11/libcoolkeypk11.so which was the coolkey install location.

At this point I tried quite a few things trying to get my certificates to work, restarting into vista and exporting my certificates there, then importing them into Firefox in Ubuntu was the first thing I tried.  Then trying to do a cac login to ako in Ubuntu it would ask for the passcode, I would input it, and it would give the default AKO 403 error message for cac login.  The error message prompted to register my cac certificates through a normal AKO login.  I did that and it all started working through Firefox.

My suggestion to others is to get the card reader working where it will recognize your card, add the security device module to firefox, then see if you can register your cac card in ako and follow their steps to see if they work.

Let me know if these instructions are any help.

---

### Post by HarleySteve on 2007-12-05
I have followed this AWESOME walk-through

[http://ubuntuforums.org/showthread.php?t=564763&highlight=cac+reader](http://ubuntuforums.org/showthread.php?t=564763&highlight=cac+reader)

I was diging through some stuff at work and found a PCMCIA Card Reader, SCR 201, Made by SCM Microsystems.  I think the writeup and all the info I have found was based on a USB CAC Reader.  Has anyone had any success with a PCMCIA or Internal CAC Reader?  Or would any one have any ideas or where to start looking?

Thanks,
Steve

---

### Post by battlesound on 2007-12-06
I've been going through a couple walk-throughs, but I'm stuck now.

```
battlesound@dell:~$ pcsc_scan
PC/SC device scanner
V 1.4.9 (c) 2001-2006, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.2
Scanning present readers
Waiting for the first reader...

```

Obviously, the ActivCard v 2.0 usb card reader doesn't work.  Can it be flashed to work like the SCM-331??

Or is there another way to get it to work?

---

### Post by MrFSL on 2007-12-06
There is a reason why the scr331 is referenced as the "working solution."  As it is the reader is only 1/2 the problem. There are many different CAC cards that are made by many different manufacturers. Currently, the SCR331 is the only reader to support the latest cards.

My suggestion - the SCR331 is cheap and easily found (even pre-patched) on the internet.

---

### Post by battlesound on 2007-12-17
Sweet.  It works.  I just got my SCR 331, flashed the firmware with windows xp (quite a hassel to have it only work that way, plus it's hard to find what you need to download)... 

I hooked up the cac reader to my ubuntu studio 7.10 laptop, restarted pcscd as stated (which returned "okay") and then did pcsc_scan, showed status perfectly.

I already had the certificates downloaded in firefox (I think I used the DOD Configuration add-on).

it worked out just fine... went to NMCI email address, did my cac password and my email login info and nmci webmail came up!  Awesome.  Too many IT folks saying it would never be supported or work!!  Nice.  Thanks guys for the help.

More info is available at:
[https://help.ubuntu.com/community/CommonAccessCard]("https://help.ubuntu.com/community/CommonAccessCard")

---

### Post by MrFSL on 2008-01-11
Just a quick note - It is no longer necessary to have XP to flash the firmware.

The manufacturer has now released a utility to update the firmware from linux.
[http://www.scmmicro.com/security/view_product_en.php?PID=2](http://www.scmmicro.com/security/view_product_en.php?PID=2)

Furthermore it looks like increased driver support as well.

Things to note - the firmware utility, and the firmware wizard says there is no firmware update for Linux. So you would have to download the bin file from the Windows firmware updater.

Also, you have to make sure when using this utility that it isn't being used by an application. For me that meant stopping pcscd:
```
sudo /etc/init.d/pcscd stop
```
After the update:
```
sudo /etc/init.d/pcscd start
```

Worked Great!

---

### Post by Remanifest on 2008-01-16
Please see the Wiki that myself (Onyx12) and others have worked on.  It answers many of the questions raised in this thread... specificially, that an ActivCard USB Reader 2.0 **will** work with the SCM firmware.  I don't want people to keep spending money where they don't really need to.

[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

---

### Post by ZanexGt on 2008-01-19
> **battlesound said:**
> 
it worked out just fine... went to NMCI email address, did my cac password and my email login info and nmci webmail came up!  Awesome.  Too many IT folks saying it would never be supported or work!!  Nice.  Thanks guys for the help.

More info is available at:
[https://help.ubuntu.com/community/CommonAccessCard]("https://help.ubuntu.com/community/CommonAccessCard")

Battlesound, I am able to log into my email however, when i try to open a mail item I get the following error:

"HTTP/1.1 500 Internal Server Error"

Does anyone know what this error means? 

I can't seem to open any mail items in Microsoft outlook web access however, all other sites requiring DOD CAC work. I'm stuck! 

Any help is appreciated.

---

### Post by Ds2600 on 2008-01-27
> **Remanifest said:**
> Please see the Wiki that myself (Onyx12) and others have worked on.  It answers many of the questions raised in this thread... specificially, that an ActivCard USB Reader 2.0 **will** work with the SCM firmware.  I don't want people to keep spending money where they don't really need to.

[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

I used this and ran into the same problem where I get

```

PC/SC device scanner
V 1.4.5 (c) 2001-2006, Ludovic Rousseau
Compiled with PC/SC litev ersion 1.2.9-beta9
Scanning present readers
Waiting for the first reader...
```

And am using an ActivCard reader, is there something I am missing?

---

### Post by captkirk on 2008-01-29
I am no expert, but the fastest way *I* know to get an activcard reader to work is to update the reader.  

You might also try the restart command where you are.  It was up a couple of posts.  That helped me at one time.

---

### Post by Remanifest on 2008-01-30
> **Ds2600 said:**
> I used this and ran into the same problem where I get

```

PC/SC device scanner
V 1.4.5 (c) 2001-2006, Ludovic Rousseau
Compiled with PC/SC litev ersion 1.2.9-beta9
Scanning present readers
Waiting for the first reader...
```

And am using an ActivCard reader, is there something I am missing?

Did you flash the firmware?  If so, it should be good to go.

If it's not, I'm usually in #Ubuntu on FreeNode, and I'll be able to help you out later on today if you want.  I want to make sure everyone who has one of these is able to get it working properly.

---

### Post by Remanifest on 2008-01-30
> **ZanexGt said:**
> Battlesound, I am able to log into my email however, when i try to open a mail item I get the following error:

"HTTP/1.1 500 Internal Server Error"

Does anyone know what this error means? 

I can't seem to open any mail items in Microsoft outlook web access however, all other sites requiring DOD CAC work. I'm stuck! 

Any help is appreciated.

ZanexGt,
Chances are that you didn't put your DOMAIN before the username.

EX:  NADSUSEA\first.last
       Password

Another common variation for NADSUSEA is NADSUWE.  Give those a try (or whatever your domain is), and let us know how that goes.

---

### Post by Vinnie_Fits on 2008-04-06
[FONT="Lucida Sans Unicode"][SIZE="4"]**Quick and Dirty CAC install on Gutsy Gibbon**[/SIZE][/FONT]

I had to mix directions from two webpages I found by googling.

[http://ubuntuforums.org/showthread.php?t=564763&highlight=cac%20reader%20install](http://ubuntuforums.org/showthread.php?t=564763&highlight=cac%20reader%20install)
 and
[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard) 

These worked for the most part but there were some minor things which caused frustration (like locating the libcoolkeypk11.so file in Firefox. I couldn't find the file where it was supposed to be, so I had to hunt. Anyway, I made this document up for my future reference but decided to slap it up here in case it helps anyone else. The full directions aren't here, I highly recommend clicking on and reading both the above links thoroughly before using my directions so you can understand better the issues I was having and maybe then it will make some sense to you. However, if you have the SCR 331 USB smart card reader with part no. 904622 (and not an earlier part number), these directions below will probably work just fine for you. Remember, it doesn't have all the inf you might need but serves well as a checklist for me for future installation on another Ubuntu box.

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
wget http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt –output-document=/home/gniibe/.smartcard_list.txt
```
 
into your terminal and it will get the latest card info. Then run the pcsc scan again. If your card is in the updated list, you should see something akin to the first result above when doing the scan (I had this problem with a CAC and this worked for me).

**Install Coolkey from Synaptic**
My recommendation is don't bother trying to install it manually through the terminal or getting the deb package. It's in the Gutsy repository so just install it in that manner. Open System > Administration > Synaptic Package manager. Search for coolkey. Mark it for upgrade and apply. It will download one additional dependency. Close out Synaptic after installation.

**Install authentication for Firefox**
From within Firefox, Edit-> Preferences -> Advanced -> Encryption.
Click Advanced Tab
Click “Security Devices” button
Click “Load” button
Type “CAC Module” in module name
Browse to the file “/usr/lib/pkcs11/libcoolkeypk11.so” and click OK and OK again. (File might also be in /usr/**local**/lib/pkcs11/libcoolkeypk11.so).

**Install DOD Root Certificates**
Go here [http://dodpki.c3pki.chamb.disa.mil/rootca.html](http://dodpki.c3pki.chamb.disa.mil/rootca.html) and click on the links to install the root certificates. Check all three boxes and click “Install”. You may get some error on the first one about not being able to install it because it's not signed. Just keep clicking Yes (about 4 times I think). The other two links shouldn't give you a problem.

**Check certificates install in Firefox**
Edit > Preferences > Advanced > “View Certificates”. ***WARNING! IT MAY ASK YOU FOR YOUR CAC PIN. Don't make the mistake of typing in your Firefox main password (if you use one) or you may lock out your CAC!*** You should see a bunch of certificates now under U.S. Government. I would specifically for the three you just installed, but you should see all the common ones you see on a windows machine.

**Verify CAC works**
Browse to the site you need to login with your CAC and try it out! Or go to [https://www.us.army.mil/](https://www.us.army.mil/) and do the CAC login option. It should popup a little window and ask you to pick the certificate. Don't change it, just click OK and you should be logged in. It may or may not ask for your PIN (probably not if you bother to check to see if the certificates were loaded/installed in Firefox per the Check certificate install in Firefox directions in the above paragraph.

ATTACH: Zipped doc file containing above for your printing pleasure!

---

### Post by bone2006 on 2008-07-09
Thanks

---

