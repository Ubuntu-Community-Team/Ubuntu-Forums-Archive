---
title: "HOW TO Avoid Wubi &amp; Install Ubuntu on USB Drive"
date: 2010-12-22
forum: Tutorials
---

### Post by amjjawad on 2010-12-22
[CENTER][COLOR=DarkRed][SIZE=5][B]HOW TO Avoid Wubi 
& 
Install Ubuntu on USB Drive

[/B][/SIZE][/COLOR][LEFT][COLOR=Black][SIZE=3]
[/SIZE][/COLOR][U][B][FONT=Verdana][SIZE=3]Introduction
[/SIZE][/FONT][/B][/U][FONT=Verdana][SIZE=3]Don't be confused. I know _[**Wubi**]("https://help.ubuntu.com/community/Wubi")_ has nothing to do with installing _[**Ubuntu**]("http://www.ubuntu.com/")_ on an USB-Drive but if you just could wait for few seconds, you'll understand everything.[/SIZE][/FONT][U][B][FONT=Verdana][SIZE=3]
[/SIZE][/FONT][/B][/U][SIZE=3][FONT=Verdana]
This guid[/FONT][/SIZE][COLOR=Black][SIZE=3]e has been written based on a real experiment which I have recently done by myself. I have not used any word from any website, guide, thread, etc whatsoever.
If you have any questions, suggestions or feedback, please feel free to post it here.

[/SIZE][/COLOR][SIZE=3][COLOR=Red]In order not to confuse anyone, I'm going to use the "**_[LiveCD]("https://help.ubuntu.com/community/LiveCD")_**" in this guide instead of the **_[LiveUSB]("https://help.ubuntu.com/community/Installation/FromUSBStick")_**. It does not mean you can't use LiveUSB, but I'm just avoiding that with this guide. This guide is targeting the new comers to Ubuntu so it should be crystal clear.[/COLOR]
[/SIZE][COLOR=Black][SIZE=3]
[/SIZE][/COLOR][FONT=Verdana][SIZE=3]**_[Hardware Used (click):]("http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7125")_**[/SIZE][/FONT][URL="http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7125"][FONT=Verdana][SIZE=3]
[/SIZE][/FONT][/URL]   [FONT=Verdana][SIZE=3]Motherboard: Intel [/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]CPU: Pentium 4 @3.00GHz[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]RAM: 448MB DDR PC400[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]HDD: Samsung 20GB[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Graphics Card: ATI (Built-in)[/SIZE][/FONT][FONT=Verdana][SIZE=3]
USB: USB-Drive Imation 4GB[B][U]

Requirements:[/U][/B][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Ubuntu 10.04 LiveCD[/SIZE][/FONT]
[COLOR=Black][SIZE=3]USB-Drive


[U][B]Aim of this guide
[/B][/U][/SIZE][/COLOR]
[LIST=1]
[*][SIZE=3]Avoid **Wubi **which I don&#8217;t recommend to any user who is willing to try Ubuntu without making major changes on his/her system.[/SIZE]
[*][SIZE=3]Learn how to install Ubuntu in a plain and a simple way.
[/SIZE]
[*][SIZE=3]Install and Use Ubuntu **without** making **any changes** to your **HDD**.[/SIZE]
[/LIST]
[SIZE=3]_**Explanation**_[/SIZE]
[SIZE=3]I'm not going to explain about Wubi here but I'll provide all the useful links that you may want to have a look at.

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29")

Now, this is **my own personal opinion** about Wubi that you may disagree with it which is fine with me but keep in mind that I'm writing this guide for a reason. I'm trying to save your time and offer a better choice for you.

Unlike what some may think about Wubi, I think it's a problematic choice more than a helpful one. Again, this is my own personal opinion.
Lots of users faced many troubles with Wubi. This guide is an alternative *better* solution.

It's true that Wubi will be installed inside Windows just like any other program you run under Windows but, again, I've seen lots of problems and users were complaining and had no idea what to do?
Eventually, sooner or later, you're going to install Ubuntu. In most cases, this is what will happen. IMHO, I think those who don't want to install Ubuntu is because they faced lots of problems with Wubi, thus they did not have the chance to try and see what the real Ubuntu is. I don't blame them. The first impression is quite important.

Having all that said, the best choice is to avoid Wubi all together and instead of that, you can [COLOR=Red]_**"Install"**_ [/COLOR][B][COLOR=Red]Ubuntu _WITHOUT_ making _any changes_ to your HDD.[/COLOR]

[/B]I know that sounds silly and impossible for the very first moment but again, wait and see.

Ubuntu, just like most/some of the other Linux Distributions, can be installed on an **_[USB-Drive/Pen-Drive/USB-Flash]("http://en.wikipedia.org/wiki/USB_flash_drive")_**. 

By installing Ubuntu on an USB-Drive, you will achieve this (even if that will be your first time to use Ubuntu):

a) Learn how to install and use Ubuntu
b) No changes will be made to your HDD whatsoever

Are we in the same page? good :)

Before we start, please have a look at [**_this link_**]("https://help.ubuntu.com/community/Installation").

_**Steps**_

0- A [COLOR=Red]**backup**[/COLOR] to your current OS and/or your important data is and will be always recommended if not a must.

1- _[Download]("http://www.ubuntu.com/desktop/get-ubuntu/download")_ the version that works on your hardware (32-bit/64-bit).

2- Check _[MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")_ and compare it to _[Ubuntu Hashes]("https://help.ubuntu.com/community/UbuntuHashes#10.04%20LTS")_

3- Create the LiveCD as per the instruction given in this _[link - See#2]("http://www.ubuntu.com/desktop/get-ubuntu/download")_

4- [/SIZE][SIZE=3][SIZE=4]**Please make sure your USB-Drive is plugged in to one of your USB-Ports.**[/SIZE][/SIZE]
[SIZE=3]
5- Insert the LiveCD and Restart/Re-boot your machine.

6- Enter BIOS

7- Make sure that the [COLOR=Blue]**first device**[/COLOR] to boot from is the [COLOR=Red]**CD-ROM**[/COLOR]. See this [**_image_**]("http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126").
And make sure the [COLOR=Blue]**second boot device**[/COLOR] is the [COLOR=Sienna]**HDD**[/COLOR].
Please note that your BIOS may look different so it's better to refer back to your Motherboard's manual.

8- Now, make sure to change the ***[COLOR=Sienna]"Hard Disk Boot Priority"[/COLOR]***.
Please, don't be confused. This option is used to set which **[COLOR=Sienna]HDD [/COLOR]**will boot first. In this guide, the HDD as a **"boot device"**, will be the "**second** **device"** to boot up from and the **[COLOR=Red]CD-Drive[/COLOR]** will be the first. Please, try to understand that clearly.

As per this **_[image]("http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191")_**, the USB-Drive must be the first then your Internal HDD after that.
[COLOR=Red][B][SIZE=4][COLOR=Navy]USB-HDD0 is refer to the USB-Drive.[/COLOR][/SIZE]
[/B][/COLOR]

9- Save your new BIOS settings and Exit.

10- Once your machine will reboot, it should boot up from the LiveCD.

11- Press any key, select your language from the list and choose "**_[Try Ubuntu without installation]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132")_**".

12- Make sure you get to the GUI Desktop. You may have some problems to get the GUI Desktop. Either because of your Graphics Card or corrupted CD. *Perhaps later on we could discuss that.*

13- _[GParted]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7133")_.

14- Make sure to _[select your USB-Drive from GParted List]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7192")_. In this guide, it's **[COLOR=Navy]sdb[/COLOR]**. If you have another OS installed (XP is installed in this guide), please be careful not to select it by mistake and remove one of the partitions or format the whole drive.

15- Now, just follow these steps as per the images:

a) [_Right Click on sdb1 and choose "Delete"_]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7193")
Then, click on the GREEN TICK icon to apply the change.

b) You'll see unallocated space. _[Right click on that unallocated space and choose "New".]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7194")_

c) You'll see a new window. Choose "Primary Partition" and "ext4" as a file system and then decide the size of your partition. [_That's will be your root partition_]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7195"). Then Click "Add".

You need to read [[COLOR=Red]_**this guide**_[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition") to understand what I'm talking about, especially if you're new to Ubuntu.

d) A new partition will be created after that. Whatever left as unallocated space, please right click on that gray space and yet again _[choose "New"]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7196")_. 

e) Create your swap partition as per [_this image_]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7197"). Then Click "Add".

f) After that, all what you need to do is click "Apply", the green tick icon. You'll have then two partitions: **[COLOR=Navy]sdb1[/COLOR]** and [COLOR=Navy]**sdb2**[/COLOR].

16- At this point, you're done from creating the needed partitions for your installation of Ubuntu. You just need now to click "Install" from that icon on your desktop.

17- Kindly _[check this link out]("https://help.ubuntu.com/community/GraphicalInstall")_. It will guide you through the steps of installation one by one. However, [COLOR=DarkGreen]**[_step 4_]("https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4b.png") and _[step 8]("https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step6.png")_**[/COLOR] in the _[**[COLOR=DarkGreen]graphical installation guide[/COLOR]**]("https://help.ubuntu.com/community/GraphicalInstall")_ need your attention so I'm going to explain that in the next steps in this guide.

18- When you reach _**[Step 4]("https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4b.png")**_ in the [_Graphical Guide_]("https://help.ubuntu.com/community/GraphicalInstall"), you need to select the last options which is:
[B]Specify Partitions Manually (Advanced)
[/B]
19- By default, you should have a HDD and your USB-Drive that you want to install Ubuntu to. Thus, you'll see two entries or two HDDs, **[COLOR=Navy]sda [/COLOR]**and [COLOR=Navy]**sdb**[/COLOR]. 
[B][COLOR=Navy]
sda [/COLOR][/B]is your main internal **[COLOR=Sienna]HDD[/COLOR]**
**[COLOR=Navy]sdb [/COLOR]**is your **[COLOR=Blue]USB-Drive[/COLOR]**

Make sure you select the correct drive.

As per [**_this image_**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7198"), you need to select **[COLOR=Navy]/dev/sdb1[/COLOR]** which is the first partition in **[COLOR=Navy]sdb[/COLOR]** and that was the partition your created using GParted ***before*** you start the installation process.

20- Now, you need to **right click** on **[COLOR=Navy]/dev/sdb1[/COLOR]** and choose change.

21- A new [**_window will pop up_**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7199"). Please, set the following:

a) Use as > ext4
b) Format the partition > tick - means yes.
c) Mount Point > / - means this is the root partition.

Select OK in this window. Note that you don't have to change anything in [/SIZE][SIZE=3]**[COLOR=Navy]/dev/sdb2[/COLOR]** because this is the swap partition which you already created before using GParted. The installer will detect that partition so you don't need to do anything here.

Make sure you did all the required changes and click "Forward" in the main window.

22- Now, please may I have you attention here?
This is the most important step in the whole guide. Without this step, there is no point to do all this.

Once you reach step 8 (Ready to install) which is the final step, you'll see a list of all the changes you've made since the beginning of the installation process. 
In the bottom, you see "Advanced ..." right? okay, click on that one.

Now, you should see **_[a new window just like this one]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7200")_**. 
The title says: Advanced Options
Then it says: [_Boot loader_]("http://en.wikipedia.org/wiki/Booting")
Then a check box says: Install Boot Loader.
**[SIZE=4][COLOR=Red]>>>> [/COLOR][/SIZE][SIZE=4]MAKE SURE that option is ticked. Yes, we need to install the boot loader.[/SIZE]**

There's a list with this title: ***Device for boot loader installation.***

**[SIZE=4][COLOR=Red]ALL what you have to do is [COLOR=Black]>>>[/COLOR] select [COLOR=Navy]/dev/sdb[/COLOR].[/COLOR][/SIZE]**

And you're done. You now just need to click on "Install" and that is all.

What you just did was: you asked the installer to install Ubuntu Boot Loader ([_**GRUB2**_]("https://help.ubuntu.com/community/Grub2")) in the [**_MBR_**]("http://en.wikipedia.org/wiki/Master_boot_record") of the USB-Drive.

Why we need to do this?
Plain and simple.
a) You already have an OS installed before. Windows or any other OS, doesn't matter. We don't need to mess around with that OS.

b) By installing Ubuntu Boot Loader in the **[MBR ]("http://en.wikipedia.org/wiki/Master_boot_record")**of the USB-Drive, we grantee that the MBR of the internal HDD will keep doing the same old job which is boot the OS that is installed on the main internal HDD. We don't want to change anything. Remember, the whole point of this guide was to install Ubuntu without any changes to the HDD.
 
c) Also, by installing Ubuntu Boot Loader in the MBR of the USB-Drive, we created a bootable USB-Drive. Whenever you plug it to your machine, turn it on and set the BIOS settings to boot from that USB-Drive, you'll be able to boot up your machine and GRUB2 menu will show up. Then you can select whether to start Ubuntu or Windows (or any other OS you have installed already on your internal HDD).

What could be better than this? do you see how many benefits you can from that? 
1- You installed Ubuntu on an USB-Drive
2- You created a Bootable USB-Drive with a complete OS installed.
3- You will be able to choose which OS to boot into from a list.
4- You did not do any changes on your HDD.
5- If you unplug your USB-Drive, nothing wrong will happen and you'll still be able to boot into your OS which you have already installed.
6- You just learned the easiest way to install Ubuntu
7- You can now try Ubuntu and do whatever you want. Your System remain as it's. ALL what you need to do is:
Change the BIOS settings to make sure your System will boot up from the USB-Drive first.

What else do you want? :)

23- As shown in the Graphical Guide, you need to **[_restart_]("https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step8.png")**.
You need to take out the LiveCD but keep your USB-Drive plugged in, don't remove it.

24- Once done, [**_you should see something like this_**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7149").
If you have another OS rather than Windows, it should be listed there.

25. Congratulation. :D



I know it's a long guide but this guide has been created to help new comers to Ubuntu. If you already an Ubuntu's User, then you can use this guide to help you in installing Ubuntu to an USB-Drive if you don't know the steps for that.


**There are [_some other points_]("http://ubuntuforums.org/showpost.php?p=10271403&postcount=2") I'd like to highlight but I'll do it later on.**

Please, make sure to read each and every external link I have provided with this guide. I'm not making it harder for you but without the extra effort by you, you'll never learn to do it the right way. After all, it's you who will install and it's you who will do everything. The whole point is >>> you should know how to do it the right way ;)

ALL THE BEST and WELCOME TO UBUNTU :)

_[COLOR=Red]**Final word**[/COLOR]_: Let's **NOT **use Ubuntu in ***Windows-Way*** and YES, unquestionably, I mean Wubi ;)


[/SIZE]  [/LEFT]
[/CENTER]

---

### Post by amjjawad on 2010-12-23
[SIZE=3]Okay, as promised, there are still some **extra points** I'd like to highlight. I'm going to put that in a new post so you won't be confused. This is **EXTRA POINTS** and if you will not understand this part, don't panic, there's nothing wrong with you, you just need some time to be more familiar with this.

_[COLOR=Red]**Note that:**[/COLOR]_ [COLOR=Red]These points will NOT change anything. These are some facts and benefits you'll gain from installing Ubuntu on an USB-Drive.[/COLOR]


[/SIZE][SIZE=4][U][B]Point1
[/B][/U][/SIZE][SIZE=3]The USB Drive that I have used in this guide to install Ubutnu was a 4GB USB Drive. 1GB of Free Space left.
In case someone is wondering how much is the minimum size of installing Ubuntu? then I guess you already know the answer by now.

The Swap Partition was 512MB and the rest for Ubuntu.

Definitely, DO NOT go for this kind of installation IF you're willing to use Ubuntu on a daily basis. 1GB Free Space is nothing nowadays. I'm just saying that: "Yes, Ubuntu can be installed on 4GB USB Drive".

By the way, I have installed Ubuntu 10.4


[U][B][SIZE=4]Point2[/SIZE]
[/B][/U]The USB Drive after the installation can be used as a rescue disk to boot up your machine just in case something wrong will happen. Just like the LiveCD. 

[SIZE=4][U][B]Point3
[/B][/U][/SIZE]And because Ubuntu 10.04 has GRUB2 and because GRUB2 is an amazing boot loader that I like so much, with one single command, you'll be able to boot any other OS installed just in case something will go wrong.

HOWTO DO THAT?

1 ) Plug your USB to your Machine.
2 ) Reboot
3 ) Enter BIOS
4 ) Make sure your machine will boot from CD-ROM first THEN from USB Drive (USB-HDD). You need to update the settings manually.
5 ) Save and Exit
6 ) Your System will boot from the USB and will login to Ubuntu.
7 ) From Terminal, run this command:

[/SIZE]```
sudo update-grub

```[SIZE=3]

8 ) Done.
9 ) Reboot your machine again and a list of all your Operating Systems will be available, just pick whatever OS you want to login to.

Can't find more now ;)
[/SIZE]

---

### Post by C.S.Cameron on 2010-12-23
Is this for 10.10?
The instructions seem like they are for 10.04.

> 
22- Now, please may I have you attention here?
This is the most important step in the whole guide. Without this step, there is no point to do all this.

Once you reach step 8 (Ready to install) which is the final step, you'll see a list of all the changes you've made since the beginning of the installation process.
In the bottom, you see "Advanced ..." right? okay, click on that one.

Now, you should see a new window just like this one.
The title says: Advanced Options
Then it says: Boot loader
Then a check box says: Install Boot Loader.

---

### Post by amjjawad on 2010-12-23
> **C.S.Cameron said:**
> Is this for 10.10?
The instructions seem like they are for 10.04.

10.04 - check the 2nd post :)

Okay, I edited the main post.

---

### Post by presence1960 on 2010-12-27
Pretty good work! I personally do not like wubi, however I refrain from telling others whether or not they should use wubi. The only advice I offer is that should one have problems with wubi it is much more difficult to get help with wubi since most of us do not use it. I also offer this [link]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/"), which if you read down the main developer states that wubi is not meant to be a permanent install but rather a test drive before installing a true dedicated ubuntu on a HDD.

---

### Post by Rubi1200 on 2010-12-27
> **presence1960 said:**
> The only advice I offer is that should one have problems with wubi it is much more difficult to get help with wubi since most of us do not use it.
True and not true.

There is now somewhere for both Wubi users and forum regulars to turn to for help with Wubi installs.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by amjjawad on 2010-12-27
> **presence1960 said:**
> Pretty good work!

Appreciate that :)

> I personally do not like wubi, however I refrain from telling others whether or not they should use wubi. The only advice I offer is that should one have problems with wubi it is much more difficult to get help with wubi since most of us do not use it. I also offer this [link]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/"), which 
I'm sure you read this paragraph:

> [I][SIZE=3]Now, this is my own personal opinion about Wubi that you  may disagree with it which is fine with me but keep in mind that I'm  writing this guide for a reason. I'm trying to save your time and offer a  better choice for you.

Unlike what some may think about Wubi, I think it's a problematic choice  more than a helpful one. Again, this is my own personal opinion.
Lots of users faced many troubles with Wubi. This guide should offer a better choice for you.[/SIZE]
[/I]I see many threads on daily basis. Users upgraded, others installed Wine in Wubi just to avoid switching between Windows and Ubuntu (which is not a real dual-boot to begin with) and lots of other stuff we both know :)
I wrote this guide for purely new users to Ubuntu. I'm doing my best to show them the path that will save their time for their own good. That's all.

> if you read down the main developer states that **wubi is not meant to be a _permanent install_ but rather a test drive before installing a true dedicated ubuntu on a HDD**.That's another reason why I wrote this guide ;)
Most of the users who are using Wubi do not know that fact.

Thank you :)

---

### Post by amjjawad on 2010-12-27
> **Rubi1200 said:**
> True and not true.
 
 There is now somewhere for both Wubi users and forum regulars to turn to for help with Wubi installs.
 [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I was waiting for you to post your link here ;)

---

### Post by amjjawad on 2010-12-27
Sorry, because of my bad internet connection, Firefox made 3 posts instead of one.

---

### Post by Rubi1200 on 2010-12-27
> **amjjawad said:**
> I was waiting for you to post your link here ;)
Note that I also linked to the interview with Agostino Russo about Wubi installs in my thread.

Personally, I would rather see people using Ubuntu on a dedicated partition.

But, since there is Wubi I also think it is our duty to help those users as best we can.

Many of them eventually install Ubuntu on the hard-drive too thanks to the wubi migration thread put together by bcbc.

---

### Post by amjjawad on 2010-12-27
> **Rubi1200 said:**
> Note that I also linked to the interview with Agostino Russo about Wubi installs in my thread.

Personally, I would rather see people using Ubuntu on a dedicated partition.

But, since there is Wubi I also think it is our duty to help those users as best we can.

Many of them eventually install Ubuntu on the hard-drive too thanks to the wubi migration thread put together by bcbc.

I don't know anything about that interview until I saw the link here.

Everyone here is trying to help. Everyone has his/her own style.
I do have a personal opinion about Wubi but that has nothing to do with writing this guide. As I keep mentioning, I did this to help new comers.
It's their call to take Wubi's Route or not.
Also, it's kind of 2 in 1 guide.

Now, you posted your link. I guess the picture is complete.

---

### Post by presence1960 on 2010-12-27
> **Rubi1200 said:**
> True and not true.

There is now somewhere for both Wubi users and forum regulars to turn to for help with Wubi installs.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Thanks for the link. I will try to make use of it. Since I do not use wubi (I did try it for a while to gain some experience) I am hard pressed to help those who post about problems with wubi.

---

### Post by Rubi1200 on 2010-12-27
> **presence1960 said:**
> Thanks for the link. I will try to make use of it. Since I do not use wubi (I did try it for a while to gain some experience) I am hard pressed to help those who post about problems with wubi.
You are more than welcome :)

I also do not use Wubi (or Windows for that matter), but I saw so many posts from people experiencing problems that I decided to put something together.

Apparently, it has helped already judging by the number of views as well as responses I have received by PM.

---

### Post by h4ckluserr on 2011-01-03
I went the WUBI route.  Let me describe why.  This is my own **_personal_** experience.

Being a gamer, I am primarily on Windows.  However, I have a USB drive which I carry an ubuntu install, a couple of my primary games, and a couple other windows registry free games that I can transport.  all of which run under WINE.  This is great when I boot into my personal computer(windows 7) and can run everything I need.. and then when I travel to a seperate work site, I carry one laptop, and just boot into Ubuntu when I want my own setup/games/applications/tools.  I can't go Linux full time due to having incompatibility with games.  WINE is awesome, but one update to WoW that causes incompatibility and my primary game is down. :(

I have run into a seperate issue.  my linux partition(WUBI albeit) is 30gb.  I can't seem to get the other 270GB to mount since I updated to 10.10. it's weird.  I think this setup is going to be my solution.  by creating a third partition that will be Fat32.

---

### Post by Sail323 on 2011-01-03
Your guide was very helpful.  I'm posting this from my new 4GB USB flash drive installation of Ubuntu 10.04 LTS.

I have a 80GB hard drive in a SATA/ USB 2.0 enclosure.  Will the same process work with this drive?  Can I put the bootloader on this drive and boot from it as I do from the USB flash drive?

---

### Post by amjjawad on 2011-01-03
> **Sail323 said:**
> Your guide was very helpful.  I'm posting this from my new 4GB USB flash drive installation of Ubuntu 10.04 LTS.

Thank you and I'm glad you have installed Ubuntu on an USB Drive :)

> I have a 80GB hard drive in a SATA/ USB 2.0 enclosure.  Will the same process work with this drive?  Can I put the bootloader on this drive and boot from it as I do from the USB flash drive?Yes, you can follow exactly the same process. Nothing will change except for the space. I mean, you have 80GB instead of 4GB.
I've done that before with a 20GB IDE HDD. I think it was my Samsung IDE HDD.

As for the boot loader, in this guide, I'm trying to avoid installing it in the MBR of the main HDD. Why? because in this guide, I'm not trying to do any changes to the main HDD.
In other cases, mostly GRUB will be installed in the MBR of the main HDD.
It depends on what you want. If this is a temp installation (same as this guide) then GRUB2 should be installed in the MBR of the USB Drive NOT the internal Main HDD.
If this is an installation that you'll keep for ... say 6 months then you could install in the MBR of the main HDD "or" in the MBR of the USB Drive. Your call :)

---

### Post by h4ckluserr on 2011-01-03
This guide confirmed my theory and worked perfectly.  I'm currently sitting on a seagate 320gb drive.  Broken up as shown.  Making one change to support my personal needs of this drive.

30GB -> ext4
4GB -> Swap(overkill I know.. but I'd rather have to much than to little)
the rest -> FAT32

Other than that, following these directions line for line worked.

Also, there is only one modification for 10.10(if you so wish to add/modify your original post).  In Step4 you get a direct drop down to pick where to load your bootloader.  it's still "/dev/sdb"  and you do not pick which loader, it just goes with GRUB2.

Fantastic write up, thank you.

---

### Post by amjjawad on 2011-01-04
> **h4ckluserr said:**
> This guide confirmed my theory and worked perfectly.  I'm currently sitting on a seagate 320gb drive.  Broken up as shown.  Making one change to support my personal needs of this drive.

30GB -> ext4
4GB -> Swap(overkill I know.. but I'd rather have to much than to little)
the rest -> FAT32

Other than that, following these directions line for line worked.

Glad to know it worked for you :)

> Also, there is only one modification for 10.10(if you so wish to add/modify your original post).  In Step4 you get a direct drop down to pick where to load your bootloader.  it's still "/dev/sdb"  and you do not pick which loader, it just goes with GRUB2.

Yes, I'm aware of that and thanks a lot for the reminder :)
I'm trying to focus on [10.04 because it's LTS]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#History_and_development_process") (Long Term Support) in all my guides so far. I might update that in the near future or just add a link or an image to show that.

> Fantastic write up, thank you.
Appreciate that, thanks a lot :)

---

### Post by Mamacia on 2011-02-18
Newbie here.  Looking forward to using Ubutnu 10.10 and would like to do this install.  However am not getting any images on Windows 7.  Am I the only one?

---

### Post by Mamacia on 2011-02-18
Me again.  I am one of the unfortunates with a black screen at startup wishing to use your USB method to run Ubutnu.  I have found a resolution to the problem, but it begins "At the install screen ..."  I have yet to see the install screen.

In my attempts to install Ubutnu 10.10, I have gotten as far as setting BIOS, step 6 in your tutorial, but have not seen the GUI Desktop you refer to in step 12.

Here is what I have found to "cure" black screen (edited by me.)  Wondering how this would fit into your USB install:  (OR perhaps you know a different way?
**[SIZE=1]Ubuntu 10.04 “Lucid” Blank Screen at Startup : Workaround[/SIZE]**

 [SIZE=1]There have been a number of reports regarding blank screens at startup pre and post installation on the new Ubuntu 10.04 “Lucid” release. It seems there are some** incompatibilities with some video drivers, particularly (not surprising) some ATI **and nVidia. Also in the mix are some older Intel cards. This post outlines a workaround you can try in order to get your video working properly again.[/SIZE]
 [SIZE=1]**[FONT=Corbel, sans-serif]Booting from CD:  [/FONT]**[/SIZE][FONT=Corbel, sans-serif][SIZE=1]This section outlines how to workaround the video issue while booting from the CD. Your mileage may vary, depending on your video card, but hopefully this steers you in the right direction:[/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Corbel, sans-serif][SIZE=1]At 	the install screen press ‘[/SIZE][/FONT][SIZE=1]*[FONT=Corbel, sans-serif]F6[/FONT]*[/SIZE][FONT=Corbel, sans-serif][SIZE=1]‘ 	and insert [/SIZE][/FONT][FONT=Corbel, sans-serif][SIZE=1][/SIZE][/FONT][SIZE=1]*[FONT=Corbel, sans-serif]**xforcevesa 	 **[/FONT]*[/SIZE] 	
[*][FONT=Corbel, sans-serif][SIZE=1]On 	first boot after install, press [/SIZE][/FONT][SIZE=1]*[FONT=Corbel, sans-serif]e[/FONT]*[/SIZE][FONT=Corbel, sans-serif][SIZE=1] 	to edit the GRUB menu.[/SIZE][/FONT]
[*][FONT=Corbel, sans-serif][SIZE=1]Using 	the arrow keys to navigate, delete [/SIZE][/FONT][SIZE=1]**[FONT=Corbel, sans-serif]quiet[/FONT]**[/SIZE][FONT=Corbel, sans-serif][SIZE=1] 	and [/SIZE][/FONT][SIZE=1]**[FONT=Corbel, sans-serif]splash[/FONT]**[/SIZE][FONT=Corbel, sans-serif][SIZE=1] 	and again insert [/SIZE][/FONT][FONT=Corbel, sans-serif][SIZE=1][/SIZE][/FONT][SIZE=1]*[FONT=Corbel, sans-serif]**xforcevesa 	**[/FONT]*[/SIZE][FONT=Corbel, sans-serif][SIZE=1] 	[/SIZE][/FONT] 	
[*][FONT=Corbel, sans-serif][SIZE=1]Press [/SIZE][/FONT][SIZE=1]**[FONT=Corbel, sans-serif]Ctrl[/FONT]**[/SIZE][FONT=Corbel, sans-serif][SIZE=1] 	and [/SIZE][/FONT][SIZE=1]**[FONT=Corbel, sans-serif]X[/FONT]**[/SIZE][FONT=Corbel, sans-serif][SIZE=1] 	to boot.[/SIZE][/FONT]
[/LIST]
 [FONT=Corbel, sans-serif][SIZE=1]The suggested **options** that I have found **are hardware specific.** Here is a list:[/SIZE][/FONT]
 
[LIST]
[*][FONT=Corbel, sans-serif][SIZE=1]Older 	Intel video card: [/SIZE][/FONT][SIZE=1]*[FONT=Corbel, sans-serif]i915.modeset=1[/FONT]*[/SIZE][FONT=Corbel, sans-serif][SIZE=1] 	or i915.modeset=0[/SIZE][/FONT]
[*][FONT=Corbel, sans-serif][SIZE=1]nVidia: 	[/SIZE][/FONT][SIZE=1]*[FONT=Corbel, sans-serif]nomodeset[/FONT]*[/SIZE]
[*][FONT=Corbel, sans-serif][SIZE=1]**Generic: 	**[/SIZE][/FONT][SIZE=1]*[FONT=Corbel, sans-serif]**xforcevesa**[/FONT]*[/SIZE]
[/LIST]
 [FONT=Corbel, sans-serif][SIZE=1]Hopefully one of these options will get you up and running. Keep reading now to make these changes persistent![/SIZE][/FONT]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]**[FONT=Corbel, sans-serif]GRUB:  [/FONT]**[/SIZE][FONT=Corbel, sans-serif][SIZE=1]You’ll want to change these settings in GRUB so they’ll automatically be applied on each reboot. To do so, follow the steps below:[/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Corbel, sans-serif][SIZE=1]Edit 	the [/SIZE][/FONT][SIZE=1]*[FONT=Corbel, sans-serif]/etc/default/grub[/FONT]*[/SIZE][FONT=Corbel, sans-serif][SIZE=1] 	file. You will need Admin privileges to do so (sudo)[/SIZE][/FONT]
[*][FONT=Corbel, sans-serif][SIZE=1]Find 	this line: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”[/SIZE][/FONT]
[*][FONT=Corbel, sans-serif][SIZE=1]Replace 	with: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash ***xforcevesa***”[/SIZE][/FONT]
[/LIST]
 [FONT=Corbel, sans-serif][SIZE=1]For example, if I had an older Intel model, my GRUB configuration would read:[/SIZE][/FONT]
 [INDENT][FONT=Corbel, sans-serif][SIZE=1]GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash i915.modeset=1&#8243;[/SIZE][/FONT][/INDENT] [FONT=Corbel, sans-serif][SIZE=1]Save your changes and you should get proper graphics on each reboot.[/SIZE][/FONT]
 [SIZE=1]*[FONT=Corbel, sans-serif]UPDATE: Based on a lot of user feedback I am reminded that you need to r[/FONT]**[FONT=Corbel, sans-serif]**un ‘update-grub’ after you make changes**[/FONT]**[FONT=Corbel, sans-serif].[/FONT]*[/SIZE]
 [SIZE=1]
[/SIZE] 
 Thanks much in advance for any help you can offer.  I am really looking forward to be able to use Ubutnu.

I've got Windows 7

---

### Post by astrob0t on 2011-04-17
hi ..

just wondering whether its possible to install ubuntu in an internal hdd but install the GRUB2 loader on an external usb flash..

i just dont want to mess up the oem partition given in my laptop..

any ideas??

---

### Post by amjjawad on 2011-07-22
> **aviatsit said:**
> hi ..

just wondering whether its possible to install ubuntu in an internal hdd but install the GRUB2 loader on an external usb flash..

i just dont want to mess up the oem partition given in my laptop..

any ideas??

My apology for being too late to reply this.

**[GRUB2 Files]("https://help.ubuntu.com/community/Grub2#File%20Structure")** will be stored in the root partition and that will be where you choose to install Ubuntu (Internal HDD, USB, etc). Only part of GRUB2 will be stored in the MBR. Having that said, I see no point to do that :)

If something will go wrong, you can always fix the MBR either with Windows Disc or Ubuntu LiveCD.

Not to mention that GRUB2, IMHO, is one of the best Boot-Loaders I have ever seen. I haven't got any problem with it until now. It doesn't mean it's perfect - nothing is prefect - but it means there are tons of guide and howto to deal with GRUB2. 

I know it's a late reply but this reply will help anyone else who may have the same Q :)


[B]Edit:
[/B]The main idea behind this guide is how to install Ubuntu on an external media instead of installing it on the internal HDD. As long as Ubuntu and it's boot loader is NOT installed in the internal HDD, everything will remain untouched on the internal HDD.

Check the aim of this guide ;)

---

### Post by x-D on 2011-08-10
Remind me again, why it is recommended to check the MD5SUM against the Ubuntu hashes?

:guitar:

---

### Post by amjjawad on 2011-08-10
> **x-D said:**
> Remind me again, why it is recommended to check the MD5SUM against the Ubuntu hashes?

:guitar:

Please, edit your post and remove "QUOTE" as the post is so long :(

About MD5SUM, please check this link:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Your answer should be there.

---

### Post by fredcm3 on 2011-10-20
OK.  I've got 11.10 on a USB stick.  I can select it from the computer's boot menu and it works!
Well ... it works except the Startup-Manager doesn't run!!  

I wanted to use Startup-Manager to get the USB-based GRUB2 to default to a hard drive-resident  OS.
But, I don't know how to do that and could use some pointers.

I guess I won't be using Startup-Manager unless I can run it from the hard drive Ubuntu install and point it at the USB GRUB2 files.

I guess I could edit GRUB2 files on the USB manually with a text editor, eh?
But then I have to figure out what the GRUB2 boot will see as hard drive installs.
sda1 ???  Ubuntu is in the first partition of the one and only hard drive.

I'm such a noob with Ubuntu/Linux that I really could use some help!

---

### Post by amjjawad on 2011-10-20
> **fredcm3 said:**
> OK.  I've got 11.10 on a USB stick.  I can select it from the computer's boot menu and it works!
Well ... it works except the Startup-Manager doesn't run!!  

I wanted to use Startup-Manager to get the USB-based GRUB2 to default to a hard drive-resident  OS.
But, I don't know how to do that and could use some pointers.

I guess I won't be using Startup-Manager unless I can run it from the hard drive Ubuntu install and point it at the USB GRUB2 files.

I guess I could edit GRUB2 files on the USB manually with a text editor, eh?
But then I have to figure out what the GRUB2 boot will see as hard drive installs.
sda1 ???  Ubuntu is in the first partition of the one and only hard drive.

I'm such a noob with Ubuntu/Linux that I really could use some help!

I promise to read your post again but I don't understand what are you trying to achieve here?
You need to keep in mind that the whole idea/concept of having Ubuntu (or any of its variant) installed to an USB-Drive is ... well, I already explained that in page 1 :)

---

### Post by amjjawad on 2011-10-22
> **rajesh.kalapura said:**
> Thanks amjjawad for the post.A nice how-to........

You most welcome. Thanks for your nice words :)
Glad to help and support this community :)

---

### Post by mohamedtoma73 on 2011-11-09
wubi installation is a  temporary installation to see if ubuntu is compatible  with the hardware and see the improvements and feature of a new ubuntu installation. i have a usb key and i need it for putting restored herensbootcd 14 which have riplinux image booting in addition to other features of herensbootcd

---

### Post by amjjawad on 2011-11-10
> **mohamedtoma73 said:**
> wubi installation is a  temporary installation to see if ubuntu is compatible  with the hardware and see the improvements and feature of a new ubuntu installation. i have a usb key and i need it for putting restored herensbootcd 14 which have riplinux image booting in addition to other features of herensbootcd

I'm sure if you'll read the first post on this thread, you'll understand why this guide has been created :)

Yes, Wubi might be helpful but problematic too. There are many other ways to do what you stated. LiveCD, LiveUSB, installing on Virtual Machine, Installing on USB Drive, Installing on USB External HDD and Installation on Test-Machines ... that all in case one doesn't want to install it on the internal HDD :)

---

### Post by davidc60 on 2011-11-10
*Hi Amjjawad,*
[I][B][U]Re: Your Article: [I]How to Avoid Wubi & Install Ubuntu on USB Drive
[/I][/U][/B]I have recently installed Ubuntu 11.10 on to a USB drive based on your excellent description in December 2010 about 'how to avoid Wubi'. (Everything seems to be working as it probably should). 
What I am wondering now is that as the Bootloader is located in the MBR (ie. sdb) on the USB is it possible to install a second operating system (eg. Fedora 16 desktop) **on to the same USB **(subject to the USB being big enough) so that when the Grub2 menu appears it may be possible to choose between Ubuntu (from the USB), Windows (from the HDD) and, say, Fedora (from the same USB)? 
(At the moment I have put Fedora 16 on to a second USB - I am simply trying out both Ubuntu and Fedora for the first time to see which one I will stick with for the future but it would help if I could choose them from the same USB rather than needing 2 USB's).
davidc[/I]

---

### Post by amjjawad on 2011-11-10
> **davidc60 said:**
> *Hi Amjjawad,*
[I][B][U]Re: Your Article: [I]How to Avoid Wubi & Install Ubuntu on USB Drive
[/I][/U][/B]I have recently installed Ubuntu 11.10 on to a USB drive based on your excellent description in December 2010 about 'how to avoid Wubi'. (Everything seems to be working as it probably should). 
What I am wondering now is that as the Bootloader is located in the MBR (ie. sdb) on the USB is it possible to install a second operating system (eg. Fedora 16 desktop) **on to the same USB **(subject to the USB being big enough) so that when the Grub2 menu appears it may be possible to choose between Ubuntu (from the USB), Windows (from the HDD) and, say, Fedora (from the same USB)? 
(At the moment I have put Fedora 16 on to a second USB - I am simply trying out both Ubuntu and Fedora for the first time to see which one I will stick with for the future but it would help if I could choose them from the same USB rather than needing 2 USB's).
davidc[/I]

Hi there :)

Thanks for your nice word and for your post.

Yes, you can and it's really great idea to do that.
I haven't tested Fedora 16 yet and not sure what they have done with the option whether to install or not to install the bootloader? Fedora, unlike Ubuntu and its variant, gives you an option to install its bootloader to the MBR or NOT to install it at all. With Ubuntu and its variant, if you won't install the bootloader to the MBR then you must install the bootloader to the same partition where you have installed your system on.

Fedora 16 now uses GRUB2 (finally) and I need to test that.
Anyway, whether Fedora still have the same previous options, just make sure not to install its bootloader to the MBR of your USB.

After Fedora's installation is done, reboot, login to Ubuntu and run "sudo update-grub" and that should do the job.

Sadly, I don't have large size USB Drive to test that. Theoretically, that should work.

Please let me know if you need more assistance :)

---

### Post by bogan on 2012-02-08
Hi!, **amijawad**,
 
I have just completed  the full installation and update of Ubuntu 11.10 to 3.0.0-15, using your brilliant HowTo. More than 320 updated packages. It takes up 3.13GiB so even if there was a Swap file of only 512 MB, it would be very tight on a 4GB USB drive.
 
I used an 8GB USB with  4.4GB partition for Linux, – as recommended as an “At Least” in the 11.10 installation instructions –  a 2GB Swap File and a 1GB Switch file, Fat32, so I can easily transfer data or program files across platforms, without problems, or risk of confusing 'filesystems'.
 
I undertook the exercise mainly to be able to know what I was about when advising an OP who was having problems:
[http://ubuntuforums.org/showthread.php?t=1919286&highlight=installing](http://ubuntuforums.org/showthread.php?t=1919286&highlight=installing)
But it is good to have full backup bootable disk that I know will have the right drivers for both WiFi and Video, rather than the minimale Boot disk made by Startup Disk Creator.
 
I am Posting this to say thank-you, and to suggest that you might want to make a few additions to cover differences in the layout of the 11.10 Installation app in a LiveCD/USB.
 
Please do not take this as criticism, it is that I still remember the difficulties I had with making sense  of  instructions which did not match the display in front of me; it can be very anxiety-provoking for a Newbie groping in the dark with a non-standard set-up.
 
For instance, if you do not put something in the boot mount box, you get a message to go back to the Partition Menu and put one in; but going back there is nothing resembling a Menu, in the 11.10 version, you have to Click on the 'Change' button to enter the change page.
 
First: your stage 8 para, I found very ambiguous, as it sys “ the CD-DRIVE will be first”, and then says  “the USB-Drive must be first and then the Internal HDD after that”.
 
Second: Stage 20 “[SIZE=3]Now, you need to [/SIZE][SIZE=3]**right click**[/SIZE][SIZE=3] on [/SIZE][COLOR=#000080][SIZE=3]**/dev/sdb1**[/SIZE][/COLOR][SIZE=3] and choose change[/SIZE]“.  This is no longer the case. You select – Left-Click -  on the chosen entry and select the 'Change' Button below. Right-Click does nothing.
 
Third: Stage [SIZE=3]22-” Now, please may I have you attention here?
This is the most important step in the whole guide.[/SIZE] …....[SIZE=3]In the bottom, you see "Advanced ..." right? okay, click on that one.[/SIZE]“ This and the para that follows is not so either, there is a Boot Loader Box below on the same page, titled as you state, with a drop-down list. The list of actions is visible below, but  no Advanced option nor extra page.  
 
Minor point: the 'Install' button actually says “Install Now”.
 
25 Stage: and Congratulations to you too, for producing a very valuable HowTo !!

Chao!, **bogan**

---

### Post by ytkuser12 on 2012-05-20
hi there i have a 1 terabit hard drive that i use for back ups and stuff for windows. i was wondering is there a whey to install ubuntu to it and also keep it as my back up drive for windows as well?. i want to try out ubuntu the right whey. thanks for all the help you can offer and god bless.

---

### Post by wilee-nilee on 2012-05-20
> **ytkuser12 said:**
> hi there i have a 1 terabit hard drive that i use for back ups and stuff for windows. i was wondering is there a whey to install ubuntu to it and also keep it as my back up drive for windows as well?. i want to try out ubuntu the right whey. thanks for all the help you can offer and god bless.

If you put a ext type partition needed for ubuntu at the front of the drive windows will not be able to read it or the rest of the drive. It would have to be at the end of the drive if it is a ntfs now.

---

### Post by ytkuser12 on 2012-05-20
forgive me if i sound dumb but i'm all new to this partition stuff how to do this? is there a quid for how to partition a drive and install for back of drive?. or should i just use wubi in my situation?. i want to get the full use out of it like install native video card drivers for ubuntu and stuff. i'm afraid if i use wubi i wont be able to do that.

---

### Post by wilee-nilee on 2012-05-20
> **ytkuser12 said:**
> forgive me if i sound dumb but i'm all new to this partition stuff how to do this? is there a quid for how to partition a drive and install for back of drive?. or should i just use wubi in my situation?. i want to get the full use out of it like install native video card drivers for ubuntu and stuff. i'm afraid if i use wubi i wont be able to do that.

I would not use a backup drive for a install, that’s me personally, I could with no problems, but from your description I would not recommend it for you.

All the same hardware is used in wubi, it is just a file in windows rather then in a partition. Good way to check it out though, and the wubi can be moved to a partition once you feel you want that and feel confident in doing partitioning.

There is a thread on the forum for transferring wubi's as well.

The right way would be just a partitioned install to the internal HD, or at least more common.

Really if you want to do anything hear start a thread of your own. It will be easier for people to help. :)

---

### Post by tolbert on 2012-10-10
Hi, everyone.

I'm new to Ubuntu and new to these forums.  I know that this is a pretty old thread, but I have a question about the partitions described in this installation process, and I 'm hoping someone can help me out.  

I've been trying out Ubuntu from the Live CD and I love it, but I need to keep Windows (sadly) to run some of the software that I need.  I'd like to run Ubuntu from a persistent USB drive so I can have the awesome-ness that is Ubuntu without screwing with my Windows OS.  I searched around, and this seems to be one of the best, most clearly written set of instructions online on how to do what I'm trying to do.  But there's just one thing I don't understand.  I'm a total newbie to working with partitions.  I do understand that I make an ext4 primary partition on my USB drive to serve as my root partition, which will hold the Ubuntu OS files.  I also have read about swap partitions and understand that I need to make one.  However, I have seen other instructions online that say to create a third partition to save things in (downloaded applications, created files, whatever).  With the method described in this thread, with just two partitions created on the USB drive, where do things get saved?  In the root directory along with the OS files?  Or do I need another partition if I want to save all my Ubuntu-related files to the USB drive? If so, how do I make this partition?  I've seen several comments mentioning a third partition that is FAT32 file system.  Is this what I need?

Thanks!!!
tolbert

---

