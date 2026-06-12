---
title: "Downloading Debs without apt-get or synaptic"
date: 2006-09-01
forum: Repositories &amp; Backports
---

### Post by brim4brim on 2006-09-01
Right so basically the question I'm asking is:

Am I the only user stuck on a 56K connection with a winmodem and os can't use synaptic or apt-get to update to download any .debs?

At the moment, the only way for me to get anything installed in Ubuntu is to download it from packages.ubuntu.com and I have to download each package individually through windows.

So what I'm wondering is:

Is there space for either adding a download all packages required for installing link for each app in packages.ubuntu.com or is there space for an application for downloading debs locally in windows so that you can then transfer them using a memory stick to the Ubuntu machine.

Obviously there maybe issues but is there anything to stop this from working that would be impossible to sort out?  I do think it should be possible to download an application from packages.ubuntu.com and double click to install it and have all the dependencies automatically install if required.

---

### Post by Omnios on 2006-09-01
To install a .deb file use:
```
sudo dpkg -i file_name
``` Sudo installs as root, dpkg is the teminal package command -i = install and lastly the filename or the file to be installed.

 Edit: My dad has a  superlink es 1838 2839
Which I think is a hardware modam and all we did with his is run
 > $ sudo wvdialconf /etc/wvdial.conf\
to get the modem port and config the networking dial up with that port and it worked with just doing that. Other modems might take more work though

---

### Post by brim4brim on 2006-09-01
> **Omnios said:**
> To install a .deb file use:
```
sudo dpkg -i file_name
``` Sudo installs as root, dpkg is the teminal package command -i = install and lastly the filename or the file to be installed.

 Edit: My dad has a  superlink es 1838 2839
Which I think is a hardware modam and all we did with his is run
 \
to get the modem port and config the networking dial up with that port and it worked with just doing that. Other modems might take more work though


Yeah the problem is my modem does not support Linux in pretty much anyway and likely never will so my only method is to download the debs via windows.

My modem is a Conexant D110 MDC V.92.  It's a laptop modem in a Dell Latitude D810 so if anyone knows how to get it working I'd be happy but I don't think it'll ever work.  I'm wondering about alternative methods for installing apps.

---

### Post by kspringer on 2006-09-01
Yeah, I can't connect with my modem either.  But rather than use a stick, I've created a vfat/fat32 partition that Windows and Kubuntu both recognize.  Then transfer the debs from Windows to Kubuntu using that drive.

Ran into a bunch of "dependency issues" though. Usually with upgrading libraries.

Don't know how to fix that yet but I'm learning...

---

### Post by brim4brim on 2006-09-01
> **kspringer said:**
> Yeah, I can't connect with my modem either.  But rather than use a stick, I've created a vfat/fat32 partition that Windows and Kubuntu both recognize.  Then transfer the debs from Windows to Kubuntu using that drive.

Ran into a bunch of "dependency issues" though. Usually with upgrading libraries.

Don't know how to fix that yet but I'm learning...

Yeah basically even if you could setup a similar setup to yours to store a library for dependencies for synaptic then have a windows synaptic like application that could get the packages for you, then boot backup to ubuntu and complete install from windows.

That way it could check your dependencies from the shared partition information and work out what was required.

Anything but this basically because the way I'm doing things now is very annoying.

Either that or get modem providers to support their damn modems in Linux :x

---

### Post by brim4brim on 2006-09-02
Right I got my modem working (sort of) from linuxant.com's free drivers which limit me to about 1.5KB per second unless I pay for the unlimited version ($20).

Could these be included in Ubuntu's repository so that users can use their modem out of the box and then buy the version they need if they want it?  This way you would at least have Internet access out of the box even if the driver's aren't GPL.

---

### Post by mvdw on 2006-09-14
If your main problem is working out which particular files to download, the solution is in synaptic. Open synaptic, select all the packages you'd like to install, as well as selecting the upgrades (by hitting the "Mark all upgrades" button). Now, instead of hitting "apply", go to file->generate script. Choose a suitable place, and voila, you have a download script.

Over in windows, you'll have to get a "wget" client; either install cygwin or do a google for wget - you should find a windows client in there somewhere. Edit the script you generated to remove the first line (just a #!/bin/sh header), rename the script to whatever.bat and run it. It'll get all the .debs for you, so make sure you run it from a place with lots of disk space.

Now you have all the debs you need, you can add the directory you downloaded them to into your repositories, or alternatively you can manually install them using dpkg.

---

### Post by Matchless on 2006-09-15
I was just wondering if this will work on a pc where synaptic has never seen the outside world? The sources.list will not have updated the Packages.gz and as such synaptic will not know of any updates or programs except those already presented to it on the install cd??
The only real easy solution to get Ubuntu up to date without any such direct connection is to borrow from or visit a friend and connect via lan to a PC that can see the internet. Otherwise is to copy the complete cache from another PC that is up to date and present it to your PC as a repository on a CD and use synaptic to install from that CD.
I personally hope that modem dialup is going to receive a much higher interest by the Ubuntu developers in Edgy as there are still a great many users out there that have only dialup as a means of connecting and can only dream of broadband in the distant future!

---

