---
title: "HOWTO: Lexmark Printers"
date: 2005-07-17
forum: Tutorials
---

### Post by black hole sun on 2005-07-17
Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

> Lexmark 5700 (black & white only)
Lexmark X1100 
Lexmark X1110 
Lexmark X1130 
Lexmark X1140 
Lexmark X1150 
Lexmark X1180
Lexmark X1185 
Lexmark Z513 
Lexmark Z515 
Lexmark Z715
Lexmark Z55 
Lexmark Z615 
Lexmark Z705 
Lexmark Z605 
Lexmark Z600 
Lexmark Z25 
Dell A920
Z65 (z65 driver)
Lexmark Z33 (z35 driver)
Lexmark Z33 (z35 driver)With that said, let's get to it! :D

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```

The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:> direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.

---

### Post by michellembrodeur on 2005-07-27
[QUOTE=black hole sun]Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

With that said, let's get to it! :D

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```

The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:If you get no output at all, you have problems.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.[/QUOTE]



Thanks for trying though

I have a z35 and it didn't work. It initialized and move the paper but that was it.

also the last line 
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped

couldn't do because there was no .gz at the end
but z600 showed up in the folder where it was supposed to be
and the test came out ok with
"direct z600:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer""

but no luck on my end.

thanks anyway.

---

### Post by black hole sun on 2005-07-29
[QUOTE=michellembrodeur]Thanks for trying though

I have a z35 and it didn't work. It initialized and move the paper but that was it.

also the last line 
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped

couldn't do because there was no .gz at the end
but z600 showed up in the folder where it was supposed to be
and the test came out ok with
"direct z600:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer""

but no luck on my end.

thanks anyway.[/QUOTE]
 Did you try the z600 or z35 driver? Your printer should be able to work!

---

### Post by newage on 2005-07-29
thanks dude!! i have lexmark z615 and it really helped me!!! thanks a lot again :)

---

### Post by Spudgun on 2005-07-30
Hmm, I can't select another driver to use in the Gnome printer tool, anyone know why this is?

Thanks in advance.

---

### Post by black hole sun on 2005-07-30
[QUOTE=Spudgun]Hmm, I can't select another driver to use in the Gnome printer tool, anyone know why this is?

Thanks in advance.[/QUOTE]
What do you mean by "another driver"? You mean the lexmark one?

Have you re-started CUPS?

---

### Post by michellembrodeur on 2005-07-30
I found this for the z35 somewhere else on these forums.

it work no problem for a Z35

OK, this will take some skill on your part, but it can be done.

First, log in as root and download the drivers from

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242)

Make a directory and put the Lexmark driver in it... Let's assume we named it LEX, and that folder is sitting in /root OK? (in all of the commands, you do not type the # key, this is just to signify the prompt)

OK, so we have moved the driver into the folder now, and we will go into the folder by opening a command prompt and typing:

# cd /root/LEX

We will now extract the archive by typing the following command:

# tar -xzvf CJLZ35LE-CUPS-2.0-1.TAR.GZ

This now leaves us with a shell script rpm installer called lexmarkz35-CUPS-2.0-1.gz.sh... not very useful to a Debian distribution like Xandros, so now comes the fun part...We will make another directory now, and extract the files into it...

# mkdir lextemp

# tail -n +143 lexmarkz35-CUPS-2.0-1.gz.sh | gzip -cd | tar xvf - -C lextemp

Now we will enter the lextemp directory and convert the rpm files, since Xandros should not use rpms unless absolutely necessary.

# cd lextemp

# alien -t *.rpm


Next, we will use the tar command to extract the files to their proper place.

# tar -zxf lexmarkz35-CUPS-2.0.tgz -C /

# tar -zxf z35llpddk-2.0.tgz -C /

Now for some editing... type the following commands in the order shown below..

# cd /usr/local/z35llpddk/utility

# ln -s auckUS.lut bnsi1.lut

# cd /usr/lib

# ln -s liblexz35core.so.0.0.0 liblexz35core.so.0

# ln -s liblexz35printer.so.0.0.0 liblexz35printer.so.0

# ln -s liblexz35printjob.so.0.0.0 liblexz35printjob.so.0

Now to test and see if the driver is working...

# /usr/lib/cups/backend/z35

Output should not error out, and give an output similar to this...

direct z35:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer"

OK, if all is well, we allign the print heads by typing;

# /usr/lib/cups/backend/z35 utilities

Now that the heads are aligned, we can select the printer in the control center by following Launch > Control Center. Once in there in the Periphrial devices section there chould be a setting called printers... highlight printers and then go to add >local printer > Lexmark inkjet color printer and now under the model number one should see an entry for Z35 v 2.0-1... Select that, and then do your test page... Congrats, You're finished!

Hopefully Xandros will eventually make a Debian installer for this driver, but until then this works pretty well... Best of Luck, and hope this helps..

the howto worked really find under hoary.
only problem i have is that i am able to print the testpages with the utility software, but when i add the printer via cups to use it with other applications nothing will happen.

perhaps someone can help me
---------------------------------------

Do not thank me. someone else came up with it.

Something to remember, you need both b&W and colour catridages. I have only colour and it will not print black. But windows can use the colour to make black, but not linux. someday hope that willb e fixed.

---

### Post by jerrybme on 2005-08-02
@black hole sun

Your How-to worked fine for me, I get the following output at your last step:
```
jerry@Tuxbox:/usr/lib/cups/backend$ ./z600 
direct z600:/dev/usb/lp0 "Lexmark  Lexmark 510 Series" "Lexmark Printer"
jerry@Tuxbox:/usr/lib/cups/backend$
```
I use the gnome utility to configure the printer & chose the Z600 driver but when I send a test page to my Lexmark Z515, nothing happens  ](*,) 

The gnome utility doesn't show any pending jobs. I'm at a loss.

Any suggestions? Also don't think it'd make a difference but I'm running the 64 bit Hoary version

---

### Post by black hole sun on 2005-08-03
[QUOTE=jerrybme]@black hole sun

Your How-to worked fine for me, I get the following output at your last step:
```
jerry@Tuxbox:/usr/lib/cups/backend$ ./z600 
direct z600:/dev/usb/lp0 "Lexmark  Lexmark 510 Series" "Lexmark Printer"
jerry@Tuxbox:/usr/lib/cups/backend$
```
I use the gnome utility to configure the printer & chose the Z600 driver but when I send a test page to my Lexmark Z515, nothing happens  ](*,) 

The gnome utility doesn't show any pending jobs. I'm at a loss.

Any suggestions? Also don't think it'd make a difference but I'm running the 64 bit Hoary version[/QUOTE]
 :(

 I have no idea why it's not working for you. It might be due to your 64 bit environment but i doubt that...

When you typed in the printer location did you put in /dev/usb/lp0? I am not in gnome at the moment and i cant quite remember what i did to get my printer working but i remember having to manually enter a /dev/ location for my printer; perhaps you didnt do that?

Also make sure you have ghostscript installed (search for in synaptic)

---

### Post by jerrybme on 2005-08-12
Well, it turned out to be a 64 bit library linkage problem. I created a 32 bit chroot and the printer driver works fine. I'll puzzle it out at a later time. Now I don't have to boot into windows to print  \\:D/

---

### Post by az on 2005-08-13
Would someone with one of these printers *please* ask on the developmental list for these drivers to be packaged for Ubuntu?

Answer back here, if or when you have already done so.....

Thanks!

(Yes, I mean YOU!)

---

### Post by Spudgun on 2005-08-13
Will do, but could you provide a link to where I ask?

---

### Post by derrick1985 on 2005-08-13
Both howto's didn't work for me.

The Z600 one tries to print, the paper comes through a little bit, then stalls.

Too bad, I really need to get this printer working!

---

### Post by az on 2005-08-13
[QUOTE=Spudgun]Will do, but could you provide a link to where I ask?[/QUOTE]

[http://ubuntuforums.org/forumdisplay.php?f=29](http://ubuntuforums.org/forumdisplay.php?f=29)


If you cannot start a new thread there, you will need to sign up and do it by emal here:

[http://lists.ubuntulinux.org/mailman/listinfo/ubuntu-devel](http://lists.ubuntulinux.org/mailman/listinfo/ubuntu-devel)


Thanks!

---

### Post by az on 2005-08-13
Spudgun, I added some detail to your post on the devel mailing list, since there are already some Lexmark printers that work out-of-the-box, I clarified your question.

Please keep an eye on that thread so that you can give pertinent information about getting the thing to work in Ubuntu, if asked.

Thanks!

---

### Post by freelsjd on 2005-08-13
I cannot say this in a nice way. I bought a Lexmark printer (z23) because it was listed as linux compatible from the old elinux web site. Worst mistake I ever made. This printer and Chyrsler motor vehicles go hand-in-hand as poor excuses for what they are supposed to be: printers and cars respectively. I am now the proud owner of n HP-6210 all-in-1 and GM vehicles and all working great with Linux.

Forget Lexmark until they either really do support Linux or open source their drivers.

---

### Post by derrick1985 on 2005-08-16
THANK YOU!


I did the same steps as in post 1, except using the z35 driver (I have a z25 printer) and it works great now!

I also had to use the command sudo /etc/init.d/cupsys restart to get it to show up in the printing manager.

Thanks again!

---

### Post by transactionlogfiller on 2005-08-20
Thanks for this howto! It's one of the smoothest I've used from this site.

My comments below seem a bit pedantic but I just thought, keeping it simple enough for everyone, in-keeping with the style of this site, maybe add some points to the howto?

I had to sudo apt-get install alien first.

When I run alien I get a warning about ownership of files, because you didn't tell me to run it as root, so I went back and did "sudo alien"

That said, it's probably still the howto where the output I got differed least from what I was expecting, if you see what I mean. Which might be partly because I'm using breezy.

---

### Post by Spudgun on 2005-08-20
Excellent, it works :D
My is Lexmark X1180 is working great now, although it is printing a little on the slow side. Anyone know how to speed things up?

---

### Post by ben72 on 2005-08-29
[QUOTE=michellembrodeur]I found this for the z35 somewhere else on these forums.

it work no problem for a Z35

OK, this will take some skill on your part, but it can be done.

First, log in as root and download the drivers from

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242)

Make a directory and put the Lexmark driver in it... Let's assume we named it LEX, and that folder is sitting in /root OK? (in all of the commands, you do not type the # key, this is just to signify the prompt)

OK, so we have moved the driver into the folder now, and we will go into the folder by opening a command prompt and typing:

# cd /root/LEX

We will now extract the archive by typing the following command:

# tar -xzvf CJLZ35LE-CUPS-2.0-1.TAR.GZ

This now leaves us with a shell script rpm installer called lexmarkz35-CUPS-2.0-1.gz.sh... not very useful to a Debian distribution like Xandros, so now comes the fun part...We will make another directory now, and extract the files into it...

# mkdir lextemp

# tail -n +143 lexmarkz35-CUPS-2.0-1.gz.sh | gzip -cd | tar xvf - -C lextemp

Now we will enter the lextemp directory and convert the rpm files, since Xandros should not use rpms unless absolutely necessary.

# cd lextemp

# alien -t *.rpm


Next, we will use the tar command to extract the files to their proper place.

# tar -zxf lexmarkz35-CUPS-2.0.tgz -C /

# tar -zxf z35llpddk-2.0.tgz -C /

Now for some editing... type the following commands in the order shown below..

# cd /usr/local/z35llpddk/utility

# ln -s auckUS.lut bnsi1.lut

# cd /usr/lib

# ln -s liblexz35core.so.0.0.0 liblexz35core.so.0

# ln -s liblexz35printer.so.0.0.0 liblexz35printer.so.0

# ln -s liblexz35printjob.so.0.0.0 liblexz35printjob.so.0

Now to test and see if the driver is working...

# /usr/lib/cups/backend/z35

Output should not error out, and give an output similar to this...

direct z35:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer"

OK, if all is well, we allign the print heads by typing;

# /usr/lib/cups/backend/z35 utilities

Now that the heads are aligned, we can select the printer in the control center by following Launch > Control Center. Once in there in the Periphrial devices section there chould be a setting called printers... highlight printers and then go to add >local printer > Lexmark inkjet color printer and now under the model number one should see an entry for Z35 v 2.0-1... Select that, and then do your test page... Congrats, You're finished!

Hopefully Xandros will eventually make a Debian installer for this driver, but until then this works pretty well... Best of Luck, and hope this helps..

the howto worked really find under hoary.
only problem i have is that i am able to print the testpages with the utility software, but when i add the printer via cups to use it with other applications nothing will happen.

perhaps someone can help me
---------------------------------------

Do not thank me. someone else came up with it.

Something to remember, you need both b&W and colour catridages. I have only colour and it will not print black. But windows can use the colour to make black, but not linux. someday hope that willb e fixed.[/QUOTE]
 I have a Lexmark Z33 so I tried the Z35 driver and everything worked fine until the last instruction:

$ /usr/lib/cups/backend/z35
direct z35:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer"

$ /usr/lib/cups/backend/z35 utilities
ERROR: Unable to open printer port "/usr/lib/cups/backend/z35": Text file busy

How can I fix that? Any suggestions?

---

### Post by ben72 on 2005-08-29
I have a Lexmark Z33 so I tried the Z35 driver and everything worked fine until the last instruction:

$ /usr/lib/cups/backend/z35
direct z35:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer"

$ /usr/lib/cups/backend/z35 utilities
ERROR: Unable to open printer port "/usr/lib/cups/backend/z35": Text file busy

How can I fix that? Any suggestions?

---

### Post by thebilko on 2005-08-31
I have the x1185 and when I get to the first command that begins with sudo i get an error that says that it cannot find argument --C or somthing like that please help feel free to email me or im me at s2k Bilko

---

### Post by Pablo El Vagabundo on 2005-09-03
This is a great howto..Everything goes great for me until I get to the Add Printer part.

I cannot find the newly installed driver, I have restarted cups a few times and gnome, if i user the have driver button i get told it is already installed. 

Is it under the manufactor lexmark?? what is it called in the list. I have checked them all and none are z600 or anything like that..

any hints??

Pablo

---

### Post by roger6106 on 2005-09-03
[QUOTE=black hole sun]The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```[/QUOTE]

I had to do that with sudo for it to work.

---

### Post by Pablo El Vagabundo on 2005-09-04
I gave it a reboot and i could now see the driver..

I setup the printer.

Now when i try and print a test page it sucks in the the paper and then the second light is on and it moves the heads, its like it is in slow motion. but nothing really happens.

these printers are crap methinks.
Pablo

---

### Post by Pablo El Vagabundo on 2005-09-04
okay after my previous ranting I decided to try again.

Yeeeeeaaaaaaa!!

I tried the instructions above and can verify that it works like a charm for the Z25 if you use the z35 driver and z35 cups 1.01 driver, here are the links:

[http://www.downloaddelivery.com/srfilecache/CJLZ35LE-1.0-1.tar.gz](http://www.downloaddelivery.com/srfilecache/CJLZ35LE-1.0-1.tar.gz)

[http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-1.0-1.TAR.gz)

One other hint, as mentioned two post above, when restarting cups uses sudo, otherwise nothing happens:):)..

Thanks!!

Pablo

---

### Post by eveisdawning on 2005-09-17
It worked great for a Lexmark z515. Thanks!

Someone should put this in the wiki...

---

### Post by LGP on 2005-09-17
[QUOTE=black hole sun]Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

With that said, let's get to it! :D

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```[/QUOTE]



I have a Lexmark Z715 and when i try doing this get error messages when i put in the commands.  I downloaded the file with the drivers and saved them to a folder named Lexmark on my desktop.  

```
:~ $ mkdir lexmark
mkdir: cannot create directory `lexmark': File exists
:~ $ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory
``` 

If you could help me i would greatly appreciate it.

---

### Post by fortytwo on 2005-09-18
I've got a Z55 and unfortunately had no luck.  The instructions all went fine and the output looked right, and I can select the z600 driver from the KDE printer selection menu, but when I try to print, the job comes up in the manager and then goes away a little later...all the while my printer has done absolutely nothing.  Any ideas?

EDIT: Just noticed my printer isn't even on the supported list.  damn :/
DOUBLE EDIT:  Well, I guess my original question *does* stand, as a z55 is in fact on the list.

So..anyone had any luck?

---

### Post by mjpieters on 2005-09-25
There are a few possible simplifications to the HOWTO. First of all, the unpacking can be a little less elaborate. The following commands install the packages just fine; ignore the various errors

 ```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$  # Run the script and *keep* the installer dir (ingnore the errors):
$ sh z600cups-1.0-1.gz.sh -keep
$ cd installer/
$ # Install using alien
$ sudo alien -i z600cups-1.0-1.i386.rpm
$ sudo alien -i z600llpddk-2.0-1.i386.rpm

```

After these steps you can use the driver to install the printer in CUPS as described in the HOWTO. No need to lddconfig, no need to unzip the ppd (CUPS can read the PPD zipped).

Unfortunately for me, I still cannot print as it appears the driver cannot deal with the raster format generated by newer gs-esp versions (gs-esp is the CUPS-specific gs). See [http://www.cups.org/espgs/str.php?L691+P0+S0+C0+I30+E1+Q]("http://www.cups.org/espgs/str.php?L691+P0+S0+C0+I30+E1+Q"). The driver dates from Aug. 2003 and the CUPS version I use (Debian Unstable gs-esp 8+8.15rc4.dfsg.1-2) is far newer. The error message from rastertoz600 is 'Cannot Process Raster'.

---

### Post by mjpieters on 2005-09-25
I solved the problem. If you get a **'Cannot Process Raster**' errors, the Z600 raster filter cannot read the required datafiles. When converting the RPMs and installing the resulting tarball or deb package, certain directories end up being readable only to root.
 
To check if this is the problem, try and look at the /usr/local/z600llpddk/utility/ directory (with ls or with your favourite file manager). If you get a permission denied error, chances are the conversion filter cannot read it either.
 
The following two commands will fix this for you. Run these as root (sudo or log in as root) to fix this, and another directory likely to have the wrong permissions:
 
  ```
chmod -R +rX /usr/local/z600llpddk/
chmod -R +rX /usr/include/lexmark/
```
 These changes made the printer work for me.

---

### Post by yesidh on 2005-09-30
Hello, thanks a lot fot the HOWTO, I got a problem, I do everything you say and It worked, but then when I try to open de Printing systems in Gnome I give a error that say: The CUPS server cannot be connected. I'll apreciete it if you can help me,

---

### Post by StianH on 2005-10-02
I can confirm that the printer works for my Lexmark Z708 as well! Should be added to the list so if poeple search for the specific model on google, they can find it (as I did) :)

---

### Post by magomago on 2005-10-02
does anyone know if it works for the lexmark Z11 printer?  Its an older printer (which hopefully means support) with paralell port plug, but I'm not in a current position to test it out.  Thanks!

---

### Post by phlawed on 2005-10-08
Worked like a charm on my new lexmark z515 series. I just got it at wal-mart for $25 if anyone wants 4800dpi printer for linux cheap. Thank you agian.

---

### Post by yesidh on 2005-10-14
I want to report a Lexmark X1155 printer working out of the box, I would like to know how can I get the scanner working, any ideas?

Thanks a lot.

---

### Post by Sale on 2005-10-15
I've had lexmark z605 printer installed on ubuntu 5.04, according to the how-to at the beginning of this thread. I can't install the same printer on Ubuntu 5.10. When i come to the "alien -t....@ line of the how to, the bash reports that there is no such command.

Is there a solution to this?

TIA

Sale

---

### Post by uselessinfo on 2005-10-18
[QUOTE=LGP]I have a Lexmark Z715 and when i try doing this get error messages when i put in the commands.  I downloaded the file with the drivers and saved them to a folder named Lexmark on my desktop.  

```
:~ $ mkdir lexmark
mkdir: cannot create directory `lexmark': File exists
:~ $ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory
``` 

If you could help me i would greatly appreciate it.[/QUOTE]

I've got a Lexmark Z515, and I'm having the same problem. I would also appreciate any help.

---

### Post by Rouge8 on 2005-10-22
[quote=uselessinfo]I've got a Lexmark Z515, and I'm having the same problem. I would also appreciate any help.[/quote] 
You can skip that step, as all that does is move the files into the folder called lexmark (well, it also creates that folder.).

I have a Lexmark Z715, and after falling these instructions and the ones in [this](http://ubuntuforums.org/showthread.php?t=62353&highlight=z715) thread.

---

### Post by strawman on 2005-10-24
printing an Ubuntu test page on my Lexmark z515 as i type this.  Excellent howto!
thanks you. :)

---

### Post by arunsub on 2005-10-25
I'm using Breezy now. I bought a Dell All-in-one 962 photo printer 2 weeks back. I found out by googling that Dell 962 is Lexmark X7170.
I got the driver for Lexmark X7170 from this link.
[http://www.lexmark.com/US/products/i...7170_rev2.html](http://www.lexmark.com/US/products/i...7170_rev2.html)

I ran alien filename as normal user (not as root). I then got the deb file. I then issued
$sudo dpkg -i x7170llpddk_2.0-5_i386.deb
(Reading database ... 95758 files and directories currently installed.)
Preparing to replace x7170llpddk 2.0-5 (using x7170llpddk_2.0-5_i386.deb) ...
Unpacking replacement x7170llpddk ...
Setting up x7170llpddk (2.0-5) ...
$

I then rebooted the system. When I went to add printer, I didn't see the driver under either Dell or Lexmark. I would appreciate if someone can help me.

---

### Post by h3avyarms on 2005-10-26
I tried this methog and it did not work for me. I have a x1150 That I have never been able to get to work in linux. Here is what happens...

h3avyarms@ubuntu:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Everything works fine untill that step. I'm trying this on a fresh install of Ubuntu 5.10 and the printer works fine under windows. If I ignore this and continue with the instructions it will say it is printing the test page but nothing happens, I really need some help here. TIA

---

### Post by h3avyarms on 2005-10-26
Nevermind, If you change the margins it will work. Still no test page though.

---

### Post by yaaarrrgg on 2005-10-30
[QUOTE=h3avyarms]I tried this methog and it did not work for me. I have a x1150 That I have never been able to get to work in linux. Here is what happens...

h3avyarms@ubuntu:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Everything works fine untill that step. I'm trying this on a fresh install of Ubuntu 5.10 and the printer works fine under windows. If I ignore this and continue with the instructions it will say it is printing the test page but nothing happens, I really need some help here. TIA[/QUOTE]

yeah...i got that too with breazy.  you can go to

 System ->Administration -> Synaptic Package  Manager

search for libstdc, and install version 5.

---

### Post by thestarslookdown on 2005-11-01
This works fine on my z700, but 1) It won't print with a one inch margin on the left side even if (as in OO.o) there is one; and 2) printing something from gvim is somewhat fine, but a bit of text is moved forward or backward (and it suffers from #1 too).

EDIT: Using OO.o 2.0 now prints out the left and right margins but the top margin now isn't there.

---

### Post by SunshineSmile on 2005-11-01
[QUOTE=black hole sun]
```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```
[/QUOTE]

HELP!!! I have Lexmark Z601, but can't get your procedure right!! 

I figured I had to install alien, and I figured out how to move to the lexmark folder with the cd command.

but then, in the next step, sudo tar xv..etc.. following happens:

eine@eine:~/Desktop/Lexmark$ sudo tar xvzf  z600llpddk-2.0.tgz -C
tar: option requires an argument -- C
Try `tar --help' or `tar --usage' for more information.
eine@eine:~/Desktop/Lexmark$

What??

I type c (not capital):
eine@eine:~/Desktop/Lexmark$ sudo tar xvzf  z600llpddk-2.0.tgz -c
tar: Du kan ikke angi mer enn ett av «-Acdtrux»-flaggene #(you can't specify more than one of the Acdtrux flags- translated from norwegian.)
Try `tar --help' or `tar --usage' for more information.
eine@eine:~/Desktop/Lexmark$

Could you help me through the basic steps?

---

### Post by Rouge8 on 2005-11-01
[quote=SunshineSmile]HELP!!! I have Lexmark Z601, but can't get your procedure right!! 

I figured I had to install alien, and I figured out how to move to the lexmark folder with the cd command.

but then, in the next step, sudo tar xv..etc.. following happens:

eine@eine:~/Desktop/Lexmark$ sudo tar xvzf  z600llpddk-2.0.tgz -C
tar: option requires an argument -- C
Try `tar --help' or `tar --usage' for more information.
eine@eine:~/Desktop/Lexmark$

What??

I type c (not capital):
eine@eine:~/Desktop/Lexmark$ sudo tar xvzf  z600llpddk-2.0.tgz -c
tar: Du kan ikke angi mer enn ett av «-Acdtrux»-flaggene #(you can't specify more than one of the Acdtrux flags- translated from norwegian.)
Try `tar --help' or `tar --usage' for more information.
eine@eine:~/Desktop/Lexmark$

Could you help me through the basic steps?[/quote]

sudo tar xvzf  z600llpddk-2.0.tgz -C /

The trailing slash there is important, as -C refers to the corresponding directories.

---

### Post by SunshineSmile on 2005-11-02
eine@eine:~/Desktop/Lexmark$ cd /usr/share/cups/model
eine@eine:/usr/share/cups/model$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
eine@eine:/usr/share/cups/model$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
gunzip: Lexmark-Z600-lxz600cj-cups.ppd.gz: No such file or directory
eine@eine:/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart
 * Restarting Common Unix Printing System: cupsd start-stop-daemon: **Unable to open pidfile `/var/run/cups/cupsd.pid' for writing: Permission denied **(Permission denied)
                                                                         [ ok ]
eine@eine:/usr/share/cups/model$

I made the bold typing. Next step?

If somebody has time enough to explain the next few steps with backports and stuff, so I can get my z601 up and running, I would be delighted. Was a bit more difficult than just cut and paste. Understanding where to be, where to put in the commands, where the stuff is installed, etc. is a bit more than I have been doing with my windows... :D

---

### Post by Nubuntuzr on 2005-11-02
Finally!!
Thanks so much...Not sure if I was doing something wrong with other ways I was trying that I found via Google.....but kept getting one error or another until I tried these instructions and Bingo....my z515 prints.
Thanks again.

---

### Post by SunshineSmile on 2005-11-03
I reinstalled ubuntu to remove my windows partition and wanted to see if I could get this lexmark installing thingy working when starting with clean sheets..

What do you make of this? So close but so far.....

eine(username)@chello212186066182(my hostname):/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart
 * Restarting Common Unix Printing System: cupsd start-stop-daemon: Unable to open pidfile `/var/run/cups/cupsd.pid' for writing: Permission denied (Permission denied)
                                                                         [ ok ]
eine@chello212186066182:/usr/share/cups/model$ cd /usr/lib/cups/backend
eine@chello212186066182:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
eine@chello212186066182:/usr/lib/cups/backend$

---

### Post by vinil on 2005-11-04
thank man¡¡¡ it has very useful for me.... i have a dell a920 , and it works great..:D

---

### Post by arunsub on 2005-11-08
Does anyone have any solution to my Lexmar X7170 problem? I would appreciate if someone can help me install the driver.

---

### Post by dinap1 on 2005-11-10
What about the scanner feature of Lexmark X1180 ?

Has anyone managed to solve this problem?

---

### Post by manicka on 2005-11-10
[QUOTE=dinap1]What about the scanner feature of Lexmark X1180 ?

Has anyone managed to solve this problem?[/QUOTE]

Lexmark support is poor in Linux. This problem hasn't been solved because Lexmark won't help out with the drivers.

It drives me batty. I'm not sure we'll ever see a satisfactory outcome with Lexmark

---

### Post by SunshineSmile on 2005-11-11
I can't tell you how much I have been trying to get my z601 work. I can get all the way to *the very last step*, but I get no output. Oh, I had to type sudo before the alien command. Without superuser do, it says something about not running from root and how the files may be focked. :

K, have a look at my commands, and tell me what you think could be the reason why my z 601 wont print. 

Even without the last step displaying the wanted output, the printer setup under "system" recognised the driver and printer. It just wont print. Bummer. :(  And I need to use it now..
 

**myname@hostname:~/Desktop/lexmark$ cd ..**
**myname@hostname:~/Desktop$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz **lexmark
[B]myname@hostname:~/Desktop$ cd lexmark
myname@hostname:~/Desktop/lexmark$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz[/B]
[SIZE="1"]COPYING
README
z600cups-1.0-1.gz.sh[/SIZE]
[B]myname@hostname:~/Desktop/lexmark$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
myname@hostname:~/Desktop/lexmark$ tar -xvzf install.tar.gz[/B]
[SIZE="1"]globals.tcl
install
lexinstall
lexinstall.tcl
license
setup.tcl
testpage
usb.tcl
xlexinstall
xlexinstall.tcl
z600cups-1.0-1.i386.rpm
z600llpddk-2.0-1.i386.rpm[/SIZE]
**myname@hostname:~/Desktop/lexmark$ sudo alien -t z600cups-1.0-1.i386.rpm**
Password:
z600cups-1.0.tgz generated
**myname@hostname:~/Desktop/lexmark$ sudo alien -t z600llpddk-2.0-1.i386.rpm**
z600llpddk-2.0.tgz generated
**myname@hostname:~/Desktop/lexmark$ sudo tar xvzf  z600llpddk-2.0.tgz -C /**
[SIZE="1"]./
./usr/
./usr/include/
./usr/include/lexmark/
./usr/include/lexmark/alignmentdata.h
./usr/include/lexmark/cartridgemanager.h
./usr/include/lexmark/cartridgeuserinterface.h
./usr/include/lexmark/cleaningdata.h
./usr/include/lexmark/clock.h
./usr/include/lexmark/errorcommunicator.h
./usr/include/lexmark/linuxinkjetprinter.h
./usr/include/lexmark/mediamanager.h
./usr/include/lexmark/portmonitor.h
./usr/include/lexmark/printerdevice.h
./usr/include/lexmark/printjobmanager.h
./usr/lib/
./usr/lib/liblexprinter.a
./usr/lib/liblexprinter.la
./usr/lib/liblexprinter.so.0.0.0
./usr/lib/liblexprintjob.a
./usr/lib/liblexprintjob.la
./usr/lib/liblexprintjob.so.0.0.0
./usr/lib/liblexz600core.a
./usr/lib/liblexz600core.la
./usr/lib/liblexz600core.so.0.0.0
./usr/local/
./usr/local/z600llpddk/
./usr/local/z600llpddk/utility/
./usr/local/z600llpddk/utility/bnsi1.lut
./usr/local/z600llpddk/utility/bnsi2.lut
./usr/local/z600llpddk/utility/bnsi3.lut
./usr/local/z600llpddk/utility/lxbcalgn.out
./usr/local/z600llpddk/utility/lxbccln.out[/SIZE]
**myname@hostname:~/Desktop/lexmark$ sudo tar xvzf z600cups-1.0.tgz -C /**
[SIZE="1"]./
./usr/
./usr/lib/
./usr/lib/cups/
./usr/lib/cups/backend/
./usr/lib/cups/backend/z600
./usr/lib/cups/filter/
./usr/lib/cups/filter/rastertoz600
./usr/share/
./usr/share/cups/
./usr/share/cups/model/
./usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz[/SIZE]
[B]myname@hostname:~/Desktop/lexmark$ sudo ldconfig
myname@hostname:~/Desktop/lexmark$ cd /usr/share/cups/model
myname@hostname:/usr/share/cups/model$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz[/B]
gunzip: Lexmark-Z600-lxz600cj-cups.ppd already exists; do you wish to overwrite (y or n)? y
**myname@hostname:/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart**
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: Unable to open pidfile `/var/run/cups/cupsd.pid' for writing: Permission denied (Permission denied)
                                                                         [ ok ]
**myname@hostname:/usr/share/cups/model$ sudo /etc/rc2.d/S19cupsys restart**
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
[B]myname@hostname:/usr/share/cups/model$ cd /usr/lib/cups/backend
myname@hostname:/usr/lib/cups/backend$ ./z600[/B]
[SIZE="4"]./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/SIZE]
 
What THE HELL does that mean????? HELP, please...:(

---

### Post by manicka on 2005-11-11
You need to install libstdc++5

---

### Post by franohern on 2005-11-15
> If you get no output at all, you have problems.

What knid of problems? Did I do something wrong? Is there anything I can do?

I have a dell a940 that I tried this on. I was able to get through everything in your how-to, but got no response on the last step. I was able to set up a new printer with that driver, the system sees my a940, but nothing happens when I try to print a test page. 

Now, it may be that it won't work with an a940, but if I got no output from that last step, then I can't be sure whether I've done everything right and whether this is a no go for my printer.

I would appreciate any help or suggestions you can give me.

Thanks,
Fran

---

### Post by jimmyj on 2005-11-15
I followed the directions, but when I try to run ./z600 nothing happens. Where should I start looking for problems?

---

### Post by TmP on 2005-11-16
Hi!
Everything works fine untill i try to run the administration > printing

I receive a prompt saying that i cant connect to cups,
Or when I'm on the internet, it simply doesn't run...

Another person had this problem.
I'm using Breezy and my printer is z515

Help!

---

### Post by Ubuntist on 2005-11-17
I'm trying to install a Z55 under Breezy.  Following the instructions worked fine until I got to testing the backend by executing ./z600.  First, I got the error message
[INDENT]
./z600: error while loading shared libraries: libstdc++.so.5: cannot op en shared object file: No such file or directory
[/INDENT]
Following a suggestion from matthewv, I used Synaptic to load libstdc++5, and that solved the problem.  Now, however, executing the backend produces no output at all.  Any hints on where to go from here?

---

### Post by Ubuntist on 2005-11-17
OOPS!!!  I now see that this thread applies to Hoary (5.04) and there is an updated version for BREEZY (5.10): [http://www.ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+printer](http://www.ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+printer)

---

### Post by jockjunior on 2005-12-03
Hi,
  tried this got as far as the ALIEN command but get error 

Bash shell  no alien command or something like that

what went wrong. ?

thanks

Jock:confused:

Please ignore  I was following the wrong set of instructions (5.10 needed) and didnt see the link to the relevant alterations .

thanks

Jock

---

### Post by Rouge8 on 2005-12-03
Try:
> sudo apt-get install alien

---

### Post by jockjunior on 2005-12-03
Yes thanks that did it.

duh.........


jock

---

### Post by plug on 2005-12-10
hi every one i am new to linux.

could anyone please help i have no printer it show it in the printer set up thing see told you i was new lol.
and i have set it for usb lexmark z517 it gives me sugested driver,but not a thing happends when i do a test page.
if anyone could help me with this it would be great.
please dont forget i am a noob at linux ubuntu so please make it in easy turms for me to understand.

---

### Post by Ub(untu)erNewb on 2005-12-14
[QUOTE=michellembrodeur]I found this for the z35 somewhere else on these forums.

it work no problem for a Z35

OK, this will take some skill on your part, but it can be done.

First, log in as root and download the drivers from

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242)

Make a directory and put the Lexmark driver in it... Let's assume we named it LEX, and that folder is sitting in /root OK? (in all of the commands, you do not type the # key, this is just to signify the prompt)

OK, so we have moved the driver into the folder now, and we will go into the folder by opening a command prompt and typing:

# cd /root/LEX

We will now extract the archive by typing the following command:

# tar -xzvf CJLZ35LE-CUPS-2.0-1.TAR.GZ

This now leaves us with a shell script rpm installer called lexmarkz35-CUPS-2.0-1.gz.sh... not very useful to a Debian distribution like Xandros, so now comes the fun part...We will make another directory now, and extract the files into it...

# mkdir lextemp

# tail -n +143 lexmarkz35-CUPS-2.0-1.gz.sh | gzip -cd | tar xvf - -C lextemp

Now we will enter the lextemp directory and convert the rpm files, since Xandros should not use rpms unless absolutely necessary.

# cd lextemp

# alien -t *.rpm


Next, we will use the tar command to extract the files to their proper place.

# tar -zxf lexmarkz35-CUPS-2.0.tgz -C /

# tar -zxf z35llpddk-2.0.tgz -C /

Now for some editing... type the following commands in the order shown below..

# cd /usr/local/z35llpddk/utility

# ln -s auckUS.lut bnsi1.lut

# cd /usr/lib

# ln -s liblexz35core.so.0.0.0 liblexz35core.so.0

# ln -s liblexz35printer.so.0.0.0 liblexz35printer.so.0

# ln -s liblexz35printjob.so.0.0.0 liblexz35printjob.so.0

Now to test and see if the driver is working...

# /usr/lib/cups/backend/z35

Output should not error out, and give an output similar to this...

direct z35:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer"

OK, if all is well, we allign the print heads by typing;

# /usr/lib/cups/backend/z35 utilities

Now that the heads are aligned, we can select the printer in the control center by following Launch > Control Center. Once in there in the Periphrial devices section there chould be a setting called printers... highlight printers and then go to add >local printer > Lexmark inkjet color printer and now under the model number one should see an entry for Z35 v 2.0-1... Select that, and then do your test page... Congrats, You're finished!

Hopefully Xandros will eventually make a Debian installer for this driver, but until then this works pretty well... Best of Luck, and hope this helps..

the howto worked really find under hoary.
only problem i have is that i am able to print the testpages with the utility software, but when i add the printer via cups to use it with other applications nothing will happen.

perhaps someone can help me
---------------------------------------

Do not thank me. someone else came up with it.

Something to remember, you need both b&W and colour catridages. I have only colour and it will not print black. But windows can use the colour to make black, but not linux. someday hope that willb e fixed.[/QUOTE]


Hi guys, thanks for your work so far, but i still got a problem: 

I got a Z35 and i tried everything i quoted so far but every time i want to test  it i get this answer:
/usr/lib/cups/backend/z35: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

My printer gets the order to print but it simply refuses to work. I do not know why but i help that there is help anywhere out there.

---

### Post by Ub(untu)erNewb on 2005-12-14
Sorry, i just installed libstcd++5 and now everything just works perfectly. 

\\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by Ub(untu)erNewb on 2005-12-19
Hi, sorry to disturb again, but now, after a few days i tried to print a very important paper but the printer simply refused to work. He gets the job to print but he simply spits out the sheet. 

I tried:  /usr/lib/cups/backend/z35 utilities
and i got this as an answer: ERROR: Unable to open printer port "/usr/lib/cups/backend/z35": Text file busy


Please help me.....i´m simply:confused:

---

### Post by sas171 on 2005-12-21
I had to use another USB port to get my z515 work but its awesome.

Is there some app to see how many tint I have and so on?

---

### Post by M4VE on 2005-12-25
Dude!  I just got my X1185 working in about 5 minutes using your HOWTO!  Much thanks, you ROCK!!!

---

### Post by ivuntu on 2006-01-30
\\:D/ This is probably an old post, but thanks a lot from an ubuntu newbie for the detailed recipe, it worked on my Lexmark p707, where a lot of other drivers and stuff had failed! I might have missed a step or two in other How to's. 
Ivuntu

---

### Post by dcriswell on 2006-01-31
Thanks for the great HOWTO! 
Just FYI, the new sane-backend (1.0.17 I think) has support for lexmark x1100 series scanners. I just tested it, using the CVS version, with my x1150 and it works like a charm.

---

### Post by manicka on 2006-02-01
[QUOTE=dcriswell]Thanks for the great HOWTO! 
Just FYI, the new sane-backend (1.0.17 I think) has support for lexmark x1100 series scanners. I just tested it, using the CVS version, with my x1150 and it works like a charm.[/QUOTE]

That is good news, where would i find it?

---

### Post by mips on 2006-02-01
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

---

### Post by dcriswell on 2006-02-01
I'm actually using the lexmark backend. It is supposed to be in the 1.0.17 release from [Sane]("http://www.sane-project.org/"). They have debian packages available from their download page although I haven't tried them. Instructions on how to get the CVS version is there as well. I had to upgrade [xsane]("http://www.xsane.org") to 0.99.1 in order to scan in gimp. Scanimage worked with just the backend installed.

---

### Post by manicka on 2006-02-02
[QUOTE=dcriswell]I'm actually using the lexmark backend. [/QUOTE]

Where would I find the Lexmark backend?

---

### Post by arunsub on 2006-02-03
Did anyone find the driver for X7170 model?

---

### Post by johnmxl on 2006-02-17
I followed the HOWTO to the letter and sucessfully added the X1185 attached to one of the WinXP boxes on my home LAN as a network printer for my laptop running Breezy Badger (Ubuntu 5.10).  Including a detour to install alien it probably took 20 minutes start to finish.

I found  the HOWTO on google, searching on 'ubuntu X1185'.

Thanks, Black Hole Sun!

johnmxl

---

### Post by BrejoSacor on 2006-02-22
Great How-to, but maybe it should be mentioned to do this command first:
    sudo apt-get install alien

I realized this and found it in the middle of the post... Maybe add it to the first post, or stick it to the top of the forum...

Anyway, couldn't have done it with out ya, Thanks

---

### Post by funkjunkie on 2006-02-27
i just cant seem to get past this part:
 
sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place

i tried this too 
sudo tar xvzf  z600llpddk-2.0.tgz -C /usr/share/cups/model 
seemed to do the same.

it seems to go thru and say its extracting files to the proper places, but when i go to the next steps and look in that dir, the files just are not to be found.  

argh. @$!% dell printer.  my hp worked w/o a hitch.

---

### Post by mishranurag on 2006-03-11
Will this work in dapper?

---

### Post by ZephyrXero on 2006-03-13
Dapper user here, with a Lexmark X1185

I just followed the instructions in the first post and when I ran ./z600 it gave me an error saying it could not find stdlibc++5 or something, and then proceeded to make Gnome start acting weird and crash. After a reboot GDM won't even come up now...

Another weird thing is that I can't get sudo access anymore either....I don't know what the hell happened but it's bad (writing this from the recovery mode). I've even tried installing stdlibc+5 and that didn't fix it either.

---

### Post by bertpatt on 2006-03-13
This might be simple, but how do I copy or print the code that's been put in a scrolling box, why can't it be typed in so we can see it all?

---

### Post by emitter on 2006-03-14
Hi!

I've followed the instructions written in [Lexmark Z600 printers]("http://ubuntuforums.org/showthread.php?t=83456") #1, but when typing ./z600 nothing did appear... That's a problem, isn't it?:-k 

in System-admin-printers I see "CUPS printer (IPP)" - under Network printer since my Z602 is on a windoz-machine on the network. Should I choose this IPP, or the Windows SMB? Do you think will that work for me with this driver to print on network?

Thanks
emitter

---

### Post by tagra123 on 2006-03-15
I posted a how to  for the Z23:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z23](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z23)

tagra123  -- Tom G

---

### Post by emitter on 2006-03-15
#84:

This problem still prevails... If I connect the printer (usb) directly to the laptop, printing goes smoothly. But normally the laptop isn't near the printer, so I would like to use my wlan-network to print through the desktop-pc.
I just don't know what type of network-printer to choose: CUPS (ipp) or Windows SMB? And how should I fill the appropriate fields? (Server, printer, user, pwd)

---

### Post by timbl_ubuntu on 2006-03-21
I have the same problem as ZephyrXero

ubuntu dapper flight 5
lexmark x1130

I got the same error and now when I boot, the xserver craches
sudo doesn't work
(su does work, but then I get complaints about me giving the wrong password for root access...)

any solutions?

---

### Post by emitter on 2006-03-23
[QUOTE=timbl_ubuntu]I have the same problem as ZephyrXero

ubuntu dapper flight 5
lexmark x1130

I got the same error and now when I boot, the xserver craches
sudo doesn't work
(su does work, but then I get complaints about me giving the wrong password for root access...)

any solutions?[/QUOTE]


Unless I'm mistaken you have to enter your user-pw when sudo, or rather the root-pw in case of su

---

### Post by timbl_ubuntu on 2006-03-23
off course, tried them both, didn't fix it, recovery mode did work, tried to undo the attempt to install printer

couldn't get it fixed

---

### Post by ZephyrXero on 2006-03-23
[QUOTE=timbl_ubuntu]off course, tried them both, didn't fix it, recovery mode did work, tried to undo the attempt to install printer

couldn't get it fixed[/QUOTE]

Ditto. I just had to end up reinstalling :(

---

### Post by gymsmoke on 2006-03-23
Lexmark X6100 series just doesn't work.  The entire install went fine, and the test page is sent, but no soap... I also tried every swinging driver under Lexmark and got the same results... looks like i'll be in the market for a printer...

---

### Post by tico on 2006-03-24
It worked!! My Lexmark z515 it's alive and works!!!!!
Many thanks for your help!!!

---

### Post by Smakfull on 2006-03-25
[QUOTE=franohern]What knid of problems? Did I do something wrong? Is there anything I can do?

I have a dell a940 that I tried this on. I was able to get through everything in your how-to, but got no response on the last step. I was able to set up a new printer with that driver, the system sees my a940, but nothing happens when I try to print a test page. 

Now, it may be that it won't work with an a940, but if I got no output from that last step, then I can't be sure whether I've done everything right and whether this is a no go for my printer.

I would appreciate any help or suggestions you can give me.

Thanks,
Fran[/QUOTE]
Same here and it looks like we're not alone. I think I've read all the support sheats there is on the net. It seems so easy but I JUST can't get it to WORK! ](*,) 

The last I found was this: [http://www.staerk.de/thorsten/modules.php?name=News&file=article&sid=43](http://www.staerk.de/thorsten/modules.php?name=News&file=article&sid=43) but no luck there either *cry*

Any ideas?
I love you guys/gals for all your help. I've been stuck with this for two weeks now and it's beginning to get on my nerves :(

That is: no output for the last step. Everything SEEMS to be working, but when my job exits the printing queue, nothing prints.

---

### Post by Smakfull on 2006-04-02
[QUOTE=jerrybme]Well, it turned out to be a 64 bit library linkage problem. I created a 32 bit chroot and the printer driver works fine[/QUOTE]
Ehr. How? :confused:

edit:
eh nevermind, found [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by ultra.nj on 2006-04-03
[QUOTE=Smakfull]Same here and it looks like we're not alone. I think I've read all the support sheats there is on the net. It seems so easy but I JUST can't get it to WORK! ](*,) 

The last I found was this: [http://www.staerk.de/thorsten/modules.php?name=News&file=article&sid=43](http://www.staerk.de/thorsten/modules.php?name=News&file=article&sid=43) but no luck there either *cry*

Any ideas?
I love you guys/gals for all your help. I've been stuck with this for two weeks now and it's beginning to get on my nerves :(

That is: no output for the last step. Everything SEEMS to be working, but when my job exits the printing queue, nothing prints.[/QUOTE]

bump.

please help, i get this exact same problem.  i've read through all ten pages and found that many people have had this problem but no one has posted any way to fix it.  is there any way to fix it, or should we just give up?

but, the printer that i'm using is the dell j740, and i don't know if the z600 is the right printer or not, is there any other way to find out what what lexmark drivers i need to get to use for the dell J740?

---

### Post by Mookawaka on 2006-04-05
I am a newbie who is trying to get his shiny new Ubuntu operating system fully up and running and configured.
Unfortunately the only printer that I have available at this time is a LEXMARK 810.  From searching these forums I see that Lexmark does not like to play nice with open source.
I have tried this walkthrough for the z600 driver without any troubles, but when I try to print a page the process stops immediately with the STATUS:

Paused: Both cartridges are invalid. Please use appropriate cartridges.

Interestingly I got a similar warning in Windoze(TM) but pages would still print correctly.  I suspect that this has to do with being in East Berlin and the ink cartridges and Lexmark software somehow not matching up.

Is there any hope for getting around this problem?

---

### Post by black hole sun on 2006-04-05
Everyone -- I'm so sorry I haven't been here for a long time so I haven't been able to help you guys. :(

I figured out your problem -- you need to mount the usb filesystem. Add this line to /etc/fstab

usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 

Then type 

sudo mount usbfs

Try the backend again and it should work.

---

### Post by black hole sun on 2006-04-06
Okay, I just had to reinstall because of the lexmark driver :|

I have no idea why it is doing that... apparently it causes GDM to just _DIE_.

If anyone is running Dapper - DO NOT USE THIS DRIVER YET until I can figure this out.

---

### Post by ontos81 on 2006-04-10
Hello!
I am new in the forum, but I used ubuntu for a long time, since Hoary. The HowTo always worked so far. But I reinstalled Ubuntu, using dapper flight 6 because of improved wireless support for my notebook, and so I did take the same steps hoping my lexmark z513 printer work, as it did at previous trials. I did not folowed the thread up to the end, and did not see your advice. Now I am without GDM as the other people. In my case, using XFCE as my default wm, only typing "startx" resolves, but if you get a solution to the GDM problem please inform.

---

### Post by Smakfull on 2006-04-16
[QUOTE=black hole sun]I figured out your problem -- you need to mount the usb filesystem. Add this line to /etc/fstab

usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 

Then type 

sudo mount usbfs

Try the backend again and it should work.[/QUOTE]

Thanks... Didn't work though :( My system tells me my USB-port is already mounted on /proc/bus/usb. Still no output from backend!

Thank you for your time!

---

### Post by robogock on 2006-04-16
[QUOTE=Smakfull]
eh nevermind, found [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)[/QUOTE]

Okay, I was just handed a freebie Dell 720 printer, which is a repackaged Lexmark z615. I'm running 64-bit hoary, so, like others, the standard install instructions for the lexmark drivers didn't work. I followed the instructions to create a 32bit chroot enviornment, but now I'm stuck. What do I do now? Do I run cups as a 32bit app?

---

### Post by aegypius on 2006-04-17
Hello

Thank to you, now i can print in my Lexmark X1180. But how can i put my scaner work.

---

### Post by JetPack on 2006-04-24
Hi,

I'm a newbie (but slowly getting there...) and I've hit a problem with the Lexmark install.

First, I tried using a file lexmarkz55-2.0-1.gz.sh that I found on the net (as I have a Z55) and applied the extraction techniques to get the .rpm, etc. But then I got stuck. I have no idea what I've actually installed using dpgk (once I'd turned it into a .deb using alien).

So....

I went over the LZ600 procedure and ended up with the error message:-
```
martin@Majestic-L:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

And, of course, it no work....

I can see the LZ600 printer driver in the list when I use the Gnome print utility and it will even let me set up a printer but the "print test page" operation doesn't even make the printer twitch.

I am guessing that a lot of the editing done in the Z35 install (an earlier post) solves these object/library discrepancies but I don't know how to go about translating what was done there for the Z55 issue.

My system base config is attached and some help would be appreciated - thanks.

OK - just followed another branch and installed the libstd5. This took away the error mesage but didn't seem to achieve anything else. When I run z600 I get no output at all. Will try a re-boot...

Nope - and I tried the whole installation procedure again, and removed and recreated the printer in Gnome Printers. Not working.

The printer is on the parallel port and Ubuntu doesn't seem to be able to detect it - maybe this is the underlying casue.

Any ideas? (thanks)

---

### Post by VincenzoDiMassa on 2006-05-12
If your printer does not work you can try:

$ sudo chmod 755 /usr/local/z600llpddk
$ sudo chmod 755 /usr/local/z600llpddk/*

It worked for me.

Vincenzo

---

### Post by Smakfull on 2006-05-14
Got this from /var/log/cups/error_log (don't know how to set LogLevel to debug I'm afraid - *Yea I do, fixed it*). No output from backend. Are there any more logs I can provide to help? I can't understand this system, and am really close to go back to windows, almost solely due to this printer problem.

```
I [14/May/2006:18:38:45 +0200] Listening to 7f000001:631
D [14/May/2006:18:38:45 +0200] AddLocation: added location '/'
D [14/May/2006:18:38:45 +0200] DenyIP: / deny 00000000/00000000
D [14/May/2006:18:38:45 +0200] AllowIP: / allow 7f000001/ffffffff
D [14/May/2006:18:38:45 +0200] AddLocation: added location '/jobs'
D [14/May/2006:18:38:45 +0200] AddLocation: added location '/admin'
D [14/May/2006:18:38:45 +0200] DenyIP: /admin deny 00000000/00000000
D [14/May/2006:18:38:45 +0200] AllowIP: /admin allow 7f000001/ffffffff
I [14/May/2006:18:38:45 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [14/May/2006:18:38:45 +0200] Configured for up to 100 clients.
I [14/May/2006:18:38:45 +0200] Allowing up to 100 client connections per host.
I [14/May/2006:18:38:45 +0200] Full reload is required.
D [14/May/2006:18:38:45 +0200] LoadAllPrinters: Loading printer Z600-v1.0-1...
E [14/May/2006:18:38:45 +0200] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
D [14/May/2006:18:38:45 +0200] LoadDevices: Added device "ipp"...
D [14/May/2006:18:38:45 +0200] LoadDevices: Added device "http"...
D [14/May/2006:18:38:45 +0200] LoadDevices: Added device "bluetooth"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "epson:/dev/lp0"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "canon:/dev/lp0"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "smb"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "lpd"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "parallel:/dev/lp0"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "socket"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb://Dell/Photo%20AIO%20Printer%20924"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp1"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp2"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp3"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp4"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp5"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp6"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp7"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp8"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp9"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp10"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp11"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp12"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp13"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp14"...
D [14/May/2006:18:38:46 +0200] LoadDevices: Added device "usb:/dev/usb/lp15"...
I [14/May/2006:18:38:46 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 4107 PPDs...
I [14/May/2006:18:38:47 +0200] LoadPPDs: No new or changed PPDs...
D [14/May/2006:18:38:47 +0200] LoadAllJobs: Scanning /var/spool/cups...
D [14/May/2006:18:38:47 +0200] LoadAllJobs: Loading attributes for job 1...
D [14/May/2006:18:38:47 +0200] LoadAllJobs: Loading attributes for job 2...
D [14/May/2006:18:38:47 +0200] LoadAllJobs: Auto-typing document file d00002-001...
I [14/May/2006:18:38:47 +0200] Full reload complete.
D [14/May/2006:18:38:47 +0200] StartListening: NumListeners=1
D [14/May/2006:18:38:47 +0200] StartListening: address=7f000001 port=631
D [14/May/2006:18:38:47 +0200] ResumeListening: setting input bits...
D [14/May/2006:18:38:47 +0200] StartJob(2, 0x80961a0)
D [14/May/2006:18:38:47 +0200] StartJob() id = 2, file = 0/1
D [14/May/2006:18:38:47 +0200] job-sheets=none,none
D [14/May/2006:18:38:47 +0200] banner_page = 0
D [14/May/2006:18:38:47 +0200] StartJob: argv = "Z600-v1.0-1","2","smakfull","(stdin)","1","PreFilter=Level1","/var/spool/cups/d00002-001"
D [14/May/2006:18:38:47 +0200] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [14/May/2006:18:38:47 +0200] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [14/May/2006:18:38:47 +0200] StartJob: envp[2]="USER=root"
D [14/May/2006:18:38:47 +0200] StartJob: envp[3]="CHARSET=utf-8"
D [14/May/2006:18:38:47 +0200] StartJob: envp[4]="LANG=sv"
D [14/May/2006:18:38:47 +0200] StartJob: envp[5]="TZ=Europe/Stockholm"
D [14/May/2006:18:38:47 +0200] StartJob: envp[6]="PPD=/etc/cups/ppd/Z600-v1.0-1.ppd"
D [14/May/2006:18:38:47 +0200] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [14/May/2006:18:38:47 +0200] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [14/May/2006:18:38:47 +0200] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [14/May/2006:18:38:47 +0200] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [14/May/2006:18:38:47 +0200] StartJob: envp[11]="DEVICE_URI=usb://Dell/Photo%20AIO%20Printer%20924"
D [14/May/2006:18:38:47 +0200] StartJob: envp[12]="PRINTER=Z600-v1.0-1"
D [14/May/2006:18:38:47 +0200] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [14/May/2006:18:38:47 +0200] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/May/2006:18:38:47 +0200] StartJob: envp[15]="CUPS_SERVER=localhost"
D [14/May/2006:18:38:47 +0200] StartJob: envp[16]="IPP_PORT=631"
D [14/May/2006:18:38:47 +0200] StartJob: statusfds = [ 4 5 ]
D [14/May/2006:18:38:47 +0200] StartJob: filterfds[1] = [ 6 -1 ]
D [14/May/2006:18:38:47 +0200] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [14/May/2006:18:38:47 +0200] StartJob: filterfds[0] = [ 7 8 ]
D [14/May/2006:18:38:47 +0200] start_process("/usr/lib/cups/filter/pstops", 0xbfd154f0, 0xbfd14a68, 6, 8, 5)
I [14/May/2006:18:38:47 +0200] Started filter /usr/lib/cups/filter/pstops (PID 7476) for job 2.
D [14/May/2006:18:38:47 +0200] StartJob: filter = "/usr/lib/cups/filter/pstoraster"
D [14/May/2006:18:38:47 +0200] StartJob: filterfds[1] = [ 6 9 ]
D [14/May/2006:18:38:47 +0200] start_process("/usr/lib/cups/filter/pstoraster", 0xbfd154f0, 0xbfd14a68, 7, 9, 5)
I [14/May/2006:18:38:47 +0200] Started filter /usr/lib/cups/filter/pstoraster (PID 7477) for job 2.
D [14/May/2006:18:38:47 +0200] StartJob: filter = "/usr/lib/cups/filter/rastertoz600"
D [14/May/2006:18:38:47 +0200] StartJob: filterfds[0] = [ 7 8 ]
D [14/May/2006:18:38:47 +0200] start_process("/usr/lib/cups/filter/rastertoz600", 0xbfd154f0, 0xbfd14a68, 6, 8, 5)
I [14/May/2006:18:38:47 +0200] Started filter /usr/lib/cups/filter/rastertoz600 (PID 7478) for job 2.
D [14/May/2006:18:38:47 +0200] StartJob: backend = "/usr/lib/cups/backend/usb"
D [14/May/2006:18:38:47 +0200] StartJob: filterfds[1] = [ -1 6 ]
D [14/May/2006:18:38:47 +0200] start_process("/usr/lib/cups/backend/usb", 0xbfd154f0, 0xbfd14a68, 7, 6, 5)
I [14/May/2006:18:38:47 +0200] Started backend /usr/lib/cups/backend/usb (PID 7479) for job 2.
D [14/May/2006:18:38:47 +0200] [Job 2] Printer using device file "/dev/usb/lp0"...
D [14/May/2006:18:38:47 +0200] [Job 2] LPGETSTATUS returned a port status of 18...
D [14/May/2006:18:38:47 +0200] [Job 2] Running /usr/bin/gs-esp -dQUIET -dDEBUG -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOMEDIAATTRS -sDEVICE=cups -sstdout=%stderr -sOUTPUTFILE=%stdout -c -
D [14/May/2006:18:38:47 +0200] [Job 2] Page = 595x842; 18,36 to 585,837
D [14/May/2006:18:38:47 +0200] [Job 2] slowcollate=0, slowduplex=0, sloworder=0
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BoundingBox: 0 0 612 792
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Creator: Mozilla PostScript module (rv:1.7.13/2006041813)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentData: Clean8Bit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentPaperSizes: Letter
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Orientation: Portrait
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Pages: (atend)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%PageOrder: Ascend
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndComments
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginProlog
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndProlog
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%IncludeResource: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginResource: CMap Bitstream_Vera_Sans.Bold.0.0_cmap
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Title: (Bitstream_Vera_Sans.Bold.0.0_cmap mozilla_printout UBjaCT1xV6MA9PkdvDbZmDyoqeA= 0)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Version : 1
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndResource
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%IncludeResource: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginResource: CIDFont Bitstream_Vera_Sans.Bold.0.0
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Title: (Bitstream_Vera_Sans.Bold.0.0 mozilla_printout UBjaCT1xV6MA9PkdvDbZmDyoqeA= 0)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Version: 1
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginData: 11621 Binary Bytes
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndData
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndResource
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%IncludeResource: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginResource: CMap Bitstream_Vera_Sans_Mono.Roman.0.0_cmap
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Title: (Bitstream_Vera_Sans_Mono.Roman.0.0_cmap mozilla_printout f6U0d65zzBHouM157hSFOUVU6uE= 0)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Version : 1
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndResource
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%IncludeResource: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginResource: CIDFont Bitstream_Vera_Sans_Mono.Roman.0.0
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Title: (Bitstream_Vera_Sans_Mono.Roman.0.0 mozilla_printout f6U0d65zzBHouM157hSFOUVU6uE= 0)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Version: 1
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginData: 13191 Binary Bytes
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndData
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndResource
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%IncludeResource: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginResource: CMap Bitstream_Vera_Sans_Mono.Bold.0.0_cmap
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Title: (Bitstream_Vera_Sans_Mono.Bold.0.0_cmap mozilla_printout XCJqh1WCzx8tJgqb+JzS7kcENY0= 0)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Version : 1
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndResource
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%IncludeResource: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginResource: CIDFont Bitstream_Vera_Sans_Mono.Bold.0.0
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Title: (Bitstream_Vera_Sans_Mono.Bold.0.0 mozilla_printout XCJqh1WCzx8tJgqb+JzS7kcENY0= 0)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Version: 1
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginData: 1440 Binary Bytes
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndData
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndResource
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%IncludeResource: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginResource: CMap Bitstream_Vera_Sans.Oblique.0.0_cmap
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Title: (Bitstream_Vera_Sans.Oblique.0.0_cmap mozilla_printout 57c1KJ55Zs+fBvJlM0DyIl4FuQo= 0)
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Version : 1
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%EndResource
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%IncludeResource: procset CIDInit
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%BeginResource: CIDFont Bitstream_Vera_Sans.Oblique.0.0
D [14/May/2006:18:38:47 +0200] [Job 2] 0 %%Title: (Bitstream_Vera_Sans.Oblique.0.0 mozilla_printout 57c1KJ55Zs+fBvJlM0DyIl4FuQo= 0)
D [14/May/2006:18:38:47 +0200] [Job 2] START 0 1414672 116499 1421640 132248 true 474 3 <0>
D [14/May/2006:18:38:47 +0200] [Job 2] END PROCS 0 1414672 128676 1421640 133616 true 586 3 <0>
D [14/May/2006:18:38:47 +0200] [Job 2] gs_std_e.ps 0 1454864 142008 1421640 134992 true 594 3 <0>
D [14/May/2006:18:38:47 +0200] [Job 2] gs_il1_e.ps 0 1454864 144727 1421640 134992 true 595 3 <0>
D [14/May/2006:18:38:47 +0200] [Job 2] END FONTDIR/ENCS 0 1454864 144879 1421640 134992 true 597 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] END DEVS 0 1469480 175728 1421640 134992 true 601 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] END STATD 0 1489576 186125 1421640 136604 true 605 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] END GS_FONTS 0 1509672 207229 1421640 136604 true 648 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_type1.ps 0 1509672 210779 1421640 136604 true 664 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_dps1.ps 0 1509672 212626 1421640 136604 true 666 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_lev2.ps 10 1549864 234709 1517296 232656 true 673 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] BEGIN RESOURCES 10 1549864 236845 1517296 232656 true 673 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] END CATEGORY 10 1549864 238315 1517296 232812 true 674 5 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] END GENERIC 10 1549864 241513 1517296 232812 true 674 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] END FIXED 10 1549864 246844 1517296 232812 true 674 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] END MISC 10 1549864 251254 1517296 232812 true 674 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] END ENCODING 10 1569960 256434 1517296 232812 true 674 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_res.ps 10 1569960 256585 1517296 232812 true 678 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_typ42.ps 10 1569960 256899 1517296 232812 true 681 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] ./CIDFnmap 10 1569960 264791 1517296 232812 true 840 4 <3>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/cups/fonts/CIDFnmap 10 1569960 264830 1517296 232812 true 840 4 <3>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/gs-esp/7.07/lib/CIDFnmap 10 1569960 264874 1517296 232812 true 840 4 <3>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/gs-esp/fonts/CIDFnmap 10 1569960 264915 1517296 232812 true 840 4 <3>
D [14/May/2006:18:38:48 +0200] [Job 2] /var/lib/defoma/gs.d/dirs/fonts/CIDFnmap 10 1569960 264964 1517296 232812 true 840 4 <3>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/cups/fonts/CIDFnmap 10 1569960 265998 1517296 232812 true 840 4 <3>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/ghostscript/fonts/CIDFnmap 10 1569960 266044 1517296 232812 true 840 4 <3>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/local/lib/ghostscript/fonts/CIDFnmap 10 1569960 266094 1517296 232812 true 840 4 <3>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_cidfn.ps 10 1569960 266036 1517296 232812 true 706 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_cidcm.ps 10 1590056 278320 1517296 232812 true 706 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_cmap.ps 10 1590056 284386 1517296 232812 true 710 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_btokn.ps 10 1590056 287352 1517296 232812 true 711 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_dps2.ps 10 1590056 289790 1517296 232812 true 712 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_setpd.ps 10 1610152 300513 1517296 232812 true 712 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_typ32.ps 10 1610152 301585 1517296 232812 true 710 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_frsd.ps 10 1610152 302293 1517296 232812 true 710 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_ll3.ps 20 1610152 313681 1602852 319126 true 711 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_mex_e.ps 20 1610152 319032 1602852 319126 true 711 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_mro_e.ps 20 1630248 323016 1602852 319126 true 711 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_pdf_e.ps 20 1650344 327008 1602852 319126 true 711 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_wan_e.ps 20 1650344 327645 1602852 319126 true 711 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] pdf_ops.ps 30 1650344 338209 1602852 319126 true 711 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_l2img.ps 30 1650344 339937 1602852 319126 true 714 3 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] pdf_base.ps 30 1650344 347431 1602852 319126 true 913 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] pdf_draw.ps 30 1670440 370785 1602852 319126 true 913 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] pdf_font.ps 30 1690536 389002 1602852 319126 true 913 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] pdf_main.ps 30 1730728 415585 1602852 319126 true 915 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] pdf_sec.ps 30 1730728 418434 1602852 319126 true 915 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_css_e.ps 40 1730728 419302 1602852 319126 true 915 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_cff.ps 40 1750824 435785 1602852 319126 true 917 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_mgl_e.ps 40 1750824 439630 1602852 319126 true 917 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_agl.ps 40 1803968 486908 1602852 319126 true 918 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_ttf.ps 40 1860684 544455 1602852 319126 true 969 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_icc.ps 40 1860684 545332 1602852 320688 true 969 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_dps.ps 40 1880780 550053 1602852 320688 true 982 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_dpnxt.ps 40 1880780 550738 1602852 320688 true 998 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_epsf.ps 40 1880780 551227 1602852 320688 true 1000 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_pdfwr.ps 40 1907076 590878 1602852 320688 true 1024 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_lgo_e.ps 40 1907076 591605 1602852 320688 true 1024 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] gs_lgx_e.ps 40 1907076 591899 1602852 320688 true 1024 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] dmp_init.ps 40 1941668 622003 1622948 334454 true 1024 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] END INITFILES 50 1961764 628690 1622948 334454 true 1051 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] ./Fontmap 50 1961764 630197 1622948 335248 true 1052 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/cups/fonts/Fontmap 50 1961764 630234 1622948 335248 true 1052 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/gs-esp/7.07/lib/Fontmap 50 1961764 630276 1622948 335248 true 1052 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/gs-esp/fonts/Fontmap 50 1981860 652376 1622948 335248 true 1052 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] /var/lib/defoma/gs.d/dirs/fonts/Fontmap 50 1981860 652423 1622948 335248 true 1052 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/cups/fonts/Fontmap 50 2082340 693082 1622948 335248 true 1052 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/share/ghostscript/fonts/Fontmap 50 2082340 693126 1622948 335248 true 1052 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] /usr/local/lib/ghostscript/fonts/Fontmap 50 2082340 693174 1622948 335248 true 1052 4 <1>
D [14/May/2006:18:38:48 +0200] [Job 2] END FONTS 50 2082340 693215 1622948 335248 true 1052 4 <0>
D [14/May/2006:18:38:48 +0200] [Job 2] num_components = 1, depth = 1
D [14/May/2006:18:38:48 +0200] [Job 2] cupsColorSpace = 3, cupsColorOrder = 0
D [14/May/2006:18:38:48 +0200] [Job 2] cupsBitsPerPixel = 1, cupsBitsPerColor = 1
D [14/May/2006:18:38:48 +0200] [Job 2] max_gray = 1, dither_grays = 2
D [14/May/2006:18:38:48 +0200] [Job 2] max_color = 0, dither_colors = 0
D [14/May/2006:18:38:48 +0200] [Job 2] old_depth = 1, depth = 1, size_set = 0
D [14/May/2006:18:38:48 +0200] [Job 2] cache_size = 8388608
D [14/May/2006:18:38:48 +0200] [Job 2] cups->header.Duplex = 0
D [14/May/2006:18:38:48 +0200] [Job 2] cups->page = 1
D [14/May/2006:18:38:48 +0200] [Job 2] cups->ppd = 0x89ec310
D [14/May/2006:18:38:48 +0200] [Job 2] cups->ppd->flip_duplex = 0
D [14/May/2006:18:38:48 +0200] [Job 2] width = 850, height = 1100
D [14/May/2006:18:38:48 +0200] [Job 2] PageSize = [ 612 792 ], HWResolution = [ 100 100 ]
D [14/May/2006:18:38:48 +0200] [Job 2] HWMargins = [ 0.000 0.000 0.000 0.000 ]
D [14/May/2006:18:38:48 +0200] [Job 2] matrix = [ 1.389 0.000 0.000 -1.389 -0.000 1100.000 ]
D [14/May/2006:18:38:48 +0200] [Job 2] cups->header.Duplex = 0
D [14/May/2006:18:38:48 +0200] [Job 2] cups->page = 1
D [14/May/2006:18:38:48 +0200] [Job 2] cups->ppd = 0x89ec310
D [14/May/2006:18:38:48 +0200] [Job 2] cups->ppd->flip_duplex = 0
```

---

### Post by nipx on 2006-05-15
Hey,

Thanks :D. This has worked for me on Breezy and Dapper with X1185, works great.

---

### Post by Smakfull on 2006-05-21
I gave up and installed debian with xfce. Thank you anyway!

---

### Post by minimoose on 2006-05-21
Thanks everybody. I have one of those horrible "Dell Photo Printer 720"s, which are rebranded Lexmark Z615's. I followed all of the instructions on the first page and now the printer is working perfectly (under Ubuntu Breezy)! One thing though, when I tried to execute ./z600, there was no output, even after I edited /etc/fstab. It said that usbfs was already mounted. Oh well, as long as it works. At least now I can *finally* get rid of Windows!:cool:

---

### Post by UbuntuniX on 2006-05-26
When I try to open the z600cups file Gedit says it cannot automatically detect the character coding.

How can I open it?

---

### Post by o0blueardvarko0 on 2006-05-29
Ok. I tried all of that already. The way you have it laid out but once i get to the part you extract it using the tail command everything just fails. Can you help me? Maybe tell me why my Lexmark X1185 isnt working?

---

### Post by jrd on 2006-06-03
Thank you for writing this how-to!! I've been tring to get this printer working for a wile now. Now it works perfect!! Thank you.

---

### Post by at2000 on 2006-06-04
sudo apt-get install install libstdc++5 if "libstdc++.so.5" is missing.

---

### Post by cosine7 on 2006-06-05
Lexmark E230

Just a quick note, the E230 will work happily with Generic PCL-6-PCL-XL driver

---

### Post by Schalken on 2006-06-05
Thank you so much! I successfully printed across a Windows network to a Lexmark X1100 connected to a Windows ME computer thanks to this HOWTO! \\:D/ 

**Note: this HOWTO does NOT work on AMD64**! (not sure if this has already been concluded) This was my initial problem, since I previously used Ubuntu 64bit but changed to 32bit so more stuff works (including my printer).

---

### Post by migraineboy on 2006-06-05
Does it work for x1195? Does anyone have tryed?

---

### Post by H.E. Pennypacker on 2006-06-07
**black hole sun**, I kindly ask that you remove the following from your instructions and instead tell members to use the GUI as much as possible.  The following can be done using a few clicks here and there right inside Ubuntu:

$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.

Those three lines are:

1.  Create a folder named Lexmark on the Desktop.
2.  Move the downloaded file (the one from Lexmark.com) to the Lexmark folder.
3.  Once inside the Lexmark folder, right click on the .Tar.gz file, and select "Extract here."

It's a lot easier for newbies to understand English than messing around with all sorts of commands for the Terminal.  That's why I always recommend people using the GUI as much as possible, and it also makes us Linux users more human like (the more we rely on GUI, the more human like we are). :)

Also, can you please link directly to the .Tar.gz file so that totally lost newbies don't have to go the page, and figure out what to download.  Here's the link:

[http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

Moreover, you failed to mention that members need to download the "tail" command from Synaptic, before they can use it.  Fortunately, I figured out that you must download commands before you can use them.  So, I opened Synaptic, searched for "tail," and downloaded what I found.  It would be nice to add this note.

A note to newbies:

For the lines that preceed with "sudo," you can omitt "sudo" if you are either signed in as root, or you have already put in the "su" command and offered your password.  It's actually easier to begin everything by typing in "su," and then typing your password when requested.  That way, you won't have to add "sudo" for almost every line.

Also, keep in mind that you actually need to add the forward slash ("/") to the following line:

sudo tar xvzf z600cups-1.0.tgz -C /

The same goes for other lines that use the forward slash.  

When black hole sun says "Add this to your /etc/fstab file," open gEdit and edit the file /etc/fstab.  You can do this real easily by going to the terminal and typing in gedit /etc/fstab.  Remember to first begin with su and your password before doing this!  Typing gedit /etc/fstab opens up /etc/fstab in gEdit.

**black hole sun**, if you could, please do add these instructions to your original post.  It can save a lot of headache for newbies.  Thanks! :)

---

### Post by H.E. Pennypacker on 2006-06-07
I forgot to mention that it would be REAL NICE if there was a way to involve the GUI more, and less command line work.  So, for the next release, people could just browse for a file or whatever and install things that way.  It's always more convenient to use GUI, and its more attractive to newbies.  Basically, I am asking for a several-step process that doesn't require command line work.

---

### Post by sess420 on 2006-06-09
Your the man Black Hole Sun thanks alot

---

### Post by Tobas on 2006-06-10
Im having problems with adding a printer trough the webinterface of cups.
I have a working Ubuntu 6.06 server with no gui, and i have to work with the web interface.
But it wont let me add a printer ?
I have to be logged in as root but there is no login screen of some sort ?
I get this error

"426 Upgrade Required
You must access this page using the URL https://**********:631/admin"


everything worked fine in this HOW-TO and i see that my printer is found ( z65 ) but i cannot add him to be a active printer.
Can someone help me ?


Tobas

---

### Post by ivuntu on 2006-06-14
Hi!

I got my lexmark p707 working with Breezy thanks to this howto, with the Z600 driver. However, one day (probably after an ubuntu update) it did not work anymore: I could see the printing job in the printer properties window (it status sayed "printing"), but nothing happened.

now I upgraded to Dapper, and still the printer does not respond. I followed the instructions again, and here is where I got stuck:

$ cd /usr/lib/cups/backend
$ ./z600

I get no output, even though the usbfs is already mounted. 

Any suggestions are most welcome! Thanks in advance!

---

### Post by john.mccarty on 2006-06-17
Hello, I was trying to install the driver per the instructions in the first post for this topic and my system is completely screwed up now.

After executing the following step:
sudo tar xvzf  z600llpddk-2.0.tgz -C /

My user no longer existed in the sudoers file.  My user no longer has any rights to do anything.
I rebooted, but now Xwindows can't even start.

What happened, and how do I recover?

thanks,
john

---

### Post by joriad on 2006-06-18
help!!!! 

Ok, I went through the instructions in the first post to attempt to install a lexmark x2350, 3 in 1 printer. things seemed ok and drivers installed and backend seemed to be ok. however when I tried to print anything out the pages were in a constant state of processing and the printer just sat there like a large paper weight. 

I then shut down my computer and rebooted on my windows partition to make sure my printer wasn't faulty, it worked fine. I again rebooted my ubuntu 6.06 partition and tried to check if the printer worked and got this message "Cup server could not be contacted" and my printer was no longer to be found. 

So I went through the process again and this time when I got to "/etc/rc2.d/s19cupsys restart"
I got the response
"bash: /etc/rc2.d/s19cupsys: No such file or directory"
I then navigated to the folder and found that s19cupsys had disappeared

What happened and how do I fix this problem? And what do I do with this large :evil: paper weight that is consuming space on my desk and my sanity?](*,) 

Thanks 
Joriad

---

### Post by bitoiu on 2006-06-18
Hi,

I have a fresh 6.06 ubuntu, and decided to have a new try with my z515, and this how to worked perfectly.

Thanks black hole sun, great post!

---

### Post by rough raider on 2006-06-19
hi ! I have lexmark z705 and ubuntu 5.10 , drivers installed fine , test page prints in all colours but ... when I try to print something else like page from writer , printer loads paper but it's nothing on it - it is blank 

is there solution for it ? 
ps : ink is full

---

### Post by magnocrow on 2006-06-29
Lexmark Z32/Z22 or compaq IJ600  Run in Dapper??

---

### Post by reefland on 2006-07-02
I've been tasked with getting a Lexmark P4350 working under ubuntu 6.06.  I found this thread where several with Z or X based printers have had sucess.  Should I try these steps on a "p" printer?

---

### Post by reefland on 2006-07-02
[QUOTE=reefland]I've been tasked with getting a Lexmark P4350 working under ubuntu 6.06.  I found this thread where several with Z or X based printers have had sucess.  Should I try these steps on a "p" printer?[/QUOTE]

Well I figured the advice would be to just try it.  So I did.  No errors, but no results.

Got this at the end:

$ ./z600
direct z600:/dev/usblp0 "Lexmark Lexmark 4300 Series" "Lexmark Printer"

Nothing happenes after I add the printer.  Not even the sound of an attempt of the printer to do anything.

Suggestion?

---

### Post by ivuntu on 2006-07-11
Hi,

I followed your guide in Breezy: it worked very good, but in Dapper, the printer failed to work, so I followed the howto again. it gets down to this: I get no output when I type ./z600. So I added ```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
```  in /etc/fstab.

When I typed 

```
sudo mount usbfs
``` I got this:
```
mount: usbfs already mounted or /proc/bus/usb busy
mount: according to mtab, procbususb is already mounted on /proc/bus/usb

```

Any suggestions?

---

### Post by mhancoc7 on 2006-07-12
Thank you so much. I just tried this with Dapper and a Lexmark X1150 and it worked perfect. I was really desperate since I told my 3 year old that I would print out a picture of Thomas the Train that we had painted. There were only a few things I had to change in the instructions. Simply things like changing the directory and such.
Thanks, Jereme

---

### Post by denisesballs on 2006-07-19
You are a lifesaver! We've been struggling with these POS' for years! Confirmed on a Lexmark Z517 in Dapper. Thank you!

---

### Post by imhdd on 2006-07-20
Dapper 6.06. Configuring Lexmark z515.

Tried everything I could find about installing the z600le driver. I tried for hours but nothing worked for me (I'm new to command line). 

I learned a lot along the way; thanks to all who contributed to this thread.

Then I found this installation How To:

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605)

I followed these directions and EUREKA! My z515 works perfectly. Thank you all for help.

---

### Post by ivuntu on 2006-07-20
> **ivuntu said:**
> Hi,

I followed your guide in Breezy: it worked very good, but in Dapper, the printer failed to work, so I followed the howto again. it gets down to this: I get no output when I type ./z600. So I added ```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
```  in /etc/fstab.

When I typed 

```
sudo mount usbfs
``` I got this:
```
mount: usbfs already mounted or /proc/bus/usb busy
mount: according to mtab, procbususb is already mounted on /proc/bus/usb

```

Any suggestions?

I got it working again: it was a faulty USB Hub. The HOWTO works for Dapper too, it seems. good luck everybody

---

### Post by StarSkeptic on 2006-07-29
Worked lika charm --Lexmark z515
Many thanx:p

---

### Post by Leonivek on 2006-08-06
Finally!  I got my Lexmark x1110 printer to work in Dapper! :p  I haven't tested my scanner, yet, though.  

Thank you so much!

BTW, I can't seem to be able to print from Firefox. :-k  Anyone else have this issue? :-?

---

### Post by aviper2k7 on 2006-08-11
> **black hole sun said:**
> Everyone -- I'm so sorry I haven't been here for a long time so I haven't been able to help you guys. :(

I figured out your problem -- you need to mount the usb filesystem. Add this line to /etc/fstab

usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 

Then type 

sudo mount usbfs

Try the backend again and it should work.

Excuse my lack of Linux-knowlege, but how do you "add" that line to /etc/fstab.

---

### Post by davidrcuervo on 2006-08-15
This Howto works with my Lexmark X1195 and dapper.

Thanks a lot for your work:D

---

### Post by gates on 2006-08-16
Hi,
Got that driver going for my lexmark-X1195 on SuSE 10.0. The only changes I had to make were :-

1.did not do the alien part - just did :-
  rpm -ivh --nodeps ( both rpms on same line )
2.to reatart cups :- /etc/init.d/cups restart
3.added that usbfs line to my existing fstab ( after backing up fstab ) 
4.umount usbfs & did 'mount usbfs'
5.ran out the test print via gnome  ... all went well !!


Regards, .

---

### Post by bobmcferren on 2006-08-17
Many thanks!  Absolute newbee and your thorough indtructions were the best!

---

### Post by matchstich on 2006-08-20
> **imhdd said:**
> Dapper 6.06. Configuring Lexmark z515.

Tried everything I could find about installing the z600le driver. I tried for hours but nothing worked for me (I'm new to command line). 

I learned a lot along the way; thanks to all who contributed to this thread.

Then I found this installation How To:

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605)

I followed these directions and EUREKA! My z515 works perfectly. Thank you all for help.

 being a complete newbie my self . where do i put those commands. i tryed opening terminal but got nothing but error messages after typing in the commands listed on that link.
thanks

---

### Post by matchstich on 2006-08-20
> **black hole sun said:**
> Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

With that said, let's get to it! :D

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```

The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.
ok, i opened terminal typed in the commands as you had them written.
i downloaded the driver from lexmark.
but when i got to the 2nd one, the reply i got the file connot be found in any file or directory.
what did i do wrong?
thanks

---

### Post by KjetilK on 2006-08-26
Hi there!

Thanks for putting this together. I have a Dell A920 I'd like to get working. My platform is Kubuntu Breezy (allthough I have plans of a Dapper upgrade soon). 

> **black hole sun said:**
> 
The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:


I got this far, and it worked. 
```

root@owl:/usr/lib/cups/backend>  ./z600
direct z600:/dev/usb/lp0 "Lexmark Dell A920" "Lexmark Printer"

```

Then I run the KDE config tool, and at first it looks good, since the printer shows up in the port selection dialogue, it even shows as Dell A920! :-) 

But then something goes wrong. When building the list of drivers, nothing comes up, so I select "others", and select z600. It detects an error:

```

Wrong driver format.
/usr/lib/cups/backend/z600(line 1): syntax error, unexpected OPTION

```

I think, in a previous trail, that I saw a complaint about something on line 92 as well...

On my terminal, it says 
```

kdeprint: WARNING: PPD syntax error, PPD parse failed

```

Any ideas here?

---

### Post by KjetilK on 2006-08-26
> **KjetilK said:**
> 
```

Wrong driver format.
/usr/lib/cups/backend/z600(line 1): syntax error, unexpected OPTION

```

I think, in a previous trail, that I saw a complaint about something on line 92 as well...

On my terminal, it says 
```

kdeprint: WARNING: PPD syntax error, PPD parse failed

```


Actually, I decided to make a final attempt as a normal user rather than root. And then it worked. So, perhaps it was some kind of stale driver cache or something? If that's the case, how can I flush the cache?

---

### Post by LinLenLap on 2006-08-27
Thanks Black Hole Sun!

Your original post, the very first one, got me up and running with no problems!

Best,

LLL

---

### Post by FastZ on 2006-08-28
When I get to the

$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
steps, it says 

```
bash: alien: command not found
```

---

### Post by LinLenLap on 2006-08-29
I had the same problem, the solution is in this thread.

If I recall correctly it was:

> sudo apt-get install alien

Best,

---

### Post by 429148 on 2006-08-29
I keep getting this error 

bash: alien: command not found

this is after I type:
$ alien -t z600cups-1.01.i386.rpm

any ideas?

---

### Post by LinLenLap on 2006-08-29
Did you do this:

> Sudo apt-get install alien

If that doesn't work, make sure that you have the universe and community repositories enabled. It might be among those repositories.

Best,

---

### Post by fuxord22 on 2006-08-31
Thanks it worked, i don thave much ink, but when i printed i did see the shadow of what i wrote, so thanks. I dont understand how the whole process worked so need to work on that. but overall-thanks.

---

### Post by weemikey on 2006-09-04
[B]Many many thanks for this <black hole sun>.
I've re-done it as it worked out for me and hopefully even a total newbie, like myself, will be able to follow it and have a working Lexmark Z35 Printer.
WeeMikey[/B]

> **black hole sun said:**
> Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

With that said, let's get to it! :D

[B]%% black hole sun,
I'd like to make a couple of suggestions which I found necessary:

  first off I installed <alien> by going through <System> <Administration> <Synaptic Package Manager> <Search> <alien>.

  then for your driver go to: 

[http://support.lexmark.com/cgi-perl/selections.cgi?ccs=-1:1:0::0:0](http://support.lexmark.com/cgi-perl/selections.cgi?ccs=-1:1:0::0:0)

select your country and go from there.
When I got to the drivers section I picked up the Red Hat Linux driver as it's a *.rpm file which suits your script.[/B]

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

**At this point I went to <Places> <Home Folder> then clicked on <File> <New Folder> and when that appeared named it <lexmark>.  Then on the download of the driver I assigned it to that folder.**

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.


**These first two lines of code aren't necessary if you have already done  the suggestions above**

$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 

[B]]Open a terminal through <Applications> <Accessories> <Terminal> and follow the script.  I entered <sudo> at the start of each line of script - probably not necessary, but it made me feel better! This way your first line of code would be entered as:

$ sudo tar -xvzf CJLZ35LE-CUPS-2.0-1.TAR.GZ

rather than:[/B]

$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.

[B]My specific driver for Z35 was named <CJLZ35LE-CUPS-2.0-1.TAR.GZ>  so I substituted that in the line of code -exactly, remember capitals MUST be capitals, and lower case must be lower case for linux file names. Sorry to state the obvious to old timers, but it took me a while to learn many of these things.
At this point examine your extracted files and note their names -exactly!
I found <lexmarkz35-CUPS-2.0-1.gz.sh> and used that in the next line of the script.[/B]


$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail

[B]In these next two lines, using <alien> I found, through an error message, that I had to add <c> after the <-t> to get the scripts done too. For example the next 2 lines of code should read:

$ alien -tc lexmarkz35_CUPS-2.0-1.i386.rpm
$ alien -tc z35llpddk-2.0-2.i386.rpm

or the equivalent file names for your driver. You can see that it is important to identify equivalent files![/B]

$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.

**In the next two lines of code again make sure you have identified your specific *.tgz files AND don't forget the </> following the space after <C>. I did and it makes a mess**

$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model

**At this point I went to the selection bar at the top of the main window and clicked <Places> <Computer> <Filesystem> <usr> <share> <cups> <model> to identify the correct file for the next line of code. This turned out to be <Lexmark-Z35-lxz35cj-cups.ppd.gz> so I used that, Mind those CAPITALS and lower case letters!**

$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped[/code]

The driver is now installed. 

[B]Now open a new Terminal window <Applications> <Accessories> <Terminal> and enter:
$ sudo /etc/rc2.d/S19cupsys restart
you'll be asked for your password and you'll get the message:
   *Restarting Common Unix Printing System: cupsd
$ cd /usr/lib/cups/backend 
$ ./z35

at which point I got the message:

direct z35:/dev/usblp0 "Lexmark Inkjet color printer" "Lexmark Printer"

All is well! Carry on as below at the <If you get no output...> if you get no output.  I didn't have to do this so I can't say if it works or not.
Then jump to the <Now simply set up your printer ....>.  [/B]

Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

[B]The only difference I found here was that my printer showed up as <Z35-v2.0-1> and the driver was listed as <standard> .  If you enter the <Properties> option of the Printer itself you'll find the Driver as:
Manufacturer: Lexmark
Model: Z35 v2.0-1
Driver: Standard (suggested)

Go to <System> <Adminstration> <Printing>, your new Printer will appear in the <Printers> box.  Right click on it and highlight <Properties>. Check out the <Advanced> tab: I selected:
PageRegion: Letter
Output Mode: Grayscale  # can't afford colour cans 
Print Quality: Draft (300 dpi>   # life is short
Inkset:  # whatever suits you. [/B]

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.

**I really hopes this helps - especially all the new folks out there.**

---

### Post by bajjer31 on 2006-09-04
Worked perfect for my x1150, thanks!

---

### Post by ward.miller on 2006-09-07
Dear Black Hole Sun or anyone else who thinks they can help,

I am new to Linux (this is actually my first attempt at using the community)  and have not yet figured out its advantages.  I spent about 15 hours getting my wireless to work (vs. 5 minutes in XP) and have logged about 5 thus far on trying to install my Lexmark x1150.  I followed your directions, but am having trouble from the start.  I am using Dapper and have downloaded CJLZ600LE-CUPS-1.0-1.TAR.gz onto my desktop.  I then opened the terminal and begun typing what you suggested.  I had no problem making the directorylexmark as you suggest in the first step, but when I tried to move the file there this is what I got:

ward@ward-laptop:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

I also tried installing it through the system administration and it seemed like everything was in place but when I went to print it never came out even though it said it had been sent to the printer.  Any ideas, help, or even hope you could float my way would be much appreciated.  Thanks,
Ward

---

### Post by ivuntu on 2006-09-08
Hello Ward,

I think I know what went wrong. When you open up a terminal, it starts at a specific directory, the home-directory of the account you logged on. 
For example account ward: directory is /home/ward.

the file you want to move is in another directory, .i.e. on your desktop: /home/ward/Desktop (notice the upper case)

so you might want to try this:

```
cd Desktop
mv CJLZ600LE-CUPS-1.0-1.TAR.gz /home/ward/lexmark

```

Good luck!


> **ward.miller said:**
> Dear Black Hole Sun or anyone else who thinks they can help,

I am new to Linux (this is actually my first attempt at using the community)  and have not yet figured out its advantages.  I spent about 15 hours getting my wireless to work (vs. 5 minutes in XP) and have logged about 5 thus far on trying to install my Lexmark x1150.  I followed your directions, but am having trouble from the start.  I am using Dapper and have downloaded CJLZ600LE-CUPS-1.0-1.TAR.gz onto my desktop.  I then opened the terminal and begun typing what you suggested.  I had no problem making the directorylexmark as you suggest in the first step, but when I tried to move the file there this is what I got:

ward@ward-laptop:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

I also tried installing it through the system administration and it seemed like everything was in place but when I went to print it never came out even though it said it had been sent to the printer.  Any ideas, help, or even hope you could float my way would be much appreciated.  Thanks,
Ward

---

### Post by illu45 on 2006-09-09
I'm having the same issue that others here have had before, although I can't seem to find any resolution. Everything seems to work fine until I try the 
```
./z600
```

I get no output from this command. I added the usbfs line to my /etc/fstab, but when I try the 
```
sudo mount usbfs
```

I get the following error:

```

mount: usbfs already mounted or /proc/bus/usb busy
mount: according to mtab, procbususb is already mounted on /proc/bus/usb

```

I had some trouble with two of my USB ports in Windows, so it may be corrupt ports, which I know another user had, but I don't know how I would fix that.

---

### Post by Joedude on 2006-09-11
I look forward to generating a driver for the Lexmark X2350 all in one, thanx for the starter kit.

---

### Post by ubunturules on 2006-09-11
Joedude: Have you been able to get the Lexmark X2350 working?

---

### Post by Joedude on 2006-09-12
Not at all, it is appearing as though I'm going to have to do it from scratch. However, Ubuntu does acknowledge there is a lexmark 2300 series printer hooked up to it, so they are talking, they just don't understand each other yet...I'm gonna try n fix that.

---

### Post by ubunturules on 2006-09-23
how its coming?

---

### Post by Joedude on 2006-09-23
Nope, not yet. Give me time...it's the one thing I have very little of. I'm the father of kids, 2 and 3 years old, and have a job that demands 12 hour days...As soon as I get it, this will be the first place I post it. I'll even submit it to the developers.

---

### Post by lupin492 on 2006-09-26
Please, Jerrybme:  it would be VERY useful for us, 64-bit ridders, if you tell us how did you make the jail.  Specifically, wich libraries did you put in there por the printer to work.
Or did you make a complete 32bit-Ubuntu installation there ?
Hope you have time to tell us.
Thanks !!!

---

### Post by jmwinn21 on 2006-09-26
Thanks man!! I'm a Ubuntu newbie and it worked like a charm the first time around!! Thanks again.

---

### Post by rookieone on 2006-09-27
Thanks, that worked fine. OK I had to fiddle a bit but third time's a charm as they say.
Now I need to replace my cartridges, they've dried out.

---

### Post by matchstich on 2006-10-02
i have been trying all this stuff in here for a while and nothing is working, i give up. where can i find a list of printers that will work on ubuntu, thanks

---

### Post by H.E. Pennypacker on 2006-10-11
Will these instructions work with Lexmark X85 (which is a lot like the X75)?

> **matchstich said:**
> i have been trying all this stuff in here for a while and nothing is working, i give up. where can i find a list of printers that will work on ubuntu, thanks

You should consider [linuxprinting.org's recommendation page]("http://linuxprinting.org/suggested.html").

---

### Post by Chickenfoot on 2006-10-13
ARRGGGGGG,

Gods Frakkin' Damnit!!!

Trying to get my Lexmark 5150 working on DApper.

Read the whole thread, especially page 12! Added to my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1 /media/windows ntfs nls=utf8,umask=0222 0 0
usbfs /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

went to terminal, ran the following command:

tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver. 
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien --to-deb *.rpm # convert unusable rpm packages to deb.
dpkg -i *.deb # install the debs
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/init.d/cupsys restart # The driver is now installed. Restart the cups daemon.

I get this:

gunzip: Lexmark-Z600-lxz600cj-cups.ppd.gz: No such file or directory
chickenfoot@spanky:/usr/share/cups/model$ sudo /etc/init.d/cupsys restart # The driver is now installed. Restart the cups daemon./usr/lib/cups/backend/z600
 * Restarting Common Unix Printing System: cupsd                         [ ok ]


Still cannot print out. What am I doing wrong?

---

### Post by H.E. Pennypacker on 2006-10-18
I went to the first tail line, and I got a whole bunch of gibberish.  There is no text...just random characters...as you would see in a crashed text document.  

I followed these instructions before, and I downloaded tail, but now I don't know what to download anymore.  What exactly does tail go by in Synaptic?

---

### Post by twstokes on 2006-10-19
Worked beautifully with my Dell 720 over a network!

Prints a tad on the slow side, but that's way quicker than booting into Windows now isn't it?

---

### Post by H.E. Pennypacker on 2006-10-19
> **H.E. Pennypacker said:**
> I went to the first tail line, and I got a whole bunch of gibberish.  There is no text...just random characters...as you would see in a crashed text document.  

I followed these instructions before, and I downloaded tail, but now I don't know what to download anymore.  What exactly does tail go by in Synaptic?

It turned out I was only copying a part of the line.  Make sure you copy everything until the number symbol ("#"), which in programming languages, is used to preceed any lines that a programmer does not want the computer to recognize and use.  These "hidden from the computer" lines are called comments, and are useful for adding notes to a programming language.  In other areas of computers, comments are widely popular as well, and are used frequently.

---

### Post by makadam on 2006-10-21
Hello.

Thanks for your HOWTO.
I installed my Lexmark Z602 in a similar way. I used this French HowTo you can find here : [http://doc.ubuntu-fr.org/materiel/imprimante_lexmark_z600_serie](http://doc.ubuntu-fr.org/materiel/imprimante_lexmark_z600_serie)

---

### Post by Luthy on 2006-10-26
luthy@luthy-desktop:~$ sudo mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory
luthy@luthy-desktop:~$

Ok can some one please PM detailed instructions? I am somewhat of a newbie when it comes to comand lines, is there anyway you can do this w/o going into root? please and thank you hunnies!

---

### Post by DonKyot on 2006-11-02
Hi,
I'm being a bit thick.
Did everything on post #1. Then in
> **black hole sun said:**
> Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.no z600 shows up in the driver list.

I tried a few that do show up - no luck (X1180).

Any ideas?

ta

---

### Post by plb on 2006-11-04
> **DonKyot said:**
> Hi,
I'm being a bit thick.
Did everything on post #1. Then in
no z600 shows up in the driver list.

I tried a few that do show up - no luck (X1180).

Any ideas?

ta

Same here, here's what I did click the install driver button and goto /usr/share/cups/model and select the z600 driver...from there everything worked for me.

---

### Post by Barney on 2006-11-05
black hole sun,

Thanks, again.  I have used your procedure on three different Dapper installations and it worked flawlessly each time.  On the most recent install, everything appeared as though I had added the printer through the normal system, it was online and set as default, but still wouldn't print.  Again, I use your directions, and viola - she prints.

Thanks, for taking the time to be of such great help.

Barney

---

### Post by DonKyot on 2006-11-05
> **plb said:**
> Same here, here's what I did click the install driver button and goto /usr/share/cups/model and select the z600 driver...from there everything worked for me.
bingo:D 
Thanks.

---

### Post by pantsroptional on 2006-11-07
did not work for Z45

---

### Post by bjarne_w on 2006-11-10
Thanx man, worked like a charm - the first time on my Dell A920. :KS 

/Bjarne

---

### Post by murlosad on 2006-11-11
Great how-to man, I never managed to get my X1185 working in suse, but with edgy it works. I'm a very happy man tonight.

---

### Post by klaramalinowska on 2006-11-11
I've got lexmark Z705 printer.
I've followed HOWTO instructions carefully and almost everything works properly. Almost, cause back color is printed about 2 cm. on the left from other colors. It's partly printed besides paper.
What should I do to prevent such a situation? Is it the result of failed instalation, improper driver (I've used one for lexmark Z600, link is given at the begining of this howto) or bad properties?
Thanks in advence!

---

### Post by Ubuntist on 2006-11-22
Could I please suggest that anybody making use of this thread complain to Lexmark about the lack of a driver that works out-of-the box.

Go to [www.lexmark.com](www.lexmark.com), select Customer Support and then Technical Support, and you can take a survey on the quality of service provided by Lexmark that allows you to enter specific comments, i.e., that the Linux drivers don't work right.

---

### Post by H.E. Pennypacker on 2006-12-05
> **murlosad said:**
> Great how-to man, I never managed to get my X1185 working in suse, but with edgy it works. I'm a very happy man tonight.

Regarding your setting up of the Lexmark printer in Edgy, did you do anything differently from what's in the Lexmark Printers thread guide?

I am installing a Lexmark (well, its Dell, rebranded) in Edgy, but I am not sure if I should completely follow the guide, or whether I have to follow the guide at all.

---

### Post by drummer1189 on 2006-12-12
that link for the z600 driver is now broken

---

### Post by Alendit on 2006-12-23
Hi,

driver is installed, printer is added, but when I try to print test page there 1 job with job-hold-until-specified and nothing happens if I resume it...strange =)

Alendit

---

### Post by rykel on 2006-12-24
> **black hole sun said:**
> Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:


Hi,

I am trying to get a Lexmark X1195 to work... but I think there is a wrongly written instruction in your guide and a different backend that resulted on my Edgy Eft system:

1. To restart CUPS daemon, I believe it should be:
[INDENT]**sudo** /etc/rc2.d/S19cupsys restart[/INDENT]

2. The backend that came up on my screen was:
[INDENT]**direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"**[/INDENT]

Anyway, I tried to identify the printer in GNOME Printing as z600, but I could not find the model... (See screenshot; also notice how the driver is missing!)

Any help?

---

### Post by BLTicklemonster on 2006-12-29
Just set this up with a Lexmark Z1270. thanks for the help. I wonder if the scanner will work? Hmmmm

---

### Post by BLTicklemonster on 2006-12-29
> **rykel said:**
> Hi,

I am trying to get a Lexmark X1195 to work... but I think there is a wrongly written instruction in your guide and a different backend that resulted on my Edgy Eft system:

1. To restart CUPS daemon, I believe it should be:
[INDENT]**sudo** /etc/rc2.d/S19cupsys restart[/INDENT]

2. The backend that came up on my screen was:
[INDENT]**direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"**[/INDENT]

Anyway, I tried to identify the printer in GNOME Printing as z600, but I could not find the model... (See screenshot; also notice how the driver is missing!)

Any help?

Click install driver, then use the lexmark ppd in /usr/share/cups/model
and let it set up. Then try to print. If it won't, open your printer dialogue, delete the printer you just set up, then go through set up again, and you will probably see Z600 listed this time. That's what I had to do. 

GLuck.

---

### Post by Frostmourne on 2006-12-29
The instructions in the original post are somewhat dangerous. The "sudo tar....." steps change the user permissions in every directory the files extract into. For example, when I did these steps the / directory, /usr, etc. changed from the root owning the directories to my user, so I could create files and folders where I shouldn't be able to.

On my Edgy installation I simply used alien (like another user suggested) to install the z600cups and z600llpddk packages after extracting them and my printer worked. This method is better because you can easily uninstall every related file should you want to.

---

### Post by BLTicklemonster on 2006-12-29
Hey, how does one go about putting permissions back to normal once that has happened? 

Thanks for the heads up, too.

---

### Post by minimoose on 2006-12-31
Following up on Frostmourne, I suggest these instructions:

```

$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the package
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # put the needed files into a tar file
$ tar -xvzf install.tar.gz # extract the tar file
$ sudo alien -i z600cups-1.0-1.i386.rpm # install the printer driver
$ sudo alien -i z600llpddk-2.0-1.i386.rpm # install misc. printer libraries
$ sudo /etc/init.d/cupsys restart # restart the cups daemon
$ /usr/lib/cups/backend/z600 # check that the printer backend works (I get no output but it works fine)

```

Ldconfig is not needed since the drivers were installed through dpkg nor does the printer driver have to be gunzipped.

Go to System - Administration - Printing and choose the printer driver Z600 v1.0-1 under Lexmark (or, if it's not there, go to Install Driver and choose /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz), and enjoy!

For some resaon I have to go through the printer dialogue twice to get the printer to show up but it works nonetheless.

---

### Post by Raavea on 2007-01-05
WOO! I love you, black hole sun.

 I was so worried my new spangly printer wouldn't work. But (the printing part at least, so far) is working! 

 Big props! 

 
 PS: I have a Lexmark X1270 All-in-one.

---

### Post by csmaccath on 2007-01-21
Hey All,

I am a BRAND NEW Ubuntu user, and I found this how-to really helpful.  However, when I completed the process, the driver was not listed as an available driver in printer setup.  

After a bit of investigation on Google, I found the following thread:
[http://www.ubuntuforums.org/archive/index.php/t-29374.html]("http://www.ubuntuforums.org/archive/index.php/t-29374.html")

From that thread, I extracted the following solution:
If the driver doesn't show up as an option when you install the printer, click the "Install Driver" button and go to /usr/share/cups/model.  The .ppd file should be listed there.  Select it as the driver for the printer.

Hope this helps! :D

---

### Post by Lumumba on 2007-01-25
THANKS!!!  
This worked on Warty 4.1 with a Z605.  I got an error with restarting cups, so I shut everything down and rebooted.  The driver was there on reboot, and works!
THANKS A BUNCH from a *very* new to linux/ubuntu person!!!:D :D :D

---

### Post by BLTicklemonster on 2007-01-25
Raavea, have you gotten the scanner to work yet?

---

### Post by heyilikeyoursweater on 2007-01-26
I have a z750 and I think I got the drivers working, but when I try to print, it just shoots blank paper out. I have to get this printer working or else I have to go back to windows, and we all know we don't want that...

---

### Post by NoVista on 2007-01-28
Installation went great on a P707 Lexmark printer, installed on Edgy.
Hmm, I never had to go get the 'tail' file.

But .. .. it prints as though the printer heads need to be aligned.

How can I fix this?

---

### Post by ECPCLINUX on 2007-01-29
I have a Lexmark X1150 :(  and I followed instructions steps by Black Hole Sun  to a T to no avail. I have been trying to install the 600z driver for about 3 month (the time I have been using Ubuntu). I was able to installed the lexmark 35 driver but that only made my X1150 pass a paper (as if it were GAS! NO PRINTING). Well, I would go on to other project and come back to my lexmark from time to time only to be frustrated and look for an alternative printer that might work with Ubuntu. After a while I just hoped I could get the printer to work forget the scanner,lol. After several self imposed projects in Ubuntu I decide to try again, I figured I have learned a little and I do mean a little more. I could not get passed the first two commands. so l just extracted the file on my desktop by double clicking on the downloaded tar.gz file.  Then I used BLACK HOLE SUN'S original codes from line 4 on. From there  all was smooth sailing, seem like I had found a way to this. I got up to code line 12, where the terminal acknowledged that I have installed the driver, hooray!!! But wait! :(  The next steps is where it all crapped out again.:lolflag:  when I added these code :
"$ cd /usr/lib/cups/backend
$ ./z600"
 I got nothing!!! :mad: Well I did what Black Sun Hole suggested we do and nothing! Could not get it to work. I looked at the printer setup to see if by some miracle the driver would be there, "after all the driver did install". Well no such luck. I tried this about three time, when it occurred to me that maybe I can get the printer setup to install the driver. I remembered that there was a button that can install driver from printer setup and it had a CD icon. I then set out to find the location of the driver that was pretty easy "etc/cups/ppd". I installed it using the printer setup and ... ready for this??? Hooray!!! it installed!!! Now the next step was to have the printer print, doooh!! Ok, lets not panic, proceeded to Say a little prayer, crossed my fingers  and got on my knees before attempting to print. I found a text file to print and set up the printer 600z as default using Openoffice  sent the job to the printer. yeahhhhhhhhhhhh!!! I got my first print, perfect!!! Thank you to all of you for the help specially Black Hole Sun for initiating these instructions. Best of luck to you all maybe these unconventional instructions will work for some one out there. After countless hours of fun I got Ubuntu to do all I need it to do...for now :D  No more singing the Blues, unless I want to do so!  :guitar:

---

### Post by jesus5511 on 2007-02-02
Is it possible to do this with the X75?

---

### Post by barney_1 on 2007-02-03
My System:
Kubuntu 7.10 Feisty Fawn (still in development)
Printer: Lexmark Z25

I used this HOWTO when setting up my Lexmark Z25 printer.  Everything seemed to install properly but I could not print a test page.  When I looked at my CUPS log I found this error message:

```
02/03/2007 04:11:13 PM	[Job 1] Unable to open printer port "/dev/usblp0": Permission denied
```

I couldn't find much through searching but I think i figured out the problem, hopefully this will help you out if you have the same troubles.

In my case, the systemuser: "cupsys" did not have access to /dev/usblp0 because that user was not a member of the plugdev group.  By adding "cupsys" to the "plugdev" group using the user management dialog I was able to allow cups to access my printer.

Once you have added that user to the group, restart the cups daemon:
```
sudo /etc/init.d/cupsys restart
```

Good luck!

---

### Post by blackhole82 on 2007-02-06
I have a lexmark x2470 attached to a windows machine set up as a shared printer.  I followed this guide completely and it seemed to be setup.  When I selected the z600 model in cups and then tried to print a test page the printing dialogue came up on my windows machine.  However,  after the whole document was transferred my printer failed to print.  It seems to be kind of slow transferring as well.  I guess the driver just isn't very compatible with the x2470.  I thought maybe if I could find the actual driver on the original CD I could use that, but I seem to have lost the CD.

---

### Post by eschatologicalhumor on 2007-02-11
This Forum has been abundantly helpful to me in the past week or so during my endeavors in switching from MS to NIX, specifically UBUNTU(K,U,X), and for that I thank you all in advance and in retrospect.

This post has a dual purpose: First commending the code that lead to my printers inevitable usage(even though I think my ink is dried up from it's rest in the attic) and also to point out a couple code strings that not only didn't work, but weren't required to install and use the driver.

One quick, and confused comment before the strings....When I ran the tail command my terminal screen scrolled like a mad penguin full of strange characters, probably binary code of some sort due to the inscribed action 'tail' is supposed to perform, and left me at a /dir with this:

/home/sotec/Desktop/lexmark# 62;9;c62;9;c62;9;c62;9;c;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;ctar

Any explanation? All I know is that after the confusion ceased to interest me, I decided to skip that part and move ahead to the commands :

$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped

Which in fact did as they were supposed to; they config'd, moved to dir and unzipped the driver, which was cake to find in the /usr/share/cups/model dir.

The printer works now and I couldn't be happier! But I wanted to post and share with you all the fact that the commands:

$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place

...didn't work...not did they need to on my machine.
So thank you for the awesome Tutorial!
(now if I could only get my ink to fire on the paper....)

Anyone know how to perform the maintenance printer actions? i.e. head cleaning?

Thanks!

---

### Post by divali on 2007-02-12
Using Edgy.
I have a Lexmark Z715 and followed all of the Howto as given by Black Hole Sun and everything
went fine but when I rebooted and tried to add the new printer in the Gnome printer Cups 
system the z600 wasn't listed. 
Can anyone help. What could I have missed.

---

### Post by sh4d3z on 2007-02-13
i simply made a shell script out of the tutorial called lexmark_install.sh
it spits this output :

```
sh4d3z@nix-machine:~$ lexmark.sh
creating ~/.lexmark dir
downloading CJLZ600LE-CUPS-1.0-1.TAR.gz
--12:57:48--  http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz
           => `CJLZ600LE-CUPS-1.0-1.TAR.gz'
Resolving www.downloaddelivery.com... 199.106.212.28
Connecting to www.downloaddelivery.com|199.106.212.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,301,167 (4.1M) [application/x-tar]

100%[===================================================================================>] 4,301,167      1.08M/s    ETA 00:00

12:57:55 (725.52 KB/s) - `CJLZ600LE-CUPS-1.0-1.TAR.gz' saved [4301167/4301167]

extracting it
COPYING
README
z600cups-1.0-1.gz.sh
repairing nessessary shell script
Password:
extracting the contents of installer
globals.tcl
install
lexinstall
lexinstall.tcl
license
setup.tcl
testpage
usb.tcl
xlexinstall
xlexinstall.tcl
z600cups-1.0-1.i386.rpm
z600llpddk-2.0-1.i386.rpm
coverting rpm packets to tgz
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z600llpddk-2.0.tgz generated
extracting tgz and puting the files in their right places
./
./usr/
./usr/include/
./usr/include/lexmark/
./usr/include/lexmark/alignmentdata.h
./usr/include/lexmark/cartridgemanager.h
./usr/include/lexmark/cartridgeuserinterface.h
./usr/include/lexmark/cleaningdata.h
./usr/include/lexmark/clock.h
./usr/include/lexmark/errorcommunicator.h
./usr/include/lexmark/linuxinkjetprinter.h
./usr/include/lexmark/mediamanager.h
./usr/include/lexmark/portmonitor.h
./usr/include/lexmark/printerdevice.h
./usr/include/lexmark/printjobmanager.h
./usr/lib/
./usr/lib/liblexprinter.a
./usr/lib/liblexprinter.la
./usr/lib/liblexprinter.so.0.0.0
./usr/lib/liblexprintjob.a
./usr/lib/liblexprintjob.la
./usr/lib/liblexprintjob.so.0.0.0
./usr/lib/liblexz600core.a
./usr/lib/liblexz600core.la
./usr/lib/liblexz600core.so.0.0.0
./usr/local/
./usr/local/z600llpddk/
./usr/local/z600llpddk/utility/
./usr/local/z600llpddk/utility/bnsi1.lut
./usr/local/z600llpddk/utility/bnsi2.lut
./usr/local/z600llpddk/utility/bnsi3.lut
./usr/local/z600llpddk/utility/lxbcalgn.out
./usr/local/z600llpddk/utility/lxbccln.out
./
./usr/
./usr/lib/
./usr/lib/cups/
./usr/lib/cups/backend/
./usr/lib/cups/backend/z600
./usr/lib/cups/filter/
./usr/lib/cups/filter/rastertoz600
./usr/share/
./usr/share/cups/
./usr/share/cups/model/
./usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz
finding required libs
unzipping the ppd
restarting cups daemon
 * Restarting Common Unix Printing System: cupsd                                                                        [ ok ] 
checking back end
all done :)
test it by running  ./z600
output should look similar to:
direct z600:/dev/usb/lp0 Lexmark Lexmark Z600 Series Lexmark Printer
sh4d3z@nix-machine:~$ ./z600
bash: ./z600: No such file or directory
sh4d3z@nix-machine:~$ cd /usr/lib/cups/backend
sh4d3z@nix-machine:/usr/lib/cups/backend$ 
sh4d3z@nix-machine:/usr/lib/cups/backend$ ./z600
direct z600:/dev/usblp0 "Lexmark  Lexmark Z700-P700 Series" "Lexmark Printer"

```

this worked fine on dapper, but not so great on edgy... it just sits there like a friggin' tard when i try to print test page
i'm using a z705... we'll see what i can do later, i've been in front of this machine way too long and needa break before i resort to using sledgehammer to fix the problem lol

---

### Post by eschatologicalhumor on 2007-02-13
> **divali said:**
> Using Edgy.
I have a Lexmark Z715 and followed all of the Howto as given by Black Hole Sun and everything
went fine but when I rebooted and tried to add the new printer in the Gnome printer Cups 
system the z600 wasn't listed. 
Can anyone help. What could I have missed.

First thought would be that you're attempting to use a z600 driver with a z715 printer. I have a z515 myself, but my assumption would be that the z600 driver works with all 'previous' printers of the z family, and my personal opinion is that any z driver should suffice for any z family printer, unfortunately Lexmark isn't as yet that thorough in offering drivers for all of their printer models.

Also, I had the same problem finding the driver on my harddrive, so try looking in /usr/share/cups/model after you complete the tutorial. In that folder there will be a .tar.gz with the name Lexmark-z600-lxz600cj.cups somethingorother. Right click and extract it to that folder and it will turn it into a .ppd. That's the driver you use in the printer setup.

Hope that helps. I'm a newbie myself, so I have no problem batting back and forth with solutions.

---

### Post by divali on 2007-02-13
Holy crap! 
It worked. A million thankyou's.
 I could rain kisses down upon your cherubic upturned face.

---

### Post by Wight_Rhino on 2007-02-13
I got a Lexmar 1270 given to me as a gift by people who wouldn't know that I used Linux and there might be compatibility problems.

Long story short you got it working. Thankyou.

I'm applying to The Vatican to have you Canonised.:guitar:

---

### Post by ssavelan on 2007-02-21
Indeed, the original instructions by Black Hole Sun were close in my case.

I have xubuntu, which shouldn't be that different.  Like many users, I had to direct the printer GUI (whatever I have with xfce) to the .ppd in the

/usr/share/cups/model/

directory.  The z600 driver failed to come up under the Lexmark section in the GUI. No biggy.

I told the GUI to print a test page and it looks beautiful.

I have set this driver a few times with ubuntu and now with xubuntu.  It works really well for my z615 and doesn't ever insist on calibrating like windows does which is an annoying waste of time and ink.

Everyone, good luck with your printer issues, keep the faith.  I almost had an emergency meltdown  when my old instructions from "the fine bush people of south africa" ended up being outdated.  Thanks everyone for taking the time out to keep the z600 ubuntu alive):P ):P ):P

---

### Post by tchslemur on 2007-02-21
i got to the part where you move the package to the lexmark folder and this is what i got

mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

i have already downloaded the file and it is on my desktop and i checked to see if it was the name and they were the same

 can you help

---

### Post by karlosfandango64 on 2007-02-27
Hi.  I'm new to Ubuntu as of today, but not entirely to Linux.  I've run through all these instructions and despite having the usbfs mounted, and restarting cups I still get no output from /usr/lib/cups/backend/z600.  Can you help?  I am running ubuntu 6.10 on an IBM ThinkPad T21 laptop, in a docking station, with a Lexmark X1130 connected via the USB port on the docking station.  Thanks.  Karl.

---

### Post by swa2b41 on 2007-02-27
Help... I've been trying and trying to follow the directions from page one of this post and I keep getting the following error: 

tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

What am I doing wrong? I've downloaded the driver and put it in folder on my desktop called lexmark, I've put it on my desk top and nothing... 

Please help me.... I am very new to all of this... :confused:

---

### Post by karlosfandango64 on 2007-02-28
> **karlosfandango64 said:**
> Hi.  I'm new to Ubuntu as of today, but not entirely to Linux.  I've run through all these instructions and despite having the usbfs mounted, and restarting cups I still get no output from /usr/lib/cups/backend/z600.  Can you help?  I am running ubuntu 6.10 on an IBM ThinkPad T21 laptop, in a docking station, with a Lexmark X1130 connected via the USB port on the docking station.  Thanks.  Karl.

Well.  It looks like this problem was down to the USB port.  I hope this helps all the others who had this problem.  I unplugged the printer's USB cable from the docking station USB port and plugged it into one of the ports on the PCMCIA USB2 card I have installed, also in the docking station, and then I got the required output from running z600.

After that I was able to install the printer OK, although it did seem to take a couple of attempts before I could see the z600 driver in the list of Lexmark drivers in the printer config wizard.  Also, the first time I added it, with a customized name, it didn't show up.  When I tried to add it again and just accepted the default name, it was fine.

Thanks & I hope this helps someone.

---

### Post by pmgordon on 2007-03-03
Worked Perfectly with a x1150 over smb.

---

### Post by starcraft.man on 2007-03-08
I got and understood everything till the USB thing. After using all the terminal commands I confirmed that my USB was detecting my Z65. I think I messed up at the part where you have to add it in the gnome control panel for printers... I picked the z65 from the detected column and then pushed next and pointed the driver installer to the Z600 driver in /usr/share/cups/model and clicked through and it installed, but when I do a test page the que pauses the print job and won't print even if I push resume. Did I do something wrong?

---

### Post by LMelior on 2007-03-11
Wow, works with my Lexmark X1270, excellent stuff!

Note to several members of this thread (if they're still around) - if your printer is already on the list when you go to System>Administration>Printing (that's in 6.06), try that first!!!

Also, to swa2b41, in the instructions it gives an optional line to move the downloaded tar.gz file to the newly created lexmark folder.  If you did that line, you have to do:

```
cd lexmark
```

right afterwards so you can start working with the files from that directory.

One last hint to avoid spelling mistakes, when you get to long confusing names, type the first letter or two and hit <TAB>, or just highlight the individual commands on the first page, bring up your terminal window and click your mouse wheel (the wonderful copy and paste method that I always miss when I'm in Windows).

---

### Post by Seiti on 2007-03-18
Nice tutorial! 
It did make my Z645 works under Ubuntu Edgy.  But I had to give the PPD file path, when asked by printing dialogs, to make the z600 model available on the items list.

---

### Post by doctrdev on 2007-03-20
UG!! PLEASE HELP

I followed the instructions to the LETTER!  NOTHING but error messages.. and why does it ask me for a password?  I am already logged in as an administrator...

devin@devin-desktop:~$ mkdir lexmark
mkdir: cannot create directory `lexmark': File exists
devin@devin-desktop:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark #
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory
devin@devin-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz #
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
devin@devin-desktop:~$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz #
tail: cannot open `z600cups-1.0-1.gz.sh' for reading: No such file or directory
devin@devin-desktop:~$ tar -xvzf install.tar.gz #

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
devin@devin-desktop:~$ alien -t z600cups-1.0-1.i386.rpm #
bash: alien: command not found
devin@devin-desktop:~$ alien -t z600llpddk-2.0-1.i386.rpm # 
bash: alien: command not found
devin@devin-desktop:~$ sudo tar xvzf  z600llpddk-2.0.tgz -C / #
Password:
Sorry, try again.
Password:

---

### Post by Mickus on 2007-03-22
Thanks, works perfectly with my X1110.  Could not at first find the new installed z600 driver.Found it finally in: /usr/share/cups/model      :)

---

### Post by Feenix3k on 2007-03-24
I found that my Dell A920 will work in 6.06 using these instructions

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605)

I never could get it to work in 6.10, so I went back to 6.06

---

### Post by gnat79 on 2007-03-24
Hi,

I have followed all the directions to the part where I run ./z600. I get no output. I have mounted usbfs as shown, and that still doesn't change it. Can anyone suggest more ideas? Thanks

---

### Post by Fleetness on 2007-04-05
I had a little different setup, I was connecting to a Lexmark 510 series printer attached to a windows XP box on my home network.

This howto works to the point where you try to use System/Administration/Printers to setup the printer.  It would never show the driver and if you tried to install it, it would say that it was already installed.

I got some help from this post [http://www.aquarionics.com/article/name/Making_the_Lexmark_Z515_work_under_Debian_Linux](http://www.aquarionics.com/article/name/Making_the_Lexmark_Z515_work_under_Debian_Linux)

The default printer utility doesn't allow you to setup the printer.  You can set it up by connecting to [http://localhost:631](http://localhost:631)  and using the web admin interface to setup your printer.  I set mine up to connect to the printer using smb://WindowsXPcomputerName/PrinterName
as the URI and then choosing the z600 driver in /usr/share/cups/model directory.   This set the printer up and I could then print to it.  

The default Gnome printer utility is a little brain dead and never shows the new printer driver or allows you to manually choose it.  Using the Cups web admin interface gives you much better control and selection in setting the printer up correctly under Feisty Fawn Beta.

So to use this howto under Edgy or Feisty, follow it till the end and Don't try to use the Gnome printer setup utility, Use the Cups web interface at the end of the tutorial by connecting to http:/localhost:631 to do the final configuration after you have the z600 driver installed.

---

### Post by trigggl on 2007-04-08
For those who are still getting the scanner to work for a X1100 series AIO, this is the small step that often gets left out.  The standard setup for sane looks for the scanner at /dev/usb/scanner0.  The answer that I always find for this is don't use udev.  What?!

It's such an easy fix once someone actually takes the time to put out there.  Sane looks for the scanner based on the config file for the scanner in /etc/sane.d/lexmark.conf.  Guess what that file says:

/dev/usb/scanner0

So, I assume that's where the scanner is supposed to be.  No.  To find out where the scanner really is, look in the file /etc/sane.d/hotplug/libsane.db.

In there, you will see that the X1100 scanners are at:

0x043d  0x007c

To make a long story short, your /etc/sane.d/lexmark.conf file (or wherever Ubuntu puts it, I run Debian) should have this one line in it:

> usb 0x043d 0x007c

So, to repeat.  Here's what I did.

$su
Password:
#vi /etc/sane.d/lexmark.conf

Then I deleted the line that reads "usb /dev/usb/scanner0" by hitting "dd", type "i" to insert, typed in the line above, hit escape to get out of insert mode and typed in ":wq".

Then just make sure you exit out of root before trying scanimage or xsane or anything.

For some reason my X1150 still won't scan, but it does something to let me know Debian found it.

I guess it's more appropriate to say that usb 0x043d 0x007c is what the vendor code for the scanner is.  Linux will find it based off of you telling it what the vendor ID is even though it already knows that something with the ID of 0x043d 0x007c is connected to it.

Scanner access now easy.

Edit:  If you don't want to look through config files, the vendor ID can be located with "lsusb -v".  Of course that produces a rather large output and there's more than one ID on the X1100.

---

### Post by herbster on 2007-04-09
> **o0blueardvarko0 said:**
> Ok. I tried all of that already. The way you have it laid out but once i get to the part you extract it using the tail command everything just fails. Can you help me? Maybe tell me why my Lexmark X1185 isnt working?

Yeah, I get lots of really funky, wierdo output when I run the tail command, it just keeps going, I don't know what to do. Someone help??

---

### Post by BHelts on 2007-04-12
Thank you very much.  I got my Lexmark x1150 that is connected to my wife's xp box working across the wireless.  I too had to manually install the .ppd to get z600 on the list, but once that happened it worked perfectly.  Thanks again.

---

### Post by mohanjith on 2007-04-14
I had trouble downloading the archive from Lexmark. I maged to download from opendrivers.com

So I decided to host the 2 rpms my self.

Here are the links

[http://www.mohanjith.net/downloads/drivers/printers/lexmark/z600cups-1.0-1.i386.rpm]("http://www.mohanjith.net/downloads/drivers/printers/lexmark/z600cups-1.0-1.i386.rpm")

[URL="http://www.mohanjith.net/downloads/drivers/printers/lexmark/z600llpddk-2.0-1.i386.rpm"]http://www.mohanjith.net/downloads/drivers/printers/lexmark/z600llpddk-2.0-1.i386.rpm
[/URL]

Hope this helps.

---

### Post by ssavelan on 2007-04-18
Great Howto. Bravo. Thanks a lot.

---

### Post by THEBIGEYE on 2007-04-19
Help i had my Lexmark x1100 USB printer with the z600 driver installed and working in edgy I386
 I've just upgraded to feisty fawn AMD64 installed driver in exactly the same way can select printer but when i try to print a test page
 it just says job stopped anyone have a solution is this to do with the 64 bit architecture could i install 32 bit cups would this work?
any ideas would be greatly appeacated

---

### Post by transactionlogfiller on 2007-04-21
I'm having the same problem after going from 32bit edgy to 64bit feisty. My Lexmark z615 installs but will not print.

---

### Post by Drk_Guy on 2007-04-22
Hey, this doesn't work on 32-Bits Feisty either, i have a Z605

---

### Post by THEBIGEYE on 2007-04-22
i think i have found a AMD64 workaround but its for gentoo could anyone have a look see if it is and poss translate for ubuntu sorry i hav enever used gentoo so i can t see what the commands how they relate to ubuntu cheers [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

---

### Post by josno on 2007-04-23
> **Drk_Guy said:**
> Hey, this doesn't work on 32-Bits Feisty either, i have a Z605
I have the same model and managed to get it working in Feisty. I followed the instructions, and then just had to select the PPD file when it came to choosing the driver (by clicking on the 'Install driver' button or whatever it is).

---

### Post by THEBIGEYE on 2007-04-23
jonso i can get it to work on 32 bit arch but no 64 bit can u get it on 64 bit
if so how im really stuck

---

### Post by josno on 2007-04-23
Sorry, I gave up on amd64 just because of things like this :S I don't have the technical know-how to translate that Gentoo stuff either.

---

### Post by kevdog on 2007-04-23
I bet I already know the answer but I cant seem to get the Lexmark X6150 to work despite installing the z55 driver as someone recommended.  I sent a test page that took 10 minutes and nothing was printed.  Ive searched the internet and it seems this printer might be a dud as far as getting it to work.  Any driver suggestion I could try???

---

### Post by Sycrat on 2007-04-24
Thanks mate, thanks HEAPS, I got my x5150 working through LAN with your help :D. Good job and good luck to everyone else.

~Aaron Blair

---

### Post by kgriffin on 2007-04-26
Hi there,

I followed all the steps,

When I go to System -> Administration - Printing

and Add a new printer

It says use a detected printer

Lexmark Lexmark Z65

Woohoo!

When I go on to select a driver, the z65 nor z600 ones are there :S

any ideas?

Thanks
Kev

---

### Post by josno on 2007-04-26
Have a look here: [http://ubuntuforums.org/showthread.php?p=2518474#post2518474](http://ubuntuforums.org/showthread.php?p=2518474#post2518474)

---

### Post by kgriffin on 2007-04-26
Thanks I tried that, but nothing has come up in my Printers screen, I tried doing it again and it says it is already installed.

I tried printing something and just get "Error whilst printing"

Any more ideas? :)

---

### Post by revilodraw on 2007-04-27
When i try to add a printer I cannot see z600 at all... but when i use z31 and/or z32 my printer will shoot paper out, but not print on it... any ideas?
I have a x1270..

---

### Post by offchance on 2007-04-27
I basically cut'n'pasted the commands. the only trouble I ran into was installing alien [no big deal] and having to wait a few minutes for ./z600 to return any results. thanks for the tut!

---

### Post by DJiNN on 2007-05-03
Does anyone know of a way to get a Lexmark X5250 working on Xubuntu? Is there a PPD driver available anywhere or would i be better of getting an old WinMachine & just setting it up on the Network as a Print Server? It's for my partners machine. She's been using XP up until now, and i've just installed Xubuntu (Feisty) on it for her.... working great, even picked up the D-Link USB wifi stick (Which it wouldn't do when i tried a year or so ago) so i'm very pleased..... if i can just get this printer going then she'll be set & i'll have another converted Linux user!! :)

Any help or pointers much appreciated.

Thanks......

DJiNN

---

### Post by kenora_kid02 on 2007-05-06
Hey all!  I'm new to the forums... fun and games..

Anyways, I don't suppose anyone knows how to get the scanner bit of a Lexmark X1185 to work, eh?  I've tried XSANE, and it just stalls the scanner... a hideous "BRRRRRR!" noise emanates from deep within the plastic heap.  I also tried the GNOME Scanner Utility, but to no avail.. it just crashes.

From what I've seen in other Linux forums, the best way to fix the issue seems to be to just scrap the Lexmark.  

Thanks in advance for any help or insight on the issue.

MJ

Also, using Ubuntu Edgy on this machine.

---

### Post by 2whlgeezer on 2007-05-07
Another newbie here.  Followed the first post, went pretty well (had to install alien and had to sudo to restart cupsys), got to the end and got this-
usr1@desktop:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
usr1@desktop:/usr/lib/cups/backend$    

Using KDE desktop.

Tried to install printer anyway, found the nre z600 driver fine, went through install, test print comes up, reports test sent to printer OK, but nothing else.  Suggestions?

Thanks

---

### Post by tatakae on 2007-05-13
Hello. I'm trying to download the z600 driver from Lexmark's site but it is giving me a 404 error. I tried googling for the file but all sites point back to the Lexmark page. :( 

Can anyone point me to a site that has the driver archived?

Thanks,
tatakae

---

### Post by johny 69 on 2007-05-13
hi 
I just follow what was writen in first page and I have same problem as 2whlgeezer.
So if can anyone help us.............. please. Thank you.
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
Sorry ............. I use Kubuntu 7.04.................... and is my first linux system..............and I do not speak english wright.................. so be patient pls.

---

### Post by rputtagunta on 2007-05-14
> **kevdog said:**
> I bet I already know the answer but I cant seem to get the Lexmark X6150 to work despite installing the z55 driver as someone recommended.  I sent a test page that took 10 minutes and nothing was printed.  Ive searched the internet and it seems this printer might be a dud as far as getting it to work.  Any driver suggestion I could try???

    kevdog, I have the same EXACT printer and I couldn't get it to work. Wondering if you have had some success recently? Please let me know.


Thank you,
Rahul.

---

### Post by GremlinUK on 2007-05-16
Have there been any developments on the Lexmark P4350 questions?

This is currently the only thing stopping me from switching from Windows XP on my laptop to Ubuntu 7.04!

Ta,
Gremlin

---

### Post by juniorsonny on 2007-05-18
The download link on Lexmark's site for  CJLZ600LE-CUPS-1.0-1.TAR.GZ is a dead link.  Please someone help me find the file!

---

### Post by mrfuzzemz on 2007-05-19
> **juniorsonny said:**
> The download link on Lexmark's site for  CJLZ600LE-CUPS-1.0-1.TAR.GZ is a dead link.  Please someone help me find the file!

I, too, need this file.  I confirm that it is down. Would anyone still have it and could maybe post it here?

Thanks so much!

---

### Post by sk8dork on 2007-05-20
i was just trying to download the file too. the result, i've found, is that whoever is maintaining the lexmark site is an idiot.

note that the link on their site points to 
[http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.**[SIZE="3"]GZ[/SIZE]**](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.GZ)

the actual file name is case sensitive and the correct file is
[http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.**[SIZE="3"]gz[/SIZE]**](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

happy downloading =)

---

### Post by mrfuzzemz on 2007-05-20
> **sk8dork said:**
> i was just trying to download the file too. the result, i've found, is that whoever is maintaining the lexmark site is an idiot.

note that the link on their site points to 
[http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.**[SIZE="3"]GZ[/SIZE]**](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.GZ)

the actual file name is case sensitive and the correct file is
[http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.**[SIZE="3"]gz[/SIZE]**](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

happy downloading =)

Haha.  Well.  This is excellent!  Thanks, sk8!

---

### Post by resistfascism on 2007-05-20
Just successfully printed a test page going by the directions in the original post.

Cut and paste worked fine, no additional tweaking of the commands given.

However, I did have trouble getting the initial tarball off lexmark's web site to get the process started.  I don't know if they've taken the file off permanently, or it was just missing temporarily, but I kept getting a 404 error when I tried to download it.

I did find the file on this howto ([http://www.staerk.de/thorsten/index.php/Set_up_a_Dell_A902_printer_with_SUSE_Linux](http://www.staerk.de/thorsten/index.php/Set_up_a_Dell_A902_printer_with_SUSE_Linux))

The file can be downloaded directly by using this link:
[http://downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

---

### Post by orentini on 2007-05-25
works fine on feisty and Lexmark X1190.

Thank you.

---

### Post by Daniel15 on 2007-06-03
This seems to work for my Lexmark X1150 on both Ubuntu Feisty and Debian Etch... Thanks! :D

I only encountered one problem - In the GNOME "New Printer" wizard, it did not display the Z600 driver. The solution to this is to open CUPS (go to [http://localhost:631/](http://localhost:631/) in your web browser), and add the driver via its "Add Printer" wizard. When you're prompted to choose a driver, click the "Browse" or "Choose" button next to the "Or Provide a PPD File:" field, and browse to **/usr/share/cups/models/Lexmark-Z600-lxz600cj-cups.ppd**.

---

### Post by mrfuzzemz on 2007-06-03
> **Daniel15 said:**
> This seems to work for my Lexmark X1150 on both Ubuntu Feisty and Debian Etch... Thanks! :D

I only encountered one problem - In the GNOME "New Printer" wizard, it did not display the Z600 driver. The solution to this is to open CUPS (go to [http://localhost:631/](http://localhost:631/) in your web browser), and add the driver via its "Add Printer" wizard. When you're prompted to choose a driver, click the "Browse" or "Choose" button next to the "Or Provide a PPD File:" field, and browse to **/usr/share/cups/models/Lexmark-Z600-lxz600cj-cups.ppd**.

Thanks Dan for that last note.  I couldn't find the driver in CUPS for gnome.

---

### Post by Contrast on 2007-06-08
Just now got a Lexmark X1100 working by following this guide. Thanks a LOT!! :-D

---

### Post by CapPicard on 2007-06-11
I finally got my Z515 to work under 64-bit Ubuntu Feisty.

I created a 3-bit chroot jail as posted in another thread.

Then, I installed cups, libusb, and libstdc++ in the jail. The one line I was missing in the parent's fstab was this line:

*usbfs         /usr/local/chroot32/proc/bus/usb usbfs   devgid=14,devmode=0660 0  0*

Adjust according to wherever your jail resides. In my case, it is /usr/local/chroot32/

The Z600 driver works like a dream. :)

---

### Post by CapPicard on 2007-06-11
And i can successfully print to my printer (connected to my 64-bit linux desktop) from my vista laptop. 

Since 64-bit samba knows nothing about my printer, I just setup cups-lpd via inetd/xinetd within the jail. On my vista laptop, i just create a new LPR port and away I go. A slight delay when I print (it's over wifi), but it works like a dream.

No more rebooting into 32-bit XP just to print. :)

---

### Post by Halogenmaster on 2007-06-12
Thank you very much.It works for x1270.:p

---

### Post by kfir_w on 2007-06-12
Hi, I have a Lexmark Z612.
Your HOWTO worked!!

Thanks a lot,

   Kfir

---

### Post by dwlegg on 2007-06-18
If you get to the ./z600 line and get the message:

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

... it means you need the compat-libstdc++-33 package.

On Fedora Core 6, to get it you just type:
yum install libstdc++.so.5

Cool.  No doubt some-one will say how you do it on Ubuntu.

---

### Post by samuraiCat on 2007-06-22
Every day for the last two weeks, I have seen people posting about their Lexmark printers. They have tried all the tips that have shown up on this board, and nothing has worked. They are ready to give up.

I was in that place until last night. I have a Lexmark Z517, which was deemed a paperweight. I had tried all the instructions posted here, and nothing had worked.

Then I found this page: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)

I followed it to the letter, and despite the fact that my printer is neither a multifunction printer nor listed as being supported in the instructions, it worked like a charm.

If you have any kind of Lexmark, take a break from scouring these forums for a second and try that howto.

---

### Post by Arenlor on 2007-06-26
MEOW! Another X1270 working flawlessly with the tip to do it through the cups interface.

---

### Post by kiev on 2007-06-28
and Lexmark scanner - how?

---

### Post by mrfuzzemz on 2007-06-28
> **kiev said:**
> and Lexmark scanner - how?

I've been able to use the scanner on my X1100 with XSane in Applications > Graphics, but for some reason it only scans a small portion of the area of the bed.

---

### Post by ry4n on 2007-06-29
problems already, 

mkdir lexmark worked fine but mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark

gives me a,

 mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

help me if you can, thank you:(:(

---

### Post by herbster on 2007-06-29
Excellent HowTo!!

I don't know if it's been mentioned in this long thread but perhaps worth repeating if so, I just needed to get my XP machine networked Lexmark X1195 to work so I don't have to keep going into Remote Desktop and printing inside the XP box, and all I did was:

1. System > Admin > Printing
2. Make sure Detect LAN Printers is checked under the Global Settings menu
3. New Printer
4. Network Printer, select your network and the printer from the detected list
5. When it asks the driver, select Lexmark and Install Driver
6. Go to /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd, using the driver this HowTo instructs to install.
7. DO NOT change the name of the printer, perhaps it was just me but I did and it didn't work, then I installed again and didn't change the name or anything and hit Apply and it worked. Just printed a test page and it's bootyful :)

---

### Post by ry4n on 2007-06-29
Hello i am back already, I just found these instructions and they are much better check them out. [http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge](http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge)

thank you all that tried to help me.

---

### Post by rallenk on 2007-07-01
when I attempt to run this command:  tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz

I get this:
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Where's my error?

---

### Post by rahimveron on 2007-07-04
Thank you for the suggestion. After trying hours of typing and extracting and what not i read your comments and installed the Z600 drivers. The printer Lexmark X1185 is printing all right but the scanner does not work. I use XSane but after pressing scan from Xsane it hangs but my printer scanner does move but the program Xsane hangs!!!
Any ideas???
> **ECPCLINUX said:**
> I have a Lexmark X1150 :(  and I followed instructions steps by Black Hole Sun  to a T to no avail. I have been trying to install the 600z driver for about 3 month (the time I have been using Ubuntu). I was able to installed the lexmark 35 driver but that only made my X1150 pass a paper (as if it were GAS! NO PRINTING). Well, I would go on to other project and come back to my lexmark from time to time only to be frustrated and look for an alternative printer that might work with Ubuntu. After a while I just hoped I could get the printer to work forget the scanner,lol. After several self imposed projects in Ubuntu I decide to try again, I figured I have learned a little and I do mean a little more. I could not get passed the first two commands. so l just extracted the file on my desktop by double clicking on the downloaded tar.gz file.  Then I used BLACK HOLE SUN'S original codes from line 4 on. From there  all was smooth sailing, seem like I had found a way to this. I got up to code line 12, where the terminal acknowledged that I have installed the driver, hooray!!! But wait! :(  The next steps is where it all crapped out again.:lolflag:  when I added these code :
"$ cd /usr/lib/cups/backend
$ ./z600"
 I got nothing!!! :mad: Well I did what Black Sun Hole suggested we do and nothing! Could not get it to work. I looked at the printer setup to see if by some miracle the driver would be there, "after all the driver did install". Well no such luck. I tried this about three time, when it occurred to me that maybe I can get the printer setup to install the driver. I remembered that there was a button that can install driver from printer setup and it had a CD icon. I then set out to find the location of the driver that was pretty easy "etc/cups/ppd". I installed it using the printer setup and ... ready for this??? Hooray!!! it installed!!! Now the next step was to have the printer print, doooh!! Ok, lets not panic, proceeded to Say a little prayer, crossed my fingers  and got on my knees before attempting to print. I found a text file to print and set up the printer 600z as default using Openoffice  sent the job to the printer. yeahhhhhhhhhhhh!!! I got my first print, perfect!!! Thank you to all of you for the help specially Black Hole Sun for initiating these instructions. Best of luck to you all maybe these unconventional instructions will work for some one out there. After countless hours of fun I got Ubuntu to do all I need it to do...for now :D  No more singing the Blues, unless I want to do so!  :guitar:

---

### Post by Lacrimstein on 2007-07-06
i have a problem: i have entered all the commands, without any errors. However, when i try to install the printer in the dialog, the z600 driver is not displayed in the drivers list for lexmark drivers:(
please help...

---

### Post by Lacrimstein on 2007-07-06
nvm figured it all out!!!  :D

---

### Post by pswartout on 2007-07-10
I have followed these extremely good instructions to have the driver installed on my Ubuntu Linux laptop with a SMB share printer set up (the printer is currently attached to my Windows server and shared over my home network). Sometime I shall get around to converting this to Linux. Many thanks :lolflag:

---

### Post by GremlinUK on 2007-07-12
Well, the Z600 method certainly doesn't work for the P4350. The device installs, the driver claims to send a test page to the printer, but nothing, nada, zip, happens at the other end of the USB cable.

:(

---

### Post by centrinoduo on 2007-07-16
hi i have a lexmark x1180 and the printer doesnt zeem to work help me here pleaaaaaaaaaseee:confused::confused::confused::confused::confused::confused::

---

### Post by abrianb on 2007-07-19
I just got my x1150 to print after a lot of trial and even more error. The tutorial on page one worked when  I made this change. First down load the file from lexmark.Next install alien,in terminal type install get alien. Next type this command
     cd Desktop
 notice that the D in Desktop is capitalized. this will add the word Desktop to your prompt. Now run every command listed in the tutorial. I copied and paste each line one at a time. Before you enter the command   tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # you will want to open the lexmark folder on your desktop and drag the file z600cups-1.0-1.gz.sh out of the folder and on to the desktop.
During this process my desktop was filled with about 15 or 20 icons. Don't worry about them, we will clean up later.
 Once you have ran all the commands from page 1s tutorial , you will need to go to System>Administration>Printing on your desktop. Click on add new printer. select the detected printer and click forward. it will suggest you use a driver, DON'T. Click install driver. A window opens  titled select a ppd file. There will be an arrow< button next to your user name click that arrow twice. From this menu scroll down to a file marked usr. Click usr twice to get a new  menu. scroll down to the file share,click twice,scroll to the file cups, click twice, Scroll down to model,click twice and then among your choices should be Lexmark -Z600-lxz600.ppd  Click twice to install and then print something. 
 I sure hope this works for you. It took me about 7 hours t get mine printing.

---

### Post by ortutt on 2007-08-01
I have Ubuntu for just two days.
I tried the HOWTO on my Ubuntu 7.04, and it doesn't work.
I think I had a few problems - "alien" is not installed, and no matter what I couldn't make the last code line -  /.z600 - work.
Trying to enter the whole code at once, nothing past the "mkdir lexmark" works.
I probably sound like a spoiled windows user, but isn't there an easy way of installing drivers in Ubuntu?

---

### Post by ep3w on 2007-08-02
I have a lexmark z705 and followed all the steps but when i go to the printer GUI and try to add it as a printer, when it tells me to select the model the z705 is not an option.  Am i supposed to select a different model or did I do something wrong? Thanks for the help!

---

### Post by ortutt on 2007-08-02
Hi,
I finally installed the Z600 driver for my X1270, but it does nothing.
I understand it's because I have Ubuntu AMD64.
I understand I need to "create a 32 chroot", and I even tried to do it but it didn't work, maybe becuase the howto for it is two years old.
Does someone know of a new howto, or a new way to get around this problem?
Thanks...

Moved to 32bit, it works!!!

---

### Post by Vince4Amy on 2007-08-04
Works on the Lexmark Z640.

---

### Post by TrashmanL on 2007-08-04
OK, I have a Lexmark PrinTrio 3150. In Windows, the drivers it uses are Lexmark 3100 Series. When I go to Administration/Printing in Gnome and click on new printer, it goes to Step 1 of 3: Printer Connection. Uner "Use a detected Printer" it correctly lists Lexmark 3100 Series. However, when I hit forward and go to Step 2 of 3: Printer Driver, there is no 3100 in the list it asks me to select from.

Additionally, if I go to Lexmark.com and search for 3100 series, it offers Windows 98/ME and 2000/XP drivers and a note that says if an OS isn't listed, drivers are not available.

From the list, I've tried 3000 and 3200... both get my printer to turn on and respond, but I cannot print anything (in fact, after attempting to use either, I have to unplug my printer and plug it back in before even Windows will print to it again). 600 series and z35 drivers do not work for it. There's a host of others. Anyone else out there have a 3100 series they've gotten to work? If so, what drivers were used?

---

### Post by gimpguy2000 on 2007-08-13
Well, I went through all the steps, even got the correct output, no errors, etc...right to a T.  However, my drivers still aren't listed when I set up the new printer. It shows two lexmarks, one lexmark z600 the other lexmark z600 (usb). Same printer but neither work. there is no z600 driver listed. 


Thanks,

Paul

I am not running 64 just for informational sake. ;)

---

### Post by gimpguy2000 on 2007-08-14
> **black hole sun said:**
> Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

With that said, let's get to it! :D

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```

The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.



Just a note: ** PER INSTRUCTIONS ABOVE** What I had to do AFTER in my case was this...

1. Open System; Administration; Printing 

2. When setting up printer,  choose the lexmark  printer but manually choose a driver \ location. 

3.Go to directory>>>   ** /usr/share/cups/model** choose the "most likely" only ppd file and manually install the driver. It remained listed and my printer works. 


Cheers, thanks for the great head start BHS ;)

Paul

---

### Post by white3454 on 2007-08-15
I tried these instructions with a Lexmark E232...  and the printer would send out reams of single line jibberish...  but I thought 'Hey it's printing, just not what I want it to print....   it was a start' 

So I finally stumbled upon this link:

[http://www.linuxforums.org/forum/ubuntu-help/70037-lexmark-e232.html](http://www.linuxforums.org/forum/ubuntu-help/70037-lexmark-e232.html)

Setup your up printer as Generic and use the PCL 5c driver.  Not the best quality but if you use this scale

Dot Matrix______Color Laser____________Kinko's
 1.....2.....3.....4.....5.....6.....7.....8.....9.....10

I say it's at leat a 5-6...  The webpage I used to test the printer came out pretty clear.

So I hope this works if you have a lexmark laser printer...  Also doesn't HP own Lexmark?  Businesses use Lexmark printers in Unix/Linux just like they use HP...  I know beating a dead horse...

---

### Post by rdagijones on 2007-08-16
I have a Lexmark Z65n printer.  I have followed the steps listed at the beginning of this thread and installed the drivers for the printer.  **Is it possible to "tweek" the driver so that I can use the ethernet connection on the printer instead of USB?**  My Ubuntu box is connected to an existing LAN through a router.  Two wireless laptops use the WLAN to print to the Z65n.  I would like to print from the Ubuntu box as well.

---

### Post by Lihaässä on 2007-09-04
Hi!I bought this wonder machine called Lexmark x4580 and its part of their 3500-4500 series. The problem is, that I couldn't find suitable drivers for this piece of scanning-, copying- and printing machine. If anyone knows how to get this machine working I would appreciate! Thanks already for your efforts.. btw. I'm using Feisty 7.04.

---

### Post by divali on 2007-09-22
Okay, here's my problem.
I used this howto on  Ubuntu Feisty for my Lexmark Z517 and it worked a treat.
 But, I am now trying to use it to get my printer working with Debian Etch and I am stuck. 
You might be wondering what someone using Debian is doing in this Forum. Wel the reason is that Iguessed both are based on Debian so  if the howto works on Ubuntu then why not on Debian. I have searched the Debian forum but there isn't much ragarding Lexmark printers.

I followed the instructions to the letter,I believe.
Everything went ok:  installed the drivers etc and the result of /usr/lib/cups/backend/z600  returned the correct printer.

Here's the result of /var/log/cups
E [22/Sep/2007:12:44:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [22/Sep/2007:15:42:08 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [22/Sep/2007:15:43:34 +0100] PID 4601 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [22/Sep/2007:15:44:08 +0100] PID 4658 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [22/Sep/2007:15:44:24 +0100] CUPS-Delete-Printer: Unauthorized


 
Time after time I used the printer manager but, the Z600 would not show up in the Lexmark list.

Am I totally barking up the wrong tree using this method with Debian
or did I miss something
Time after time I used the printer manager but, the Z600 would not show up in the Lexmark list.

Am I totally barking up the wrong tree using this method with Debian
or did I miss something?

Any help would be greatly appreciated.

---

### Post by uldics on 2007-09-23
Thank you very much for this great and precise manual!

I have Lexmark X5150 all in one. Have tried to get life into it for more than a year. Have heared, that z55 drivers are good for it, but never had a luck of getting it to work. Now I got them from Lexmark page and did exactly the steps described here. And it works! Driver names were CJLZ55LE.tar.gz and CJLZ55LE-CUPS-1.0-1.TAR.GZ. Inside are same type sh scripts as described here.

Thank you!

PS Yes, I use Debian Etch and was tempted to do that alien thing to .deb, but had to return to .gz conversion, hehe ;)

---

### Post by timothy632 on 2007-09-23
MUST INSTALL BOTH OF THESE

Lexmark Z600   in .deb                no need for tar or rpm

[http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb)

[http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb)

USE THE GDEBIAN PACKAGE INSTALLER

GO TO PRINTERS AND U SHOULD FIND THE Z600 UNDER DRIVERS USE THIS FOR THE X1270

FOR MORE HELP GO HERE [http://dgtlmoon.com/dell_720_printer...n_debian_sarge](http://dgtlmoon.com/dell_720_printer...n_debian_sarge)


hope this helps

---

### Post by mexiloco on 2007-09-23
i tried doing this on my emac but i get this error right away
```
mkdir: cannot create directory `lexmark': File exists

```
i have a Lexmark X1185

---

### Post by Stochastics on 2007-09-27
Hi

When you write :

$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place

what's your "right place" ?

Thanks 

Stochastics

---

### Post by jakv on 2007-09-28
Okay, so there seems to be some people that have amd64 systems and can't get the driver to work. I know, because I'm one of them :) so, here's a little outline on how to I did the chroot. There's already a bunch of guides everywhere on how to make chroots, so just follow one of them. If you need one, try this:

[https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292281](https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292281)

part way down the page, it has instructions on how to do a 32 bit chroot. there's also more links from previous posts.

disclaimer: I'm actually on debian lenny, but really, ubuntu's based off debian, so it shouldn't matter that much. Also, my printer is one of those terrible dell 720 rebranded lexmark 615 or whatever, so I don't know how it works for anything else.

Okay, so get your chroot. and follow the driver install instructions for the chroot. Then, make sure you have cups in the chroot, and libstdc++5. I don't think ./z600 works, so don't mind about that. If it does, and the printer prints, great. Anyways...

Now, stop cups in the host system, and start cups in 32-bit mode. You can add your printer by going through the web interface of cups (I'm not sure if you can use regular gui tools to configure cups at this point) at [http://localhost:631](http://localhost:631) and installing the ppd there. Now, print a test page, and it should work. If it doesn't, then you have issues. But seriously, I don't know what's up. The only other pieces of advice I have to offer are:

make sure your chroot 32bit has /chroot/lib/modules mounted from /lib/modules. My cups or something didn't work until I did that.

When you're printing from something, like openoffice, and it just spits out blank sheets instead of beautifully formatted stuff, you should play around with the printer settings. Set the postscript level to an actual number, set it to color or grayscale. 

Okay, so that's my advice. I still haven't figured out how to do it automatically at boot time, but that's just a matter of scripting. 

Peace

---

### Post by jakv on 2007-09-28
oh, and btw,

@Stochastics
the right place is in the right system directories. Unless you had to do a chroot like me, then do it to the root directory, and you'll be fine = P

---

### Post by smd0665 on 2007-09-29
Has anyone had any luck with the Lexmark X75 yet?

I followed these instructions: [http://users.netwit.net.au/~pursang/lex.html](http://users.netwit.net.au/~pursang/lex.html)

and changed the .rpm files to .deb using alien. When I try to print, the printer responds, the paper moves a bit, but I get a blinking status light. That's all.

---

### Post by BLTicklemonster on 2007-09-29
What I think is funny is how lexmark has this:

[http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html)

which makes it look like they have everything under control (to the casual observer), when in fact, their support is weak. Scanner support is basically nonexistant from what I've see.

My wifey-poo got me a nice scanner/printer for Christmas, and it's basically useless in linux. I can get it barely working to print, but the scanner (which loads right up in the other operating system, and does incredible scanning) support just isn't there at all.

One would think that the entire printer industry would stop and see the - oddness? - of making different drivers for just about every printer made. What's the point in that? I'm speaking of companies, not HP drivers supporting Lexmark, but one set of drivers for all of one company's printers. Sure, each scanner has different needs, but building the drivers on a core, and working out from there would be more efficient, wouldn't it?

---

### Post by Lacrimstein on 2007-10-03
I just reinstalled ubuntu today, and i'm trying to install my z515 printer again. Last time, i installed it using this tutorial, and it installed very smoothly.
but now, I cannot find the z600 in the models list even after rebooting. I think that it has something to do with the fact that ./z600 outputs 
> direct z600:/dev/usblp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"
instead of
> direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"
basically, the slash between usb and lp0 is missing. how can I change it? or is it something else?

---

### Post by Mountaingod on 2007-10-10
I've got a [SIZE="3"]z708[/SIZE] and somebody else here said it worked for them so I tried it. I don't think it's working for me.

Everything went fine, except for a couple of warning messages half way through that went along the lines of "not executed as root, some of the permissions may not be right" - but I didn't change to doing those commands via sudo because I figured it was deliberate, being as how the instructions didn't omit sudo in other places.

When I was done, and went to **System > Administration > Printing > Add printer**, I now get two detected instead of the usual one:

[IMG]http://i182.photobucket.com/albums/x154/MountainGod/Screenshot-AddaPrinter.png[/IMG]

The top one I always had, the bottom one is new. Whichever one I choose, when it comes to identifying the model in the next step, neither the z600 or z708 is an option.

Checking the printer backend (one of the last steps in the howto) prints out a message pretty much the same as what it should be.

If I can't fix this and get my printer working, my alternative question is:
[SIZE="4"]how do I reverse whatever this howto has just done to my computer??[/SIZE]

---

### Post by Mountaingod on 2007-10-11
Any suggestions? It appeared to be putting stuff all over my filesystem, and if it's stuff made with alien I'd rather it come back off again being as how it's not doing anything useful.

---

### Post by spacetree on 2007-10-13
just install xsane. it worked for me

---

### Post by HardcoreLinux on 2007-10-16
> **aviper2k7 said:**
> Excuse my lack of Linux-knowlege, but how do you "add" that line to /etc/fstab.

$ sudo nano -w /etc/fstab

Add that line to the file

---

### Post by rahimveron on 2007-10-21
Will this work in Lexmark X1185 in Gutsy Gibbon?
It is recognized as a generic X1100 series but it does not print. It remains idle.

---

### Post by Nichtigkeit on 2007-10-26
Confirming that this solution works for the X1155 printer-scanner. Perfectly!! Thanks so much for this workaround :guitar:

---

### Post by blank.bruno on 2007-10-26
Under Gutsy Gibbon (7.10), my X1270 works perfectly for me (printing portion).  I had one minor issue, in that I had to delete the existing entry from System->Administration->Printing, then perform the steps to add a printer, making sure to select the Z600 driver as instructed.  Thank you so very much for the help with this.  :)

---

### Post by andrewdodd13 on 2007-10-29
I was about to post in here, asking how I could make this work over SAMBA - I have my Lexmark X1150 connected to my Windows PC and shared so I can print from my laptops (well one is my sisters). I'd followed the guide, and added the printer via Gnome administration, I pressed "Print Test"... and... nothing.

"Damned" I thought. So I thought... right... I have no idea how to debug this, so first thing I thought... maybe network printing needs the printer to be switched on, so I pressed the button, and since I couldn't hear the mechanical noises cause of the loud music I had on, I assumed it went on.

But it didn't. _Long story short, it works fine over a network._

I'd just pulled the power cable out with my feet.

Accepting nominations for the Darwin award. :)

---

### Post by duruttye on 2007-10-30
Hey guys!
I have the same problem! Was there a solution to this? I already did the tutorial for like 4 times, but it doesn't work for me.
printer: lexmark z 605, ubuntu 7.04


> **Lacrimstein said:**
> I just reinstalled ubuntu today, and i'm trying to install my z515 printer again. Last time, i installed it using this tutorial, and it installed very smoothly.
but now, I cannot find the z600 in the models list even after rebooting. I think that it has something to do with the fact that ./z600 outputs 

instead of

basically, the slash between usb and lp0 is missing. how can I change it? or is it something else?

---

### Post by duruttye on 2007-10-30
this is what my system log says:

/var/log/cups/error:
E [30/Oct/2007:10:44:50 +0200] cupsdAuthorize: Local authentication certificate not found!
E [30/Oct/2007:10:45:32 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [30/Oct/2007:10:46:21 +0200] [Job 9] No %%BoundingBox: comment in header!

---

### Post by duruttye on 2007-10-30
Got it working, but I don't know what I did different for the 6th time.:popcorn:

---

### Post by thefunnyman on 2007-11-03
I have a Lexmark X1185 printer....I'm VERY new to linux. I followed the HowTo step by step on the first page of this thread and everything worked fine.  I've set up the printer in the Printer Config using Z600.  When I try to print a test page, the printer arm slams the cartridge against the side of the printer and the light just starts blinking on the printer.  Any insight from anyone?  

Thanks in advance.

---

### Post by ruibar on 2007-11-04
> **transactionlogfiller said:**
> Thanks for this howto! It's one of the smoothest I've used from this site.

My comments below seem a bit pedantic but I just thought, keeping it simple enough for everyone, in-keeping with the style of this site, maybe add some points to the howto?

I had to sudo apt-get install alien first.

When I run alien I get a warning about ownership of files, because you didn't tell me to run it as root, so I went back and did "sudo alien"

That said, it's probably still the howto where the output I got differed least from what I was expecting, if you see what I mean. Which might be partly because I'm using breezy.

I have a Lexmark 1195 and this worked fine. Just had to get  alien: ```
sudo apt-get install alien
``` and execute the restart CUPS daemon in super user mode: ```
sudo /etc/rc2.d/S19cupsys restart
```

---

### Post by welshlion on 2007-11-11
> **rahimveron said:**
> Will this work in Lexmark X1185 in Gutsy Gibbon?
It is recognized as a generic X1100 series but it does not print. It remains idle.

This reply is probably a bit too late for you, but i've just got an X1180 working with Gutsy Gibbon... further info, I followed the original 'How To'  but didn't get any output at the end, however by going to System>Administration>printing>new printer I was able to work through the wizards until I found the Z600 option and selected that.

---

### Post by aj61779 on 2007-11-13
I tried the HOW TO and got this error:

aj@aj-desktop:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
aj@aj-desktop:~$ tar -svzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: You must specify one of the `-Acdtrux' options
Try `tar --help' or `tar --usage' for more information.
aj@aj-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
aj@aj-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
aj@aj-desktop:~$ 
HELP please!

---

### Post by JimBobble on 2007-11-17
aj, I believe a "cd lexmark" is needed in between the top two lines.  mv the file to folder "lexmark," then cd, then tar.

> **aj61779 said:**
> I tried the HOW TO and got this error:

aj@aj-desktop:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
aj@aj-desktop:~$ tar -svzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: You must specify one of the `-Acdtrux' options
Try `tar --help' or `tar --usage' for more information.
aj@aj-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
aj@aj-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
aj@aj-desktop:~$ 
HELP please!

---

### Post by JimBobble on 2007-11-17
For whatever it's worth, I got an X1150 shared across the network working under Gutsy after much wailing and gnashing of teeth.  The how-to executed perfectly (minus the USB part because of the network connection) except for the fact that nothing happened when submitting print jobs.  A tip somewhere along the way to install libstdc version 5 got me going:

> yeah...i got that too with breazy. you can go to

System ->Administration -> Synaptic Package Manager

search for libstdc, and install version 5.

From the looks of it, Gutsy installs version 6 but 5 is necessary here. ???  Anyway, thanks much for the leg up to all and sundry.
__________________

---

### Post by the_Ben on 2007-11-30
Howdy all, I've been trying to use these instructions for my Lexmark 510 series, but I have trouble when I get to this part:

> If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
```

Then just type: sudo mount usbfs. That should fix it.

I can get to the fstab file, open it, and enter the new code, but it won't let me save it.  Do I need to log in as root to fix this?  Thanks in advance.

Edit: Logged in as root, edited the file, IT WORKS!  One less reason to use XP!  Now to get my webcam working...

---

### Post by dmonner on 2007-12-05
I had to do one extra step to get my X5150 working in Gutsy with the z55 driver. When I would add the printer in Gnome's printer configuration, it would detect my printer and automatically set the device URI as:

```
usb://Lexmark%20/X5100%20Series
```

Even though running /usr/lib/cups/backend/z55 showed:

```
direct z55:/dev/usb/lp0 "Lexmark Lexmark X5100 Series" "Lexmark Printer"
```

The solution is to manually set the device URI in the Gnome printer config to:

```
z55:/dev/usb/lp0
```

Now it works fine!  Hope this helps someone!

---

### Post by wavesound on 2007-12-07
HI
 I have the C534n which worked fine in 6.06 LT.
On installing 7.10 it didnt work ( it's networked)
I then just used synaptic and searched for printers, then downloaded other printer stuff and  it now shows up on Gnome and works with raw.

I dont suppose this is nice but it works and I dont have windoze to boot into so was a show stopper for me.

Thing is I have 64studio,  Debian based on here ( duel boot) and it found the printer fine. 

Cheers
Bob

---

### Post by Chymera on 2007-12-15
ok, i tried this and it didn't work.... how can I get rid of the files I've installed?

---

### Post by wavesound on 2007-12-15
> **Chymera said:**
> ok, i tried this and it didn't work.... how can I get rid of the files I've installed?

HI
Normally back into synaptic and uninstall the apps.
Just check what they will uninstall. make sure you don't remove the desktop and such.

I use the 'raw'  setting on my Lexmark seems to get nice results although is slow to print.
I still haven't found a ppd for this printer anywhere.

Cheers
Bob

---

### Post by divali on 2007-12-23
> **mjpieters said:**
> I solved the problem. If you get a **'Cannot Process Raster**' errors, the Z600 raster filter cannot read the required datafiles. When converting the RPMs and installing the resulting tarball or deb package, certain directories end up being readable only to root.
 
To check if this is the problem, try and look at the /usr/local/z600llpddk/utility/ directory (with ls or with your favourite file manager). If you get a permission denied error, chances are the conversion filter cannot read it either.
 
The following two commands will fix this for you. Run these as root (sudo or log in as root) to fix this, and another directory likely to have the wrong permissions:
 
  ```
chmod -R +rX /usr/local/z600llpddk/
chmod -R +rX /usr/include/lexmark/
```
 These changes made the printer work for me.

This worked for me after I spent ages trying to find the drivers when z600 drivers weren't showing in the CUPS printer list.
Thanks.

---

### Post by chewit on 2007-12-24
I have a Z640, when i did the install command, it said the file doesn't exist

---

### Post by dccrens on 2008-01-01
First of all these forums are wonderful! I even got my WPC11 wireless work... Now I an trying to set up printing. I have Gutsy and have gotten an HP printer working on the network and am now trying to get a Lexmark X5150 working. The X5150 is on my windows XP box. I have SAMBA working (can mount shares, etc) I can also print to the HP printer direct (IP) or via the shared (windows XP box). I also install Unix Printer Services on the Windows XP box.

I have followed this guide (a couple of times) using the Z55 drivers but each time I get to the part of executing "./z55" i get the following. Has anyone else seen this? Seems like a missing lib... 

Any help would be great. 

dccrens@caverubuntu:/usr/lib/cups/backend$ ./z55
./z55: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Dave

---

### Post by dccrens on 2008-01-01
In doing some more investigation I found that I don't have the libstdc++.so.5 on the system but rather have ./usr/lib/libstdc++.so.6 

Not sure how to fix this...

---

### Post by dccrens on 2008-01-01
> **dccrens said:**
> In doing some more investigation I found that I don't have the libstdc++.so.5 on the system but rather have ./usr/lib/libstdc++.so.6 

Not sure how to fix this...

Problem solved. Ran across a similar issue of a missing lib on another board. It appears on KUBUNTU you have to install libstdc++5. So I ran "apt-get install libstdc++5". I then did the "/etc/rc2.d/S19cupsys restart". Now when I ran ./z55 I didn't get an error... However, I got NO output. So I went ahead and added the printer using kde and it printed the test page no problem.... Not sure why I didn't get the output from the ./z55 but everything else seems to work. :)

Dave

---

### Post by alladnsane on 2008-01-08
I've tried all this with various drivers on the z1300.  Is there anyway to get this model to work???   PLEASE

---

### Post by dccrens on 2008-01-11
> **alladnsane said:**
> I've tried all this with various drivers on the z1300.  Is there anyway to get this model to work???   PLEASE

Mine works great. I followed the guide above and except for having to install the lib mentioned everything worked ok.

---

### Post by alladnsane on 2008-01-12
> **dccrens said:**
> Mine works great. I followed the guide above and except for having to install the lib mentioned everything worked ok.

what driver did you use to get the lexmark z1300 printer to work??????

---

### Post by NoVista on 2008-01-12
I just stopped back in to say the P-707 is supported.
I used this when I had Ubuntu 7.04.

---

### Post by neorab on 2008-01-13
The directions in the OP worked for a Lexmark z705 in 7.10 flawlessly.

Thanks a mint!

---

### Post by ajcloud on 2008-01-14
1st time here !
I have a x1150 . I looked up x1150 on linuxpring,org and it said x1150 Print Trio --- I suppose it is the same since mine prints/scans/copies (3 =ing Trio) It recommended the CJLZ_600LE driver. I downloaded it and I
 followed the install proceedure on the first page, when I run ./z600 I get :
./z600: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by ./z600)
./z600: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by ./z600)

What do I have to do to get this thing to work ? 

I'm new to Linux , I have Debian 4 and U 7.10. Having my printer working is one of my very basic have-to-haves. Without it, I'll have to abandon Linux all together.

Please help,
Andy

---

### Post by bodymind on 2008-01-21
> **bodymind said:**
> There is a simple way to get lexmark x1100 series working....

go to: [http://localhost:631](http://localhost:631)

add a new printer, on the step where you have to choose the driver, browse your files and install the file in attach :popcorn:

now print all you can :cool:

i hope i help someone ;)

---

### Post by vortex2000 on 2008-01-23
Hi, Newb here, 

Ok, down to business. I have a Lexmark Z515 printer. I followed every step of Blackholesun's howto. Everything worked, however now when I go to setup my printer in the KDE Control Module, I can setup everything, but when i try to send a test page, nothing happens. It waits for a few seconds then says "halted" or "error". 

Please help. 

I have the following address for the printer that I can choose from, and I have tried both:

z600:/dev/usblp0
and
usb://Lexmark%20/510%20Series

I am running Kubuntu Fiesty 64bit. 

Thanks,

---

### Post by pliktrologos on 2008-01-23
Hello,
I have a p707 Lexmark (p700/z700 series) and I configured it excellent on Kubuntu Gutsy using
**lexmark-z700-cups-driver-1.1.1-1.i586.rpm**
and
**z700llpddk-2.0-1.i386.rpm**

I had the above two files in the same folder and run this
```
alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm
alien -t z700llpddk-2.0-1.i386.rpm
sudo tar xvzf  z700llpddk-2.0.tgz -C /
sudo tar xvzf lexmark-z700-cups-driver-1.1.1.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z700-lxz700cje-cups.ppd.gz 
cd /usr/local/z35llpddk/utility
sudo ln -s auckUS.lut bnsi1.lut
sudo /usr/lib/cups/backend/z700
sudo /usr/lib/cups/backend/z700 utilities
sudo /etc/init.d/cupsys restart
sudo /etc/rc2.d/S19cupsys restart
```
I check whether the printer backend works
```
cd /usr/lib/cups/backend
./z600
```
I got no output so I added this to the **/etc/fstab** file:
```

usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
```
And run this
```
sudo mount usbfs
```
Finally I added the printer to my Kubuntu:
System Settings -> Printer -> Add -> Add Printer/Class

---

### Post by vortex2000 on 2008-01-23
I figured out kind of what my problem was. After checking:

/var/log/cups/error_log:

I noticed that I had to reseat the printer cartridges. After doing this, it did print a test page. However after the inital test page, nothing else would print. When I try to print something, it pops up in the queue and states that here is an error, but there are no error's in the error_log. A tail of /var/log/user.log reveals  the following:

Jan 23 14:43:08 Thor cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Jan 23 14:43:08 Thor cupsd: Unable to open log file "/var/log/cups/error_log" - Permission denied
Jan 23 14:43:09 Thor cupsd: Unable to open log file "/var/log/cups/error_log" - Permission denied

Think this may be the no error problem. 

Any help is appreciated. Been trying to get this crappy printer running for 3 days now. 
Thanks.

---

### Post by divali on 2008-02-03
SUCCESS USING GUTSY. Lexmark Z517 working using black hole-sun's
method. Thanks.

---

### Post by mailbiz on 2008-02-04
> **bodymind said:**
> i hope i help someone ;)


Quote:
Originally Posted by bodymind View Post
There is a simple way to get lexmark x1100 series working....

go to: [http://localhost:631](http://localhost:631)

add a new printer, on the step where you have to choose the driver, browse your files and install the file in attach

now print all you can
i hope i help someone
Attached Files
File Type: gz 	Lexmark-Z600-lxz600cj-cups.ppd.gz (2.5 KB, 5 views)
__________________


Greetings,

I just followed this advice for a Lexmark x1170 multi function centre and it seems to be OK. 

Unfortunately I use this unit just for the scanner as the ink tubes blocked up a few years ago due to non-use. I will look for the answer on this forum, too, but does any body have any ideas about getting the scanner function working?

I will post what I find.

Thanks all,

Andreas Krokene.

---

### Post by bodymind on 2008-02-10
> **mailbiz said:**
> Quote:
Originally Posted by bodymind View Post
There is a simple way to get lexmark x1100 series working....

go to: [http://localhost:631](http://localhost:631)

add a new printer, on the step where you have to choose the driver, browse your files and install the file in attach

now print all you can
i hope i help someone
Attached Files
File Type: gz 	Lexmark-Z600-lxz600cj-cups.ppd.gz (2.5 KB, 5 views)
__________________


Greetings,

I just followed this advice for a Lexmark x1170 multi function centre and it seems to be OK. 

Unfortunately I use this unit just for the scanner as the ink tubes blocked up a few years ago due to non-use. I will look for the answer on this forum, too, but does any body have any ideas about getting the scanner function working?

I will post what I find.

Thanks all,

Andreas Krokene.

i've just installed **xsane**

---

### Post by dukedome on 2008-02-12
Thank you thank you thank you for the original post!

---

### Post by oonincx on 2008-02-12
i have the lexmark dx7450 all in one how and wich fdriver must i install

---

### Post by bodymind on 2008-02-12
> **oonincx said:**
> i have the lexmark dx7450 all in one how and wich fdriver must i install

If it is: X7350... its marked as paperweigth(u can't use in linux) in openprinting database:
[http://openprinting.org/show_printer.cgi?recnum=Lexmark-X7350](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X7350)

u can see a lexmark list of printers in here:
[http://openprinting.org/printer_list.cgi?make=Lexmark](http://openprinting.org/printer_list.cgi?make=Lexmark)

---

### Post by engcon on 2008-02-15
I bought a cheapo X1480 Lexmark at Circuit City, 29$ after discount and would like to make it work with ubuntu 7.10 anybody got any ideas?

Thanks

---

### Post by erginemr on 2008-02-16
> **engcon said:**
> I bought a cheapo X1480 Lexmark at Circuit City, 29$ after discount and would like to make it work with ubuntu 7.10 anybody got any ideas?

Thanks

Then welcome to the Losers' Club. :guitar:

I also own a Lexmark (X2450) all-in-one printer, which is almost only thing that prevents me from ditching Windows, as it is reported as "paperweight" so is not supported under Linux.

I am planning to write down a petition to Lexmark customer service nowadays for a better Linux support.

---

### Post by n-alexander on 2008-02-18
> **black hole sun said:**
> 
Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.



what is the 14 here?

I have this:
>lsusb
Bus 001 Device 003: ID 0686:4004 Minolta Co., Ltd Scan Elite II
> ls /proc/bus/usb
>

Meaning it's not mounted. So xsane doesn't see it. But should I use gid=14?

Thanks,
Alex

---

### Post by dukedome on 2008-02-18
Hey,

i have a lexmark z603 and i've installed the driver. But, it dosnt print at all. When i restart the cups from terminal says:

l-desktop:~$ /etc/rc2.d/S19cupsys restart
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 4843: Operation not permitted
cupsd: Child exited with status 1!



Please, some help?

---

### Post by n-alexander on 2008-02-19
> **dukedome said:**
> Hey,

i have a lexmark z603 and i've installed the driver. But, it dosnt print at all. When i restart the cups from terminal says:

l-desktop:~$ /etc/rc2.d/S19cupsys restart
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 4843: Operation not permitted
cupsd: Child exited with status 1!



Please, some help?

is that under root?

---

### Post by dukedome on 2008-02-19
ok,

under root worked....but...my lexmark doesnt print at all! Its like ubuntu doesnt recognize the usb port...when i conect the lexmark on any usb, nothing happens! and the exmark driver is installed!

So, what can i do?

---

### Post by n-alexander on 2008-02-19
lets be a bit more specific. As root, does the printer work? If yes, it could be a USB permissions problem. It's been discussed here on the forum, will need some searching.

You should make it work under root first.

I haven't got to setting up my printer yet, still working on the scanner.

---

### Post by dukedome on 2008-02-19
thanks for help, i will search for usb permissions...

---

### Post by satkus on 2008-02-20
Just got my x1270 working....thank you.

---

### Post by pliktrologos on 2008-02-22
Is there a way to power up the printer via USB (with a command maybe?) without having to push printer's power button everytime I want to use it and power down automatically at OS shut down just like the Windows' default behavior that I have used and was really loving?

---

### Post by starminx on 2008-02-23
> **black hole sun said:**
> Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

With that said, let's get to it! :D

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```

The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.

Dear ubuntu specialist

I have tried numerous times to follow your instructions however as you can see in the included actions I seem to encounter a stumble block . Should you be able to advise me a different method I would be very pleased to hear from you
Kind regards

anna@annadesk:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory
anna@annadesk:~$  tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
anna@annadesk:~$ usbfs
bash: usbfs: command not found
anna@annadesk:~$  /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
bash: /proc/bus/usb: is a directory
anna@annadesk:~$  sudo mount usbfs
[sudo] password for anna:
mount: can't find usbfs in /etc/fstab or /etc/mtab
anna@annadesk:~$ /etc/rc2.d/S19cupsys restart
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 5057: Operation not permitted
cupsd: Child exited with status 1!
anna@annadesk:~$

---

### Post by vbman11 on 2008-03-11
I have a printer(lexmark z515) connected up to a windows xp computer   I'm networked to. Does anyone know how to connect to that?:confused:

---

### Post by n-alexander on 2008-03-12
> **starminx said:**
> Dear ubuntu specialist

anna@annadesk:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory
anna@annadesk:~$  tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
anna@annadesk:~$ usbfs
bash: usbfs: command not found
anna@annadesk:~$  /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
bash: /proc/bus/usb: is a directory
anna@annadesk:~$  sudo mount usbfs
[sudo] password for anna:
mount: can't find usbfs in /etc/fstab or /etc/mtab
anna@annadesk:~$ /etc/rc2.d/S19cupsys restart
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 5057: Operation not permitted
cupsd: Child exited with status 1!
anna@annadesk:~$

anna@annadesk:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

this means there is no file named CJLZ600LE-CUPS-1.0-1.TAR.gz in the directory you're executing these command in. Further trying to untar this nonexistent file are meaningless.

anna@annadesk:~$ usbfs
bash: usbfs: command not found

usbfs is not a command to be run in a terminal, but as stated above, the whole line shall be added to your fstab file which is located in /etc. This will mount the USB filesystem every time you boot, allowing access to USB devices.

anna@annadesk:~$  sudo mount usbfs
[sudo] password for anna:
mount: can't find usbfs in /etc/fstab or /etc/mtab

As you didn't add the usbfs line to fstab, mount can't mount the filesystem. So you can't access your USB device properly.

---

### Post by preacher2B on 2008-03-17
\\:D/
This works great!
I am running Hardy Heron 64-bit. Upgraded today from Gutsy. Using a Lexmark X1270.
Maybe one day I will be able to use the scanner, until then --- Thanks!

---

### Post by ashandla on 2008-03-27
Hi guys,

I have a Lexmark p4350. I have followed all the steps on the initial post. my problem is, no matter what I do I cannot see Z600 on the driver list of the printer installer. restarted cups using "/etc/rc2.d/S19cupsys restart" and even the entire system. Please help.

---

### Post by chicki on 2008-03-28
Thank you. Thank you black hole sun.

My Lexmark x1150 PrinTrio prints. *happy* 

Here is a helpful tip to add to the instructions to the very first post: 
-- I had to include sudo in front of both alien commands. 
-- Remember to install the following packages:

sudo apt-get install libstdc++5 alien


Thank you again. 

~chicki

---

### Post by ashvee on 2008-03-28
has anyone tried this for lex x5470 . 

is there any way we can use x5470 in ubuntu

---

### Post by MrWES on 2008-04-03
Anyone have any luck getting the X3350 to work -- damn thing is a BIG paper weight. Actually, I just have it connected to my XP laptop and shared it over the network.

Bill

---

### Post by markcgriffiths on 2008-04-05
Thanks,

It worked on my x1110.

---

### Post by ashvee on 2008-04-05
so to print in x5470 is not a near reality . hope we will have to wait for long

---

### Post by orengolan on 2008-04-05
> **illu45 said:**
> I'm having the same issue that others here have had before, although I can't seem to find any resolution. Everything seems to work fine until I try the 
```
./z600
```

I get no output from this command. I added the usbfs line to my /etc/fstab, but when I try the 
```
sudo mount usbfs
```

I get the following error:

```

mount: usbfs already mounted or /proc/bus/usb busy
mount: according to mtab, procbususb is already mounted on /proc/bus/usb

```

I had some trouble with two of my USB ports in Windows, so it may be corrupt ports, which I know another user had, but I don't know how I would fix that.

trying to print with z1420 and got the same error.
any ideas?

---

### Post by dismal_denizen on 2008-04-09
I am running Hardy Heron beta and managed to get my Z605 working simply by going through System > Preferences > Printing and adding the printer using the PPD file installed from the guide in post #1. It works just fine.

---

### Post by Ryuki_NdranC on 2008-04-10
Awesome :)

I made my Lexmark X1195 work perfectly with this howto, using Ubuntu 7.10 AMD64. All the printing options work perfect.

I only had to do an additional step, because for some reason the gnome printing tool didn't use the ppd from the driver, he used a generic one <.<

Thanks for helping the Ubuntu community.

P.S. Is there a way to make the scanner work to? How can i try if already is working?

---

### Post by raffeyg on 2008-04-15
I have my lexmark/dell printer on a network.  Outside of finding the printer and adding it (which I have done) are there any changes to the procedure on this?  I have successfully installed an HP Photosmart with no problems, I am getting much closer to being Microsoft free!

---

### Post by Gripp on 2008-04-20
it took a little tweaking but this guide worked out great for me!
i was completely at a loss until now
thanks :)

---

### Post by divali on 2008-04-20
I've used this tutorial about 4 times for my Lexmark Z517 and it worked every time on both Gutsy and Fiesty.
 Thanks.
(Although I couldn't get it to work on Debian Etch. No problem.)

---

### Post by ninjashoes on 2008-04-20
I just spent like 4 hours getting this to work then I tried your guide and it worked great. Thanks a bunch threadstarter.

I followed the guide exactly then I switched the driver to the very bottom z600 driver in Cups then it finally worked!

---

### Post by Ryuki_NdranC on 2008-04-21
for Ubuntu Hardy Heron i used this guide and i just had to change the

```
/etc/rc2.d/S19cupsys restart
```

for

```
/etc/rc2.d/S20cupsys restart
```

Hardy has a newer version i guess :)

worked for my Lexmark X1195 again :)

---

### Post by derrin on 2008-04-22
I have followed instructions here.....   everything seemed to be sweet but when I run ./z600  I get no output.

What could be causing this.

Derrin.

---

### Post by derrin on 2008-04-22
Finally got the X1270 running using these instructions but it is coming out in Black and White only.  Any ideas??

---

### Post by Ryuki_NdranC on 2008-04-22
> **derrin said:**
> I have followed instructions here.....   everything seemed to be sweet but when I run ./z600  I get no output.

What could be causing this.

Derrin.

Did you follow ALL the guide? Even the part where it says:

```
"If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:


usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.
```

In ubuntu hardy i had to change 19 for 20 in the commnad to reset the cups server :/

And at last in the printer manager i had to manually add the printer driver.

---

### Post by markcgriffiths on 2008-04-26
it worked perfect in 7.10, in 8.04, I get the following error when I type ./z600

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Any ideas?

---

### Post by se7ensamurai on 2008-04-27
I have the same trouble. This is a Z515 that i haven't used for almost a year... (this tutorial helped massivly on previous versions)

./z600 gives this output:

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I found this:
> libstdc++.so.5: cannot open shared object file: No such file or directory

Problem: An application is running on Linux 7.x which uses gcc 3.2.x. It gets one of the following error messages:

libstdc++.so.5: cannot open shared object file: No such file or directory
libgcc_s.so.1: cannot open shared object file: No such file or directory

Explanation: libstdc++.so.5 (the library for gcc 3.2.x) is installed in /usr/local/lib However, the system will only seach /usr/lib (where the 2.95.0 and other older libraries are stored).

Solution: Create symbolic links to make the libraries appear in the old folder:

```
ln -s /usr/local/lib/libstdc++.so.5 /usr/lib/libstdc++.so.5
ln -s /usr/local/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1
```
 

here: [URL="http://www.joewein.de/sw/swnotes002.htm"]http://www.joewein.de/sw/swnotes002.htm
[/URL]

tried it, and still get same output.


also tried [THIS]("http://www.ozzu.com/unix-linux-forum/libstdc-error-t54972.html")

Which give me an error about Python > cElementTree.

Anyone else have any ideas? I'm flummoxed.

---

### Post by yaaarrrgg on 2008-04-27
> **se7ensamurai said:**
> 

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


I just installed it from System -> Synaptic Package Manager 
search for libstdc++5

---

### Post by yaaarrrgg on 2008-04-27
Hmm ... these instructions have been working great for me in the past with different lexmark printers, although my Lexmark z705 is acting weird now. Everything was shifted off the page to the left, about a centimeter.  Although I finally got this printer to work using a similar approach, just different drivers. 

Not sure if it matters, but just to note my system is a fresh Hardy Heron 8.04 install ... with the exception that:
I previously installed alien
I previously installed libstdc++5
I previously turned on usbfs 

#### START BASH COMMANDS ####
### GET RPM DRIVERS FROM:

wget [http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm](http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm)
wget [http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm](http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm)

### THEN similarly, use alien to convert to tarballs.

alien -t z700llpddk-2.0-1.i386.rpm
alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm

### INSTALL TARBALLS

sudo tar -C / -xvzf z700llpddk-2.0.tgz 
sudo tar -C / -xvzf lexmark-z700-cups-driver-1.1.1.tgz 
sudo ldconfig
sudo /etc/rc2.d/S*cupsys restart

#### END BASH COMMANDS ####

THEN ADD PRINTER:

Add printer in Adminitration -> Printing.
Oddly this seemed to show up in several places ... required a bit of trial and error.

I selected "Lexmark Z700-P700 USB Printer #1" (I did NOT select the z600:/ z700:/ type urls ..)
Next, selected Lexmark
Next, selected z700 in select list

---

### Post by markcgriffiths on 2008-04-28
> **yaaarrrgg said:**
> I just installed it from System -> Synaptic Package Manager 
search for libstdc++5

Thanks, that did it.  My X1110 is working again.

---

### Post by se7ensamurai on 2008-04-29
> **markcgriffiths said:**
> Thanks, that did it.  My X1110 is working again.


NICE! that did it for me to, my little z515 is humming again. Muchas Gracias.
(OH, i'm not running a fresh install, upgraded from 7.10, but it was still S19cupsys, not 20... odd?) 


thanks to everyone on this thread!

---

### Post by the_Ben on 2008-05-01
This tutorial has helped me in the past, but after reinstalling 7.10 (I was giving 8.04 a try but decided to go back) it no longer works.  I am able to complete every command successfully except ./z600.  Here is what I'm getting in the terminal:

```
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

I'm able to set "Lexmark Z600 v1.0-1" as the printer driver, but I can't print a test page.  Nothing happens when I try to print.  Like I said, I got it to work before, so I'm not sure why it's giving me trouble this time around.  Any ideas?

EDIT: Fixed my own problem by installing libstdc++5 in Synaptic Package Manager.  Prints like a dream now!

---

### Post by ninjashoes on 2008-05-05
> **the_Ben said:**
> This tutorial has helped me in the past, but after reinstalling 7.10 (I was giving 8.04 a try but decided to go back) it no longer works.  I am able to complete every command successfully except ./z600.  Here is what I'm getting in the terminal:

```
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

I'm able to set "Lexmark Z600 v1.0-1" as the printer driver, but I can't print a test page.  Nothing happens when I try to print.  Like I said, I got it to work before, so I'm not sure why it's giving me trouble this time around.  Any ideas?

EDIT: Fixed my own problem by installing libstdc++5 in Synaptic Package Manager.  Prints like a dream now!

same thing happened to me just now when I upgraded to 8.04 and installing libstdc++5 worked for me also, glad I found this thread again

---

### Post by Jordanwb on 2008-05-05
> **se7ensamurai said:**
> NICE! that did it for me to, my little z515 is humming again.

Same for me. My Z515 works.

---

### Post by doogiekd on 2008-05-08
There are many directions for setting up this printer. I am taking part of a direction from another forum and adding some information of my own to make this a simple install. 

1. Install two items: (1) The linux library file libstdc++5. (2) File titled "alien." Ubuntu users will find this in the Synaptic Package Manager. Click System>Administration>Synaptic Package manager. 

2. Download the driver at 

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151)

3. Create a folder titled lexmark on the Desktop.

4. Move the download from above to this folder.

5. Follow these following steps. Cut and paste each command (line) in a terminal window. Make sure in terminal you are changed to look at files on the Desktop. Use "cd \Desktop" 

Code:

mkdir lexmark
mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm
sudo tar xvzf  z600llpddk-2.0.tgz -C / 
sudo tar xvzf z600cups-1.0.tgz -C / 
sudo ldconfig 
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

6. The printer driver is now installed.

7. Restart your computer.

8. Go to System>Administration>Printing.

9. Select "add new printer".

10. The driver for Z600 should now be in the selection.

11. Select the Z600 driver.

12. The printer should now be installed.

13. Change ink set to CMYK if it is not already done.

14. Ink quality "better should be selected.

15. Enjoy your working printer.

---

### Post by ZeRoNiXxX on 2008-05-09
this helped alot, thanks

---

### Post by matizs on 2008-05-11
Hi
I followed your description in details. Unfortunatelay I could not get my new printer to work with Ubuntu Hardy Eron 8.0.4.
It is a Lexmark X9575 (all-in-one, but I only want to print) and it is not directly attached to the PC but attached to a LAN.
The CUPS server shows the job as printing, but no print out is done.
The apparmor configuration looks good to me (I read another thread about a bug with cups and apparmor). Is there any additional hint or, better solution I could go for?
Thanks

---

### Post by Terri on 2008-05-15
I have an X1185, on Hardy. I had to install alien and libstdc++5. Works great Thank You

---

### Post by Lenhix on 2008-05-16
Hello guys

This is first post in UbuntuForums. Actually I registered to be able to post in this thread.
I been using Linux since the year began and have learned a lot but definitely not enough. I don't use Ubuntu, I actually use Debian with KDE but as Ubuntu is based on Debian I thought these instructions could work and, indeed, I got the Lexmark X1250 we have at work working (with Lexmark's Z605 driver; couldn't download Z600 from Lexmark's website, only Z60x so I choose the one which seemed the latest). EDIT: Black Hole Sun, you're the man! Thanks!
My question is: ¿Has been anyone able to get scanners working? I read every and each post on the 38 pages this thread has and just one guy got his X1150 scanner working. I know the X1250 isn't in the supported devices list published in the OP but if he could I'd like to be able to and I still can't get my X1250 to scan (Xine says there are not scanning devices connected). May be it's because the Z600 is only a printer, not an all-in-one so the scanner support wouldn't be included?.
Any help/ideas are really appreciated.



@ H.E. Pennypacker:
You asked black hole sun to remove some instructions and tell the other members to use the GUI because using the console made people less human like.
> It's a lot easier for newbies to understand English than messing around with all sorts of commands for the Terminal. That's why I always recommend people using the GUI as much as possible, and it also makes us Linux users more human like (the more we rely on GUI, the more human like we are).I really do no think relying on the GUI makes you more human like (or that using the console makes you less human like). It's always good to know a little bit of everything (and that doesn't makes you a know-it-all). I'm not saying that using GUI is bad, but using the console isn't bad either. And, if you ever, for whatever reason you could imagine, get to be in front of a server (with no display manager) or need to access remotely using SSH you'll need to know enough console commands to -at least- have some of the work done (if it REALLY needs a GUI, but, as far as I know, everything can be done via console in Linux).
People: Something is hard/difficult to get/do only if you think it is.

Sorry, everybody else, for not writing exclusively about the forum's main topic.

---

### Post by jwkungfu on 2008-05-22
> **black hole sun said:**
> Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

With that said, let's get to it! :D

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```

The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.


Hi there,
Here's my terminal result...

john@john-laptop:~$ mkdir lexmark
mkdir: cannot create directory `lexmark': File exists
john@john-laptop:~$ mv CJLZ600LE-CUPS-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.TAR.gz': No such file or directory
john@john-laptop:~$

:confused:

---

### Post by jjgomera on 2008-05-22
> **jwkungfu said:**
> 
john@john-laptop:~$ mkdir lexmark
mkdir: cannot create directory `lexmark': File exists

you have already a directory named "lexmark" in your home (/home/john/lexmark/

> **jwkungfu said:**
> 
john@john-laptop:~$ mv CJLZ600LE-CUPS-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.TAR.gz': No such file or directory


where have you saved this file? with this command terminal thinks this archive is in your home (/home/john), but if it's in another site, mv can't find it, you have to write his complete path (for example, if the file is in the desktop, that command would mv /home/john/Desktop/CJLZ600LE-CUPS-1.TAR.gz lexmark)

Really that step can be done easier graphically in nautilus, simply create a new directory, and save the printer driver downloaded in it


do anyone use this tutorial with lexmark z33? i have no good result :(

---

### Post by jwkungfu on 2008-05-22
Many thanks,
It's getting late here, bedtime, I need my beauty sleep!
I will tackle this later, I've found some Wiki links that might work...?

---

### Post by Jordanwb on 2008-05-23
This how to worked for my Lexmark Z515 and my Z33 jwkungfu, so you don't need the wiki links. Also one thing the writer forgot is that you need to install libstdc++5

---

### Post by Lenhix on 2008-05-23
Well, I never had to install that libstdc++5. I don't know what I installed before or if Debian (yes, I use Debian) came with it, but I got absolutely no problems when using this HOWTO.
Anyway, I gotta admit the instructions can be a little confusing but have no major problems.

---

### Post by skarootz on 2008-06-01
me sirvio , segui todos los pasos y listo,ahora mi lexmark 1195 esta funcionando, solo hay que tener en cuenta que en la ultima fase debemos navegar hasta donde se encuentra el archivo ppd.

---

### Post by jr_herman on 2008-06-04
Hello all,
My name is Herman and I'm a complete linux noob. "Hi Herman):P"

I have a LEXMARK X1185 and using the directions I can not get it to work. I am running Ubuntu 8.04. I DL'd the file to my deskstop. 

**1st Problem:**
[COLOR="Blue"]~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory[/COLOR]

So I manually moved the file to the lexmark folder created in 'home' directory.

**2nd Problem:**
[COLOR="Blue"]~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/COLOR]

So I manually extracted the file and a folder 'CJLZ600LE-CUPS-1.0-1' appeared.

**3rd Problem:**
[COLOR="Blue"]~$ tail -n +143 z600cups-1.0-1.gz.sh
tail: cannot open `z600cups-1.0-1.gz.sh' for reading: No such file or directory[/COLOR]

So I dont know what a 'tail' command is. When I manually open i get [COLOR="Blue"]"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."[/COLOR]

I am completely lost can someone help.

Thanks a bunch.

---

### Post by Peter White on 2008-06-05
Great Information that is more helpful...

---

### Post by Vince4Amy on 2008-06-07
Is it possible at all to install this Driver on 64-bit or are there any alternatives?

---

### Post by l.duesing on 2008-06-10
About Lexmark X9575.
I had a call to Lexmark this day about that. They told me, the only driver for linux is the here described one. This driver doesn't work for it.
They said, Lexmark DOES NOT support linux because of the very fast changing linux printer subsystem. We should ask the community. After asking for protocol information, I was told, there are no protocol information because of trade secrets. 
So far the calls. 
Seems we are on our own. Bad luck. Any new information is apreciated.

---

### Post by El1iP3S01D on 2008-06-25
Doogiekd, your suggestion was impecable; Because installing the driver was a breeze yet i my Debian ethc amd64 machine did not access my Lexmark x7350 All in One...Any suggesions as to how i can remedy the situation?:guitar:

---

### Post by Brian031168 on 2008-06-26
Hi

Followed all the intructions and everything seemed to go fine. I then open the printer config and select print test page, it sends it to a printer cue but nothing prints. I opened the printer applet ad it tells me i have jobs pending but nothing is coming.

Any ideas?

---

### Post by narcisgarcia on 2008-06-27
I'm trying to configure a "Dell 725" printer, which I've read is a "Lexmark z615" rebranded by Dell.

In a Xubuntu GNU/Linux 8.04 (Hardy Heron) I had to install these packages to follow 'black hole sun' procedure: alien libstdc++5

I had also to replace the command:
/etc/rc2.d/S19cupsys restart
to:
sudo /etc/init.d/cupsys restart

My problem is that when I run the "./z600" in /usr/lib/cups/backend directory I haven't any answer anytime.
The new "z600" driver can be selected when configuring the printer in the "system-config-printer" (version 0.7.81), but the printer remains silent when send a test page.

---

### Post by jemvyc on 2008-06-28
I found a post which says I can use the lexmark z55 driver.  I got the tar file and tried to run it.  The lexmark instructions say to run the following and I get an error.  I don't understand  Can anybody tell me where to look next/
jim@Acer-Hardy:~/Desktop$ sh lexmarkz55-CUPS-1.0-1.gz.sh
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 2713560553 2366800349
jim@Acer-Hardy:~/Desktop$ 


Thanks

Jim

---

### Post by badboyrh on 2008-07-08
I have a Lexmark Z715 printer and am using Ubuntu 8.04 and I am unable to go further than creating a 'lexmark' directory. After downloading the tar.gz file I am unable to use it as I get a response saying the file doesn't exist. What do you recommend?

---

### Post by jqball2u on 2008-07-17
> **jr_herman said:**
> Hello all,
My name is Herman and I'm a complete linux noob. "Hi Herman):P"

I have a LEXMARK X1185 and using the directions I can not get it to work. I am running Ubuntu 8.04. I DL'd the file to my deskstop. 

**1st Problem:**
[COLOR=Blue]~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory[/COLOR]

So I manually moved the file to the lexmark folder created in 'home' directory.

**2nd Problem:**
[COLOR=Blue]~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/COLOR]

So I manually extracted the file and a folder 'CJLZ600LE-CUPS-1.0-1' appeared.

**3rd Problem:**
[COLOR=Blue]~$ tail -n +143 z600cups-1.0-1.gz.sh
tail: cannot open `z600cups-1.0-1.gz.sh' for reading: No such file or directory[/COLOR]

So I dont know what a 'tail' command is. When I manually open i get [COLOR=Blue]"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."[/COLOR]

I am completely lost can someone help.

Thanks a bunch.



Try doing the above in either a root terminal or use su:

example:

```
user@localhost ~] # su root
Password: (enter root password here...you won't see what you typed)
[root@localhost root] $ (here you can type the commands from your post, you 
                         _should_ be able to do them now...)
```i.e.```
[root@localhost root] $  mkdir lexmark
[root@localhost root] $  mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark 
[root@localhost root] $   tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
[root@localhost root] $  tail -n +143 z600cups-1.0-1.gz.sh
[root@localhost root] $  tar -xvzf install.tar.gz
[root@localhost root] $  alien -t z600cups-1.0-1.i386.rpm
[root@localhost root] $  alien -t z600llpddk-2.0-1.i386.rpm
[root@localhost root] $  tar xvzf  z600llpddk-2.0.tgz -C /
[root@localhost root] $  tar xvzf z600cups-1.0.tgz -C /
[root@localhost root] $   ldconfig
[root@localhost root] $  cd /usr/share/cups/model
[root@localhost root] $  gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
```If you get an error for the alien part of it, do an urpmi for it

```
[root@localhost root] $  urpmi alien
```Hope this helps?:confused:

QBall:popcorn:

---

### Post by jjgomera on 2008-07-17
> **jr_herman said:**
> DL'd the file to my **deskstop**. 

**1st Problem:**
[COLOR=Blue]**~$** mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory[/COLOR]

your problem is same that 5 post above, if you download file to desktop, you terminal must be work in desktop, so do before:
~$ cd Desktop
~/Desktop$ 

or write complete path of file

[COLOR=Blue]**~$** mv /home/<user>/Desktop/CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark[/COLOR]

---

### Post by Lenhix on 2008-07-17
> **jqball2u said:**
> 
Try doing the above in either a root terminal or use su example:
[code] user@localhost ~] # su root
Password: (enter root password here...you won't see what you typed)
[root@localhost root] $ (here you can type the commands from your post...)


I don't think this would work, as many have said, you need to be in the Desktop folder of the user, not in the root user folder (/root/) (notice that that's not the root folder which is located at / )

---

### Post by Mahinva on 2008-07-19
By following the guide, I get stuck similar to jr_herman. Hopefully the way I explain the problem makes sense.

_$ mkdir lexmark_

    This works fine; the directory is created.

_$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark _

     I had to change this line to the one below, since file was on Desktop.

_$ mv /home/<USER>/Desktop/CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark_

    This works fine; the TAR.gz is put into the "lexmark" folder.

_$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz_

    This returns the following error:

tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Do I need to modify that last terminal command? I think I am in the same boat as Herman - we downloaded the file to the desktop, we're both new to Linux and unfamiliar with Terminal. Would I have any success trying to install the file without going through the Terminal? I'd rather type a few Terminal commands and have everything work, but right now, I am stumped.

---

### Post by daevyd on 2008-07-20
I'm getting VERY frustrated and p.O.ed!!  I'm about to throw Ubuntu out the door and never look back.  I'm about to throw my ENTIRE PC out the door and move to Alaska and EAT SOME POISONOUS PLANT LIKE THAT MCCANDLESS IDIOT DID!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  I CANNOT get ANY printer to work on this GODFORSAKEN POS.  HELP ME, PLEASE!!!!!!!!!!!!!!  This is the only thing keeping me from installing Ubuntu permanently on a separate partition.  I homeschool my son and I HAVE GOT to have a printer.

---

### Post by jjgomera on 2008-07-20
> **Mahinva said:**
> 
    This works fine; the TAR.gz is put into the "lexmark" folder.

_$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz_

    This returns the following error:

tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Do I need to modify that last terminal command? I think I am in the same boat as Herman - we downloaded the file to the desktop, we're both new to Linux and unfamiliar with Terminal. Would I have any success trying to install the file without going through the Terminal? I'd rather type a few Terminal commands and have everything work, but right now, I am stumped.

Really, this guide is incomplete, or not for noobs.

Now is same error again, if you have moved driver file to lexmark directory, your file is not in environment of terminal

you must do before:
~$ cd lexmark
~/lexmank$

---

### Post by Mahinva on 2008-07-20
daevyd, nobody can help you if you don't explain what problems you're running into. Take a deep breath and post your problem. Wait to see what someone says - I've been waiting for my reply, and I'm going to keep waiting since that's the only choice I have.

If you are that frustrated, you should look into an alternative option to printing, just in case you can't get your printer working in Ubuntu before your son's schooling starts. Going to a library or having your son go to a friend's house may be an option.

I wish you the best of luck.

---

### Post by Mahinva on 2008-07-20
> **jjgomera said:**
> Really, this guide is incomplete, or not for noobs.

Now is same error again, if you have moved driver file to lexmark directory, your file is not in environment of terminal

you must do before:
~$ cd lexmark
~/lexmank$

I wish I could afford to by a printer that is compatible with Linux without any configuring, but I cannot afford it. Thank you for your patience with me.

I made some progress, but now I get confused on the following:

```
Add this to your /etc/fstab file:

usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

```

My problem is that I do not know what to type into terminal to open up the fstab file. As a learning experience, I opened up the file in text editor and pasted the line of text, but I am not allowed to save the file. So, I need to do this via Terminal.

I tried _~$ cd /etc_ and I can get into the folder, however I do not know how to open up the fstab file through Terminal or how to add the required line into the fstab file.

---

### Post by jjgomera on 2008-07-20
you can do it:

sudo nautilus

and navigate to folder to open the file, you will can save changes in files

or:

sudo gedit /etc/fstab

---

### Post by daevyd on 2008-07-20
I'm getting error messages telling me these files already exist.  By the way my version of Ubuntu is installed INSIDE Windows if that matters at all.

---

### Post by daevyd on 2008-07-20
I got it to work!!!!!!!!!!!!!!  Check it out at [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)  followed it to the letter and viola!!!

---

### Post by nearownkira on 2008-07-21
anyone can tell me if the instruction in the first post work for X1270 model also?

---

### Post by Mahinva on 2008-07-21
jjgomera - Thank you so much for the help! I was trying to install this driver for my Dell A920 (which is actually a Lexmark printer). I then realized that the ink for Dell A920 was too expensive, so I would not use it for printing (just scanning). I had a second printer, a Lexmark z645. This Lexmark z600 driver worked! I was surprised to see that the scanner on the Dell A920 works too. Now, I can finally uninstall Windows XP and not have to dual-boot. I just hope that when I reinstall Ubuntu, I will be able to reinstall the z600 driver without any problems.

daevyd - I am very happy your printer works!

nearownkira - Here is a useful link regarding your printer model: [http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X1270](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X1270)

This site (openprinting) told me that my own Lexmark z645 was a "paperweight", but installing the z600 driver makes my printer work. I would suggest that you try to install the z600 driver since it sounds like it will work for your printer model.

---

### Post by Izek on 2008-07-22
I have this problem:

```
ian@ian-desktop:/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart
bash: /etc/rc2.d/S19cupsys: No such file or directory
```

But the printer still installs. However, I tried printing a test page, but nothing happened. It just made noise, and nothing printed.

---

### Post by Bigpom on 2008-07-23
I have read your thread with interest and I followed everything until you mention entering code.Please give me step by step instructions of where to go to enter the code. I have only just downloaded Ubuntu8.04 and would dearly love to get rid of Windows.........Dave:lolflag:

---

### Post by cetheriel on 2008-07-24
> I have read your thread with interest and I followed everything until you mention entering code.
enter it on the terminal. it's on Applications>Accessories>Terminal.
enter a line at a time. do not enter what follows the # (it's in the code just as comment).
--
do anyone know whether the tutorial works on hardy (ubuntu 8.4.1)?

---

### Post by cetheriel on 2008-07-27
how do i delete posts?

---

### Post by cetheriel on 2008-07-27
works for lexmark z603 on 8.04.1 (should work for other printers as well)
this is how i did it, starting on home folder (defalut if you open from Applications>Accessories>Terminal

```
$ sudo apt-get install alien libstdc++5 # libstdc++5 was suggested as needed for compatibility issues
$ mkdir lexmark # creates subfolder named lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # moves the package folder lexmark
$ cd lexmark # goes to said lexmark
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extracts the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # extracts the binary portion of the script.
$ tar -xvzf install.tar.gz # extracts the contents produced by tail
$ sudo alien -t z600cups-1.0-1.i386.rpm # converts unusable rpm packages to tgz. ignore script-related warnings.
$ sudo alien -t z600llpddk-2.0-1.i386.rpm # converts unusable rpm packages to tgz. ignore script-related warnings.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extracts the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extracts the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model # changes folder where you are operating
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzips the ppd, which should _not_ be gzipped
```

i then rebooted my pc. when it booted up i open the terminal again and
```
$ cd /usr/lib/cups/backend
$ sudo ./z600
```
i returned nothing, but i guess it means something. i then rebooted again, just to make sure. then opened System>Administration>Printing.
selected Z600 Series (it _was_ there) but printing tests didn't work. so i chose offer ppd file, and looked for the one on /usr/share/cups/models and when it asked whether i wanted to keep configurations, i chose not to. tried printing test page and it worked.

---

### Post by bepcapo on 2008-07-31
this all works now thatks for positn this tutorial

---

### Post by badperson on 2008-08-10
HI,

I went through the tutorial, everything went fine until trying to mount the usbfs. 

I get this output:

```
jason@jason-desktop:/usr/lib/cups/backend$ sudo mount usbfs
mount: usbfs already mounted or /proc/bus/usb busy
mount: according to mtab, usbfs is already mounted on /proc/bus/usb

```

I added this to the /etc/fstab file:

.usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0

thanks, 
bp

---

### Post by badperson on 2008-08-10
I followed ctheriel's instructions, still no luck. 
my printer is a Dell  Photo AIO Printer 924

---

### Post by cetheriel on 2008-08-10
it *might* be because it is a tutorial for LEXMARK printers. i'm sure you will find instructions for DELL printers somewhere on this forum.

---

### Post by badperson on 2008-08-10
Hi,

thanks..I looked for that, but I was told (somewhere, in some post) that the Dell AIO printers are just rebranded lexmark's and that driver might work. 

will keep looking. 
thanks, 
bp

---

### Post by Temposs on 2008-08-11
Please try out my debian package for the lexmark z600 driver:

[http://temposs.googlepages.com/liblexz600core0.deb](http://temposs.googlepages.com/liblexz600core0.deb)

Just install it and then set your printer to be a Lexmark z600. Hopefully this will work for you.

---

### Post by querent on 2008-08-12
couple of problems:  first, don't have a 

```
/etc/rc2.d/S19cupsys
```

S20 is there, but only restarts with sudo.  normal?

also: upon typing ./z600 in the given directory I get

```
me@home:~$ /usr/lib/cups/backend/z600
/usr/lib/cups/backend/z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```


any help?

(I also lost wireless in the middle of all this...hopefully that's the router.  any ideas there?)

q

---

### Post by Temposs on 2008-08-12
querent, have you installed the libstdc++5 library? This is required for the driver to work.

---

### Post by querent on 2008-08-12
> **Temposs said:**
> querent, have you installed the libstdc++5 library? This is required for the driver to work.

just did that and all is well now.  thanks.

any thoughts on the wifi card?

(nice avatar)

q

---

### Post by querent on 2008-08-12
Ne'er mind...I'm back.  Router or ISP weirdness, I suppose.  Thanks!

---

### Post by cetheriel on 2008-08-12
```
sudo apt-get install libstdc++5
``` should do it. mine was S20 as well, and needed sudo.

---

### Post by amh4501 on 2008-08-20
> **plb said:**
> Same here, here's what I did click the install driver button and goto /usr/share/cups/model and select the z600 driver...from there everything worked for me.

thankyou so much i have been having same problem for a while with the driver not showing up and this fixed it for me thankyou again you are a life saver

---

### Post by smooth3006 on 2008-08-20
my x1270 works but i have to manually turn on the printer before trying to print something out. also it won't auto shut off when i restart ubuntu. is there a way to correct this issue ?

---

### Post by smooth3006 on 2008-08-20
> **smooth3006 said:**
> my x1270 works but i have to manually turn on the printer before trying to print something out. also it won't auto shut off when i restart ubuntu. is there a way to correct this issue ?

^ anybody ?

---

### Post by MyR on 2008-08-28
> **smooth3006 said:**
> my x1270 works but i have to manually turn on the printer before trying to print something out. also it won't auto shut off when i restart ubuntu. is there a way to correct this issue ?

use the power button.

seriously though.. file a bug report on launchpad.

peace

---

### Post by Shrikey on 2008-08-29
No go with X500n All-in-One printer thingie. 
If anyone has tips on how to enable printing with X500, please let me know.

I just wanted to print something dammit :)

**EDITed to add:** I sent an email to Lexmark Finland, requesting that they look into *nix [OpenPrinting]("http://www.linuxfoundation.org/en/OpenPrinting") and while the tech support person was sympathetic to my request, he stated that "as a Lexmark employee, he can not comment the subject [of linux printing or OpenPrinting]". He did how ever say he would forward my email to his boss. I've no real hopes, but atleast I tried.

Everyone please, send some polite mail to your local Lexmark support person and request linux drivers and that Lexmark take part in OpenPrinting. At some point, they have to respond. Personally, I can't understand why they wouldn't even try looking into OpenPrinting... or give out info for the community to support their printers.

---

### Post by smooth3006 on 2008-10-04
is there a way to get the scanner / copier functions to work with a x1270 ? also id like to know if there is a way to check ink levels ?

---

### Post by Shrikey on 2008-10-08
> **Shrikey said:**
> No go with X500n All-in-One printer thingie. 
If anyone has tips on how to enable printing with X500, please let me know.

I just wanted to print something dammit :)

**EDITed to add:** I sent an email to Lexmark Finland, requesting that they look into *nix [OpenPrinting]("http://www.linuxfoundation.org/en/OpenPrinting") and while the tech support person was sympathetic to my request, he stated that "as a Lexmark employee, he can not comment the subject [of linux printing or OpenPrinting]". He did how ever say he would forward my email to his boss. I've no real hopes, but atleast I tried.

Everyone please, send some polite mail to your local Lexmark support person and request linux drivers and that Lexmark take part in OpenPrinting. At some point, they have to respond. Personally, I can't understand why they wouldn't even try looking into OpenPrinting... or give out info for the community to support their printers.
We gave up and returned this crapheap to the seller.

After some deliberation we decided to go with HP Color LaserJet CM2320nf. We've had good experiences with HP printers and linux, despite the fact that I personally don't like their use of soft-/hardware to limit ink cartridge use. 
This was a good move, since the printer was up and running in 15 minutes after the box was opened and it took some 15 seconds for a Ubuntu laptop to install it over network and print a test page.

---

### Post by duanyang on 2008-10-16
Hi,
i use all the steps, except the 2nd step from the last (where my system has S20cupsys instead of S19cupsys):

 sudo /etc/rc2.d/S20cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

all seem fine, except when i run ./z600, i got this error: 

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared

i see libstdc++.so.6 is in my lib folder. how can i do now? 

thanks,
Dan

---

### Post by duruttye on 2008-10-17
Hello!

I just set up a lexmark z605 printer on my ubuntu pc,  it works okey, the procedure was something like in this guide. The only problem i'm having is the special characters. I would like it to print my Hungarian documents, but it leaves out two characters: **í** and **u**, yes, you're seeing it right: **u**, not úü&#369;, just a simple **u**.

Any ideas on that?

I'm using a dell inspiron 1501 and ubuntu 8.10, cause v. 8.04 didn't work out for me at all.

Thanx
take care!

---

### Post by Fatman_UK on 2008-10-18
> **duanyang said:**
> Hi,
i use all the steps, except the 2nd step from the last (where my system has S20cupsys instead of S19cupsys):

 sudo /etc/rc2.d/S20cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

all seem fine, except when i run ./z600, i got this error: 

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared

i see libstdc++.so.6 is in my lib folder. how can i do now? 

thanks,
Dan

Dan,

I had this too. Gutsy and Hardy install version 6 of the library and the driver is dynamically linked to version 5. So type this into your Terminal:

```
sudo aptitude install libstdc++5
```

That should fix it. :)

By the way, I know you fixed this already, but S19cupsys and S20cupsys are both links to /etc/init.d/cupsys. So either way this should work:

```
sudo /etc/init.d/cupsys restart
```

HtH,
Fatman

---

### Post by pnjabi4lyfe on 2008-10-19
I just recently changed from windows to ubuntu and I am trying to get my lexmark 1150 printer to work but every time I try to run the code
 tar xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz I get an error message saying
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Everything before works this line. Any ideas?:(

---

### Post by Shrikey on 2008-10-20
> **pnjabi4lyfe said:**
> tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
This line says the file CJLZ600LE-CUPS-1.0-1.TAR.gz is not present where it should be. Check to see if you actually have it in the directory you are trying to run the uncompress command from. Capital lettering matters, so use TAB to see if it would find the correct file and its name.

---

### Post by pnjabi4lyfe on 2008-10-20
> **Shrikey said:**
> This line says the file CJLZ600LE-CUPS-1.0-1.TAR.gz is not present where it should be. Check to see if you actually have it in the directory you are trying to run the uncompress command from. Capital lettering matters, so use TAB to see if it would find the correct file and its name.

Thanx I just extracted it though and just put it on my desktop.

---

### Post by Mikail Ali on 2008-10-22
> **duanyang said:**
>  

all seem fine, except when i run ./z600, i got this error: 

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared

i see libstdc++.so.6 is in my lib folder. how can i do now? 

thanks,
Dan

Have you tried sudo apt-get install libstdc++5 ?  You obviously have version 6, but I had to install the older one as well to get it working - once you've actually got the thing printing you can remove it.

---

### Post by Mikail Ali on 2008-10-22
> **Mikail Ali said:**
> Have you tried sudo apt-get install libstdc++5 ? 

Sorry - just noticed this one's been answered.  I was so pleased to get my printer working I wanted to help someone!

---

### Post by earthwarrior on 2008-10-22
Hi,

I followed all the steps 
but when I type ./z600 I get no output I mounted the USBFS and tried using sudo but still didn't get any output
I am running intrepid beta and have a dell 924 which is a re-branded lexmark 615

thanks

---

### Post by tiggsy on 2008-10-23
i found xsane worked fine with my 1200 series - not as nicely as the native lexmark but at least it works

---

### Post by tiggsy on 2008-10-23
Thanks. Printer working, although 
```
/usr/lib/cups/backend/z600
```

gives no output at all. Wasted a couple of hours trying to get that to work, before realizing printer was unplugged. Plugged it in - it works fine.

:))

---

### Post by Philip Burrell on 2008-10-25
Hi,

I am trying to work through the How To for adding Lexamrk but I cannot add the code
[I]usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
[/I] to my fstab file as I do not have permission to save it. Can anyone help please

---

### Post by the_Ben on 2008-10-26
> **Philip Burrell said:**
> Hi,

I am trying to work through the How To for adding Lexamrk but I cannot add the code
[I]usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
[/I] to my fstab file as I do not have permission to save it. Can anyone help please

When you open the fstab file, try this command.

```
sudo gedit /etc/fstab
```

Hopefully that will allow you to save it after adding the additional line.  Hope that helps!

---

### Post by MyR on 2008-10-27
> **the_Ben said:**
> When you open the fstab file, try this command.

```
sudo gedit /etc/fstab
```

Hopefully that will allow you to save it after adding the additional line.  Hope that helps!

instead, use: gksudo gedit /etc/fstab

bad things can happen when using sudo to run graphical apps.

peace

---

### Post by MasterNetra on 2008-11-15
How do i get a Lexmark X6100 working on Kubuntu 8.10 ?

---

### Post by Izek on 2008-11-15
> **MasterNetra said:**
> How do i get a Lexmark X6100 working on Kubuntu 8.10 ?

Have you tried using the Z55 driver from lexmark.com?

---

### Post by alisonjo2786 on 2008-11-16
Tell me if I'm asking this in the wrong place...

How about a Lexmark X5150?  (I searched this thread and didn't see anything on it, but if it was there and I missed it, I apologize, I'll look again.)

---

### Post by alisonjo2786 on 2008-11-16
Never mind!!  I take my question back.

(I searched "5150" instead of "x5150" -- now I see there have been posts about the x5150.  I will post again if I still have problems.  Thank you, sorry!)

---

### Post by MasterNetra on 2008-11-18
> **Izek said:**
> Have you tried using the Z55 driver from lexmark.com?

Nope but i will.

---

### Post by PooAvenger on 2008-11-18
Hey does anyone know how to get a x2500 all in one to work?

Or (for bonus points!) how to get that same printer to work over a network with Vista as the host?

So far I've got Vista hosting my x2500 all in one and it works fine (all functions work on the host machine) but on Ubuntu Hardy I can't see the printer on the network though I can get into Vista's shared files.

Anyway, if anyone can help it would be very much appreciated. Thanks!

---

### Post by MyR on 2008-11-18
> **PooAvenger said:**
> Hey does anyone know how to get a x2500 all in one to work?

Or (for bonus points!) how to get that same printer to work over a network with Vista as the host?

So far I've got Vista hosting my x2500 all in one and it works fine (all functions work on the host machine) but on Ubuntu Hardy I can't see the printer on the network though I can get into Vista's shared files.

Anyway, if anyone can help it would be very much appreciated. Thanks!
it works great as a [paperweight]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-x2500"). make sure you set up vista to *share* the printer.
peace

---

### Post by hamada_2233a on 2008-11-24
> **black hole sun said:**
> Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

With that said, let's get to it! :D

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. 

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```

The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.

thaaaaaaanks foooooooooor you

---

### Post by linux_tech on 2008-11-24
Steps to install the z23 printer can be found here-
[http://www.funnestra.org/ubuntu/intrepid/#z23](http://www.funnestra.org/ubuntu/intrepid/#z23)

---

### Post by pixarinc on 2008-11-29
I have a problem. I read in a thread from a year ago that Lexmark stopped supporting the x8350 on Linux. I was wondering if any of the older drivers work, or if I can get it working on Wine. If anyone has any other suggestions I'd be happy to hear them. Thank you.

---

### Post by hawkhock on 2008-11-30
RE:  How To.... from gentoo (2005)

This newbie is very happy to find this thread and will do my best to follow directions.  Am running Wubi Ubuntu 8.10 at present. 

???
Will installing the Z600 driver for Lexmark X1270 affect the Windows driver in any way?

Or because it is being installed on the Ubuntu partition does it work independently?

I have a Dell A920 which is in your list of tested printers.  Would I be better off using it?

Not sure I want to install a new driver and not have my printer work with WinXP.
Sr. Citizen in UT

---

### Post by MyR on 2008-12-01
> **pixarinc said:**
> I have a problem. I read in a thread from a year ago that Lexmark stopped supporting the x8350 on Linux. I was wondering if any of the older drivers work, or if I can get it working on Wine. If anyone has any other suggestions I'd be happy to hear them. Thank you.
WINE cannot be used to install drivers.
Check [http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi) for the drivers that work best for your printer.

> **hawkhock said:**
> Will installing the Z600 driver for Lexmark X1270 affect the Windows driver in any way?

Or because it is being installed on the Ubuntu partition does it work independently?

I have a Dell A920 which is in your list of tested printers.  Would I be better off using it?

Not sure I want to install a new driver and not have my printer work with WinXP.
Sr. Citizen in UT
No, the Linux drivers will not affect windows in any way.
peace

---

### Post by greca01 on 2008-12-03
Hi,

I have Ubuntu version 8.10 and I get this error when trying to restart the cups daemon:
:/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart

bash: /etc/rc2.d/S19cupsys: No such file or directory
clare@clare-laptop:/usr/share/cups/model$

Does 8.10 have a cups daemon of a different name?

Thanks in advance

---

### Post by greca01 on 2008-12-03
No probs I found the problem.  My cups is called S20cups so I had to enter this command: -

:/etc/rc2.d$ sudo /etc/rc2.d/S20cups restart

 * Restarting Common Unix Printing System: cupsd                        [ OK ]

---

### Post by hopeunseen on 2008-12-20
I know I'm gonna sound really retarted here. I have spent my whole life using Microsoft Windows and finally got sick of that crap. I have literally just started using Ubuntu and I'm loving it. I'm totally new to Linux and all the hand coding is freaking my out. I'm trying to get my Lexmark X1290 to work and this how-to threat looks great. Thanks.

Anyway here is my retarted questions - where am I supposed to be inputting the code? Is it in the Terminal programme found in the Accessories list? I seriously have no clue what I'm doing, everything else is perfectly fine, I just want to get my printer working.

Any help (once you've finished laughing!) would be really appreciated. Thanks - Dave

---

### Post by MyR on 2008-12-20
> **hopeunseen said:**
> where am I supposed to be inputting the code? Is it in the Terminal programme found in the Accessories list?
That's right ;]

also you can copy commands using ctrl+c and paste them into the terminal using ctrl+shift+v

peace

---

### Post by NoBugs! on 2008-12-30
Thanks for the info!

About the alien -t command, shouldn't that be alien -d to make easy to install/uninstall .deb files? Worked for me.

Thanks


The .deb files and instructions are here: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/29620/comments/5](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/29620/comments/5)

---

### Post by DarkReaper79 on 2009-01-02
Thank you so much for the how-to. In all the times I tried to get my dell A910 to work with linux. This is the first time in many long hours, I got it:D It only took 10 minutes and I used the Z600 drivers. =D>

---

### Post by mrqz on 2009-01-11
I have a x1100 and after the whole process i had to install libstdc5 to make it work fine.

Thank you for your help!!!

---

### Post by su2117 on 2009-01-21
Hello 
I am new to Linux and Ubuntu. I was following the document however I get an error when I tried to restart the cupsys service. 
I then proceeded to check the directory the file mentioned below does not exist 

 :/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart
 : /etc/rc2.d/S19cupsys: No such file or directory
 :/usr/share/cups/model$ cd /
 :/$ cd etc

Thanks for your help

---

### Post by MyR on 2009-01-21
> **su2117 said:**
> Hello 
I am new to Linux and Ubuntu. I was following the document however I get an error when I tried to restart the cupsys service. 
I then proceeded to check the directory the file mentioned below does not exist 

 :/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart
 : /etc/rc2.d/S19cupsys: No such file or directory
 :/usr/share/cups/model$ cd /
 :/$ cd etc

Thanks for your help
 all you have to do is find the correct name of the file (it is not the same on all systems).
first, navigate to /etc/rc2.d/ (you can use nautilus or terminal)
cd /etc/rc2.d
then, determine a list of files and pick the one you need.
ls
for example, mine is S20cupsys
then just modify the command to reflect the correct name. 
following my example: /etc/rc2.d/S20cupsys restart

sorry if this is unclear at all; just let me know if it is.

peace

---

### Post by su2117 on 2009-01-21
> **MyR said:**
> all you have to do is find the correct name of the file (it is not the same on all systems).
first, navigate to /etc/rc2.d/ (you can use nautilus or terminal)
cd /etc/rc2.d
then, determine a list of files and pick the one you need.
ls
for example, mine is S20cupsys
then just modify the command to reflect the correct name. 
following my example: /etc/rc2.d/S20cupsys restart

sorry if this is unclear at all; just let me know if it is.

peace
Hello 
thank for that tip - however now I have a new issue when I submit the following command 
./z600

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Thanks

---

### Post by runkl on 2009-01-22
in konsole type 


sudo apt-get install libstdc++5

---

### Post by dragonfixed on 2009-01-30
Looking for instructions for Lexmark p4350 in ubuntu.

---

### Post by Izek on 2009-01-30
> **dragonfixed said:**
> Looking for instructions for Lexmark p4350 in ubuntu.

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-P4350](http://openprinting.org/show_printer.cgi?recnum=Lexmark-P4350)

It's also a paperweight.

---

### Post by w9awx on 2009-02-02
OK, I know I am new to this but I can't figure out how to do all of these things you are talking about doing.  I try to add them into the termial and they keep coming up saying that the file isnt found.  I could only get the first line entered before the file not found message came up so I stopped.

Can someone post a non-computer geek version on how to do this so I can use my printer or to relieve the rest of the posters from my stupidity just send better instructions to my email?

Thanks

---

### Post by p3tris on 2009-02-05
Really Really Really thanks! No more logging to windows to print a single piece of paper! I love you! :p

---

### Post by MyR on 2009-02-05
> **w9awx said:**
> OK, I know I am new to this but I can't figure out how to do all of these things you are talking about doing.  I try to add them into the termial and they keep coming up saying that the file isnt found.  I could only get the first line entered before the file not found message came up so I stopped.
Please see my post above (#465)
If you have any further problems be more specific with your question.

peace

[Ubuntu Linux printer]("http://www.linuxaisle.com/compatible-printers")

---

### Post by rickrob on 2009-02-06
mkdir: cannot create directory `lexmark': File exists i keep getting this?downloaded the driver and put it in a folder called lexmark but seems the command doesnt work?

---

### Post by MyR on 2009-02-06
> **rickrob said:**
> mkdir: cannot create directory `lexmark': File exists i keep getting this?downloaded the driver and put it in a folder called lexmark but seems the command doesnt work?

You have already completed the first 2 steps of the tutorial, so you can:

cd lexmark

then continue with step 3....
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz

---

### Post by rickrob on 2009-02-06
What a mess this is what i got now 

ricks@ricks-desktop:~/lexmark$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by MyR on 2009-02-06
> **rickrob said:**
> tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory

That means you don't have the file (or it has a different name).

either download the file and move it to that folder, or use the actual name of it.

type ls to list the files
if the file has a different name you can use tar -xvzf C*.gz

peace

---

### Post by ansmith4 on 2009-02-08
So, I've been trying to use this method to make a Dell AIO 924 printer compatible with Ubuntu 8.10. I have been unsuccessful.

I downloaded the Z600 driver from Lexmark and followed the instructions listed earlier. I can choose the Z600 the driver option for my printer when setting up my printer, but it there is no response from my printer when attempting to print a document.

I'm relatively new to Linux, so I'm not the most fluent when it comes to the programming. Are there any other workarounds available for the Dell AIO 924 and Ubuntu 8.10? Thanks for your help.

---

### Post by MyR on 2009-02-08
I'm afraid it's a paperweight.

[http://www.openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_924_All_In_One](http://www.openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_924_All_In_One)

If you have 1GB RAM and a windows install disc you can use a virtual machine to print.

peace

---

### Post by ansmith4 on 2009-02-08
I have read it's a paperweight. Which virtual machine program would you recommend to use?

---

### Post by MyR on 2009-02-08
> **ansmith4 said:**
> I have read it's a paperweight. Which virtual machine program would you recommend to use?

virtualbox (package virtualbox-2.1)

---

### Post by ansmith4 on 2009-02-08
Okay. Thanks for your help.

---

### Post by martc on 2009-02-11
> **MyR said:**
> That means you don't have the file (or it has a different name).

either download the file and move it to that folder, or use the actual name of it.

type ls to list the files
if the file has a different name you can use tar -xvzf C*.gz

peace
martin@martin-desktop:~$ cd lexmark
martin@martin-desktop:~/lexmark$ tar -xvzfCJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
martin@martin-desktop:~/lexmark$ 

I keep getting the same message, it doesn't matter how many times i try it. I have downloaded the file four or five times now and am beginning to think something is wrong with the download side of things rather than my ignorance. Have attached screen shot showing downloaded file and terminal saying file is not there.
 Anybody got any other suggestions? please

---

### Post by MyR on 2009-02-11
> **martc said:**
> martin@martin-desktop:~$ cd lexmark
martin@martin-desktop:~/lexmark$ tar -xvzfCJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
martin@martin-desktop:~/lexmark$ 
....
Have attached screen shot showing downloaded file and terminal saying file is not there...

In the terminal you need to be in the same directory as the file you are trying to extract.  Right now you are in ~/lexmark but the file is in ~/Desktop

So first you must either:
cd ~/Desktop
to change the working directory of the terminal OR move the file to where you want it with
mv ~/Desktop/C*gz ~/lexmark

also, martin-desktop is the name of your computer, not the folder you are in.

peace

---

### Post by martc on 2009-02-11
ok sorry the screenshot is a bit misleading, I did move the package to lexmark and still got the same message, The screenshot was just to prove to myself that the files were there and not just a figment of my imagination

---

### Post by MyR on 2009-02-11
> **martc said:**
> ok sorry the screenshot is a bit misleading, I did move the package to lexmark and still got the same message, The screenshot was just to prove to myself that the files were there and not just a figment of my imagination

try this:
tar -xvzf CJ
then hit tab and enter

peace

---

### Post by martc on 2009-02-12
thanks for trying to help but it still says no such file. i think i'm going to give up on that one for now as i just got a nashua lazer printer given to me and that works fine using a hp driver so i'm not in a rush to get the lexmark running.

---

### Post by candell on 2009-02-16
Lexmark z65 on Kubuntu Intrepid (lenny/sid) or Debian (sid/experimental)

Error:
[email]root@louiscandell.com[/email]:~/z65/CJLZ65LE-CUPS-1.0-1# sh lexmarkz65-CUPS-1.0-1.gz.sh -keep
Creating directory installer
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 3618464304 3922816710

Fix:
* aptitude install tcl tcllib tk tklib alien
* cd /usr/lib && ln -s libtcl8.4.so.0 libtcl8.4.so && ln -s libtk8.4.so.0 libtk8.4.so
wget -c [www.ossh.com/linux/lexmark/CJLZ65LE-CUPS-1.0-1.TAR.GZ](www.ossh.com/linux/lexmark/CJLZ65LE-CUPS-1.0-1.TAR.GZ)
tar -zxvf CJLZ65LE-CUPS-1.0-1.TAR.GZ
cd CJLZ65LE-CUPS-1.0-1
export _POSIX2_VERSION=199209
sh lexmarkz65-CUPS-1.0-1.gz.sh -keep
cd installer
alien -d lexmarkz65-CUPS-1.0-1.i386.rpm
alien -d z65llpddk-2.0-2.i386.rpm
dpkg -i lexmarkz65-cups_1.0-2_i386.deb
dpkg -i z65llpddk_2.0-3_i386.deb
unset _POSIX2_VERSION
nano -w /etc/cups/printers.conf
###################### start of /etc/cups/printers.conf
<DefaultPrinter z65>
Info z65
Location z65
DeviceURI usb://Lexmark/Z65
#DeviceURI hal:///org/freedesktop/Hal/devices/usb_device_43d_1a_13D005003029004_if0_printer_noserial
State Idle
StateTime 1234757818
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
######################### end of /etc/cups/printers.conf
/etc/init.d/cups restart

above should work...

you can also use [http://localhost:631/admin](http://localhost:631/admin) to set up your printer through the CUPS administration web interface.

*  steps 1 / 2 might not be required, but they clear tcllib tklib errors when you `sh CJ*.sh -keep' and try to obtain the rpm's.  

export _POSIX2_VERSION="199209"

The gnu utilities normally conform to the version of POSIX that is standard for your system. To cause them to conform to a different version of POSIX, define the _POSIX2_VERSION environment variable to a value of the form yyyymm specifying the year and month the standard was adopted. Two values are currently supported for _POSIX2_VERSION: ‘199209’ stands for POSIX 1003.2-1992, and ‘200112’ stands for POSIX 1003.1-2001. For example, if you have a newer system but are running software that assumes an older version of POSIX and uses ‘sort +1’ or ‘tail +10’, you can work around any compatibility problems by setting ‘_POSIX2_VERSION=199209’ in your environment. 

Source: [http://www.gnu.org/software/coreutils/manual/html_node/Standards-conformance.html](http://www.gnu.org/software/coreutils/manual/html_node/Standards-conformance.html)

Peace,

BLouis

---

### Post by Martman60 on 2009-02-19
Thank you Black Hole Sun your How-TO for the Lexmark Z600 worked first time for me, and after many hours of trying many post on different sites I had begun to believe I wasn't going to find a solution your How-TO is very much appreciated :KS

Martman60

---

### Post by queeniebee on 2009-02-19
I had to install this driver on a friends PC and I encountered some problems which I solved and would like to document then here for future reference for any other people encountering a similar problem.

When I ran:
halimah@halimah-desktop:~$ cd /usr/lib/cups/backend
halimah@halimah-desktop:/usr/lib/cups/backend$ ./z600
direct z600:/dev/usb/lp0 "Lexmark Lexmark X1100 Series" "Lexmark Printer"
halimah@halimah-desktop:/usr/lib/cups/backend$

Which is what it should have been.

However when I sent the jobs, they went but nothing was happening with the printer although I had sent the drive to z600 from System>Administration>Printers. The printer manager suggested that perhaps the printer was not plugged in.

So when you go into the printer configuration you see the x1100 series on the side, click on it. and the following should read:

Dev URI: z600:/dev/usb/lp0

Make and Model: Lexmark Z600 v1.0-1

Set them to the default.

Originally they were set to x1100 specs which clearly did not work. Click on change and the info should come up for you to change it because that is where the collision is i.e you have a driver installed and the location of the device is not the right one, so it cannot print to the device
I apologise if it is long-winded. I hope it helps someone.

Queeniebee

PS: These instructions were so helpful!!!

---

### Post by karotka on 2009-02-20
hello, everything works with this tutorial but at the end ....

ondro@notebook:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ondro@notebook:/usr/lib/cups/backend$



can anyone help pls???

---

### Post by logan27 on 2009-02-28
> hello, everything works with this tutorial but at the end ....

ondro@notebook:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ondro@notebook:/usr/lib/cups/backend$



can anyone help pls??? 

sudo aptitude install libstdc++5

---

### Post by inearlygaveup on 2009-03-02
[QUOTE=

The driver we'll be using is the z600 one, which can be found [here](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151). Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first. [/QUOTE]

Help please I can't find the driver z600  only the Z605 does the howto work with this driver.

---

### Post by andrea88 on 2009-03-04
Hello everybody!:(


my lexmark p707 does not work. how can i use my printer with ubuntu? where do i get a driver from?

Last week i installed ubuntu on my hp notebook and i didn't have any problems with it except my printer. 

i'm absolutely new on linux, so please write your answer as if it was for a 5-year-old child!

greets :)

---

### Post by NaamanN on 2009-03-11
Ever thing works smoothly until I get to /etc/rc2.d/S19cupsys restart 
and then it breaks.

Searching rc2.d reveals S19cupsys isn't there. Any thoughts where it might have gotten lost?

Naaman

---

### Post by run1206 on 2009-03-14
> **NaamanN said:**
> Ever thing works smoothly until I get to /etc/rc2.d/S19cupsys restart 
and then it breaks.

Searching rc2.d reveals S19cupsys isn't there. Any thoughts where it might have gotten lost?

Naaman

try /etc/init.d instead...
```
sudo /etc/init.d/cups restart
```
enter your password afterwards, then linux should restart cupsys.

---

### Post by newonlinux on 2009-03-31
Hi, I had a lot of trouble with this, but finally got it working, before I saw there was more than one page to this thread:neutral:
I put all the info together (I think) to help anyone still stuck.

First check "libstdc++5" and "libstdc++6" files are installed. Go system -> administration -> synaptic package manager, 
search for libstdc, mark the two files for installation if not already installed, and click apply.

Then download Z600 linux redhat driver, save to desktop, from here:
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151)

Into terminal type these commands (without $)

```
$ cd ~/Desktop
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
$ cd ~/Desktop/lexmark
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
$ tar -xvzf install.tar.gz
```

Install "alien" program, if it is not already installed, then do:

```
$ alien -t z600cups-1.0-1.i386.rpm
$ alien -t z600llpddk-2.0-1.i386.rpm
$ sudo tar xvzf  z600llpddk-2.0.tgz -C /
$ sudo tar xvzf z600cups-1.0.tgz -C /
$ sudo ldconfig
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

```
Then in a fresh terminal do:
```

/etc/rc2.d/S19cupsys restart
```
[but if this gives you an error message type in:
```
[$ /etc/init.d/cups restart
```

then do:

```
$ cd /usr/lib/cups/backend
$ ./z600
```

If you get output "direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer" " then it is great, miss the next bracketed bit.
If you get no output, then:
```
$ sudo gedit /etc/fstab
and copy and paste to the bottom of the document the words: "usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0"
-without the quotation marks, and then in terminal do:
$ sudo mount usbfs

```
Now hopefully your driver is installed and ready,
so go system -> administration -> printing,
click New,
choose printer from list,
close the "searching for drivers" or wait for it to finish,
check the "provide ppd file"
and browse for it in /usr/share/cups/model
then follow the instructions to name the printer etc and you are done!

---

### Post by Dr.C on 2009-04-08
> **newonlinux said:**
> [I][I]Hi, I had a lot of trouble with this, but finally got it working, before I saw there was more than one page to this thread:neutral:
I put all the info together (I think) to help anyone still stuck.[/I][/I]

[B]Newonlinux:  I recently installed Ubuntu on a friend's machine and it was important that I also enable its associated LexMark 1270 printer.  Your summary instructions for installing the required  driver made it possible to do so.  Thanks so much!  ~rc
[/B]

---

### Post by Earendil1982 on 2009-04-10
Direct download link for the Z600 driver:
[http://www.downloaddelivery.com/downloads/cpd/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/downloads/cpd/CJLZ600LE-CUPS-1.0-1.TAR.gz)

---

### Post by silentrebel on 2009-04-14
**If you've done everything here and you are sure you have the right printer; but the darn thing will still not do what its manufacturers built it to do, try this:**

```
apt-get install libstdc++.so.5
```
and
```
urpmi libstd++.so.5
```
or
```
urpmi libstdc++
```

---

### Post by Please Help on 2009-04-16
Hi there!

I went to the Lexmark website to download the Z35 driver for Ubuntu (Linux), selected the Linux/Unix tab, and no OS comes up!
Is there anything else that I can do please? 

I only started using Ubuntu this year, and am only having problems installing the driver for my Lexmark Z35 Colour Jet Printer.

Any suggestions would be appreciated!

---

### Post by boobah on 2009-04-19
> **Please Help said:**
> Hi there!

I went to the Lexmark website to download the Z35 driver for Ubuntu (Linux), selected the Linux/Unix tab, and no OS comes up!
Is there anything else that I can do please? 

I only started using Ubuntu this year, and am only having problems installing the driver for my Lexmark Z35 Colour Jet Printer.

Any suggestions would be appreciated!


I had the same problem for a Z65 model. It seems Lexmark don't want to support Linux drivers anymore :-(
I'd suggest using google to search for the driver file from an archive site.
eg. [http://ftp.nluug.nl/pub/os/Linux/distr/pardusrepo/sources/](http://ftp.nluug.nl/pub/os/Linux/distr/pardusrepo/sources/) looks
to have the Z35 driver file: CJLZ35LE-CUPS-1.0-1.TAR.gz   
Download this file and follow the instructions on this forum changing
the file name references to your driver filenames.
I did this with a Z65 driver file: CJLZ65LE-CUPS-1.0-1.TAR.GZ 
and finally got a successful test page. Using this HOWTO I got it
working in about 15 mins! 
The key for my system (KUbuntu 8.10) was the /etc/fstab file update,
plus needed to install v5 of libstdc++:
sudo aptitude install libstdc++5

Unfortunately I didn't find this HOWTO first and was trying an 
install method from an older forum topic specifically for Z65 which didn't work which wasted a few hours beforehand.

---

### Post by Rob-e on 2009-04-21
**[SIZE="5"]***In Jaunty 9.04 you need to install libstdc++5 for this to work***[/SIZE]**

and I also ran ldconfig and restarted cupsys

---

### Post by MFinkel on 2009-04-23
Hi, Would you happen to have information to run a Lexmark Optra E312? Thanks, Michael.

---

### Post by monkeyslayer56 on 2009-04-29
THANK YOU SOOOO MUCH btw this still works in ubuntu 9.04 but the mounting of the usbfs and creating it didn't work and restarting cups did not work and when i had ot type the /.z600 nothing happned but it is working just had to select the driver btw the printer is a z611

---

### Post by slofish75 on 2009-04-30
> **michellembrodeur said:**
> Thanks for trying though

I have a z35 and it didn't work. It initialized and move the paper but that was it.

also the last line 
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped

couldn't do because there was no .gz at the end
but z600 showed up in the folder where it was supposed to be
and the test came out ok with
"direct z600:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer""

but no luck on my end.

thanks anyway.

Well, got the driver from lexmark for the 2650 ( I think) and got it to partially install but my computer still says the 5470 is not plugged in USB wise and I can't finish the full driver install until the USB cord is connected. Help!

---

### Post by CAPLinux on 2009-04-30
I have a Lexmark X2600 and when I was using 8.10 I downloaded the driver from Lexmark and walked though the Lexmark set up and I was done, everything worked.  Now I upgrade to 9.04 and it will not print at all.

Any and all help is greatly appreciated.  I do not want to go back to 8.10 if I don't have to but I will if that is the only solution.

---

### Post by gjl409 on 2009-04-30
I am working with Jaunty and have a lexmark x5150 and installed the z55 driver.  The printer will not print the test page, and displays the following status:  

/usr/lib/cups/filter/rasteroz55 failed

What can I do to fix this problem?  Any help is appreciated.

---

### Post by CAPLinux on 2009-05-02
Everyone, I am now able to print!!

I did not realize I was getting the "cups-mising-filter" error when I was trying to print.  I had a backup of my etc folder with my old /etc/cups/ppd folder and I copied its contents into my 9.04 cups folder and ran the command found here

[http://ubuntuforums.org/showthread.php?t=590256](http://ubuntuforums.org/showthread.php?t=590256)

Everything works perfectly now!!

---

### Post by sahyuhr on 2009-05-02
hi all ... i'm a newb and this is the last thing i've attempted after having so many issues trying to get ubuntu actually installed.... my situation now is the printer won't print and i've tried to follow the codes that have been provided in this thread. i don't know what else to do. 

i am running ubuntu 9.04 64bit and have a lexmark x7350 all-in-one printer. any help would be greatly appreciated.. i've added the printer and see it on there with the z600 driver but i get nothing when trying a test page.

---

### Post by liposuctionguide on 2009-05-04
I have a Lexmark printer.
I love my lexmark x1270. I can do everything I need.

---

### Post by winterg on 2009-05-09
I have a Dell 924 printer which might work with Lexmark drivers. I followed the startpost procedure and some procedures from other posts. I'm at this point that I'm able to create a new printer and select the pps driver(s). Everything looks OK but no printing at all. Can someone please check below if something went wrong in the process? :)
[B]
-Is it OK that I don't get output when I do this? This should be important for printer backend to find libraries:[/B]
$ sudo ldconfig
$

**-Then I tried this:**
$ /etc/rc2.d/S19cupsys restart
bash: /etc/rc2.d/S19cupsys: No such file or directory
[B]
-When I browse to the specific dir, I see this:[/B]
/etc/rc2.d$ dir
README		       S30gdm			 S89atd
S01policykit	       S50avahi-daemon		 S89cron
S10acpid	       S50cups			 S90binfmt-support
S10apmd		       S50NetworkManager	 S98usplash
S10sysklogd	       S50pulseaudio		 S99acpi-support
S11klogd	       S50rsync			 S99laptop-mode
S12dbus		       S50saned			 S99ondemand
S20apport	       S50system-tools-backends  S99rc.local
S20dkms_autoinstaller  S70bootlogs.sh		 S99rmnologin
S20hotkey-setup        S70dns-clean		 S99stop-readahead
S24hal		       S70pppd-dns
S25bluetooth	       S89anacron

**-No S19cupsys there, so I tried this: **
/etc/rc2.d$ S50cups restart
bash: S50cups: command not found

**-Then tried if backend works, but NO output again:**
/usr/lib/cups/backend$ dir
beh	   dnssd  hp	 http  lpd	 scsi	 smb   socket  z35
bluetooth  hal	  hpfax  ipp   parallel  serial  snmp  usb     z600
es@es:/usr/lib/cups/backend$ ./z35
es@es:/usr/lib/cups/backend$ ./z600
es@es:/usr/lib/cups/backend$


**_UPDATE: did more research but still doesn't work_**

**-In synaptic I installed al 'cupsys' items**

**-Some suggestions from other threads I used:**
sudo mkdir /etc/cups/interfaces/
sudo gedit /etc/cups/cupsd.config
file is empty but added:
#AuthType Basic
#AuthClass System

**-Added cupsys to the shadow group:**
sudo vi /etc/group (added cupsys manually at the end of the shadow line)

**-Restart of cupsys doesn't work, but this does:**
sudo /etc/init.d/cups stop
sudo /etc/init.d/cups start

**-I tried this to deactivate the AppArmor protection of CUPS temporarily:**
sudo aa-complain cupsd

**-Wich version of cupsys is installed:**
dpkg -l cupsys | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Naam                                       Versie                             Omschrijving
+++-==========================================
-==================================-
==================================================
ii  cupsys                                     1.3.9-17ubuntu3                    Common UNIX Printing System (transitional package)

**-I worked with CUP via GUI at [http://localhost:631](http://localhost:631)**
I can add/manage printers and assign drivers. When I check System->Administration->Printing it shows a printer (with a green V or with a red hearth) but when I try to print it says that the printer is offline.

**-I added a printer manually:** 
Via System->Administration->Printing and everything looks OK, it even says that the printer is online/connected. But nothing happens

---

### Post by quatoria on 2009-05-12
> **liposuctionguide said:**
> I have a Lexmark printer.
I love my lexmark x1270. I can do everything I need.



Thats nice for you.

I have that printer, and this HOWTO is appallingly useless, 

Either can't find directory or worse, 
While trying to use alien (had to install it) nothing happened, 

The bit that says binary literally does binary, the computers starts screeching from it's buzzer and the screen is filled with junk for a minute.

The commands requiring RPM come back as an error and I can't get beyond that as there is little point. 

Things like this that make me want to just go back to windows and all the problems it had, at least it would just print.

I don't have time to sit for three hours today just reading 52 pages of a forum on the OFF CHANCE people have corrected something to make it work. 

And between the complete lack of Java support and now this printer it is a wonder ANYONE who dabbles in computers can be bothered with this linux lark.

So 45 minutes wasted, one cup of tea drunk (can't stand coffee), and I am back at square one. Ubuntu won't print!
:confused:

Anyone that actually can do a short step by step guide without 300 comments and without confusing the situation would be appreciated, and then perhaps get it put somewhere useful instead of page 53.

Or better yet, make it into ubuntu itself so I don't have to read yet another forum.

---

### Post by Zachs Kappler on 2009-05-19
Interesting, in Ubuntu 9.04 after following only the list of instructions on page 1 I get this: ```
daniel@Egg-Carrier:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

Following more advice in the thread, I installed the v5 of the libstdc++ package which gets me: ```
daniel@Egg-Carrier:/usr/lib/cups/backend$ ./z600
daniel@Egg-Carrier:/usr/lib/cups/backend$ 

```

It prints but it says the lack of output for ./z600 means something is wrong. Oh well, it works once again after clean installing Ubuntu 9.04 from Ubuntu 8.04. Thanks guys!:p

---

### Post by ronanp on 2009-05-22
Ok newbe here for ubuntu, a lot of this thread is going way over my skill level. 

Before I start tryig to figure stuff out, has anyone actually managed to get ubuntu to work with a dell 725 printer?

If not it's a case of getting new printer or dumping ubuntu?

---

### Post by fwre01 on 2009-05-25
I googled this quickly and it would appear not,

[http://ubuntuforums.org/showthread.php?t=511115](http://ubuntuforums.org/showthread.php?t=511115)

however, keep googling, you may find something different

---

### Post by fwre01 on 2009-05-25
Ive also just spotted that the link on that other article points back to here... resulting in a never ending loop of lexmark related pain

---

### Post by pwebster25 on 2009-05-27
I had followed the howto on the Lexmark X6170 (using the z55 driver) at 
[http://ubuntuforums.org/showthread.php?t=419661]("http://ubuntuforums.org/showthread.php?t=419661") and was banging my head against the monitor, searching for solutions for my Lexmark X6150.  It worked under Intrepid but I did a complete reinstall of Jaunty and I couldn't get it to go.  It ran a blank test page and then all my test jobs just went to nowhere (the computer thought they printed but they didn't do anything).  I suddenly thought, what if I unplug the printer.  Sure enough.  I disconnected the power to the printer and then powered it back up and then my print jobs worked.

Go figure.  I hate my Lexmark printer.  It is a pain in every way.  I have to feed each individual sheet through.

---

### Post by CAPLinux on 2009-06-03
Ok, I am back, and my printer will not print at all.  I have a Lexmark x2600, and I deleted and reinstalled the driver but the driver says I need CUPS 1.2 or higher installed.

What Gives, I am using 9.04!! I am in desperate need of help here.

---

### Post by pwebster25 on 2009-06-04
You might try the open printing page for this printer [http://openprinting.org/show_printer.cgi?recnum=Lexmark-X2600_Series]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-X2600_Series")
and the lexmark site.  Openprinting recommends the lexmark-inkjet-08-driver, which it says can be downloaded from the lexmark site.  Is that the driver you are using?

---

### Post by run1206 on 2009-06-16
you can get a new printer, or if you dual boot with XP, virtualize into your XP partition with virtualBox and print that way.

---

### Post by pwebster25 on 2009-06-20
> **run1206 said:**
> you can get a new printer, or if you dual boot with XP, virtualize into your XP partition with virtualBox and print that way.

I am curious about how this would work.  
Is this right?
So, in windows, you install the printer with the regular driver.
You probably need to make the printer sharable.
You shut down windows and boot up in Ubuntu.
How do you virtualize into the windows printer?
I don't know how I would get to the shared windows printer if Windows is shut down.

---

### Post by Lenhix on 2009-06-21
Virtualization lets you run an operating system "inside" another. It's like using your hardware to run multiple operating systems simultaneously but not bootingthem all at the same time but booting into one and running the others inside. 
So, you boot up in your normal OS, open the virtualization program and start the virtual machine. In this case it'd be like this:
- You boot up into Ubuntu
- Open the virtualization program you have installed
- You start your Windows virtual machine
- You install the printer in Windows
- You share the printer in Windows
- You access the shared printer from Ubuntu and send your documents to the printer
That works and probably the driver installation process is easier than in Ubuntu BUT you have to install the virtualization program, create the virtual machine, install Windows in the virtual machine, run Windows (it uses RAM and CPU you could be using for Ubuntu, besides the resources the virtualization software uses itself), then install the driver in Windows, share the printer, configure the shared printer in Ubuntu and finally you can send the documents to the printer.
And "virtualizing into your XP partition" means that instead of creating a new machine and installing Windows you just use the Windows partition as the hard disk drive of the virtual machine (so you can use the Windows you had installed instead of configuring a new one and installing the driver and all that stuff).
So, virtualizing a Windows machine works but... the process is quite long, isn't it? And why going back to Windows when you can do that in Ubuntu? For the people who are getting started all those commands on the console can seem quite complicated, but they're not. Perhaps you will find some trouble or come up with some doubts when doing all the things written in this thread, but that's why we're here: to help.

Some popular Virtual Machine programs are VirtualBox, Qemu and VMware Server (this is not free software (as far as I know), though it's freeware, and requires a free registration in their website to send you the serial which will make VMware Server work).

---

### Post by run1206 on 2009-06-22
it does take while to virtualize since you're booting up your Windows partition; i did it because instead of switching which main OS to print from (shutdown, then restart...), i can use the printer while Linux is still mounted. some other machine might be better to just open physically in Windows to print your documents.

---

### Post by pwebster25 on 2009-06-22
One problem I typically have with my Lexmark X6150 is that it jams paper when it has something to print close to the top edge of the paper.  Usually this would be the header on a web page.  The reason, I believe, is that it stops the paper on it's way into the machine to print and then it can't keep moving it because it isn't far enough in.  I think this is generally a roller/paper feed problem but eliminating headers on my print jobs seems to fix most of the problems.  Any ideas on solving this (either the rollers themselves or a workaround in the software).

---

### Post by pwebster25 on 2009-06-22
That is an interesting idea.  So, can you then install that shared printer in Ubuntu or do you actually have to print from within the virtual windows?  I use virtualbox on my ubuntu machine to run MS Access and MS Publisher, so I am familiar with the process.  I didn't know that I could setup Virtualbox to use an actual physical partition.  I have always setup virtual drives by default.  That would save a lot of space to just let virtualbox use my real windows partition that is sitting idly.

---

### Post by ROY.G.BIV on 2009-07-02
Well crap...

I got my printer to work, but then I messed with it and now it doesn't anymore... I tried using a different driver(same one, I just tried the one that I actually downloaded rather than the one on the drop list because it only printed b&w) and now it doesn't do more than move its tray... how do I fix that? I assume that I need to uninstall a driver, but I can't find any other than the one that is installed.

---

### Post by SmasherOd on 2009-07-07
hi/ i've got a little problem. when i'm trying to do the last three steps from the first post,to install printer, i've got next:
sudo: can't open /etc/sudoers: Permission denied

Its when im trying to do:
sudo tar xvzf z600cups-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

---

### Post by darkeale on 2009-08-04
hi,

has anyone managed to get a lexmark z735 working with any of the techniques mentioned?

thanks,
Alex

---

### Post by jaymcd on 2009-08-12
has anyone got these to work for a network attached lexmark. i have an x9575 that is connected via local network.

jay

---

### Post by PGouws on 2009-08-24
When I browse through this post it seems like the z600 driver is used for locally connected printers. BUT, we use a Lexmark x502n network (x500 Series) printer in our office. This printer was bought before a couple of us started migrating to Ubuntu, only to find out afterwards that there is no driver available for this printer. I do not want to install any version of Windows again BUT we need to be able to print.

Is there anyone that can assist with this.

---

### Post by kanimambo on 2009-09-01
:guitar:

hallo Guys, i have got lexmark Z1380, i cant get it working..... it works on vista , when i need to print something  have to go back to vista. 

Any hope that this will be possibel on my Ubuntu 9.04?

i welcome any help
kanimambo

by the way kanimambo means thank u

---

### Post by jimmy_j71 on 2009-09-01
Can anyone help me with installing printing support for my Lexmark x5650? It is an AIO but all I want is printing support. I like my Ubuntu 9.04 system and I hate the thought of going back to Windows. I have tried over and over to get this to go and I've failed. Help!!!

---

### Post by Sale on 2009-09-02
It looks like Lexmark recently released a new version of their Linux driver. Here is how i got it to work on Ubuntu 9.04 Jaunty 64bit. 

Download:
[http://tinyurl.com/kou629]("http://tinyurl.com/kou629")

**Note:** You may need to instal "alien" (and possibly "tail") from Synaptic if it is not already installed on your system.

Open terminal, cd to download directory, then:

tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
sudo alien -t z600cups-1.0-1.i386.rpm
sudo alien -t z600llpddk-2.0-1.i386.rpm
sudo tar xvzf z600llpddk-2.0.tgz -C /
sudo tar xvzf z600cups-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
sudo /etc/init.d/cups restart

(Command line instructions taken from: [http://tinyurl.com/mo6qnm]("http://tinyurl.com/mo6qnm") )

Then: System->Administration->Printing->New->Printer

---

### Post by pwebster25 on 2009-09-02
That is really great news.  I'll give it a go.  I have an X6150 that runs with the previous driver but I have a new Ubuntu laptop I need to install the drivers on. We'll see how it goes.

Thanks for the tip.  Lexmark doesn't make these easy to find.  I have no idea how you ever came across it.

---

### Post by pwebster25 on 2009-09-02
> **jimmy_j71 said:**
> Can anyone help me with installing printing support for my Lexmark x5650? It is an AIO but all I want is printing support. I like my Ubuntu 9.04 system and I hate the thought of going back to Windows. I have tried over and over to get this to go and I've failed. Help!!!

Jimmy_J, Sorry I can't be more helpful.  Your X5650 isn't even listed on the openprinting.org site.  I would suggest you try the steps in the how to here, maybe with this very most recent driver.  See what you get.  Either way, post it to openprinting.org so that others will know what has been tried and whether it worked or not.  I found very little at on the web about this model on Linux but it might be just a lucky day that it might use this same driver.  Your model number is pretty close to mine and it works for me (mine is X6150).

---

### Post by pwebster25 on 2009-09-02
> **kanimambo said:**
> :guitar:

hallo Guys, i have got lexmark Z1380, i cant get it working..... it works on vista , when i need to print something  have to go back to vista. 

Any hope that this will be possibel on my Ubuntu 9.04?

i welcome any help
kanimambo

by the way kanimambo means thank u

Kanimambo,
openprinting.org doesn't have an entry for the z1380.  However, they do for the z1300 and z1310 at [http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z1310]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z1310")

I'd give it a go and post your results.  You also could try this how to on the z600 (I have no idea what your results might be.  It works for my lexmark X6150, even though my printer is nothing like the z600.  I suppose it can't be worse than what you have now, a paperweight.

---

### Post by Sale on 2009-09-02
> **pwebster25 said:**
> 
Thanks for the tip.  Lexmark doesn't make these easy to find.  I have no idea how you ever came across it.

No problem, I'm happy it helped.

BTW, I was actually looking for the old *.tar.gz file, as I somehow lost it from my HD, when I stumbled upon tis one :)

---

### Post by acornbrain on 2009-09-03
New Ubuntu user/Jaunty/Dell a920 AIO printer

I followed the instructions in post#533 by Sale exactly.

Everything *seemed* to work, but nothing prints. Jobs keep filling up in the queue, but nothing happens @ the printer end of things.

I am hoping there is a small fix I need to make here...

please help

EDIT: when I say I followed the instructions "exactly", that is not entirely true, so this may be a clue.

when I got to the end of the instructions RE: System>Administration>Printing>New>Printer

it got hung up there and I had to point it to the ppd file @ the usr/share/cups/model directory

hope that helps at all.

EDIT#2 more searching the forums, tried a couple of things...jobs still can't get from the queue to the printer. 

clue#2: brian@Hunkajunk:/usr/lib/cups/backend$ ./z600

when I type the above into terminal, I gather I am supposed to get some sort of response "Lexmark blah blah etc", but it returns nothing.

I am seriously in the weeds now.

---

### Post by Sale on 2009-09-03
> **acornbrain said:**
> 
clue#2: brian@Hunkajunk:/usr/lib/cups/backend$ ./z600


I noticed there is also a \usr\lib64\cups\backend\ directory and I have a z600 file in there too. Looks like it's the same file as in \usr\lib\cups\backend\ Maybe you could try to symlink or just copy/paste the file if you don't already have z600 in \usr\lib64\cups\backend\.

---

### Post by acornbrain on 2009-09-03
Seal, 

I don't have the directory "usr\lib64\cups\backend" in my file system.

Question: under Printer Configuration, what is the proper "Device URI"? I am connected via a usb hub.

thanks for taking time to help make sense of this.

---

### Post by jimmy_j71 on 2009-09-03
> **pwebster25 said:**
> Jimmy_J, Sorry I can't be more helpful.  Your X5650 isn't even listed on the openprinting.org site.  I would suggest you try the steps in the how to here, maybe with this very most recent driver.  See what you get.  Either way, post it to openprinting.org so that others will know what has been tried and whether it worked or not.  I found very little at on the web about this model on Linux but it might be just a lucky day that it might use this same driver.  Your model number is pretty close to mine and it works for me (mine is X6150).


Well, I switched back to Windows today... What a pain in the @ss it is working with Windows again. I have used Linux for almost 2 years but it lacks driver support for many types of peripherals. This is something that really needs to be addressed. I'll dump my windows system and come back but someone has to provide me with a fix to this. I spent 3 days trying to get my AIO to work and that was more than enough for me to say screw it. Give me the exacto steps that "Will" make my Lexmark X5650 work and I'll be back... XP is so static compared to Ubuntu...

---

### Post by jimmy_j71 on 2009-09-03
By the way, thanks for trying anyway... I'm just frustrated and embarrassed to say that I am a Windows user again... I have failed... :(

---

### Post by Sale on 2009-09-03
> **acornbrain said:**
> Seal, 

I don't have the directory "usr\lib64\cups\backend" in my file system.

Question: under Printer Configuration, what is the proper "Device URI"? I am connected via a usb hub.


I thought I saw somewhere in your message that you had a 64 bit system :) If not, then, I guess you shouldn't have a ***\lib64\*** directory.

As for the device URI, mine is like this:
usb://Lexmark%20/Z600%20Series

---

### Post by acornbrain on 2009-09-03
> **Sale said:**
> I thought I saw somewhere in your message that you had a 64 bit system :) If not, then, I guess you shouldn't have a ***\lib64\*** directory.

As for the device URI, mine is like this:
usb://Lexmark%20/Z600%20Series

naw, no 64 bit for me.

that doesn't match my URI either, but perhaps it shouldn't. I tried a couple of different URI's i copied from forums, but no change. just thought I may have been on to something there.

I'm pretty sure i'm getting fouled up in the CUPS "backend" part of the howto, but perhaps I messed something up even before that step. the closest I ever got was the status screen on the printer itself actually read "Printing..." but nothing ever happened. Jobs were in limbo "processing" in the queue until I got fed up and cancelled them.

what saddens me is, it seems like my dream of ditching windows is slowly dying (for now). Even dual-booting doesn't seem to make sense if I can't even print. (I tell you what, I'm never buying another piece of hardware unless I check the Ubuntu forums first for Linux-compatibility)

first it was the wireless adapter, but I solved that. Then I found out I'd still need to keep windows around for iTunes and AutoCAD and a couple of other programs. OK, bummer, but I could live with that. Now this dell a922/lexmark z600 fiasco.

Actualy, this leads me to another point: Every time I try to patch some bug, or use some workaround, it never hits a homerun on the first try. that's fine, I'm a stubborn sort anyway. But I'm getting worried that all these failed "strikes" in the meantime are clogging up my nice, clean Ubuntu install with downloaded scripts and packages that I don't need. I don't think I could even recall them all. I'm scared to use the computer janitor.

---

### Post by jakespet on 2009-09-06
I have installed my z600 driver but my printer still does not work. This the message I get. I no idea what I am to do from this point. Any help is greatly appreciated.
Thank you

---

### Post by jimmy_j71 on 2009-09-06
Is there anyone out there that can provide me with proper steps to get my Lexmark X5650 installed on Ubuntu 9.04??? My computer is an Intel P4 3Ghz... This Windows garbage is killing me. I haven't had to worry about spyware or viruses in almost 2 years... Someone must know something??? All I need is my AIO to work as a basic printer... Heeeeeeeeeeeeeeeeeeeeeeelp!!!

---

### Post by patek on 2009-09-09
> **roger6106 said:**
> 
> Originally Posted by black hole sun
The driver is now installed. Restart the cups daemon:
Code:

```
/etc/rc2.d/S19cupsys restart
```

I had to do that with sudo for it to work.

I have the x1170, I ran it fine on my old installation but upgraded recently and can't do it now.

1. I couldn't find the non-distro-specific driver on the page from the link, but there was one for RedHat and I tried that. I went through all the steps of the howto with no problems.

2. I don't have a /etc/rc2.d/S19cupsys - there is a /etc/rc2.d/S20cupsys though and I did```
# /etc/rc2.d/S20cupsys restart
```  instead - does that matter? Could it be because of a RH specific driver?

 I also did a ```
# /etc/init.d/cupsys restart
``` and both put out ```
 * Restarting Common Unix Printing System: cupsd                         [ OK ]
```

Everything still seemed fine, I get the correct```
 direct z600:/dev/usb/lp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"
```


3. I use xfce and the printer does not appear in the printing settings or the print dialog (there is only the print-to-pdf there).

4. I really do not understand this: ```
# /usr/lib/cups/backend/z600 options
Usage: z600 job-id user title copies options file
```
I tried using utilities or just z600 as well (in the place of options) but none helped.

Where am I going wrong? Any clues?

---

### Post by n2stc on 2009-09-13
jaunty on KDE 4.x  Z640 printer
use the code below for restarting
```

sudo /etc/rc2.d/S50cups restart 

```
If that doesn't work, do an 
```

cd /etc/rc2.d
ls

```

and substitute the cups program you have in the restart line.

Browse to [http://localhost:631/printers](http://localhost:631/printers)  (with internet browser)

Add your printer and browse to /usr/share/cups/model and select 
Lexmark-Z600-lxz600cj-cups.ppd for the driver file

---

### Post by darkeale on 2009-09-14
hi guys, i need some help. im trying this guide with a lexmark z730.

when i try the line:-

/etc/rc2.d/S19cupsys restart

i get the error:-

bash: /etc/rc2.d/S19cupsys: No such file or directory

can anyone help with this?

thanks,
alex

---

### Post by n2stc on 2009-09-14
See my post above yours.

Also see
[http://ubuntuforums.org/showthread.php?p=7115192&highlight=jaunty#post7115192](http://ubuntuforums.org/showthread.php?p=7115192&highlight=jaunty#post7115192)

---

### Post by darkeale on 2009-09-14
> **n2stc said:**
> See my post above yours.

Also see
[http://ubuntuforums.org/showthread.php?p=7115192&highlight=jaunty#post7115192](http://ubuntuforums.org/showthread.php?p=7115192&highlight=jaunty#post7115192)
sorry, i missed that. my bad.

that solved that problem, thanks.  ive set up the printer as you instructed but when i try to print the test page i get the following message in the printer properties window:-

printer state:  idle - both cartridges are invalid. please use appropriate cartridges.

i know this is incorrect because i have had the printer working in windows. 

any suggestions?

thanks,
Alex

---

### Post by doogiekd on 2009-09-19
Thank YOU NewonLinux!


I followed your instructions exactly. 

My Lexmark Z645 is working perfectly now.

doogiekd

---

### Post by rhoward on 2009-10-09
I followed the instructions on this page and even though the z600 driver is in the drivers list. it will not print. When I try to print a test page nothing happens. complete silence except for my expletives.

Does anyone have any ideas or offer me some help? 
Thanks

---

### Post by patek on 2009-10-11
> **n2stc said:**
> jaunty on KDE 4.x  Z640 printer
use the code below for restarting
```

sudo /etc/rc2.d/S50cups restart 

```
If that doesn't work, do an 
```

cd /etc/rc2.d
ls

```

and substitute the cups program you have in the restart line.

Browse to [http://localhost:631/printers](http://localhost:631/printers)  (with internet browser)

Add your printer and browse to /usr/share/cups/model and select 
Lexmark-Z600-lxz600cj-cups.ppd for the driver file
This forum hasn't got a thank you option - thank you here then. I did it a few weeks ago but hadn't got round to responding until a thread subscription email prompted me:-)

And by the way, what's the chance that quoting your post here will help rhoward? In fact, I could vaguely remember doing it on my old distro, working on a funny path in my internet browser - that's the baby:-)

Rhoward try thoroughly browsing this localhost settings page - I had to play with activating things etc. if I remember right - sorry for a vague post.

---

### Post by andy.stallwood on 2009-11-02
I had a small problem, when trying to follow this procedure in karmic, as libstdc++5 is not available in karmic (it seems to have been replaced by libstdc++6), and so I got the "	
libstdc++.so.5: cannot open shared object file: No such file or directory" error when trying to do the ./z600.

So, to solve this I installed libstdc++5 from the jaunty repository ([http://packages.ubuntu.com/jaunty/i386/libstdc++5/download]("http://packages.ubuntu.com/jaunty/i386/libstdc++5/download")) by downloading the .deb file and opening it using GDebi Package Installer. It worked a treat, and my Z615 is now happily printing away.

Cheers

Andy

---

### Post by newonlinux on 2009-11-02
Hi, I had a lot of trouble with this, but finally got it working.
I had your problem andrupop, but follow this exactly and it should fix it.

First check "libstdc++5" and "libstdc++6" files are installed. Go system -> administration -> synaptic package manager, 
search for libstdc, mark the two files for installation if not already installed, and click apply.

Then download Z600 linux redhat driver, save to desktop, from here:
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151)

Into terminal type these commands (without $)

```
$ cd ~/Desktop
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
$ cd ~/Desktop/lexmark
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
$ tar -xvzf install.tar.gz
```

Install "alien" program, if it is not already installed, then do:

```
$ alien -t z600cups-1.0-1.i386.rpm
$ alien -t z600llpddk-2.0-1.i386.rpm
$ sudo tar xvzf  z600llpddk-2.0.tgz -C /
$ sudo tar xvzf z600cups-1.0.tgz -C /
$ sudo ldconfig
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

```
Then in a fresh terminal do:
```

$/etc/rc2.d/S19cupsys restart
```
[but if this gives you an error message type in:
```
[$ /etc/init.d/cups restart
```

then do:

```
$ cd /usr/lib/cups/backend
$ ./z600
```

If you get output "direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer" " then it is great, miss the next bit.
If you get no output, then:
```
$ sudo gedit /etc/fstab
and copy and paste to the bottom of the document the words: "usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0"
-without the quotation marks, and then in terminal do:
$ sudo mount usbfs

```
Now hopefully your driver is installed and ready,
so go system -> administration -> printing,
click New,
choose printer from list,
close the "searching for drivers" or wait for it to finish,
check the "provide ppd file"
and browse for it in /usr/share/cups/model
then follow the instructions to name the printer etc and you are done!:guitar:

EDIT: Since updating to karmic...
> Hi, I've not used this for ages,
but updated to karmic and found my printer did not work.
I've managed to get it to work by deleting the printer from Administration>Printing
and starting over..

This time I had to install libstdc++5 manually as it's not on karma
from here [http://packages.debian.org/etch/libstdc++5](http://packages.debian.org/etch/libstdc++5)
and choose your architecture (if you choose the wrong one it'll tell you when you try to install after downloading) then continent

I then did the process, but this wasn't the end, as i got some error messages and could not print.

it seemed to set the wrong permissions for some files and thus i was told that filter was insecure etc

so to change the files to the correct user (of root)
type into terminal
[COLOR="Red"]sudo -s
chown root [FILE]
chgrp root [FILE][/COLOR]

and replace the word [FILE] with these files and directories:
usr/lib/cups/filter/rastertoz600
usr/lib/cups/filter
usr/lib/cups/backend/z600
usr/lib/cups/backend

and do both commands for each file, 
hope this gets your printer working!

Just reposted this all so it's altogether,
my last post seemed to help some people, so maybe this will help people with update to karmic...
newonlinux :)

---

### Post by giocarra on 2009-11-08
Hi newonlinux,
I followed your how-to and I've got my Lexmark printer printing like a charm on my KarmicKoala i386 32 Bit. 
Thanks a lot.
I repeated the same operation (two or  more time) on my KarmicKoala amd64 64 bit with no success at all.
All has gone well up to the end.
I did not receive any warning, I was not told about "cups.insecure-filter" but when I try to print the test-page I'm told " error printing test page ", no more no less.
It is very strange, after all is gone fine .
Any suggestion?
Excuse me for my bad Englis and receive my best regard.

giocarra

---

### Post by mjp29 on 2009-11-08
Will copying and pasting this into terminal do the trick?

> **black hole sun said:**
> 
```
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
```

The driver is now installed. Restart the cups daemon:```
/etc/rc2.d/S19cupsys restart
```Check whether the printer backend works;```
$ cd /usr/lib/cups/backend
$ ./z600
```The output of the above command should be _similar_ to this:
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0 
```

Then just type: sudo mount usbfs. That should fix it.


Will copying and pasting this into terminal do the trick?

---

### Post by blazemore on 2009-11-09
Am I to understand there's still no way to get 1200 series (Specifically x1270) working on 64 bit Karmic, due to the driver requiring version 5 of some library?

I've had to stick with Jaunty just because the karmic upgrade broke printing.

---

### Post by tiggsy on 2009-11-12
I'm sad, because this new update on how to fix for karmic has not fixed my problem. I've done everything, and even got the message about Lexmark 1200 series, which made me think it was all working, but it wasn't. I tried logging out and back in, but no change. I also tried a full restart, but again, no change.

---

### Post by ShadowMage on 2009-11-14
[SIZE=5][COLOR=DarkGreen]**HOWTO: Lexmark X1270 Printing on Ubuntu 9.10 (Karmic Koala)**[/COLOR][/SIZE][COLOR=DarkGreen]
[/COLOR] 
It took me a while to get this to work so I decided to put this guide together. Most of this information is already in this thread but somewhat scattered, so I decided to make a step-by-step guide for Karmic. While I did put this together I would like to give many thanks and most of the credit to all the others who posted before me in this thread since, after all, it's this thread that helped me get this to work in the first place. I obviously cannot name everyone, so I thank you all here. Within the steps below are only the thanks for things requiring changes to this guide after it was posted.

[COLOR=Red]NOTE: THIS ONLY WORKS FOR PRINTING, NOT SCANNING OR FAXING.[/COLOR]

[SIZE=3][COLOR=DarkGreen]**Part A. Download and install the dependencies of the driver**[/COLOR][/SIZE]
[SIZE=3]
[/SIZE] [SIZE=2][COLOR=DarkGreen]**Step A-1. Get libstdc++5**[/COLOR][/SIZE]

  **For 64-bit systems, you'll need to install both the 32-bit and 64-bit versions of libstdc++5...**

Please see this link (thanks giocarra) on how to do this: [[COLOR=Blue]http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000[/COLOR]]("http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000")

-

**For 32-bit systems, you can get libstdc++5 a little more easily as follows...**

Download and install **libstdc++5** from [[COLOR=Blue]http://packages.debian.org/etch/libstdc++5[/COLOR]]("http://packages.debian.org/etch/libstdc++5").
This package depends on **gcc-3.3-base** which can be downloaded from [[COLOR=Blue]http://packages.debian.org/etch/gcc-3.3-base[/COLOR]]("http://packages.debian.org/etch/gcc-3.3-base").

On those pages, select your architecture to download the correct .deb file, and install them (libstdc++5 won't install unless gcc-3.3-base is installed).

[COLOR=DarkGreen]**[SIZE=2]Step A-2. Get alien[/SIZE]**[/COLOR]

Next, install alien. This is in the repositories so you can get it from the terminal by typing
```
sudo apt-get install alien
```[COLOR=DarkGreen]**[SIZE=3]Part B. Download and install the driver[/SIZE]**[/COLOR]

[COLOR=DarkGreen]**[SIZE=2]Step B-1. Download and extract the archived driver[/SIZE]**[/COLOR]

Download and extract the archived driver for the Lexmark Z600 (this is the driver that works with Lexmark X1270 for printing). It's a driver for Red Hat, but don't worry, that's what alien is for (later).

The official download page is [[COLOR=Blue]here[/COLOR]]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151"), but I use the wget command below to make things easier. Also, note the tail command; this is important so don't try to simply extract it from the GUI. For this whole step (Step B-1), just enter the following commands in a terminal:

```
cd ~/Desktop
mkdir lexmark
cd ~/Desktop/lexmark
wget http://www.downloaddelivery.com/downloads/cpd/CJLZ600LE-CUPS-1.0-1.TAR.gz
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
```[B][SIZE=2][COLOR=DarkGreen]Step B-2. Convert the RPM files into something more useful for Ubuntu[/COLOR]
[/SIZE][/B]
Before starting this step, your terminal should still be in the lexmark folder we created. If not (maybe you closed the terminal, that's alright), run this command to go back there:
```
cd ~/Desktop/lexmark
```The files this step creates need to be owned by root (by sending the commands as root). Originally, I did this using **sudo -s** (allows you to run a bunch of commands as root) and **exit** (to exit this mode). In general, though, it's not recommended to use "sudo -s" unless you're sure you know what your doing.

I've decided to update this by using **individual sudo commands** to eliminate the possibility of someone forgetting to exit.
This is the recommended method:
```

sudo alien -t z600cups-1.0-1.i386.rpm
sudo alien -t z600llpddk-2.0-1.i386.rpm
sudo tar xvzf z600llpddk-2.0.tgz -C /
sudo tar xvzf z600cups-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

```**You can now go to Step B-3.**

For reference purposes, or for advanced users, here's the alternative "sudo -s" method since I already have it written. 
> ```
sudo -s
alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm
tar xvzf z600llpddk-2.0.tgz -C /
tar xvzf z600cups-1.0.tgz -C /
ldconfig
cd /usr/share/cups/model
gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
exit
```[COLOR=DarkGreen]**[SIZE=2]Step B-3. Restart CUPS and check the driver backend[/SIZE]**[/COLOR]

Restart CUPS:
```
sudo /etc/init.d/cups restart
```Now, check the backend of the Lexmark Z600 driver:
```
cd /usr/lib/cups/backend
./z600
```You should receive output like this:
> direct z600:/dev/usb/lp0 "Lexmark  Lexmark 1200 Series" "Lexmark Printer"If you don't receive any output, it's ok, just move on to the next step (Step B-4) to fix it.
[B]If you DID receive the output, then SKIP THE NEXT STEP (Step B-4) and move on to Part C.

[/B][COLOR=DarkGreen]**[SIZE=2]Step B-4. Fix the driver backend[/SIZE]**[/COLOR]

So, you got no output after running ./z600 in the last step? No worries.

Open up fstab
```
sudo gedit /etc/fstab
```and add this line at the end, **without** the quotes,
```
"usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0"
```then save and exit the gedit Text Editor.

Once you've added the entry above in fstab, don't forget to mount it (thanks Mr.Banana) by entering the command
```
sudo mount usbfs
```Now, run z600 again (no need to cd again if you're already there, but it's here just in case you started this step from a new terminal):
```
cd /usr/lib/cups/backend
./z600
```Hopefully, now you got the output and you can go to Part C. If you're still not getting any output, you might want to try Part C anyway and see if it works. There have been cases of everything working without getting the output here (thanks yourlonglostpal).

[COLOR=DarkGreen]**[SIZE=3]Part C. Add the printer[/SIZE]**[/COLOR]

At this point, you need to make sure your printer is properly connected to your computer. Also, turn it on if it isn't already.

Then go to **System > Administration > Printing** to open Printer configuration. In there, click on New (then select Printer if you're using the dropdown). Now it will search for printers and open up a wizard.

**Select Device**:
Select your device and click "Forward".

**Choose Driver:** 
Select the "Provide PPD file" option. Of course, now it wants to know what PPD file to use. Browse to /usr/share/cups/model/ and select Lexmark-Z600-lxz600cj-cups.ppd, then click "Forward".

**Describe Printer:**
Enter the names you want and click "Apply".

---

And now you're done! Enjoy printing :D  As a side note, once everything is working you can delete the lexmark folder that we created on the desktop.

If there are any problems in this guide, let me know and I will do my best to fix them. I hope this guide is helpful. I know it's kinda long but my goal is to be really clear on how to make this work, because I know how confusing it is to get this working.

---

### Post by giocarra on 2009-11-15
If there are any problems in this guide, let me know and I will do my best to fix them. I hope this guide is helpful. I know it's kinda long but my goal is to be really clear on how to make this work, because I know how confusing it is to get this working.

Hi ShadowMage,
tonight I saw your How-To ,many thanks for your work,and I used it.
[COLOR="SeaGreen"]First of all :  please note that I'm using UBUNTU KARMIC KOALA amd 64  64bit
[/COLOR]
All is gone fine until this point :
```
giorgio@KKamd64:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
giorgio@KKamd64:/usr/lib/cups/backend$ 

```

As you see :libstdc++ cannot open ........
But I went to select the PPD file, I found it, I selected it, and I went forward, I applied it.
Then I accepted to print the text page and I got a warning and I was told, more or less, : there is an error processing (elaborating)  the text page (see the enclosed capture, please)
What to do ?  Do you have any suggestion?

Sorry for my bad English.

Please accept my best regard,
giocarra

During this morning, looking for some suggestion, I found here :  [http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000)
the solution that solved my problem.
Now my lexmark prints like a charm.
Thanks to you and to ....him.
giocarra

---

### Post by ShadowMage on 2009-11-15
Hi giocarra,

I'm glad to see it's working now. After reading the link you posted, I think I now understand why it didn't work. It seems that on 64-bit system, you need to install both the 32-bit and 64-bit versions of libstdc++5, I'm assuming because the Z600 driver we're using here needs the 32-bit version.

Sorry you ran into difficulties, but thanks for catching this. I've now updated the guide, with a reference to (and thanks for) that link :)

---

### Post by giocarra on 2009-11-15
Hi ShadowMage,
in Italy we say " all is good what ends good ( or fine ? ) ".
It does mean that the things we do are fine, good, if at their end, them are ended good (or fine); and your and mine searches for the lexmark to work are finished with success.
Thank for your interest in this job and for the reference you did to me ;)

Have a nice day.
giocarra

and of course, sorry for my bad English.

Now I found on an American Idioms Dictionary, maybe the correct way to translate the Italian "Tutto è bene quello che finisce bene", that is "All is gone for the best, despite many things happened"
Correct?

---

### Post by Mr.Banana on 2009-11-17
> **ShadowMage said:**
> [SIZE=5][COLOR=DarkGreen][B]


Open up fstab
```
sudo gedit /etc/fstab
```and add this line at the end, **without** the quotes,
```
"usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0"
```then save and exit the gedit Text Editor.




Problem: even if I add the line, I cannot get the output to show up.

followed the guide to the letter.

---

### Post by ShadowMage on 2009-11-18
@giocarra: I understand. Awesome :)

@Mr.Banana:

Hi Mr.Banana,

I seem to have missed a command in that step, which I had in my notes but somehow was not posted in the guide (added now). You need to mount the entry that was added to fstab, like so:
```
sudo mount usbfs
```Please let me know if this gets you the output in your case when you do ./z600 from /usr/lib/cups/backend

Regards

---

### Post by w2vy on 2009-11-20
Above in Step B-4 you enable mounting of the usb device.

How does (or might) things change if I am not using the driver for a local drive but for a SAMBA mounted network drive (on *gasp* a windows machine)?
(B-4 gives no output, but adds the network printer fine)

Also in A-1 what is the proper way to install the debian packages?
(ok sudo dpkg --install package-name.deb)

Tom

---

### Post by tiggsy on 2009-11-21
A wizard called "Printing troubleshooter" suddenly opened while I was trying again to select the drivers. After it (very slowly) had finished running, I got this message: 

**Status Messages**
There are status messages associated with this queue.

The pinter's state message is: 'Filter "usb/lib/cups/filter/rastertoz600" for printer "1200_Series" not owned by root'.

Warnings are listed below:
Printer '1200_Series': 'cups-insecure-filter'.


There was another message which occurred when I tried to print a test page again inside the wizard, after turning debugging on. It was:

Stopping because the scheduler could not execute a filter.

[Apologies for any spelling mistakes. For some reason, none of these messages were selectable.]

I'm running Karmic Koala on my trusty Alienware desktop. And i feel that I'm getting close to a possible result on this issue... ?

---

### Post by ShadowMage on 2009-11-22
I've only been able to test this on Karmic myself for Lexmark X1270 using USB and on a 32-bit system, but I'd be glad to expand the guide if there are solutions for other cases (such as the link giocarra provided for libstdc++5 with 64-bit systems).

Also, if anyone ever decides to make a better guide I would not mind at all and they can of course use whatever they want from the one I posted. Since I got my X1270 to work on Karmic I decided to post that guide because I want other people's printers (and stuff) to work too so hopefully it would help some people out. But unfortunately I can't test the other scenarios myself.

With that said, I would love to help out wherever possible, but I am by no means an expert.

@w2vy: Yeah, the guide assumes the printer is being used through USB. For a network printer, I'm not sure if and how it can be setup. Perhaps there is a way to mount the network drive similar to what was done for the USB? If there is, I unfortunately don't know how. I'm also not sure if this would solve the problem because the Z600 driver itself might not work for this scenario, I'm not sure.

@tiggsy: The following gives me the feeling that some file permissions may be incorrect
> The pinter's state message is: 'Filter "usb/lib/cups/filter/rastertoz600" for printer "1200_Series" not owned by root'.Did you do Step B-2 as root? See also [[COLOR=Blue]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=49714&page=56#post8225585") in the same thread, a guide posted by newonlinux for doing this on Jaunty; it has a quote at the end about the file permissions and Karmic.

---

### Post by w2vy on 2009-11-23
> **ShadowMage said:**
> 
@w2vy: Yeah, the guide assumes the printer is being used through USB. For a network printer, I'm not sure if and how it can be setup. Perhaps there is a way to mount the network drive similar to what was done for the USB? If there is, I unfortunately don't know how. I'm also not sure if this would solve the problem because the Z600 driver itself might not work for this scenario, I'm not sure.


I edited my post... in short B-4 gives no output and the driver works fine.

---

### Post by blazemore on 2009-11-23
When I get home I will write a script to do this automatically.
Rather than manually choosing a PPD, is there a way to get the Z600 driver included in the list of Lexmark printers?
This would probably make it easier.

---

### Post by w2vy on 2009-11-23
> **blazemore said:**
> When I get home I will write a script to do this automatically.
Rather than manually choosing a PPD, is there a way to get the Z600 driver included in the list of Lexmark printers?
This would probably make it easier.

I believe this step does add the PPD to the database.
I was able to select Lexmark/Z600 and assume these steps
made that happen (AKA **B-2**)

```
cd ~/Desktop/lexmark
```Now, enter the following commands.

```
sudo -s
alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm
tar xvzf z600llpddk-2.0.tgz -C /
tar xvzf z600cups-1.0.tgz -C /
ldconfig
cd /usr/share/cups/model
gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
exit
```[COLOR=DarkGreen]**[SIZE=2]Step B-3. Restart CUPS and check the driver backend[/SIZE]**[/COLOR]

Restart CUPS:
```
sudo /etc/init.d/cups restart
```

Tom

---

### Post by blazemore on 2009-11-23
Oh right, OK.
I just assumed it wouldn't be, as the guide says to manually browse to the PPD.
Thanks.

---

### Post by ShadowMage on 2009-11-23
w2vy, are you saying your printer works even though you get no output if you run ./z600 from /usr/lib/cups/backend, or could you clarify what you mean by it gives no output but the driver works?

By the way, has anyone gotten any errors when they enter
```
sudo /etc/init.d/cups restart
```to restart CUPS? It worked for me but I've seen different ways of restarting CUPS so I wonder if it's different for certain systems.. anyone know?

---

### Post by tiggsy on 2009-11-23
Woohoo it's working!!! Thanks ShadowMage.

I had in fact done the chown/chgrp commands you pointed me to, but did them again and the printer is now functioning as well as it ever has under linux. Great stuff, thanks!

---

### Post by Kopasakis on 2009-11-26
ok i am getting an error when trying to check the file ./z600, although i may have errors before, when i execute 

```
root@kopasakis-desktop:/usr/share/cups/model# sudo -s
root@kopasakis-desktop:/usr/share/cups/model# alien -t z600cups-1.0-1.i386.rpm
File "z600cups-1.0-1.i386.rpm" not found.
root@kopasakis-desktop:/usr/share/cups/model# alien -t z600llpddk-2.0-1.i386.rpmFile "z600llpddk-2.0-1.i386.rpm" not found.
root@kopasakis-desktop:/usr/share/cups/model# tar xvzf z600llpddk-2.0.tgz -C /
tar: z600llpddk-2.0.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@kopasakis-desktop:/usr/share/cups/model# tar xvzf z600cups-1.0.tgz -C /
tar: z600cups-1.0.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@kopasakis-desktop:/usr/share/cups/model# ldconfig
root@kopasakis-desktop:/usr/share/cups/model# cd /usr/share/cups/model
root@kopasakis-desktop:/usr/share/cups/model# gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
gzip: Lexmark-Z600-lxz600cj-cups.ppd already exists; do you wish to overwrite (y or n)? y
    not overwritten
root@kopasakis-desktop:/usr/share/cups/model# exit
exit
root@kopasakis-desktop:/usr/share/cups/model# 

```

i don't know if this is right or not but i decided to continue 
i can restart cups fine but then when i check the backend i get an error 
```
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

so i go ahead and insert ```
"usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0"
``` 

in fstb

so then i insert and then get 

 ```
sudo mount usbfs
mount: usbfs already mounted or /proc/bus/usb busy
mount: according to mtab, usbfs is already mounted on /proc/bus/usb

```
and then i get no such file directory again 

when i open the folder that is mentioned in the code /usr/lib/cups/backend i see an executable titled z600 that opens with wine 

so when i go through to add the printer i get everything to go through like normal i find the pdd file and the printer is added but when i go to print nothing comes out and i get an error message saying to fix the printer

---

### Post by yourlonglostpal on 2009-11-27
At last, after several days and wearily reading every post in this thread, my X1180 is working perfectly on 9.04.  Many thanks to all concerned. You guys are all so patient, even when people are going back to Windows or posting shouty threads.  I find it both thrilling and humbling to have joined such a community.  It also taught me more about using command line than any book could have, and has given me confidence to go ahead and sort out other stuff.  Here's one who's never going back! Thanks again.

Just noticed I'm registered under Karmic.  I went back to 9.04 because I couldn't sort other problems, but I'll have another go NOW!

---

### Post by yourlonglostpal on 2009-11-28
> **ShadowMage said:**
> w2vy, are you saying your printer works even though you get no output if you run ./z600 from /usr/lib/cups/backend, or could you clarify what you mean by it gives no output but the driver works?

By the way, has anyone gotten any errors when they enter
```
sudo /etc/init.d/cups restart
```to restart CUPS? It worked for me but I've seen different ways of restarting CUPS so I wonder if it's different for certain systems.. anyone know?
ShadowMage, I got no output when I entered ./z600 from /usr/lib/cups/backend but I thought what the hell and went on with the other steps, and the printer worked perfectly.  Hope this is of help.
Al.

---

### Post by ShadowMage on 2009-12-01
@tiggsy: No problem, I'm glad to hear it's working now :)

@yourlonglostpal: I'm glad to hear your printer is working as well :) Thanks for the note about the output.

@Kopasakis:
It looks like the problem might be here.
> **Kopasakis said:**
> 
i can restart cups fine but then when i check the backend i get an error 
```
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```
Did you install libstdc++5? Are you using a 64-bit system or a 32-bit system? The Z600 driver needs the 32-bit version of libstdc++5. So if you're using a 64-bit system, you need to install both versions of libstdc++5 (32-bit and 64-bit). Or if you're using a 32-bit system, you need to install just the 32-bit version of libstdc++5. Hope this helps.

---

### Post by anotherone33 on 2009-12-02
hy guys.
I'm another victim of 9.10. Before with 9.04 I had a splendid lexmark z645 running and printing.

Now all broken, no printing at all. I tried to make it working with your guides. But till now nothing running.

./z600       gives no output.

Before trying to add usbfs to /etc/fstab when installing new printer I had usb choice, now it disappeared, only 'other' choice . 
I added usbfs in fstab and mounted it. 

I cancelled all old printers, also a pdf that with 9.04 was working (missing pdf backend ...). 
I installed new printer z645 with ppd ... and URI z600:/dev/usb/lp0  ....

I don't know what I can do to test and solve.


Any idea ?
Thanks to any helping me.
M.

---

### Post by anotherone33 on 2009-12-02
solved.

unconnecting printer

Using another printer usb hp ... installed ... working ...
I found again usb type choice when adding printer, then I add printer  with same hp choice, same usb, modifying text titles from hp to lexmark ... choosing then lexmark ppd:  /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd

printing.

the uri is now:
usb://Lexmark/640%20Series

and going in /usr/lib/cups/backend$ 
./z600
now it outputs:
direct z600:/dev/usb/lp0 "Lexmark  Lexmark 640 Series" "Lexmark Printer"

Still in place the usbfs mount in /etc/fstab  .

see you.
M.

PS: My system   xubuntu / ubuntu 9.10 /   2.6.31-15-generic / i686 GNU/Linux

PSPS: during disconnecting lexmark I forced from synaptic reinstalling some cups* packets .... blocked system ... restart ...

---

### Post by nimishprasad on 2009-12-04
I have a Lexmark X6675 and I run Karmic. I followed all the steps of the HOW TO but still cant get my printer to work. I don't get any output when I run ./z600. 

I have an amd64 and I have both libstdc++5 and libstd++6 installed.

When I tried sudo mount usbfs, i get ... 

mount: usbfs already mounted or /proc/bus/usb busy
mount: according to mtab, usbfs is already mounted on /proc/bus/usb

I have both these lines in my /etc/fstab. I believe the first one was added while i was trying to get something working in VirtualBox. Is that a problem?

none /proc/bus/usb usbfs devgid=126,devmode=664 0 0
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

Inspite of this, I went ahead and used the Z600 driver while installing the printer and fired a test print but nothing happened. The Job queue just said Processing but nothing printed.

Any help is appreciated.

Thanks,
Nimish

---

### Post by nimishprasad on 2009-12-04
Update: I now get the below when i run ./z600 under /usr/lib/cups/backend. I removed the first entry from /etc/fstab.

direct z600:/dev/usb/lp0 "Lexmark 5600-6600 Series" "Lexmark Printer"

However, when I fire a print, it still just says Processing and nothing prints. After a while the job disappears from the queue as though something printed, but nothing really did print.

Thanks,
Nimish

---

### Post by Kopasakis on 2009-12-04
well uh good news and bad news the printer has come back to life, but unfortunately it is printing only white pages, as for why it wasn't working before it was because i had accidently downloaded libstdc++5 for the amd64 processor i have an amd athlon that for some reason registers as an intel i386 but i guess this works

---

### Post by Phrost on 2009-12-05
Hey guys... looking to install a Dell A940 printer.. word around Google is that it's basically a rebranded Lexmark printer. Anyway, I'm having trouble installing it. Using Linux Mint 8.0 (32-bit GNOME edition) and it'll detect the printer but not install any drivers. I tried using some of the work-around hacks I found online but nothing has worked thus far.. anyone have any ideas? I'd really like to have one less reason to rely on Windows.

---

### Post by emnog on 2009-12-05
Thank you! Worked like a charm!

---

### Post by NoVista on 2009-12-05
> Hey guys... looking to install a Dell A940 printer.. That printer appears to be a paperweight.
[http://openprinting.org/show_printer.cgi?recnum=Dell-all_in_one_A940_printer](http://openprinting.org/show_printer.cgi?recnum=Dell-all_in_one_A940_printer)

---

### Post by Phrost on 2009-12-06
That's what I was afraid of.. thanks anyway. :(

---

### Post by Kopasakis on 2009-12-11
well not entirely a paper weight mine is a dell a920 but for some reason i was able to get it to work in 9.04 it just wont work now

---

### Post by NoVista on 2009-12-12
[http://www.openprinting.org/show_printer.cgi?recnum=Dell-all_in_one_920_printer](http://www.openprinting.org/show_printer.cgi?recnum=Dell-all_in_one_920_printer)

But it's the 940 in question, and it is a paperweight.

---

### Post by ubushtu on 2009-12-12
Hey guys, I'm trying to get my Dell 3010cn working.  I understand that, like many other Dells, this is more than likely a rebranded Lexmark.  I installed the CUPS ppd from openprinting.org and added the printer via USB with no problem.  But every time I submit a print job, the printer LCD displays "Cancelling ..." and job goes off into the ether.

Any ideas?

Granted, it *is* a low end color laser, but it still cost me a decent penny so I'd really like to get it working.

---

### Post by Kopasakis on 2009-12-14
sorry my bad kinda got excited hoping to see someone else with the same printer

---

### Post by Brewer_clan on 2009-12-17
looking to get a lexmark 2400 series to work  in kubuntu 9.10. any ideas? 
   thank you.

---

### Post by .kelp on 2009-12-22
Ok, before I start a completely new thread, here's my problem:
I have a Lexmark X1270 and it obviously doesn't work. I followed every guide and tried every solution in this thread but it still just sits there and mocks me its idling, non-working way.
At the moment I get this error message when I try ./z600: "./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory" (It was working fine (not the printer, but ./z600) before I installed version 5 of libstdc++).
And "Stopping job because the scheduler could not execute a filter" once I try to print a test page (though I already had solved this problem through chmod, but it appeared again because someone here claimed the "filter" folder had to be owned by root). And of course the "cups-insecure-filter" warning.
Please help me, it's somewhat urgent... my graduation depends on it... more or less...

---

### Post by rastiles on 2010-01-02
> **.kelp said:**
> Ok, before I start a completely new thread, here's my problem:
I have a Lexmark X1270 and it obviously doesn't work. I followed every guide and tried every solution in this thread but it still just sits there and mocks me its idling, non-working way.
At the moment I get this error message when I try ./z600: "./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory" (It was working fine (not the printer, but ./z600) before I installed version 5 of libstdc++).
And "Stopping job because the scheduler could not execute a filter" once I try to print a test page (though I already had solved this problem through chmod, but it appeared again because someone here claimed the "filter" folder had to be owned by root). And of course the "cups-insecure-filter" warning.
Please help me, it's somewhat urgent... my graduation depends on it... more or less...
Check out this link particularly part A
[http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer+karmic&page=57](http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer+karmic&page=57)

---

### Post by .kelp on 2010-01-04
I feel so stupid... I think I partly followed the guide for 64-bit users ^^;
Now I get the "direct z600:/dev/usb/lp0 "Lexmark  Lexmark 1200 Series" "Lexmark Printer"" message. Let's see if I can get it to work now.
Thank you for pushing me into the right direction :)

Hmm, "Stopping job because the scheduler could not execute a filter" and "cups-insecure-filter" still bother me...

---

### Post by rahilm on 2010-01-06
getting error
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

and since libstdc++.so.5 does not exist now and i have tried installing the latest versions

---

### Post by w2vy on 2010-01-07
> **rahilm said:**
> since libstdc++.so.5 does not exist now and i have tried installing the latest versions

Follow the instructions and install version 5, that is what is required.

I did this that too, loading the correct version fixed it

tom

---

### Post by rahilm on 2010-01-09
> **w2vy said:**
> Follow the instructions and install version 5, that is what is required.

I did this that too, loading the correct version fixed it

tom

how to do that? synaptic doesn't show version 5 anymore. Its 6 now

---

### Post by w2vy on 2010-01-09
> **rahilm said:**
> how to do that? synaptic doesn't show version 5 anymore. Its 6 now

Re-read the instructions, I believe is said something like

download c++ 5 from "here" (link supplied)

tom

---

### Post by rahilm on 2010-01-10
> **w2vy said:**
> Re-read the instructions, I believe is said something like

download c++ 5 from "here" (link supplied)

tom

phew!! i hav to go thru 60 pages now!!

---

### Post by NoVista on 2010-01-11
Shame on W2vy not going through all the pages themselves and doing it for you.
As a matter of fact, I'm surprised W2vy isn't over at your house right now doing it for you.
We do have terrible support, don't we?

---

### Post by rahilm on 2010-01-11
> **NoVista said:**
> Shame on W2vy not going through all the pages themselves and doing it for you.
As a matter of fact, I'm surprised W2vy isn't over at your house right now doing it for you.
We do have terrible support, don't we?
yes.. i agree..

---

### Post by rahilm on 2010-01-11
got it
pg 57

---

### Post by rahilm on 2010-01-11
i installed it, and getting the output fine. but when i gave command to print a test page , it gave an error saying:
Stopping because scheduler could not execute a filter

---

### Post by rahilm on 2010-01-12
> **.kelp said:**
> I feel so stupid... I think I partly followed the guide for 64-bit users ^^;
Now I get the "direct z600:/dev/usb/lp0 "Lexmark  Lexmark 1200 Series" "Lexmark Printer"" message. Let's see if I can get it to work now.
Thank you for pushing me into the right direction :)

Hmm, "Stopping job because the scheduler could not execute a filter" and "cups-insecure-filter" still bother me...

Hey .. i have the same problem.. but i just figured it out. mine is a 32-bit system but anyways..what i did was google cups-insecure-filter and got a solution
[http://ubuntuforums.org/showthread.php?t=1313291](http://ubuntuforums.org/showthread.php?t=1313291)

basically, you have to make sure that every file in /usr/lib/cups/backend  and /usr/lib/cups/filter   is owned by root

i used nautilus to sort file by owner.. find your way
and restart cups daemon after that
```
sudo /etc/init.d/cups restart
```

---

### Post by yourlonglostpal on 2010-01-13
> **ShadowMage said:**
> @tiggsy: No problem, I'm glad to hear it's working now :)

@yourlonglostpal: I'm glad to hear your printer is working as well :) Thanks for the note about the output.

@Kopasakis:
It looks like the problem might be here.

Did you install libstdc++5? Are you using a 64-bit system or a 32-bit system? The Z600 driver needs the 32-bit version of libstdc++5. So if you're using a 64-bit system, you need to install both versions of libstdc++5 (32-bit and 64-bit). Or if you're using a 32-bit system, you need to install just the 32-bit version of libstdc++5. Hope this helps.
Hi Shadowmage, I want to thank you again.  After sorting my other issues with Karmic, I followed your howto and installed the printer on that too!

---

### Post by almozavr on 2010-01-20
> **rahilm said:**
> 

basically, you have to make sure that every file in /usr/lib/cups/backend  and /usr/lib/cups/filter   is owned by root

i used nautilus to sort file by owner.. find your way
and restart cups daemon after that
```
sudo /etc/init.d/cups restart
```

That's pretty right!

In my case I've got only 1 file (rastertoz600) not owned but root, so I used 2 commands in terminal:
```
cd /usr/lib/cups/filter
sudo chown root rastertoz600
```

---

### Post by Please Help on 2010-01-20
Hi! I go to print a test page, and the message "Stopping job because the scheduler could not execute a filter" comes up, and the print job is cancelled. How can this be fixed please?

---

### Post by .kelp on 2010-01-23
> **Please Help said:**
> Hi! I go to print a test page, and the message "Stopping job because the scheduler could not execute a filter" comes up, and the print job is cancelled. How can this be fixed please?

Still got the same problem.
sudo chown root:root /usr/lib/cups/filter
sudo chown root:root /usr/lib/cups/backend
is supposed to fix that problem, but it doesn't for me.

Have an HP F2480 (my last one was apparently broken, what would explain why all of my previous attempts were futile) now but this issue persists. It works, however, in Virtualbox, so it's not that bad.

---

### Post by mihai_2468 on 2010-01-27
I have a Lexmark X1180 on Ubuntu 9.10 Karmic Koala and I followed the steps from post #[**561**]("http://ubuntuforums.org/showpost.php?p=8318091&postcount=561") .
My printer works now. I can print and scan with it. THANK YOU!!

---

### Post by Skinnybill on 2010-01-30
THANK YOU!!!
I couldnt get it to work before (my X1270) and now it prints!!! It diddnt show any output for ./z600, not on Karmic 9.10 anyway. I havent tested scanning yet, but ill post if it works :P

Also, if in doubt, when you first choose the driver, and it asks to print a test page, the first one diddnt print. It said 'processing' then the printer made a noise and it finished. i sent another test page and it printed!

once again, thank you!
Oh and please also note, on the alien commands, you might want to add sudo at the beginning and --scripts at the end, it gives a warning but it worked this time

eg sudo alien etc.rpm --scripts

---

### Post by Noreaster on 2010-01-31
[**Post #561**]("http://ubuntuforums.org/showpost.php?p=8318091&postcount=561") worked for me as well! **[COLOR="DarkOrange"]Thank you, ShadowMage, and everyone else who helped figure this out!! This totally rocks![/COLOR]** And now, my aunt and my mom and the rest of my family won't be so angry at me for replacing Windows with the marvelous excellence that is Ubuntu!

---

### Post by Timberwolf76275 on 2010-02-01
Hi
I am new to linux and took the dive on my notebook I have it up and running very easy much better than windows. My 1 question is there a complete driver set for a lexmark X1150 out there somewhere ? for the scanner & copier & printer, or am I just out of luck

---

### Post by rottweiler2 on 2010-02-02
Black hole you're the ubuntu god!!! although this help is very old, the FSTAB mount is the only way I could get my Lexmark Z645 to work. I have been messing around with all the various help forums for three days now. By the way, this fixed my broken pipe error. I'm new to Linux ubuntu 9.10. Since my wife likes windows, I had to install UBUNTU 9.10 on my 32GB usb stick. Thanks again

---

### Post by P.Forest on 2010-02-03
Still no help.

---

### Post by KIAaze on 2010-02-03
Info centralisation: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

---

### Post by deboh on 2010-02-17
thanks a lot man, i followed your explanations here and it got to a point that i thot i was totally gone off track but at the end of it all. i got my test page and did anothr print myself and my Lexmark 1250 printed for the very first time since i have started using ubuntu 3 versions ago that is since 8.10 i suppose.

thanks again

---

### Post by mooortin on 2010-02-18
Hi everybody,

I'm french and noob on linux :???:. I get Karmic 64 bits installed. And My printer is a P707, i've done the installation of the driver with
> 
**Re: HOWTO: Lexmark Printers**
         Info centralisation: [https://help.ubuntu.com/community/Ha...exmarkPrinters]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters")
and it almost  works. The printing is not well positioned on my page, too much on the left.  it's printing 2 cm too much on the left.
 and now i don't know what to do... coz i don't know where it could it be to change it.
could you help me??

one more thing when i did what Black hole sun said on the very first page, for the step: 
$ tail -n +143 ...etc... that gave me : (and it's just a preview of what i got in reality) 

|p&#65533;&#65533;&#65533;wˆ3Ø!ÎÄ‡¼È›wøåòò÷µ’U¯k>øÜ¾hÈœB¾S3Æ¿Éi¤‹ÞzúàtfQÀ9P=e    ¬§ÄuDs‘ÚBäÅÙ"öŸ¿¯þÄþÅ×Ÿ×&#65533;o&#65533;+&#65533;&&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;jm&#65533;H&#65533;&#65533;9&#65533;&#2015;&#65533;=&#65533;&#65533;&#65533;>&#65533;/&#65533;&#65533;&#65533;z&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7_&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?s&#65533;&#65533;&#65533;:&#65533;&#65533;&#65533;?g&#1007;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;>4[&#65533;&#65533;9|&#65533;&#65533;&#65533;3F&#65533;(&#65533;`&#65533;&#65533;Q0
F&#65533;(&#65533;`&#65533;&#65533;Q0
&#65533;&#65533;n&#65533;&#65533;Ymartin@martin-desktop:~/lexmark$ 62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c^C

strange and a bit spooky ...

and as you though i don't get the install.tar.gz created... maybe it's coz that tuto was made in the 60's :D (joke) and not really appropriate for 64 bits architecture. (don't know actually)

thx a lot for what you've done all of you, and thx for what you could do for me

---

### Post by KIAaze on 2010-02-18
> **mooortin said:**
> 
one more thing when i did what Black hole sun said on the very first page, for the step: 
$ tail -n +143 ...etc... that gave me : (and it's just a preview of what i got in reality) 

|p&#65533;&#65533;&#65533;wˆ3Ø!ÎÄ‡¼È›wøåòò÷µ’U¯k>øÜ¾hÈœB¾S3Æ¿Éi¤‹ÞzúàtfQÀ9P=e    ¬§ÄuDs‘ÚBäÅÙ"öŸ¿¯þÄþÅ×Ÿ×&#65533;o&#65533;+&#65533;&&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;jm&#65533;H&#65533;&#65533;9&#65533;&#2015;&#65533;=&#65533;&#65533;&#65533;>&#65533;/&#65533;&#65533;&#65533;z&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7_&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?s&#65533;&#65533;&#65533;:&#65533;&#65533;&#65533;?g&#1007;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;>4[&#65533;&#65533;9|&#65533;&#65533;&#65533;3F&#65533;(&#65533;`&#65533;&#65533;Q0
F&#65533;(&#65533;`&#65533;&#65533;Q0
&#65533;&#65533;n&#65533;&#65533;Ymartin@martin-desktop:~/lexmark$ 62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c^C

strange and a bit spooky ...
and as you though i don't get the install.tar.gz created... 

The tail command returns a certain number of lines from the end of the file.
In this case, the file ends with a tar.gz (imagine a tar.gz attached to a text file).
Since a tar.gz is a compressed file, it is not clear text.
That's why you get that result.
The idea is to redirect the output into "install.tar.gz" to create a tar.gz ("tail" only outputs data in the terminal, but does not store it in a file).

You should have run:
```
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
```

> 
maybe it's coz that tuto was made in the 60's :D (joke) and not really appropriate for 64 bits architecture. (don't know actually)


The driver is a 32-bit binary.
That's why you need to install the 32-bit versions of libstdc++5 as specified [here]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z600%20Series%20Printers"). ;)

I have no idea how to solve your printing problem unfortunately.
It might be because the driver is for the Lexmark Z6xx series and not Lexmark P707.

---

### Post by mooortin on 2010-02-20
Thanks for your answer,

you were right, i missed a part of that tuto, i think i didn't type the end > install.tar.gz #-o

but i have done everything from that page [here.]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z600%20Series%20Printers")
so it should be allright if i got a z6xx series. no??

ok so does anybody know a driver lexmark that should work for P7xx series ??

---

### Post by mooortin on 2010-02-20
> 
                                  **printing marges uncorrect**             
                                                                Hello all,

I have a problem with printing: the marges are incorrect, especially the left marge. It seems that the whole print is shifted to the left. I get this in every program I print in (OPenOffice, Gedit, Browser etc.). 

I have Lexmark P707 printer and use the Z600 CUPS driver (it is the only driver that actually works). 

Does anybody else have this problem or do you know how or where to correct this?

Help greatly appreciated!
And that was pretty much 4 years ago....... :P 
Today i got exactly the same problem !!! com'on guys tell me that someone knows how to fix it or install properly a P707 on Linux ( i got Karmic 64 bits).

cheers anyway !!

---

### Post by NoVista on 2010-02-20
Once the driver is properly installed,
go to system/administration/printing.
You will see the printer listed as Lexmark -z700-p700-series.
Right click on it, go to properties.
In the column on the left, click on "Job Options."
Most of the settings are here. 
(be sure to open up the 'More' sections, there is more than one).
For printing of text, you can set margins for all four sides, along with lines per inch, and characters per inch, pretty print, word wrap, and there is even a command box to enter other options.

---

### Post by mooortin on 2010-02-21
Great i didn't see the more option arrows the first time....
but still not enough, I've been changing the left margin and that didn't fix the problem. :(

The more option box is a cool idea, but donno which option name i have to type in the box.
How to get more option names?:P

And Nobody for another driver ?? maybe it will be better for a p707:confused::confused:

Cheers

---

### Post by KIAaze on 2010-02-21
Contact Lexmark and ask them for a driver that works (and perhaps also for a way of contacting the developers of the other driver, which might know an easy fix).

It's unlikely it will have much effect, but you've got nothing to loose by doing it.
And the more people do ask for GNU/Linux drivers, the more likely they will be made.

P.S.: Just found this via Google:
[http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)
Have you tried it already?

---

### Post by mooortin on 2010-02-22
Hi, thx that's not a bad idea at all, i'll e-mail them asap.

For the second one,
 i can't create any .deb . I donno what's going on. Alien is saying that there nothing for 64 bits architecture.

Terminal said :
> 
martin@martin-desktop:~$ cd /home/martin/Modèles/
martin@martin-desktop:~/Modèles$ alien -d lexmark-z700-cups-driver-1.1.1-1.i586.rpm 
Must run as root to convert to deb format (or you may use fakeroot).
martin@martin-desktop:~/Modèles$ sudo alien -d lexmark-z700-cups-driver-1.1.1-1.i586.rpm 
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package lexmark-z700-cups-driver: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/lexmark-z700-cups-driver
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: erreur: pas d'information de dépendance trouvée pour /usr/lib32/libstdc++.so.5 (utilisé par debian/lexmark-z700-cups-driver/usr/lib/cups/backend/z700).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: [binary-arch] Erreur 1 (ignorée)
dh_gencontrol
dpkg-gencontrol: erreur: l'actuelle architecture hôte « amd64 » n'apparaît pas dans la liste d'architecture du paquet (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Erreur 1
find: "lexmark-z700-cups-driver-1.1.1": Aucun fichier ou dossier de ce type

it's a bit in French :confused:, my bad.
What am i supposed to do in this case? Force to install in 32bits??

Third solution: i don't know what to do with those tar.gz I don't know how to compilate... sry i'm a real noob:(

---

### Post by sincerelyydavid on 2010-02-24
Okay, guys. I did everything in the instructions. Found the Z600 driver in the printer configuration. tried to print a test page, but here's what I got:
"Print Error: there was a problem printing document 'test page'(job 3): stopping because the scheduler could not execute a filter."
how do i fix this filter problem?

---

### Post by KIAaze on 2010-02-25
Try running:
```
sudo chmod +x /usr/lib/cups/backend/z600
sudo chmod +x /usr/lib/cups/filter/rastertoz600

```
Then it should work.

Otherwise, post "/var/log/cups/access_log" and "/var/log/cups/error_log" for more info on the error.

@mooortin:
It should be possible to extract the files from the .rpm files or use the tar.gz package.
I don't have time to look more into it now, but I will as soon as I can. I could probably make a debian package for it.
If you have already solved the problem, let me know.
(et sinon, pas de problème pour le Français. ;) )

---

### Post by mooortin on 2010-02-25
Thx KIAaze if you get time for it,
oh, and no problems have been solved... except for the french one :D 

How do you a make a deb package from tar.gz ? it's for 64bits architecture, and it's about CUPS....:(

I'll try find out... :P

---

### Post by sincerelyydavid on 2010-02-25
> **KIAaze said:**
> Try running:
```
sudo chmod +x /usr/lib/cups/backend/z600
sudo chmod +x /usr/lib/cups/filter/rastertoz600

```Then it should work.

Otherwise, post "/var/log/cups/access_log" and "/var/log/cups/error_log" for more info on the error.


hmm... i'm not getting the filter problem anymore. i tried to print a test page again and here's what it says:
"Print error: there was a problem processing document 'test page.'"

i'm trying to post my /var/log/cups/access_log and /var/log/cups/error_log but it's not letting me.

---

### Post by mooortin on 2010-02-26
Hi,
i've been trying to make a deb from those files from [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)
but i can't i'm too noob for that...:D
i don't understand how to make it. The configure command won't work ...
i do need your help.

cheers

---

### Post by mooortin on 2010-03-01
Hi ,
just a small up, i really need your help....

---

### Post by KIAaze on 2010-03-02
Ok, I finally created the debian package! :)
Here it is: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z700%20Series%20Printers](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z700%20Series%20Printers)

z600 instructions are just above it. ;)

Sorry for the long delay. :oops:

Quick info on what I did:
```
# .rpm extract
rpm2cpio lexmark-z700-cups-driver-1.1.1-1.i586.rpm | cpio -dimv
rpm2cpio z700llpddk-2.0-1.i386.rpm | cpio -dimv
# .deb extract
dpkg -e package.deb DIR
dpkg -x package.deb DIR
# .deb creation
dpkg-deb -b DIR package.deb

```

(I did it on an OpenSUSE machine.)

---

### Post by mooortin on 2010-03-04
ok i've uninstall the z600 driver with synaptic. "i don't know if it was the way to do it". Then i've installed the .deb you've made.
i went to printer selection and didn't find the driver z7 or z700 in lexmark. 
so were did it go? i mean i know where with the files listing in your .deb package. so i try to find the ppd file. but didn't work either.
lost in "linuxation" :)

---

### Post by KIAaze on 2010-03-04
Yes, removing the package through synaptic is correct. It's the same as using "apt-get remove".

The .ppd file is in "/usr/share/cups/model/Lexmark-Z700-lxz700cje-cups.ppd".

_Ways of listing contents of packages:_
1)For installed packages:
a) In Synaptic: Right-click->Properties->Installed files
b) dpkg -L PACKAGE
2).deb packages:
a) gdebi-gtk or gdebi-kde (what you run by double-clicking a .deb): "Included files" tab
b) dpkg --contents PACKAGE.deb

edit: Oops, I think I misunderstood. ^^'
So it did not work, even when specifying the .ppd file manually?
Can you find the z700 driver in the System->Administration->Printing dialog?

re-edit: Fixed debian package.
v0.3 available here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z700%20Series%20Printers](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z700%20Series%20Printers)

---

### Post by mooortin on 2010-03-04
no can't find it. there is no z700 driver in lexmark.
I even try as root, in graphic mode to choose my own ppd file situated in "/usr/share/cups/model/Lexmark-Z700-lxz700cje-cups.ppd" and it doesn't work....
although the liblexz700core0 driver is marked as installed in synaptic... :S

---

### Post by KIAaze on 2010-03-04
Try the new package: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z700%20Series%20Printers](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z700%20Series%20Printers)

---

### Post by mooortin on 2010-03-04
i finally get it, don't really know how this thing had worked !! thanks to your job, i reckon.

ok so i've been there[COLOR=Red] *_**[http://ubuntuforums.org/archive/index.php/t-772161.html](http://ubuntuforums.org/archive/index.php/t-772161.html)**_*[/COLOR]

and i followed the steps and now i get my printer working and perfectly configured. !!!


edit: OK Problem Solved !! **Printer lexmark P707 works perfectly on Ubuntu Karmic AMD 64Bits**

---

### Post by KIAaze on 2010-03-04
Great. :)
But I would like to know if the debian package works too.
It will make installation a lot easier for new users.
Only complex part right now is on 64-bit (because Lexmark only made 32-bit drivers).

---

### Post by alket on 2010-03-04
> **KIAaze said:**
> Try the new package: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z700%20Series%20Printers](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z700%20Series%20Printers)

Does this work for Lexmark x1270 printers ?

---

### Post by KIAaze on 2010-03-04
Google!
[http://ubuntuforums.org/showthread.php?t=933616](http://ubuntuforums.org/showthread.php?t=933616)

Apparently, yes, Lexmark x1270 printers work with the z600 drivers. :)

I'm currently reworking the wiki page:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

Everybody is welcome to help me improve it and correct errors.

---

### Post by mooortin on 2010-03-04
How do you want me to check if your new package works??
i'de like to but i get it already so i'll not know if yours is working tell me and i do :)

---

### Post by KIAaze on 2010-03-04
Well, ideally, you should reinstall Ubuntu and try it from there. ^^
You could also just try installing the z700 package and see if it still works. That would be good enough.
But you don't have too. C'est vous qui voyez. ;)

---

### Post by MeanRoy on 2010-03-04
I'm trying to install a Lexmark Z32.
It shows up in the printer list and appears at first to install.

The first clue I got that all was not well was that it was configured as a serial device.
The Z32 connects to the parallel port.
I browsed through a number of threads and note that (as far as I can tell) only one user claims to have gotten it to *sorta* work. but with some problems. ([here]("http://ubuntuforums.org/showthread.php?t=934663&highlight=lexmark+z32") - no replies to the thread) He used foomatic lxm3200-tweaked driver but has problems with appearance.

Any suggestions? 

Roy.

==
In the interest of being proactive with this, I checked the Lexmark site and find they have a driver for the Z32 which is intended to work with Linux Mandrake, Red Hat Linux, SuSE Linux.
> [SIZE="1"]Release Notes
Lexmark Enhanced Printer Driver for LINUX(R) Systems. Once downloaded, uncompress the file using the gunzip utility, untar the file using the tar utility and install the package files with the Red Hat Package Manager - rpm. For Detailed Installation instructions, see the README file. The Linux driver has an interdependancy with the GhostScript (R) utility -- it is recommended to use Ghostscript v6.01. For Support Information on this file visit "http://support.lexmark.com". Linux - Mandrake 7.0, Linux - Mandrake 7.1 RedHat Linux 6.0, RedHat Linux 6.1, RedHat Linux 6.2 SuSe 6.2, SuSe 6.3 These drivers can be downloaded from this web site free of charge. However, there will be a fee to cover materials and handling if requested from the Technical Support Center.[/SIZE]
It is beyond my current capability to make it work from there.

---

### Post by KIAaze on 2010-03-05
I created a .deb package using alien in a chrooted 32-bit environment.
You can get it here:
[http://www.mediafire.com/?2yngmkm2gjx](http://www.mediafire.com/?2yngmkm2gjx)
[http://www.mediafire.com/?iyw0rzzw54n](http://www.mediafire.com/?iyw0rzzw54n)

Try the version without scripts first! (Actually, it seems they are the same because alien converts scripts by default, but I'm not sure.)

Here's the readme that came with it:
[http://www.mediafire.com/?o0yyajmalam](http://www.mediafire.com/?o0yyajmalam)

You will need it, since unlike the z600/z700 packages, it seems to use a GUI instead of a simple .ppd file used by Ubuntu.

_Warning:_
I have not tested the packages and lintian (.deb checker) reported several errors, so there may be problems!
You might also be unable to install it on 64-bit for the moment.

(Uploaded to mediafire instead of the wiki because of all these uncertainties for now.)

===================
_What I did to create those debian packages:_
**(you don't need to follow these instructions, unless you want to create the debian packages yourself instead of using the ones I made)**

1) Downloaded the Z32 driver here: [http://support.lexmark.com/index?page=content&id=DR11906&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=Z32_COLOR_JETPRINTER&searchid=1267772536962](http://support.lexmark.com/index?page=content&id=DR11906&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=Z32_COLOR_JETPRINTER&searchid=1267772536962)
2) Extracted it:
```
tar -xzvf z32_eng_us-1.0-5.tgz
```
(same as using gunzip and then tar)
3) ```
cd rpm/z32/english_US/
```

Now you're in a directory with a README.txt and an .rpm file.

4) If you are on a 32-bit system, you can directly convert the .rpm to .deb with:
```
sudo alien --scripts lexmarkz22-z32-1.0-5.i386.rpm
```

Since I have a 64-bit system, I had to create a 32-bit chroot by following this:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by nuchdog on 2010-03-08
> **.kelp said:**
> Still got the same problem.
sudo chown root:root /usr/lib/cups/filter
sudo chown root:root /usr/lib/cups/backend
is supposed to fix that problem, but it doesn't for me.

Have an HP F2480 (my last one was apparently broken, what would explain why all of my previous attempts were futile) now but this issue persists. It works, however, in Virtualbox, so it's not that bad.

I also had to:

sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend

also for those trying to get cups-pdf to work, you might have to manually create the folder ~/PDF

mkdir ~/PDF

---

### Post by MeanRoy on 2010-03-13
OK, I confess I scanned too quickly over the instructions and started to follow steps 1-4.
When I finally pulled my head out of my butt I went ahead and installed the deb you provided.

This was apparently successful.
I then went to System - Administration - Printing and Printer configuration came up.
I selected New - Printer and got the message "Searching for printers".
I got a New Printer panel with "Select Device - other and no printers listed.

Not sure where to go from here.
I haven't a clue as to what I might enter in the "Enter device URI" box or if that would be the appropriate thing to do here.
I've been reading through the Wiki and some of the stuff on the Linux Foundation "Open printing" site.
I ran cups-config --version in a term and got 
> The program 'cups-config' is currently not installed.  You can install it by typing:
sudo apt-get install libcups2-dev
cups-config: command not found
I decided to wait for advise before going further.

Roy.

---

### Post by blazemore on 2010-03-13
> **MeanRoy said:**
> OK, I confess I scanned too quickly over the instructions and started to follow steps 1-4.
When I finally pulled my head out of my butt I went ahead and installed the deb you provided.

This was apparently successful.
I then went to System - Administration - Printing and Printer configuration came up.
I selected New - Printer and got the message "Searching for printers".
I got a New Printer panel with "Select Device - other and no printers listed.

Not sure where to go from here.
I haven't a clue as to what I might enter in the "Enter device URI" box or if that would be the appropriate thing to do here.
I've been reading through the Wiki and some of the stuff on the Linux Foundation "Open printing" site.
I ran cups-config --version in a term and got 

I decided to wait for advise before going further.

Roy.

[apt:libcups2-dev](apt:libcups2-dev)
Click that ^

---

### Post by MeanRoy on 2010-03-13
OK, did that.
Now get>  meanroy@meanroy-desktop:~$ cups-config --version
1.4.1
meanroy@meanroy-desktop:~$

Still no joy at seeing the printer.

Roy.
==================
On further reading on the Open Printing site I find this:
> The drivers issued by Lexmark do not contain any CUPS or PDQ configuration file, so use them either with LPD or with my Lexmark Foomatic Kit.
I fired up [http://localhost:631/admin](http://localhost:631/admin) and tried to find a printer from there but none was found.

I found that *some* foomatic stuff was loaded but some wasn't so I installed what wasn't.
Now I'm trying to figure out what to do with it.

R.

---

### Post by MeanRoy on 2010-03-16
It doesn't appear that the driver works.
After much searching around I've given up for the time being.
I have 2 other printers an HP712C and an Epson RX580, neither of which look to be any easier.

My, there is certainly a plethora of print techniques aren't there! And they all look mutually exclusive to me but what do I know.
Not much obviously!

Roy.

---

### Post by tapman1 on 2010-03-21
Hi, I tried to use your code to install the Z600 driver, and got to the line "sudo tar xvzf z600llpddk-2.0.tgz -c" and got an error code "tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information."

Not sure what went wrong, but I can't get past that point. Any suggestions?

I am on a Dell 2.0Ghz P4 w/ 500M ram running 9.04

Thanks,

---

### Post by alket on 2010-03-25
> **KIAaze said:**
> Google!
[http://ubuntuforums.org/showthread.php?t=933616](http://ubuntuforums.org/showthread.php?t=933616)

Apparently, yes, Lexmark x1270 printers work with the z600 drivers. :)

I'm currently reworking the wiki page:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

Everybody is welcome to help me improve it and correct errors.

I tried both but doesn't seem to work with Lexmark x1270

---

### Post by helmut888 on 2010-04-10
Try the x2600 series drivers ([http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip](http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip)) they seem to do the job.

---

### Post by vnieto on 2010-04-22
> **ShadowMage said:**
> [SIZE=5][COLOR=DarkGreen][B]

Once you've added the entry above in fstab, don't forget to mount it (thanks Mr.Banana) by entering the command
```
sudo mount usbfs
```Now, run z600 again (no need to cd again if you're already there, but it's here just in case you started this step from a new terminal):


At this point make this error:
"mount: mounting point  /proc/bus/usb don't exist"

but work (i don't know why)

---

### Post by xisxas on 2010-05-15
installing Lexmark Z640 printer in Ubuntu 10.04.
 
I first downloaded liblexz600core0.deb package -see link below. I then used:< sh z600cups-1.0-1.tar.gz.sh > command without the brackets, which gave a reading in the terminal = cam@cam-desktop:~$ sh z600cups-1.0-1.tar.gz.sh 
sh: Can't open z600cups-1.0-1.tar.gz.sh
cam@cam-desktop:~$ 
 
But for some reason the printer worked after this - a mystery to me because of the reported "Can't open z600cups-1.0-1.tar.gz.sh" in the terminal".
 
I had also installed beforehand libstdc++5 The GNU Standard C++ Library v3 in synaptics.
 
libstdc++6 The GNU Standard C++ Library v3, was already installed in synaptics.
 
I'm just a get by person really, though I've used Ubuntu for a few years now. Hope this helps
 
 
For the package thank Temposs
[http://sites.google.com/site/temposs/liblexz600core0.deb?attredirects=0](http://sites.google.com/site/temposs/liblexz600core0.deb?attredirects=0)


Hello Steve

---

### Post by rarsa on 2010-05-26
I've created a script that does most of the work and some instructions for pre-Karmic and post-Karmic installation.

The script and instructions also work with most other distributions:

[http://kwlug.org/node/742]("http://kwlug.org/node/742")

---

### Post by wuffeemoz on 2010-06-21
hi, i put ubuntu 10.04 netbook remix on my sister's eee 900a. she has a lexmark x1185 printer that does not work natively. the scanner part works fine. the printer page has the driver for the z600 listed so i did that along with what you and about 3 other forums said to do, i keep getting the same message: something about unable to process. ill post in another post

---

### Post by wuffeemoz on 2010-06-21
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest Lexmark--X1100-Series (default)>,
 'cups_instance': None,
 'cups_queue': 'Lexmark--X1100-Series',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/X1100%20Series',
                       'printer-info': u'Lexmark  X1100 Series',
                       'printer-is-shared': True,
                       'printer-location': u'windows-pc',
                       'printer-make-and-model': u'Lexmark Z600 v1.0-1',
                       'printer-state': 3,
                       'printer-state-message': u'Processing page 1...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Lexmark--X1100-Series'},
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
                                 'device-uri': u'usb://Lexmark/X1100%20Series',
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
                                                     u'iso_a4_210x297mm',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'na_legal_8.5x14in',
                                                     u'jis_b5_182x257mm',
                                                     u'na_executive_7.25x10.5in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-4x6_4x6in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_personal_3.625x6.5in',
                                                     u'na_number-9_3.875x8.875in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_a2_4.375x5.75in',
                                                     u'jpn_chou3_120x235mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'adobe_Chokei40_89.9583x240.947mm',
                                                     u'adobe_Kakugata3_8.5x10.9028in',
                                                     u'adobe_Kakugata4_7.75x10.5139in',
                                                     u'adobe_Kakugata5_190.147x239.889mm',
                                                     u'iso_c5_162x229mm',
                                                     u'adobe_L_3.5x5in',
                                                     u'na_5x7_5x7in',
                                                     u'custom_min_2x4in',
                                                     u'custom_max_8.58333x13in'],
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
                                 'printer-info': u'Lexmark  X1100 Series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'windows-pc',
                                 'printer-make-and-model': u'Lexmark Z600 v1.0-1',
                                 'printer-more-info': u'http://localhost:631/printers/Lexmark--X1100-Series',
                                 'printer-name': u'Lexmark--X1100-Series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1277140685,
                                 'printer-state-message': u'Processing page 1...',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 167948,
                                 'printer-up-time': 1277140703,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Lexmark--X1100-Series'],
                                 'queued-job-count': 1,
                                 'server-is-sharing-printers': False,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'},
                               u'Others': {u'ColorModel': u'Color',
                                           u'Inkset': u'CMYK',
                                           u'PrintQuality': u'Normal'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Lexmark ;CMD:CPDNPA001;MODEL:X1100 Series;CLASS:Printer;DES:Lexmark X1100 Series;COMMENT:030305-1;',
                      'device-info': u'Lexmark X1100 Series',
                      'device-location': u'',
                      'device-make-and-model': u'Lexmark X1100 Series'}}
Page 8 (Printer state reasons):
{'printer-state-message': u'Processing page 1...',
 'printer-state-reasons': [u'none']}
Page 9 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 455021L,
 'error_log_debug_logging_set': True}
Page 10 (Print test page):
{'test_page_attempted': '21/Jun/2010:12:19:24 +0000',
 'test_page_job_id': [25],
 'test_page_job_status': [(True,
                           25,
                           'Lexmark--X1100-Series',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 25,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/25',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'windows',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/rastertoz600 failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1277140781,
                            'job-printer-uri': u'ipp://windows-pc:0/printers/Lexmark--X1100-Series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/25',
                            'job-uuid': u'urn:uuid:8638059b-5ae8-3b27-5818-462b98c08820',
                            'printer-uri': u'ipp://localhost/printers/Lexmark--X1100-Series',
                            'time-at-completed': None,
                            'time-at-creation': 1277140764,
                            'time-at-processing': 1277140764})],
 'test_page_successful': False}
Page 11 (Error log fetch):
{'error_log': ['D [21/Jun/2010:12:18:51 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:51 -0500] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [21/Jun/2010:12:18:51 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Jun/2010:12:18:51 -0500] cupsdAuthorize: No authentication data provided.',
               'D [21/Jun/2010:12:18:51 -0500] cupsdReadClient: 11 1.1 Get-Jobs 1',
               'D [21/Jun/2010:12:18:51 -0500] Get-Jobs ipp://localhost/printers/',
               'D [21/Jun/2010:12:18:51 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [21/Jun/2010:12:18:51 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:51 -0500] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [21/Jun/2010:12:18:51 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Jun/2010:12:18:51 -0500] cupsdAuthorize: No authentication data provided.',
               'D [21/Jun/2010:12:18:51 -0500] cupsdReadClient: 11 1.1 Get-Jobs 1',
               'D [21/Jun/2010:12:18:51 -0500] Get-Jobs ipp://localhost/printers/',
               'D [21/Jun/2010:12:18:51 -0500] [Job 1] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 2] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 3] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 4] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 5] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 6] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 7] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 8] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 9] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 10] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 11] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 12] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 13] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 14] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 15] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 16] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 17] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 18] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 19] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 20] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 21] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 22] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] [Job 23] Loading attributes...',
               'D [21/Jun/2010:12:18:51 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [21/Jun/2010:12:18:51 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:51 -0500] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [21/Jun/2010:12:18:51 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Jun/2010:12:18:51 -0500] cupsdAuthorize: No authentication data provided.',
               'D [21/Jun/2010:12:18:51 -0500] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1',
               'D [21/Jun/2010:12:18:51 -0500] Create-Printer-Subscription /',
               'D [21/Jun/2010:12:18:51 -0500] cupsdCreateSubscription(con=0x21e75a58(11), uri="/")',
               'D [21/Jun/2010:12:18:51 -0500] pullmethod="ippget"',
               'D [21/Jun/2010:12:18:51 -0500] notify-lease-duration=86400',
               'D [21/Jun/2010:12:18:51 -0500] notify-time-interval=0',
               'D [21/Jun/2010:12:18:51 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [21/Jun/2010:12:18:51 -0500] Added subscription 23 for server',
               'D [21/Jun/2010:12:18:51 -0500] cupsdMarkDirty(-----S)',
               'D [21/Jun/2010:12:18:51 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [21/Jun/2010:12:18:51 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:52 -0500] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [21/Jun/2010:12:18:52 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Jun/2010:12:18:52 -0500] cupsdAuthorize: No authentication data provided.',
               'D [21/Jun/2010:12:18:52 -0500] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [21/Jun/2010:12:18:52 -0500] Get-Notifications /',
               'D [21/Jun/2010:12:18:52 -0500] cupsdIsAuthorized: requesting-user-name="windows"',
               'D [21/Jun/2010:12:18:52 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Jun/2010:12:18:52 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdAuthorize: No authentication data provided.',
               'D [21/Jun/2010:12:18:59 -0500] cupsdReadClient: 11 1.1 Cancel-Subscription 1',
               'D [21/Jun/2010:12:18:59 -0500] Cancel-Subscription /',
               'D [21/Jun/2010:12:18:59 -0500] cupsdIsAuthorized: requesting-user-name="windows"',
               'D [21/Jun/2010:12:18:59 -0500] cupsdMarkDirty(-----S)',
               'D [21/Jun/2010:12:18:59 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [21/Jun/2010:12:18:59 -0500] cupsdReadClient: 13 GET /admin/log/error_log HTTP/1.1',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdAuthorize: No authentication data provided.',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdAuthorize: No authentication data provided.',
               'D [21/Jun/2010:12:18:59 -0500] cupsdIsAuthorized: username=""',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSendHeader: 13 WWW-Authenticate: Basic realm="CUPS", trc="y"',
               'D [21/Jun/2010:12:18:59 -0500] cupsdCloseClient: 13',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [21/Jun/2010:12:18:59 -0500] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdAuthorize: Authorized as windows using PeerCred',
               'D [21/Jun/2010:12:18:59 -0500] cupsdIsAuthorized: username="windows"',
               'I [21/Jun/2010:12:18:59 -0500] Installing config file "/etc/cups/cupsd.conf"...',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Dirty files',
               'D [21/Jun/2010:12:18:59 -0500] cupsdCloseClient: 11',
               'D [21/Jun/2010:12:18:59 -0500] cupsdCloseClient: 13',
               'I [21/Jun/2010:12:18:59 -0500] Saving printers.conf...',
               'I [21/Jun/2010:12:18:59 -0500] Generating printcap /var/run/cups/printcap...',
               'I [21/Jun/2010:12:18:59 -0500] Saving subscriptions.conf...',
               'D [21/Jun/2010:12:18:59 -0500] cupsdSetBusyState: Not busy',
               'I [21/Jun/2010:12:18:59 -0500] cupsdDefaultRIPCacheSize: 513308k',
               'E [21/Jun/2010:12:18:59 -0500] Filter directory "/usr/lib/cups/filter" for printer "Lexmark--X1100-Series" not owned by root',
               'E [21/Jun/2010:12:19:20 -0500] Filter directory "/usr/lib/cups/filter" for printer "Lexmark--X1100-Series" not owned by root',
               'E [21/Jun/2010:12:19:28 -0500] [Job 25] Job stopped due to filter errors; please consult the error_log file for details.',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] The following messages were recorded from 12:19:24 to 12:19:28',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Adding start banner page "none".',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Adding end banner page "none".',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] File of type application/vnd.cups-banner queued by "windows".',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] hold_until=0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Queued on "Lexmark--X1100-Series" by "windows".',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] job-sheets=none,none',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] argv[0]="Lexmark--X1100-Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] argv[1]="25"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] argv[2]="windows"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] argv[3]="Test Page"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] argv[4]="1"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] argv[5]="job-uuid=urn:uuid:8638059b-5ae8-3b27-5818-462b98c08820 job-originating-host-name=localhost"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] argv[6]="/var/spool/cups/d00025-001"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[10]="SERVER_ADMIN=root@windows-pc"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[13]="TZ=America/Chicago"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[14]="USER=root"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[17]="IPP_PORT=631"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[18]="CHARSET=utf-8"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[19]="LANG=en_US.UTF-8"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[20]="PPD=/etc/cups/ppd/Lexmark--X1100-Series.ppd"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[21]="RIP_MAX_CACHE=513308k"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[23]="DEVICE_URI=usb://Lexmark/X1100%20Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[24]="PRINTER_INFO=Lexmark  X1100 Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[25]="PRINTER_LOCATION=windows-pc"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[26]="PRINTER=Lexmark--X1100-Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[27]="CUPS_FILETYPE=document"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[28]="FINAL_CONTENT_TYPE=printer/Lexmark--X1100-Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Started filter /usr/lib/cups/filter/bannertops (PID 1514)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Started filter /usr/lib/cups/filter/pstopdf (PID 1515)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Started filter /usr/lib/cups/filter/pdftopdf (PID 1516)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Started filter /usr/lib/cups/filter/pdftoraster (PID 1517)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Started filter /usr/lib/cups/filter/rastertoz600 (PID 1518)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Started backend /usr/lib/cups/backend/usb (PID 1519)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] pstopdf 5 args: 25 windows Test Page 1 job-uuid=urn:uuid:8638059b-5ae8-3b27-5818-462b98c08820 job-originating-host-name=localhost',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PPD: /etc/cups/ppd/Lexmark--X1100-Series.ppd',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Lexmark--X1100-Series: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] load_banner(filename="/var/spool/cups/d00025-001")',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] STATE: +connecting-to-device',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Page = 612x792; 18,36 to 594,787',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Printer using device file "/dev/usblp0"...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] STATE: -connecting-to-device',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0x27cb40)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Resolution:',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Page size: Letter',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Width: 612, height: 792, absolute margins: 18, 36, 594, 787',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Relative margins: 18, 36, 18, 5',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PostScript to be injected:',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=1 -dcupsRowStep=3 -scupsPageSizeName=Letter -c -f -_',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[10]="SERVER_ADMIN=root@windows-pc"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[12]="TZ=America/Chicago"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[13]="USER=root"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[16]="IPP_PORT=631"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[17]="CHARSET=utf-8"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[18]="LANG=en_US.UTF-8"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[19]="PPD=/etc/cups/ppd/Lexmark--X1100-Series.ppd"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[20]="RIP_MAX_CACHE=513308k"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[22]="DEVICE_URI=usb://Lexmark/X1100%20Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[23]="PRINTER_INFO=Lexmark  X1100 Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[24]="PRINTER_LOCATION=windows-pc"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[25]="PRINTER=Lexmark--X1100-Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[26]="CUPS_FILETYPE=document"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] envp[27]="FINAL_CONTENT_TYPE=printer/Lexmark--X1100-Series"',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_put_params(0xb761703c, 0xbfc51748)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_set_color_info(0xb761703c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[0] = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[65535] = 1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] num_components = 1, depth = 1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_gray = 1, dither_grays = 2',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_color = 0, dither_colors = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Updating PageSize to [612 792]...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting initial media size, [612 792] = 5100x6600 pixels...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] ppd = (nil)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612.000 792.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] margins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWResolution = [ 600.000 600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 5100, height = 6600',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_put_params(0xb761703c, 0xbfc5174',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting cupsBitsPerColor to 8...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting cupsColorOrder to 0...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting cupsColorSpace to 1...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting cupsCompression to 1...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting cupsRowStep to 3...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting cupsPageSizeName to "Letter"...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_set_color_info(0xb761703c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[0] = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[65535] = 255',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] num_components = 3, depth = 24',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_gray = 0, dither_grays = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_color = 255, dither_colors = 256',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting initial media size, [612 792] = 5100x6600 pixels...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] ppd = (nil)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612.000 792.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] margins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWResolution = [ 600.000 600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 5100, height = 6600',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_open(0xb761703c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Processing page 1...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_set_color_info(0xb761703c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[0] = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[65535] = 255',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] num_components = 3, depth = 24',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_gray = 0, dither_grays = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_color = 255, dither_colors = 256',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_space_params(0xb761703c, 0xbfc5166c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cache_size = 525627392',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5170',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 5100, height = 6600',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc516b',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 5100, height = 6600',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5176',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 5100, height = 6600',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5167',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 5100, height = 6600',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5172',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 5100, height = 6600',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc516d',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 5100, height = 6600',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -0.000 6600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_put_params(0xb761703c, 0xbfc5174',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting LeadingEdge to 0...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_set_color_info(0xb761703c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[0] = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[65535] = 255',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] num_components = 3, depth = 24',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_gray = 0, dither_grays = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_color = 255, dither_colors = 256',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Updating PageSize to [612 792]...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->header.Duplex = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->header.Tumble = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->page = 1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->PPD = 0x9ef6d70',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->PPD->flip_duplex = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] (4) Flip: X=0 Y=0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->header.cupsPageSizeName = Letter',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] size = Letter',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Reallocating memory, [612 792] = 4800x6258 pixels...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_space_params(0xb761703c, 0xbfc513ac)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cache_size = 525627392',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Reallocated memory, [612 792] = 4800x6258 pixels...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] ppd = 0x9ef6d70',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612.000 792.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] margins = [ 0.250 0.500 0.250 0.069 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWResolution = [ 600.000 600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5168',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5163',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5170',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc516b',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5175',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5176',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51740)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5167',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc516d',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_put_params(0xb761703c, 0xbfc51c3',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting LeadingEdge to 0...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_set_color_info(0xb761703c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[0] = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[65535] = 255',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] num_components = 3, depth = 24',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_gray = 0, dither_grays = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_color = 255, dither_colors = 256',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_put_params(0xb761703c, 0xbfc51c3',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Setting LeadingEdge to 0...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_set_color_info(0xb761703c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[0] = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->EncodeLUT[65535] = 255',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] num_components = 3, depth = 24',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_gray = 0, dither_grays = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] max_color = 255, dither_colors = 256',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Updating PageSize to [612 792]...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->header.Duplex = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->header.Tumble = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->page = 1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->PPD = 0x9ef6d70',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->PPD->flip_duplex = 0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] (4) Flip: X=0 Y=0',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups->header.cupsPageSizeName = Letter',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] size = Letter',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] margins[] = [ 0.250000 0.500000 0.250000 0.069444 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Reallocating memory, [612 792] = 4800x6258 pixels...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_space_params(0xb761703c, 0xbfc5189c)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cache_size = 525627392',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Reallocated memory, [612 792] = 4800x6258 pixels...',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] ppd = 0x9ef6d70',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612.000 792.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] margins = [ 0.250 0.500 0.250 0.069 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWResolution = [ 600.000 600.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc51bf',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc51ba',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc51c4',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc51c5',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc51b6',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc51bc',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc51bc',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_matrix(0xb761703c, 0xbfc5155',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Portrait matrix: XX=+1 XY=0 YX=0 YY=-1',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] width = 4800, height = 6258',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] HWMargins = [ 18.000 36.000 18.000 5.000 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_get_params(0xb761703c, 0xbfc51c30)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] before gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] after gdev_prn_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] Leaving cups_get_params()',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cups_print_pages(0xb761703c, 0x2664e0, 1)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] cupsBitsPerPixel = 24, cupsWidth = 4800, cupsBytesPerLine = 14400, srcbytes = 14400',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] End of messages',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] printer-state=3(idle)',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] printer-state-message="Processing page 1..."',
               'D [21/Jun/2010:12:19:28 -0500] [Job 25] printer-state-reasons=none'],
 'error_log_debug_logging_unset': True}
Page 12 (Printer state reasons):
{'printer-state-message': u'Filter directory "/usr/lib/cups/filter" for printer "Lexmark--X1100-Series" not owned by root',
 'printer-state-reasons': [u'cups-insecure-filter-warning']}
Page 13 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by ddreamer on 2010-07-05
I have found a great reference. I just succeeded. You guys may try it out.

My printer is Lexmark Z515.
OS: Ubuntu Lucid Lynx, amd64

The great reference is as below:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Problems%20with%20Ubuntu%209.10%20Karmic](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Problems%20with%20Ubuntu%209.10%20Karmic)

---

### Post by w2vy on 2010-07-05
Wow, I did not see this before.

I am going to try this driver...They say:

Operating Systems
Ubuntu 9.04, Ubuntu 9.10, Ubuntu 10.04 

Release Notes
Linux Driver for Lexmark for X5070 Series, X7600 Series, X6600 Series, X5600 Series, Z2400 Series, X4900 Series, X4600 Series, X3600 Series for Linux OS.

[Lexmark Driver for Ubuntu!]("http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz")

tom
ps. it supports x86 only

---

It works like a champ!

Need to SUDO the install script and if the printer is not local (it *is* wireless after all)
just cancel when it asks for you to insert USB cable

Then add printer as normal, the driver is installed priperly

Thank You Lexmark!
This is proof that Ubuntu/Linux use is growing!

---

### Post by osviweb on 2010-07-18
hello sorry for asking but this thread is quite huge and I cannot read it all.
I'd appreciate if someone can tell me (a beginner) how to install my Lexmark x1200 printer on Ubuntu 10.4 

I have this printer shared on a win pc. 
I can see the printer with samba network.
I've tryed to install and use the x600 driver but even if document is correctly sent to printer it do not load paper and do nothing.
Anyone can please help?

thanks

---

### Post by KIAaze on 2010-07-19
According to [this page]("http://ubuntica.com/use-your-lexmark-on-ubuntu.html"), the Z600 driver should work.
Very detailed instructions for Lexmark printers are here:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

Does the printer work when directly connected to your PC (i.e. not on the network and not shared with the Windows PC)?

---

### Post by osviweb on 2010-07-19
Thank for your help.
The instructions you sent me are for ubuntu 9. They can fit also ubuntu 10 ?

About the printer I cannot connect it directly but I don't think it is a network issue.

thanks again

---

### Post by KIAaze on 2010-07-19
> **osviweb said:**
> 
The instructions you sent me are for ubuntu 9. They can fit also ubuntu 10 ?

I don't know. Just try! :)
Usually, things do not change that much from one Ubuntu release to the other.

---

### Post by rickson on 2010-08-31
Hello there,

i´m very new to the linux world. shortly i have installed ubuntu server. 
i would like install my good old lexmark z33 printer but have big trouble with it.
i have read many posts about an installation work arround with some lexmark printers but
i got it not work. So dear experts i need your help.

i followed all this installation instruction from this thread but then at the point at step:

Check whether the printer backend works; 	Code:
 	$ cd /usr/lib/cups/backend
$ ./z600 
i got nothing back.

then i tried out to modifie /etc/fstab

with: 

usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

and the mount command : mount usbfs
i got this error:
mount: mount point /proc/bus/usb does not exist

what can i do fix it?
I think i make mistake in the meantime. i tried out this command in my confusing sutation:
mount --bind /dev/bus  /proc/bus
and have overwritten my folders in /proc/bus  ?!
can i redo this binding command?

So i hope you can help me.

---

### Post by tiggsy on 2010-08-31
@rickson

I had a similar problem. Here's how I got my printer working (not the same model, but worth a go)

[http://ubuntuforums.org/showthread.php?t=1507972](http://ubuntuforums.org/showthread.php?t=1507972)

---

### Post by rickson on 2010-08-31
@tiggsy your version do not work for me.
if i select in add new printer my lexmark i got the message driver not found.
if i add a new printer by uri i cannot go further. so this seems not be the right for z33.
:(

---

### Post by rickson on 2010-08-31
how can i add an mountpoint?

---

### Post by stepstools on 2010-08-31
It seems as if the URL's have changed, I cant find the RPM's for any of the printers.  Can anybody help?

---

### Post by stepstools on 2010-08-31
Nevermind, found a more up to date tut.

---

### Post by Vereda on 2010-09-04
I'm looking for the Windows 7 driver for the Lexmark Z615. So far nothing is printed, because the system detects communication problems.

---

### Post by Jay214 on 2010-09-08
> **stepstools said:**
> Nevermind, found a more up to date tut.


plz could you post the link if you remember it?

---

### Post by AjitDingankar on 2010-10-16
After installing Ubuntu 10.10 my Lexmark MFD didn't work, 
and the download page linked on the first post was dangling 
(it has been 5 years, after all ;-) but I found that searching 
for "<YourPrinterModel> linux" at: 
[http://support.lexmark.com/index?page=home&locale=en&userlocale=EN_US%20&segment=DOWNLOAD](http://support.lexmark.com/index?page=home&locale=en&userlocale=EN_US%20&segment=DOWNLOAD) 
takes you to a page that actually works! ;-) Except that you have to 
sudo (or run as root) the included shell script.

---

### Post by I, the Deceiver on 2010-11-07
this worked for me:
[http://ubuntuforums.org/showthread.php?p=10083099](http://ubuntuforums.org/showthread.php?p=10083099)

---

### Post by fagulhaspt on 2010-11-10
> **osviweb said:**
> hello sorry for asking but this thread is quite huge and I cannot read it all.
I'd appreciate if someone can tell me (a beginner) how to install my Lexmark x1200 printer on Ubuntu 10.4 

I have this printer shared on a win pc. 
I can see the printer with samba network.
I've tryed to install and use the x600 driver but even if document is correctly sent to printer it do not load paper and do nothing.
Anyone can please help?

thanks
Try the instructions of [this other thread]("http://ubuntuforums.org/showthread.php?p=10083099") , they are for Ubuntu 10.04 (and most probably also work with newer ubuntus)

I have a feeling they will also work for your Lexmark model

---

### Post by agemini68 on 2010-11-23
Okay, I'm a newbie and I'm having some issues getting my lexmark z705 printer to work. I installed the z700 package mentioned below and I get this:Error: Dependency is not satisfiable: libstdc++5. What does this mean? I don't know anything about codes, I'm trying ubunto after I had several virus issues with windows, (another story). Windows is all I know, I'm kind of the point and click user. I'm running ubunto 10.10 desktop.

I'm still struggling with my lexmark z705 printer. I finally got the driver package to install, but still can't get it to print, when I view the attributes of the print job I saw this:

job printer state message  /usr/lib/cups/filter/rastertoz700 failed

I did a little research and followed this suggested command: 
ldd /user/lib/cups/filter/rastertoz700

In response I got this:

```
libc.so.6 => /lib32/libc.so.6 (0xf74c9000)
    libgssapi_krb5.so.2 => /usr/lib32/libgssapi_krb5.so.2 (0xf749a000)
    libgnutls.so.26 => /usr/lib32/libgnutls.so.26 (0xf73ff000)
    libavahi-common.so.3 => /usr/lib32/libavahi-common.so.3 (0xf73f3000)
    libavahi-client.so.3 => /usr/lib32/libavahi-client.so.3 (0xf73e2000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf73c8000)
    libz.so.1 => /usr/lib32/libz.so.1 (0xf73b3000)
    libtiff.so.4 => /usr/lib32/libtiff.so.4 (0xf7358000)
    libpng12.so.0 => /lib32/libpng12.so.0 (0xf7333000)
    libjpeg.so.62 => /usr/lib32/libjpeg.so.62 (0xf7312000)
    /lib/ld-linux.so.2 (0xf7788000)
    libkrb5.so.3 => /usr/lib32/libkrb5.so.3 (0xf7260000)
    libk5crypto.so.3 => /usr/lib32/libk5crypto.so.3 (0xf723c000)
    libcom_err.so.2 => /lib32/libcom_err.so.2 (0xf7238000)
    libkrb5support.so.0 => /usr/lib32/libkrb5support.so.0 (0xf7230000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf722c000)
    libkeyutils.so.1 => /lib32/libkeyutils.so.1 (0xf7227000)
    libresolv.so.2 => /lib32/libresolv.so.2 (0xf7213000)
    libtasn1.so.3 => /usr/lib32/libtasn1.so.3 (0xf7202000)
    libgcrypt.so.11 => /lib32/libgcrypt.so.11 (0xf718f000)
    libdbus-1.so.3 => /lib32/libdbus-1.so.3 (0xf7156000)
    librt.so.1 => /lib32/librt.so.1 (0xf714d000)
    libgpg-error.so.0 => /lib32/libgpg-error.so.0 (0xf7147000)
```

Someone please interpret and suggest solution. Thank You

Well hallelujah it works, I'm not sure if the download is fixed or if there is a new update but here is what I did to get it to work, I fought Windows for 13hrs for it to create a decent boot disc, everytime I tried to download the ubunto software, I got the blue screen of death. I was running ubunto with windows, but once I was able to get the boot disc, I installed ubunto desktop 10.10 as the only operating system. I ran all the updates and then installed the driver located in the link below and now my lexmark z705 printer works.

Bye Bye Microsoft windows!
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z700-0.4.deb](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z700-0.4.deb)

---

### Post by KIAaze on 2010-11-24
I'm very glad to hear that. :D
Not only because you solved your problem and I don't have to figure out what the problem was, but also because it means the package still works on Ubuntu 10.10! (it wasn't modified since 2010-03-04 and is still the one I made)

And thanks for also posting your solution here. :)

I don't remember you mentioning that you were using Wubi (Ubuntu on Windows) anywhere before.
That's a very important detail, since it is not the standard way of running Ubuntu.
So always mention it in the future in case you try Wubi again. ;)

Here are a few links for you as a beginner:
[Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")
[New to Ubuntu? Start here...]("http://ubuntuforums.org/showthread.php?t=801404")

And there's also IRC for realtime help:
[https://help.ubuntu.com/community/InternetRelayChat]("https://help.ubuntu.com/community/InternetRelayChat")
(but it's a bit chaotic compared to a forum)

---

### Post by agemini68 on 2010-11-24
I wanted to add that if you have more difficulty than I did making a boot disc, you can always have one sent to you if you can wait for snail mail. It's on the site somewhere.

[http://www.ubunto.com]("http://www.ubunto.com/")

---

### Post by justfred on 2010-12-20
Hi,

Just upgraded my dauthers laptop from kramic to lucid (i386) but now I have difficulties to find libstdc++5 : the link that I followed for installing a Dell A920 = Lexmark X1150 on kramic :

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark)

which contains a reference to the Z600 drivers and which depend on libstdc++5 :

[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

comes back with an error : two or more packages specified (libstdc++5 jaunty) ??? In fact when moving up the tree one does not find Jaunty any longer : all links for jaunty came back with an error.

I could find it from hardy : libstdc++5_3.3.6-15ubuntu6_i386.deb
but that one throws up an error when trying to install it :

Error: Dependency is not satisfiable: gcc-3.3-base (>= 1:3.3.6-15ubuntu6)

Is it a case that a more recent version of libstdc++5 (say linstdc++6) needs to be soft linked to ? Does any one know if this will work with the lexmark.z600-0.4.deb ?

Also the lexmark website (as indicated in one of the earlier posts) does not give a linux version for this model (only Win and MacOS).

Any help much appreciated ...

---

### Post by KIAaze on 2010-12-22
Since you upgraded to lucid, why not use this package?:
[http://packages.ubuntu.com/lucid-backports/libstdc++5](http://packages.ubuntu.com/lucid-backports/libstdc++5)

---

### Post by justfred on 2010-12-22
> **KIAaze said:**
> Since you upgraded to lucid, why not use this package?:
[http://packages.ubuntu.com/lucid-backports/libstdc++5](http://packages.ubuntu.com/lucid-backports/libstdc++5)

I didn't think of that ... in the mean time I found a thread where the libstdc++5 was extracted from an amd64 package and this seems to work (but alas I did not find the thread back otherwise I would have posted it here).

I think it should be useful to update the [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark) page to include your suggestion : it would be, I'm sure, greatly appreciated by people trying to install such kind of printers.

How can we achieve that ?

---

### Post by KIAaze on 2010-12-22
Very easily: Just create a launchpad account and you should be able to log in to edit the wiki. :)

I can do it, but I need to finish something else now and I would also like to see people edit the wiki themselves instead of always waiting for others to do it. ;)

---

### Post by inearlygaveup on 2010-12-22
[QUOTE=justfred;10268743]I didn't think of that ... in the mean time I found a thread where the libstdc++5 was extracted from an amd64 package and this seems to work (but alas I did not find the thread back otherwise I would have posted it here).


**I think it may have been post 7 by fagulhaspt at**

[http://ubuntuforums.org/showthread.php?t=1507972&highlight=Lexmark+x1270](http://ubuntuforums.org/showthread.php?t=1507972&highlight=Lexmark+x1270)

---

### Post by justfred on 2010-12-22
Yes, that's the thread.

---

### Post by justfred on 2010-12-22
> **KIAaze said:**
> Very easily: Just create a launchpad account and you should be able to log in to edit the wiki. :)

I can do it, but I need to finish something else now and I would also like to see people edit the wiki themselves instead of always waiting for others to do it. ;)
Ok, done that : added a section for Lucid Lynx with your suggestion and added a similar link for the Karmic Koala section ([http://packages.ubuntu.com/karmic-backports/libstdc++5](http://packages.ubuntu.com/karmic-backports/libstdc++5)) as an alternative source.

---

### Post by VietCanada on 2010-12-28
Installing Lexmark x1270 on a desktop with Ubuntu 10.10 amd64 installed.

I followed the steps outlined here: [http://ubuntuforums.org/showthread.php?t=1507972&highlight=Lexmark+x1270](http://ubuntuforums.org/showthread.php?t=1507972&highlight=Lexmark+x1270)

At the part where I double clicked on the libstdc++5_3.3.6-17ubuntu1_i386.deb icon to install it, I was informed that it was the wrong version since I have amd64.

So after some searching around this _**[Link]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z600%20Series%20Printers")**_ worked.

What I did:

1) I installed libstdc++5 from synaptic.

2)  I dl'd and installed _**[getlibs-all.deb]("http://frozenfox.freehostia.com/cappy/")**_ by double clicking on it's icon. 

3) I dl'd and installed _**[lexmark.z600-0.4.deb]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb")**_ by double clicking on it's icon. 

4) I went to System/Administration/Printing.

   Added my printer from the list and chose 
   the z600 colour inkjet driver.

5) I printed a test page. Now I need to buy ink.

---

### Post by inearlygaveup on 2010-12-29
5) I printed a test page. Now I need to buy ink.[/QUOTE]

**Same here**    :roll:

---

### Post by Quibbleknott on 2011-06-03
> **VietCanada said:**
> Installing Lexmark x1270 on a desktop with Ubuntu 10.10 amd64 installed.

I followed the steps outlined here: [http://ubuntuforums.org/showthread.php?t=1507972&highlight=Lexmark+x1270](http://ubuntuforums.org/showthread.php?t=1507972&highlight=Lexmark+x1270)

At the part where I double clicked on the libstdc++5_3.3.6-17ubuntu1_i386.deb icon to install it, I was informed that it was the wrong version since I have amd64.

So after some searching around this _**[Link]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z600%20Series%20Printers")**_ worked.

What I did:

1) I installed libstdc++5 from synaptic.

2)  I dl'd and installed _**[getlibs-all.deb]("http://frozenfox.freehostia.com/cappy/")**_ by double clicking on it's icon. 

3) I dl'd and installed _**[lexmark.z600-0.4.deb]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb")**_ by double clicking on it's icon. 

4) I went to System/Administration/Printing.

   Added my printer from the list and chose 
   the z600 colour inkjet driver.

5) I printed a test page. Now I need to buy ink.
Worked perfectly on my lexmark x1150:guitar:

---

### Post by elGSdude on 2011-07-01
i have a lexmark Z515 and i found no support no where, only previous or other lexmark models supported by Ubuntu. the drivers on either dont work for s**t

---

### Post by KIAaze on 2011-07-01
> **elGSdude said:**
> i have a lexmark Z515 and i found no support no where, only previous or other lexmark models supported by Ubuntu. the drivers on either dont work for s**t

If you want to complain, go complain to Dell and Lexmark. They are the ones who should provide GNU/Linux drivers.

Otherwise, have you tried this: [http://www.aquarionics.com/journal/2005/04/15/making_the_lexmark_z515_work_under_debian_linux/](http://www.aquarionics.com/journal/2005/04/15/making_the_lexmark_z515_work_under_debian_linux/) ?

The link to the driver in it doesn't work and I couldn't find Z515 drivers, however, according to the howto, they use z600cups-1.0-1.gz.sh, i.e. the driver for z600.
You can find that driver here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

The .deb is quite old, but might still work.
If it doesn't, it should still be possible to get it to work, by extrac ting the necessary files and following one of the multiple tutorials using them.

I can eventually remake the .deb for the latest Ubuntu version, as I did in the past.
Just need to get more important things done in real life at the moment. :/

---

### Post by b.ash on 2011-08-29
I don't know if this is the right place to post this, but here goes

I have a lexmark s301 printer I'm trying to install on 10.10
I downloaded the driver from Lexmarks site

lexmark-inkjet-legacy-wJRE-1.0-1.amd64.deb.sh

It opens a window saying it will install the drivers
After accepting the license agreement, a new window pops up, saying

"   This operation requires root(administrative) privileges.
    Please enter the administrative password below:         "

but when I do it tells me the password is incorrect? I know I'm entering the correct password, I've even tried it with caps lock on/off number lock on/off and every other way I can think of to enter the same password, but I keep getting the same output.
My password works when I run synaptic and every other thing that needs root access. 

Anyone have any ideas about this? 
I figure it's a problem with the Lexmark software, but I'm a newb to linux so I don't know how else to do it. 
I tried searching through the install CD for the PPD file, but didn't find anything
I sent an email to Lexmark's tech support, but who knows how long that will take, so I thought I'd try here.

---

### Post by b.ash on 2011-08-31
Ahh, nevermind, I found the answer to this problem here:

[http://ubuntuforums.org/showthread.php?t=1831534&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=1831534&highlight=nautilus)

Printer works great now

---

### Post by TheBigH on 2012-06-10
I can confirm that the method given on page 57 of this thread works for a Lexmark X1290. I was able to get it running in linux using the Z600 driver. 

[http://ubuntuforums.org/showthread.php?t=49714&highlight=X1290+lexmark&page=57](http://ubuntuforums.org/showthread.php?t=49714&highlight=X1290+lexmark&page=57)

There's just a few little things you need to be aware of:

-You need libstdc++5 installed, and this can no longer be obtained in one step using sudo apt-get, I think because libstdc++6 supersedes it. You need to do it this way. On 64 bit the following should do the trick
```

wget  http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-20_amd64.deb 
dpkg-deb -x libstdc++5_3.3.6-20_amd64.deb ia64-libs 
sudo cp ia64-libs/usr/lib/libstdc++.so.5.0.7 /usr/lib64/ 
 wget  http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_20090808ubuntu2_amd64.deb 
dpkg-deb -x ia32-libs_20090808ubuntu2_amd64.deb ia32-libs 
sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib32/ 
cd /usr/lib64/ 
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5 
cd /usr/lib32 
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

```On 32 bit this worked for me:
```

wget  http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-20_i386.deb 
dpkg-deb -x libstdc++5_3.3.6-20_i386.deb libstdc++-files 
sudo cp libstdc++-files/usr/lib/libstdc++.so.5.0.7 /usr/lib/ 
cd /usr/lib/ 
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

```-the guide on page 57 says in step B-4 you should get some output after running ./z600
I got no output, even after editing /etc/fstab, but the method still worked.

If you edited fstab and the computer hangs at startup, boot to a command line and just comment out the line you added and all should be well.

I hope this helps someone, and thanks to ShadowMage for the original method.

---

### Post by VietCanada on 2012-06-13
I have finally opted for the ultimate solution.

I was having all kinds of issues with my Lexmark - hardware related. So I went out and bought an HP deskjet for about $100.

It took five minutes to unpack it, plug it in and do the 'add printer' thing to get a test page printed. No terminal, no downloading, no work arounds, no searching the net for virtual rubber bands and duct tape. It just works.

If you can do it, I'd recommend going to HP. The support is terrific. Lexmark is just a pita. You will kick yourself for not doing it sooner.

---

### Post by Geezanansa on 2012-09-08
All credit to and thank you to **black hole sun** for starting this  thread  and sharing how to get lexmark printers working in ubuntu.  

Just adding update for what worked to get my old lexmark x1270 working in ubuntu 12.04.

Referring to [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) was very handy for getting to grips of what and how to do simple tasks using Terminal.


Download and save the driver cjlz600le-cups-1.0-1.tar.gz (which Lexmark calls "Driver for RedHat Linux 9.0") from [http://support.lexmark.com](http://support.lexmark.com) using your favorite browser.

From terminal install alien and libstdc++5 which are z600cups dependencies
```
sudo apt-get install alien
```
```
sudo apt-get install libstdc++5
```

To unzip and install driver-give these commands from terminal
```
$mkdir Lexmark
$cd Downloads #or location of file downloaded from Lexmark website.
$mv CJLZ600LE-CUPS-1.0-1.TAR.gz ~/Lexmark
$cd Lexmark
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver. 
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script. 
$ tar -xvzf install.tar.gz # extract the contents produced by tail 
$ sudo alien --scripts -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz. 
$ sudo alien --scripts -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz. 
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place 
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place 
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries 
$ cd /usr/share/cups/model 
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
$ exit

```

Then connect printer and switch on and go to settings button at top right of unity desktop click and select printers.
Click Add
Select device from list and click forward
Leaving "Select printer from database" selected choose "Lexmark" and then click forward
Select Z600 v1.0-1 driver
Rename device and description to your liking and apply.

Reboot


Go  printing.

---

### Post by Samme Adema on 2012-09-25
Thank you very much. I followed the directions step by step and my Lexmark X1195 started to print.

---

### Post by Samme Adema on 2012-11-29
in Ubuntu 12.04, Lexmark X1195 printerpart works now; thank you; after upgrade to Ubuntu 12.10 scannerpart works fine with xscanimage;

---

### Post by TheBigH on 2012-12-28
Just an update to my previous thread:

the link I provided to get the libstdc++5 library is now broken. But you can download it from one of the mirrors listed at

[http://packages.debian.org/squeeze/i386/libstdc++5/download](http://packages.debian.org/squeeze/i386/libstdc++5/download)

---

### Post by michdal on 2012-12-31
> **Geezanansa said:**
> All credit to and thank you to **black hole sun** for starting this  thread  and sharing how to get lexmark printers working in ubuntu.  

Just adding update for what worked to get my old lexmark x1270 working in ubuntu 12.04.

Referring to [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) was very handy for getting to grips of what and how to do simple tasks using Terminal.


Download and save the driver cjlz600le-cups-1.0-1.tar.gz (which Lexmark calls "Driver for RedHat Linux 9.0") from [http://support.lexmark.com](http://support.lexmark.com) using your favorite browser.

From terminal install alien and libstdc++5 which are z600cups dependencies
```
sudo apt-get install alien
``````
sudo apt-get install libstdc++5
```To unzip and install driver-give these commands from terminal
```
$mkdir Lexmark
$cd Downloads #or location of file downloaded from Lexmark website.
$mv CJLZ600LE-CUPS-1.0-1.TAR.gz ~/Lexmark
$cd Lexmark
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver. 
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script. 
$ tar -xvzf install.tar.gz # extract the contents produced by tail 
$ sudo alien --scripts -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz. 
$ sudo alien --scripts -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz. 
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place 
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place 
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries 
$ cd /usr/share/cups/model 
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
$ exit

```Then connect printer and switch on and go to settings button at top right of unity desktop click and select printers.
Click Add
Select device from list and click forward
Leaving "Select printer from database" selected choose "Lexmark" and then click forward
Select Z600 v1.0-1 driver
Rename device and description to your liking and apply.

Reboot


Go  printing.

I tried your how-to for my Lexmark X1150 on Ubuntu 12.04. The installation went fine, the printer was detected correctly. However, it don't print anything. I'm at a loss what to do... Any suggestions? Thanks in advance.

---

