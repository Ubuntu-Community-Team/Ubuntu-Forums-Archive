---
title: "The Simple Brother MFC-240C Hardy How To"
date: 2008-09-06
forum: Tutorials
---

### Post by chrisby on 2008-09-06
The instructions from Brother's Website work fine [http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html") for Hardy 32 bit (or Intrepid 32 bit), but for the lazy like me here they are without any of the other distro stuff:

```

sudo mkdir /usr/share/cups/model
sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd
sudo mkdir /var/spool/lpd
sudo apt-get install tcsh sane-utils
```

install mfc240clpr-1.0.1-1.i386.deb from 

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc240clpr-1.0.1-1.i386.deb&lang=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc240clpr-1.0.1-1.i386.deb&lang=English_lpr")

install mfc240ccupswrapper-1.0.1-1.i386.deb from 

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/mfc240ccupswrapper-1.0.1-1.i386.deb&lang=English_gpl]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/mfc240ccupswrapper-1.0.1-1.i386.deb&lang=English_gpl")

now for the scanner:
install brscan2-0.2.4-0.i386.deb from 

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.4-0.i386.deb&lang=English_sane]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.4-0.i386.deb&lang=English_sane")

and to make the key on the printer work for scanning install brscan-skey-0.2.1-1.i386.deb from [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/s-keytool/brscan-skey-0.2.1-1.i386.deb&lang=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/s-keytool/brscan-skey-0.2.1-1.i386.deb&lang=English_lpr")


Now plug your usb cable into the computer, and Ubuntu should automatically recognize the printer/scanner.

Happy printing!!!

---

### Post by Rocket2DMn on 2008-09-07
I have approved your post, but can you please add a link to the original source, please.  Otherwise I will need to remove this thread.  Thank you.

---

### Post by chrisby on 2008-09-07
fixed!

---

### Post by Rocket2DMn on 2008-09-07
Thank you.

---

### Post by BBgrave on 2008-09-07
**[Buy Ads](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[Sell Ads](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by tardis on 2008-09-09
Thanks really helped to set up with these instruction was not getting there on my own....:)

---

### Post by xualzan on 2008-10-08
best thread to date, thanks a lot for this.

---

### Post by chrisby on 2008-10-29
Thanks, glad it worked for you.  

I just followed the steps again on 8.10 RC and it works flawlessly.

---

### Post by ferral-cat on 2008-11-07
Just want to confirm that this works 100% on Ubuntu 8.10 (Intrepid) as well.  

And here is the code to install the packages from the command line:

```

sudo dpkg -i --force-architecture mfc240clpr-1.0.1-1.i386.deb

```

and so on

---

### Post by jay vyas on 2008-11-14
Hello
I am still lost on this install.tests work, printing motion,paper comes out but no print-no ink mark.New learner to Ubuntu and need help.Thanks

---

### Post by chrisby on 2008-11-15
I need more information.  Did you follow all steps, and its printing blank?

---

### Post by Eric_Denison on 2008-11-30
Chrisby, thanks for this.  Just one little snag.  I'm installing in 8.10 and when installing the cupswrapper am getting this error message on the package installer:  Error: Dependency is not satisfiable: mfc260clpr

Is this because I'm installing mfc-240c and it is just defaulting to mfc260c because I'm using 8.10?

ferral-cat posted this: sudo dpkg -i --force-architecture mfc240clpr-1.0.1-1.i386.deb

I will try using the terminal with this code and see what happens.

Everything else downloaded perfectly in 8.10.  Thanks, I'm a bit new to all of this so still playing around and making mistakes.

---

### Post by syntaxerrorsix on 2008-11-30
Is there any intrinsic difference in setup between Hardy and Intrepid?  I'm running 8.10 and managed to get the mfc240c to print before discovering this post but I cannot get it to scan from the button or from Xsane after installing the scanner driver packages.

With Xsane I get error message "failed to open device 'brother2:bus3;dev1':

Error during device I/O"

From the button I get "Connecting to PC" forever....

All prerequisites appear to be met and folders suggested in the first post were already present.

---

### Post by syntaxerrorsix on 2008-11-30
> **Eric_Denison said:**
> Chrisby, thanks for this.  Just one little snag.  I'm installing in 8.10 and when installing the cupswrapper am getting this error message on the package installer:  Error: Dependency is not satisfiable: mfc260clpr

Is this because I'm installing mfc-240c and it is just defaulting to mfc260c because I'm using 8.10?

ferral-cat posted this: sudo dpkg -i --force-architecture mfc240clpr-1.0.1-1.i386.deb

I will try using the terminal with this code and see what happens.

Everything else downloaded perfectly in 8.10.  Thanks, I'm a bit new to all of this so still playing around and making mistakes.


sudo dpkg -i --force-architecture mfc240clpr-1.0.1-1.i386.deb

Is what I used to get the printer side of the house up and running.  Unfortunately I'm still cut an pasting CL without fully understanding it but it did in fact work.  Hope to learn something useful in regards to the scanner next.

---

### Post by robi on 2008-12-01
> **syntaxerrorsix said:**
> Is there any intrinsic difference in setup between Hardy and Intrepid?  I'm running 8.10 and managed to get the mfc240c to print before discovering this post but I cannot get it to scan from the button or from Xsane after installing the scanner driver packages.

With Xsane I get error message "failed to open device 'brother2:bus3;dev1':

Error during device I/O"

From the button I get "Connecting to PC" forever....

All prerequisites appear to be met and folders suggested in the first post were already present.

Try this

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.

2. then locate the following lines:
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", [COLOR="Yellow"][COLOR="Red"]MODE="0664"[/COLOR][/COLOR]
SUBSYSTEM=="usb_device",                [COLOR="Yellow"][COLOR="Red"]MODE="0664"[/COLOR][/COLOR]

and change MODE="0664" to MODE="0666"

Hope it works for you like it worked for me.

---

### Post by syntaxerrorsix on 2008-12-01
> **robi said:**
> Try this

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.

2. then locate the following lines:
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", [COLOR="Yellow"][COLOR="Red"]MODE="0664"[/COLOR][/COLOR]
SUBSYSTEM=="usb_device",                [COLOR="Yellow"][COLOR="Red"]MODE="0664"[/COLOR][/COLOR]

and change MODE="0664" to MODE="0666"

Hope it works for you like it worked for me.

I've already gone that route with no joy.

Thanks for the suggestion however.

---

### Post by syntaxerrorsix on 2008-12-09
> **robi said:**
> Try this

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.

2. then locate the following lines:
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", [COLOR="Yellow"][COLOR="Red"]MODE="0664"[/COLOR][/COLOR]
SUBSYSTEM=="usb_device",                [COLOR="Yellow"][COLOR="Red"]MODE="0664"[/COLOR][/COLOR]

and change MODE="0664" to MODE="0666"

Hope it works for you like it worked for me.



Seems after running Ubuntu for a week or so I decided to ditch XP for good.  I spent about half a day backing up, partitioning and installing.

Last on the list was printer drivers.  Following the above commands now allows Xsane to scan.  The machine will still not scan from the button as it seeks the PC forever. 

One step closer.

---

### Post by bozodclown on 2008-12-10
Had same issue, the link provided in first post is incorrect, it is for 260C, copied the link and changed to 240C. The installation worked and printer was automatically detected.

---

### Post by syntaxerrorsix on 2008-12-11
More partial success.  It appears you have to run the bscan-skey program after each re-boot or add it to your start sequence or sessions menu (system-preferences-sessions (add+file name)in order to use the function.  

This allows me now to scan (by button) to Gimp (as image) but not to Thunderbird (as Email) nor to a folder view (as file) and zero luck with scan to OCR.  

So I can scan now either initiated from the hardware or software but 3/4 of the options are still not available but the major hurdle was getting the scanner to communicate period.

If there is anyone out there pointing and laughing as they read this feel free to impart your experiences :)

---

### Post by syntaxerrorsix on 2008-12-11
I have found that scanning to file from the button creates a folder/file under the home directory in the "brscan" folder.  It doesn't actually tell you that it has happened but this is where the scanned image is deposited.

1/2 the options are working/discovered now.

---

### Post by ferral-cat on 2008-12-11
When I had to reinstall Ubuntu 8.10 I ran int so em trouble with the scanner part.  

So what i did was remove the 2 brscan program via Synaptic and start over from scratch.  

This page was very helpful:

[http://wiki.archlinux.org/index.php/Brother_MFC-420CN](http://wiki.archlinux.org/index.php/Brother_MFC-420CN)

Disregard the "rpmextract" part because we are working with the .deb package format instead of .rpm

I also made the suggested modifications to /etc/udev/rules.d/40-basic-permissions.rules

After all this I was still getting the error in SANE so I rebooted the PC and after that the error has disappeared.  

Yay.

---

### Post by FireFighter on 2008-12-24
> **chrisby said:**
> The instructions from Brother's Website work fine [http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html") for Hardy 32 bit, but for the lazy like me here they are without any of the other distro stuff:

```

sudo mkdir /usr/share/cups/model
sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd
sudo mkdir /var/spool/lpd
sudo apt-get install tcsh sane-utils
```

install mfc240clpr-1.0.1-1.i386.deb from 

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc240clpr-1.0.1-1.i386.deb&lang=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc240clpr-1.0.1-1.i386.deb&lang=English_lpr")

install mfc240ccupswrapper-1.0.1-1.i386.deb from 

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/mfc260ccupswrapper-1.0.1-1.i386.deb&lang=English_gpl]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/mfc260ccupswrapper-1.0.1-1.i386.deb&lang=English_gpl")



I followed chrisby's how to and it worked well except that the url's here on one of these files was pointed to the wrong printer. Here is the page for the latest drivers for the printing side of the MFC-240C: 

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-240C](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-240C)

Just scroll down to the proper printer and click on the file needed (deb extension), install them just as chrisby advised, and all should work well. Did for me once I figured out the intitial problem. Hope this helps all who are searching for a solution. Great post by the way chrisby, really simplifies things! Thank you!

---

### Post by manco1911 on 2009-02-18
Hi, im using Ubuntu 8.10 Intrepid Ibex, and the Brother MFC-240c
Printing works 100%
But when trying to scan with XSane i get :

"Failed to open device 'brother2:bus1;dev1':
 Error during device I/O "

:(

I followed this thread instructions step by step.. 
What could be going on ?

---

### Post by manco1911 on 2009-02-18
ok, after trying all the tips on the tread, this is my result:

1) sudo dpkg -i --force-architecture mfc240clpr-1.0.1-1.i386.deb

"dpkg: error processing mfc240clpr-1.0.1-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc240clpr-1.0.1-1.i386.deb"

So, instead of c/p lines, i tryied to understand what was going on. (yes, im quite new to this, please be patient with me)

Obiusly the file is missing.
Thanksfully i could install the packages manualy (winstyle.. :oops:)

2) . Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
   . then locate the following lines:
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

and change MODE="0664" to MODE="0666"

This aparently didnt do anything.. with 0666 or 0664 works.. either way.

So, the original packages worked 100% on Intrepid. 
The issue i was having was that i had the printer pluged in a USB hub. If i plug it directly to one of the main USB it works printing/scanning.

How could i solve this? I mean.. been able to scan with the printer conected to de usb hub and not directly to de main USB? 
BTW, i get the I/O error when pluged to the usb hub.

(didn't tested scanning from the button yet, will update this)


Thnks in advance guys

---

### Post by carpetmanleo on 2011-01-06
I am new to ubuntu, I have my printer working but I can not get my scanner working. I have the MFC-240c,Have followed every step in this thread and others and get nothing. worked the other day when i was running XP. Any help will be appreciated.:confused:

---

### Post by syntaxerrorsix on 2011-01-07
> **carpetmanleo said:**
> I am new to ubuntu, I have my printer working but I can not get my scanner working. I have the MFC-240c,Have followed every step in this thread and others and get nothing. worked the other day when i was running XP. Any help will be appreciated.:confused:

Best of luck.  It worked fine when I started using Ubuntu Intrepid however after upgrading I lost the option to scan from the keys and Xsane gives me a Failed to Open Device I/O failure message.  I've reinstalled packages and searched for news but I've pretty much given up. Nothing I've attempted will allow me to scan anymore with the device other than windows.

---

### Post by carpetmanleo on 2011-01-07
Excellent I just found this in another thread. find where your scanner is by using lsusb, then ;
user@somelinuxbox:~$ lsusb
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


as you can see the scanner resides on Bus 002 as the second (002) device  in my case. The syntax for changing permissions of the scanner device  is


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/$BUS/$DEVICE


remember to change the $BUS and $DEVICE variables according to the lsusb  output as described above. to change permissions to my scanner device i  would enter:


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002
 Worked for me thanks Aouie):P

---

### Post by syntaxerrorsix on 2011-01-07
> **carpetmanleo said:**
> Excellent I just found this in another thread. find where your scanner is by using lsusb, then ;
user@somelinuxbox:~$ lsusb
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


as you can see the scanner resides on Bus 002 as the second (002) device  in my case. The syntax for changing permissions of the scanner device  is


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/$BUS/$DEVICE


remember to change the $BUS and $DEVICE variables according to the lsusb  output as described above. to change permissions to my scanner device i  would enter:


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002
 Worked for me thanks Aouie):P



Good search!  Worked here as well.  I still wish I understood why it quit working after the update but I'll settle for it working again.

---

### Post by arjay1 on 2011-03-29
Thanks for the guide - really easier than fiddling about on the Brother site.  However I still have a printing problem.

I have an MFC240C.  It prints fine except that it misses out the top 2-3 lines on each page.  That is, it is printing too high up on the page.  I have done the usual things like setting the page as A4 and the margins as sensible figures.  But I still have to then allow 4-5 empty lines at the top of a document to get the first line to print.  I am using OpenOffice 3.3

Can anyone help?

Cheers.

RJ

EDIT:  BTW, the Page Preview looks fine but the printed page is not the same as the preview

---

### Post by kiplantt on 2011-08-24
> **arjay1 said:**
> I have an MFC240C.  It prints fine except that it misses out the top 2-3 lines on each page.  That is, it is printing too high up on the page.  I have done the usual things like setting the page as A4 and the margins as sensible figures.  But I still have to then allow 4-5 empty lines at the top of a document to get the first line to print.

After installing the packages *brother-cups-wrapper-bh7* and *brother-lpr-drivers-bh7*, I had the same problem.

To correct the vertical shift of the page, you have to edit ```
/usr/Brother/Printer/mfc240c/inf/brmfc240crc
``` and change the line:
```
PaperType=Letter
```
to:
```
PaperType=A4
```

---

### Post by arjay1 on 2011-08-24
> **kiplantt said:**
> After installing the packages *brother-cups-wrapper-bh7* and *brother-lpr-drivers-bh7*, I had the same problem.

To correct the vertical shift of the page, you have to edit ```
/usr/Brother/Printer/mfc240c/inf/brmfc240crc
``` and change the line:
```
PaperType=Letter
```
to:
```
PaperType=A4
```

Wow - fancy getting a reply after 6 months or so.  Magic - your solution works just fine. Pretty pathetic is it not that if you set up the page in any word processing program to be A4 it still reads in this file as Letter?

Anyway - just in case someone else is looking for the same file, its location could be different.  For example, mine is in **/usr/local/Brother/Printer/mfc240c/inf/brmfc240crc** (Mepis).

I suggest you search in a terminal as root for the file.  For example **find / -name brmfc240crc.**

Anyway many thanks kiplannt.  I have been switching to Windows XP (yuch) in a virtual machine just to be able to print critical documents.  You save me many hours!!

Regards

Richard

---

