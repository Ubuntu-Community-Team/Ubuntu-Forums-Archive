---
title: "Today's update remove gedit (saucy-proposed enabled)."
date: 2013-05-23
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2013-05-23
sudo apt-get -V dist-upgrade

```
Calculating upgrade... Done
The following packages will be REMOVED:
   **gedit (3.6.2-0ubuntu1)**
   libgtksourceview-3.0-0 (3.6.3-0ubuntu1)
The following NEW packages will be installed:
   libgtksourceview-3.0-1 (3.8.0-1)
The following packages have been kept back:
   usb-modeswitch-data (20120815-2 => 20121109-3)
The following packages will be upgraded:
   e2fslibs (1.42.5-1ubuntu4 => 1.42.5-1.1ubuntu1)
   e2fsprogs (1.42.5-1ubuntu4 => 1.42.5-1.1ubuntu1)
   gir1.2-gtksource-3.0 (3.6.3-0ubuntu1 => 3.8.0-1)
   grep (2.14-1 => 2.14-2)
   libcomerr2 (1.42.5-1ubuntu4 => 1.42.5-1.1ubuntu1)
   libgd3 (2.1.0~alpha1-5 => 2.1.0~alpha1-6)
   libgtksourceview-3.0-common (3.6.3-0ubuntu1 => 3.8.0-1)
   libsemanage-common (2.1.6-6ubuntu1 => 2.1.10-2)
   libsemanage1 (2.1.6-6ubuntu1 => 2.1.10-2)
   libss2 (1.42.5-1ubuntu4 => 1.42.5-1.1ubuntu1)
   unity-webapps-facebookmessenger (2.4.16daily13.05.22-0ubuntu1 => 2.4.16daily13.05.23-0ubuntu1)
   unity-webapps-gmail (2.4.16daily13.05.22-0ubuntu1 => 2.4.16daily13.05.23-0ubuntu1)
   unity-webapps-googleplus (2.4.16daily13.05.22-0ubuntu1 => 2.4.16daily13.05.23-0ubuntu1)
   unity-webapps-launchpad (2.4.16daily13.05.22-0ubuntu1 => 2.4.16daily13.05.23-0ubuntu1)
   unity-webapps-reddit (2.4.16daily13.05.22-0ubuntu1 => 2.4.16daily13.05.23-0ubuntu1)
   unity-webapps-tumblr (2.4.16daily13.05.22-0ubuntu1 => 2.4.16daily13.05.23-0ubuntu1)
   unity-webapps-youtube (2.4.16daily13.05.22-0ubuntu1 => 2.4.16daily13.05.23-0ubuntu1)
17 upgraded, 1 newly installed, 2 to remove and 1 not upgraded.
Need to get 2,248 kB of archives.
After this operation, 2,552 kB disk space will be freed.
Do you want to continue [Y/n]? Y
```

sudo apt-get install gedit

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gedit : Depends: libgtksourceview-3.0-0 (>= 3.0.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

apt-cache policy libgtk-3.0

```
libgtk-3-0:
  Installed: 3.8.2-0ubuntu1
  Candidate: 3.8.2-0ubuntu1
  Version table:
 *** 3.8.2-0ubuntu1 0
        500 http://my.archive.ubuntu.com/ubuntu/ saucy-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     3.6.4-0ubuntu8 0
        500 http://my.archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
```

---

### Post by Harry33 on 2013-05-23
> **serdotlinecho said:**
> sudo apt-get -V dist-upgrade
...


Yes this happens because of the gtksourceview3 (3.8.0-1).
It has a new so-name.

We have to loosen the dependencies of the gtksourceview (like it is done in the Gnome3 Staging PPA) or better, have a new gedit built against new gtksourceview3.

---

### Post by Harry33 on 2013-05-24
This issue is fixed now with a new gedit build (3.8.2-0ubuntu1) in Saucy proposed repos.

---

### Post by cariboo on 2013-05-24
If you aren't willing to put up with breakage, I'd suggest you disable the proposed archives, as the developers have warned us all that proposed will break your distribution more often then not. the proposed repositories don't work the same way during the development cycle as they do for a released version. They are used as a holding area for new packages that are waiting for dependencies to be built before being moved into the regular repositories.

---

### Post by Cavsfan on 2013-05-24
> **cariboo907 said:**
> If you aren't willing to put up with breakage, I'd suggest you disable the proposed archives, as the developers have warned us all that proposed will break your distribution more often then not. the proposed repositories don't work the same way during the development cycle as they do for a released version. They are used as a holding area for new packages that are waiting for dependencies to be built before being moved into the regular repositories.

This did not happen to me but, cariboo907 while asking what appears to be a dumb question :D which are "the proposed archives"?

I see a key Ubuntu Archive, but that is all I see mentioning archive in my software sources.

---

### Post by cariboo on 2013-05-24
@Cavsfan, see the screenshot of Software & Updates, on how to enable/disable the proposed repositories.

---

### Post by deadflowr on 2013-05-24
@cavsfan, you can also comment the proposed-updates lines in the sources.list, if you want.

But +1 to disabling proposed in development, it's not used like normal proposed in the stable releases.
They don't do solid testing like stable proposed, it's more like a staging area now.

---

### Post by Cavsfan on 2013-05-24
> **cariboo907 said:**
> @Cavsfan, see the screenshot of Software & Updates, on how to enable/disable the proposed repositories.

Glad I asked because I had Pre-released updates checked! Not sure If I checked it myself or what.

I got confused when you said 
> I'd suggest you disable the _proposed archives_

But, then again I am easily confused. :biggrin: 

> **deadflowr said:**
> @cavsfan, you can also comment the proposed-updates lines in the sources.list, if you want.

But +1 to disabling proposed in development, it's not used like normal proposed in the stable releases.
They don't do solid testing like stable proposed, it's more like a staging area now.

Thanks deadflowr but, as you said unchecking the box was the easiest thing possible. :D

Think I am good to go now. Good thing I spotted this.
Thanks!

---

### Post by grahammechanical on 2013-05-24
The proposed repositories make the difference between the Edge and the Bleeding Edge in running Ubuntu development. The blood on the bleeding Edge has to come from someone.

---

### Post by deadflowr on 2013-05-24
> **grahammechanical said:**
> The proposed repositories make the difference between the Edge and the Bleeding Edge in running Ubuntu development. The blood on the bleeding Edge has to come from someone.

There is still a good amount of blood on the edge, without proposed.

---

### Post by Cavsfan on 2013-05-24
Yes, I am happy with the edge versus the bleeding edge. :lol:

---

### Post by serdotlinecho on 2013-05-25
> **grahammechanical said:**
> The proposed repositories make the difference between the Edge and the Bleeding Edge in running Ubuntu development. The blood on the bleeding Edge has to come from someone.

^^^ This...and I have btrfs snapshot  :D

> This issue is fixed now with a new gedit build (3.8.2-0ubuntu1) in Saucy proposed repos.

Thank you @Harry33

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  gedit-plugins
The following NEW packages will be installed:
  gedit
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 495 kB of archives.
After this operation, 2,625 kB of additional disk space will be used.
Get:1 http://my.archive.ubuntu.com/ubuntu/ saucy-proposed/main gedit i386 3.8.2-0ubuntu1 [495 kB]
Fetched 495 kB in 10s (49.1 kB/s)
Supported
Create a snapshot of '/tmp/apt-btrfs-snapshot-mp-va88l4/@' in '/tmp/apt-btrfs-snapshot-mp-va88l4/@apt-snapshot-2013-05-25_12:49:16'
Selecting previously unselected package gedit.
(Reading database ... 174485 files and directories currently installed.)
Unpacking gedit (from .../gedit_3.8.2-0ubuntu1_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Processing triggers for menu ...
Setting up gedit (3.8.2-0ubuntu1) ...
update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode
Processing triggers for menu ...
```

[IMG]http://i.imgur.com/RZ6NR7m.png[/IMG]

---

### Post by Cavsfan on 2013-05-25
I got the gedit update this morning with **sudo apt-get dist-upgrade** because it was removing a file and installing another new file.

I hope this fixes the problem with the 2 tabs opening up with **gksudo gedit *filename***.

---

