---
title: "How to install cdemu.."
date: 2005-09-27
forum: Tutorials
---

### Post by EjeCt on 2005-09-27
Hi all this is my first howto.. Soo bare with me..
(All commandos are in a console..)
cdemu is a tool for mounting thoose peskey cue/bin files.. 

first you need some tools to get the job done..
```

sudo apt-get install build-essential

```
then you need youre kernel headers that you are using..
Mine are 2.6.12-9-686
You can simply find them by opening a console
write: 
```

uname -r
sudo apt-get install linux-headers-`uname -r`

```
now this is done
Get the the src off cdemu
```

wget [http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2](http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2)

```
extract the files using
```

tar -jxvf cdemu-0.7.tar.bz2

```
next go into the newly created directory
```

cd cdemu-0.7

```
type in:
```

sudo ls -la /lib/modules/`uname -r`/build

```
if this is goes bad.. you got the wrong linux-header
next type:
```

sudo make

```
next:
```

sudo make install

```
next:
```

sudo modprobe cdemu

```
then your all done.. 
to use it
```

sudo mkdir /media/iso

```
(0 is the drive you can have from 0 to 7 cue/bin files mounted at the same time)
```

sudo cdemu 0 something.cue
sudo mount /dev/cdemu/0  /media/iso -t iso9660

```
and then you have it..
Just browse to the /media/iso folder in you're nautilus..
to get nice overview what is mounted with cdemu
type:
```

cdemu -s

```
If something isnt right please post back..

EjeCt

---

### Post by frodon on 2005-09-27
I suggest to add in the install section : ```
sudo apt-get install checkinstall
``` and then replace "sudo make install" by : ```
sudo checkinstall -D
```It will allow to create a .deb file during install and also to see cdemu in synaptic (easy to uninstall).

Thanks for this helpful HOWTO.

---

### Post by Swoop on 2005-09-27
It didnt work with the sudo checkinstall command ... it got some error it couldnt overwrite someting :D

Anyways used the normal make install and it works great :D Could have used this tool earlier when i had som bin-cue files to mount :D

---

### Post by Anything Generic on 2005-12-11
.

---

### Post by Laterix on 2005-12-31
[QUOTE=Anything Generic]I'm having trouble doing the Make command.  Everything else went A-ok... can anyone help me pinpoint what's wrong?[/QUOTE]
It says that it cannot find gcc-3.4 compiler. Breezy comes with a newer version, but I'm not sure does this require 3.4 version. I got it working by simply installing 3.4 version
```

sudo apt-get install gcc-3.4

```

---

### Post by sceptre0 on 2006-11-20
Great post!  I was up and running in less than 5 minutes.  One small thing I want to point out was that the device directories were /dev/cdemu0 through cdemu7 not cdemu/0-cdemu/7.  I used version 0.8 not 0.7 so they may have changed it.  Thanks!  Keep up the good work!

---

### Post by adamkane on 2006-11-21
checkinstall doesn't work, since cdemu is a kernel module. Each version of Ubuntu needs its own installer, i386, i686, k7.

To install, you use:
```

make
sudo make install

```

To uninstall, you use:
```

sudo make uninstall

```

You can create a .deb file that installs the cdemu.ko file where it needs to go. Open the automatix 1 .deb file to learn how to create a .deb from a simple install script.

You just create your install script, and package it with:
```

sudo dpkg -b cdemu-0.7 cdemu-0.7.deb

```

Your files will be laid out like this under cdemu-0.7:
> 
/control
/DEBIAN/control
/DEBIAN/preinst
/usr/bin/cdemu
/usr/bin/create_cdemu_devs
/lib/kernel/misc/cdemu.ko
/lib/python/python_script.py
etc.


---

### Post by frodon on 2006-11-22
If i remember well (it's quite old now) i used checkinstall to create the .deb below. But anyway even with the .deb you need the kernel headers.

If some of you are interested by a .deb file, here is the one i created with checkinstall :

---

### Post by adamkane on 2006-11-22
Tell everyone which kernel you have installed.

We need to put out different .debs for each kernel, or create some sort of universal .deb.

How did you get checkinstall to work? It doesn't work on dapper, because checkinstall tries to overwrite existing files, and apt doesn't like that.

---

### Post by slapgat on 2007-10-26
Hi there please help. I'm a noobie to linux. 
Followed your guide bit when i get to sudo make i get this:

slapdash@lappy:~/Desktop/cdemu-0.8$ sudo make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
/bin/sh: Syntax error: Bad fd number
  CC [M]  /home/slapdash/Desktop/cdemu-0.8/cdemu_mod.o
/home/slapdash/Desktop/cdemu-0.8/cdemu_mod.c: In function &#8216;cdemu_exit&#8217;:
/home/slapdash/Desktop/cdemu-0.8/cdemu_mod.c:198: error: too many arguments to function &#8216;invalidate_bdev&#8217;
make[2]: *** [/home/slapdash/Desktop/cdemu-0.8/cdemu_mod.o] Error 1
make[1]: *** [_module_/home/slapdash/Desktop/cdemu-0.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

i'm using gutsy gibbon 7.10

thx

---

### Post by Herm87 on 2007-10-30
Try this patch: [http://bugs.gentoo.org/attachment.cgi?id=127042&action=view](http://bugs.gentoo.org/attachment.cgi?id=127042&action=view)
Worked fine for me (being a linux-newbie) using ubuntu 7.10 gutsy x86_64 on an AMD64 with Kernel ver 2.6.22-14-generic. Packaging with checkinstall -D also works.

---

### Post by nomis-s on 2007-11-02
Hey,

can anybody tell me how to apply the patch?
thanks...

EDIT:
OK, nervermind id did it:
```

patch -p1 < name.diff

```

---

### Post by robertfisk on 2007-11-17
> **nomis-s said:**
> Hey,

can anybody tell me how to apply the patch?
thanks...

EDIT:
OK, nervermind id did it:
```

patch -p1 < name.diff

```

Hello , I get the same error as you got when trying to compile.
I am quite the ubuntu n00b so I am not able to work out how to get the patch above working . Could you please elaborate a little ? How do you make a update file of the text in the link ?

---

### Post by ace214 on 2007-11-17
To get the patch working, download the source code, extract it to your desktop. Then download the patch and it put in the folder that was just created on your desktop. Then open up your terminal, and cd to the folder and use the command posted above. Then you can follow the instructions on the first page of this topic starting with make.

If you don't have patch, the terminal will tell you the apt command to get it. Also be sure you get the headers as described in the first post.

---

### Post by Haos on 2007-11-28
First of all, thx Herm87 for the patch provided, it helped me to compile CDemu 0.8 from their website.
Secondly, CDemu is supposedly having issues with 2.6.22.6 and 2.6.22.8 kernels, as reported here:
[http://sourceforge.net/mailarchive/forum.php?thread_name=9bdbd2500711271552o15fd1d31yff8f9a1a4584736f%40mail.gmail.com&forum_name=cdemu-devel]("http://sourceforge.net/mailarchive/forum.php?thread_name=9bdbd2500711271552o15fd1d31yff8f9a1a4584736f%40mail.gmail.com&forum_name=cdemu-devel")

Its a big issue, and as CDemu is only software of its kind on Linux platform, i`m considering kernel update. Are you guys using CDemu on 2.6.22.x and if so, what version exactly?

Best regards

---

### Post by norwizzle on 2007-12-01
Hi,

Just want to give thanks as well for making it easy for yet another newbie. That patch worked for me.

---

### Post by goldencako on 2007-12-03
I get the same error the patch is supposed to fix, but whenever i try to patch it by the command above, nothin happens. If anyone can help me Id appreciate it, even if its by just tellin me to get another emulator !

---

### Post by ace214 on 2007-12-03
Please post your exact steps and anything the terminal returns.

Did you download the patch file and put in the extracted source directory?

---

### Post by Walmsley on 2007-12-17
Hello all,
Firstly, let me state that I'm very new to Ubuntu, and have fairly limited experience with linux in general, hence my mistake may be something blindingly obvious to you.
I'm trying to install CDemu on Gutsy Gibbon (7.10)
I have followed the original guide posted and come to the same error as slapgat on entering the command 'make'. I'm now trying to install the patch and I'm afraid I don't really follow the instructions given. Clicking the link gives a wall of code, which presumably must be saved. I've saved it in a text document, which I've guessed from the command given ought to be named name.diff and then copied said file into my cdemu-0.8 folder. Running the command 
patch -pl < name.diff
gives the error 'patch: **** strip count l is not a number'
Running 'make' then errors as before.
What am I doing wrong? My guess is that I'm saving the patch as the wrong thing / in totally the wrong way.
Any help would be greatly appreciated.

---

### Post by ace214 on 2007-12-17
> **Walmsley said:**
> Running the command 
patch -pl < name.diff


It should be a number 1 not an l. Hence, it telling you that l is not a number.

Also, for learning purposes, in most cases filename doesn't matter as long as you're concious of what you're doing. If you save the patch as ABC.diff, then when you use the command you do patch -p1 < ABC.diff. The "name.diff" was a variable, a filler.

---

### Post by confy on 2007-12-20
ace214 thank you it was only a typo...

after installing i have another problem... it simply halts and dosen't mount...
> confy@rox:~/Desktop$ sudo mount /dev/cdemu0 /mnt/genije -t iso9660
mount: block device /dev/cdemu0 is write-protected, mounting read-only

I guess it should be normal and i it should exit but it shouldn't halts there...
if i go to /mnt/genije/ it's empty...
my uname -a is: 

Linux rox 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux

---

### Post by confy on 2007-12-21
it's interesting that it dosen't work even with ISO files :(
```
root@rox:/home/confy# cdemu -s
Drive Loaded Comment
  0:     1   agcnccci.cue
  1:     1   agcnccci.cue
  2:     1   h-cbtccna3.iso
  3:     1   agcnccci.cue
  4:     0   NO_CD_LOADED
  5:     0   NO_CD_LOADED

```
then 
```
root@rox:/home/confy# mount /dev/cdemu2 ./Desktop/work -t iso9660
mount: block device /dev/cdemu2 is write-protected, mounting read-only
here i can write text asi wanted
alt_+Z dosen't help.. it printsasdasd
asfdasdfasdfgasdg

```
and again i get that stupid halt situation....
any suggestions?

---

### Post by ace214 on 2007-12-25
Just so anyone subscribed to this thread notices, there is a new version of CDEmu. Go to the SourceForge site to check it out: [http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

---

### Post by hOmerscousin on 2007-12-28
hey ace214,

i installed the CDemu debian files from sourceforge but now i have no idea as to how to use it... I am a noob... Ubuntu had no problems installing it if you start from bottom of the sourceforge list to the top. But after the install, how do I configure it? Where do the files go? I read on another forum that CDemu needs the Kernel in order to work--how do I make that happen??? I really confused. It was cool that Ubuntu installs it after downloading automatically, but I no idea what to do next.... Suggestions???

---

### Post by zipperback on 2007-12-28
> **hOmerscousin said:**
> hey ace214,

i installed the CDemu debian files from sourceforge but now i have no idea as to how to use it... I am a noob... Ubuntu had no problems installing it if you start from bottom of the sourceforge list to the top. But after the install, how do I configure it? Where do the files go? I read on another forum that CDemu needs the Kernel in order to work--how do I make that happen??? I really confused. It was cool that Ubuntu installs it after downloading automatically, but I no idea what to do next.... Suggestions???

What does the documentation say about it? There should be a support forum on the sourceforge project website for the application, as that is where the developers are for it.

- zipperback
:popcorn:

---

### Post by hOmerscousin on 2007-12-28
I looked on sourceforge on there wasn't documentation that went along with the packages. That's the first thing I did. The second was google CDemu and found a couple of sites talking about installation of older versions. Any ideas, there is talk in this site [http://www.linuxquestions.org/questions/linux-software-2/trying-cdemu-userspace-569454/](http://www.linuxquestions.org/questions/linux-software-2/trying-cdemu-userspace-569454/)
about a README file but I haven't found it yet. I am scanning through all the files that were installed, hopefully I'll stumble on it.

---

### Post by kurumin on 2008-02-29
I install cdemu but not know its works what the controll for it  work?
i use ubuntu 7.10

---

### Post by yowshi on 2008-04-05
this is out of date the wget no longer works

---

### Post by amano on 2008-09-21
Does anybody know, if there are chances that cdemu is packaged regularily to be intalled via a simple apt-get?

A new version of libmirage was released on September 13th... [http://cdemu.sourceforge.net/#status](http://cdemu.sourceforge.net/#status)

---

### Post by olebob on 2008-12-02
There is a simpler way to install CDemu is to run:

sudo gedit /etc/apt/sources.list

then add this line

deb [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) intrepid main

save the file and run

sudo apt-get update
sudo apt-get install cdemu
sudo reboot

thats it! no need for compiling

this worked great for me in intrepid. If you use gnome I recommend you to also install gCDemu with

sudo apt-get install gcdemu

then add 'gCDEmu Applet' in your gnome panel. 

Now you have easy access to cdemu

hope this help:)

---

### Post by robobot on 2008-12-03
The cdemu package isn't in the repository, but the gcdemu package is, and that installs fine.

---

### Post by trazart on 2008-12-16
Not cdemu but cdemu-client and cdemu-daemon ;)

---

### Post by Tictoon on 2009-01-01
It does not work for me:
```
gagan@gagan-desktop:~$ cdemu load big-buck-bunny-PAL.iso
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon (bus: 'session')!

```

---

### Post by Arno Sluismans on 2009-06-06
[http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2](http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2)
That link seems to be broken. Does anybody know of a different link I can use?

---

### Post by Yiguro on 2010-09-03
I've found a very complete guide for fedora 13, but compiling shoudn't be very different from Ubuntu:

[http://www.linuxquestions.org/questions/showthread.php?p=4086165#post4086165](http://www.linuxquestions.org/questions/showthread.php?p=4086165#post4086165)

---

### Post by jtarin on 2010-09-03
> **EjeCt said:**
> Hi all this is my first howto.. Soo bare with me..
(All commandos are in a console..)
If something isnt right please post back..

EjeCtDoes the military know of this? Is this one of those Black-OPS?

---

### Post by ysf on 2010-09-13
```
sudo add-apt-repository ppa:cdemu/ppa
sudo apt-get update
sudo apt-get install cdemu-client gcdemu
```

---

### Post by ashnur on 2011-03-12
> **ysf said:**
> ```
sudo add-apt-repository ppa:cdemu/ppa
sudo apt-get update
sudo apt-get install cdemu-client gcdemu
```

thanks

---

### Post by teoman99 on 2012-08-01
I want to explain my experience with ubuntu 11.10 or higher in cdemu installation

open software installation center in ubuntu 11.10
in top menu ---->  edit   ----> software resources  ----> enter password
    a window is opened  for software sources
here  click   Third-party software   menu  then   add button
 
in the opened window  enter       (     ppa:cdemu/ppa     )    without  parenthesis

click     add resource button

in command line   sudo apt-get   update

repository  is updated.

in software  installation center  search for  cdemu

packages   cdemu-client    gcdemu     extra extra   come
install them
for mounting   ---->  open the iso file  in nautilus  --->    right click   ---->open with cdemu client

a new nautilus window is opened ----->    there you see  your virtual cd

You can Mount 2 CD /DVD drives at once. 

     CDemu  supports following formats:-

    .nrg format,
    .cdi format,
    .ccd/.sub/.img,
    .cue/.bin format,
    .iso format,
    .toc format,
    .b6t format,
    .mds format,
    .cif format,
    .c2d format,
    .daa format.
    .toc format.

---

