---
title: "HOW TO: Set up pdf printer"
date: 2006-03-07
forum: Tutorials
---

### Post by anil_robo on 2006-03-07
NOTE: This how-to is for Breezy users. For Dapper Drake users, please refer to this thread: [http://www.ubuntuforums.org/showthread.php?t=188860](http://www.ubuntuforums.org/showthread.php?t=188860)

1. Install cups-pdf package
```
sudo apt-get install cups-pdf
``` 
2.  Open Terminal
     sudo gedit /etc/cups/cupsd.conf
     Search for line RunAsUser Yes
     Change it in RunAsUser No

3. Now restart your computer or do a virtual reset of cups driver by ```
sudo /etc/init.d/cupsys restart
``` 4. Then go to System--> Administration--> Printing
Add printer
Select "Local Printer" and use a "detected printer--> PDF printer".
Manufacturer--> Generic,
Model-->PostScript Color Printer,
Driver-->Should come preselected with a green dot (rev3a)
Apply
 
Your pdf printer should be up and running by now... test it by printing a page from firefox or openoffice. Here is a sample: [ATTACH]7241[/ATTACH]

**Tip:** To further enhance the printing experience, you can follow the following steps:
1. In firefox, click File menu--> Page setup.
2. Select "Print Background (colors and images), then close it.
3. Open your printers setup by System--> Administration--> Printing
4. Right click the pdf printer and select properties (this may take some time to show up)
5. Set resolution to 1200 dpi if you want good quality (=bigger filesize) pdfs
6. In the paper tab, set paper size to A4
7. In the advanced tab, set PageRegion to A4 as well.

 **NOTE1:** [B]The printed files go to your home/PDF/ folder.
NOTE2:[/B] You can configure the printing options by System--> Administration--> Printing --> Right click on your printer, and select "properties"

---

### Post by Insanely on 2006-03-09
Awsome!

It won't take my username for CUPS web administration.

[http://localhost:631](http://localhost:631)

Was trying to get into their to rename it.

---

### Post by neoflight on 2006-03-09
nice...

i already had cups installed.. i didnt know that...

and still i follwed this howto and it works.....one question tho...

is it supposed to print it to ps? or it should directly give us a pdf?

and iam not getting all the color fields in this page for instance.... but its color i can see...but not all fields for eg, the brown color bar with 'reply to thread' text on it....

any idea?

---

### Post by arnieboy on 2006-03-09
The pdf printer got installed and everything went smoothly till I actually tried to print a document (convert it into pdf). It said that its printing and seemed to "spool" all the pages but after that the printing icon came into the system tray with the paused sign and it would keep going back into paused mode every time I would try to resume it. I checked the spool list and the document is listed there with the printer in paused mode(tried resuming it from there too but it went back into paused mode). Also, the "PDF" folder does not get created in the home folder. I tried creating it manually but even then it does not work... 
any ideas?

---

### Post by Insanely on 2006-03-09
Yeah I had the same arnieboy.

---

### Post by desperado666 on 2006-03-09
Cups-PDF needs to be run in root mode. So you have to edit file /etc/cups/cupsd.conf

Open Terminal

sudo gedit /etc/cups/cupsd.conf

Search for line RunAsUser Yes
Change it in RunAsUser No

Oringinal Howto can be found here
[http://wiki.ubuntuusers.de/Druckwerkzeuge?highlight=%28cups-pdf%29#head-568bc3e9ced669d8b5b7a125f987a288ae4c1286](http://wiki.ubuntuusers.de/Druckwerkzeuge?highlight=%28cups-pdf%29#head-568bc3e9ced669d8b5b7a125f987a288ae4c1286)
Its in german language.

After printing your pdf file is in your home directory.
New versions of Cups-pdf are available here
[http://cip.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/](http://cip.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/)

If you install new version the pdf file can be found in user/home/pdf
Edit : New Version of cups-pdf can be foudn here for various architecture types
[http://packages.debian.org/unstable/graphics/cups-pdf](http://packages.debian.org/unstable/graphics/cups-pdf)

---

### Post by anil_robo on 2006-03-09
[quote=Insanely]Awsome!

It won't take my username for CUPS web administration.

[http://localhost:631]("http://localhost:631")

Was trying to get into their to rename it.[/quote]

Im sorry I forgot to mention a little editing in the cups config file. The how-to has now been updates. Try it and lemme know if it works well. Thanks! :)

---

### Post by anil_robo on 2006-03-09
[quote=neoflight]is it supposed to print it to ps? or it should directly give us a pdf?[/quote]

It gives you a pdf file, not the postscript. This pdf file is compatible with acrobat and **all** pdf readers.

> and iam not getting all the color fields in this page for instance.... but its color i can see...but not all fields for eg, the brown color bar with 'reply to thread' text on it....

These forums are not the best pages to try printing. Open some other website. (I tried [www.buy.com](www.buy.com) and it prints well). Complex pages do not print well in web browsers I believe - its been my experience over the last 11 years. For your reference, I am attaching few pdf files generated using cups printer to this reply (bz archive). Take a look. [ATTACH]6880[/ATTACH]

---

### Post by anil_robo on 2006-03-09
Also look at this pdf file - its the default test page printed by cups pdf printer.
[ATTACH]6881[/ATTACH]

---

### Post by Jedeye on 2006-03-09
worked great thanks!

---

### Post by anil_robo on 2006-03-09
[quote=arnieboy]The pdf printer got installed and everything went smoothly till I actually tried to print a document (convert it into pdf). It said that its printing and seemed to "spool" all the pages but after that the printing icon came into the system tray with the paused sign and it would keep going back into paused mode every time I would try to resume it. I checked the spool list and the document is listed there with the printer in paused mode(tried resuming it from there too but it went back into paused mode). Also, the "PDF" folder does not get created in the home folder. I tried creating it manually but even then it does not work... 
any ideas?[/quote]

Arnav please edit the cups configuration file to allow non-root users to use this pdf printing system. (Refer to the starter thread again - I have included this information now). My apologies for the mistake.

---

### Post by KillerKiwi on 2006-03-09
Why is this not installed by default???

---

### Post by arnieboy on 2006-03-09
[QUOTE=anil_robo]Arnav please edit the cups configuration file to allow non-root users to use this pdf printing system. (Refer to the starter thread again - I have included this information now). My apologies for the mistake.[/QUOTE]
yes it worked with the correction suggested by desperado666. Thanks for updating your howto.

---

### Post by anil_robo on 2006-03-09
[quote=KillerKiwi]Why is this not installed by default???[/quote]

I don't know!
But I want it installled by default! It's so handy!
Take a look at [this]("http://www.ubuntuforums.org/showthread.php?t=140848")

---

### Post by froggay on 2006-03-15
thanks for the howto,
everything work great on my local machine.

I tried to share pdf virtual printer via samba to use it on windows.

I can see the job in the spool when i print from samba share but where is the pdf file ? i can't see it in /home/$user.

The job seems to be stuck, it doesn't dissappear from the spool

thanks for your help

---

### Post by anil_robo on 2006-03-15
[quote=froggay]thanks for the howto,
everything work great on my local machine.

I tried to share pdf virtual printer via samba to use it on windows.

I can see the job in the spool when i print from samba share but where is the pdf file ? i can't see it in /home/$user.

The job seems to be stuck, it doesn't dissappear from the spool

thanks for your help[/quote] 
Froggay,
I'm not in front of my Ubuntu Machine right now. So more details later. For now, see what level of security have you set for Samba (security=user, or security=share). If you have set security=user, you need to create user accounts on samba before others can use this.

To check, try accessing your ubuntu shared folders from the windows computer. If you can access them without entering username and password, security level is "share" and the printer should work fine from there.

More info is found in these threads:
 [http://www.ubuntuforums.org/showthread.php?t=106807]("http://www.ubuntuforums.org/showthread.php?t=106807")
[http://www.ubuntuforums.org/showthread.php?t=95123]("http://www.ubuntuforums.org/showthread.php?t=95123")
[http://www.ubuntuforums.org/showthread.php?t=89824](http://www.ubuntuforums.org/showthread.php?t=89824)
[https://wiki.ubuntu.com/NetworkPrintingFromWin2000](https://wiki.ubuntu.com/NetworkPrintingFromWin2000)
[http://www.ubuntuforums.org/showthread.php?t=61863](http://www.ubuntuforums.org/showthread.php?t=61863)
[http://ubuntuforums.org/showthread.php?t=20384](http://ubuntuforums.org/showthread.php?t=20384)
[http://www.ubuntuforums.org/showthread.php?t=10609](http://www.ubuntuforums.org/showthread.php?t=10609)

---

### Post by froggay on 2006-03-17
thanks a lot for your links anil_robo

my share works fine now with a HPlaserjet printer and folder share.

but the virtual pdf printer installed with cup-pdf doesn't work on windows throuh
g samba share.

on winodws when i connect to the "postscript-color-printer-(rev3)" i don't now which driver to use . 

a idea ?

thanks a lot

---

### Post by anil_robo on 2006-03-17
[quote=froggay]but the virtual pdf printer installed with cup-pdf doesn't work on windows throuhg samba share.

on winodws when i connect to the "postscript-color-printer-(rev3)" i don't now which driver to use .[/quote]

I am sorry, but my knowledge of Linux fails here! Maybe someone more competent can find a way of sharing virtual pdf printer through samba. There is a lot of information in the links I gave above, but many of them still elude me :(

---

### Post by Ancalagon on 2006-03-17
Sweet HowTo!

As it turned out I needed to download, build and install the latest cups-pdf to get 'PDF printer' to show up in the 'detected printer' window, but after that it worked ... after I also install gcc.

Has anyone found a way to PDF pages like these forum pages?  When I do they just come out all messed up.

I can print them to ps files, but was hoping to archive them as PDFs.

Thanks

---

### Post by akiro.yamamoto on 2006-03-18
Nice Job anil_robo ;)

---

### Post by GMachine_24 on 2006-03-18
Hi: Actually, I can print Ubuntu forum pages to a PDF file and they come out perfect. I use Acrobat Reader 7 to read the file - perhaps it depends on the reader you use..??

My problem is I'd like to be able to NAME the file before it shows up in my PDF folder labeled with incomprehensible gibberish.

Is there a way to do this before the pages are *printed* to PDF?

Thanks.

---

### Post by anil_robo on 2006-03-18
[quote=Ancalagon]Sweet HowTo![/quote] Thanks Ancalagon! :)

> Has anyone found a way to PDF pages like these forum pages?  When I do they just come out all messed up. I can print them to ps files, but was hoping to archive them as PDFs. 
1. In firefox, click File menu--> Page setup.
2. Select "Print Background (colors and images)
3. Open your printers setup by System--> Administration--> Printing
4. Right click the pdf printer and select properties (this may take some time to show up)
5. Set resolution to 1200 dpi if you want good quality (=bigger filesize) pdfs
6. In the paper tab, set paper size to A4
7. In the advanced tab, set PageRegion to A4 as well.

Now test it by File--> Print Preview. You can play around with these settings to suit your needs. And post your experiences here, so that I can update my how-to to make this even more useful to everyone! :) Thanks!

---

### Post by teataster on 2006-03-27
Thanks for all your efforts on this!

I have installed the printer on a Ubuntu machine acting as a print server and can print remotely, but the pdf file created is created on the network server- is there a way that I can save it on the local machine?

Also per the previous post, it would be useful if you could name the file when created, rather like pdf995 in Windows.

---

### Post by WoodyMahan on 2006-03-28
Followed Directions as noted and all worked great.  Thanks.

---

### Post by towsonu2003 on 2006-04-14
printed files go to /home/username instead of /home/username/PDF

other than that, excellent howto. I was tired of ps2pdf (although it's a perfect converter).

---

### Post by dnccnd on 2006-04-15
I have been looking into other threads in order to find out how to print web pages as PDF. I played a little with gs, gs-esp, gs-gpl, gs-common... but without success.

Now I have followed the instruction in this HowTo and everything seems to work, apart from the fact that my PDFs are wierd, with no text in it. I tried to print a simple page like [www.google.com](www.google.com) and there I can't see any text.

I can see though that the driver installed with the postscript-color-printer is "rev3" and not "rev3a". Could it be this the problem?

Thank you for helping...

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=dnccnd]
I can see though that the driver installed with the postscript-color-printer is "rev3" and not "rev3a". [/QUOTE]
mine is "rev3" as well. try enabling printing of background images in the Firefox>File>Page Setup dialog.

---

### Post by dnccnd on 2006-04-16
I tried but it doesn't work! When I open the pdf files with Document Viewer the text is still missing.

But then I installed Acrobat Reader and when I open the same files with Acrobat  everything looks fine!!! Apart from some small details...

Thank you!

---

### Post by anil_robo on 2006-04-16
[quote=dnccnd]I tried but it doesn't work! When I open the pdf files with Document Viewer the text is still missing.

But then I installed Acrobat Reader and when I open the same files with Acrobat  everything looks fine!!! Apart from some small details...[/quote]

I'm glad it worked. Some of the documents do not look alright in the document viewer - for everyone. So don't worry much. 

> Thank you!

You're welcome :)

---

### Post by Jergar on 2006-04-17
I've tried your Howto in Dapper and it works great. Thanks a lot!

Wolf

---

### Post by rogerioferro on 2006-04-23
I had cups-pdf installed and working very well in Dapper. But this weekend I update the system and its stoped work.
When I Select "Local Printer" doesn't have a "detected printer--> PDF printer" to choice.
Anybody know what happen?

---

### Post by shuttleworthwannabe on 2006-04-23
same here dapper kernel 2.6.15-21 todays update. Could not find the local printer. What happened??? Please help. This is what I was looking for all along!! I want it to work!

---

### Post by imagineit on 2006-04-23
By looking at the Debian changelog for cupsys it looks like the devs completely disabled the capability to run as root, which makes cups-pdf stop working.  Cupsys-pdf must be run as root so it can set file permissions.  The non-optimum solution I found to get it working again was to setuid root the cups-pdf binary.  I definitely would not do this on a multi-user system, but here is the solution anyways:

```
sudo chmod +s /usr/lib/cups/backend/cups-pdf
```

---

### Post by hentaidan on 2006-04-24
Why is it just when I have a need for something the updates go and break it :rolleyes: 

imagineit, that command works great, but how do you reverse it? I guess using:

```
sudo chmod -s /usr/lib/cups/backend/cups-pdf 
```

Is that correct?

---

### Post by gpw1 on 2006-04-25
[QUOTE=anil_robo]1. Install cups-pdf package
```
sudo apt-get install cups-pdf
``` 
2.  Open Terminal
     sudo gedit /etc/cups/cupsd.conf
     Search for line RunAsUser Yes
     Change it in RunAsUser No

3. Now restart your computer or do a virtual reset of cups driver by ```
sudo /etc/init.d/cupsys restart
``` 4. Then go to System--> Administration--> Printing
Add printer
Select "Local Printer" and use a "detected printer--> PDF printer".
Manufacturer--> Generic,
Model-->PostScript Color Printer,
Driver-->Should come preselected with a green dot (rev3a)
Apply
 
Your pdf printer should be up and running by now... test it by printing a page from firefox or openoffice. Here is a sample: [ATTACH]7241[/ATTACH]

**Tip:** To further enhance the printing experience, you can follow the following steps:
1. In firefox, click File menu--> Page setup.
2. Select "Print Background (colors and images), then close it.
3. Open your printers setup by System--> Administration--> Printing
4. Right click the pdf printer and select properties (this may take some time to show up)
5. Set resolution to 1200 dpi if you want good quality (=bigger filesize) pdfs
6. In the paper tab, set paper size to A4
7. In the advanced tab, set PageRegion to A4 as well.

 **NOTE1:** [B]The printed files go to your home/PDF/ folder.
NOTE2:[/B] You can configure the printing options by System--> Administration--> Printing --> Right click on your printer, and select "properties"[/QUOTE]
1. Install cups-pdf package
Code:

sudo apt-get install cups-pdf


2. Open Terminal
sudo gedit /etc/cups/cupsd.conf
Search for line RunAsUser Yes
Change it in RunAsUser No


I can't find "RunASUser" per your instructions. The first install worked fine. There is no "text as you stated, tried "Find" nothing there. Only been using Linus a few weeks:(

gpw1

---

### Post by hentaidan on 2006-04-25
[QUOTE=gpw1]I can't find "RunASUser" per your instructions. The first install worked fine. There is no "text as you stated, tried "Find" nothing there. Only been using Linus a few weeks:([/QUOTE]

Yeah I noticed that as well, but I added it the end for luck :rolleyes: 

Can't say whether it helped because the updates broke it (see above msg).

I noticed today that there have been some more updates to cupsys; the details say something about fixing permissions?

---

### Post by anil_robo on 2006-04-25
[quote=gpw1]1. Install cups-pdf package
Code:

sudo apt-get install cups-pdf


2. Open Terminal
sudo gedit /etc/cups/cupsd.conf
Search for line RunAsUser Yes
Change it in RunAsUser No


I can't find "RunASUser" per your instructions. The first install worked fine. There is no "text as you stated, tried "Find" nothing there. Only been using Linus a few weeks:(

gpw1[/quote] 
Click on this screenshot to see where runasuser lies.

[ATTACH]8745[/ATTACH]

 If it doesn't exist, you might create it as well. Remember Dapper is going through changes, so don't mind if something breaks. But this should work well in Breezy.

---

### Post by orev on 2006-04-26
Sweet.  I needed this feature.  Thanks.

---

### Post by Norppa on 2006-04-26
Does this work on Gimp? Has anybody tested?


- UBUNTU 4 LIFE -

---

### Post by Parkotron on 2006-04-26
I'm kind of surprised that this isn't included by default. Kubuntu comes with a PDF printer set up, so I assumed Ubuntu would to. It's definately a key feature.

---

### Post by towsonu2003 on 2006-04-26
[QUOTE=Norppa]Does this work on Gimp? Has anybody tested?
[/QUOTE]
not in my breezy. seems like it works, but it doesn't actually save the file..

---

### Post by dj1120 on 2006-04-27
Thank you. Followed your instructions and it worked -on the first try

---

### Post by Norppa on 2006-04-27
It looks as it would be printing it, the progress bar shows the printing, but I can't find the file. In other words it does not create it (like townsonu2003 pointed out). Does anybody know a printer for Gimp (if indeed this Cups does not work with Gimp) that produces/converts the files to PDF-files? 


UBUNTU 4 LIFE

---

### Post by timczer on 2006-04-27
I tried to get this to work, but it didn't.  I had the problem mentioned earlier, that the pdf option was not available when setting up a printer.  I tried the permission modification mentioned earlier as well.

Now, here is my real problem, printing doesn't work at all anymore.  I have restarted cups, removed the cups-pdf software, still no printing.  Everything seems to be still setup, my printer is still the default, but no print.  Can anyone help with this?

---

### Post by hentaidan on 2006-04-27
[QUOTE=Norppa]Does this work on Gimp? Has anybody tested?[/QUOTE]

Yes it works fine. You need the gimp-print plugin installed from Synaptic.

---

### Post by Norppa on 2006-04-27
[QUOTE=hentaidan]Yes it works fine. You need the gimp-print plugin installed from Synaptic.[/QUOTE]

How do I install this (I am very new to Ubuntu..)? I downloaded the package from the net but do not know how to install it. How do I do it through code?

---

### Post by towsonu2003 on 2006-04-27
[QUOTE=Norppa]How do I install this (I am very new to Ubuntu..)? I downloaded the package from the net but do not know how to install it. How do I do it through code?[/QUOTE]
Connect to net, open System>Administration>Synaptic, hit "Reload", search for gimp, find the proper plugin (I'm not using ubuntu here, so I donno), select it to install, click "apply" (this is the way to install anything)

PS. didn't test it w/ gimp-print yet, will test it later. let us know :)

---

### Post by hentaidan on 2006-04-27
[QUOTE=towsonu2003]find the proper plugin (I'm not using ubuntu here, so I donno)[/QUOTE]

gimp-print is the one you want.

Once its installed, open up an image in gimp, and go file > print. Click on "setup printer", select "standard command", and click on the drop down box. I get 3 printers listed: (Default printer); HP_PSC1210 and postscrip-color-printer (i.e. the pdf printer). 

Select the one you want, go OK, and click print.

---

### Post by Norppa on 2006-04-27
I installed gimp-print, but I still could not get Gimp to print PDF-files. Actually the package/plugin name was gimpprint-locales (locale data files for Gimp-print) (version 4.2.7-10) that I installed. Could not find anything else. What to do?

*I never thought I would want to produce PDFs this much...*

---

### Post by towsonu2003 on 2006-04-27
[QUOTE=Norppa]I installed gimp-print, but I still could not get Gimp to print PDF-files. [/QUOTE]
same here (just to confirm) -breezy-

---

### Post by Norppa on 2006-04-28
[QUOTE=hentaidan]gimp-print is the one you want.

Once its installed, open up an image in gimp, and go file > print. Click on "setup printer", select "standard command", and click on the drop down box. I get 3 printers listed: (Default printer); HP_PSC1210 and postscrip-color-printer (i.e. the pdf printer). 

Select the one you want, go OK, and click print.[/QUOTE]

Have you actually got this to work? I really could use this (PDF-printing). Does anybody know a separate program to accomplish this?

---

### Post by anil_robo on 2006-04-28
[quote=timczer]I tried to get this to work, but it didn't.  I had the problem mentioned earlier, that the pdf option was not available when setting up a printer. [/quote]

Are you using Dapper? I'm noticing even my cups-pdf is not working for the last few days... Dapper is going through heavy editions each day and that may explain some of this. I hope it'll be fixed soon.

---

### Post by hentaidan on 2006-04-28
[QUOTE=hentaidan]gimp-print is the one you want.[/QUOTE]

My apologies, it appears that gimp-print is only present in Dapper, not Breezy.

Just as a side note, a few programs (e.g. gedit/evince) use a common print dialog with an option to "Create PDF Document".

---

### Post by fparri on 2006-05-01
Cool, this saved my day on Dapper, Now, let's hope in a different, more secure, solution soon.

Thanks a bunch again :) [QUOTE=imagineit]I definitely would not do this on a multi-user system, but here is the solution anyways:

```
sudo chmod +s /usr/lib/cups/backend/cups-pdf
```[/QUOTE]

---

### Post by LordMau on 2006-05-02
Can cups-pdf set security level for created PDF? If yes, how? TIA.

---

### Post by timczer on 2006-05-02
Sorry, anil_robo.  I haven't had a chance to get back to this thread for a few days.  I got printing to work again.  I am using a compiled kernel (2.6.16) in Breezy.  I am guessing that the using the compiled kernel is the reason I do not get the pdf option.  I am wondering if there is anyone out there who is using a compiled kernel and got this to work?

---

### Post by WrathofthePenguin on 2006-05-04
Alright, I've got it all set up so that I can print directly to a pdf file. However, I'm not able to view the document correctly with Evince. If I print this page, for example, I can see the page layout and a lot of the graphics, but no text. If I transfer the document to my Windows machine and open it with Acrobat Reader it looks fine.

What else do we have that will allow us to view pdf files?

Also, is there a way to name the pdf file before it's written?

---

### Post by orev on 2006-05-04
I tend to use Adobe Acrobat on Ubuntu to view PDFs.  The probable most simple way to install this would be using Automatix, which you can find [here]("http://ubuntuforums.org/showthread.php?t=138405").

To my knowledge, there is no way to name the files before they print using this printer setup.

---

### Post by WrathofthePenguin on 2006-05-04
[QUOTE=orev]I tend to use Adobe Acrobat on Ubuntu to view PDFs.  The probable most simple way to install this would be using Automatix, which you can find [here]("http://ubuntuforums.org/showthread.php?t=138405").

To my knowledge, there is no way to name the files before they print using this printer setup.[/QUOTE]

I'm a little torn between starting a new thread for this problem and just continuing the discussion here, but since you're already familiar with the issue...

I've installed Adobe Acrobat Reader by downloading it directly from Adobe (rather than using Automatix). When I run it I get the Adobe banner on the screen for a second, which disappears quickly. Then nothing. I ran acroread directly from the command line with exactly the same result and no error message. Any ideas?

---

### Post by WrathofthePenguin on 2006-05-05
[QUOTE=WrathofthePenguin]I'm a little torn between starting a new thread for this problem and just continuing the discussion here, but since you're already familiar with the issue...

I've installed Adobe Acrobat Reader by downloading it directly from Adobe (rather than using Automatix). When I run it I get the Adobe banner on the screen for a second, which disappears quickly. Then nothing. I ran acroread directly from the command line with exactly the same result and no error message. Any ideas?[/QUOTE]

Ok, I've got a good solution (which I did not come up with on my own). I posted about the above problem in the Gnome Desktop Support forum, and somebody had a very good suggestion. Instead of trying to install Acrobat using what I downloaded directly from Adobe, use Synaptic. It worked like a charm. My pdfs now open up in Acrobat, and they display correctly. Apparentely, the problem is not with the pdf printing driver, but with Evince.

---

### Post by faulkner132 on 2006-06-01
[QUOTE=imagineit]By looking at the Debian changelog for cupsys it looks like the devs completely disabled the capability to run as root, which makes cups-pdf stop working.  Cupsys-pdf must be run as root so it can set file permissions.  The non-optimum solution I found to get it working again was to setuid root the cups-pdf binary.  I definitely would not do this on a multi-user system, but here is the solution anyways:

```
sudo chmod +s /usr/lib/cups/backend/cups-pdf
```[/QUOTE]
Just confirmed it, this fixes it on Dapper.
Thanks for the update.

---

### Post by chajuram on 2006-06-12
Hi,

I could not fine "RunAsUser" in the cups.conf file in dapper. I wonder if I am making a mistake, I tried following the instructions.

Chajuram.

---

### Post by digby280 on 2006-06-12
[QUOTE=chajuram]Hi,

I could not fine "RunAsUser" in the cups.conf file in dapper. I wonder if I am making a mistake, I tried following the instructions.

Chajuram.[/QUOTE]

I had the same problem.  You need this thread:
[http://www.ubuntuforums.org/showthread.php?t=188860](http://www.ubuntuforums.org/showthread.php?t=188860)

---

### Post by froggay on 2006-06-30
[QUOTE=teataster]Thanks for all your efforts on this!

I have installed the printer on a Ubuntu machine acting as a print server and can print remotely, but the pdf file created is created on the network server- is there a way that I can save it on the local machine?

Also per the previous post, it would be useful if you could name the file when created, rather like pdf995 in Windows.[/QUOTE]

please can you describe how did you manage to make a pdf virtual rinter server ?
i would like to use it from a basic unix distirb, like SUnOs

---

### Post by mattheweast on 2006-07-02
Nice guide! I've noticed somebody has put a version of it on the documentation wiki, can you confirm that this is ok?

See [https://help.ubuntu.com/community/forum/software/cups-pdf](https://help.ubuntu.com/community/forum/software/cups-pdf)

Thanks,

Matt

---

### Post by anil_robo on 2006-07-07
> **neoflight said:**
> 
is it supposed to print it to ps? or it should directly give us a pdf?


I apologize for a long delay in answering this question, but this virtual pdf printer stopped working ever since I upgraded to Dapper. However, now I have managed to get it working again.

Yes, cups-pdf can print to postscript files. To do this, use a little "print to file" checkbox during the printing confirmation dialogue box. It'll ask you where to save the file (default location is home directory) and you will see the postscript file there. Works excellent for me!

[ATTACH]12354[/ATTACH]

---

### Post by froggay on 2006-07-13
> **anil_robo said:**
> 

 **NOTE1:** [B]The printed files go to your home/PDF/ folder.
select "properties"


Can someone explain how to change the default pdf location ?

thanks

---

### Post by Eric DANE on 2006-10-16
A good (complete & working for me :cool: ) documentation is available in wiki mode at :
[https://help.ubuntu.com/community/PDFPrinting](https://help.ubuntu.com/community/PDFPrinting)

---

### Post by Mikesco3 on 2007-12-26
I had an issue with it not prompting me for a file name to where it would create the pdf. 
    So I checked the configuration file suggested a few threads above 
```
 sudo gedit /etc/cups/cupsd.conf
```
    And in one part the configuration file suggests that users of the group **lpadmin** would be allowed to print, so I thought I might point that out.
    You can add your username to the **lpadmin** group by going on the menu to 
 [LIST=1]
[*]  ***System \ Administration \ Users and Groups***
[*]  on the screen called  ***User Settings*** click on ***Manage Groups***
[*]  on the screen called  ***Groups Settings*** scroll down and select ***lpadmin*** 
[*]  click ***Properties*** put a check mark next to your username and click ***OK*** and close out of all the boxes
[/LIST]

---

### Post by riyasmp on 2008-01-17
hi

guys this is the result what i am gettig when i run the command sudo gedit /etc/cups/cupsd.conf

i don get Runas user Yes line at all, can you help please



# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
# Disable printer sharing and shared printers.
Browsing Off
DefaultAuthType Basic
<Location />
  # Restrict access to the server...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
  Allow localhost
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>]

---

### Post by riyasmp on 2008-01-19
sorry to post the above message, i have sorted it myself. if at all it helps any newbie like me

i actually was trying to install pdf printer on 7.10 which is pretty straight forward.install cups pdf and the add a new printer.

i will tell you the mistake i was repeating myself.when u print anything with your newly added pdf printer it saves ur file into the pdf folder inside ur home folder by default (as a pdf file)

but i was trying to print the file onto my dektop/usb disk which gave me a ps file.i thought my installation was wrong. but anyway i have found out the trick now.

if it helps anybody

thanks

---

### Post by atwin on 2009-02-15
Hi, I just set the PDF pronter as outlined and its working.  I can see the job processing but I am not getting any output file.  Where does the PDF printer save the PDF file?

Thanks,
atwin

---

### Post by anil_robo on 2009-02-15
> **atwin said:**
> Hi, I just set the PDF pronter as outlined and its working.  I can see the job processing but I am not getting any output file.  Where does the PDF printer save the PDF file?

Thanks,
atwin

Look for a folder named "PDF" in your home directory.

---

### Post by davidwhthomas on 2009-04-20
you may need to actually create a folder in your home dir called 'PDF'

```
cd ~
mkdir PDF
chmod 777 PDF
```

that was the final step that got it working for me Kubuntu 8.10
I also use the Generic CUPS/PDF driver.

---

### Post by n6yga on 2009-04-20
> **davidwhthomas said:**
> you may need to actually create a folder in your home dir called 'PDF'

```
cd ~
mkdir PDF
chmod 777 PDF
```

that was the final step that got it working for me Kubuntu 8.10
I also use the Generic CUPS/PDF driver.

Yep. That did the trick for me as well.

Mark.

---

### Post by nkjoep on 2009-07-08
I'm running Ubuntu 9.04 jaunty and the cupd-pdf printer won't work until you create the PDF directory in your home.

Each user who will use the cups-pdf printer should have PDF directory under the own home.

My pdf printer wansn't working... so i created the the directory 
```
cd
``` 
```
mkdir PDF
```

and everything work.

---

### Post by dmp2010 on 2010-09-10
Only ran the first command and then went to add printer from the System -->Admin. It works great.

Thank you.

---

### Post by dmp2010 on 2010-10-08
My pdf printer started print only first page for some reason. It has printed all pages in the past.

---

### Post by nba_1234 on 2011-02-22
> **anil_robo said:**
> NOTE: This how-to is for Breezy users. For Dapper Drake users, please refer to this thread: [http://www.ubuntuforums.org/showthread.php?t=188860](http://www.ubuntuforums.org/showthread.php?t=188860)

1. Install cups-pdf package
```
sudo apt-get install cups-pdf
```2.  Open Terminal
     sudo gedit /etc/cups/cupsd.conf
     Search for line RunAsUser Yes
     Change it in RunAsUser No

3. Now restart your computer or do a virtual reset of cups driver by ```
sudo /etc/init.d/cupsys restart
``` 4. Then go to System--> Administration--> Printing
Add printer
Select "Local Printer" and use a "detected printer--> PDF printer".
Manufacturer--> Generic,
Model-->PostScript Color Printer,
Driver-->Should come preselected with a green dot (rev3a)
Apply
 
Your pdf printer should be up and running by now... test it by printing a page from firefox or openoffice. Here is a sample: [ATTACH]7241[/ATTACH]

**Tip:** To further enhance the printing experience, you can follow the following steps:
1. In firefox, click File menu--> Page setup.
2. Select "Print Background (colors and images), then close it.
3. Open your printers setup by System--> Administration--> Printing
4. Right click the pdf printer and select properties (this may take some time to show up)
5. Set resolution to 1200 dpi if you want good quality (=bigger filesize) pdfs
6. In the paper tab, set paper size to A4
7. In the advanced tab, set PageRegion to A4 as well.

 **NOTE1:** [B]The printed files go to your home/PDF/ folder.
NOTE2:[/B] You can configure the printing options by System--> Administration--> Printing --> Right click on your printer, and select "properties"

I have the problem when i gedit /etc/cups/cupsd.conf
the runasuser yes do not appear and only come with this:
#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

so i cannot go through the whole procedure i dont know why????

---

### Post by attilab on 2011-03-11
same here, I guess something to do with:

# Administrator user group...
SystemGroup lpadmin

on home laptop is working, I have a PDF folder created automaticaly, but not on this machine...:(  and seem to me all ppl left this topic

---

### Post by tim.hoeffel on 2011-07-27
1. Install cups-pdf package
```
sudo apt-get install cups-pdf
```2.  Open Terminal
     sudo gedit /etc/cups/cupsd.conf
     Search for line RunAsUser Yes
     Change it in RunAsUser No
-------------------
Error message:
(gedit:2585): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.HMLNZV': No such file or directory

(gedit:2585): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

line: RunAsUser Yes not found in cupsd.conf
running NN 11.04

Suggestions? Thanks in advance :)

---

### Post by leopoldbirkholm on 2012-05-30
@ tim.hoeffel, the OP. Thank you for this simple but still very useful tutorial on how to get an PDF-printer on Ubuntu. 

Now I can save paper and be eco-friendly :-)

The code that worked for me:
```

sudo apt-get install cups-pdf

```

---

### Post by Stanwilliamsmusic on 2012-06-28
> **leopoldbirkholm said:**
> @ tim.hoeffel, the OP. Thank you for this simple but still very useful tutorial on how to get an PDF-printer on Ubuntu. 

Now I can save paper and be eco-friendly :-)

The code that worked for me:
```

sudo apt-get install cups-pdf

```
It just worked for me on Lubuntu 11.10

I printed a page of  my website and  another webpage  just now to test it.
The resulting .pdf  files were  in a directory it created  in my home folder named PDF.
 Thanks for the tip!

---

