---
title: "GnuCash Data File Does Not Replicate"
date: 2010-01-25
forum: Ubuntu One (CLOSED)
---

### Post by AugieWest on 2010-01-25
I am trying to replicate my GnuCash files between two computers. My GnuCash folder has three types of files: 

* One Gzip archive file
* Many xac files (GnuCash Financial Data)
* Many log files

The xac and log files replicate with no problem. However the Gzip file does not. Without this Gzip file, GnuCash cannot makes sense of the other files.

Why would this Gzip file not sync? Have others used Ubuntu One to sync their GnuCash files?

Thanks!

---

### Post by AugieWest on 2010-01-25
Well, the that that file did replicate when I simply created a copy of it in the Ubuntu One/gnuCash folder. Both the original and copy appeared to make it over to my other computer. I wonder why it did not replicate before?

---

### Post by AugieWest on 2010-01-26
Wow! I have lost all faith in Ubuntu One! After using GnuCash, my local files shows I have modified 17 files. The Ubuntu One web interface shows I only modified one! In addition, the very important Gzip archive is not listed! It has disappeared into the cloud.

There is no way I can continue to use Ubuntu One. I found at least one other file modified locally that did not make it to the cloud.

---

### Post by duanedesign on 2010-01-27
well its unfortunate you are having an issue with Ubuntu One. It definitely should not be acting in the manner you describe. The Ubuntu One team is working hard to take care of these issues and everyday they are making great progress. Please hang in there i know your issue will be resolved as soon as possible. Canonical is taking steps to deal with the influx of users to the service so don't sudo apt-get remove quite yet.

You might take a look at [this wiki page]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/Diagnostics"). There is a python script you can run and some tips on what to look for in your $HOME/.cache/ubuntuone/log/syncdaemon-exceptions.log. If you need any help with this i will be more than happy to help.

*The most common bugs for sync problems (click bug number to go to report):*
**[455544]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/455544") **- Protocol version error - There are two ways to spot this error. First, the syncdaemon-exceptions.log will have ERROR - Protocol version error in it. Second, when the bug is reported via apport, the description will include the following:```
[bandwidth_throttling]
 on = True
 read_limit = -1
 write_limit = -1
```
The problem is that setting the bandwidth preferences to the defaults (clicking on the checkboxes and not changing the values) results in the read and write limits to be set to -1. The workaround is to delete the ~/.config/ubuntuone/syncdaemon.conf, restart the client, and don't set the bandwidth settings to the defaults. 

**[368626]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/368626")** - Invalid UTF-8 Characters - Look for UnicodeDecodeError: 'utf8' codec can't decode bytes in the syncdaemon-exceptions.log for bugs affected by this issue. 

**[490988]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/490988")** - A lot of MakeDir and MakeFile errors - Look for a number of repeated ERROR - MakeFile and ERROR - MakeDir  entries in the syncdaemon-exceptions.log file. These errors appear to be caused by a user switching Ubuntu One users on their computer without cleaning out their ~/Ubuntu One folder and meta data folder (~/.local/share/ubuntuone).

---

### Post by AugieWest on 2010-01-27
Thanks, duanedesign, but none of these bugs seem to apply to me. 

It seems like Ubuntu One does not like the ~/Ubuntu One to be a "working folder." By "working folder", I mean a folder with a lot of writing, overwriting and deleting of files and folders. 

I have pulled my gnuCash files out of the Ubuntu One folder and now tar and zip the files and drop them into the Ubuntu One. This seems to work better. Now, I need to write a perl script to make that happen automatically. I wish I just use ~/Ubuntu One as a working folder.

---

### Post by duanedesign on 2010-01-27
After digging through many bugs today i came across some that are similar to yours in that they were having trouble using the Ubuntu One folder as a working directory.
I tried to find it and post it here for you to reference but i couldnt lay my hands on it immediately. When i come across it and/or any additional info related to this i will post it here.

---

