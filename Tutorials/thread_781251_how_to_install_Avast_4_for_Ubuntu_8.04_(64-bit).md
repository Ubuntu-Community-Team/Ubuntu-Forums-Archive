---
title: "how to install Avast 4 for Ubuntu 8.04 (64-bit)"
date: 2008-05-04
forum: Tutorials
---

### Post by linuxed on 2008-05-04
[color=red]**UPDATED:**[/color] Guide has been updated for v8.10

Avast.com currently offers a free Avast download for Ubuntu.  Unfortunately they only provide a deb package for 32-bit systems.  Avast actually runs quite well on a 64-bit system, but the installation requires a few extra steps.  This guide will walk you through the process of installing Avast on a 64-bit system.


[list=1]
[*]First off, install the ia32-libs package if it's not already installed.
```

sudo apt-get install ia32-libs

```
[_[color=red]**The ia32-libs package must be >= 2.2ubuntu18.**[/color]_](http://packages.ubuntu.com/intrepid/amd64/ia32-libs/download)


[*]Download the Avast debian package _[here](http://www.avast.com/eng/download-avast-for-linux-edition.html)_ and save it to your desktop.  The instructions below assume that the avast package can be found on your desktop so it's important that you choose your desktop as the download location.
[*]After it's downloaded change to your desktop folder.
```

cd /home/YourUserName/Desktop

```
[*]Install the avast deb package.
```

sudo dpkg --force-architecture -i avast4workstation_1.3.0-2_i386.deb

```
[*]You need to make sure that all of the required libraries can be found in your /usr/lib32 folder.  To help simplify this task I've created a libs package for avast and attached it to this post.  Simply download the attachment and then type the following:
```

sudo dpkg -i ia32-avast-libs.deb

```
[*]After the packages are installed make sure that all of the required libraries can be found.  Type the following:
```

ldd /usr/lib/avast4workstation/bin/avastgui
ldd /usr/lib/avast4workstation/bin/avast

```
[*]Scroll through both lists and make sure that none of them say 'Not found'.  As long as you didn't find any libraries listed as 'not found' then you should now be able to run Avast from your Applications menu.
[/list]


**Library Not Found**
If any say not found then you may need to install additional packages or as a last resort manually extract the libraries from a package into your /usr/lib32 folder.  [_You can do a package contents search here._](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=contents&keywords=libesmtp.so.5)  Just enter the name of the missing library and search for a package that contains it.  Once you've found the package download the i386 version and use file-roller to extract the missing library into your /usr/lib32 folder.


**To uninstall this package simply type the following:**
```

sudo dpkg -r avast4workstation

```

---

### Post by WeEatVista on 2008-06-06
I'm sorry to bump this thread, but I just have one question. How do I remove avast antivirus once I install it using this tutorial?

Thanks in advance,
WeEatVista

---

### Post by Lakjin on 2008-07-15
anyone varify this works?

---

### Post by veiloctane on 2008-07-25
great tutorial but how to i increase the font in avast application because i cannot read anything. all the text is too small

---

### Post by Kow on 2008-07-25
> **WeEatVista said:**
> I'm sorry to bump this thread, but I just have one question. How do I remove avast antivirus once I install it using this tutorial?

Thanks in advance,
WeEatVista

As you would any normal Ubuntu package. Either from synaptic or from command-line. The name of the package is avast4workstation. Perhaps the author can add a tidbit about uninstalling.

Yes, the tutorial works as is.

---

### Post by veiloctane on 2008-07-26
> **veiloctane said:**
> great tutorial but how to i increase the font in avast application because i cannot read anything. all the text is too small

found the answer:[http://ubuntuforums.org/showthread.php?t=229128](http://ubuntuforums.org/showthread.php?t=229128)


If you like to use GTK 2.x then work your way to the avast directory.
Code:

cd /usr/lib/avast4workstation

Then just remove the
Code:

sudo rm -rf lib-x11/

and
Code:

sudo rm -rf lib-gtk2/



confirmed working in ubuntu studio!

---

### Post by beneedict on 2008-07-26
why don't you simply use
```
 sudo dpkg --force-architecture -i avast4workstation_1.0.8-2_i386.deb
```
?
the only disadvantage I see is the missing proper entry in the menu but this is no big deal to do yourselves.

works fine for me in Ubuntu!

---

### Post by alex199020 on 2008-07-30
I did this to install avast and it worked fine. But then i messed up ubuntu so did a full reinstall and did it again and it didn't work. Its in my system tools but when i click it the loading sign appears for less than a second and thats it. 
How do i completly reverse the process so i can try it again with out formatting again?
Thanks for the help!

---

### Post by beneedict on 2008-08-02
> **alex199020 said:**
> I did this to install avast and it worked fine. But then i messed up ubuntu so did a full reinstall and did it again and it didn't work. Its in my system tools but when i click it the loading sign appears for less than a second and thats it. 
How do i completly reverse the process so i can try it again with out formatting again?
Thanks for the help!

First of all, which of the installation procedures did you follow? 
And NO, you do not need to reinstall Ubuntu every time something does not work (forget your Windows behaviour ;) ). And in the case if you were not very experienced with linux: you do NOT need to have a virus scan installed (linux is safe unless you do not install packages from strange sources). The virus scan is only there to occassionally look for viruses on your windows installation.

---

### Post by xTOGUROx on 2008-08-08
i have installed Avast in Ubuntu 8. however i can only run it by opening a terminal and execute avastgui command, i cant find any shortcuts anywhere. how can i create a shortcut to run avast with just a few clicks?

---

### Post by underground on 2008-08-10
Me too..can't find any shortcuts

---

### Post by zithedragon on 2008-08-12
thanks for this but one question dose it mean something is wrong when it closes out without warning while scanning and is there a way to fix it

i have a duel boot with windows vista and the window side has a virus im trying to find that keeps shutting off the explorer

---

### Post by beneedict on 2008-08-15
Sadly for the shortcut you have to use the full and rather complicated procedure in post #1. A workaround for klickers is to right-click on the applications button and edit the menu by adding the "avastgui" command into some submenu. The avast icon is found in /usr/lib/avast4workstation/share/avast/icons/avast-appicon.png
or just choose one of the available ones shown if you click on the icon button. I cannot give you a more detailed description of the procedure with the exact name of the menues since I am running a German ubuntu installation. Make use of your brain ;) Good luck!

---

### Post by StephSD3 on 2008-10-07
Thanks, this has been very helpful :KS
The only problem that I encountered was that I wasn't able to create a launcher in the /Applications/Systemtools ... So I just created a shortcut on my Desktop.

[COLOR="Blue"]edit: Thanks beneedict, its indeed a lot easier your way (for first timers like me)[/COLOR]

---

### Post by lanr01 on 2008-10-07
Wow... worked great.. Only had to change things a bit as I am not running the 64 version... Very easy to follow, which for a newbie to linux was a plus..


A big thank you...

---

### Post by lucanuscervus on 2009-01-21
I can confirm that works in 8.10 64bits.

---

### Post by brunoscunha on 2009-01-22
Great tutorial :D and it worked flawlessly

---

### Post by yateendra on 2009-06-16
I'm new to Linux and was interested in trying Avast with 64-bit Kubuntu 9.04. Following the above instructions and installing the attached "deb" file seems to install the needed avast libraries, but not avast itself. Is there a missing step (such as an explicit install of the Avast4 "deb" downloaded to the desktop)? Or is that process supposed to occur as a result of installing the attached library? I will note that in addition to a OS version update, the Avast "deb" file has also been updated since this article was written.

If installing on 9.04 is too much to ask, do you think it's best to try to undo the effect of installing the authors attached libraries, or just let it go? (I backed up the OS before trying this).

---

### Post by linuxed on 2009-06-18
Apparently I left out a step when I updated the guide. :) Sorry for the confusion.  The guide has now been corrected to include the extra step.  In order to complete the installation just type the following from the folder containing the avast deb package (the example below assumes it can be found in your Desktop folder).
```

cd /home/yourUserName/Desktop
sudo dpkg --force-architecture -i avast4workstation_1.3.0-2_i386.deb

```

---

### Post by yateendra on 2009-06-22
The revised instructions worked great!--Installed on 64-bit Kubuntu 9.04.

I had hoped to use Avast for realtime Email scanning, but this feature is not available in the free "home" edition (it's available in the server edition). I'm migrating from Thunderbird in Windows and have many mail filters, but I'm not sure they can be converted by the Kmail program (Kmail is attractive for its integration with clamav). I suppose AVG Antivirus might be an option (am using it in Windows, but haven't been too enthusiastic in its latest direction--it's seeming to become a resource-hog).

All the Best.

---

### Post by yateendra on 2009-06-23
I've been exploring command-line options for possibly setting up Avast in a script with my Email client as a means of scanning mail shortly after it's received.

Two features needed for practical use are indeed available in the home version. Once installed, you can enter the following on the command line for more information:

```
avast --help
``````
avast-update --help
```

---

### Post by ssk.green on 2009-07-06
thank you so much:guitar:

---

### Post by naklinaam on 2009-07-15
Hi,
I am on 9.04 64 bit. 
I followed these instructions and was successfully(?) able to install Avast!
The question mark is because when I ran the ldd commands to check the libraries, I found two missing.

libesmtp.so.5
libavastengine-4.so.7

I was able to use synaptic manager to install libesmtp.so.5 but have not been able to get libavastengine-4.so.7 even after a minimal amount of googling.

I do see the menu entry (Applications > Accesoties > avast! Antivirus) along with a good icon and everything. 
I even ran it and the app did its stuff and gave me the reportof what it found (or rather did not ;)..).

So my question is, how did it work without libavastengine-4.so.7? Am I under some illusion that it worked while it actually did not do anything?
In either case, how can I install libavastengine-4.so.7.

I was unable to locate the attachment refered to in post#1 else I guess this question would arise.

update:
Duh.....
I just looked for the attachment again and found it (I guess I should have opened my eyes the first time round). However, the question still remains, how did it work with a package missing. What does this package do. It sounds like it is a critical package (with the word engine and all). Anybody??? or do we go to the avast forum?

---

### Post by linuxed on 2009-07-16
The package attached to the first post contains all of the missing libraries including a symlink for the avast engine.  You don't need to manually install the esmtp libraries because they're included in the package.  The package contents are listed below.
```

lib32:
4096 2009-07-16 15:32 esmtp
52 2009-07-16 15:32 libavastengine-4.so.7 -> /usr/lib/avast4workstation/lib/libavastengine-4.so.7
823 2008-06-06 15:50 libesmtp.la
17 2009-07-16 15:32 libesmtp.so.5 -> libesmtp.so.5.1.5
63280 2008-06-06 15:50 libesmtp.so.5.1.5

lib32/esmtp:
855 2008-06-06 15:50 sasl-cram-md5.la
9512 2008-06-06 15:50 sasl-cram-md5.so
834 2008-06-06 15:50 sasl-login.la
5388 2008-06-06 15:50 sasl-login.so
834 2008-06-06 15:50 sasl-plain.la
5384 2008-06-06 15:50 sasl-plain.so

```

---

### Post by master_kernel on 2009-07-16
Scanning now - but I'm getting errors: File was not tested due to configuration details.

---

### Post by linuxed on 2009-07-17
> **master_kernel said:**
> Scanning now - but I'm getting errors: File was not tested due to configuration details.
I've occasionally encountered some errors with the Quick Scan option.  If for some reason the Quick Scan throws an error I would suggest sticking with the Standard or Thorough Scan options.

You can also delete the configuration folder which should reset everything.
```

rm -R ~/.avast

```

---

### Post by mcfunthomas on 2009-08-23
When I try to install avast on my laptop I get 

root@LAPSUS:<my_directory_path># dpkg --force-architecture -i avast4workstation_1.3.0-2_i386.deb
dpkg-deb: --control avast4workstation_1.3.0-2_i386.deb /var/lib/dpkg/tmp.ci
(Reading database ... 183906 files and directories currently installed.)
Unpacking avast4workstation (from avast4workstation_1.3.0-2_i386.deb) ...
dpkg-deb: --fsys-tarfile avast4workstation_1.3.0-2_i386.deb
cp: cannot stat `avast4workstation_1.3.0-2_i386.deb': No such file or directory
cd: 52: can't cd to debian/*/
dpkg: error processing avast4workstation_1.3.0-2_i386.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 avast4workstation_1.3.0-2_i386.deb

Has anybody got any idea what's goin on?
I downloaded the package twice (thought it was corrupted) but same effect. :(

---

### Post by linuxed on 2009-08-23
I'm not sure if this will help but you might try specifying the full path to the deb file.
```

sudo dpkg --force-architecture -i /home/YourUserName/Desktop/avast*.deb

```

---

### Post by mcfunthomas on 2009-08-25
This is what I got applying your suggestion:
```
mcfunthomas@LAPSUS:~$ sudo dpkg --force-architecture -i /home/mcfunthomas/Desktop/avast4workstation_1.3.0-2_i386.deb
[sudo] password for mcfunthomas: 
dpkg-deb: --control /home/mcfunthomas/Desktop/avast4workstation_1.3.0-2_i386.deb /var/lib/dpkg/tmp.ci
(Reading database ... 184284 files and directories currently installed.)
Unpacking avast4workstation (from .../avast4workstation_1.3.0-2_i386.deb) ...
dpkg-deb: --fsys-tarfile /home/mcfunthomas/Desktop/avast4workstation_1.3.0-2_i386.deb
parsechangelog/debian: warning:     debian/changelog(l5): badly formatted trailer line
LINE:  -- root <root@localhost>  Wed, 26 Aug 2009 01:18:53 AM +0200
parsechangelog/debian: warning:     debian/changelog(l5): found eof where expected more change data or trailer
Use of uninitialized value $v in pattern match (m//) at /usr/share/perl5/Dpkg/Fields.pm line 229, <STDIN> line 5.
Use of uninitialized value $v in pattern match (m//) at /usr/share/perl5/Dpkg/Fields.pm line 229, <STDIN> line 5.
dch: fatal error at line 467:
Cannot find usr/share/doc/avast4workstation/changelog!
Are you in the correct directory?
(You could use --create if you wish to create this file.)
Setting up avast4workstation (1.3.0~11ubuntu1) ...

Processing triggers for man-db ...
mcfunthomas@LAPSUS:~$ 
```Different but still errors. :(

---

### Post by slightlystoopid on 2009-08-26
> **mcfunthomas said:**
> When I try to install avast on my laptop I get 

root@LAPSUS:<my_directory_path># dpkg --force-architecture -i avast4workstation_1.3.0-2_i386.deb
dpkg-deb: --control avast4workstation_1.3.0-2_i386.deb /var/lib/dpkg/tmp.ci
(Reading database ... 183906 files and directories currently installed.)
Unpacking avast4workstation (from avast4workstation_1.3.0-2_i386.deb) ...
dpkg-deb: --fsys-tarfile avast4workstation_1.3.0-2_i386.deb
cp: cannot stat `avast4workstation_1.3.0-2_i386.deb': No such file or directory
cd: 52: can't cd to debian/*/
dpkg: error processing avast4workstation_1.3.0-2_i386.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 avast4workstation_1.3.0-2_i386.deb

Has anybody got any idea what's goin on?
I downloaded the package twice (thought it was corrupted) but same effect. :(

I'm getting the exact same error. I did a fresh install of ubuntu today on a usb flash drive for the soul purpose of doing virus scans of others' windows machines. I started with a command line only system and have only installed xfce4 and ia32-libs. Anyone have any unresolved dependency ideas? or perhaps there's some configuration I'm missing?

---

### Post by slightlystoopid on 2009-08-26
> **mcfunthomas said:**
> This is what I got applying your suggestion:
```
mcfunthomas@LAPSUS:~$ sudo dpkg --force-architecture -i /home/mcfunthomas/Desktop/avast4workstation_1.3.0-2_i386.deb
[sudo] password for mcfunthomas: 
dpkg-deb: --control /home/mcfunthomas/Desktop/avast4workstation_1.3.0-2_i386.deb /var/lib/dpkg/tmp.ci
(Reading database ... 184284 files and directories currently installed.)
Unpacking avast4workstation (from .../avast4workstation_1.3.0-2_i386.deb) ...
dpkg-deb: --fsys-tarfile /home/mcfunthomas/Desktop/avast4workstation_1.3.0-2_i386.deb
parsechangelog/debian: warning:     debian/changelog(l5): badly formatted trailer line
LINE:  -- root <root@localhost>  Wed, 26 Aug 2009 01:18:53 AM +0200
parsechangelog/debian: warning:     debian/changelog(l5): found eof where expected more change data or trailer
Use of uninitialized value $v in pattern match (m//) at /usr/share/perl5/Dpkg/Fields.pm line 229, <STDIN> line 5.
Use of uninitialized value $v in pattern match (m//) at /usr/share/perl5/Dpkg/Fields.pm line 229, <STDIN> line 5.
dch: fatal error at line 467:
Cannot find usr/share/doc/avast4workstation/changelog!
Are you in the correct directory?
(You could use --create if you wish to create this file.)
Setting up avast4workstation (1.3.0~11ubuntu1) ...

Processing triggers for man-db ...
mcfunthomas@LAPSUS:~$ 
```Different but still errors. :(

after this is done, we have a gui, but the scans and updates are inoperable. :confused:

EDIT:
I'm not sure it's relevant since there was an installation error but I guess I'll add that the error avast4workstation gives during update is "Unable to write to body."

EDIT:
This isn't limited to avast. [http://ubuntuforums.org/showthread.php?t=999532](http://ubuntuforums.org/showthread.php?t=999532)

---

### Post by mcfunthomas on 2009-08-31
> **slightlystoopid said:**
> after this is done, we have a gui, but the scans and updates are inoperable. :confused:

EDIT:
I'm not sure it's relevant since there was an installation error but I guess I'll add that the error avast4workstation gives during update is "Unable to write to body."

EDIT:
This isn't limited to avast. [http://ubuntuforums.org/showthread.php?t=999532](http://ubuntuforums.org/showthread.php?t=999532)as far as my installation ... avast seems to work: updates, finds+removes threats n viruses (on windows partition). It has problems with linux partitions, though; weird indeed. I need to see to that.

---

### Post by ccnjim on 2009-09-03
Thanks for the tutorial. Very easy to follow for a novice.

---

### Post by demoniodojo on 2009-11-09
Great info! Works perfectly in Ubuntu Server 9.04!

---

### Post by After8eighT on 2009-12-15
Thanks! works fine!! :)

---

### Post by Astrals on 2010-01-15
I use ubuntu-9.10-alternate-amd64.


 My original post:
[[COLOR=Blue]http://forum.avast.com/index.php?topic=53107.0[/COLOR]]("http://forum.avast.com/index.php?topic=53107.0")

Got it working again via command line.
It turned out that I needed to install **ia32-libs**.
Got the idea from:
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=781251[/COLOR]]("http://ubuntuforums.org/showthread.php?t=781251")

That was all I installed, now works great once again via terminal.

Looks like it was an update that stopped it from working and not my fault. (good news for me).

Thank you everybody for your help with this it was much appreciated and as usual I posted my results for good news.

---

### Post by tnewt on 2010-02-14
I'm being a bit snarky here, but if Avast can't even bother to offer a 64 bit version of their Linux virus scanner, then you have to wonder about their commitment to Linux, and, as a result, the quality of their Linux scanner.

Just sayin'.

(I mean, they sure as heck offer a 64 bit version of their Windows scanner.)

---

### Post by crash123 on 2010-04-04
Confirmed to work with 10.04 Beta 1, 64-bit. Awesome directions, thanks!

---

### Post by alexdelprogramador on 2010-04-04
why do we need avast for linux??

to scan a weack windows partition??

ive ever installed an antivirus under linux

it havent any logical use in a system wich doesnt have any viruses.

---

### Post by linuxed on 2010-04-05
If anyone encounters an error after updating the Avast signatures you'll need to perform the following steps.
```

sudo gedit /etc/init.d/rcS

```
Copy the following and paste it before the "exec /etc/init.d/rc S" line.
```

echo 128000000 > /proc/sys/kernel/shmmax

```
Save and close the file. You should now be able to run Avast with the latest signatures.

@alexdelprogramador
That was an incredibly shortsighted comment.  Windows viruses may not be able to infect Linux systems directly but many Linux users do have Wine installed or perhaps a Windows virtual machine.  [Clicking on an infected exe file can infect the Wine installation](http://74.125.95.132/search?q=cache:SqUFdmwvt4MJ:blog.opensourcenerd.com/i-can-haz-virus+virus+infect+wine&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a) or by accessing an infected file through a shared folder from a virtual machine can infect the guest OS.  These are not major issues and can be remedied by simply reinstalling the virtual machine or purging the Wine installation, but those hassles can be avoided by simply scanning any Windows files that you download prior to executing them.  You also have to keep in mind that the majority of viruses spread through email and the majority of computer users do have Windows installed on their pc.  So by downloading a windows file, attaching it to an email and sending it to someone running Windows without scanning it you could be compromising the security of that person's pc.  And there *are* native Linux viruses such as rootkits so making the statement that Linux viruses don't exist is quite a exaggeration.  A virus can also be something as simple as a javascript that causes your browser to crash which is not limited to any specific platform.

---

### Post by wesamer on 2010-04-10
> **linuxed said:**
> If anyone encounters an error after updating the Avast signatures you'll need to perform the following steps.
```

sudo gedit /etc/init.d/rcS

```Copy the following and paste it before the "exec /etc/init.d/rc S" line.
```

echo 128000000 > /proc/sys/kernel/shmmax

```Save and close the file. You should now be able to run Avast with the latest signatures.

@alexdelprogramador
That was an incredibly shortsighted comment.  Windows viruses may not be able to infect Linux systems directly but many Linux users do have Wine installed or perhaps a Windows virtual machine.  [Clicking on an infected exe file can infect the Wine installation]("http://74.125.95.132/search?q=cache:SqUFdmwvt4MJ:blog.opensourcenerd.com/i-can-haz-virus+virus+infect+wine&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a") or by accessing an infected file through a shared folder from a virtual machine can infect the guest OS.  These are not major issues and can be remedied by simply reinstalling the virtual machine or purging the Wine installation, but those hassles can be avoided by simply scanning any Windows files that you download prior to executing them.  You also have to keep in mind that the majority of viruses spread through email and the majority of computer users do have Windows installed on their pc.  So by downloading a windows file, attaching it to an email and sending it to someone running Windows without scanning it you could be compromising the security of that person's pc.  And there *are* native Linux viruses such as rootkits so making the statement that Linux viruses don't exist is quite a exaggeration.  A virus can also be something as simple as a javascript that causes your browser to crash which is not limited to any specific platform.

hu there ,

I followed these instructions and still not working!!!!

---

### Post by linuxed on 2010-04-10
The rcS file should look like the following.
```

#! /bin/sh

echo 128000000 > /proc/sys/kernel/shmmax
exec /etc/init.d/rc S

```
Make sure to restart your pc after modifying the rcS file.  If that still doesn't work then delete your Avast configuration files.
```

rm -R -f ~/.avast

```

---

### Post by indiepop on 2010-04-25
Installed on Ubuntu 10.04 TLS RC AMD64 without problem by following the steps above exactly as described without variation.  Runs fine as well, thank you.

---

### Post by Old Marcus on 2010-05-03
Installed Avast on Linux Mint 8 x64 using the instructions above, worked fine. I do have a problem however. I just updated the database and avast will no longer start. Is this because it's running on x64? and is this fixable?

The error message:

An error occured in avast! engine: Invalid argument

---

### Post by Old Marcus on 2010-05-18
Any hope of help? Or does no one know?

---

### Post by howefield on 2010-05-18
> **Old Marcus said:**
> Any hope of help? Or does no one know?

Did you read post 40 in this thread, or did it not work for you ?

An alternative would be to use a 64 bit application like Bitdefender. Much as I like Avast on my windows machines, I prefer to run 64 bit applications on a 64 bit system.

---

### Post by Old Marcus on 2010-05-18
> **howefield said:**
> Did you read post 40 in this thread, or did it not work for you ?

An alternative would be to use a 64 bit application like Bitdefender. Much as I like Avast on my windows machines, I prefer to run 64 bit applications on a 64 bit system.

Damn, I really need to check threads properly. Sorry about that, and thanks for pointing it out.

---

### Post by create.vibe on 2010-05-24
Thanks!  This worked great - using Ubuntu 10.04

---

### Post by 1dbzfanjake on 2010-06-01
Awesome!!! Thank you so much for going through all the steps for downloading avast! The only little error i came up with, which was easily remedied, was that the addition library that you atttached, ia32-avast-libs.deb, was named ia32-avast-libs.download when I tried to locate it on my laptop. This probably happened by me, but whatever. Thank you once again

---

### Post by JochenK on 2010-06-12
thanks for this tutorial. it was my first achievement of the evening that actually worked :p

cheers

---

### Post by Usuzumizakura on 2010-09-21
I have no privilege to download the attachment:(
 I am a novice and just have my exploration in Ubuntu.
How can I get a sufficient privilege?

---

### Post by linuxed on 2010-09-21
As long as you're logged in you should be able to download the attachment.  Just log in and then click [this link.](http://ubuntuforums.org/attachment.php?attachmentid=107895&d=1238262808)  Save it to your desktop, then type the following.
```

cd ~/Desktop
sudo dpkg -i ia32-avast-libs.deb

```

---

### Post by makelol on 2010-10-25
Hi, the install work nice, but now i can get the registration code for avast.
tried 2 times and still no success.

---

### Post by ibayley on 2010-10-31
Thank you so much for taking the time to post this install step by step.

---

### Post by frankduffey on 2011-03-28
> **linuxed said:**
> Apparently I left out a step when I updated the guide. :) Sorry for the confusion.  The guide has now been corrected to include the extra step.  In order to complete the installation just type the following from the folder containing the avast deb package (the example below assumes it can be found in your Desktop folder).
```

cd /home/yourUserName/Desktop
sudo dpkg --force-architecture -i avast4workstation_1.3.0-2_i386.deb

```


What about the registration code I can not run the free addition without this code that really stinks I was running clam which did not require a code I have requested a install code but so far nothing??? Why is this required for a free addition of the software????:(

---

### Post by jdunn on 2011-04-22
Has anyone tried this on Natty, yet?

---

### Post by Adamskilocropolis on 2011-04-23
Hi there, I just registered to say thank you to Linuxed for putting up this guide! (finally got around to registering, I've only had Ubuntu since September...:)).

Ubuntu has proven to be an awesome, painless faster, easier and friendlier switch from XP for me, largely thanks to these forums, thank you! :) Maybe one day I could be of help to someone else (doubtful, but maybe)

---

### Post by jdunn on 2011-04-24
The guide does not seem to work for Natty.  I'm not sure why but I noticed the libesmtp5 package is a dependency for Avast but the package does not exist in Natty.  I can get Avast to run and to scan using the default virus signature file but if I try to update the signatures, Avast displays an error message and quits.

---

### Post by jdunn on 2011-04-24
Looks like the problem and the solution is [HERE]("http://forum.avast.com/index.php?PHPSESSID=6oan7f26ole1i24d1p1rr0ptf5&topic=57775.0").

---

### Post by Black_Sirrah239 on 2011-11-05
First, the downloads are broken.
Second, it says  "libavastengine-4.so.7 => not found" and "libesmtp.so.5 => not found". How do i fix this?

---

### Post by northd_tech on 2011-11-11
> **Black_Sirrah239 said:**
> First, the downloads are broken.
Second, it says  "libavastengine-4.so.7 => not found" and "libesmtp.so.5 => not found". How do i fix this?

Although **this** old thread states to be for Ubuntu 8,04, I was able to get Avast 4 partially running under 64-bit Ubuntu Lucid Lynx 10.04.3 LTS.  Now Avast is throwing some error message(s) at me though and will not start up- I'll probably try the above fix after reading more about it.

I posted some links to download avast at my post #1 here:

[http://ubuntuforums.org/showthread.php?t=1867564](http://ubuntuforums.org/showthread.php?t=1867564)

That may or may not fix your missing libraries and you may see the same error messages that I'm seeing now.  Also, I've only been able to find a 32-bit .DEB package (64 bit Avast needs some hackish 'workarounds' using the tarball that haven't been too 'clean' so far).

FWIW, my 'hackish' setup currently tells me this:

> **locate libavastengine**

/lib/avast4workstation/lib/libavastengine-4.so.7
/lib/avast4workstation/lib/libavastengine-4.so.7.0.5
/usr/src/avast4workstation-1.3.0/lib/avast4workstation/lib/libavastengine-4.so.7
/usr/src/avast4workstation-1.3.0/lib/avast4workstation/lib/libavastengine-4.so.7.0.5
/usr/src/avast4workstation-1.4.0/lib/avast4workstation/lib/libavastengine-4.so.7
/usr/src/avast4workstation-1.4.0/lib/avast4workstation/lib/libavastengine-4.so.7.0.5> **locate libesmtp**

/lib/avast4workstation/lib-esmtp/libesmtp.so.5
/lib/avast4workstation/lib-esmtp/libesmtp.so.5.1.4
/usr/share/doc/avast4workstation-1.4.0/libs/libesmtp-1.0.3r1-avast-reloc.patch
/usr/src/avast4workstation-1.3.0/lib/avast4workstation/lib-esmtp/libesmtp.so.5
/usr/src/avast4workstation-1.3.0/lib/avast4workstation/lib-esmtp/libesmtp.so.5.1.4
/usr/src/avast4workstation-1.3.0/share/doc/avast4workstation-1.3.0/libs/libesmtp-1.0.3r1-avast-reloc.patch
/usr/src/avast4workstation-1.4.0/lib/avast4workstation/lib-esmtp/libesmtp.so.5
/usr/src/avast4workstation-1.4.0/lib/avast4workstation/lib-esmtp/libesmtp.so.5.1.4
/usr/src/avast4workstation-1.4.0/share/doc/avast4workstation-1.4.0/libs/libesmtp-1.0.3r1-avast-reloc.patch


It looks like I might have a conflict with those 1.3.0 vs. 1.4.0 libraries above- I will try blasting out those "1.3.0" versions (and possibly my whole Avast setup and starting over).

---

### Post by northd_tech on 2011-11-11
> **northd_tech said:**
> 
It looks like I might have a conflict with those 1.3.0 vs. 1.4.0 libraries above- I will try blasting out those "1.3.0" versions ...

Nope, it's still telling me "Avast! Error: An error occurred in avast! engine: Invalid argument"

Here are the last lines of **~/.avast/log/avastgui.log**:

>  2    2011-11-03 06:43:08    An error occured in avast! engine: Invalid argument
3    2011-11-03 06:43:08    Error while initializing avast! engine: Invalid argument.
2    2011-11-03 06:43:19    An error occured in avast! engine: Invalid argument
3    2011-11-03 06:43:19    Error while initializing avast! engine: Invalid argument.
2    2011-11-04 10:53:06    An error occured in avast! engine: Invalid argument
3    2011-11-04 10:53:06    Error while initializing avast! engine: Invalid argument.
2    2011-11-04 10:53:16    An error occured in avast! engine: Invalid argument
3    2011-11-04 10:53:16    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 13:36:02    An error occured in avast! engine: Invalid argument
3    2011-11-10 13:36:02    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 13:36:33    An error occured in avast! engine: Invalid argument
3    2011-11-10 13:36:33    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 13:36:45    An error occured in avast! engine: Invalid argument
3    2011-11-10 13:36:45    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 13:37:31    An error occured in avast! engine: Invalid argument
3    2011-11-10 13:37:31    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 13:47:41    An error occured in avast! engine: Invalid argument
3    2011-11-10 13:47:41    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 14:42:45    An error occured in avast! engine: Invalid argument
3    2011-11-10 14:42:45    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 14:42:54    An error occured in avast! engine: Invalid argument
3    2011-11-10 14:42:54    Error while initializing avast! engine: Invalid argument.
0    2011-11-10 15:14:06    Updated virus database to version 111110-0, 11/10/2011.
2    2011-11-10 19:40:39    An error occured in avast! engine: Invalid argument
3    2011-11-10 19:40:39    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 19:41:09    An error occured in avast! engine: Invalid argument
3    2011-11-10 19:41:09    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 19:49:32    An error occured in avast! engine: Invalid argument
3    2011-11-10 19:49:32    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 19:49:47    An error occured in avast! engine: Invalid argument
3    2011-11-10 19:49:47    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 19:50:01    An error occured in avast! engine: Invalid argument
3    2011-11-10 19:50:01    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 19:54:47    An error occured in avast! engine: Invalid argument
3    2011-11-10 19:54:47    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 19:55:44    An error occured in avast! engine: Invalid argument
3    2011-11-10 19:55:44    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 20:42:26    An error occured in avast! engine: Invalid argument
3    2011-11-10 20:42:26    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 21:29:51    An error occured in avast! engine: Invalid argument
3    2011-11-10 21:29:51    Error while initializing avast! engine: Invalid argument.
2    2011-11-10 21:43:06    An error occured in avast! engine: Invalid argument
3    2011-11-10 21:43:06    Error while initializing avast! engine: Invalid argument.
2    2011-11-11 07:08:45    An error occured in avast! engine: Invalid argument
3    2011-11-11 07:08:45    Error while initializing avast! engine: Invalid argument. 

I'll try a clean restart, since I've been running for quite a while and just recently made that "1.3.0" library change.

---

### Post by northd_tech on 2011-11-11
> **northd_tech said:**
> Nope, it's still telling me "Avast! Error: An error occurred in avast! engine: Invalid argument"

This post #2 had a fix that seems to have worked for me (although one should ALWAYS use **gksu gedit** instead of 'sudo' to avoid messing up file permissions from what I have read):

[http://ubuntuforums.org/showthread.php?p=10136473#post10136473](http://ubuntuforums.org/showthread.php?p=10136473#post10136473)

Briefly, this is the fix:

```
gksu gedit /etc/sysctl.conf
```Add this to the bottom of that file that gedit opens:

> # Workaround for Avast [4] antivirus error preventing Avast AV startup
kernel.shmmax = 128000000Save that file, exit/quit **gedit** and reboot.  Now your error message should have disappeared when starting **avastgui**.

Edit:  Avast 1.4.0 now seems to be working fine under 64-bit Ubuntu Lucid Lynx 10.04.3 LTS for me under this kernel:

> Linux HOSTNAME 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux


It also worked for me with the 2.6.32-35-generic and 2.6.32-21-generic Ubuntu 10.04.3 kernels.

There is more about gksu and gedit here at post #4:

[http://ubuntuforums.org/showpost.php?p=11447893&postcount=4](http://ubuntuforums.org/showpost.php?p=11447893&postcount=4)

---

