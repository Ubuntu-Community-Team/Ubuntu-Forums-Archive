---
title: "Licencing problem with Autodesk Maya 2009"
date: 2009-05-08
forum: Ubuntu Studio
---

### Post by mickie.kext on 2009-05-08
I instaled Maya on Ubuntu. I have legal license, used it on Windows. But every time I try to install license, it sez that my HostID is invalid. I have OSx86 and Vista installe on same computer, and Maya works on both those OS-es. With same licence. But on Ubuntu, does not. I tried manualy editing the AW file, but problem persists. I appears that Maya can't se my MAC addres. Here is what I get when enter to License Utility Tasks. It should list Ethernet Controllers (does that in Windowz an OS X) but is empty

---

### Post by mickie.kext on 2009-05-08
Is there any package I should install in order to Maya se ethernet adresses. And to be able to install licence. I yust called Autodesk technical support, and they say that same licene should work on every OS as long is the same computer.

---

### Post by mickie.kext on 2009-05-08
come on guys, I really hate using Windowz, but need Maya. I talked with tech support guys again, and they confirm that hardware identifier must show Ethernet adapters, and that is the problem. What should I install to get hardware identifier seing mu LAN controllers?

---

### Post by lukeiamyourfather on 2009-05-08
Usually that FlexLM crap uses the MAC address of the LAN adapter which should already be available to the licensing utility. Is the network adapter functioning normally, can you access the internet, does it show up in the network manager?

Not sure if this is related or not but Houdini doesn't like it when the system has the default name of "localhost" on the network. Maybe try it on Fedora or something else since they might be accessing the network adapter information with a method not supported in Ubuntu. Cheers!

---

### Post by kayosiii on 2009-05-08
It really really depends on what method the Flexlm guys are using to get the MAC Address of the card.... for instance if I want to know the MAC address of any of my ethernet adapters. I simply type in ifconfig.

ifconfig

It appears that (after a little research) flexlm will freak out if your main ethernet adapter isn't eth0; (which in IMO is just as retarded as Maya looking for your wacom tablet by the name it's called in xorg.conf)....  

could you type ifconfig into a terminal and post the output here?...

---

### Post by mickie.kext on 2009-05-09
Thank guys for the reply. I know about ifconfig comand, and I alredy used it. It shows both of my Ethernet controlers and internet is working fine. MAC adress is the same as in Windows and Maya works in Windows. I don't want to paste mt MAC adress here, afraid of hacking :sad: 

I did not managed to get it working... 

Network is working fine and controllers are shown in network connections:

---

### Post by mickie.kext on 2009-05-09
eth3 is for internet and that is the one I ned to show to Maya

vboxnet is from Virtual Box machine, and eth2 is for LAN with other computer in the room. All is working fine, I am sure that is only problem in Maya not seing the Ethernet controller. I remember when installing in windows, hardware identifier screen was listin Ethernet controlers and showed MAC addreses. 

I posted what shows in Linux. NOTHING. 

I am pretty pised of because my free Ubuntu wont work with expensive software... if is up to me I would use Blender, but company bought me Maya and they want results. And I uncomfortable working in Window$ and fell that I can do better in Linux. 
Please help

---

### Post by mickie.kext on 2009-05-09
I just tried with reinstall of Maya and did not get it work. But I noticed something interesting. In Linux64 folder of maya DVD, there are folowing .rpm files: 
MAYA2009.RPM
MAYA2010.RPM
AWCOMMON.RPM
AWCOMMO1.RPM

I used installing tutorial from here [http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/](http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/)

When I conwerted, I only got two .deb files and two corrupted folders. Here is folder with old files along with that converted:

---

### Post by mickie.kext on 2009-05-09
I think that those files that did not converted(so are not installed)are the source of trouble. It has AW in name, AW is licence file. So I tried to convert those separetly and got this:

```
miki@miki-desktop:~/MayaInstall/LINUX_64$ sudo alien AWCOMMON.rpm
Warning: Skipping conversion of scripts in package AWCommon: postinst postrm
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
		xargs -0 -r -i cp -a {} debian/awcommon
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: symbol XtStrings used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XScreenCount used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XBell used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XOpenIM used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XpQueryExtension used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XWidthOfScreen used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XtMergeArgLists used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XPutImage used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetOMValues used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XtMalloc used by debian/awcommon/usr/aw/COM/lib/libXm.so.2.1 found in none of the libraries.
dpkg-shlibdeps: warning: 432 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: dependency on libXp.so.6 could be avoided if "debian/awcommon/usr/aw/COM/bin/installKey" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libm.so.6 could be avoided if "debian/awcommon/usr/aw/COM/bin/lmutil" were not uselessly linked against it (they use none of its symbols).
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: `AWCommon-11.5': No such file or directory
```

I gues that I am forced to switch to some RPM distro unless someone here gives me better idea. If not, please recommend me RPM distro to use. I dont like Fedora and SuSe, to bugy. I have Mandriva on DVD. I maybe can download some other...

---

### Post by kayosiii on 2009-05-11
From the  following article it seems that Eth0 may need to be physical hardware. [http://www.artwork.com/support/linux/eth0_configuration.htm](http://www.artwork.com/support/linux/eth0_configuration.htm)
I am not sure how you would go about reconfiguring your machine to make sure that eth0 was a real network card with a real mac Address.

---

### Post by mickie.kext on 2009-05-11
But I tried manualt changing controller name to eth0, and still did nothing. Thank for that link, but it sems to complicated, and I dont want to have static IP adress. 

I have question. Is it normall to get only two deb. out of four RPMs ? I posted picture on this thread. Only two main files got converted by alien. Is that enough? I think that missing two files are the part of the problem...

---

### Post by skullmunky on 2009-05-11
It has to be eth0.  I smashed my head against this for ages with other versions of Maya because it is not documented.  I solved it before, and I'll see if I can remember how I did it.

You -could- try installing an officially supported distro, because then Autodesk might be slightly more able to help you - but I bet it won't matter.

Just checking, are you running Linux in VirtualBox or native?

When you said you changed the controller's name, how did you do it?

---

### Post by skullmunky on 2009-05-11
real quick - i gotta run right now - but look in
 
/etc/udev/rules.d/

at the file

70-persistent-net-generator.rules

it maps hardware devices to device names, so try changing it there.

EDIT:

ok, try this.

```

sudo gedit /etc/udev/rules.d/70-persistent-net-generator.rules

```

here's what my macbook has:
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x168c:0x001c (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:f2:3f:00:ef", ATTR{type}=="1", KERNEL=="ath*", NAME="ath0"

# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:cb:8e:ae:e1", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

The first is for my wifi card, the second is for my ethernet card.  Look for NAME="eth3" and change it to NAME="eth0"

then do a hard reboot.

---

### Post by mickie.kext on 2009-05-12
I was runing ubuntu native. Not VBOX. VBOX was just installed in ubuntu, so that controller was shownig. I am saying in past tense because I formated ubuntu partition and tried: Fedora, SuSe, Mandriva. Fedora Live CD won't boot and goes Kernel Panic. SuSe works fine and installs fine untill I install FGLRX, and then X breaks and I cant get to desktop. Just console. And Mandriva bricks prety much like openSuSe, just on first boot. Probablly because FGLRX display driver is included and activated from start. I will switch back to Ubuntu when I get some free time. And I will try again.

When I say "renamed to eth0 manually" i mean right click to network icon in panel and go to edit conections, and then changing in name field. Next I will try that your advice skullmunky but I am pretty sure it wont work. I am concerned with that two files that did not get converted with alien. One of them is licence server and anotger licence client.

[http://ubuntuforums.org/showpost.php?p=7247976&postcount=9](http://ubuntuforums.org/showpost.php?p=7247976&postcount=9)
[http://ubuntuforums.org/showpost.php?p=7247958&postcount=8](http://ubuntuforums.org/showpost.php?p=7247958&postcount=8)

Those two post says prety mutch what is the problem. Alien wont convert two RPM files who are responsible for licencing:confused:

---

### Post by kayosiii on 2009-05-12
I would like to note that in Jaunty udev's configuration files are in /lib/udev rather than /etc/udev I can't remember which version the OP said they were using but is worth noting.

Also it is worth noting that the rpms seem to be for a 32bit version of MAYA or at least the parts that won't convert are (Alien seems to be failing because of this)....
You may have a lot more luck with 32 bit version of Ubuntu or at least use a 32bit version of the system to convert the packages...

---

### Post by skullmunky on 2009-05-13
Good point about trying the 32bit, although, if it does launch and get to the point where it complains about the license, that's a good sign.

@mickie: don't worry about the awcommon.rpm and awcommon-server.rpm.  Yes, those packages typically do give errors when you try to convert it; there are ways to fix that, but luckily it doesn't matter, you don't actually need it.  

The license server is used if you have multiple computers running Maya, and you want to store all the licenses on a central server instead of having to assign one to each individual machine.  In your case you do not need it, since you have just a single nodelocked license file.

All awcommon has is other little license installing tools.  If you know how to copy your aw.dat into /var/flexlm, you don't need them either.  You can safely ignore both of those RPMs.


I suspect the "Right-Click and Change the Interface Name" may not change it as deeply or completely as it needs to, so try editing the udev rules manually, reboot, and see if that helps.

After you do the edit and reboot, open a terminal, run the command
```

ifconfig

```
and post the output.

also, post the contents of the file ```
/etc/network/interfaces
```.  more information is always better. :)

Another note about converting the RPM's : if converting into debs is giving you horrible problems, you can also just convert the RPM to a tar.gz archive with ```
alien -t *.rpm
```.

Extract the archive, it'll just make a folder which will look something like
```

/usr
  /autodesk
    /maya2008
      etc.

```

You can manually do the installation by just copying the autodesk folder into your /usr folder.  This method doesn't set up the menu shortcuts etc., but all that can be done by hand pretty quickly too.

Usually RPM and DEB packages are important because they put a lot of files into a lot of different places.  Maya is different, it's basically all just in one folder, like a Windows or Mac application.

---

### Post by mickie.kext on 2009-05-13
Thanks for help guys, but I installed Fedora instead of Ubuntu, thinking it will be easier. But no. Fedora 10 did not boot, so i used Fedora 11 preview. And it works (I mean OS works), but I am still having troble with maya. I installed all four RPMs, but maya won't start. 

It say:
```
Failed to execute child process "/usr/autodesk/maya/bin/maya" (No such file or directory)
```

And then I remember that Openmotif and FAM are needed, but they are nowhere to be found in Fedora repositories. I can't find them??? I cant use that openmotif in support folder because fedora wont start it. 

I am yet to come to licencing problem with fedora :o  First starting problem](*,)

Where can i find FAM and Openmotif RPMs for Fedora?

---

### Post by mickie.kext on 2009-05-13
I installed GAMIN and Openmotif, and nothing changed. Still can't start maya

---

### Post by skullmunky on 2009-05-14
No idea about anything with Fedora, but that error looks like something else.  It looks like the file /usr/autodesk/maya/bin/maya is missing, so you should look and make sure it's actually there.  

In these screengrabs, note that the "maya" folder is actually an alias to the "maya2008" folder.  Yours should be an alias to the "maya2009" folder.

Similarly, the actual program "maya" is an alias to "Maya2008".  Yours should be an alias to the "Maya2009".

If Maya is launching now, but the FlexLM still isn't recognizing your ethernet MAC address, then it's probably the same issue as on Ubuntu - the ethernet card needs to be named eth0.   If you can, please post the output of the "ifconfig" command and try editing the udev rules file.  If you like, post the contents of "70-persistent-net.rules", which should be in /etc/udev/rules.d, or in /lib/udev/rules.d.  (That's for ubuntu, probably in the same place in Fedora, but let me know if you can't find the file).

---

### Post by mickie.kext on 2009-05-14
I deleted stupid Fedora and installed Ubuntu again. And converted those two AWCommon RPMs to deb via 32bit ubuntu in Vbox. But when I tried to install them od my main (host) ubuntu, it sez that is wrog arhitectue. i386. And i use 64-bit So I gived up those two files an instaled other two which is 64-bit and more important. I insatled Maya. And now I cant even get to Licencing. It is like Fedora again. First was the same mesage, and now I installed csh, and when I tupe Maya in terminal I get this

```
sh: apcw: not found
```

---

### Post by mickie.kext on 2009-05-14
I am going crazy... this always pops out

```
sh: apcw: not found
```

---

### Post by mickie.kext on 2009-05-14
Heeeelp :sad::sad: Heeeeeeeeeeeeeeeeeeeelpppp


](*,)](*,)](*,)](*,)](*,)

---

### Post by skullmunky on 2009-05-15
First, take a deep breath .... :D

1. Seriously, don't worry about the awcommon debs. 
2. You might try installing the 32 bit (i386) version of Ubuntu and the 32 bit (i386) version of Maya, and see if that works.  If it does, then that'll help in making the 64 bit version work.
3. "apcw" is the "Autodesk Product Configuration Wizard", the program that you use to show the hardware identifier and install license files. 

It should be in /usr/autodesk/maya/bin.  If it's not found, then that means there's some small error with installation, probably having to do with correct aliases between directories.  

Try this:

1. go into the maya directory:
```

cd /usr/autodesk/maya/bin

```
Did that give you an error like "No such file or directory"?  If so, just try 
```

cd /usr/autodesk ; ls -l

```

and show me what's in there.

2. list the files that are in /usr/autodesk/maya/bin:
```

ls -l

```
3. is "apcw" in there?  how about maya?  

4. assuming yes, launch maya from inside this directory:
```

./maya

```

does it still complain about apcw not being found?

5. try
```

./apcw

```

if apcw is actually there.

Don't forget, we probably still need to fix your ethernet issues, so post that info when you can.

---

### Post by mickie.kext on 2009-05-15
Thank yo for your efort man. Both of the files are there
```

-rwxr-xr-x 1 root root   72047 2006-08-22 19:56 **apcw**
-rw-r--r-- 1 root root   56442 2008-09-11 07:23 BatchRenderWrapper
-rwxr-xr-x 1 root root    5019 2008-09-11 06:04 blur2d
-rwxr-xr-x 1 root root   72947 2008-09-11 07:23 blur2d.bin
drwxr-xr-x 2 root root    4096 2009-05-15 01:07 Cg
-rw-r--r-- 1 root root 3351216 2008-09-11 06:02 cgc
-rwxr-xr-x 1 root root    4995 2008-09-11 06:04 delace
-rwxr-xr-x 1 root root  238752 2008-09-11 07:23 delace.bin
-rwxr-xr-x 1 root root    8675 2008-09-11 07:23 dispatch_maya_render
-rwxr-xr-x 1 root root    8864 2008-09-11 06:17 eLutExe
-rwxr-xr-x 1 root root    4995 2008-09-11 06:04 fcheck
-rwxr-xr-x 1 root root  264396 2008-09-11 07:23 fcheck.bin
-rwxr-xr-x 1 root root 2202496 2008-09-11 06:04 fg_copy
-rwxr-xr-x 1 root root    4994 2008-09-11 06:04 filePaste
-rwxr-xr-x 1 root root   15833 2008-09-11 07:23 filePaste.bin
-rwxr-xr-x 1 root root    4995 2008-09-11 06:04 fileStats
-rwxr-xr-x 1 root root   12814 2008-09-11 07:23 fileStats.bin
-rwxr-xr-x 1 root root  925321 2008-09-11 07:24 FurRenderer
-rwxr-xr-x 1 root root   36831 2008-09-11 06:02 helpTable
-rwxr-xr-x 1 root root     306 2008-09-11 06:04 imconvert
-rwxr-xr-x 1 root root 3167744 2008-09-11 06:04 imf_copy
-rwxr-xr-x 1 root root 3170912 2008-09-11 06:04 imf_diff
-rwxr-xr-x 1 root root 3262000 2008-09-11 06:04 imf_disp
-rwxr-xr-x 1 root root 3170080 2008-09-11 06:04 imf_info
-rwxr-xr-x 1 root root    5257 2008-09-11 06:04 imgcvt
-rwxr-xr-x 1 root root  440052 2008-09-11 07:23 imgcvt.bin
-rwxr-xr-x 1 root root    4995 2008-09-11 06:04 imgdiff
-rwxr-xr-x 1 root root   82199 2008-09-11 07:23 imgdiff.bin
-rwxr-xr-x 1 root root    5236 2008-09-11 06:04 interlace
-rwxr-xr-x 1 root root   20801 2008-09-11 07:23 interlace.bin
drwxr-xr-x 2 root root    4096 2009-05-15 01:07 l10n
-rwxr-xr-x 1 root root    1105 2008-09-11 06:04 launchNetscapeHelp
-rw-r--r-- 1 root root       0 2008-09-11 06:02 License.env
lrwxrwxrwx 1 root root       8 2009-05-15 01:08 **maya -> maya2009**
-rwxr-xr-x 1 root root    6551 2008-09-11 06:04 **maya2009**
-rw-r--r-- 1 root root    6549 2009-05-14 23:59 **maya2009~**
-rwxr-xr-x 1 root root  288201 2008-09-11 07:25 **maya.bin**
-rwxr-xr-x 1 root root   28125 2008-09-11 07:27 mayaClockServer
-rwxr-xr-x 1 root root    6542 2008-09-11 06:03 mayald
-rwxr-xr-x 1 root root     189 2008-09-11 06:02 mayapy
-rwxr-xr-x 1 root root   37794 2008-09-11 07:27 mayaServerTest
-rwxr-xr-x 1 root root 1530360 2008-09-11 06:04 mkmishader
-rw-r--r-- 1 root root    6852 2008-07-29 16:13 pcw_mayaopa.xml
drwxr-xr-x 5 root root    4096 2009-05-15 01:07 plug-ins
-rw-r--r-- 1 root root   13986 2008-09-11 06:03 precompTemplate.py
-rwxr-xr-x 1 root root   10231 2008-09-11 06:02 python-bin
-rwxr-xr-x 1 root root  399408 2008-09-11 07:23 Render
drwxr-xr-x 2 root root    4096 2009-05-15 01:07 rendererDesc
-rwxr-xr-x 1 root root   43714 2008-09-11 06:02 stdlib.aws
-rwxr-xr-x 1 root root   18808 2008-09-11 06:03 stdlib.msl
-rwxr-xr-x 1 root root    9212 2008-09-11 06:17 toFloatExe
-rwxr-xr-x 1 root root   26482 2008-09-11 06:04 toxik-maya-import.py
-rwxr-xr-x 1 root root    1362 2008-09-11 06:04 toxpm
-rwxr-xr-x 1 root root    4008 2008-09-11 06:04 wrl2ma
-rwxr-xr-x 1 root root  716950 2008-09-11 06:17 wrl2ma.bin
```

That is with **ls -l** of **usr/autodesk/maya/bin** I higlighted everything I think it is important, so you can see right away.

---

### Post by mickie.kext on 2009-05-15
```
apcw: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS64
```

^this is what I get when I do **./maya** from within **usr/autodesk/maya/bin** 

```
./apcw: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS64
```
^ That is with **./apcw **

---

### Post by skullmunky on 2009-05-15
great, getting closer.  

That error (probably) means it's trying to run 64 bit code, but you are actually in a 32 bit operating system.  It probably means you installed the standard "i386" version of Ubuntu, instead of the "x86_64", 64 bit version.  You mentioned you had installed the 64 bit version of Maya, so I think that might be problem.  

If you're not sure which version of Ubuntu you installed, you can always check with the "uname" command in the terminal:

```

uname -a

```

if you see "i686" or similar, you have the 32 bit version of linux installed.  If you see "x86_64", then you have the 64 bit version installed.  

My guess is you have Ubuntu 32 bit installed, so my next move would be to just go ahead and install Maya 32 bit and see how that goes.

---

### Post by mickie.kext on 2009-05-15
> Linux miki-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

It is 64-bit ubuntu and 64-bit Maya. I dont have 32-bit maya for linux to install. 

And I dont fell like going back to 32-bit linux because I have 8GB of RAM. I can try with VBOX but what's the point?

---

### Post by mickie.kext on 2009-05-15
First time when I installed maya, I did not have that problem. It was only licencing problem. I dont know why i formated when it only got worse:-?

---

### Post by mickie.kext on 2009-05-15
Sorry for spamming man... are you here??? I dont know what to do. I just unisntalled maya and now I am converting again with alien. You give some idea please.

---

### Post by mickie.kext on 2009-05-15
It is not converted properly with alien. I must try again

---

### Post by mickie.kext on 2009-05-15
apcw: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS64


Installed, still geting this ^

I saw this thread [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7043882](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7043882)

But I cant find those libs that guy talks about.

---

### Post by mickie.kext on 2009-05-15
How can I convince Maya that my OS is 64-bit?

---

### Post by skullmunky on 2009-05-15
I'm guessing a little - I don't actually use 64bit so I can't test some of this.

so it -is- a 64bit maya, and 64bit ubuntu.  hmm, so where the heck could that error be coming from?  I googled "apcw linux 64" and got some answers.  Apparently it is because the apcw program is NOT 64 BIT!  (good job, Autodesk).  

You can verify this with the "file" command in the terminal:

```

file apcw
apcw: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), not stripped

```

that's my apcw, which is for a 32bit install of Maya 2008 on 32 bit Ubuntu 8.04.  If yours says the same - ELF 32-bit - then there's the culprit.  *grrr*

Try installing the package "ia32-libs":

```

sudo apt-get install ia32-libs

```

that has some of the libs you need, like libstdc++, in 32 bit form.  

This might explain why you didn't get stuck on this step originally - if you had that initial ubuntu installation for a while and installed other stuff on it, from time to time, some other app could've very easily installed the 32 bit library dependencies.  

You know, if your license key works, then apcw never runs at all.  It may be that if we can fix your original problem - ethernet card not showing up as eth0, hence license not recognized - it'll just work.  So we could also take a little detour down that route, just for kicks - give me the output from 
**ifconfig** and the contents of **/etc/udev/rules.d/70-persistent-net.rules**

---

### Post by mickie.kext on 2009-05-16
It makes perfect sense. IA32 libs was missing, and now I can get to licencing part again. And now, it shows one controler in hardware identifier, but wrong one :biggrin: and it wot't get licence.  I figure that is eth0 issue. Just send you those two infos via private message. I tried switching internet cable to another controller, but still it shows wrong controller. I need to rename it ti eth0. Butt don't know how. 

I am also thinking of reinstalling Ubuntu with cable switched, to force that other flaging as eth0. But that will mean mor tinkering with FLEXLM/AW for licencing, and probably calling Autodesk tech again... and they charge call in my country...

---

### Post by thedaemon on 2009-05-16
I am having the same problem, but with 8.5. Could be the Eth0 thing, I will check it out, thanks.

---

### Post by mickie.kext on 2009-05-16
Please post if you solve the problem.

---

### Post by mickie.kext on 2009-05-16
It works, it works:guitar::guitar::popcorn:

I reinstalled Ubuntu with ADSL cable swiched to another controller to force it to be recognized as eth0. And then installed all dependencies, installed maya, and tried. And it did not work rigt away, but I had to regenerate my licnence in windows, and change OPA hardvare idnetifier to that controller, and I had to call tech support again. So I now copied that AW file from Windowz in Ubuntu /var/flexlm and is now working

See:

---

### Post by mickie.kext on 2009-05-16
Full dependencises, thanks to Skullmunky:

csh
GAMIN
libmotif3
Alien 
ia32-libs

And internet conection on **eth0** (that is the hardest part)

Tutorial for install... I used this one [http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/](http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/)

---

### Post by mickie.kext on 2009-05-16
Thanks skullmunky, I would never do it witout your help. I owe you big :D

Also thanks to Madman who made tutorial for converting and installation. And not thanks to Autodesk who take insane money and then make problems. Shame on them:mrgreen:

---

### Post by skullmunky on 2009-05-16
:popcorn::popcorn::guitar::popcorn::popcorn:

Fantastic!

---

### Post by mickie.kext on 2009-05-21
Hey guys, do I seeing things or is Linux version of Maya severely striped down. Like half of options in missing or misplaced... Is Autodesk planing to kill Linux version of Maya??

---

### Post by skullmunky on 2009-05-21
I don't think so - what's missing?

---

### Post by mickie.kext on 2009-05-22
> **skullmunky said:**
> I don't think so - what's missing?

I found it! Surface menu was missing, but now I found it. It was probably my fault, I messed up menus somehow. Now I switched it back to default. The whokle openMotif UI has me confused... So I still not use Linux full time.

---

### Post by skullmunky on 2009-05-22
ha, yeah, Motif takes a while to get used to.  I wish they'd switch to something more modern, like Qt.  I don't mind the look of Motif that much, although I notice people tend to get really confused by the style of the radio buttons and checkboxes and can't figure out when they're "activated" or not.   My only real complaint is the horrible file browser window.  On the other hand Motif is pretty rock solid and dependable, so there's something to be said for that.

If you can't get sound import to work, I have some things to try - I'm curious about whether this'll work for other people.  

Test case: Import a standard WAV file (44KHz, 16 Bit PCM).  Put it in the timeline and try to play it.  

Error 1: can't find libaudiofile.so; unable to import the WAV file at all.

Fix: libaudiofile should be there, it may just be named "libaudiofile.so.0". 

Look in the /usr/lib directory for "libaudiofile.so.0":

```

ls -l /usr/lib/libaudiofile*

```

if there's a libaudiofile.so.0 but no libaudiofile.so, make a link:

```

cd /usr/lib
sudo ln -s libaudiofile.so.0 libaudiofile.so

```

Error 2: "Can't Open Audio Port".  Importing works and you can put the sound in the timeline, you get the waveform, but when you try to play you get this error in the script editor, and no sound.

Fix: Use the alsa-oss emulation tools.  Maya still uses the OSS sound library, which is ancient and doesn't play well with modern distros that use more modern sound systems like ALSA and Jack.  The biggest limitation to OSS here is that if anything else uses the sound card, then Maya can't access it.  "Anything else" includes even just the GNOME or KDE desktops.

Luckily there's a thing called "alsa-oss" emulation, which lets old OSS-using apps work ok in a newer system that uses ALSA.

1. install "alsa-oss" 
```

sudo apt-get install alsa-oss

```

2. edit the Maya launcher script: the file "Maya2009" in /usr/autodesk/maya/bin.

this is not actually a binary executable, it's a text script that sets up the environment for running maya, so you can tweak things in it.  Open it in a text editor:

```

sudo gedit /usr/autodesk/maya/bin/Maya2009

```

look down towards the bottom, for the section labeled "Set up the location of the DSO's and run".  Before that, paste in these lines:

```


# Set up ALSA - OSS Emulation

if (-d "/proc/asound") then
  setenv LD_PRELOAD /usr/lib/libaoss.so


```

that tells it to load the Alsa-OSS emulation library.

now run Maya as usual, see if sound playback works.  I tested this in Maya2008 on Kubuntu Jaunty 64 bit, and it worked great, no skipping, scrubbing is fine, etc.

---

### Post by jsday187 on 2009-06-09
Crikey, is this guy one of those Help Vampires I've been hearing about or what? 
Pretending he has a legit Maya and everything. 

The f'ing crack for Maya even says in the nfo to generate the License file in Windows, which is this guy claims is what finally worked for him.

That program is more complicated to use than Gentoo for hells sake. 
And this guy's acking like "his company bought for him and they want results!" what a jee-oke!

And whats with all these Newbies who make threats about going back to Windblows95 thinking that it will cause some Linux Missionary or something to come make sure we don't lose a convert who's faith is waivering.

Go back to your first and true love for all we care!

Go do some |337 h4X0r'ing in your 7 beta "command prompts" and get the phuck from round our ttys!

Amen!
****

---

### Post by mickie.kext on 2009-06-10
Dude, what are smoking?..What is your problem? I really tried not to reply to your flaming, but have to.

First, I don't have any efficient (and safe) way of persuading you in legality of Maya copy I currently use, so I'm not gonna bother trying. Believe anything you want. 

That program (Maya) IS more complicated than Slackware and Gentoo, but I have been using it from version 7.0 (thruth to be told, those days I was using pirated version od Windowz)to 8.5, and eventualy switched to Blender, since I was considering going pro. And recently got back to Maya. But that is not important, this is what tickled me:

> And whats with all these Newbies who make threats about going back to Windblows95 thinking that it will cause some Linux Missionary or something to come make sure we don't lose a convert who's faith is waivering.

Go back to your first and true love for all we care!

Go do some |337 h4X0r'ing in your 7 beta "command prompts" and get the phuck from round our ttys
You have me confused with somebody. You talking about linux missionaries... I DON'T need any (missionary) to tell me that Windows SUCK!!! I saw that my self. I like using Linux, and Windows is never again gona be my full-time OS. I use it when I have to, trying to leave it forever. You probably decided to flame me because I don't post on this forum very often, so you think I gived up on linux. That is not true. I just switched to Debian. I dont like that Jaunty lacks Ctrl+Alt+Backspace shortcut for restarting X. My Radeon needs it.

This kind of flame war is not suited for forum like this. It is not for any forum. I think I will delete some of my earlier post on this thread, just not atract jerks like you!!

---

### Post by skullmunky on 2009-06-12
Huh?

Which of us is the vampire?  I'm confused.

So, I've been using Maya on linux since maya 4.  This thread was interesting to me because it presented some new challenges, and I learned some valuable new things.  Getting involved in troubleshooting something can be a bit of work, but often really pays off.  

chillax.

---

### Post by barx on 2009-06-22
The ati radeaon are a problem, yes, but there's solution.

First of all, I recomend you to use Ubuntu Intrepid Ibex (8.10)
And Ati driver 8.54 in Intrepid has a way to install it's propietary drivers by one clic at System &#8594; Hardware Drivers (well I don't now how it's named in english but icon has a green something, it's easy to see xD).

Actual Ati radeon drivers doesn't work with new ubuntu's xorg, so It's not necesary update actally, if you're in Juanty.

Second. You have follow the an old guide, converting rpms to debs . . .  that's old haha. Look at this link were Some guys and Me are doing some efforts to install Maya follow the link . .  . [LINK]("http://ubuntuforums.org/showthread.php?p=7499483#post7499483") . . 

You don't need convert to deb files, you can have it done also with rpms by terminal, and it has some troubles of libraries converting to deb 'cause they are different class of packages, of course.

So, doing natural way at Ubuntu's way, it's easy at this rate ;). Also I can do Software and Harware render, ha ha, no problems.

Don't believe me? I'm using a Toshiba Satellite A215-S7437 AMD Turion 64x2, and AMD procesors are a kind of extra steps in everything, but, the power is mention of envy haha, see ya noob.

P.S. I've installed Maya 2009 more than 10 times with the guide in the link I've said you to follow, TRY!!

---

### Post by tesuki on 2009-07-01
I dunno if this is out of place.
But to change interface names have a look at the file **/etc/udev/rules.d/70-persistent-net.rules**.
Just change the NAME="eth?" from the eth you use to eth0.
and restart udev by
```

sudo /etc/init.d/udev restart
```
And you network card will be switched. You also might need to change the file **/etc/network/interfaces** if you have configured a static IP.

---

### Post by babygenius55 on 2009-07-29
I PM'd Micket.kext already about this, but I didn't read far enough, he got his fixed...


I was having the exact same problem. File names were in all caps, etc.  In short, your file names are truncated.

This is an excerpt from a post I made to... [http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/](http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/)

 The problem was that I was mounting an ".iso" file and when I used the terminal to copy, the names were changed. I'm pretty suer they were truncated while they were mounted, but not certain. anyway I just double-clicked on the iso, and navigated my way to the LINUX64 folder, and I noticed it right away.(That the file names were being truncated) I guess using the archiver would be the way to go. I find it strange that noone ever mentioned this.  I really am sorry for all the caps.

---

### Post by jorx on 2009-10-10
Just thought I'd throw my two cents in here as well; 

in my experience getting the 64-bit linux version of Maya to run under kubuntu (or more specifically, linux mint running kde-desktop ) -

Alot of this has been said before but I just want to restate the importance:
Using the mac address of eth0 is *vital* as Maya licensing only looks at eth0.  
You can edit the file in 
**/etc/udev/rules.d/70-persistent-net.rules**.
to alter the name of your network advice. Just change from "eth3" or whatever it is to "eth0", restart, and problem fixed. "ifconfig" to double check.

Also, Maya runs *FAR* better under KDE then under gnome. I'm not sure why, it just does. It's quite buggy in Gnome but under KDE it runs mostly fine.  (only thing I haven't been able to fix is the spacebar tap to toggle full-windows) But the hotbox works fine.

Also, once you get it running, look into "KE_FileBrowser" or "k_mayabrowserHOWTO.pdf"  Do some googling- these set of scripts replace Maya's crap default file dialog with a nice KDE interface.  A must have.

---

