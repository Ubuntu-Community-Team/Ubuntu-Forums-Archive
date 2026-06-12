---
title: "HOWTO GUIDE: TrueCrypt on new version of Ubuntu"
date: 2006-03-24
forum: Tutorials
---

### Post by Matthai on 2006-03-24
TrueCrypt is Free open-source disk encryption software for Windows XP/2000/2003 and Linux.
Main Features:
    * Creates a virtual encrypted disk within a file and mounts it as a real disk.
    * Encrypts an entire hard disk partition or a device, such as USB flash drive.
    * Encryption is automatic, real-time (on-the-fly) and transparent.
    * Provides two levels of plausible deniability, in case an adversary forces you to reveal the password:
      1) Hidden volume (steganography).
      2) No TrueCrypt volume can be identified (volumes cannot be distinguished from random data).

    * Encryption algorithms: AES-256, Blowfish (448-bit key), CAST5, Serpent, Triple DES, and Twofish.
      Mode of operation: LRW  (CBC supported as legacy).



How to install TrueCrypt on NEW version of Ubuntu, including new version of Ubuntu Breezy kernel (this is important, since Breezy updated kernel through security updates).

Download TrueCrypt code at: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) (tar.gz version) to your home directory. Assume you have version 4.1 (of TrueCrypt)

 cd
 tar xvfz truecrypt-4.1-source-code.tar.gz 

Check the version of our Linux kernel:

 uname -r

For instance, it is 2.6.12-10-386 - so we have to install source for 2.6.12:

 sudo apt-get install linux-source-2.6.12
 cd /usr/src/
 sudo tar xvjf linux-source-2.6.12.tar.bz2

Create symbolic link:

 sudo ln -s linux-source-2.6.12 linux

Install tools needed for compiling:

 sudo apt-get install build-essential

Check wit which version our kernel was compiled:

 cat /proc/version

output is something like that:

 Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:13:17 UTC 2006

So we need gcc 3.4 (subversion 3.4.x is not important). Let's install it:

 sudo apt-get install gcc-3.4


Let's use it and compile the modules (everything should be set to default - so answer with pressing "enter" key):

 export CC=gcc-3.4
 sudo make -C /usr/src/linux-source-2.6.12 config modules

Now, install TrueCrypt:

 cd
 cd truecrypt-4.1-source-code/Linux/
 sudo ./build.sh

 sudo ./install.sh

You should set this also:

 Install man page to [/usr/local/man]: **/usr/share/man**

That's it.

Now the funniest part: mounting TC volume from the USB key to /mnt:
 sudo truecrypt /media/MATTHAI/TrueCrypt/mobile.tc /mnt/
 Enter password for '/media/MATTHAI/TrueCrypt/mobile.tc':

List all mounted TrueCrypt partitions:

 sudo truecrypt -vl
 /dev/mapper/truecrypt0:
 Volume: /media/MATTHAI/TrueCrypt/mobile.tc
 Type: Normal
 Size: 15728128 bytes
 Encryption algorithm: AES
 Mode of operation: LRW
 Read-only: No
 Hidden volume protected: No

Let's check the encrypted files:

 cd /mnt/
 ls
 
 password.txt    secret.txt    System Volume Information

Unmount the drive:

 cd
 sudo truecrypt -d

Check if it is really unmounted:

 ls -l /mnt/
 total 0

Have fun and also check the documentation: [http://www.truecrypt.org/documentation.php](http://www.truecrypt.org/documentation.php)

---

### Post by alaaji on 2006-04-05
I really appreciate the guide.  Thanks a bunch b/c I was having trouble getting my encrypted volume mounted.

---

### Post by Mr.Auer on 2006-04-21
Does this howto also work with Dapper as it is? And if I update the kernel later, do I have to redo this?
I mean, can I use the Breezy .deb, or should I compile it myself under Dapper..Breezy used different version of gcc right? So it means I need to compile, and then do like your howto says?

---

### Post by Nais on 2006-04-24
[QUOTE=Mr.Auer]Does this howto also work with Dapper as it is? And if I update the kernel later, do I have to redo this?[/QUOTE]

This method works fine in Dapper, I've done it myself. However, I too would like to know if there's any way to avoid having to compile all the modules each time I update the kernel.

Edit: Seems like you don't have to recompile at all. Not sure if it's because I update to the newest version.

---

### Post by flyingbrass on 2006-04-26
I'm running 2.6.12-10-686 in Breezy.  Truecrypt's module won't load unless forced.  Dmesg shows:
> truecrypt: version magic '2.6.12 586 gcc-3.4' should be '2.6.12-10-686 686 gcc-3.4'
Truecrypt works if I force load the module.  Where is it getting "2.6.12 586"?

---

### Post by flyingbrass on 2006-04-26
This fixed it.  Found in the Truecrypt forum:
> rm -rf linux-source-2.6.12 
tar xfvj linux-source-2.6.12.tar.bz2 
cd linux-source-2.6.12 
make oldconfig && make modules 

(for some reason make clean didn't do it?) 

THEN recompiled truecrypt

---

### Post by flyingrhino on 2006-04-30
Hi all,
I'm new to this linux thing, is there any way I can do an apt-get install
to make truecrypt work ? Or is there a package I can just install with dpkg ?
I have kubuntu dapper installed and am not very confident in doing all the kernel stuff you originally mentioned.

Now if I just want to manually fire up truecrypt and mount a container, isn't there
a way of just running an executable and getting it to work ?

---

### Post by ken_fallon on 2006-05-09
I'd like to confirm this works on Dapper (Kubuntu) running kernels 2.6.15-22-386, 2.6.15-21-386, 2.6.15-20-386 and on 2.6.15-19-386 (different compile for each :))

For  2.6.15-22-386 I replaced 2.6.12 with 2.6.15 throughout

As "cat /proc/version" reported "Linux version 2.6.15-22-386 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sun May 7 15:49:09 UTC 2006", I replaced export CC=gcc-3.4 with export CC=gcc-4.0

Finally as I didn't want to hit enter all the time I used make oldconfig instead of just make config:
sudo make -C /usr/src/linux-source-2.6.12 config modules with
sudo make -C /usr/src/linux-source-2.6.15 oldconfig modules

---

### Post by ken_fallon on 2006-05-09
[QUOTE=flyingrhino]Hi all,
I'm new to this linux thing, is there any way I can do an apt-get install
to make truecrypt work ? Or is there a package I can just install with dpkg ?
I have kubuntu dapper installed and am not very confident in doing all the kernel stuff you originally mentioned.

Now if I just want to manually fire up truecrypt and mount a container, isn't there
a way of just running an executable and getting it to work ?[/QUOTE]

The version of truecrypt you run is different for each Kernel version. I also run Kubuntu Dapper and there have been four kernel updates in the last two months alone and each time TrueCrypt needs to be updated. Until TrueCrypt is added to a repository your options are to wait for someone to make a package for you or compile it yourself.

I'll admit that the instructions are a bit daunting the first time you do it but it's not actually that difficult because you don't need to make any decisions during the kernel compile. Epically if you use the make oldconfig instead of make config). If you're willing to give it a try then I can make custom instructions for you.

I'll need to know your kernel version and the version of gcc (the compiler that will make a running TrueCrypt version) that you have installed.


The following commands will make a text file on your Desktop called output.txt that has the kernel version you are using and the version of build-essentials and gcc you have installed if any.
Please open a terminal window and paste the following commands:
cat /proc/version >> ~/Desktop/output.txt
aptitude show build-essential gcc  >> ~/Desktop/output.txt

Then post the contents of the file output.txt

If you're not ready to do this then post the output anyway and wait and see if some nice person may make a debian package for you.

---

### Post by monkman on 2006-05-14
Hello!

How do i uninstall truecrypt using this howto? is it just deleteing the man pages and the binary?

Thanks!

---

### Post by Lypsis on 2006-05-14
EDIT: Sorry - this post was shit ](*,)

---

### Post by lex1 on 2006-05-21
Am I missing something but 4.2 was released in april are we talking the same set up here and will it work on BB 5-10 2.6.10-12-686-smp kernel.

thanks

lex1;)

---

### Post by Mr.Auer on 2006-05-26
I have it installed (according to this howto) on Dapper LTS with 2.6.15-23 kernel..Havent yet tried to actually use it, but it installed fine at least..I mean i havent encrypted any drives with it, i have checked that u can run it..

---

### Post by sefs on 2006-05-28
Hi all.  I have a question.

When I download and compile the linux source which is in /usr/src/linux  using the the step suggested in the first post of this thread...does this actually replace the existing kernel i have? or does it just compile it and everything remains in the /usr/src/linux directory for the sole purpose of compiling the truecrypt.

Thanks.

---

### Post by freeweazl on 2006-05-29
[QUOTE=sefs]
does this actually replace the existing kernel i have? or does it just compile it and everything remains in the /usr/src/linux directory for the sole purpose of compiling the truecrypt.
[/QUOTE]

I did this last week for using Truecrypt with my 2.6.12_i686 kernel, and it didn't replace my default kernel in the /boot folder (That is, I haven't noticed any change of behavior when starting up and running my kubuntu). 

Normally a certain person would move the kernel to /boot manually after building a kernel. I think the truecrypt build script doesn't even build the kernel as a whole but only the modules. But hey... you could always view the internals of the build and install scripts of Truecrypt if you can read the code... It would save tou the trouble of a post to this forum....

Prior to building TrueCrypt 4.2 on my system, I didn't even manually compile my kernel modules, nor did I manually specifiy a gcc version. The build script figured everything out and did everything for me. The only thing it asked was wheter I wanted to use my current kernel config file. I now think that if a user answers with 'yes', it will use the config file of the currently running kernel from the /boot folder...

Thanks TrueCrypt creators for making things easy!

---

### Post by Mr.Auer on 2006-05-30
I suppose it only uses the source to compile the kernel module for Truecrypt, you dont have to actually change the whole kernel..The last step after compilation is installing the kernel module, it says so on the howto. The source is needed to compile the module correctly for the current kernel, and this is also why it needs to be recompiled after kernel updates, with the new kernels sources.

---

### Post by flyingbrass on 2006-05-31
Yep.  I first tried kernel headers, but they weren't enough.  I wish someone would explain or point me to a clear explanation of what kernel headers accomplish vs. the source.

The main problem with Truecrypt at present seems to be in creating decent-sized volumes in Linux.  I haven't tried yet in Dapper, but in Breezy (and this isn't limited to Ubuntu -- read the Truecrypt forums for more info) I was limited to about 2 GB without crashing, even after making an initial FAT32 volume and then converting to ext3.

---

### Post by sefs on 2006-05-31
I'm not a specialist in linux or complilations but it may be that 

1) the headers are used for software compilation that does not require a kernel module. (maybe totally dependant on its own code? or something like that?) 

2) the source is needed for software which has as part of it a "kernel module" that needs to "plug in" to th linux kernel or something like that.

I am just guessing there.

---

### Post by flyingbrass on 2006-06-01
Truecrypt installed easily in Dapper.  Someone should make a .deb.

Don't consider this a proper howto for Dapper because I might be forgetting or overlooking something.  I installed Truecrypt several days ago after a fresh Dapper install.  The steps below are to the best of my recollection.  I didn't have to bother with everything listed in the first post here.

Install build-essential:

sudo apt-get install build-essential


Install the kernel source:  

sudo apt-get install linux-source-2.6.15 


I don't remember if I had to manually untar the source.  I think it happened automatically (to my surprise), but check in /usr/src and make sure you have a directory named linux-source-2.6.15, not just a file with tar.bz2 at the end.  If you only have the tar.bz2 file:

sudo tar -xjvf /usr/src/linux-source-2.6.15.tar.bz2


Create a link to the source:

sudo ln -s /usr/src/linux-source-2.6.15 /usr/src/linux


Go to [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) and download "Other (source code)."

Extract the file (if in nautilus right click it and select extract here).

Read the readme, which tells you to cd into the Linux directory, and then:

sudo ./build.sh

sudo ./install.sh


When running the install script change the man directory to /usr/share/man

IIRC, at some point it asked whether to use the config of the running kernel.  Yes.

Done.

Be forewarned that when creating volumes in Linux you only have the choice between a FAT32 filesystem and none.  Using mkfs to convert to ext3 doesn't work for volumes over about 2 GB.  If you try, the whole system locks up hard.  There are posts about this in the Truecrypt forum.  I'm hoping this issue will be solved in their next release.  Apart from that, it seems to work pretty well.

---

### Post by flyingrhino on 2006-06-01
What happens with truecrypt when you upgrade your kernel ? with new kernel images coming out every other week, don't tell me I need to compile a whole new kernel just to make truecrypt work ?

---

### Post by Mr.Auer on 2006-06-01
Yes, you will have to compile it again. But you dont need to update at once to a new kernel if u dont want to? I know its a pain, on my older box (P4 1.6 Ghz) compiling the kernel and modules takes about 2 hours :)

I also noticed as I installed Truecrypt on 2 fresh Dapper Drake boxes today that I needed to manually add "truecrypt" in /etc/modules, just running install.sh wasnt enough - Truecrypt just told me "kernel module not loaded" after running install.sh and rebooting. Then I did "sudo modprobe truecrypt", started working, so decided to add it in modules. Now works.

---

### Post by flyingrhino on 2006-06-04
Reading all the comments on this thread (thank you all for your responses and offers to help), I think that ultimately getting truecrypt to work is too much of a hassle.
I use the windows version of it and that works with zero trouble. I see no reason why the linux version should put us through this much hassle.
Since I'm not a linux hacker, I want to do a simple apt-get and expect it to work. There will at some stage be a nice guy who knows linux and makes a package that works. I will wait until this angel comes along.

---

### Post by HammyGross on 2006-06-06
Hi there,

I've got truecrypt 4.2 running on Ubuntu Dapper Drake 6.06 and am interested in running a script at boot time to mount two truecrypt volumes. It should be run before I log in, since I would like to mount one of the volumes to /home.

The problem is that I'm not entirely sure that it's possible to run interactive scripts (i.e. one which prompts the user for a password) as part of the system startup scripts. In Fedora Core 5 it was possible without any problems.

Here is an example of the script which I have tried without success to run:

#! /bin/sh
#
#  This script was generated by The Ubuntu Linux Startup Script Builder
#  version 1.5 located at [http://rob.pectol.com/startup_scriptbuilder/](http://rob.pectol.com/startup_scriptbuilder/).
#
#  Generated: Mon Jun  5 05:23:28 MDT 2006

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

if [ -r /lib/lsb/init-functions ]; then
	. /lib/lsb/init-functions
	logbegin="log_begin_msg"
	logend="log_end_msg"
else
	logbegin="echo -n"
	logend=`printf "echo .\n"`
fi

# Exit if the daemon binary is NOT available, executable, etc.
test -x /usr/local/bin/truecrypt || exit 0

# Start function
d_start() {
	/usr/local/bin/truecrypt -u /dev/hda3 /mnt/shared
	/usr/local/bin/truecrypt -k /mnt/shared/home.keyfile /dev/hda7 /home
}

# Stop function
d_stop() {
	/usr/local/bin/truecrypt -d
}

case "$1" in
	start)
		$logbegin "Mounting Truecrypt Volumes"
		d_start
		$logend $?
		;;
	stop)
		$logbegin "Dismounting Truecrypt Volumes"
		d_stop
		$logend $?
		;;
	restart)
		$0 stop
		sleep 1
		$0 start
		;;
	*)
	log_success_msg "Usage: truecrypt.sh {start|stop|restart}"
	exit 1
	;;
esac
exit 0

=====

The problem is getting the password prompt to work for the first mount - I never get prompted during the Ubuntu boot. Has anyone had any success with this at all? Are there any other ways of entering a truecrypt password to mount the volume as part of the startup process?

Thanks,

Hamilton

---

### Post by lcbu on 2006-06-13
First thank you for this nice howto.

I would like to know if Tuecrypt can mount scramdisk containers.

I tried to install Scramdisk (SD4L) (has a nice GUI), but the program doesn't mount containers, and the options window doesn't show completely. :-(
(there are a few errors during 'make' and 'make install')

Does anyone has successfully installed SD4L in ubuntu 6.06 2.6.15-23-386?

TIA.

---

### Post by ken_fallon on 2006-06-16
I've had problems compiling the kernel 
*** Warning: Can't handle masks in drivers/net/wireless/mrv8k/mrv8k:1385
  LD [M]  drivers/net/ndiswrapper/ndiswrapper.ko
make: Leaving directory `/usr/src/linux-source-2.6.15'

I found that if I removed and reinstalled the linux-sources that the problem fixed itself fine.
aptitude purge linux-source-2.6.15
aptitude install linux-source-2.6.15
cd /usr/src
tar xvjf linux-source-2.6.15.tar.bz2
ln -s linux-source-2.6.15 linux

---

### Post by 454redhawk on 2006-08-19
The .deb is now available for Ubuntu 6.06 at Truecrypt.org

---

### Post by dm@n on 2006-08-31
The .deb from truecrypt site does not work for me.. looks like i386 I use i686 kernel

---

### Post by bluntu on 2006-09-04
Do you have to repeat this howto each time you update your kernel? How often does Ubuntu updates kernel? Like once a month?

---

### Post by TrinitronX on 2006-10-03
Every time you update the kernel, you must rebuild the kernel module, otherwise it won't be able to load the module and truecrypt will spit out an error when you try to mount something.
It doesn't seem like they created a script that will compile only the kernel module while still updating your kernel .config file.

I finally got this to compile correctly for the 686 kernel after looking inside the build.sh script and finding that it was not using the current running kernel config, but instead an older one that was left in the /usr/linux-source-2.6.15/.config from one of my previous kernel compiles.
Doing a make oldconfig was bad in my case since the older config wasn't for the currently running 686 kernel. First, I had to do a make clean inside the linux source directory.
Then, I finally figured out to copy /boot/config-$(uname -r) to /usr/src/linux/.config . (with $(uname -r) evaluating to 2.6.15-27-686, and the symlink /usr/src/linux pointing to /usr/src/linux-source-2.6.15  in my case)


The problem arose from this part in the build.sh script:
```
if [ ! -f "$KERNEL_SRC/.config" ]
then
	if [ -f /proc/config.gz -o -f /boot/config-$(uname -r) ]
	then
		echo -n "Configure kernel source according to the currently running kernel? [Y/n]: "
		read A
		if [ -z "$A" -o "$A" = "y" -o "$A" = "Y" ]
		then
			echo -n "Configuring kernel source in $KERNEL_SRC... "
			
			if [ -f /proc/config.gz ]
			then
				zcat /proc/config.gz >$KERNEL_SRC/.config || exit 1
			else
				cp /boot/config-$(uname -r) $KERNEL_SRC/.config || exit 1
			fi
			
			make -C $KERNEL_SRC oldconfig </dev/zero >/dev/null || exit 1
			echo Done.
		fi
	fi

	if [ ! -f "$KERNEL_SRC/.config" ]
	then
		error "Kernel not configured. You should run make -C $KERNEL_SRC config"
		exit 1
	fi
fi
```

This part in the script makes it so it only asks you if you want to configure using the currently running kernel's config when it doesn't find a .config file there already!
This won't usually cause problems assuming that for every different kernel version you'd have a separate folder for it: (ex: linux-source-2.6.15-27-686, linux-source-2.6.15-27-386, linux-source-2.6.15-26-386).  That way there would be a separate config file in each one, and the script would use it by default.
However, it seems ubuntu keeps the kernel config separate from the base source tree.  So for every kernel version or revision, there is just the one source tree.  The actual config files for the different kernel versions (686, 386, k7), and revisions are kept in their respective /usr/src/linux-headers-<REVISION>-<VERSION>/.config files.

I'd have the script ask all the time whether or not you want to use the current kernel's config instead of only when one isn't found.
It is safe to remove that outermost if statement (or comment out the if, then and fi) so that it asks every time, but still dies if no .config file is found if you were to say no, or the copy commands failed.  I've just tested it and it worked for me, but I don't want people blaming me if it somehow breaks their system, so I don't guarantee anything ;)

So a fix would be to replace the code with this:
```

	if [ -f /proc/config.gz -o -f /boot/config-$(uname -r) ]
	then
		echo -n "Configure kernel source according to the currently running kernel? [Y/n]: "
		read A
		if [ -z "$A" -o "$A" = "y" -o "$A" = "Y" ]
		then
			echo -n "Configuring kernel source in $KERNEL_SRC... "
			
			if [ -f /proc/config.gz ]
			then
				zcat /proc/config.gz >$KERNEL_SRC/.config || exit 1
			else
				cp /boot/config-$(uname -r) $KERNEL_SRC/.config || exit 1
			fi
			
			make -C $KERNEL_SRC oldconfig </dev/zero >/dev/null || exit 1
			echo Done.
		fi
	fi

	if [ ! -f "$KERNEL_SRC/.config" ]
	then
		error "Kernel not configured. You should run make -C $KERNEL_SRC config"
		exit 1
	fi
```

So: if you are having problems with truecrypt complaining about the wrong kernel module or 'unknown symbols', then try doing what I did, or edit the script.
If that still fails, try simply uninstalling all linux-source and linux-headers packages for your current kernel, go into the /usr/src/ directory and `sudo rm -r` any folders that stuck around (only the ones that have your current kernel version of course), then re-install from synaptic the linux-source and linux-headers packages.

If you haven't edited the script, you should be able to hotwire it by making an empty .config file in your source directory too, then choosing to use the current running kernel's config.

Hope this helps all the people who have been able to compile everything ok, but are getting those kernel module errors. :D

---

### Post by MontanaMax on 2006-12-04
I'm having a spot of trouble with this. ](*,) 

I was running truecrypt on Kubuntu 6.06 (Dapper) with NVIDIA and all was good with the world.

Then I did the dist-upgrade to Kubuntu 6.10 (Edgy) a few weeks ago, and truecrypt stopped working (because of the kernel change to 2.6.17 I assume). NVIDIA drivers kept right on working however. At no point did I try to change or update my video drivers or play with the new beryl or compiz stuff for Edgy.

So I tried to install the Ubuntu 6.10 .deb file from truecrypt.org, and of course that didn't work. Next I uninstalled everything truecrypt related and followed the excellent instructions on this forum to build the truecrypt kernel modules and everything worked great! :D 

Then something bad happened after I shutdown my laptop - NVIDIA threw an error about loading the kernel module, and xwindows will no longer start for any window manager (KDE, E17, Fluxbox). But truecrypt still works from the CLI.

I tried force reinstalling the NVIDA drivers, but no luck. My next step tonight is to download the vanilla Ubuntu 6.10 kernel and try to get my video drivers back in shape.

My question at large is - has anyone else had this problem? It seems to me that there was some conflict between the kernel for 6.10 settings script that the truecrypt installer used and the NVIDIA kernel modules, but it's all just a little bit more technical than I am.

Any advice would be appreciated - I'm going to keep banging away on this for another day or two before just formatting and starting with a clean Edgy install.

Thanks,

- Jon Pruett

---

### Post by charlieMOGUL on 2007-02-22
After searching why after the kernel ugrade in Ubunty Feisty Fawn (2.6.8.20) Truecrypt went belly-up, I found the post of TrinitronX.
Compiling seemed to go okay, except the dreaded kernel module error.
I posted the patch from TrinitronX at
[http://www.ubuntuforums.org/showthread.php?p=2193023#post2193023](http://www.ubuntuforums.org/showthread.php?p=2193023#post2193023)

Hope this helps, it helped me...

charlieMOGUL

---

### Post by Traveses on 2007-04-22
I tried this method but have a problem.  I followed the instructions (see below) but ran in to a problem when I got to
/usr/src/linux-source-2.6.20 config modules
and
cd
cd truecrypt-4.1-source-code/Linux/  I enter cd truecrypt-4.3-source-code/Linux/

see sequence of events showing my inputs and system returns.

Hope you can help
Thanks


Download TrueCrypt code at: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) (tar.gz version) to your home directory. Assume you have version 4.1 (of TrueCrypt)

At this point I downloaded Truecrypt-4.3-ubuntu-6.10-x86.tar.gz (no version available for 7.04)

cd (returns colin@colin-desktop:)
tar xvfz truecrypt-4.1-source-code.tar.gz  (I change to Truecrypt-4.3-ubuntu-6.10-x86.tar.gz)

Check the version of our Linux kernel:

uname -r (returns 2.6.20-15-generic)

For instance, it is 2.6.12-10-386 - so we have to install source for 2.6.12:

sudo apt-get install linux-source-2.6.12  (I enter sudo apt-get install linux-source-2.6.20)
COMMENT:  	at this point the sytem returns Password:
		I enter my password
		The system returns 	Reading package lists... Done
					Building dependency tree       
					Reading state information... Done
					linux-source-2.6.20 is already the newest version.
					0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

cd /usr/src/	(the system returns colin@colin-desktop:/usr/src$ )

sudo tar xvjf linux-source-2.6.12.tar.bz2 (i enter sudo tar xvjf linux-source-2.6.20.tar.bz2)

At this point the system displays a long list for example linux-source-2.6.20/ubuntu/ssb/Makefile and returns colin@colin-desktop:/usr/src$ 

Create symbolic link:

sudo ln -s linux-source-2.6.12 linux  (I enter sudo ln -s linux-source-2.6.20 linux)
The sytem returns colin@colin-desktop:/usr/src$ 

Install tools needed for compiling:

sudo apt-get install build-essential
The system returns 	Reading package lists... Done
			Building dependency tree       
			Reading state information... Done
			build-essential is already the newest version.
			0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Check wit which version our kernel was compiled:

cat /proc/version
System returns Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007


output is something like that:

Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:13:17 UTC 2006

So we need gcc 3.4 (subversion 3.4.x is not important). Let's install it:

sudo apt-get install gcc-3.4  (I enter sudo apt-get install gcc-4.1)

System returns 	Reading package lists... Done
		Building dependency tree       
		Reading state information... Done
		gcc-4.1 is already the newest version.
		0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Let's use it and compile the modules (everything should be set to default - so answer with pressing "enter" key):

export CC=gcc-3.4   I enter export CC=gcc-4.1
sudo make -C /usr/src/linux-source-2.6.12 config modules  I enter sudo make -C /usr/src/linux-source-2.6.20 config modules


The system returns with al ist for example
make: Entering directory `/usr/src/linux-source-2.6.20'
make[1]: Nothing to be done for `/usr/src/linux-source-2.6.20/scripts/Kbuild.include'.
scripts/kconfig/conf arch/i386/Kconfig

This list goes on forever asking for Y/N responses
At this point I closed the terminal and continued


*
* Linux Kernel Configuration
*
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] 
*
* General setup
*
Local version - append to kernel release (LOCALVERSION) [] 


Now, install TrueCrypt:

cd
cd truecrypt-4.1-source-code/Linux/  I enter cd truecrypt-4.3-source-code/Linux/

PROBLEM HERE  The system returns  bash: cd: truecrypt-4.3-source-code/linux/: No such file or directory

sudo ./build.sh

sudo ./install.sh

You should set this also:

Install man page to [/usr/local/man]: /usr/share/man

That's it.

Now the funniest part: mounting TC volume from the USB key to /mnt:
sudo truecrypt /media/MATTHAI/TrueCrypt/mobile.tc /mnt/
Enter password for '/media/MATTHAI/TrueCrypt/mobile.tc':

List all mounted TrueCrypt partitions:

sudo truecrypt -vl
/dev/mapper/truecrypt0:
Volume: /media/MATTHAI/TrueCrypt/mobile.tc
Type: Normal
Size: 15728128 bytes
Encryption algorithm: AES
Mode of operation: LRW
Read-only: No
Hidden volume protected: No

Let's check the encrypted files:

cd /mnt/
ls

password.txt secret.txt System Volume Information

Unmount the drive:

cd
sudo truecrypt -d

Check if it is really unmounted:

ls -l /mnt/
total 0

---

### Post by Dirtycash on 2007-04-22
Ok so I just got truecrypt working myself.

Upgraded to Feisty and got the dreaded kernel error.

The guide is pretty much spot on.
I noticed a few things in your post.  

1. I also downloaded the 4.3 truecrypt source.  But I installed gcc-3.4 instead of 4.1 which is what i already had along with linux 2.6.20.

2. Instead of closing the terminal when the long list of Y/N questions comes up, press enter to choose the default answer.  This will take a looong time, i just held down the Enter key until they stopped.  After all the questions it will compile for a long time (1.5 hours for me).

3. Once its finished compiling you can install truecrypt almost exactly how the guide specifies.  It already installed the man page in the proper place for me and I also made it so Non-Admin users could use truecrypt.  The reason I did this is because i use my various truecrypt drives alot and using sudo just made it all the more confusing for me because i could not view my old files in various applications once I opened the volume.

Hope this helps...

---

### Post by Traveses on 2007-04-23
Hello Dirtycash thanks for responding.  Still have a problem though
 have detailed below exactly the steps I have taken.
All is o/k down to step 14) below.
But then I don't know what the following means

* Linux Kernel Configuration
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] 
*
* General setup
*
Local version - append to kernel release (LOCALVERSION) [] 

I did not see anything like this. Should I?.

I continued however but at step 16) I have the same problem as before as follows -
	bash: cd: truecrypt-4.3-source-code/Linux/: No such file or directory

Hope ypu can help




1) 	Download TrueCrypt code at: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) (tar.gz version) to your home directory.
	I downloaded Truecrypt-4.3-ubuntu-6.10-x86.tar.gz (no version available for 7.04 at this time (April 23 2007))
	For the purpose pf this guide the username will be colin.

2)	Open the terminal. To do this go to Applications-Accessories-Terminal.
	You will see something like this username@username-desktop:~$ (username being your chosen username)

3)	cd 
	system returns colin@colin-desktop:

4)	tar xvfz truecrypt-4.3-source-code.tar.gz
	this unpacks the file and creates a directory called truecrypt-4.3 in the home directory.

Now check the version of our Linux kernel using the command below:

5) 	uname -r
	system returns in this case - 2.6.20-20-generic
	so we have to install source for 2.6.20: using the command below.

6)	sudo apt-get install linux-source-2.6.20
	at this point the sytem returns Password:
	so I enter my password
	the system returns
		Reading package lists... Done
		Building dependency tree       
		Reading state information... Done
		linux-source-2.6.20 is already the newest version.
		0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

7)	cd /usr/src/
	the system returns - colin@colin-desktop:/usr/src$

8)	sudo tar xvjf linux-source-2.6.20.tar.bz2
		At this point the system displays a long list for example linux-source-2.6.20/ubuntu/ssb/Makefile 
		and returns - colin@colin-desktop:/usr/src$ 

Create symbolic link:

9)	sudo ln -s linux-source-2.6.20 linux
	sytem asks for password
	I enter password
	the sytem returns - colin@colin-desktop:/usr/src$ 

Install tools needed for compiling:

10)	sudo apt-get install build-essential
	The system returns 	
			Reading package lists... Done
			Building dependency tree       
			Reading state information... Done
			build-essential is already the newest version.
			0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Now Check witch which version our kernel was compiled with the command below:

11)	cat /proc/version
	system returns - Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007

So we need gcc 4.1 (subversion 4.1.x is not important). Let's install it:

12)	sudo apt-get install gcc-4.1
	System returns 	Reading package lists... Done
		Building dependency tree       
		Reading state information... Done
		gcc-4.1 is already the newest version.
		0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
		colin@colin-desktop:/usr/src$ 

Let's use it and compile the modules (everything should be set to default - so answer with pressing "enter" key):

13)	export CC=gcc-4.1
	system returns - colin@colin-desktop:/usr/src$ 

14)	sudo make -C /usr/src/linux-source-2.6.20 config modules
		The system returns with al ist for example
		make: Entering directory `/usr/src/linux-source-2.6.20'
		make[1]: Nothing to be done for `/usr/src/linux-source-2.6.20/scripts/Kbuild.include'.
		scripts/kconfig/conf arch/i386/Kconfig

	This list goes on forever asking for Y/N responses
	hold down the return key takes about 2 mins. Eventualy the system will go off on its own
	this takes a long time in my case 1 Hour

	The last line returned was
	make: Leaving directory `/usr/src/linux-source-2.6.20'


* Linux Kernel Configuration
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] 
*
* General setup
*
Local version - append to kernel release (LOCALVERSION) [] 


Now, install TrueCrypt:

15)	cd
	system returns - colin@colin-desktop:~$ 
	
16)	cd truecrypt-4.3-source-code/Linux/

PROBLEM HERE  The system returns  bash: cd: truecrypt-4.3-source-code/linux/: No such file or directory

sudo ./build.sh

sudo ./install.sh

You should set this also:

Install man page to [/usr/local/man]: /usr/share/man

That's it.

Now the funniest part: mounting TC volume from the USB key to /mnt:
sudo truecrypt /media/MATTHAI/TrueCrypt/mobile.tc /mnt/
Enter password for '/media/MATTHAI/TrueCrypt/mobile.tc':

List all mounted TrueCrypt partitions:

sudo truecrypt -vl
/dev/mapper/truecrypt0:
Volume: /media/MATTHAI/TrueCrypt/mobile.tc
Type: Normal
Size: 15728128 bytes
Encryption algorithm: AES
Mode of operation: LRW
Read-only: No
Hidden volume protected: No

Let's check the encrypted files:

cd /mnt/
ls

password.txt secret.txt System Volume Information

Unmount the drive:

cd
sudo truecrypt -d

Check if it is really unmounted:

ls -l /mnt/
total 0

---

### Post by Dirtycash on 2007-04-25
It looks like you are still installing the 4.1 version of gcc.  You might run into problems with that version I am not sure.  

When you are holding enter basically you are just giving the default answer for each question.  This worked fine for me and I have had no adverse effects.  Everything is working great!

Make sure to use a capital "L" when spelling Linux for the 'cd' command.  All this stuff is case-sensitive.  

When you typed in the command from step 4, it made a directory called 'truecrypt-4.3-source-code' in the exact directory that you typed the command from.  In step 16 you are to 'cd' into the directory that 'tar' made.  Wherever you downloaded the truecrypt.tar.gz file to and then used the tar command is where this folder should be. 


So long story short, It looks like you are all set you just have to use a capital "L" in the 'cd truecrypt-4.3-source-code/Linux/' command.  This should work and then you just have to follow the rest of the guide to finish.  :guitar:

---

### Post by homunq on 2007-06-06
There's a zipped .deb file available for 7.0.4 or 6.10 available now at [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) .

---

### Post by zbyszek on 2007-08-05
I have installed truecrypt and it work fine. Except, that truecrypt demand sudo password for mounting volume. Chmod 777 and chown for other owner of the directory and encrypted file gives nothing. Is it possible to mount encrypted truecrypt volume by the other user without sudo password?

---

### Post by Matthai on 2007-08-06
I think not.

---

### Post by gbswales on 2007-08-08
Have fun and also check the documentation: [http://www.truecrypt.org/documentation.php](http://www.truecrypt.org/documentation.php)[/QUOTE]

Obviously there are people here using Truecrypt - I use it in windows and am used to an easy to use GUI interface - I am getting the impression that it is all command line stuff here?  Also I am not sure if the linux version handles  File Container encryption or not?
Lastly if it does would it be able to open container files created in windows?  If it wont then I am wasting my time trying to learn how ot install it - I am using ubuntu 7.04

---

### Post by Palmyra on 2007-09-02
> I use it in windows and am used to an easy to use GUI interface - I am getting the impression that it is all command line stuff here?

Yeah, that's pretty accurate.  The command line interface is heavily used by Linux users.  You may try using Forcefield if you'd like a Truecrypt GUI.

> Also I am not sure if the linux version handles File Container encryption or not?

In terms of features, the Linux version is no different.  If you have previously created a Truecrypt volume under Windows, you'll still be able to mount the volume under Linux provided that you still have the key you used.  

But yes, be prepared for heavy use of the terminal when requesting forum help.

---

### Post by d351GuJu on 2007-09-03
Matthai,

Thanks so much for this guide, I have followed your instructions on multiple systems with Gutsy Alpha 5 release and it worked like charm!  :)

d351GuJu

---

### Post by bluespymaster on 2007-09-03
For Feisty users who upgraded to the Gutsy Kernel, here's how I did it:

I. Update build-essential:

1. Update /etc/apt/sources.list to include the Gutsy sources. Add this line:  "deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted".
2. Run "sudo apt-get update".
3. Run "sudo apt-get install build-essential".
4. Remove the line you added in step #1, otherwise you will be notified to upgrade to other Gutsy components.
5. Run "sudo apt-get update" again.

II. Build Truecrypt:

1. Download 2.6.22 kernel from [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.6.tar.gz](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.6.tar.gz).
2. Extract the files to /usr/src and rename the created directory to "linux" (you can also create a symbolic link).
3. Download Truecrypt source code from [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php).
4. Extract the Truecrypt files to /usr/src.
5. Go to "Linux" folder (under Truecrypt) and run "sudo ./build.sh".
6. Run "sudo ./install.sh".

Good luck!

---

### Post by 50words on 2007-10-25
Truecrypt now has a .deb file available for 7.10 on their downloads page!

---

### Post by mohabe on 2007-11-13
I've just installed Ubuntu Feisty on my windows machine (yes, I know). You can imagine what I know about anything. Anyway, I got Ubuntu running and wanted to install Truecrypt (I use it with W). Downloaded the .deb filed, extrated it, found it my file system/tmp folder, right clicked on it and selected Open with "GDebi Package Installer". 
Now,
- it is on my system (File System /usr/bin)
- it works (I executed "sudo truecrypt" and got the list of options)
BUT
- I have no icon in my Applications folder, and no GUI !
Am I missing something is it just my evil windows self? 
Has Truecrypt lost the GUI it has on Windows? 
Thankx

---

### Post by JetSirus on 2007-11-18
You are very helpfull!  Thanks so much for the guide!

---

### Post by pjbgravely on 2007-11-23
> **mohabe said:**
> 
- I have no icon in my Applications folder, and no GUI !
Am I missing something is it just my evil windows self? 
Has Truecrypt lost the GUI it has on Windows? 
Thankx

There is no GUI front end for Truecrypt. I guess we should feel lucky that they even made a Linux port in the first place. As for documentation the [Man Page is all you get]("http://www.truecrypt.org/docs/?s=linux-manpage")

  Since they don't even count the amount of Linux downloads don't expect one soon. 

Paul

---

### Post by mutineer612 on 2008-01-01
I've upgraded to Ubuntu 7.10 and Truecrypt has released a nice .deb package that can be used to easily install an uninstall Truecrypt.  Looks like they also have this package for older Ubuntu vintages.  

The Truecrypt Debian package had 1 dependency for dmsetup.  The Linux Kernel Device Mapper (dmsetup) is the LVM (Linux Logical Volume Management) Team's implementation of a minimalistic kernel-space driver that handles volume management.

INSTALL
1.) sudo -i
2.) apt-get install dmsetup
3.) dpkg -i truecrypt_4.3a-0_i386.deb
[INDENT]a.)Using the -r switch for dpkg will remove Truecrypt[/INDENT]
4.) Create a directory in /mnt to use as your mount point.
[INDENT]a.)ex: cd /mnt/crypt [/INDENT]
5.) truecrypt <truecrypt container> /mnt/crypt 

Hope that helps.

---

### Post by meho_r on 2008-01-01
> **pjbgravely said:**
> There is no GUI front end for Truecrypt. I guess we should feel lucky that they even made a Linux port in the first place. As for documentation the [Man Page is all you get]("http://www.truecrypt.org/docs/?s=linux-manpage")

  Since they don't even count the amount of Linux downloads don't expect one soon. 

Paul

Oh, yes, there is a fantastic GUI: EasyCrypt. It's in Hardy's repos and can be install through Synaptic. Add this to sources:

deb [http://ppa.launchpad.net/stevenharperuk/ubuntu](http://ppa.launchpad.net/stevenharperuk/ubuntu) hardy main restricted universe multiverse
deb-src [http://ppa.launchpad.net/stevenharperuk/ubuntu](http://ppa.launchpad.net/stevenharperuk/ubuntu) hardy main restricted universe multiverse

---

### Post by kryth on 2008-01-02
There's also Forcefield [http://bockcay.de/forcefield/wiki](http://bockcay.de/forcefield/wiki)

---

### Post by kryth on 2008-01-02
^ ^ But Easy crypt is nice.

---

### Post by meho_r on 2008-01-03
Couple of days ago a member of forum (thanks, wag_) pointed out that truecrypt's activity is recorded in /var/log/auth.log where is stored your password (if you use -p parameter) in clear text, as your keyfile path and name too, which is unacceptable. Steven has found a way to avoid this security catastrophe and implemented it in EasyCrypt. 

[http://ubuntuforums.org/showthread.php?t=585578&page=17](http://ubuntuforums.org/showthread.php?t=585578&page=17)

---

### Post by mindunit on 2008-02-28
more to the point, why are you putting the password in with -p? .bash_history will even store this... passwords are not meant to be this visible!

---

### Post by maino on 2008-04-10
Just wanted to add that TrueCrypt does have a GUI now, at least the same as the one in Windows.
Simply run
```
truecrypt
```
and a window pops up.

The package I installed was version 5.1a.
```
sudo dpkg -i truecrypt_5.1a-0_i386.deb
```
and that's it.
No need to make a new directory yourself, either.
TrueCrypt makes its own directory under /media as /media/truecrypt1, /media/truecrypt2, and so on.

ADDED LATER:
The above is for using TrueCrypt for files and not the whole system.

---

### Post by Lypsis on 2008-04-10
I think the text-mode in TrueCrypt is still superior than the buggy GUI. But if you want to build it from source and use it with for an example with ext3 filesystem I wrote up a tutorial here:

[http://thiscouldbeliving.com/?p=46]("http://thiscouldbeliving.com/?p=46")

Perhaps it's useful for some guys out there!

---

### Post by Capa Pinbacker on 2008-07-28
Here is how I installed Truecrypt on 8.04, and formatting volumes with ext3 format:

1. Download & Install truecrypt using the Ubuntu deb file ([http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php))
2. You can run the truecrypt gui by opening a Terminal and typing: 
   "gksu truecrypt"

The GUI is useful for creating encrypted volumes.  In the latest version (at this time), it only allows FAT formatting, so the next thing is to change the format to Linux ext2 or ext3 by doing the following for new containers via a Terminal window:

  a) after creating/mounting your new container, type 'mount' to see what the 'dev' device is used (in my case I see "/dev/loop0 on /media/truecrypt1 type ext3 (rw)")
  b) then type 'sudo umount /media/truecrypt1' to unmount the drive
  c) now, to format it type: sudo mkfs -t ext3 /dev/loop0 (or whatever mount showed as your dev)
  d) finally type 'truecrypt -d' to release truecrypt
  e) now mount it using the GUI and verify it is ext3 formatted.

(I link my evolution mail directory to an encrypted drive, and it only works with Linux file systems, not FAT, so I need to do the formatting step).

---

### Post by WiseMaturin on 2008-12-01
I cannot get this to work at all.
Is there a less labor intensive way to do this currently?
Or can someone walk me through it?


I either don't understand what to do, or something is not going how it is expected to.

---

### Post by Matthai on 2008-12-01
Yes. Just download deb packet and doubleclick it.

---

### Post by WiseMaturin on 2008-12-01
When I download it and double-click it, it opens a file and tells me I cannot save it. It looks like it would auto-install TrueCrypt, but it's viewing the code instead of running it.

Is there a reason why?

---

### Post by Matthai on 2008-12-01
I would say it is some Firefox setting. Try to go (in Firefox) to Edit - Preferences - Applications tab - select DEB file under "Content Type" and then click on "Action" and selet Always ask.

Then try to download deb file again.

---

### Post by WiseMaturin on 2008-12-13
> **Matthai said:**
> I would say it is some Firefox setting. Try to go (in Firefox) to Edit - Preferences - Applications tab - select DEB file under "Content Type" and then click on "Action" and selet Always ask.

Then try to download deb file again.

deb doesn't even show up on the list actually. I'll try and download it again, and see if I can't get it to work the way it should.

---

### Post by jt_04 on 2008-12-14
One of the things I miss from the windows build of truecrypt is the option to automatically unmount the truecrypt volume after a period of inactivity, like an hour.  Has anyone figured out how to do this in ubuntu, or can anyone think of how it might be done?  I think this is a pretty important security feature, in case the user forgets to unmount the volume when he is done using it (which I often do).

Thanks!
-jt

---

### Post by sumwale on 2008-12-14
This should be possible even with a shell script using inotifywait -- will try to work on this sometime on next weekend.

A script which I do use is one that mounts all the favourite volumes on login and unmounts them automatically on logout. To use it:
[LIST]
[*]Save the script and copy in say /usr/local/bin (chmod +x truecrypt-init.sh && sudo cp truecrypt-init.sh /usr/local/bin)
[*]Go to System->Preferences->Sessions, click on Add button in "Startup Programs" tab and enter TrueCrypt as the name and truecrypt-init.sh as the command
[*]Add all the volumes that you want automounted on login as favourites using the "Favorites" menu item in truecrypt GUI
[/LIST]

On next login all the volumes marked as "Favorites" will be mounted by truecrypt asking for password of each volume. On logout all the volumes will be automatically unmounted. Tested with 6.1a on hardy and intrepid -- use at your own risk ...

edit: Forgot to mention that I had to add "xts" to /etc/modules to avoid truecrypt from asking for password as administrator during the unmount (truecrypt -d). Somehow the "truecrypt -d" command was asking for password which the above script cannot handle. Even though "truecrypt -d" no longer asks for password after adding "xts" and the attached script then works fine, the truecrypt mount still asks for password the first time it is started and as far as I can tell does not do anything useful with it since "xts" is already loaded.

edit2: I think some playing around with autofs/amd can also achieve the automatic unmounting requirement after inactivity.

---

### Post by Francewhoa on 2008-12-27
Another how-to install TrueCrypt [guide here]("http://www.randyjensenonline.com/blog/installing-truecrypt-51a-on-ubuntu-804"). Great for absolute beginners. It worked with Ubuntu Desktop 8.04.1 and TrueCrypt version 5.1a or 6.1a. Thanks Randy.

---

### Post by jt_04 on 2009-01-11
sumwale,

that's a good idea with mounting the volumes automatically with logon.  were you able to make anything work to automatically unmount the volume after inactivity?  just wondering.  can you explain what autofs/amd is and how to use it?

thanks,
jt

---

### Post by jackmetal on 2009-10-16
Just wanted to make a quick reply here (I know, it's an old topic); but I wanted to say thanks to sumwale.  I was just looking into this when I stumbled across your script to Auto Mount/UnMount the TrueCrypt volumes!  

so...sumwale, Thank-You!!

---

### Post by JobeJahova on 2009-10-20
Hi. I'm trying to get truecrypt installed on my Ubuntu machine. I have a large partition using ext4 with encryption. It is a /home partition for a Fedora 10 x86_64 install. It works fine in Fedora 10, but it is not seen with Ubuntu 9.04 32-bit. 

When I try to install the 32-bit truecrypt by double-clicking the package (after extracting it), the installer opens it but the "install package" button is greyed out.

Here is a thread I posted about it:
[http://ubuntuforums.org/showthread.php?t=1296289](http://ubuntuforums.org/showthread.php?t=1296289)

Here is a screenshot:
[http://ubuntuforums.org/attachment.php?attachmentid=132522&d=1256060230](http://ubuntuforums.org/attachment.php?attachmentid=132522&d=1256060230)

I was hoping to use this partition as a /home for ubuntu sometime.

---

### Post by pjbgravely on 2009-10-30
Why are you trying to install truecrypt without using the repositories? If you need a newer version try [http://www.getdeb.net/]("http://www.getdeb.net/"). 9.10 has ext4 encryption. That may be the way to go.

Paul

---

### Post by mordak13 on 2009-11-20
> **pjbgravely said:**
> Why are you trying to install truecrypt without using the repositories? If you need a newer version try [http://www.getdeb.net/]("http://www.getdeb.net/"). 9.10 has ext4 encryption. That may be the way to go.

Paul
Truecrypt isn't listed as an available package in my Ubuntu install. What repo is it in?

---

### Post by doas777 on 2009-11-20
> **mordak13 said:**
> Truecrypt isn't listed as an available package in my Ubuntu install. What repo is it in?

howdy,

truecrypt is available at [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) . just grab the .deb for your platform. doubleclick to open the package manager and install. this guide is way out of date, and it is far easier now.

---

### Post by mordak13 on 2009-11-20
> **doas777 said:**
> howdy,

truecrypt is available at [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) . just grab the .deb for your platform. doubleclick to open the package manager and install. this guide is way out of date, and it is far easier now.
Yep I did that already but I thought it used to be in the repo. Just wondering.

---

### Post by doas777 on 2009-11-20
> **mordak13 said:**
> Yep I did that already but I thought it used to be in the repo. Just wondering.
nope. I think the problem is licenses. truecrypt is composed of items under like 12 differant types of licenses.

---

### Post by Dezfor on 2010-03-26
i have strange problem. I want to encrypt my container with Blowfish-448. There is no blowfish in my truecrypt 6.3a,but on the Net i can see that TrueCrypt supports it. On official web-site i found nothing. Could u help me with configuring Blowfish for TrueCrypt

---

### Post by thejoeyz on 2010-04-02
I'm a new Ubuntu user here. 

I've tried many Linux distributions over my 24 years of working on, with and around computers and I must say that Linux in any form is still no where near ready for the general public. It is crazy to me that everything in a Linux distribution (I'm using Ubuntu's latest version) is so difficult to complete. 

My problems started with the installation of Ubuntu. I was attempting to do a dual boot with 2 separate hard drives. Long story short, 6 hours, 2 Ubuntu installations and a rebuild of my Windows MBR, I was able to get Ubuntu on one hard drive without messing with my Windows XP Pro on the other hard drive. I ended up using my system's BIOS Boot options to boot to either Windows or Ubuntu....nothing should be this difficult. 

So I'm happy and all is working well until I attempt to upgrade Firefox from 3.5xx to 3.6xx. What a fringing joke...the task on a Windows computer would take all of 30-45 seconds but with Ubuntu I had to search Web sites for instructions and though I finally got Firefox upgraded to the latest version, it took almost 2 hours from start to finish! This is crazy...

Now I'm trying to use TrueCrypt which I have used for years on my Windows computers and so far It's been over 2 hours of terminal codes and compiling and I  have to do this with every upgrade? This is insane???

I tried Ubuntu because it was said to be the most user friendly and I wanted to use a Linux based OS for more security on line while banking and such. But all one needs to do is search Google for Ubuntu and you will see that tons of people are asking for help with this or that. 

I guess you can not expect something that is free to work without issues....but my time is worth something.

IMO...Ubuntu has nothing over Windows 7 or Windows XP other than it's free.  A user should not have to reinvent the wheel every time they need to install or uninstall software....

I'm not sure if I'm going to keep using Ubuntu or not...I'm still waiting for the compiling for TrueCrypt to finish at which time I'm sure another issue will certainly appear.

Frustrated Ubuntu newbe,

Joe

---

### Post by pjbgravely on 2010-04-03
> **thejoeyz said:**
> I'm a new Ubuntu user here. 


Now I'm trying to use TrueCrypt which I have used for years on my Windows computers and so far It's been over 2 hours of terminal codes and compiling and I  have to do this with every upgrade? This is insane???


Frustrated Ubuntu newbe,

Joe

Um, Truecrypt offers a binary for Ubuntu. [ Get it here.](http://www.truecrypt.org/downloads) Down load the script for what you want, standard is the GUI version. Next right click on the tar file and click extract here. Click on the extracted truecrypt script, and then click run. click install and it should install fine. It should be in the menu and you click to run. Otherwise open a terminal and type truecrypt. 

Almost no one compiles anything anymore, and although trucrypt no longer seems to supply a .deb anymore their system seems to work.

  As for your install problem, I am guessing it was a Grub2 problem that kept you from dual booting. Microsoft windows xp pro has a boot loader that can boot Linux, you might want to try that. Personally I haven't used Microsoft products in 7 years so I do very little with dual booting OS's. You might also try using a VM next time. It will let you learn without risking borking your system.

Paul

---

### Post by Objectivity on 2010-06-12
[SIZE=4] PLZ need help. Do you folks know WHERE THE HECK is " Auto dismount " option in trycrypt for LINUX ? STRANGE ! windows has it but linux version does not ! or maybe I am do not know how to fix it. This feature is very important to me as I sometimes forget to dismount my volume.

 Thank you for your help.
   Objectivity
[/SIZE]

---

### Post by Objectivity on 2010-06-12
[SIZE=4]PLZ need help. Do you folks know WHERE THE HECK is " Auto  dismount " option in trycrypt for LINUX ? STRANGE ! windows has it but  linux version does not ! or maybe I am do not know how to fix it. This  feature is very important to me as I sometimes forget to dismount my  volume.

 Thank you for your help.
   Objectivity[/SIZE]

---

### Post by gacb on 2010-08-05
Ah, but you're thinking like a Windows user, where everything is hard until you figure it out.

With Ubuntu, things are just easier, such as burning an ISO. No Nero to download, not licence to verify; just right-click the file and choose 'burn disk'.

Try using the Update Manager once in a while, and if you want the latest greatest versions before they are considered 'safe', just enable them in Software Sources.

Once you use Ubuntu for a few weeks, you'll get more used to easy solutions for your issues.

---

### Post by chrcoe on 2010-10-08
> **thejoeyz said:**
> I'm a new Ubuntu user here. 

I've tried many Linux distributions over my 24 years of working on, with and around computers and I must say that Linux in any form is still no where near ready for the general public. It is crazy to me that everything in a Linux distribution (I'm using Ubuntu's latest version) is so difficult to complete. 

My problems started with the installation of Ubuntu. I was attempting to do a dual boot with 2 separate hard drives. Long story short, 6 hours, 2 Ubuntu installations and a rebuild of my Windows MBR, I was able to get Ubuntu on one hard drive without messing with my Windows XP Pro on the other hard drive. I ended up using my system's BIOS Boot options to boot to either Windows or Ubuntu....nothing should be this difficult. 

So I'm happy and all is working well until I attempt to upgrade Firefox from 3.5xx to 3.6xx. What a fringing joke...the task on a Windows computer would take all of 30-45 seconds but with Ubuntu I had to search Web sites for instructions and though I finally got Firefox upgraded to the latest version, it took almost 2 hours from start to finish! This is crazy...

Now I'm trying to use TrueCrypt which I have used for years on my Windows computers and so far It's been over 2 hours of terminal codes and compiling and I  have to do this with every upgrade? This is insane???

I tried Ubuntu because it was said to be the most user friendly and I wanted to use a Linux based OS for more security on line while banking and such. But all one needs to do is search Google for Ubuntu and you will see that tons of people are asking for help with this or that. 

I guess you can not expect something that is free to work without issues....but my time is worth something.

IMO...Ubuntu has nothing over Windows 7 or Windows XP other than it's free.  A user should not have to reinvent the wheel every time they need to install or uninstall software....

I'm not sure if I'm going to keep using Ubuntu or not...I'm still waiting for the compiling for TrueCrypt to finish at which time I'm sure another issue will certainly appear.

Frustrated Ubuntu newbe,

Joe

not to bring up old threads, but i was trying to get some info on TrueCrypt and found this thread, then I ran across this.  The problem is that he has been around what it seems like Windows only environments for 24 years.  Everything takes him 30-45 seconds to do in Windows.  Maybe it's because he's most likely a windows pro, just like kids that have used it for 10 years, things seem to be much easier when you've used them your whole life.

This is a completely different OS, you can't assume it will work the same way as Windows, or Mac.  You need to work with it and get used to the way things work on linux platforms, then it all becomes second nature and then the only thing slowing you down might be your computer's speed when you install/uninstall things, sort of like windows and mac right?

/rant

I do not have access to my kubuntu right now, so I can't check, but does this have an apt-get installation yet?  or do I still need to DL from their main site?

-chrcoe

---

### Post by clay.michaels on 2011-01-08
Do any of you fine folks know where an enterprising gentlemen could stumble across a .deb for TC? I've searched extensively, and I also tried to make my own from source without luck. Frankly, it was my first time trying to build source and I probably messed it up. 

I know how to install it, but I want a .deb file too. Is it outside the realm of possibility for someone to make a .deb and upload it somewhere? My email address is my forum username at gmail, if that's easier.

Regards,
Clay

---

### Post by user790 on 2011-10-20
FYI, I came across this discussion because I was too looking for a way to install TrueCrypt on 11.10, as it isn't in the standard repositories.

As explained above, the solution is simply to download the installer from the truecrypt website. Took me about 10s to install, works fine.

As for the rant of [thejoeyz]("http://ubuntuforums.org/member.php?u=1047479"), although everybody agrees that Linux is different from Windows, and in some way less friendly (I'm thinking particularly about peripherals), you need to be fair. Here's an eye opener: you rant about how you struggled installing Ubuntu on a Windows machine (which is not my experience btw), but you failed to notice that installing Windows on a Linux machine is, well, not possible.

---

