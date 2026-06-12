---
title: "Can I get to the Text Mode Partition Editor from the Installer?"
date: 2010-01-19
forum: Server Platforms
---

### Post by MaximumFish on 2010-01-19
Hi,

We're planning on running some performance tests on various LVM and straight disk configurations before we settle on one to use for our live servers, but while I can setup LVM volumes and partitions till the cows come home using the text mode GUI that's part of the Server Edition installer, I tend to get very confused trying to do the same from the command line.

So, is there any way to get to that text mode GUI from the installer *after* the system has been installed? I know there are various tools to do the job within Gnome etc, but we're trying to keep the system as unbloated as possible.

Much thanks,

Max

---

### Post by Wej on 2010-07-26
Has anyone found an answer to this question yet? I am in the same boat. I have 14 new hard drives plugged in to a system that I need to create one big LVM, but I have no idea how to do it manually or to even see if all my drives are showing up properly.

---

### Post by ruffEdgz on 2010-07-26
To answer you question about on this post, I haven't seen anything that is great but you can try out the package 'partitionmanager' which just helps with partitions but could be a good solution to your tests.

If you are interested in more LVM management, I know that Fedora/Redhat have a LVM System Management GUI - [http://rpm.pbone.net/index.php3/stat/4/idpl/13916339/dir/fedora_13/com/system-config-lvm-1.1.13-1.fc13.noarch.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/13916339/dir/fedora_13/com/system-config-lvm-1.1.13-1.fc13.noarch.rpm.html)

Because its an RPM and not a DEB file, you will have to install and learn the command 'alien'. I found this old post from 2006 that talked about how to install an older version of this application on Ubuntu: [http://ubuntuforums.org/showthread.php?t=216117](http://ubuntuforums.org/showthread.php?t=216117) (please read it and use it as a reference)

I'm really comfortable with LVM management and if you want some extra help on the matter, I can do my best to guide you to a good solution for your tests.

Hope this helps.

---

### Post by FuturePilot on 2010-07-26
> **ruffEdgz said:**
> To answer you question about on this post, I haven't seen anything that is great but you can try out the package 'partitionmanager' which just helps with partitions but could be a good solution to your tests.

If you are interested in more LVM management, I know that Fedora/Redhat have a LVM System Management GUI - [http://rpm.pbone.net/index.php3/stat/4/idpl/13916339/dir/fedora_13/com/system-config-lvm-1.1.13-1.fc13.noarch.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/13916339/dir/fedora_13/com/system-config-lvm-1.1.13-1.fc13.noarch.rpm.html)

Because its an RPM and not a DEB file, you will have to install and learn the command 'alien'. I found this old post from 2006 that talked about how to install an older version of this application on Ubuntu: [http://ubuntuforums.org/showthread.php?t=216117](http://ubuntuforums.org/showthread.php?t=216117) (please read it and use it as a reference)

I'm really comfortable with LVM management and if you want some extra help on the matter, I can do my best to guide you to a good solution for your tests.

Hope this helps.

No need to do that. system-config-lvm is in the Ubuntu repos.

---

### Post by ruffEdgz on 2010-07-26
> **FuturePilot said:**
> No need to do that. system-config-lvm is in the Ubuntu repos.

Wow, I totally missed that one :P Glad you caught that one for me ;)

Then the possible resolutions to this could be (depending on the request from this post):
[LIST=1]
[*]Partition Manager
[*]system-config-lvm
[*]pv, vg, and lv commands
[*]fdisk, sfdisk commands
[/LIST]
Hope this helps and thanks [FuturePilot]("http://ubuntuforums.org/member.php?u=178962") for correcting me ;)

---

