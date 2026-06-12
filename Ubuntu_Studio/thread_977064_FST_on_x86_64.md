---
title: "FST on x86_64"
date: 2008-11-09
forum: Ubuntu Studio
---

### Post by duffrecords on 2008-11-09
I have actually managed to compile 32-bit FST on 64-bit Ubuntu Studio without any errors.  

Read that sentence again in case you thought your eyes were playing tricks on you.  Now for the fine print:  I can't get Wine to run the EXE yet.  Anyway, here's what I did, in case someone wants to grab the torch and keep running.

When compiling FST on 64-bit Ubuntu Studio, you will get errors such as "skipping incompatible /usr/lib64/libgtk-x11-2.0.so."  This is because you need the ia32-libs package.  However, when these 32-bit libraries are installed in /usr/lib32 there are no links created that end in ".so" like in the error above.  You need to go through the whole /usr/lib32 directory and make symbolic links to dozens of shared libraries.  Fortunately you can use my bash script to do all the work.```
#!/bin/bash

LIST=`ls /lib32/*.so.* /usr/lib32/*.so.*`	#list all the system's 32-bit libraries
for i in $LIST;
do
  if [ -L "$i" ]	#if library is a link
  then
    newlink=${i/%.so.*/.so};	#generate simple link name
    if [ ! -e "$newlink" ]	#if link doesn't already exist
    then
      ln -s $i $newlink;	#create symbolic link
    fi
  fi
done
```Since it's modifying /usr/lib32, you'll need to run the script as root.  Of course, you should **always** read a script thoroughly so you understand what it does before executing it as root.  Now that you know where the 32-bit libraries are, you might want to ensure that the Makefile looks for that directory.  Add this line to the "Common settings" section in FST's Makefile:```
LDFLAGS               = -L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32
```We're almost there.  FST depends on liblash, and LASH depends on libuuid.  Those libraries weren't included in ia32-libs.  Go to launchpad.net and get the i386 .deb packages for liblash and libuuid (make sure you select the version of Ubuntu that you currently use).  Save these packages and open them with an archive manager.  Within the packages you'll find two archives--control and data.  Open the data archive and extract all the /usr/lib files into the /usr/lib32 directory on your hard drive.

Follow the instructions on the [FST website]("http://www.joebutton.co.uk/fst/") and compile FST.  It will give you some warnings like "incompatible implicit declaration of built-in function" but it will compile successfully at this point.  Try to run FST:> ./fst /path/to/vst/plugin.dll
Wine will produce a "Bad EXE format" error.  This is where I'm stuck.  Any ideas?

---

### Post by polzleitner on 2009-01-18
Hi,

Many thanks for this contribution. I have been able to compile fst-1.9 with your hints. However, I'm also stuck at the wrong ELF format problem. Have you been able to resolve this?

---

### Post by duffrecords on 2009-01-30
No, but the developer of FST is working on an updated version.  As far as I know, there's no release yet.  For now, however, I've found that [dssi-vst]("http://dssi.sourceforge.net/") works quite reliably, and I'm pretty sure I remember reading in the README that it can run 32-bit VST plugins on x86_64 architecture.  Haven't tried it yet, though.

---

### Post by crazydudearam on 2011-02-26
Hi I was just wondering if there were any updates on this 64-bit system fst compatibility. I got as far as I believe you have. this was my output at link-time:

/usr/bin/ld: Relocatable linking with relocations from format elf32-i386 (audiomaster.o) to format elf64-x86-64 (fst.CCunij.o) is not supported
winebuild: /usr/bin/ld failed with status 1
winegcc: winebuild failed
make: *** [fst.exe] Error 2

So I couldn't even make a binary fst. I was wondering if anyone could help me in doing so; either that or getting dssi-vst to load something. because I've successfully built dssi-vst but when attempting to load dll's with either dssi-vst-host (vsthost command) or jack-dssi-host, I get the following error:

Testing VST compatibility... 
dssi-vst-server[1]: VST 2.4 entrypoint "VSTPluginMain" not found in DLL "FL Keys.dll", looking for "main"
dssi-vst-server: ERROR: VST entrypoints "VSTPluginMain" or "main" not found in DLL "FL Keys.dll"
Plugin server timed out on startup: No such device or address
vsthost: bailing out

Any help would be greatly appreciated. My ultimate goal is getting windows VST plugins to work in an svn version of Ardour3, which I know is pretty difficult and in many places has been suggested not to be done. But, again, any help would be greatly appreciated. :)

---

### Post by sgx on 2011-02-27
Hi, Reaper is going to be your best option, and you'll notice FL Studio is also being used, with a long thread covering the process.
Few vsts have preset controls in their gui, so a host is needed to
control patch changes. There is a long thread at the Reaper forum covering it's use in linux, and you'll need to google for terms you'll
want to be familiar with:

wineasio
regsvr32
winecfg

There are 'deb packages for fst, and festige, its replacement.
These can start some vsts, but you'll need ones with built-in patch loading, and connections made using qjackctl, or patchage. Not all vsts will work. Reaper has a high success ratio.

Qtracktor is another option, which I have not used, but it on the
to - do list for 2011.

Yoshimi (zynaddsubfx variant) and phasex are two fine linux synthesizers, there are hundreds of presets for yoshimi, thanks to several people who shared large collections they have made.
Phasex has great sound, and lots of easy to use controls, and a
nice soundset of 50 or 60 presets.

Rakarrack is a great multifx app to take your sounds to new places.

Cheers

---

