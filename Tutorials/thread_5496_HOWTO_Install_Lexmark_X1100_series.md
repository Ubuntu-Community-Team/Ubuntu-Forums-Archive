---
title: "HOWTO: Install Lexmark X1100 series"
date: 2004-11-19
forum: Tutorials
---

### Post by Pionner on 2004-11-19
Firs of all, download the Z600 driver from this link [http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242)

Extract the file and rename it from  *z600cups-1.0-1.gz.sh* to *z600cups-1.0-1.tgz.*

Open it with your favourite text editor and remove the script from the begginig of the file.

Extract the tar and convert the two rpm packages whit alien ("sudo alien *.rpm")
Install both packages whit "sudo dpkg -i *.deb" and you got the driver installed.
Finally install it with the gnome printer dialog and select Lexmark -> X600 1.01 driver.

Enjoy  :grin:

NOTE: I had to restart gnome before installing the printer.
NOTE 2: Sorry for my bad english

---

### Post by bud111 on 2006-12-12
I'm having trouble extracting and installing the Z600 driver.
I've only gotten to the point where z600cups-1.0-1.gz.sh to z600cups-1.0-1.tgz has been downloaded to my desktop; after that I'm lost.
I do not know what script to remove from the beginning of the file, and I don't know to extract the tar and convert the two rpm packages, etc, etc.
Any help or simplification would be appreciated.

Thank you

---

### Post by ramonthomas on 2007-01-04
It seems like there's a few steps missing in this HOWTO on installing a printer driver for the Lexmark X1100. To add more complexity I'm running AMD64 version of Ubuntu.

So please post more details steps on setting this up.

thanks
Ramon

---

### Post by ianfp on 2007-11-04
The instructions on this thread didn't work for my X1150, but the ones on the following page did:

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

---

### Post by bodymind on 2008-01-21
There is a simple way to get lexmark x1100 series working....

go to: [http://localhost:631](http://localhost:631)

add a new printer, on the step where you have to choose the driver, browse your files and install the file in attach :popcorn:

now print all you can :cool:

---

### Post by alexandrupop on 2009-02-07
I tried the to install it using the custom ppd file but when I try to print a test page I have an error message saying :  	
Lexmark_X1100_Series_USB_1 (Default Printer) "Can't write page 1 header"
Has anyone else had any luck with this?

---

### Post by newonlinux on 2009-03-31
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

---

### Post by xlq on 2009-10-30
There is no libstdc++5 package in Karmic. What to do now?

(I'm on amd64)

---

### Post by newonlinux on 2009-11-02
[http://packages.debian.org/lenny/amd64/libstdc++5/download](http://packages.debian.org/lenny/amd64/libstdc++5/download)

click this link and click on your area

---

### Post by newonlinux on 2009-11-02
Hi, I've not used this for ages,
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

---

### Post by w2vy on 2009-11-14
Will this driver help when configuring x1100 via samba or is strictly for a local printer?

tom

---

### Post by newonlinux on 2009-11-15
if your using windows, install the "generic" driver "microsoft publisher color printer", well this works for vista anyway.

If it's on Ubuntu you should be using the driver from this thread.

---

### Post by w2vy on 2009-11-15
Windows XP Desktop USB Lexmark X1100

Laptop Ubuntu 9.10 wants to print via samba to network printer on the XP Desktop

So I need the driver on the laptop.

right?
tom

---

### Post by Nicola Panozzo on 2009-12-26
I get an error whe I try the commands chown root and chgrp root.

I get message:  cannot access `usr/lib/cups/filter/rastertoz600': No such file or directory

Could you please advise?

---

### Post by w2vy on 2009-12-27
> **Nicola Panozzo said:**
> I get an error whe I try the commands chown root and chgrp root.

I get message:  cannot access `usr/lib/cups/filter/rastertoz600': No such file or directory

Could you please advise?

Should it be:

/usr/lib/cups/filter/rastertoz600

---

### Post by jlownie on 2012-05-13
Update for 2012 - More modern instructions [here]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z600%20Series%20Printers").  Follow the instructions for the Z600 printers.

---

