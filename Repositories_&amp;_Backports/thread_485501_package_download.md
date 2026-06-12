---
title: "package download"
date: 2007-06-26
forum: Repositories &amp; Backports
---

### Post by Huji on 2007-06-26
Pardon me for the simple question, but I'm new to Linux.

I have installed Ubuntu 7.0.4 on my home PC. Now, in order to install its modem driver, I need this package installed:

[http://packages.ubuntu.com/feisty/devel/linux-headers-386](http://packages.ubuntu.com/feisty/devel/linux-headers-386)

I must download it from work where I have access to high speed internet, and bring it home. However, I don't find a download link in the above page. How would I do that?

---

### Post by 67GTA on 2007-06-27
That should already be installed. What are you trying to do exactly?

---

### Post by Huji on 2007-06-27
> **67GTA said:**
> That should already be installed. What are you trying to do exactly?

I'm trying to do this:

[http://ubuntuforums.org/showthread.php?p=1071324](http://ubuntuforums.org/showthread.php?p=1071324)

It says I have to have two packages, and I have to get them like this:

sudo apt-get install build-essential
sudo apt-get install linux-headers-386

however, as I cannot get them from the internet directly from the Linux OS, I have to get them and burn them to a CD, then install them from there. I found the first one on the Ubuntu CD, but not the second one. Any idea?

---

### Post by 67GTA on 2007-06-27
You can go here [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and search for your package, but it will not download all the dependencies. Every time you see a red circle beside the file name, there is other files that it depends on to work. It may take a while that way.

---

### Post by 67GTA on 2007-06-27
If you could get away with it, you could use your live cd at work and copy it to an empty cd so you could take it home.

---

### Post by Huji on 2007-06-27
Suppose that I connect to the internet through LAN at work, while running the Live CD. Then I can apt-get the required package and all dependecies, perhaps. However, I don't know where these files go, so I cannot find and burn them on a CD. Just show me how.

On the other hand, I've notcied the dependencies, as mentioned on [http://packages.ubuntu.com/feisty/devel/linux-headers-386](http://packages.ubuntu.com/feisty/devel/linux-headers-386) and related pages, and compared them to what I already have installed (using Synaptic Package Manager). I've noticed that the parts the I do not have are the following three:

[http://packages.ubuntu.com/feisty/devel/linux-headers-386](http://packages.ubuntu.com/feisty/devel/linux-headers-386) seems to be relevant

[http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-16-386](http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-16-386) is just what I want to download

[http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-16](http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-16) Seven megabytes in size, this is the most important part of the dependecies.

What I'm currently doing, is to download the above three files using the same machine, but in Windows environment. Then I'm going to see if I can install them correctly.

Nevertheless, I'm still eager to have your comments on how to use the Live CD at work to get all those files I need.

---

### Post by Huji on 2007-06-27
Something else, I think linux-headers-386 is dependant to the latest version of 2.6.20 and I noticed that I have 2.6.20.**15** currently installed. I think it would be a good idea if I could install linux-headers-386 over this version (and not over 2.6.20.**16**). However, when looking at [this page]("http://packages.ubuntu.com/feisty/devel/"), I'm not sure if this same version works with the 2.6.20.15 version of headers, or whether I need to download another (compatible) version of this package. What do you think?

---

### Post by Huji on 2007-06-28
Actually, I did the last thing. I downloaded the 2.6.20.***15*** version files, and installed them. Although I didn't install my modem successfully, I think this thread is answered.

---

### Post by 67GTA on 2007-06-28
The best way would be to download them and save them to a usb stick if you have one. If you have to download them manually with Windows just be sure to get all the dependencies. You can go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and see what all is included or dependent for any given file. If they have a red dot beside them then they have dependencies. Some of them may already be installed on your system though.

---

### Post by 67GTA on 2007-06-28
Did the package have install errors?

---

### Post by Huji on 2007-06-29
No. I installed the package successfully (the version which I wanted) and now I have also installed the modem driver (I'm going to learn how to work with a modem now).

---

