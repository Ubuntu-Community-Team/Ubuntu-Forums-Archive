---
title: "server guidence"
date: 2012-10-11
forum: Server Platforms
---

### Post by markschum on 2012-10-11
Hi all, 

This was posted in the beginners forum and suggested I try here.

I am new to web development but am learning. I have 25 years in mainframe operations and IBM S/36, S/38 and Mainframe in both systems and application programming with Cobol, RPG, visual basic 6 and some C , forth , etc. 

I have running apache, PHP and mysql on a windows xp desktop.

I want to duplicate as much as possible a commercial webserver so am looking at Linux or one of the variants.  

I have downloaded Ububtu server 12.04 i386 and have either a DELL Optiplex G or a pentium 4 440mhz processor box to run it on. It will only be me running tests as I learn php, java script and mysql.  

I have a severe budget for this so need to use what I have if possible.  

Am I going in the right direction for this ?  

I dont want to waste the weekend trying to install this if its the wrong way to go.  
I dont need specifics on how to do anything, just guidence that the server bundle is right and the systems I have will run it.  

any advice appreciated. Thanks

---

### Post by kennethconn on 2012-10-11
The way I see it, you have two requirements:

1) Get it up and running and test it in terms of functionality and usability.

2) Once requirement 1 is met, see how it performs in a real-world scenario (multiple user connections, stress testing, server hardware).

For requirement 1, I see no reason why you could not set it up to run in Virtualbox (or similar) on your XP machine, at zero cost. I would not be in a position to advise you on requirement 2, sorry.

Good luck.

---

### Post by spynappels on 2012-10-12
Kennethconn is absolutely correct about VirtualBox being adequate for point 1, but if you have the hardware already, there are benefits to running the server on it's own hardware.

I've done both, and with the VirtualBox option it was sometimes frustrating to have to boot the host if I wanted to check something quickly on the test machine from my phone or tablet. Having the test server allowed the test machine online all the time without having the VB host powered. This only really applies if you will be accessing the test server from several different machines within your network, it is not an issue if you will only use the host to access the virtual test machine.

On a more general note, getting experience on a test server at home is a good idea, and when you are ready to migrate to a production hosted server, there are many options available. I use Linode after a recommendation on here, and am happy to recommend them on, I'm very happy with their service.

---

### Post by Lars Noodén on 2012-10-12
If you're the only one using the server than just about any hardware or even a virtual machine will do.  To install the lamp stack is easy:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Note the caret (^)

Also, note that perl  and python are pre-installed and in use already on your system so they do not need to be added, though you may wish to add certain modules depending on where your development interests take you.

---

### Post by coldraven on 2012-10-12
I have been experimenting with Ubuntu server to get some Apache and PHP skills.
I run it in VirtualBox on my Ubuntu laptop. You can download a ready made Virtulabox image from here:
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

The advantage for me is that if I mess it up I can quickly either restore from a VirtualBox "Snapshot" or just create a new one with the original image.

I recommend to always keep a log of what files or utilities you change and always backup config files before you edit them.

See also tasksel, it might come in handy
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

