---
title: "browser-plugin-freshplayer-pepperflash || Chromium doesnt detect"
date: 2017-03-29
forum: Ubuntu Development Version
---

### Post by linuxyogi on 2017-03-29
I followed instructions from [this page]("http://askubuntu.com/questions/748629/how-to-install-pepper-flash") and installed browser-plugin-freshplayer-pepperflash but Chromium wont detect it. 

In Chromium's Extentions page I see

> [COLOR=#303942][FONT=Ubuntu]**Oh dear… You have no extensions :-(**[/FONT][/COLOR][COLOR=#303942][FONT=Ubuntu]Want to [browse the Chrome Web Store]("https://chrome.google.com/webstore/category/extensions?hl=en-GB") instead?[/FONT][/COLOR]

How do I make Chromium to detect the flash plugin ?

Using 17.04.

I also purged the adobe-flashplugin but same thing.

```
$ sudo apt-get purge adobe-flashplugin   
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools cgmanager libpam-cgfs libubuntuoneauth-2.0-0
  signon-plugin-password ubuntuone-client-data ubuntuone-credentials-common
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flash-properties-gtk* adobe-flashplugin*
0 upgraded, 0 newly installed, 2 to remove and 61 not upgraded.
After this operation, 37.9 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 208232 files and directories currently installed.)
Removing adobe-flash-properties-gtk (1:20170214.1-0ubuntu1) ...
Removing adobe-flashplugin (1:20170214.1-0ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Processing triggers for bamfdaemon (0.5.3+16.10.20160929-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
(Reading database ... 208203 files and directories currently installed.)
Removing adobe-flashplugin (1:20170214.1-0ubuntu1) ...
Purging configuration files for adobe-flashplugin (1:20170214.1-0ubuntu1) ...
```

---

### Post by zika on 2017-03-30
1. Use PepperFlash by copying files to desired proper location (pick one from many or communicate one used via command line switch)
2. use command line switch to communicate PF version to Ch. if needed (for latest nightly's it is)

---

### Post by linuxyogi on 2017-03-30
> **zika said:**
> 1. Use PepperFlash by copying files to desired proper location (pick one from many or communicate one used via command line switch)


What location is that ? 

> **zika said:**
> 
2. use command line switch to communicate PF version to Ch. if needed (for latest nightly's it is)

I am using 
```
 Version 56.0.2924.76 Built on Ubuntu , running on Ubuntu 17.04 (64-bit)

```


How do I do that ?[COLOR=#303942][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by dino99 on 2017-03-30
i does not get such issue on ZZ 64 bits with chromium. I suggest you open 'synaptic' to purge the installed one, then reinstall it (take time to clean the system first if its not a fresh install)

---

### Post by linuxyogi on 2017-03-30
On Chromium's Extentions page I see

```
Oh dear… You have no extensions :sad:Want to [browse the Chrome Web Store]("https://chrome.google.com/webstore/category/extensions?hl=en-GB") instead?                      

```

But on the > chrome://version/

I see 

[TABLE="width: 0"]
[TR]
[TD="class: label"][ATTACH=CONFIG]274359[/ATTACH]






[/TD]
[TD="class: version"][/TD]
[/TR]
[/TABLE]

That means its detected ? Sorry for the confusion.

---

### Post by deadflowr on 2017-03-30
Flash is not an extension, but a plugin.
It's never been nor ever will be listed in the Extensions page.
I think you can still see the plugins page at chrome://plugins for ver 56
(they dropped it on ver 57, now you open the settings page go to content settings to control flash.)

More on that here
[https://ubuntuforums.org/showthread.php?t=2355276]("https://ubuntuforums.org/showthread.php?t=2355276")

---

