---
title: "Copying info = securtiy breach?"
date: 2008-09-10
forum: Security
---

### Post by Camilia on 2008-09-10
In windows I got trojans from copying pictures for avatars. I had additional firewall and virus scan.  Spyware scanner prevented problems.  Can this happen in ubuntu?  Is there a scan to check if this occurs?

---

### Post by cdenley on 2008-09-10
An image parsing bug that allows attackers to create an image that executes arbitrary code when viewed is not necessarily impossible, but malware which targets linux computers are rare, especially ones that are embedded in images since linux malware is probably usually targeted at servers. To check for malware on your computer, you can use something like chkrootkit.

An example of one recently discovered image parsing bug
[http://www.ubuntu.com/usn/usn-639-1](http://www.ubuntu.com/usn/usn-639-1)

If you want to make web browsing more secure, the best thing you can do is use noscript.
```

sudo apt-get install mozilla-noscript

```

---

### Post by Camilia on 2008-09-10
I have Ubuntu 8.04 LTS. It suggest upgrading. How do I do that?
I read that rkhunter only need if using a server and I don't have 1. Is this true?

---

### Post by Nepherte on 2008-09-11
You can update your computer with:
```
sudo apt-get update && sudo apt-get upgrade
```
Be sure that you enabled the necessary repositories. You can safely enable security, hardy-updates, universe and multiverse. I've never had problems with backports, but in some cases it might cause some problems. And last but not least, do not enable the proposed repository!

Sometimes you will see an output saying "some updates are held back". You can install those as well with:
```
sudo apt-get dist-upgrade
```

You can install rkhunter on a desktop as well if you like.

---

### Post by Camilia on 2008-09-11
Went into synapse clicked upgrades. Then pasted sudo apt-get update
After download of other material, such as Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages  got this:
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems.

Uncertain if this important?

rkhunter confuses me for I get warnigs on the hidden files.  Read this is only necessary if you have a server connected to pc.  I am just connected to cable,  so is it of any use for me?   I downloaded rkhunter.  How do I get it on my desktop?  I don't see in applications, places or system.

---

### Post by Dave_Connor on 2008-09-11
With the default Rkhunter config you need to gedit or nano the rkhunter config file to whitelist those directorys so they aren't flagged like they are.

---

### Post by Camilia on 2008-09-12
> **Dave_Connor said:**
> With the default Rkhunter config you need to gedit or nano the rkhunter config file to whitelist those directorys so they aren't flagged like they are.

What do you mean by gedit or nano the rkhunter config file?
Okay so the computer is confused, white list the directories. How?
How about how to put rkhunter on desktop?

---

### Post by cariboo on 2008-09-12
The error message about the medibuntu repositories you can ignore as they seem to be up and down with no notice.

Rkhunter does not have an icon and runs in the background. There are two ways to access the log files, Open a Applications-->Accessories-->Terminal and type:

```
mail
```

to read the mail press **t**, to delete mail press **d** to quit the mail program press **q**. If that doesn't work go to Places-->Home Folder-->Filesystem-->var-->log and look for rkhunter.log. You can right click on the file and click Open with Text Editor.

Jim

---

### Post by EnGorDiaz on 2008-09-13
ok who the hell would make viruses for linux

microsoft developers?

---

### Post by Camilia on 2008-09-22
Thank you everyone for your suggestions.  I have been using the script blocker.  Been preoccupied with health problems.  Now unable to get in to comcast account so removing it to see if I can get into it.  Script so who else wants to view where I am going.

---

### Post by Dave_Connor on 2008-09-23
gedit is the graphical text editor and nano is a text only cl editor. The rkhunter config is located at /etc/rkhunter.conf.

---

### Post by Camilia on 2008-09-26
> **cariboo907 said:**
> The error message about the medibuntu repositories you can ignore as they seem to be up and down with no notice.

Rkhunter does not have an icon and runs in the background. There are two ways to access the log files, Open a Applications-->Accessories-->Terminal and type:

```
mail
```

to read the mail press **t**, to delete mail press **d** to quit the mail program press **q**. If that doesn't work go to Places-->Home Folder-->Filesystem-->var-->log and look for rkhunter.log. You can right click on the file and click Open with Text Editor.

Jim

mail didn't work. Got to filesystem > var> rkhunter. and got I don't have permission to look in.

---

### Post by cariboo on 2008-09-26
Try in a terminal: 

```
sudo cat /var/log/rkhunter.log | less
```

enter your password, this should display the log file use the space to scroll down.

Jim

---

### Post by Camilia on 2008-09-28
This is the result.  These items that concern me.  Should I be concerned?
 Performing 'shared libraries' checks
[01:03:41] Info: Starting test name 'shared_libs'
[01:03:41] Checking for preloading variables                 [ None found ]
[01:03:41] Checking for preload file                         [ Not found ]
[01:03:41] Info: Starting test name 'shared_libs_path'
[01:03:41] Checking LD_LIBRARY_PATH variable                 [ Not found

/usr/bin/ldd                                      [ Warning

Warning: The file properties have changed:
[01:03:45]          File: /usr/bin/ldd
[01:03:45]          Current inode: 1140389    Stored inode: 1139272
[01:03:45]          Current file modification time: 1221229932
[01:03:45]          Stored file modification time : 1207352282

Warning: Suspicious files found in /dev:
[01:04:20]          /dev/shm/pulse-shm-807103893: data
[01:04:21]   Checking for hidden files and directories       [ Warning ]
[01:04:21] Warning: Hidden directory found: /dev/.static
[01:04:21] Warning: Hidden directory found: /dev/.udev
[01:04:21] Warning: Hidden directory found: /dev/.initramfs

---

### Post by Camilia on 2008-09-28
> **EnGorDiaz said:**
> ok who the hell would make viruses for linux

microsoft developers?

To me that is the like asking who writes trojan viruses, which rkhunter does check for.

---

