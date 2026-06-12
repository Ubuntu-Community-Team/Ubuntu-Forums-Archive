---
title: "How do can I get Ubuntu to list all the drivers in use?"
date: 2009-06-14
forum: The Cafe
---

### Post by MasterNetra on 2009-06-14
I was thinking about setting up a partition for Arch and giving it ago, but off hand I don't know all the drivers Ubuntu is using for my system. So I was wondering if I could get it to simply display them all and prehaps a brief desc? Oppose to hunting in synaptic for them and possibly missing some that maybe critical.

---

### Post by blueturtl on 2009-06-14
You're probably looking for the 'lsmod' command. It will list all modules plugged into the kernel. However since modules are not necessarily separate downloads, you will have to research which modules are "in stock" and which are included in extra repository packages.

For example I discovered under Debian that if I wanted to use webcams, I had to install a package called gspca-modules which installs all the web cam related module files.

---

### Post by .Maleficus. on 2009-06-14
Arch isn't like Gentoo in the sense that you need to know EVERYTHING about your system.  Like Ubuntu, Arch has most the the "common" kernel modules built in, and you're unlikely to have any hardware issues (or at least I didn't on any of the 6 machines Arch has been on).  Like blueturtl said, 'lsmod' will show all of the modules currently loaded though.


Edit:  And if you do have any troubles, 'modprobe xxx' will load a module and 'rmmod xxx' will unload a module.

---

### Post by MasterNetra on 2009-06-14
> **blueturtl said:**
> You're probably looking for the 'lsmod' command. It will list all modules plugged into the kernel. However since modules are not necessarily separate downloads, you will have to research which modules are "in stock" and which are included in extra repository packages.

For example I discovered under Debian that if I wanted to use webcams, I had to install a package called gspca-modules which installs all the web cam related module files.

Xorg isn't even in that list don't look like what I'm looking for. When installing Arch it would help to know the packages I need to and should install for my Dell Latitude D530 ^.^

> **.Maleficus. said:**
> Arch isn't like Gentoo in the sense that you need to know EVERYTHING about your system.  Like Ubuntu, Arch has most the the "common" kernel modules built in, and you're unlikely to have any hardware issues (or at least I didn't on any of the 6 machines Arch has been on).  Like blueturtl said, 'lsmod' will show all of the modules currently loaded though.


Edit:  And if you do have any troubles, 'modprobe xxx' will load a module and 'rmmod xxx' will unload a module.

Perhaps I didn't make myself clear, if thats the case my apologize. Possibily a more accurate question would be. "Is there a way to see all the driver packages that Ubuntu uses?" Like xorg for example, with them displaying the full package name of course. ^.^

---

### Post by anystupidname on 2009-06-14
Others answered the first part of your question better than I could. To answer the second part, "modinfo -d <module name>" will give you the short description.

---

### Post by Skripka on 2009-06-14
> **MasterNetra said:**
> Xorg isn't even in that list don't look like what I'm looking for. When installing Arch it would help to know the packages I need to and should install for my Dell Latitude D530 ^.^



Perhaps I didn't make myself clear, if thats the case my apologize. Possibily a more accurate question would be. "Is there a way to see all the driver packages that Ubuntu uses?" Like xorg for example, with them displaying the full package name of course. ^.^

In all honesty, if you follow the Arch Beginner's Wiki document top to bottom, you should have a system with most all the Core things you need.

Some niceties like on demand CPU scaling are easy to do-and in the Arch Wiki.

---

### Post by anystupidname on 2009-06-14
> **MasterNetra said:**
> Xorg isn't even in that list don't look like what I'm looking for. When installing Arch it would help to know the packages I need to and should install for my Dell Latitude D530 ^.^

Perhaps I didn't make myself clear, if thats the case my apologize. Possibily a more accurate question would be. "Is there a way to see all the driver packages that Ubuntu uses?" Like xorg for example, with them displaying the full package name of course. ^.^

After reading your followup post, I'm thinking you're looking more for something like "apt-show-versions" in combination with "aptitude show <package>"

---

### Post by MasterNetra on 2009-06-14
> **Skripka said:**
> In all honesty, if you follow the Arch Beginner's Wiki document top to bottom, you should have a system with most all the Core things you need.

Some niceties like on demand CPU scaling are easy to do-and in the Arch Wiki.

Does the Arch CD come with the Broadcom STA wireless driver do you know? I generally have to connect wirelessly :/

---

### Post by Skripka on 2009-06-14
> **MasterNetra said:**
> Does the Arch CD come with the Broadcom STA wireless driver do you know? I generally have to connect wirelessly :/

From the linky in my sig ;)

[http://wiki.archlinux.org/index.php/Beginners_Guide#Wireless_Quickstart_For_the_Live_Environment_.28If_you_need_wireless_connectivity_during_the_installation_process.29](http://wiki.archlinux.org/index.php/Beginners_Guide#Wireless_Quickstart_For_the_Live_Environment_.28If_you_need_wireless_connectivity_during_the_installation_process.29)

---

### Post by mikewhatever on 2009-06-14
> **MasterNetra said:**
> I was thinking about setting up a partition for Arch and giving it ago, but off hand I don't know all the drivers Ubuntu is using for my system. So I was wondering if I could get it to simply display them all and prehaps a brief desc? Oppose to hunting in synaptic for them and possibly missing some that maybe critical.

sudo lshw | grep driver

---

### Post by Sealbhach on 2009-06-14
Yes, or simply run lshw it lists your hardware and gives the driver used for each piece.

.

---

### Post by MasterNetra on 2009-06-14
> **Skripka said:**
> From the linky in my sig ;)

[http://wiki.archlinux.org/index.php/Beginners_Guide#Wireless_Quickstart_For_the_Live_Environment_.28If_you_need_wireless_connectivity_during_the_installation_process.29](http://wiki.archlinux.org/index.php/Beginners_Guide#Wireless_Quickstart_For_the_Live_Environment_.28If_you_need_wireless_connectivity_during_the_installation_process.29)

Thanks, it lead me (eventully) to where I needed to see for the wireless. which was: [http://wiki.archlinux.org/index.php/Broadcom_BCM4312](http://wiki.archlinux.org/index.php/Broadcom_BCM4312) ^.^

---

### Post by MasterNetra on 2009-06-14
Could I edit Arch's iso with a archiver to throw in the wireless tarball so i can extract it accordingly and install it? Or would that be a bad idea? I tried looking at: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) but it served only to confuse me. I think a more basic and simple tutorial is required for extracting and Puting together a generic iso... With windows you could use some iso program to drag and drop files into a iso to be created, but meh.

Never mind found this: [http://ubuntuforums.org/archive/index.php/t-6509.html](http://ubuntuforums.org/archive/index.php/t-6509.html)

---

