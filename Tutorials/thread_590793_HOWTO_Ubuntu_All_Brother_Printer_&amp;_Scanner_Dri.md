---
title: "HOWTO: Ubuntu All Brother Printer &amp; Scanner Driver Installation for Newbies!"
date: 2007-10-25
forum: Tutorials
---

### Post by BoardDWorld on 2007-10-25
Please note this is my first How-To, if there is an error please let me know. I have comprised this simply from how I went about doing it which worked perfectly. Printing tested in Firefox, Gimp & OpenOffice. Scanning tested in Xsane.

[COLOR="Red"]FIRST MAKE SURE YOUR SYSTEM HAS ALL UPDATES INSTALLED IF YOU HAVE A FRESH INSTALLATION OF UBUNTU.[/COLOR]

[COLOR="Red"]64bit printing:[/COLOR]
Works fine but with a little more fine tuning. HERE'S REFERENCE TO ALL PRINTERS INSTALLED SUCCESSFULLY ON UBUNTU 64BIT IN THIS THREAD: [[COLOR="Blue"]HERE[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4014274&postcount=98"), [[COLOR="Blue"]HERE[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3748048&postcount=40") and [[COLOR="Blue"]HERE[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3835451&postcount=61") 

**_Printer:_**

I'm quite a newbie to Linux and I found it really easy to install my Printer with the help of the official Brother Linux Driver [[COLOR="Blue"]WEBSITE[/COLOR]]("http://solutions.brother.com/linux/en_us/index.html"). The site is a little outdated but the installation still remains simple thanks to Ubuntu & not to forget [[COLOR="Blue"]Debian[/COLOR]]("http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png").

[COLOR="Red"]Step 1:[/COLOR]
Open Terminal by selecting **Applications** ---- **Terminal** from the task bar. 

[COLOR="Red"]Step 2:[/COLOR]
Type or Copy & Paste the following into Terminal and press enter: 
```
sudo apt-get install tcsh
```

[COLOR="Red"]Step 3:[/COLOR] (don't know if it matters but I did it anyway)
From the task bar go to: **System** ---- **Administration** ---- **Printing**, select your printer that's not working then select edit and click delete.

[COLOR="Red"]Step 4:[/COLOR]
Download the LPR Driver and CUPS Wrapper. Locate your model & download your "**Debian**" LPR printer driver from [[COLOR="Blue"]HERE[/COLOR]]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html").
Locate your model & download your "**Debian**" CUPS wrapper from [[COLOR="Blue"]HERE[/COLOR]]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html").

[COLOR="Red"]Step 5:[/COLOR]
Now change to the directory where the drivers are. Presuming you downloaded the driver to your desktop Type or Copy & Paste the following into Terminal:
```
cd Desktop
```

[COLOR="Red"]Step 6:[/COLOR]
Create the lpd directory. This is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 7 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

```
sudo mkdir /var/spool/lpd
```

[COLOR="Red"]Step 7:[/COLOR]
Install the LPR Driver. In terminal Type or Copy & Paste the following command changing **mfc210clpr-1.0.2-1.i386.deb** to match the driver you've downloaded. The following line is for the MFC-210C which is also used for the following printers:
DCP-115C, DCP-117C, DCP-120C, DCP-315CN, DCP-340CW,MFC-215C, MFC-425CN, MFC-640CW, MFC-820CW

```
sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb
```

[COLOR="Red"]Step 8:[/COLOR]
Create the model directory. As with the lpd directory this is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 9 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

```
sudo mkdir /usr/share/cups/model
```


[COLOR="Red"]Step 9:[/COLOR]
Now to install the CUPS wrapper driver. In terminal Type or Copy & Paste the following command changing **cupswrapperMFC210C-1.0.2-3.i386.deb** to match the driver you've downloaded.The following line is for the MFC-210C which is also used for the following printers:
DCP-115C, DCP-117C, DCP-120C, DCP-315CN, DCP-340CW,MFC-215C, MFC-425CN, MFC-640CW, MFC-820CW
```
sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb

```

After the installation observe that there are no errors. Here are 2 examples of a successful and unsuccessful installation:

[COLOR="Red"]Successful:[/COLOR]
```
matthew@matthew-laptop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
[sudo] password for matthew:
(Reading database ... 119742 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.2-3 (using cupswrapperMFC210C-1.0.2-3.i386.deb) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.2-3) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

matthew@matthew-laptop:~/Desktop$
```

[COLOR="Red"]Unsuccessful:[/COLOR]
```
turner@turner-desktop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
[sudo] password for turner:
Selecting previously deselected package cupswrappermfc210c.
(Reading database ... 91832 files and directories currently installed.)
Unpacking cupswrappermfc210c (from cupswrapperMFC210C-1.0.2-3.i386.deb) ...
Setting up cupswrappermfc210c (1.0.2-3) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
chmod: cannot access `/usr/local/Brother/inf/brMFC210Crc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ]
```

If your installation was successful please continue at Step 10. If it was unsuccessful please repeat the installation at the LPR Driver installation at Step 7. Copy the output(text from the install commands in the terminal) of both the LPR and CUPS driver installations and save them to a text document for future reference. As there have been reports of errors but the the printer still worked perfectly you may have no problem. Continue on with Step 10.

[COLOR="Red"]Step 10:[/COLOR] (This is for Gutsy 64bit users only, 32bit users continue onto Step 11 )
If you're using the MFC-210C driver Type or Copy & Paste the following command in Terminal:
```
sudo cp /usr/lib/cups/filter/brlpdwrapperMFC210C /usr/lib64/cups/filter
```
If you're using another driver please adjust MFC210C to suit your model. Example for the MFC-3820CN driver:
```
sudo cp /usr/lib/cups/filter/brlpdwrapperMFC3820CN /usr/lib64/cups/filter
```

If you're not sure you can check by typing the following in Terminal:
```
cd /usr/lib/cups/filter
dir
```
 
[COLOR="Red"]Step 11:[/COLOR]
From the task bar go to: **System** ---- **Administration** ---- **Printing**, select your printer and click Print Test Page. That's It!
[I][COLOR="Red"]
Please note that adjusting printer settings for all applications takes place in this Printing Configuration menu by selecting your printer then selecting the tab **Printer Options**.[/COLOR][/I]

**[COLOR="Red"]Not working?[/COLOR]**
Some printers might not configure themselves without a few more adjustments as follows:

After completing the driver installation open Firefox and enter the following into the address bar:
```
http://localhost:631
```

Click on &#8220;Manage Printers&#8221; and confirm that the driver name is listed there.

If the driver name is NOT listed there, click on "Add Printer" and install the driver following the on-screen instructions.

The default port is USB. If you want to use a different port, click on &#8220;Modify Printer&#8221; and select the required printer port.


[B][U]
Scanner:[/U][/B]

Unfortunately the Sane Scanner Driver wasn't quite as straight forward to setup, however it will be a lot easier with these steps:

[COLOR="Red"]FIRST MAKE SURE YOUR SYSTEM HAS ALL UPDATES INSTALLED IF YOU HAVE A FRESH INSTALLATION OF UBUNTU.[/COLOR]

[COLOR="Red"]Step 1:[/COLOR]
Locate your model & download the appropriate "**Debian**" **brscan** or **brscan2** driver from [[COLOR="Blue"]HERE[/COLOR]]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html#model"). Please take note that there is a separate driver depending on whether you have a 32bit or 64bit Gutsy installed. Typically it will be 32bit.

[COLOR="Red"]Step 2:[/COLOR]
Now change to the directory where the **brscan** or **brscan2** driver has downloaded to. Presuming you downloaded the driver to your desktop Type or Copy & Paste the following into Terminal:
```
cd Desktop
```
[COLOR="Red"]
Step 3:[/COLOR]
For the brscan2 32bit driver which most will be using Install with the following command in Terminal:
```
sudo dpkg -i brscan2-0.2.4-0.i386.deb
```
Please note that if you don't use the 32bit brscan2 driver change the **brscan2-0.2.4-0.i386.deb** in the terminal command above according to your sane driver you've downloaded. Example: brscan2-0.2.4-0.amd64.deb

[COLOR="Red"]Step 4:[/COLOR]
Confirm you need to continue on with the following steps, I believe it is only Gutsy that has problems. Simply open Xsane, choose you scanner and click OK. If you get an I/O-Error you will need to continue onto Step 5, if it's all working you're done!

[COLOR="Red"]Step 5:[/COLOR]
Give yourself permission to use it! At time of release it's a Gutsy Quirk/Bug... First we need to find out the **Vendor ID** & **Product ID** for our scanner or printer/scanner combo. For anyone using the DCP-115C printer/scanner ignore this step as your ID's are the same as mine; Vendor ID: **04f9** Product ID: **018c**.

Any other model type the following in Terminal:
```
lsusb
```

Your output will be something like this:
```
matthew@matthew-laptop:~/Desktop$ lsusb
Bus 005 Device 004: ID 05ca:1810 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID **04f9:018c** Brother Industries, Ltd 
Bus 001 Device 001: ID 0000:0000  
matthew@matthew-laptop:~/Desktop$ 

```

Locate **Brother Industries, Ltd** and take note of your **Vendor ID:Product ID** as shown in bold in the above output and adjust Step 6 to match.

[COLOR="Red"]Step 6:[/COLOR]
In Terminal type the following:

Ubuntu:
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
Kubuntu:
```
sudo kate /etc/udev/rules.d/45-libsane.rules
```
At the bottom of the page but before LABEL="libsane_rules_end" add the following changing YOUR-VENOR-ID & YOUR- PRODUCT-ID to yours, both are 4 characters long:
```
# Brother DCP-115C
SYSFS{idVendor}=="**YOUR-VENOR-ID**", SYSFS{idProduct}=="**YOUR-PRODUCT-ID**", MODE="664", GROUP="scanner"

```

The last section of 45-libsane.rules should look like this after adding your scanner/printer to the last line:
```
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5105", MODE="664", GROUP="scanner"
# Dell A960
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5107", MODE="664", GROUP="scanner"
# Dell 922
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5109", MODE="664", GROUP="scanner"
# Dell 1600n
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5250", MODE="664", GROUP="scanner"
# Brother DCP-115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"
```

[COLOR="Red"]Step 7:[/COLOR]
Save your changes and restart your PC. All going well it will be working!

[SIZE="1"]Search Aid:
DCP-7010, DCP-7020, DCP-7025, DCP-8060, DCP-8065DN, FAX-2820, FAX-2920, HL-2030, HL-2040, HL-2070N, HL-5240, HL-5250DN, HL-5270DN, HL-5280DW, MFC-7220, MFC-7225N, MFC-7420, MFC-7820N, MFC-8460N, MFC-8660DN, MFC-8860DN, MFC-8870DW, MFC-9420CN, HL-4040CN, HL-4050CDN, HL-4070CDW, MFC-9440CN, MFC-9840CDW, DCP-9040CN, DCP-9045CDN, DCP-130C, DCP-135C, DCP-150C, DCP-153C, DCP-330C, DCP-350C, DCP-353C, DCP-540CN, DCP-560CN, DCP-750CW, DCP-770CW, FAX-1860C, FAX-1960C, FAX-2480C, FAX-2580C, MFC-230C, MFC-235C, MFC-240C, MFC-260C, MFC-3360C, MFC-440CN, MFC-465CN, MFC-5460CN, MFC-5860CN, MFC-660CN, MFC-665CW, MFC-680CN, MFC-685CW, MFC-845CW, MFC-885CW, FAX1835C, FAX1840C, FAX1940CN, FAX2440C, MFC3240C, MFC3340CN, MFC5440CN, MFC5840CN, MFC210C, MFC410CN, MFC420CN,MFC620CN,DCP110C, DCP310CN, FAX1815C, FAX1820C, FAX1920CN, MFC3220C, MFC3320CN, MFC3420C, MFC3820CN[/SIZE]

---

### Post by PriceChild on 2007-10-25
poke

---

### Post by drejom on 2007-10-28
thanks for ya post - got the scanner working no probs, but on amd64 gutsy, my cups error log is full of:

```
E [28/Oct/2007:23:48:11 +1100] CUPS-Add-Modify-Printer: Unauthorized
E [28/Oct/2007:23:48:52 +1100] cupsdAuthorize: Local authentication certificate not found!
E [28/Oct/2007:23:48:52 +1100] cupsdAuthorize: Local authentication certificate not found!
E [28/Oct/2007:23:48:52 +1100] cupsdAuthorize: Local authentication certificate not found!
E [28/Oct/2007:23:48:57 +1100] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [28/Oct/2007:23:49:05 +1100] cupsdAuthorize: Local authentication certificate not found!
E [28/Oct/2007:23:49:07 +1100] cupsdAuthorize: Local authentication certificate not found!
E [28/Oct/2007:23:49:07 +1100] CUPS-Add-Modify-Printer: Unauthorized
E [28/Oct/2007:23:49:07 +1100] Filter "brlpdwrapperMFC210C" for printer "MFC-210C" not available: No such file or directory
E [28/Oct/2007:23:49:07 +1100] Filter "brlpdwrapperMFC210C" for printer "MFC-210C" not available: No such file or directory
E [28/Oct/2007:23:49:07 +1100] Filter "brlpdwrapperMFC210C" for printer "MFC-210C" not available: No such file or directory
E [28/Oct/2007:23:49:40 +1100] Filter "brlpdwrapperMFC210C" for printer "MFC-210C" not available: No such file or directory
E [28/Oct/2007:23:52:40 +1100] CUPS-Add-Modify-Printer: Unauthorized
E [28/Oct/2007:23:53:28 +1100] cupsdAuthorize: Local authentication certificate not found!
E [28/Oct/2007:23:53:32 +1100] cupsdAuthorize: Local authentication certificate not found!

```

I've tried copying the brlpdwrapper to /usr/lib64(etc), reinstalling cups, reinstalling the cupswrapper.deb all to no avail!
any help appreciated!

---

### Post by BoardDWorld on 2007-10-28
Hello drejom,

Did you use "--force-all" when installing the driver?

---

### Post by drejom on 2007-10-28
yup!

---

### Post by BoardDWorld on 2007-10-28
Just been having a read, apparently there's no "official" support for AMD64 but try this:

```
sudo cp /usr/lib/cups/filter/brlpdwrapperMFC210C /usr/lib64/cups/filter
```

Please let me know if this works as I will update my guide.

---

### Post by drejom on 2007-10-29
yup tried that too - but no joy. 
in the meantime, i've totally screwed my system by tinkering about with other things. I'm going to do  a fresh install tonight - i'll try your howto again first thing, and see how it goes.
thanks again...

---

### Post by BoardDWorld on 2007-10-29
Haha, I haven't managed to do that with Ubuntu yet, but I have done that twice with SUSE 10. (my first Linux experience)

I have added the 64bit how-to into the installation steps at Step 7. This being said I'm not able to personally test it as I'm running on 32bit.

---

### Post by drejom on 2007-10-30
thanks to you both - but still no luck... i'll check the FAQ later (mine's a particularly problematic amd64)

---

### Post by TURNER on 2007-10-30
Worked a treat for my Brother DCP 115, many thanks for taking the time to write a great how to!

---

### Post by BoardDWorld on 2007-10-31
> **mp035 said:**
> Hi BoardWorld,

Great How-To! It will help many users pick up Ubuntu. 

I have a couple of steps that are required for most brother printers, that are not in your how-to,

[COLOR="Red"]Step 3A[/COLOR] (these steps need to happen before installing the cupswrapper driver)
go to [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html") and get the brother lpr driver for Debian.  The lpr driver proivides the actual printer functionality, the cupswrapper then provides the "glue" to make it work with CUPS. 

[COLOR="Red"]Step 3B[/COLOR] Install the lpr driver BEFORE the cupswrapper driver.
```
 sudo dpkg -i --force-architecture mfc210clpr-1.0.2-1.i386.deb 
```
the force-architecture switch is used to force the 64 bit systems to accept the driver.

Any problems, visit the FAQ at [http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html")

I hope this helps someone.  

Again BoardWorld, top job in puting together this how-to!! :)



Yes the LPR is required for older versions of Ubuntu. This guide is for Gutsy 7.10 and above that do not require the LPR, this being the reason why is not included. Did you not follow my HowTo?

If you also noticed I said the brother site was a little out of date, not needing the LPR is what I was referring to mostly. Please remove your post.

---

### Post by TURNER on 2007-10-31
Iam using a (fresh) install of Gutsy and following your "how to" without the LPR didnt work for me, upon rolling back and trying again WITH the LPR I got the printer working....I think it might be worth leaving the part ref the LPR..

---

### Post by BoardDWorld on 2007-10-31
Are you sure? As you can see from my guide I too am using the DCP-115C WITHOUT the LPR. This is actually working better than Feisty that needs the LPR as page positioning was out of alignment. Also print initiating is far quicker than I have ever had it before on any OS. Are you using Gutsy or an earlier OS? as my guide is focussed at Gutsy.

---

### Post by dukbilt on 2007-11-01
Hi,

thanks for the guide. Unfortunately, it didn't help me. I have an MFC-425CN connected as a networked printer, and after following your guide the printer doesn't print. I don't get any error messages whatsoever.

I have another installation of Ubuntu (7.04) and the printer works properly - I have to re-boot to this installation to print documents, and it's frustrating having to do this!

I originally installed the printer WITH the LPR driver, following the same routine I had used under earlier Ubuntu installations. However, when printing, the top of the page was missing (about an inch or so). When I discovered your How-To, I uninstalled the Brother LPR and CUPSWrapper drivers, then re-installed CUPSWrapper (without the LPR driver). Unfortunately, the printer doesn't work at all. It is detected, and I can change settings, but it just doesn't print.

Here's a printout from "printingbuginfo" which I have included in case there's anything of use.

Thanks,

Ewan

ProblemType: printingbuginfo v2.0: printingbug ([https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript))
CupsConfiguredDevices:
 device for MFC210C: socket://192.168.0.2:9100
 device for PDF: cups-pdf:/
CupsConfiguredPPDs:
 MFC-425CNold: Brother MFC-210C CUPS v1.1
 MFC210C: Brother MFC-210C CUPS v1.1
 PDF: Generic PDF file generator
Date: Fri Nov  2 13:33:40 2007
DesktopEnvironment: GNOME
DistroRelease: Ubuntu 7.10
EtcPapersize: A4
InstalledPrintingPackages:
 ii  cupsys                   1.3.2-1ubuntu7           Common UNIX Printing System(tm) - server
 ii  cupsys-driver-gutenprint 5.0.1-0ubuntu8           printer drivers for CUPS
 ii  foo2zjs                  20070625-0ubuntu1        Support for printing to ZjStream-based printers
 ii  foomatic-db              20070919-0ubuntu3        OpenPrinting printer support - database
 ii  foomatic-db-engine       3.0.2-20070719-0ubuntu4  OpenPrinting printer support - programs
 ii  foomatic-db-hpijs        20070813-0ubuntu1        OpenPrinting printer support - database for HPIJS driver
 ii  foomatic-filters         3.0.2-20070719-0ubuntu1  OpenPrinting printer support - filters
 ii  ghostscript              8.61.dfsg.1~svn8187-0ubu The GPL Ghostscript PostScript/PDF interpreter
 ii  hpijs                    2.7.7+2.7.7.dfsg.1-0ubun HP Linux Printing and Imaging - gs IJS driver (hpijs)
 ii  hplip                    2.7.7.dfsg.1-0ubuntu5.1  HP Linux Printing and Imaging System (HPLIP)
 ii  libgnomeprint2.2-0       2.18.2-0ubuntu1          The GNOME 2.2 print architecture - runtime files
 ii  min12xxw                 0.0.9-1build1            Printer driver for KonicaMinolta PagePro 1[234]xxW
 ii  openprinting-ppds        20070919-0ubuntu3        OpenPrinting printer support - PostScript PPD files
 ii  pnm2ppa                  1.12-16                  PPM to PPA converter
 ii  pxljr                    1.1-0ubuntu1             Driver for HP's Color LaserJet 35xx/36xx color laser printers
 ii  splix                    1.0.1.1-0ubuntu2         Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
 ii  system-config-printer    0.7.75+svn1653-0ubuntu2  Printer configuration GUI
Locale: LANG=en_AU.UTF-8, LC_CTYPE=en_AU.UTF-8, LC_PAPER=en_AU.UTF-8
Uname: Linux latitude 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by camiguin on 2007-11-02
Thanks for the detailed Howto. I followed it carefully and didn't resolve the problem (not printing on Brother DCP-115C after Gutsy upgrade, although it does scan). However, the symptoms have changed: before, the print job disappeared from the screen after a while, now it stays forever, in both cases nothing coming out of the printer; also, now the URI in Printers - Interface is wrong, and I cannot modify it, since the option "local printer" is greyed out. What can I do? Many thanks

---

### Post by phobos512 on 2007-11-02
Thanks for the how-to!  I am now able to print to our networked MFC-640CW.

The scanner function still eludes me however.  I followed the how-to and when I start XSane it tells me there are no scanners.  Would the problem be that it is networked rather than directly attached?  I have a feeling it is...

---

### Post by Mr.Mechano on 2007-11-03
> **dukbilt said:**
> Hi,

thanks for the guide. Unfortunately, it didn't help me. I have an MFC-425CN connected as a networked printer, and after following your guide the printer doesn't print. I don't get any error messages whatsoever.



Hi there!

I've been able to setup the same printer on Gutsy.

If networked you have to go into cups web interface [http://localhost:631](http://localhost:631) and modify printer port.
It's not an IPP o TCP network queue.

IT'S AN LPD/LPRNG NETWORK QUEUE. 

After selecting LPD queue set the address on socket://IPADDRESS:9100
(change IPADDRESS with the hostname or ip address of your printer).

It will work also without installing the LPD brother driver...

Don't forget to setup paper and margins, and the True2life color enancement for better color printing.

---

### Post by dukbilt on 2007-11-03
Still no joy - when I attempt to print, I receive an error - "/usr/lib/cups/filter/brlpdwrapperMFC210C failed". Why is it attempting to use the brlpdwrapper driver if it doesn't need it???

So I removed the brlpdwrapper file - now I get:

  Unable to start filter "brlpdwrapperMFC210C" - No such file or directory.

Any suggestions?

Ewan

EDIT - I have looked through the script file for "cupswrapperMFC210C-1.0.2" and it creates the "brlpdwrapperMFC210C" automatically... So the problem is either in one of those two files, I think.

Ewan

EDIT - I have discovered that the brprintconfij2 file did not exist in the /usr/bin directory. I copied the file from my Ubuntu 7.04 installation into the /usr/bin (7.10) and now there are no CUPS errors! However - it still won't print! AAARRRGGGGHHHHHH!!!! I have tried re-starting CUPS, but to no avail... Any suggestions now?

---

### Post by nathandetroit on 2007-11-04
My Brother MFC-420CN stopped printing after I upgraded to Ubuntu 7.10. I tried various things as outlined in the this discussion. Here is what finally worked for me:

Uninstalled all "mfc" related packages (ran System -> Administration -> Synaptic Package Manager; searched for "mfc" and removed all matching PRINTER RELATED packages).

Downloaded and installed latest packages from the Brother site INCLUDING the lpr package. Installed the lpr package first, then the cupswrapper as follows:

      sudo dpkg -i --force-all mfc420cnlpr-1.0.2-1.i386.deb

      sudo dpkg -i --force-all cupswrapperMFC420CN-1.0.2-3.i386.deb

Now, I understand that Ubuntu 7.10 does not require the lpr package anymore, but I think the Brother scripts expect it, because when I do NOT install the lpr package first I get this (note the error) when I install the cupswrapper::

Selecting previously deselected package cupswrappermfc420cn.
(Reading database ... 142310 files and directories currently installed.)
Unpacking cupswrappermfc420cn (from cupswrapperMFC420CN-1.0.2-3.i386.deb) ...
Setting up cupswrappermfc420cn (1.0.2-3) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperMFC420CN
chmod: cannot access `/usr/local/Brother/inf/brMFC420CNrc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd

As a final note, it does not appear to me that Ubuntu is acutally *using* the lpr package, but it does seem to make the cupswrapper installation work.

In any case, my printer is now working fully (I also did the scanner update as noted earlier in this discussion), and I am once again a happy Ubuntu user.

---

### Post by Jose Catre-Vandis on 2007-11-04
Shame you missed the long running howto and various links for setting up Brother printers on the forum already:

[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

[http://ubuntuforums.org/showthread.php?t=302960](http://ubuntuforums.org/showthread.php?t=302960)

[http://ubuntuforums.org/showthread.php?t=123539](http://ubuntuforums.org/showthread.php?t=123539)

Anyhow, these threads might help those who get stuck. Also interested to see that you didn't have to switch off the printer/MFC at any point. This was a big stumbling point with Edgy/Feisty for many users.

---

### Post by djin44 on 2007-11-04
> **nathandetroit said:**
> My Brother MFC-420CN stopped printing after I upgraded to Ubuntu 7.10. I tried various things as outlined in the this discussion. Here is what finally worked for me:

Uninstalled all "mfc" related packages (ran System -> Administration -> Synaptic Package Manager; searched for "mfc" and removed all matching PRINTER RELATED packages).

Downloaded and installed latest packages from the Brother site INCLUDING the lpr package. Installed the lpr package first, then the cupswrapper as follows:

      sudo dpkg -i --force-all mfc420cnlpr-1.0.2-1.i386.deb

      sudo dpkg -i --force-all cupswrapperMFC420CN-1.0.2-3.i386.deb

Now, I understand that Ubuntu 7.10 does not require the lpr package anymore, but I think the Brother scripts expect it, because when I do NOT install the lpr package first I get this (note the error) when I install the cupswrapper::

Selecting previously deselected package cupswrappermfc420cn.
(Reading database ... 142310 files and directories currently installed.)
Unpacking cupswrappermfc420cn (from cupswrapperMFC420CN-1.0.2-3.i386.deb) ...
Setting up cupswrappermfc420cn (1.0.2-3) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperMFC420CN
chmod: cannot access `/usr/local/Brother/inf/brMFC420CNrc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd

As a final note, it does not appear to me that Ubuntu is acutally *using* the lpr package, but it does seem to make the cupswrapper installation work.

In any case, my printer is now working fully (I also did the scanner update as noted earlier in this discussion), and I am once again a happy Ubuntu user.

I had problems with the MFC-210C not working when I only installed the CUPS, but when I followed these steps and included the LPR, it worked perfectly, thanks nathan.

---

### Post by mp035 on 2007-11-04
--deleted--

---

### Post by BoardDWorld on 2007-11-04
As you can see there are already people that have said here that they are not using the LPR. And general rule of thumb it will be mostly people with problems that are going to add remarks to this thread.

That's great to anyone of you who have managed to get it running with the LPR. Though this is strange as it isn't suppose to be required and is in fact performing better without it on my system.

I can only gather that as future (less buggy) releases of Ubuntu become available not using the LPR will be more applicable to my HowTo.

Jose Catre-Vandis:

The threads you provided while they are still currently valid are all for anything prior to Gutsy's new printing system, this most likely being the reason why my HowTo was approved. Also the new printing system has resolved a couple of major head aches I had in Feisty that uses the LPR.

Via Gutsy's new printing system without the LPR I am having a very pleasant printing experience.

---

### Post by dukbilt on 2007-11-05
For those that do have printing with the MFC-210C working, do you mind posting the following files:

[INDENT]/usr/lib/cups/filter/brlpdwrapperMFC210C

/usr/share/cups/model/brmfc210c_cups.ppd

/usr/local/Brother/lpd/filterMFC210C

/usr/bin/brprintconfij2[/INDENT]

In the reply, please let us know if any of the files are in different locations to what I have listed as the directory location, and also if you installed the LPR driver or not.

Also, a screen print of all the "mfc" programs listed under synaptic or similar would be helpful.

Finally, please add in any files (with their locations) that you think will help.

TIA,

Ewan

---

### Post by jfank on 2007-11-06
Ok I'm extremely new to linux myself, and I can't get the printer to install.  I have the Brother MFC420CN, and I am using the newest version of Kubuntu.  I did everything that was described in the original post on this topic, and it will tell me that there is the printer, but it just won't print.  Now with Kubuntu when you go to system, there is no admin, printer.  the only thing I get there is for HP printers.  I'm just confused on what to do, because nothing is working for me.  If I didn't describe this well enough please let me know, and I will try to explaine it better.  Thank you for the help.

---

### Post by TURNER on 2007-11-06
I am currently reinstalling my printer in an effort to have it printing correctly, at the moment all of my prints are blurred and the quality shocking....as I am currently re installing using your how to I'd like to highlight the following:

OS: Ubuntu 7.10 gutsy.

upon installing the relevant cups (MFC 210 in this case) I receive the following error:
```

turner@turner-desktop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
[sudo] password for turner:
Selecting previously deselected package cupswrappermfc210c.
(Reading database ... 91832 files and directories currently installed.)
Unpacking cupswrappermfc210c (from cupswrapperMFC210C-1.0.2-3.i386.deb) ...
Setting up cupswrappermfc210c (1.0.2-3) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
chmod: cannot access `/usr/local/Brother/inf/brMFC210Crc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
```

seems in my case the LPR is required....unsure why.

---

### Post by dukbilt on 2007-11-06
I had this issue - it's a result of the installation software attempting to delete files or folders which do not exist. In your case, /usr/local/Brother/inf/brMFC210Crc and /usr/local/Brother/inf.  I don't know if it actually stops the installation or not, but to eliminate the error:

Open a terminal window, then type "sudo nautilus" and then enter your password (this starts nautilus as administrator, to allow you to create folders in the / partition).

Use the new nautilus program which appeared to go to the "/usr/Brother" directory.

Create a folder called "inf" in the "/usr/Brother" directory.

Open the "/usr/Brother/inf" directory.

Create a folder titled ""brMFC210Crc" in /usr/local/Brother/inf directory.

Exit out of nautilus.

In the terminal window, type "sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb" and it should work.

NOTE:  It think it WILL come up with "ERROR : Brother LPD filter is not installed" but I think the other errors should not occur.

Good luck!

Ewan

---

### Post by jfank on 2007-11-06
Okay, nevermind that last reply I put in here about it not installing.  I found out what the problem was.  I was making a error when I typed in the command for the driver file.  I kept putting in the wrong letter, and it wouldn't work for me.  I have it installed now, and the printer, and the scanner are working perfectly.  That was excellent steps that you gave us to follow.

---

### Post by ilkkak on 2007-11-06
Brother DCP-330C installation didn't work

I repeated steps 1 - 5

```

i@ijar:~$ sudo dpkg -i --force-all cp330ccupswrapper-1.0.0-10.i386.deb
Valitsen aikaisemmin valitsemattoman paketin dcp330ccupswrapper.
(Luetaan tietokantaa... 135049 tiedostoa ja hakemistoa tällä hetkellä asennettuna.)
Puretaan pakettia dcp330ccupswrapper (.../dcp330ccupswrapper-1.0.0-10.i386.deb)...
dpkg: dcp330ccupswrapper: riippuvuusongelmia, mutta konfiguroin kuitenkin kuten pyysit:
 dcp330ccupswrapper depends on dcp330clpr; however:
  Package dcp330clpr is not installed.
Säädän asetukset: dcp330ccupswrapper (1.0.0-10) ...
ERROR : Brother LPD filter is not installed.
chmod: tiedostoa "/usr/local/Brother/Printer/dcp330c/inf/brdcp330crc" ei voi käsitellä: No such file or directory
chmod: tiedostoa "/usr/local/Brother/Printer/dcp330c/inf" ei voi käsitellä: No such file or directory
 * Restarting Common Unix Printing System: cupsd    
```

Printer exists in system and 

i@ijar:~$ lsusb  | grep Brother
Bus 003 Device 003: ID 04f9:01a9 Brother Industries, Ltd
i@ijar:~$     

Test print doesn't function. Syslog event is 

```

Nov  6 18:43:29 localhost NetworkManager: <debug> [1194367409.737557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4f9_1a9_BROH6F567037_if2_scsi_host').
Nov  6 18:43:29 localhost NetworkManager: <debug> [1194367409.744200] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4f9_1a9_BROH6F567037_if2_scsi_host_scsi_device_lun0').
Nov  6 18:43:29 localhost NetworkManager: <debug> [1194367409.765023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4f9_1a9_BROH6F567037_if2_scsi_host_scsi_device_lun0_scsi_generic').
Nov  6 18:43:29 localhost NetworkManager: <debug> [1194367409.988265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Brother_DCP_330C_BROH6F567037_0_0').
Nov  6 18:43:38 localhost kernel: [ 2118.034031] ppdev0: registered pardevice
Nov  6 18:43:38 localhost kernel: [ 2118.081384] ppdev0: unregistered pardevice
Nov  6 18:43:38 localhost kernel: [ 2118.133509] audit(1194367418.471:5):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=7727 profile="/usr/sbin/cupsd"
Nov  6 18:43:40 localhost python: [7733]: warning: Unable to set locale.

```

and in print-report there is the message "Printer not connected - retry in 30 seconds"

I also changed apparmor mode as

 sudo aa-complain cupsd


Please - any succestion.

---

### Post by BoardDWorld on 2007-11-06
Anyone receiving these LPR and chmod errors as described in the last few posts should install the LPR. A successful installation without the LPR should look something like this(as if it had the LPR installed):

```
matthew@matthew-laptop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
[sudo] password for matthew:
(Reading database ... 119742 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.2-3 (using cupswrapperMFC210C-1.0.2-3.i386.deb) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.2-3) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

matthew@matthew-laptop:~/Desktop$
```

I will adjust my HowTo to incorporate the LPR if necessary.

I don't know quite why this is working for some but not others, I can only gather it's due to the new printing system in Ubuntu being not quite so complete.

---

### Post by dukbilt on 2007-11-07
ONCE AGAIN: FOR THOSE WHO HAVE THE MFC-210C INSTALLATION WORKING WITHOUT LPR, PLEASE SUBMIT

    /usr/lib/cups/filter/brlpdwrapperMFC210C

    /usr/share/cups/model/brmfc210c_cups.ppd

    /usr/local/Brother/lpd/filterMFC210C

    /usr/bin/brprintconfij2

In the reply, please let us know if any of the files are in different locations to what I have listed as the directory location, and also if you installed the LPR driver or not.

Also, a screen print of all the "mfc" programs listed under synaptic or similar would be helpful.

Finally, please add in any files (with their locations) that you think will help.

TIA,

Ewan

---

### Post by jfank on 2007-11-07
Ok now I need help with the SCANNER DRIVER INSTALL.  When I copy and past   sudo gedit /etc/udev/rules.d/45-libsane.rules   IT tells me the following:  

jfank2006@Justin-laptop:~/Desktop$ sudo gedit /etc/udev/rules.d/45-libsane.rules
sudo: gedit: command not found

I'm now running Kubuntu, and I don't know if I have to type something different in to get that part to work.  Can someone help me out with this so I can get the scanner drivers installed.  Thank you.

---

### Post by BoardDWorld on 2007-11-07
> **dukbilt said:**
> ONCE AGAIN: FOR THOSE WHO HAVE THE MFC-210C INSTALLATION WORKING WITHOUT LPR, PLEASE SUBMIT

    /usr/lib/cups/filter/brlpdwrapperMFC210C

    /usr/share/cups/model/brmfc210c_cups.ppd

    /usr/local/Brother/lpd/filterMFC210C

    /usr/bin/brprintconfij2

In the reply, please let us know if any of the files are in different locations to what I have listed as the directory location, and also if you installed the LPR driver or not.

Also, a screen print of all the "mfc" programs listed under synaptic or similar would be helpful.

Finally, please add in any files (with their locations) that you think will help.

TIA,

Ewan

Here we go, as you know I'm not using, nor ever have used, the LPR Driver. All files were in the locations you have shown. Hope this helps!

---

### Post by BoardDWorld on 2007-11-07
> **jfank said:**
> Ok now I need help with the SCANNER DRIVER INSTALL.  When I copy and past   sudo gedit /etc/udev/rules.d/45-libsane.rules   IT tells me the following:  

jfank2006@Justin-laptop:~/Desktop$ sudo gedit /etc/udev/rules.d/45-libsane.rules
sudo: gedit: command not found

I'm now running Kubuntu, and I don't know if I have to type something different in to get that part to work.  Can someone help me out with this so I can get the scanner drivers installed.  Thank you.

Here's the same answer to the private message you first sent (sorry I didn't see this post):

[I]Yes sorry, my fault. Kubuntu(KDE) uses its own text editors (Kate, Kedit, and Kwrite). Ubuntu(Gnome) uses Gedit etc...

I think kwrite was the most popular when I tried Linux Suse 10. Try anyone of the following commands:

```
sudo kwrite /etc/udev/rules.d/45-libsane.rules
```

```
sudo kedit /etc/udev/rules.d/45-libsane.rules
```

```
sudo kate /etc/udev/rules.d/45-libsane.rules
```

Please let me know how each command works and which editor you preferred. Also I'm interested in knowing what you think of Kubuntu over Ubuntu?

[/I]

Edit:
I've done some research and kate is suppose to be the best...

---

### Post by jfank on 2007-11-07
I got everything to work perfectly with the scanner after you helped me out.  the onyl problem I have is the glass part of the scanner needs some serious cleaning :lolflag:  Anyhow I used the KWRITE and it brought up what I needed to to add the part for the printer in at the bottom of the page.  KATE also works, it just brings up a smaller side screen thing like how Adobe Acrobat Reader has the side deal on the left.  They both work, but I just used the KWRITE since it was the first, and then i tested the other two.  The KEDIT didn't do anything.  But now my scanner is working, and Thank you for helping me with it.  

I had everything working perfectly on Ubuntu, but when I switched to Kubuntu it had a different type of script than what normal Ubuntu has. Everything works perfectly though.  Now only if I can get Halo to work on Linux. lol:lolflag:

---

### Post by whistlerspa on 2007-11-09
Back to the printer issue  - thanks that got my printer going again  - but no joy on the scanner side. 

recorded an IO error every time.

---

### Post by Am3ndment on 2007-11-10
Worked like a charm! Thanks a lot!

---

### Post by cyberia81 on 2007-11-10
Hello! Thanks for the guide. I'm looking forward to using it. However, I have a bit of a problem as referenced in this thread: [http://ubuntuforums.org/showthread.php?t=217952&highlight=hl5140lpr]("http://ubuntuforums.org/showthread.php?t=217952&highlight=hl5140lpr")
I tried installing a laser printer. Something went terribly wrong. I decided to get rid of it and I'm getting this error:

stephanie@boxofmallards:~$ sudo apt-get install tcsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hl5140lpr
The following NEW packages will be installed:
  tcsh
0 upgraded, 1 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 338kB of archives.
After unpacking 709kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe tcsh 6.14.00-7 [338kB]
Fetched 338kB in 6s (52.9kB/s)                                                 
(Reading database ... 132943 files and directories currently installed.)
Removing hl5140lpr ...
/var/lib/dpkg/info/hl5140lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl5140lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl5140lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)


 I now want to install a Brother MFC-465CN all-in-one but I can't get anywhere until I solve this problem. Any ideas would be greatly appreciated!

---

### Post by xaph on 2007-11-10
Not a Linux  wizard  however a friend Richard T  is a "Arch Linux  Wizard"  and assisted  with  the following, hope it may assist others, my  printer now works fine.

Please note this was  for  7.10  distro and  on  AMD 64  CPU.
  

HOW TO INSTALL THE MFC440CN Brother Printer  for Ethernet use.
============================

1. apt-get install alien (to be able to convert rpm to deb
2. used the arch-linux instructions with modifications:
   from this link download the .rpm files below

[http://eithansmith.wordpress.com/2007/10/24/cups-driver-for-brother-mfc440cn/](http://eithansmith.wordpress.com/2007/10/24/cups-driver-for-brother-mfc440cn/)


mfc440cncupswrapper-1.0.0-9.i386.rpm
mfc440cnlpr-1.0.0-9.i386.rpm

3. Run these commands as root (sudo -s and put in your user password):

alien -d mfc440cnlpr-1.0.0-9.i386.rpm 
alien -d  mfc440cncupswrapper-1.0.0-9.i386.rpm 

to generate these files:

mfc440cncupswrapper_1.0.0-10_i386.deb
mfc440cnlpr_1.0.0-10_i386.deb

Install these files by simply clicking on them in a file manager.

4. as root type this in;
root# cd /usr/local/Brother/Printer/mfc440cn/cupswrapper
root#  ./cupswrappermfc440cn 

5. Now go to the browser admin for cups:

[http://localhost:631/](http://localhost:631/) (e.g in firefox).

And make sure the printer has the correct driver and it should work.


Good Luck:grin::grin::grin:

---

### Post by BoardDWorld on 2007-11-11
> **xaph said:**
> Not a Linux  wizard  however a friend Richard T  is a "Arch Linux  Wizard"  and assisted  with  the following, hope it may assist others, my  printer now works fine...

...Good Luck:grin::grin::grin:

Hey That's awesome thanks. I will reference this for now until I work out from the debs what was required to get it running.

---

### Post by BoardDWorld on 2007-11-11
> **cyberia81 said:**
> Hello! Thanks for the guide. I'm looking forward to using it. However, I have a bit of a problem as referenced in this thread: [http://ubuntuforums.org/showthread.php?t=217952&highlight=hl5140lpr]("http://ubuntuforums.org/showthread.php?t=217952&highlight=hl5140lpr")
I tried installing a laser printer. Something went terribly wrong. I decided to get rid of it and I'm getting this error:

stephanie@boxofmallards:~$ sudo apt-get install tcsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hl5140lpr
The following NEW packages will be installed:
  tcsh
0 upgraded, 1 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 338kB of archives.
After unpacking 709kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe tcsh 6.14.00-7 [338kB]
Fetched 338kB in 6s (52.9kB/s)                                                 
(Reading database ... 132943 files and directories currently installed.)
Removing hl5140lpr ...
/var/lib/dpkg/info/hl5140lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl5140lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl5140lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)


 I now want to install a Brother MFC-465CN all-in-one but I can't get anywhere until I solve this problem. Any ideas would be greatly appreciated!

Sorry I'm a little lost with that output. Firstly why is the LPR driver being removed to install tcsh?

---

### Post by nu2lnx on 2007-11-11
In attempt after attempt my Ubuntu experience has been better than my Fedora experience.  I am running Fedora on my desktop and Ubuntu on my laptop.  I have been able to get wireless and mp3 playback operational in half the time it has taken me on my desktop and now, after a week of effort on Fedora, I still cant print.  In my first attempt on Ubuntu I was able to get the spiffy CUPS test page to print.  I am about to attempt the scanner driver install, but my confidence is high that this to will be a straight forward install. 

I am very impressed with everything Ubuntu so far - keep up the outstanding work!

---

### Post by cyberia81 on 2007-11-11
Thank you for the reply. The error I kept getting was a result of a botched install a few weeks ago. It kept preventing me from installing ANYTHING new. I think I fixed my problem. I kept getting this:

stephanie@boxofmallards:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hl5140lpr
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132943 files and directories currently installed.)
Removing hl5140lpr ...
/var/lib/dpkg/info/hl5140lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl5140lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl5140lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
stephanie@boxofmallards:~$

I removed the hl5140lpr.postrm file manually, ran sudo apt-get install -f again and all seems well. Sorry, this is monumental for me as I am just getting the hang of this! I finally solved my own problem... :D

Now I can use your guide to install my new MFC-465CN. Thank you!

---

### Post by nu2lnx on 2007-11-11
Seems I spoke a touch too soon...  After modifying the 45-libsane.rules I rebooted. Everything is going just great, but can't get the scanner to work.  When I run xsane is gives me an error stating:

Failed to open device 'brother2:net1;dev0': Invalid argument

um.. yeah... Help?

---

### Post by cyberia81 on 2007-11-12
Back again...

I finally installed the drivers without a problem. I was able to print a test page once. Somehow I manged to screw something up and now nothing prints. 

This is what I have in CUPS:

Description: MFC440CN
Location: Office
Printer Driver: Brother MFC-440CN CUPS v1.1
Printer State: idle, accepting jobs, published.
Device URI: ipp://192.168.0.3:9100

When I click to print a test page it appears like it is going to work (LCD lights up on the printer) but nothing happens. Cups displays "Connected to 192.168.0.3:9100." 

What am I doing wrong? I have no idea if that URI is correct- I was guessing.

Any help would be greatly appreciated. Thanks!

---

### Post by plunkjunket on 2007-11-12
Thank You,

This is the most complete instructions for Ubuntu printing I have found. I follow you instruction step by step and it work the first time.:)

UBUNTU 7.10
Dell Dimension 8250
Brother HL-2070N

---

### Post by trash on 2007-11-17
grrrrr, I hate printers lol.

can anybody help me out here, I had errors on step 5 or 6 so I had to install lpr but now i am still getting errors...

Preparing to replace mfc240ccupswrapper 1.0.0-10 (using mfc240ccupswrapper-1.0.0-10.i386.deb) ...
/var/lib/dpkg/info/mfc240ccupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: error processing mfc240ccupswrapper-1.0.0-10.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc240ccupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
cp: cannot stat `/usr/share/cups/model/brmfc240c.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc240ccupswrapper-1.0.0-10.i386.deb

---

### Post by trash on 2007-11-17
sudo rm /var/lib/dpkg/info/mfc240ccupswrapper*

seems to have got me past the install error:)

---

### Post by saulysw on 2007-11-17
Thanks! Worked a treat with my MFC-640CW.

One minor comment. In step 7, it did complain that it couldn't create some directories. Doesn't  seem to stop it from working fine though.

---

### Post by BoardDWorld on 2007-11-18
> **trash said:**
> sudo rm /var/lib/dpkg/info/mfc240ccupswrapper*

seems to have got me past the install error:)

Interesting you had to remove the cups seeing the LPR is being forced? I will add it to my How-To if it's mentioned again. Thanks!

---

### Post by trash on 2007-11-18
> **BoardDWorld said:**
> Interesting you had to remove the cups seeing the LPR is being forced? I will add it to my How-To if it's mentioned again. Thanks!

I actually thought it was cause by previous failed attempts installing... still might come in handy for othes though.
Thanks for the howto!

---

### Post by Roger Mudd on 2007-11-18
Great work! I have a DCP-7020 and had been trying to follow the instructions on Brother's web site with little luck. Your well-written HOWTO did the trick and I'm up and running with what appears to be fully functional MFC. One step closer to removing Windows altogether. Thanks again!

---

### Post by ericartman on 2007-11-20
Another one adding my vote for installing lpr first. Then Cupswrapper, worked like a charm, Thank you. Have now used instructions on my MInt 32 bit and all went well. I know its ubuntu based but just fyi
.

Cart

---

### Post by ikester8 on 2007-11-20
Marvelous! Your method worked perfectly for my Brother HL-2070N with just a couple of small changes, all of which were menu options under System | Administration | Printing when I got to that point.

I then just deleted the old printer, changed the uri to the network address, changed the paper size to letter and viola! I had been struggling with this for days now, ever since upgrading to Gutsy. Thanks a ton!

---

### Post by neoroses on 2007-11-20
i  cannot for the life of me get the dcp-135c to work ???? errors everywhere lol any special ways for this printer?

---

### Post by keywest on 2007-11-20
My Brother MFC 8420 was detected and installed as a printer automatically by Ubuntu 7.10.  I jumped directly to the Scanner section and followed the steps without error other than the I/O errors after step 4 and after step 7.  I deleted the printer and started with the printer steps and encountered the following errors installig the lpr driver.  The cupswrapper installed fine.  Have not been able to make work as a scanner yet even though it worked fine with Kubuntu 7.0.4
 Preparing to replace mfc8420lpr 1.1.2-1 (using mfc8420lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8420lpr ...
/var/lib/dpkg/info/mfc8420lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8420lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8420lpr-1.1.2-1.i386.deb

---

### Post by floresena on 2007-11-22
Hi BoarDWorld,

Thanks for your useful post.

The only thing is that I found an error in it. In the step 5 of the scanner installation you noted that Product ID for Brother **MFC-215C** is **018c**. I tried this way and it didn't work.

So I executed the *lsub* command in the terminal and found that the Product ID for that printer-scanner is **0193** (the Vendor ID is the same you noted).

I changed it and it works perfectly.

---

### Post by Euandownunder on 2007-11-22
Thanks guys!..that how-to worked a treat..i can now use my Brother DCP-540CN scanner! One more thing to go, and i can finally be rid of Windows forever!!

---

### Post by BoardDWorld on 2007-11-22
> **floresena said:**
> Hi BoarDWorld,

Thanks for your useful post.

The only thing is that I found an error in it. In the step 5 of the scanner installation you noted that Product ID for Brother **MFC-215C** is **018c**. I tried this way and it didn't work.

So I executed the *lsub* command in the terminal and found that the Product ID for that printer-scanner is **0193** (the Vendor ID is the same you noted).

I changed it and it works perfectly.

Hey thanks for that, you're quite right. That was daft of me as it will only apply to DCP-115C printers of course. It's now adjusted, Thanks!

---

### Post by BoardDWorld on 2007-11-22
> **neoroses said:**
> i  cannot for the life of me get the dcp-135c to work ???? errors everywhere lol any special ways for this printer?

Hello, I have taken a look at brothers website and it seems that it may not configure itself without a few more adjustments as follows:

After completing the driver installation open Firefox and enter the following into the address bar:
```
http://localhost:631
```

Click on &#8220;Manage Printers&#8221; and confirm that the device name(DCP135C) is listed there.

If the device name is NOT listed there, click on "Add Printer" and install the driver following the on-screen instructions.

The default port is USB. If you want to use a different port, click on &#8220;Modify Printer&#8221; and select the required printer port.


Hope this helps!

---

### Post by C-A on 2007-11-24
Worked great for my MFC-440-CN Printer!
Thanks!

---

### Post by blazoner on 2007-11-25
**Network MFC420CN on Gutsy 7.10 64bit:**

After following steps 1-9 listed in the tutorial, printing from my MFC420CN still wasn't working, so I found another step from the Brother website:

A note from the [BSC Linux Support FAQ for Printer]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html"):
> *** I am using a AMD64 bit version of Debian/Ubuntu Linux. I installed both LPD/LPRng driver and the CUPS Wrapper driver, but I cannot print.**

      Install "lib32stdc++6" or "ia32-libs".Also:> [B]*  I'm using an AMD64 bit version of Linux. Can I use the Brother Linux printer drivers?
[/B]
      Yes, but please note the following conditions:

      For DPKG package users:
      Install the driver using the command option "--force-architecture".
      If you cannot print, install lib32stdc++6 or ia32-libs.

      Also, try copying the file which name starts with "brlpdwrapper" in the
      " /usr/lib/cups/filter" to the "/usr/lib64/cups/filter".
After installing both lib32stdc++6 and ia32-libs for good measure, and setting "Device:" to "LPD/LPR Host or Printer" on the second page of the "Modify Printer" dialog, with device URI set to "lpd://xxx.xxx.xxx.xxx", my test page fired right up!

---

### Post by wickedlester on 2007-11-25
Thanks for this howto. I set up my brother MFC-240C with no troubles. everything works great.

---

### Post by tvaddict on 2007-11-25
Thankyou for a comprehensive easy guide to install the Brother printer-scanner, I tried 64 bit Ubuntu and and couldn't get it to work, so I installed the i386 ubuntu and have now got my Brother DCP-115C working fine, thanks again from a newbee::)

Perhaps someone can give me a step by step for Ubuntu AMD64

---

### Post by BoardDWorld on 2007-11-26
> **tvaddict said:**
> Thankyou for a comprehensive easy guide to install the Brother printer-scanner, I tried 64 bit Ubuntu and and couldn't get it to work, so I installed the i386 ubuntu and have now got my Brother DCP-115C working fine, thanks again from a newbee::)

Perhaps someone can give me a step by step for Ubuntu AMD64

There's enough info posted by others in this thread to confidently add the information required. I'll update it tomorrow.

---

### Post by BoardDWorld on 2007-11-26
> **blazoner said:**
> **Network MFC420CN on Gutsy 7.10 64bit:**

After following steps 1-9.....

Thanks for sharing this, I'm sure it will help others.

---

### Post by nikef on 2007-11-26
> **BoardDWorld said:**
> Hey thanks for that, you're quite right. That was daft of me as it will only apply to DCP-115C printers of course. It's now adjusted, Thanks!

Hi thanks for this great how to
i am running ubuntu gutsy gibbon 7.10
i have installed my printer,and it prints :)

but i can not get my scanner to work :confused:

i found the above thread about changing the product id,but its not worked 
any1 got any ideas 

thanks

---

### Post by BoardDWorld on 2007-11-26
Hello, could you please tell me what model scanner or combo you are using? 32bit or 64bit Ubuntu? What errors showed during the installation? Can you post the output after running the "sudo dpkg -i brscanxxxxxxx.deb" command.

---

### Post by nikef on 2007-11-26
Hi and thank you
yes sorry,my printer is a brother dcp-115c ,the printer works brill :)

but i can not scan ,there was no errors during install,here is the file you asked for

trish@trish-desktop:~$ sudo dpkg -i brscanxxxxxxx.deb
[sudo] password for trish:
dpkg: error processing brscanxxxxxxx.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 brscanxxxxxxx.deb
trish@trish-desktop:~$


when i open xsane,i get this error after searching for the scanner 

failed to open device brother2;bus4devl
error during device i/0

---

### Post by nikef on 2007-11-26
Ooops i think its a 32bit ubuntu

how do i find out ?

---

### Post by BoardDWorld on 2007-11-26
That's ok it will most likely be 32bit. Could you please confirm that the brscan2-0.2.4-0.i386.deb file is on your desktop.

Also can I confirm you have run steps 6 and 7.

---

### Post by nikef on 2007-11-26
Yes here is a screen shot

---

### Post by BoardDWorld on 2007-11-26
Very cool desktop :) Could you please complete the following steps then post the output after the completeing the installation in step 2

Step 1:
```
cd Desktop
```

Step 2:
```
sudo dpkg -i brscan2-0.2.4-0.i386.deb
```

---

### Post by nikef on 2007-11-26
[QUOTE=BoardDWorld;3842546]Very cool desktop :) 

thank you :)

here is the file 

trish@trish-desktop:~$ cd Desktop
trish@trish-desktop:~/Desktop$ sudo dpkg -i brscan2-0.2.4-0.i386.deb
[sudo] password for trish:
(Reading database ... 163521 files and directories currently installed.)
Preparing to replace brscan2 0.2.4 (using brscan2-0.2.4-0.i386.deb) ...
Unpacking replacement brscan2 ...
Setting up brscan2 (0.2.4) ...

trish@trish-desktop:~/Desktop$



thank you very much for helping me

---

### Post by BoardDWorld on 2007-11-26
Great, so the installation was successful. Have you checked the Vendor and Product ID's are correct with the lsusb command?

Happy to try and help...

---

### Post by nikef on 2007-11-26
Yes,i think its correct


trish@trish-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c517 Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04f9:018c Brother Industries, Ltd
Bus 001 Device 001: ID 0000:0000
trish@trish-desktop:~$


have checked with yours and its seems the same

---

### Post by BoardDWorld on 2007-11-26
Could you please show me the last section of your libsane rules showing your scanner:

```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```

---

### Post by nikef on 2007-11-26
Last section of the libsane rules

# Dell A920
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5105", MODE="664", GROUP="scanner"
# Dell A960
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5107", MODE="664", GROUP="scanner"
# Dell 922
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5109", MODE="664", GROUP="scanner"
# Dell 1600n
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5250", MODE="664", GROUP="scanner"
# Brother DCP-115C
SYSFS{idVendor}=="Vendor ID: 04f9", SYSFS{idProduct}=="0193", MODE="666", GROUP="scanner"
LABEL="libsane_rules_end"

---

### Post by BoardDWorld on 2007-11-26
> **nikef said:**
> Last section of the libsane rules

# Dell A920
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5105", MODE="664", GROUP="scanner"
# Dell A960
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5107", MODE="664", GROUP="scanner"
# Dell 922
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5109", MODE="664", GROUP="scanner"
# Dell 1600n
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5250", MODE="664", GROUP="scanner"
# Brother DCP-115C
SYSFS{idVendor}=="**Vendor ID: **04f9", SYSFS{idProduct}=="0193", MODE="666", GROUP="scanner"
LABEL="libsane_rules_end"

Bingo, delete the area that's bold including the space so the ID number is directly after the quote:

```
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="666", GROUP="scanner"
```

P.S. you'll need to restart the PC. Goodnight! Or in your case "day" ;) (It's 2am!)

---

### Post by nikef on 2007-11-26
Wow thank you very much,sorry for keeping you up 

as soon as i clicked xsane this is what popped up,i can not thank you enough

you are a :KS

good night and god bless 

trish

---

### Post by BoardDWorld on 2007-11-26
That's great! Xsane is awesome software. 

God Bless you too!

---

### Post by nikef on 2007-11-27
Yes,just need to learn how to use xsane now,although i dont do a lot of scanning

one last question,you know the driver files i downloaded to my desktop? can they be deleted or moved somewhere safe,as its making  my desktop untidy 

thanks

---

### Post by BoardDWorld on 2007-11-27
Yes you can safely remove them. They will always be available from Brother.

---

### Post by nikef on 2007-11-27
Thanks  for all your help  :)

---

### Post by yellowbean on 2007-11-28
Well I'm hoping there's a simple reason my DCP7020 isn't printing. I followed the how-to and it is showing up in my "Printing Configuration" screen, but the test page doesn't print. When I look at the printer via [http://localhost:631](http://localhost:631) it says "Printer not connected; will retry in 30 seconds..."

Any ideas?

---

### Post by BoardDWorld on 2007-11-28
Try this: [http://ubuntuforums.org/showpost.php?p=3817666&postcount=59](http://ubuntuforums.org/showpost.php?p=3817666&postcount=59)

---

### Post by yellowbean on 2007-11-28
Actually nevermind. Bad port on my USB hub apparently. When I switched ports suddenly Ubuntu recognized that a printer was attached and installed the DCP7025 driver for me. Of course that didn't work, but when I redid all the steps in your how-to it worked beautifully. Still had to install the LPR, but I guess that seems to be pretty common.

Now to get this thing network shared with my wife's Windows PC...

Thanks for the great guide!

---

### Post by billio on 2007-11-29
Following Step 7, the outcome is this 
...:~/Desktop/Brother$ sudo dpkg -i --force-all dcp330clpr-1.0.0-9.i386.deb
Selecting previously deselected package dcp330clpr.
(Reading database ... 99563 files and directories currently installed.)
Unpacking dcp330clpr (from dcp330clpr-1.0.0-9.i386.deb) ...
Setting up dcp330clpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/dcp330c': No such file or directory
chown: cannot access `/var/spool/lpd/dcp330c': No such file or directory
chgrp: cannot access `/var/spool/lpd/dcp330c': No such file or directory
chmod: cannot access `/var/spool/lpd/dcp330c': No such file or directory

What next ?.

Bill

---

### Post by billio on 2007-11-29
What next ?. Well you just ignore the error messages - not easy for a new user. :-)

In order to make the driver work with a networked printer on a iMac, I had to put in the actual ip address rather than the local name, modifying this using localhost:631 .

Possibly worth adding these two points to the HowTo .. Thanks.

Bill

---

### Post by bluvy on 2007-12-01
Hello,
I'm currently using Kubuntu 7.10, 32-bit. I've installed LPR and CUPS, my MFC 7420 is connected via USB, and when I go to [http://localhost:631/printers/](http://localhost:631/printers/) it says:

Description: MFC7420
Location:
Printer Driver: Brother MFC7420 for CUPS
Printer State: processing, accepting jobs, published.
Device URI: usb:/dev/usb/lp0
(this is set as my default printer)

The installation was successful, however when I try to print test page it says "Printer not connected; will retry in 30 seconds...".
Is there something I have to adjust to connect the printer?

Thank you for your time.

---

### Post by keywest on 2007-12-06
If my MFC-8420 was detected by Ubuntu 7.10 and is working properly as a printer, do I need to start at step 1 of the printer section? Do I need to remove the recognized printer first? Any other precautions? It is encouraging to see others with success. I am determined to make it work and I have put a daily email alert on this thread.

---

### Post by Col-1023 on 2007-12-07
I've just upgraded to Gutsy and can't even print the test page using my brother MFC210C

I followed the guide and the printer drivers installed correctly,

I did not install LPR, since the guide said it wasn't necessary for gutsy.

I used firefox to go localhost:631 and found my printer was identified as Brother MFC210C.

When I try to print a test page the printer status changes from 'idle, accepting jobs, published' to 'processing, accepting, published."

The printer is ON, and the ink levels are ok.

Any help very much appreciated, thank you.

---

### Post by Col-1023 on 2007-12-07
I want to my windows box and tried to print a test page on the brother and it worked.

The mfc210c is linked to my ubuntu box via usb and my ubuntu box is networked to my windows box through a router, i use samba to print and transfer files ffrom my windows box to the ubuntu one and vice versa.

If I can print a page from the windows box, why won't anything print from the ubuntu box.

TIA.

---

### Post by Col-1023 on 2007-12-07
This is weird.

I followed the scanner howto and the scanner works perfectly, even xsane works without having to be root.

The only minor problem I have found with xsane so far is that when I quit, it throws up three errors before finally closing, something about not having permission to save files, but eventually the app closes.

I still can't print from the ubuntu box, but I assume it's some small tweak that I don't know about.

Any Help Appreciated.

---

### Post by ericartman on 2007-12-09
This guide has been a lifesaver for me and my Brother fax2580c. It works in 32 and 64 bit for me if I follow these steps
 
do the install tcsh
cd desktop
download both the lpr and cups driver to the desktop
force install the lpr then the cupsdriver
then go to the local host 631 page and print a page from the printers there, using the installed one not the generic

Worked everytime for me in any bit 64, 32, and mint, ultimate, and studio distros

Thanks a million.

Cart

---

### Post by Col-1023 on 2007-12-15
I really need help getting the brother to print.

As I've said above, the printer works when I print from a windowx box over samba, but when I print from the linux box, nothing happens.

The job que shows the job as first running, then processing, then completed, however nothing happens.

The printer is shown as ready, and idle when not in use, printing a test page has no effect.

The printer url in the applet is usb://Brother/MFC-210C

Any help appreciated.

---

### Post by Col-1023 on 2007-12-18
anyone have any ideas on what could cause this problem?

---

### Post by mikewhatever on 2007-12-18
Thanks a lot BoardDWorld! I am glad to have found this how-to before it had turned into a mega thread like the other one on Brother printers. Everything seems to work, although I had to install the LPR Driver to get over errors while installing MFC210C. Hopefully, guys at Brother Ltd will get the driver for DCP-115C out some day, yet it seems unlikely to happen any time soon. Cheers!

---

### Post by Posh on 2007-12-25
Ok after much pain I have my MFC-5840CN working in Gutsy amd64.  The instructions went fine except it wouldnt print anything. So i edited cupsd.conf and put in LogLevel debug and watched the /var/log/cups/error_log after trying to print a test page and I was getting an error about one of the libraries weren't able to be loaded..... so here is what I had to do

 sudo ln -s /usr/lib/libbrcompij2.so.1.0.2 /usr/lib32/libbrcompij2.so.1

apparently it was expecting the library in /usr/lib32 instead of /usr/lib  

Scanner installation went just fine.

I hope this can help someone else.

---

### Post by Polten on 2008-01-07
Thank you for this how-to.
My DCP-120C didn't print anymore after upgrade to 7.10.  Scanning was still OK.
I followed the printer steps and it went just fine.  Thank you!

---

### Post by spookyu on 2008-01-07
Hey, great how to, perfect for someone who is only a little linux savvy like myself. One minor problem that I could use a hand with though. I installed the printer driver perfectly by following your steps. I also installed the scanner driver without much of a hitch, but unfortunately xsane doesn't see the scanner (I have an MFC-465CN) and I need to continue with step 5. The problem is that I have my printer connected directly to the router and I'm not sure how to find the vendor ID as the printer doesn't come up when I enter that one command into the terminal (I assume that list is of things connected to my computer directly). So I just need to know how to find out my vendor ID and all that so I can finish setting this thing up. Thanks for your help.

---

### Post by BoardDWorld on 2008-01-09
> **spookyu said:**
> Hey, great how to, perfect for someone who is only a little linux savvy like myself. One minor problem that I could use a hand with though. I installed the printer driver perfectly by following your steps. I also installed the scanner driver without much of a hitch, but unfortunately xsane doesn't see the scanner (I have an MFC-465CN) and I need to continue with step 5. The problem is that I have my printer connected directly to the router and I'm not sure how to find the vendor ID as the printer doesn't come up when I enter that one command into the terminal (I assume that list is of things connected to my computer directly). So I just need to know how to find out my vendor ID and all that so I can finish setting this thing up. Thanks for your help.


I've never had to set up a network printer before but I'll try helping. Firstly I don't think you'll need to add it to your libsane.rules. I would first try the following command I found [[COLOR="Blue"]HERE[/COLOR]]("http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html")

```
brsaneconfig2 -a name=SCANNER1 model=MFC-465CN ip=**xx.xx.xx.xx**
```

You'll need to find out your printers IP by logging into your router and viewing the connected devices. You  will find your printer and its IP, change **xx.xx.xx.xx** in the code above to suit.

If you did need to add it to your libsane.rules you could simply connect your printer directly to your computer just to obtain it, I'm not savvy enough to tell you how to achieve this via network.

---

### Post by wankel on 2008-01-09
Kubuntu 7.10 Gutsy (clean install, back then)
Brother DCP-330c
MSI S271 notebook

starting situation: no print, no scan

ending situation: can print, some issue with margins. Scan not yet fully tested, as a user I got permission errors before editing the udev rules, guess that is also sorted out now.


------------------------------------------------------------------------------------------
Thanks all for either writing a nice howto or supplying with similar errors as I got with some hints.

After reading through the first 5 pages (and some other threads), I convinced my system that in the END the printer really should start doing what it was bought for, and while typing this post, my dcp-330c is printing the code I will paste below for future reference :-)

I followed a bit of a different path, as under Feisty I could get away with (mostly) installing the .debs as root with csh as shell. No luck this time though, but in the end it worked out.

```

wbk@sandi:~$ su -
Password:
root@sandi:~# cd /home/wbk/download/
root@sandi:/home/wbk/download# ls
brscan2-0.2.4-0.amd64.deb  dcp330ccupswrapper-1.0.0-10.i386.deb  dcp330clpr-1.0.0-9.i386.deb

root@sandi:/home/wbk/download# csh

# sudo dpkg -i --force-all  dcp330clpr-1.0.0-9.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package dcp330clpr.
(Reading database ... 143716 files and directories currently installed.)
Unpacking dcp330clpr (from dcp330clpr-1.0.0-9.i386.deb) ...
Setting up dcp330clpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/dcp330c': No such file or directory
chown: cannot access `/var/spool/lpd/dcp330c': No such file or directory
chgrp: cannot access `/var/spool/lpd/dcp330c': No such file or directory
chmod: cannot access `/var/spool/lpd/dcp330c': No such file or directory

# mkdir /var/spool/lpd

# dpkg -i dcp330clpr-1.0.0-9.i386.deb
dpkg: error processing dcp330clpr-1.0.0-9.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 dcp330clpr-1.0.0-9.i386.deb

# dpkg -i --force-all  dcp330clpr-1.0.0-9.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 143735 files and directories currently installed.)
Preparing to replace dcp330clpr 1.0.0-9 (using dcp330clpr-1.0.0-9.i386.deb) ...
Unpacking replacement dcp330clpr ...
Setting up dcp330clpr (1.0.0-9) ...

# ls
brscan2-0.2.4-0.amd64.deb  dcp330ccupswrapper-1.0.0-10.i386.deb  dcp330clpr-1.0.0-9.i386.deb

# dpkg -i --force-all  dcp330ccupswrapper-1.0.0-10.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package dcp330ccupswrapper.
(Reading database ... 143735 files and directories currently installed.)
Unpacking dcp330ccupswrapper (from dcp330ccupswrapper-1.0.0-10.i386.deb) ...
Setting up dcp330ccupswrapper (1.0.0-10) ...
cp: `/usr/lib/cups/filter/brlpdwrapperdcp330c' and `/usr/lib64/cups/filter/brlpdwrapperdcp330c' are the same file
 * Restarting Common Unix Printing System: cupsd                                                                                                                           [ OK ]

(http://ubuntuforums.org/showthread.php?t=590793, step 8)
# ls /usr/lib/cups/filter/
brlpdwrapperdcp330c  commandtoepson  foomatic-rip  hpgltops   imagetoraster  pdftops  pstopxl     rastertodymo   rastertogutenprint.5.0  rastertolabel  textonly
commandtocanon       cupsomatic      gziptoany     imagetops  oopstops       pstops   pstoraster  rastertoepson  rastertohp              rastertospl2   texttops
# ls /usr/lib64/cups/filter/
brlpdwrapperdcp330c  commandtoepson  foomatic-rip  hpgltops   imagetoraster  pdftops  pstopxl     rastertodymo   rastertogutenprint.5.0  rastertolabel  textonly
commandtocanon       cupsomatic      gziptoany     imagetops  oopstops       pstops   pstoraster  rastertoepson  rastertohp              rastertospl2   texttops
#

# dpkg -i brscan2-0.2.4-0.amd64.deb
Selecting previously deselected package brscan2.
(Reading database ... 143738 files and directories currently installed.)
Unpacking brscan2 (from brscan2-0.2.4-0.amd64.deb) ...
Setting up brscan2 (0.2.4) ...

#

Install ready, no good though
==================================================

retry:
---------------------------
wbk@sandi:~$ sudo dpkg -i --force-architecture /home/wbk/download/dcp330ccupswrapper-1.0.0-10.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 143822 files and directories currently installed.)
Preparing to replace dcp330ccupswrapper 1.0.0-10 (using .../dcp330ccupswrapper-1.0.0-10.i386.deb) ...
Unpacking replacement dcp330ccupswrapper ...
Setting up dcp330ccupswrapper (1.0.0-10) ...
/var/lib/dpkg/info/dcp330ccupswrapper.postinst: 3: /usr/local/Brother/Printer/dcp330c/cupswrapper/cupswrapperdcp330c: not found
cp: cannot stat `/usr/share/cups/model/brdcp330c.ppd': No such file or directory
dpkg: error processing dcp330ccupswrapper (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dcp330ccupswrapper
wbk@sandi:~$ ls /usr/local/Brother/Printer/dcp330c/
inf/ lpd/
wbk@sandi:~$ ls /usr/local/Brother/Printer/dcp330c/inf/
brdcp330cfunc    brio06ab.bcm     brio06af.bcm     brPrintListij2   setupPrintcapij
brdcp330crc      brio06ac.bcm     brio06ag.bcm     paperinfij2
wbk@sandi:~$ ls /usr/local/Brother/Printer/dcp330c/lpd/
brdcp330cfilter  filterdcp330c  psconvertij2
wbk@sandi:~$ lpinfo -v
network socket
network beh
direct usb://Brother/DCP-330C
direct hpfax
direct hp
network http
network ipp
network lpd
file cups-pdf:/
direct scsi
network smb
wbk@sandi:~$ ls /usr/share/cups/model

===========================================
2 changes: rm * cupswrapp, dpkg force all:
-------------------------------------------

wbk@sandi:~$ sudo rm /var/lib/dpkg/info/dcp330ccupswrapp*
wbk@sandi:~$ sudo dpkg -i --force-all /home/wbk/download/dcp330ccupswrapper-1.0.0-10.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ...
dpkg: serious warning: files list file for package `dcp330ccupswrapper' missing, assuming package has no files currently installed.
143819 files and directories currently installed.)
Preparing to replace dcp330ccupswrapper 1.0.0-10 (using .../dcp330ccupswrapper-1.0.0-10.i386.deb) ...
Unpacking replacement dcp330ccupswrapper ...
Setting up dcp330ccupswrapper (1.0.0-10) ...
cp: `/usr/lib/cups/filter/brlpdwrapperdcp330c' and `/usr/lib64/cups/filter/brlpdwrapperdcp330c' are the same file
 * Restarting Common Unix Printing System: cupsd                                                                         [ OK ]

wbk@sandi:~$

```


Now I can print,but all of the page is moved vertically. I read that some more users got that symptom, but I could not figure out yet how it is solved.

Thanks again, good luck to all of you :-)

---

### Post by wankel on 2008-01-09
> 
Now I can print,but all of the page is moved vertically. I read that some more users got that symptom, but I could not figure out yet how it is solved.

Maybe I found the cause: in the KDE print administration all formats were set to A4, but the web interface of CUPS still showed letter format.

This behaviour (KDE admin module and/or incorrect vertical margins)... could it have to do with the differences in Feisty and Gutsy? (I didn't use the printer too long with Feisty) Or is it since it is Apple instead of Eazy Software Products?

Anyway, too deep in the night for me now to test more.Relieved basic printing works.

---

### Post by wankel on 2008-01-09
> **wankel said:**
> 
starting situation: no print, no scan

ending situation: can print, some issue with margins. Scan not yet fully tested, as a user I got permission errors before editing the udev rules, guess that is also sorted out now.


Just a quick test: scanning as user (with fuse permission) works. Since I expect most of the margins-issues are solved as well, that leaves me without issues!

---

### Post by iansane on 2008-01-18
well the printer works regardless of the errors I got with the lpr driver.

```
from lpr driver

ian@lotus-control:~/Desktop$ sudo dpkg -i --force-all mfc6800lpr-1.1.2-1.i386.deb
[sudo] password for ian:
Selecting previously deselected package mfc6800lpr.
(Reading database ... 108426 files and directories currently installed.)
Unpacking mfc6800lpr (from mfc6800lpr-1.1.2-1.i386.deb) ...
Setting up mfc6800lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC6800': No such file or directory
chown: cannot access `/var/spool/lpd/MFC6800': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC6800': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC6800': No such file or directory
/var/lib/dpkg/info/mfc6800lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing mfc6800lpr (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc6800lpr



from cupswrapper

ian@lotus-control:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC6800-1.0.2-1.i386.deb
Selecting previously deselected package cupswrappermfc6800.
(Reading database ... 108440 files and directories currently installed.)
Unpacking cupswrappermfc6800 (from cupswrapperMFC6800-1.0.2-1.i386.deb) ...
Setting up cupswrappermfc6800 (1.0.2-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC6800
 * Restarting Common Unix Printing System: cupsd    

```

As you can see, the cups driver still installed corectly. I have to disagree with the brother site being any help. According to them, I am supposed to have something called lpd installed first. I don't have that installed. The only thing I did different on this try is to install that thcs or whatever it was. Some kind of c shell? Sorry I forgot the name but the first thing you say to install. What is that and why is it nessesary? Last time I tried installing without it, I got a ton of errors and then couldn't remove the partially installed driver, but apt-get, update console, and synaptic wouldn't work. Nothing would remove it so I had to format and start over.
I'm glad this worked. Thanks a lot for the how to. :-)

---

### Post by iansane on 2008-01-19
don't know what happend. The printer quit working and now my synaptic and apt-get are locked up and won't work. Looks like I'm going to have to format again. 

all the brother install howto's keep telling me to install the lpr package and then they go on to the other steps. my problem is I can't get past the first part. lpr won't install. Its telling me now that there's no /etc/init.d/lpd isn't lpd part of the lpr package? Of cource it can't find it. It hasn't installed it yet!!  Brother says lpd needs to be installed before installing the cups wrapper driver. What tha heck is lpd and where is it?!! I freakin hate brother and will never buy one again!

---

### Post by endersbean3k1 on 2008-01-19
Thank you SO MUCH! Couldn't get my MFC 420CN working before, and now I just printed a test page (first try!) as well as a test page I had tried to print from within a VMware virtual machine yesterday! \\:D/ I havn't tried to do the scanner yet, but the printing works and that is AWESOME. Thank you so much 

:guitar:
=D>=D>

---

### Post by AgentZ86 on 2008-01-20
Which is the best director to put drivers when you installed them ?

I guess my question is that if I download them to desktop and install and have everything working, if I delete my downloaded folders both the compressed download and the extracted download which I used for my driver installation, will that break my install if I remove those folders ?

I'm not sure how the linux drivers installation works does it continue to use those file on the desktop or does it copy/create what it needs then I can discard those files ???

Please advise
Thanks

---

### Post by wankel on 2008-01-24
> **iansane said:**
> don't know what happend. The printer quit working and now my synaptic and apt-get are locked up and won't work. Looks like I'm going to have to format again. 

Apt is quite a robust system, and it takes a while to make it lock up. The not so bright side is, that it is also more difficult to solve a problem once it really does not work anymore. 

If you used synaptic and apt-get with no luck, you can still try aptitude instead (command line tool as well, it scripts around apt-get)

Did you look up the errors you got from apt-get? Maybe you could ask help for that in a seperate thread.

> 
all the brother install howto's keep telling me to install the lpr package and then they go on to the other steps. my problem is I can't get past the first part. lpr won't install. Its telling me now that there's no /etc/init.d/lpd isn't lpd part of the lpr package? Of cource it can't find it. It hasn't installed it yet!!  

It is a bit confusing, but there are various print systems available for Linux. One of the deamons is lpd, and to let that deamon use your printer, it needs the lpr driver from Brother. 

Ubuntu 7.10 seems not to have a package lpd installed, but another package that includes lpd. Did you use dpkg with --force-all ?

> Brother says lpd needs to be installed before installing the cups wrapper driver. What tha heck is lpd and where is it?!! I freakin hate brother and will never buy one again!

I have to admit that it took me a while to get my DCP-330c up and running as well. I bought a Brother especially because Brother develops Linux drivers, so I expected a painless install.

It seems they still have to work on the website a bit, since it is not too clear for people just starting Linux.

I have heard and read though, that the support team is very responsive, so you could try sending them an email.

All in all, now that my printer is working and comes with big, easy to refill cartridges (admitted, that was a strong incentive as well to buy Brother, though Linux support came first) I am happy with my printer and do not hesitate to give a positive buying advice for those who need a reliable printer for documents (I did not use the photo printing capabilities and do not expect too much from them)

Anyway, good luck with your system!

---

### Post by wankel on 2008-01-24
> **AgentZ86 said:**
> Which is the best director to put drivers when you installed them ?

I guess my question is that if I download them to desktop and install and have everything working, if I delete my downloaded folders both the compressed download and the extracted download which I used for my driver installation, will that break my install if I remove those folders ?

I'm not sure how the linux drivers installation works does it continue to use those file on the desktop or does it copy/create what it needs then I can discard those files ???

Please advise
Thanks

Hi AgentZ86,

I expect that you can just throw away those files and folders. It depends a bit though on which package you downloaded and how you installed it.

If you used dpkg, and did not _try_ to install the drivers on your desktop, then dpkg copied them to the appropriate system directories.

On the other hand, if you used sources (as far as they are available) and asked to install them on your desktop, then they are where you said to put them.

If all of this does not make much sense to you, than you probably took the first path, and that means that you can throw away those files on your desktop. 

You can find loads of information on directory structures in GNU/Linux on the net, you could start at [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/) or, more in depth, at [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

Good luck!

---

### Post by AgentZ86 on 2008-01-24
> **wankel said:**
> Hi AgentZ86,

I expect that you can just throw away those files and folders. It depends a bit though on which package you downloaded and how you installed it.

If you used dpkg, and did not _try_ to install the drivers on your desktop, then dpkg copied them to the appropriate system directories.

On the other hand, if you used sources (as far as they are available) and asked to install them on your desktop, then they are where you said to put them.

If all of this does not make much sense to you, than you probably took the first path, and that means that you can throw away those files on your desktop. 

You can find loads of information on directory structures in GNU/Linux on the net, you could start at [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/) or, more in depth, at [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

Good luck!

Awsome thanks,

I forgot I posted about this I've actually figured that part  but those links are going be good for me.

Thanks

---

### Post by AgentZ86 on 2008-01-28
Nice how too,

I see many posts with errors and things for these brother printers, especially with Gutsy 7.10 
I believe this is related to the lpr and how the cups wrapper looks for it when you install the cups wrapper driver.

I think this can be solved by creating the symbolic link just after installing the lpr driver. This is noted on the brother site as well. And I get no errors

Basically like so:
Install your printers LPR driver found on the brother solutions site, either click and install with gdebi etc.OR download to desktop then click and install with gdebi you may get some errors about var/spool etc. (just ignore it) no problem here.[/LIST]
[LIST]
Then create symbolic link with this command in the terminial:
sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd[/LIST]
[LIST]
Install cups wrapper driver with gdebi-[/LIST]
Then remove the symbolic link which will be located in the /etc/init.d/ folder typically the one with the arrow next to it; and it may be the only one if you've not had any symbolic links created there.

And printing should be working perfectly and installing the cups wrapper driver should give no errors at all.

Then you can work on setting up your scanner portion using the how to listed here.

Now if I could just get my fax part working. I'm working on that now so hopefully I post back on that.

I hope this helps

---

### Post by mafiax on 2008-01-30
Ok I followed all the instructions and I can't get the scanner to work when I'm logged in under my user name.. if I log in as root it works. 

HELP

---

### Post by GamingMazter on 2008-01-31
Cheers Matey!

---

### Post by billgoldberg on 2008-02-01
I was in shock (not really, but still) when I heared my mother bought a new printer/scanner/fax machine.

We only use ubuntu and I thought I was screwed. 

This one saved me.

Thanks.

---

### Post by AgentZ86 on 2008-02-02
> **mafiax said:**
> Ok I followed all the instructions and I can't get the scanner to work when I'm logged in under my user name.. if I log in as root it works. 

HELP

To make it all work as normal user
basically the same as the how to listed in the begining of this post, but anyhow here it is.
[LIST]
Open the file "/etc/udev/rules.d/45-libsane.rules" with an editor.
I used gedit and you need to be root, so I did sudo gedit, then password
I like the clickety method of browsing so while in gedit select open and then browse to /etc/udev/rules.d/45-libsane.rules and either click or double click depending on how you have set your preferences and it will open the 45-libsane.rules in the gedit editor program. now you can add a line to the bottom of the file[/LIST]
[LIST]
#brother
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="666", GROUP="scanner"
NOTE: the 04f9 and the 018c entry? this is the product ID and vendor ID, and this one is specific for my printer/scanner so to find your vendor and product ID's open a terminal and type this command (lsusb)
This will show your printer vendor and product ID
Just replace the 04f9:018c with your vendor and product ID that you just found in the terminal.[/LIST]
[LIST]
Anyhow
You will see an entry all the way at the end of the /etc/udev/rules.d/45-libsane.rules file which says:
LABEL="libsane_rules_end" (do you see it?)[/LIST]
[LIST]
Your entry will go just above that.
and will include your vendor and product ID and will looks something like this:

#Brother MFC-240C   (note: this entry can be whatever your want to describe your printer/scanner)
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01ab", MODE="666", GROUP="scanner"

LABEL="libsane_rules_end"[/LIST]
[LIST]
Once you have your entry correct, then select save, then exit
exit your terminal by typing exit, then hit enter,[/LIST]

Then restart the OS

Scanning should now work well as a regular user.
I've tested with Xsane, and scan2pdf and more as regular user

I hope this helps

---

### Post by AgentZ86 on 2008-02-02
> "When two opposite points of view are expressed with equal intensity, the truth does not necessarily lie exactly halfway between them. It is possible for one side to be simply wrong."

LOL also possible for both sides to be equally right, and also both can be equally wrong, or even so both can be disproportionally right, and also disproportionally wrong.

LOL:guitar:

---

### Post by C-A on 2008-02-03
I am using my printer as a network printer. My printer works fine until the ip address changes and then I have to manually change it in cups. So, I guess I need to set the printer to have a static ip address.

I am not sure how to access those settings from my linux box. Any help/advice would be greatly appreciated.

---

### Post by AgentZ86 on 2008-02-03
> **C-A said:**
> I am using my printer as a network printer. My printer works fine until the ip address changes and then I have to manually change it in cups. So, I guess I need to set the printer to have a static ip address.

I am not sure how to access those settings from my linux box. Any help/advice would be greatly appreciated.

I'll try to help, but can you describe how your using it as a network printer ?

Do you have it plugged to a server and using the server as a print server / print share, or are you simply trying to access the printer when it's plugged into some local machine on the network.

In the later case then, most likely your using it as a local printer and want to share it with the other users on the network.

I'll fool with this some here at home, but I don't think you have to install any network options or do any network stuff for just doing that, it should be as simple as making sure your workgroup name is the same, and then the printer should appear on the network for use and adding it to your printer list.

I'll toy with it some more on mon. sometime after the superbowl etc. and see how the brother printers react.

My hp and all other printers on the network all are working anc can be shared over the network no problems there, but the network workgroup all has to be the same as far as that goes.

Anyhow I'll post back on this some more on mon.

---

### Post by C-A on 2008-02-03
> **AgentZ86 said:**
> I'll try to help, but can you describe how your using it as a network printer ?

Do you have it plugged to a server and using the server as a print server / print share, or are you simply trying to access the printer when it's plugged into some local machine on the network.

In the later case then, most likely your using it as a local printer and want to share it with the other users on the network.

I'll fool with this some here at home, but I don't think you have to install any network options or do any network stuff for just doing that, it should be as simple as making sure your workgroup name is the same, and then the printer should appear on the network for use and adding it to your printer list.

I'll toy with it some more on mon. sometime after the superbowl etc. and see how the brother printers react.

My hp and all other printers on the network all are working anc can be shared over the network no problems there, but the network workgroup all has to be the same as far as that goes.

Anyhow I'll post back on this some more on mon.

Thanks for the reply. My printer is a network printer and it is connected directly to my router.

---

### Post by pyxu619 on 2008-02-04
> **C-A said:**
> Thanks for the reply. My printer is a network printer and it is connected directly to my router.

I believe you can set the ip address just the way you do in windows. Go into the router page and set it as static. Depending on what router you have, the router's homepage address is different.

---

### Post by AgentZ86 on 2008-02-06
Sorry for the delay response.

You have to consult your printer documentation or poke around with the menu buttons on the printer, and set the IP address to a static IP address on the printer, And make sure it's within the IP address range of the DHCP range of the router. In other words if the router is dishing out IP's in the lets say 192.168.0.1 thru 192.168.0.255 or so then make sure that the static IP of the printer is set to something like 192.168.0.105 or something 

Or if your router is dishing out the range in the 10.1.10.200 to 10.1.10.255 then put the printer at 10.1.10.230 or something.

Anyhow this is something you can to on the printer itself, I would not change the router to static cause then you have to set all the machines IP addresses and they won't receive one automatically from the router, so it's simple for a couple machines, but if you have a larger network that gets real old real quick.

Anyhow if you disclose your model I may be able to clarify some more.

I hope this helps.

---

### Post by Kevin Funnell on 2008-02-09
BoardDWorld,
Thanks for your great article "[COLOR="Blue"]HOWTO: Ubuntu Gutsy 7.10 All Brother Printer Scanner Driver Installation for Newbies![/COLOR]", I stumbled across it in the Forum while waiting for the Brother's to open.  Following each step I successfully installed a Brother DCP-150C on both Feisty Fawn 7.04 and Gusty Gibbon 7.10.  All the functions of the unit are working perfectly, not bad for something that only cost $AUS 74:00,  a worth while machine for an old guy.
Thanks, Old Kevin

---

### Post by yasio on 2008-02-17
I've got problem with scanner in brother mfc 235C. i installed brscan2 and when i used xsane on destop i saw a announcement: ' couldn't open a device :'brother2:bus5;dev1'. Error during operation Input/Output ' i've got Ubuntu 7.10.

---

### Post by AgentZ86 on 2008-02-17
> **yasio said:**
> I've got problem with scanner in brother mfc 235C. i installed brscan2 and when i used xsane on destop i saw a announcement: ' couldn't open a device :'brother2:bus5;dev1'. Error during operation Input/Output ' i've got Ubuntu 7.10.

did you run xsane as root, or regular user ??

Try to run xsane as root (sudo xsane) from the terminal and see if that changes anything.

If it does then you have to follow these instructions listed here to get the scanner to work with regular users.

I hope this helps

I've created this page for help with Brother printers.
[www.iclbiz.com/brothermfc](www.iclbiz.com/brothermfc)

Also I've posted in the How To: section under How To: Brother MFC
I'ts very similar to the other how to's that have been posted;

See How to here:
[http://ubuntuforums.org/showthread.php?t=691781&highlight=Brother+MFC](http://ubuntuforums.org/showthread.php?t=691781&highlight=Brother+MFC)

---

### Post by Kevin Funnell on 2008-02-24
Yasio & Agent286,   Following the instructions in this post when installing the drivers for a DPC150C I did have problems on my first attempt on an old P3 computer the system was not current - no updates installed and I got the same error as Yasio got.  Second attempt the system was as current  Update Manger reported "Your system is up-to-date".  
With the printer & USB cable disconnected I installed the Printer drivesr, 
checked Firefox - Printer recognised
Disconnected Printer & USB cable again then I installed brscan2-0.2.4-0.i386.deb, powered down the computer re-connected the Printer & USB cable.
Restarted the computer, started XZane. I was able to use the scanner no problems or errors.
I suggest you make sure your system is current -using Update Manager.before reinstalling the drivers.   The only problem I have is if I press the Scan button and try to scan to a file option, the Brother's Control Panel displays a message "Connecting to PC" but nothing happens, it appears to clear the message after a few minutes.  I hope this helps you in getting you Scanner to work, when I had the same error as Yasio received I could us the scanner through OpenOffice.org Writer.  Old Kevin

---

### Post by Elderlygent on 2008-03-03
Fantastic! You are a public benefactor.:)

---

### Post by BoardDWorld on 2008-03-10
> **Kevin Funnell said:**
> Yasio & Agent286,   Following the instructions in this post when installing the drivers for a DPC150C I did have problems on my first attempt on an old P3 computer the system was not current - no updates installed and I got the same error as Yasio got.  Second attempt the system was as current  Update Manger reported "Your system is up-to-date"...  Old Kevin

Thanks for the help Kevin, I've added this to the tutorial.

---

### Post by growingneeds on 2008-03-11
I recently purchased the DCP-135C at the IT Show 2008 (Suntec City). The installation of the printer was a breeze. Although Feisty Fawn did not have the appropriate drivers for the printer, it did manage to detect the USB connection. Here's what I did to get the printer running:

1. At the terminal console, install tcsh.
2. Connect and turn on the printer.
3. From Brother Solutions ([http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)), download the LPR printer driver specific to DCP-135C in the form of a debian package. Double-click to install.
4. From the same website, download the CUPS printer driver specific to DCP-135C. (Again, a debian package.) Double-click to install.

And voilà, the new printer is installed. There is a slight misalignment to the right of the test print page. But, it is very slight. I can live with that.

---

### Post by growingneeds on 2008-03-11
The scanner for DCP-135C was set-up in an easy manner as described by BoardDWorld:

1. From Brother Solutions ([http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)), download the SANE scanner driver specific to DCP-135C in the form of a debian package. Double-click to install.
2. At the terminal, issue lsusb. Note the **Vendor ID:Product ID** listed for **Brother Industries, Ltd**. Mine was 04f9:01ce.
3. At the terminal, type "sudo gedit /etc/udev/rules.d/45-libsane.rules"
4. At the end of the list of recognised products, add
```
# Brother DCP-135C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01ce", MODE="664", GROUP="scanner"
```
Note that the Vendor ID & Product ID have to be changed accordingly.
5. Save the file. Reboot, and start scanning with XSane Image Scanner.

Thank you, BoardDWorld!

---

### Post by jack188 on 2008-03-26
hi all ubuntu it's great!!!!
sorry but i've a problem with this tutorial and my Brother DCP-115 and 'im on a amd64 bit
when i get this command
```


sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb



```
```


jack@Panzer-Faust:~$ cd Scrivania
jack@Panzer-Faust:~/Scrivania$ sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb
dpkg - attenzione, ignoro il seguente problema perché si è usata --force:
 il pacchetto è per una architettura (i386) diversa da quella del sistema (amd64)
(Lettura del database ... 119404 file e directory attualmente installati.)
Mi preparo a sostituire mfc210clpr 1.0.2-1 (con mfc210clpr-1.0.2-1.i386.deb) ...
Spacchetto il sostituto di mfc210clpr ...
Configuro mfc210clpr (1.0.2-1) ...
mkdir: impossibile creare la directory `/var/spool/lpd/MFC210C': Nessun file o directory
chown: impossibile accedere a `/var/spool/lpd/MFC210C': Nessun file o directory
chgrp: impossibile accedere a `/var/spool/lpd/MFC210C': Nessun file o directory
chmod: impossibile accedere a `/var/spool/lpd/MFC210C': Nessun file o directory
ln: creazione del link simbolico `/usr/lib/libbrcompij2.so.1.0' a `/usr/lib/libbrcompij2.so.1.0.2': Il file esiste
ln: creazione del link simbolico `/usr/lib/libbrcompij2.so.1' a `/usr/lib/libbrcompij2.so.1.0.2': Il file esiste
ln: creazione del link simbolico `/usr/lib/libbrcompij2.so' a `/usr/lib/libbrcompij2.so.1.0.2': Il file esiste

```

sorry for my english because i'm only 14...   :guitar:

---

### Post by Kevin Funnell on 2008-03-28
G'Day All,
In my post #126 Quote: "[COLOR="Magenta"]The only problem I have is if I press the Scan button and try to scan to a file option, the Brother's Control Panel displays a message "Connecting to PC" but nothing happens, it appears to clear the message after a few minutes.[/COLOR]"  With the help from Brother Solutions Center Japan I can now scan any document using the Scan Button or Xzane.  
I had to send  Brother Solutions Cente the "*brscan-skey --diagnosis*" from this they told me that "*Scanimage is not installed.  Since Scanimage is contained in sane-utils in Ubuntu, please install it.*" (the Japanese are so polite).
Also there are new drivers for a lot of their newer DCP printer/scanners, installing the new version may help those that are having minor problems with their printer/scanner functions.  Old Kevin
.

---

### Post by Doorslammer on 2008-04-01
probem with scan /xsane 
followed brothers site 
```
Devices on network
  0 SCANNER1            "MFC-5440CN"        N:BRN_ABA9E7

```
using the node name   because my printer is networked  
when I open xsane is scans for devise then nothing happens , the xsane program never opens up .
should I have left the node name as BRN_XXXX or input like I did the real name 
using kubuntu 7.10 
my printer works fine been working fine for a long time  just wanted to *** the scanner

never mind 
deleted /usr/local/Brother/sane/brsanenetdevice2.cfg  file  
got it to work by using the ip instead of the node name 
sudo brsaneconfig2 -a name=SCANNER1 model=MFC-5440CN ip=192.168.001.100

---

### Post by galleonway on 2008-04-05
[I]Step 6:
In Terminal type the following:

Ubuntu Code:

sudo gedit /etc/udev/rules.d/45-libsane.rules
[/I]

Could someone please advise how to modify this for Hardy? I'm stuck.

---

### Post by galleonway on 2008-04-07
How would I get my Brother MFC scanner working in Hardy?

---

### Post by galleonway on 2008-04-09
This is the content of  //usr/local/Brother/sane/models2 in Hardy. My model isn't listed. Is that why the scanner doesn't work?  

[Support Model]

0x01c9,  16,2,"DCP-9040CN"
0x01ca,  16,1,"MFC-9440CN"
0x01cb, 116,2,"DCP-9045CDN"
0x01cc, 116,1,"MFC-9840CDW"
0x01ec, 116,1,"MFC-9640CW"



0x01e4, 10,2,"DCP-357C"
0x01e3, 10,2,"DCP-353C"
0x01e2, 10,2,"DCP-157C"
0x01e1, 10,2,"DCP-153C"
0x01e0, 12,1,"MFC-265C"
0x01df, 10,2,"DCP-155C"
0x01de, 12,1,"MFC-880CDN"
0x01dd, 10,1,"MFC-870CDN"
0x01dc, 10,1,"MFC-650CD"
0x01db, 12,1,"MFC-480CN"
0x01da, 12,1,"MFC-885CW"
0x01d9, 12,1,"MFC-685CW"
0x01d8, 12,1,"MFC-680CN"
0x01d7, 12,1,"MFC-465CN"
0x01d6, 12,1,"MFC-260C"
0x01d5, 10,1,"MFC-235C"
0x01d4, 10,1,"MFC-230C"
0x01d3, 10,2,"DCP-770CN"
0x01d2, 10,2,"DCP-770CW"
0x01d1, 12,2,"DCP-560CN"
0x01d0, 10,2,"DCP-350C"
0x01cf, 10,2,"DCP-150C"
0x01ce, 10,2,"DCP-135C"

---

### Post by darrenleeweber on 2008-04-09
> **Posh said:**
> Ok after much pain I have my MFC-5840CN working in Gutsy amd64.  The instructions went fine except it wouldnt print anything. So i edited cupsd.conf and put in LogLevel debug and watched the /var/log/cups/error_log after trying to print a test page and I was getting an error about one of the libraries weren't able to be loaded..... so here is what I had to do

 sudo ln -s /usr/lib/libbrcompij2.so.1.0.2 /usr/lib32/libbrcompij2.so.1

apparently it was expecting the library in /usr/lib32 instead of /usr/lib  

Scanner installation went just fine.

I hope this can help someone else.



This may  be just one file among many that require symbolic links for amd64.  See this Brother web page for details:

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142)

---

### Post by darrenleeweber on 2008-04-09
Brother HL-4040CN series on Ubuntu Gutsy 7.10 amd64

```

sudo -i
aptitude install lpr
mkdir /var/spool/lpd
dpkg -i --force-all --force-architecture hl4040cnlpr-1.0.0-7.i386.deb
dpkg -i --force-all --force-architecture hl4040cncups-1.0.0-7.i386.deb

```

This installed into
/usr/local/Brother/Printer/hl4040cn/

The CUPS web admin, [http://localhost:631/printers/](http://localhost:631/printers/)
shows that I have a problem with access to a filter:

"Filter "/usr/local/Brother/Printer/hl4040cn/cupswrapper/brlpdwrapper_hl4040cn" for printer "HL4040CN" not available: Permission denied"

I've checked all the file path and file permissions, they seem fine to me (everyone read/execute), eg:

```

-rwxr-xr-x 1 root root 18160 2007-08-23 10:51 brcupsconfcl1
-rwxr-xr-x 1 root root  4529 2007-08-23 10:51 brlpdwrapper_hl4040cn
-rwxr-xr-x 1 root root  2265 2007-08-23 10:51 cupswrapperSetup_hl4040cn

```


Turns out there is a specific how-to about this issue here:
[http://www.schmut.com/howto/hl-4040-cn-on-kubuntu-gutsy](http://www.schmut.com/howto/hl-4040-cn-on-kubuntu-gutsy)

Please add this link to the top of this how-to.

---

### Post by MichaelSM on 2008-04-13
Thank you very much BoardDWorld.

I'd already done the DCP-115C printer and scanner installs with the downloads from Brother. Printer fine, scanner no go.

So I simply copied the line:

# Brother DCP-115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner"

into   /etc/udev/rules.d/45-libsane.rules  restarted, and perfect result!

Can't get better than that, can we!?

Excellent how-to.

Thanks again,

Michael.

PS. This is on a Gutsy box. I haven't changed my personal description becos my main box is still Feisty. OK?

PPS. The advice also worked perfectly with a Brother MFC-3240C install on Ubuntu Ultimate (Kubuntu) Just a matter of "lsusb" and entering the model name and ids into the sane library.

Absolutely fantastic fix for a silly problem.

---

### Post by avtolle on 2008-04-18
Thank you very much, BoardDWorld. Used your how to to install Brother MFC240C on Hardy Beta AMD-64. Printer and scanner are working (that's all I need for now). Two modifications to the how-to:

1) Under Hardy, need to do: ```

sudo mkdir /usr/share/cups/model 
```
as Hardy does not create this directory. I did this before step 7, as the FAQ at the Brother Web Site indicated this would be needed. 

2) Under Hardy amd-64, no need to perform step 8. 

The scanner driver for 64 bit brscan2, Debian, worked on installation.

Again, thanks.

---

### Post by BoardDWorld on 2008-04-30
> **avtolle said:**
> Thank you very much, BoardDWorld. Used your how to to install Brother MFC240C on Hardy Beta AMD-64. Printer and scanner are working (that's all I need for now). Two modifications to the how-to:

1) Under Hardy, need to do: ```

sudo mkdir /usr/share/cups/model 
```
as Hardy does not create this directory. I did this before step 7, as the FAQ at the Brother Web Site indicated this would be needed. 

2) Under Hardy amd-64, no need to perform step 8. 

The scanner driver for 64 bit brscan2, Debian, worked on installation.

Again, thanks.

Thank you, I'll run through the installation myself soon and update the how-to accordingly.

---

### Post by Kevin Funnell on 2008-05-04
G'Day Forum Readers,     Thanks in advance

I need some help in getting a Brother DCP150C Printer/Scanner to work with Xsane Image Scanner under 64bit (Intel) Hardy Herron 8.04.  
I have successfully installed the above printer/scanner on two 32bit Gusty Gibbon 7.04 computers using [COLOR="Blue"]BroadDWorld's[/COLOR] post [COLOR="SandyBrown"]HOWTO: Ubuntu Gutsy 7.10 All Brother Printer Scanner Driver Installation for Newbies![/COLOR], and using the Brothers Web site for reference, I have read all 142 entries plus other post on Installing scanners. 

I have now updated one computer to Hardy Heron 8.04 64bit.  The printer installation went well no problems and all functions work well, I ran into problems when installing the scanner side of the unit.  After closing down the unit and removing the USB cable I followed the steps 1, 2 3 ,3a & 3b,  &#8211; 4.  I omitted step 5 as I already knew the Vendor ID & Product ID.  When I tried to edit:  [COLOR="SandyBrown"]sudo gedit /etc/udev/rules.d/45-libsane.rules[/COLOR] (Step 6) error no file found.  I can use the scanner by pressing the Scan Button on the Scanners Control Panel but this saves the scanned file to [COLOR="Blue"]/root/brscan[/COLOR] which is hard to remove when the task is completed.  When I start-up  Xsane Image Scanner it show the scanner (available devices) clicking on the scanner button a pop-up appears, Error  - Failed to open device 'brother2:bus2:dev1':   Error during device I/O. 

Is there anyway I can correct the above problem so I can use Xsane Image Scanner.  I tried various options (create /45-libsane.rules and installing and/or re-installed: sane, sane-utils, xsane, xsane-common), or should I do a re-install (everything and clear out posible errore I have created.

Thanks again,  Old Kevin

---

### Post by sameer102 on 2008-05-10
Hello, I am fairly new to Ubuntu, and I am having trouble installing my Brother DCP-135c.

I have followed this tutorial, but I have run into some trouble. I use Ubuntu 7.10.

I have downloaded the CCUPS and the LPR files to my desktop.

This is what happened:

> sameer@sameer-laptop:~/Desktop$ sudo dpkg -i --force-all dcp135clpr-1.0.1-1.i386.deb
(Reading database ... 111991 files and directories currently installed.)
Preparing to replace dcp135clpr 1.0.1-1 (using dcp135clpr-1.0.1-1.i386.deb) ...
Unpacking replacement dcp135clpr ...
Setting up dcp135clpr (1.0.1-1) ...
mkdir: cannot create directory `/var/spool/lpd/dcp135c': No such file or directory
chown: cannot access `/var/spool/lpd/dcp135c': No such file or directory
chgrp: cannot access `/var/spool/lpd/dcp135c': No such file or directory
chmod: cannot access `/var/spool/lpd/dcp135c': No such file or directory

sameer@sameer-laptop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.desudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.debdcp135ccupswrapper-1.0.1-1.i386.deb
dpkg: error processing cupswrapperMFC210C-1.0.2-3.i386.desudo (--install):
 cannot access archive: No such file or directory
dpkg: error processing dpkg (--install):
 cannot access archive: No such file or directory
dpkg: error processing -i (--install):
 cannot access archive: No such file or directory
dpkg: error processing --force-all (--install):
 cannot access archive: No such file or directory
dpkg: error processing cupswrapperMFC210C-1.0.2-3.i386.debdcp135ccupswrapper-1.0.1-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cupswrapperMFC210C-1.0.2-3.i386.desudo
 dpkg
 -i
 --force-all
 cupswrapperMFC210C-1.0.2-3.i386.debdcp135ccupswrapper-1.0.1-1.i386.deb


Could someone help please?

---

### Post by Roger Mudd on 2008-05-25
Hardy Update

Just installed Hardy. I have a DCP-7020 that worked well under Gutsy using this guide.
Working from a fresh install, I had the same experience as avtolle.
Creating the directory "/usr/share/cups/model" solved my printer driver installation problems. I did not have to manually add the device ID. My scanner was recognized immediately.

---

### Post by eauvirgo on 2008-05-26
Thanks worked Great!

---

### Post by mahasmb on 2008-06-16
What an awesome How To!

It worked nicely. Thank you ever so much. I was having so much trouble getting my printer (connected to a separate Windows computer) to work through a networked Ubuntu laptop.

---

### Post by null byte on 2008-06-17
Nevermind solved. :)

Perfect guide ;)

---

### Post by elderbuy on 2008-07-27
Just want to say "Thanks".  Your post got my printer working on the network on the first try.

---

### Post by Ben Dover on 2008-07-29
Thanks BoardDworld, this how-to solved all my problems with a Brother DCP540CN.Up untill now i had to boot into windows to do any printing or scanning. Now i'm off to boot windows out!
Thanks again.
Euan..

---

### Post by BoardDWorld on 2008-07-30
> **Ben Dover said:**
> Thanks BoardDworld, this how-to solved all my problems with a Brother DCP540CN.Up untill now i had to boot into windows to do any printing or scanning. Now i'm off to boot windows out!
Thanks again.
Euan..

You're welcome, thanks for the feedback! :guitar:

---

### Post by mella2000 on 2008-08-02
I go to step 10 and Printer MFC210C may not be connected. 
Ubuntu read a Brother 115 dpc but cannot find properly driver and it sugest Brother 1200 dcp.

---

### Post by cedric on 2008-08-06
Hi,

On Hardy with Brother MFC-235 and drivers installed, I have same problem discussed earlier as : I cannot scan if I am not root.

However the solution which seems to have been working on Gutsy is maybe not available on Hardy since I have no *libsane* in /etc/udev/rules.d/

How can I fix permissions for this ?


Thanks,

---

### Post by BoardDWorld on 2008-08-08
> **cedric said:**
> Hi,

On Hardy with Brother MFC-235 and drivers installed, I have same problem discussed earlier as : I cannot scan if I am not root.

However the solution which seems to have been working on Gutsy is maybe not available on Hardy since I have no *libsane* in /etc/udev/rules.d/

How can I fix permissions for this ?


Thanks,

Hello, with Hardy you shouldn't need to run it as root or modify the libsane rules as performed in step 5 and onwards. Did you perform step 4 and check to see if it was working? I have 2 printers (115c and 215c) and they both didn't need the device added to the libsane rules. Others have reported this also.


Thanks!

---

### Post by BoardDWorld on 2008-08-08
> **mella2000 said:**
> I go to step 10 and Printer MFC210C may not be connected. 
Ubuntu read a Brother 115 dpc but cannot find properly driver and it sugest Brother 1200 dcp.

First I would like to confirm if you are running 64bit?

---

### Post by kyoshi52 on 2008-08-10
Thanks very much from a newbie.
This was extremely helpful.
Kyoshi52

---

### Post by RavanH on 2008-08-13
> **BoardDWorld said:**
> First I would like to confirm if you are running 64bit?

Hi BoardWorld,

Another user but I seem to be in a similar situation. I am on a 64bit Hardy system and my DCP-115C was recognized upon first connection and (like the other poster) the DCP 1200 driver was recommended.

With that driver, printing was not possible. No errors or anything and the printer even showed 'Receiving Data' on it's little LCD screen but nothing was printed out...

Then I found your how to and installed the MFC 210C drivers by just following your steps and copy-pasting the commands (first part only, for printing) in terminal. All went VERY smooth , THANKS :) but one problem remains: the same result as with the recommended 1200 driver, no actual printing taking place :(

Any idea?

--ravan

EDIT: for what it is worth, I did already have lib32stdc++6 and ia32-libs installed on my system.

---

### Post by mella2000 on 2008-08-18
> **BoardDWorld said:**
> First I would like to confirm if you are running 64bit?

No, I'm 32 bit. Ubuntu 8.
It read two printers: DCP 115 and MFC 210. It doesn't allow me to print...

---

### Post by ACGarib on 2008-08-21
Hi I just got a MFC-465cn and the printer part of the guide worked great, but the scanner part is giving me problems.

In order to scan something, I have to run xsane as root. I'm running 32 bit Hardy, and there is no 45-libsane.rules, so I can't fix the problem.

I read here: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/205496](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/205496) that installing sane-utils fixes the problem, but it didn't work for me.

Anyone have any suggestions?



**EDIT**: I fixed it by following:

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9)

Once again, a few minutes after I run out of ideas and make a post here, I somehow figure it out.

---

### Post by BoardDWorld on 2008-08-21
> **ACGarib said:**
> Hi I just got a MFC-465cn and the printer part of the guide worked great, but the scanner part is giving me problems.

In order to scan something, I have to run xsane as root. I'm running 32 bit Hardy, and there is no 45-libsane.rules, so I can't fix the problem.

I read here: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/205496](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/205496) that installing sane-utils fixes the problem, but it didn't work for me.

Anyone have any suggestions?



**EDIT**: I fixed it by following:

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9)

Once again, a few minutes after I run out of ideas and make a post here, I somehow figure it out.

I don't think that remedy is very safe as it opens all your usb ports to security threats. Can you try this:

[http://ubuntuforums.org/showpost.php?p=5636012&postcount=4](http://ubuntuforums.org/showpost.php?p=5636012&postcount=4)

---

### Post by ACGarib on 2008-08-22
> **BoardDWorld said:**
> I don't think that remedy is very safe as it opens all your usb ports to security threats. Can you try this:

[http://ubuntuforums.org/showpost.php?p=5636012&postcount=4](http://ubuntuforums.org/showpost.php?p=5636012&postcount=4)

I looked at dll.conf and "brother2" is already there.

What I did was ```
sudo scanimage -L
```

and it showed ```
device `brother2:bus5;dev1' is a Brother MFC-465CN USB scanner
```

so I knew that brother2 is needed in dll.conf.

I followed the rest of the directions and it doesn't work.

I guess I'll stick with running xsane as root and not doing the fix I mentioned in the earlier post. It's not like I scan stuff very often.

We'll see what happens in Intrepid Ibex.

---

### Post by corbcox on 2008-08-25
I have been trying for several weeks to get my brother printer to work over my network at work.  Finally I was able to by following this.  Thanks for the time and effort youve put into this guide.

corbcox

---

### Post by JC0124 on 2008-09-01
Wonderful how to, this worked great with my brother MFC240C, which always causes a lot of problems with Linux in general.  Keep up the great work.

---

### Post by Breakar on 2008-09-08
My printer stopped working, it was working fine then stopped after i reinstalled ubuntu.

im using the drivers from synaptic manager, mfc 260c and im using hardy 8.04

the printer detects when i plug it in it will have a searching icon then say MFC-260 found and have configuration button, when i try print it will say "printer 'MFC-260' may not be connected".

```
/usr/lib/cups/filter$ dir
brlpdwrapperDCP110C    brlpdwrapperMFC3220C   foomatic-rip
brlpdwrapperdcp135c    brlpdwrapperMFC3240C   gziptoany
brlpdwrapperdcp150c    brlpdwrapperMFC3320CN  hpgltops
brlpdwrapperdcp153c    brlpdwrapperMFC3340CN  imagetops
brlpdwrapperDCP310CN   brlpdwrapperMFC3420C   imagetoraster
brlpdwrapperdcp350c    brlpdwrapperMFC3820CN  oopstops
brlpdwrapperdcp353c    brlpdwrapperMFC410CN   pdftops
brlpdwrapperdcp560cn   brlpdwrapperMFC420CN   pstops
brlpdwrapperdcp770cw   brlpdwrappermfc465cn   pstopxl
brlpdwrapperFAX1815C   brlpdwrapperMFC5440CN  pstoraster
brlpdwrapperFAX1820C   brlpdwrapperMFC5840CN  rastertodymo
brlpdwrapperFAX1835C   brlpdwrapperMFC620CN   rastertoepson
brlpdwrapperFAX1840C   brlpdwrappermfc680cn   rastertoescpx
brlpdwrapperFAX1920CN  brlpdwrappermfc685cw   rastertogutenprint.5.0
brlpdwrapperFAX1940CN  brlpdwrappermfc885cw   rastertohp
brlpdwrapperFAX2440C   commandtocanon	      rastertolabel
brlpdwrapperMFC210C    commandtoepson	      rastertopclx
brlpdwrappermfc230c    commandtoescpx	      rastertospl2
brlpdwrappermfc235c    commandtopclx	      textonly
brlpdwrappermfc260c    cupsomatic	      texttops

```

I also get the error

There was an error during the CUPS operation: 'server-error-service-unavailable'.

This happens when i go to administration>printing


edit - fixed my problem when my printer is low on ink it won't print ! replaced the ink and it worked.

---

### Post by augoldfinger on 2008-09-10
Yikes!
I got a system error
The package 'mfc665cwcupswrapper' is in a inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?

What did I do wrong?

Then I got
The package 'mfc665cwcupswrapper' is in a inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.

How Do I start over?
Wow Sorry!!

---

### Post by bigfootx2 on 2008-09-15
Thanks BoardDWorld

I stumbled around trying to get my printer to work until I found your HOWTO.

The scanning was more tricky as my MFC440CN is networked. However, it's now working as well.

After your scanner step 3 I configured my MFC in Terminal like this

```
 brsaneconfig2 -a name=Brother-MFC model=MFC-440CN ip=192.168.1.19
```

Precise model and ip details were necessary.

I can't resist a swipe at Brother though. Why can't they do something as simple as the hp-setup program?

But thanks again for the HOWTO and all those who have contributed.

---

### Post by badfish69 on 2008-09-18
MFC-465CN works on 64 bit Ubuntu with these instructions and "lib32stdc++6" and "ia32-libs" installed. CUPS wasn't successful the first time, so lpr and CUPS both had to be reinstalled. About to try the scanner.

The scanner also works, but not quite how described. Apparently for Ubuntu releases following 7.10, there is no 45-libsane.rules. Instead I had follow these instructions:

[For Ubuntu 8.04]

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
2. Edit "0664" to "0666" in "USB devices" section.

Before the edit --------------------------
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"
```

After the edit --------------------------
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
```

3. Restart the OS.

source
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9)

---

### Post by Liametc on 2008-10-09
THANKYOU THANKYOU badfish!

your solution worked for me. it was a shame that i had to read through 17 pages and yours was the last post but it was worth it!

you are a legend among men sir!:)

---

### Post by stig on 2008-10-21
Hi, I use two computers, each with the same Ubuntu software and each connected to its own Brother HL-2030 printer. Earlier in the month I upgraded the PCs from Ubuntu 6.04 to 8.04. The printers no longer worked and finally, on 15th October, I had to re-install the lpr and CUPS files from the Brother site. Then all seemed OK - I could print as previously from Open Office, Gedit, Thunderbird etc.

But I have since loaded an Ubuntu update to CUPS and now I can still print a test page and print from Gedit and Thunderbird - but I cannot print from Open Office (OO). When I try to print in OO, the printer light blinks once and then nothing more happens. System/Printer shows nothing queued. Yet the print dialog in OO looks OK.

Has anyone else encountered this? It is the same problem on both of my PCs. I haven't re-installed the lpr or CUPS files because the printers work OK for Gedit and Thunderbird so I reason it cannot be due to the ppd files.

When I go to [http://localhost:631/printers](http://localhost:631/printers) and click on Manage Printers I get:
HL2030-for-CUPS
Description: HL2030-for-CUPS
Location:
Printer Driver: Brother HL2030 for CUPS
Printer State: idle, accepting jobs, published.
Device URI: usb://Brother/HL-2030%20series

As far as I can recall this is the same as when the printers were working. It seems to be a problem in communication between the printers and OO (but not between the printers and other software).

Printing is important for my work and it's a real hassle finding first that the Ubuntu 8.04 upgrade wrecked my printing and possibly the CUPS update has wrecked it again!

---

### Post by Hypnosleepman on 2008-10-21
[QUOTE=stig;6004861]But I have since loaded an Ubuntu update to CUPS and now I can still print a test page and print from Gedit and Thunderbird - but I cannot print from Open Office (OO). When I try to print in OO, the printer light blinks once and then nothing more happens. System/Printer shows nothing queued. Yet the print dialog in OO looks OK.

Has anyone else encountered this? It is the same problem on both of my PCs. I haven't re-installed the lpr or CUPS files because the printers work OK for Gedit and Thunderbird so I reason it cannot be due to the ppd files.

When I go to [http://localhost:631/printers](http://localhost:631/printers) and click on Manage Printers I get:
HL2030-for-CUPS
Description: HL2030-for-CUPS
Location:
Printer Driver: Brother HL2030 for CUPS
Printer State: idle, accepting jobs, published.
Device URI: usb://Brother/HL-2030%20series

As far as I can recall this is the same as when the printers were working. It seems to be a problem in communication between the printers and OO (but not between the printers and other software).

Same kind of thing happening with my MFC-3240C. I get the same [http://localhost:631](http://localhost:631) results except they are for MFC-3240C. I can print a test page, I can print text and some html pages from terminal using "lp" but lose the formatting. But I get nothing from any apps. Scanner works great in all apps. The LCD on the printer says receiving data for about 1/2 a second when I send to the printer, then... nothing. And no errors I can find. The print queue says complete. Must be something simple i am not able to figure out. I'm using kubuntu with ABIT VH6II motherboard. Pentuim 1.0g CPU, 1gb RAM. installed kubuntu 10/15/2008. Any help appreciated.

---

### Post by stig on 2008-10-22
> **Hypnosleepman said:**
> Same kind of thing happening with my MFC-3240C.

My problem seems to be solved now. I had said above "I haven't re-installed the lpr or CUPS files because the printers work OK for Gedit and Thunderbird so I reason it cannot be due to the ppd files". Well, my reasoning was wrong (not unusual!). In desperation, I went through the installation steps at the beginning of this thread and the pinter now works in Open Office as well as my other software.

But before doing the installation I deleted the old printer from the System | Printers dialog and I also deleted the /var/spool/lpd folder and the /usr/share/cups/model folder. In the installation I then followed the steps including those which install these two folders again.

My system was Dapper 6.06 but then I upgraded to Hardy 8.04. According to this thread, the lpr and cups folders are not present by default in Hardy and have to be created. However when I upgraded from Dapper the ones already there seemed to be carried over into my Hardy set up - and worked fine in all my apps. It was only when a few days ago there was an Ubuntu update to CUPS files that I lost the ability to print in Open Office.

So it seems a good idea to get rid of the folders and install from scratch.

I also noticed that when I finished the installation and printed a test page from the System | Printing dialog, a second version of the printer icon appeared in the printer box. This one did not work and I deleted it. 

I have now done the re-install on both my PCs and they seem to be printing correctly.

Thank you BoardDWorld for your HOWTO!

---

### Post by shamrock_uk on 2008-10-22
Just wanted to say a big thank you to the OP, I was able to talk my mum through the walkthrough in 20 mins over the phone and it worked like a charm! :smile:

---

### Post by maxter on 2008-11-04
for a lot of models lps drivers and cups wrapper are already packaged in universe.
simply try to find your model name in synaptic searching name&description.

my dcp353c drivers are included in brother-cups-wrapper-extra and brother-lpr-driver-extra.

i think all requirements for installation will be resolved from apt (for example csh is a required package)

i didn't test those packages, because i already installed all the stuff following this thread procedure, but i don't see why it shouldn't work

cheers

---

### Post by d4nnyt on 2008-12-13
I can't get my DCP-120c to install properly on xubuntu intrepid. I have followed the instructions carefully and repeated over 10 times! 

The printer appears to be installed but when I try to print a test page it hangs on "processing" and the print job manager says "Printer MFC-210C may not be connected.".

When I installed; I got this;

```
d4nnyt@d4nnyt-desktop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
(Reading database ... 198673 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.2-3 (using cupswrapperMFC210C-1.0.2-3.i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.2-3) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 


```

"lpadmin: The printer or class could not be found." - Does that have anything to do with why it wont work?

Cheers,
Danny

---

### Post by d4nnyt on 2008-12-17
The install is still the same but I managed to get the printer to print by terminal;

```
sudo chmod a+rwx /dev/usb*
```

Don't know what it means, but it prints after I type this in.

When I restart the computer it no longer prints and I have to use the same fix again.

With this knowledge does anyone know a complete fix or how to make this permanent?

Regards,
Danny

---

### Post by Roger Mudd on 2008-12-20
Had some problems getting my DCP-7020 to print under 64-Bit Intrepid. Had to  create some symbolic links as described by the [FAQ]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142"):

```
The reference directories for 32 bit applications have changed on the 64 bit version of Ubuntu7.10.
If your version shows the following files after the installation, you will have to make symbolic links for them under /usr/lib32.

Example of the command (Issue the command as a superuser);
ln -s /usr/lib/libbrcomplpr2.so /usr/lib32/libbrcomplpr2.so

List of files required to make symbolic links

    /usr/lib/libbrcompij2.so
    /usr/lib/libbrcompij2.so.1
    /usr/lib/libbrcompij2.so.1.0
    /usr/lib/libbrcompij2.so.1.0.2

    /usr/lib/libbrcompij.so.1
    /usr/lib/libbrcompij.so.1.0
    /usr/lib/libbrcompij.so.1.0.4

    /usr/lib/libbrcomplpr.so

    /usr/lib/libbrcomplpr2.so

    /usr/lib/libbrcompcl1.so
    /usr/lib/libbrcompcl1.so.1
    /usr/lib/libbrcompcl1.so.1.0
    /usr/lib/libbrcompcl1.so.1.0.0
```

Seems to be working now.

---

### Post by ambiogas on 2008-12-21
deleted

---

### Post by salviablue on 2008-12-24
Hi, not quite sure on the exact relevance to this thread but by following instructions here I have managed to get my DCP-135c working on Hardy, mostly. I cant seem to print off anything where I set the paper as "Brother premium Glossy photo paper" or "other photo paper". According to ubuntu, the info gets sent to the printer ok and is not showing as queued in the printer spool, the printer shows "receiving data" for a few minutes, makes a few noises, then stops doing anything and says "data remaining".
  According to the destructions, "Print data is left in the machine's memory. Re-start printing from your computer."
 But doing as suggested in the manual gets the printer stuck in "receiving data"?

 It prints fine if I select normal paper (the default selection for paper type)?

---

### Post by billgoldberg on 2008-12-29
Just letting people know that on eeebuntu 8.04 I had to manually reconfigure my printer in the cups webinterface.

---

### Post by Cal55 on 2008-12-29
Just to say thanks to the OP:KS.  This worked for a DCP-350C, on Hardy 8.04 with the addition of the link to the Scanner permissions fixed from sub-post #160.

Cheers
Cal

---

### Post by tom-japan on 2009-01-02
This was an excellent tutorial. It works perfectly for DCP-9040CN model (bought in Japan).

Printer and scanner working via usb and network.

Prior to finding this tutorial, I found that the cups "MFC-9420CN BR-Script3" and cups "HL-4000CN Foomatic/Postscript (recommended)" worked equally when printing, the colors seemed a bit off and light though.

---

### Post by wxturtle on 2009-01-06
Hi all,

Upgraded from 8.04 to 8.10 and it broke my MFC210 installation.  Tried using this help to get it reinstalled but these are the messages I have received.

> xxx@DESKTOP:~/Desktop$ sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb(Reading database ... 146310 files and directories currently installed.)
Preparing to replace mfc210clpr 1.0.2-1 (using mfc210clpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc210clpr ...
Setting up mfc210clpr (1.0.2-1) ...
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so': File exists

> xxx@DESKTOP:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
(Reading database ... 146310 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.2-3 (using cupswrapperMFC210C-1.0.2-3.i386.deb) ...
lpadmin: Unable to connect to server: Connection refused
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.2-3) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
lpinfo: Unable to connect to server: Connection refused
lpinfo: Unable to connect to server: Connection refused
lpinfo: Unable to connect to server: Connection refused
lpadmin: Unable to connect to server: Connection refused


Any idea?

---

### Post by neoroses on 2009-01-06
brilliant howto mate one little thing when editing the rules text for the scanner my file was ```
/etc/udev/rules.d/45-libmtp8.rules
```

not

```
/etc/udev/rules.d/45-libsane.rules
```

just a little help if anyone was stumped as to why the file was empty

safe

---

### Post by irockonguitar on 2009-01-11
> **neoroses said:**
> brilliant howto mate one little thing when editing the rules text for the scanner my file was ```
/etc/udev/rules.d/45-libmtp8.rules
```

not

```
/etc/udev/rules.d/45-libsane.rules
```

just a little help if anyone was stumped as to why the file was empty

safe


Thank you! I was certainly stumped by the empty file. However, I still get the I/O error even after editing that step. :( Then again, my printer keeps giving me the "not connected...retry in 30 seconds error. So maybe that's my problem. Anybody have any ideas?

EDIT: When I go to [http://localhost:631](http://localhost:631), my printer IS listed, and it gives me this error: "No %%Pages: comment in header!" What does this mean, and what can I do to fix it?

---

### Post by irockonguitar on 2009-01-13
I can hardly believe this, but I just found a German forum ( [http://www.turboprint.de/support/viewtopic.php?t=431&sid=45b7a7e373d026a8dc1ece945992bd18](http://www.turboprint.de/support/viewtopic.php?t=431&sid=45b7a7e373d026a8dc1ece945992bd18) ) and used an online translator, to figure out how to solve my problem. 

sudo chmod 700 /usr/lib/cups/backend/usb


Being a complete noob, I'm not entirely sure what the above line even means, but I typed it in my terminal, and then opened an Office document and said "print," and sure enough, it did! I hope this helps someone else, and if anybody could possibly explain to me why this worked, that'd be great, too.

Cheers

---

### Post by themagicmanfromtrent on 2009-01-25
FANTASTIC. Up and running in seconds (DCP-150C). Great How To.

Thanks

---

### Post by bayvista on 2009-01-25
Hi Guys,

Great Howto

I am thinking of buying a Brother All-in-one. Can I suggest that we create a 'Sticky' for people to enter their Model No. (I don't know how to do this). It would help intending buyers see what works

---

### Post by bayvista on 2009-02-03
Just bought and installed a DCP-165C All-in-one using this How To on Intrepid 8.10. Fantastic. Thanks to the Author. Had to use the Scanner Patch mentioned around 160.

:p  :p  :p

---

### Post by RavanH on 2009-02-09
Hi,

Thanks for this extensive how-to. I have posted on this thread before because I could not get my DCP-115C working on Hardy AMD64 but now on a clean Intrepid 64bit install, I managed to get the printer going with this step-by-step :)

One problem remains: scanning will not work. I tried to complete step 6 from the scanner instructions:
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
``` but I have no file called 45-libsane.rules !!!

Another poster suggested ```
sudo gedit /etc/udev/rules.d/45-libmtp8.rules
``` but I find only rules belonging to GROUP="audio" in this file and hesitate to put the lines ```
# Brother DCP-115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner"
``` in there...

Can anyone please advise?

---

### Post by PhoenixDream on 2009-02-10
Thank you very much, after a bit of learning and finding my way round, I have success!

Cheers!

---

### Post by bayvista on 2009-02-12
Hi,

My Brother DCP-165C all-in-one worked fine until this morning, When I send anything to print, it sits there for about 5 minutes, then spits out a blank page. Same applies to a Test Page.

Checked Printer under Windows and works OK so I guess I have a driver problem.

Checked the CUPS page and everything looks normal.

Any suggestions?

---

### Post by TopEnder on 2009-02-13
> **bayvista said:**
> Hi,

My Brother DCP-165C all-in-one worked fine until this morning, When I send anything to print, it sits there for about 5 minutes, then spits out a blank page. Same applies to a Test Page.

Checked Printer under Windows and works OK so I guess I have a driver problem.

Checked the CUPS page and everything looks normal.

Any suggestions?
The last time I looked in 8.10 Synaptic Package Manager there were no drivers listed for the Brother DCP-165C but you may want to check I am on 8.04 at the moment if no drivers in Synaptic Package Manager you may withe to check out the Brother site: [http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/) it worked for me with installing the Brother DCP-150C Printer & Scanner on 32bit 8.10. let the forum know it you could install.  TopEnder

---

### Post by bayvista on 2009-02-13
Sorry. I should have said that I installed the driver following the instructions in this thread. It worked just fine for 2 weeks then suddenly died. I suspect this was due to an automatic update, but I have no idea how to nail it.

If no other suggestions, I'll try the Brother page.

---

### Post by bayvista on 2009-02-14
OK I seemed to have solved this problem. By reading the 'Howto' again after Step 9. If  unsuccessful, go back to Step 7 which I did. After reinstalling the LPR driver and CUPS driver, everything is back to normal??? WHY???

---

### Post by deevus on 2009-02-14
Great HOWTO. Just set up a DCP150C networked from Windoze for my mother.

Thanks.

---

### Post by mriendea on 2009-02-15
This worked fine for the Brother MFC-7220 on Ubuntu 8.10 Server AMD_64.

---

### Post by billgoldberg on 2009-02-28
I used this tutorial on Ubuntu 8.04 and everything worked fine.

On 8.10 however, when setting up the scanner, there is no

45-libsane.rules files, nor anything similar in the directory.

I tried making it myself, but that just gave an I/O error.

Any advice?

---

### Post by irockonguitar on 2009-02-28
> **billgoldberg said:**
> I used this tutorial on Ubuntu 8.04 and everything worked fine.

On 8.10 however, when setting up the scanner, there is no

45-libsane.rules files, nor anything similar in the directory.

I tried making it myself, but that just gave an I/O error.

Any advice?


I used this fellow's advice:

> **neoroses said:**
> brilliant howto mate one little thing when editing the rules text for the scanner my file was ```
/etc/udev/rules.d/45-libmtp8.rules
```

not

```
/etc/udev/rules.d/45-libsane.rules
```

just a little help if anyone was stumped as to why the file was empty

safe

---

### Post by luctor on 2009-03-04
For the scanner to work in jaunty I had to edit line 52 in 
```
/lib/udev/rules.d/50-udev-default.rules
```
```
lsusb 
Bus 001 Device 005: ID 04f9:01a9 Brother Industries, Ltd DCP-330C

```
```
sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x01a9) at libusb:001:005
 # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```
```
scanimage -L
device `brother2:bus2;dev1' is a Brother DCP-330C USB scanner

```

---

### Post by Andavane on 2009-03-04
> **BoardDWorld said:**
> Please note this is my first How-To.....

[COLOR="Red"]Step 6:[/COLOR]
In Terminal type the following:

Ubuntu:
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
.......[/SIZE]
I only get a blank page, as shown hereunder, so can't see how to get at the file I'm supposed to open:

What do I do to open it?

Regards
John

---

### Post by TopEnder on 2009-03-04
> **Andavane said:**
> I only get a blank page, as shown hereunder, so can't see how to get at the file I'm supposed to open:

What do I do to open it?

Regards
John
G'Day,  I don't beleive you need to use: /etc/udev/rules.d/45-libsane.rules

For the scanner you could try the following:
What I have set out below works on Ubuntu 8.04 64bit and Ubuntu 8.10 32 bit for a Brother DCP-150C it has been used by other forum member for other Brother scanners models.

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.

Code:
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules

2. Edit "0664" to "0666" in "USB devices" section.

Before the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

After the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

3. Save file

4. Restart the system.

&#65279;To get the scan-key-tool to start automatically at Ubuntu boot by default.

Install: sane-utils if not already installed (it's in Synaptic Package Manager)

Add the brscan-skey command to your startup program.

System -> Preference -> Sessions -> Startup Programs -> New
Enter brscan-skey in:
Name: and
Command:
Comment: Enter what you want to call your printer/scanner

Press OK and enable the entry.

If you get an error with Xsane close it down open it up again and try again, some times it will work, also try using the Scanner Control panel (using SCAN / up butter (scan to file) / OK / Start / Mono or Colour. It should save the file in your Home Folder/brscan.

The Brother Web Page has a lot of useful information including most of the above. If you have any problems then feel free to PM me. TopEnder

---

### Post by Andavane on 2009-03-04
> **TopEnder said:**
> G'Day,  I don't beleive you need to use: /etc/udev/rules.d/45-libsane.rules

For the scanner you could try the following:
What I have set out below works on Ubuntu 8.04 64bit and Ubuntu 8.10 32 bit for a Brother DCP-150C it has been used by other forum member for other Brother scanners models.

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.

Code:
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules

2. Edit "0664" to "0666" in "USB devices" section.

Before the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

After the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

3. Save file

4. Restart the system.

&#65279;To get the scan-key-tool to start automatically ...

Hiya mate,
Well that's my problem: when I type: 

"gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules"

I can't see a file to edit ;)

The attached is what I see!

Regs,

John

---

### Post by billgoldberg on 2009-03-04
> **TopEnder said:**
> G'Day,  I don't beleive you need to use: /etc/udev/rules.d/45-libsane.rules

For the scanner you could try the following:
What I have set out below works on Ubuntu 8.04 64bit and Ubuntu 8.10 32 bit for a Brother DCP-150C it has been used by other forum member for other Brother scanners models.

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.

Code:
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules

2. Edit "0664" to "0666" in "USB devices" section.

Before the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

After the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

3. Save file

4. Restart the system.

&#65279;To get the scan-key-tool to start automatically at Ubuntu boot by default.

Install: sane-utils if not already installed (it's in Synaptic Package Manager)

Add the brscan-skey command to your startup program.

System -> Preference -> Sessions -> Startup Programs -> New
Enter brscan-skey in:
Name: and
Command:
Comment: Enter what you want to call your printer/scanner

Press OK and enable the entry.

If you get an error with Xsane close it down open it again and try some tomes it will work, also try using the Scanner Control panel (using SCAN / up butter (scan to file) / OK / Start / Mono or Colour. It should save the file in Home Folder/brscan.

The Brother Web Page has a lot of useful information including most of the above. If you have any problems then feel free to PM me. TopEnder

Thanks, this worked for me.

The other solution didn't.

---

### Post by Andavane on 2009-03-04
> **billgoldberg said:**
> Thanks, this worked for me.

The other solution didn't.

Yes but how do you edit this file, when all you can see is a blank screen with the file name at the top? i.e. how do you get the textof the file up in front of you in order to edit it?

I don't understand why I can't navigate physically to the location and open it from there.

John

---

### Post by Andavane on 2009-03-04
I got there!

I made a launcher with

"gksudo nautilus" in the taskbar.

Then used the window it opened (after typing in password), navigated to the required file, made the alteration, saved then exited.

It seems clearer now.

Regs

John

---

### Post by visciousirene on 2009-03-05
Dear all or the great person who wrote the how to...
I did all of that but when getting to Step 6:
In Terminal type the following:

Ubuntu:
Code:

sudo gedit /etc/udev/rules.d/45-libsane.rules

The documents 45-libsane is totally empty!!!

What do I do now??

Cheesr in advance

Irene

---

### Post by TopEnder on 2009-03-05
Irene,

If you are useing Hardy 8.04 or Intrepid 8.10 I dont beleive you need to uses sudo gedit /etc/udev/rules.d/45-libsane.rules.  Have a look above at my post 201 and use it and hopefully you will be up an scanning in no time.  TopEnder

---

### Post by Andavane on 2009-03-06
> **visciousirene said:**
> Dear all or the great person who wrote the how to...
I did all of that but when getting to Step 6:
In Terminal type the following:

Ubuntu:
Code:

sudo gedit /etc/udev/rules.d/45-libsane.rules

The documents 45-libsane is totally empty!!!

What do I do now??

Cheesr in advance

Irene

On this machine, running Intrepid, there is no such file as 45-libsane.rules  in that location.
But there is one called "45-libmtp8.rules"; I have a feeling I read somewhere that that is the file which is needed.

Rgs,

John

---

### Post by visciousirene on 2009-03-06
Hello,

Sorry I didn't give much details, I am running Hardy Heron, the printer is a brother dcp150-c, I have tried what is said in post 201 but to no avail, in fact, after that the printer is not recognised either!!!
So I went back to initial state.
Thanks
irene

---

### Post by visciousirene on 2009-03-06
NB Hardy Heron 32 bit

---

### Post by visciousirene on 2009-03-06
sudo gedit /etc/udev/rules.d/45-libmtp8.rules

This directory is also empty, at least on my machine, Ubuntu 8.04 32 bit... thanks anyways

---

### Post by Andavane on 2009-03-06
> **visciousirene said:**
> sudo gedit /etc/udev/rules.d/45-libmtp8.rules

This directory is also empty, at least on my machine, Ubuntu 8.04 32 bit... thanks anyways
Irene, I went and looked on my laptop which has 8.04 Hardy, the nearest files go from:
"... 40-basic-permissions.rules ~~~ 40-permissions.rules ~~~ 45-fuse.rules ~~~ 45-linmtp7.rules..."
There is no "45-libmtp8.rules".

On my other machine (Intrepid 8.10) we have, in the same directory,
"... libmtp8.rules..." directly in the udev directory; but there is no "45" in front of the name.

I reckon that these files must change according to distro.
Sometimes they are the same, sometimes a bit of research is needed, I should imagine.

Regards

John

---

### Post by blueyelabs on 2009-03-07
Worked brilliantly for printing, but alas, scanning is so far a no-go. Xsane doesn't recognise the printer for some absurd reason...
Using a brother MFC5860CN on Ubuntu64. What's odd is that last time I followed this guide, it worked ferpectly on Ubuntu32...
Great guide though!

---

### Post by desperado666 on 2009-03-07
Why not just using 

System - Administration - Users and groups- User rights - Use scanner ?

---

### Post by altonbr on 2009-03-16
The scanner fix for Brother MFC-8440 doesn't work for Ubuntu 9.04 Jaunty because /etc/udev/rules.d/45-libsane.rules doesn't exist! MFC-8440 requires brscan, not brscan2.

Any ideas?

---

### Post by luctor on 2009-03-16
You need to edit 
```
/lib/udev/rules.d/50-udev-default.rules in jaunty
```

see my post at 
[http://ubuntuforums.org/showpost.php?p=6834677&postcount=198](http://ubuntuforums.org/showpost.php?p=6834677&postcount=198)

---

### Post by gandalf2000 on 2009-03-20
Thanks for the original guide.  It worked well for my DCP-560CN to get the printer working on the network.  But I had to go back to the Brother site for the scanner.  However, all is well .........at the moment.

---

### Post by Quintasan on 2009-03-28
> **luctor said:**
> You need to edit 
```
/lib/udev/rules.d/50-udev-default.rules in jaunty
```

see my post at 
[http://ubuntuforums.org/showpost.php?p=6834677&postcount=198](http://ubuntuforums.org/showpost.php?p=6834677&postcount=198)

I think line 53, and what did you change exacly cause the line is:
```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"
``` in mine case.

I also added:
```
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01e4", MODE="0666", GROUP="scanner", ENV{libsane_matched}="yes"
```
to
```
/lib/udev/rules.d/40-libsane-extras.rules
```
but it didn't help

---

### Post by MixMastaYoda on 2009-03-30
Great step by step guide! However, my printer all of a sudden doesn't work?!

I installed it less than 30 minutes ago! It printed the test page, it even printed two documents. 

I restarted and tried printing something else and I get a message "printer may not be connected". I know its connected because the scanner works great...printing not so much.

I also noticed ubuntu installed the same printer after I had restarted so I have two icons of the same printer but neither work?

Any suggestions to fixing this? I followed the guide over and over again but no luck :( 

Is there a way to just remove all the printers present and all the settings related to it with out the fresh install?

Thanks in advance!

---

### Post by bayvista on 2009-03-30
Yes. I had a similar problem. I think I fixed it by following the notes around Step 9. Try this.

---

### Post by djbon2112 on 2009-04-06
Hello all. I'm trying to get my printer (DCP-120C) working over the network. It is hosted on a Windows XP machine, and I'm using Ubuntu 9.04 "Jaunty" beta x86_64. I've installed the drivers and followed the OP to the letter, and I see the printer in my CUPS page, but when I go to print a test page to it it says "Pending", then the page refreshes and I see "Stopped", with nothing appearing on the printer. Any suggestions?

---

### Post by BobSongs on 2009-04-08
Greetings!

I'm an Ubuntu user and I once created a tutorial on how to install the MFC210c.

While this is not directly related to "installing" a Brother MFC printer on an Ubuntu box, I suggest adding the following link directly in the tutorial as a courtesy service for MFC users.

**[The Link]("http://www.wisebread.com/how-to-refill-an-ink-cartridge-with-a-small-piece-of-tape")**

This link points to a blog that Brother printer users would find indispensable when our cartridges run out of ink (apparently).

Half-way through a project where time was of the essence, the printer suddenly declared there was no black ink.

:eek:

The cartridge had more than enough ink to complete the job. There wasn't time to run off to the store to replace it. The link provided above helped get the job done. The final required pages printed beautifully.

Do not throw out "almost finished" cartridges. Save yourself time and money.

---

### Post by Jose Catre-Vandis on 2009-04-08
> **BobSongs said:**
> Greetings!

I'm an Ubuntu user and I once created a tutorial on how to install the MFC210c.

While this is not directly related to "installing" a Brother MFC printer on an Ubuntu box, I suggest adding the following link directly in the tutorial as a courtesy service for MFC users.

**[The Link]("http://www.wisebread.com/how-to-refill-an-ink-cartridge-with-a-small-piece-of-tape")**

This link points to a blog that Brother printer users would find indispensable when our cartridges run out of ink (apparently).

Half-way through a project where time was of the essence, the printer suddenly declared there was no black ink.

:eek:

The cartridge had more than enough ink to complete the job. There wasn't time to run off to the store to replace it. The link provided above helped get the job done. The final required pages printed beautifully.

Do not throw out "almost finished" cartridges. Save yourself time and money.

Took a fair bit of searching to find out "exactly" what to do. These two direct links to extra life for your brother print cartridges should help:

[http://journal.drfaulken.com/trick-your-brother-inkjet-into-working-when-an-ink-cartridge-runs-dry/](http://journal.drfaulken.com/trick-your-brother-inkjet-into-working-when-an-ink-cartridge-runs-dry/)

[http://www.fixyourownprinter.com/forums/inkjet/15942#1](http://www.fixyourownprinter.com/forums/inkjet/15942#1)

---

### Post by fishnchips on 2009-04-08
solved

---

### Post by fishnchips on 2009-04-08
> **TopEnder said:**
> G'Day,  I don't beleive you need to use: /etc/udev/rules.d/45-libsane.rules

For the scanner you could try the following:
What I have set out below works on Ubuntu 8.04 64bit and Ubuntu 8.10 32 bit for a Brother DCP-150C it has been used by other forum member for other Brother scanners models.

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.

Code:
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules

2. Edit "0664" to "0666" in "USB devices" section.

Before the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

After the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

3. Save file

4. Restart the system.

&#65279;To get the scan-key-tool to start automatically at Ubuntu boot by default.

Install: sane-utils if not already installed (it's in Synaptic Package Manager)

Add the brscan-skey command to your startup program.

System -> Preference -> Sessions -> Startup Programs -> New
Enter brscan-skey in:
Name: and
Command:
Comment: Enter what you want to call your printer/scanner

Press OK and enable the entry.

If you get an error with Xsane close it down open it again and try some tomes it will work, also try using the Scanner Control panel (using SCAN / up butter (scan to file) / OK / Start / Mono or Colour. It should save the file in Home Folder/brscan.

The Brother Web Page has a lot of useful information including most of the above. If you have any problems then feel free to PM me. TopEnder

wow thanks for the write up...u saved me :)

---

### Post by BobSongs on 2009-04-09
> **Jose Catre-Vandis said:**
> <snip>Took a fair bit of searching to find out "exactly" what to do.</snip>
Sorry about that. When you're under pressure reading a long article that spends more time trashing **Brother** than explaining what to do is rather annoying. But the conclusion is what I was after.

:)

I'm sure there are quite a number of articles on the web that help out with **Brother** cartridges. Thanks for the extra links. Since **Brother** has a variety of cartridge shapes/sizes/etc., no one article solves the issue clearly and adequately. However, I still think a link to one or more of these blogs would be useful to the Ubuntu community, regardless which blog.

I added that link to my old thread.

---

### Post by somking95 on 2009-04-14
thanks for the great how-to

---

### Post by solar2 on 2009-04-14
My solution to only being able to use a scanner as root in Jaunty:
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 002 Device 002: ID 04f9:0182 Brother Industries, Ltd Composite Device
or
sudo xsane
The xsane top panel might say something different, like: xsane 0.996 DCP-7010:bus3;dev2

sudo pcmanfm
navegate to /dev/bus/usb/002/002
(You might want to try  /dev/bus/usb/003/002 as well if this bus no. confusion exists)
Right click on the mouse - properties - permissions
Allow Run for Group and Other Users.
After rebooting, we can now scan as normal users

Cheers
Jamie

---

### Post by linuxonbute on 2009-04-16
I have Intrepid on my laptop and have just bought a Brother DCP-585CW and 

the instructions here for printing worked fine. I have it set up as a wireless 

printer and had to do the [http://localhost:631](http://localhost:631) bit and modify the printer 

settings as it had been set as being connected via USB.

The scanning worked after I followed the instructions on the Brother site.


Hope this helps anyone with the same printer.

---

### Post by fdgwjames on 2009-04-20
> **solar2 said:**
> My solution to only being able to use a scanner as root in Jaunty:
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 002 Device 002: ID 04f9:0182 Brother Industries, Ltd Composite Device
or
sudo xsane
The xsane top panel might say something different, like: xsane 0.996 DCP-7010:bus3;dev2

sudo pcmanfm
navegate to /dev/bus/usb/002/002
(You might want to try  /dev/bus/usb/003/002 as well if this bus no. confusion exists)
Right click on the mouse - properties - permissions
Allow Run for Group and Other Users.
After rebooting, we can now scan as normal users

Cheers
Jamie

Thanks for the clue: I ran "sudo xsane"  and then could scan. It's  a good idea though somewhat  unusual. I suppose there must be a bug in 9.04. In anycase, that was the only way out. Thanks again, that will avoid my going back to 8.10!.

---

### Post by dazzlindonna on 2009-04-26
By combining this thread with an old thread, I was able to figure out how to fix the xsane only running as root problem.  Since I don't have pcmanfm, I did the following:

Ran in terminal:

```
lsusb 
```

(My scanner/printer was listed as 002/004)

Then ran this:

```
sudo chmod a+w /dev/bus/usb/002/004
```

That fixed it for good.

---

### Post by arnesu on 2009-04-26
I have just installed ubuntu 9.04 and the scanner DCP-117C didn't work. The printer works after installing the driver DCP-110C.

In Janunty 9.04, the file /etc/udev/rules.d/45-libsane.rules does not exist, so I had to do as follows:
1) Install the driver brscan2-0.2.4-0

2) Install brscan-skey-0.2.1-.1

3) Check bus and device with  lsusb
Bus 001 Device 005: ID 04f9:018e Brother Industries, Ltd DCP-117C

4) Go to /dev/bus/usb/001/005

5) Change the rights for file: device 005. (sudo nautilus in terminal, go to the file in nautilus as root user and right click the file) Allow  group and other users

6) Go to sudo gedit /lib/udev/rules.d/ and find line 52
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"

7) Add the line:
#Brother DCP-117C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018e", MODE="664", GROUP="scanner"

8) Reboot the pc and the scanner works.

:-)

---

### Post by anonymous_user on 2009-04-26
Thanks dazzlindonna; that helped me.

---

### Post by irockonguitar on 2009-04-26
> **dazzlindonna said:**
> By combining this thread with an old thread, I was able to figure out how to fix the xsane only running as root problem.  Since I don't have pcmanfm, I did the following:

Ran in terminal:

```
lsusb 
```

(My scanner/printer was listed as 002/004)

Then ran this:

```
sudo chmod a+w /dev/bus/usb/002/004
```

That fixed it for good.

Thank you so much!! This finally fixed my scanner problem, too. For the printer I had to use

```
sudo chmod 700 /usr/lib/cups/backend/usb 
```

but every time I install updates, I have to run this command again in order to print, so I imagine I will have to do the same for the scanner.
But oh well, at least it works. Thanks!

---

### Post by rohan1 on 2009-05-05
> **linuxonbute said:**
> I have Intrepid on my laptop and have just bought a Brother DCP-585CW and 

the instructions here for printing worked fine. I have it set up as a wireless 

printer and had to do the [http://localhost:631](http://localhost:631) bit and modify the printer 

settings as it had been set as being connected via USB.

The scanning worked after I followed the instructions on the Brother site.


Hope this helps anyone with the same printer.
Hi

I too have the same brother printer (dcp 585cw) connected to hardy heron via usb...however, although I can print pdf and gedit files, I am unable to print open office files..also, how does one connect to the printer wirelessly...have already downloaded the required files but cannot find info regarding the wireless settings needed on local host..

Thanks in advance

---

### Post by iceman198 on 2009-05-06
BoardD

Thanks so much for this post!  I haven't been able to get my mfc210c to work with my Ubuntu for a few months now.  I have my printer actually hooked up to my Windows XP box and have been trying to get it networked through my ubuntu laptop.  Thanks to your post, it works like a charm networked through the XP box!

Thanks again!

iceman198

---

### Post by daileyad on 2009-05-08
Okay, I need some serious help as I know nothing about all this.  I have followed the instructions in post #1 to try to get my Brother MFC-210c working.  I have made it all the way through the instructions to step #11 and everything seems to be showing up correctly.  My current Device Uri is listed as usb:/dev/usb/lp0

The problem is, my printer is not hooked directly up to my computer through the usb.  It is attached to our wireless network at MSHOME/FAMILY/Brother%20Printer.  I have no idea how to get from the last step where it sets it up as a usb local printer to my actual network.

Please, can someone help me with instructions for a dummy?

---

### Post by mousestalker on 2009-05-08
> **daileyad said:**
> Okay, I need some serious help as I know nothing about all this.  I have followed the instructions in post #1 to try to get my Brother MFC-210c working.  I have made it all the way through the instructions to step #11 and everything seems to be showing up correctly.  My current Device Uri is listed as usb:/dev/usb/lp0

The problem is, my printer is not hooked directly up to my computer through the usb.  It is attached to our wireless network at MSHOME/FAMILY/Brother%20Printer.  I have no idea how to get from the last step where it sets it up as a usb local printer to my actual network.

Please, can someone help me with instructions for a dummy?

I have a similar lack of skills, so take the following with many, many grains of salt.

If you know your numeric URI, you might try reinstalling the printer as a network printer using it. The URI for my (wired) networked Brother printer on my system is: socket://192.168.0.100:9100, so if you can find a similar number in your printer's documentation, you might try that.

---

### Post by linooks on 2009-05-08
Hi

 I use a DCP-135C on Ubuntu 9.04 and have fixed the usb-problem on scanning by editing the file **/lib/udev/rules.d/50-udev-default.rules**.
 
 Edit this entry:

 ```
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"
```into:
 [FONT=monospace]
[/FONT]```
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"
``` Then perform:
 [FONT=monospace]
[/FONT]```
sudo /etc/init.d/udev restart 
``` That's it.
 
 Found on the german ubuntu wiki: 
 
 [http://wiki.ubuntuusers.de/Brother/Scanner](http://wiki.ubuntuusers.de/Brother/Scanner)

I hope that helps.

---

### Post by abrianb on 2009-05-11
I could not get the edit of **/lib/udev/rules.d/50-udev-default.rules to work so I just opened a text editor and created a file "51-udev-default.rules that said**...
device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"            Then saved it. Then moved it to /lib/udev/rules.d
 Now my scanner works.

---

### Post by Andavane on 2009-05-11
> **abrianb said:**
> I could not get the edit of **/lib/udev/rules.d/50-udev-default.rules to work so I just opened a text editor and created a file "51-udev-default.rules that said**...
device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"            Then saved it. Then moved it to /lib/udev/rules.d
 Now my scanner works.

Care to enlighten us as to your promptings for this ? ;)

---

### Post by linooks on 2009-05-11
At 8.10 and 8.04 it's a different file to edit: it's  [B]/etc/udev/rules.d/40-basic-permissions.rules.

[/B] Different name, but same procedure.

---

### Post by abrianb on 2009-05-13
[Andavane]("http://ubuntuforums.org/member.php?u=265138") , the reasons for doing it in that fashion were as follows... 
first , it was a fresh install but in my last install I had to modify the file to get my Brother MFC240c to scan without using sudo. So I felt that editing the file should work. But after editing and booting did not work I guessed that the line of code would work since it had in the past.
Second I new that if I added a rule file with a higher number then the system would see the higher number as an override to the lower numbered files. So I tried adding the file as 51 which overrode rule 50 and after booting it worked.
I have no guesses as to why editing the file did not work I am relatively inexperienced at this. I f you have suggestions for me I would be pleased to hear them.
Thanks!

---

### Post by bela42 on 2009-05-13
Avoid Brothers printer driver at least for the MFC7820N. Since years Ubuntu was autodetecting this also if only network connected, but the "Brscript-3" driver (ppd) available for this model did only give problems. Like being unable to print from Firefox, like displaced print output from Open Office.

Usually I did install this model as generic PCL5 network printer and got proper results.

Eventually in Jaunty it seems the hardware detection does also avoid Brothers "BRScript" and selects a generic foomatic postscript ppd.

Great news, as this model does work out of the box now, no need to install Brothers drivers.

To use the scanner, you will need to install brothers scanner driver, of course, but that one did always work OK for me.

---

### Post by bayvista on 2009-05-19
How to I admin my Brother DCP-165C? There is no entry under "System - Administration".

Solved: Go to System/Administration/Printing. Right click on the DCP165C and select "Properties"

Thanks.

---

### Post by TopEnder on 2009-05-19
> **bayvista said:**
> How to I admin my Brother DCP-165C? There is no entry under "System - Administration".
bayvista,   Not sure what your really want to do.  Have you downloaded drivers for the DCP-165C from brother ([COLOR="Blue"]http://solutions.brother.com/linux/en_us/download_prn.html[/COLOR]) as I do not beleive there are any drivers for the DCP-165C in Ubuntu 8.10 Intrepid Ibex Synaptic Package Manager. Just post any installation problems and someone will help.  TopEnder

---

### Post by bayvista on 2009-05-21
Had some problems getting the scanner to work on my DCP-165C. Be careful when downloading the drivers from the Brother site. I accidentally downloaded the wrong driver and spent a happy couple of hours stuffing around. Once I installed the RIGHT driver, it all worked like magic!

):P ):P ):P

---

### Post by hieronymouse on 2009-06-02
I haven't checked through the whole forum to see if this was mentioned, but to get the scanner running under Jaunty (9.04), we need to follow the additional instructions in the responses at:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/217571](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/217571)

I had the problem that the udev rules file didn't exist, and then,

Quoting VPablo:

In 9.04 we must edit /lib/udev/rules.d/50-udev-default.rules and change:

# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"

to

# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"

and restart.

That worked for me.

---

### Post by newb85 on 2009-06-04
I would like to remove this message...can't find the remove button...help?

---

### Post by mgw2008 on 2009-06-06
All Brother drivers are here:
[http://solutions.brother.com/linux/en_us/download_prn.html](http://solutions.brother.com/linux/en_us/download_prn.html)
I strongly recommend to use CUPS to install the printer. Simply select install printer from the menu. No cmdline dialog needed.

Cheers mgw

---

### Post by dhaight on 2009-06-27
Thanks, Great "How To" Since I am using a networked brother 440cn printer, I simply had to delete the printer that was installed by this process and add a new networked printer. the driver was ready and waiting!

---

### Post by Skip Da Shu on 2009-06-29
> **AgentZ86 said:**
> Sorry for the delay response.

You have to consult your printer documentation or poke around with the menu buttons on the printer, and set the IP address to a static IP address on the printer, And make sure it's within the IP address range of the DHCP range of the router. In other words if the router is dishing out IP's in the lets say 192.168.0.1 thru 192.168.0.255 or so then make sure that the static IP of the printer is set to something like 192.168.0.105 or something 

Or if your router is dishing out the range in the 10.1.10.200 to 10.1.10.255 then put the printer at 10.1.10.230 or something.

Anyhow this is something you can to on the printer itself, I would not change the router to static cause then you have to set all the machines IP addresses and they won't receive one automatically from the router, so it's simple for a couple machines, but if you have a larger network that gets real old real quick.

Anyhow if you disclose your model I may be able to clarify some more.

I hope this helps.

True static IPs do not and should NOT be in the DHCP assigned IP range as you risk having two things with the same IP show up.  If the router's DHCP is set to dish out .100 thru .200 then set the printer static IP to be under 100 or over 200 (last nodes).

Assigning a constant IP to a device/machine via the router is not a static IP but a 'fixed' IP that is assigned by DHCP.  Using it this way the IP of the printer MUST be in the DHCP assigned IP range.

---

### Post by Skip Da Shu on 2009-06-29
> **bluvy said:**
> ...I've installed LPR and CUPS, my MFC 7420 is connected via USB, and when I go to [http://localhost:631/printers/](http://localhost:631/printers/) it says:

Description: MFC7420
Location:
Printer Driver: Brother MFC7420 for CUPS
Printer State: processing, accepting jobs, published.
Device URI: usb:/dev/usb/lp0
(this is set as my default printer)

The installation was successful, however when I try to print test page it says "Printer not connected; will retry in 30 seconds...".

I followed the modified how-to on page 1 including the copy for 64b.  All seemed to work well and no errors once the machine and I came to an agreement that "MFC3240C" really isn't the same as "MFC3420C".  

This is on an Intrepid v8.10 AMD_64 install. 

However when I select the 'print test page' I get the same error as above.  I confirmed the printer is physically connected to a USB port in the back of the machine.  

System->Admin-Printing shows MFC3420C there and as the default printer.  It's URI is **usb:/dev/usb/lp0**.  

In the browser going to localhost:631/printers shows the printer installed:
```
Description: MFC3420C
Location: c15-desktop printer
Printer Driver: Brother MFC-3420C CUPS v1.1
Printer State: idle, accepting jobs, published.
Device URI: usb:/dev/usb/lp0 
```

This is on my wife's machine who I'm trying to convince that she doesn't need windoze anymore.  So, getting the printer working is a bit 'politically' important despite my opinions of what she prints.

Thanx in advance, Skip

---

### Post by Docgk on 2009-06-30
Here running Jaunty 9.04 and with DCP115C - great thread helped no-end in getting the print side working. However, the scanner proved to need one more step than those above.  I still got a comms error from Xsane.  Thus the permissions problem still existed even after the above steps.

Solved as follows:

 You will need to run lsusb to identify bus and device.  In my case bus 6 and device 2 - replace as appropriate and:

sudo chmod 777 /dev/bus/usb/006/002

However, this only works until next reboot or unless the device is allocated a different device number. As a newbie can I ask how to make this a permanent fix?

Thanks



UPDATE: permanent solution found in post #247 this thread.


[COLOR=Red]In 9.04 we must edit /lib/udev/rules.d/50-udev-default.rules and change:

# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"

to

# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"

and restart.[/COLOR]

---

### Post by grrrlshapedthing on 2009-07-03
I followed your directions to install my Brother DCP-165C and everything seems to have worked far as installation goes but It's still not printing anything!

ETA: I'm using Linux Mint 6

---

### Post by grrrlshapedthing on 2009-07-03
okay so I got it to print but the alignment is all off... any ideas on how to fix that??

---

### Post by newbymick on 2009-07-15
Ok - after 2 hours of reading, copying, pasting, restarting, swearing, clicking, typing and more swearing - I finally have my printer and scanner working (dcp-115c) 

BTW - been using Linux - From FC5 to Linpus to Ubuntu (how I hated the very 1st Ubuntu) and most other flava's in between for the last 4 years and finally got a printer to work (and as a bonus - A scanner) 

Big thank you to the originator of this How To and a big thank you Docgk for the permanent solution

Footnote - just looked back at my stats - last post before this one - August 2006.  That's how much I disliked Ubuntu before 9.04 came along.  Was using mint for a long time before the creator got political about his users :(

---

### Post by ratdude747 on 2009-07-30
using ubuntu 9.04

isntalled both lpr and cups](*,)

but... after realizing i had the wrong ip address it works great :) needs a bit of fresh ink but im impressed. thank you.

---

### Post by Beatbreaker on 2009-08-01
Nice work, I still find this tutorial helpful every time i set up my Brother network printer because the mfc-7420 drivers are still not included in the printer drivers provided by default by Ubuntu.

---

### Post by ratdude747 on 2009-08-02
they REALLY need to put them in the repos or just include them. i know they are ar not open source (or are they?)... but some companies are sticks in the mud... they wont go open souce in a million years. boycotting the companies works for those who already use linux but for those who are about to jump onbard, it is discouraging. besides, you get bottom feeders like me who find nice stuff at thrift stores... since they are donated the company gets nothing off of it other than supplies. 

btw, how do you get network scanning to work? my machine uses brscan2. it is an mfc-420cn.

---

### Post by matchstich on 2009-08-14
> **TURNER said:**
> Iam using a (fresh) install of Gutsy and following your "how to" without the LPR didnt work for me, upon rolling back and trying again WITH the LPR I got the printer working....I think it might be worth leaving the part ref the LPR..

how do i roll back, i need to start all over again

thanks
ok, it works now, printer and scanner. what i did was to put 8.04 back on. was using 9.04.  and could not get it. have mfc-210c

---

### Post by ozkhalsa on 2009-08-28
Hi , guys I am breaking my head on this issue. No matter how many times i download the correct lpr file from Brother site i am always having the following error. I am following the step by step to the hilt but still getting this have done repeat of theis several times same result. Help Help , i am new to Ubuntu.


```
suprit@namindodell:~/Desktop$ sudo dpkg -i --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb
dpkg-deb: --control mfc6490cwlpr-1.1.2-2.i386.deb /var/lib/dpkg/tmp.ci
(Reading database ... 160490 files and directories currently installed.)
Unpacking mfc6490cwlpr (from mfc6490cwlpr-1.1.2-2.i386.deb) ...
dpkg-deb: --fsys-tarfile mfc6490cwlpr-1.1.2-2.i386.deb
cp: cannot stat `mfc6490cwlpr-1.1.2-2.i386.deb': No such file or directory
cd: 52: can't cd to debian/*/
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb
suprit@namindodell:~/Desktop$
```

I have done all the pre-requisites as per the brother linux help site. Infact i had installed the printer correctly in Jaunty as WUBI install , but ow with this new Jaunty install on seperate partition ( ext4) i am unable to make this work. Is my tar unpacking package corruptes , or the driver file at Brother web site is corrupted , or simply some other problem I cannot say.

Pls help Help.

---

### Post by IanW2121 on 2009-08-29
Having problems with the Scanner on my Brother MFC-8860DN

I downloaded the 'brscan2' and 'skey' drivers and installed them. 

A driver check (grep Brother) is positive.

ii  brmfc8860dnlpr                           2.0.1-1                                   Brother MFC-8860DN LPR driver
ii  brscan-skey                                0.2.1-3                                   Brother Linux scanner S-KEY tool
ii  brscan2                                      0.2.4                                      Brother Scanner Driver
ii  cupswrappermfc8860dn               2.0.1-2                                  Brother MFC8860DN CUPS wrapper driver

When running brscan-skey I get no confirmation on screen and when I run Sane I get the error "Failed to open 'brother2:bus1:dev1; Error during device I/O"

Looking at the Brother site it says I should edit /etc/udev.rules.d/45-libsane.rules but there is no such file!!??

I've had the printer working fine for some time (and it still is!!).

I also noticed while I was installing several error reports like this ....

Error: "/var/tmp/kdecache-ian" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-ian" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-ian" is owned by uid 1000 instead of uid 0.

Can this be the problem and if so what should I do about it and how??

My Op Sys is Kubuntu 9.4 (32-bit) on an Intel CPU

Thanks

---

### Post by santana99 on 2009-09-05
Hi,

I am new to Linux and looking for a solution to connect a Brother DCP-7025 scanner to Kubuntu 9.04 environment.
It works for sudo but not for the normal user. I have seen a lot of solutions for this particular problem but they all start with the assumption that you have libsane rules - files or permission rules - file in a directory called /etc/udev/rules.d. I don't have these files on my system. I loaded the packages sane and xsane and also gscan2pdf for testing purposes.

Any help would be great !!

---

### Post by aljoriz on 2009-10-10
You are a genius!!!!

I was able to made my friend's brother printer in Xubuntu 8.04

---

### Post by LarsSikstrom on 2009-10-22
I am very pleased to have found this advice for with its help I finally mangaged to install my newly bought Brother printer.Due to a misunderstanding of the instructions given in the Brother Solutions Center I have spent hours trying to understand what I did wrong. The answer was that it was necessary to install the lpr file before the cupswrapper.

Thank you very much

---

### Post by aparkes on 2009-10-27
After two days of getting the Brother MFC420CN to work, I stumbled upon this thread. I followed along and got the printer working in no time. Thank you for this wonderful how to.

---

### Post by desperado666 on 2009-10-31
For Karmic you have to do this

Create **55-libsane.rules** file in directory **/etc/udev/rules.d/** with an editor you like


```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
```

Then restart udev with
 
```
sudo /etc/init.d/udev restart 
```

---

### Post by brookie on 2009-10-31
> **desperado666 said:**
> For Karmic you have to do this

Create **55-libsane.rules** file in directory **/etc/udev/rules.d/** with an editor you like


```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
```Then restart udev with
 
```
sudo /etc/init.d/udev restart 
```


I had this up and running in Intrepid following the how to on the first page. Xsane scanner worked great. I upgraded to Karmic, and now Xsane only sees my MFC-210C scanner if I run it as sudo Xsane. 

I added the 55-libsane.rules file above but still no go. Do I need to delete the 45* rules I made before? And, how do I get Xsane to play nice without being root? 

Also, lsusb does not see the printer. Only sudo lsusb brings it up. This seems like some kind of permissions thing but I can't figure it out. Any help will be GREATLY appreciated. 
Thanks. :) 

Cheers, 
brook

---

### Post by brookie on 2009-10-31
Okay, I found a fix on post #253, thanks Docgk. My MFC-210C scanner is now working. But I have some questions about cleaning up all of this stuff now if anyone can help. 

1. Do I need the 45* and 55* rules I made in /etc/udev/rules.d/ or can I delete them? 


2. I found anther [link]("http://ubuntuforums.org/showthread.php?p=2514847&highlight=fstab#post2514847") that said to change the fstab file like: 

sudo gedit /etc/fstab

ADD:

none /proc/bus/usb usbfs auto,devmode=0666 0 0

sudo umount /proc/bus/usb
sudo mount /proc/bus/usb
sudo mknod -m 666 /dev/usbscanner c 180 48

I did that. So can I delete this after doing the stuff in post #253? 


3. And last but not least, when I edited /lib/udev/rules.d/50-udev-default.rules, the top of the file stated something like, 'do not edit this file.... it will be over written on update...'

...so will I have to redo this edit after my system gets some type of kernel update or something? 

Thanks, 
brook

---

### Post by zeiz on 2009-11-01
I created the "55-.." file and I also added my model MFC6800 (vendor=="04f9" product=="0111") to /lib/udev/rules.d/40-libsane.rules Everything works fine.

However I'm also curious how Brother could recommend editing a file to be overwritten upon relevant update?

---

### Post by amano on 2009-11-01
**Brother DCP-115C printer part in Karmic:**

1) Turn off your printer

2) Open Synaptic

3) Search for the package brother-lpr-drivers-extra and install it and all its dependencies (the dependencies should be installed automatically)

4) Turn on the printer

5) The print wizard comes up

6) It doesn't find your printer automatically 

7) Look for the manual printer list in the wizard and open the brother printer section

8) Choose the MFC-210C printer (yes, even for the DCP-115C)

9) Done.


**Brother DCP-115C scanner part in Karmic:**
1) For the scanner functionality download the brscan2 deb package from the brother homepage. Take care that it is the right packages: 32 bit or 64 - that depends on your Ubuntu version. Brscan2 is the right package for the DCP-115C, but be careful: There is another brscan package offered for other printers.

2) Install it.

3) Now you need permissions. For Karmic create the file 55-libsane.rules in the folder /etc/udev/rules.d/   > sudo gedit /etc/udev/rules.d/55-libsane.rules

An insert this stuff into the file: > # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
Don't forget to save your changes.

4) Then restart the computer (or at least restart udev > restart udev


Report back if that worked. Otherwise you will have to add some additional rules from this thread (I tried some before, but this rule finalley got my scanner to work)

---

### Post by bayvista on 2009-11-09
Thanks again. I have just installed my DCP165C into Karmic and it worked first time. Please note: you need to download the drivers from [here]("http://solutions.brother.com/linux/en_us/download_prn.html#DCP-165C"), not from the link in this HowTo.

---

### Post by Gene58 on 2009-11-10
Hey All

I have JUST started getting into this stuff and am feeling VERY stupid about now. I have tried to follw this thread on installing a MFC-440cn printer and was going pretty good (I thought) until I got to where i was to choose the print driver. I could not find MFC-440cn listed.... WHAT am I missing? PLEASE help .. want to get totally away from the windows thing

thanks

---

### Post by amano on 2009-11-13
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc440cnlpr-1.0.1-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc440cnlpr-1.0.1-1.i386.deb&lang=English_lpr)

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc440cncupswrapper-1.0.1-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc440cncupswrapper-1.0.1-1.i386.deb&lang=English_gpl)

Aren't those drivers working? Just from the link one post above yours?

---

### Post by Mark_in_Hollywood on 2009-12-09
> **amano said:**
> **Brother DCP-115C printer part in Karmic:**

1) Turn off your printer

2) Open Synaptic

3) Search for the package brother-lpr-drivers-extra and install it and all its dependencies (the dependencies should be installed automatically)

4) Turn on the printer

5) The print wizard comes up

6) It doesn't find your printer automatically 

7) Look for the manual printer list in the wizard and open the brother printer section

8) Choose the MFC-210C printer (yes, even for the DCP-115C)

9) Done.


**Brother DCP-115C scanner part in Karmic:**
1) For the scanner functionality download the brscan2 deb package from the brother homepage. Take care that it is the right packages: 32 bit or 64 - that depends on your Ubuntu version. Brscan2 is the right package for the DCP-115C, but be careful: There is another brscan package offered for other printers.

2) Install it.

3) Now you need permissions. For Karmic create the file 55-libsane.rules in the folder /etc/udev/rules.d/   

An insert this stuff into the file: 
Don't forget to save your changes.

4) Then restart the computer (or at least restart udev 

Report back if that worked. Otherwise you will have to add some additional rules from this thread (I tried some before, but this rule finalley got my scanner to work)

I have an Brother MFC-240C. I followed your instructions. XSane reports no scanner.

---

### Post by bayvista on 2009-12-21
This is a very good 'how-to'. However, the original instructions have not been updated. Please review all posts BEFORE installing as it will save you a lot of time. For example, there is another driver available for the scanner called brscan3 which you may need.

---

### Post by picklemonkey on 2009-12-21
thank you, this worked great for my Brother MFC-3360C printer!  I was worried at the end of step 11 but the additional localhost step fixed me right up

---

### Post by PartisanEntity on 2009-12-26
Anyone have instructions for installing the MFC40CW scanner in a networked environment?

I connect to the printer through wifi, so lsusb or any usb related HowTo's don't work here.

Thanks

---

### Post by jfbooth on 2009-12-29
> **amano said:**
> **Brother DCP-115C printer part in Karmic:**

1) Turn off your printer

2) Open Synaptic

3) Search for the package brother-lpr-drivers-extra and install it and all its dependencies (the dependencies should be installed automatically)

4) Turn on the printer

5) The print wizard comes up

6) It doesn't find your printer automatically 

7) Look for the manual printer list in the wizard and open the brother printer section

8) Choose the MFC-210C printer (yes, even for the DCP-115C)

9) Done.


**Brother DCP-115C scanner part in Karmic:**
1) For the scanner functionality download the brscan2 deb package from the brother homepage. Take care that it is the right packages: 32 bit or 64 - that depends on your Ubuntu version. Brscan2 is the right package for the DCP-115C, but be careful: There is another brscan package offered for other printers.

2) Install it.

3) Now you need permissions. For Karmic create the file 55-libsane.rules in the folder /etc/udev/rules.d/   

An insert this stuff into the file: 
Don't forget to save your changes.

4) Then restart the computer (or at least restart udev 


Report back if that worked. Otherwise you will have to add some additional rules from this thread (I tried some before, but this rule finalley got my scanner to work)

What if printer is not listed in the manual printer list?  Is there any way to find out if it is BEFORE doing all this?

---

### Post by jfbooth on 2009-12-29
I am hoping my MFC-7440N IS listed and I can install it to Karmic.  Maybe someone can look on their list and see if it is there b4 I install "package brother-lpr-drivers-extra and install it and all its dependencies".  Thanks in advance.

---

### Post by PartisanEntity on 2009-12-29
> **jfbooth said:**
> What if printer is not listed in the manual printer list?  Is there any way to find out if it is BEFORE doing all this?

There are three links on the Brother website, for the 3 versions of brscan and each lists which models are supported.

For example for my MFC-490CW I had to download the brscan3 package.

---

### Post by jfbooth on 2009-12-29
yes, . for my printer (MFC-7440N) I have perused all of the 'linux' brother site info.  I have researched threads here also.  I find tons of info, but since a lot of it is outdated, it is totally confusing.  I am waiting to get clear, concise procedure but I don't think that will happen.

FWIW, I can make a lot of assumptions but unanswered questions remain.  I'm still trying to figure out exactly what to download from Brother. 

Looks like 
cupswrapper driver deb 2.0.2-1 13 KB 2008.Jun.25
brscan3 32bit deb 0.2.8-1 56 KB 2009.Dec.16
scan-key-tool 32bit deb 0.2.1-3 43 KB 2009.Apr.09

but I don't know about scan-key-tool  .. what is it and do I need it?  Guess that is the first question.

Then, there are confusing prerequisites at:

welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#prereq

Just don't feel I have found the support I need to do this.

---

### Post by PartisanEntity on 2009-12-29
> **jfbooth said:**
> yes, . for my printer (MFC-7440N) I have perused all of the 'linux' brother site info.  I have researched threads here also.  I find tons of info, but since a lot of it is outdated, it is totally confusing.  I am waiting to get clear, concise procedure but I don't think that will happen.

FWIW, I can make a lot of assumptions but unanswered questions remain.  I'm still trying to figure out exactly what to download from Brother. 

Looks like 
cupswrapper driver deb 2.0.2-1 13 KB 2008.Jun.25
brscan3 32bit deb 0.2.8-1 56 KB 2009.Dec.16
scan-key-tool 32bit deb 0.2.1-3 43 KB 2009.Apr.09

but I don't know about scan-key-tool  .. what is it and do I need it?  Guess that is the first question.

Then, there are confusing prerequisites at:

welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#prereq

Just don't feel I have found the support I need to do this.

In order to avoid confusion:

a) ignore the instructions on the Brother website
b) download only the packages mentioned in the first post of this thread (but of course use brscan3 in your case)
c) scan-key-tool is not needed, I don't know what it does, but I did not install it and all is working fine

post back if you have problems with the installation.

---

### Post by jfbooth on 2009-12-29
Partisan, .. thank you for stepping up to my request. 

First problem I have is this thread says "Step 4: Download the LPR Driver and CUPS Wrapper."  At the Brother site there are two deb files for my printer:

cupswrapperMFC7440N-2.0.2-1.i386.deb
LPR driver

So I downloaded them.  So far, so good.  Then this thread says "Install the LPR Driver."

I know you said ignore their instructions but Brother says _under instructions for installing LPR driver)) it clearly says "*** If CUPS is working on your system, we recommend to use CUPS."

Does that mean EITHER/OR?  Sounds like they want me to NOT use the LPR download but use the cups download instead and if so, being this thread is outdated, I tend to go w/ Brother on this .. but I am also a Xubuntu idiot.  If I am right, this thread discusses USING the LPR driver and that is where all the confusion begins.

So far, I have downloaded cupswrapperMFC7440N-2.0.2-1.i386.deb  brmfc7440nlpr-2.0.2-1.i386.deb    and     brscan3-0.2.8-1.i386.deb (for scanner)

I have also performed "sudo apt-get install tcsh" from this thread.  Not sure what to do next.  Thread says "Step 7: Install the LPR Driver." but I am not sure that is right.

---

### Post by PartisanEntity on 2009-12-29
Well, using these instructions (i.e. the ones here in the thread) we end up with both lpr and cups, so I don't quite see what the problems is.

In Step 7 we install lpr, and in Step 9 we install cups.

---

### Post by jfbooth on 2009-12-29
I think the confusion is in reply #10.  First time in this thread that I am able to find that suggests NOT to use LPR.  I am installing to Karmic XUBUNTU 9.10.

The thread seems to instruct for installing LPR then at reply 10 is says NOT to (for my distro) if I am reading it right.  I can't find, in the thread, where to pick up from where I am at this point.

---

### Post by PartisanEntity on 2009-12-29
Okay, I just read reply #10 and you are right, you can safely ignore the step that requires the installation of lpr and head on to cups.

Although I can verify that installing both did not hurt the system (I have Ubuntu 9.10).

---

### Post by jfbooth on 2009-12-29
that did not work.  installing cups indicated I need lpr (go figure) so I installed lpr then cups and have some results but still have problems.  here is some info:

cable out of well to cable modem
ethernet modem to router
ethernet router to printer
ethernet router to linux box
wifi to xp box

xp box sees and uses printer OK

linux box .. probably messed up 'cause I tried some things intuitively.

[http://localhost:631/printers/](http://localhost:631/printers/) shows correct printer.
[http://localhost:631/printers/MFC7440N](http://localhost:631/printers/MFC7440N) shows the following:

Description:	MFC7440N
Location:	Back Room
Driver:	Brother MFC7440N for CUPS (grayscale)
Connection:	dnssd://Brother%20MFC-7440N._ipp._tcp.local/
Defaults:	job-sheets=none, none media=iso_a4_210x297mm

I do not think connection is correct .. but it could be.  Will not print test page.

MFC7440N-8  	Test Page  	anonymous  	1k  	Unknown  	pending since
Tue 29 Dec 2009 07:28:50 PM CST

cancel job.  go back to printer page .. says:
MFC7440N	MFC7440N	Back Room	Brother MFC7440N for CUPS	Paused - "Destination printer does not exist!"

According to the printer's configuration page, I can ping its IP address 1.192.168.3

Click Applications/System/Printing.  Window titled Printer Configuration Localhost shows icon of my printer with a green check mark on it.  Click on that icon and get PRINTER PROPERTIES SETTINGS which says , Printer State: Stopped.  Destination Printer Does Not Exist.  Device URI says dnssd://Brother%20MFC-7440N._ipp._tcp.local/

All options are greyed out .. change Device URI, change Make/Model, Print Test Page, Print Self-test Page, Clean Print Heads ... all greyed out.

POLICIES .. no check in box for Enabled.  Check Accepting jobs   Shared unchecked.

Will continue this tomorrow.  Any help appreciated.  Thank you.

---

### Post by jfbooth on 2009-12-30
It prints.  Somehow I had it in my head it was a network printer .. it is a local printer.  Thank those who helped me.  Will tackle scanner tomorrow.  Thank you again.

---

### Post by TheCat on 2010-01-02
I just configured my wireless HL-4070CDW for Karmic 9.10 using a combination of multiverse and the instructions in the first post.  Note that the printer was previously initialized using a Mac, so if you're just taking it out of the box YMMV.

1. Use synaptic to install brother-cups-wrapper-ac from multiverse.
2. sudo mkdir /var/spool/lpd
3. sudo mkdir /usr/share/cups/model
4. System -> Administration -> Printing -> New -> Printer
4a. Network Printer -> select the Brother printer that has a description "AppSocket/JetDirect network printer via DNS-SD" -> forward
4b. Enter description -> Apply
5. Print a test page.

---

### Post by newguyjan2010 on 2010-01-10
Hi all;

I found this thread and it partially helped, thanks to those who started / updated.  In that spirit I'm adding what I did to resolve my issue.  

My problem:  getting my Brother MFC-6800 scanner to work.

My uname -a:  Linux xxxxx-desktop 2.6.31-17-generic #54-Ubuntu

My resolution:

1)  I plugged the USB cable from the MFC-6800 into my computer

2)  lsusb showed (relevant line only)

Bus 002 Device 002:  ID 04f9:0111 Brother Industries, Ltd MFC 6800

(I believe that if you can't see the device, you need to establish why that is, before proceeding further - may be a cable issue, USB port issue, etc.)

3)  the file I then edited was

/lib/udev/rules.d/40-libsane.rules

4)  just before the end of the file, I added the following lines:

# Brother MFC-6800
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0111", ENV{libsane_matched}="yes"

This is because the other device descriptors used that syntax, in my system.  

5)  Then, in my GUI console (F7), I chose Applications --> Graphics --> XSane Image Scanner

The application scanned for, and found, my device.

At that point, you should be able to scan and save images from the device.

Hope this helps.

Best regards, all.

---

### Post by yaku85 on 2010-01-18
Hi, i have a printer/scanner BROTHER DCP 8065DN i was trying to install brscan driver but i see the page says Scanner driver does not support print server connections.
I must use the scanner with a print server (edimax), is this possible? the print fuction now work with no problem, but the scanner with xane doesnt work, it know the device but i get an error when i try to scan.
thanks...

---

### Post by _dino_ on 2010-01-25
Hi,
Thanks for providing this great HOWTO Install Brother HL-2170W on Ubuntu Desktop 9.10.  I followed your steps and everthing installed successfully, however, I still can not print Test Page.  When I hover over the printer icon, it shows message "Printer HL2170W may not be connected" and the test page will not print.  This is wireless printer and when I open Printer Properties, it says that Device URI is usb:/dev/usb/lp0.
Any idea what could be wrong and how to fix it.
Much Appreciated,
_dino_

---

### Post by cmfeeney on 2010-02-04
uh... yeah. That looks easy. <sarc/> I know it's not OS X, but for a printer install, it all seems a bit much to me.

---

### Post by burdebc on 2010-02-26
.

---

### Post by confused57 on 2010-02-27
I found this thread after using the instructions on the Brother website for installing Linux drivers, which required over an hour to get everything working...somewhat difficult navigating the website to find everything I needed.  May not help anyone, but here's basically what I did:

Prerequisites:
```
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
sudo mkdir /var/spool/lpd
```
Installed sane-utils & psutils from Synaptic...tcsh wasn't needed for my printer.

Downloaded the drivers I needed for my MFC295CN:
LPR driver:  mfc295cnlpr-1.1.2-1.i386.deb
Cupswrapper driver: mfc295cncupswrapper-1.1.2-2.i386.deb
Brscan3 32-bit: brscan3-0.2.9-1.i386.deb
Scan-key-tool 32-bit: brscan--skey-0.2.1-3.i386

Then connected & turned on the printer, cd to Desktop, where I downloaded the drivers.
Issed the following commands to install the drivers:
```
sudo dpkg -i --force-all (driver name)
```
I tried installing the cupswrapper driver first, but couldn't because the lpr driver was listed as a dependency...worked when I installed the lpr driver, then cupswrapper.

Then checked if they were installed:
```
dpkg -l | grep Brother
```

Opened Firefox: [http://localhost:631/printers](http://localhost:631/printers), which showed the printer listed.

At first, Xsane couldn't find a device, but a quick reboot remedied this.

I'm not sure if this was needed, but I found in another thread that I needed to modify permissions for a normal user in /etc/udev/rules.d/40-basic-permissions.rules(I'm using 8.04, may be different for other versions), changed the line: SUBSYSTEM=="usb"ENV{DEVTYPE}...MODE="0664" to SUBSYSTEM....MODE="0666"

The description of the printer in "Ubuntu Printers:
Description:  MFC295CN
Device URI:  usb://Brother/MFC-295CN
Make&Model:  Brother MFC-295CN CUPS

I must admit, there was some trial-and-error to finally get the printer added & working.  I think the scan-tool-key is just a command line method of scanning & isn't needed.  I can scan directly from the printer/scanner, but have to turn off Firestarter(don't really want to open the necessary port)...easier to scan using Xsane.

Installed the MFC 295CN on a 2nd pc running 8.04, which required all of about 10 minutes to get everything working.

Update:  These instructions work equally well with Ubuntu 10.04 over Linksys router network, I just put in the URI: [http://192.168.1.100:631/printers/MFC295CN](http://192.168.1.100:631/printers/MFC295CN) of the computer the printer is connected to.

---

### Post by redsoul on 2010-03-05
Omg guys, i followed the Confused57 reply and it seems that my printer is installed (it is a brother mfc-295cn) but i have this printer connected by network. And i cannot print anything anyway.it just says that printer may not be connected. Pls help, there is a way to install this ***** brother and have it to work by network???? tnx and i'm newbie so pls be simple!


OK! I SOLVED! i tnx all of u and confused57 in particular way. I followed his instruction and the printer worked. For the problem about the network i solved like this:

i went to properties of the printer and where there was the url of the printer i just put the address of the printer like this --> lpd://192.168.1.54/BINARY_P1   where obviusly that is my printer ip address. I'm sorry for my english but i hope u understand anyway. Tnx to all again..

---

### Post by tommynz1975 on 2010-03-06
Much thanks for this.

After a clear sober head I was able to follow the instructions. I am confident now that when sister gets her A3 printer that it will install painlessly


due to brother changing stuff on their web site could you please update the links

Main linux page
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)[

printer drivers lpr and cups

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

scanner drivers

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

Also on the 15th of the month, I guess usa time. the site will have an outage for server upgrade or some such fluff

---

### Post by saabaru on 2010-03-10
BoardDworld, THANK YOU for your original writeup! I was racking my brain trying to figure out how to get this working. I followed your steps/instructions you posted and I CAN PRINT! thank you again! 

*ps- using 9.10. THANKS!!!

---

### Post by Beowulf.1000 on 2010-03-11
And we wonder why people avoid linux, sigh. I love linux, but I tell you I can easily return to Windows because of what should be basic simple stuff that steals time and causes headaches. Sigh. Unbelievable. I recall in Ubuntu  6  I easily added a printer, now with 9.10 I can not figure out whatsoever how to add the same damn printer, nothing has changed except ubuntu.

---

### Post by TopEnder on 2010-03-11
G'Day Beowulf.1000,  It's called Ubuntu Evolution, yes they do change a lot between release whether to keep us on the ball or someone has a hidden agenda, Who knows, at least we have to do a lot of reading. TopEnder

---

### Post by dowlicd on 2010-04-12
i have a brother mfc-210c printer. i ran an installation of the driver from the brother site, but i got this error in my terminal. 

[B]The following NEW packages will be installed:
  csh
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 253kB of archives.
After this operation, 414kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe csh 20070713-2ubuntu1 [253kB]
Fetched 253kB in 1s (146kB/s)
Selecting previously deselected package csh.
(Reading database ... 273156 files and directories currently installed.)
Unpacking csh (from .../csh_20070713-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up cupswrappermfc210c (1.0.2-3) ...
touch: cannot touch `/usr/share/cups/model/brmfc210c_cups.ppd': No such file or directory
/usr/share/cups/model/brmfc210c_cups.ppd: No such file or directory.
dpkg: error processing cupswrappermfc210c (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up csh (20070713-2ubuntu1) ...
update-alternatives: using /bin/bsd-csh to provide /bin/csh (csh) in auto mode.

Errors were encountered while processing:
 cupswrappermfc210c
E: Sub-process /usr/bin/dpkg returned an error code (1)


[/B]also, everytime i get notifications from the update manager and it automatically installs new updates/securities, etc. i always get the cupswrapper error and that all updates were not completed successfully b/c of this cupswrapper situation.  HELP PLEASE.

---

### Post by abrianb on 2010-04-13
Don't use the brother web site drivers . In it's stead click on System>Administration>Synaptic package manager. In synaptic's search  type "Brother".
You will find a package named "Brother-cups-wrapper-extra" and one named "Brother-lpr-drivers-extra". Click on the Box to mark them for application. Then click on the apply box. Follow along the prompts, enter your password where required and you will be printing.

---

### Post by Nencio on 2010-04-20
Hi,

I've just finished installing my brother dcp-115c on Hardy 8.04.

For the printer I simply downloaded the brother*-extra packages from synaptic (cups and lpr).

For the scanner I downloaded and installed the brscan2 deb package from the brother website ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)).

Everything seems to work fine.

---

### Post by RamboGT on 2010-04-28
No Joy!

Here is the process I did:

me@house:~/Downloads$ dir *.deb
brhl2170wlpr-2.0.2-1.i386.deb	     picasa_3.0-current_i386.deb
cupswrapperHL2170W-2.0.2-1.i386.deb  skype-ubuntu-intrepid_2.1.0.81-1_i386.deb
opensong_1.6.1-1_i386.deb
me@house:~/Downloads$ sudo mkdir /var/spool/lpd
mkdir: cannot create directory `/var/spool/lpd': File exists
me@house:~/Downloads$ sudo dpkg -i --force-all brhl2170wlpr-2.0.2-1.i386.deb 
(Reading database ... 179417 files and directories currently installed.)
Preparing to replace brhl2170wlpr 2.0.2-1 (using brhl2170wlpr-2.0.2-1.i386.deb) ...
Unpacking replacement brhl2170wlpr ...
Setting up brhl2170wlpr (2.0.2-1) ...

me@house:~/Downloads$ sudo mkdir /usr/share/cups/model
mkdir: cannot create directory `/usr/share/cups/model': File exists
me@house:~/Downloads$ sudo dkpg -i --force-all cupswrapperHL2170W-2.0.2-1.i386.deb 
sudo: dkpg: command not found
me@house:~/Downloads$ sudo dkpg -i --force-all cupswrapperHL2170W-2.0.2-1.i386.deb
sudo: dkpg: command not found
me@house:~/Downloads$ sudo dpkg -i --force-all cupswrapperHL2170W-2.0.2-1.i386.deb
(Reading database ... 179417 files and directories currently installed.)
Preparing to replace cupswrapperhl2170w 2.0.2-1 (using cupswrapperHL2170W-2.0.2-1.i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement cupswrapperhl2170w ...
Setting up cupswrapperhl2170w (2.0.2-1) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

me@house:~/Downloads$ 

The printer is hooked via a CAT5 cable to my router. The router is set to DHCP, and the printer is localed at 192.168.254.105

Any idea on how to make this work?

It looks to be installed, but when I send something to it(web page, odm, anything)...nothing happens; it just sits there, and does nothing.

Thanks.

RamboGT

---

### Post by towb on 2010-05-06
> **Nencio said:**
> Everything seems to work fine.

As with my DCP-135C. I also followed [this instruction]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10") linked from the driver download, but maybe that's not necessary.

---

### Post by dryad on 2010-05-15
Thank you!  Worked beautifully to install a Brother MFC640CW  in Ubuntu 10.04 AMD 64. Those missing directories were the key.  Thanks once again.

---

### Post by MrD_scifi on 2010-05-17
Tried to install my MFC-215C to scan, but found an issue with Linux Mint 9rc

the file: 45-libsane.rules  is not there.

Instead I have three files present:

70-persistent-cd.rules
70-persistent-net.rules
README

neither of the two .rules files has any libsane entries where I can place my printers ID


I did find a way to install the printer in Mint 8 and 9rc though that seems quite straight forward:

Download the two packages for the MFC-210C from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)
You want both the following here on  that page: 

LPR driver 	deb 	1.0.2-1 	740 KB 	2006.Mar.31
cupswrapper  driver 	deb 	1.0.2-3 	12 KB 	2007.Jul.11

The files are called:

mfc210clpr-1.0.2-1.i386.deb
cupswrapperMFC210C-1.0.2-3.i386.deb

**--->**open package Manager and  install "csh"
**--->** plug in  printer and install mfc210clpr-1.0.2-1.i386deb file
**--->**open terminal, enter "sudo  nautilus" browse to "usr/share/cups" directory in the file system,   create a "model" directory, keep nautilus open to watch.
**--->** Install the  cupswrapperMFC210C-1.0.2-3.i386.deb file.  Watch in nautilus as a file  is created in there, brmfc210c_cups.ppd.  this is important!
**--->**Click Menu/Control  Centre/Printing and up comes the printer popup.
**--->**Clicked add new printer.  
**--->**Click on Brother MFC-215C,  click forward and it tries to find drivers.  It fails and offers to add a  .ppd file, choose this option and then click to browse for the .ppd  file that was made in "usr/share/cups/model directory and it will  install your printer driver!!!!  
**--->**You  can now print a test page, which should work, then go on to print your  documents.

---

### Post by brentb37043 on 2010-05-24
Kudos and thanks a million. I have both my printer and scanner working.

---

### Post by kidsodateless on 2010-05-28
:Help: I installed all the drivers of DCP-165c on 8.10 , my printer works and the scanner detected also using xsane, but there's a problem when I press the scan button:

 **ERROR! Failed to start scanner: Invalid agrument**

---

### Post by lizzie2 on 2010-06-10
Hi,
I have Ubuntu 10.04 & Brother DCP-150c
With regard to Scanner step 6.
10.04 has no "/etc/udev/rules.d/45-libsane.rules"
So i put into "Lib/udev/rules.d/40-libsane.rules" the following which has worked for me.

# Brother DCP-150C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01cf", ENV{libsane_matched}="yes"

all the best Les

---

### Post by reedhashlock on 2010-06-17
I'm trying to setup a brother mfc-295cn as a network printer through a wired LAN and I seem to be running into a bit of trouble.

I read through and followed the instructions on the article and it worked. I was able to install the drivers and detect the printer. I found the printer's IP through the printer menu and copied it in the printer properties on my intended work station.

So after I had everything set up I tried to print a test page and it failed. Waited about 10 mins with no result. I don't know what the problem was if it was the cable  I figured that the computer wouldn't be able to detect the printer in the first place.

Anywho I tried the add new printer option in system->administration->printing and selected the network printer option. I placed the ip-add I got from the printer and clicked on find. Lo and behold "no printer found" any ideas?

Running an ubuntu 10.04 by the way and I made sure the printer was on while doing all of this.

edit: I tried to delete the printer and tried to add it again using it's ip, didn't work computer can't find the printer.

---

### Post by lescrooge on 2010-07-18
> **abrianb said:**
> Don't use the brother web site drivers . In it's stead click on System>Administration>Synaptic package manager. In synaptic's search  type "Brother".
You will find a package named "Brother-cups-wrapper-extra" and one named "Brother-lpr-drivers-extra". Click on the Box to mark them for application. Then click on the apply box. Follow along the prompts, enter your password where required and you will be printing.
Hi AbrianB,
Did all that, it found the printer asked for a test page, actually went into the print queue, disappeared, then didn't print.
I'm going to try it on anohter pc with LL before ripping the remains of my hair out.
Incidentally the printer does work, just not on the network.
I've got these Edimax ew 7318Ug usb wirelss dongles. 
They flash for 3 seconds on plug-in, then get very hot - and believe this - even with the pc switched OFF!
They don't show up anywhere on the desktop.
I'm beginning to regret buying 2 of them. 

I've been thru 3 routers in 3 months.
The first D-link - a 2740B - packed up. Started getting too hot, then losing the place.
D-link say it is the firmware, but I am disinclined to believe them. As I had only recently upgraded the firmware on it.
The second is another D-link, but a vertical one. 
Doesn;t get hot, but only has 1 wired netport.
If I had had wirelsss active on KK or even LL I might be able to use it to verify whether it was the The 3rd (Thomson) router or something else.
I am really screwed right now.

TVM
Louis

---

### Post by lescrooge on 2010-07-19
Millagre! On LL I have print. TVM
Now all I need to do is either change the DNS in the router to AutoDNS or find this elisive RT73 GUI installer.
While we are still hooked how do I get back to a post after a reboot.
I noticed someone had a problem solved with scanning, but I cannot find it. 
I need to do that too.
Once again many thanks

---

### Post by thol4u on 2010-07-25
Thank you very much for this How-to. The same steps worked for MFC-420CN printer too. I guess mkdir /var/spool/lpd is an important step.
Appreciate your post!

---

### Post by Beatnink on 2010-07-28
Great instructions particularly for a Linux newbie like me, but unfortunately I wasn't able to get past the DPKG command step, as it keeps complaining that the file that I downloaded is not a valid debian format archive..  I running Ubuntu Lucid 10.04.   Error message shown below:

[COLOR=Navy]root@Office:/home/[user]/Downloads# dpkg -i --force-all dcp130clpr-1.0.1-1.i386.debdpkg-deb: `dcp130clpr-1.0.1-1.i386.deb' is not a debian format archive
dpkg: error processing dcp130clpr-1.0.1-1.i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 dcp130clpr-1.0.1-1.i386.deb[/COLOR]

---

### Post by imachequa on 2010-08-28
It just worked perfect for my DCP-385C...  It was installed over Ubuntu 10.4 Netbook edition... 

I did encountered a single problem... when trying to print the test page nothing happened.  I went to CUPS link ([http://localhost:631/](http://localhost:631/)) delete the printer and added it again.. then everything was ok.

Notice that when adding the printer I saw two DCP-385C drivers... I took the second one.

BTW... for those of you asking, there are 64Bit drivers over Brother site.

Have a happy printing!!!

---

### Post by imachequa on 2010-08-28
> **Beatnink said:**
> Great instructions particularly for a Linux newbie like me, but unfortunately I wasn't able to get past the DPKG command step, as it keeps complaining that the file that I downloaded is not a valid debian format archive..  I running Ubuntu Lucid 10.04.   Error message shown below:

[COLOR=Navy]root@Office:/home/[user]/Downloads# dpkg -i --force-all dcp130clpr-1.0.1-1.i386.debdpkg-deb: `dcp130clpr-1.0.1-1.i386.deb' is not a debian format archive
dpkg: error processing dcp130clpr-1.0.1-1.i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 dcp130clpr-1.0.1-1.i386.deb[/COLOR]

Have you tried to download it again? It might be due to a corrupted file

---

### Post by imachequa on 2010-08-29
Scan well quite well for me... I follow the steps but it is pretty much the same information given on brother site... 

All for DCP-385c

Additionally for 10.4 the USB permission for regular users is a little bit different... (same as described in brother page)

On "/lib/udev/rules.d/40-libsane.rules" file.


Add below lines... before the end as described in the original post here:
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"


Links:
All drivers, intrusions,etc related to linux (at least till 2010-08-29)
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Happy scanning.

---

### Post by imachequa on 2010-08-29
> **abrianb said:**
> Don't use the brother web site drivers . In it's stead click on System>Administration>Synaptic package manager. In synaptic's search  type "Brother".
You will find a package named "Brother-cups-wrapper-extra" and one named "Brother-lpr-drivers-extra". Click on the Box to mark them for application. Then click on the apply box. Follow along the prompts, enter your password where required and you will be printing.

Well it doesn't just work!!! at least not for my system (Samsung NC10 with a Brother DCP-365C printer)

If you check the packages described by abrianb.. they don't include all possible brother printers... so when I did it for my DCP-385C it wasn't part of the drivers and therefore nothing was installed.... I could had installed another driver with my printer just for testing... but this is not a testing box.

Following Brother instructions and together with the very first post on this enormous thread... I managed to have it worked easily... it took me around two hours.. but that is just because I'd to read everything people is saying just to dare doing it on my own system....

BTW... it is now my own system.. it is my wife's and if Ubuntu wants an entry at home.. she needs to approve it!!! ;-)

---

### Post by rumplestilts on 2010-08-29
sudo apt-get install brother-cups-wrapper-extra

Di this in Terminal and, when it was done, I was able to add my MFC-465CN without a problem. Works perfectly.

I did a web search and found a webpage with the answer. Got lucky, I guess.

---

### Post by zazootheparrot on 2010-09-06
I have a Brother DCP-375CW printer/scanner. I've done exactly as mentioned in the 1st page without encountering any errors but the printer is not working! :( I have also installed brother-cups-wrapper-extra.
lsusb gives me the following : 
Bus 007 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 006 Device 002: ID 04f9:0224 Brother Industries, Ltd **
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 054c:0281 Sony Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any ideas what I have to do now?

Thanks

Computer: Sony Vaio VGN-SZ740
Operating system: Ubuntu 10.04 Lucid Lynx

---

### Post by ChrisNZ on 2010-09-10
Hi Everyone

I had the following fault with Linux 10.04 fresh install and a Brother MFC-215c Printer, Scanner and Fax machine. Although I had the Printer working with the relevant cups drivers the scanner just would not work with any of the scanner programs via synaptics (gscan2pdf, Simple Scan or Xsane Image scanner – under 9.04 it ran fine) The scanner drives were installed though!
So after searching the net again and again coming back to Ubuntu Forums here, (still the best place to keep stuff) this is how I fix the following problem.

“Unknown message: scanimage: open of device brother2:bus2;dev1 failed: Error during device I/O”

Following these instructions as per from page 1 helped part of the problem...

Step 1:
Open Terminal by selecting Applications ---- Terminal from the task bar. 

Step 2:
Type or Copy & Paste the following into Terminal and press enter: 
Code:
sudo apt-get install tcsh

Step 3: (This was not loaded so check anyway)
From the task bar go to: System ---- Administration ---- Printing, select your printer that's not working then select edit and click delete.

Check
jump to Step 8:
Create the model directory. As with the lpd directory this is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 9 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:
Code:
sudo mkdir /usr/share/cups/model

Scanner:

Unfortunately the Sane Scanner Driver wasn't quite as straight forward to setup, however it will be a lot easier with these steps: (he's not wrong here!!)

FIRST MAKE SURE YOUR SYSTEM HAS ALL UPDATES INSTALLED IF YOU HAVE A FRESH INSTALLATION OF UBUNTU.

Steps 1 - 3 were no an issue

Step 4:
Confirm you need to continue on with the following steps, I believe it is only Gutsy that has problems. Simply open Xsane, choose you scanner and click OK. If you get an I/O-Error you will need to continue onto Step 5, if it's all working you're done!

(From the brother site)
Ubuntu 9.10, 10.04
1. Open "/lib/udev/rules.d/40-libsane.rules" file. 

Ubuntu:
Code:
sudo gedit /lib/udev/rules.d/40-libsane.rules

2.Add the following two lines to the end of the device list. (Before the line ....."# The following rule will disable ..."):

The lines to be added as below --------------------------- 

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
 
3. Restart the OS. 

After this the scanner software worked!
Swt

Hope this helps someone else?

---

### Post by zazootheparrot on 2010-09-18
The problem with the Brother DCP-375CW PRINTER is solved!!! (in fact, you can use it for any printer!) 
Just follow the link step by step: 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html) 

To download the required drivers click on the link below: 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Thx

---

### Post by zazootheparrot on 2010-09-18
For scanner, use the following: 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

and don't forget to [Use your usb-connected scanner by a normal user]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html")

---

### Post by Ben_neB on 2010-09-22
I have installed the drivers, and I can install the printer, but when I try to print a test page (Or anything else), it submits the job, and then it lists the "Printer State" as "Connecting to Printer..." and it never prints. (And the printer icon receives a yellow triangle.) 

It is a Brother MFC 465cn printer attached as a network printer. Any ideas?

---

### Post by horsemanoffaith on 2010-09-23
Installation of Brother MFC-6800 printer drivers in Ubuntu Linux 10.04 Lucid


[LEFT]These are the exact steps that I followed to get my brother printer working on my Lucid install. This how-to was written specifically for a MFC 6800 printer. My printer is attached to a NetGear USB print server, so I installed the it as a network printer. However, none of these steps are specific to the MFC 6800, so as long as you download the correct drivers and follow this how-to in the order presented, it should work for you!


This is my first how-to, so be gentle!
[/LEFT]
 

 Open a Terminal- **Applications>Accessories>Terminal**
 

 Type the following command- **sudo apt-get install tcsh**
 

 You should get the following output:
 **Reading package lists... Done ** 
 **Building dependency tree       ** 
 **Reading state information... Done ** 
 **The following NEW packages will be installed: ** 
   **tcsh ** 
 **0 upgraded, 1 newly installed, 0 to remove and 63 not upgraded. ** 
 **Need to get 359kB of archives. ** 
 **After this operation, 733kB of additional disk space will be used. ** 
 **Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe tcsh 6.17.00-3 [359kB] ** 
 **Fetched 359kB in 1s (197kB/s) ** 
 **Selecting previously deselected package tcsh. ** 
 **(Reading database ... 123917 files and directories currently installed.) ** 
 **Unpacking tcsh (from .../tcsh_6.17.00-3_i386.deb) ... ** 
 **Processing triggers for man-db ... ** 
 **Setting up tcsh (6.17.00-3) ... ** 
 **update-alternatives: using /bin/tcsh to provide /bin/csh (csh) in auto mode.**
 

 Shrink the terminal (you will need to use it later) and download the LPR and Cupswrapper driver from the following page:
 **[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6800](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6800)**
This link will open the page at the MFC 6800 driver location, but if you scroll to the top of the screen, it shows a complete list of printers there. Find your model and click on it's link!


 **DO NOT OPEN THE DRIVERS FROM THE LOCATION! **If you do so, Gdebi Package Installer will try to install the drivers, and they will fail because not all the of the needed directories will be installed. Save the files to your default download location.
 

 Now, bring up the terminal again and create the LPD directory with the following command:
 **sudo mkdir /var/spool/lpd**
 

 If you are using Ubuntu after 8.10, create the symbolic link between the cups and lpd using the following command:
 **sudo ln -s /etc/init.d/cups /etc/init.d/lpd**

If you are using Ubuntu before 8.10, create the symbolic link between the cups and lpd using the following command:
**sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd**

 Now, create the model directory:
 **sudo mkdir /usr/share/cups/model**
 

 You are now ready to install the printer drivers. Start with the LPR driver first. I simply opened the directory that I downloaded the drivers to, then double-clicked the LPR driver. This installed the LPR driver automatically.  After the LPR driver is installed, install the cupswrapper driver by following the same procedure.
 

 Once you have finished this procedure, click **System>Administration>Printing** and print a test page. You should be set up for printing!

---

### Post by -DBO- on 2010-10-16
This question has probably been asked before but:

How do I use SANE for a brother scanner with a dynamic IP? Printing works with dnssd but I cannot figure out how to do the same with scanning...

Any help would be greatly appreciated.

BG INFO
******************************
OS: Lucid - 10.04
SANE Version: 1.0.2
Printer/Scanner: MFC-7820N


THANKS!!!!
:?::?::?::?:

---

### Post by -DBO- on 2010-10-17
Fixed ^.^

Ended up using nodename instead of ip

Thanks! :):):):)

Code Becomes:
```
sudo brsaneconfig2  -a  name=MFC-7820N  model=MFC-7820N  nodename=XXX***X.local
```

PS:
It was really helped me to find how to remove scanners:
```
sudo brsaneconfig2  -r SCANNERNAME
```

Once again this has all probably been said before in the 33 pages... -.-

---

### Post by rykel on 2010-10-23
Hi, I am late to this thread, but here goes my question - since Ubuntu detects my Brother printer (HL-2140L) out of the box, does it make sense to still install the drivers from the Brother website?

I also noticed that the Official drivers are GPL, so would I be right to assume that the Ubuntu-supplied drivers are in fact the same ones as those on Brother's website?

Thank you for answering!

---

### Post by Sparky75 on 2010-10-23
Greetings to all you Ubuntu users and geeks.  I am new to post here but have been looking up information the last approximately couple of years.  I started using Ubuntu back around version 7.  I need help and hope some one can help me fix my printing problem.  I am running 10.10 on a dell vostro 1500. I am running the 64 bit version.  I tried the 64 bit version back around version 9.0x.  I wound up going back to the 32 bit version because of bugs and incompatibility, mainly the printer.  This time its working very well except for the printer.

I tried a couple of the solutions above.  Rumplestilt's suggestion gave me a lot more printer driver selections but not the one for my printer.  I also tried horsmanoffaith's procedure.  It failed for me when I tried to install the cups and lpd drivers because they are 32 bit.    My printer is the Brother 290c.  I would like the other functions to work but most importanly I need to print.

Please help!

---

### Post by Andavane on 2010-10-24
Ubuntu repositories have many drivers for their scanners and printers.
Mine's an HL1430. I remember that on one of the distros it was listed so I selected another one I thought would probably do for it, and it printed fine.

Scanners are quite a bit more iffy though, when it's a printer/scanner combo.

---

### Post by Sparky75 on 2010-10-24
Yea, I tried the different model number printer thing hoping to hit on one that was similar but no luck that way either.  Thanks though, I wish it was that easy.

---

### Post by nunatakker on 2010-10-29
I use Ubuntu with Brother DCP-120C since 8.10 and it allways worked fine. Now after I updated to Maverick (10.10) I can't use the scanner. Printer works, and all drivers and entries at libsane.rules are done. But neither XSane nor Simple Scan recognize the connected scanner. Maybe it's importend to say that I use Ubuntu 64bit.

Can someone give me a clue to solve this?

---

### Post by Nuno Oliveira on 2010-11-01
Hi,

I have the same problem with my Brother dcp-135c. Printer works fine but no scanner detected... :(

Any help?

Thank you all

---

### Post by zazootheparrot on 2010-11-07
I have exactly the same problem. My printer and scanner all worked fine on ubuntu 10.04 but when I upgraded to 10.10 the printer works but the scanner can not be detected by simple scan/XSane! 

Would appreciate any help :)

Device: Brother DCP-375CW
Laptop: Sony Vaio VGN-SZ740

---

### Post by zazootheparrot on 2010-11-07
By the way, I have already tired the solution given in this link: 
[http://welcome.solutions.brother.com...n1c.html#u9.10]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10")

It still doesn't work!

---

### Post by jblock312 on 2010-11-07
There are a few Brother machines in the brscan3 group that need additional installation.
The instructions and models are listed after the driver list on Brother's website. I'd never noticed them before.

---

### Post by migounanounet on 2010-11-10
Hi,
I have a DCP-135C and manage to make the scanner work on Maverick by doing the following :
On step 6 of the scanner installation I did :

```
sudo gedit /lib/udev/rules.d/40-libsane.rules
```

At the bottom of the page but before LABEL="libsane_rules_end", I add the following line :

```
# Brother DCP-135C
SYSFS{idVendor}=="**YOUR-VENDOR-ID**", SYSFS{idProduct}=="**YOUR-PRODUCT-ID**", MODE="664", GROUP="scanner", ENV{libsane_matched}="yes"
```

And it works... don't know why but it works.
Hope it'll help you.

---

### Post by dojida on 2010-11-29
Thanks a lot, I just got my DCP-385C working on Karmic. This HOWTO is excellent, great work BDW.

---

### Post by wattttaw on 2010-12-03
Many thanks for this Howto it certainly solved my problem.:D

---

### Post by remoteONE on 2010-12-06
Hi,hope this old thread..is still active...
I actually had the brother printer working on 9.10 but after updating, it stoped working ! Sill using 9.10server, as 10.14 just crashed everything.
Followed the instruction and got errors on lpd  install.:

sudo dpkg -i --force-all mfc9660lpr-1.1.2-1.i386.deb
Selecting previously deselected package mfc9660lpr.
(Reading database ... 176430 files and directories currently installed.)
Unpacking mfc9660lpr (from mfc9660lpr-1.1.2-1.i386.deb) ...
Setting up mfc9660lpr (1.1.2-1) ...
/var/lib/dpkg/info/mfc9660lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing mfc9660lpr (--install):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc9660lpr

The  printers shows in the Printer manager & in [http://localhost:631/printers/](http://localhost:631/printers/)
But does not print a test page .. (yes the printer is on)

Ubuntu Printer Manage Print Jobs : the job just sitts in the cue ,
This is strange since , It was working before update.

ALSO, **Synaptic Package Manager** now **CRASHES and is BROKEN**  with error:
E: The package mfc9660lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by remoteONE on 2010-12-06
OK, since I know the printer is on 192.168.1.10, in "Change Device URI> Network Printer > Find Printer>
If I search for the printer and, instead of the port found automatically ,
I select "lpd://192.168.1.10/lp" or "lpd://192.168.1.10/PASSTHRU" or "dnssd://1P_PrintServC7767C._printer._tcp.local/" the printer seems to work.
!

---

### Post by remoteONE on 2010-12-06
Now to the scanner,
> [COLOR=Red]Step 4:[/COLOR]
Confirm you need to continue on with the following steps, I believe it  is only Gutsy that has problems. Simply open Xsane, choose you scanner  and click OK. If you get an I/O-Error you will need to continue onto  Step 5, if it's all working you're done!

[COLOR=Red]Step 5:[/COLOR]
Give yourself permission to use it! At time of release it's a Gutsy Quirk/Bug... First we need to find out the **Vendor ID** & **Product ID**  for our scanner or printer/scanner combo. For anyone using the DCP-115C  printer/scanner ignore this step as your ID's are the same as mine;  Vendor ID: **04f9** Product ID: **018c**.

Any other model type the following in Terminal:
 	Code:
 	lsusb


MY scanner/printer MFC-9600 is on a network Printer server at 192.168.1.10
Can this be set up to com w scanner? clearly the above steps wont work .
Cheers

---

### Post by eryngium on 2010-12-08
I am completely baffled. My PC has 2 drives both running maverick. On the secondary 
drive I have got the scanner working by creting a file in 45-libane.rules that only contains 

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

The exact same does not work on the primary drive. Any suggetions?

---

### Post by slwx on 2010-12-18
thanks, this was very usefull

---

### Post by Carlsen66 on 2011-01-02
I have tried many of the "HOWTO Install Brother 115c printer", but only one has worked for me. And I haven't fount it in this forum.
So here it comes.... 

```

sudo aptitude install brother-lpr-drivers-extra brother-cups-wrapper-extra

```
After running the code, just add new printer and you will now see MFC-210c ( driver for DCP-115C) 

Very simple and is't work!! :p ( for mine DCP-115C ) 

I fount on linuxin.dk [http://www.linuxin.dk/node/15041#comment-39315](http://www.linuxin.dk/node/15041#comment-39315)

Sorry my English is not so good.

---

### Post by Matthewthegreat on 2011-01-03
Just wanted to say thanks! This helped me get my 440cn printer up and running great! :popcorn:

---

### Post by Gompo on 2011-01-04
> **Carlsen66 said:**
> I have tried many of the "HOWTO Install Brother 115c printer", but only one has worked for me. And I haven't fount it in this forum.
So here it comes.... 

```

sudo aptitude install brother-lpr-drivers-extra brother-cups-wrapper-extra

```After running the code, just add new printer and you will now see MFC-210c ( driver for DCP-115C) 

Very simple and is't work!! :p ( for mine DCP-115C ) 

I fount on linuxin.dk [http://www.linuxin.dk/node/15041#comment-39315](http://www.linuxin.dk/node/15041#comment-39315)

Sorry my English is not so good.

This worked instantly for DCP350c after a LOT of unsuccesful methods. Thank you!

---

### Post by raydar on 2011-01-16
> **Matthewthegreat said:**
> Just wanted to say thanks! This helped me get my 440cn printer up and running great! :popcorn:

I've got the printer going on my MFC-440CN, but the scanner is defying me:

There was no file "/etc/udev/rules.d/45-libsane.rules" already in existence, so I created one and edited it to read as follows
> # Brother mfc-440cn
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01af", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"
and restarted, but while SimpleScan doesn't say it can't *find* a scanner, when I scan, it says "failed to connect to scanner." XSane tells me "Failed to open device 'brother2:bus4;dev1."  Any ideas what's up?

Thanks!

---

### Post by sophy_m on 2011-01-17
Hello,

I've got the DCP-195C printer/scanner, and it works fine for printing but can't seem to get it to scan! I'm running 10.10 and as far as I can see there isn't an updated procedure for this distro on the Brother site. I've tried doing the pre-required procedures for the most up-to-date version (even then I had to change the commands), and also tried several of the fixes posted on this thread, but all to no avail! Please can someone help?

Thanks
Sophie

---

### Post by abrianb on 2011-01-17
Sophy, have you tried running "sudo xsane" in terminal. If it works as root (sudo) then its a permissions problem. try this
 				 				**Re: HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies!** 			
 			 			 		   		 		 		I could not get the edit of **/lib/udev/rules.d/50-udev-default.rules  to work so I just opened a text editor and created a file  "51-udev-default.rules that said**...
device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",  NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"            Then  saved it. Then moved it to /lib/udev/rules.d
 Now my scanner works.

---

### Post by sophy_m on 2011-01-18
Thank you, but neither of those things worked :( 

Of course I've tried so many different things that there are probably now all kinds of compatibility issues! I might start again from scratch.

---

### Post by sophy_m on 2011-01-20
I've done it! Used the .deb package instead of the .rpm... No doubt if I were a more terminal-savvy person I would never have made that mistake in the first place, but hey, it works now.

---

### Post by abrianb on 2011-01-20
Congrats! 
  I didn't think of that. Always use .debs for Ubuntu.

---

### Post by A K Das on 2011-01-21
Hi all, I am new in this forum. My problem is -I'm trying to add my printer/scanner Samsung  SCX-4521F to my machine running Ubuntu 10.04.  I was successful setting  up the printer.  It  works perfectly.  The only problem is that Sane  does not find the scanner.  I looked at the sane-project website and did  not find my device under supported devices. 

even i do not know much about ubuntu and i really loved it after using. 
please anybody tell me how to do it step by step, that will be great help. 



being a new member, i will get a help.

---

### Post by backdoc on 2011-01-23
I don't know if this is old news on this thread.  But, I wanted to document, how I got scanning working on an MFC-420CN with 11.04.

It was actually really easy.  I just followed the instructions on the Brother website.  While this worked for my situation, you might not have to do everything I did or possibly more.  It's just what I did.

To download, I went here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html").  Be sure to search the page for your model number.  The first time, I did it I got in a hurry and chose the wrong one.

I downloaded 2 files: [brscan2 32bit]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan2-0.2.5-1.i386.deb&lang=English_sane") and [scan-key-tool 32bit]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.i386.deb&lang=English_lpr").

I installed the debs with dpkg -i.

Then, if you look just below the files listed, there are 2 links for how to install.  Here's a [page with instructions]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html").  I chose the 3rd option, the one for normal users ([Setting for normal users (Required for USB Connection)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html")).  Since the option for my version of Ubuntu wasn't there, I just followed the most recent version I could find.

I rebooted and scanning just worked.

KUDOS to Brother for making this available and to Ubuntu for making a terrific distro.

I hope this helps someone.

---

### Post by jeepzj on 2011-01-23
Well...I think I've read almost every single post on this scanner issue with the 490CW, and I'm still no further ahead.

I've been running Ubuntu for years with no issues, but since 9.04 expired, and I got a new Nvidia card, it was time to upgrade to 9.10, and this is where some 'issues' happened..

Here is my unique situation... I have the Brother MFC-490CW installed as a network printer 192.168.1.151. *(EDIT : this is setup as a wireless printer)* I can print to it from my Karmic box no problem, but when I try to lunch Xscan, it tells me it sees no scanners attached.  When I do lsusb i get :

```
hu@hu-desktop:~$ sudo lsusb
Bus 001 Device 003: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 001 Device 004: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I did the mods to the mods to the /lib/udev/rules.d/50-udev-default.rules file.

Output of my (brscan-skey --diagnosis) is :

```

...
/usr/local/Brother/sane/brsanenetdevice3.cfg:
DEVICE=SCANNER , "MFC-490CW" , 0x4f9:0x1fb , IP-ADDRESS=192.168.1.151 

....

```

_hu@hu-desktop:~$ brsaneconfig3 -q_ shows the following :

```

Devices on network
  0 SCANNER             "MFC-490CW"         I:192.168.1.151

```



So, from what I can tell, it sees the scanner.

Now comes the kicker.. when I scan by using the button on the printer, it scans no problem, and opens up GIMP or saves the file in my home dir, but if I try to scan from GIMP afterwards (using create), it opens up xsane, and states again that no scanner is available after a few seconds..

Has anyone see this before?  What the heck could be wrong?

Much appreciate any info or comments that can help me get my scanner back !!

Thanks for reading..

-Hubert

---

### Post by Newbus on 2011-02-04
This HowTo was extremely well constructed.  Many of the basics are assumed on the Brother website which helps keep it concise.  Without this How To I struggled: eg csh error was encountered.  But now I am the proud owner of Test Page which I am going to use as a beer mat while I print and scan.

Thanks very much for making an effort, one of the first things a new user wants to do is connect the scanner and printer.  Well done and please continue to write quality like this.

---

### Post by LanoxxthShaddow on 2011-02-18
```
$sudo vim /lib/udev/rules.d/50-udev-default.rules
```Then add this line somewhere in the file. I added below the #printer section

```

#scanner
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"

```The instructions on the first page which were still for gutsy didnt work for me even though i created the scanner group.

This works for Maverick with a Brother DCP-560CN, I got the driver from here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html)

---

### Post by Newbus on 2011-02-24
Xsane works if I first use the preview window, then the scan button.  Otherwise it returns an error. Failed to open device:invalid argument.

---

### Post by Bladeforger on 2011-02-26
> **Carlsen66 said:**
> I have tried many of the "HOWTO Install Brother 115c printer", but only one has worked for me. And I haven't fount it in this forum.
So here it comes.... 

```

sudo aptitude install brother-lpr-drivers-extra brother-cups-wrapper-extra

```
After running the code, just add new printer and you will now see MFC-210c ( driver for DCP-115C) 

Very simple and is't work!! :p ( for mine DCP-115C ) 

I fount on linuxin.dk [http://www.linuxin.dk/node/15041#comment-39315](http://www.linuxin.dk/node/15041#comment-39315)

Sorry my English is not so good.
Wonderful--much better than the Brother website instructions.  

Also, Synaptic works.  Type Brother and your printer model in the search box, and it'll even select the driver pkgs with that model mentioned.

---

### Post by davidwhthomas on 2011-03-13
Thanks the simple apt-get install instructions then adding a new printer and selecting that driver worked fine on my DCP-115C

```
sudo aptitude install brother-lpr-drivers-extra brother-cups-wrapper-extra
```

System > Administration > Printing > Add

Followed instructions and selected driver MFC-210c ( driver for DCP-115C) 

Lucid 10.4

---

### Post by paaating on 2011-03-14
> **davidwhthomas said:**
> Thanks the simple apt-get install instructions then adding a new printer and selecting that driver worked fine on my DCP-115C

```
sudo aptitude install brother-lpr-drivers-extra brother-cups-wrapper-extra
```

System > Administration > Printing > Add

Followed instructions and selected driver MFC-210c ( driver for DCP-115C) 

Lucid 10.4

Is it safe to install using this?

---

### Post by Fraoch on 2011-03-24
> **paaating said:**
> Is it safe to install using this?

It should be, packages installed using aptitude come from the repositories, all signed with a key.  It's a pretty secure system, if unauthorized changes are done to the files the system breaks and the package won't install.

However note in this case that brother-lpr-drivers-extra contains drivers for the following models:

> FAX-1815C FAX-1820C FAX-1835C FAX-1840C FAX-1920CN FAX-1940CN FAX-2440C MFC-210C MFC-3220C MFC-3240C MFC-3320CN MFC-3340CN MFC-3420C MFC-3820CN MFC-410CN MFC-420CN MFC-5440CN MFC-5840CN MFC-620CN DCP-110C DCP-310CN DCP-560CN DCP-770CW DCP-350C DCP-353C MFC-465CN MFC-680CN MFC-685CW MFC-885CW MFC-230C MFC-235C MFC-260C DCP-135C DCP-150C DCP-153C

(from the [package details page]("http://packages.ubuntu.com/hardy/brother-lpr-drivers-extra"), I believe the cups-wrapper package contains drivers for the same models)

Those are older printers - these packages were made when Hardy was introduced in April 2008, so if you have a newer printer they *might* work, or they might not.

But Brother makes it fairly easy with Linux support for most/all (?) of their newer models here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

The printer drivers are here, the scanner drivers are there, the PC-FAX drivers are there, heck, there's even a little app that sends scans to the program of your choice.:D

Support printer manufacturers who support Linux!  I have an expensive Canon imageCLASS MF5770 which I bought before I was into Linux and it's an expensive paperweight now, so I was hesitant about buying Canon again.  When I saw the extensive support Brother had for Linux, I went ahead and got an MFC-J615W.

---

### Post by Fraoch on 2011-03-24
Not sure if the OP is still around, but if he/she is, THANKS!

Here are a few comments installing this stuff on Ubuntu 10.10 amd64 with a new Brother MFC-J615W (this has wireless networking so it doesn't have to be connected by USB) - note I didn't read the entire 37-page thread.

> **BoardDWorld said:**
> [COLOR="Red"]Step 6:[/COLOR]
Create the lpd directory. This is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 7 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

```
sudo mkdir /var/spool/lpd
```

This is required and NOT covered in the Brother instructions.

If you don't do this, you will get an error message stating that /var/spool/lpd/[driver name] can't be created.  However if you try creating /var/spool/lpd/[driver name] by using mkdir, you can't, not even using sudo.  You can create /var/spool/lpd though, and then the driver install will create /var/spool/lpd/[driver name] for you with no errors.

I learned this the hard way.;)

Everything else is more or less hunky-dory.  The Brother instructions, while simple, work pretty well.

> [COLOR="Red"]Step 10:[/COLOR] (This is for Gutsy 64bit users only, 32bit users continue onto Step 11 )
If you're using the MFC-210C driver Type or Copy & Paste the following command in Terminal:
```
sudo cp /usr/lib/cups/filter/brlpdwrapperMFC210C /usr/lib64/cups/filter
```
If you're using another driver please adjust MFC210C to suit your model. Example for the MFC-3820CN driver:
```
sudo cp /usr/lib/cups/filter/brlpdwrapperMFC3820CN /usr/lib64/cups/filter
```

If you're not sure you can check by typing the following in Terminal:
```
cd /usr/lib/cups/filter
dir
```

This doesn't seem to be required anymore for 10.10.  The files in /usr/lib/cups/filter seem to be synced with /usr/lib64/cups/filter.  Still, it doesn't hurt to check.
 
> After completing the driver installation open Firefox and enter the following into the address bar:
```
http://localhost:631
```

Click on &#8220;Manage Printers&#8221; and confirm that the driver name is listed there.

If the driver name is NOT listed there, click on "Add Printer" and install the driver following the on-screen instructions.

The default port is USB. If you want to use a different port, click on &#8220;Modify Printer&#8221; and select the required printer port.

Note, the "Modify Printer" command seems to take quite a while on my system, about 10-20 seconds.  I initially thought it hung.  Just be patient.

> [COLOR="Red"]Step 5:[/COLOR]
Give yourself permission to use it! At time of release it's a Gutsy Quirk/Bug... First we need to find out the **Vendor ID** & **Product ID** for our scanner or printer/scanner combo. For anyone using the DCP-115C printer/scanner ignore this step as your ID's are the same as mine; Vendor ID: **04f9** Product ID: **018c**.

Any other model type the following in Terminal:
```
lsusb
```

Your output will be something like this:
```
matthew@matthew-laptop:~/Desktop$ lsusb
Bus 005 Device 004: ID 05ca:1810 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID **04f9:018c** Brother Industries, Ltd 
Bus 001 Device 001: ID 0000:0000  
matthew@matthew-laptop:~/Desktop$ 

```

Locate **Brother Industries, Ltd** and take note of your **Vendor ID:Product ID** as shown in bold in the above output and adjust Step 6 to match.

[COLOR="Red"]Step 6:[/COLOR]
In Terminal type the following:

Ubuntu:
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
Kubuntu:
```
sudo kate /etc/udev/rules.d/45-libsane.rules
```
At the bottom of the page but before LABEL="libsane_rules_end" add the following changing YOUR-VENOR-ID & YOUR- PRODUCT-ID to yours, both are 4 characters long:
```
# Brother DCP-115C
SYSFS{idVendor}=="**YOUR-VENOR-ID**", SYSFS{idProduct}=="**YOUR-PRODUCT-ID**", MODE="664", GROUP="scanner"

```

The last section of 45-libsane.rules should look like this after adding your scanner/printer to the last line:
```
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5105", MODE="664", GROUP="scanner"
# Dell A960
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5107", MODE="664", GROUP="scanner"
# Dell 922
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5109", MODE="664", GROUP="scanner"
# Dell 1600n
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5250", MODE="664", GROUP="scanner"
# Brother DCP-115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"
```

Here's where I'm stuck.  I don't have the Vendor and Product ID.  I could get it by connecting the printer by USB and reading it using these instructions.

BUT - the file /etc/udev/rules.d/45-libsane.rules does not exist on my system.  I verified I have sane, libsane, sane-utils and xsane installed, so it should be there, but maybe 10.10 has another way of doing this?  Hmm.

I'll have to do some digging to see what to do - create the file from an old copy on the net or find a complete other way to do it.

There was an issue with the fax driver, it was installed but disabled with the warning "Filter "/usr/lib/cups/filter/brfaxfilter" for printer "BRFAX" has insecure permissions (0100777)" - not good.

A clue is given with the scanner section above, the file /usr/lib/cups/filter/brfaxfilter must have improper permissions (777).  I fixed this:

```
sudo chmod 755 /usr/lib/cups/filter/brfaxfilter
```

(make sure the filter has execute permissions!)

Then I restarted CUPS (the procedure has changed since this how-to was originally written):

```
sudo initctl restart cups
```

Bam, the problem went away for the fax driver.

I'm left wondering how to change permissions for the scanner.  As the OP listed it as a Gutsy bug, I'm hoping it's been resolved in Maverick.  The absence of a /etc/udev/rules.d/45-libsane.rules file seems to indicate the whole thing is handled differently now.

I haven't been able to test everything out yet as the printer is actually a gift for my fiance so I can't open it yet :D but I'll update when/if everything works.

---

### Post by Jose Catre-Vandis on 2011-03-26
DCP-540CN on network: Printer works fine but Scanner stopped working after update to 10.10. Does using the USB info in libsane.rules work for network scanning as well?

---

### Post by Fraoch on 2011-03-31
> **Jose Catre-Vandis said:**
> DCP-540CN on network: Printer works fine but Scanner stopped working after update to 10.10. Does using the USB info in libsane.rules work for network scanning as well?

There's some other file which controls scanning in 10.10 - I don't have the libsane.rules file but network scanning for my MFC-J615W works just fine.

This is using the Brother scanner driver though.  Looks like your model uses brscan2: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan2](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan2)

---

### Post by Fraoch on 2011-03-31
> **Fraoch said:**
> I haven't been able to test everything out yet as the printer is actually a gift for my fiance so I can't open it yet :D but I'll update when/if everything works.

All set up and everything works just fine, first try!  Printing, scanning over network using the printer key, scanning over network to a program using xsane, scanning using the flatbed, scanning using the ADF.  It all just works without any fuss.

Some minor tips and reconfiguration for newbies:

- if the printer IP address changes or you specified the wrong one following the Brother instructions, reconfigure it using the CUPS page, Administration tab - Manage Printers - [select printer] - [in pulldown menu on right] Modify Printer.

This is not exactly intuitive, but select something other than "Current Connection" in order to change the Current Connection entry.  The Brother instructions for my model state to use "AppSocket/HP JetDirect" for the printer function, and "LPD/LPR Host or Printer" for the Fax.  Your model may be different.  On the next page, specify the "Device URI" as the Brother instructions call it in the "Connection:" line.  Everything else is straightforward.

I had to change both the printer and fax drivers this way.

Follow Brother's instructions for installing the network scanner driver.  Where you enter:

```
name=(name  your  device)  model=(model  name)
```

use underscores instead of spaces for the names if you need to.

If you make a mistake or your scanner's IP address changes, edit the configuration file:

```
gedit /usr/local/Brother/sane/brsanenetdevice3.cfg
```

(or brsanenetdevice or brsanenetdevice2)

This assumes that the file is able to be modified by you, as it was on my system.  If it's protected, the text editor will indicate "READ ONLY" in its title bar and any changes you make won't be able to be saved.  In this case, modify it as root using:

```
gksudo gedit /usr/local/Brother/sane/brsanenetdevice3.cfg
```

(or brsanenetdevice or brsanenetdevice2)

When it's configured properly, the scanner could be accessed from [for example] GIMP just fine, using xsane.  Give it some time after clicking xsane though, it takes a while to come up.

In order to send scans from the printer to Ubuntu using the printer control panel, you have to install brscan-key as indicated in the Brother instructions.  You enter:

```
brscan-skey
```

to start the little app which receives data from the scanner.  Incidentally, it will place scanned images in /home/[you]/brscan as PPM (raw bitmap) images.  This was also not intuitive, I had no idea where it sent the files at first.

If you will be doing this, it will help to put this little app in your startup programs using System - Control Center - Sessions - Startup Programs tab.  Press the Add button and add the program startup command listed above to the "Command:" field.  Put whatever you want in the other fields.  This way the program will be started again if you restart Ubuntu.

And that's it, everything is working perfectly!

We will hardly be using this as a fax, if ever, but I'm testing it a bit and it's not working as well as everything else.  I'll cover it in another post.

Still very happy though!

---

### Post by Fraoch on 2011-03-31
Regarding the fax driver, I found a mistake in my directions above.  Fixing this helps, but I still can't fax from the Ubuntu machine.

It turned out I did not give execute permissions to /usr/lib/cups/filter/brfaxfilter.  When I tried to print to it, I got an error message stating that the filter could not be executed.

I'll edit my other post to correct this, but even after correcting the permissions, the problem I'm having is that although I can print to the fax, it doesn't do anything - it just sits there forever, receiving data.  There's nowhere where I can specify what number to send the fax to.

The "printer" configuration for the fax is suspiciously sparse, only allowing a change to media size and quality.  Makes me think that the fax driver didn't install correctly...?

Ubuntu's native fax program, Efax (installed from Ubuntu Software Centre) does contain a field for the fax recipient's number, but there doesn't seem to be a way to specify this machine as a fax machine.  In Efax-gtk - File - Settings - Modem - Serial Device, the default is ttyS0, sort of like COM1 in Windows.  Definitely not right for a device on the network.  However there doesn't seem to be a way to specify a network device.  If you leave it blank, it uses /dev/modem.  In my file system, /dev/modem is a symlink pointing to /dev/brusbmfc.  Based on the name of that file, I'm guessing this should work if the fax was connected by USB, but I have no idea how to get it to connect across the network.

I'll keep playing with it and update if I solve it.

---

### Post by Fraoch on 2011-03-31
I've figured out the fax, although it works in kind of a roundabout way.

For the MFC-J615W, there are two ways of using the fax from your Ubuntu PC:

- using the LPR and CUPS-wrapper drivers

- using the fax-modem driver, which is made specifically for Ubuntu and specifically for Ubuntu 10.10

The LPR and CUPS-wrapper drivers can't be used ("printed" to) from programs in the way you would with other CUPS printers.  If you print to it, nothing happens - the MFC wakes up and indicates "receiving data", the print spool will indicate that the MFC is receiving 0 bytes out of [whatever] and just sit there.

You have to use Brother's command-line-only brpcfax as stated in the Brother instructions:

```
brpcfax  -o  fax-number=(fax-number)  (filename)
```

and it only accepts .ps (PostScript) files.  Making .ps files is a little clunky, the easiest way is to open or create the file in OpenOffice, then select print, specifying "Print to File" in the checkbox.  I'm using BRFAX as the printer but I think any PostScript printer would work (the Brother printer, others).  All it's doing is converting the text and images to PostScript, which you then fax.

So - not very direct.:(

I sent a test file (not a .ps file though) this way and the printer woke up and started dialing, so I think it should work if you can make a .ps file.

I also haven't thoroughly tested it out, but the fax-modem driver method through Efax should work OK.  However it's limited to USB only as explained in the Brother instructions.  The Brother instructions tell you to modify /etc/efax.rc, changing DEV from ttyS1 to modem.  You should also modify the other parameters like your name, your telephone number, etc.

However this is for the Efax command-line program.  If you're using the Efax-gtk graphical frontend, it has a separate configuration file.  You should be able to modify it using Efax-gtk - File - Settings but for some reason I couldn't alter the settings, it would revert to what it was before when I exited the program.  Efax-gtk uses a separate configuration file at /etc/efax-gtkrc which can only be altered as root, so use:

```
gksudo gedit /etc/efax-gtkrc
```

change DEV to modem and alter your name, telephone number, paper settings, etc.

Unfortunately while Efax-gtk is more user-friendly than brpcfax, it will still only accept .ps files, although it will also accept plain text files according to its description in Synaptic.

Could be better I guess, but the otherwise flawless operation of this printer in Ubuntu Linux makes up for it.:)

---

### Post by Jose Catre-Vandis on 2011-03-31
> **Jose Catre-Vandis said:**
> DCP-540CN on network: Printer works fine but Scanner stopped working after update to 10.10. Does using the USB info in libsane.rules work for network scanning as well?

OK I can confirm this does the trick on Maverick (Xubuntu)

I had to create the libsane.rules file as it didn't exist:
```
sudo nano /etc/udev/rules.d/45-libsane-rules
```
then I put this in it:
```
# Brother DCP-540CN
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01aa", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"
```

Fraoch's search for the brscanconfig file turns up that it also stores the device ids, so good find.

I saved the file, clicked on my xsane icon, and up it came and scanned away immediately. Back in business.:)

---

### Post by Fraoch on 2011-03-31
> **Jose Catre-Vandis said:**
> Fraoch's search for the brscanconfig file turns up that it also stores the device ids, so good find.

Thanks!

Glad you got it working again.

---

### Post by Cristvo on 2011-04-04
Hi,
 Thanks a lot for your post, i got the printer working perfectly but i couldnt make it with the scanner. when i wrote on console "*sudo gedit /etc/udev/rules.d/45-libsane.rules* " just appear a blank page.
I would be grateful for any help.

---

### Post by Fraoch on 2011-04-04
> **Cristvo said:**
> Hi,
 Thanks a lot for your post, i got the printer working perfectly but i couldnt make it with the scanner. when i wrote on console "*sudo gedit /etc/udev/rules.d/45-libsane.rules* " just appear a blank page.
I would be grateful for any help.

Your setup is like mine.  I presume Ubuntu 10.10 doesn't use this file anymore and it didn't exist on my system either.

Go here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

, find your printer/scanner model, download the driver and follow the instructions.

Incidentally the little scanner key program also on this page works just fine, while the Windows and Mac versions I installed on other computers in the household didn't (errors out when the scan gets transferred).  Thought that was mildly amusing.:P

---

### Post by Cristvo on 2011-04-05
Thanks, scanner is working perfectly!

---

### Post by Fraoch on 2011-04-05
> **Cristvo said:**
> Thanks, scanner is working perfectly!

Good to hear!  Incidentally what model is your Brother machine?

---

### Post by Cristvo on 2011-04-05
> **Fraoch said:**
> Good to hear!  Incidentally what model is your Brother machine?

It's a MFC-820CW.

---

### Post by Fraoch on 2011-04-06
I stumbled upon this post which improved the fax usage for my MFC:

[http://ubuntuforums.org/showpost.php?p=10624376&postcount=8](http://ubuntuforums.org/showpost.php?p=10624376&postcount=8)

Also I played around with the scripts that get executed when the machine keys are pressed to be a bit more useful to me.  Note this is newbie stuff because I'm a newbie, so don't expect anything dramatic.:)

First, the script at /usr/local/Brother/sane/script/scantofile-0.2.1-3.sh (the version numbers at the end of your script may be different).  This controls what happens when you select Scan to File on the machine.  By default, it scanned at 100 dpi in an unusual .PPM format and left the file in /home/[your user name]/brscan.

I changed it to 200 dpi because I always scale it down in another program - it's easy to scale down images, but impossible to scale up if you don't have enough detail.  Plus a 200 dpi full-page scan is still manageable across a wireless network, it's a little over 10 MB and takes about 10 seconds to transmit using "g" wireless networking.  I changed the file format to TIFF - I don't know much about .PPM and it could be compressed, I want the raw scan and I'll save it in the format of my choice.  Finally I always look at a scan in a graphics editor because it almost always needs to be cropped, at the very least, so I want to start GIMP automatically with this file loaded after the scan completes.

My modified script looks like this:

```
#! /bin/sh
set +o noclobber
#
#   $1 = scanner device
#   $2 = friendly name
#

#   
#       100,200,300,400,600
#
resolution=200
device=$1
mkdir -p ~/brscan
if [ "`which usleep`" != '' ];then
    usleep 10000
else
    sleep  0.01
fi
output_file=`mktemp ~/brscan/brscan.XXXXXX`
chmod 644 $output_file
echo "scan from $2($device) to $output_file"
scanimage --device-name "$device" --format=tiff --resolution $resolution> $output_file
echo gimp $output_file \;rm -f $output_file | sh &
```

To edit your script, use

```
gksudo gedit /usr/local/Brother/sane/script/scantofile-0.2.1-3.sh
```

, modifying the version number as necessary, and either overwrite the existing script with this one or change the number after "resolution" and the last two lines.

Other niceties which you might want but which I kept - change the location the files are sent to (change the "mkdir -p ~/brscan" line) and don't delete the initial raw scan after editing (remove "\;rm -f $output_file" at the end).

Next, /usr/local/Brother/sane/script/scantoimage-0.2.1-3.sh.  This one already called GIMP but I changed the resolution and file format:

```
#! /bin/sh
set +o noclobber
#
#   $1 = scanner device
#   $2 = friendly name
#

#   
#       100,200,300,400,600
#
resolution=200
device=$1
mkdir -p ~/brscan
if [ "`which usleep`" != '' ];then
    usleep 10000
else
    sleep  0.01
fi
output_file=`mktemp ~/brscan/brscan.XXXXXX`
echo "scan from $2($device) to $output_file"
scanimage --device-name "$device" --format=tiff --resolution $resolution> $output_file
echo gimp $output_file \;rm -f $output_file | sh &
```

Finally, /usr/local/Brother/sane/script/scantoocr-0.2.1-3.sh.  Turns out this one doesn't work by default at all - there were two lines at the end of the script which were supposed to say that OCR is not supported and then delete the scan.:lolflag:  This can be rectified by installing two packages, tesseract-ocr (probably the most accurate command-line OCR engine) and OCRFeeder, a GUI for command-line OCR engines.  To install these packages:

```
sudo apt-get install tesseract-ocr ocrfeeder
```

Then the OCR script can be modified to send the scanned file to OCRFeeder, at 200 dpi and in TIFF:

```
#! /bin/sh
set +o noclobber
#
#   $1 = scanner device
#   $2 = friendly name
#

#   
#       100,200,300,400,600
#
resolution=200
device=$1
mkdir -p ~/brscan
if [ "`which usleep`" != '' ];then
    usleep 10000
else
    sleep  0.01
fi
output_file=`mktemp ~/brscan/brscan.XXXXXX`
echo "scan from $2($device) to $output_file"
scanimage --device-name "$device" --format=tiff --resolution $resolution> $output_file
echo ocrfeeder --images $output_file \;rm -f $output_file | sh &
```

I may work on this one a little bit, the images you send to OCR need to meet certain requirements (1-bit black & white, etc), but this will only send colour scans to OCRFeeder even if you press the "Black" scan button - the program which detects the button press doesn't seem to differentiate between the two scan buttons.  It might be possible to format the image correctly using the options for "scanimage".

Hope this helps!

---

### Post by carloscmt on 2011-04-19
I have a brother mfc 9120nc connected to the network. I am able to print but how can I install the scanner driver? I am new to ubuntu 10.10 and help will be greatly appreciated.

---

### Post by Fraoch on 2011-04-19
> **carloscmt said:**
> I have a brother mfc 9120nc connected to the network. I am able to print but how can I install the scanner driver? I am new to ubuntu 10.10 and help will be greatly appreciated.

Go here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3)

(your model is located on this list, "brscan3") and download the brscan3 and scan-key-tool .deb files.  You probably have 32-bit.  Then follow the instructions:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html)

Check my posts on this page and a last page regarding scanner installation - if I recall correctly there's a "gotcha" or two.  It's not too hard, and if you get stuck don't hesitate to come back here.

You'll be doing all this through the command line.  Don't be intimidated, just follow the instructions and make sure not to make a typo (copy and paste the commands to be sure).  There are times when you'll have to issue a command as a "superuser" - you'll know if you issue the command and it errors out saying something about permissions.  In that case type "sudo" without the quotations ahead of the command.  It will ask you your password the first time.

If the instructions say you require packages, probably the easiest way as a new user is to open the Ubuntu Software Center, type the exact package into the search box and install.

---

### Post by luismgl on 2011-04-29
I have a brother dcp 165c and I cannot install the driver on the new ubuntu 11.04

I do this
```
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/dcp165c
cd Downloads
```and up to here no problems, later I do this:

```
sudo dpkg  -i  --force-all  (lpr-dcp165clpr-1.1.2-2.i386)
```and in here I get " bash: syntax error near unexpected token `(' "

I tried fixing it with this 
```
sudo mkdir /var/spool/lpd
sudo mkdir /var/spool/dcp165c
``` but it didn't work.

Anyone has any ideas?
Thank you.

---

### Post by Bushcraft Bill on 2011-04-29
Well its back to square one with my brother MFC-5440CN printer I had no problems with 10.04 and the tutorial for getting it to work but now 11.04 I did it all over again but no luck this time guess enough has changed were it is now broken unless someone comes up with a new fix....
May just be time/excuse for me to get one of them new wireless printer/fax/scanners

---

### Post by Fraoch on 2011-04-29
> **luismgl said:**
> ```
sudo dpkg  -i  --force-all  (lpr-dcp165clpr-1.1.2-2.i386)
```and in here I get " bash: syntax error near unexpected token `(' "

Indicates something wrong in the script - did it work in 10.10?

Some of the Brother drivers seem to be specific to the distro version, which means they might not work for anyone under 11.04 until/if they're updated.:(

Given issues like these and the general concern I'm seeing over Unity, I'm not only holding off, I'm investigating replacements like Arch and Debian - running in a VM for now.  Even tried Gentoo and did get it working although it's a lot of work.

---

### Post by luismgl on 2011-04-29
> **Fraoch said:**
> Indicates something wrong in the script - did it work in 10.10?

Some of the Brother drivers seem to be specific to the distro version, which means they might not work for anyone under 11.04 until/if they're updated.:(

Given issues like these and the general concern I'm seeing over Unity, I'm not only holding off, I'm investigating replacements like Arch and Debian - running in a VM for now.  Even tried Gentoo and did get it working although it's a lot of work.

Haven't tried this on the 10.10, it was actually my first try with a Brother printer on a Linux system. 

Searching for this issue in the companies official site was useless, they go far back to Ubuntu 8.04.

I might just put Windows or something running on a VM to get my work done, at least until there is a driver available.

---

### Post by walt.smith1960 on 2011-04-29
> **luismgl said:**
> Haven't tried this on the 10.10, it was actually my first try with a Brother printer on a Linux system. 

Searching for this issue in the companies official site was useless, they go far back to Ubuntu 8.04.

I might just put Windows or something running on a VM to get my work done, at least until there is a driver available.

If you're using 32 bit Ubuntu, I just did these:
**sudo aa-complain cupsd**
**sudo mkdir /usr/share/cups/model**then used Gdebi to install the .deb package.  Installing in a 64 bit system you have to use the command line because you have to use the --force-all part of the command and if that can be done from the GUI I don't know how.  I've installed Brother MFC-7820N and MFC-6490CW in different distros including 11.04 Ubuntu & Xubuntu.  No problems at all.  I used Gdebi to install the scanner package as well but had to do the one command line  **brsaneconfig(2,3,4)  -a  name=(name  your  device)  model (model  name)  ip=xxx.xxx.xxx.xxx**  That was it, it works fine.

sudo dpkg  -i  --force-all  (lpr-dcp165clpr-1.1.2-2.i386)Did you try this command without the parentheses?  I cheated when I installed onto the 64 bit systems.  I just typed the "sudo dpkg -i --force-all" then copied and pasted the file name, no parentheses or other characters. Installed as expected.  I hope you're able to get this working.  I don't know if your machine is USB or networked but if networked, check the Device URI.  Every time I install the Brother MFC-6490CW, the device URI starts out usb:/XXXXX.  There's no USB cable so of course it doesn't print.  I've had the best reliability with networked printers using socket.  E.g. socket://xxx.xxx.xxx.xxx(inserting the i.p. address.  Set the printer to have a static i.p. address)  I hope this is of some help to you.

---

### Post by Fraoch on 2011-04-29
> **walt.smith1960 said:**
> sudo dpkg  -i  --force-all  (lpr-dcp165clpr-1.1.2-2.i386)Did you try this command without the parentheses?  I cheated when I installed onto the 64 bit systems.  I just typed the "sudo dpkg -i --force-all" then copied and pasted the file name, no parentheses or other characters.

Well spotted - that could be the "(" syntax error the CLI referred to.

luismgl - when using dpkg, only use the parentheses if they are a part of the file name.  Use the exact file name including the .deb extension.

If you get the file name wrong it will let you know by responding that there's no file with that name.

---

### Post by doubtful wisdom on 2011-05-03
My MFC-440CN was easy to install. Printing and scanning worked well.  I believe that it was always necessary to re-install the drivers after each upgrade, but 11.04 is a problem.  Cannot add the printer.  Add does not find the drivers, which have been installed and re-installed.  Synaptic even has the drivers for the 440, but no joy.

Scanner is not recognized either. 

Nothing special, USB connection to printer, a 32 bit PC install (a fresh install since update to 11.04 went poorly).  

Help would be appreciated.  I have read most of the relevant postings on this thread, tried many suggestions, but....no joy.

---

### Post by Fraoch on 2011-05-04
> **doubtful wisdom said:**
> My MFC-440CN was easy to install. Printing and scanning worked well.  I believe that it was always necessary to re-install the drivers after each upgrade, but 11.04 is a problem.  Cannot add the printer.  Add does not find the drivers, which have been installed and re-installed.  Synaptic even has the drivers for the 440, but no joy.

Scanner is not recognized either. 

Nothing special, USB connection to printer, a 32 bit PC install (a fresh install since update to 11.04 went poorly).  

Help would be appreciated.  I have read most of the relevant postings on this thread, tried many suggestions, but....no joy.

Have you tried the drivers from the Brother site rather than the drivers from the repos?

Most of the drivers there seem to be for all Ubuntu versions.  Only one is listed as specifically for Ubuntu 10.10, the fax modem driver, and it's not even for your model.

I haven't tried the full functionality of my MFC-615W since the upgrade to 11.04, but the scanner is working fine over wireless so I presume the rest is as well.

---

### Post by doubtful wisdom on 2011-05-08
I have now re-downloaded and re-installed 11.04 twice, just to be reasonably certain that the CD was not the problem.  I am just trying to get the MFC-440CN printer to work first.  I installed the drivers from Brother as I have done for other versions of Ubuntu.  The 440 is seen as attached to USB.  However, it will not add.  Drivers are not found.

Wiped out 11.04.  Re-installed from another CD and another download.  Used Synaptic supplied 440 drivers.  Printer will not add.  Driver not found.  Tried to install drivers from the Brother site, but dpkg did not want to do so, since I have "later" drivers installed.

Since drivers are installed, WHY can't I add the 440?  Where are these drivers supposed to be located?

Many hours invested searching for answers and trying suggested solutions.  Getting rather frustrated here.  Lost everything with the bad initial up grade to 11.04, so may just re-install 10.10 and forget about it.

---

### Post by kidsil on 2011-05-12
This guide is critical!

Here are links to the files mentioned in the guide,
I've uploaded them to my rapidshare account
since they are almost impossible to find:

**mfc210clpr-1.0.2-1.i386.deb**
[https://rapidshare.com/files/409075112/mfc210clpr-1.0.2-1.i386.deb](https://rapidshare.com/files/409075112/mfc210clpr-1.0.2-1.i386.deb)

**cupswrapperMFC210C-1.0.2-3.i386.deb**
[https://rapidshare.com/files/2393274682/cupswrapperMFC210C-1.0.2-3.i386.deb](https://rapidshare.com/files/2393274682/cupswrapperMFC210C-1.0.2-3.i386.deb)

**brscan2-0.2.4-0.i386.deb**
[https://rapidshare.com/files/3269319021/brscan2-0.2.4-0.i386.deb](https://rapidshare.com/files/3269319021/brscan2-0.2.4-0.i386.deb)

enjoy :)

---

### Post by Segarra on 2011-05-13
> **doubtful wisdom said:**
> I have now re-downloaded and re-installed 11.04 twice, just to be reasonably certain that the CD was not the problem.  I am just trying to get the MFC-440CN printer to work first.  I installed the drivers from Brother as I have done for other versions of Ubuntu.  The 440 is seen as attached to USB.  However, it will not add.  Drivers are not found.

Wiped out 11.04.  Re-installed from another CD and another download.  Used Synaptic supplied 440 drivers.  Printer will not add.  Driver not found.  Tried to install drivers from the Brother site, but dpkg did not want to do so, since I have "later" drivers installed.

Since drivers are installed, WHY can't I add the 440?  Where are these drivers supposed to be located?

Many hours invested searching for answers and trying suggested solutions.  Getting rather frustrated here.  Lost everything with the bad initial up grade to 11.04, so may just re-install 10.10 and forget about it.

Hi... I have the same printer and I was able to install drivers.
Did you follow those instructions?
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002)

The problem that I have now, is that the firs 3 or 4 lines are not printed.
But It works... my printer it's in the lan.

---

### Post by rgoddard on 2011-05-14
Thank you so much!  After trying several things, this way worked for me.

---

### Post by HoffmanP on 2011-05-16
Can someone help me to setup printer wireless setting? My printer is Brother MFC 255CW
I think I installed my driver properly, I can see the printer on my system setting. I haven't tried to print through usb cable. Never use it anymore so I don't keep it around my workdesk.

---

### Post by EmpireJones on 2011-06-10
My Brother HL-2170W stopped working after a recent update. This was resolved by running:

```
sudo aa-complain cupsd
```:popcorn:

---

### Post by crazykiller on 2011-06-14
I had stuck. But this [http://ubuntuforums.org/showpost.php?p=4014274&postcount=98]("http://ubuntuforums.org/showpost.php?p=4014274&postcount=98") solved my problem

The exact file were a different one, but the idea of changing the cupsd.conf to debug mode show me the guidline.

My exact ln is 
"sudo ln -s /usr/lib/libbrcomplpr2.so /usr/lib32/libbrcomplpr2.so"

Thank you all!

---

### Post by skidzo on 2011-07-07
Hi Brother users:

I call the perfect DCP-9055CDN my own, everything was working brilliant,
I could scan and I could print, and that was basically what I wanted.

I'm interested if the scan to PC from the printer menue could also work with my linux machines yet it only works with my windows laptop...

Now my problem is, and I think most of you will also run into this:

I recently dist-upgraded to kubuntu 11.04 and during this upgrade I had run into a problem with cupsd, there is a bug description on launchpad Bug # 705067.

in my case the upgrade got stuck at installing the new cups.conf and opening a new shell and running the command 'stop cups' let me finish the distribution upgrade.

I only found this solution in the sudo do-release-upgrade way...

```

dpkg  -l  |  grep  Brother
rFR dcp9055cdncupswrapper:i386            1.1.1-5                                        Brother CUPS Laser Printer Definitions
ii  dcp9055cdnlpr:i386                    1.1.1-5                                        Brother lpr Laser Printer Definitions

```

If someone knows how to repair the printer setup please let me know...

Cheers Skidzo

---

### Post by WasMeHere on 2011-07-14
Thanks a lot!

This howto worked perfectly for me when installing the Brother printer HL-2250DN to be reached from Ubuntu 10.04 via Ethernet. The only thing not mentioned was to select network instead of usb in the printer menu, but that was easy to find.

Olle

---

### Post by fettuohi on 2011-08-13
I've got a dcp7045n brother printer and it works fine. I can print, scan and copy. But printing from KDE applications like Kate, Kwrite, Koffice etc. gives bad margins. Everything is shifted up into the right corner, meaning that page is cut off on the right side and on the top. The print preview looks correct. Printing from a gtk app (openoffice, adobe reader etc.) works perfectly. Anybody got any ideas why this is happening??? This has been driving me nuts for many many months now.

---

### Post by Mediosordo on 2011-08-24
I hope someone can help me.

I've been trying all afternoon to configure my new Brother DCP-J315W on my Desktop Computer with Ubuntu 10.10. I've managed to configure the printer and scanner through USB, but not through wi-fi. I've followed the steps of this guide, creating the neccessary directories and using force-all to install the dcpj315wlpr-1.1.1-1.i386.deb & dcpj315wcupswrapper-1.1.1-1.i386.deb packages, with no use. Everytime I try to print a test page, it fails and the Ubuntu Diagnostics tells me it's not activated. I reactivate it and try again, and the same thing happens.

This is the report I get. I post it in full as I don't really know what parts are relevant.


```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Brother-DCP-J315W>,
 'cups_instance': None,
 'cups_queue': 'Brother-DCP-J315W',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'lpd',
 'cups_printer_dict': {'device-uri': u'lpd://dhcppc7/BINARY_P1',
                       'printer-info': u'Brother DCP-J315W',
                       'printer-is-shared': True,
                       'printer-location': u'dhcppc7',
                       'printer-make-and-model': u'Brother DCP-J315W CUPS',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8392780,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Brother-DCP-J315W'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.4',
                                 'device-uri': u'lpd://dhcppc7/BINARY_P1',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
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
                                 'generated-natural-language-supported': [u'en-us'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'ippget-event-life': 15,
                                 'job-creation-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'ipp-attribute-fidelity',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'job-sheets',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
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
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
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
                                 'media-bottom-margin-supported': [493, 35],
                                 'media-col-supported': [u'media-bottom-margin',
                                                         u'media-left-margin',
                                                         u'media-right-margin',
                                                         u'media-size',
                                                         u'media-source',
                                                         u'media-top-margin',
                                                         u'media-type'],
                                 'media-default': u'iso_a4_210x297mm',
                                 'media-left-margin-supported': [493, 35],
                                 'media-right-margin-supported': [493,
                                                                  0,
                                                                  529,
                                                                  35,
                                                                  458,
                                                                  1023,
                                                                  564],
                                 'media-supported': [u'iso_a4_210x297mm',
                                                     u'om_br-a4-b_209.9x297.03mm',
                                                     u'na_letter_8.5x11in',
                                                     u'oe_br-letter-b_8.5x11in',
                                                     u'na_legal_8.5x14in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'jis_b5_182x257mm',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'om_br-a6-b_114.65x156.98mm',
                                                     u'oe_post-c4x6_4x6in',
                                                     u'oe_br-post-c4x6-b_4x6in',
                                                     u'oe_index-c5x8_5x8in',
                                                     u'oe_br-index-c5x8-b_5x8in',
                                                     u'oe_photo-l_3.5x5in',
                                                     u'oe_br-photo-l-b_3.5x5in',
                                                     u'om_photo2-l_126.64x178.15mm',
                                                     u'om_br-photo2-l-b_126.64x178.15mm',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'om_br-hagaki-b_100.18x147.81mm',
                                                     u'jpn_oufuku_148x200mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_dl_110x220mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'jpn_you4_105x235mm'],
                                 'media-top-margin-supported': [599,
                                                                141,
                                                                635,
                                                                176,
                                                                1023,
                                                                1975,
                                                                670],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en-us',
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
                                 'output-bin-default': u'face-up',
                                 'output-bin-supported': [u'face-up'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 12,
                                 'pages-per-minute-color': 12,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'Brother DCP-J315W',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'dhcppc7',
                                 'printer-make-and-model': u'Brother DCP-J315W CUPS',
                                 'printer-more-info': u'http://localhost:631/printers/Brother-DCP-J315W',
                                 'printer-name': u'Brother-DCP-J315W',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-resolution-default': '(unknown IPP tag)',
                                 'printer-resolution-supported': '(unknown IPP tag)',
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1314207658,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8392780,
                                 'printer-up-time': 1314207666,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Brother-DCP-J315W'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Color Enhancement': {u'BRBlue': u'0',
                                                      u'BRBrightness': u'0',
                                                      u'BRColorEnhancement': u'OFF',
                                                      u'BRContrast': u'0',
                                                      u'BRGreen': u'0',
                                                      u'BRRed': u'0'},
                               u'General': {u'BRBiDir': u'ON',
                                            u'BRColorMediaType': u'Plain',
                                            u'BRColorPaperThick': u'Regular',
                                            u'BRJpeg': u'Recommended',
                                            u'BRMonoColor': u'Color',
                                            u'BRResolution': u'600x600dpi',
                                            u'BRReverse': u'OFF',
                                            u'BRSlowDrying': u'OFF',
                                            u'BrMirror': u'OFF',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4'},
                               u'Image Type': {u'BRColorMatching': u'Natural',
                                               u'BRHalfTonePattern': u'Diffusion'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'network',
                      'device-id': u'MFG:Brother;CMD:HBP,BRPJL;MDL:DCP-J315W;CLS:PRINTER;',
                      'device-info': u'Brother DCP-J315W',
                      'device-location': u'',
                      'device-make-and-model': u'Brother DCP-J315W'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': '',
                          'DefaultAuthType': 'Basic',
                          'LogLevel': 'warn',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '1',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 387457L,
 'error_log_debug_logging_set': True}
Page 8 (Error log fetch):
{'error_log': ['D [24/Aug/2011:19:41:29 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:29 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:29 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:29 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:29 +0200] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [24/Aug/2011:19:41:29 +0200] Get-Jobs ipp://localhost/printers/',
               'D [24/Aug/2011:19:41:29 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [24/Aug/2011:19:41:29 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:29 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:29 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:29 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:29 +0200] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [24/Aug/2011:19:41:29 +0200] Get-Jobs ipp://localhost/printers/',
               'D [24/Aug/2011:19:41:29 +0200] [Job 5] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] [Job 6] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] [Job 7] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] [Job 8] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] [Job 9] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] [Job 10] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] [Job 11] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] [Job 13] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] [Job 14] Loading attributes...',
               'D [24/Aug/2011:19:41:29 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [24/Aug/2011:19:41:29 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:29 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:29 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:29 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:29 +0200] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1',
               'D [24/Aug/2011:19:41:29 +0200] Create-Printer-Subscription /',
               'D [24/Aug/2011:19:41:29 +0200] cupsdCreateSubscription(con=0x217b2988(12), uri="/")',
               'D [24/Aug/2011:19:41:29 +0200] pullmethod="ippget"',
               'D [24/Aug/2011:19:41:29 +0200] notify-lease-duration=86400',
               'D [24/Aug/2011:19:41:29 +0200] notify-time-interval=0',
               'D [24/Aug/2011:19:41:29 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [24/Aug/2011:19:41:29 +0200] Added subscription 23 for server',
               'D [24/Aug/2011:19:41:29 +0200] cupsdMarkDirty(-----S)',
               'D [24/Aug/2011:19:41:29 +0200] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [24/Aug/2011:19:41:29 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:30 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:30 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:30 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:30 +0200] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:30 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:30 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:30 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:30 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:35 +0200] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [24/Aug/2011:19:41:35 +0200] cupsdReadClient: 13 POST /printers/Brother-DCP-J315W HTTP/1.1',
               'D [24/Aug/2011:19:41:35 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:35 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:35 +0200] cupsdReadClient: 13 1.1 Print-Job 1',
               'D [24/Aug/2011:19:41:35 +0200] Print-Job ipp://localhost/printers/Brother-DCP-J315W',
               'D [24/Aug/2011:19:41:35 +0200] [Job ???] Auto-typing file...',
               'I [24/Aug/2011:19:41:35 +0200] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [24/Aug/2011:19:41:35 +0200] cupsdMarkDirty(----J-)',
               'D [24/Aug/2011:19:41:35 +0200] add_job: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:35 +0200] Adding default job-sheets values "none,none"...',
               'I [24/Aug/2011:19:41:35 +0200] [Job 15] Adding start banner page "none".',
               'D [24/Aug/2011:19:41:35 +0200] cupsdMarkDirty(-----S)',
               'D [24/Aug/2011:19:41:35 +0200] cupsdMarkDirty(----J-)',
               'I [24/Aug/2011:19:41:35 +0200] [Job 15] Adding end banner page "none".',
               'I [24/Aug/2011:19:41:35 +0200] [Job 15] File of type application/vnd.cups-banner queued by "manuel".',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] hold_until=0',
               'I [24/Aug/2011:19:41:35 +0200] [Job 15] Queued on "Brother-DCP-J315W" by "manuel".',
               'D [24/Aug/2011:19:41:35 +0200] cupsdMarkDirty(----J-)',
               'D [24/Aug/2011:19:41:35 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Aug/2011:19:41:35 +0200] cupsdMarkDirty(-----S)',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] job-sheets=none,none',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] argv[0]="Brother-DCP-J315W"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] argv[1]="15"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] argv[2]="manuel"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] argv[3]="Test Page"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] argv[4]="1"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] argv[5]="job-uuid=urn:uuid:4baf46e4-0964-3328-795a-9b0e5516dd27 job-originating-host-name=localhost"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] argv[6]="/var/spool/cups/d00015-001"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[10]="SERVER_ADMIN=root@manuel-Sinosuke"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[11]="SOFTWARE=CUPS/1.4.4"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[13]="USER=root"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[16]="IPP_PORT=631"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[17]="CHARSET=utf-8"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[18]="LANG=es_ES.UTF-8"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[19]="PPD=/etc/cups/ppd/Brother-DCP-J315W.ppd"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[20]="RIP_MAX_CACHE=auto"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[22]="DEVICE_URI=lpd://dhcppc7/BINARY_P1"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[23]="PRINTER_INFO=Brother DCP-J315W"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[24]="PRINTER_LOCATION=dhcppc7"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[25]="PRINTER=Brother-DCP-J315W"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[26]="CUPS_FILETYPE=document"',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] envp[27]="FINAL_CONTENT_TYPE=printer/Brother-DCP-J315W"',
               'I [24/Aug/2011:19:41:35 +0200] [Job 15] Started filter /usr/lib/cups/filter/bannertops (PID 2602)',
               'I [24/Aug/2011:19:41:35 +0200] [Job 15] Started filter /usr/lib/cups/filter/pstops (PID 2603)',
               'I [24/Aug/2011:19:41:35 +0200] [Job 15] Started filter /usr/lib/cups/filter/brlpdwrapperdcpj315w (PID 2604)',
               'I [24/Aug/2011:19:41:35 +0200] [Job 15] Started backend /usr/lib/cups/backend/lpd (PID 2605)',
               'D [24/Aug/2011:19:41:35 +0200] cupsdMarkDirty(-----S)',
               'D [24/Aug/2011:19:41:35 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Brother-DCP-J315W) from localhost',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] STATE: +connecting-to-device',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] Looking up "dhcppc7"...',
               'D [24/Aug/2011:19:41:35 +0200] cupsdMarkDirty(-----S)',
               'D [24/Aug/2011:19:41:35 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] load_banner(filename="/var/spool/cups/d00015-001")',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] Page = 595x842; 14,14 to 581,825',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] Page = 595x842; 14,14 to 581,825',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] slow_collate=0, slow_duplex=0, slow_order=1',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] Before copy_comments - %!PS-Adobe-3.0',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %!PS-Adobe-3.0',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%BoundingBox: 14 14 581 825',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %cupsRotation: 0',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%Creator: bannertops/CUPS v1.4.4',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%CreationDate: mi\xc3\xa9 24 ago 2011 19:41:35 CEST',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%LanguageLevel: 2',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%DocumentData: Clean7Bit',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%Title: (Test Page)',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%For: (manuel)',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%Pages: 1',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%DocumentSuppliedResources: font Monospace',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%+ font Monospace-Bold',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%+ font Monospace-BoldOblique',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%+ font Monospace-Oblique',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] %%EndComments',
               'D [24/Aug/2011:19:41:35 +0200] [Job 15] Before copy_prolog - %%BeginProlog',
               "E [24/Aug/2011:19:41:36 +0200] [Job 15] No se ha podido localizar la impresora 'dhcppc7'.",
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] Set job-printer-state-message to "No se ha podido localizar la impresora \'dhcppc7\'.", current level=ERROR',
               'D [24/Aug/2011:19:41:36 +0200] cupsdMarkDirty(-----S)',
               'D [24/Aug/2011:19:41:36 +0200] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [24/Aug/2011:19:41:36 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.36:631',
               'D [24/Aug/2011:19:41:36 +0200] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [24/Aug/2011:19:41:36 +0200] cupsdNetIFUpdate: "eth0" = fe80::207:e9ff:fee7:b43d%eth0:631',
               'D [24/Aug/2011:19:41:36 +0200] PID 2605 (/usr/lib/cups/backend/lpd) stopped with status 4!',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] Before copy_setup - %%Page: coverpage 1',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] Before page loop - %%Page: coverpage 1',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] Copying page 1...',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] pagew = 567.0, pagel = 811.0',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] PageLeft = 14.0, PageRight = 581.0',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] PageTop = 825.0, PageBottom = 14.0',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] PageWidth = 595.0, PageLength = 842.0',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [24/Aug/2011:19:41:36 +0200] Get-Jobs ipp://localhost/printers/',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 18 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:36 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:36 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:36 +0200] cupsdCloseClient: 17',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:36 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:36 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:36 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:36 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:36 +0200] cupsdCloseClient: 17',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1',
               'D [24/Aug/2011:19:41:36 +0200] CUPS-Get-Printers',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Classes 1',
               'D [24/Aug/2011:19:41:36 +0200] CUPS-Get-Classes',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Default 1',
               'D [24/Aug/2011:19:41:36 +0200] CUPS-Get-Default',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] PID 2603 (/usr/lib/cups/filter/pstops) exited with no errors.',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:36 +0200] [Job 15] Wrote 1 pages...',
               'D [24/Aug/2011:19:41:36 +0200] PID 2602 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 19 1.1 Get-Job-Attributes 1',
               'D [24/Aug/2011:19:41:36 +0200] Get-Job-Attributes ipp://localhost/jobs/15',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:36 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:36 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1',
               'D [24/Aug/2011:19:41:36 +0200] CUPS-Get-Printers',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Classes 1',
               'D [24/Aug/2011:19:41:36 +0200] CUPS-Get-Classes',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Default 1',
               'D [24/Aug/2011:19:41:36 +0200] CUPS-Get-Default',
               'D [24/Aug/2011:19:41:36 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [24/Aug/2011:19:41:36 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Aug/2011:19:41:36 +0200] cupsdReadClient: 19 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:36 +0200] cupsdCloseClient: 19',
               'D [24/Aug/2011:19:41:37 +0200] PID 2604 (/usr/lib/cups/filter/brlpdwrapperdcpj315w) exited with no errors.',
               'I [24/Aug/2011:19:41:37 +0200] [Job 15] Backend returned status 4 (stop printer)',
               'D [24/Aug/2011:19:41:37 +0200] cupsdMarkDirty(-----S)',
               'I [24/Aug/2011:19:41:37 +0200] [Job 15] Printer stopped due to backend errors; please consult the error_log file for details.',
               'D [24/Aug/2011:19:41:37 +0200] cupsdMarkDirty(----J-)',
               'D [24/Aug/2011:19:41:37 +0200] cupsdMarkDirty(-----S)',
               'D [24/Aug/2011:19:41:37 +0200] cupsdMarkDirty(P-----)',
               'D [24/Aug/2011:19:41:37 +0200] cupsdRegisterPrinter(p=0x21752f00(Brother-DCP-J315W))',
               'D [24/Aug/2011:19:41:37 +0200] cupsdMarkDirty(P-----)',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:38 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:38 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:38 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:38 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:38 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:38 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:38 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 19 1.1 Get-Jobs 1',
               'D [24/Aug/2011:19:41:38 +0200] Get-Jobs ipp://localhost/printers/',
               'D [24/Aug/2011:19:41:38 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 19 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:38 +0200] cupsdCloseClient: 19',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:38 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:38 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:38 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:38 +0200] cupsdCloseClient: 16',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 18 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:38 +0200] cupsdCloseClient: 18',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:38 +0200] cupsdCloseClient: 17',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Printers 1',
               'D [24/Aug/2011:19:41:38 +0200] CUPS-Get-Printers',
               'D [24/Aug/2011:19:41:38 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [24/Aug/2011:19:41:38 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:38 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Classes 1',
               'D [24/Aug/2011:19:41:38 +0200] CUPS-Get-Classes',
               'D [24/Aug/2011:19:41:38 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [24/Aug/2011:19:41:38 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 20 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:38 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 20 1.1 CUPS-Get-Default 1',
               'D [24/Aug/2011:19:41:38 +0200] CUPS-Get-Default',
               'D [24/Aug/2011:19:41:38 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [24/Aug/2011:19:41:38 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:38 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:38 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:38 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:38 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:38 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:38 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:38 +0200] cupsdReadClient: 19 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:38 +0200] cupsdCloseClient: 19',
               'D [24/Aug/2011:19:41:48 +0200] cupsdReadClient: 13 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:48 +0200] cupsdCloseClient: 13',
               'D [24/Aug/2011:19:41:48 +0200] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [24/Aug/2011:19:41:49 +0200] cupsdReadClient: 13 POST /jobs/ HTTP/1.1',
               'D [24/Aug/2011:19:41:49 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:49 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:49 +0200] cupsdReadClient: 13 1.1 Cancel-Job 1',
               'D [24/Aug/2011:19:41:49 +0200] Cancel-Job ipp://localhost/jobs/15',
               'D [24/Aug/2011:19:41:49 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:49 +0200] cupsdMarkDirty(-----S)',
               'I [24/Aug/2011:19:41:49 +0200] [Job 15] Job canceled by "manuel"',
               'D [24/Aug/2011:19:41:49 +0200] cupsdMarkDirty(----J-)',
               'I [24/Aug/2011:19:41:49 +0200] [Job 15] Canceled by "manuel".',
               'D [24/Aug/2011:19:41:49 +0200] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/15) from localhost',
               'D [24/Aug/2011:19:41:49 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:49 +0200] cupsdReadClient: 13 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:49 +0200] cupsdCloseClient: 13',
               'D [24/Aug/2011:19:41:49 +0200] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [24/Aug/2011:19:41:49 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:49 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:49 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:49 +0200] cupsdReadClient: 13 1.1 Get-Notifications 1',
               'D [24/Aug/2011:19:41:49 +0200] Get-Notifications /',
               'D [24/Aug/2011:19:41:49 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:49 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Aug/2011:19:41:49 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:49 +0200] cupsdReadClient: 13 WAITING Closing on EOF',
               'D [24/Aug/2011:19:41:49 +0200] cupsdCloseClient: 13',
               'D [24/Aug/2011:19:41:50 +0200] [Job 15] Unloading...',
               'D [24/Aug/2011:19:41:51 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:51 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:51 +0200] cupsdReadClient: 12 1.1 Get-Job-Attributes 1',
               'D [24/Aug/2011:19:41:51 +0200] Get-Job-Attributes ipp://localhost/jobs/15',
               'D [24/Aug/2011:19:41:51 +0200] [Job 15] Loading attributes...',
               'D [24/Aug/2011:19:41:51 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:51 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:51 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:51 +0200] cupsdReadClient: 12 1.1 Cancel-Subscription 1',
               'D [24/Aug/2011:19:41:51 +0200] Cancel-Subscription /',
               'D [24/Aug/2011:19:41:51 +0200] cupsdIsAuthorized: requesting-user-name="manuel"',
               'D [24/Aug/2011:19:41:51 +0200] cupsdMarkDirty(-----S)',
               'D [24/Aug/2011:19:41:51 +0200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:51 +0200] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:51 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Aug/2011:19:41:51 +0200] cupsdIsAuthorized: username=""',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSendHeader: 12 WWW-Authenticate: Basic realm="CUPS", trc="y"',
               'D [24/Aug/2011:19:41:51 +0200] cupsdCloseClient: 12',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:51 +0200] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [24/Aug/2011:19:41:51 +0200] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Aug/2011:19:41:51 +0200] cupsdAuthorize: Authorized as manuel using PeerCred',
               'D [24/Aug/2011:19:41:51 +0200] cupsdIsAuthorized: username="manuel"',
               'I [24/Aug/2011:19:41:51 +0200] Installing config file "/etc/cups/cupsd.conf"...',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Dirty files',
               'D [24/Aug/2011:19:41:51 +0200] cupsdCloseClient: 20',
               'D [24/Aug/2011:19:41:51 +0200] cupsdCloseClient: 12',
               'D [24/Aug/2011:19:41:51 +0200] cupsdDeregisterPrinter(p=0x21731ce8(Brother), removeit=1)',
               'D [24/Aug/2011:19:41:51 +0200] cupsdDeregisterPrinter(p=0x21752f00(Brother-DCP-J315W), removeit=1)',
               'D [24/Aug/2011:19:41:51 +0200] cupsdDeregisterPrinter(p=0x217368d0(DCP-J315W), removeit=1)',
               'I [24/Aug/2011:19:41:51 +0200] Saving printers.conf...',
               'I [24/Aug/2011:19:41:51 +0200] Generating printcap /var/run/cups/printcap...',
               'I [24/Aug/2011:19:41:51 +0200] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [24/Aug/2011:19:41:51 +0200] Saving subscriptions.conf...',
               'D [24/Aug/2011:19:41:51 +0200] cupsdSetBusyState: Not busy',
               'I [24/Aug/2011:19:42:05 +0200] Listening to 0.0.0.0:631 (IPv4)',
               'I [24/Aug/2011:19:42:05 +0200] Listening to :::631 (IPv6)',
               'I [24/Aug/2011:19:42:05 +0200] Listening to /var/run/cups/cups.sock (Domain)'],
 'error_log_debug_logging_unset': True}
Page 9 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'es_ES',
 'user_locale_messages': 'es_ES'}
```Many thanks!!

---

### Post by alecxs on 2011-09-06
I have not followed all the pages, so I'm not sure if this was said before. 

On the brother website, there is an FAQ which provides a universal installer for brother printers. My network printer (HL-2250DN) worked flawlessly after trying all solutions with no result.   

[URL="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090"]http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090  
[/URL] 
This is the blog post that led me there:  

[URL="http://www.associatedcontent.com/article/5976666/the_retail_detail_brother_releases.html"]http://www.associatedcontent.com/article/5976666/the_retail_detail_brother_releases.html  
[/URL] 
When I was prompted for the URI of the printer, I chose (through trial and error) the option to specify the IP of the printer (I did know it, though).  

Hope this helps anyone.

---

### Post by PakeJow on 2011-09-17
i cant get my printer to work over a network. the printers drivers installed correctly, and its reognized in the "printers" menu.
but it says "printer may not be connected" 
for the URl it says :usb:/dev/usb/lp0
but i want it to be used wirelessly, so shouldnt it say the printers IP adress that i gave to set it up?
kind of a newb, help please :???:

---

### Post by photonian on 2011-10-30
For Wireless and Wired Printer Driver setup:

This worked for my wireless Brother MFC-665CW. 
[NOTE: If you have another model just search for it in your software manager - you may have to turn on multiverse repository too]

Printer Driver is already in Ubuntu's Multiverse Repository.
Just goto synaptic and install:
brother-lpr-drivers-bh7       [or whatever package includes your printers driver - see note above]

Then install the printer using your printer manager. (the driver should be automatically selected for you.)

--------------------------------------------   
For Scanner on wireless setup:

*download* and *install*: appropriate brscan package from Brother's Site: [Here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html")

Then inside a terminal enter: brsaneconfig2 -a name=[COLOR="DarkRed"]whatever-name-you-choose[/COLOR] model=[COLOR="DarkRed"]Your-Printer-Model[/COLOR] ip=192.168.[COLOR="DarkRed"]x[/COLOR].[COLOR="DarkRed"]x[/COLOR]
[NOTE: Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models) or brsaneconfig3 (for brscan3 models) accordingly.

That's it, you can use your scanner software now.

---

### Post by Jose Catre-Vandis on 2011-11-04
Anyone had this problem and solved it?

Brother DCP-540CN, print and scan drivers all working fine on Xubuntu 11.10. Up until now, the driver has never recognised or done anything with ink levels, but having replaced a colour catridge, the driver now complains that I have no ink left, and refuses to print. I was able to get the print run through by switching off and on the printer. However the error message still remains....

---

### Post by puntigamer on 2011-11-30
HI guys, I've just installed my DCP-165C cups driver, and it works fine for me. But the scan drivers don't, the brscan can't see my device... I've got all the needed drivers installed, and added the ```

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```
to /lib/udev/rules.d/40-libsane.rules

Any idea?


```
daniel@oneiric:~$ dpkg  -l  |  grep  Brother
ii  brscan-skey                                    0.2.1-3                                 Brother Linux scanner S-KEY tool
ii  brscan3                                        0.2.11-4                                Brother Scanner Driver
ii  dcp165ccupswrapper:i386                        1.1.2-2                                 Brother CUPS Inkjet Printer Definitions
ii  dcp165clpr:i386                                1.1.2-2                                 Brother lpr Inkjet Printer Definitions
ii  dcp195ccupswrapper:i386                        1.1.2-2                                 Brother CUPS Inkjet Printer Definitions
ii  dcp195clpr:i386                                1.1.2-1                                 Brother lpr Inkjet Printer Definitions
ii  ptouch-driver                                  1.3-0ubuntu11                           CUPS/Foomatic driver for Brother P-touch label printers
```

---

### Post by RefinersFire on 2011-12-04
ubuntu 11.04. Followed Brother's instructions precisely. Worked like a charm on my wife's 10.10 system. Will not work on this 11.04 system. Tried some of the suggestions here.

The printer shows up but will not print, clean heads, etc.

Any help will be appreciated.

---

### Post by War Tribe on 2011-12-11
Is there anything like this for a lexmark x4650 3 in one printer?

---

### Post by jfbooth on 2011-12-11
> **War Tribe said:**
> Is there anything like this for a lexmark x4650 3 in one printer?

Google search on:

lexmark x4650 ubuntu

About 40,200 results

---

### Post by rykel on 2011-12-15
I am now using Linux Mint 12 and while it is not Ubuntu, I believe the printer application is the same.

I noticed that before printing, the tabs in the pop-up dialog no longer offer the choice of "Draft" or "Normal" when printing PDFs. I assume that the "Normal" (ie. NON-toner saving) mode is enabled as default.

My printer is a Brother HL-2140L.

Would you know how to reset the application to be what it used to be under Maverick?

---

### Post by kurt18947 on 2011-12-15
> **rykel said:**
> I am now using Linux Mint 12 and while it is not Ubuntu, I believe the printer application is the same.

I noticed that before printing, the tabs in the pop-up dialog no longer offer the choice of "Draft" or "Normal" when printing PDFs. I assume that the "Normal" (ie. NON-toner saving) mode is enabled as default.

My printer is a Brother HL-2140L.

Would you know how to reset the application to be what it used to be under Maverick?

I've only used Mint 12 as a live session, I've never installed it to a hard drive.  Mint 12 is based on Gnome 3 shell which is my default.  Your problem with the inability to set default print modes seems like a shortcoming of Gnome shell's interface.  Unity and Xfce-desktop offer more printer options than Gnome 3 shell and I assume Mint 12. Below is my printer window:
[ATTACH]209143[/ATTACH]
Options is print jobs, not printer settings.  I can usually select print quality from within applications but it's a bother to change it each time.

---

### Post by rykel on 2011-12-17
> **kurt18947 said:**
> I've only used Mint 12 as a live session, I've never installed it to a hard drive.  Mint 12 is based on Gnome 3 shell which is my default.  Your problem with the inability to set default print modes seems like a shortcoming of Gnome shell's interface.  Unity and Xfce-desktop offer more printer options than Gnome 3 shell and I assume Mint 12. Below is my printer window:
[ATTACH]209143[/ATTACH]
Options is print jobs, not printer settings.  I can usually select print quality from within applications but it's a bother to change it each time.

I am inclined to understand it so too... the only problem is, even within applications, it might NOT be possible to change printer settings.

For example, if I am printing a webpage (HTML), it will give me printer settings (ie. "Normal" vs "Draft" aka Toner-Save?) but if I am printing a PDF, then the entire printer settings tab is simply gone.

What gives?

---

### Post by YMS_1975 on 2011-12-17
WOW,

That was a lot to read!!!! I'm running Ubuntu 11.10 and I've got the MFC-465CN Brother Multi-Function. I just can't get it to scan. I can get it to print....but not scan.

Can anybody help me? I've gone through so many different tips and tricks but it just won't work.

Anybody????    :confused:

---

### Post by mechanizedmedic on 2011-12-26
> **YMS_1975 said:**
> WOW,

That was a lot to read!!!! I'm running Ubuntu 11.10 and I've got the MFC-465CN Brother Multi-Function. I just can't get it to scan. I can get it to print....but not scan.

Can anybody help me? I've gone through so many different tips and tricks but it just won't work.

Anybody????    :confused:
Brother has a driver/utility for this machine called brscan2. The download and instructions are [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan2"). This should allow you to use the SCAN button on the machine but IMO it's easier to just use Xsane as you can pick the file name, save location and format in advance.

---

### Post by YMS_1975 on 2011-12-26
> **mechanizedmedic said:**
> Brother has a driver/utility for this machine called brscan2. The download and instructions are [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan2"). This should allow you to use the SCAN button on the machine but IMO it's easier to just use Xsane as you can pick the file name, save location and format in advance.

I downloaded the Brscan2 but the scanner STILL isn't working.  :(
Has anybody who has my version of Ubuntu and this exact same model got it to work??????????

Maybe I'm doing something wrong.

---

### Post by tomek_wap on 2011-12-31
i don't know why, but scanner drivers used to work.
then they stopped.
tried to install all from scratch, printer works as always, no problems at all.

when trying to install brscan2 with given command:
sudo apt-get install brscan2-0.2.5-1.i386.deb

shows error message: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brscan2-0.2.5-1.i386.deb
E: Couldn't find any package by regex 'brscan2-0.2.5-1.i386.deb'

Running command:
brsaneconfig2 -q    shows

 1 BROTHER-SCANNER     "DCP-540CN"         I:192.168.2.20

which is all correct.

Running xsane, shows that no scanner drivers were found.

How to get it to work again?
Thnx

---

### Post by newb85 on 2011-12-31
I followed the normal installation procedures for a MFC-3360C on Oneiric.  Unfortunately, neither xsane nor the simple scan utility find my scanner.  

This scanner worked perfectly using the same procedures on my old machine running natty until a couple months ago, when that machine's graphics card died, rendering the machine a high-tech paperweight.  This is the first time I've tried to install the scanner since then.

Running > sane-find-scanner does find the scanner.  However, running > scanimage -L does not.

---

### Post by newb85 on 2011-12-31
> **tomek_wap said:**
> 
E: Unable to locate package brscan2-0.2.5-1.i386.deb
E: Couldn't find any package by regex 'brscan2-0.2.5-1.i386.deb'
Thnx

Sounds to me like you either didn't type the name of the driver correctly or weren't in the folder containing the driver when you ran the install command.

---

### Post by tomek_wap on 2011-12-31
> **newb85 said:**
> Sounds to me like you either didn't type the name of the driver correctly or weren't in the folder containing the driver when you ran the install command.

The thing is that the driver name (file name) was entered correctly, as I was in correct folder.
The procedure was exactly the same as before when I installed my Brother device (1-2 months ago) - i.e. dragging with mouse to terminal, so there was no chance for a typo.
But I also moved into the right folder, and typed in the driver name correctly.

PS. just about I managed to install brscan2 with no problems, no errors came up, all seems OK. But still no scanner was found by XSANE.

PS.2. When running XSANE, it shows "no devices available" - just to be clear.

PS.3. Intalled drivers using sudo dpkg -i --force-all, to see how it works ... gives me terminal message

(Reading database ... 227436 files and directories currently installed.)
Preparing to replace brscan2:i386 0.2.5-1 (using .../brscan2-0.2.5-1.i386.deb) ...
Unpacking replacement brscan2:i386 ...
Setting up brscan2:i386 (0.2.5-1) ...

So it seems OK.


Also... when checking drivers it shows:

ic  brscan2                                0.2.5-1                                 Brother Scanner Driver
ii  brscan2:i386                           0.2.5-1                                 Brother Scanner Driver
ii  dcp540cncupswrapper:i386               1.0.1-1                                 Brother CUPS Inkjet Printer Definitions
ii  dcp540cnlpr:i386                       1.0.1-1                                 Brother lpr Inkjet Printer Definitions
ii  ptouch-driver                          1.3-0ubuntu11                           CUPS/Foomatic driver for Brother P-touch label printers

---

### Post by kurt18947 on 2011-12-31
Re scanning in 11.10.  There's an install glitch, fix is here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)
This problem was still around after 11.10 was released.

---

### Post by tomek_wap on 2011-12-31
> **kurt18947 said:**
> Re scanning in 11.10.  There's an install glitch, fix is here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)
This problem was still around after 11.10 was released.

It works!!  Thnx!!!

I wonder why it all worked before (in 11.10) ... and not it didn't until I've copied the files.
Now I was thinking, maybe before it worked in 11.10 32-bit, and never tried to scan in 64-bit, just installed drivers and assumed that it's all working.

Brother should do a proper/official package/application for Linux, like they have it for Windows or Mac :)

---

### Post by rogerb1583 on 2012-01-13
I give up. I have wasted a couple of hours trying to get my Brother 6490CW driver stalled. I have not felt this stupid since DOS. I am going to buy an HP printer. At least they support Ubuntu Linux. 

El Stupido

---

### Post by jfbooth on 2012-02-02
**XUBUNTU 11.10.  NETWORKED MFC-7440N PRINTER/SCANNER**

Used to work .. but stopped printing/scanning at some unknown point, possibly when I upgraded from 11.04.

I have managed to get it printing again, but after reading this entire thread and trying 'everything' I could .. I now need help getting it to scan.

When I run XSANE I get an error window:

[COLOR="Red"]Failed to open device 'brother3:net 1;dev0': Invalid argument[/COLOR]

```
jb@Compaq:~$ dpkg  -l  |  grep  Brother
ii  brmfc7440nlpr                          2.0.2-1
   Brother MFC-7440N LPR driver
ii  brscan-skey                            0.2.1-3
   Brother Linux scanner S-KEY tool
ii  brscan3                                0.2.11-4
   Brother Scanner Driver
ii  cupswrappermfc7440n                    2.0.2-1
   Brother MFC7440N CUPS wrapper driver
ii  ptouch-driver                          1.3-0ubuntu11
   CUPS/Foomatic driver for Brother P-touch label printers
jb@Compaq:~$
```

Not sure what else to say.  I have read and complied with BROTHER FAQ tips, and tried most of the advice given in this thread.  Thank you in advance to anyone who can help me out.

---

### Post by YMS_1975 on 2012-02-03
> **rogerb1583 said:**
> I give up. I have wasted a couple of hours trying to get my Brother 6490CW driver stalled. I have not felt this stupid since DOS. I am going to buy an HP printer. At least they support Ubuntu Linux. 

El Stupido

You're not stupid.

This is quite tricky! LOL. I've been fiddling around with an MFC-465CN.

I downloaded the drivers from Brothers website, then I read that it was already in the repositories so there was no need to do that.
Then I uninstalled everything, and reinstalled from the repositories....STILL NO LUCK.  :(

So you're definitely not alone (or stupid).

---

### Post by jfbooth on 2012-02-03
> **rogerb1583 said:**
> I give up. I have wasted a couple of hours trying to get my Brother 6490CW driver stalled. I have not felt this stupid since DOS. I am going to buy an HP printer. At least they support Ubuntu Linux. 

El Stupido

No .. you are not stupid.  I spent almost a month just getting my printer to work .. and .. AND .. I am not sure what I did to fix it .. but it works!!  Now .. the scanner .. hopefully, much sooner.

This thread .. many, many compliments to it .. and it deserves compliments .. BUT it is REALLY outdated .. and is no longer a tutorial .. it is a 30 pg monster of redundant and outdated material.  There must be 10 replies that recommend editing 40-libsanerules or whatever it's called .. and it is not there.

I don't mean to beat on this thread .. it is just way outdated is all.

---

### Post by YMS_1975 on 2012-02-03
> **jfbooth said:**
> No .. you are not stupid.  I spent almost a month just getting my printer to work .. and .. AND .. I am not sure what I did to fix it .. but it works!!  Now .. the scanner .. hopefully, much sooner.

This thread .. many, many compliments to it .. and it deserves compliments .. BUT it is REALLY outdated .. and is no longer a tutorial .. it is a 30 pg monster of redundant and outdated material.  There must be 10 replies that recommend editing 40-libsanerules or whatever it's called .. and it is not there.

I don't mean to beat on this thread .. it is just way outdated is all.

Agreed (to a certain point).

I think what we should do, is dedicate a hardware section and break it down by peripheral **brand name, model # & Ubuntu version compatibility** (if such a section does not exist already).

And if it does exist.....then....we should be looking there!  :D

---

### Post by jfbooth on 2012-02-03
> **YMS_1975 said:**
> I downloaded the drivers from Brothers website, then I read that it was already in the repositories so there was no need to do that.
Then I uninstalled everything, and reinstalled from the repositories....STILL NO LUCK.  :(

So you're definitely not alone (or stupid).

Yeah .. I read that too, but I also read that those in the repositories only apply to certain models .. so I used the specified drivers from Brother's website.  If you are using the repository packages .. they STILL may not be right for your model printer.

---

### Post by jfbooth on 2012-02-03
> **YMS_1975 said:**
> I think what we should do, is dedicate a hardware section and break it down by peripheral **brand name, model # & Ubuntu version compatibility** (if such a section does not exist already).

And if it does exist.....then....we should be looking there!  :D

There certainly is a hardware section of this Forum .. but to my knowledge there is nothing there in particular about Brother Printers.  Maybe .. but this 'tutorial' is about the best thing I have found .. as lacking as it is.

I think TUTORIALS should be locked to replies.  That right there would reduce this one to a few posts .. all by the author of the tutorial.  Instead of 30 pages ..it could be cut down to one.  The author could edit/add to/expand the tutorial and keep it updated.  The feedback to the tutorial could be done in another thread.  What took me the longest and I still did not find the answer, was going through this entire thread ... all that 'input' is outdated, redundant, mistaken, misleading, and time consuming.

---

### Post by exsencon on 2012-02-09
Just my 2 cents. I just bought a Brother 195C all in one (the lights went out on my Canon Pixma MP520)and installed it on my WinXP desktop. Then I went about getting it to work on my Ubuntu 10.10 laptop over my home wireless connection. Went to the Brother website to get the Linux drivers for my 195C-no sweat. Just put in the IP of my desktop and I could print wirelessly from my Ubuntu laptop to my WinXP desktop that's connected to my new Brother with USB and of course shared printer. Great stuff!
See about the scanner later. Very good feeling about Brother and Linux!

---

### Post by jfbooth on 2012-02-09
> **exsencon said:**
> Great stuff!

I am sincerely glad you had so little trouble.  This is a 'good' tutorial .. if you are connected USB.  It only covers NETWORK connected through the evolution of replies .. so in that respect, it is a good tutorial .. but fails miserably for a networked Brother 'device' .. at this point.

---

### Post by exsencon on 2012-02-10
> **jfbooth said:**
> I am sincerely glad you had so little trouble.  This is a 'good' tutorial .. if you are connected USB.  It only covers NETWORK connected through the evolution of replies .. so in that respect, it is a good tutorial .. but fails miserably for a networked Brother 'device' .. at this point.

jfbooth
I understand your problem which is quite different of mine.I am in a home situation with two PC's(Desktop-Laptop).Laptop is connected wireless to my Linksys router with the Desktop and the internet and that's it.
Now,on my laptop I have WinXP and Ubuntu 10.10, on my Desktop I have WinXP on one HD and 12 Linux OS and Solaris and PCBSD on the second HD. So right now I am getting all those Linux OS's to work with my new Brother DCP195C. I am about half way and still going strong! I'll leave Solaris and PCBSD for last because they are tricky ones. But so far,so good.
I am still hoping printer manufacturers give the same treatment to Linux users as they do for Win users!

---

### Post by rcorea1563 on 2012-02-19
Your procedure worked fine for a network attached MFC-425CN on Ubuntu 10.04 (Lucid).
The installation assumed it was USB connected, but a visit to the CUPS admin page ([http://localhost:631](http://localhost:631)) ->Manage Printers -> Modify Printer resolved the problem. 
It discovered the networked printer and I just had to click on it.

Thank you for a detailed and accurate How To. Excellent.

---

### Post by crazyness003 on 2012-03-05
Hey guys (and gals). Here's a weird one:

I cannot get my Brother MFC-6665CW to print, but it scans beautifully.

I recently reinstalled Ubuntu 11.10 x64 on my desktop (coming from 10.04, I figured a clean reinstall would be best), and the first thing I did was get my printer/scanner to work.

I'm an intermediate user, and I breezed through the install for the printer. I set it up as a network printer since I plan on physically moving it in the near future. In the end I even printed a test page- successfully. No sweat.
Got through the scanner part, and after a couple of minutes I got that to work too, so I figured "GREAT SUCCESS!".

Yesterday, I went to print, so I selected the printer, it showed up, and even sent the job to spool, then it just completed...yet nothing printed. Its like the printer never got the instructions. I can still scan, but after countless failed attempts to print, reinstall drivers, use USB, wired, wirless, LDP, AppSocket, nothing works. I truly am stumped.

I tried setting the device uri to
dnssd://Brother%20MFC-665CW._pdl-datastream._tcp.local/  (done automatically when I select AppSocket/JetDirect)
dnssd://Brother%20MFC-665CW._printer._tcp.local/ (done automatically when I select LDP network printer)
usb://Brother/MFC-665CW?serial=BROD7F118271  (done automatically when I select USB)
ldp://192.168.0.165/binary_p1 (manual entry using assigend IP by DHCP)

I tried uninstalling the drivers (in my case the 'brother-lpr-driversbh7' and 'brother-cups-wrapper-bh7), reinstalling, purging, installing again from the brother site; all to no success. If anyone can give me some advice as to what else I can try, save for reinstalling ubuntu.

I'm not sure where to take it from here. So, thanks in advance.

Oh, I almost forgot, whenever it "completes" print jobs, it keeps complaining that I'm completely out of ink, yet my ink levels are satisfactory. Weird.

Again, thanks.

---

### Post by crazyness003 on 2012-03-07
bump?

---

### Post by ferdnyc on 2012-03-08
> **crazyness003 said:**
> ldp://192.168.0.165/binary_p1 (manual entry using assigend IP by DHCP)

I just want to make sure... this was just a typo in your post, right? Because, the line _should_ be:

lpd://192.168.0.165/BINARY_P1

**(Note the transposed second and third letters.)**

That's the address format my MFC-5460CN has been working successfully with for the past 3+ years, it should work for yours as well.

(BTW: I don't _believe_ the capitalization on "BINARY_P1" makes any difference.)

---

### Post by crazyness003 on 2012-03-15
Good sir, I don't know who you are, or where you're from, but I believe you deserve a beverage of your choice*

You are oh so very correct. 
[COLOR=Red]**ldp**[/COLOR] does [COLOR=Red]NOT[/COLOR] work
[COLOR=SeaGreen]**lpd**[/COLOR] on the other hand, [COLOR=SeaGreen]DOES[/COLOR].

Its these simple mistakes that make me wanna punch myself in the face sometimes.

You're a lifesaver. And I just noticed the 'Thanks' button is still missing. Because if it was present, I would have smashed my mouse pressing that thing (and I have a pretty bad-*** mouse)

*alcoholic beverages apply only if you are of the legal age in the locale you will be drinking said beverage.

---

### Post by ferdnyc on 2012-03-16
Glad to hear you got it worked out! :-)

The acronym thing is definitely an annoyance, you're not at all alone in that. I agree — ldp, lpd, lbj, who can keep the alphabet soup straight?

That kind of thing is why I'm a *_big_* proponent of learning the expansions for acronyms, even if (*especially* if!) they're "irrelevant" or "outdated". I just find it easier to remember phrases than jumbles of letters.

No, it's definitely not _relevant_ anymore that LPD stands for "Line Printer Daemon", and certainly nobody will ever "need" to know that. But once you do, you'll never misspell "LPD".

By the same token, I could _never_ remember how to spell PCMCIA, until I learned what it stands for. Which is, of course, "People Can't Memorize Computer Industry Acronyms". 

(Hey, I never said it was necessary to know the _correct_ expansion! That's the nice thing. Any phrase that fits will work just as well. Truth is, I'm not sure what PCMCIA properly stands for. Some string of generic near-meaningless buzzwords, no doubt. "Personal Computer Memory Card Interface Attachment"?)

---

### Post by weirdfate on 2012-04-13
sooooooo..... 

brothers mfc210c not working under 11.10?????

---

### Post by Fraoch on 2012-04-29
Just reinstalling this for 12.04 and I'm not sure if it's 12.04 or the recently updated Brother scan key tool/scanner driver (updated about a month ago) but these handy little scripts are gone.

Not the end of the world I suppose but it's a little annoying.:-(

> **Fraoch said:**
> I stumbled upon this post which improved the fax usage for my MFC:

[http://ubuntuforums.org/showpost.php?p=10624376&postcount=8](http://ubuntuforums.org/showpost.php?p=10624376&postcount=8)

Also I played around with the scripts that get executed when the machine keys are pressed to be a bit more useful to me.  Note this is newbie stuff because I'm a newbie, so don't expect anything dramatic.:)

First, the script at /usr/local/Brother/sane/script/scantofile-0.2.1-3.sh (the version numbers at the end of your script may be different).  This controls what happens when you select Scan to File on the machine.  By default, it scanned at 100 dpi in an unusual .PPM format and left the file in /home/[your user name]/brscan.

I changed it to 200 dpi because I always scale it down in another program - it's easy to scale down images, but impossible to scale up if you don't have enough detail.  Plus a 200 dpi full-page scan is still manageable across a wireless network, it's a little over 10 MB and takes about 10 seconds to transmit using "g" wireless networking.  I changed the file format to TIFF - I don't know much about .PPM and it could be compressed, I want the raw scan and I'll save it in the format of my choice.  Finally I always look at a scan in a graphics editor because it almost always needs to be cropped, at the very least, so I want to start GIMP automatically with this file loaded after the scan completes.

My modified script looks like this:

```
#! /bin/sh
set +o noclobber
#
#   $1 = scanner device
#   $2 = friendly name
#

#   
#       100,200,300,400,600
#
resolution=200
device=$1
mkdir -p ~/brscan
if [ "`which usleep`" != '' ];then
    usleep 10000
else
    sleep  0.01
fi
output_file=`mktemp ~/brscan/brscan.XXXXXX`
chmod 644 $output_file
echo "scan from $2($device) to $output_file"
scanimage --device-name "$device" --format=tiff --resolution $resolution> $output_file
echo gimp $output_file \;rm -f $output_file | sh &
```

To edit your script, use

```
gksudo gedit /usr/local/Brother/sane/script/scantofile-0.2.1-3.sh
```

, modifying the version number as necessary, and either overwrite the existing script with this one or change the number after "resolution" and the last two lines.

Other niceties which you might want but which I kept - change the location the files are sent to (change the "mkdir -p ~/brscan" line) and don't delete the initial raw scan after editing (remove "\;rm -f $output_file" at the end).

Next, /usr/local/Brother/sane/script/scantoimage-0.2.1-3.sh.  This one already called GIMP but I changed the resolution and file format:

```
#! /bin/sh
set +o noclobber
#
#   $1 = scanner device
#   $2 = friendly name
#

#   
#       100,200,300,400,600
#
resolution=200
device=$1
mkdir -p ~/brscan
if [ "`which usleep`" != '' ];then
    usleep 10000
else
    sleep  0.01
fi
output_file=`mktemp ~/brscan/brscan.XXXXXX`
echo "scan from $2($device) to $output_file"
scanimage --device-name "$device" --format=tiff --resolution $resolution> $output_file
echo gimp $output_file \;rm -f $output_file | sh &
```

Finally, /usr/local/Brother/sane/script/scantoocr-0.2.1-3.sh.  Turns out this one doesn't work by default at all - there were two lines at the end of the script which were supposed to say that OCR is not supported and then delete the scan.:lolflag:  This can be rectified by installing two packages, tesseract-ocr (probably the most accurate command-line OCR engine) and OCRFeeder, a GUI for command-line OCR engines.  To install these packages:

```
sudo apt-get install tesseract-ocr ocrfeeder
```

Then the OCR script can be modified to send the scanned file to OCRFeeder, at 200 dpi and in TIFF:

```
#! /bin/sh
set +o noclobber
#
#   $1 = scanner device
#   $2 = friendly name
#

#   
#       100,200,300,400,600
#
resolution=200
device=$1
mkdir -p ~/brscan
if [ "`which usleep`" != '' ];then
    usleep 10000
else
    sleep  0.01
fi
output_file=`mktemp ~/brscan/brscan.XXXXXX`
echo "scan from $2($device) to $output_file"
scanimage --device-name "$device" --format=tiff --resolution $resolution> $output_file
echo ocrfeeder --images $output_file \;rm -f $output_file | sh &
```

I may work on this one a little bit, the images you send to OCR need to meet certain requirements (1-bit black & white, etc), but this will only send colour scans to OCRFeeder even if you press the "Black" scan button - the program which detects the button press doesn't seem to differentiate between the two scan buttons.  It might be possible to format the image correctly using the options for "scanimage".

Hope this helps!

---

### Post by BozeWolf on 2012-05-29
One of the tasks I hate most is installing my Brother printer. So I decided to do some shell hacking to automate this task. Wanted to lean more about the "sed" command anyway. **Here's my little automated printer installation script.**

Please note: enter the model name of your printer in lowercase and remove the minus. Example: DCP7010 becomes dcp7010
Example 2: DCP-540CN becaomse dcp540cn.

[B]Save the code below as  "printer.sh"
[/B]roel@roel-desktop:/tmp$ **chmod +x printer.sh**  roel@roel-desktop:/tmp$[B] ./printer.sh
[/B]  
```

#!/bin/bash
echo "What is your printer model?"
echo "Find your printer model here..."
echo "http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html"
echo "Example: If your printer model is a DCP585-CW, enter dcp585cw here:"
read PRINTER_MODEL
PRINTER_URL="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html"
PRINTER_RGX='s/\(.*\)\('${PRINTER_MODEL}'\(lpr\|cupswrapper\)-.*deb\)\(.*\)/\2/p'
declare -a PRINTER_DEBS=(`wget -qO- ${PRINTER_URL} |sed -n -e $PRINTER_RGX`)
echo "creating /var/spool/lpd"
sudo mkdir /var/spool/lpd
echo "Downloading and Installing: " ${PRINTER_DEBS[@]}
for deb in "${PRINTER_DEBS[@]}"
do
        PRINTER_DL_URL="http://www.brother.com/pub/bsc/linux/dlf/dcp585cwlpr-1.1.2-2.i386.deb?"${deb}
        echo ${PRINTER_DL_URL}
        wget ${PRINTER_DL_URL} -O /tmp/${deb}
        sudo dpkg  -i --force-all /tmp/${deb}
done
echo "See if it's listed here..."
sudo dpkg  -l  |  grep  Brother

```**Enjoy! Let me know if it works or fails.**

---

### Post by kwanylongy on 2012-07-03
Thanks so much for creating this useful thread. 
The scanner instruction did not work for me and I wish to troubleshoot with this reply.
I am on Ubuntu 12.04, and I have a Brother 130C printer-scanner-in-one. 
I have previously managed to get the printer function to work. 

I have a problem following "step 6" of the scanner instruction. 
My computer does not have the file "/etc/udev/rules.d/45-libsane.rules" 
Rather, the directory contains 2 similarly named files, which are:
[INDENT]70-persistent-cd.rules     70-persistent-net.rules[/INDENT]

Since I could not have followed step 6 with the missing file, I tried to improvise this step by doing the following:

In the first attempt, I create the file "/etc/udev/rules.d/45-libsane.rules" with the following content
[INDENT]# Brother DCP-130C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01a8", MODE="664", GROUP="scanner"
LABEL="libsane_rules_end"[/INDENT]
where '04f9' and '01a8' are the 'VendorID' and 'ProductID' of my Brother130C

In the second attempt, I appended the above lines except the "LABEL=..." part to the file "/etc/udev/rules.d/70-persistent-cd.rules"

In both attempts, I re-booted my machine afterwards and opened xsane, but xsane reported the following error message:
[INDENT]Failed to open device 'brother2:bus1;dev1': Invalid argument. [/INDENT]


Any thoughts? Any help or comment will be much appreciated! :p

---

### Post by Fraoch on 2012-07-03
About a year ago I discovered that you don't need the file - just ignore that section, scanning is handled differently since at least Ubuntu 10.10.

See [http://ubuntuforums.org/showpost.php?p=10596645&postcount=366](http://ubuntuforums.org/showpost.php?p=10596645&postcount=366) and the few posts below it.

Undo what you did above and simply install the scanner driver off Brother's site.  Follow their instructions and it should work.

---

### Post by kwanylongy on 2012-07-03
I got it working eventually!
This is the [solution]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10").

Thank you Fraoch for your generous help!

---

### Post by slalala on 2012-07-09
Hello everybody!

I'm new to this forum but I'm using Ubuntu for quite some
time now. My parents own a brother all-in-one machine. It
took me quite some time to be able to print and scan with
it. But it works now.I don't know if this is the right
place to post my question. If it's not, please tell me
where to go. 

Whenever I print, the upper margin is smaller (and the
lower one bigger) than on my screen. Totally fed up
with it I've put my odt file on a usb stick, planning to
use my parents windows machine for printing. I realized
just on time that odt is useless that way so I turned
it into a pdf. It came out the printer the way I intended
it to be, but the text size was to big to my taste. So
I opened the odt that was still on the stick. Apparently
word is able to open odt files! I adjusted the size and
printed the file. Guess What? The margins where wrong.
Does this mean that nor Ubuntu nor the drivers are the
cause of this problem? By the way, printing in evince
gives the same result.

Thank you for your help!

---

### Post by kwanylongy on 2012-07-09
You have certainly come to the right place!

For solution, please see Kiwiexpat's solution in this thread: [http://ubuntuforums.org/showthread.php?t=1869282](http://ubuntuforums.org/showthread.php?t=1869282)

Come back to me if you run into trouble

---

### Post by slalala on 2012-07-10
Thank you for your response! I will try it and keep you posted.

---

### Post by mimo74 on 2012-07-18
I've had the same problem as mentioned here with my network printer. For some reason, I wasn't able to print! Until I tried this:
In the printer ipd I just wrote the printer IP address instead of the printer name and VOILA! working. You may try it.

And if somebody knows why it doesn't recognize the printer name (instead of IP) please post it.

Thanks.

---

### Post by celem on 2012-08-05
The brother installation instructions for the MFC-J430 failed when executed as written. The following worked for me:

From the printer, using the printer's control panel, setup the MFC-J430W to connect to your WiFi.


Verify that "lib32stdc++6" or "ia32-libs" are installed.

in the directory where you placed the downloaded files from Brother, **mfcj430wcupswrapper-3.0.0-1.i386.deb** and **mfcj430wlpr-3.0.0-1.i386.deb**, open a shell and execute:

sudo dpkg -i --force-architecture mfcj430wlpr-3.0.0-1.i386.deb 
*and*
sudo dpkg -i --force-architecture mfcj430wcupswrapper-3.0.0-1.i386.deb


Next, load the scanner driver 64-bit brscan4-0.4.1-1.amd64.deb from the Brother site at:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html")

sudo dpkg  -i  --force-all brscan4-0.4.1-1.amd64.deb

Observe the correct scanner name for your device:

brsaneconfig4 -q (You should see MFC-J430W in the list)

Next, identify your printer's reserved IP address and save it for the next command:

sudo brsaneconfig4 -a name=SCANNER model=MFC-J430W ip=192.168.1.202 (substitute your printer's IP address)

Verify correct installation:

brsaneconfig4 -q | grep SCANNER

You should see something similar to:
0 SCANNER "MFC-J430W" I:192.168.1.202

After this MFCJ430W will appear in your printer list, and your printer and scanner are good to go.

---

### Post by rareish on 2012-08-08
Hey just wanted to say that, the place you have to download the drivers has changed, [[SIZE=4]**here.**[/SIZE]]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html")[SIZE=4][SIZE=2]ohh and by the way loved the howto relly helped me.:D[/SIZE]
[/SIZE]

---

### Post by lookit on 2012-09-01
Not getting this to work. I'm running 32-bit 12.04  trying to get my HL-2130 to print, and it won't. Everything went as it should according to the tutorial, with the exception of the actual printing at the end :P

Any ideas? And oh, I'm very much a newbie with ubuntu, so plz bear with me!

---

### Post by pdc on 2012-09-03
> *Everything went as it should according to the tutorial*

which tutorial?

if you paste the link below

[http://localhost:631/printers/](http://localhost:631/printers/)

into a page on your browser: it opens CUPS: your printing admin

do you see your brother listed..if not, it is not installed..

.......if not installed, Brother make an INSTALLER.......

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

that folks report does all the work for you...

....if you think your HL-2130 is installed but not working you can delete it and try the installer

...if you subscribe to a thread, folks can respond more quickly

---

### Post by lookit on 2012-09-06
thanks for your reply!

> **pdc said:**
> which tutorial?


this one!   

> **pdc said:**
> 

....if you think your HL-2130 is installed but not working you can delete it and try the installer

tried, did everything over for the n-th time, failed. did it a n+1:th and it worked! :D the only thing I can think of that went wrong earlier is some error, which I must have missed.

> **pdc said:**
> 
...if you subscribe to a thread, folks can respond more quickly

how do I subscribe to threads? can't find it. 

again, thanks! :)

---

### Post by pdc on 2012-09-06
glad it is working;

to subscribe: go to thread tools: top rightish of screen;

click down to subscribe:

I often subscribe to notify by email and then one keeps in touch quickly

---

### Post by Fraoch on 2012-09-06
Incidentally I got an MFC-7460DN laser multifunction for office work, the print functions also work perfectly for Ubuntu 12.04.

The scanner isn't fully working.  Everything seems to go as normal, in fact scanning from the MFC to the Ubuntu machine is totally normal, but XSane-initiated scans are impossibly tiny ("0.03 cm X 0.03 cm") and can't be changed.

I'm thinking it's either an XSane problem or there's an error in the driver.

---

### Post by Fraoch on 2012-09-06
> **Fraoch said:**
> Incidentally I got an MFC-7460DN laser multifunction for office work, the print functions also work perfectly for Ubuntu 12.04.

The scanner isn't fully working.  Everything seems to go as normal, in fact scanning from the MFC to the Ubuntu machine is totally normal, but XSane-initiated scans are impossibly tiny ("0.03 cm X 0.03 cm") and can't be changed.

I'm thinking it's either an XSane problem or there's an error in the driver.

Strange, it was an XSane problem, I'm thinking caused by an error in the Brother driver which set the scanner size values in XSane.

Start Xsane, either on its own or through a program like GIMP.  In XSane's menu at the top of the screen, select "Window" - "Show advanced options".  This sets the scanner geometry and it's these values that were all screwed up, resulting in a tiny, tiny image size.  Comparing these wonky values to the known working ones from the MFC-J615W, the J615W's top-left x and top-left y corners were defined as 0, 0 and the bottom-right x and bottom-right y were defined as 21.57 and 29.97 cm respectively.  The 7460's top-left values were 14 some-odd...I can't remember what the bottom-right values were but the end result is that XSane thought the scanner was impossibly tiny.

I just copied the values from the J615W to the 7460 entries, assuming the scanners were the same size, and it now works perfectly.

Weird.

---

### Post by dcimadevilla on 2012-09-13
Thanks BoardDWorld!

Just a note: the step 10 for 64 bits users is not needed any longer since Ubuntu 12.04 as now the directory /usr/lib is shared for 32 and 64 libs: [http://unix.stackexchange.com/questions/43190/where-did-usr-lib64-go-and-what-is-usr-lib-x86-64-linux-gnu]("http://unix.stackexchange.com/questions/43190/where-did-usr-lib64-go-and-what-is-usr-lib-x86-64-linux-gnuhttp://")

---

### Post by flander3444 on 2012-10-24
just upgraded to 12.10 64b and my dcp115c stopped working, followed the instructions in the 1st post and it is working fine thanks to the op.

---

### Post by Fraoch on 2012-10-25
Dangit, upgraded to 12.10 64-bit and lost scanner functionality on BOTH an MFC-J615W and an MFC-7460DN.

Amazingly the 7460DN's scanner doesn't even work over USB.

:(

Both work fine for printing.

---

### Post by abrianb on 2012-10-25
During an upgrade you will be asked if you want to replace your customized cups file with a new version. Don't replace it or you will have to repeat part of the install procedure to get your brother gear to work.

---

### Post by Fraoch on 2012-10-25
Actually it wasn't an upgrade, I wiped the old install clean and installed new.

I can't help but think it's an obscure permissions issue, but it's odd that both printers work fine yet both scanners don't work, even over USB.

---

### Post by abrianb on 2012-10-25
have you tried running "sudo xsane" in terminal. If it works as root (sudo) then its a permissions problem. try this
 				 				**Re: HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies!** 			
 			 			 		   		 		 		I could not get the edit of **/lib/udev/rules.d/50-udev-default.rules   to work so I just opened a text editor and created a file   "51-udev-default.rules that said**...
device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"            Then   saved it. Then moved it to /lib/udev/rules.d
 Now my scanner works.

---

### Post by Fraoch on 2012-10-26
Yes, I've tried running xsane as root.  Same as before, xsane can't find any devices.

I've made the 45-udev-default.rules file as outlined on page 1 of this thread.  However I haven't seen anything about your 50/51 file which references USB buses so I'll give that a shot.

Thanks.

---

### Post by Hakunka-Matata on 2012-11-02
> **abrianb said:**
> have you tried running "sudo xsane" in terminal. If it works as root (sudo) then its a permissions problem. try this
 				 				**Re: HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies!** 			
 			 			 		   		 		 		I could not get the edit of **/lib/udev/rules.d/50-udev-default.rules   to work so I just opened a text editor and created a file   "51-udev-default.rules that said**...
device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"            Then   saved it. Then moved it to /lib/udev/rules.d
 Now my scanner works.

The first line in /lib/udev/rules.d/50-udev-default.rules is:
**# do not edit this file, it will be overwritten on update**
After much searching through Brother Solutions Website I've found this nugget.  This solution still violates the "do not edit" warning.............  what's a body to do??????
**SCANNER SETTING FOR NORMAL USER (i.e. NOT superuser)**
[http://welcome.solutions.brother.com/bsc/Public_s/id/linux/en/instruction_scn1c.html]("http://welcome.solutions.brother.com/bsc/Public_s/id/linux/en/instruction_scn1c.html")

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"". 

The lines to be added---------------------------

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
 
3. Restart the OS.


**MORE Excellent INFORMATION FROM BROTHER Solutions Website**
[(http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)"][http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)]("[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
The above link has excellent instructions on installing my scanner - a DCP-9040CN on a 12.04-64 system, change the device if you're looking for information on a different model.

---

### Post by michalt on 2012-11-24
After upgrade from 12.04 to 12.10 the Brother scanner (DCP-7060D) stopped working. The printer is working fine, lsusb identifies scanner, though the xsane will fail to scan with "Scanner startup failed, Invalid argument" window. Regardless the xsane is started as root or normal user.

Anyone know what to do? I suspect it's buggy driver.

---

### Post by Fraoch on 2012-11-24
> **michalt said:**
> I suspect it's buggy driver.

I'm having a similar problem (xsane can't find any devices) and I suspect 12.10 introduced some incompatibility with the Brother scanner driver.

I have two Brother scanners - both were working perfectly before the upgrade, now both aren't found.  I tried both network scanning and directly connected by USB.  Yet the printer functions work fine.

I'd like to bring this up with Brother but there doesn't appear to be a way to submit bug reports to them.

---

### Post by pdc on 2012-11-24
out of interest, did you both have to do what Brother recommends, to have a working scanner in 12.04

> 
Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".

    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

If you have a read through this page

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

it describes what to me are the individual querks of a zillion distros ..one uses the word linux as though it were a unitary force..it could instead be compared to a tower of babel.......with manufacturers continually chasing a moving target of changes by the distro releases..

....... you can find similarly patient distro advices sheets by Canon talking of the individual fixes to suit the temperaments of a multitude of different distros............ maybe that is where the problem lies !!

---

### Post by Fraoch on 2012-11-24
> **pdc said:**
> out of interest, did you both have to do what Brother recommends, to have a working scanner in 12.04

Yes, I tried that.  No effect.:(

---

### Post by michalt on 2012-11-25
> **Fraoch said:**
> I'm having a similar problem (xsane can't find any devices) and I suspect 12.10 introduced some incompatibility with the Brother scanner driver.

Seems not quite same error - In my case xsane sees the scanner and attempts to scan, but nothing is happening.

@pdc - I had working scanner with 12.04 and yes, I did edit the UDEV rules. Anyway even without editing UDEV rules, the scanner should be working for root, which is not the case now.

---

### Post by michalt on 2012-11-29
I wrote to Brother support and got message that the new driver is in the pipe and should address the issue with 12.10...

---

### Post by michalt on 2012-12-04
> **michalt said:**
> I wrote to Brother support and got message that the new driver is in the pipe and should address the issue with 12.10...

New driver is out there ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)), though doesn't seem to address my issue...

$scanimage -L identifies my scanner:

```
device `brother4:bus2;dev1' is a Brother DCP-7060D USB scanner
```

though $scanimage -T results in :

```

scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567
scanimage: sane_start: Invalid argument

```

Any suggestions?

---

### Post by Fraoch on 2012-12-04
> **michalt said:**
> New driver is out there ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html))

OMG it works!! :D

My MFC-7460DN is now working both over the network and over USB (in fact, xsane lets me choose between the two).  Still no sign of the MFC-J615W (looks like they need to update brscan3 in the same way), but some progress at least.

Unfortunately in regards to your issue michalt I had a suspicion it was improper scan dimensions in a configuration file for your scanner, but I found that through xsane, not sane.  It should have worked through the command line...

---

### Post by michalt on 2012-12-05
> **Fraoch said:**
> 
Unfortunately in regards to your issue michalt I had a suspicion it was improper scan dimensions in a configuration file for your scanner, but I found that through xsane, not sane.  It should have worked through the command line...

I think it can be some problem with USB usb, maybe even the issue is not caused by the brother drivers. Because sane-find-scanner won't find the scanner, but scanimage -L and and lsusb does.

This is the outup of dmesg:

```

Dec  4 21:21:14 Gurkha kernel: [  686.619600] usb 3-3: usbfs: interface 0 claimed by usblp while 'scanimage' sets config #1
Dec  4 21:21:14 Gurkha kernel: [  686.619627] usb 3-3: usbfs: process 7449 (scanimage) did not claim interface 1 before use
Dec  4 21:21:15 Gurkha kernel: [  687.674368] usb 3-3: usbfs: interface 0 claimed by usblp while 'scanimage' sets config #1
Dec  4 21:21:15 Gurkha kernel: [  687.674398] usb 3-3: usbfs: process 7449 (scanimage) did not claim interface 1 before use

```

Does it ring the bell to anyone?

---

### Post by Fraoch on 2012-12-05
> **michalt said:**
> I think it can be some problem with USB usb, maybe even the issue is not caused by the brother drivers. Because sane-find-scanner won't find the scanner, but scanimage -L and and lsusb does.

This is the outup of dmesg:

```

Dec  4 21:21:14 Gurkha kernel: [  686.619600] usb 3-3: usbfs: interface 0 claimed by usblp while 'scanimage' sets config #1
Dec  4 21:21:14 Gurkha kernel: [  686.619627] usb 3-3: usbfs: process 7449 (scanimage) did not claim interface 1 before use
Dec  4 21:21:15 Gurkha kernel: [  687.674368] usb 3-3: usbfs: interface 0 claimed by usblp while 'scanimage' sets config #1
Dec  4 21:21:15 Gurkha kernel: [  687.674398] usb 3-3: usbfs: process 7449 (scanimage) did not claim interface 1 before use

```

Does it ring the bell to anyone?

Hmm, do you have a custom kernel?

Entering "interface 0 claimed by usblp" into Google shows some hints.  This one may help:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545288](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545288)

---

### Post by michalt on 2012-12-06
> **Fraoch said:**
> Hmm, do you have a custom kernel?

Nope. Also blacklisting usblp module doesn't seem to bring any change.

---

### Post by Caldo1 on 2012-12-28
> **Bushcraft Bill said:**
> Well its back to square one with my brother MFC-5440CN printer I had no problems with 10.04 and the tutorial for getting it to work but now 11.04 I did it all over again but no luck this time guess enough has changed were it is now broken unless someone comes up with a new fix....
May just be time/excuse for me to get one of them new wireless printer/fax/scanners

Resolved this problem rather quickly with the following:
1.) go to web site:
[http://pkgs.org/ubuntu-12.10/ubuntu-multiverse-amd64/brother-lpr-drivers-extra_1.2.0-2-0ubuntu5_amd64.deb.html](http://pkgs.org/ubuntu-12.10/ubuntu-multiverse-amd64/brother-lpr-drivers-extra_1.2.0-2-0ubuntu5_amd64.deb.html)
2.) connect printer first to ethernet cable
3.) run the following commands
 
[LIST=1]
[*]Update the package index: # sudo apt-get update
[*]Install brother-lpr-drivers-extra deb package: # sudo apt-get install brother-lpr-drivers-extra
[/LIST]
  
4.) go to system settings / printers
 hopefully a printer MFC-5440CN appears
5.) print test page
6.) right mouse click on printer icon in system settings page and duplicate
7.) rename duplicated printer as MFC-544CN-USB
8.) select properties
9.) disconnect ethernet cable, connect USB cable
10.) in properties field, change Device URL: usb://Brother/MFC-5440CN?serial=BROE6F992284
11.) print test page using USB printer
12.) make USB printer system wide default

---

### Post by apos on 2013-01-05
Hi there.

I almost successfully got my Brother DCP-8065DN scanner/printer working under Ubuntu 12.04. I followed all recommendations on the brother page and this thread. I also have another Brother brscan4 model here, which is working without any clue.

The printer has USB and a network card. But there are two problems remaining when using it as **scanner**:


[1] **brscan2** (2! - which is the intended version for this device) is not working.
The scanner can be configured via **brsaneconfig2**, but will not work scanning with Xsane or equal programs.

[2] If I install **brscan4** (yes 4!), the scanner works flawlessly when scanning black and white or greyscale. Color scans result in very bad experience.

**_Output:_**

brsaneconfig2 gives nothing (and again: this should work with this scanner)

brsaneconfig4 gives me:
```

brsaneconfig4 -q

Devices on network
  0 SCANNER_HOME        "DCP-8065DN"        I:192.168.178.43

scanimage -L
device `brother4:net1;dev0' is a Brother *SCANNER_HOME DCP-8065DN

```

_**Simplescan:**_

[LIST]
[*]Greyscale- and textscan works.
[*]colorscan delivers wrong color (everything is pink)
[/LIST]

_**Gscan2pdf:**_

[LIST]
[*]greyscale- and textscan works.
[*]colorscan works with 150dpi and Color 24bit [FAST]
[/LIST]

Greetings
Axel

---

### Post by jimbean on 2013-01-11
Im running 12.10 ubuntu, every time i install the drivers for my mfc5840cn they install and work fine 
but
the package manager wants to fix broken broken packages and remove the drivers?
i havent read the entire post but am fixing to do so now
but if i cant find info 
im posting now to speed up process
any help? thanks in advanced
this is what it says
{Sorry, Ubuntu 12.10 has experienced an internal error
if you notice further problems try restarting the computer}
Allready done that ,restarted pc
nevermind, i installed the drivers from synaptic and they were conflicting with the drivers from brother

---

### Post by organmorgan on 2013-02-09
I'm very new to this, although I've used Ubuntu now since 8.04.  What a useful thread!

I have an MFC-465CN printer/scanner, connected via USB which eventually worked perfectly when I updated to Ubuntu 10.04 on my desk-based  computer.

I now have an Acer Aspire 5560 laptop on which I loaded Ubuntu 12.04 (32bit).  After a number of tries, using information in this thread and the Brother website I eventually got the machine to work from the laptop but only as a network printer.  It still works from the Ubuntu 10.04 system as both network and USB printer.

With or without the network cable attached, if I then connect the MFC-465 via the USB port the laptop computer recognizes it as a MFC465 printer, insists on connecting it a a generic text printer, which is absolutely useless as others in this thread have found! 

Can anyone offer a solution, please?  (expressed in very simple terms please!) 

Much to my surprise and delight, somehow or other I have connected it as a  network scanner with no problems at all from both machines!:D

---

### Post by pdc on 2013-02-09
hi morgan;

I wondered if you were familiar with the CUPS interface using your browser

if you paste

[http://localhost:631/printers/](http://localhost:631/printers/)

into a spare window on your browser, this should allow you to manage things..does it allow you to specify different things?

.......also from MENU: Administration: Printing ..can you open the printing interface and right-clicking on the icons select properties for each printer?

---

### Post by organmorgan on 2013-02-11
> **pdc said:**
> hi morgan;

I wondered if you were familiar with the CUPS interface using your browser

if you paste

[http://localhost:631/printers/](http://localhost:631/printers/)

into a spare window on your browser, this should allow you to manage things..does it allow you to specify different things?

.......also from MENU: Administration: Printing ..can you open the printing interface and right-clicking on the icons select properties for each printer?
Many thanks.
I have used the CUPS interface, but that does not seem to allow me to change things.  Nor does Applications/System Tools/ System Settings/Printers.
However if I select Printers from the menu (as for shutting down etc) then I could change it to use the Brother Driver for the USB connection.
Having printed the test page from that window, though, I have to give it the three fingered salute to get out of the Printer Settings page!   But it works on both USB and network connections!  Many thanks, again, pdc.

---

### Post by Jackalyn on 2013-02-11
I think this might be helpful if I was actually sure that the printer I am trying to use at work is compatible with linux! Brother MFCJ5910

I did find and download drivers but still seem to be getting it wrong. 

Just to make life really hard there is no instruction for actually printing a document as opposed to a photo from a flash drive - which of course, would save a lot of bother. 

Wondering if anyone can help me out on either - thanks.

---

### Post by Fraoch on 2013-02-11
> **organmorgan said:**
> Many thanks.
I have used the CUPS interface, but that does not seem to allow me to change things.

This could be the source of your trouble - note the Brother instructions state that some modification work must be done in the CUPS web interface:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

[quote=Brother website]
Step 5a. (for USB Connection) Check your printer on the cups web interface
    5a-1. Open a web browser and go to "http://localhost:631/printers".

        Check if the Device URI of your printer is "usb://Brother/(your printer's model name)" 

        If the device URI is different from the example above, please go to "Modify Printer" of your printer to select proper device and driver.

        If your printer is not listed on "http://localhost:631/printers", please go to "http://localhost:631/admin" and click "Add printer" and select proper device and driver.

Step 5b. (for Network Connection) Configure your printer on the cups web interface
    5b-1. Open a web browser and go to "http://localhost:631/printers". 
    5b-2. Click "Modify Printer" and set following parameters.

    - "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect" 	     	for Device
    - lpd://(Your printer's IP address)/binary_p1 	     	for Device URI
    - Brother 	     	for Make/Manufacturer Selection
    - Your printer's name 	     	for Model/Driver Selection[/quote]

You indicate you can't modify things on the CUPS web interface.  How so, does it just do nothing when you select certain things?

The CUPS web interface is a little hard to understand at first.  To get to the point where you can actually carry out the Brother instructions, click the "Administration" tab at the top of the page.  Then press the "Manage Printers" button.  Click on the printer, then in the second roll-down list pick "Modify Printer".  It'll ask for a user name and password, your user name with your root password should work.  Then you can actually carry out the above instructions.

---

### Post by organmorgan on 2013-02-11
> **Fraoch said:**
> This could be the source of your trouble - note the Brother instructions state that some modification work must be done in the CUPS web interface:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)



You indicate you can't modify things on the CUPS web interface.  How so, does it just do nothing when you select certain things?

The CUPS web interface is a little hard to understand at first.  To get to the point where you can actually carry out the Brother instructions, click the "Administration" tab at the top of the page.  Then press the "Manage Printers" button.  Click on the printer, then in the second roll-down list pick "Modify Printer".  It'll ask for a user name and password, your user name with your root password should work.  Then you can actually carry out the above instructions.
Many thanks for your trouble - it is clear that having successfully installing it as network printer I never thought of re-reading the Brother instructions. (idiot!) 
As regards the CUPS web interface, I could not see how to modify the settings: right clicking on the manage printers showed open link etc - no properties option.  (ldiot-squared - you didn't put right click, so why did I?)
Luckily my setting it via the printers properties achieved enough to overcome my ignorance. There is so much to learn and so much forgotten!

---

### Post by Fraoch on 2013-02-11
> **organmorgan said:**
> Many thanks for your trouble - it is clear that having successfully installing it as network printer I never thought of re-reading the Brother instructions. (idiot!)
As regards the CUPS web interface, I could not see how to modify the settings: right clicking on the manage printers showed open link etc - no properties option.  (ldiot-squared - you didn't put right click, so why did I?)
Luckily my setting it via the printers properties achieved enough to overcome my ignorance. There is so much to learn and so much forgotten!

Oh I also didn't read properly then, you now indicate it's working - sorry!

Anyway, yeah, to get to printer properties in CUPS, just click the link, don't right-click.

The CUPS web interface is pretty powerful once you wrap your head around it.  You can print test pages, add/modify/delete printers, set a default printer, etc.  There's little need for the Windows-like Printers box and it has less control.

---

### Post by Fraoch on 2013-02-11
> **Jackalyn said:**
> I think this might be helpful if I was actually sure that the printer I am trying to use at work is compatible with linux! Brother MFCJ5910

I did find and download drivers but still seem to be getting it wrong.

If there's a driver on the Brother website for it then it's compatible and should work.  And yes, yours is listed:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J5910DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J5910DW)

Then follow the instructions, it's not too hard but it's more than just installing the .deb:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

> Just to make life really hard there is no instruction for actually printing a document as opposed to a photo from a flash drive - which of course, would save a lot of bother.

It works just like a printer in Windows or Mac - you must have something to print open in an editing program, then select "File - Print" from the menu.

---

### Post by mining3 on 2013-02-12
Your set 4 HERE link does not work.  I think I downloaded printer CUPs from Brother. I was prompted by soft centre this did not meet some criteria I a went ahead .....hope it does not bung things up. I absolutely hate the layout for Ubuntu 12.04 could not find anything. So I now us Mate desktop to replace with the familiar three Applications Places  Systems drop down menus. 

Under control centre why no have the selection for scanner just like printer if it is different?

scanner still not working

---

### Post by pdc on 2013-02-12
mining3:

please start a new thread if you would like some help;

it really gets impossible when you have 4-5 people jumping up and down in a thread ..........

.......help us to help you .........

..........please start a new thread and tell us about your system a

---

### Post by Jackalyn on 2013-02-12
> **Fraoch said:**
> If there's a driver on the Brother website for it then it's compatible and should work.  And yes, yours is listed:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J5910DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J5910DW)

Then follow the instructions, it's not too hard but it's more than just installing the .deb:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)



It works just like a printer in Windows or Mac - you must have something to print open in an editing program, then select "File - Print" from the menu.

I just have no idea what bit of the instructions to follow and yet again why is the terminal convinced I am not a super user? How do I tell it I am?

I just do not understand what I do to get the drivers opened. I assume I do all the Ubuntu things listed but am still not sure this is going to work.

Maybe my  brain is fried because I opened up the laptop to find the laptop had 'lost' the OS! I got it back by putting in a Ubuntu server disk (which did not do anything but seemed to jump start things!) Got no hot water either lol so maybe it is one of them days.

DUH.......SUDO!!!!!!!!!!!!!! I forgot to put that in.

---

### Post by Fraoch on 2013-02-12
> **Jackalyn said:**
> I just do not understand what I do to get the drivers opened. I assume I do all the Ubuntu things listed but am still not sure this is going to work.

There's really only one critical step:

```

dpkg  -i  --force-all  (cupswrapper-drivername)
```

That's it.  It says to open and install (dpkg - "depackage") the driver.

You have to navigate to the directory where the .deb sits first.  By default, that's /home/[your user name]/Downloads unless you changed the download directory in Firefox.  Note this is case-sensitive.

When you start the terminal you will be in /home/[your user name] and the prompt will tell you what user name you are.  Mine says:

```
mark@Sauron:~$
```

My user name is mark and my machine name is Sauron.

Navigate to the Downloads directory using the "cd" (change directory) command:

```
cd /home/[your user name]/Downloads
```

So for example I use:

```
cd /home/mark/Downloads
```

In the interest of completeness, you can use a shortcut for /home/[your user name], the "tilde", "~".  So:

```
cd ~/Downloads
```

is equivalent.

The prompt will now tell you where you are.  For example:

```
mark@Sauron:~/Downloads$
```

You then follow the Brother instructions using superuser privileges.  There are two ways to do this - "sudo" before a command carries out the command with superuser privileges once.  You have to type "sudo" every time.  "sudo su" changes you to a superuser for the duration of the terminal session.  You only have to enter it once and all commands are carried out with superuser privileges.

After the first "sudo" the system will ask for your password - this is the one you set when you installed Ubuntu.  For convenience it only does this once, then it won't ask you again for a period of time (10 minutes?)

So you type either:

```
sudo dpkg  -i  --force-all  (cupswrapper-drivername)
```

or:

```
sudo su
root@Sauron:/home/mark/Downloads# dpkg  -i  --force-all  (cupswrapper-drivername)
```

Note the prompt changed after "sudo su" and shows me logged in as "root" (i.e. the superuser). To find the exact driver name, list the directory contents with "ls".  You need to get the driver name exact and the Brother drivers are long with many version numbers.  The terminal will tell you if you get it wrong.

The other Brother commands just check to see that the driver installed correctly and go through some modifications in CUPS.

Oh, another shortcut - press the up and down arrows to cycle through the commands you previously entered.  This is helpful when you get the exact driver name wrong and you get an error, just type "ls" to show the directory contents and get the driver name, then press the up arrow twice to cycle to the command where you used the driver name.  Correct the driver name and press Enter.

---

### Post by PhilAlban on 2013-03-04
Dredging this up from the long-past! Working through step 9 for just the printer fixed my issues (I do not need the brother scanner installed). I have the Brother MFC-J825DW. Thanks for posting this. Attempting to install the drivers (debian) using the Brother website instructions was completely unhelpful.

---

### Post by larytet on 2013-05-15
My /etc/udev/rules.d/70-persistent-printer.rules file

```
SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01a8", MODE="0666" 

```

---

### Post by abrianb on 2013-05-15
This [http://askubuntu.com/questions/145680/getting-my-brother-mfc-j825dw-working-as-a-network-scanner](http://askubuntu.com/questions/145680/getting-my-brother-mfc-j825dw-working-as-a-network-scanner)link helped me set up my Mfc J825dw

---

### Post by roygbiv808 on 2013-05-21
Thank you for solving my problem. I have 13.04 and after downloading from the brother website, I didn't have a single problem. I spent forever trying to find instructions. Thanks again.

---

### Post by spicy50210 on 2013-06-12
hi i have a lenov y730 and a samsung nb28 plus with a brother mfc465cn and i am at the step to check the scanner by xsane and it seems that it doesn't see it.  And the file gedit /etc/udev/rules.d/45-libsane.rules is **EMPTY !! **:shock: 

PLEASE  help !!!!

---

### Post by gperrot on 2013-07-01
Hello,

I am using Ubuntu 13.04 on 64bits PC portable. Do you know if I can easily use DCP-7055 printer and scanner on Ubuntu 13.04 ?

Thanks in advance for your help.

Gigi

---

### Post by krisbee2000 on 2013-08-26
Just wanted to note here, I finally got my MFC210C scanner to work in 12.04 64bit - the package from Brother works, however, it installs some symlinks in (at work, but I believe /usr/lib/sane) that when I ran xsane in a debug mode complained about too many links (links of links of links)... so I copied the files to that location and it then worked (along with modifying the 40-libsane-rules file and dll.conf as is scattered throughout the forums/threads/websites)...

---

### Post by wewa2 on 2013-09-12
Hello,

could anyone help me with getting the Brother DCP-J140W printer running on my raspberry?
Or has anyone experiences with brother printer drivers and armhf architectures?

Best regards

wewa

EDIT: [COLOR=#333333][FONT=Helvetica Neue] I tried to install the driver on my own. I installed both i386 drivers (lpr and cupswrapper) with the force option. Then I compiled the cupswrapper source and replaced the old binary from the *.deb package with the new binary. Than I added the printer via CUPS webinterface. And tried to print a testpage. But still without success. To get some additional information I set the cups logger to "debug". Here [/FONT][/COLOR][http://codeviewer.org/view/code:3662](http://codeviewer.org/view/code:3662)[COLOR=#333333][FONT=Helvetica Neue] you can see the debug log.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Can you find any errors?[/FONT][/COLOR]

---

### Post by dave.leland on 2013-09-14
Brother MFC-J6710DW Now Prints (Ubuntu 13.04 x64) -Thank You! :popcorn:

Here are a few notes for those who are Newer Noobs like myself. Step 10 gave me a bit of trouble due to my own lack of knowledge. First I used Midnight Commander to find the LPD Wrapper and get the correct filename to copy.  Next, I had to cd to /usr/lib64 and use mkdir to create the folder "cups", cd to cups and create the folder "filter". After that, I was able to copy the LPD Wrapper into the new /usr/lib64/cups/filter folder.

Thanks Again,
Dave Leland

---

### Post by rickrodriguez1971 on 2014-01-28
I know this is an old thread, but for those who are still having problems...


I have the Brother MFC-J615w (Wireless thus the W...lol)
I tried all the above and nothing worked, they may have contributed to what now works, but this is what finally made it all come together, so I say try this and if this isn't the solution do all the other stuff too
the directions never mention super user, but I found it helpful to use it

[SIZE=3][B]remember "sudo nautilus" in a terminal... then proceed
Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10 or farther (in my case, 13.10 32 bit)
[/B][/SIZE][B]
1.[/B] Open "/lib/udev/rules.d/40-libsane.rules" file.**2. **Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"". 

The lines to be added---------------------------
[B]
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

 [/B]**3.** Restart the OS.

**4. *scan away...***

---

### Post by gary21 on 2014-03-06
I am a complete newbie to Ubuntu.  Although I have tried to use it several times.   When I first loaded Ubuntu everything went well.  Printer and all hardware installed in a breeze.  But as last time after several days,  the printer won't work again,  I can't set a home page,  there are no help pages from the help in the task bar.  I know nothing about "code",  and what should be a simple fix turns to a major project.  That is why I have never kept linux very long because it can be so flustrating.  So as much as I hate Microsoft Windows,  Linux makes everything so damn complicated.  I have tried to find out why my printer doesn't work most of the day yesterday to no avail.  No one seems interested in helping, and when they do,  they start talking over my head about things of which I know nothing.  Nothing is ever simple.  Even your help pages seem to think everone is a computer whiz, which I wish I was.   I am very flustrated.
Gary

---

### Post by larytet-48904418 on 2014-03-22
> **larytet said:**
> My /etc/udev/rules.d/70-persistent-printer.rules file

```
SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01a8", MODE="0666" 

```

To make scanner to work without sudo for all users I did following 
1.  Edit file (create if it does not exist) ```
sudo nano /etc/udev/rules.d/40-libsane.rules
```
2. Add line ```
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes", MODE="0666"
```

---

### Post by paul_h on 2014-03-23
Here it is, 2014, and this 2007 tutorial still is the best help I have come across on installing Brother printers.
Easy to follow and it works!
Thanks BoardDWorld.

---

### Post by _sluimers_ on 2014-05-23
```
~$ scanimage -T
scanimage: rounded value of br-x from 297 to 296.973
scanimage: rounded value of br-y from 420 to 419.962
scanimage: scanning image of size 2304x3306 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 6912 bytes...	FAIL Error: Out of memory
```

I'm stuck!! :frown:
Can someone please get me out of this horror error?

---

### Post by shai3 on 2014-08-14
Yet another thanks to a great tutorial that got my Brother printer working from my Ubuntu box on a networked Brother printer. So easy, but only because of this tutorial!

---

