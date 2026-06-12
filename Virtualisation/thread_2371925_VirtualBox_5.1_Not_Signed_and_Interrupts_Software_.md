---
title: "VirtualBox 5.1 Not Signed and Interrupts Software Updater"
date: 2017-09-19
forum: Virtualisation
---

### Post by jaydub868 on 2017-09-19
I installed VirtualBox 5.1 using as follows:
   ```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove
   wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
   sudo sh -c 'echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" >> /etc/apt/sources.list'
   sudo apt-get update
   sudo apt-get install virtualbox-5.1
``` 

When I run apt-get update, it returns this:
   ```
W: GPG error: [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) zesty InRelease: The following signatures couldn't be verified because the public key is not available: 
        NO_PUBKEY A2F683C52980AECF
   W: The repository 'http://download.virtualbox.org/virtualbox/debian zesty InRelease' is not signed.
   N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
   N: See apt-secure(8) manpage for repository creation and user configuration details.
```

This causes Software Updater to stall and return:
   Failed to download repository information
   Check your Internet connection
About 10 seconds later, Software Updater returns:
   Your software is up to date

So, I go into Software Updater and uncheck the VirtualBox respository, and I no longer get the failed to download message.  But that also means that I won't be getting updates for VirtualBox, I presume.  Is this normal behavior?  What does everyone else do?

---

### Post by mastablasta on 2017-09-20
there is a slight difference in your install procedure from what is described here: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)   under **Debian-based Linux distributions**.

read carefully and follow the steps. it should work with no issues.

---

### Post by slickymaster on 2017-09-20
*Thread moved to **Virtualisation**.*

---

### Post by rava2 on 2017-09-20
disable the repo in software and updater , you can install latest version on their site

---

### Post by jaydub868 on 2017-09-20
Ok, I see.  A few questions: 

OK, I completely uninstalled Virtual Box.

Added to /etc/apt/sources.list:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) zesty contrib  [without preceding # sign]

It should be noted that when I open pluma, I get the following message:
** (pluma:4030): WARNING **: Could not load Pluma repository: Typelib file for namespace 'Pluma', version '1.0' not found
I'm not sure what that means, but the sources list does open and allows me to add to the list.  I just downloaded UbuntuMate and I have version 1.18.


Then ran:
sudo apt-key add oracle_vbox_2016.asc
which returns:
gpg: can't open 'oracle_vbox_2016.asc': No such file or directory

Then ran:
sudo apt-key add oracle_vbox.asc
which returns:
OK

Then I run:
sudo apt-get update
which returns:
Get:1 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) zesty InRelease [7,774 B]
Ign:1 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) zesty InRelease         
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease                      
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease [89.2 kB]    
Hit:4 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) zesty InRelease       
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease [89.2 kB]     
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports InRelease [89.2 kB]  
Hit:7 [http://ppa.launchpad.net/flexiondotorg/youtube-dl-gui/ubuntu](http://ppa.launchpad.net/flexiondotorg/youtube-dl-gui/ubuntu) zesty InRelease
Hit:8 [http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu](http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu) zesty InRelease     
Hit:9 [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) zesty InRelease 
Fetched 275 kB in 1s (218 kB/s)                    
Reading package lists... Done
W: GPG error: [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) zesty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF
W: The repository 'http://download.virtualbox.org/virtualbox/debian zesty InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

And so I have the same issue.  

I'm not sure what I'm doing wrong.

---

### Post by mastablasta on 2017-09-21
you need to add [COLOR=#000000]add oracle_vbox_2016.asc

[/COLOR]> The Oracle public key for apt-secure can be downloadedhere for Debian 8 ("Jessie") / Ubuntu 16.04 ("Xenial") and later[COLOR=#000000]
link: [/COLOR]https://www.virtualbox.org/download/oracle_vbox_2016.asc


[COLOR=#000000]file is obviously there and available: [/COLOR]http://download.virtualbox.org/virtualbox/debian

you need to download the key and add it:

```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
```

---

### Post by jaydub868 on 2017-09-21
OK, I get it.  That works.
But when I go through the routine, it apparently automatically installs the 32-bit version of VB, as I can't add any 64-bit VM's.  How do I change that?

---

### Post by SeijiSensei on 2017-09-21
> **jaydub868 said:**
> OK, I get it.  That works.
But when I go through the routine, it apparently automatically installs the 32-bit version of VB, as I can't add any 64-bit VM's.  How do I change that?
You need to enable VT-x or the equivalent in the BIOS to have 64-bit hosts and guests.

---

### Post by deadflowr on 2017-09-21
VT-x will actually allow you to run 64-bit guests on a 32-bit host machine.
But you should look at why it's installing the 32-bit version in the first place.

---

### Post by jaydub868 on 2017-09-21
OK all issues resolved.  It appears that when you install Linux VB inside a pre-existing Linux VM running hosted on Windows, it installs the 32-bit version of the program.

Many thanks to MastaBlasta.

---

### Post by efflandt on 2017-09-23
You originally failed to mention that you were trying to install virtualbox on a virtual guest.

---

### Post by jaydub868 on 2017-09-24
It wasn't my original intent to install the VB on a virtual guest.  That happened by mistake after several tries at installing...my error.

---

