---
title: "System76 green light to install Jaunty w/ EXT4?"
date: 2009-04-01
forum: System76 Support
---

### Post by arepaking on 2009-04-01
Tom,
I am eager to hear from you the green light to update our systems to Jaunty once the final version goes public. However, I was wondering if System76 will provide some insight and guidance about installing Jaunty with EXT4?

Regards,
AK

---

### Post by Lee_Machine on 2009-04-02
There were errors in the way GRUB handled an ext4 root partition, but that was resolved. 

There are also "bugs" in ext4 with the way it save data for applications. I put bugs in quotations because it's just doing what it was designed to do. 

Here is the whole story.

[http://www.h-online.com/open/Kernel-developers-squabble-over-Ext3-and-Ext4--/news/112937](http://www.h-online.com/open/Kernel-developers-squabble-over-Ext3-and-Ext4--/news/112937)

Anyways I personally would just wait and use ext3. Most of the performance gains would be most noticeable with large amounts of data. ie a database. 

I use Jaunty Beta with ext3, and it now boots in 14 seconds, plus the over all experience is a lot responsive and smoother....not sure the latter has anything to do with it. 

I'm sure I will try it out on one of my machines.

---

### Post by arepaking on 2009-04-02
Thanks Lee_Machine for sharing with us. 

I think you made a point over there. Maybe it is not the right time to switch to EXT4 for now. Let's see what others think.

Another question that I have is: What would be better, upgrading Intrepid to Jaunty? or doing a Jaunty fresh install? I'm concern about the "garbage" that this upgrade may leave behind.

Thanks again for your input.

---

### Post by Lee_Machine on 2009-04-02
I have been on the Ubuntu bandwaggon since Breezy and I have never had a flawless Distro Upgdrad. Yes they work, but one of two things usually happen. I do it right when it's released, and due to server overloads there is an error, or two it works but some config file is dicked up with a program. If i recall last time it was with sound....a few releases back. 


 Given I like to tweek my system, and I'm always trying new things to learn. So I'm sure that has something to do with it. My advice is to do a fresh install. This way you don't have to worry about messed up config files and such.

Not sure if you have one, but an external HDD is always good for backing up data. 

By the way Jaunty + Gnome-Do (with Docky) = A great Environment!

---

### Post by arepaking on 2009-04-02
Outstanding! Thanks for sharing your upgrades past experience. I am going to prepare for the release date by starting to backup my data. This brings me to the following questions: By backing up "Home" folder should be enough? or should I consider other ones?

Thanks again Lee!

---

### Post by FraggedLocust on 2009-04-02
I have installed jaunty 64-bit with both my root and home partitions using ext4. I have not encountered any large problems with the filesystem thus far, as I'm only using ~7.7GB. Nor can I make any comments on the speed, because I'm not sure if it's jaunty or ext4 that's speeding up my boot, but it's definitely an improvement over 8.10.

---

### Post by Lee_Machine on 2009-04-02
By home do you mean /home partition or your data in the home dir ie Documents, Movies, Music etc ect...?

I have no exp with backing up the /home partition (If one is made, which is standard protocol with a new S76 machine)  

But yes, if all your data is saved in the home directory. 

Make a list of all the programs you are going to want to keep. Makes it easier to remember. 

If ya need any help with the upgrade then at the time just start a thread. :p

Lastly when I back up data I like to use the time to delete what is not needed. Its easy to become a digital pack rat :lolflag:

---

### Post by speedkreature on 2009-04-08
> **FraggedLocust said:**
> I have installed jaunty 64-bit with both my root and home partitions using ext4. I have not encountered any large problems with the filesystem thus far, as I'm only using ~7.7GB. Nor can I make any comments on the speed, because I'm not sure if it's jaunty or ext4 that's speeding up my boot, but it's definitely an improvement over 8.10.

I just upgraded my new Pangolin notebook to Jaunty and replaced grub with grub2-pc, then migrated from ext3 to ext4.  A performance increase is not noticeable to me during most "normal" operations like opening documents, surfing the web, or playing a game, etc.  However when moving lots of tiny files or any number of really large files ( > 1GB) there is a wonderful performance increase.  I also noticed an increase during the writing stages of editing a video.

As of yet, I have not had any problems using ext4.

However, from what I've read about ext4 support, there aren't any plans to support it mainstream (or at least as a default file system) until Ubuntu 9.10 at the earliest.  I wish I could find that article...

---

### Post by thomasaaron on 2009-04-08
[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

> Ext4 filesystem support

Ubuntu 9.04 Beta supports the option of installing the new ext4 file system. ext3 will remain the default filesystem for Jaunty, and we will consider ext4 as the default for the next release based on user feedback. There has been extensive discussion about the reliability of applications running on ext4 in the face of sudden system outages. Applications that use the conventional approach of writing data to a temporary file and renaming it to its final location will have their reliability expectations met in Ubuntu 9.04 beta; further discussion is ongoing in the kernel community.

---

