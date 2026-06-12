---
title: "HPLIP is not installed properly"
date: 2015-03-15
forum: Ubuntu Development Version
---

### Post by denys-usynin on 2015-03-15
With the current version of vivid I cannot run HP printer setup utilility hp-setup. I get a message
[INDENT]error: HPLIP is not installed properly or is installed without graphical support. Please reinstall HPLIP[/INDENT]
[INDENT]warning: Qt/PyQt 4 initialization failed.[/INDENT]
[INDENT]error: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.[/INDENT]
[INDENT]error: No device found that support this feature.[/INDENT]

I already tried sudo apt-get install python-qt4 which I found on ubuntu wiki, but that didn't help. 
Looks like at the very least some dependencies are missing. Running hp-check returns the following:
-----------
| SUMMARY |
-----------


Missing Required Dependencies
-----------------------------
error: 'libcups2' package is missing/incompatible 
error: 'libdbus-1-dev' package is missing/incompatible 
error: 'libsnmp-dev' package is missing/incompatible 
error: 'snmp-mibs-downloader' package is missing/incompatible 
error: 'libusb-1.0.0-dev' package is missing/incompatible 
error: 'libcups2-dev' package is missing/incompatible 
error: 'cups-bsd' package is missing/incompatible 
error: 'cups-client' package is missing/incompatible 
error: 'python3-dev' package is missing/incompatible 
error: 'openssl' package is missing/incompatible 
error: 'libsane-dev' package is missing/incompatible 
error: 'libjpeg-dev' package is missing/incompatible 
error: 'libcupsimage2-dev' package is missing/incompatible 
error: 'python3-pyqt4' package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'libtool' package is missing/incompatible 


Missing Optional Dependencies
-----------------------------
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'xsane' package is missing/incompatible 
error: 'python3-notify2' package is missing/incompatible 
error: 'python3-dbus.mainloop.qt' package is missing/incompatible 


Total Errors: 16
Total Warnings: 2

---

### Post by dino99 on 2015-03-15
is your installation a genuine one ? or have you also added some extra repositories like ppa ?
Looks like there is some non trusted packages installed which conflict with the hplip expected version

---

### Post by denys-usynin on 2015-03-15
i am running current ubuntu 15 vivid, no extra repositories added apart from google chrome.
I ran hp-doctor utility and it installed some additional packages, after which I was able to run hp-setup.
However, hp-setup still failed to configure the printer, finishing with an error message:
    error:  The printer you are trying to setup requires a binary driver plug-in and it failed to install.  Please check your internet connection and try again.  Visit  [http://hplipopensource.com](http://hplipopensource.com)  for more infomation. 

That might be a problem of hplip itself.

---

### Post by dino99 on 2015-03-15
well, maybe your model is not yet supported ; what is that model ? (knowing it will let us browse the net for info)

---

### Post by denys-usynin on 2015-03-15
[HP LaserJet Pro MFP m127fw]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_pro_mfp_m127fw.html")
It is listed as fully supported at [http://hplipopensource.com/hplip-web/supported_devices/laserjet.html](http://hplipopensource.com/hplip-web/supported_devices/laserjet.html) 

But it seems the problem is that hplip is misconfigured in Ubuntu Vivid somehow, and not in a particular model of printer.

---

### Post by lishdigg on 2015-03-15
I did install the HP printer setup with the HP printer utilility on Ubuntu Gnome 15.04. I was having issues using the utility on my 15.04 Ubuntu Mate. I get to the building stage and the utility force closes. I have not been able to look into it, I am at work !

---

### Post by denys-usynin on 2015-03-15
poking around a bit more, it seems that hp-doctor wasn't able to fix all the dependency issues, as I am still getting 
[INDENT][FONT=courier new]error: libtool       libtool - Library building support services                  REQUIRED        -               -               MISSING    'libtool needs to be installed'[/FONT][/INDENT]

even though libtool was already installed - probably a version mismatch.
Another piece of potentially useful info - when I ran hp-plugin command to just download the plugin, it failed with the following messages in terminal:

[INDENT][FONT=courier new][COLOR=#000000]Checking for network connection...[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Downloading plug-in from: [/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Receiving digital keys: /usr/bin/gpg --homedir /home/boomka/.hplip/.gnupg --no-permission-warning --keyserver pgp.mit.edu --recv-keys 0xA59047B9[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Creating directory plugin_tmp[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Verifying archive integrity... All good.[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Uncompressing HPLIP 3.15.2 Plugin Self Extracting Archive...............................[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Error importing HPLIP modules.  Is HPLIP installed?[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]error: Python gobject/dbus may be not installed[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]error: Plug-in install failed.[/COLOR][/FONT][/INDENT]

---

### Post by mightyiam on 2015-03-23
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1422004](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1422004)

---

### Post by mbott on 2015-03-27
I'm glad my install was completed before I read this.  :)

I installed my HP ENVY 5530 via CUPS add a printer, then I installed the HPLIP Toolbox for the GUI and everything just works. 

-- 
Mike

---

### Post by dino99 on 2015-03-28
> **denys-usynin said:**
> poking around a bit more, it seems that hp-doctor wasn't able to fix all the dependency issues, as I am still getting 
[INDENT][FONT=courier new]error: libtool       libtool - Library building support services                  REQUIRED        -               -               MISSING    'libtool needs to be installed'[/FONT][/INDENT]

even though libtool was already installed - probably a version mismatch.
Another piece of potentially useful info - when I ran hp-plugin command to just download the plugin, it failed with the following messages in terminal:

[INDENT][FONT=courier new][COLOR=#000000]Checking for network connection...[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Downloading plug-in from: [/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Receiving digital keys: /usr/bin/gpg --homedir /home/boomka/.hplip/.gnupg --no-permission-warning --keyserver pgp.mit.edu --recv-keys 0xA59047B9[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Creating directory plugin_tmp[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Verifying archive integrity... All good.[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Uncompressing HPLIP 3.15.2 Plugin Self Extracting Archive...............................[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]Error importing HPLIP modules.  Is HPLIP installed?[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]error: Python gobject/dbus may be not installed[/COLOR][/FONT]
[FONT=courier new][COLOR=#000000]error: Plug-in install failed.[/COLOR][/FONT][/INDENT]

seems your vivid installation is borked: libtool is a gcc dependency, and gcc is always installed as it is mandatory

---

### Post by kc1di on 2015-03-28
Try adding hplip-gui from software center.  if that does not work. 
The go to a browser and enter the following address in the address line and try installing the printer via Cups.
```
localhost:631
```

---

### Post by Dave_Barker on 2015-03-31
I am also not managing to set my printer up on Ubuntu Vivid (beta 2). I need to use hplip for the model I have, it works fine on Trusty.

 - I'm not seeing any crashes.
 - I can add the printer from the Ubuntu GUI OK but when I try to print the job will stop with a message of "Filter failed".
 - I've tried adding the printer via CUPS. Again I'm able to add the printer but I'm unable to print anything at all. Print jobs end up with a "stopped "Filter failed" state.
 - `hp check -t` reports that the package "libtool" is missing/incompatible when it is installed.
 - I've tried running `hp-setup`, it fiinds my printer but then says I need to install the driver. When I click OK to that I eventually get a vague "Plug-in install failed" message and I can't progress.

I'm running on a Thinkpad T450 and my printer is a Hewlett-Packard-HP-LaserJet-Professional-P-1102w. I've installed a fresh copy of beta 2 of Vivid this morning, I only started messing around with the hplip stuff after I couldn't get the included stuff to work.

Cheers, Dave.

Edit: I've now got my printer working [by installing the foo2zjs driver]("http://foo2zjs.rkkda.com/") and using that instead of the hplip one.

Edit 2: I eventually found best solution for my situation was to [install Ubuntu 14.10, install a newer kernel and the drivers I needed for my laptop]("https://gist.github.com/kzar/5fc9e288f655285bac40"). That way all my hardware worked but I avoid bugs like this.

---

### Post by Chazall1 on 2015-03-31
I did a manual install and printers work. 
Here: [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

---

### Post by denys-usynin on 2015-04-02
> **9d9 said:**
> seems your vivid installation is borked: libtool is a gcc dependency, and gcc is always installed as it is mandatory

libtool is installed, it just doesn't match what HPLIP is expecting.

---

### Post by mrkeef on 2015-04-24
Try this page. It seems there is an error in hplip
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1430561](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1430561)

---

### Post by Ahunt on 2015-04-30
Working through the[ bug report]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1430561"), which is somewhat out of date I found the fix for this problem. 

Due to problems with the switch from Python 2 to 3, hplip was broken at the upgrade from 14.10 to 15.04. This problem affects all 'buntus, including Ubuntu, Lubuntu, Xubuntu, Kubuntu, etc. hplip is the system that allows most HP printers to work and without it there is "no printing".

Here is what I did to get my printer working:

1 Download hplip-3.15.4.run from [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)
2 Run the command in a terminal: sh hplip-3.15.4.run and follow through the dialogue.
* This returns: error: Printer queue setup failed. Error : successful-ok-ignored-or-substituted-attributes and then error: hp-setup failed. Please run hp-setup manually.
3 Set up the printer from the printer GUI.
4 Printing now works!

---

### Post by Cavsfan on 2015-04-30
> **Ahunt said:**
> Working through the[ bug report]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1430561"), which is somewhat out of date I found the fix for this problem. 

Due to problems with the switch from Python 2 to 3, hplip was broken at the upgrade from 14.10 to 15.04. This problem affects all 'buntus, including Ubuntu, Lubuntu, Xubuntu, Kubuntu, etc. hplip is the system that allows most HP printers to work and without it there is "no printing".

Here is what I did to get my printer working:

1 Download hplip-3.15.4.run from [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)
2 Run the command in a terminal: sh hplip-3.15.4.run and follow through the dialogue.
* This returns: error: Printer queue setup failed. Error : successful-ok-ignored-or-substituted-attributes and then error: hp-setup failed. Please run hp-setup manually.
3 Set up the printer from the printer GUI.
4 Printing now works!

I believe if you make hplip-3.15.4.run executable before you enter **sh hplip-3.15.4.run** perhaps you will not get that error.
**chmod +x ~/Downloads/hplip-3.15.4.run** or right click on it and got to properties and then permissions and check the execute box to allow executing file as program like I did.
I didn't get any errors and printed a test page successfully.

I installed hplip-3.15.4 on my Mint 17.1 and Trusty 14.04 installs with directions that said to do that first.

I also chose custom because I didn't want the fax utility files installed because I have an HP Photosmart C3180 printer/copier/scanner and it does not fax.

I had been following this thread as I was interested in installing the drivers after final release.

Now thanks mission accomplished!

---

