---
title: "HOWTO: Installing TiLP2 for Feisty"
date: 2007-04-29
forum: Tutorials
---

### Post by jpeach on 2007-04-29
TiLP II is an open source linking program for Texas Instruments calculators.  It runs on a number of OSes including Ubuntu but there is no deb package to install it.  While trying to get it working on Feisty I ran into a number of problems.  So, hopefully this tutorial will help others install this application with fewer headaches.  If you run into problems, join the user mailing list.  The developers have been very helpful. [http://lpg.ticalc.org/prj_tilp/mailing_list.html](http://lpg.ticalc.org/prj_tilp/mailing_list.html)

As of this writing, the most current release is 1.03.

Out of the box, Ubuntu (Desktop) does not have installed the tools needed to compile the software.  So, we need to get that.  We will need to use the command line interface to do this.  We can get a terminal window by:
Applications->Accessories->Terminal

We will need root access to do this.  There are two ways we can get these permissions based on how your computer is setup
# sudo su -
or
# su 

Now that we have root permissions we need to update our system and install several packages.
# apt-get update
# apt-get install libglade2-dev libusb-dev libgtk2.0-dev g++ gcc

TiLP II requires a newer version glib then what comes with Feisty.  So, we will need to download the source and install that.  
# wget [ftp://ftp.gtk.org/pub/glib/2.12/glib-2.12.11.tar.gz](ftp://ftp.gtk.org/pub/glib/2.12/glib-2.12.11.tar.gz)
# tar xzf glib-2.12.11.tar.gz
# cd glib-2.12.11
# ./configure
# make
# make install

In order to get the source code, go to the following web page (you may need to create an account) 
[http://www.ticalc.org/pub/unix/](http://www.ticalc.org/pub/unix/) and download

Search the page for the following source packages and download them.  Be careful as there are two versions of the files because tilp (version 1) is still be downloaded but development has stopped
tilibs2.tar.gz  (library files)
tilp2.tar.gz     (TiLP II program)

Go back to the command line interface and use the cd command to change to the directory where you downloaded tilibs2.tar.gz and tilp2.tar.gz

Unpack the following files
# tar xzf tilibs2.tar.gz
# tar xzf tilp2.tar.gz

Now, let us compile and install the files
# cd tilibs2

# tar xzf libticonv-1.0.1.tar.gz 
# tar xzf libtifiles2-1.0.4.tar.gz
# tar xzf libticables2-1.0.4.tar.gz
# tar xzf libticalcs2-1.0.5.tar.gz

# cd libticonv-1.0.1
# ./configure
# make
# make install

# cd ../libtifiles2-1.0.4
# ./configure
# make
# make install

# cd ../libticables2-1.0.4
# ./configure
# make
# make install

# cd ../libticalcs2-1.0.5
# ./configure
# make
# make install

# cd ../../tilp2-1.03/
# ./configure
# make
# make install

Now we have to setup the rules for using the USB sub-system.  We are going to give the group 'tilp' access to the TI USB interface.  Using your favourite edit as root create the following file
# nano /etc/udev/rules.d/25-ticables.rules

Put the following 4 lines in that file and save it.

BUS=="usb", ACTION=="add", SYSFS{idVendor}=="0451", SYSFS{idProduct}=="e001", MODE="660", GROUP="tilp"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="0451", SYSFS{idProduct}=="e003", MODE="660", GROUP="tilp"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="0451", SYSFS{idProduct}=="e004", MODE="660", GROUP="tilp"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="0451", SYSFS{idProduct}=="e008", MODE="660", GROUP="tilp"

Create the group and add the user account to the tilp group.  Replace USERNAME below with the name of the user you want to add to the group.  Repeat the usermod command for each user you want to give access to.
# groupadd -f tilp
# usermod -a --groups tilp USERNAME

The next time USERNAME logs in they will be part of the new tilp group.

To run the program, run the following command
# tilp

Comment:
I have been having some problems with a regular user being able to use the Direct Link cable on a TI89 Titanium.  There are some bugs in the firmware of that calculator.  If I run tilp as root, it works fine.

Here are some helpful references.
References:
Homepage: [http://lpg.ticalc.org/prj_tilp/](http://lpg.ticalc.org/prj_tilp/)
Mailing List: [http://lpg.ticalc.org/prj_tilp/mailing_list.html](http://lpg.ticalc.org/prj_tilp/mailing_list.html)

---

### Post by max-k on 2007-05-03
Hi, i have tried this and it works fine.
Thank you.
But my TI-84+ USB aren't recognized.
The left side of TILP is grey.
When i double-click on operating system and then on NEXT, TILP is closed and i have this error : "Erreur de segmentation (core dumped)".
Do tou have an idea on what's the problem ?

---

### Post by coffee on 2007-08-05
Thanks for the how to.

When I tried to compile tilp2-1.04 I got an error about the X libraries.  So I installed the file in the repos.  When I try and connect to my Ti-89 Titanium I get this error.

Msg: Error occurred while initializing the libusb.
Cause: Check that your cable is connected or not stalled. Check your libusb and usbfs, too.
System: Device or resource busy (errno = 16)

Not sure what to do next 

Thanks

---

### Post by RLovelett on 2008-01-17
Use the DirectLink and not USB option.
Also, remember to run tilp as sudo tilp.

---

### Post by supernix on 2009-05-28
I installed the tilII package and can't get the Nspire to be recognized.
I did get tilp running using sudo tilp but again trying to access the Nspire gets a seg fault. I am running Jaunty as well.

---

### Post by csmgj on 2011-11-29
Did y'all ever figure out how to fix the Segmentation Fault problem in TiLP2?

---

