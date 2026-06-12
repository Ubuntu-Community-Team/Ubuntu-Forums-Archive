---
title: "Offline Software Installation in Ubuntu"
date: 2011-12-26
forum: Tutorials
---

### Post by cortman on 2011-12-26
**[SIZE="3"]Offline Software Installation in Ubuntu[/SIZE]**

There's been a number of requests for help regarding installing programs in Ubuntu without an internet connection. It was one of my first questions when I started using Ubuntu, so I thought I'd make this tutorial to explain how.
This tutorial assumes you have access to another Ubuntu machine that is online, and that Synaptic Package Manager is installed on both machines. If you only have access to an online computer running Windows, you can still do it- see [my other tutorial]("http://ubuntuforums.org/showthread.php?t=1915489") for instructions. If you did a fresh installation of 11.10 Oneiric Ocelot or higher, you'll need to install Synaptic on the offline machine first. (For some reason it didn't come bundled with 11.10) This is a little involved but very doable. [Here's]("http://ubuntuforums.org/showthread.php?t=1901446") a link to my tutorial on that procedure.

[SIZE="2"]**1.**[/SIZE] On **offline** machine: Open a terminal with Control+Alt+t and type

```
synaptic
```

This will open up the Synaptic Package manager. You can browse available software in the column on the far left, or if you know specifically what you're looking for, type it into the search box.
When you find the software you want to install, right click it and select "Mark for Installation". If a dialog comes up "Mark Additional Required Changes" select Mark. This will ensure that all the packages required for the selected software get installed as well.

[SIZE="2"]**2.**[/SIZE] Once you've picked your software, go to File>Generate Package Download Script. Save the script to a USB flash drive or some other portable media. You can name the script whatever you want, but for clarity we'll assume you named it "download".
The Package Download Script is just a little text file (with a .sh extension) that will tell your online computer which packages to download, so you can transfer them to the offline computer.

**[SIZE="2"]3.[/SIZE]** Take the flash drive to your **online** computer. Create a new folder called "packages" in the home folder to hold the downloaded packages, and copy the script to that folder.

[SIZE="2"]**4.**[/SIZE] Open up a terminal on the online computer using Control+Alt+t, and copy/paste the following code:

```
cd package
```

Now copy/paste

```
chmod +x download.sh
```

And finally

```
./download.sh
```

This will download the packages to the folder containing the script. If you open the package in a file manager you'll see one or more files with the extension .deb. These are the software package files. 

[SIZE="2"]**5.**[/SIZE] Copy the "packages" folder containing the .deb files to the flash drive and onto the /home folder of the **offline** computer.

[SIZE="2"]**6.**[/SIZE] Open up a terminal on the offline computer and type

```
sudo dpkg -iR packages
```

You'll be prompted for your administrator password, which will be the same as your user login password. Enter it and Ubuntu will install your software!

---

### Post by Channi on 2011-12-27
here are some more options...
[http://channikhabra.blogspot.com/2011/07/why-not-to-install-linux-offline-and.html](http://channikhabra.blogspot.com/2011/07/why-not-to-install-linux-offline-and.html)

---

### Post by cortman on 2011-12-29
Thanks for the link. Obviously I recommend the way shown above as being simplest and most universal, but it's good to have other options too.

---

### Post by grahammechanical on 2012-01-01
@cortman

I have just posted a link to your tutorial for someone who wanted to know how to install wine in Ubuntu 11.10 without an internet connection.

Well done. Regards.

---

### Post by cortman on 2012-01-02
> **grahammechanical said:**
> @cortman

I have just posted a link to your tutorial for someone who wanted to know how to install wine in Ubuntu 11.10 without an internet connection.

Well done. Regards.

Thanks a lot, grahammechanical! I'm glad it was of help!

---

