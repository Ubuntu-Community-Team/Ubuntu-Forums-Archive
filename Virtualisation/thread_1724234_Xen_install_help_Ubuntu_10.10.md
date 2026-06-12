---
title: "Xen install help Ubuntu 10.10"
date: 2011-04-08
forum: Virtualisation
---

### Post by Newuser901 on 2011-04-08
I'm in using ubuntu 10.10 and installing xen using this page

[https://help.ubuntu.com/community/Xen#Maverick%20Notes%20%28Xen%204.0.1%20pvops%20on%20Ubuntu%2010.10%29](https://help.ubuntu.com/community/Xen#Maverick%20Notes%20%28Xen%204.0.1%20pvops%20on%20Ubuntu%2010.10%29)

I'm at the start of step 2 and I'm lost. I don't quite understand anything from that point and was looking for some pointers.

I tried looking for some other guides for compiling the dom0(I have no real idea what it is yet. besides something about giving access to the machine as base layer somehow.) but everything was too disconnected to help.

Anyone know how to do this part. I did everything up to that point including the 64 bit one. unless I've done something wrong in any of them or they didn't work.(don't know how to tell really. or didn't see anything that seemed to indicate that to me.) I think I just have to get 2. and down done. can anyone help me. 8)

I'm at this point and I don't understand it. I went into the /usr/src after going to rood using cd /(unless that isn't root) and typing cd usr/src. Those commands do nothing. I think I tried from a usr or usr/src(if there was one) in the new windows type directory but it didn't seem to work. And I couldn't find anywhere it did anything.

Current Step:

"Now be in your /usr/src (<src>) directory and issue following command(s):

cd <src>
#check out the 'xen/master' default branch
#check out the latest xen/stable branch"


Figured something else out:

I apparently did step one in the default directory. I have now moved the .tar.gz file into /usr/src. And i ran the next step which was

Move the downloaded xen-4.0.1 tar ball to /usr/src. Unpack Xen hypervisor to /usr/src directory (NOT as root).***I did it as root though I think. How do I change without root?***

sudo tar -xzvf xen-4.0.1.tar.gz

now I try to do the make files and it screws up

*****:/usr/src$ sudo make xen
make: *** No rule to make target `xen'.  Stop.
*****:/usr/src$ sudo make xen
make: *** No rule to make target `xen'.  Stop.
*****:/usr/src$ sudo make tools
make: *** No rule to make target `tools'.  Stop.
****:/usr/src$ sudo make stubdom


I deleted everthing and started over. I'm going through the steps again. i'll make a reply if I find a problem. I think I misread and messed up to much at start.

---

### Post by Newuser901 on 2011-04-08
OK. I redid everything up to 2. again and now I'm confused as to what to do. I paste that whole window or parts in and nothing. what is <src> refering too?

I also have /xen but no /xen/master and no /xen/stable

anyone know?

BTW it is now all installed and contained in the /usr/src/ and installed into /usr/src/xen4.0.1 folder(I think that is the name) Everything was now run correctly up to step 2.(or atleast I don't see anything I did wrong.)

*****(:/usr/src/xen-4.0.1$ ls
buildconfigs  Config.mk.orig  docs        Makefile  tools
config        COPYING         extras      README    unmodified_drivers
Config.mk     dist            install.sh  stubdom   xen

this is what i have in that folder.

*****:/usr/src/xen-4.0.1/xen$ dir
arch	COPYING  drivers  Makefile  tools  xen.gz    xsm
common	crypto	 include  Rules.mk  xen    xen-syms


And this folder. Edit: Well at least if you can make out the spaces. I'll never know why they don't put spaces on forums like this. or at least allow them. There is so much functionality lost because of it.

---

### Post by Newuser901 on 2011-04-09
Can anyone help with this?

---

### Post by Newuser901 on 2011-04-10
Can anyone simplify step 2 of that install? Has anyone else run from it. It seems to pop up in every search so I figure someone else may have run from it.

I could use a simplification? is <src> a command or a reference to the source file. Because the following aren't doing anything. It sounds from the next paragraph after the cd <src> #... commands at the start of step 2 that it needs to upload something and that should trigger it.

You may notice from the directory showing that I don't have master or stable directories or files in /xen.4.0.1/xen. So did I mess up?

Sorry if I have to ask more than others. I just have an ailment of sorts and I have pressure in my head a lot and I have a harder time thinking than other people.I get caught up more easily.

---

### Post by mariomiy on 2011-04-13
I downloaded the xen-4.0.1.tar.gz, extracted the directory and entered the command "make world" as directed by the README file. Everything looked fine, until, by the end, there was an error: missing zlib. I tried "apt-get install zlib" and nothing was found. My problem seems to be slightly different from yours. Is there anyone who can help with this zlib missing? Thanks.

---

### Post by mariomiy on 2011-04-13
Partial quotation of your description:

[I apparently did step one in the default directory. I have now moved the .tar.gz file into /usr/src. And i ran the next step which was

[Move the downloaded xen-4.0.1 tar ball to /usr/src. Unpack Xen hypervisor to /usr/src directory (NOT as root).***I did it as root though I think. How do I change without root?***

sudo tar -xzvf xen-4.0.1.tar.gz]

I think the next steps are:
cd xen-4.0.1
make world
make install

I got stuck at "make world" with missing libraries: zlib.

---

### Post by mariomiy on 2011-04-15
> **Newuser901 said:**
> Can anyone simplify step 2 of that install? Has anyone else run from it. It seems to pop up in every search so I figure someone else may have run from it.

I could use a simplification? is <src> a command or a reference to the source file. Because the following aren't doing anything. It sounds from the next paragraph after the cd <src> #... commands at the start of step 2 that it needs to upload something and that should trigger it.

You may notice from the directory showing that I don't have master or stable directories or files in /xen.4.0.1/xen. So did I mess up?

Sorry if I have to ask more than others. I just have an ailment of sorts and I have pressure in my head a lot and I have a harder time thinking than other people.I get caught up more easily.
How to go about the second step:
One has to get the updated xen source code in this way: (following instructions of [http://wiki.xensource.com/xenwiki/XenParavirtOps](http://wiki.xensource.com/xenwiki/XenParavirtOps))

$ git clone git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git linux-2.6-xen
This command takes a long time to execute, because it downloads about 500 megabytes of git objects. Then I did:
$ cd linux-2.6-xen
$ git reset --hard
$ git checkout -b xen/stable-2.6.32.x origin/xen/stable-2.6.32.x
$ git pull
$ git log | less
$ cp /boot/config-2.6.32-30-generic .config
$ make menuconfig  (then follow instructions in [https://help.ubuntu.com/community/Xen#Maverick%20Notes%20%28Xen%204.0.1%20pvops%20on%20Ubuntu%2010.10%29](https://help.ubuntu.com/community/Xen#Maverick%20Notes%20%28Xen%204.0.1%20pvops%20on%20Ubuntu%2010.10%29))
Next, when I typed "make" as root, I got stuck with many compile errors for driver agp.o
That is where I stand now. I need someone to tell me what to do now.

---

### Post by bodhi.zazen on 2011-04-15
As you can see from that wiki page:

1. Xen has people who really like the technology.

2. Xen is not supported by Ubuntu.

So you should post your questions / problems on the Xen mailing list =)

With that said, for the compilation error re zlibs, you need to install the -dev package.

Probably this one:

[http://packages.ubuntu.com/maverick/zlib1g-dev](http://packages.ubuntu.com/maverick/zlib1g-dev)

Perhaps if you were to post the exact error you are getting we can be of further assistance.

For the most part, Xen is depreciated, and I think even RHEL has dropped xen support. You might want to see if you can convert to Virtualbox, KVM, and/or LXC although those have issues as well.

You might have better luck with Debian, or at least a debian Xen kernel.

---

### Post by mariomiy on 2011-04-19
Thank you for your reply. 
I suspected that was the case. Xen looks so impressive from description, but it is not a finished product.
I tried VirtualBox. Looks like it only works with a bootable CD, and not with the .iso file, which is a pity.

---

### Post by bodhi.zazen on 2011-04-19
> **mariomiy said:**
> Thank you for your reply. 
I suspected that was the case. Xen looks so impressive from description, but it is not a finished product.
I tried VirtualBox. Looks like it only works with a bootable CD, and not with the .iso file, which is a pity.

virtualbox boots iso, what give you the impression it does not ?

People test iso all the time with vbox.

---

### Post by agent8131 on 2011-04-24
Seriously, if you want to use Xen save yourself the trouble and just use Debian.  But make sure you understand your needs.  Nothing can compare with Xen on servers, but for the desktop VirtualBox is a much more user friendly way to go.

---

### Post by agent8131 on 2011-05-08
This is a pretty good writeup on getting Xen 4.1 working under Ubuntu:

[http://www.zeroaccess.org/2011/04/xen-4-1-on-ubuntu-10-04-64bit/](http://www.zeroaccess.org/2011/04/xen-4-1-on-ubuntu-10-04-64bit/)

---

### Post by bodhi.zazen on 2011-05-08
> **agent8131 said:**
> This is a pretty good writeup on getting Xen 4.1 working under Ubuntu:

[http://www.zeroaccess.org/2011/04/xen-4-1-on-ubuntu-10-04-64bit/](http://www.zeroaccess.org/2011/04/xen-4-1-on-ubuntu-10-04-64bit/)

Nice link =)

---

