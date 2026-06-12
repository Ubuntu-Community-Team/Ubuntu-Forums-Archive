---
title: "driver for OKI B4100 printer"
date: 2006-09-12
forum: Tutorials
---

### Post by Easterly Wind on 2006-09-12
Hi,

For all those owners of OKI B4100 printers and other lower models in B series, I composed a ppd file and attach it to this post.

I checked it works with Dapper and Breezy, might work with other distributions, doesn't work on FC5 (don't know why).

Basically, it's a heavily modified ppd for hp laserjet 6, and uses hpijs driver.

With the attached ppd you can use all OKI options, and you can set paper type, weight, 2 toner saver modes, tray/manual feed, etc.

With this ppd OKI prints at 600dpi. You can tell your printer to use 1200dpi too but hpijs doesn't support resolutions over 600dpi.

DON'T FORGET to switch off duplex printing in printer properties, otherwise each page you print will be followed by a blank one.

For those completely new to Ubuntu <like me :D >, download the attachment and double-click on it, then extract the .ppd file to a convenient location. Then go to System->Administration->Printing, Double-click on 'Add new printer', then follow instructions, when asked for printer model, click on 'install driver' and open your ppd file, then follow instructions again.

---

### Post by Donnw on 2007-01-13
Hi 

Thanks for the driver.  I am very new to Linux and i am still trying to set up my computer to use it.  I installed the driver as you described but when I go to print a document from openoffice the light on the printer flashes as though everything is Ok but it fails to continue printing.  Have I forgoten to do something? The printer is connected by the parallel port not USB

Thanks

---

### Post by mintar on 2007-03-12
Thank you a million times! This is the third time in the last 5 years that I try migrating to linux, and I think this time I'll make it. What I love about ubuntu is that there are people like you that make my life so much easier and less frustrating.

Driver works like a charm. :)

Cheers,
Martin

---

### Post by ScoobyP1 on 2007-04-24
Many thanks from me, too. Driver works perfectly under Ubuntu 7.04

---

### Post by jano32 on 2007-05-14
works great under debian (etch), thx   :popcorn:

---

### Post by smajeon on 2007-07-10
Wow, thanks so much. This was THE ONE THING that I'd been pulling my hair out about.

---

### Post by mikca on 2007-07-23
thank a lot! it works in Fedora 7

Miky

---

### Post by Dripbagulhos on 2007-11-12
> **Easterly Wind said:**
> Hi,

For all those owners of OKI B4100 printers and other lower models in B series, I composed a ppd file and attach it to this post.

I checked it works with Dapper and Breezy, might work with other distributions, doesn't work on FC5 (don't know why).

Basically, it's a heavily modified ppd for hp laserjet 6, and uses hpijs driver.

With the attached ppd you can use all OKI options, and you can set paper type, weight, 2 toner saver modes, tray/manual feed, etc.

With this ppd OKI prints at 600dpi. You can tell your printer to use 1200dpi too but hpijs doesn't support resolutions over 600dpi.

DON'T FORGET to switch off duplex printing in printer properties, otherwise each page you print will be followed by a blank one.

For those completely new to Ubuntu <like me :D >, download the attachment and double-click on it, then extract the .ppd file to a convenient location. Then go to System->Administration->Printing, Double-click on 'Add new printer', then follow instructions, when asked for printer model, click on 'install driver' and open your ppd file, then follow instructions again.

Thank you very much for the post. The driver works perfectly, except by two little issues:

1) I have a blank page at the end of every job with I can not prevent  of being released, 

2) Although I think this is an issue between the cups on my local machine and the router in wich the printer is installed (a Siemens SE551 router): there is a delay of 1 to 3 minutes between every page.

Have anyone experienced some situations like this?

Thanks!

---

### Post by Dripbagulhos on 2007-11-20
> **Dripbagulhos said:**
> Thank you very much for the post. The driver works perfectly, except by two little issues:

1) I have a blank page at the end of every job with I can not prevent  of being released, 

2) Although I think this is an issue between the cups on my local machine and the router in wich the printer is installed (a Siemens SE551 router): there is a delay of 1 to 3 minutes between every page.

Have anyone experienced some situations like this?

Thanks!

Let me add some pieces of information:

If I boot Windows on the same machine, I can print 50 pages in 10 minutes (3 times faster), with little better quality and no blank page at the end of the job. I guess the problem is not a problem but two problems:
[LIST=1]
[*]CUPs
[*]Driver
[/LIST]

Cups had bad performance with all printers I tested. With any inkjet pluged durectely on my micro, it has worse quality and is 3 times slower than windows

The driver must be the responsible to send 1 blank page at the end of every job, since I didn't get this issue with any other printer

---

### Post by seenxu on 2008-04-07
how to disable the duplex printing in property.
i had checked the .ppd file, it says that *DefaultDuplex: None

don't know why and how to avoid the printer always to print out a blank paper

---

### Post by aigelonic on 2008-04-27
Thanks!
It worked great with my new Oki B2200 printer. :)
If just everything was as easy to get working as this :P


Cheers!

---

### Post by cscsc on 2008-05-05
Thanks for the ppd file, I can now print to our oki b4300 printer.  No problems yet!  Also, your instructions were very helpful, since this is our first time with linux.  :)

---

### Post by vroy on 2008-05-09
I downloaded the ppd file. But, I can't find the model B6300 in it. Ane help?

---

### Post by exwindowsuser on 2008-05-11
Thank you very much :)
It worked just fine for me =D>
On Ubuntu 8.04 install under Windows :mad:

---

### Post by likerice on 2008-05-25
for anyone who stumbles upon this page using Hardy 8.04:

i was able to install my Oki B4100 (attached via USB) without additional drivers.

in Firefox, i navigated to [http://localhost:631](http://localhost:631), clicked on "Administration" -> "Find New Printers" and was given 2 choices: 

OKI DATA CORP B4100, and

OKI_DATA_CORP_B4100_USB_1.

i chose the second option, clicked-through the default options, and VOILA!

my flawlessly functional Oki B4100 settings now read as follows:

```
Description: OKI DATA CORP B4100
Location: Local Printer
Printer Driver: Okidata Okipage 6e - CUPS+Gutenprint v5.0.2
Printer State: stopped, accepting jobs, published.
Device URI: usb://OKI%20DATA%20CORP/B4100 
```

it's worth noting that i was *unable* to install this printer via System -> Administration -> Printing, for whatever reason (most likely, my n00b incompetence).

---

### Post by Heliooos on 2008-07-14
Thanks much. Works nice under PCLinuxOS 2007 :-)

---

### Post by skili2008 on 2008-08-18
** Thanx mate... It worked for me.. **

:guitar:

---

### Post by edilsonka on 2008-10-26
Hey Easterly Wind, thanks for the driver - works great!!!!

---

### Post by pjtb on 2008-11-02
Thank You for this driver - Have this working on Acer One Linpus Lite fantastic.

---

### Post by FloSch369 on 2008-12-01
As none of the methods mentioned worked for me I just want to leave another note on this topic for those still seeking.

I always had the problem that the printer simply cut off a little on the top - no matter where the text really starts (doesn't necessarily need to be at the very top of the page).

Only thing that worked for me so far: adding the OKI B4100 with the ppd for HP Laserjet 1100.

Greatings

---

### Post by denhussam on 2008-12-14
Thanks for help, it works great with Oki B2200 printer =D>

---

### Post by Chocolates on 2008-12-31
Hi

I had a problem finding a driver for my Oki C5510 MFP and found to get the Oki C5510 MFP to work on Ubuntu you need to select the Oki C5500 driver from the Oki database within Ubuntu print driver database.

Other drivers that worked in Black and White BUT not color were C5500 and C3530.

Chocies!!:)

---

### Post by lakeoftea on 2009-01-30
yes works brilliantly on ubuntu 8.10 on b2200 cheers and thx so much

---

### Post by zegh on 2009-02-06
Thank you for the driver. 

I followed the instructions [here]("http://www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/") to get to a printer in xp, but never got to make it function well. Now with this driver I can finally print directly from Ubuntu!

---

### Post by PepeWasquez on 2009-04-27
gracias, funciona perfectamente con ubuntu 9.0 y una impresora oki b2200  conectada a una maquina con windows xp,  a traves de la red local
:popcorn:

---

### Post by brantonc on 2009-05-25
Works on opensuse 11.1 as well. Thank-you for your hard work on this printer.

---

### Post by nextwave on 2009-06-13
Works great for my B2200! Works on Mandriva 2008.0, 2008.1, 2009.0, and 2009.1.
funny that openprinting.org sees the printer as a paper wieght. Oh well, can't always gettem' all :)
Thanks for your hard work!

---

### Post by pigpen23 on 2009-08-06
works perfect for my b2200 on 9.04

---

### Post by kuzrics on 2009-08-25
> **Easterly Wind said:**
> Hi,

For all those owners of OKI B4100 printers and other lower models in B series, I composed a ppd file and attach it to this post.

I checked it works with Dapper and Breezy, might work with other distributions, doesn't work on FC5 (don't know why).

Basically, it's a heavily modified ppd for hp laserjet 6, and uses hpijs driver.

With the attached ppd you can use all OKI options, and you can set paper type, weight, 2 toner saver modes, tray/manual feed, etc.

With this ppd OKI prints at 600dpi. You can tell your printer to use 1200dpi too but hpijs doesn't support resolutions over 600dpi.

DON'T FORGET to switch off duplex printing in printer properties, otherwise each page you print will be followed by a blank one.

For those completely new to Ubuntu <like me :D >, download the attachment and double-click on it, then extract the .ppd file to a convenient location. Then go to System->Administration->Printing, Double-click on 'Add new printer', then follow instructions, when asked for printer model, click on 'install driver' and open your ppd file, then follow instructions again.

I should be a type of graphical status monitor oki b4100 printer thanks

---

### Post by The KB Stockpiler on 2009-09-18
> **Easterly Wind said:**
> Hi,

For all those owners of OKI B4100 printers and other lower models in B series, I composed a ppd file and attach it to this post.

I checked it works with Dapper and Breezy, might work with other distributions, doesn't work on FC5 (don't know why).

Basically, it's a heavily modified ppd for hp laserjet 6, and uses hpijs driver.

With the attached ppd you can use all OKI options, and you can set paper type, weight, 2 toner saver modes, tray/manual feed, etc.

With this ppd OKI prints at 600dpi. You can tell your printer to use 1200dpi too but hpijs doesn't support resolutions over 600dpi.

DON'T FORGET to switch off duplex printing in printer properties, otherwise each page you print will be followed by a blank one.

For those completely new to Ubuntu <like me :D >, download the attachment and double-click on it, then extract the .ppd file to a convenient location. Then go to System->Administration->Printing, Double-click on 'Add new printer', then follow instructions, when asked for printer model, click on 'install driver' and open your ppd file, then follow instructions again.

              I tried this file on Mandriva(2000) with a B2200 printer and according to the ppd helper file it is in the wrong format. I have tried other ppd files for the B4200 and the 2400 which Mandriva accepts but the printer won't do anything. I'm trying to become pro efficient at tar files  because urpmi and rmp are limited so this is not a concern.Can anyone recommend a legitimate dictionary for Linux off line. StarDict. is interesting but I don't need one for humor.  Any help in the right direction would be appreciated.              
                                Thanks in advance.

---

### Post by The KB Stockpiler on 2009-09-19
> **Easterly Wind said:**
> Hi,

For all those owners of OKI B4100 printers and other lower models in B series, I composed a ppd file and attach it to this post.

I checked it works with Dapper and Breezy, might work with other distributions, doesn't work on FC5 (don't know why).

Basically, it's a heavily modified ppd for hp laserjet 6, and uses hpijs driver.

With the attached ppd you can use all OKI options, and you can set paper type, weight, 2 toner saver modes, tray/manual feed, etc.

With this ppd OKI prints at 600dpi. You can tell your printer to use 1200dpi too but hpijs doesn't support resolutions over 600dpi.

DON'T FORGET to switch off duplex printing in printer properties, otherwise each page you print will be followed by a blank one.

For those completely new to Ubuntu <like me :D >, download the attachment and double-click on it, then extract the .ppd file to a convenient location. Then go to System->Administration->Printing, Double-click on 'Add new printer', then follow instructions, when asked for printer model, click on 'install driver' and open your ppd file, then follow instructions again.

        Is there a way to get this to work on Mandriva? When I try to set up the printer and load it as a ppd file the helper application won't accept it.
                                              Thanks in advance

---

### Post by dustingold09 on 2009-09-20
Hi ,
Easterly Wind !


Thanks for giving  information about printer driver , I am new for the Linux platform so i 

have no idea about , how to connect printer  to the computer with Linux OS ?




[Laser Printers]("http://www.brother.ca")

---

### Post by cmtek on 2009-10-14
it worked great with my oki b2200 too :P

---

### Post by Sigeuner on 2009-10-18
Hey Guys,

I have, maybe a quite simple Question, but actually im stucked a bit..

I got a Speedport V900W Router. The Oki B4100 is connected on the USB Port there. Normally, with a Windows Operation System, i have to send my printing messages by network to the ip:631. 
According to this i tried it with Linux and it.. doesnt work ^^ Well, anyhone has a clue what the Problem might be?

Thanx,

Sigeuner

---

### Post by Sigeuner on 2009-10-18
**update**
Well, acutally i tried it with Port 9100 and - it works ^^
Maybe s.o. can explain, why it works on Port 9100 and doesn't on 631 (Difference between Unix - Windows ? O.o )

-Sigeuner

---

### Post by euux on 2009-10-30
> **Easterly Wind said:**
> Hi,

For all those owners of OKI B4100 printers and other lower models in B series, I composed a ppd file and attach it to this post.

I checked it works with Dapper and Breezy, might work with other distributions, doesn't work on FC5 (don't know why).

Basically, it's a heavily modified ppd for hp laserjet 6, and uses hpijs driver.

With the attached ppd you can use all OKI options, and you can set paper type, weight, 2 toner saver modes, tray/manual feed, etc.

With this ppd OKI prints at 600dpi. You can tell your printer to use 1200dpi too but hpijs doesn't support resolutions over 600dpi.

DON'T FORGET to switch off duplex printing in printer properties, otherwise each page you print will be followed by a blank one.

For those completely new to Ubuntu <like me :D >, download the attachment and double-click on it, then extract the .ppd file to a convenient location. Then go to System->Administration->Printing, Double-click on 'Add new printer', then follow instructions, when asked for printer model, click on 'install driver' and open your ppd file, then follow instructions again.

:D :D :D it works in karmic koala !! thanks

---

### Post by bookworm1000 on 2009-12-04
Thank you so much,

worked with my OKI B2200!


Thanx,

bookworm

---

### Post by strider22 on 2010-02-07
This driver also worked for an OKI OKIdata B410d laser printer.
The printer has duplex printing and it works fine although so far I have only tested with text files.

I am puzzled though as to why neither of the supplied ppd files work.
There are 8 files but really 2 in 4 languages, so only 2 english. I tried both.

Can anyone explain why the supplied files don't work?

The symptom is one line printed per page starting with;
%!PS-Adobe-3.0
               %%Title: PPR Test Page
etc.

I did notice that the memory options in this file are 64 or 128Meg of ram. The printer spec say it comes with 32 Meg of ram. I added a line in the section below;

> *OpenUI *InstalledMemory/Memory Configuration: PickOne
*DefaultInstalledMemory: 64MB
*InstalledMemory 32MB/32 MB RAM: ""
*InstalledMemory 64MB/64 MB RAM: ""
*InstalledMemory 192MB/192 MB: ""
*?InstalledMemory : "
 currentsystemparams /InstalledRam get
 1024 idiv 1024 idiv 20 string cvs print (MB) = flush"
*End
*CloseUI: *InstalledMemory


This appears to be just a configuration option and it didn't change the problem at all so I assume I need to add an entry below but I don't know what values to use. If 192MB = 21886000 then why doesn't 64MB equal 1/3?

> 
*% _____ Memory Configuration(VM Size) _____
*FreeVM: "33554390"
*VMOption 64MB/64 MB RAM: "33554390"
*VMOption 192MB/192 MB: "33554420"

*% _____ Memory Configuration(FontCache Size) _____
*FCacheSize 64MB:5215000
*FCacheSize 192MB:21886000


Thanks.

---

### Post by lakeoftea on 2010-03-05
works great on 9.10.  thank you very much

---

### Post by duuchung on 2010-04-18
Dear comrades,

I had never successfully hooked up any printers to Linux since 2005 until today. I can now print with my OKI B2200 under Ubuntu.

Tks Ubuntu
Tks the gurus

---

### Post by begoodness on 2010-04-28
Hi, this post was really usefull to me. I configured it in 1 minute. THANK YOU!

---

### Post by hipericus on 2010-05-20
Works perfectly with OKI B2200!!!!


It has been the only place I did found a solution to the problem. I am using Ubuntu Karmic Koala, for next users information.

Just downloading the ppd file, and following your instructions. Great!!!!


Thanks a lot.

---

### Post by rikhard.fsoss on 2010-10-10
works great with Debian testing and #!CrunchBang 10 Statler before that i used to install HP 1100 laserjet driver.

---

### Post by lolo001 on 2010-10-13
It works great on my OKI B2200 with Ubuntu 10.10! Choose the ppd's drivers during the installation and set the first post file up!

Thanks

:)

---

### Post by aalxndrv on 2010-10-23
Thanks much!
Works fine on Ubuntu 10.10 / Oki B2200n

---

### Post by maydule on 2010-11-09
Another happy user! Thanks!!! :D
Works perfectly - b2200 & ubuntu 9.10

---

### Post by Alokin on 2010-11-16
Well, worked great for my OKI B2200 on 10.04, but since i changed to 10.10, it does, say 20% of the jobs, and just blinks red most of the time.
Not sure what's the problem...

Turn off / on the printer works sometimes, though... :)

---

### Post by Alokin on 2010-11-17
Correction: Today it prints just fine, though it still blinks red. I guess it's the printer:roll:, the driver is OK.:)

---

### Post by richler on 2010-12-18
Many thanks, it works on Fedora Core 14 too.

---

### Post by avz10 on 2011-01-06
Hi
I just want to know if this driver can be used for Windows as well. I have Windows 7

Regards

---

### Post by mhismail on 2011-01-09
> **Easterly Wind said:**
> Hi,

For all those owners of OKI B4100 printers and other lower models in B series, I composed a ppd file and attach it to this post.

I checked it works with Dapper and Breezy, might work with other distributions, doesn't work on FC5 (don't know why).

Basically, it's a heavily modified ppd for hp laserjet 6, and uses hpijs driver.

With the attached ppd you can use all OKI options, and you can set paper type, weight, 2 toner saver modes, tray/manual feed, etc.

With this ppd OKI prints at 600dpi. You can tell your printer to use 1200dpi too but hpijs doesn't support resolutions over 600dpi.

DON'T FORGET to switch off duplex printing in printer properties, otherwise each page you print will be followed by a blank one.

For those completely new to Ubuntu <like me :D >, download the attachment and double-click on it, then extract the .ppd file to a convenient location. Then go to System->Administration->Printing, Double-click on 'Add new printer', then follow instructions, when asked for printer model, click on 'install driver' and open your ppd file, then follow instructions again.



I am certainly jealous with the success several of you have had! I downloaded the driver. I went to the add printer option. However, unfortunately there is nothing I can do to get the printer to communicate with my HP mini. I have the printer on and the cable is plugged in! But the dialog box read, among others " Stopped - unplugged or turned off!! I am thoroughly .....
Pls help.

---

### Post by avz10 on 2011-01-11
> **Re: driver for OKI B4100 printer** 			
 			 			 		   		 		 		Hi
I just want to know if this driver can be used for Windows as well. I have Windows 7

Regards


Anyone can help me with this??

---

### Post by texaswriter on 2011-01-16
By the way. Linux kernel 2.6 and 2.4 drivers are available for some of these printers. Look up your printer on the okidata website below and check the os. If not, try a similar printer. Best of luck. 

[http://my.okidata.com/dsdownWeb.nsf/driverlookup/D9D9DDCB82AD7C498525773F005310B8?OpenDocument](http://my.okidata.com/dsdownWeb.nsf/driverlookup/D9D9DDCB82AD7C498525773F005310B8?OpenDocument)

Gooogle search: 

[http://www.google.com/search?client=ubuntu&channel=fs&q=okidata+linux+driver&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=okidata+linux+driver&ie=utf-8&oe=utf-8)

---

### Post by james_dk on 2011-02-24
Thanks for this...

Worked on the first attempt for me...

:)

---

### Post by dima206 on 2011-03-15
OkiData released official printer driver
[http://my.okidata.com/PP-B2200.nsf?opendatabase](http://my.okidata.com/PP-B2200.nsf?opendatabase)

---

### Post by exitcode on 2011-04-14
fine with b2200, thanks!

---

### Post by Mike843 on 2011-04-15
Thanks it worked first time. It is also my first request for assistance on Ubuntu and is most encouraging.

Any chance of you doing something similar for a Canon scanner N640P?
Mike

---

### Post by Johnston10.10 on 2011-05-01
The driver works pretty good with my OKI B2200 under Ubuntu 10.10, Ubuntu 10.04 and also OpenSuSE 11.4.

Only problem is: The printer only prints. There's no option to clean the printheads or print a self-test hardcopy like there was with the original OKI driver and software under Windows. And I'm badly in need of cleaning the printheads since the hardcopies I'm printing are getting stripes. 

There's also no option to see the charging level of the toner cartridge using this ppd-file under Linux. Well, at least the printer does the job... :D

Thanks for the upload!!

---

### Post by silove on 2011-05-30
Works great with my OKI B2200 on Ubuntu 11.04!


Thanks a lot!

---

### Post by crisgue on 2011-06-01
Hi, I need to install the OKI B420dn in Unix using the parallel port. I don't have driver.
What to do???

---

### Post by Clippy on 2011-08-29
Just a "heads up" - I just tried using the official OKI driver (i.e., [this one]("http://my.okidata.com/PP-B2200.nsf?opendatabase")), and found that I couldn't get the duplex to work. After fighting with it for a while, I used Easterly Wind's .ppd (the one posted at the beginning of this thread) and *voila*, duplexing worked. So, many thanks to Easterly Wind for the wonderful work - try his/her driver first! 

B410d on 10.04 Lucid

---

### Post by luismunhoz on 2012-07-04
Many thanks from me, too. Driver works perfectly under Ubuntu 12.04

---

### Post by gikacz on 2013-03-18
It doesn´t work on my Fedora 18. There is some information in Printers panel that B2200 is stopped, and if I make it started, it do nothing. When I transfer a job from my working HP printer to B2200, there is a the window which says that it isn´t possible because ¨B2200 doesn´t exist¨.
Please, help me if it possible.

---

### Post by Cannibal_Dog on 2014-01-22
> **luismunhoz said:**
> Many thanks from me, too. Driver works perfectly under Ubuntu 12.04

Oh my! Have spent 3 hours trying to get this going, now 3.30am. Had "memory overflow" error come up. Tearing my hair out, as (almost) everyone says here it works brilliantly.
Turns out just pushing ONLINE on the printer (B4300) got things going. Spat out error mesage, test print and my actual document all at once.
Will let you know how it goes in the future - thanks everyone!
On Ubuntu 12.04, totally new to this.

---

### Post by Fredrik_L on 2014-04-30
Works on xubuntu 14.04. Thank you.

---

### Post by vgalegov on 2015-01-29
Hello!
I have found the official driver. It works on the ubuntu 14.04 LTS fine.
[http://www.myokidata.com/dsdownWeb.nsf/driverlookup/90B6329133696B8585257A8000721484?OpenDocument](http://www.myokidata.com/dsdownWeb.nsf/driverlookup/90B6329133696B8585257A8000721484?OpenDocument)

---

