---
title: "Is it possible to scan with no ink at all"
date: 2016-08-27
forum: Windows
---

### Post by tech291083 on 2016-08-27
Hi Friends,

I have been using this HP Deskjet 1050 All-in-One J410 Series printer for almost 2 years now without any problems. Both my cartridges ran out of ink two days ago. I wanted to scan an important document to PDF format, which I always do, but the device would not allow me to scan at all. I installed and re-installed the drivers so many times, but to no avail. As far as I know, scanning does not need any ink, so why am I not able to scan? Is this a common feature among all-in-one printer brands, that once there is no ink in both cartridges, the scanning would not be allowed?

This is first time ever that I have tried to scan without any ink whatsoever, that too by accident only. I called HP, but they won't support me since my device is out of warranty. I asked a couple of friends, but there was no clear answer from them either, also did some internet search, but that too confused me a bit.

Can you please guide me? Is some amount of ink a must to doing scanning work? I do not intend to blame HP, the manufacturer, but I am really very upset, if this is what happens when one runs out of ink, looking to scan, then its a shame.

Thanks & regards,

---

### Post by user1397 on 2016-08-27
What software are you using to scan?  The default ubuntu scanning app?

It doesn't make sense for it to require ink for scanning.

---

### Post by tech291083 on 2016-08-27
> **user1397 said:**
> What software are you using to scan?  The default ubuntu scanning app?


Oh no, I am using HP's own app called HP Printer Assistant, which got installed when I installed the required drivers on my Windows 7 Home Basic machine (fully protected with a paid anti-virus solution and Windows updates). I would love to install it on my Ubuntu 16.04 LTS Desktop machine as well. As soon as I power on the device, all the indicator lights start flashing, not stopping at all, no matter whatever I try.

> 
It doesn't make sense for it to require ink for scanning.


That's what I am thinking. Thanks.

---

### Post by n0wje on 2016-08-27
The HP software under windows 7 is likely causing the printer not to function as long as there a low ink or no ink error. in Ubuntu the scanner package will let the scanner scan without ink. I have a HP F4500 that has no ink at all, just for scanning only. Depending what you use you windows 7 box for I would switch to Ubuntu. Hope this helps.

---

### Post by howefield on 2016-08-27
Thread moved to the "Windows" sub forum.

Does the printer have a built in card reader that might let you scan straight to USB/SD card ect.

---

### Post by tech291083 on 2016-08-27
> **howefield said:**
> 
Thread moved to the "Windows" sub forum.


Thanks for moving it to the right place, please accept my apology for the inconvenience caused to you. 

> 
Does the printer have a built in card reader that might let you scan straight to USB/SD card ect.


Oh no, not at all.

Thanks.

> **n0wje said:**
> 
The HP software under windows 7 is likely causing the printer not to function as long as there a low ink or no ink error. 


I have had my doubts about this HP software from the day this issue first surfaced, and I did search the internet, and to my surprise there happened to be a few forums talking about the same issue, with the same brand and model no, but then again they were not that many in terms of numbers, forcing me to seek help here.

The whole issue is of very serious nature, if there is any truth in it. Companies must not mislead customers and force them to buy ink, if they do not want to or need to.

> 
in Ubuntu the scanner package will let the scanner scan without ink. I have a HP F4500 that has no ink at all, just for scanning only. Depending what you use you windows 7 box for I would switch to Ubuntu. Hope this helps.

This is really a good news. Well done Ubuntu. From the HP software it looks like both my cartridges are totally empty, but no one knows for sure. What annoys me most is that all the indicators lights keep flashing constantly from the moment the device is switched on. So far, I have not been able to stop them from flashing at all.

Thanks a lot.

> **user1397 said:**
> What software are you using to scan?  The default ubuntu scanning app?

It doesn't make sense for it to require ink for scanning.

So far, I have never used my printer in Ubuntu, but I have got a lot of inspiration from your reply and now I am excited to install the device in Ubuntu 16.04 LTS edition of mine. I did come across the following site, is this the right one for downloading drivers for Ubuntu? Thanks.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

This whole issue has left me pretty upset. Are there any all-in-one printers that allow to scan to both PDF and jpeg formats when there is no ink at all in both cartridges? If you know, then please let me know the make and model number. I will make sure that I buy them only. Thanks.

I just run into a forum topic, which seems to discuss a similar issue with the original poster asking the following query in quotes. Thanks.

> 
  The ink of my Canon PIXMA MP280 all-in-one inkjet printer just ran  out and I realized that not only I cannot print but I cannot scan (which  doesn't need any ink, of course).
  Upon making some further research it seems to me that it's a general  practice on the behalf of all-in-one inkjet printer manufacturers to  block the scanning function in order to "motivate" users to buy a new  cartridge as soon as possible.
  1) Is this true?
  As a conscious buyer in the future I'd rather like to reward  manufacturers that place the interests of their customers before their  profit and allow scanning even when the cartridge is empty.
  2) Does anyone know about any such manufacturers?
     


[http://superuser.com/questions/492971/are-there-any-all-in-one-printers-that-allow-scanning-after-the-ink-ran-out](http://superuser.com/questions/492971/are-there-any-all-in-one-printers-that-allow-scanning-after-the-ink-ran-out)

I have downloaded Ubuntu drivers for my AIO HP printer from the below site,

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

But will I be able to scan both, my photos and regular documents (papers) to jpeg as well as PDF format? I am easily able to do that with my AIO device in Windows 7 as the attached image shows, thanks.

---

### Post by user1397 on 2016-08-28
You probably can't scan directly to PDF with the default ubuntu scanning utility, but that doesn't really matter since there are many ways to convert a JPG or PNG image file to PDF.  So, say you scan your document in ubuntu using the default scan app, and it saves as a picture file.  Then go to this free service: [https://smallpdf.com/](https://smallpdf.com/)  and click on "JPG to PDF" and voila.

Also,  you probably don't need to do any manual installation of drivers.  When in ubuntu before you try anything else, just try plugging your printer in and see if ubuntu recognizes it by default.  HP printers usually automatically work out of the box in ubuntu.

*****EDIT: so I opened Simple Scan on my ubuntu laptop just to double check, and it actually does have an option to save to pdf.  After scanning the document just go to file > save as > pdf

---

### Post by tech291083 on 2016-08-28
> **n0wje said:**
> 
The HP software under windows 7 is likely causing the printer not to function as long as there a low ink or no ink error.


How correct you are!
My manager just asked this question on HP forums and got a very clear answer.

> 
The printer must have ink and pass the power on self test in order to continue and scan. Replace your ink.


[http://h30434.www3.hp.com/t5/Inkjet-Printing/No-scanning-after-no-ink-in-both-cartridges/td-p/5742300](http://h30434.www3.hp.com/t5/Inkjet-Printing/No-scanning-after-no-ink-in-both-cartridges/td-p/5742300)
 

> 
in Ubuntu the  scanner package will let the scanner scan without ink. 


I love Ubuntu even more now. Will definitely start scanning in Ubuntu ASAP. Thanks for letting me know.

> 
I have a HP F4500  that has no ink at all, just for scanning only. 


This is your personal experience and it means a lot to me, goes on to confirm that Ubuntu can be really handy when you do not want to buy ink as you do not want to print and rather stick to scanning process only. Brilliant info from you, just what I wanted. Thanks again.

> **user1397 said:**
> 
You probably can't scan directly to PDF with the default ubuntu scanning utility, but that doesn't really matter since there are many ways to convert a JPG or PNG image file to PDF.  So, say you scan your document in ubuntu using the default scan app, and it saves as a picture file.  Then go to this free service: [https://smallpdf.com/](https://smallpdf.com/)  and click on "JPG to PDF" and voila.


This is great, yes, you are right there are format converters online. Thanks indeed.


> 
Also,  you probably don't need to do any manual installation of drivers.  When in ubuntu before you try anything else, just try plugging your printer in and see if ubuntu recognizes it by default.  HP printers usually automatically work out of the box in ubuntu.


This is even better info from you, very encouraging. I will definitely start scanning in Ubuntu ASAP.

> 
I opened Simple Scan on my ubuntu laptop just to double check, and it actually does have an option to save to pdf.  After scanning the document just go to file > save as > pdf


I feel like crying, I will soon arrange an extra hard drive, which I have lent to a friend ASAP and install Ubuntu onto it.

You have helped me so much. I am very thankful to you. Regards.

---

### Post by user1397 on 2016-08-28
You're welcome!

---

### Post by tech291083 on 2016-08-30
> **user1397 said:**
> 
*****EDIT: so I opened Simple Scan on my ubuntu laptop just to double check, and it actually does have an option to save to pdf.  After scanning the document just go to file > save as > pdf


Hi,

I tried to scan immediately after installing Ubuntu 16.04 LTS Desktop 32-bit version, but although the printer was recognized, I could not scan at all. (image 1). I was very excited when you mentioned that there might not be any need for me to install drivers and Ubuntu might pick up the printer automatically, but unfortunately that did happen, although you are right, it might be my printer acting up.

Then I checked all the repositories to download updates from the GUI and then updated the system using the following 3 commands. Restarted the system and again tried to scan, but no success. (image 2)

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Finally, I went to the following site and downloaded the necessary drivers.

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

Then, as per the instructions on the below page, I tried to install drivers, something went wrong and I could not scan again. Here is what I tried.

```

john@john-To-be-filled-by-O-E-M:~/Downloads$ sh hplip-3.16.8.run
Creating directory hplip-3.16.8
Verifying archive integrity... All good.
Uncompressing HPLIP 3.16.8 Self Extracting Archivehplip-3.16.8.run: 464: cd: can't cd to hplip-3.16.8
  100%  hplip-3.16.8.run: 466: cd: can't cd to hplip-3.16.8
chown: cannot read directory './hplip-3.16.8': Permission denied
chgrp: cannot read directory './hplip-3.16.8': Permission denied

hplip-3.16.8.run: 479: cd: can't cd to hplip-3.16.8

HP Linux Imaging and Printing System (ver. 3.16.8)
HPLIP Installer ver. 5.1

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Tue-30-Aug-2016_13:44:08.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
 

INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...


INTRODUCTION
------------
This installer will install HPLIP version 3.16.8 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 16.04.

Is "Ubuntu 16.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the sudoer (john)'s password: 
 

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: q
john@john-To-be-filled-by-O-E-M:~/Downloads$ 
=======================================================================================

```


but now I see so many files in the Downloads folder, where I had download the original drivers ie hplip-3.16.8.run (image 3)

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Can you please help me? thanks.

Please visit the following link to view all the images. Thanks.
[https://postimg.org/gallery/rxm81x8u/](https://postimg.org/gallery/rxm81x8u/)

---

### Post by user1397 on 2016-08-31
It looks like you pressed q for quit in the end of that script instead of hitting enter to continue.  If the files in your downloads folder have become too convoluted I would just delete them all and re-download the hplip files from the website (make sure to move the files to a sensical folder somewhere after the download).  Then go through that script in the terminal and see where it takes you.  When in doubt, reboot.

---

### Post by tech291083 on 2016-09-04
> **user1397 said:**
> It looks like you pressed q for quit in the end of that script instead of hitting enter to continue.  If the files in your downloads folder have become too convoluted I would just delete them all and re-download the hplip files from the website (make sure to move the files to a sensical folder somewhere after the download).  Then go through that script in the terminal and see where it takes you.  When in doubt, reboot.

First of all, please accept my apology for reply so late. I will take into consideration what you have said. But right now, I do not have the device with me as I panicked and gave it for repairs. But once its back, I will follow your instructions, thanks a lot.

---

### Post by user1397 on 2016-09-05
No worries, I ain't losing sleep over it :P

---

### Post by tech291083 on 2016-09-13
Thanks, I am still waiting for my printer to come from the repairs shop.

---

