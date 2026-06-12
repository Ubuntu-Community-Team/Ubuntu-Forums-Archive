---
title: "Installing Ubuntu Studio"
date: 2016-07-28
forum: Ubuntu Studio
---

### Post by LaughingHorse on 2016-07-28
This may be a really stupid question, but the question unasked is the truly stupid question.

I am about to upgrade Ubuntu from 14.04 LTS to 16.04 LTS
A long time ago I was using Ubuntu Studio and I'm wondering about the upgrade.

When I upgrade, I am going to do a fresh install.

Would I upgrade from 14.04 to 16.04 and then use say synaptic to install Ubuntu Studio on top, or is there a special package for Ubuntu Studio tht includes 16.04?

Also, what is the DAW in Ubuntu Studio?

What is the difference between just installing the packages that come with Ubuntu Studio vs. installing Ubuntu Studio?

Thanks in advance for your replies.

---

### Post by sudodus on 2016-07-29
I have some experience of Ubuntu Studio, but like you, I have only run older versions.

In general (for all flavours of Ubuntu), it is often easiest to make a fresh installation and add whatever extra program packages you want afterwards.

It is risky to upgrade to a new version, and if you do, you should ***backup*** your old system, because something might go wrong. Many people keep only a ***home*** partition (where many tweaks are stored in the hidden files of each user's home directory). If your /home directory is in the root partition you can create a new partition (with the ext4 file system) and copy the content of /home to that partition. During a fresh installation you select ***Something else*** at the partitioning window and select both a root partition,/, and the home partition, /home, that you prepared. Do ***not*** format the home partition.

It is a good idea to have a separate ***data*** partition for your own files like pictures, music, multimedia files. Then it is easy to backup these own files and the linux system separately.

---

### Post by Bucky Ball on 2016-07-29
If you install ubuntustudio-desktop on top of Ubuntu you will end up with all the default Ubuntu apps and all the UStudio default apps. Messy.

Ubuntu uses the Unity desktop environment. UStudio uses xfce4. Totally different beasts. That is a major difference between the two.

I advise a clean install of Ubuntu Studio for best results. Rule of thumb for serious AV production is to have as little as possible of what you don't need off the machine so all resources are used for editing/rendering, AV related stuff. Installing one on top of the other defeats the purpose and doesn't make for the greatest AV workstation. 

If you have enough disk space, no reason why you can have an install of each on different partitions (or run Ubuntu as a virtual machine in UStudio, not the other way around as a vm is not a good idea if you're intending resource intensive audio/visual work).

Having said all that, theoretically, there is nothing whatsoever stopping you from install ubuntustudio-desktop, rebooting and choosing the UStudio session from the login screen. Up to you if you're satisfied with the outcome. 

And what sudodus said: make sure you have backups before proceeding. 

Good luck. :)

---

### Post by LaughingHorse on 2016-07-29
Thank You for your replies!

I know there are a few things I need in addition to AV stuff.

Libre Office
Skype
Internet Browsers 
Email (Thunderbird)
Adobe Reader
The usual biz apps :)

Where would I get the download for Ubuntu Studio?
What are the DAW's that come with Ubuntu Studio?

---

### Post by sudodus on 2016-07-29
Ubuntu Studio can use the same repositories as the other Ubuntu flavours, and you can use command lines with ***apt-get*** or you can use GUI tools, ***synaptic*** or some ***software center*** to install the program packages you need.

I don't know what you mean by DAW. Please explain! (I am not a native English speaker, and I am not a multimedia or music expert.)

---

### Post by Bucky Ball on 2016-07-29
> **LaughingHorse said:**
> 
Where would I get the download for Ubuntu Studio?
What are the DAW's that come with Ubuntu Studio?

1/ The official [Ubuntu Studio]("http://ubuntustudio.org/") site.
2/ You can use whatever DAW you like, not sure what it comes with by default. You can find the default package list, probably on their site, with a bit of investigation. Ardour is popular, but costs. There is another one around but can't think of the name, also costs.

---

### Post by LaughingHorse on 2016-07-29
Thank You, Bucky.

Sudodus, DAW means Digital Audio Workstation for recording music in a recording studio or home studio. Like Pro Tools would be the DAW software for example.

---

### Post by sudodus on 2016-07-29
Thanks to explaining DAW :-)

- I support the tips by Bucky Ball, to install Ubuntu Studio from its own iso file from the Ubuntu Studio web site (not via a standard Ubuntu iso file).

- Read the documentation at the Ubuntu Studio web site.

- It is a good idea to make a fresh install.

- Add standard programs like you would into any of the Ubuntu family flavours.

Please ask again, if you are still not sure what to do :-)

---

### Post by LaughingHorse on 2016-07-29
Thank You

---

### Post by yoshii on 2016-07-31
Distrowatch.org is a great resource for answers to some of the above questions:  

[http://distrowatch.com/table.php?distribution=ubuntustudio](http://distrowatch.com/table.php?distribution=ubuntustudio)

For example, yes, Ubuntu Studio v16.04.x has LibreOffice, FireFox, Evince (PDF  reader), and a mail program (I forget it's name because I don't use it).  etcetera...

---

