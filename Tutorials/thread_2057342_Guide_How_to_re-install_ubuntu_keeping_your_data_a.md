---
title: "Guide How to re-install ubuntu keeping your data and settings"
date: 2012-09-13
forum: Tutorials
---

### Post by Ace..... on 2012-09-13
[B][COLOR=#800000]_[SIZE=6]How to re-install Ubuntu keeping your data and settings[/SIZE]_[/COLOR]

YannBuntu pointed me to this doc[/B]

[COLOR=Navy][https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)[/COLOR]

It was a revelation.
Authored by YannBuntu it was great, and highly understandable for those who are quite conversant with Ubuntu fixing.
 
I've written this guide, with the more noobish in mind, particularly because the re-installation was so much easier than trying to fix my system (which we anyway failed to do).

**Note:** 
- Bob_Briscoe has provided additional instructions, in the event your system fails to boot. [Here!]("http://ubuntuforums.org/showthread.php?t=2057342&p=13319348#post13319348")
- Any specific system issues preventing re-installation, should be addressed to the relevant forum.

[SIZE=4][B][COLOR=#800000][SIZE=5]_You have a reason to re-install Ubuntu_[/SIZE][/COLOR]
[/B][/SIZE]
It could be because it is clearly no longer working correctly, or you have noticed that it's performance has diminished.

The good news is that you can re-install ubuntu very easily without overwriting your data and settings.
So easily that in fact, it may be the first thing that you do, when trying to rectify any problem that you might have.

You will still need to re-install any downloaded apps, but this is very quick, and when you launch them, they are just as before. Eg. Google-chrome..... had to be re-installed, but on launch all my bookmarks were as before.

However, the main point is:

After around 4 days intensive effort to try to fix my broken ubuntu - I spent only 2hr re-installing it and some apps, and ubuntu was back in operation and running very fast again.

Ok... there was a little bit of prep, but that's a one off.
Once you're sorted for bakups (as you should be anyway) you can re-install whenever you wish.

Here is how you do it, first in brief, and then a fuller explanation:

[SIZE=3]**Brief**[/SIZE]

[LIST=1]
[*] Create a list of your log in name, user name, and pcname (Password must be the same)
[*] Create a back up of 'home'
[*] Boot from install disk, choose 'something else, Dclick on your '/' partition, choose a file system, choose '/' as your mount (do not format)
[*] Enter your names and password (same as before), choose to update during install etc.
[*] Reboot, install updates, install any apps you regularly use that are missing, reboot.
[/LIST]

[SIZE=3][B][SIZE=3]Full Explanation[/SIZE]
[/B][/SIZE]
[SIZE=5][COLOR=#800000]**1. Create a list of your 3 log in names - get these wrong and you lose your data.**[/COLOR][/SIZE][INDENT][B]
a)[/B]  Take note of the 'name' above your password (log in screen) - you must enter exactly the same during ubuntu install, in the field asking for your name.

**b)**  At desktop press ctrl+Alt+T and type ```
gksudo nautilus
``` to launch file manager. You'll be asked for your ubuntu login password. type it (nothing displays) press enter.
In Nautilus, dclick on 'File System' on the left, and on the right look for 'home'.
Dclick on 'home' and you will see your username under the icon - Take note of that for use during install.

**c)**  If you close Nautilus - in the terminal you'll see ```
username@anothername:~$
```
anothername is the name of your pc.
This is the 3rd name required at install.


[/INDENT]
[I]**Note:** If you had originally let 'ubuntu install' do its own thing, you would have entered your first Name and Surname, and ubuntu would have auto filled user name, without a capital letter, and would have merged this with the name of your pc (pulled from the bios or wherever).
So for me, I took care to note all these names, yet on re-install, I entered my first and surname, and all the rest auto filled in correctly.

[/I][INDENT]**d) ** press ctrl+Alt+T and type ```
gedit
```
Type or copy and paste the **3 names** into the text editor, and save as '**ubuntu re-install info**' (_add this guide and other resource links below, before printing_).[/INDENT]
[INDENT](By the way..... at re-install, you MUST use the same password that you normally use)[/INDENT]

That's the first mission critical step done **ie. you have taken note of your 3 login names.**

[SIZE=5][COLOR=#800000]**2. Create a back up of the directory called 'home' (see 1. b) above)**[/COLOR][/SIZE]

[I]**Note:** you can backup this directory how you want: cloud, different partition, external drive OR not at all if your data has no value to you. The backup is done in case something goes wrong, like a power cut etc.

[/I][INDENT]**Repeat 1. b) above** and Rclick on 'home' and choose 'properties'.
Take note of how much disk space is being used.[/INDENT]

[I]Let's say it's 15Gb (cos you have loads of photos etc.)
You are gonna need a storage device with that much space available and more.
(I used the hard drive from my last laptop, slipped into a case with a usb cable - cost only 15&#8364;)
[/I][INDENT][B]
Repeat 1. b) above[/B] but now on the left look under the title 'Devices'.[/INDENT]
[INDENT][I]For me I see 'System Reserved', Win7, Home_Data (where I keep my data), 16Gb Filesystem (old data I have kept)

[/I][/INDENT]
[INDENT]**RClick on the usb hard drive icon** (the icon should show the usb cactus sign) and choose properties.
This will display the free space.

**Delete all the un-needed programs & files**, to create the space you need.[/INDENT]
[INDENT]You could format the drive, using say 'gparted' or 'disk utility'
[use either disk utility to examine your pc hard drive so that you know where your ubuntu '/' partition is (you need to know this during install)]

**Click top right corner of desktop and choose system settings, backup**. 
Configure it to back up to your usb drive (or wherever), and make the backup.
*Backing up say 15Gb of data takes time, for me it was around 30min (I guess) but it looks after itself.*[/INDENT]

[SIZE=5][COLOR=#800000]**3. Install ubuntu from your install disk (or first download and burn a new disk)**[/COLOR][/SIZE][INDENT][B]
Insert your disk[/B] and cancel any autoplay dialogue.

**Re-start your pc, and enter your bios** (for me I press F2 at start of boot).
**Find the section** that lists the boot order, check the top of the list is cd/dvd drive (or move it to the top), save & exit

**The pc will then boot** to 'try ubuntu' or 'install' - **choose install, then choose 'do something else'.**[/INDENT]
[INDENT][I](At this point you will need to know which is your ubuntu '/' partition - see the screen shot below - mine is 2nd from the right, the farthest right is the /swap partition.)

[/I][/INDENT]
[INDENT][B]So you are now looking at a graphic of your hard disk partitions.
[/B][/INDENT]
[INDENT]**Dclick on the one holding your ubuntu data,** and in the next box that appears, choose** 'use as' 'ext4 journaling file system', mount point '/'**, ok.
You'll return to the graphic of your hard disk partitions, it will look something like the graphic below - **BUT YOU DON'T TICK THE FORMAT BOX**. 

**Hit Install now.**[/INDENT]

[SIZE=3][B][SIZE=5][COLOR=#800000]4. Follow the simple 'Install' steps: [/COLOR][/SIZE]
[/B][/SIZE][INDENT][SIZE=3][SIZE=2]
**Enter your names and password (same as before)**, choose to update during install etc.[/SIZE][/SIZE]
*(get on with another job, and in an hour it's done.)*[/INDENT]

[SIZE=5][COLOR=#800000]**5. Reboot - install updates - install additional apps - Reboot.**[/COLOR][/SIZE][INDENT][SIZE=3][I]
**That's it done!!!!!!**[/I][/SIZE][/INDENT]

Resources:
[COLOR=navy][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)[/COLOR] [COLOR=DarkRed]If you lose your boot this repair can be downloaded using your 'try ubuntu' cd.[/COLOR]
[COLOR=navy][https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)[/COLOR] [COLOR=DarkRed]Good info[/COLOR]
[COLOR=navy][https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)[/COLOR] [COLOR=DarkRed]Good info[/COLOR]

---

### Post by geazzy on 2013-08-04
keep sharing great tutorial dude :)

---

### Post by Ace..... on 2013-08-06
Thanks Geazzy for your appreciation,

It kicked me into action, and I finally got around to formatting the guide, to improve its clarity.

:)

---

### Post by bapoumba on 2013-08-06
If I may, you should change sudo nautilus to gksudo nautilus.
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by Cheesemill on 2013-08-06
*Thread moved to **Tutorials**.*

---

### Post by Ace..... on 2013-08-11
> **bapoumba said:**
> If I may, you should change sudo nautilus to gksudo nautilus.
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

Thanks bapoumba,

that change has been made.

:p

---

### Post by FuzzyFeat on 2013-08-13
First I would recommend that you have a problem that you ABSOLUTELY can not live with before you re-install.

I did a re-install and encountered a HOST of problems that did not previously exist. Among them - mouse did not work, No HDMI, NO Unity 3D and more. A second re-install, which involved  formatting of the partition, solved many of those. 

Of course I had to reload MANY aps, some of which required compiling and downloading various files.  In addition, my former problem i thought i could not live with was not solved either!  Now if only I can get the damed HDMI and the spell checker to work. :evil:Did not have that problem before, at least I don't remember if I did, or if I did, how I solved it.

It is easy to forget just how many apps and the problems you had to solve (and the solutions) to get them to run correctly.

Re-installing  may be a quick fix, but it can also become a real time suck. And it is no sure thing that your original problem will  be solved.

Often, it is better to live with the devil you know.

Good luck

---

### Post by Ace..... on 2013-08-23
Thanks for the response Fuzzy,
It sounds like you've had a bad time of it.

Can I re-phrase your opening line:


> **FuzzyFeat said:**
> 

I would recommend that you only perform a re-install, IF the problem that you have, 'cannot be lived with'.

I did a re-install and encountered a HOST of problems that did not previously exist. Among them - mouse did not work, No HDMI, NO Unity 3D and more. A second re-install, which involved  formatting of the partition, solved many of those. 

Of course I had to reload MANY aps, some of which required compiling and downloading various files.  In addition, my former problem i thought i could not live with was not solved either!  Now if only I can get the damed HDMI and the spell checker to work. :evil:Did not have that problem before, at least I don't remember if I did, or if I did, how I solved it.

It is easy to forget just how many apps and the problems you had to solve (and the solutions) to get them to run correctly.

Re-installing  may be a quick fix, but it can also become a real time suck. And it is no sure thing that your original problem will  be solved.

Often, it is better to live with the devil you know.

Good luck

**[SIZE=3]Response[/SIZE]**

I think your story is a valuable cautionary tale.... though, extremely difficult to convert completely into hard advice.
I have no idea how many similar problem instances might potentially exist, after performing what is a complete re-install (other than your data).

However, I will PM YannBuntu, who may recognise a fundamental problem, that might cause the procedure to fail.

You are the first to provide feedback on a failed re-install.
Let's hope that the problem continues to be rare.

---

### Post by ansari.ibrahim1 on 2014-08-02
You can use Aptik to backup software too.
[http://www.omgubuntu.co.uk/2014/01/reinstall-apps-on-ubuntu-fresh-install](http://www.omgubuntu.co.uk/2014/01/reinstall-apps-on-ubuntu-fresh-install)

---

### Post by Peter_Lustig on 2014-08-07
> **ansari.ibrahim1 said:**
> You can use Aptik to backup software too.
[http://www.omgubuntu.co.uk/2014/01/reinstall-apps-on-ubuntu-fresh-install](http://www.omgubuntu.co.uk/2014/01/reinstall-apps-on-ubuntu-fresh-install)

Thanks for this info!! I was looking for that tool cuz I heard about it somewhere but could not remember the name. But do you know how "successful" this soft is?

I have installed over many years so much soft like cinelerra, googleEarth, skype, vmware, netfabb, darktable, insane_bump ... that I really try to avoid a reinstallation. (it would take me days ^^)

Greetings):P

---

### Post by hop5uk on 2014-11-17
I have several raid 5 arrays built using SW (mdadm).If i reboot from a newly installed Ubuntu memory stick, will i have access to them?

---

### Post by Ace..... on 2014-11-17
> **hop5uk said:**
> I have several raid 5 arrays built using SW (mdadm).If i reboot from a newly installed Ubuntu memory stick, will i have access to them?

I believe this question would be better asked in one of the discussion forums, such as General help, or Hardware.

---

### Post by Bob_Briscoe on 2015-07-11
Thanks for this.

Note that steps 1 & 2 assume you have booted the system you want to reinstall. For those who (like me) are reinstalling because their system fails to boot, you can still (probably) do steps 1&2, but another way.

**Insert your install disk or pen drive** and cancel any autoplay dialogue.

**Re-start your pc in the way that will enter your BIOS** (on my Lenovo laptop you push the little 'Novo' button beside the power button with something pointed).
**Arrange it to boot off your install disk** (on mine you request the **boot menu** and select the pen drive, on others you might have to **find the section** that lists the boot order, check the top of the list is cd/dvd drive / pen drive (or move it to the top), save & exit

**Boot off the install disk**

Select **Try Ubuntu**

**Ubuntu should boot**, and if you're in luck, it will **automount** the system partition (the one you can no longer boot off), and any other data partition(s) you have. If it doesn't you may be able to mount them manually.

You can now proceed to collect the 3 identifiers in the following alternative to step 1 of the above tutiorial:

1. Launch the nautilus **File Manager**, and click on the device in the left-hand column that **looks like your old system partition**. It may have a name like "nnGB Volume". Once selected, on the right it should show the top level directories expected on a Linux system (bin, boot, dev, etc, home, ...). 

Double click **home** (on the right, not the other home on the left) and within it there should be a directory for each user that had been created on your old system. 
Warning: If you only see the directory **ubuntu** within home, you are not in your old system partition; you are in the install disk's system partition. Keep looking at other devices.

Now you've confirmed which is your old system partition, click again on its name in the left hand column, e.g. nnGB Volume, and this time double click **etc**, when it is listed on the right. Then scroll down to find the file **passwd**, and double click it.

Look for your username, probably more than 30 ines down, and **most likely User ID 1000** (as below) if you were first on the system.
```
bertieboop:x:1000:1000:Bertie Boop,,,:/home/bertieboop:/bin/bash
```

From the above example line, **the names to be found at 1a) and 1b) **[above]("http://ubuntuforums.org/showthread.php?t=2057342") would be "Bertie Boop" and "bertieboop"
Close the passwd file.

Next, scroll and Dclick the **hosts** file, stll within the **etc** directory. The **computer name to be found at 1c)** [above]("http://ubuntuforums.org/showthread.php?t=2057342") is probably on the second line, against 127.0.1.1. In the example below, the computer name is "deepthought".
 ```

127.0.0.1    localhost
127.0.1.1    deepthought

```

Continue with Step 1d) as in the tutorial above, making sure to save the text file you create to remember these usernames on a partition that you are not going to wipe, e.g. one with your  other user data.

2. To **make a back-up  of your home directory**, remember to use the home directory in the old system partition you found in step 1, not the home in the grey left column of the file manager. You should be able to find the partition with your user data on too, and back it up.

Now, you can **proceed directly with step 3**. and onward.

---

### Post by Ace..... on 2015-07-13
Thanks Bob, for contributing to this guide.
I've added a link to your instruction, in the Guide first paragraphs.

Currently it has been viewed 35k times, in almost 3 years.
Your addition is certain to help many people.
:)

---

### Post by ccbitz on 2015-07-16
First off, thanks for this tutorial it very nearly helped me recover a badly borked box...

However, I faced a serious issue after following the guide.  While booting, my system showed a dialog that said "*System running in low graphics mode:  Your screen, graphics card, and input device settings could not be detected correctly.  You will need to configure these yourself*"  If I could get passed this I might have had a hope of fixing it, but the problem was I couldn't click OK on the dialog because mouse and keyboard were not functional...  I couldn't even boot to command prompt because keyboard would not work at command prompt to input my password!

Keep in mind my system was already in bad shape following a failed upgrade from 12.04 to 14.04, so I didn't have much hope that this guide could save me (would not boot, similar issue to people in [this thread]("http://askubuntu.com/questions/361332/ubuntu-13-04-to-13-10-filesystem-check-or-mount-failed"), but nothing could help me recover).

I ended up using the live CD to go into my partition and blow away everything except my old home folder, then went ahead with your instructions.  I now have to go install all my apps again, but at least I get to keep my home folder without having to copy all 700+GB of it :P

---

### Post by Ace..... on 2015-07-17
Thanks ccbitz for registering with Ubuntu forums, to provide this feedback.

It is clear that on occasion, certain specific 'system issues' can impact on this re-installation method.

I'll add a note to the guide, advising users to address specific system problems to the relevant forum, in the hope that these can be resolved, to allow re-installation to proceed.

Anyway.... happily it looks as though you managed to find a way forward :)

---

