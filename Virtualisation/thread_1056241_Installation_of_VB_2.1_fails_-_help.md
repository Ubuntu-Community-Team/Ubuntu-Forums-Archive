---
title: "Installation of VB 2.1 fails - help"
date: 2009-01-31
forum: Virtualisation
---

### Post by WildeBeest on 2009-01-31
Ubuntu 8.04 64 bit.

I attempted to install Virtualbox 2.1 from the repositories.

I had virtualbox-ose installed.

I get the following error:

```
sudo apt-get install virtualbox-2.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxalan110 libxerces27
Use 'apt-get autoremove' to remove them.
Recommended packages:
  libsdl-ttf2.0-0
The following NEW packages will be installed:
  virtualbox-2.1
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/37.1MB of archives.
After this operation, 84.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  virtualbox-2.1
Install these packages without verification [y/N]? y
Preconfiguring packages ...
(Reading database ... 242488 files and directories currently installed.)
Unpacking virtualbox-2.1 (from .../virtualbox-2.1_2.1.2-41885%5fUbuntu%5fhardy_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/virtualbox-2.1_2.1.2-41885%5fUbuntu%5fhardy_amd64.deb (--unpack):
 trying to overwrite `/lib/modules/2.6.24-23-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-23-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-2.1_2.1.2-41885%5fUbuntu%5fhardy_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by HotShotDJ on 2009-01-31
You must FIRST completely remove all virtualbox-OSE packages (which is hinted at in the error message -- but certainly not crystal clear).  Even if you've removed virtualbox-OSE, you may very well have left the modules in place.  Try using System --> Administration --> Synaptic Package Manager and search for virtualbox.  Make sure to uninstall using the "Completely Remove" option.  This should get rid of the old module that seems to be blocking the installation of Virtualbox-2.1.  While you can upgrade directly from within either the OSE line or the PUEL ("official Sun packages") line, you cannot upgrade directly between them -- although the VM's that you set up in one will work fine within the other (sometimes with some minor settings changes).

Also, you should add the authentication key -- this will insure that you don't get corrupted files and get rid of the "WARNING: The following packages cannot be authenticated!" problem.  Run the following code in a terminal to do this:```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

---

### Post by WildeBeest on 2009-01-31
Thanks, I thought I had removed all the OSE packages. Noticed a few more when I ran Synaptic Package Manager.

Installed like a champ.

---

### Post by WildeBeest on 2009-01-31
I saw that you answered a post about Windows 7. That's exactly what I'm trying to do.

Do I have to use the 64 bit version of W7 if I'm running 64 bit Hardy?

I downloaded the 32 bit iso and it doesn't run.

I get the following error message:

I don't know how to display a screen shot, ie the attached file from gimp.

---

### Post by HotShotDJ on 2009-01-31
> **WildeBeest said:**
> Do I have to use the 64 bit version of W7 if I'm running 64 bit Hardy?

I downloaded the 32 bit iso and it doesn't run.I did some quick research (very quick, actually) and found that you should be able to run 32 bit version of Windows as a guest on your 64 bit host.  So that is probably not the issue.  Did you try the steps suggested in the error message?

I've seen many reports of downloads from the MS servers being corrupt.  This could be the problem for you as well.  You may need several attempts before getting a good download.

---

### Post by Dyffo on 2009-02-01
Hi - I have Virtual Box  2.0.6 installed and would like to upgrade to 2.1.2 , my question is do I have to completely remove my original version - thereby losing all settings, configs files etc to upgrade. if yes I shan't bother unless you can tell me that 2.0.6 is  a greatly improved version.What I would really like  is to be able to  RECORD  cd/dvd on V.Box, which is not possible at the moment

---

### Post by WildeBeest on 2009-02-01
Thanks again. It was a bad download.

---

### Post by HotShotDJ on 2009-02-01
> **Dyffo said:**
> Hi - I have Virtual Box  2.0.6 installed and would like to upgrade to 2.1.2 , my question is do I have to completely remove my original version - thereby losing all settings, configs files etc to upgrade.First of all, your settings, configuration files, etc, are stored in your home directory (~/.VirtualBox) and are not touched by the upgrade process or even by completely removing VirtualBox.  So you don't have to worry about that.  However, your configuration files will be reorganized and changed to make them compatible with 2.1.* when you first run the upgraded version.  You will be given the choice of backing up the original files.  If you choose not to back them up, you will not be able to roll back to previous versions of VirtualBox.  Since I have regular backups of my home directory anyway, I chose not to have VB make the backups.  Everything went well.

The more important question is this -- Do you have the OSE version of 2.0.6 installed currently or the official Sun PUEL version?  IF you have the OSE version, you must completely remove that version first before installing the PUEL version from Sun (See my HowTo: [http://ubuntuforums.org/showpost.php?p=6398716&postcount=1](http://ubuntuforums.org/showpost.php?p=6398716&postcount=1) )  If you have the PUEL version of 2.0.6, then you can upgrade directly.

In either case, your settings and configuration will be preserved.

EDIT:  Yes, 2.1.2 represents a significant improvement, and with proper configuration of your CDRW/DVDRW drive in VB, you will be able to burn DVD's and CD's from the guest OS.  (Although, I can't imagine why you would want to do that... native Linux CD/DVD burning software is at least as good as (and sometimes better than) the tools available in Windows.

---

