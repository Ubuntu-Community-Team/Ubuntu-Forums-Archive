---
title: "Create zip archive fails from thunar/caja"
date: 2018-04-15
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2018-04-15
I attached a recording of the issue to the bug report
[https://bugs.launchpad.net/ubuntu/+source/engrampa/+bug/1764116](https://bugs.launchpad.net/ubuntu/+source/engrampa/+bug/1764116)
recording attached to bug report

---

### Post by &amp;KyT$0P# on 2018-04-15
If you install xarchiver, set it up [like this]("https://ubuntuforums.org/showthread.php?t=2384394&p=13756447&viewfull=1#post13756447"), and purge engrampa, does that work around this bug?

---

### Post by pqwoerituytrueiwoq on 2018-04-15
```
sudo apt-get purge engrapma -y && sudo apt-get install xarchiver
```
Works, but the ui is not as compact
the file does not exist in that location
found similar in /usr/luib/x86_64-linux-gnu/thunar-archive-plugin/ but no match

---

### Post by ajgreeny on 2018-04-15
Is this using a fully installed Xubuntu 18.04 or using a live USB OS from the live install media as mentioned in the bug?

---

### Post by pqwoerituytrueiwoq on 2018-04-15
Live Session form my usb flash drive loaded with today's daily ISO, will be doing a full clean install in 2 weeks on my main computer which is running 14.04 and it's last 2 kernel updates are not working with my nvidia driver

---

### Post by ajgreeny on 2018-04-15
I wonder if the live system is why you can not get it to work as I have just tried it on my full install of Xubuntu 18.04 (admittedly as a VM in VBox) and there it all worked exactly as I expected it to and I could create a .zip, any of the .tar types, and all that I attempted without a problem of any kind.

---

### Post by pqwoerituytrueiwoq on 2018-04-15
were the files you were compressing on a read only media source?
when i opened thunar as root it work properly
try to turn say /usr/share/themes/Greybird into a 7z or zip file in your ~/Desktop or /tmp folder that fails for me on the live usb
It works as expected for everything i tried except 7z and zip

[https://bugs.launchpad.net/ubuntu/+source/engrampa/+bug/1764116/+attachment/5116969/+files/Screencast%202018-04-15%2020%3A06%3A54.mp4](https://bugs.launchpad.net/ubuntu/+source/engrampa/+bug/1764116/+attachment/5116969/+files/Screencast%202018-04-15%2020%3A06%3A54.mp4)

---

### Post by ajgreeny on 2018-04-15
I'll try that tomorrow; much too late tonight!

---

### Post by ajgreeny on 2018-04-16
You are correct; trying to create a zip from /usr/share/themes/Greybird failed, presumably due to ownership problems of the files and folders that are to be in the zip archive.
No problem, however, creating exactly the same archive in 16.04 which uses file-roller and not engrampa.

---

### Post by pqwoerituytrueiwoq on 2018-04-16
Than can you please mark the bug as confirmed
BTW just confirmed the issue in ubuntu mate

---

### Post by ajgreeny on 2018-04-17
Commented on the bug that I also have this problem, though I have not the same amount of knowledge of the whole process that you obviously have, and was not aware of the process to creating a temporary archive in the source folder prior to saving it in a destination folder where I have write permissions, ie, my home.

---

### Post by pqwoerituytrueiwoq on 2018-04-17
I managed to figure that out when i saw it worked in directories i owned i suspected it may be a permission issue, so i tried it as root when it worked i used [FONT=courier new]ls -la[/FONT] to confirm my suspicions
now if i just knew where in the source code to look i could probably make a patch

---

### Post by flocculant on 2018-04-18
Did you add something to Thunar to do this? Not seeing the possibility to create archive in Thunar here. 

(Possibly because Thunar 1.7.2 Gtk3 version)

---

### Post by pqwoerituytrueiwoq on 2018-04-18
> **flocculant said:**
> Did you add something to Thunar to do this? Not seeing the possibility to create archive in Thunar here. 

(Possibly because Thunar 1.7.2 Gtk3 version)
the option is there on a stock live ISO of xubuntu 18.04
This appears to be a bug in engrampa, verified via command line, see bug reports for details
thunar has a plugin supporting both file-roller and engrampa i believe the package is [thunar-archive-plugin]("apt:thunar-archive-plugin")
.tap file are located in [FONT=courier new]/usr/lib/x86_64-linux-gnu/thunar-archive-plugin/[/FONT]

my upsteam report has more in-depth details, see downstream bug report for link

---

### Post by ajgreeny on 2018-04-19
I did not install any particular package to get the ability to create an archive using the context menu from a right click, so I presume the *thunar-archive-plugin* must be installed by default.

I will check next time I boot to the 18.04 install to see what exactly I have installed and will report back.

---

### Post by pqwoerituytrueiwoq on 2018-04-19
I assume [flocculant]("https://ubuntuforums.org/member.php?u=1990108") compiled thunar him/her self
on the install notes for thunar-archive-plug is seems they need to have the same prefix, so i guess that is why flocculant's thunar lacks that option
[http://goodies.xfce.org/projects/thunar-plugins/thunar-archive-plugin](http://goodies.xfce.org/projects/thunar-plugins/thunar-archive-plugin)

---

### Post by ajgreeny on 2018-04-19
Thunar-archive-plugin is a suggested package of thunar itself but is installed in the default Xubuntu 18.04 (and 16.04) installation.

---

### Post by flocculant on 2018-04-20
> **pqwoerituytrueiwoq said:**
> I assume [flocculant]("https://ubuntuforums.org/member.php?u=1990108") compiled thunar him/her self
on the install notes for thunar-archive-plug is seems they need to have the same prefix, so i guess that is why flocculant's thunar lacks that option
[http://goodies.xfce.org/projects/thunar-plugins/thunar-archive-plugin](http://goodies.xfce.org/projects/thunar-plugins/thunar-archive-plugin)

Yea - been testing a lot of the 'not in Xubuntu yet Gtk3 things' thunar is one of them :)

---

