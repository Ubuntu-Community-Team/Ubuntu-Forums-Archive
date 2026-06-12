---
title: "Question about release 13.04.."
date: 2013-01-06
forum: Ubuntu Development Version
---

### Post by Burnedbrain on 2013-01-06
Hello to all!Thats my first post in ubuntu community and is gonna be a little long one..First of all sorry if someone cant understand some of my sentences cause my english arent so good!In the point now..

I bought a netbook last year and with windows7 it was really ennoying,i think is too heavy os for my netbook so i thought that this was the perfect timing to try linux at last!
I downloaded many distros and most of all i liked xubuntu cause it was fast and friendly and much similar to windows but not everything worked fine.Some problems with sound and microphone that officially as i saw there are no solutions.
So i decided to get back on windows :(
Now i am waiting for the new xubuntu release(thats gonna released at april or not?) and i have a question..Did the problems for my netbook (acer aspire one 522) gonna be solved?
Maybe my question cant be answered but as i said,i am new to this community so forgive me...
Cheers dear "penguins",i hope to install xubuntu at april again without problems!

---

### Post by buckyaustin on 2013-01-07
When you installed Xubuntu did you try updating the system? Also posting the hardware that is part of your netbook helps solve the problem. I also hope that Xubuntu 13.04 will solve your problem. The release date of Xubuntu 13.04 is not set to a time period, it can and could be delayed. I am not saying that it is delayed but it could be

---

### Post by sudodus on 2013-01-07
> **buckyaustin said:**
> When you installed Xubuntu did you try updating the system? Also posting the hardware that is part of your netbook helps solve the problem. I also hope that Xubuntu 13.04 will solve your problem. The release date of Xubuntu 13.04 is not set to a time period, it can and could be delayed. I am not saying that it is delayed but it could be
+1

Also, you may need to tweak the settings of pulse-audio. There is a GUI tool, and after some time you will probably find settings that work. Do it while playing some music or video, so that you notice when it starts working.

Usually the light Ubuntu flavours Xubuntu and Lubuntu work well with netbooks. Xubuntu 12.04 has long time support until April 2015 and is very stable now.

- Is it according to this spec: acer aspire one 522

- Is there 1 GB RAM and Radeon HD 6250 graphics?

And a big Welcome to the Ubuntu Forums :-)

---

### Post by Burnedbrain on 2013-01-07
Thanks for the warm welcome guys!
Of course i updated the system but the problems didnt solved.I guess that for now noone have a solution cause its officially reported that these problems exist at this link [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

Also sudodus the specs you are writing are correct,my netbook have the c-50 cpu,1 gb ram and the hd6250 ati.
I read that many people with this netbook have the same problems.
Also..the version 12.04 is better than 12.10?I didnt knew that,i thought that the newer will be better..

---

### Post by dino99 on 2013-01-07
its good you have found the thread about your model; and look also to the other url(s) listed at the end of that thread.
Generaly speaking, with recent hardware, its better to use one of the latest kernel to grab the latest fixes. You can install that kernel after having downloaded it into an empty folder:
-select the 32 or 64 bits packages (in your case, 32 bits is ok)
- you need 2 kernel-headers : .... all.deb  &  ....i386.deb
- you need 2 images : ....image....i386.deb  & .....image-extra....i386.deb

Then open a terminal & from that folder (cd command), run :

```
sudo dpkg -i *
```

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

On the next reboot, then look at possible errors logged into /home.xsession-errors and into /var/log/dmesg ; that let you google around the issue and find possible solutions already found by other users.

---

### Post by sudodus on 2013-01-07
> **Burnedbrain said:**
> ...
Also..the version 12.04 is better than 12.10?I didnt knew that,i thought that the newer will be better..

12.04 LTS:

+ More stable (less bugs)
+ Long time support

- May lack some driver for new hardware
- Some software may lack some new ability

so it depends ... Generally an older version might be better for old hardware and a newer version for new hardware. But use only supported versions. Watch out for the end of life because of the important security updates!

---

### Post by buckyaustin on 2013-01-07
You should install the amd-microcode. I have an AMD CPU and this solved a lot of problems with speed, sound, visual and stability of the system overall. Also have you tried installing the agrlx driver for your ati graphics card?

ps: your netbook supports another 1gb of Ram.

---

### Post by Burnedbrain on 2013-01-07
sudodus thanks again!
Dino99 thank you too but as a new linux user as me these solutions you are writing seems so confusing.I just want to do an installation and all function properly from the beginning,will be easier for me to get used to a new operating system,hope you understand me.

Offtopic question:i have a partition on my hard disk,the first one have windows7 and the other one is for storing my staff..if i do a format at the first one to install xubuntu,the second one gonna be recognized properly with all of my staff inside or i have to change the format of the second partition also?NTFS is recognized by linux?

---

### Post by Bucky Ball on 2013-01-07
[I]Thread moved to [B]Ubuntu +1

[/B][/I]Welcome to the forums. ;)

If you are wanting to try Linux, 13.04 is not the best place to start. It's not released until April and is very much 'testing'. Stick with the LTS release to dip your toe in; 12.04 LTS and work from there. You would be much better to post regarding the issues you are having with Xubuntu 12.04 LTS and try fix them rather than waiting until April. Waste of good learning time!

There is absolutely no guarantee the 'latest is the greatest'. It doesn't work that way and might not fix anything. Your problem is probably already fixable. I advise installing Xubuntu 12.04 again (unless it's already there), and posting new threads addressing whatever issues you're having with that as you're tackling it from the wrong end. ;)

Good luck.

---

### Post by dino99 on 2013-01-07
yes ubuntu deals with ntfs via its ntfs-3g driver.

here is how im doing installation:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

note: now the "manual" installation has been renamed "try something else" inside the installer.

---

### Post by Burnedbrain on 2013-01-07
> **Bucky Ball said:**
> You would be much better to post regarding the issues you are having with Xubuntu 12.04 LTS and try fix them rather than waiting until April. **_Waste of good learning time!_**

The bold sentence was the key word to convince me to give xubuntu 12.04 another one chance:D I will try to install it without loosing my staff at the second partition.
Also,dino99 thanks for the help again.I will return with more info in next days.
Love this penguin community!

---

### Post by sudodus on 2013-01-07
> **Burnedbrain said:**
> The bold sentence was the key word to convince me to give xubuntu 12.04 another one chance:D I will try to install it without loosing my staff at the second partition.
Also,dino99 thanks for the help again.I will return with more info in next days.
Love this penguin community!

Good luck :-)

---

### Post by Burnedbrain on 2013-01-07
Two more questions before i download and install xubuntu..

-Whats the difference between alternate and desktop distro?
-At the moment i have installed already win7 with double partition as i said...can i install xubuntu now to have duall boot without touching the other 2 partitions or i have to format the first one again?

---

### Post by sudodus on 2013-01-07
> **Burnedbrain said:**
> Two more questions before i download and install xubuntu..

-Whats the difference between alternate and desktop distro?

The alternate iso has a text-based installer, that works also with small RAM. [COLOR="Green"]***1GB is enough for the desktop distro, and it gives you the possibility to run a live session, that is to boot Xubuntu from the install CD/USB drive and test it without installing it to the internal HDD.***[/COLOR]
> 
-At the moment i have installed already win7 with double partition as i said...can i install xubuntu now to have duall boot without touching the other 2 partitions or i have to format the first one again?
If you have less than 4 partitions, you can 'steal' some disk space from one of them and create an extended partition. And in the extended partition you create two partitions, one for the root file system (ext4) mounted on /, and one swap partition (virtual memory).

If you already have 4 partitions, there are options too, either to wipe one partition (after backing up its content), or running wubi with Xubuntu. If you are happy with Xubuntu, I'd recommend that you give it own partitions (wubi is good for testing, but not for long time regular usage).

---

### Post by kansasnoob on 2013-01-07
> **Burnedbrain said:**
> Two more questions before i download and install xubuntu..

-Whats the difference between alternate and desktop distro?
-At the moment i have installed already win7 with double partition as i said...can i install xubuntu now to have duall boot without touching the other 2 partitions or i have to format the first one again?

Please use the desktop image :)

Once installed they both behave the same but the desktop installer is easier to understand. Since you're asking noob questions (not an insult - look at my name) I'd begin by downloading and burning the Xubuntu desktop image, then from the boot menu choose "check disc for defects".

If that completes showing "no defects found" then choose "try Xubuntu w/o installing". Next post the output of this command here:

> sudo parted -l

That will show us how many partitions already exist so we can better advise you :D

---

### Post by Burnedbrain on 2013-01-10
Version 12.04 installed!I have to report some crashes when i was trying to update the system but after updating first the language packages and then try again system update it finnaly worked.Now my system seems steady and nice!
Shall i open new topic for my sound problems cause i cant find a soluition already?

---

### Post by BlinkinCat on 2013-01-10
> **Burnedbrain said:**
> Shall i open new topic for my sound problems cause i cant find a solution already?

Hi,

Yes, you should open a new thread for any new problem as it arises in the correct forum.  I am glad you appear to be up and running.

I have Xubuntu 12.04 and enjoy it very much.

Cheers - ):P

---

### Post by BlinkinCat on 2013-01-10
Hi again,

If you are satisfied all of your issues in this thread have been resolved, you could mark the thread as "Solved". Just open the thread tools at the top of the page and select "Mark as Solved".

All the best - :)

---

### Post by Burnedbrain on 2013-01-10
> **BlinkinCat said:**
> Hi again,

If you are satisfied all of your issues in this thread have been resolved, you could mark the thread as "Solved". Just open the thread tools at the top of the page and select "Mark as Solved".

All the best - :)

Thanks a lot,i'll try first at a greek community cause its easier for me to understand and i will post back here if the problems remains!
Cheers =D>

---

### Post by dino99 on 2013-01-10
one thing to remember: here its a 13.04 thread; so post your future comments inside the "upgrade" subforum, not here (you will be kicked out  ;)  )

---

