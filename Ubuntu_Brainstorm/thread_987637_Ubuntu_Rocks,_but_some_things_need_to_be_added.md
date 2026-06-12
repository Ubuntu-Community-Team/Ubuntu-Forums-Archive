---
title: "Ubuntu Rocks, but some things need to be added"
date: 2008-11-19
forum: Ubuntu Brainstorm
---

### Post by Ice Dragon on 2008-11-19
Hi all,

I am having great success with Ubuntu 8.10, ive installed it on my work computer, home desktop, laptop, and i have Ubuntu 8.04 on my home server. Things are going great!

I would love to see this OS keep rising in popularity and eventually become a threat for microsoft as another option for the average computer user.

To that end, there are some key things missing from Ubuntu that seems a bit odd for such a highly advanced OS to be missing.

1. Format GUI, particularily accessable from right clicking on any drive. I inserted a USB drive into my laptop, right clicked on it, expecting id be able to chose format and pull up a GUI where I could select my format options, but nothing was there. Apparently format is only available through command line.

2. My laptop has an svideo port that I use to hook up to my TV and watch videos on. Unfortunately when I go into gnome-display-settings to enable to tv display the only way it will work is if i mirror displays, thats too bad since windows allows me to simply click the secondary display click extend desktop and i can drag windows back and forth from laptop to tv without having to mirror displays. Mirroring displays is bad due to the intensive stress it puts on the video card when it tries to play two images of the video your watching in VLC.

3. Permissions on files and folders needs to be done by default in an easier way. I am having all kinds of trouble when i copy something from my laptop to a share on my desktop. I goto my desktop and that file is locked and cannot be moved from the shared folder because i am not the owner. Yet the share is set to give everyone full read and write access, so i dont know why it keeps restricting files so much. Its agrivating to continually goto the command line and chmod or chown everything after i copy it over the network.

---

### Post by jenkinbr on 2008-11-19
Format GUI: Try gparted ```
sudo apt-get install gparted
```

---

### Post by Keen101 on 2008-11-19
yeah, gparted is what you want for gui partitioning. 

and as for me... i think it's already a threat to Microsoft.

Sure there are some quirks here and there, but i like it better than the windows quirks. hopefully i can become a developer some day, and fix some of the quirks that bug me. Maybe you can too someday.

---

### Post by sdennie on 2008-11-19
> **Ice Dragon said:**
> 
2. My laptop has an svideo port that I use to hook up to my TV and watch videos on. Unfortunately when I go into gnome-display-settings to enable to tv display the only way it will work is if i mirror displays, thats too bad since windows allows me to simply click the secondary display click extend desktop and i can drag windows back and forth from laptop to tv without having to mirror displays. Mirroring displays is bad due to the intensive stress it puts on the video card when it tries to play two images of the video your watching in VLC.


My laptop has HDMI and not svideo but, see if there is a Fn key combination on your laptop to swap through available outputs (and configurations of those outputs).  On my laptop I can hit Fn-F8 and it magically switches between Laptop, Laptop + Mirrored HDMI, HDMI only, etc.  I don't know how to configure that in X, the buttons just worked.

---

### Post by Ng Oon-Ee on 2008-11-19
> **Ice Dragon said:**
> 3. Permissions on files and folders needs to be done by default in an easier way. I am having all kinds of trouble when i copy something from my laptop to a share on my desktop. I goto my desktop and that file is locked and cannot be moved from the shared folder because i am not the owner. Yet the share is set to give everyone full read and write access, so i dont know why it keeps restricting files so much. Its agrivating to continually goto the command line and chmod or chown everything after i copy it over the network.

With regards to this issue, I believe that the permissions of the copied files are set by the copying computer, your laptop in this case. If this is an NTFS share, then you should be mounting it with full read-write permissions for everyone (including 'others'). If this is a native Linux file-system share, then the original permissions on the files are maintained when copying. If they've been copied from the /home folder, by default the permissions for files there are 644 (I believe), so others can only read your files. Some paranoid people set it to not allowing others even to read your files.

Anyway, what you've run into is quite integral to the idea of a multi-user OS, the fact that your files aren't by default editable by just anyone.

---

### Post by Ice Dragon on 2008-11-19
> **jenkinbr said:**
> Format GUI: Try gparted ```
sudo apt-get install gparted
```

Thank you, that is exactly what I was looking for. 

Now the question becomes, since such a wonderful formatting GUI exists, why is it not part of Ubuntus default installation? a partitioning and formatting gui really seems like it should be a default item.

---

### Post by Ice Dragon on 2008-11-19
> **vor said:**
> My laptop has HDMI and not svideo but, see if there is a Fn key combination on your laptop to swap through available outputs (and configurations of those outputs).  On my laptop I can hit Fn-F8 and it magically switches between Laptop, Laptop + Mirrored HDMI, HDMI only, etc.  I don't know how to configure that in X, the buttons just worked.

I think my laptop has that too only its fn-f5, i went to check when you posted this. however when pressing it with the tv hooked up through svideo the tv flickered a bit but still remained a blank screen.

I went into screen resolution to turn the tv in the software, i set the resolution  to 1024x768, however it asks me about writing to my xorg.conf which im not confortable with unless i know its not going to break things. here is a screen shot of what it said.

[screen shot]("http://tibbetts.homelinux.com/snapshot001.png")

---

### Post by jenkinbr on 2008-11-19
> **Ice Dragon said:**
> Thank you, that is exactly what I was looking for. 

Now the question becomes, since such a wonderful formatting GUI exists, why is it not part of Ubuntus default installation? a partitioning and formatting gui really seems like it should be a default item.
It is on the liveCD, but Ubuntu doesn't install it because the goal is to cram as much software as possible to get a funtioning usable system for most user and hardware configurations.  One of the reasons that it isn't installed is that most partitioning tasks are best done in a liveCD environment with no actual disks mounted.  Don't expect to be able to resize your /home partition while in ubuntu - it simply will not work because you will be unable to unmount it.

---

### Post by Ice Dragon on 2008-11-19
> **jenkinbr said:**
> It is on the liveCD, but Ubuntu doesn't install it because the goal is to cram as much software as possible to get a funtioning usable system for most user and hardware configurations.  One of the reasons that it isn't installed is that most partitioning tasks are best done in a liveCD environment with no actual disks mounted.  Don't expect to be able to resize your /home partition while in ubuntu - it simply will not work because you will be unable to unmount it.

im thinking something more simple like formatting a usb drive, one shouldent be expected to boot from a cd to do that simple task.

---

### Post by Ng Oon-Ee on 2008-11-19
> **Ice Dragon said:**
> im thinking something more simple like formatting a usb drive, one shouldent be expected to boot from a cd to do that simple task.
Ah, but I doubt any new user would open a partition editor to format a USB drive.

This probably needs to be 'solved' as a usability issue by some scripts within Nautilus or changes to Gnome. Though frankly I believe its nowhere near top priority.

---

### Post by tjwoosta on 2008-11-19
> I inserted a USB drive into my laptop, right clicked on it, expecting id be able to chose format and pull up a GUI where I could select my format options, but nothing was there.

that would be a great improvement for ubuntu


you should submit your idea at ubuntu brainstorm
[http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")

---

### Post by Ng Oon-Ee on 2008-11-20
> **tjwoosta said:**
> that would be a great improvement for ubuntu


you should submit your idea at ubuntu brainstorm
[http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")
Please note, though, that base Ubuntu is not able to label FAT16/32 or NTFS-formatted drives, and this would mean that existing labels would not be preserved. Behaviour which would be unexpected for the vast majority of Windows users.

---

### Post by Ice Dragon on 2008-11-20
> **Ng Oon-Ee said:**
> Please note, though, that base Ubuntu is not able to label FAT16/32 or NTFS-formatted drives, and this would mean that existing labels would not be preserved. Behaviour which would be unexpected for the vast majority of Windows users.

Why is base Ubuntu not able to label those? its certainly not an impossibility from the programming perspective, so it is a legal issue? Im not sure why you wouldent be able to format as a compatabile type of OS. 

If it is a legal issue then maybe the first time you right click and chose format it points you to add/remove to grab the format gui that way to avoid legal troubles.

Either way im sure someone is clever enough to get around this and still allow people to have basic functionality that should be included in the OS by default.

---

### Post by sdennie on 2008-11-20
You can label fat/ntfs drives just fine.  This link says USB drivers but, it's applicable to any partition on any drive: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Kellemora on 2008-11-21
Hi Ice

I thought I already mentioned this to you in another post.

For sharing files, DON'T PUT the file you are sharing onto the OTHER Computer, leave it on your OWN computer.  Then FETCH it from your computer from the other computer you want it on.  That way all the permissions stay intact as they should.

Don't know if thats a Bug in Ubuntu or if it was designed that way for security reasons?  Took me a while to figure it out myself!
But it makes it hard to keep things where they BELONG!
So I made a little Cron Job that goes and fetches all the files and brings them back to where they belong, hi hi........

TTUL
Gary

---

### Post by aysiu on 2008-11-21
These are already on Ubuntu Brainstorm:
[Idea #5502: easy right click format of sd cards and other usb media](http://brainstorm.ubuntu.com/item/5502/)
[Idea #15507: Ubuntu needs much better support for Extended desktop display](http://brainstorm.ubuntu.com/item/15507/)
[Idea #2560: Option to Propagate permissions of parent directory to new files](http://brainstorm.ubuntu.com/idea/2560/)

---

### Post by gnomeuser on 2008-11-21
> **Ice Dragon said:**
> im thinking something more simple like formatting a usb drive, one shouldent be expected to boot from a cd to do that simple task.

Your friends at Red Hat are already working on this:

[http://blog.fubar.dk/?p=103](http://blog.fubar.dk/?p=103)

Of interest is page 9 in Davidz presentation. Alternatively next week when Fedora 10 comes out you can download that and install the gnome-disk-utility package then reboot (to get DeviceKit started) and enjoy a complete format, fsck and other related tasks experience.

---

### Post by Ng Oon-Ee on 2008-11-23
> **vor said:**
> You can label fat/ntfs drives just fine.  This link says USB drivers but, it's applicable to any partition on any drive: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

I know, I've come across that, my point is that base Ubuntu (the standard install) is not able to label fat/ntfs drives. As your link says, you need to install the programs (ie, which are not default) to do so.

I'm not sure there's any legal issue here, as read-write capability for NTFS is available by default in Ubuntu. Probably just not something the devs see as important enough to support explicitly.

EDIT: I just checked my install, for some reason or other I do have mlabel (used for renaming FAT drives) installed. As I can't remember ever needing it, it is probably part of the base install. However, ntfslabel is NOT part of the base install, as I don't have it here.

---

