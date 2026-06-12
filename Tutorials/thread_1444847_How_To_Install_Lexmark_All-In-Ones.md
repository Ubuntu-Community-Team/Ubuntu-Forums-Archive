---
title: "How To: Install Lexmark All-In-Ones"
date: 2010-04-01
forum: Tutorials
---

### Post by wbar2 on 2010-04-01
Recently Lexmark published drivers for many of its all-in-one printer/scanner/faxes. Here's how to get them working on Ubuntu 10.04 and 10.10. I've tested this on both Ubuntu 10.04 and 10.10 using printer models X5650 and X4650. I have tested it both on 32-bit and 64-bit machines. This tutorial should work for the following series of printers: X3600 Series, X4600 Series, X4900 Series, X5070 Series, X5600 Series, X6600 Series, X7600 Series, Z2400 Series.


[SIZE="2"]**1. Download and Extract the Lexmark Driver Installation Script**[/SIZE]

Here is the driver file for the printers listed above:
[http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz](http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz)

You might have a similar model not listed above. Find your driver here:
[http://support.lexmark.com/index?page=productSelection&linkSelected=node0&locale=EN&userlocale=EN_US](http://support.lexmark.com/index?page=productSelection&linkSelected=node0&locale=EN&userlocale=EN_US)

After the file has completed downloading, extract the script to your home folder. You can do this by double-clicking the file. Then click the "Extract" button near the top of the new window. On the left select your home folder (it will be your user name). Then click the "Extract" button at the bottom. Then click "Quit" at the prompt.


[SIZE="2"]**2. Install the Drivers and Printer Using "Sudo"**[/SIZE]

If you've tried running the installation script you have realized that it asks you for your root password, and it will not accept your user's password (by default Ubuntu has no root password). You will need to use "sudo" to run the script to make this work (for more information on sudo, visit [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)).

To do so go to Applications > Accessories > Terminal. In the terminal type:

```
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh
```

Follow the instructions in the prompt, making sure not to plug in the printer until instructed. Most likely you will end up with two printers installed, but thats ok. During the installation you will install the printer and Ubuntu will also detect it. Most likely the one Ubuntu detected and installed will work. Once the installation has finished, you can close the terminal window.

[SIZE="2"]**3. Setup Wireless (applicable models only)**[/SIZE]

If you have a wireless Lexmark All-In-One, you have a few more things to do to get it working without plugging in the USB cable. First, you need to find the IP address. You can do this by printing the network settings page from the printer as follows ([_source_]("http://support.lexmark.com/index?page=content&id=HO3372&locale=EN&userlocale=EN_US")). Press the setup button on your printer (its a physical actual button on the printer itself, not in Ubuntu; it might look like a wrench). Press the right or left arrow until you see the display say "Network Setup". Press "OK". Press "OK" where it says "Print Setup Page". Press "OK" again.

Now that you have the IP address of your printer, let's add it (thanks to Ubuntu forums user relapse for this part). In Ubuntu go to System > Administration > Printing. Right-click the printer that was added from the previous steps and select "Duplicate". Give the duplicate a new name, something like "Lexmark Wireless" or whatever you want.

Right-click this new wireless printer and select "Properties". Enter the IP address from the printout you got earlier in the "Device URI:" box. For example, if your printer's IP address is 123.45.67 enter "socket://123.45.67" without quotes. Click "OK" when finished.

If you've followed all the instructions on this tutorial you should now have two printers installed of the same version. One is for when you plug it in with the USB; the other is for wireless. **At this time, as far as a I know, scanning over the wireless is not available until Lexmark updates the drivers. If you know otherwise, please let me know.**


[SIZE="2"]**4. Print a Test Page; Test Scanning**[/SIZE]

You should now test to see if your printer works. Go to System > Administration > Printing. Right-click the printer you wish to test. Click the "Print Test Page" button. You may have two printers installed. If one does not print, try the other installed printer. One of them should work.

Scanning should work automatically now. Go to Applications > Graphics > Simple Scan. Try to scan something, and it should show up.


[SIZE="2"]**Ubuntu 10.04 64-bit Issue**[/SIZE]

If you are running Ubuntu 10.04 64-bit, you may need libstdc++5. Follow the instructions here: [http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000) This does not seem to be an issue on Ubuntu 10.10.

------------------------

**Complete Removal and Reversal.** If you want to completely reverse the above procedures and remove everything installed do the following:
1. Delete the downloaded archive of the drivers.
2. Delete the driver installation script (in your home folder according to the above instructions).
3. Delete the printer(s) by going to System > Administration > Printing, right-click the installed printer and select Delete.
4. Remove the printer drivers by going to Applications > Accessories > Terminal. Enter the following into the Terminal:
```
sudo dpkg -r lexmark-08z-series-driver
```

---

### Post by elys22 on 2010-04-29
Thank you! This worked perfectly for my 4900 on Ubuntu.

---

### Post by Blacksheep01 on 2010-04-30
I have a Lexmark x5650 and am having a problem getting it to work still. First, I've been using Linux for exactly 6 days, I actually installed it for my parents after their WinXP machine got a Trojan so bad I couldn't root it out with HiJackThis or ComboFix! This was their 20th+ virus that they "had no idea" where it came from, so I said, "it's time to try Linux." I've read the beginner manual, I managed to get Karmic 9.10 set up no problem, even got the beta of Wine up and running with my dad's favorite poker games, Full Tilt and Poker Stars and also Firefox, Chrome, Opera, Thunderbird, almost everything they had in Windows, so far they are happy.

My last problem is this printer, the x5650. I stumble across this thread when I had Karmic and tried it, hoping just maybe it would work, but it didn't. However, I have now upgraded to Lucid as of last night and still no luck.

Here is what happened. When I installed Karmic, the printer was detected but would not function, it would never print. I tried the steps here, knowing they might not work, and big surprise, they didn't. What happened was it would get to the point of the install where it asked to connect the USB cable, but it would never detect it and I'd close it out, try again, same problem. So I "removed" the printer from printer options thinking that would reset everything and re-detect the printer, but the printer was never detected again.

I then installed Lucid last night, thinking the printer would at least be detected now. Nope, it never was. I then followed these steps and ended up getting stuck at the "connect USB" cable part again. I have tried unplugging the printers power and USB and reconnecting and every combination. Nothing. So now my printer isn't auto detected and it doesn't notice when I plug it in during the driver installation. 

On a whim, scrambling for answers last night, I saw something about CUPS and installed it via synaptic. It not only did nothing for me, but now I don't even have the option to search for or manually add a printer (which wasn't working anyway). So I then uninstalled CUPS, but have the same problem. Admittedly I had little idea what CUPS was other than some kind of print server software, but I'm always willing to try something crazy and see if it works. 

So that is where I am. Any ideas how I can get this back on track? I feel like I need to reset all my printing options to default, but I don't know how. The other option running through my head is to just reformat and install Lucid from scratch, but damn, I just got everything else working and just reinstalled all their pictures and music, I'd hate to do that.

Thanks in advance. :)

---

### Post by Blacksheep01 on 2010-04-30
Nvm, I just went ahead and suffered the pain of a reformat, drivers worked on the first try after that. Excellent, my parents will be very happy now!

---

### Post by wbar2 on 2010-04-30
> **Blacksheep01 said:**
> Nvm, I just went ahead and suffered the pain of a reformat, drivers worked on the first try after that. Excellent, my parents will be very happy now!

Awesome. I'm sorry for not responding sooner and that you had to reformat to get it working, but I'm glad that you got it going.

---

### Post by Blacksheep01 on 2010-05-01
No problem on not getting to my post. The fresh install was probably a better idea anyway, I had a lot of loose files, old .debs and entries I didn't know how to remove after tinkering for the first few days and your advice here and the drivers link worked like a charm so thanks again for the original post!

My next problem is going to be the scanning, for some reason the scanner was not auto detected and was asking me to choose a device, which didn't work. I'm burning out after re-formating/re-installing everything tonight, but if you or anyone have any tips on why that scanner might not be detected and how to fix it, I'd appreciate it. Who knows though, sometimes with Ubuntu I've noticed I make a change and nothing happens right away, then it takes effect several minutes later, maybe the hard drive is on the way out or something, who knows, but scanner could be up and working tomorrow magically lol.

---

### Post by wbar2 on 2010-05-01
> **Blacksheep01 said:**
> No problem on not getting to my post. The fresh install was probably a better idea anyway, I had a lot of loose files, old .debs and entries I didn't know how to remove after tinkering for the first few days and your advice here and the drivers link worked like a charm so thanks again for the original post!

My next problem is going to be the scanning, for some reason the scanner was not auto detected and was asking me to choose a device, which didn't work. I'm burning out after re-formating/re-installing everything tonight, but if you or anyone have any tips on why that scanner might not be detected and how to fix it, I'd appreciate it. Who knows though, sometimes with Ubuntu I've noticed I make a change and nothing happens right away, then it takes effect several minutes later, maybe the hard drive is on the way out or something, who knows, but scanner could be up and working tomorrow magically lol.

I'm not sure why you can't get scanning working. Do you have a webcam integrated? I have had problems on a laptop with an integrated webcam conflicting with the scanner. Maybe you should open a new thread in the General Help section?

---

### Post by Blacksheep01 on 2010-05-01
No webcam, but good news, as I suspected, it is magically working after booting up the PC this afternoon. I did absolutely nothing to get it to appear, I simply tried scanning with simple scan again and it worked like a charm lol.

Thanks for reading through my posts, again, I'm uncertain if I am the only one experiencing this, but it does seem that when I make a change/update a program, nothing changes at first, then minutes/hours later or after next reboot, it is working.

---

### Post by smellems on 2010-05-03
I also installed the lexmark drivers for my x4975.  everything is working great with the usb cable plugged in.  I would like to configure the printer so that it connects to my wireless network.  there is no option for that on the printer menu (confirmed by lexmark).  is there a way to access the configuration so that I could configure SSID and WEP?

---

### Post by wbar2 on 2010-05-03
> **smellems said:**
> I also installed the lexmark drivers for my x4975.  everything is working great with the usb cable plugged in.  I would like to configure the printer so that it connects to my wireless network.  there is no option for that on the printer menu (confirmed by lexmark).  is there a way to access the configuration so that I could configure SSID and WEP?

I've never setup a wireless printer with Ubuntu. But here's what I think the process would be:

Go to System - Administration - Printing. Click Add. Ubuntu *should* detect it automatically and you should be able to add it right there. You've already installed the driver, so you should be able to select the x4975 driver when you add it.

So, in effect, you will have two printers installed. One will be the printer when it is hooked up by USB. The other will be for when the printer is used wirelessly. Let us know what happens.

EDIT: I have added wireless instructions above. Please test these on your specific model and let me know if it works.

---

### Post by giocarra on 2010-05-08
Hi wbar2,
I use two ubuntu (*), one is i386 (and I have a Lexmark X1195 printer that goes very fine) and the other is a amd64 which does not allow me to use the same printer.
I've used the way showed in a post inside this forum where is indicated a way for a 32 system and a little variation for the amd64 one.

But, as I told before I've not been able to use my Lexmark on the second Ubuntu.

Do you have a suggestion for me, since I see that You have a Ubuntu 64 O.S.?

Sorry for my bad English, but I'm from Italy..................

Best Regards, have a nice day.

giocarra

edit : (*) I mean Lucid Lynx 10.04 32-bit and Lucid Lynx amd64 64-bit, of course.

---

### Post by wbar2 on 2010-05-10
> **giocarra said:**
> Hi wbar2,
I use two ubuntu (*), one is i386 (and I have a Lexmark X1195 printer that goes very fine) and the other is a amd64 which does not allow me to use the same printer.
I've used the way showed in a post inside this forum where is indicated a way for a 32 system and a little variation for the amd64 one.

But, as I told before I've not been able to use my Lexmark on the second Ubuntu.

Do you have a suggestion for me, since I see that You have a Ubuntu 64 O.S.?

Sorry for my bad English, but I'm from Italy..................

Best Regards, have a nice day.

giocarra

edit : (*) I mean Lucid Lynx 10.04 32-bit and Lucid Lynx amd64 64-bit, of course.

The tutorial has been tested to work on 32-bit Lucid Lynx. I have attempted to get this to work on 64-bit, but I have not been able to. In the past I was able to install it after finding some libraries that were needed. It was libstdc++5. You might have to google around to find it. I'm not even sure if it will help. I may try to test it myself later this week.

---

### Post by tdf711 on 2010-05-12
you guys rock. I am very new to Linux, just did a clean install of Ubuntu 10.04  and needed to hook up my Lexmark 4690.  Instructions worked perfectly.  The only thing I have to add is I had to go into the Terminal and do a* sudo passwd *to change the root pw from nothing to something.  That resolved the problem of the install wizard not recognizing my password.  I thought the root pw would have been the password I used when I did the install, but guess not.  So far so good with Ubuntu.  :-\"

---

### Post by MyR on 2010-05-18
Would this work for the x2600 series?

You linked from this thread: [http://ubuntuforums.org/showthread.php?t=1021755](http://ubuntuforums.org/showthread.php?t=1021755)

thanks!

---

### Post by wbar2 on 2010-05-18
> **MyR said:**
> Would this work for the x2600 series?

You linked from this thread: [http://ubuntuforums.org/showthread.php?t=1021755](http://ubuntuforums.org/showthread.php?t=1021755)

thanks!

I'm not sure. I do know that the driver is different. The X2600 driver is located here (**_not_** the same as posted above):
[http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip](http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip)

I would think the process would be the same. The main issue is the installation script accepting your password. There are a few ways to do this. I just modified the tutorial above to what I think might be a better way. Try out the tutorial and let me know if it works and I will add your printer to this tutorial.

---

### Post by relapse on 2010-06-09
Thanks for the guide **wbar2**!

The wired installation for my Lexmark x4975 printer under Lucid went without a hitch. 

The wireless setup didn't work for me however. When it asks you to select a driver it asks for a ppd file which is nowhere to be found and trying a driver from the list of provided ones resulted in an error when I tried to finish the setup wizard.

There was an easy fix though. 

Go to System > Administration > Printers

After running the wired installation you'll have a new printer listed, e.g. Lexmark_4900_Series. Right-click on it and select Duplicate, give it a new name like "Lexmark_4900_Series_Wireless". 

[IMG]http://i46.tinypic.com/2ebhee8.jpg[/IMG]

Right-Click again and select properties. In the field marked Device URI, enter socket://IP_ADDRESS_OF_PRINTER. Then close the window.

[IMG]http://i50.tinypic.com/2i9oxm9.jpg[/IMG]

---

### Post by Jim1804 on 2010-06-13
I can confirm that these instructions also work for the Z2420 - can now print both wired and wirelessly with Ubuntu Karmic. Thanks!

---

### Post by PTelly on 2010-06-16
wbar2, Thank you very much. Have been try to get my Lexmark X7675 install since new driver came out. Have contacted Lexmark 3 times to no avail. Using the sudo passwd did the trick. Rest was easy installing the sh file.
Thanks again and have a Great Life.

Paul

---

### Post by wbar2 on 2010-06-18
> **relapse said:**
> Thanks for the guide **wbar2**!

The wired installation for my Lexmark x4975 printer under Lucid went without a hitch. 

The wireless setup didn't work for me however. When it asks you to select a driver it asks for a ppd file which is nowhere to be found and trying a driver from the list of provided ones resulted in an error when I tried to finish the setup wizard.

There was an easy fix though. 

Go to System > Administration > Printers

After running the wired installation you'll have a new printer listed, e.g. Lexmark_4900_Series. Right-click on it and select Duplicate, give it a new name like "Lexmark_4900_Series_Wireless". 

[IMG]http://i46.tinypic.com/2ebhee8.jpg[/IMG]

Right-Click again and select properties. In the field marked Device URI, enter socket://IP_ADDRESS_OF_PRINTER. Then close the window.

[IMG]http://i50.tinypic.com/2i9oxm9.jpg[/IMG]

Thanks! I've updated the tutorial!

---

### Post by n.hinton on 2010-06-21
How do you restore your root password back to the Ubuntu default? (i.e.same as after a fresh install)

---

### Post by MyR on 2010-06-21
> **n.hinton said:**
> How do you restore your root password back to the Ubuntu default? (i.e.same as after a fresh install)

There is no default root password.

---

### Post by wbar2 on 2010-06-21
> **giocarra said:**
> Hi wbar2,
I use two ubuntu (*), one is i386 (and I have a Lexmark X1195 printer that goes very fine) and the other is a amd64 which does not allow me to use the same printer.
I've used the way showed in a post inside this forum where is indicated a way for a 32 system and a little variation for the amd64 one.

But, as I told before I've not been able to use my Lexmark on the second Ubuntu.

Do you have a suggestion for me, since I see that You have a Ubuntu 64 O.S.?

Sorry for my bad English, but I'm from Italy..................

Best Regards, have a nice day.

giocarra

edit : (*) I mean Lucid Lynx 10.04 32-bit and Lucid Lynx amd64 64-bit, of course.

I recently was able to install the drivers on 64-bit and print. Maybe you should try again?

---

### Post by n.hinton on 2010-06-21
> How do you restore your root password back to the Ubuntu default? (i.e.same as after a fresh install)

> **MyR said:**
> There is no default root password.

Yes, so how do you restore it to that condition?

---

### Post by MyR on 2010-06-21
> **n.hinton said:**
> Yes, so how do you restore it to that condition?

not sure. probably something with adding -d to passwd. see "man passwd".

---

### Post by n.hinton on 2010-06-21
> **MyR said:**
> not sure. probably something with adding -d to passwd. see "man passwd".

'man passwd' only appears to reference user passwords

---

### Post by wbar2 on 2010-06-22
> **n.hinton said:**
> 'man passwd' only appears to reference user passwords

It also refers to the root user. This code worked for me:
```
sudo passwd -d root
```

---

### Post by n.hinton on 2010-06-22
Many thanks wbar2

Have been googling passwd and some suggest ```
sudo usermod -p ! root
``` I' not sure!

See [http://ubuntuforums.org/archive/index.php/t-846093.html](http://ubuntuforums.org/archive/index.php/t-846093.html)

---

### Post by wbar2 on 2010-06-22
> **n.hinton said:**
> Many thanks wbar2

Have been googling passwd and some suggest ```
sudo usermod -p ! root
``` I' not sure!

See [http://ubuntuforums.org/archive/index.php/t-846093.html](http://ubuntuforums.org/archive/index.php/t-846093.html)

I think you are correct. By changing the password to "!" you are both deleting the password and locking the account. The following code gives the same effect:

```
sudo passwd -d -l root
```

---

### Post by n.hinton on 2010-06-22
> **wbar2 said:**
> I think you are correct. By changing the password to "!" you are both deleting the password and locking the account. The following code gives the same effect:

```
sudo passwd -d -l root
```

Using ```
sudo getent shadow root|cut -d : -f 2
``` on a 'as installed installation' root password returns ```
!
``` been unable so far to establish if the condition is locked or unlocked

---

### Post by wbar2 on 2010-06-22
Post removed.

---

### Post by n.hinton on 2010-06-23
Excellent, many thanks wbar2

---

### Post by doclongopc on 2010-06-26
hi guys, I have a lexmark s405 on LL 10.04 amd64.
I found a tip to extract and install the official driver and it work fine, but only for printing.
I need to use the scanner that LL is able to see (lsusb and sane-find-scanner as 0x043d 0x0180 on libusb:002:006) but it doesn't work anywhere whit xsane or other.
Wbar2 can you help me?

---

### Post by n.hinton on 2010-06-26
Does it work with xsane if you run gksudo xsane? if it does try adding yourself to the saned group

---

### Post by doclongopc on 2010-06-27
just done, but nothing change.
someone know how estract or similar the source of driver?

---

### Post by Pougnet on 2010-06-28
Thanks so much for this, my printer is no longer a $100 paper weight.

---

### Post by n.hinton on 2010-06-28
Hi doclongopc,

Is this what you downloaded:[http://shorterlink.org/14752](http://shorterlink.org/14752)
and see here:[http://shorterlink.org/14753](http://shorterlink.org/14753)

Hi wbar2,

Just curious, why did you use ```
sudo sh lexmark-08z-series-driver-1.0-1.i386.deb.sh
``` and not```
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh
```

---

### Post by wbar2 on 2010-06-30
You know, honestly, I don't know the difference in them.

---

### Post by n.hinton on 2010-06-30
```
sh
```calls a bash script```
./
```runs 'executable' from current location

---

### Post by dexxyy on 2010-07-20
Clear and easy to follow tutorial. Cheers!!
Worked perfectly on Lexmark 3600-4600 Series

Thank you

---

### Post by doclongopc on 2010-07-20
Just done n.hinton, but nothing change.
Contacted the US or UK assistance by e-mail and suggested the phoronix guide at [http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=4]("http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=4").
It works fine for printing and now I can scan everything, also thanks to St. Gimp for fine adjusting.

The italian assistance say that we (linux user) are too much haker for their programmers and not much noumberouses (boh) to having a 64-bit fork

---

### Post by waterboy0911 on 2010-09-19
I don't know where I got wrong..

But mine is not working on lexmark 2300 series
 ```


jerald@jerald-laptop:~/Desktop$ sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
TRACKING IDENT = 170209
cpu speed = 1467 MHz
ram size = 2000.265625 MB
hd avail = 1551 MB
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
SELECTION ==> Lexmark Printer
auto Q in 2.6.32-24-generic = Lexmark--2300-Series
jerald@jerald-laptop:~/Desktop$ 

```
[IMG]http://i641.photobucket.com/albums/uu136/waterboy0911/Screenshot-3-2.png[/IMG]
please help.. :D

---

### Post by Cuppa-Chino on 2010-09-19
> **doclongopc said:**
> Just done n.hinton, but nothing change.
Contacted the US or UK assistance by e-mail and suggested the phoronix guide at [http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=4]("http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=4").
It works fine for printing and now I can scan everything, also thanks to St. Gimp for fine adjusting.

The italian assistance say that we (linux user) are too much haker for their programmers and not much noumberouses (boh) to having a 64-bit fork

hi, I can get it to print but not to scan did you do any other steps bar the ones in the tutorial to get the scanner to work (via USB)?

```
    Prerequisite packages: ia32-libs, openjdk-6-jre

    1. Get the latest driver
    2. Untar driver
    3. run in terminal "./lexmark-inkjet-09-driver-1.5.i386.deb.sh --noexec --target lexmark"
    4. a "lexmark" (from --target) directory was created, "cd lexmark"
    5. run in terminal "tar xvf instarchive_all --lzma"
    6. run in terminal "dpkg -i --force-all lexmark-inkjet-09-driver-1.5-1.i386.deb"
```

and can you scan via wireless ?

thanks

(Using 10.04 amd64 version)

---

### Post by 12apennachi on 2010-10-19
UPDATE: I no longer have this problem, if anyone else had this problem, update the libstdc++5 from [http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000) and reinstall it, it should work.

I am running ubuntu 10.04 Lucid 64-bit with an x-4650 Printer. When I installed the drivers everything went fine. When I go to print something to the printer via usb, it gives me an error and nothing happens. I check the printer's screen and it didn't receive any job. This printer works fine with windows, but I almost never use windows. any help would be appreciated. This is the troubleshooting code:

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest My_Lexmark_3600-4600_Series>,
 'cups_instance': None,
 'cups_queue': 'My_Lexmark_3600-4600_Series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/3600-4600%20Series',
                       'printer-info': u'My_Lexmark_3600-4600_Series',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Lexmark 3600-4600 Series, 1.0',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lexinkjet/08zero/bin/printdriver failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 53260,
                       'printer-uri-supported': u'ipp://localhost:631/printers/My_Lexmark_3600-4600_Series'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'usb://Lexmark/3600-4600%20Series',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raster',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'na_arch-a_9x12in',
                                                     u'adobe_LetterBA_8.5x110in',
                                                     u'na_legal_8.5x14in',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'adobe_HalfLetter_4.25x5.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_letter-plus_8.5x12.69in',
                                                     u'adobe_A4BA_209.973x2970.04mm',
                                                     u'iso_a5_148x210mm',
                                                     u'adobe_A5BL_155.434x236.079mm',
                                                     u'jis_b5_182x257mm',
                                                     u'adobe_B5JISBL_189.512x283.069mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'adobe_Envelope9_3.97222x8.875in',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_personal_3.625x6.5in',
                                                     u'adobe_EnvelopeBaronial_4.375x5.64306in',
                                                     u'na_a2_4.375x5.75in',
                                                     u'iso_b5_176x250mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_dl_110x220mm',
                                                     u'jpn_chou3_120x235mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'adobe_EnvelopeChokei40_89.9583x225.002mm',
                                                     u'adobe_EnvelopeKakugata3_216.041x277.001mm',
                                                     u'adobe_EnvelopeKakugata4_197.026x266.996mm',
                                                     u'adobe_EnvelopeKakugata5_7.48056x9.45in',
                                                     u'iso_c5_162x229mm',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-5x8_5x8in',
                                                     u'iso_a6_105x148mm',
                                                     u'adobe_CardA6BL_112.466x174.061mm',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'adobe_PostcardHagakiBL_107.491x174.061mm',
                                                     u'adobe_Photo312x5_3.49819x5in',
                                                     u'adobe_Photo312x5BL_96.333x153.106mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'adobe_4x6BL_109.079x178.506mm',
                                                     u'adobe_4x8_4x8in',
                                                     u'na_5x7_5x7in',
                                                     u'adobe_Photo5x7BL_134.479x203.906mm',
                                                     u'na_govt-letter_8x10in',
                                                     u'adobe_PhotoL_3.50556x5in',
                                                     u'adobe_PhotoLBL_3.8x6.02778in',
                                                     u'na_5x7_5x7in',
                                                     u'adobe_Photo2LBL_134.479x203.906mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'adobe_10x15cmBL_109.079x178.858mm',
                                                     u'na_5x7_5x7in',
                                                     u'adobe_13x18cmBL_134.479x204.329mm',
                                                     u'adobe_10x20cm_99.9984x200mm',
                                                     u'adobe_10x20cmBL_106.772x225.4mm',
                                                     u'om_large-photo_200x300',
                                                     u'adobe_9x13cm_89.9583x129.963mm',
                                                     u'adobe_15x21cm_150.036x209.973mm',
                                                     u'custom_min_3x5in',
                                                     u'custom_max_8.5x17in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 15,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': u'none',
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'My_Lexmark_3600-4600_Series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'',
                                 'printer-make-and-model': u'Lexmark 3600-4600 Series, 1.0',
                                 'printer-more-info': u'http://localhost:631/printers/My_Lexmark_3600-4600_Series',
                                 'printer-name': u'My_Lexmark_3600-4600_Series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1287533825,
                                 'printer-state-message': u'/usr/lexinkjet/08zero/bin/printdriver failed',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 53260,
                                 'printer-up-time': 1287533836,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/My_Lexmark_3600-4600_Series'],
                                 'queued-job-count': 2,
                                 'server-is-sharing-printers': True,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'ColorModel': u'Color',
                                            u'MediaType': u'Automatic',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintMirror': u'False',
                                            u'PrintQuality': u'Automatic',
                                            u'Sharpening': u'Automatic'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Lexmark;CMD:CPDNPA004;MODEL: 3600-4600 Series;CLASS:Printer;DES:Lexmark 3600-4600 Series;',
                      'device-info': u'Lexmark 3600-4600 Series',
                      'device-location': u'',
                      'device-make-and-model': u'Lexmark 3600-4600 Series'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lexinkjet/08zero/bin/printdriver failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '1',
                          '_remote_any': '1',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 567409}
Page 9 (Print test page):
{'test_page_attempted': '19/Oct/2010:20:17:43 +0000',
 'test_page_job_id': [6],
 'test_page_job_status': [(True,
                           6,
                           'My_Lexmark_3600-4600_Series',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 6,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/6',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'pennachi',
                            'job-printer-state-message': u'The printer is currently busy. Your job will resume as soon as current processing is complete.',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1287533896,
                            'job-printer-uri': u'ipp://pennachi-laptop:631/printers/My_Lexmark_3600-4600_Series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/6',
                            'job-uuid': u'urn:uuid:8b4502a9-0736-3731-74b6-df6b676e7ade',
                            'printer-uri': u'ipp://localhost/printers/My_Lexmark_3600-4600_Series',
                            'time-at-completed': None,
                            'time-at-creation': 1287533863,
                            'time-at-processing': 1287533863})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [19/Oct/2010:20:17:41 -0400] cupsdSetBusyState: Not busy',
               'D [19/Oct/2010:20:17:41 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:41 -0400] cupsdSetBusyState: Active clients',
               'D [19/Oct/2010:20:17:41 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:41 -0400] cupsdReadClient: 19 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:41 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:41 -0400] [Job 5] Loading attributes...',
               'D [19/Oct/2010:20:17:41 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:41 -0400] cupsdSetBusyState: Not busy',
               'D [19/Oct/2010:20:17:41 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:41 -0400] cupsdSetBusyState: Active clients',
               'D [19/Oct/2010:20:17:41 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:41 -0400] cupsdReadClient: 19 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:41 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:41 -0400] [Job 1] Loading attributes...',
               'D [19/Oct/2010:20:17:41 -0400] [Job 2] Loading attributes...',
               'D [19/Oct/2010:20:17:41 -0400] [Job 3] Loading attributes...',
               'D [19/Oct/2010:20:17:41 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:41 -0400] cupsdSetBusyState: Not busy',
               'D [19/Oct/2010:20:17:41 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:41 -0400] cupsdSetBusyState: Active clients',
               'D [19/Oct/2010:20:17:41 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:41 -0400] cupsdReadClient: 19 1.1 Create-Printer-Subscription 1',
               'D [19/Oct/2010:20:17:41 -0400] Create-Printer-Subscription /',
               'D [19/Oct/2010:20:17:41 -0400] cupsdCreateSubscription(con=0x7fe54155eaa0(19), uri="/")',
               'D [19/Oct/2010:20:17:41 -0400] pullmethod="ippget"',
               'D [19/Oct/2010:20:17:41 -0400] notify-lease-duration=86400',
               'D [19/Oct/2010:20:17:41 -0400] notify-time-interval=0',
               'D [19/Oct/2010:20:17:41 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [19/Oct/2010:20:17:41 -0400] Added subscription 16 for server',
               'D [19/Oct/2010:20:17:41 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:41 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [19/Oct/2010:20:17:41 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [19/Oct/2010:20:17:41 -0400] cupsdSetBusyState: Dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:43 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:43 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:43 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAcceptClient: 27 from localhost (Domain)',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 18 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:43 -0400] cupsdCloseClient: 18',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:43 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:43 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 27 POST /printers/My_Lexmark_3600-4600_Series HTTP/1.1',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 27 1.1 Print-Job 1',
               'D [19/Oct/2010:20:17:43 -0400] Print-Job ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:43 -0400] [Job ???] Auto-typing file...',
               'I [19/Oct/2010:20:17:43 -0400] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [19/Oct/2010:20:17:43 -0400] cupsdMarkDirty(----J-)',
               'D [19/Oct/2010:20:17:43 -0400] add_job: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:43 -0400] Adding default job-sheets values "none,none"...',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Adding start banner page "none".',
               'D [19/Oct/2010:20:17:43 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:43 -0400] cupsdMarkDirty(----J-)',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Adding end banner page "none".',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] File of type application/vnd.cups-banner queued by "pennachi".',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] hold_until=0',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Queued on "My_Lexmark_3600-4600_Series" by "pennachi".',
               'D [19/Oct/2010:20:17:43 -0400] cupsdMarkDirty(----J-)',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] job-sheets=none,none',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] argv[0]="My_Lexmark_3600-4600_Series"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] argv[1]="6"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] argv[2]="pennachi"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] argv[3]="Test Page"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] argv[4]="1"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] argv[5]="job-uuid=urn:uuid:8b4502a9-0736-3731-74b6-df6b676e7ade job-originating-host-name=localhost"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] argv[6]="/var/spool/cups/d00006-001"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[10]="SERVER_ADMIN=root@pennachi-laptop"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[13]="TZ=America/New_York"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[14]="USER=root"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[17]="IPP_PORT=631"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[18]="CHARSET=utf-8"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[19]="LANG=en_US.UTF-8"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[20]="PPD=/etc/cups/ppd/My_Lexmark_3600-4600_Series.ppd"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[21]="RIP_MAX_CACHE=755010k"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[23]="DEVICE_URI=usb://Lexmark/3600-4600%20Series"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[24]="PRINTER_INFO=My_Lexmark_3600-4600_Series"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[25]="PRINTER_LOCATION="',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[26]="PRINTER=My_Lexmark_3600-4600_Series"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[27]="CUPS_FILETYPE=document"',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] envp[28]="FINAL_CONTENT_TYPE=printer/My_Lexmark_3600-4600_Series"',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Started filter /usr/lib/cups/filter/bannertops (PID 4720)',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Started filter /usr/lib/cups/filter/pstopdf (PID 4721)',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Started filter /usr/lib/cups/filter/pdftopdf (PID 4722)',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Started filter /usr/lib/cups/filter/pdftoraster (PID 4723)',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Started filter /usr/lexinkjet/08zero/bin/printdriver (PID 4724)',
               'I [19/Oct/2010:20:17:43 -0400] [Job 6] Started backend /usr/lib/cups/backend/usb (PID 4725)',
               'D [19/Oct/2010:20:17:43 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:43 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] pstopdf 5 args: 6 pennachi Test Page 1 job-uuid=urn:uuid:8b4502a9-0736-3731-74b6-df6b676e7ade job-originating-host-name=localhost',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] PPD: /etc/cups/ppd/My_Lexmark_3600-4600_Series.ppd',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] STATE: +connecting-to-device',
               'D [19/Oct/2010:20:17:43 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] Printer using device file "/dev/usblp0"...',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] STATE: -connecting-to-device',
               'D [19/Oct/2010:20:17:43 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0x7fc1b7af76a0)',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] load_banner(filename="/var/spool/cups/d00006-001")',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] Page = 612x792; 18,36 to 594,787',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [19/Oct/2010:20:17:43 -0400] PID 4720 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] Resolution:',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] Page size: Letter',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] Width: 612.00, height: 792.00, absolute margins: 18.00, 36.00, 594.00, 787.20',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] Relative margins: 18.00, 36.00, 18.00, 4.80',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] PPD options: -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] PostScript to be injected:',
               'D [19/Oct/2010:20:17:43 -0400] [Job 6] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 -sOutputFile=-  -c .setpdfwrite -f -',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:43 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:43 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:43 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:43 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:43 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 22 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:43 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:43 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:43 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:43 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:43 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:43 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 22 1.1 Get-Job-Attributes 1',
               'D [19/Oct/2010:20:17:43 -0400] Get-Job-Attributes ipp://localhost/jobs/6',
               'D [19/Oct/2010:20:17:43 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/6) from localhost',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:43 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:43 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:43 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:43 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:43 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:43 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:44 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:44 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:44 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:44 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] PID 4721 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -sOutputType=5 -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=1 -dcupsRowStep=1 -scupsPageSizeName=Letter -c -f -_',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[10]="SERVER_ADMIN=root@pennachi-laptop"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[12]="TZ=America/New_York"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[13]="USER=root"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[16]="IPP_PORT=631"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[17]="CHARSET=utf-8"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[18]="LANG=en_US.UTF-8"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[19]="PPD=/etc/cups/ppd/My_Lexmark_3600-4600_Series.ppd"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[20]="RIP_MAX_CACHE=755010k"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[22]="DEVICE_URI=usb://Lexmark/3600-4600%20Series"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[23]="PRINTER_INFO=My_Lexmark_3600-4600_Series"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[24]="PRINTER_LOCATION="',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[25]="PRINTER=My_Lexmark_3600-4600_Series"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[26]="CUPS_FILETYPE=document"',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] envp[27]="FINAL_CONTENT_TYPE=printer/My_Lexmark_3600-4600_Series"',
               'D [19/Oct/2010:20:17:44 -0400] PID 4722 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] num_components = 1, depth = 1',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_gray = 1, dither_grays = 2',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_color = 0, dither_colors = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Updating PageSize to [612 792]...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting initial media size, [612 792] = 5100x6600 pixels...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting OutputType to "5"...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting cupsBitsPerColor to 8...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting cupsColorOrder to 0...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting cupsColorSpace to 1...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting cupsCompression to 1...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting cupsRowStep to 1...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting cupsPageSizeName to "Letter"...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] num_components = 3, depth = 24',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_gray = 0, dither_grays = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_color = 255, dither_colors = 256',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting initial media size, [612 792] = 5100x6600 pixels...',
               'I [19/Oct/2010:20:17:44 -0400] [Job 6] Processing page 1...',
               'D [19/Oct/2010:20:17:44 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:44 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] num_components = 3, depth = 24',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_gray = 0, dither_grays = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_color = 255, dither_colors = 256',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting LeadingEdge to 0...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] num_components = 3, depth = 24',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_gray = 0, dither_grays = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_color = 255, dither_colors = 256',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Updating PageSize to [612 792]...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] size = Letter',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] margins[] = [ 0.250000 0.500000 0.250000 0.066666 ]',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:44 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:44 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:44 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 22 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:44 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:44 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:44 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:44 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:44 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:44 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:44 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:44 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:44 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:44 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:44 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:44 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting LeadingEdge to 0...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] num_components = 3, depth = 24',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_gray = 0, dither_grays = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_color = 255, dither_colors = 256',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Setting LeadingEdge to 0...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] num_components = 3, depth = 24',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_gray = 0, dither_grays = 0',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] max_color = 255, dither_colors = 256',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] Updating PageSize to [612 792]...',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] size = Letter',
               'D [19/Oct/2010:20:17:44 -0400] [Job 6] margins[] = [ 0.250000 0.500000 0.250000 0.066666 ]',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] STATE: -media-empty-warning',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] STATE: -offline-report',
               'I [19/Oct/2010:20:17:45 -0400] [Job 6] Printer is now online.',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:17:45 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Received 8 bytes of back-channel data!',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] cups_print_chunked: xflip = 0, yflip = 0, height = 6260',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Read 15 bytes of print data...',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Wrote 15 bytes of print data...',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Received 15 bytes of back-channel data!',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:45 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:45 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:45 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:45 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:45 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Read 16 bytes of print data...',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Wrote 16 bytes of print data...',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Received 9 bytes of back-channel data!',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:45 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:45 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:45 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:45 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'E [19/Oct/2010:20:17:45 -0400] [Job 6] The printer is currently busy. Your job will resume as soon as current processing is complete.',
               'D [19/Oct/2010:20:17:45 -0400] [Job 6] Set job-printer-state-message to "The printer is currently busy. Your job will resume as soon as current processing is complete.", current level=ERROR',
               'D [19/Oct/2010:20:17:45 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:45 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:45 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:45 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:45 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:45 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:45 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:45 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:45 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:45 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:45 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:45 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:45 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:45 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:48 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:17:48 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:17:48 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:17:48 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:17:48 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:48 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:49 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:49 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:49 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:49 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:49 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:49 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:49 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:49 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:49 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:49 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:49 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:49 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:49 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:49 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:49 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:49 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:49 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:49 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:49 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:49 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:49 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:49 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:49 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:49 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:51 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:17:51 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:17:51 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:17:52 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:17:52 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:52 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:52 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:52 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:52 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 22 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:52 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:52 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:52 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:52 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:52 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:52 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:52 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:52 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:52 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:52 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:52 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:52 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:52 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:52 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:52 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:52 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:52 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:52 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:52 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:52 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:52 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:55 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:17:55 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:17:55 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:17:55 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:17:55 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:55 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:55 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:55 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:55 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:55 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:55 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:55 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:55 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:55 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:55 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:55 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:55 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:55 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:55 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:55 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:55 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:55 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:55 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:55 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:55 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:55 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:55 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:55 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:55 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:55 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:58 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:17:58 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:17:58 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:17:58 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:17:58 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:58 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:17:58 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:17:58 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:58 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:58 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:58 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:58 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:17:58 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:17:58 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:58 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:58 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:17:58 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:17:58 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:17:58 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:17:58 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:58 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:17:58 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:17:58 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:17:58 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:17:58 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:17:58 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:17:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:17:58 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:17:58 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:17:58 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:17:58 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:01 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:18:01 -0400] Report: clients=11',
               'D [19/Oct/2010:20:18:01 -0400] Report: jobs=6',
               'D [19/Oct/2010:20:18:01 -0400] Report: jobs-active=3',
               'D [19/Oct/2010:20:18:01 -0400] Report: printers=2',
               'D [19/Oct/2010:20:18:01 -0400] Report: printers-implicit=0',
               'D [19/Oct/2010:20:18:01 -0400] Report: stringpool-string-count=5138',
               'D [19/Oct/2010:20:18:01 -0400] Report: stringpool-alloc-bytes=10496',
               'D [19/Oct/2010:20:18:01 -0400] Report: stringpool-total-bytes=119496',
               'D [19/Oct/2010:20:18:01 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:18:01 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:18:01 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:18:01 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:01 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:18:02 -0400] [Job 4] Unloading...',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:02 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:02 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:02 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:18:02 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:18:02 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 22 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:18:02 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:18:02 -0400] [Job 4] Loading attributes...',
               'D [19/Oct/2010:20:18:02 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:02 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:02 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:02 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:02 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:02 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:02 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:18:02 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:02 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:02 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:18:02 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:18:02 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:18:02 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:18:02 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:02 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:18:02 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:18:02 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:18:02 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:04 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:18:04 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:18:04 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:18:05 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:18:05 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:05 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:05 -0400] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [19/Oct/2010:20:18:05 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.1.4:631',
               'D [19/Oct/2010:20:18:05 -0400] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [19/Oct/2010:20:18:05 -0400] cupsdNetIFUpdate: "wlan0" = fe80::eee:e6ff:feac:fe9b%wlan0:631',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:05 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:05 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:05 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 22 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:18:05 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:18:05 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:05 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:18:05 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:18:05 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:05 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:05 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:05 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:05 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:05 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:18:05 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:05 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:18:05 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:18:05 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:18:05 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:18:05 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:18:05 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:18:05 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:18:05 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:05 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:05 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:18:08 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:18:08 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:18:08 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:18:08 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:18:08 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:08 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:18:08 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:18:08 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:08 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:08 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:08 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:08 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:08 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:08 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:08 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:18:08 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:18:08 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:08 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:08 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:18:08 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:08 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:18:08 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:18:08 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:18:08 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:18:08 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:18:08 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:18:08 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:18:08 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:08 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:08 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:18:11 -0400] [Job 6] Read 8 bytes of print data...',
               'I [19/Oct/2010:20:18:11 -0400] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [19/Oct/2010:20:18:11 -0400] Saving subscriptions.conf...',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Printing jobs',
               'D [19/Oct/2010:20:18:11 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:18:11 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:18:11 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:18:11 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:11 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:11 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:11 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 22 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:18:11 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:18:11 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:11 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:18:11 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:18:11 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:11 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:11 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:11 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:11 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:11 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:18:11 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:11 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:18:11 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:18:11 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:18:11 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:18:11 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:18:11 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:18:11 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:18:11 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:11 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:11 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:18:14 -0400] [Job 6] Read 8 bytes of print data...',
               'D [19/Oct/2010:20:18:14 -0400] [Job 6] Wrote 8 bytes of print data...',
               'D [19/Oct/2010:20:18:14 -0400] [Job 6] Received 559 bytes of back-channel data!',
               'E [19/Oct/2010:20:18:14 -0400] [Job 6] The printer is busy printing.',
               'D [19/Oct/2010:20:18:14 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:14 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 20 1.1 Get-Jobs 1',
               'D [19/Oct/2010:20:18:15 -0400] Get-Jobs ipp://localhost/printers/',
               'D [19/Oct/2010:20:18:15 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:15 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:15 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:15 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:15 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 20 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:15 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:15 -0400] cupsdIsAuthorized: requesting-user-name="pennachi"',
               'D [19/Oct/2010:20:18:15 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1',
               'D [19/Oct/2010:20:18:15 -0400] Get-Printer-Attributes ipp://localhost/printers/My_Lexmark_3600-4600_Series',
               'D [19/Oct/2010:20:18:15 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/My_Lexmark_3600-4600_Series) from localhost',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [19/Oct/2010:20:18:15 -0400] Get-Notifications /',
               'D [19/Oct/2010:20:18:15 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:18:15 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:15 -0400] cupsdCloseClient: 22',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [19/Oct/2010:20:18:15 -0400] CUPS-Get-Printers',
               'D [19/Oct/2010:20:18:15 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [19/Oct/2010:20:18:15 -0400] CUPS-Get-Classes',
               'D [19/Oct/2010:20:18:15 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdAuthorize: No authentication data provided.',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [19/Oct/2010:20:18:15 -0400] CUPS-Get-Default',
               'D [19/Oct/2010:20:18:15 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [19/Oct/2010:20:18:15 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:15 -0400] cupsdReadClient: 20 WAITING Closing on EOF',
               'D [19/Oct/2010:20:18:15 -0400] cupsdCloseClient: 20',
               'D [19/Oct/2010:20:18:16 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:16 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:16 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:18:16 -0400] cupsdReadClient: 19 1.1 Get-Job-Attributes 1',
               'D [19/Oct/2010:20:18:16 -0400] Get-Job-Attributes ipp://localhost/jobs/6',
               'D [19/Oct/2010:20:18:16 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/6) from localhost',
               'D [19/Oct/2010:20:18:16 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:16 -0400] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [19/Oct/2010:20:18:16 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:16 -0400] cupsdAuthorize: Authorized as pennachi using PeerCred',
               'D [19/Oct/2010:20:18:16 -0400] cupsdReadClient: 19 1.1 Cancel-Subscription 1',
               'D [19/Oct/2010:20:18:16 -0400] Cancel-Subscription /',
               'D [19/Oct/2010:20:18:16 -0400] cupsdIsAuthorized: username="pennachi"',
               'D [19/Oct/2010:20:18:16 -0400] cupsdMarkDirty(-----S)',
               'D [19/Oct/2010:20:18:16 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [19/Oct/2010:20:18:16 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [19/Oct/2010:20:18:16 -0400] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [19/Oct/2010:20:18:16 -0400] cupsdReadClient: 20 GET /admin/log/error_log HTTP/1.1',
               'D [19/Oct/2010:20:18:16 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [19/Oct/2010:20:18:16 -0400] cupsdAuthorize: No authentication data provided.']}
Page 11 (Printer state reasons):
{'printer-state-message': u'The printer is busy printing.',
 'printer-state-reasons': [u'none']}
Page 12 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```
Also, when my printer is sleeping, and i print something, it turns on but doesn't print anything.

---

### Post by elzhi on 2010-11-17
Has anyone had any luck scanning wirelessly with any Lexmark printers? 
I can scan with the USB cable but would like to use the wireless feature.  I am able to print over wireless, but I'm not able to detect the scanner using xsane. Any insights would be appreciated.

---

### Post by wbar2 on 2010-11-17
> **elzhi said:**
> Has anyone had any luck scanning wirelessly with any Lexmark printers? 
I can scan with the USB cable but would like to use the wireless feature.  I am able to print over wireless, but I'm not able to detect the scanner using xsane. Any insights would be appreciated.

I don't think scanning is possible over the wireless until Lexmark updates their drivers for it (unless anyone else has any more insight on this).

---

### Post by wbar2 on 2010-11-23
I have updated the tutorial in light of some of the comments posted. I used to suggest changing the root password, but using sudo in the terminal to run the script works just fine. I have also added a note about a 10.04 64-bit issue.

---

### Post by doclongopc on 2010-11-25
hi guys,
now I have a serious problem: a friend on the italian forum says that were available the newest 64bit driver that works with 10.04, so I downloaded it and install, crazy. The new one works exactly like the installed, so I tried to delete all, by system->admin->print, and reinstall.
Here the SURPRISE: the installation fails due to two files ( -- lexmark-inkjet-legacy & -- lexmark-wsu-legacy)also present in my system, so I try to find them and then ANOTHER SURPRISE theese files seems not exist.

HEEELP!!!
How can I do?

this is the message reported into the terminal:

seeing ii  lexmark-legacy-wsu                    1.0-1                                                 This package contains the lexmark-legacy-wsu. 
seeing ii  lexmark-inkjet-legacy                 1.0-1                                                 This package contains the lexmark-inkjet-legacy. 
ls: impossibile accedere a /usr/local/lexmark/wsu_legacy/etc/*.desktop: Nessun file o directory
ls: impossibile accedere a /usr/local/lexmark/wsu_legacy/etc/*.png: Nessun file o directory


:D:D:D

**[SIZE="4"]SOLVED  REMOVED SIMPLY BY PACKAGE MANAGER[/SIZE]**

---

### Post by doclongopc on 2010-11-25
> **wbar2 said:**
> I have updated the tutorial in light of some of the comments posted. I used to suggest changing the root password, but using sudo in the terminal to run the script works just fine. I have also added a note about a 10.04 64-bit issue.

sorry where?:)

---

### Post by wbar2 on 2010-11-28
> **doclongopc said:**
> sorry where?:)

Where is what? The tutorial is the first post of this thread that you are responding to: [http://ubuntuforums.org/showpost.php?p=9062855&postcount=1](http://ubuntuforums.org/showpost.php?p=9062855&postcount=1)

---

### Post by zurgoth on 2010-11-30
--------------------------
I am running ubuntu 10.04 Lucid 64-bit with an x-4650 Printer. When I installed the drivers everything went fine. When I go to print something to the printer via usb, it gives me an error and nothing happens. I check the printer's screen and it didn't receive any job. This printer works fine with windows, but I almost never use windows. any help would be appreciated. This is the troubleshooting code:

----------------------------


Having the exact same problem here.  Did you find a fix for this?

---

### Post by wbar2 on 2010-12-02
> **zurgoth said:**
> --------------------------
I am running ubuntu 10.04 Lucid 64-bit with an x-4650 Printer. When I installed the drivers everything went fine. When I go to print something to the printer via usb, it gives me an error and nothing happens. I check the printer's screen and it didn't receive any job. This printer works fine with windows, but I almost never use windows. any help would be appreciated. This is the troubleshooting code:

----------------------------


Having the exact same problem here.  Did you find a fix for this?

Read that same post you quoted again. He has updated it to show that there is a solution. You need libstdc++5. The link is in his post.

---

### Post by Hack.The.Pow. on 2010-12-13
Just for your reference I was having issues with 64 bit printing from my x4650 on Ubuntu 10.10 and installing libstdc++5 fixed all my issues.

Thanks for the post!

---

### Post by navtex on 2012-04-20
I am on precise,trying to install lekmark x4975.
dpkg stops after few seconds with that message :
=============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz3599/pkg/files/dpkg_msgs

dpkg : erreur de traitement de lexmark-08z-series-driver-1.0-1.i386.deb (--install) :
 analyse du fichier '/var/lib/dpkg/tmp.ci/control' vers la ligne 9 paquet 'lexmark-08z-series-driver' :
 blank line in value of field 'Description' 
Des erreurs ont été rencontrées pendant l'exécution :
 lexmark-08z-series-driver-1.0-1.i386.deb
=============================

=============================
Execute: rm lexmark-08z-series-driver-1.0-1.i386.deb

-----------------------------------------------------
so I ask what is the matter there?

printing on SD card and transfer to printer is a solution too,if dont know better,thanks

---

### Post by IdanSuper on 2012-04-20
may it works with my lexmark x3300 printer?

---

### Post by Hack.The.Pow. on 2012-06-04
Anybody tried this with ubuntu 12.04?  Using the same drivers and having libstdc++5 doesn't help anymore....

---

### Post by nesretep on 2013-10-01
I am trying this with raring and the installer fails every time at the same place as navtex did.  My printer is a x4690, and none of the suggestions in this thread have worked so far.

---

### Post by nesretep on 2013-10-03
I was finally able to get the printer part to work by following these commands I found elsewhere online:
```
sudo apt-get install ia32-libs-multiarch xz-lzma 
wget [http://downloads.lexmark.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz](http://downloads.lexmark.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz) -O lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz 
tar xzvf lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz 
./lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target lexmark 
cd lexmark 
tar xJvf instarchive_all 
dpkg-deb -I lexmark-08z-series-driver-1.0-1.i386.deb 
mkdir raw-lexmark-archive 
dpkg-deb --raw-extract lexmark-08z-series-driver-1.0-1.i386.deb raw-lexmark-archive 
sed -i "/^ $/d" raw-lexmark-archive/DEBIAN/control 
cat raw-lexmark-archive/DEBIAN/control 
dpkg-deb -b ./raw-lexmark-archive fixed-lexmark-08z-series-driver-1.0-1.i386.deb 
sudo dpkg -i fixed-lexmark-08z-series-driver-1.0-1.i386.deb 
```


Basically it looks like it builds a new .deb package from the files in the original package.  After I installed the new "fixed" version the driver were listed in the add printer dialog under Lexmark.

---

