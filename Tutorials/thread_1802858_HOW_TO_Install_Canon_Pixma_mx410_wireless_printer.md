---
title: "HOW TO: Install Canon Pixma mx410 wireless printer"
date: 2011-07-12
forum: Tutorials
---

### Post by texla on 2011-07-12
The information in this thread has been moved to [https://help.ubuntu.com/community/InstallCanonPixmaMx410WirelessPrinterInUbuntu](https://help.ubuntu.com/community/InstallCanonPixmaMx410WirelessPrinterInUbuntu)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062085#post12062085](http://ubuntuforums.org/showthread.php?p=12062085#post12062085)

Thread closed.


This printer has a great and easy install method for Ubuntu.  Unfortunately, it does not install all of the tools that the Windows version does but it will allow you to print with wireless and scan (wired only I believe) with its software scangearmp.  This how to is for the wireless printer only. The download says 10.04 only but it has worked for me on 10.04 32 and 11.04 64bit, too - Also, check out the tweaks at the end of this post if you want more flexibility with resolutions and grayscale.

(this is just a note in case you get an error in the install because you had a previous pixma printer installed like a 32 bit forced onto a 64bit architecture.  I had to uninstall my mx330 like this and then all was good: sudo dpkg -r cnijfilter-common:i386 3.10-1)

(For wireless conectivity, I use a router with WPS button.  That can be setup easily from the printer.  The manual shows how to do this on p.46.  If you have one, do this step first before installation and Linux will see your printer in the install.  (If you don't have WPS then there is another method but I haven't used it - check with manual) From printer console: Menu:Device Settings:LAN Settings:WLAN Active:OK:Wireless LAN setup: WPS push button method : Go press WPS button for 5 seconds on router: Now click OK within 2 minutes on printer.)


OK - first, download drivers here:

[http://software.canon-europe.com/products/0011010.asp](http://software.canon-europe.com/products/0011010.asp)

Place them in your Home folder.
Untar the file (named something like Linux IJ Printer Driver MX410.tar) by double clicking on it - this will place all of the files in your home folder - some you will not need but just follow the instructions below and it will pick the correct ones for you.

 You can untar the guide and the deb.tar.gz files and then install the guide and follow the directions  (you can skip the preparation step in Ubuntu I believe, I did).
[COLOR=DarkRed]
[B]Or you can see them consolidated here below:
 [/B][/COLOR]
 (1)    Expanding the archived file and switching to the expanded directory
 

(on mine I had to replace the 3.50-x below with 3.50-1)


[user@zzz /yyy]$ tar zxvf cnijfilter-mx410series-3.50-x-deb.tar.gz
[user@zzz /yyy]$ cd cnijfilter-mx410series-3.50-x-deb
 

(2)    Installing the printer driver
  [user@zzz /yyy]$ sudo ./install.sh



 When the installation is completed, a message instructing you to register the printer is displayed.
  Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
>
  Check that the machine is properly connected and that the power is on. Then press the Enter key.
  

    

  2.    Select the connection method
  Select the connection method for this machine.
Select the connection method to be used, and then press Enter.
  1) USB
2) Network
Select the connection method.[1]
  For a USB connection, enter "1" and press the Enter key.
For a network connection, enter "2" and press the Enter key.
  The default selection value is displayed in [ ].
  

 
   

  3.    Select the printer
  From the list of detected printers, select the printer to be registered.
  (1)    Example when USB is selected
  Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
----------------------------------------------------------
0) Update
----------------------------------------------------------
Target printers detected
1) Canon MX410 series (/dev/usb/lp0)
----------------------------------------------------------
Currently selected:[1] Canon MX410 series (/dev/usb/lp0)
Enter the value. [1]

 Enter the number of the printer to be registered, and then press Enter.

Good Luck - This is a great printer for the money and very sturdy.  I had the 330mx until I spilled coffee on it, it was a tank.  BTW don't put any beverages by this bad boy - the top has no lid because of the ADF slot so everything goes right to the inside if something is spilled - it is no good, trust me!


Here's some tweaks as well - Go to admin - printers and duplicate the printer about two or three times.  Then gksudo nautilus and go into the etc/cups/ppd and click on one of your duplicates and add the following by replacing the lines with *OpenUI *Resolution/Output Resolution with these below:

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 300
*Resolution 100/100 dpi: "<</HWResolution[100 100]>>setpagedevice"
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CloseUI: *CNQuality

You can do this to each of them and then go in through printer settings and set them to different levels - this will save lots of ink.  You can even go up to 1200 dpi I believe but I'm not that crazy - there is a post about that somewhere from my mx330.

And for a Grayscale setting - you can go to one of your duplicates from the printer settings and go to job options.  Scroll down and where it says add. type CNGrayscale.  Then TRUE where it asks for a field and apply.  This printer you should rename to grayscale because it will always print in grayscale unless you go back in and change it to false.

---

### Post by jfmd on 2011-07-22
Thanks for the this handy guide, I'm running 10.10, I got my printer working through wireless, which is a first for me with linux!:)

---

### Post by texla on 2011-07-27
Glad this helped - I would like to see the mx410 work with SANE however to use Gscan2pdf and other linux programs.  I went through all the sane-backends install commands and the best results I have is this message:

found USB scanner (vendor=0x04a9 [Canon], product=0x174e [MX410 series]) at libusb:002:011
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

And then scanimage only sees my webcam.  Hopefully this will get added to SANE or someone will figure out a workaround.

---

### Post by landersohn on 2011-08-01
Based on this very cool How-To I bought the MX410. When I tried tyo run the install script, though, it gives me a bunch of errors.
First error is that it can not determine the package type (RPM vs. DEB). If I force it to DEB in the install script, the next error is that it can not find the package files.
I am running 10.04 64bit. I got the printer kind of working by installing the two deb files manually but am not sure whether I got all configuration files where they need to be.

---

### Post by texla on 2011-08-01
Hey Landersohn - I did this on my 10.04 32bit and it worked.  Don't see why it would hang on 64bit.
I'm not sure what happened on yours but I know that I started the way you ended - by installing the debs only and I think it worked well but I don't think it set up the wireless which is why I went for their method and that's what I wrote up above. If you need the wireless and/or just want to go for this again you might just want to **only** untar the deb file this time. 

 If you click on the file you downloaded: it should be called (Linux IJ Printer Driver MX410.tar) - you can then select **only **the deb file to untar.  This way you are not even putting the rpm file into your home folder.  Then make sure the file is in your home folder (copy paste it if it is not there).  You may also want to untar the en file because that is the guide that says what the rest of the how to says (except for the tweaks)

With this command below you can get it opened:

 tar zxvf cnijfilter-mx410series-3.50-1-deb.tar.gz

 Also be very careful that you type in exactly the model number in the instructions in (3.50-1 is what you should have downloaded)

then :
cd cnijfilter-mx410series-3.50-1-deb

and then:
sudo ./install.sh


then the rest of the howto should apply.  Now I did have my wireless set up with a wps setting on my router before I did any of this and that made the selecting of the printer very easy during the install.  If you haven't done this then go through it - it can all be done between the printer and your router without using the computer.  If you don't have the wps you can enter the password and all of that is in their printed guide either with the printer or you can download it from their usa site I believe.
Hope you get it going.

---

### Post by closbar on 2011-10-04
hello my friend can you help me with the installation of the mx410 drivers i download the drivers but can install them. I tried in one dell laptop and in one acer notebook when I try to  install them trough terminal it said error. Thanks for your help

---

### Post by harvc on 2011-10-09
Very helpful. Worked perfectly for me. Is much appreciated.

---

### Post by texla on 2011-10-09
> **harvc said:**
> Very helpful. Worked perfectly for me. Is much appreciated.
Glad to hear it, harvc!  Closbar, I don't know what to tell you.  These types of installations can be a bit tricky for a newcomer to linux (if that is what you are - please excuse me if I am wrong!) This is why I tried to be as detailed as possible in this how to.  I will try to help though:

a. One thing to be careful of is to make sure that the tar.gz file is in your home directory when you type the tar command into the terminal. Otherwise, this will surely not go forward. 

b.  make sure you type in exactly the model number in the  instructions in place of all the 350-x lines - (3.50-1 is probably what you have)

so it should say :
cd cnijfilter-mx410series-3.50-1-deb

 c.  As an emergency, you could always just install the USB version by opening up the tar.gz file and finding either the 32bit or the 64 bit deb and double clicking on it depending on which one you are using.  This will give a default install through the ubuntu install program and should work great but it will not give wireless like the above method does.  All the tips will work though afterwards to get grayscale and different resolutions.

d.  speaking of wireless - if that is indeed the method you are trying, it could be very problematic so go the USB route for now and do some research on wireless as it applies to this printer, your router at home and your laptop or desktop - those can all be sources of trouble!

---

### Post by heyitseric on 2011-10-21
all i did to install is unpacked cnijfilter-mx410series-3.50-1-deb.tar.gz, when i got to the folder cnijfilter-mx410series-3.50-1-deb, i did a right click on install.sh and chose open in terminal and it did all the work for me.

---

### Post by texla on 2011-11-12
That's cool - will try that as well next time!

---

### Post by Kevin108 on 2011-12-27
I've installed these drivers without issue previously but now these directions don't seem to work.

[PHP]kevin@Serenity ~/Downloads/Canon/Printer/cnijfilter-mx410series-3.50-1-deb $ sudo ./install.sh
sudo: ./install.sh: command not found

[/PHP]Any help would be appreciated!  I've been distro hopping and partially restored my configuration from a /home backup.  Is it possible that the drivers are there (though aren't visible in Printing) and conflicting with the install script?

---

### Post by texla on 2011-12-27
I suppose in your case there may be a problem because of the restore.  I know that I had to completely uninstall my other Canon printer (Pixma 350)  to get this one to install correctly.

I'm no Ubuntu guru by any means - still new at this - but here's some ideas:
1. You may need to look at some uninstall techniques for your 410 drivers like I posted for my Pixma 350
earlier in this how to (but I'm not sure how it would apply to the 410) then reinstall.

2. Just in case, you opened up the [COLOR=#000000][COLOR=#0000BB]cnijfilter[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]mx410series[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]3.50[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]deb [/COLOR][/COLOR]folder in your printer folder and saw the install.sh file there right?  If not, you should just get it back by running the untar command on the original tar.gz 

good luck

---

### Post by Kevin108 on 2011-12-27
I wiped the drive and reinstalled.  Decompressed the files from the archive and took the extra step of naming the directory something simple and placing it in /home/kevin

kevin@Serenity ~/printer $ ls
install.sh  packages  resources
kevin@Serenity ~/printer $ sudo ./install.sh
[sudo] password for kevin: 
sudo: ./install.sh: command not found
kevin@Serenity ~/printer $

---

### Post by Kevin108 on 2011-12-28
Just had a thought.  I had copied the decompressed files to an NTFS partition and back to my EXT4 so I've totally lost the various permissions.  I'm going to download the drivers again to restore the permissions (as I know OF chmod but don't know the numbers off the top of my head) and I believe that will take care things.  Reporting back in a few.

Worked perfectly.  Sorry for being a noob and wasting your time.  I'm learning though.  Thank you for your help and the excellent write-up!

---

### Post by susja on 2012-02-13
Hey Folks,
Maybe someone could help me?
I'm stuck with my Canon MX410 wireless all-in-one. I'm all set with printer but I have a problem with scanner. I downloaded scanner driver 1.70 and successfully installed it as I did with printer. The problem is when I  try to scan a document. It failed to find PC. Well scanning is very important for me ... so please help if you could. Maybe driver 1.70 is not good ? or something else ... I tried to install driver again and again and every time it succeed but failed to redirect to PC. I'm just confused why it works with printer but does not with scanner.
Any help would be appreciated.
Thanks.

---

### Post by japzone on 2012-02-16
Thanks for this! I got a Cannon Pixma mx495 on sale at Office Depot and was confused as to why I couldn't change the Print Quality on it while I was able to easily do it on the Network Shared wired HP printer hooked up to my Windows PC. Duplicating the Printer and Modifying the ppd as prescribed is a nice workaround. Not as convenient as having the option to change at print time(as I was able to on the HP) but good enough.

---

### Post by texla on 2012-02-16
> **susja said:**
> Hey Folks,
Maybe someone could help me?
I'm stuck with my Canon MX410 wireless all-in-one. I'm all set with printer but I have a problem with scanner. I downloaded scanner driver 1.70 and successfully installed it as I did with printer. The problem is when I  try to scan a document. It failed to find PC. Well scanning is very important for me ... so please help if you could. Maybe driver 1.70 is not good ? or something else ... I tried to install driver again and again and every time it succeed but failed to redirect to PC. I'm just confused why it works with printer but does not with scanner.
Any help would be appreciated.
Thanks.
Maybe your trying to scan with wireless?  You cannot scan wireless (wirelessly?) with linux and this printer.   You will have to be connected through a usb port to scan.  If that's not the problem you may need to do a complete reinstall following the instructions because I have had no problems with the scanner through usb.  Scangear can be a bit tricky of a program to use and that could be another source of your problem - I think it needed a workaround before but I'm not sure if it still needs it.  However, simple scan in the ubuntu repos should work fine with this scanner - once you are installed properly and again NO wireless option with this pixma and ubuntu.

---

### Post by susja on 2012-02-21
hi folks,
just noticed this thread and speculation about being able to scan wordlessly and etc.
Just wanted to let you know that I was able to connect my MX410 wirelessly to my router and print and scan.
Regards,
susja

---

### Post by texla on 2012-02-22
That's great!  So you got the scanner to work with wireless after all.  How?

---

### Post by susja on 2012-02-22
well ... I think I didn't do anything special. Just installed scan driver and then started scangear on my PC. First time I failed because I expected that I could just scan from printer and it'll recognize my PC but after that I realized that process should start from PC / scangear. Then it recognizes my scanner and I'm all set.

---

### Post by texla on 2012-02-22
Mine in 64 bit is still not working unless plugged in - glad yours is all good though! Are you using 32 bit?

---

### Post by susja on 2012-02-22
yes, mine is 32 bit

---

### Post by maxmojo53 on 2012-03-06
Thanks for this post.  I tried looking for a linux driver in Canon USA and it states in RED that the 410 is incompatible with linux.  I wonder why?  Anyway thanks again.

---

### Post by texla on 2012-03-06
> **maxmojo53 said:**
> Thanks for this post.  I tried looking for a linux driver in Canon USA and it states in RED that the 410 is incompatible with linux.  I wonder why?  Anyway thanks again.

No clue why they say that - probably because it is very poorly supported in comparison to all the fancy and useful software they developed for Windows that doesn't work on Linux at all - maybe even they say that for more reasons... But these workarounds make it quite useful - that's not to say there may not be other printers worth supporting more that want to work with Linux - this one is just a good one for my purposes but I do have to go to the dark side and use the Windoze programs from time to time to get the full use of it - so it goes...

The European link to the drivers should work though - wonder for how long though...

---

### Post by Ricalsin on 2012-03-25
Wonderful Post!  I especially liked the tweaks to provide easy control of the dpi and grayscale printing.  Thanks!  

For those WITHOUT a WPS enabled router you will need to enter the WEP Key into the printer's "Device Settings>LAN Settings>Wireless LAN Setup>Easy Setup .. which will discover your wireless signal and display it on the screen for you to "OK".  BUT THAT'S NOT THE END OF IT.   Once you OK the signal the printer will show it as your choice...BUT THEN YOU HAVE TO ENTER "Ok" AGAIN, in order to present to you the prompt for the WEP Key that will enable the communication.  Sadly, I found no such mentioning of this in the User manual.  Hope that helps.  

Great printer, BTW.  It's worth the trouble to set it up on a Linux system.  I bought it for $69 at Fry's Electronics.  Nice!

---

### Post by bmanzana on 2012-04-17
just wanted to say thank you for this install guide, it was easy to do and made perfect sense. thanx again you saved the day for me!

---

### Post by JosephC on 2012-04-19
First, thanks to everyone for the help. But I think it would be wise to reiterate, perhaps more clearly, that wireless scanning is possible in Ubuntu with the MX410, but apparently only through the Canon Scangear Software (Scan Gear MP), which is available, tested, and working with Precise, by installing the following .deb:

[http://support-sg.canon-asia.com/contents/SG/EN/0100330601.html](http://support-sg.canon-asia.com/contents/SG/EN/0100330601.html)

Terminal command to run the software, or if you want to make a menu link, is scangearmp. 

However, (the best way for GUI users) Scan Gear is also conveniently accessible through GIMP by default - File > Create > ScanGear MP. So make sure you have GIMP installed, then all you have to do is ignore the warning that ScanGear isn't recognizing the scanner (assuming you've already got it turned on and broadcasting wirelessly) then click "Update Scanner List" and it will detect the MX410 scanner. That's it. Wireless scanning on Ubuntu with MX410.

Very easy. Hope that helps. Hurray for Canon for supporting Ubuntu!

P.S.
I didn't have to install the MX410 printer drivers in 12.04, as they seem to be included with Ubuntu now, as the MX410 now works out of the box. I only needed to install ScanGear to get wireless scanning to work.

---

### Post by forrestallen on 2012-04-28
I lost printing after the upgrade from 11.10 to 12.04; this saved the day, and my MX410 is again printing wirelessly through my LAN.

Thank you!

---

### Post by zylden on 2012-05-02
Hi 
I am running 12.04 64bit, my wife uses 32bit. We have the canon MX410 printer.
Printing wireless is not my problem. That has always worked straight from the box.

My problem is my printer is printing at a very high quality and I cant get the thing to print in grayscale or a lower resolution. It doesnt give me an error but just never prints the document. As soon as I put it back, it prints.

Any ideas? This is using up my ink very quickly.

---

### Post by texla on 2012-05-02
Yes you can - the tweaks are a bit technical that were on my first post but here they are again.  They are not too bad but you do have to go into the terminal and type in the gksudo nautilus command.  Then you use the browser that opens to find the etc folder, the cups folder, and edit the files inside with these tweaks.  The result will never print higher than 600dpi and will also give you Grayscale and lower res options like 300 or 100 dpi.  But they will all look like other printers in Ubuntu.  So you choose your default printer after the tweaks are made.  then whenever you want something different, you just choose the printer with the resolution you want.  Here' s the original post with a few extra instructions below in case you need them:

 Go to admin - printers and duplicate the printer three or four times.  Then in your terminal, enter the command: gksudo nautilus and go into the etc/cups/ppd  and click on one of your duplicates and replace  the paragraph that starts with the lines:
*OpenUI *Resolution/Output Resolution...

with all of the text below:

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 300
*Resolution 100/100 dpi: "<</HWResolution[100 100]>>setpagedevice"
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CloseUI: *CNQuality



You can do this to each of them (although save your original printer just in case!) and then go in to the printer settings through admin again  and set them to different levels - this will save lots of ink.   I then renamed each printer as lo-res (100dpi normal quality), med-res (300 dpi normal quality) and hires (600 dpi high quality)

And for a Grayscale setting - you can go to one of your duplicates from  the printer settings and go to job options.  Scroll down and where it  says add. type CNGrayscale.  Then TRUE where it asks for a field and  apply.  This printer you should rename to grayscale because it will  always print in grayscale unless you go back in and change it to false. 		                   		  		  		  		  		 		 			 				 				* 					 						good luck!*

---

### Post by zylden on 2012-05-14
> **texla said:**
> Yes you can - the tweaks are a bit technical that were on my first post but here they are again.  They are not too bad but you do have to go into the terminal and type in the gksudo nautilus command.  Then you use the browser that opens to find the etc folder, the cups folder, and edit the files inside with these tweaks.  The result will never print higher than 600dpi and will also give you Grayscale and lower res options like 300 or 100 dpi.  But they will all look like other printers in Ubuntu.  So you choose your default printer after the tweaks are made.  then whenever you want something different, you just choose the printer with the resolution you want.  Here' s the original post with a few extra instructions below in case you need them:

 Go to admin - printers and duplicate the printer three or four times.  Then in your terminal, enter the command: gksudo nautilus and go into the etc/cups/ppd  and click on one of your duplicates and replace  the paragraph that starts with the lines:
*OpenUI *Resolution/Output Resolution...

with all of the text below:

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 300
*Resolution 100/100 dpi: "<</HWResolution[100 100]>>setpagedevice"
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CloseUI: *CNQuality



You can do this to each of them (although save your original printer just in case!) and then go in to the printer settings through admin again  and set them to different levels - this will save lots of ink.   I then renamed each printer as lo-res (100dpi normal quality), med-res (300 dpi normal quality) and hires (600 dpi high quality)

And for a Grayscale setting - you can go to one of your duplicates from  the printer settings and go to job options.  Scroll down and where it  says add. type CNGrayscale.  Then TRUE where it asks for a field and  apply.  This printer you should rename to grayscale because it will  always print in grayscale unless you go back in and change it to false.                                                                                                                                    *                                              good luck!*

Hey
thank, I redid the whole process and now it works. I must have done something wrong the first time.

---

### Post by harvc on 2012-05-26
> **JosephC said:**
> First, thanks to everyone for the help. But I think it would be wise to reiterate, perhaps more clearly, that wireless scanning is possible in Ubuntu with the MX410, but apparently only through the Canon Scangear Software (Scan Gear MP), which is available, tested, and working with Precise, by installing the following .deb:

[http://support-sg.canon-asia.com/contents/SG/EN/0100330601.html](http://support-sg.canon-asia.com/contents/SG/EN/0100330601.html)

Terminal command to run the software, or if you want to make a menu link, is scangearmp. 

However, (the best way for GUI users) Scan Gear is also conveniently accessible through GIMP by default - File > Create > ScanGear MP. So make sure you have GIMP installed, then all you have to do is ignore the warning that ScanGear isn't recognizing the scanner (assuming you've already got it turned on and broadcasting wirelessly) then click "Update Scanner List" and it will detect the MX410 scanner. That's it. Wireless scanning on Ubuntu with MX410.

Very easy. Hope that helps. Hurray for Canon for supporting Ubuntu!

P.S.
I didn't have to install the MX410 printer drivers in 12.04, as they seem to be included with Ubuntu now, as the MX410 now works out of the box. I only needed to install ScanGear to get wireless scanning to work.

Thank you for this post. I can now scan wirelessly too. Your help has been greatly appreciated.

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/InstallCanonPixmaMx410WirelessPrinterInUbuntu](https://help.ubuntu.com/community/InstallCanonPixmaMx410WirelessPrinterInUbuntu)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012414](http://ubuntuforums.org/showthread.php?t=2012414)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

