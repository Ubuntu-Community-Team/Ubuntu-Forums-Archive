---
title: "How To: Make Your Own Ubuntu Repository DVDs"
date: 2007-02-03
forum: Tutorials
---

### Post by BobSongs on 2007-02-03
[FONT=Verdana]**[SIZE=5][COLOR=Gray]How to make your own Ubuntu Repository DVDs[/COLOR][/SIZE]**

[COLOR=DarkSlateGray]**preamble**
Corrections and fixes submitted by the community are added and credited within the main tutorial. **However**, many of the posts that follow add great ideas. Please feel free to browse. But this first post should have all you need in terms of accomplishing the task at hand. And a big thanks to the brilliant souls who've added so many detailed and beautifully formatted ideas!

EDIT: This tutorial has fallen behind a bit. A clean up will begin shortly.


[/COLOR] 
**[SIZE=4]note[/SIZE]**
Sensiva reports that **9.10 Karmic Koala** has an issue with this, stemming from a bug in apt:

> Let me describe it in details. If I want to install a program that needs more than one package, and those packages are located on different DVDs, APT used to fetch then install then ask for the next disc. But with Karmic, after fetching it doesn't install, it prompts for the next discs... etc and then starts installation, the packages currently in the last disc in the drive are installed, then giving an error about the other packages which are located in the previous discs because they are not there. Its not a problem in the discs, I think its APT behavior itself that should be changed. Unfortunately I don't know how to adjust this way of APT in Karmic. but a workaround for this is pointing APT to the local repos already downloaded on the harddrive and not using the created DVDs. I have tested it and worked fine.[INDENT] 
:confused: [SIZE=3][COLOR=Teal]**! What's The Point Of This Tutorial?**[/COLOR][/SIZE]

A local set of repositories proves useful for friends and family who have **slow** or **no** bandwidth. Assembled from *various sources* (see the references below) these steps should create Ubuntu repository DVDs to share or keep in storage, however the need arises.

:-s [SIZE=3][COLOR=Purple]**What level experience do you need?**[/COLOR][/SIZE]

I've tried to conform to the tutorial rules. However, the very nature of this tutorial requires a bit more thinking than simply copying and pasting. Feel free to post a question about some step that may not work right for you. But the idea is to reduce the amount of text in the tutorial within reason by not detailing each step. 

:?: [SIZE=3]**[COLOR=RoyalBlue]Hard Disk Requirements (_Please Read This_)[/COLOR]**[/SIZE]

Roughly 45 gigabytes free hard drive space: to store the complete set of **.deb** files Ubuntu offers; to create four DVD ISOs; left-over space for the function of the PC. Now, in a day and age of the 1 terabyte drive... this may not be a huge consideration any more. But if your drive is smaller than 60 Gb, this download will take its toll. Download sizes alone (not including space required to make DVD ISOs):[INDENT]4.10 - Warty Warthog: [FONT=Verdana]9.72 GB[/FONT]
5.04 - Hoary Hedgehog: [FONT=Verdana]11.53 GB[/FONT]
5.10 - Breezy Badger: [FONT=Verdana]12.17 GB[/FONT]
6.06 - Dapper Drake: [FONT=Verdana]15.71 GB[/FONT]
6.10 - Edgy Eft: [FONT=Verdana]17.46 GB[/FONT]
7.04 - Feisty Fawn: [FONT=Verdana]19.90 GB[/FONT]
7.10 - Gutsy Gibbon: [FONT=Verdana] 24.81 GB[/FONT]
8.04 - Hardy Heron: [FONT=Verdana]28.85 GB[/FONT]
8.10 - Intrepid Ibex: [FONT=Verdana] 26.72 GB[/FONT]
9.04 - Jaunty Jackalope: [FONT=Verdana]27.53 GB[/FONT]
9.10 - Karmic Koala: [FONT=Verdana] 32.11 GB[/FONT]
10.04 - Lucid Lynx: [FONT=Verdana]32.29 GB[/FONT]
10.10 - Maverick Meerkat: 39.38 GB
11.04 - Natty Narwhal: 40.00 GB
11.10 - Oneiric Ocelot: 42.79 GB
Well, you get the point. From Warty to Oneiric we went from roughly 10 Gb to 43 Gb. 
[/INDENT][/INDENT][/FONT][COLOR=Gray]**[SIZE=4]Index[/SIZE]**
[/COLOR][INDENT]**01. Install the necessary tools** covers what you'll need to get started.
 **02. Extract debcopy** is not necessary to do first, but we get it out of the way at the beginning.
 **03. The Big Download** has the command necessary to download the desired repositories. Make your changes according to the type you need.
 **04. Divide into DVD-sized portions** prepares the files to make the DVDs.
 **05. Create ISOs** finishes what began in step 4.
 **06. Burning the ISO files** covers how to write the files to blank discs.
 **07. Getting It All To Work** is the instructions on how to tell Ubuntu to use the DVDs as a source for installing new software.
 **08. Updating the local repositories** shows how to keep what you've downloaded up-to-date.
 **09. Pointing Apt locally** shows you how to use what you've downloaded to your own advantage (should you decide to keep it around).
 **10. You only want a setup DVD?** is a link to Ubuntu setup DVDs for download.
 **11. FAQs** answers some frequently asked questions.[INDENT] Q1: How would I do this through DOS/Windows?
 Q2: Why don't I skip this mess and download pre-made DVD ISOs?
 Q3: What if I wanted to combine or add in more repositories? Something like Canonical Commercial? Or MediBuntu?
 Q4: How to get "debmirror" to download and validate the "Release.gpg" file.
 Q5: How do I setup a local Ubuntu mirror from a set of Repository DVDs?
[/INDENT]**12. Classic Ubuntu Repository Downloads**. Warty? Hoary? Breezy? Feisty, anyone? Don't fret about older editions disappearing. Help is right here.
 **13. References** gives credit where credit is due - and links
 **14. Mission, Vision & Values** (very boring)

[/INDENT][COLOR=DarkRed]**[SIZE=4]1. Install the necessary tools[/SIZE]**[/COLOR]

**Open a terminal** (from the top-left side of the Ubuntu screen:* Applications *&#8594;* Accessories *&#8594;* Terminal*). **[COLOR=DarkRed]Please[/COLOR] do not close this application throughout the length of this tutorial**.

**Copy** the following code and **paste it** into the **terminal**.```
sudo apt-get install debmirror liblockfile-simple-perl liblog-agent-perl ruby mkisofs dpkg-dev libdigest-sha1-perl libruby libzlib-ruby
```**Hit the Enter key** after pasting. (A quick way to "paste" text into the **terminal** is to hold down the following keys **Ctrl+Shift+V**, or right click in the terminal and click **Paste** in the context menu.)

While [COLOR=Blue]**debpartial**[/COLOR] is still in the repositories (big fancy phrase that means: this is an official and valid Ubuntu file), starting with Hardy Heron, it is [COLOR=Blue]**not considered part**[/COLOR] of **[COLOR=DarkRed]Hardy Heron[/COLOR]** or **newer** -- it is 100% compatible. Provided below is the link to the necessary software:[INDENT][SIZE=3][COLOR=Red]**>> [CLICK HERE]("http://ftp.gnome.org/mirror/cdimage/snapshot/Debian/pool/main/d/debpartial/debpartial_0+20030508.1.tar.gz") **[/COLOR][/SIZE][SIZE=3][COLOR=Red]**<< to download DebPartial from Canonical.**[/COLOR][/SIZE][/INDENT]Once saved on the desktop, **double-click** the file and extract **debpartial** to your home directory/folder.


[SIZE=4]**[COLOR=Indigo]2. Extract debcopy[/COLOR]**[/SIZE]

The **debcopy** file is included in **debpartial** (downloaded and installed in **Step 1**). Let's extract it now for later use. Please paste the following code into the Terminal:```
cp /usr/share/doc/debpartial/examples/debcopy.gz ~
``````
gunzip ~/debcopy.gz
```**[SIZE=4][COLOR=Sienna]3. The Big Download[/COLOR][/SIZE]**

Use this code to start downloading **Lucid Lynx**'s repository files:```
debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=http --progress --dist=lucid,lucid-security,lucid-updates,lucid-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg
```To see the whole code with some brief explanations:```
debmirror \
    --nosource -m --passive \
    --host=archive.ubuntu.com \ (select a faster repository if need be)
    --root=ubuntu/ --method=http --progress \
    --dist=[COLOR=Blue]**lucid**[/COLOR],[COLOR=Blue]**lucid**[/COLOR]-security,[COLOR=Blue]**lucid**[/COLOR]-updates,[COLOR=Blue]**lucid**[/COLOR]-backports, \
    --section=main,restricted,universe,multiverse \
    --arch=[COLOR=Blue]**i386**[/COLOR] ~/UbuntuRepos \ (this puts our files in /home/USER/UbuntuRepos)
    --ignore-release-gpg
```Some variables in blue.


[LIST]
[*]Want a [COLOR=DarkSlateGray]**detailed explanation**[/COLOR] of this command? [**CLICK HERE**]("http://ubuntuforums.org/showpost.php?p=3060394&postcount=49"). (links to a post in this thread.)
[*]Be forewarned: this can take ***a long time***, perhaps 24 or so hours. Downloading individual files is slow.
[/LIST]
[INDENT][SIZE=3]**Did the download stop midway?**[/SIZE]
Press the up cursor key on your keyboard and the command should re-appear. Hit Enter and the download will pick up where it last left off.

**[SIZE=3]Regular network glitches?[/SIZE]**
Try adding one of the following argument(s) to the command (the number following "-t" is the length of time -- in seconds -- before the retry begins) :

```
--timeout=seconds -t 120
```The "120" means 120 seconds or 2 minutes. Increase it to 4 minutes, for example, like this:```


--timeout=seconds -t 240
```[/INDENT]**[SIZE=4][COLOR=DarkOliveGreen]4. Divide into DVD-sized portions[/COLOR][/SIZE]**

[COLOR=DarkSlateGray]**[SIZE=2]Part 1:[/SIZE]**[/COLOR]

[LIST]
[*]**Note:** If you changed repositories in **Step 3** then the following command will require editing:
[/LIST]
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=**[COLOR=Red]lucid[/COLOR]**,[COLOR=Red]**lucid**[/COLOR]-security,**[COLOR=Red]lucid[/COLOR]**-updates,[COLOR=Red]**lucid**[/COLOR]-backports [COLOR=Blue]**--size=DVD**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```1. Replace the red [COLOR=Red]**lucid**[/COLOR] in the code above with your repository choice (i.e., [COLOR=Red]**intrepid**[/COLOR], [COLOR=Red]**jaunty **[/COLOR][COLOR=Red][COLOR=Black]or[/COLOR]** karmic**[/COLOR]).

2. If you plan on burning **CDs** instead of **DVDs**, then replace [COLOR=Blue]**--size=DVD**[/COLOR] with [COLOR=Blue]**--size=CD74**[/COLOR] (for 650 megabyte CD-Rs), **or** [COLOR=Blue]**--size=CD80**[/COLOR] (for 700 megabyte CD-Rs)

[COLOR=DarkSlateGray]**[SIZE=2]Part 2:[/SIZE]**[/COLOR]
How many CDs will we need to create? How do we find out? Paste this code in the Terminal and hit Enter:```
ls -l ~/UbuntuDVDs
```If the last folder is **ubuntu[COLOR=Blue]3[/COLOR]** you need to create **[COLOR=Blue]4[/COLOR]** DVDs. If the last folder is **ubuntu[COLOR=Blue]4[/COLOR]** then it will be **[COLOR=Blue]5[/COLOR]** DVDs, and if the last folder is **ubuntu[COLOR=Blue]31[/COLOR]**, you'll need to create [COLOR=Blue]**32**[/COLOR] CDs, and so on. NOTE: Oneiric's repository size = 42.79 Gb. You're going to need a large stack of CDs.

Having determined the number of physical discs you'll need, use the following as your pattern until all discs are complete (the only change from one to the next is the final number). These represent Lucid Lynx's requirements:

```
ruby ~/debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu0
``````
ruby ~/debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu1
``````
ruby ~/debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu2
``````
ruby ~/debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu3
``````
ruby ~/debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu4
``````
ruby ~/debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu5
``````
ruby ~/debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu6
``````
ruby ~/debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu7
```[SIZE=4][COLOR=DarkGreen]**5. Create ISOs**[/COLOR][/SIZE]

These instructions assume you've got enough data to make **8 DVDs**. If you've downloaded repositories that do not need an 8th DVD, none will be created.

```
mkisofs -f -J -r -V "Ubuntu [COLOR=Red]**10.04**[/COLOR] 1/8" -o ubuntu-**[COLOR=Red]10.04[/COLOR]**-$(date -I)-complete-**[COLOR=Red]i386[/COLOR][COLOR=Blue]-dvd1.iso[/COLOR]** ~/UbuntuDVDs/ubuntu0
``````
mkisofs -f -J -r -V "Ubuntu [COLOR=Red]**10.04**[/COLOR] 2/8" -o ubuntu-**[COLOR=Red]10.04[/COLOR]**-$(date -I)-complete-**[COLOR=Red]i386[/COLOR][COLOR=Blue]-dvd2.iso[/COLOR]** ~/UbuntuDVDs/ubuntu1
``````
mkisofs -f -J -r -V "Ubuntu [COLOR=Red]**10.04**[/COLOR] 3/8" -o ubuntu-**[COLOR=Red]10.04[/COLOR]**-$(date -I)-complete-**[COLOR=Red]i386[/COLOR][COLOR=Blue]-dvd3.iso[/COLOR]** ~/UbuntuDVDs/ubuntu2
``````
mkisofs -f -J -r -V "Ubuntu **[COLOR=Red]10.04[/COLOR]** 4/8" -o ubuntu-**[COLOR=Red]10.04[/COLOR]**-$(date -I)-complete-**[COLOR=Red]i386[/COLOR][COLOR=Blue]-dvd4.iso[/COLOR]** ~/UbuntuDVDs/ubuntu3
``````
mkisofs -f -J -r -V "Ubuntu **[COLOR=Red]10.04[/COLOR]** 5/8" -o ubuntu-**[COLOR=Red]10.04[/COLOR]**-$(date -I)-complete-**[COLOR=Red]i386[/COLOR][COLOR=Blue]-dvd5.iso[/COLOR]** ~/UbuntuDVDs/ubuntu4
``````
mkisofs -f -J -r -V "Ubuntu **[COLOR=Red]10.04[/COLOR]** 6/8" -o ubuntu-**[COLOR=Red]10.04[/COLOR]**-$(date -I)-complete-**[COLOR=Red]i386[/COLOR][COLOR=Blue]-dvd6.iso[/COLOR]** ~/UbuntuDVDs/ubuntu5
``````
mkisofs -f -J -r -V "Ubuntu **[COLOR=Red]10.04[/COLOR]** 7/8" -o ubuntu-**[COLOR=Red]10.04[/COLOR]**-$(date -I)-complete-**[COLOR=Red]i386[/COLOR][COLOR=Blue]-dvd7.iso[/COLOR]** ~/UbuntuDVDs/ubuntu6
``````
mkisofs -f -J -r -V "Ubuntu **[COLOR=Red]10.04[/COLOR]** 8/8" -o ubuntu-**[COLOR=Red]10.04[/COLOR]**-$(date -I)-complete-**[COLOR=Red]i386[/COLOR][COLOR=Blue]-dvd8.iso[/COLOR]** ~/UbuntuDVDs/ubuntu7
```**Note:** If you changed repositories in **Step 3** then each command above will require editing. Replace the **[COLOR=Red]version number[/COLOR]** of **[COLOR=Red]10.04[/COLOR]** with:
[LIST]
[*][COLOR=Red]**9.04**[/COLOR] for **jaunty** and [COLOR=Red]**9.10**[/COLOR] for **karmic**, [COLOR=Red]**10.10**[/COLOR] for **maverick**
[*]**[COLOR=Red]i386 [/COLOR]**[COLOR=Red][COLOR=Black]for[/COLOR][/COLOR]**[COLOR=Red] amd64[/COLOR]**[COLOR=Black],[/COLOR]**[COLOR=Red] powerpc [/COLOR]**[COLOR=Red][COLOR=Black]or[/COLOR][/COLOR]**[COLOR=Red] sparc[/COLOR]**
[/LIST]

[LIST]
[*]**If you're committed to creating CD-R ISOs** (detailed in **Step 4**) then make the following changes:
[LIST]
[*]replace [COLOR=Blue]**-dvd1.iso**[/COLOR] with [COLOR=Blue]**-cd1.iso**[/COLOR]
[*]replace [COLOR=Blue]**-dvd2.iso**[/COLOR] with [COLOR=Blue]**-cd2.iso**[/COLOR] (and so on until all 50 or so CD-R ISOs are completed)
[/LIST]
 
[/LIST]

**[SIZE=4][COLOR=DarkSlateBlue]6. Burning the ISO files[/COLOR][/SIZE]**

[SIZE=3] **Using [COLOR=DarkRed]Ubuntu[/COLOR]**[/SIZE] (**[Link]("https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu")**)

[LIST=1]
[*]Insert a blank CD into your burner. A "CD/DVD Creator" or "Choose Disc Type" window will pop up. Close this, as we will not be using it.
[*]Browse to the created ISO image in the file browser
[*]Right click on the ISO image file and choose **Write to Disc.**
[*]Select the write speed.  It is recommended that you write at the lowest possible speed.
[*]Start the burning process and repeat these steps until all ISOs are done.
[/LIST]

 [SIZE=3]**Using [COLOR=Blue]Kubuntu[/COLOR]**[/SIZE] ([**Link**]("https://help.ubuntu.com/community/BurningIsoHowto#Kubuntu"))

[LIST=1]
[*]Find the ISO image in the file browser (available at System Menu > Home Folder on bottom of the screen next to KMenu.)
[*]Right click on the ISO &#8594; Actions &#8594; Write CD Image with K3b...
[*]K3b will now automatically verify the md5sum, make sure these match.
[*]Place Blank CD in burner and click on start.
[/LIST]

[SIZE=3]**Using [COLOR=Purple]Xubuntu[/COLOR]**[/SIZE] ([**Link**]("https://help.ubuntu.com/community/BurningIsoHowto#Xubuntu"))

[LIST=1]
[*]Launch the burning tool, **xfburn**  (available at Applications &#8594; Accessories &#8594; xfburn.)
[*]Choose from the main toolbar, or from the menu Actions the option "Burn CD Image",
[*]From the Burn CD Image dialog box, click over (None) from "image to burn", and find the ISO image in the file browser
[*]In the dialog, click 'Burn Image'.
[/LIST]

[COLOR=Teal]**[SIZE=4]7. Getting it all to work[/SIZE]**[/COLOR]

There are two ways to add a DVD/CD to your repository list:[INDENT] _**"KPackageKit" and "Adept"**_

Kubuntu's built-in package managers seem to have difficulties with adding CD/DVD ROMs to the list of available system packages. Try using the "Terminal" solution.

_**Synaptic:**_

Open Synaptic Package Manager (*System *&#8594;* Administration *&#8594;* Synaptic Package Manager*). Enter your password. From the menu: *Edit *&#8594;* Add CD-ROM....* and follow the clearly written instructions in each dialog box. Repeat until all your media (DVDs, CDs) have been entered. Should this fail, try the following.

[B]_Terminal:_

Open a Terminal[/B] (*Applications *&#8594;* Accessories *&#8594;* Terminal*) and enter the following command:```
sudo apt-cdrom add
```Insert the first disc and follow the instructions (it will ask you to name each disc). When **apt-cdrom** is finished with the disc, eject it with```
eject
```(yeah, just type it in and hit Enter) and insert the next and use the same command. Repeat the process per disc.

Once the **last disc** is done, enter this code in the Terminal:```
sudo apt-get update
```followed by```
sudo apt-get upgrade
```which will update your system if any newer files are available. You can now open **Synaptic Package Manager** to use tens of thousands of packages.

(**To be added:** how to remove previously added DVD/CD entries in apt when old discs are replaced with new, as well as correcting any goofs that occur when incorrectly labeling the discs, etc.)

[/INDENT][COLOR=Green]**[SIZE=4]8. Updating the local repositories (i.e., "Now what!?")[/SIZE]**[/COLOR]

Now that you have ***gigabytes*** of **.deb** files all tucked neatly into the ~/UbuntuRepos folder... what on earth do you do to keep it updated? Start again? Sort of. Read on...

Open the Terminal (*Applications &#8594; Accessories &#8594; Terminal*) and go to the folder where you initially ran **debmirror** (by default: your home folder) and run the command in **Step 3** again. This only makes an incremental update consuming roughly 10 minutes instead of 25 hours. Run this daily and ISO creation won't have the added bore of a long download.

If new DVDs are required or desired, delete your original .iso files (in your home folder) and run steps 5 through 7 to recreate them.

[COLOR=Purple]**[SIZE=4]9. Pointing Apt locally[/SIZE]**[/COLOR]

**luvr** has a tutorial entitled "Creating a Trusted Local Repository from which Software Updates can be installed" that is more detailed than my addition. [SIZE=2][**CLICK HERE**]("http://ubuntuforums.org/showthread.php?t=1090731")[/SIZE] for this Ubuntu Forums HOWTO. It begins with:[INDENT]*"If you manage multiple PCs running Ubuntu, you will likely want to keep them all updated. Thus, you will want to install the Ubuntu updates to each of them as they become available, and you will have each PC individually download all of the updates from the Ubuntu repositories on the internet. This may, however, be impractical to you&#8212;particularly if, e.g., you are on a rather slow internet connection, or if your monthly data transfer volume is severely limited, or if you simply prefer to save the bandwidth."*
[/INDENT]**Credit**=[COLOR=Red]**Geochelone**[/COLOR]

**It is possible** to use the files you've downloaded as your own local repository. It can be used for updates and installing new packages. But this will only work well if you keep these files up-to-date. If not, you will fall behind in security updates.

With that out of the way let's proceed. Enter the following code in the terminal:

```
cd ~/UbuntuRepos && dpkg-scanpackages . /dev/null > Packages && gzip Packages && cd ~
```This creates the necessary files for **apt** to know what is in your local repositories.

Once completed insert the following into your **sources.list** file:```
deb file:/home/[USER NAME HERE]/UbuntuRepos/ [COLOR=Red]**lucid**[/COLOR] main multiverse restricted universe
``````
deb file:/home/[USER NAME HERE]/UbuntuRepos/ **[COLOR=Red]lucid[/COLOR]**-security main multiverse restricted universe
```([COLOR=Red]**CREDIT:**[/COLOR] [**xfile087**]("http://ubuntuforums.org/member.php?u=122407"))

**NOTE:** Don't forget these two things:

[LIST=1]
[*]modify these lines for [COLOR=Olive][COLOR=Red]**jaunty **[/COLOR][COLOR=Red][COLOR=Black]or[/COLOR]** karmic**[/COLOR][/COLOR]
[*]put **hash marks** (#) before each Internet repository line you no longer require. Example:

```
[COLOR=Red]**#**[/COLOR] deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
```
[/LIST]

**[SIZE=4][COLOR=RoyalBlue] 10. You only want a setup DVD?[/COLOR][/SIZE]**

Head over to [**this link**]("http://nginyang.uvt.nl/") and select the corresponding Ubuntu suite you desire.[INDENT]The difference between the Ubuntu setup **CD** and the Ubuntu setup **DVD** is how much of the repositories are on the setup disc. The DVD contains quite a bit more, most of "Main" if I'm not mistaken. However, if you have the repository DVDs handy, a setup DVD is redundant and not recommended. Save your bandwidth and don't bother. However, if you want a snazzy setup DVD, try this on for size:

Click here: [**Ultimate Edition**]("http://ultimateedition.info/")

Click here: [URL="http://hacktolive.org/wiki/Hacktolive.org"][B]SuperOS


[/B][/URL][/INDENT][COLOR=Red]**[SIZE=4]11. F.A.Qs[/SIZE]**[/COLOR]

[SIZE=3][COLOR=DarkRed]**Question 1: How would I do this through DOS/Windows?**[/COLOR][/SIZE]

**Answer 1.** I... honestly... don't... know. I can't imagine how tedious it would be to try to assemble all this file by file. If you're a dual-booter or you've got faster bandwidth on a Windows machine elsewhere then I understand your dilemma. **debmirror** is the binary that does all the work. I cannot imagine that anyone has made a port for Windows. Until someone shows me a blog that tells Windows users how to accomplish this I suggest looking at the solutions in **Q2**.

**Answer 2.** This is a "round about" way of using a Windows PC where the bandwidth is fast. Try using the Ubuntu setup CD in "Live User Mode". Follow the instructions in this tutorial and use the Windows Hard Drive as your destination. Well, look. I didn't think it would be **easy**, just... sorta... possible.

[CENTER]__________________________________[/CENTER]

[SIZE=3][COLOR=DarkRed]**Question 2: Why don't I skip this mess and download pre-made DVD ISOs?**[/COLOR][/SIZE]

**Answer 1.** Pre-made DVD ISOs are fine for a single, never-to-be-repeated download (if time is an issue). Here's the difficulty: to get updates means downloading the ISOs **again** (sorta time consuming). If a single ISO download is right for you -- use this link: [ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/)

**Answer 2.** Modem connections make this tutorial impossible regardless the O/S. Consider purchasing inexpensive DVD ISOs from an online vendor. Examples are:

[LIST]
[*][**On-Disk.com**]("http://on-disk.com/index.php/cPath/28_135_183")
[*][**OSDisc.com**]("http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html")
[/LIST]
They will provide exactly what you need: Ubuntu Repository DVDs with setup disks - perfect for that off-line PC. These companies will ship these discs right to your door for a small fee (**no affiliation with the author**).

[CENTER]__________________________________[/CENTER]

[SIZE=3][COLOR=DarkRed]**Question 3: What if I wanted to combine or add in more repositories? Something like Canonical Commercial? Or MediBuntu?**[/COLOR][/SIZE]

**Answer.** [COLOR=Red]**Don't do it!**[/COLOR]

OK. Now that I've got your attention... let me say that **jocose** says you can. But you must [follow his instructions here]("http://ubuntuforums.org/showpost.php?p=5289323&postcount=141"). Please note: these instructions have not been tested in our labs at Muppet Central. Advance at your own risk.

For those of you who want to mess around and don't mind burning an extra CD or two, continue reading:[INDENT]**debmirror** will only **[COLOR=DarkRed]erase your original files[/COLOR]**. You must change the name of the download folder(s).[COLOR=Black] Let me explain and illustrate.[/COLOR]

[/INDENT]This is what **debmirror** appears to do when run:

[LIST=1]
[*]**debmirror** receives the file list from the server within the command line (archive.ubuntu.com, for example).
[*]**debmirror** then looks for the "destination" folder. If it doesn't exist, it creates it.
[*]if **debmirror** finds that the destination folder already exists it compares the files it finds with the remote server's file listing.
[*]**debmirror** then carefully **erases everything in the destination folder** that is not an exact match with that list.
[*]**debmirror** downloads files it deems are missing in the destination folder.
[/LIST]

If you are updating a local set of files, this is a **good** thing. But if you **choose a different server**, this is a **bad** thing.

The quick way to add files from different servers (such as MediBuntu and Canonical) is to put the additional files in unique folders. Examples:  ~**/MediBuntuRepos** and/or **~/CanonicalRepos** (your folder names may vary). Then replace [COLOR=Red]**~/UbuntuRepos**[/COLOR] in each command.

If you're feeling confused by the above description and you just want to start downloading, the following steps show how to create Canonical and Medibuntu CD sets:

[SIZE=4]**Canonical Repos**[/SIZE]```
debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=[COLOR=Red]**lucid**[/COLOR],**[COLOR=Red]lucid[/COLOR]**-backports,[COLOR=Red]**lucid**[/COLOR]-proposed,[COLOR=Red]**lucid**[/COLOR]-security,[COLOR=Red]**lucid**[/COLOR]-updates --section=partner --arch=i386 ~/CanonicalRepos --ignore-release-gpg
``````
debpartial --nosource --dirprefix=ubuntu --section=partner --dist=[COLOR=Red]**lucid**[/COLOR],[COLOR=Red]**lucid**[/COLOR]-backports,[COLOR=Red]**lucid**[/COLOR]-proposed,[COLOR=Red]**lucid**[/COLOR]-security,[COLOR=Red]**lucid**[/COLOR]-updates --size=CD80 ~/CanonicalRepos ~/CanonicalRepos/CD
``````
ruby debcopy -l ~/CanonicalRepos ~/CanonicalRepos/CD/ubuntu0
``````
mkisofs -f -J -r -V "Canonical" -o ubuntu-7.10-$(date -I)-Canonical.iso ~/CanonicalRepos/CD/ubuntu0
```Replace [COLOR=Red]**lucid**[/COLOR] with [COLOR=DarkRed]**intrepid**[/COLOR], [COLOR=Navy]**jaunty**[/COLOR] or [COLOR=Purple]**karmic**[/COLOR].

Architecture options = [COLOR=DimGray]**amd64**, **powerpc **or **sparc**[/COLOR]

**[SIZE=4]MediBuntu Repos[/SIZE]**```
debmirror --nosource -m --passive --host=packages.medibuntu.org --root=/ --method=http --progress --dist=**[COLOR=red]lucid[/COLOR]** --section=free,non-free --arch=i386 ~/MediBuntuRepos --ignore-release-gpg
``````
ruby debcopy -l ~/MediBuntuRepos ~/MediBuntuRepos/CD/ubuntu0
``````
mkisofs -f -J -r -V "MediBuntu" -o ubuntu-7.10-$(date -I)-MediBuntu.iso ~/MediBuntuRepos/CD/ubuntu0
```Replace [COLOR=Red]**lucid**[/COLOR] with[COLOR=DarkRed]** intrepid**[/COLOR][COLOR=Black],[/COLOR] **[COLOR=Purple]jaunty[/COLOR]** or **[COLOR=Sienna]karmic[/COLOR]**.

Architecture options = [COLOR=DimGray]**i386**[COLOR=Black],[/COLOR]** amd64**[COLOR=Black],[/COLOR] [/COLOR][COLOR=DarkOrchid]**[COLOR=DimGray]powerpc[/COLOR]**[/COLOR]

[COLOR=DimGray](To add MediBuntu to your personal repositories: [https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f))[/COLOR]

**[SIZE=4][COLOR=Black]Google Repos[/COLOR][/SIZE]**```
debmirror --nosource -m --passive --host=dl.google.com --root=/linux/deb/ --method=http --progress --dist=stable --section=non-free --arch=i386 ~/GoogleRepos --ignore-release-gpg
```The Google directories appear... then disappear. This is the last directory address I have. 

[CENTER]__________________________________[/CENTER]

[SIZE=3][COLOR=DarkRed]**Question 4: How to get "debmirror" to download and validate the "Release.gpg" file.**[/COLOR][/SIZE]

**Answer.** I don't know!!! But [**luvr**]("http://ubuntuforums.org/member.php?u=68732") does. Thanks for the addition.

**luvr** tackles this question with this patient and well laid out post: [**Click Here.**]("http://ubuntuforums.org/showpost.php?p=7367273&postcount=237")

[CENTER]__________________________________[/CENTER]

[LEFT][SIZE=3][COLOR=DarkRed]**Q5: How do I setup a local Ubuntu mirror from a set of Repository DVDs?**[/COLOR][/SIZE]

**Answer.** I just don't know!!! But [**luvr**]("http://ubuntuforums.org/member.php?u=68732") does. Thanks for the addition.

**luvr** tackles this question with this patient and well laid out post: [**Click Here.**]("http://ubuntuforums.org/showpost.php?p=7455095&postcount=243")

[/LEFT]

[CENTER]__________________________________[/CENTER]

[COLOR=Teal]**[SIZE=4]12. Classic Ubuntu Repository Downloads[/SIZE]**[/COLOR]

For anyone who is interested for whatever reason... be it nostalgia, business, just plain techno geek, or reasons you would probably not want everyone to know, here are example codes for the classic repositories.

[COLOR=DarkRed]**Warty Warthog**[/COLOR] on the **[COLOR=Blue]i386[/COLOR]** architecture:

```
debmirror --nosource -m --passive --host=old-releases.ubuntu.com --root=ubuntu/ --method=http --progress --dist=**[COLOR=Red]warty[/COLOR]**,**[COLOR=Red]warty[/COLOR]**-security,**[COLOR=Red]warty[/COLOR]**-updates,**[COLOR=Red]warty[/COLOR]**-backports, --section=main,restricted,universe,multiverse --arch=**[COLOR=Teal]i386[/COLOR]** ~/WartyRepos_**[COLOR=Teal]i386[/COLOR]** --ignore-release-gpg
```**[COLOR=DarkRed]Warty Warthog[/COLOR]** on the **[COLOR=Blue]64-bit AMD[/COLOR]** architecture:

```
debmirror --nosource -m --passive --host=old-releases.ubuntu.com --root=ubuntu/ --method=http --progress --dist=**[COLOR=Red]warty[/COLOR]**,**[COLOR=Red]warty[/COLOR]**-security,**[COLOR=Red]warty[/COLOR]**-updates,**[COLOR=Red]warty[/COLOR]**-backports, --section=main,restricted,universe,multiverse --arch=**[COLOR=Teal]amd64[/COLOR]** ~/WartyRepos_**[COLOR=Teal]amd64[/COLOR]** --ignore-release-gpg
```Doing it this way clearly defines a different folder for each repository set. Note the [COLOR=Red]**coloured** **[COLOR=Teal]text[/COLOR]**[/COLOR] can be changed to suit the version, architecture, and output folder as per your original tutorial method.

**Please note a few points:**

1. Don't mix repositories. If you have enough free hard drive space to keep these repositories around then put each version's files in a different folder (fear not: they're not being updated any more: what you download never needs to be updated). Here we've used "~/UbuntuReposWartyi386" and "~/UbuntuReposWartyAMD64" and not "~/UbuntuRepos". All contents of ~/UbuntuRepos will be wiped to accommodate the new download. We encourage a folder for each version, e.g. Wartyi386, WartyAMD64, Hoaryi386, HoaryAMD64, etc.

2. the architectures currently available in each (old.release) version are:

[LIST]
[*] 4.10 (Warty Warthog); i386, amd64, ppc.
[*] 5.04 (Hoary Hedgehog); i386, amd64, ppc, ia64, sparc.
[*] 5.10 (Breezy Badger); i386, amd64, ppc, ia64, sparc.
[*] 6.10 (Edgy Eft); i386, amd64, ppc, ia64, sparc.
[*] 7.04 (Feisty Fawn); i386, amd64, ppc, sparc.
[*] 7.10 (Gutsy Gibbon); amd64, armel, hppa, i386, ia64, lpia, powerpc, sparc.
[*]8.04 (Hardy Heron)
[/LIST]
**[COLOR=red]CREDIT[/COLOR]**: **k3lt01**

If you're still running a classic copy of Ubuntu and want to install software, change your sources.list file to reflect that release. If it would be Warty Warthog, 4.10, you'd use the following:

```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ warty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ warty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ warty-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ warty-backports main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu/ warty-proposed main restricted universe multiverse
```Source: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

[SIZE=4][COLOR=Gray]**13. References**[/COLOR][/SIZE]

This tutorial was pieced together from:

[LIST]
[*][SIZE=2]**Ramon's original tutorial** has vanished. It was last seen at **[http://cargol.net/~ramon/ubuntu-dvd-en]("http://cargol.net/%7Eramon/ubuntu-dvd-en")**. It was very basic and designed for Warty Warthog. Then I found...[/SIZE]
[*][SIZE=2]**[How to Make Ubuntu DVDs by Burt]("http://blog.entner.net/2006/08/16/make-ubuntu-dvds-including-everything/") **(significant modifications to Ramon's tutorial. Bert's instructions were brought to this forum for a local reference. Thanks Burt for improving on Ramon's original.)[/SIZE]
[/LIST]

The tutorial was updated with the help of the thoughtful comments by forum friends ... and I may have polished it up a bit. I take responsibility for all errors and give credit to contributors for all accuracies.

Other related links:

[LIST]
[*][SIZE=2][**Apt on CD**]("http://aptoncd.sourceforge.net/index.html")[/SIZE]
[*][[SIZE=2]**Creating a Trusted Local Repository from which Software Updates can be installed**[/SIZE]]("http://ubuntuforums.org/showthread.php?t=1090731")
[*][SIZE=2][**HowToCreateYourOwnGNULinuxDistribution**]("http://www.gnewsense.org/Builder/HowToCreateYourOwnGNULinuxDistribution")[/SIZE]
[*][SIZE=2]**[HowTo Forge]("http://www.howtoforge.com/dvd_images_of_ubuntu_repositories")**[/SIZE]
[*][SIZE=2]**[List of Ubuntu Releases]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases")**[/SIZE]
[/LIST]

[COLOR=Red]**[SIZE=4]14. Mission, Vision & Values[/SIZE]**[/COLOR]

[LIST]
[*] My **mission** was to put the repository tutorial here in the **Ubuntu Forums**, to include extra elements and ensure that those with basic Ubuntu experience could accomplish this. This tutorial was added to this Forum for these reasons:
[LIST=1]
[*] The original tutorial disappeared.
[*] The original tutorial did not reflect Ubuntu's 6-month updates or the changes the tutorial needed due to the difference in the size of the growing repositories, etc.
[*] The original tutorial tutorial only focused on **i386**.
[/LIST]
 
[*] My **vision** is to keep it maintained (the repositories are forever changing, making this necessary), improve its wording, answer questions that arise due to the lack of clarity that perpetually plagues the text.
[*] My **values** cover only [COLOR=DarkRed]**active versions**[/COLOR], with a focus on the most recent ***Long Term Support*** distribution. Support for **abandoned ("unsupported") editions** or **future alpha/beta ("unstable") editions** must be maintained by forum members who feel the need to have these. Please do not perceive my refusal to work on these as a personal affront. Send me the codes. I'll add them and credit the author.
[*]Note: **k3lt01** has stepped up to the plate and has sent me the codes for the classic (i.e., discontinued) distros. Should you encounter problems with these codes, let me know and I'll fix 'em.
[/LIST]

---

### Post by glenn45 on 2007-02-24
Hello Bobsong. Thanks for the how to. I was trying to build an amd64 DVD. I performed your scripts and all went well until i reached the part where i have to divide the download into dvd size chunks. it kept looking for i386 package.gz. Luckily i've figured out that i have to modify a bit your command line for debpartial by adding --arch=amd64. and it went well.

Thanks again. Im going onto the next step.:)

---

### Post by BobSongs on 2007-02-24
[FONT=Verdana]:-D

You caught me. Okie dokie. I'll fix the tutorial.
[/FONT]

---

### Post by glenn45 on 2007-02-26
Bobsong. 
Everything's all right. I now have a repository on my extternal hard disk and can take it home  where i dont have internet access and update and install softwares on my ubutu.  In fact i need not burn the isos i've created i just mounted them using the mount command. 
Thanks again. Nice How To.!
:)

---

### Post by airtonix on 2007-02-27
any idea how to then make incremental updates to the resulting final debmirror archive?

hence to prevent another 12hour 27gb download session. for only three or four new packages.

---

### Post by BobSongs on 2007-02-28
> **airtonix said:**
> any idea how to then make incremental updates to the resulting final debmirror archive?

hence to prevent another 12hour 27gb download session. for only three or four new packages.
[FONT=Verdana]
Good question, **airtonix**. Your answer has been integrated into the tutorial (Step 8 ).
[/FONT]

---

### Post by BobSongs on 2007-02-28
[FONT="Georgia"]> **glenn45 said:**
> Bobsong. 
Everything's all right. I now have a repository on my extternal hard disk and can take it home  where i dont have internet access and update and install softwares on my ubutu.  In fact i need not burn the isos i've created i just mounted them using the mount command. 
Thanks again. Nice How To.!
:)[/FONT]

[FONT="Verdana"]I like your idea of putting them on an external drive. I imagine that would be more than sufficient and very efficient. Mounting them makes much sense. Especially if you've got the external drive available and the PC in question only has a CD ROM reader.[/FONT]

---

### Post by glenn45 on 2007-03-04
Bobsong, the GeekSpeak part is a good addition.:)  However, maybe those who are not geek enough might not notice immediately (like me for example) that in the debpartial command, there was no instance that i386 appeared so it might not be obvious for the user of your howto to add the --arch=amd64 (ppc or whatever) to it.  Just my two cents. :guitar:

---

### Post by BobSongs on 2007-03-14
> **glenn45 said:**
> Bobsong, the GeekSpeak part is a good addition.:)  However, maybe those who are not geek enough might not notice immediately (like me for example) that in the debpartial command, there was no instance that i386 appeared so it might not be obvious for the user of your howto to add the --arch=amd64 (ppc or whatever) to it.  Just my two cents. :guitar:

[FONT=Verdana]I've replaced the **Geek Speek** section with something I hope works a bit better. The idea here is to keep things concise and precise.

Now I'm working on a way to get Synaptic to recognize the downloaded repositories as valid instead of using the online repositories. I've almost got it... but not quite. I'll post it as soon as I figure out how it's done.

[Edit]: Done. See Step 9 above. Also: all the commands have been coloured red where to show what should be changed if the need arises.[/edit][/FONT]

---

### Post by glenn45 on 2007-03-16
Bobsong. 
What if I would like to add another repository that is not on the official list? Say I would like to add a repository where Beryl is available? Should I just modify my repository list? Anyway , Im going to test it tomorrow and see what what happens. :)

---

### Post by BobSongs on 2007-03-16
> **glenn45 said:**
> Bobsong. 
What if I would like to add another repository that is not on the official list? Say I would like to add a repository where Beryl is available? Should I just modify my repository list? Anyway , Im going to test it tomorrow and see what what happens. :)

[FONT=Tahoma][COLOR=DarkSlateGray]Yo, glenn45. Excellent question. This question is answered in the FAQs.

I want to do some research in order to:[LIST]
[*]Add extra repositories like, say, the PLF files *Completed, added to main tutorial*
[*]Use the current repositories downloaded to install new software (rather than downloading again) *Completed, added to main tutorial*
[*]Figure out how to inform 'apt', 'synaptic' and 'aptitude' that the repositories are valid and can be trusted. *[FONT=Tahoma][COLOR=DarkSlateGray]Completed, added to main tutorial[/COLOR][/FONT]*[/LIST][/COLOR][/FONT]

---

### Post by glenn45 on 2007-03-22
Hey BobSongs! Are we the only two people (well maybe 3 :) ) interested on this how to? Not much traffic here, eh? Anyways, keep up the good work. I wasnt able to test last week my idea of adding new repositories, kinda busy lately. :guitar:

---

### Post by Abhi Kalyan on 2007-03-23
Thank you Bobsongs,
Very beautifull HOWTO!!
Clear, Concise and Complete.
Thank you

---

### Post by BobSongs on 2007-03-23
> **Abhi Kalyan said:**
> Thank you Bobsongs,
Very beautifull HOWTO!!
Clear, Concise and Complete.
Thank you

[FONT="Verdana"]You're very, very welcome. Your words are kind and appreciated.[/FONT]

---

### Post by BobSongs on 2007-03-23
> **glenn45 said:**
> Hey BobSongs! Are we the only two people (well maybe 3 :) ) interested on this how to? Not much traffic here, eh? Anyways, keep up the good work. I wasnt able to test last week my idea of adding new repositories, kinda busy lately. :guitar:

:lolflag:

[FONT="Verdana"]I have a philosophy about HowTo's. 1) If they're done right and cover just about every angle the questions should be few; 2) It's got to be something I return to for it's practical value. With this one that's the case. :-)

Yeah; it's a weird one. But I didn't like having to run around to various tutorials on the net to try to make sense of how this is done. If consolidated and local I figured those who roam these forums would appreciate it when the need arose. While I'm appreciative of the sources I often find that certain details are not clearly laid out. Sure: it gets figured out eventually, but usually with a loss of time.

If you can add anything at all to the tutorial I'd be much obliged. You'll be credited with the additional info.[/FONT]

---

### Post by Chyper on 2007-03-23
tyvm :)

i have to do a server install so this saves alot of time.

---

### Post by BobSongs on 2007-03-23
[Post removed. Text imported into the main tutorial.]

---

### Post by BobSongs on 2007-03-23
> **Chyper said:**
> tyvm :)

i have to do a server install so this saves alot of time.
[FONT="Verdana"]
If you'd like to add any info to my tutorial to help others accomplish the same thing (y'know: some extra tweaks and stuff) send me a painfully detailed listing of what you did and I'll add it to the main tutorial, crediting you.

What I mean by "painful" is: don't skip any steps. If you created a directory... note it. If you tweaked this file and edited that one: note it. Make it such that a total beginner could follow it.[/FONT]

:-)

---

### Post by glenn45 on 2007-03-29
Great addition, Bobsongs!
I'm going to try this. One question: i can run the commands in the directory where I downloaded the previous repositories without fear of breaking it right? Or should I run the command in a different directory?
Cheers!
Glenn

---

### Post by BobSongs on 2007-03-29
> **glenn45 said:**
> Great addition, Bobsongs!
I'm going to try this. One question: i can run the commands in the directory where I downloaded the previous repositories without fear of breaking it right? Or should I run the command in a different directory?
Cheers!
GlennI have two hard drives. The system disk is actually larger than my personal files disk that is mounted as /home. 

To run this tutorial myself, I created a new folder from the very root: /UbuntuRepos. I set its permissions to be free for all (I have my doubts anyone will roam my hard drive, but that's another issue). Then I ran the download there because of all the extra hard drive space.

It was necessary to change path names in the tutorial. To make that easier for folks I'm tempted to color them differently but I haven't worked out a scheme yet. This requires more thought.

But your answer is: yes. You can run this application anywhere and your system will be safe. Just don't run this program in a folder that contains valuable date (see the FAQs for why).


---

### Post by pana.corbului on 2007-05-17
Hi. This topic is one of my favorite :D . . What I'm interested  in is how can I tell ebmirror to download all those debs and srcs in a particular folder.That;s because my / has 30 gb and my media/sda3 has 250 gb :) (sata II, 7200.10 :D )

---

### Post by BobSongs on 2007-05-17
> **pana.corbului said:**
> Hi. This topic is one of my favorite :D . . What I'm interested  in is how can I tell ebmirror to download all those debs and srcs in a particular folder.That;s because my / has 30 gb and my media/sda3 has 250 gb :) (sata II, 7200.10 :D )

[FONT=Verdana]So, basically you want **debmirror** to download the repository files to a different folder/drive than the one described in the tutorial.

OK. Your **250 Gb** drive is located at **media/sda3**. Excellent. Determine its mount-point (such as **/bigdrive** or **/extra/bigdrive**, that sort of thing). I am assuming it is mounted and ready to be used by Ubuntu.

Here is the original command:

[/FONT]> [FONT=Courier New]debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=http --progress --dist=dapper,dapper-security,dapper-updates,dapper-backports --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg[/FONT][FONT=Verdana] 
This is an example of a possible new command:

[/FONT]> [FONT=Courier New]debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=http --progress --dist=**[COLOR=Red]dapper[/COLOR]**,**[COLOR=Red]dapper[/COLOR]**-security,**[COLOR=Red]dapper[/COLOR]**-updates,**[COLOR=Red]dapper[/COLOR]**-backports --section=main,restricted,universe,multiverse --arch=**[COLOR=Red]i386[/COLOR]** **/bigdrive/UbuntuRepos** [/FONT][FONT=Courier New]--ignore-release-gpg[/FONT]  [FONT=Verdana]
I'm not wrapping the codes with the [ code ] attribute so you can see at a glance the difference between the commands. Here's the breakdown:
[/FONT][LIST=1]
[*][FONT=Verdana]The parts highlighted in [COLOR=Red]**red**[/COLOR] are what you change to match the version of Ubuntu you wish to download (dapper, edgy, feisty, etc. - see main tutorial for explanation).[/FONT]
[*][FONT=Verdana]The part highlighted in **bold** represents the new download folder.[/FONT][/LIST][FONT=Verdana] There you go. I hope this answers your question. Feel free to tell me I'm completely wrong and did not understand your question correctly. I'll try again if I failed.

:)

<><
[/FONT]

---

### Post by pana.corbului on 2007-05-18
Thanks a lot. That was exacly my point. I didn't realized that ubunturepos was going to be a folder where everything would be downloaded :P . I just had to add /media/sda3/UbuntuRepos. Now I'm waiting for the repos to download :). I'll follow your tutorial to see if indeed I'l be a happy man ;))) thanks again.

---

### Post by pana.corbului on 2007-05-18
Later Edit... >>
Relating console commands that should be applied after download is complete ..like debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=dapper,dapper-security,dapper-updates,dapper-backports --size=DVD ~/UbuntuRepos/ ~/UbuntuDVDs/ >> I guess that I need to be in /media/sda3 before execute them . (cd /media/sda3) or to sprecify where's ~ media/sda3? :|

I solved it by replacing all ~ with /media/sda3. What I'm on it now is a utf-8 error when I'm building my dvd iso's

---

### Post by BobSongs on 2007-05-18
> **pana.corbului said:**
> ...

What I'm on it now is a utf-8 error when I'm building my dvd iso's[FONT=Verdana]
Can you paste the error message verbatim from your Terminal? I'd like to see exactly what it says. And which command invokes this error. Thanks! [/FONT]

---

### Post by pana.corbului on 2007-05-19
It isn't actually an error. It's more a warning :P 

"mkisofs: Warning: -follow-links does not always work correctly; be careful.
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
          [COLOR="red"]use -input-charset to override.[/COLOR]"
Without overriding with --input-charset, after a while it begins building the iso. This warning appeared at the second iso till the last. First iso was clean of warnings.

And relating canonical commercial repository it seems that it downloads packages but I get this message "Release signature does not verify, use -v to see the gpg error".

I've made iso's for comercial and plf and comercial has 249 mb and plf 58,8 mb . Is it normal? That is the specific size?

---

### Post by BobSongs on 2007-05-19
> **pana.corbului said:**
> It isn't actually an error. It's more a warning :P 

"mkisofs: Warning: -follow-links does not always work correctly; be careful.
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
          [COLOR=red]use -input-charset to override.[/COLOR]"
Without overriding with --input-charset, after a while it begins building the iso. This warning appeared at the second iso till the last. First iso was clean of warnings.

And relating canonical commercial repository it seems that it downloads packages but I get this message "Release signature does not verify, use -v to see the gpg error".

I've made iso's for comercial and plf and comercial has 249 mb and plf 58,8 mb . Is it normal? That is the specific size?
[FONT=Verdana]The **Canonical Commercial** repositories are very, very small compared to the main repositories. Roughly the size you described at this point in time. The **PLF** repositories are even smaller.

Good to hear it's only a warning during DVD creation. I hope the DVDs are flawless.

As far as the "Release signature does not... blah, blah" I get that from time to time too. I have a theory about this. I believe we receive this message because someone is in the process of updating some files in the repositories. And this message appears until everything is recalibrated. This is my theory. And you're welcome to it. :)
[/FONT]

---

### Post by pana.corbului on 2007-05-20
I didn't get the chance to test DVDs, but monday is gonna be the day ;) (At work I have ISA server and it has enabled only http port...I can't download anything relating apt-get or snaptic ..this is the point where DVD's come in handy :D )

Later edit: I've removed ftp. I expected to have vizitors to download iso's but there was a lack of interest. I guess some prefer online repositories. 

 So far so good, I hope there're others who found this tutorial useful as I did.

---

### Post by dipodo on 2007-06-03
I have the following problem.......
after the download i run this command:

```
dipodo@dipodo-desktop:~$ debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=feisty,feisty-security,feisty-updates,feisty-backports --size=DVD ~/ubuntu/ ~/UbuntuDVDs/

```

and i get this output

```
Reading dists/feisty/main/binary-i386/Packages.gz... failed
No such file or directory - /home/dipodo/ubuntu//dists/feisty/main/binary-i386/Packages.gz
```

any ideas???? :(:(:(:(

---

### Post by BobSongs on 2007-06-08
> **dipodo said:**
> I have the following problem.......
after the download i run this command:

```
dipodo@dipodo-desktop:~$ debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=feisty,feisty-security,feisty-updates,feisty-backports --size=DVD ~/ubuntu/ ~/UbuntuDVDs/

```and i get this output

```
Reading dists/feisty/main/binary-i386/Packages.gz... failed
No such file or directory - /home/dipodo/ubuntu//dists/feisty/main/binary-i386/Packages.gz
```any ideas???? :(:(:(:(
[FONT=Verdana] Yeah. It's an easy one. You've probably already figured it out. Correct your code to this:[/FONT] > [FONT=Fixedsys]debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=feisty,feisty-security,feisty-updates,feisty-backports --size=DVD ~/UbuntuRepos/ ~/UbuntuDVDs/[/FONT]

---

### Post by frodon on 2007-06-08
Just in case you don't know it, some of you might be interested by APTonCD, it's a graphical tool to create a repository to burn on a CD/DVD (it's in the ubuntu repositories) :
[http://aptoncd.sourceforge.net/index.html](http://aptoncd.sourceforge.net/index.html)

Screenshots here :
[http://aptoncd.sourceforge.net/screenshots.html](http://aptoncd.sourceforge.net/screenshots.html)

---

### Post by BobSongs on 2007-06-09
> **frodon said:**
> Just in case you don't know it, some of you might be interested by APTonCD, it's a graphical tool to create a repository to burn on a CD/DVD (it's in the ubuntu repositories) :
[http://aptoncd.sourceforge.net/index.html](http://aptoncd.sourceforge.net/index.html)

Screenshots here :
[http://aptoncd.sourceforge.net/screenshots.html](http://aptoncd.sourceforge.net/screenshots.html)

[FONT=Verdana] Oui, merci beaucoup Frodon. Frodon's got a point. While it's not quite the same idea it is still something to have posted in this thread for reference sake.

AptOnCD lets you create a CD- or DVD-R from the .deb files downloaded when installing packages (software). You can spare yourself a lot of downloading time if you create a CD/DVD of your current setup files. AptOnCD does this quite nicely. Just make sure you never clear your downloads before doing this. And I believe Apt-on-CD is now appearing in the repositories.

This tutorial is slightly different in that it allows you to have an image of all available .deb files for a particular flavor of **ubuntu**.

It's a cool concept and I toyed with the idea of adding a note to the main tutorial. However, this post will do quite nicely.
[/FONT]    
:-D

---

### Post by cezar on 2007-07-04
where i find iso repository for dapper or feisty to download ?

can someone yo put on a server?; i am a newbie and i want to take it already done.

;)

---

### Post by Nythain on 2007-07-06
sorry to resurrect an old thread but i just want to make sure of something
im going to attempt this project, and incorporate step 9. Point APT Locally... so here's my questions

1. do i still need to make the iso's as mentioned in steps 4 and 5 or can i skip those steps since i will be installing locally

2. In step 9 you have
[FONT=Verdana]```

cd ~/UbuntuRepos && dpkg-scanpackages . /dev/null > Packages && gzip Packages && cd ~
```[/FONT]
i modified where the repo was downloaded to
/data/backup/repos/UbuntuRepos
so should i change your command to read more like
```

cd /data/backup/repos/UbuntuRepos && dpkg-scannpackages . /dev/null > Packages && gzip Packages && cd /data/backup/repos
```there's not much explanation on what each one of those commands is doing (wich is sorta easy to figure out) or if they have to be run from certain locations... like why the cd ~ at the very end... is that just so the user is back at thier familiar home directory or does it actually serve a purpose???

3. since i changed my download location im assuming in the sources.list i should make it look more like this
```

deb file:/data/backup/repos/UbuntuRepos ./

```whats the ./ for... am i going to need to change that too???
A side note on this question... If i download multiple repos (medibuntu/canonical/wine/) they are going to need thier own deb file: entries in sources.list also correct?

sorry to be a pest but i just want to make sure i have all this right BEFORE i download that much stuff :)


Edit: Well, everything is working great... thanks for this how to... combined with a little crontab research i now update my local repos once a week... so the next time i have to reinstall upgrading will be a snap... and if i ever find myself installing ubuntu on a friends pc without broadband, i can sleep easier knowing that they are up to date also :)

---

### Post by BobSongs on 2007-07-10
[FONT=Verdana]> **cezar said:**
> where i find iso repository for dapper or feisty to download ?

can someone yo put on a server?; i am a newbie and i want to take it already done.

;)

Sorry it took so long to respond. I'm not frequently here because I get so few posts. The tutorial pretty much covers everything.


cezar: the place you're looking to download from is: [ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/) and they've got pre-made ISOs for you. Hope that helps. The link was in my FAQ at the bottom of the tutorial.
[/FONT]

---

### Post by BobSongs on 2007-07-10
> **Nythain said:**
> sorry to resurrect an old threadIt's not actually that old. But you're welcome to ask questions.
> **Nythain said:**
> but i just want to make sure of something im going to attempt this project, and incorporate step 9. Point APT Locally... so here's my questions

1. do i still need to make the iso's as mentioned in steps 4 and 5 or can i skip those steps since i will be installing locallyOkay. Good question. The answer is: No. You don't have to. Use the local files to your heart's content. Keep them up-to-date and all will be well. The DVDs are for friends or family with slow connections. You can skip all DVD creation stuff.

> **Nythain said:**
>  2. In step 9 you have 
[FONT=Verdana]```

cd ~/UbuntuRepos && dpkg-scanpackages . /dev/null > Packages && gzip Packages && cd ~
```[/FONT]
i modified where the repo was downloaded to
/data/backup/repos/UbuntuRepos
so should i change your command to read more like
```

cd /data/backup/repos/UbuntuRepos && dpkg-scannpackages . /dev/null > Packages && gzip Packages && cd /data/backup/repos
```there's not much explanation on what each one of those commands is doing (wich is sorta easy to figure out) or if they have to be run from certain locations... like why the cd ~ at the very end... is that just so the user is back at thier familiar home directory or does it actually serve a purpose???

The original tutorial has been repaired. Pointing Apt locally was flawed. Then a member pointed out the correct way to "hack" sources.list and it works perfectly.

---

### Post by regomodo on 2007-07-11
hmm. well, it finally finished the download (almost 24hours) but it ended with an error.

I re entered the command for download but it hangs at a message.

> 
Parse Packages and Sources files and add to the file list everything therein

Shall i just assume it's scanning the ~/UbuntuRepos folder to see what has been downloaded?

---

### Post by regomodo on 2007-07-11
Ok. It was scanning itself and it know has downloaded fully. 

I now have a knew problem
```

ruby debcopy -l ~/UbuntuRepos/ ~/UbuntuDVDs/ubuntu0
```

doesn't work. I get 

> ruby: No such file or directory -- debcopy (LoadError)

I have ruby installed. Anyone with ideas?

---

### Post by regomodo on 2007-07-12
bump

---

### Post by cezar on 2007-07-12
@regomondo

try this > "http://www.howtoforge.com/dvd_images_of_ubuntu_repositories" > "6 About the script 'debcopy' "

@bobsongs

can i put repositories on cd-s ? more friends of mine have a cd-rw, not dvd-rw...how can i do this ?

P.S. thanks a lot for this tutorial and for link...

Best regards...

---

### Post by BobSongs on 2007-07-13
> **regomodo said:**
> Ok. It was scanning itself and it know has downloaded fully. 

I now have a knew problem
```

ruby debcopy -l ~/UbuntuRepos/ ~/UbuntuDVDs/ubuntu0
```doesn't work. I get 

I have ruby installed. Anyone with ideas?

[FONT=Verdana]Check out Step 2 again:[/FONT][INDENT]**[FONT=Verdana]cp /usr/share/doc/debpartial/examples/debcopy.gz ~[/FONT]**[/INDENT][FONT=Verdana]and[INDENT]**gunzip ~/debcopy.gz**[/INDENT]When **debpartial** is installed you get **debcopy** too. But you must extract it. If you want to place it in your **/bin** folder (it's in your command path so it will activate every time) that's an option. To place it in your **/bin** folder extract it like this:

```
sudo cp /usr/share/doc/debpartial/examples/debcopy.gz /bin
``````
sudo gunzip /bin/debcopy.gz
```Please note: this solution is untested. If it fails, let me know.[/FONT]

---

### Post by regomodo on 2007-07-13
> **cezar said:**
> @regomondo

try this > "http://www.howtoforge.com/dvd_images_of_ubuntu_repositories" > "6 About the script 'debcopy' "

cheers! That appears to have worked

@ BobSongs - yeah. i appeared to had jumped the gun there. pretty sure i started the download early in the morn/late at night at rejoined after the downloads.

---

### Post by xfile087 on 2007-07-14
Nice tutorial - very good idea indeed!

I just wanted to mention however that i'm running feisty and by adding:
> 
deb file:/home/[USER NAME HERE]/UbuntuRepos ./

to my repo list didn't do much. It still downloaded the packages from Ubuntu's servers. I had to add the following instead... And now it installs from my local mirror beautifully!

> deb file:/home/[USER NAME HERE]/UbuntuRepos/ feisty main multiverse restricted universe
deb file:/home/[USER NAME HERE]/UbuntuRepos/ feisty-security main multiverse restricted universe 

---

### Post by BobSongs on 2007-07-15
> **xfile087 said:**
> Nice tutorial - very good idea indeed!

I just wanted to mention however that i'm running feisty and by adding:


to my repo list didn't do much. It still downloaded the packages from Ubuntu's servers. I had to add the following instead... And now it installs from my local mirror beautifully!
[FONT=Verdana]Excellent. I'll add that to this tutorial.

As you can tell it is a patchwork of various efforts across the net. In the tutorial proper I make no claims of any originality. I'm just trying to consolidate info I've found here and there. Most of the work is ensuring everything still works, updating it for the most recent Ubuntu version and keeping the formatting to look good.
[/FONT]

---

### Post by CrazyCanuck on 2007-07-17
Good evening, or morning, depending on which side of the pond you are on!

I am 1 billion percent interested in creating my own AMD64 repository, as some others are doing right now.

I am trying to download everything using wget-1.10.2b, which is an X86 binary.  Am I correct in saying that this tutorial is based on a Linux-only method?  The program that was recommended for me to download (points to Wget) is hardly intuitive.  Has anyone used Wget in an WinXP environment yet?  If so, would you kindly post your complete method, perhaps using a real example of a repository you were successfully able to mirror?

For now, please let me know how to configure Wget.  I wish some of the brilliant programmers could at least try to write decent docs for the proggies they make.  :)

Regards,

CC

---

### Post by BobSongs on 2007-07-17
> **CrazyCanuck said:**
> ...I am 1 billion percent interested in creating my own AMD64 repository, as some others are doing right now.

I am trying to download everything using wget-1.10.2b, which is an X86 binary.  Am I correct in saying that this tutorial is based on a Linux-only method? ...Greetings fellow Canadian;

I'm aware of **wget** being part of the binaries under Linux and can be acquired and used in Windows and the Mac OS. The command is fairly simple: wget blah.

I believe you can get a bit more information on how to start using **wget** from [this particular thread]("http://ubuntuforums.org/showpost.php?p=351988&postcount=2"). Combine that with the data in my tutorial and it should reduce the number of challenges you'll face.

[Edit] The FAQs have links to 1) pre-made ISOs for downloading; 2) sites that make these very same DVDs and sell them for a nominal fee. It is indeed an Ubuntu tutorial and with small mods can work easily on mother Debian. Beyond pointing to pre-made ISOs I offer no support for this tutorial outside of Ubuntu. Forgive the chavinism, but trying to get this working in Windows (all 80 million flavors), DOS, Sparx, Sun O/S is so beyond the scope that it staggers the imagination. ;) [/edit]

---

### Post by CrazyCanuck on 2007-07-17
Thanks for the link.  I have already read this entire thread, all 5 pages of it.  That silly readme for Wget is 256kb long!  For something that is a simple command line, a 256kb help file?  I will try to sort the help file out, and if I continue to be confuzzled, I will respond.  I think inclusion of the Windows version of Wget, and how it should be configured, is a wise thing to do.  Some of us have been in transition for a very long time, for this very reason - no local repository.  Cheers!


NOTE:  Ack!  Something rather obvious has slipped through the cracks here.  Where are the official repository web site addressess?  As you can recall, I am still using WinXP (dislike it entirely), so I am not able to use an automated process to download deb packages like within Ubuntu..  I am using an AMD64 architecture, and have already confirmed compatibility with the rest of my rather barebones white box.  Wget needs to be told where to go to get the deb packages, right?

CC

---

### Post by BobSongs on 2007-07-19
> **CrazyCanuck said:**
> <snip>NOTE:  Ack!  Something rather obvious has slipped through the cracks here.  Where are the official repository web site addressess?  As you can recall, I am still using WinXP (dislike it entirely), so I am not able to use an automated process to download deb packages like within Ubuntu..  I am using an AMD64 architecture, and have already confirmed compatibility with the rest of my rather barebones white box.  Wget needs to be told where to go to get the deb packages, right?</snip>
I have my own issues with Windows XP, such as that box that appears asking if XP can search the MS website for drivers when a new part is connected... then NEVER finds anything. I hear it works now in Vista... but I've drawn the line with Windows XP.

With each new version I keep telling myself I'm just wasting my time. Now the switch is complete; our home operating system is Linux/Mac OS.

As to the locations of the source files, here's the basic web address:

[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

Browse until you find what you're looking for.

:-)

But I have a question: why do you want the repositories on DVD? They are not required if you have a high-speed Internet connection.

---

### Post by BobSongs on 2007-07-22
[FONT=Verdana]:popcorn: And now, the moment you've been waiting for!

It's time to do a breakdown of the **debmirror** command. 

**--nosource**
Don't include the source files. This helps reduce the download amount to around half.

**-m **or [/FONT][FONT=Verdana]**--md5sums**[/FONT]
[FONT=Verdana]This feature slows things down a bit. It's a give and take here. We lose speed but we're ensured of accurate downloads. You can turn this off to speed things up a tiny bit. The man page describes this switch as **paranoid and too slow**.

**--passive**
Download in passive mode. I think there are four people in the world who know what this means. If you bump into one they'll let you know, and you'll let me know. In the mean time, I keep it in because it works right with it in there.

**--host=archive.ubuntu.com**
This is the basic web address where the files we want are located. In this case the whole address is: [http://archive.ubuntu.com/](http://archive.ubuntu.com/) You can surf you way there. You won't find much except...

**--root=ubuntu/**
The root folder. This folder on archive.ubuntu.com contains the files we're looking for.

**--method=ftp**
**http** is slightly faster than the **ftp** option. The tutorial suggests the file transfer protocol.

**--progress**
Displays the hashmarks ##### that indicate the download progress. Useful to ensure the downloading is still continuing.

**--dist=lucid,lucid-security,lucid-updates,lucid-backports**
The distribution. The tutorial will always be based on the latest Long Term Edition. Modify this to meet your distribution's needs.

**--section=main,restricted,universe,multiverse**
These are the different divisions available. Main, for example, has the main elements of the Ubuntu installation. You won't find restricted software in main.

**--arch=i386**
The architecture the repository files were designed for. The default is **i386**, but can be modified for other systems, such as: **amd64**, **hppa**, **ia64**, **powerpc** or **sparc** depending on availability.

**~/UbuntuRepos**
The location where **debmirror** downloads the remote mirror locally. This can be modifed to any desired folder.

**--ignore-release-gpg**
This switch stops the command from failing (dropping to a command prompt) if the 'Release.gpg' file is missing. 

[COLOR=Red]**--timeout=seconds -t 120**[/COLOR]
Specifies the timeout to use for network operations (either FTP or rsync). Set this to a higher value if you experience failed downloads. Seen here are 120 seconds. (Thanks, Jocose! Jocose was kind enough to offer this clever tidbit after feeling the urge to wander through pages and pages and pages of **man** files. This nifty feature can be built into your command in case you get a drop out at, say midnight only to discover 8 hours later that you've only got 30 Mb's worth of files and 8 hours wasted. Depending on your drop-out times adjust this number accordingly.) 


The chances this stuff's actually useful to you are... well, close to nil. But it was fun researching it all and... as much as I'd like to be on Ubuntu's payroll... I probably won't see a dime. ;-) Then again: I'm not too sure how pleased they are that I'm letting everyone know how to download a boat-load of files from their servers. :(

So happy downloading.
[/FONT]

---

### Post by Jerubaal on 2007-07-24
I have found an ftp site to download the ISOs for Dapper, but they are located at [ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/]("ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/") and are only downloading at 29kb/s on my ultra fast university connection. 
Anyone know if there is a European location where I can download repository ISOs?

(Reason for asking: I can usually download 1Mb/s at work, but only via XP. Broadband is sadly not currently an option at home.)

---

### Post by aboutTOpullmyhairout on 2007-07-28
well i'm glad i found this as a few weeks back i could not for the life of me get kubuntu to access the net to save my life, if i had this dvd set before it could have saved me mega amounts of headaches. with that being said thank you for making such a clear tutorial, you :guitar:. 

is there an easy way i could merge the PLF to the Commercial Repo. ? i take the answer is no, because if it was easy then ya would have incuded answer in tutorial?

also i'm at step 3 currnetly and all is going well so far, expect me back if i have problems, and even if i don't i will be back to report how all went. 

un related but have any of you had adept remove files it is not supposed to? i went to uninstall a few things like say 3 or 4 then i hit commit and all the sudden it is nuking the kde packes(517 items it said to remove)

other question is Dapper worth switching to, i had edgy on my machine for like 8 months i liked it better then feisty, so i'm wondering is dapper going to have an edge on the others(others = edgy or feisty) in the stability department ? that is the way i'm leaning i got the install cd for dapper but just want the opinion of somebody who has had more experience with it then i

---

### Post by BobSongs on 2007-07-29
> is there an easy way i could merge the PLF to the Commercial Repo. ? i take the answer is no, because if it was easy then ya would have included answer in tutorial?[FONT=Verdana]Exactly. Your question is answered more or less in FAQs (Q3) at the bottom of the tutorial.

Any attempt to mingle repositories will be catastrophic. You would hate to lose 3 days worth of downloading in order to download the Canonical into the same folders. Very disappointing. Avoid this at all costs.

[/FONT]  > unrelated but have any of you had adept remove files it is not supposed to? i went to uninstall a few things like say 3 or 4 then i hit commit and all the sudden it is nuking the KDE packages (517 items it said to remove)[FONT=Verdana]I don't use **adept** so I've never gotten errors with it. ;-)[/FONT]

> other question is Dapper worth switching to, i had edgy on my machine for like 8 months i liked it better then feisty, so i'm wondering is dapper going to have an edge on the others(others = edgy or feisty) in the stability department ? that is the way i'm leaning i got the install cd for dapper but just want the opinion of somebody who has had more experience with it then i[FONT=Verdana]Well. Dapper has stability. That's guaranteed. It's been developed and tweaked and it's not new. However there are few new packages added to the repositories.

I just installed Feisty Fawn (skipped Edgy Eft completely). Going through the list of new packages... WOW!! So much is new. So there's the trade-off. You may lose some stability but you will gain a lot of new and newer software. You might lose access to certain packages you're used to (depending on your familiarity with Linux--you could compile from source everything you miss). It's a matter of trade-offs.

Hope it helps.[/FONT]

---

### Post by adinugro on 2007-08-04
hi,

say i have the dvd repos for feisty, how could i update my repo without downlaoding again all files but only those has update on it?

thx,

Daniel

---

### Post by BobSongs on 2007-08-06
> **adinugro said:**
> hi,

say i have the dvd repos for feisty, how could i update my repo without downlaoding again all files but only those has update on it?

thx,

Daniel[FONT=Verdana]Open the Terminal [/FONT][FONT=Verdana]*(Applications &#8594; Accessories &#8594; Terminal)*[/FONT][FONT=Verdana] and go to the folder where you initially ran **debmirror** (by default: your home folder) and run the command in **Step 3** again. This only makes an incremental update consuming roughly 10 minutes instead of 25 hours.[/FONT]

---

### Post by ftonti on 2007-08-18
AptOnCD now also has the possibility to download the repositories. What do you think of that?
And what about including most of the functionality discussed in this thread in AptOnCD? What would that sound like to you people?

Cheers

---

### Post by BobSongs on 2007-08-22
> **ftonti said:**
> AptOnCD now also has the possibility to download the repositories. What do you think of that?
And what about including most of the functionality discussed in this thread in AptOnCD? What would that sound like to you people?

Cheers
Well. I was unaware of Apt-on-CD was able to download entire repositories. Upon investigation it looks like this is true.

:cry: Guess it's time to tear down this tutorial, huh?

So: people: install [**[COLOR=black]Apt-on-CD[/COLOR]**]("http://aptoncd.sourceforge.net/download.html") from the Ubuntu repositories and you're off and running.

I'll leave this tutorial up for a while as people get used to Apt-on-CD. Then I'll request it be removed from the Tutorials dept.

Thanks all.

---

### Post by Nythain on 2007-08-25
please dont take it down... what harm can it cause staying up... i constantly reference it for syntax and whatnot... and since i already have the repos downloaded, i am not looking forward to switching to apt on cd anytime...

---

### Post by BobSongs on 2007-09-08
> **Nythain said:**
> please dont take it down... what harm can it cause staying up... i constantly reference it for syntax and whatnot... and since i already have the repos downloaded, i am not looking forward to switching to apt on cd anytime...
My word. Well. I'm glad to hear that you... and I imagine others... are referencing this tutorial.

While there are not many posts I perceive that the tutorial is fairly clear and doesn't require much in the way of further explanation. That's encouraging.

Excellent: I'll keep it up and running, and regularly attended. Questions? Fire away! I suppose one nice thing about this particular tutorial is: it is all done at the command line. If XWindows is down and broken one could access this site, and follow the tutorial using the command-line browser **lynx** and successfully complete their task. No doubt there's even a way to burn DVDs from the command-line too.

Still, bit of a mental stretch to believe someone would do this. Nevertheless the tutorial will remain alive and well. For those wishing to use **AptOnCD**: you have my approval. For those who want to do this simply from the command-line: the tutorial remains alive until the board insists **AptOnCD** has made it completely redundant. :)

---

### Post by glenn45 on 2007-09-15
Ei Bobsong!
No need to tear down this tutorial, i think. Even if there's apt-on-cd, some people may still have a need for this tutorial. After all, linux is about choice and this tutorial provides another option for downloading the repository besides the apt-on cd.

cheers!

---

### Post by 3rock on 2007-09-16
Please don't remove or stop maintaining this HowTo, it does a better job than APTonCD.

I did notice that they seem to have found a solution to one of the problems here...

As noted in APTonCD's release notes, a file called README.diskdefines in the discs root fixes some detection issues with APT.

```

#define DISKNAME  Ubuntu 7.04 "Feisty Fawn" - Release i386
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  i386
#define ARCHi386  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1

```

I tried Googling for more info about this file, but without success so far.

Hope this helps.

---

### Post by BobSongs on 2007-09-20
> **glenn45 said:**
> Ei Bobsong!
No need to tear down this tutorial, i think. Even if there's apt-on-cd, some people may still have a need for this tutorial. After all, linux is about choice and this tutorial provides another option for downloading the repository besides the apt-on cd.

cheers!

OK. I'll comply. This tutorial will remain online along side AptOnCD. It seems there are those who prefer the command-line to graphic tools. I suppose this is the case, seeing how Linux's origins are firmly rooted in the CLI.

I am open to suggestions and tips to improve the tutorial. In no way do I think it's perfect. I always return to it to tweak it here and there. Feel free to point out the imperfections.

Thanks to all who've made this my favorite HowTo.

---

### Post by harr986 on 2007-10-08
These instructions appear clear and easy to follow. However, when I got to step 3 I got the following.

djh@DJHdesktop:~$ debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=fiesty,fiesty-security,fiesty-updates,fiesty-backports --section=main,restricted,universe,multiverse --arch=i386 UbuntuRepos/ --ignore-release-gpg
Mirroring to UbuntuRepos/ from [ftp://anonymous@archive.ubuntu.com/ubuntu//](ftp://anonymous@archive.ubuntu.com/ubuntu//)
Arches: i386
Dists: fiesty,fiesty-security,fiesty-updates,fiesty-backports
Sections: main,restricted,universe,multiverse
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/fiesty/Release       # failed:Failed to open file.
dists/fiesty/Release failed md5sum check, removing
[0%] Getting: dists/fiesty/Release.gpg   # failed:Failed to open file.
dists/fiesty/Release.gpg failed md5sum check, removing
[0%] Getting: dists/fiesty-security/Release      # failed:Failed to open file.
dists/fiesty-security/Release failed md5sum check, removing
[0%] Getting: dists/fiesty-security/Release.gpg  # failed:Failed to open file.
dists/fiesty-security/Release.gpg failed md5sum check, removing
[0%] Getting: dists/fiesty-updates/Release       # failed:Failed to open file.
dists/fiesty-updates/Release failed md5sum check, removing
[0%] Getting: dists/fiesty-updates/Release.gpg   # failed:Failed to open file.
dists/fiesty-updates/Release.gpg failed md5sum check, removing
[0%] Getting: dists/fiesty-backports/Release     # failed:Failed to open file.
dists/fiesty-backports/Release failed md5sum check, removing
[0%] Getting: dists/fiesty-backports/Release.gpg         # failed:Failed to open file.
dists/fiesty-backports/Release.gpg failed md5sum check, removing
Errors:
 Download of dists/fiesty/Release failed: Failed to open file.
 Download of dists/fiesty/Release.gpg failed: Failed to open file.
 Download of dists/fiesty-security/Release failed: Failed to open file.
 Download of dists/fiesty-security/Release.gpg failed: Failed to open file.
 Download of dists/fiesty-updates/Release failed: Failed to open file.
 Download of dists/fiesty-updates/Release.gpg failed: Failed to open file.
 Download of dists/fiesty-backports/Release failed: Failed to open file.
 Download of dists/fiesty-backports/Release.gpg failed: Failed to open file.
Failed to download some Release or Release.gpg files!
WARNING: releasing 1 pending lock... 

Any idea what went wrong.

---

### Post by BobSongs on 2007-10-12
> **harr986 said:**
> These instructions appear clear and easy to follow. However, when I got to step 3 I got the following.

djh@DJHdesktop:~$ debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=fiesty,fiesty-security,fiesty-updates,fiesty-backports --section=main,restricted,universe,multiverse --arch=i386 UbuntuRepos/ --ignore-release-gpg
Mirroring to UbuntuRepos/ from [ftp://anonymous@archive.ubuntu.com/ubuntu//](ftp://anonymous@archive.ubuntu.com/ubuntu//)
Arches: i386
Dists: fiesty,fiesty-security,fiesty-updates,fiesty-backports
Sections: main,restricted,universe,multiverse
 ... 
Failed to download some Release or Release.gpg files!
WARNING: releasing 1 pending lock... 

Any idea what went wrong.

[FONT=Verdana]Yes. I know exactly what went wrong.

"'I' before 'E' except after 'C'.... and in the word *f**ei**sty*".

And... it's not your fault. I just checked the tutorial and found I misspelled it everywhere! Change the spelling and you'll be fine.[/FONT]

---

### Post by harr986 on 2007-10-12
Every thing is progressing well now. Thanks for catching my error.

---

### Post by harr986 on 2007-10-12
oops! everything not ¨every thing¨. My spelling and grammar skill leave a lot to be desired.

---

### Post by BobSongs on 2007-10-12
[font=Verdana]> **harr986 said:**
> oops! everything not ¨every thing¨. My spelling and grammar skill leave a lot to be desired.

Well. I did a search of the tutorial and found that every instance of "Feisty" was misspelled "Fiesty". It's a bad habit I have. Feisty is one of those spelling exceptions that throws me just about every time. So if you highlighted my own text and pasted it into the command... well, technically: I'm at fault.

Soooooo, we'll let it slide. *blush*[/font]

---

### Post by hobong on 2007-10-19
Hello,

I try to make Repository for Gusty and make some change to nearest server to get the files but seem something wrong ... 
I dont know why i just got little files ...  here's my log.

hobong@cinema:/media/sda6/GutsyRepo$ debmirror --nosource -m --passive --host=dl2.foss-id.web.id --root=ubuntu/ --method=http --progress --dist=gutsy,gutsy-security,gutsy-updates,gutsy-backports --section=main,restricted,universe,multiverse --arch=i386 UbuntuRepos/ --ignore-release-gpg
Mirroring to UbuntuRepos/ from [http://dl2.foss-id.web.id/ubuntu//](http://dl2.foss-id.web.id/ubuntu//)
Arches: i386
Dists: gutsy,gutsy-security,gutsy-updates,gutsy-backports
Sections: main,restricted,universe,multiverse
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/gutsy/Release... ok
[0%] Getting: dists/gutsy/Release.gpg... ok
[0%] Getting: dists/gutsy-security/Release... ok
[0%] Getting: dists/gutsy-security/Release.gpg... ok
[0%] Getting: dists/gutsy-updates/Release... ok
[0%] Getting: dists/gutsy-updates/Release.gpg... ok
[0%] Getting: dists/gutsy-backports/Release... ok
[0%] Getting: dists/gutsy-backports/Release.gpg... ok
Get Packages and Sources files and other miscellany.
dists/gutsy/main/binary-i386/Packages.gz needs fetch
[  0%] Getting: dists/gutsy/main/binary-i386/Packages.gz... ok
dists/gutsy/main/binary-i386/Release needs fetch
[ 24%] Getting: dists/gutsy/main/binary-i386/Release... ok
dists/gutsy/restricted/binary-i386/Packages.gz needs fetch
[ 24%] Getting: dists/gutsy/restricted/binary-i386/Packages.gz... ok
dists/gutsy/restricted/binary-i386/Release needs fetch
[ 24%] Getting: dists/gutsy/restricted/binary-i386/Release... ok
dists/gutsy/universe/binary-i386/Packages.gz needs fetch
[ 24%] Getting: dists/gutsy/universe/binary-i386/Packages.gz... ok
dists/gutsy/universe/binary-i386/Release needs fetch
[ 97%] Getting: dists/gutsy/universe/binary-i386/Release... ok
dists/gutsy/multiverse/binary-i386/Packages.gz needs fetch
[ 97%] Getting: dists/gutsy/multiverse/binary-i386/Packages.gz... ok
dists/gutsy/multiverse/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy/multiverse/binary-i386/Release... ok
dists/gutsy-security/main/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-security/main/binary-i386/Packages.gz... ok
dists/gutsy-security/main/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-security/main/binary-i386/Release... ok
dists/gutsy-security/restricted/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-security/restricted/binary-i386/Packages.gz... ok
dists/gutsy-security/restricted/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-security/restricted/binary-i386/Release... ok
dists/gutsy-security/universe/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-security/universe/binary-i386/Packages.gz... ok
dists/gutsy-security/universe/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-security/universe/binary-i386/Release... ok
dists/gutsy-security/multiverse/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-security/multiverse/binary-i386/Packages.gz... ok
dists/gutsy-security/multiverse/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-security/multiverse/binary-i386/Release... ok
dists/gutsy-updates/main/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-updates/main/binary-i386/Packages.gz... ok
dists/gutsy-updates/main/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-updates/main/binary-i386/Release... ok
dists/gutsy-updates/restricted/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-updates/restricted/binary-i386/Packages.gz... ok
dists/gutsy-updates/restricted/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-updates/restricted/binary-i386/Release... ok
dists/gutsy-updates/universe/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-updates/universe/binary-i386/Packages.gz... ok
dists/gutsy-updates/universe/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-updates/universe/binary-i386/Release... ok
dists/gutsy-updates/multiverse/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-updates/multiverse/binary-i386/Packages.gz... ok
dists/gutsy-updates/multiverse/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-updates/multiverse/binary-i386/Release... ok
dists/gutsy-backports/main/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-backports/main/binary-i386/Packages.gz... ok
dists/gutsy-backports/main/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-backports/main/binary-i386/Release... ok
dists/gutsy-backports/restricted/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-backports/restricted/binary-i386/Packages.gz... ok
dists/gutsy-backports/restricted/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-backports/restricted/binary-i386/Release... ok
dists/gutsy-backports/universe/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-backports/universe/binary-i386/Packages.gz... ok
dists/gutsy-backports/universe/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-backports/universe/binary-i386/Release... ok
dists/gutsy-backports/multiverse/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-backports/multiverse/binary-i386/Packages.gz... ok
dists/gutsy-backports/multiverse/binary-i386/Release needs fetch
[100%] Getting: dists/gutsy-backports/multiverse/binary-i386/Release... ok
Parse Packages and Sources files and add to the file list everything therein.
Download all files that we need to get (38 MiB).
Downloaded 38 MiB in 173s at 219.86 kiB/s
Everything OK. Moving meta files.
Cleanup mirror.
All done.
hobong@cinema:/media/sda6/GutsyRepo$ 

There's are no deb file in those directories .. anyone could help ?
Thx

---

### Post by kcbnac on 2007-10-23
I am also running a script (found here: [https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror) )

I've documented it on the following forum post (both code and results)

[http://ubuntuforums.org/showthread.php?p=3613689](http://ubuntuforums.org/showthread.php?p=3613689)

---

### Post by BobSongs on 2007-10-26
[FONT=Verdana]> **hobong said:**
> Hello,

I try to make Repository for Gusty and make some change to nearest server to get the files but seem something wrong ... 
I dont know why i just got little files ...  here's my log. 

(removed, see post above.)

There's are no deb file in those directories .. anyone could help ?
Thx

Okay.

My kind friend, the GoogleNinja, did his usual bit of fancy keyboard work and managed to get an answer or two.

It would appear this is a problem with Gutsy Gibbon alone. The problem is with [/FONT]   [FONT=Verdana][COLOR=Sienna]**libcompress-zlib-perl**[/COLOR][/FONT][FONT=Verdana] (as appears in [**this post**]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg444176.html").) This is a known bug. And [**it is inherited**]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=435656") from grandpa **Debian**. A warning has been posted at the head of the tutorial.

It would appear, from these posts, that [/FONT][FONT=Verdana][COLOR=Sienna]**libcompress-zlib-perl_2.005-2**[/COLOR][/FONT][FONT=Verdana] would be the solution.

And where exactly do we find this? Well, verify with Synaptic or Apt-Get. Or wait until the update trickles down from Debian to Ubuntu. Its severity is listed as [/FONT][FONT=Verdana][COLOR=Red]**grave**[/COLOR][/FONT][FONT=Verdana] in the Debian report. So this may require a bit of patience on our part.

________________________
[COLOR=Sienna]**Edit:**[/COLOR] Well. At the time I saw your post, **hobong**, I was working in Windows XP & Mac OS. Now I'm back in Feisty. I gave the code a whirl:

(debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=gutsy,gutsy-security,gutsy-updates,gutsy-backports --section=main,restricted,universe,multiverse --arch=i386 UbuntuRepos/ --ignore-release-gpg)

And it's working 100% -- and I'm downloading [COLOR=Olive]**Gutsy**[/COLOR]'s repositories like there's no tomorrow.

[COLOR=black]**It is confirmed:** this problem is related to *Gutsy Gibbon alone*. I was unaware of the problem. Had I known I would have posted the warning earlier.

[Note] For those reading through this thread, this should no longer be a problem. The source file has been repaired and is now in the repositories as an update. This post remains for historical reasons.
[/COLOR] [/FONT]

---

### Post by lunamystry on 2007-10-27
I need to be sure. 

can i now make the gutsy repo DVD? 
I ran this: (debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=gutsy,gutsy-security,gutsy-updates,gutsy-backports --section=main,restricted,universe,multiverse --arch=i386 UbuntuRepos/ --ignore-release-gpg)

and what I get looks similar to what hobong got. But i have hash(#) instead of ok

---

### Post by BobSongs on 2007-10-27
> **lunamystry said:**
> I need to be sure. 

can i now make the gutsy repo DVD? 
I ran this: (debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=gutsy,gutsy-security,gutsy-updates,gutsy-backports --section=main,restricted,universe,multiverse --arch=i386 UbuntuRepos/ --ignore-release-gpg)

and what I get looks similar to what hobong got. But i have hash(#) instead of ok

[COLOR=Silver] Well, if you looked at the introduction of the tutorial you'll see a clear warning that **if you have installed and are running Gutsy Gibbon (7.10)** you should NOT be able to download the Gutsy Gibbon repositories. The answer why is detailed above. I'll agree this is a total drag. I've got no solution up my sleeve except: download the repos BEFORE you upgrade to Gutsy. Gutsy's getting great reviews. Period. But do the repository download be**fore** you upgrade. [COLOR=Black]<- no longer valid. Error has been repaired.[/COLOR][/COLOR]

Either that or contact someone who's still using Feisty/Edgy/Dapper/Breezy/Warty/Hoary and beg them for the DVDs. I've got no other solution at present. We're all waiting for libcompress-zlib-perl to be upgraded to libcompress-zlib-perl_2.005-2 (see previous posts) before everything is resovled. It's a bug: not an attempt to discourage downloading.

I successfully downloaded the Gutsy Gibbon repos in Feisty (I haven't upgraded yet). Hope this answers your question.

---

### Post by lunamystry on 2007-10-28
OH!! so If I am in Feisty I can made the DVD's? I'll just install Feisty because i am the only person who is using Ubuntu that i can ask for the DVD. 

Thank you.

---

### Post by BobSongs on 2007-10-28
> **lunamystry said:**
> OH!! so If I am in Feisty I can made the DVD's? I'll just install Feisty because i am the only person who is using Ubuntu that i can ask for the DVD.

Thank you.
If you still have Feisty Fawn installed on your computer, you're ready to download the Gutsy Gibbon repositories if you follow this tutorial.

Gutsy's current problem is that it cannot download the **Gutsy** repositories - just the Gutsy repositories. Gutsy can only download these repositories (currently):

Dapper Drake
Edgy Eft
Feisty Fawn

Gutsy cannot download these repositories:

Gutsy Gibbon

[Edit] Error repaired. Subject is no longer valid.

---

### Post by lunamystry on 2007-10-31
I apologise if this is a stupid question but while ubuntu was still in the beta phase of testing i followed the guide and I think it worked I don't know but I have four iso images left over from the time i followed it the first time. 

Did it wotk or is it just nothing in those Iso images? If it worked do i burn each iso image in its own disc because the link provided in the first thread page does not explain how to combine the four images if it is even possible.

---

### Post by k3lt01 on 2007-11-03
This is probably a really dumb question but can I add other repositories to the download. Things like Medibuntu and UbuntuStudio or the Google Repositories. If I can what do I do? Do I just add the repo name in the list or Is there more to it? There seem to be heaps of Repos available on the net so I am interested in the possibility of adding them to the download (either entirely or partially)

For what its worth I am currently downloading Feisty, I will download Gutsy when Feisty has finished.

---

### Post by BobSongs on 2007-11-03
> **k3lt01 said:**
> This is probably a really dumb question but can I add other repositories to the download. Things like Medibuntu and UbuntuStudio or the Google Repositories. If I can what do I do? Do I just add the repo name in the list or Is there more to it? There seem to be heaps of Repos available on the net so I am interested in the possibility of adding them to the download (either entirely or partially)

For what its worth I am currently downloading Feisty, I will download Gutsy when Feisty has finished.

[font=Verdana]It's not a dumb question at all. In fact, it's a frequently asked question. This would then make it an FAQ. And if you scroll down to the very bottom of the tutorial you'll find your question there. And you'll find its answer there too. :) So, I can say: I don't need to answer this one. Yay.[/font]

---

### Post by BobSongs on 2007-11-14
> **lunamystry said:**
> I apologise if this is a stupid question but while ubuntu was still in the beta phase of testing i followed the guide and I think it worked I don't know but I have four iso images left over from the time i followed it the first time. 

Did it work or is it just nothing in those Iso images? If it worked do i burn each iso image in its own disc because the link provided in the first thread page does not explain how to combine the four images if it is even possible.[FONT=Verdana]Forgive me for completely ignoring this post! This was not deliberate. I'm sometimes too hasty when reading.

If you have ISO images of Gutsy Gibbon on your Hard Disk Drive then you've done the tutorial successfully: even if it is the Gutsy Gibbon repos.
[/FONT]

---

### Post by jms1989 on 2007-11-15
Hi, I was wondering if I could create a new repository for private use are public when I can upload to a server?

I have setup a directory with apache2, php5, mysql5. I'm wanting to add deb packages to it and maby source packages but I'm unsure what directory structure I should follow. What commands I should run to update the packages file for synaptic, apt, and that other program to read?

I like the tutorial but I'm going to wait until I have enough free space to download the repositories. My biggest hard drive is just loaded with vmware OSes and video. I'm down to 24.5GB free out of 181GB. So when I do download them, I'll go for feisty and maby Gutsy.

Can anybody tell me how big those repositories are with and without sources for dapper, edgy, feisty, and gutsy?

Thanks.

---

### Post by BobSongs on 2007-11-18
> **jms1989 said:**
> Hi, I was wondering if I could create a new repository for private use are public when I can upload to a server?[FONT="Verdana"]I imagine there's no trouble with that. I think you may even find a tutorial either in this forum or elsewhere on how to create a publicly available repository. I know I've seen one, but I cannot recall where.[/FONT]

> **jms1989 said:**
> I have setup a directory with apache2, php5, mysql5. I'm wanting to add deb packages to it and maybe source packages but I'm unsure what directory structure I should follow. What commands I should run to update the packages file for synaptic, apt, and that other program to read?[FONT="Verdana"]See above.[/FONT]

> **jms1989 said:**
> I like the tutorial but I'm going to wait until I have enough free space to download the repositories. My biggest hard drive is just loaded with vmware OSes and video. I'm down to 24.5GB free out of 181GB. So when I do download them, I'll go for feisty and maby Gutsy.

Can anybody tell me how big those repositories are with and without sources for dapper, edgy, feisty, and gutsy?[FONT="Verdana"]If I recall, the Gutsy repositories **without** the source codes was approximately 19 Gigabytes... but I could be off by a few Gigs.

I hope that answers your question. Either way: before you can offer your services as a provider, you'll need the Hard Disk Drive space for these numerous files. I suppose, by the time you free up some space, you'll have found the tutorial to create a local set of publicly available repos.

When you do, feel free to send me a Private Message and I'll add it to the main tutorial.[/FONT]

:D

---

### Post by pietjanjaap on 2007-11-24
Thanks very good explaining. :):):lolflag:

Just backup up everything.
Also found warty and newer(older) ubuntu versions.

---

### Post by jocose on 2007-12-05
> **BobSongs said:**
> 
Gutsy's current problem is that it cannot download the **Gutsy** repositories - just the Gutsy repositories.

**[COLOR="Red"]This may be resolved shortly. Keep your eyes on the following page for news regarding libcompress-zlib-perl 2.005-1ubuntu0.2:[/COLOR]**

[COLOR="DarkGreen"]**Unable to download packages using Gutsy debmirror[/COLOR]**
[https://bugs.launchpad.net/ubuntu/+source/libcompress-zlib-perl/+bug/136634](https://bugs.launchpad.net/ubuntu/+source/libcompress-zlib-perl/+bug/136634)

---

### Post by jocose on 2007-12-05
Good news for Gutsy users, libcompress-zlib-perl (2.005-1ubuntu0.2) is now available in the updates repository.

From the changelog for the .deb in the Gutsy Updates repo:

> libcompress-zlib-perl (2.005-1ubuntu0.2) gutsy-updates; urgency=low

  * No-change upload of the -proposed version to -updates. For some reason
    gutsy-updates only got the source package copied. (LP: #136634)

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 05 Dec 2007 09:21:52 +0100

libcompress-zlib-perl (2.005-1ubuntu0.1) gutsy-proposed; urgency=low

  * Make debmirror work again instead of dropping the entire contents of pool/
    and not downloading anything:
    Add patch 02_restore-gzreadline-record-separator-behaviour.patch:
    Hard-codes "\n" as record separator (do not mangle with the *global* $/,
    but set it to "\n" locally) before calling $gz->getline for the
    actual read. (LP: #136634)

 -- Cesare Tirabassi <norsetto@ubuntu.com>  Wed, 31 Oct 2007 15:55:50 +0100

 Update libcompress-zlib-perl now and give this How-To a try and post your results.

---

### Post by jocose on 2007-12-05
May I suggest an additional tip for this page/post:
[http://ubuntuforums.org/showpost.php?p=3060394&postcount=49](http://ubuntuforums.org/showpost.php?p=3060394&postcount=49)

@BobSongs:
> Should the download stop unexpectedly, simply re-run the same command.

Yes, this works, but in the debmirror man page I found something better:

> --timeout=seconds -t
Specifies the timeout to use for network operations (either FTP or rsync).  Set this to a higher value if you experience failed down&#8208;loads. Defaults to 300 seconds.


---

### Post by BobSongs on 2007-12-06
Yay! Thanks, jocose. I'll make mention of it on the first page. I'll post a link directly to your posts!

Many thanks, merci beaucoup!

I'm glad to hear this issue's been resolved.

I appreciate being kept up to date. Seems this humble lil' tutorial gets a fair number of viewings. ;-)


:D

---

### Post by BobSongs on 2007-12-06
> **jocose said:**
> May I suggest an additional tip for this page/post:
[http://ubuntuforums.org/showpost.php?p=3060394&postcount=49](http://ubuntuforums.org/showpost.php?p=3060394&postcount=49)

@BobSongs:


Yes, this works, but in the debmirror man page I found something better:

lol

Excellent! You see? It's posts exactly like yours that make a tutorial like this one worth trying and maintaining.

I'll make mention of it and post your name as the submitter of a better approach.

Thanks again, **jocose**!

---

### Post by BobSongs on 2007-12-06
> **Jerubaal said:**
> I have found an ftp site to download the ISOs for Dapper, but they are located at [ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/) and are only downloading at 29kb/s on my ultra fast university connection. 
Anyone know if there is a European location where I can download repository ISOs?

(Reason for asking: I can usually download 1Mb/s at work, but only via XP. Broadband is sadly not currently an option at home.)Forgive the long delay.

Yes. This is the only site of its kind I know of that offers pre-made ISOs for downloading. I appreciate the slowness of teh connection, but patience is indeed the order of the day when someone offers a free service.

Forgive the delay: I didn't see your post at all. I know you've gotten your ISOs by now. *blush*

---

### Post by k3lt01 on 2007-12-31
Sorry again to be a pain in the proverbial but I wondered what would the commands be to add UbuntuStudio to the Repositories. I currently only have an internet connection on my laptop and want to add UbuntuStudio to my desktop so the only way I can think of to do that is by downloading the repo (if indeed there is one available) and to install it by cd.

---

### Post by k3lt01 on 2007-12-31
I just tried to do the canonical repo without success. Here is my output.

```
michael@michael-laptop:~$ debmirror --nosource -m --passive --host=archive.canonical.com --root=ubuntu/ --method=http --progress --dist=gutsy-commercial --section=main --arch=i386 CanonicalRepos/ --ignore-release-gpg
Mirroring to CanonicalRepos/ from http://archive.canonical.com/ubuntu//
Arches: i386
Dists: gutsy-commercial
Sections: main
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.

Get Release files.
[0%] Getting: dists/gutsy-commercial/Release... dists/gutsy-commercial/Release failed 404 Not Found
dists/gutsy-commercial/Release failed md5sum check, removing
[0%] Getting: dists/gutsy-commercial/Release.gpg... dists/gutsy-commercial/Release.gpg failed 404 Not Found
dists/gutsy-commercial/Release.gpg failed md5sum check, removing
Errors:
Failed to download some Release or Release.gpg files!
WARNING: releasing 1 pending lock...
 Download of dists/gutsy-commercial/Release failed: 404 Not Found Download of dists/gutsy-commercial/Release.gpg failed: 404 Not Foundmichael@michael-laptop:~$ 
michael@michael-laptop:~$ 

```
Anyone have any ideas what's wrong? The PLF repo downloaded with a problem.

---

### Post by BobSongs on 2007-12-31
[FONT="Verdana"]> **k3lt01 said:**
> I just tried to do the canonical repo without success...

<snip>

Anyone have any ideas what's wrong? The PLF repo downloaded with a problem.
Well, I'm not sure if the repositories are down at the moment, k3lt01. But I'll have a look. I've got some free time. Let's see what I can find.

Bob[/FONT]

---

### Post by smartboyathome on 2007-12-31
By the way, for faster downloading times from repositories, you can use the Software Sources tool in System > Administration (it is also able to be reached from synaptic, by going to Settings > Repositories. Click the Download from dropdown menu and select other, then click the Select Best Server button in the window that comes up.

---

### Post by BobSongs on 2007-12-31
> **k3lt01 said:**
> I just tried to do the canonical repo without success. Here is my output.

```
michael@michael-laptop:~$ debmirror --nosource -m --passive --host=archive.canonical.com --root=ubuntu/ --method=http --progress --dist=gutsy-commercial --section=main --arch=i386 CanonicalRepos/ --ignore-release-gpg
Mirroring to CanonicalRepos/ from http://archive.canonical.com/ubuntu//
Arches: i386
Dists: gutsy-commercial
Sections: main
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.

Get Release files.
[0%] Getting: dists/gutsy-commercial/Release... dists/gutsy-commercial/Release failed 404 Not Found
dists/gutsy-commercial/Release failed md5sum check, removing
[0%] Getting: dists/gutsy-commercial/Release.gpg... dists/gutsy-commercial/Release.gpg failed 404 Not Found
dists/gutsy-commercial/Release.gpg failed md5sum check, removing
Errors:
Failed to download some Release or Release.gpg files!
WARNING: releasing 1 pending lock...
 Download of dists/gutsy-commercial/Release failed: 404 Not Found Download of dists/gutsy-commercial/Release.gpg failed: 404 Not Foundmichael@michael-laptop:~$ 
michael@michael-laptop:~$ 

```Anyone have any ideas what's wrong? The PLF repo downloaded with a problem.
Well. I gather by the code that you're attempting to download the Canonical commercial software. You've probably taken this code from the FAQ from the tutorial.

No worries about that. However, it appears the file structure over at archive.canonical.com has been modified somewhat.

What I did to compose that part of the tutorial was use a browser to surf archive.canonical.com. I compared what I found to archive.ubuntu.com and created the correct paths in the proposed command. It worked well at the time.

However, it would appear that just as rivers change their courses through time, so do file structures at large servers. So, give me a bit of time to recall what it is I did to get this working. I'll post my findings here and then correct the FAQ.

Bob

---

### Post by BobSongs on 2008-01-01
[FONT=Verdana]OK. I just looked at the latest file structure of the archives.canonical.com site. Here's my initial correction. Kindly notify me if successful:[/FONT]

```
debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=gutsy,gutsy-backports,gutsy-security,gutsy-updates,gutsy-proposed --section=partner --arch=binary-i386 CanonicalRepos/ --ignore-release-gpg
```.

[FONT=Verdana]Here it is *out* of the code box for your examination:[/FONT]

[FONT=Courier New]debmirror
  --nosource
  -m
  --passive
  --host=archive.canonical.com
  --root=/
  --method=ftp
  --progress
  --dist=[COLOR=Red]**gutsy**[/COLOR],[COLOR=Red]**gutsy**[/COLOR]-backports,[COLOR=Red]**gutsy**[/COLOR]-security,[COLOR=Red]**gutsy**[/COLOR]-updates,[COLOR=Red]**gutsy**[/COLOR]-proposed
  --section=partner
  --arch=[COLOR=Red]**binary-i386**[/COLOR]
  CanonicalRepos/
  --ignore-release-gpg[/FONT]

---

### Post by k3lt01 on 2008-01-01
First of all Bob I want to thank you for your continued help with this thread. I am learning alot here through the help of people like you. Linux is not an easy OS to learn when all you have dealt with is Windows, but with help from others people like me stick it out and learn more and in turn want to help others to (at the very least I can point people to threads here on the forum).

Ok now to business. I tried your correction and it seemed really promising but still nothing unfortunately. Here is the code produced.

```

michael@michael-laptop:~$ debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=gutsy,gutsy-backports,gutsy-security,gutsy-updates,gutsy-proposed --section=partner --arch=binary-i386 CanonicalRepos/ --ignore-release-gpg
Mirroring to CanonicalRepos/ from http://archive.canonical.com///
Arches: binary-i386
Dists: gutsy,gutsy-backports,gutsy-security,gutsy-updates,gutsy-proposed
Sections: partner
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/gutsy/Release... ok
[0%] Getting: dists/gutsy/Release.gpg... ok
[0%] Getting: dists/gutsy-backports/Release... ok
[0%] Getting: dists/gutsy-backports/Release.gpg... ok
[0%] Getting: dists/gutsy-security/Release... ok
[0%] Getting: dists/gutsy-security/Release.gpg... ok
[0%] Getting: dists/gutsy-updates/Release... ok
[0%] Getting: dists/gutsy-updates/Release.gpg... ok
[0%] Getting: dists/gutsy-proposed/Release... ok
[0%] Getting: dists/gutsy-proposed/Release.gpg... ok
Get Packages and Sources files and other miscellany.
Parse Packages and Sources files and add to the file list everything therein.
Download all files that we need to get (1 MiB).
Downloaded 1 MiB in 21s at 1.67 kiB/s
Everything OK. Moving meta files.
Cleanup mirror.
All done.
michael@michael-laptop:~$ 

```

I would be sure there is more than 1MiB of data on Canonical's server so I am thinking there is another problem somewhere.

Now I know how you worked out the code to do the download I will take a look at the website later when I have alot of time to spare and learn through hands on trial and error.

Thanks again Bob.
Michael.

---

### Post by k3lt01 on 2008-01-01
> **BobSongs said:**
> [FONT="Verdana"]OK. I just looked at the latest file structure of the archives.canonical.com site. Here's my initial correction. Kindly notify me if successful:[/FONT]

```
debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=gutsy,gutsy-backports,gutsy-security,gutsy-updates,gutsy-proposed --section=partner --arch=binary-i386 CanonicalRepos/ --ignore-release-gpg
```.

[FONT="Verdana"]Here it is *out* of the code box for your examination:[/FONT]

[FONT="Lucida Console"]debmirror
  --nosource
  -m
  --passive
  --host=archive.canonical.com
  --root=/
  --method=ftp
  --progress
  --dist=[COLOR="Red"]**gutsy**[/COLOR],[COLOR="Red"]**gutsy**[/COLOR]-backports,[COLOR="Red"]**gutsy**[/COLOR]-security,[COLOR="Red"]**gutsy**[/COLOR]-updates,[COLOR="Red"]**gutsy**[/COLOR]-proposed
  --section=partner
  --arch=[COLOR="Red"]**binary-i386**[/COLOR]
  CanonicalRepos/
  --ignore-release-gpg[/FONT]

You caught me out here actually. In the "out of the box" code you have --method=ftp while "in the box" you have --method=http.

I have been playing with the code a little bit and still get no more than the above post. It is interesting trying to work through this.

---

### Post by BobSongs on 2008-01-01
[FONT=Verdana]Well, **k3lt01**, I'm pleased to report that the tutorial has been repaired. You can now highlight the Canonical Repositories, make modifications to the command-line (like replacing dapper for gutsy) and away you go.

Sorry it took so long.

I've been looking at ways to create a bootable USB pen drive. However, I do not believe, after much testing, that this motherboard CAN boot to a pen drive.

*sigh*

And some of the instructions at [**this site**]("http://www.pendrivelinux.com/") required the use of Windows to accomplish the tasks. So I was unable to test any findings.
[/FONT]

---

### Post by k3lt01 on 2008-01-01
Thanks Bob. Your efforts are much appreciated. It is working a dream now.

---

### Post by k3lt01 on 2008-01-02
I have found a problem with the code you adjusted, I thought I had better post it here so you can fix it.

Your code had:

```
 debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=dapper,dapper-backports,dapper-proposed,dapper-security,dapper-updates --section=partner --arch=i386 [COLOR="Red"]UbuntuRepos[/COLOR]/ --ignore-release-gpg 
```

After I downloaded this I started downloading the Ubuntu repos and found the canonical ones went missing, So I changed the code to this:

```
debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=dapper,dapper-backports,dapper-proposed,dapper-security,dapper-updates --section=partner --arch=i386 [COLOR="Red"]CanonicalRepos[/COLOR]/ --ignore-release-gpg 
```

Of course adjusting from Dapper to Gutsy as required.

Hope this helps a bit.

---

### Post by BobSongs on 2008-01-05
> **k3lt01 said:**
> I have found a problem with the code you adjusted, I thought I had better post it here so you can fix it.

Your code had:

```
 debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=dapper,dapper-backports,dapper-proposed,dapper-security,dapper-updates --section=partner --arch=i386 [COLOR=Red]UbuntuRepos[/COLOR]/ --ignore-release-gpg 
```After I downloaded this I started downloading the Ubuntu repos and found the canonical ones went missing, So I changed the code to this:

```
debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=dapper,dapper-backports,dapper-proposed,dapper-security,dapper-updates --section=partner --arch=i386 [COLOR=Red]CanonicalRepos[/COLOR]/ --ignore-release-gpg 
```Of course adjusting from Dapper to Gutsy as required.

Hope this helps a bit.
[FONT=Verdana]Yikes! I hope you didn't execute that code! :( Duhh. I was so interested in ensuring the code worked properly that I evidently forgot to make all the proper changes to it.

I thank you for correction. I may never have noticed it.

To create the original debmirror code for the Canonical Commercial repos, I took the original command and modified it based on what was available at the archives.canonical.com website. I did the same again but I was focused on making it simply *work*. And that it did. But I didn't have anything in those folders.

I hope the "repaired" code didn't cause you to lose your files. :'( Forgive my error if it did.

Modifications completed. Tutorial now properly formed. Thanks.
[/FONT]

---

### Post by BobSongs on 2008-02-04
> **cezar said:**
> can i put repositories on cd-s ? more friends of mine have a cd-rw, not dvd-rw...how can i do this ?

I've since tweaked the tutorial. But quickly: replace DVD with CD80 or CD74 and you've got CDs for repositories instead of DVDs. Check out the main tutorial.

---

### Post by BobSongs on 2008-02-04
> **k3lt01 said:**
> This is probably a really dumb question but can I add other repositories to the download. Things like Medibuntu and UbuntuStudio or the Google Repositories. If I can what do I do? Do I just add the repo name in the list or Is there more to it? There seem to be heaps of Repos available on the net so I am interested in the possibility of adding them to the download (either entirely or partially)

For what its worth I am currently downloading Feisty, I will download Gutsy when Feisty has finished.
Tell you what: give me the UbuntuStudio and Google repository links and I'll add them to the FAQ with Canonical Commercial and MediBuntu.

---

### Post by k3lt01 on 2008-02-13
> **BobSongs said:**
> Tell you what: give me the UbuntuStudio and Google repository links and I'll add them to the FAQ with Canonical Commercial and MediBuntu.

Google's deb line: deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
Ubuntu Studio doesn't seem to do a repo anymore, they did with Feisty but it was removed when Gutsy come out. Now to do Gusty you just go to their site and follow the apt-get instructions.

Sorry for taking so long to reply.

---

### Post by BobSongs on 2008-02-15
> **k3lt01 said:**
> Google's deb line: deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
Ubuntu Studio doesn't seem to do a repo anymore, they did with Feisty but it was removed when Gutsy come out. Now to do Gusty you just go to their site and follow the apt-get instructions.

Sorry for taking so long to reply.Hey: no hassles. I don't check this tutorial out too often simply because many good folks like yourself have contributed to it making it fairly air-tight. The FAQs answer many of the niggling questions people have.

Also: this isn't one of those incredibly important threads like: [**"How to Restore Grub when it gets All Screwed Up"**]("http://ubuntuforums.org/showthread.php?t=224351"). People who drop in on those threads are usually there because they're trying to "put out a fire", so to speak. I mean: compared to one's GrUB being messed up... a massive download is not terribly exciting. :roll:

But adding more repositories to my FAQ is more a mental challenge for me. I just hope to put enough into my tutorial to make it really rich, albeit not everyone's cup of tea. But when one is drawn to it one finds everything there. That's immensely satisfying for me.

**Note**: I did some research on the Google repositories. I found a link to Feisty Fawn repos, but the link failed as far as the browser is concerned. So I imagine more work will be required before finding them to add them.

Many thanks for the effort! Your link is what I found too. So, I'll take up my magnifying glass, I'll call Dr. Watson and off we'll go to find more repositories.

---

### Post by k3lt01 on 2008-02-17
Here is a link to an SIL repository that I would really like to download and put on to my hard drive. In this folder they have all the Ubuntu varieties from Breezy to Hardy and even Debian Etch, Sarge and Sid.

[http://packages.sil.org/ubuntu/dists/](http://packages.sil.org/ubuntu/dists/)

I use to use SIL software for work and uni and up till a few weeks ago I didn't know they supplied programs for Linux that could be considered viable Windows alternatives. I have also heard they are working on their major software suite for Linux users.

---

### Post by BobSongs on 2008-02-19
> **k3lt01 said:**
> Here is a link to an SIL repository that I would really like to download and put on to my hard drive. In this folder they have all the Ubuntu varieties from Breezy to Hardy and even Debian Etch, Sarge and Sid.

[http://packages.sil.org/ubuntu/dists/](http://packages.sil.org/ubuntu/dists/)

I use to use SIL software for work and uni and up till a few weeks ago I didn't know they supplied programs for Linux that could be considered viable Windows alternatives. I have also heard they are working on their major software suite for Linux users.

COoOol. I'll get to work immediately to figure out how to download the repositories.

Thanks for the link.

**Edit:** OK. I did my homework. There's a problem and there's a solution.

[SIZE=3][COLOR=Gray]**problem**[/COLOR][/SIZE]
The host (packages.sil.org) has not created a set of files **debmirror** requires for download. These files are **Packages** and **Packages.gpg**. The **Packages** file lists the names of the available packages for download. The **Packages.gpg** file confirms the size of the **Packages** file to ensure it is the right size and so forth. This is the error **debmirror** throws:
> Errors:
Failed to download some Release or Release.gpg files!
WARNING: releasing 1 pending lock...
Download of dists/dapper/Release failed:
404 Not Found
Download of dists/dapper/Release.gpg failed: 404 Not Found[SIZE=3][COLOR=Gray]**solution**[/COLOR][/SIZE]
I suggest a well-written e-mail addressed to SIL.org encouraging them to create their **Packages** and **Packages.gpg** files for use with **debmirror**. Step 9 of my tutorial explains how the **Packages **file is created.

---

### Post by k3lt01 on 2008-02-19
Thanks Bob, I had a similar error for my attempts. I will email SIL to see if they will oblige the extra files, I think they will do it after all it will help their own people to if they do.

---

### Post by odin1965 on 2008-02-21
Anybody know exactly how big the gutsy repos should be. I finally got my first big download to complete. I had to use the US repos, the Canadian ones are having some problems, looks like. But the total size is 22.2 gig. I had heard it should be bigger, around 30. I did just the default gutsy and gutsy-security as noted in the code in this tutorial.

---

### Post by odin1965 on 2008-02-21
Sorry, as in the default for the tutorial, I got gutsy-updates and gutsy-backports as well. No source. 

> **odin1965 said:**
> Anybody know exactly how big the gutsy repos should be. I finally got my first big download to complete. I had to use the US repos, the Canadian ones are having some problems, looks like. But the total size is 22.2 gig. I had heard it should be bigger, around 30. I did just the default gutsy and gutsy-security as noted in the code in this tutorial.

---

### Post by BobSongs on 2008-02-23
> **odin1965 said:**
> Anybody know exactly how big the gutsy repos should be. I finally got my first big download to complete. I had to use the US repos, the Canadian ones are having some problems, looks like. But the total size is 22.2 gig. I had heard it should be bigger, around 30. I did just the default gutsy and gutsy-security as noted in the code in this tutorial.
[FONT=Verdana] My downloaded Gutsy repositories (a couple weeks old) show this:

[B]36335 items, totalling 18.9 GB

[/B] Then add 4.2 GB four times (for four full DVDs) and around 2.1 GB for the fifth disc. I'll let you do the math.

If your research shows you have less than you should, try the command again. It will compare the remote file list with yours and fill in all the missing files.

If you've modified the command and removed certain sections such as the **backports**, then your amount will vary.
[/FONT]

---

### Post by BobSongs on 2008-02-24
[FONT=Verdana][SIZE=3][COLOR=Black][SIZE=2]To keep the clutter down on the main page, I've moved the rather long list of choices. Here's what you do.

**Scroll down and select** the system that best matches what you need (for example: gutsy i386).

**Highlight the text** underneath that choice and copy it (right-click the highlighted text and click Copy).

**Paste the text** into the Terminal. Review the text and make any necessary changes (such as the destination folder).

**Hit Enter** when all is to your satisfaction. Then return to the main tutorial page by closing this page or by clicking the "BACK to the tutorial" link.[/SIZE][/COLOR][B][COLOR=Sienna]

dapper[/COLOR] [COLOR=Green]i386[/COLOR][/B][/SIZE]
[/FONT]>  debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=dapper,dapper-security,dapper-updates,dapper-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg[FONT=Verdana] 
**[SIZE=3][COLOR=Sienna]dapper[/COLOR] [COLOR=Blue]amd64[/COLOR][/SIZE]**
[/FONT]>  debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=dapper,dapper-security,dapper-updates,dapper-backports, --section=main,restricted,universe,multiverse --arch=amd64 ~/UbuntuRepos --ignore-release-gpg[FONT=Verdana] 
[SIZE=3]**[COLOR=Sienna]dapper[/COLOR] [COLOR=Red]powerpc[/COLOR]**[/SIZE]
[/FONT]>  debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=dapper,dapper-security,dapper-updates,dapper-backports, --section=main,restricted,universe,multiverse --arch=powerpc ~/UbuntuRepos --ignore-release-gpg[FONT=Verdana] 
[SIZE=3]**[COLOR=Sienna]dapper[/COLOR] [COLOR=DarkOrchid]sparc[/COLOR]**[/SIZE]
[/FONT]>  debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=dapper,dapper-security,dapper-updates,dapper-backports, --section=main,restricted,universe,multiverse --arch=sparc ~/UbuntuRepos --ignore-release-gpg[FONT=Verdana][COLOR=Purple]

[**BACK to the tutorial**]("http://ubuntuforums.org/showthread.php?t=352460")
[/COLOR][/FONT][FONT=Verdana]
[SIZE=3]** [COLOR=DarkOrange][/COLOR]**[/SIZE][/FONT][FONT=Verdana][COLOR=DarkSlateGray]____________________________________[/COLOR]

[SIZE=3]** [COLOR=DarkSlateGray]hardy[/COLOR] [COLOR=Green]i386[/COLOR]**[/SIZE]
[/FONT]>  debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg[FONT=Verdana] 
[SIZE=3]** [COLOR=DarkSlateGray]hardy[/COLOR] [COLOR=Blue]amd64[/COLOR]**[/SIZE]
[/FONT]>  debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=amd64 ~/UbuntuRepos --ignore-release-gpg[FONT=Verdana] 
[SIZE=3]** [COLOR=DarkSlateGray]hardy[/COLOR] [COLOR=Red]powerpc[/COLOR]**[/SIZE]
[/FONT]>  debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=powerpc ~/UbuntuRepos --ignore-release-gpg[FONT=Verdana] 
[SIZE=3]** [COLOR=DarkSlateGray]hardy[/COLOR] [COLOR=Purple]sparc[/COLOR]**[/SIZE]
[/FONT]>  debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=sparc ~/UbuntuRepos --ignore-release-gpg[**BACK to the tutorial**]("http://ubuntuforums.org/showthread.php?t=352460")

---

### Post by R.JOEL STAFFORD on 2008-03-20
Thanks For Your Time And Insight

Peace  =]

---

### Post by glenn45 on 2008-03-22
Hey Bobsongs!
Just checking up on you and this cool tutorial! :guitar:

---

### Post by k3lt01 on 2008-03-22
Hi Bob.

I bring you tidings of joy and good news as I have found something for you to work on in what remains of your spare time. I have installed Hardy-beta on my Desktop (not my main machine so it can crash if need be) and just tried to follow your tutorial for Hardy when I come across a small but significant problem. Debpartial does not exist in the Hardy repositories so I cannot get any further than typing step one into my terminal.:( However Debpartial-mirror does exist and I am wondering if that is the Hardy equivalent.

---

### Post by BobSongs on 2008-03-24
> **glenn45 said:**
> Hey Bobsongs!
Just checking up on you and this cool tutorial! :guitar:

[FONT=Verdana] Excellent, dood! I'm glad you dropped by. Nice to sip coffee with ya! ;-)

I keep grooming the tutorial. My desire is to have it show up in the "Tutorial of the Week" section. While I carry no screenshots, I'm trying to comply with the demands of that department. Hopefully it will appear there.

I'm doing well. And it's good to see you again. Keep dropping by and, for heaven's sake: give me any criticism you can find for the tutorial. For example -- is there a spot where a print-screen would improve it? That would help.

I'm hoping all is well with you too.

Keep in touch.[/FONT]

---

### Post by BobSongs on 2008-03-24
> **k3lt01 said:**
> Hi Bob.

I bring you tidings of joy and good news as I have found something for you to work on in what remains of your spare time. I have installed Hardy-beta on my Desktop (not my main machine so it can crash if need be) and just tried to follow your tutorial for Hardy when I come across a small but significant problem. Debpartial does not exist in the Hardy repositories so I cannot get any further than typing step one into my terminal.:( However Debpartial-mirror does exist and I am wondering if that is the Hardy equivalent.
[FONT=Verdana] A big thank-you to you for your kind greetings and for pointing out Hardy's current failings. I know Hardy Heron has just moved over to Beta from Alpha. I think some of the repositories will be a bit lacking until everything is tweaked just right.

I will, however, make a note of it in the heading of the tutorial. I recall there being a problem with Gutsy when it was first released. **debmirror** was available but it did precious little for Gutsy users. The bug was found and squashed by the Debian people. It eventually trickled over to Ubuntu's repositories.

The lack of **debmirror** makes me wonder if they're discontinuing its use. That tip will spur me into doing some in-depth research. More news to follow.

[COLOR=Red]**[-=EDIT=-]**[/COLOR] **k3lt01**: Here's an idea. But I must preface it with the risk levels. I don't know what this may do to your system: it could install flawlessly or destroy everything right to point where it messes up your sock drawer. But it may install on your system. [**This Link**]("http://archive.ubuntu.com/ubuntu/pool/universe/d/debmirror/debmirror_20070123ubuntu1_all.deb") points to Gutsy's **debmirror** file. [COLOR=DarkRed]**Use at your own system's risk**[/COLOR]. But if you choose to test it and it works, let me know: I'll post it on the main page.
[/FONT]

---

### Post by pietjanjaap on 2008-04-13
Wat if you install a virtuel 7.10 ubuntu in vmware server and use debmirror inside it.

---

### Post by BobSongs on 2008-04-15
> **pietjanjaap said:**
> Wat if you install a virtuel 7.10 ubuntu in vmware server and use debmirror inside it.
[FONT=Verdana]Sorry I didn't answer sooner. This is not a high priority thread. So I only visit every couple days.

Uhm: That **would** work. But your virtual drive should have a large amount of space available for the Hardy repositories and the creation of each DVD ISO. You can get away with creating 1 DVD ISO, burning it, deleting it and creating the next in line.
[/FONT]

---

### Post by Zack McCool on 2008-04-24
Just a question...   I plan to run the debmirror command weekly from crontab.  Do I also need to run the dpkg-scanpackages command each week?  I am keeping the repo in a mounted directory on my lan (actually putting all the repos that I have machines running), and just want to make sure that everything will update properly.

And thanks for all your hard work.  I like keeping as much as possible on my home network, and playing with all kinds of stuff, so this was fun...   ;)

---

### Post by BobSongs on 2008-04-27
> **Zack McCool said:**
> Just a question...   I plan to run the debmirror command weekly from crontab.  Do I also need to run the dpkg-scanpackages command each week?  I am keeping the repo in a mounted directory on my lan (actually putting all the repos that I have machines running), and just want to make sure that everything will update properly.

And thanks for all your hard work.  I like keeping as much as possible on my home network, and playing with all kinds of stuff, so this was fun...   ;)

It may well be a good idea to add teh dpkg-scanpackages in the command, after each update. Keeping the repos mounted is an excellent idea. So, yes: I would strongly suggest that secondary process be maintained.

Cheers

---

### Post by jocose on 2008-05-04
Thanks to firefox deciding to freeze, I lost my entire re-edit of this post to correct it, so I'm going to be very brief in this re-post re-edit:

If you're unable to follow the brilliant mirroring and backup to DVD option word for word as BobSongs has so kindly written, here is an alternative:

[Warning: Use this information at your own risk, if you mess up your system  or anything bad happens, I take no blame. Understand what you are doing before you do it. Use this method only if you cannot use BobSongs' excellent instructions. Please do not post about this post in this thread. Has this post helped you? I am glad.]

First, bookmark this thread:
[http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)

Download the packages it mentions within, and download the packages mentioned in BobSongs' first post in this thread, then start with Main:

```
debmirror --nosource -m --passive --host=mirror.you.want --root=ubuntu/ --method=http --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main --arch=i386 ~/UbuntuRepos --ignore-release-gpg --timeout=999
```

Replace mirror.you.want in the code above with the mirror you wish to use.  I suggest *not* using ubuntu.com to mirror, but instead a mirror closer to you in your country. Please refer to the Launchpad Mirrors of Ubuntu page for a list of mirrors and an update status: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

When you've finished with the instructions below, and you've mirrored Main, moved the debs, deleted the ~/UbuntuRepos directory following the moving of the deb files to another folder you've created, you may start again with another repo and change --section=main to --section=restricted to mirror restricted, and follow the instructions in this post again, rinse and repeat.

After Main is downloaded, we create a folder in ~/ to move the downloaded deb files to, and run this command:

```
find /start/here -name \*.deb -exec mv {} /to/there/ \;
```

Replace /start/here with ~/UbuntuRepos and /to/there with the empty folder you've created. This will MOVE all of the deb files you've mirrored from Main into your new folder. Now you will look at the size of the new folder with the debs. Delete ~/UbuntuRepos once you've verified the debs were moved. It won't all fit on one 4.xGB DVD, so create a second folder and go into the first with Nautilus and switch to List view. Highlight the files with the shift key held down to advance more and more until you have enough to fit on one DVD. Now paste these into the other folder you created. Now compare the sizes of each folder, each should be able to fit on a DVD.

Now open the link I posted above and continue with creating an **autorepo** file for *each* folder of debs you have, and run the autorepo file in each, which will generate a package list for each.

Once this is done for each, you may burn each to a separate DVD and add them the same way as BobSongs mentioned, with apt-cdrom add. With each DVD burned, you may delete the new folders you originally created to move the mirrored Main debs to.

Start again with another repo and do one each time until you have all of them individually mirrored, manually split up between folders, autorepo ran in each one, and burned. Do not burn the DVD without first running autorepo and checking each folder for package lists, you need these on the DVD so they will add properly with apt-cdrom add later.

Done!

With this method, I have not tried downloading ALL of the repos at once and splitting them into several DVDs, when I cannot follow BobSongs' method and use debpartial to complete the process, and I have to use the method here I've described in this post, I download one repo at a time. It's a longer process, but it works.

*Optional*: It may be simpler for some to use aptoncd (available in the repos) after you have mirrored an area and moved the debs to one folder, and use aptoncd to generate the package list and create DVD images for you! I posted the manual cut/paste and autorepo method above, referring to another thread because when I tried aptoncd it created a DVD which was slightly above the size of a DVD and all of the burning applications refused to burn it, so I decided to do the manual splitting of deb files into individual folders and generating a package list manually with autorepo as mentioned in the linked thread.

---

### Post by k3lt01 on 2008-05-07
> **BobSongs said:**
> [FONT=Verdana][COLOR=Red]**[-=EDIT=-]**[/COLOR] **k3lt01**: Here's an idea. But I must preface it with the risk levels. I don't know what this may do to your system: it could install flawlessly or destroy everything right to point where it messes up your sock drawer. But it may install on your system. [**This Link**]("http://archive.ubuntu.com/ubuntu/pool/universe/d/debmirror/debmirror_20070123ubuntu1_all.deb") points to Gutsy's **debmirror** file. [COLOR=DarkRed]**Use at your own system's risk**[/COLOR]. But if you choose to test it and it works, let me know: I'll post it on the main page.
[/FONT]Sorry for not replying earlier, I have only just had enough time to play with this (I have been playing with other aspects of Ubuntu). The file you linked to is in the stable release of Hardy already (I updated my Hardy-Desktop to the stable release with a clean install). Following your excellent tutorial I still come across the same problem as before. The code is below so you can see what is happening.

```
michael@michael-desktop:~$ sudo aptitude install debmirror ruby mkisofs debpartial dpkg-dev
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find package "debpartial". However, the following
packages contain "debpartial" in their name:
  debpartial-mirror 
Couldn't find package "debpartial". However, the following
packages contain "debpartial" in their name:
  debpartial-mirror 
The following NEW packages will be automatically installed:
  build-essential g++ g++-4.2 libcompress-raw-zlib-perl 
  libcompress-zlib-perl libdigest-sha1-perl libio-compress-base-perl 
  libio-compress-zlib-perl liblockfile-simple-perl liblog-agent-perl 
  libstdc++6-4.2-dev libtimedate-perl patch 
The following NEW packages will be installed:
  build-essential debmirror dpkg-dev g++ g++-4.2 libcompress-raw-zlib-perl 
  libcompress-zlib-perl libdigest-sha1-perl libio-compress-base-perl 
  libio-compress-zlib-perl liblockfile-simple-perl liblog-agent-perl 
  libstdc++6-4.2-dev libtimedate-perl patch 
0 packages upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 522kB/5186kB of archives. After unpacking 19.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com hardy/main libcompress-raw-zlib-perl 2.008-1 [91.8kB]
Media Change: Please insert the disc labeled 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)' in the drive '/cdrom/' and press [Enter].

Get:2 http://archive.ubuntu.com hardy/main libio-compress-base-perl 2.008-1 [54.4kB]
Get:3 http://archive.ubuntu.com hardy/main libio-compress-zlib-perl 2.008-1 [135kB]
Get:4 http://archive.ubuntu.com hardy/main libcompress-zlib-perl 2.008-1 [35.7kB]
Get:5 http://archive.ubuntu.com hardy/main libdigest-sha1-perl 2.11-2 [24.7kB]  
Get:6 http://archive.ubuntu.com hardy/universe liblog-agent-perl 0.307-1 [129kB]
Get:7 http://archive.ubuntu.com hardy/universe liblockfile-simple-perl 0.2.5-7 [20.2kB]
Get:8 http://archive.ubuntu.com hardy/universe debmirror 20070123ubuntu1 [30.5kB]
Fetched 522kB in 49s (10.6kB/s)                                                 
Selecting previously deselected package libstdc++6-4.2-dev.
(Reading database ... 125264 files and directories currently installed.)
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.2.3-1ubuntu3_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu3_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Selecting previously deselected package libcompress-raw-zlib-perl.
Unpacking libcompress-raw-zlib-perl (from .../libcompress-raw-zlib-perl_2.008-1_i386.deb) ...
Selecting previously deselected package libio-compress-base-perl.
Unpacking libio-compress-base-perl (from .../libio-compress-base-perl_2.008-1_all.deb) ...
Selecting previously deselected package libio-compress-zlib-perl.
Unpacking libio-compress-zlib-perl (from .../libio-compress-zlib-perl_2.008-1_all.deb) ...
Selecting previously deselected package libcompress-zlib-perl.
Unpacking libcompress-zlib-perl (from .../libcompress-zlib-perl_2.008-1_all.deb) ...
Selecting previously deselected package libdigest-sha1-perl.
Unpacking libdigest-sha1-perl (from .../libdigest-sha1-perl_2.11-2_i386.deb) ...
Selecting previously deselected package liblog-agent-perl.
Unpacking liblog-agent-perl (from .../liblog-agent-perl_0.307-1_all.deb) ...
Selecting previously deselected package liblockfile-simple-perl.
Unpacking liblockfile-simple-perl (from .../liblockfile-simple-perl_0.2.5-7_all.deb) ...
Selecting previously deselected package debmirror.
Unpacking debmirror (from .../debmirror_20070123ubuntu1_all.deb) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu3) ...
Setting up libcompress-raw-zlib-perl (2.008-1) ...
Setting up libio-compress-base-perl (2.008-1) ...
Setting up libio-compress-zlib-perl (2.008-1) ...
Setting up libcompress-zlib-perl (2.008-1) ...
Setting up libdigest-sha1-perl (2.11-2) ...
Setting up liblog-agent-perl (0.307-1) ...
Setting up liblockfile-simple-perl (0.2.5-7) ...
Setting up debmirror (20070123ubuntu1) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu3) ...

Setting up build-essential (11.3ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
michael@michael-desktop:~$ cp /usr/share/doc/debpartial/examples/debcopy.gz ~
cp: cannot stat `/usr/share/doc/debpartial/examples/debcopy.gz': No such file or directory
michael@michael-desktop:~$ gunzip ~/debcopy.gz
gzip: /home/michael/debcopy.gz: No such file or directory

```
Now because debpartial doesn't exist and it suggested debpartial-mirror I installed that and this is what occured
```
 michael@michael-desktop:~$ sudo aptitude install debpartial-mirrorReading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  python-cdd python-pycurl 
The following NEW packages will be installed:
  debpartial-mirror python-cdd python-pycurl 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 118kB of archives. After unpacking 668kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com hardy/main python-pycurl 7.16.4-1 [82.8kB]
Get:2 http://archive.ubuntu.com hardy/universe python-cdd 0.0.7 [11.0kB]        
Get:3 http://archive.ubuntu.com hardy/universe debpartial-mirror 0.2.95 [24.1kB]
Fetched 118kB in 11s (10.2kB/s)                                                 
Selecting previously deselected package python-pycurl.
(Reading database ... 126301 files and directories currently installed.)
Unpacking python-pycurl (from .../python-pycurl_7.16.4-1_i386.deb) ...
Selecting previously deselected package python-cdd.
Unpacking python-cdd (from .../python-cdd_0.0.7_all.deb) ...
Selecting previously deselected package debpartial-mirror.
Unpacking debpartial-mirror (from .../debpartial-mirror_0.2.95_all.deb) ...
Setting up python-pycurl (7.16.4-1) ...

Setting up python-cdd (0.0.7) ...

Setting up debpartial-mirror (0.2.95) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done 
```
I then
```
michael@michael-desktop:~$ cp /usr/share/doc/debpartial/examples/debcopy.gz ~
cp: cannot stat `/usr/share/doc/debpartial/examples/debcopy.gz': No such file or directory
michael@michael-desktop:~$ gunzip ~/debcopy.gz
gzip: /home/michael/debcopy.gz: No such file or directory
michael@michael-desktop:~$ 
```
I am unable to go any further without debpartial which by what I am being told by the code coming back to me is debparital does not exist in Hardy yet.

I am going to have a surf around and see if I can locate it somehow. I apologise for the size of this post, I thought posting the code would help in the analysis of the issue.

EDIT: ok I have search through the Repo listings and there is NO debpartial in Hardy. I then went to Gutsy's listing, located Gutsy's debpartial [http://packages.ubuntu.com/gutsy/all/debpartial/download](http://packages.ubuntu.com/gutsy/all/debpartial/download)  downloaded it, installed it and everything seems ok.
```
 michael@michael-desktop:~$ cp /usr/share/doc/debpartial/examples/debcopy.gz ~
michael@michael-desktop:~$ gunzip ~/debcopy.gz
michael@michael-desktop:~$ 
```

---

### Post by k3lt01 on 2008-05-07
I have just tried to download the Ubuntu Hardy repo as per the tutorial. This is what happened. Sorry alot more code.
```
michael@michael-desktop:~$ debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg
Mirroring to /home/michael/UbuntuRepos from ftp://anonymous@archive.ubuntu.com/ubuntu//
Arches: i386
Dists: hardy,hardy-security,hardy-updates,hardy-backports
Sections: main,restricted,universe,multiverse
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/hardy/Release	 #
[0%] Getting: dists/hardy/Release.gpg	 #
[0%] Getting: dists/hardy-security/Release	 #
[0%] Getting: dists/hardy-security/Release.gpg	 #
[0%] Getting: dists/hardy-updates/Release	 #
[0%] Getting: dists/hardy-updates/Release.gpg	 #
[0%] Getting: dists/hardy-backports/Release	 #
[0%] Getting: dists/hardy-backports/Release.gpg	 #
Get Packages and Sources files and other miscellany.
dists/hardy/main/binary-i386/Packages.gz needs fetch
[  0%] Getting: dists/hardy/main/binary-i386/Packages.gz	 ###############
dists/hardy/main/binary-i386/Release needs fetch
[ 24%] Getting: dists/hardy/main/binary-i386/Release	 #
dists/hardy/restricted/binary-i386/Packages.gz needs fetch
[ 24%] Getting: dists/hardy/restricted/binary-i386/Packages.gz	 #
dists/hardy/restricted/binary-i386/Release needs fetch
[ 24%] Getting: dists/hardy/restricted/binary-i386/Release	 #
dists/hardy/universe/binary-i386/Packages.gz needs fetch
[ 24%] Getting: dists/hardy/universe/binary-i386/Packages.gz	 #######################################################
dists/hardy/universe/binary-i386/Release needs fetch
[ 96%] Getting: dists/hardy/universe/binary-i386/Release	 #
dists/hardy/multiverse/binary-i386/Packages.gz needs fetch
[ 96%] Getting: dists/hardy/multiverse/binary-i386/Packages.gz	 ###
dists/hardy/multiverse/binary-i386/Release needs fetch
[ 99%] Getting: dists/hardy/multiverse/binary-i386/Release	 #
dists/hardy-security/main/binary-i386/Packages.gz needs fetch
[ 99%] Getting: dists/hardy-security/main/binary-i386/Packages.gz	 #
dists/hardy-security/main/binary-i386/Packages.gz failed md5sum check
dists/hardy-security/main/binary-i386/Packages needs fetch
[ 99%] Getting: dists/hardy-security/main/binary-i386/Packages	 # failed:Failed to open file.
dists/hardy-security/main/binary-i386/Packages failed md5sum check, removing
dists/hardy-security/main/binary-i386/Packages failed md5sum check
dists/hardy-security/main/binary-i386/Packages.bz2 needs fetch
[ 99%] Getting: dists/hardy-security/main/binary-i386/Packages.bz2	 #
dists/hardy-security/main/binary-i386/Packages.bz2 failed md5sum check, removing
dists/hardy-security/main/binary-i386/Release needs fetch
[ 99%] Getting: dists/hardy-security/main/binary-i386/Release	 #
dists/hardy-security/restricted/binary-i386/Packages.gz needs fetch
[ 99%] Getting: dists/hardy-security/restricted/binary-i386/Packages.gz	 #
dists/hardy-security/restricted/binary-i386/Release needs fetch
[ 99%] Getting: dists/hardy-security/restricted/binary-i386/Release	 #
dists/hardy-security/universe/binary-i386/Packages.gz needs fetch
[ 99%] Getting: dists/hardy-security/universe/binary-i386/Packages.gz	 #
dists/hardy-security/universe/binary-i386/Packages.gz failed md5sum check
dists/hardy-security/universe/binary-i386/Packages needs fetch
[ 99%] Getting: dists/hardy-security/universe/binary-i386/Packages	 # failed:Failed to open file.
dists/hardy-security/universe/binary-i386/Packages failed md5sum check, removing
dists/hardy-security/universe/binary-i386/Packages failed md5sum check
dists/hardy-security/universe/binary-i386/Packages.bz2 needs fetch
[ 99%] Getting: dists/hardy-security/universe/binary-i386/Packages.bz2	 #
dists/hardy-security/universe/binary-i386/Packages.bz2 failed md5sum check, removing
dists/hardy-security/universe/binary-i386/Release needs fetch
[ 99%] Getting: dists/hardy-security/universe/binary-i386/Release	 #
dists/hardy-security/multiverse/binary-i386/Packages.gz needs fetch
[ 99%] Getting: dists/hardy-security/multiverse/binary-i386/Packages.gz	 #
dists/hardy-security/multiverse/binary-i386/Release needs fetch
[ 99%] Getting: dists/hardy-security/multiverse/binary-i386/Release	 #
dists/hardy-updates/main/binary-i386/Packages.gz needs fetch
[ 99%] Getting: dists/hardy-updates/main/binary-i386/Packages.gz	 #
dists/hardy-updates/main/binary-i386/Packages.gz failed md5sum check
dists/hardy-updates/main/binary-i386/Packages needs fetch
[ 99%] Getting: dists/hardy-updates/main/binary-i386/Packages	 # failed:Failed to open file.
dists/hardy-updates/main/binary-i386/Packages failed md5sum check, removing
dists/hardy-updates/main/binary-i386/Packages failed md5sum check
dists/hardy-updates/main/binary-i386/Packages.bz2 needs fetch
[ 99%] Getting: dists/hardy-updates/main/binary-i386/Packages.bz2	 #
dists/hardy-updates/main/binary-i386/Packages.bz2 failed md5sum check, removing
dists/hardy-updates/main/binary-i386/Release needs fetch
[ 99%] Getting: dists/hardy-updates/main/binary-i386/Release	 #
dists/hardy-updates/restricted/binary-i386/Packages.gz needs fetch
[ 99%] Getting: dists/hardy-updates/restricted/binary-i386/Packages.gz	 #
dists/hardy-updates/restricted/binary-i386/Release needs fetch
[ 99%] Getting: dists/hardy-updates/restricted/binary-i386/Release	 #
dists/hardy-updates/universe/binary-i386/Packages.gz needs fetch
[ 99%] Getting: dists/hardy-updates/universe/binary-i386/Packages.gz	 #
dists/hardy-updates/universe/binary-i386/Packages.gz failed md5sum check
dists/hardy-updates/universe/binary-i386/Packages needs fetch
[ 99%] Getting: dists/hardy-updates/universe/binary-i386/Packages	 # failed:Failed to open file.
dists/hardy-updates/universe/binary-i386/Packages failed md5sum check, removing
dists/hardy-updates/universe/binary-i386/Packages failed md5sum check
dists/hardy-updates/universe/binary-i386/Packages.bz2 needs fetch
[ 99%] Getting: dists/hardy-updates/universe/binary-i386/Packages.bz2	 #
dists/hardy-updates/universe/binary-i386/Packages.bz2 failed md5sum check, removing
dists/hardy-updates/universe/binary-i386/Release needs fetch
[100%] Getting: dists/hardy-updates/universe/binary-i386/Release	 #
dists/hardy-updates/multiverse/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/hardy-updates/multiverse/binary-i386/Packages.gz	 #
dists/hardy-updates/multiverse/binary-i386/Release needs fetch
[100%] Getting: dists/hardy-updates/multiverse/binary-i386/Release	 #
dists/hardy-backports/main/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/hardy-backports/main/binary-i386/Packages.gz	 #
dists/hardy-backports/main/binary-i386/Packages.gz failed md5sum check
dists/hardy-backports/main/binary-i386/Packages needs fetch
[100%] Getting: dists/hardy-backports/main/binary-i386/Packages	 # failed:Failed to open file.
dists/hardy-backports/main/binary-i386/Packages failed md5sum check, removing
dists/hardy-backports/main/binary-i386/Packages failed md5sum check
dists/hardy-backports/main/binary-i386/Packages.bz2 needs fetch
[100%] Getting: dists/hardy-backports/main/binary-i386/Packages.bz2	 #
dists/hardy-backports/main/binary-i386/Packages.bz2 failed md5sum check, removing
dists/hardy-backports/main/binary-i386/Release needs fetch
[100%] Getting: dists/hardy-backports/main/binary-i386/Release	 #
dists/hardy-backports/restricted/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/hardy-backports/restricted/binary-i386/Packages.gz	 #
dists/hardy-backports/restricted/binary-i386/Release needs fetch
[100%] Getting: dists/hardy-backports/restricted/binary-i386/Release	 #
dists/hardy-backports/universe/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/hardy-backports/universe/binary-i386/Packages.gz	 #
dists/hardy-backports/universe/binary-i386/Packages.gz failed md5sum check
dists/hardy-backports/universe/binary-i386/Packages needs fetch
[100%] Getting: dists/hardy-backports/universe/binary-i386/Packages	 # failed:Failed to open file.
dists/hardy-backports/universe/binary-i386/Packages failed md5sum check, removing
dists/hardy-backports/universe/binary-i386/Packages failed md5sum check
dists/hardy-backports/universe/binary-i386/Packages.bz2 needs fetch
[100%] Getting: dists/hardy-backports/universe/binary-i386/Packages.bz2	 #
dists/hardy-backports/universe/binary-i386/Packages.bz2 failed md5sum check, removing
dists/hardy-backports/universe/binary-i386/Release needs fetch
[100%] Getting: dists/hardy-backports/universe/binary-i386/Release	 #
dists/hardy-backports/multiverse/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/hardy-backports/multiverse/binary-i386/Packages.gz	 #
dists/hardy-backports/multiverse/binary-i386/Release needs fetch
[100%] Getting: dists/hardy-backports/multiverse/binary-i386/Release	 #
Errors:
 dists/hardy-security/main/binary-i386/Packages.gz failed md5sum check
 Download of dists/hardy-security/main/binary-i386/Packages failed: Failed to open file.
 dists/hardy-security/main/binary-i386/Packages failed md5sum check
 dists/hardy-security/main/binary-i386/Packages.bz2 failed md5sum check, removing
 dists/hardy-security/universe/binary-i386/Packages.gz failed md5sum check
 Download of dists/hardy-security/universe/binary-i386/Packages failed: Failed to open file.
 dists/hardy-security/universe/binary-i386/Packages failed md5sum check
 dists/hardy-security/universe/binary-i386/Packages.bz2 failed md5sum check, removing
 dists/hardy-updates/main/binary-i386/Packages.gz failed md5sum check
 Download of dists/hardy-updates/main/binary-i386/Packages failed: Failed to open file.
 dists/hardy-updates/main/binary-i386/Packages failed md5sum check
 dists/hardy-updates/main/binary-i386/Packages.bz2 failed md5sum check, removing
 dists/hardy-updates/universe/binary-i386/Packages.gz failed md5sum check
 Download of dists/hardy-updates/universe/binary-i386/Packages failed: Failed to open file.
 dists/hardy-updates/universe/binary-i386/Packages failed md5sum check
 dists/hardy-updates/universe/binary-i386/Packages.bz2 failed md5sum check, removing
 dists/hardy-backports/main/binary-i386/Packages.gz failed md5sum check
 Download of dists/hardy-backports/main/binary-i386/Packages failed: Failed to open file.
 dists/hardy-backports/main/binary-i386/Packages failed md5sum check
 dists/hardy-backports/main/binary-i386/Packages.bz2 failed md5sum check, removing
 dists/hardy-backports/universe/binary-i386/Packages.gz failed md5sum check
 Download of dists/hardy-backports/universe/binary-i386/Packages failed: Failed to open file.
 dists/hardy-backports/universe/binary-i386/Packages failed md5sum check
 dists/hardy-backports/universe/binary-i386/Packages.bz2 failed md5sum check, removing
Failed to download some Package, Sources or Release files!
WARNING: releasing 1 pending lock...
michael@michael-desktop:~$ 
```That is where it stopped and I am unable to get any further at this time. Feisty was soooo easy, Gutsy eventually came good when they fixed the bug in one of the files, I am hoping they catch this one in Hardy soon and fix it to because having the repos on hand makes things so much easier.

EDIT: The Medibuntu Repository download works. The Canonical download doesn't and has similar code as the Ubuntu download. I think the problem might be in the files on the Ubuntu and Canonical servers. Maybe somethings not there or not setup properly yet.

---

### Post by BobSongs on 2008-05-17
Thanks for the head's-up, **k3lt01**.

[edit]OK. Tutorial completely fixed. Everything should work as before. I tried using the Gutsy Gibbon **debpartial** from the Ubuntu repositories. It installs well on Hardy Heron. All three sources (Hardy's, Canonical's and MediBuntu's repositories) work fine.[/edit]

The tutorial is back online.

---

### Post by starbase1 on 2008-05-20
I'm new to all this, but a set of repositories on DVD sounds like a great idea to me! Thing is, with the net connection I have, it's not close practical to download on this scale.

Which is, er, why I want the stuff on DVD on the first place!
:rolleyes:

If it's not off topic for this thread, is there anywhere I can order a set of DVD's, (I'm in the UK, so somewhere reasonably local would save postage).

I checked out some sites that sell distros on CD, but I can't find repositories for sale.

Cheers,
Nick

---

### Post by k3lt01 on 2008-05-20
Hi Bob, its working fine for me now to. Excellent stuff now I can show my friends the brilliance that is Ubuntu and they can see everything that is available.

Starbase, I don't know about buying the Repo's on DVDs. Have you taken a look at the Ubuntu website? if that's no luck then maybe when people have got the entire set downloaded someone will send you a copy for the price of the DVDs and Postage. What version of Ubuntu are you using?

---

### Post by starbase1 on 2008-05-21
Thanks for the suggestion.

I did find one place selling the repositories on DVD's, but based in the states which normally means 2-3 weeks for a disk to arrive. (I really don't know why it should be so long, I seriously think someone must check this stuff to see there is nothing top secret being mailed...)

The outfit is here, in case anyone else is interested:
[https://on-disk.com/](https://on-disk.com/)

I think I am going to bite the bullet and tie up my net connection for a week to get the data!

As for the version, I'm still dithering, but it's looking like I'll go for 8.04 64 bit, with the current price of RAM, and my fondness for graphics stuff, I can do a lot if I can access more than 4 Gb!

> **k3lt01 said:**
> Hi Bob, its working fine for me now to. Excellent stuff now I can show my friends the brilliance that is Ubuntu and they can see everything that is available.

Starbase, I don't know about buying the Repo's on DVDs. Have you taken a look at the Ubuntu website? if that's no luck then maybe when people have got the entire set downloaded someone will send you a copy for the price of the DVDs and Postage. What version of Ubuntu are you using?

---

### Post by BobSongs on 2008-05-23
> **starbase1 said:**
> I'm new to all this, but a set of repositories on DVD sounds like a great idea to me! Thing is, with the net connection I have, it's not close practical to download on this scale.

Which is, er, why I want the stuff on DVD on the first place!
:rolleyes:

If it's not off topic for this thread, is there anywhere I can order a set of DVD's, (I'm in the UK, so somewhere reasonably local would save postage).

I checked out some sites that sell distros on CD, but I can't find repositories for sale.

Cheers,
Nick
Listen, Nick: No worries!

Here's the path: Get back to Page 1 of the tutorial and scroll down to the FAQs. Your question is right there and answered to the best of my ability. Lookin' forward to hearing from you.

:)

---

### Post by clarita78 on 2008-05-31
Hi BobSongs, this is a very useful HOWTO, but I would like to know if it is possible to download ONLY the updates of the repositories without having in a local drive (for example) the repositories previously downloaded.

Thanks again, for the HOWTO!!!!

---

### Post by woodboy on 2008-06-08
BobSongs,
Just wanted to say THANKS. This has been a huge help to me.

---

### Post by woodboy on 2008-06-08
Oh Yeah, by the way, the APTonCD works great until you run(sudo apt-get clean), then I guess the cache file is gone......like most things, I learnt it the hard way.

---

### Post by BobSongs on 2008-06-10
> **clarita78 said:**
> Hi BobSongs, this is a very useful HOWTO, but I would like to know if it is possible to download ONLY the updates of the repositories without having in a local drive (for example) the repositories previously downloaded.

Thanks again, for the HOWTO!!!!Keep reading the whole tutorial. You'll find out how to download the updates.

Since **debmirror** cannot know what you've downloaded so far without first checking the destination folder, you see how important it is to leave all the files intact and do the update.

Again: scroll down the tutorial. I edit it constantly and never leave anything out. There's no need to ever go through the following posts in order to get the complete picture.

---

### Post by BobSongs on 2008-06-10
> **woodboy said:**
> Oh Yeah, by the way, the APTonCD works great until you run(sudo apt-get clean), then I guess the cache file is gone......like most things, I learnt it the hard way.
I think you hit upon my first "Huh?" with APTonCD: the need to never clear your **apt** cache. On a larger drive that's not a problem. For smaller drives though, hmmm.

Still: it's a clever idea. I just think that APTonCD's fine for the "user", the original downloader of all the files that'll be burned to CD. However, ***friends*** might not find any of those files useful. So handing them ***all the repositories on 5 DVDs*** is a whole lot cooler.

That's my opinion and that's why I pursued this tutorial and I keep it nice and polished.

---

### Post by greentree-sa on 2008-06-13
Hi all, Please move this if needed!!

I have gone to the trouble of downloading from ftp.leg.uct.ac.za, the 5 repo DVD's and 1 CD of Hardy 8.04. :)( silly I Known...)

Now the big question: How do I convert those DVD's to a local mirror on a harddrive, and then updating my local mirror over time?

I have a Ubuntu server with samba etc, and I would like to dump the mirror on it in order for me to update/install "stuff" to other Ubuntu boxes from it. 

All I can find is How2's to make DVD's from a mirror.....and I need the sequence to do the exercise the other way round...:confused:

All feedback would be GREATLY appreciated...

Thanks in advance
Christiaan

---

### Post by BobSongs on 2008-06-15
> **greentree-sa said:**
> Hi all, Please move this if needed!!

I have gone to the trouble of downloading from ftp.leg.uct.ac.za, the 5 repo DVD's and 1 CD of Hardy 8.04. :)( silly I Known...)

Now the big question: How do I convert those DVD's to a local mirror on a harddrive, and then updating my local mirror over time?

I have a Ubuntu server with samba etc, and I would like to dump the mirror on it in order for me to update/install "stuff" to other Ubuntu boxes from it. 

All I can find is How2's to make DVD's from a mirror.....and I need the sequence to do the exercise the other way round...:confused:

All feedback would be GREATLY appreciated...

Thanks in advance
Christiaan


Sadly, your request is outside the range of my knowledge. I've never setup up a series of Ubuntu PCs with one as a server. So I'm at a loss as to how to answer this question.

I understand that having a server serve the files is the most efficient way of serving these files. So if anyone wishes to contribute to this answer, please: feel free.

[This thread appears to have the answer your looking for]("http://ubuntuforums.org/showthread.php?t=564301"). If not, it's a start that may lead you in the right direction.

Sorry.

---

### Post by linuxmilk on 2008-06-17
I really like the idea about having a local copy of all the ubuntu repositories on my harddrive. So thanks goes to people how made this tutorials possible. Some info about my laptop: MacBook Pro laptop with 120 GB harddisk. Half the size goes to MacOS Leopard. I also have external usb harddrive with 250 GB for backup purpose. I made a separate home partition for easy ubuntu install on 28 GB. I have downloaded the entire ubuntu repositories about 23 GB. Unfortuntly i have a lack of space in my harddrive because i keep a lot files in there. I was forced to move the downloaded files to my external harddrive while downloading. Later I added them as a source i Synaptic. It works well. 

PS: I don't want to create dvd's. I just want to keep them as they are in  their folders.

**Questions:**

* But how can i update the Ubuntu, Canonical and MediBuntu repositories since it no longer is in my home folder?
* If i restart step 3 in your tutorial again how can it "read" the ubuntu repositories on my external harddrive?
* Can i download a new repository directly to my external harddrive?


Thanks, Kim :)

---

### Post by k3lt01 on 2008-06-18
I have a similar system to what you have and want, my repos are on my 500 GB Seagate external drive. I have a folder on that drive called Repositories with a txt file for all the repos I download. I double click in the txt file it gives me the option to open in a few things, I click the terminal option and it opens the terminal and downloads everything into the Repositories folder creating the relevant Ubuntu, Canonical, and Medibuntu folders.

Then you just set up your Synaptic as you have already done.

---

### Post by linuxmilk on 2008-06-18
Okay, but how does that text file look like? :-s

kim

---

### Post by k3lt01 on 2008-06-19
Open Text Editor and cut and paste in the appropriate text in the first post in this thread. Name and save that file (I use names like Hardy-Ubuntu, Hardy-Medibunti, Hardy-Canonical) to your Repository folder on your external hard drive, and that's your text file.

---

### Post by RageAgainstThis on 2008-06-25
Everything worked fine with your tutorial except medibuntu and commercial.  It is asking for the public .gpg key.  I should have written exactly what it said, but I completely forgot until I got to work.  The computer using these files has no connection to the internet what so ever.  

All I did was download and dpkg-scanpackages, to produce the appropriate packages.gz.  My sources list kind of looks like this deb file:/media/REPOS/Medibuntu media as I had no idea what to put after the location of the packages.gz.  For big repo an example is given, I have no idea if this is my hold up or not.  

Any help or direction would be greatly appreciated.

---

### Post by BobSongs on 2008-06-25
> **RageAgainstThis said:**
> Everything worked fine with your tutorial except medibuntu and commercial...

:-k  Mm. OK. I'll give it a look-see.

I've only had problems with it when they've changed critical locations. But thanks for the "heads up".

[-o<  Let's see what I can do for you.

---

### Post by BobSongs on 2008-06-25
> **RageAgainstThis said:**
> ...Any help or direction would be greatly appreciated.

:-s OK: I just tried Canonical and Medibuntu. Did you copy the entire command line? It's a bit long and part of it is hidden on the right of the box. I'm bound by forum rules to publish each command in a [ code ] box even if the formatting sorta sucks.

Here's the code outside the box:

[FONT=Courier New]**debmirror --nosource -m --passive --host=www.medibuntu.org --root=repo/ --method=http --progress --dist=hardy --section=free,non-free --arch=i386 ~/MediBuntuRepos --ignore-release-gpg**[/FONT]

:D If your code is any shorter than that, be persistent and try again.

;) Again: I copied my text and gave it a whirl. It worked perfectly. So perfectly I've got to go erase those files now.

---

### Post by jocose on 2008-06-30
BobSongs and others who may be interested: with my last post or two in this thread I instructed an alternative approach, and not only did it work very well, I was able to save a few DVDs by putting a couple of the smaller repos like Restricted and Multiverse onto one DVD along with a portion of Main which would've taken up a separate CD or DVD! The previous way I had always made Ubuntu Repo DVDs was by following the method outlined by BobSongs, which still works great, but by altering the process as I describe in one or two of my posts in this thread, you are able to SAVE on DVD media, without having to burn a DVD of mostly wasted space and instead combining a few of the smaller repos together with any spill-over from another repo which would otherwise require another blank media CD or DVD!

If you want to conserve on blank media, [give my method a try](http://ubuntuforums.org/showpost.php?p=4876414&postcount=119).

---

### Post by BobSongs on 2008-07-02
> **jocose said:**
> BobSongs and others who may be interested: with my last post or two in this thread I instructed an alternative approach, and not only did it work very well, I was able to save a few DVDs by putting a couple of the smaller repos like Restricted and Multiverse onto one DVD along with a portion of Main which would've taken up a separate CD or DVD! The previous way I had always made Ubuntu Repo DVDs was by following the method outlined by BobSongs, which still works great, but by altering the process as I describe in one or two of my posts in this thread, you are able to SAVE on DVD media, without having to burn a DVD of mostly wasted space and instead combining a few of the smaller repos together with any spill-over from another repo which would otherwise require another blank media CD or DVD!

If you want to conserve on blank media, [give my method a try]("http://ubuntuforums.org/showpost.php?p=4876414&postcount=119").

I'm sorry to hear Firefox froze on you at an inopportune moment. I tell you what, **jocose**: I'll put a link to this post in my tutorial. However, if you PM me with instructions in approximately the same way I write them, I'll add them to the main body of the tutorial.

I'm zealous for clarity of text and layout. I find it helps new users to follow instructions without a hitch. (If the instructions are unclear then people continually ask the same questions for the sake of clarity... no fun).

I don't currently have a set of the repositories on my HDD, so I cannot test the additional commands at the moment. So I will be relying on you for a careful step-by-step walk-through (should you decide to accept the mission). :)

---

### Post by OldEnt on 2008-07-10
Hello,
Thank you for this excellent tutorial. You can try to download Google repository:
```
debmirror --nosource -m --passive --host=dl.google.com --root=linux/deb/ --method=http --progress --dist=stable --section=non-free --arch=i386 ~/GoogleRepos --ignore-release-gpg
```
It worked for me (30,8 MB  [32 328 737 bytes downloaded] - picasa and google-desktop).

---

### Post by BobSongs on 2008-07-10
This will now be integrated into the main tutorial.

30 Mb isn't exactly drowning in data, but it's forever for a dial-up connection.

Good call. Keep 'em coming.

:-)

---

### Post by asashnov on 2008-07-22
BobSongs, thanx for good tutorial :)

BTW, debpartial now is dropped:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=374107](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=374107)
RM: debpartial -- RoQA; very old, low user count, orphaned

I look to debian-cd package- way to create official CD/DVD images.
[http://www.debian.org/CD/faq/#diy](http://www.debian.org/CD/faq/#diy)

Seems role of debpartial plays  tools/make_disc_trees.pl programm.:guitar:

With Ubuntu 8.04 and debpartial I got 6 DVD .iso in sizes 3.8Gb, 4.0Gb, 4.1Gb....780mb *I invoce debpartial with --size 4600000). I will try --size DVD later of cause. But I'm interesting way to more precision way to fill DVD fully.

---

### Post by BobSongs on 2008-07-23
> **asashnov said:**
> BobSongs, thanx for good tutorial :)From everyone who worked to make this tutorial: you're very, very welcome!

> **asashnov said:**
> BTW, debpartial now is dropped:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=374107](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=374107)
RM: debpartial -- RoQA; very old, low user count, orphanedHmm. Not very good. I have saved a copy of this file and will keep it available. If Canonical abandons it I will make it available for download. Thank you very much for informing me.

> **asashnov said:**
>  I look to debian-cd package- way to create official CD/DVD images.
[http://www.debian.org/CD/faq/#diy](http://www.debian.org/CD/faq/#diy)Thank you for the link. It is good. I will add it to the main tutorial for reference. You are very kind.

> **asashnov said:**
> Seems role of debpartial plays  tools/make_disc_trees.pl programm.:guitar:

With Ubuntu 8.04 and debpartial I got 6 DVD .iso in sizes 3.8Gb, 4.0Gb, 4.1Gb....780mb *I invoce debpartial with --size 4600000). I will try --size DVD later of cause. But I'm interesting way to more precision way to fill DVD fully.I am surprised that **debpartial** did not do a better job of filling the DVDs fully for you. Normally it does a very good job of filling the DVDs fully. Let me see what I can do to get each DVD filled correctly.

:)

---

### Post by BobSongs on 2008-07-26
**asashnov:**
Concerning [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=374107](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=374107), I've read through it and here is the general summing up of what is said:

**Matej Vela** who works with Debian Linux stated that **Masato Taruishi** was the maintainer of the project. But it was abandoned. The request was made for someone to "adopt" or take over the project.

**Abu Zaher** has take up the project from this point (Yay!).

So, for the time being all is well. No need for alarm.

---

### Post by riseringseeker on 2008-08-02
Bobsongs,

Thanks so much for the help tonight after finding the medibuntu repos had changed.  People like you are why I love the Linux community and try to give back when I can.

---

### Post by EXCiD3 on 2008-08-03
If you have no internet or highspeed on your pc that you are trying to install packages on, you could try my new project Keryx. It allows you to download the packages easily onto a USB drive and then take them back to your Ubuntu computer. I'm looking for testers for it, please come try it out! [http://keryx.betaserver.org](http://keryx.betaserver.org)

Thanks a lot for this tutorial! I used it on a gradeschool network that we are using Xubuntu on and i will be mirroring the repositories to the local server we have so that it will be easier for the administrators especially if they need to reinstall xubuntu on a new computer or something. Thanks again!

---

### Post by jocose on 2008-08-07
> **BobSongs said:**
>  **jocose**: I'll put a link to this post in my tutorial. However, if you PM me with instructions in approximately the same way I write them, I'll add them to the main body of the tutorial.


Hi Bob, thanks for the reply and invitation. However, I don't have the time at the moment to go through it all again and document the step-by-step process as you're requesting. I would enjoy doing this in the future, but I may not be doing it until 2010, since I'm sticking with the current LTS Ubuntu version. Should I decide to grab the next version of Ubuntu when it's released as Final, and do this again, I'll gladly post the process. With the way I do it, I can fit several portions of the repos on DVDs to fill the space, rather than sticking Multiverse, Restricted, and part of Main on a small amount of individual DVDs. (which is a waste of blank DVDs in my opinion)

---

### Post by branquito on 2008-08-19
thank you for explaining this all in one place and clear..:lolflag:=;=;=;=D>

---

### Post by Achille on 2008-08-21
I successfully burn my DVDs thanks to this tutorial.

But I have a problem: Synaptic doesn't show the packages contained in the DVDs. I could update the whole system, but I can't install new packages of universe, since they don't appear in Synaptic. And it doesn't work with apt-get.

By the way, I had to add the option -joliet-long to mkisofs, otherwise it didn't work.

---

### Post by k3lt01 on 2008-08-21
> **Achille said:**
> I successfully burn my DVDs thanks to this tutorial.

But I have a problem: Synaptic doesn't show the packages contained in the DVDs. I could update the whole system, but I can't install new packages of universe, since they don't appear in Synaptic. And it doesn't work with apt-get.Have you kept the files on your HDD, if you have and don't mind keeping them there (after all you will probably want to update them once a week or so) why don't you tell apt where they are stored on your HDD. Bobsongs explained how to do that in the tutorial.

When I finally get my Hardy set downloaded that's how I will be doing it and just burning the dvd's for friends with a slow net connection.

---

### Post by Achille on 2008-08-21
Finally, I've redone all the procedure since point 3) of the tutorial. I've used the terminal (sudo apt-cdrom add) instead of Synaptic to add the DVDs, and now IT WORKS!

Thank you very much for this so helpful tutorial!

---

### Post by BobSongs on 2008-09-23
> **Achille said:**
> Finally, I've redone all the procedure since point 3) of the tutorial. I've used the terminal (sudo apt-cdrom add) instead of Synaptic to add the DVDs, and now IT WORKS!

Thank you very much for this so helpful tutorial!

I'm not surprised to hear things work better from the command prompt.

I've worked quite well in the DOS days. So the command prompt does not frighten me at all.

Glad you found it useful.

---

### Post by k3lt01 on 2008-09-25
[Quote=BobSongs][COLOR=Purple]**[SIZE=4]9. Pointing Apt locally[/SIZE]**[/COLOR]
This is a bit more involved (not for beginners at all).

It is possible to use the files you've downloaded as your own repository for installing new software and for system updates. But this will only work well if you keep these files up-to-date. If not, you will fall behind in security updates.

With that out of the way let's proceed. Enter the following code in the terminal:
[/FONT][FONT=Verdana]```
cd ~/UbuntuRepos && dpkg-scanpackages . /dev/null > Packages && gzip Packages && cd ~
```[/FONT][FONT=Verdana]This creates the necessary files for **apt** to know what is in your local repositories.[/FONT][FONT=Verdana]

Once completed insert the following into your **sources.list** file:```
deb file:/home/[USER NAME HERE]/UbuntuRepos/ [COLOR=Red]**hardy**[/COLOR] main multiverse restricted universe
``````
deb file:/home/[USER NAME HERE]/UbuntuRepos/ **[COLOR=Red]hardy[/COLOR]**-security main multiverse restricted universe
```(Thanks, [**xfile087**]("http://ubuntuforums.org/member.php?u=122407"))

**NOTE:** Don't forget these two things:
[/FONT]
[LIST=1]
[*][FONT=Verdana]modify these lines for [COLOR=Blue]**feisty**[/COLOR] and [COLOR=Olive]**gutsy**[/COLOR][/FONT]
[*][FONT=Verdana]put **hash marks** (#) before each Internet repository line you no longer require. Example:[/FONT]
[/LIST]
[FONT=Verdana]```
[COLOR=Red]**#**[/COLOR] deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
```[/FONT][/Quote]

Hi Bob.

I have come across a slight problem with pointing apt locally. I have downloaded the complete Hardy set for all the repos listed in the tutorial and have them stored on my Seagate external hdd. Now the problem is no matter how I adjust the code to point to my Seagate hdd so I can scan it so apt knows whats there it cannot see it telling me it cannot see the Seagate hdd. If I go to "Places" the Seagate hdd is listed and I can see the repos without any problem.

I have transfered all the files to my laptop and everything seems fine as long as the files are on the machine. I will keep trying but at the moment it appears as though I have to transfer all the files to each machine I have and update each machines new repository set manually.

---

### Post by sweetsinse on 2008-09-26
-----k3lt01
i believe your external drives will not automatically be mounted on boot.  after you go to "places" your drives are then mounted and thus usable by apt.

i think what you need to do is add an entry in your /etc/fstab to mount the device on boot time

-----bongsongs
excellent tutorial and thanks for the updated information.  i swear i ran across this tutorial about a year ago it seems, and i have watched it develop since then, wonderful job.  i just finally got around to syncing as i set tons of people up with ubuntu and i hate waiting for the downloads each time, now i have a little WD passport external drive with 4 repos...

hardy i386
hardy x86_64
intrepid i386
intrepid x86_64

excellent.  i did notice that the command to create the packages.gz file seems unnecessary/time consuming.  a packages.gz file already exists in each dists/{disto}/{sub-repo}/binary-{arch}/ folder and is synced with every pull.  i skipped that step and everything seems to be working fine.  i took the default sources file and just replaced each entry with my local server (i have apache on a dedicated box so no need for file://).  not sure but maybe you need that step if you want to make a single entry in the sources.list file as you have directed in the tutorial.

lastly, i have a cron that i run each night to update my repos.  i wrote a little bash script that *should* handle *any* ubuntu repository.  the script will echo:

$(date) - (dist|arch|local_folder) - SUCCESS

-or-

$(date) - (dist|arch|local_folder) - FAILED: {full stout of debmirror command}

so you can redirect this into a log.

anyone who is interested in the script it is located here:
(mirror may not always be available):
(it's also attached to this post):

[http://teleport.thruhere.net:8008/LINKED/sync_ubu_repo.sh](http://teleport.thruhere.net:8008/LINKED/sync_ubu_repo.sh)

(remember chmod +x or tighter permissions if need be)
the usage format is:

./sync_ubu_repo.sh {distibution} {architecture} {absolute_local_path}

EXAMPLE if your in the SAME folder:
(place script in /usr/sbin to use without "./" [execute]):
(may need "sudo"):

./sync_ubu_repo.sh intrepid amd64 /media/ubuREPO/8.10_INTREPID/x86_64/

EXAMPLE with SBIN + LOG (appends to result.log):

sync_ubu_repo.sh hardy amd64 /media/ubuREPO/8.04_HARDY/x86_64/ >> /home/crons/logs/sync_ubu_repo.sh/result.log

MY EXACT ROOT CRONTAB EXAMPLE (one of four repos):

0 1 * * * /home/crons/./sync_ubu_repo.sh intrepid amd64 /media/ubuREPO/8.10_INTREPID/x86_64/ >> /home/crons/logs/sync_ubu_repo.sh/result.log

that cron runs each night at 1am.

peace

---

### Post by BobSongs on 2008-09-26
> **k3lt01 said:**
> Hi Bob.

I have come across a slight problem with pointing apt locally. I have downloaded the complete Hardy set for all the repos listed in the tutorial and have them stored on my Seagate external hdd. Now the problem is no matter how I adjust the code to point to my Seagate hdd so I can scan it so apt knows whats there it cannot see it telling me it cannot see the Seagate hdd. If I go to "Places" the Seagate hdd is listed and I can see the repos without any problem.

I have transfered all the files to my laptop and everything seems fine as long as the files are on the machine. I will keep trying but at the moment it appears as though I have to transfer all the files to each machine I have and update each machines new repository set manually.

I'm going to assume you modified the lines in /etc/apt/source.list to accurately reflect the exact location of the repositories. So rather than:

> deb file:/home/[USER NAME HERE]/UbuntuRepos/ hardy main multiverse restricted universe

you've got something more like:

> deb file:/[PathToLocalRepositories]/ hardy main multiverse restricted universe

and things are still going wrong. :-k  Hmmm.

As mentioned ... somewhere in this thread's 80 billion posts: I don't run Ubuntu on a network. I ... don't even use this tutorial any more because no one I currently know has both Ubuntu and no Internet connection. (But I do keep it as up-to-date as possible.)

So please: log any and all steps you use to resolve the flaws in the tutorial. It'll benefit you because you may confidently trash your own notes and use this forum as your text book. And it'll benefit others when they see a solution to a problem they didn't know they had. :)

---

### Post by JohnFurner on 2008-09-27
Hi BobSongs,

Ubuntu Forums is the most impressive I've seen anywhere on the web! The Ubuntu info is comprehensive and staggering, to say the least.

I'm still posting on Save XP with new aliases: XP pwns Vista and XP User. I'm not answering the Trolls (VistaPwns and Kid), just pushing them down into oblivion. You are right, I had some fun with the Larry, Curly and Moe alias. 

I sent an email to Galen, requesting that he kill off the Trolls by shutting down InfoWord Save XP blog. Nobody is posting anything except me and the trolls. It is human nature to respond and I don't think anyone is visiting the blog anymore.

You and PocketPenguin are really great debaters!

Regards,
John Furner

---

### Post by JohnFurner on 2008-09-28
BobSongs, let's see how the trolls handle my new posts!

John Furner 
InfoWorld, Save XP, Sunday, September 28, 2008 
2:34:15 AM 

Risks, Cost-Benefits Analysis--The Bottom Line 
 
Why would I want to: 
1. Spend $400 for Vista Ultimate; 
2. Trash $3000 in apps that don't run under Vista 
3. Spend another $3000 to replace my XP apps; 
4. Trash a $2500 XP PC because it can't handle Vista; 
5. Spend another $2500 for a PC to run Vista 
 
That's $11,400 just to have a Vista PC whose performance is about the same as XP, and then face Vista's city dump UI and aggravating UAP. And suppose I buy a new Mobo whose drivers cause serious problems. 
 
It makes smart sense to keep my XP PC until it's Mobo dies. 
 
And good grief, Windows 7 is coming. What will happen to Vista? And will Windows 7 take another 2 years to iron out enough bugs to make it as fast as XP? 
 
I'd rather wait and see what the OS world of competition does with Windows, Linux, and Mac in 2010 or 2011 or even in 2012

---

### Post by BobSongs on 2008-10-14
Good to see you, John.

I see that the forum of SaveXP.com has pretty much come to its end. As you well know, I've used Windows since 3.0. And I've never, ever seen such a resistance to a new operating system.

But that's life. I've sent you some "private messages" to your in box. Hope we keep chatting here.

:)

---

### Post by k3lt01 on 2008-10-17
G'day BobSongs.

I decided the other day to download every official version of Ubuntu for various reasons pointed out in [this thread]("http://ubuntuforums.org/showthread.php?t=946297"). Because of this I needed to be able to download repositories for past versions, so I went looking for the site to do it and the results are listed in the thread above.

So for anyone who is interested for whatever reason be it nostalgia, business, just plain techno geek, or reasons you would probably not want everyone to know, here are the codes.

```
debmirror --nosource -m --passive --host=old-releases.ubuntu.com --root=ubuntu/ --method=http --progress --dist=[COLOR="Red"]warty[/COLOR],[COLOR="Red"]warty[/COLOR]-security,[COLOR="Red"]warty[/COLOR]-updates,[COLOR="Red"]warty[/COLOR]-backports, --section=main,restricted,universe,multiverse --arch=[COLOR="SeaGreen"]i386[/COLOR] UbuntuRepos[COLOR="SeaGreen"]i386[/COLOR]/ --ignore-release-gpg
```

```
debmirror --nosource -m --passive --host=old-releases.ubuntu.com --root=ubuntu/ --method=http --progress --dist=[COLOR="Red"]warty[/COLOR],[COLOR="Red"]warty[/COLOR]-security,[COLOR="Red"]warty[/COLOR]-updates,[COLOR="Red"]warty[/COLOR]-backports, --section=main,restricted,universe,multiverse --arch=[COLOR="SeaGreen"]amd64[/COLOR] UbuntuRepos[COLOR="SeaGreen"]amd64[/COLOR]/ --ignore-release-gpg
```

Doing this clearly defines a different folder for each repository set. Note the coloured text can be changed to suit the version, architecture, and output folder as per your original tutorial method.


Please note a couple of points:
1. I have "UbuntuRepos/" and not "~/UbuntuRepos". This makes the download occur in the folder the executable txt file is contained in. I have a folder for each version e.g. Wartyi386, Wartyamd64, Hoaryi386, Hoaryamd64 etc.

2. After creating the txt file I right click on it and open the properties dialog, then permissions and make sure the execute box is ticked. This gives you an option later when you click on the file to open it in the terminal without copy and pasting. This is also important if you want to put the repositories in individual version folders as in 1 above.

3. the architectures currently available in each (old.release) version are:
4.10 (Warty Warthog); i386, amd64, ppc.
5.04 (Hoary Hedgehog); i386, amd64, ppc, ia64, sparc.
5.10 (Breezy Badger); i386, amd64, ppc, ia64, sparc.
6.10 (Edgy Eft); i386, amd64, ppc, ia64, sparc.
7.04 (Feisty Fawn); i386, amd64, ppc, sparc.

---

### Post by BobSongs on 2008-10-19
G'day, k3lt01!

Sorry I didn't see your post until now. And it's an excellent post.

I'm going to add it to the main tutorial. You may have noted my new **mission, vision and values** section to the tutorial. I'm not saying by that part that I am not accepting the legacy versions' code. I just don't feel the need to break my hump for it. But... you broke **your** hump, so ... you get the credit.

I'll add it immediately.

Thanks.

---

### Post by k3lt01 on 2008-10-19
> **BobSongs said:**
> You may have noted my new **mission, vision and values** section to the tutorial. I'm not saying by that part that I am not accepting the legacy versions' code. I just don't feel the need to break my hump for it. But... you broke **your** hump, so ... you get the credit.

I'll add it immediately.

Thanks.G'day BobSongs.

Yes I did see it and that is one of the reasons I went searching for them. I totally understand your reasoning as 99.999999% of people would move on to the next version anyway, but for that minute number of Ubuntu fans (like myself), I thought I would take the challenge to keep the "old.releases" available for those who felt the need to have a set.

---

### Post by BobSongs on 2008-10-20
> **k3lt01 said:**
> G'day BobSongs.

Yes I did see it and that is one of the reasons I went searching for them. I totally understand your reasoning as 99.999999% of people would move on to the next version anyway, but for that minute number of Ubuntu fans (like myself), I thought I would take the challenge to keep the "old.releases" available for those who felt the need to have a set.
Understood. I've added a direct link to your post. However, I've begun cleaning up my tutorial. For some reason, probably because I use the graphic editor, I get all kinds of font codes I've got to clean up. Most of it is done. Once that's been set to order, I'll add your post into the main tutorial completely.

You must have an immoral amount of hard drive space to accommodate that many repository files. ;)  Should you ever have too much space, kindly cut off a slice and send it my way. I'll just paste it on to my hard drive.

:D

---

### Post by BobSongs on 2008-10-20
> **k3lt01 said:**
> <snip>G'day BobSongs.

I decided the other day to download every official version of Ubuntu for various reasons pointed out in [this thread]("http://ubuntuforums.org/showthread.php?t=946297"). Because of this I needed to be able to download repositories for past versions, so I went looking for the site to do it and the results are listed in the thread above.</snip>
Good day from Canada (another one of the "colonies" ;) ).

I was about to post your content to the tutorial which would look something like this:

For anyone who is interested for whatever reason... be it nostalgia, business, just plain techno geek, or reasons you would probably not want everyone to know, here are example codes.

[COLOR=DarkRed]**Warty Warthog**[/COLOR] on the **[COLOR=Blue]i386[/COLOR]** architecture:
```
debmirror --nosource -m --passive --host=old-releases.ubuntu.com --root=ubuntu/ --method=http --progress --dist=**[COLOR=Red]warty[/COLOR]**,**[COLOR=Red]warty[/COLOR]**-security,**[COLOR=Red]warty[/COLOR]**-updates,**[COLOR=Red]warty[/COLOR]**-backports, --section=main,restricted,universe,multiverse --arch=**[COLOR=Teal]i386[/COLOR]** UbuntuRepos**[COLOR=Teal]i386[/COLOR]**/ --ignore-release-gpg
```**[COLOR=DarkRed]Warty Warthog[/COLOR]** on the **[COLOR=Blue]64-bit AMD[/COLOR]** architecture:
```
debmirror --nosource -m --passive --host=old-releases.ubuntu.com --root=ubuntu/ --method=http --progress --dist=**[COLOR=Red]warty[/COLOR]**,**[COLOR=Red]warty[/COLOR]**-security,**[COLOR=Red]warty[/COLOR]**-updates,**[COLOR=Red]warty[/COLOR]**-backports, --section=main,restricted,universe,multiverse --arch=**[COLOR=Teal]amd64[/COLOR]** UbuntuRepos**[COLOR=Teal]amd64[/COLOR]**/ --ignore-release-gpg
```Doing it this way clearly defines a different folder for each repository set. Note the [COLOR=Red]**coloured** **[COLOR=Teal]text[/COLOR]**[/COLOR] can be changed to suit the version, architecture, and output folder as per your original tutorial method.

**Please note a few points:**
1. It is "UbuntuRepos/" and not "~/UbuntuRepos". This makes the download occur in the folder the executable txt file is contained in. We encourage a folder for each version e.g. Wartyi386, Wartyamd64, Hoaryi386, Hoaryamd64 etc.

2. After creating the txt file I right click on it and open the properties dialog, then permissions and make sure the execute box is ticked. This gives you an option later when you click on the file to open it in the terminal without copy and pasting. This is also important if you want to put the repositories in individual version folders as in 1 above.

3. the architectures currently available in each (old.release) version are:
4.10 (Warty Warthog); i386, amd64, ppc.
5.04 (Hoary Hedgehog); i386, amd64, ppc, ia64, sparc.
5.10 (Breezy Badger); i386, amd64, ppc, ia64, sparc.
6.10 (Edgy Eft); i386, amd64, ppc, ia64, sparc.
7.04 (Feisty Fawn); i386, amd64, ppc, sparc.

[center]__________________[/center]

But I was wondering about this part in the 2nd point: **"After creating the txt file..."** I'm at a loss as to where this text file is created. Is there something missing? :)

---

### Post by k3lt01 on 2008-10-20
> **BobSongs said:**
> You must have an immoral amount of hard drive space to accommodate that many repository files. ;)  Should you ever have too much space, kindly cut off a slice and send it my way. I'll just paste it on to my hard drive.

:D
Check my signature for what is actually in my machines. I also have another 500GB Seagate external hard drive and a 1TB that I will fit as soon as I can get a MOBO that will let me use 1 and not make me put it in a RAID configuration.

> **BobSongs said:**
> Good day from Canada (another one of the "colonies" ;) ).lol. Bob, this hit a note.
> **BobSongs said:**
> But I was wondering about this part in the 2nd point: **"After creating the txt file..."** I'm at a loss as to where this text file is created. Is there something missing? :)Yes sorry, it shou read more like,

2. After creating the txt file in the appropriate folder ***_(mine is /home/michael/Repositories/Ubuntu/(Version) )_*** I right click on it and open the properties dialog, then permissions and make sure the execute box is ticked. This gives you an option later when you click on the file to open it in the terminal without copy and pasting. This is also important if you want to put the repositories in individual version folders as in 1 above.

---

### Post by sweetsinse on 2008-10-23
Bobsongs,

One thing that might be useful to others; I used my local copy of the repo to do a net install to another machine.  I had to make a small change to the download, in addition to the standard sections like main, security, etc. you have to add:

main/debian-installer

Which is a subsection of main, but is not mirrored unless specified directly.  Will elaboate further but on mobile phone right now.

Also I can confirm the step about creating a packages.gz can be skipped as it is updated with every sync.

---

### Post by k3lt01 on 2008-10-23
> **sweetsinse said:**
> Also I can confirm the step about creating a packages.gz can be skipped as it is updated with every sync.This is true if you download a repository that has these files. If they don't have these files (e.g. the SIL repository for Linguistics) you can download the files directly from the site with a download manager but still have to create the packages.gz file yourself if you make your machine use these repositories.

---

### Post by BobSongs on 2008-10-30
> **sweetsinse said:**
> Bobsongs,

One thing that might be useful to others; I used my local copy of the repo to do a net install to another machine.  I had to make a small change to the download, in addition to the standard sections like main, security, etc. you have to add:

main/debian-installer

Which is a subsection of main, but is not mirrored unless specified directly.  Will elaboate further but on mobile phone right now.

OK, dude. I'm awaiting your instructions. They'll be added to the main tutorial and you'll be credited. I have a stand-alone machine, so I cannot test this model.

I'll take your word on the additions.

> **sweetsinse said:**
> Also I can confirm the step about creating a packages.gz can be skipped as it is updated with every sync.

Funny. I tried to do this skipping this step and it failed miserably. It was a while ago.... meh, for the meanwhile I'll leave this part in the tutorial. I'll give it a test run.

Problem is: I want to upgrade and I don't have the Intrepid repositories downloaded. :(

I'll test it and come up with my results.

---

### Post by k3lt01 on 2008-11-19
G'day Bob.

In my quest to download the entire set of Ubuntu repositories (well i386, amd64, and powerpc) I worked out a little trick that can half the amount of what is being downloaded in subsequent downloads.

Let me explain step by step, (I apologise if someone else has already posted this I haven't seen it if they have). 

1. My machines are all i386 based so I download the i386 repositories first.
2. My fathers machine is an amd64 so I create the appropriate folder (i.e. 8.04-Hardy-amd64) and copy the entire contents of the 8.04-Hardy-i386 repository into it.
3. I then execute the appropriate txt file (8.04-Hardy-amd64 Ubuntu Repository) mentioned in previous posts and let it do its thing. Now because the contents are somewhat different to what should be in an amd64 repository it will download all the packages lists files.
4. After about 10 minutes, once the system has figured out what files it needs to download it starts downloading the amd64 files that aren't in the new folder. In the case of Hardy the size of the new download is only 13 gb instead of the full 28gb. This is because about half the packages in Ubuntu are able to be used by all the architectures.
5. When it has finished downloading the system cleans up all the files not in the packages lists file so all the i386 files copied over into the amd64 folder are deleted.

I hope this is helpful to people who have multiple architectures in the systems and who want their own repository sets.

---

### Post by BobSongs on 2008-11-23
> **k3lt01 said:**
> <snip>
3. I then execute the appropriate txt file (8.04-Hardy-amd64 Ubuntu Repository) mentioned in previous posts and let it do its thing. Now because the contents are somewhat different to what should be in an amd64 repository it will download all the packages lists files.</snip>

:-k Would it be possible to post the contents of the text file? If you annotate it, it would help anyone who might be interested in duplicating the same process. Modifications could then be made based on the annotations for each component in the text file. It may so incredibly obvious that no annotations are required. It may be so obscure that almost each line needs quite a bit. I'm unsure at this point.

:-) So, help us to see more clearly by revealing the mysterious and aforementioned text file.

Also: the name you've given to this text file would be very helpful.

---

### Post by k3lt01 on 2008-11-23
Hi Bob.

Here is the contents of my txt file.

```
debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports,hardy-proposed --section=main,restricted,universe,multiverse --arch=i386 8.04-Hardy-i386/ --ignore-release-gpg
```
This is of course the i386 version and can be changed as shown in the tutorial for each other version.

I have also attached it to this post, but if anyone uses it they should try to emulate my folder setup as well which I have some screenshots of so you can see how I have it.

---

### Post by mikeuhlik on 2008-12-13
If i wanted to who would i put this repo i made on dvd to a online version like deb [http://mysite.com/repo/](http://mysite.com/repo/)

so i can have my software for my own distro?

Thanks Mike

---

### Post by k3lt01 on 2008-12-13
> **mikeuhlik said:**
> If i wanted to who would i put this repo i made on dvd to a online version like deb [http://mysite.com/repo/](http://mysite.com/repo/)

so i can have my software for my own distro?

Thanks MikeIf you mean who or what could you use as your webserver you have 3 options. 1. pay an ISP or webhosting service to host it for you, or 2. build your own Ubuntu server and host it yourself, or 3. Ask Canonical or Ubuntu if they would host it for you along with theirs.

1, costs alot of money. 2, takes time and could result in massive usage on your own server system not to mention the costs of paying for the right to have so much traffic. 3, I would think is highly unlikely but it never hurts to ask politely.

---

### Post by mikeuhlik on 2008-12-13
I understand the hosting part but how do you set up the directory /repo/
[http://mysite.com/repo/](http://mysite.com/repo/) if i use your way or this tutorial i have used.

How to build local APT repositories
[http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/")

or could i use APTCD and use whats on the cd and put it in the /repo/ directory of my server would this work or in the tutorial above they tell you how to make a local repo would i just copy that to the web server and it should work. 

The main thing i am trying to figure out is there a special way so set up the /repo/ directory or is it the same as a local directory.

here is a example of a local repo

Summary
Go to /var/cache/apt/archives and copy your debian packages to a folder of your choice, for example, /home/<username>/repository/

    * Change into the repository directory

    cd /home/username/repository

    * And generate a Packages.gz file like this:

    sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

Make sure build-essential is installed (sudo aptitude install build-essential) before you run the above command.

    * Add the following line to your sources.list file (/etc/apt/sources.list)

    deb file:/home/username/repository/ /

Remember to replace username with your real username

    * Reload your package index like this:

    sudo apt-get update

so would this local directory work in a web server directory 
deb file:/home/username/repository/ /
deb [http://mysite.com//repository/](http://mysite.com//repository/) /

and if so would it work to use whats on the APTCD copy it to the /repository/ directory on the web server and it should work ?

Thanks So Much For Your Help.
Mike

---

### Post by computer_freak_8 on 2008-12-17
Thanks so much for this tutorial. I would have hit the "Thank" icon/button, but I don't see it.

I am behind a proxy that the package managers won't authenticate with. (Yeah, it's a Microsoft-based product...)


Thanks again,
computer_freak_8

---

### Post by BobSongs on 2008-12-18
> **computer_freak_8 said:**
> Thanks so much for this tutorial. I would have hit the "Thank" icon/button, but I don't see it.

I am behind a proxy that the package managers won't authenticate with. (Yeah, it's a Microsoft-based product...)


Thanks again,
computer_freak_8
Heehee. Don't worry about using Windows. Just because this is a Linux forum doesn't mean that everyone here has a personal vendetta against Bill Gates. :lolflag:

Don't worry about the "thanks" button. I count it more important that this tutorial was helpful than getting gold stars pinned to my chest. Besides: the tutorial is what it is today because so many other people made it so. I just keep it looking pretty ... and up-to-date.

:popcorn:

---

### Post by Bleumunkie on 2008-12-18
Bob - 
    Thanks a ton for the how-to.  This makes a huge difference to my military buddies who deploy and want to get the newest *buntu, but also want to be able to install software when they need to.  I burn a new install CD, and get the most recent repository mirror for them.  

Since they don't have internet access security isn't a huge issue, and they can always get those updates when they get back.

---

### Post by k3lt01 on 2008-12-19
> **computer_freak_8 said:**
> Thanks so much for this tutorial. I would have hit the "Thank" icon/button, but I don't see it. I know Bob said it doesn't matter but giving credit where it is due is important in a thriving community. The "Thanks" icon is the shield on the bottom right of the post.

---

### Post by computer_freak_8 on 2008-12-19
> **k3lt01 said:**
> I know Bob said it doesn't matter but giving credit where it is due is important in a thriving community. The "Thanks" icon is the shield on the bottom right of the post.

I agree, and yes, that's where it [I]should[\I] be. But look at my screenshot [here]("http://farm4.static.flickr.com/3286/3121685320_412ecd5c2a_b.jpg").

Any ideas? It's got me stumped...

---

### Post by k3lt01 on 2008-12-19
Sorry mate cant help you then, it appears on mine but I don't understand why it doesn't on yours :confused:

Edit: It actually isn't on mine. Now I am very :confused:

---

### Post by BobSongs on 2009-01-03
[FONT=Trebuchet MS]> **mikeuhlik said:**
> If i wanted to who would i put this repo i made on dvd to a online version like deb [http://mysite.com/repo/](http://mysite.com/repo/)

so i can have my software for my own distro?

Thanks Mike
As far as I understand it, yes. You can certainly put 35 gigabytes of data on a host site, such as mysite.com. I hope they give you enough space to put all these files. But from what I've seen, Canonical's bandwidth is pretty efficient. If you can get better streaming, just put the files wherever you want them.

:)[/FONT]

---

### Post by paducahguy on 2009-01-12
I had an issue with being able to download the repository properly .. I need to know what this tells me ? I see the words FAILED repeatedly through the dang info printed to my terminal here... I am going to paste the entire jig below... Hope someone can help me here... It would be nice..

--------------------------

ximal@ximal:~$ debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=intrepid,intrepid-security,intrepid-updates,intrepid-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg
Mirroring to /home/ximal/UbuntuRepos from [ftp://anonymous@archive.ubuntu.com/ubuntu//](ftp://anonymous@archive.ubuntu.com/ubuntu//)
Arches: i386
Dists: intrepid,intrepid-security,intrepid-updates,intrepid-backports
Sections: main,restricted,universe,multiverse
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Keeping: dists/intrepid/Release
[0%] Keeping: dists/intrepid/Release.gpg
[0%] Getting: dists/intrepid-security/Release	 #
[0%] Getting: dists/intrepid-security/Release.gpg	 #
[0%] Keeping: dists/intrepid-updates/Release
[0%] Keeping: dists/intrepid-updates/Release.gpg
[0%] Keeping: dists/intrepid-backports/Release
[0%] Keeping: dists/intrepid-backports/Release.gpg
Get Packages and Sources files and other miscellany.
dists/intrepid-security/main/binary-i386/Packages needs fetch
[ 91%] Getting: dists/intrepid-security/main/binary-i386/Packages	 # failed:Failed to open file.
dists/intrepid-security/main/binary-i386/Packages failed md5sum check, removing
dists/intrepid-security/main/binary-i386/Packages failed md5sum check
dists/intrepid-security/main/binary-i386/Packages.bz2 needs fetch
[ 91%] Getting: dists/intrepid-security/main/binary-i386/Packages.bz2	 #
dists/intrepid-security/universe/binary-i386/Packages needs fetch
[ 92%] Getting: dists/intrepid-security/universe/binary-i386/Packages	 # failed:Failed to open file.
dists/intrepid-security/universe/binary-i386/Packages failed md5sum check, removing
dists/intrepid-security/universe/binary-i386/Packages failed md5sum check
dists/intrepid-security/universe/binary-i386/Packages.bz2 needs fetch
[ 92%] Getting: dists/intrepid-security/universe/binary-i386/Packages.bz2	 #
Errors:
 Download of dists/intrepid-security/main/binary-i386/Packages failed: Failed to open file.
 dists/intrepid-security/main/binary-i386/Packages failed md5sum check
 Download of dists/intrepid-security/universe/binary-i386/Packages failed: Failed to open file.
 dists/intrepid-security/universe/binary-i386/Packages failed md5sum check
Failed to download some Package, Sources or Release files!
WARNING: releasing 1 pending lock...
ximal@ximal:~$

---

### Post by computer_freak_8 on 2009-01-12
> **paducahguy said:**
> I had an issue with being able to download the repository properly .. I need to know what this tells me ? I see the words FAILED repeatedly through the dang info printed to my terminal here... I am going to paste the entire jig below... Hope someone can help me here... It would be nice..

Try running the command with "sudo" - I don't know if this will work or not, but it's worth a try. Also, make sure you don't have any other package management software running. (Again, I don't know if this can affect it, but it's worth trying.)

---

### Post by paducahguy on 2009-01-14
yeah I figured out using SUDO to do the command wasn't as dangerous as I thought it would be so I tried it and everything started up like it should have... It's no big deal now... Though I'm stilllllll downloading after that first reply I made... It had to start over due to issues beyond my control... Along the lines of gpg keys messing up and something about possible issues with the file showing itself where it left off after I accidentally closed the terminal window it was in... While I should have just done it in a different terminal screen to be honest to keep from having this issue :( oh well... I'm going to sit back and watch the counter until it counts down to 100% downloaded... :) ( grabs the popcorn )

---

### Post by jdavis72 on 2009-02-06
#9 Pointing apt locally

I've successfully recreated this on my local box. However, my laptop, connected by sshfs with read and write access, cannot read the apt repo. It says it cannot find and read the file "Packages", although I can see the directory with a file manager or on the cli. Why is apt on my laptop not reading the repo? The setup is: the desktop containing the repo dir has sshd enabled, the laptop mounts the dir with sshfs with read & write permission. All other network file system commands work fine. But apt on the laptop, although searching through the repo dir, is not reading the "Packages" file. Thanks in advance!

Jeremy

---

### Post by riseringseeker on 2009-02-26
Errors on update
I have friends that don't have an internet connection, so I had the download running weekly to be able to update them every month or two. I hadn't looked at it for probably 2 or more months, and when I did I found that quite a bit of it isn't there.

```

debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg

```

I ran the above command from a terminal and it began downloading correctly, but when I came back an hour or so later, it was filled with error messages and had not completed a full download. Suspecting network issues, I added "--timeout=seconds -t 180", but that did not help either.

I appended ">> ~/Desktop/repos" so I could get all the error messages, as I didn't want to sit and watch for several hours before the errors began, and by the time I checked back on it, the start of the errors was far to far back to be able to scroll back to it.

Where the errors began was:


```

#[  1%] Getting: pool/universe/z/zzuf/zzuf_0.9-1_i386.deb	 #Downloaded 240 MiB in 1584s at 154.75 kiB/s
Errors:
 Download of pool/main/l/language-pack-sc-base/language-pack-sc-base_8.04+20080415_all.deb failed:  Download of pool/main/l/language-pack-sc-base/language-pack-sc-base_8.04+20090105_all.deb failed: Connection closed Download of pool/main/l/language-pack-sc/language-pack-sc_8.04+20080415_all.deb failed: Connection closed Download of pool/main/l/language-pack-sc/language-pack-sc_8.04+20090105.1_all.deb failed: Connection closed

```

The text file is huge, 725 pages pulled into Open Office, but scanning from this point on, it appears that the connection failed on the rest of the files the script was attempting to d/l.

I sent this as a PM as well since you likely don't check on the thread but every few days.

Thanks for all your help with this!

---

### Post by BobSongs on 2009-02-26
As I answered privately in the PM, I'll also say this publicly:

My PC is experiencing technical difficulties. A friend dropped off a P4 he no longer wants to use, but it has no hard disks. The system currently used is a DreamLinux LiveCD. So testing this error is not possible for me at this point.

If someone would kindly verify this for me, I would very much appreciate it.

So far, my research has shown that the repositories have not changed location (**often the cause of failed dowloads**).

So any other errors reported by anyone else would really help. I'll stay attentive to this thread.

---

### Post by k3lt01 on 2009-02-27
I tried it just then, clean install of all the required files in a 5 day old install of Intrepid i386. Started the download and it took ages and wouldn't download the first package list. I then adjusted the "timeout" setting to 240 and everything was fine after that. I stopped it after the 3rd file was downloaded cause I already have a complete set of Hardy anyway. So the Hardy repositories haven't moved

---

### Post by Geochelone on 2009-02-28
I'm running Ubuntu as guest on my Win 7 host. Tried to download intrepid repo last night, but the download failed to continue. I guess it was because my little brother failed to properly shut down the system, causes *Archive-Update-in-Progress-geochelone-intrepid* went missing and now the download can't continue.

Now I try once again, but this time on real computer instead of VirtualBox. Thinking of disposing entire intrepid i386 repo into my external hard disk. I'm on a metered ISP (20GB per 30 days) before the speed is choked at 40KBps.

I guess this download can always be resumed. Can't afford to let my laptop running for long continuous hours (she's a new baby of mine, only 4 days old since I bought her).

How to pause the download? Ctrl+C? Or simply exit the terminal and copy paste the debmirror code later to continue?

Thanks for reading the many words above :-)

---

### Post by k3lt01 on 2009-02-28
> **Geochelone said:**
> How to pause the download? Ctrl+C? Or simply exit the terminal and copy paste the debmirror code later to continue?Just close the terminal and start it again next time with a cut and paste or create an executable txt file. This is explained in the last couple of pages.

---

### Post by Geochelone on 2009-03-01
```
[0%] Getting: dists/intrepid/Release... ok
[0%] Getting: dists/intrepid/Release.gpg... ok
[0%] Getting: dists/intrepid-security/Release... ok
[0%] Getting: dists/intrepid-security/Release.gpg... ok
[0%] Getting: dists/intrepid-updates/Release... ok
[0%] Getting: dists/intrepid-updates/Release.gpg... ok
[0%] Getting: dists/intrepid-backports/Release... ok
[0%] Getting: dists/intrepid-backports/Release.gpg... ok
Get Packages and Sources files and other miscellany.
dists/intrepid-backports/universe/binary-i386/Packages needs fetch
[100%] Getting: dists/intrepid-backports/universe/binary-i386/Packages... dists/intrepid-backports/universe/binary-i386/Packages failed 404 Not Found
dists/intrepid-backports/universe/binary-i386/Packages failed md5sum check, removing
dists/intrepid-backports/universe/binary-i386/Packages failed md5sum check
Errors:
 Download of dists/intrepid-backports/universe/binary-i386/Packages failed: 404 Not Found dists/intrepid-backports/universe/binary-i386/Packages failed md5sum check
Failed to download some Package, Sources or Release files!
WARNING: releasing 1 pending lock...
chelodina@chelodina-intrepid:~$
```

Kindly advise.

---

### Post by computer_freak_8 on 2009-03-01
> **Geochelone said:**
> Kindly advise.
Can you post the whole thing from when you entered the command to where it takes you back to the terminal prompt? Just having that last part, I can't tell where it's trying to fetch them from.

Thanks.

---

### Post by Geochelone on 2009-03-01
```
chelodina@chelodina-intrepid:~$ debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=intrepid,intrepid-security,intrepid-updates,intrepid-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/Repositories/Ubuntu/ --ignore-release-gpg --timeout=seconds -t 600
Mirroring to /home/chelodina/Repositories/Ubuntu/ from ftp://anonymous@archive.ubuntu.com/ubuntu//
Arches: i386
Dists: intrepid,intrepid-security,intrepid-updates,intrepid-backports
Sections: main,restricted,universe,multiverse
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Keeping: dists/intrepid/Release
[0%] Keeping: dists/intrepid/Release.gpg
[0%] Keeping: dists/intrepid-security/Release
[0%] Keeping: dists/intrepid-security/Release.gpg
[0%] Keeping: dists/intrepid-updates/Release
[0%] Keeping: dists/intrepid-updates/Release.gpg
[0%] Keeping: dists/intrepid-backports/Release
[0%] Keeping: dists/intrepid-backports/Release.gpg
Get Packages and Sources files and other miscellany.
dists/intrepid-backports/universe/binary-i386/Packages needs fetch
[100%] Getting: dists/intrepid-backports/universe/binary-i386/Packages	 # failed:Failed to open file.
dists/intrepid-backports/universe/binary-i386/Packages failed md5sum check, removing
dists/intrepid-backports/universe/binary-i386/Packages failed md5sum check
Errors:
 Download of dists/intrepid-backports/universe/binary-i386/Packages failed: Failed to open file.
 dists/intrepid-backports/universe/binary-i386/Packages failed md5sum check
Failed to download some Package, Sources or Release files!
WARNING: releasing 1 pending lock...
chelodina@chelodina-intrepid:~$
```

Tried downloading the repo twice. Both failed at almost the same place (around 3gig worth of debs; checked the properties of the repo folder)

Note: Just now I --dry-run the codes, it seems to be working fine.

---

### Post by Geochelone on 2009-03-01
[http://tinyurl.com/c79kms](http://tinyurl.com/c79kms)

I found a workaround to continue download the repo. The person said,

> My current work-around is to always remove the .temp directory before starting a debmirror update. Not ideal, since debmirror needs to re-download a lot of new metadata it already had under .temp.

I give it a spin and yeah, the download continues.

---

### Post by BobSongs on 2009-03-01
[COLOR=Silver]Here, try this. I'll make the modification to the tutorial if all goes well.

Replace "i386" with "binary-i386"

Replace "amd64" with "binary-amd64"

within the command. OK?[/COLOR]   

[COLOR=DarkRed]**EDIT:**[/COLOR] OK. **News update**. My PC now has Ubuntu installed. Intrepid Ibex.

I've followed my tutorial, step by step according to the wording that's been there all along. So far, so good. No glitches.

I've restored the original command. Changing the **i386** to **binary-i386** messes up the command, it seems. So that has been corrected. As I type the download is simply chugging along quite nicely.

---

### Post by Geochelone on 2009-03-22
And how is this thread --> [http://ubuntuforums.org/showthread.php?t=1090731](http://ubuntuforums.org/showthread.php?t=1090731)

related to our thread here?

---

### Post by jms1989 on 2009-03-23
I'm not sure if anyone beside me here has done this but I have a personal repo setup on my server for packages that are not found in the ubuntu repos and to get it working on my other boxes, I just add (deb [http://www.compaq-web.org/ubuntu](http://www.compaq-web.org/ubuntu) extras main) to my sources file. The files are located at ~/domains/www.compaq-web.org/public_html/ubuntu/pool/main/* and of course, there is a dist file. I build my packages.gz file by running a script like this:

```

#! /bin/bash
cd /home/jms1989/domains/www.compaq-web.org/public_html/ubuntu/
dpkg-scanpackages . /dev/null | gzip -9c > dists/extras/main/binary-i386/Packages.gz

```

I placed the script in my bin dir so it can be ran from the terminal as ($ update-mydebs). It's very nice and handy for large downloads. The files can also be access like anything else at [http://www.compaq-web.org/ubuntu](http://www.compaq-web.org/ubuntu).

Now a not on the server, its behind a firewall and cannot be accessed at that domain from the outside. It is a private domain and works only after editing the hosts file on the machines. I don't feel the need to conceal its local url.

So, for anyone wanting to setup a local repo of their own, they just need to have the packages mentioned from post #1 or at least dpkg-scanpackages installed.

1. Create a directory wherever you want. It best to put it inside a web root or outside on a larger partition and then linked to from inside the web root. I use the ~/domains/www.domain.com/public_html/ structure and have my main config file for my apache hosts pointed to it with a private domain for your machines. You can use a IP but you'd only be able to run one site config.

2. Create a structure inside the base repo dir with something like: mkdir -p {dist,pool}/extras/main/{a..z,liba..z}

3. Add packages in to your main pool but first using the first letter of the deb, I'll use example mydeb-0.15.deb, then make a dir of your package name. Starting at the repo root, it could look something like pool/main/m/mydeb/mydeb-0.15.deb.

Just add each package into their proper dirs and continue to the nest step.

4. Create a file in your bin dir under your user home dir. If it doesn't exist, do (mkdir ~/bin). Open a blank file for editing in your favorite editor, (nano ~/bin/update-mydebs) and add the following:

```

#! /bin/bash
cd /home/user/domains/www.domain.org/public_html/ubuntu/
pkg-scanpackages . /dev/null | gzip -9c > dists/extras/main/binary-i386/Packages.gz

```

Modify the cd dir so it will cd to your repo root and change extras to whatever you chose, then save the file and close the editor.

5. Last but not least, chmod your bash script to 655 so you can execute it and then run it from your terminal.

6. When accessing the personal repo and if you are using a router/gateway as the dns server, you should add your servers' IP address with the domains you are using to each systems' hosts file.

7. Repeat step 3 and 5 anytime you want to add, remove or update a file. Don't forget to update your sources so ubuntu can pick them up. :)

Cheers!

---

### Post by BobSongs on 2009-03-23
> **Geochelone said:**
> And how is this thread --> [http://ubuntuforums.org/showthread.php?t=1090731](http://ubuntuforums.org/showthread.php?t=1090731)

related to our thread here?
Excellent question. I've given the thread a cursory review... but it looks like it is certainly in the family! Thanks, Geochelone! Your detective work is impressive. I'll put a link to it in my tutorial, and credit your effort in finding it.

Thanks!

---

### Post by BobSongs on 2009-03-23
> **jms1989 said:**
> I'm not sure if anyone beside me here has done this but...
...but I think I should have a link to this post too.

Everything and anything that's practical and related to improving this thread is welcome.

Thanks!

---

### Post by Geochelone on 2009-03-24
```
 ! Package libkexiv2-dev (filename ./pool/main/k/kdegraphics/libkexiv2-dev_4.1.4-0ubuntu1~intrepid1_i386.deb) is repeat but newer version;
   used that one and ignored data from ./pool/main/k/kdegraphics/libkexiv2-dev_4.1.3-0ubuntu1~intrepid1_i386.deb !
```

I ran scanpackages, and terminal returned many similar errors (?) as above. What's happening actually? How's this affect my repo?

---

### Post by jms1989 on 2009-03-26
> **Geochelone said:**
> ```
 ! Package libkexiv2-dev (filename ./pool/main/k/kdegraphics/libkexiv2-dev_4.1.4-0ubuntu1~intrepid1_i386.deb) is repeat but newer version;
   used that one and ignored data from ./pool/main/k/kdegraphics/libkexiv2-dev_4.1.3-0ubuntu1~intrepid1_i386.deb !
```

I ran scanpackages, and terminal returned many similar errors (?) as above. What's happening actually? How's this affect my repo?

This is because it found a newer version then the older one or in this case v4.1.4 is newer than 4.1.3. One solution to use to get rid of the warning is to delete the old version.

```
rm ./pool/main/k/kdegraphics/libkexiv2-dev_4.1.3-0ubuntu1~intrepid1_i386.deb
```

Of course, if you chose to keep it, you will continue to see the warning but its safe to keep unless you are running low on space.

Cheers!

---

### Post by luvr on 2009-03-27
> **Geochelone said:**
> And how is this thread --> [http://ubuntuforums.org/showthread.php?t=1090731](http://ubuntuforums.org/showthread.php?t=1090731)

related to our thread here?

I think the threads are very much related indeed, in that they basically attempt to solve the same problem: How to keep Ubuntu up-to-date on a computer that has limited or no internet access.

**BobSongs'** approach actually has a few interesting advantages over mine, in that it will download a fully functional repository--including the control files (i.e., the package list, the release file, and even a valid digital signature)--without any further manual intervention. With my approach, you need to update the control files and regenerate your own digital signature whenever you update the local repository. *(Note, though, that with my method, you can add your own packages that are not available in any online repositories. You cannot do that unless you're prepared to create your own control files, including the digital signature.)*

Also, if I understand correctly, the approach as documented here will automatically clean up your local repository: Any old package versions that are no longer available from the original repository will automatically be removed from your local copy as well. My method, on the other hand, doesn't provide any form of automatic cleanup.

The only potential issue with this method is the humongous amount of data that you will have to download initially, when you want to set up your local copy. But once you're past this potential hurdle, I think it should work great. I think I might give it a try when Jaunty "final" gets released.

As it happens, Ubuntu's parent distribution, Debian, apparently provides pre-built repository CDs and DVDs of its Lenny (5.0) release--cfr. [the Debian web site]("http://www.debian.org/distrib") and navigate to the CD or DVD download pages for more info. *(In fact, there's even a Blu-Ray disc image available!)*

Also, as **BobSongs** notes in the original post, the *debpartial* package is no longer available in the Ubuntu repositories. Debian, on the other hand, still does provide it--cfr. [search results for debpartial in Debian Lenny.]("http://packages.debian.org/search?keywords=debpartial&searchon=names&suite=stable&section=all")

---

### Post by Geochelone on 2009-03-28
Thanks jms1989 for your very clear explaination.

Why debmirror don't clean the duplicates? Intrepid's scanpackage took significant hours to scan and display those dupes. Any bash script to auto remove them?

---

### Post by BobSongs on 2009-03-28
> **luvr said:**
> <snip>Also, if I understand correctly, the approach as documented here will automatically clean up your local repository: Any old package versions that are no longer available from the original repository will automatically be removed from your local copy as well. My method, on the other hand, doesn't provide any form of automatic cleanup.</snip>You're 100% right on that one. In fact, this cleaning up is why more than one repository cannot be easily "blended" with another. There have been attempts at it... some more successful than others... but I maintain the idea of keeping the repos separated for sanity's sake. Adding a few extra CDs when handing a friend the repos is not all that much more drudgery.

> **luvr said:**
> The only potential issue with this method is the humongous amount of data that you will have to download initially, when you want to set up your local copy. But once you're past this potential hurdle, I think it should work great. I think I might give it a try when Jaunty "final" gets released.True! This is why the tutorial is prefaced with an abundance of warning about how much hard drive space will be consumed. For older machines with smaller drives (60 Gb), this can be a problem.[/quote]

By the way, **luvr**, just wanted to say that I appreciate your tutorial's layout.

---

### Post by jms1989 on 2009-04-04
> **Geochelone said:**
> Thanks jms1989 for your very clear explaination.

Why debmirror don't clean the duplicates? Intrepid's scanpackage took significant hours to scan and display those dupes. Any bash script to auto remove them?

Sorry I didn't get back to you sooner, debmirror is supposed to delete the dupes after it finished downloading the Packages and Sources files. However, you can have debmirror delete them by running (debmirror --cleanup ~/UbuntuRepos) or something to that effect I suppose.

---

### Post by Geochelone on 2009-04-11
I don't think debmirror will remove the duplicates. According to the debmirror description, 2nd step of debmirror is

[I]1. First it downloads all Packages and Sources files for the subset of Debian it was instructed to get. 
[B]
2. Any files and directories on the local mirror that are not in the list are removed. [/B]

3.The Packages and Sources files are scanned, to build up a list of all the files they refer to. A few other miscellaneous files are added to the list. Then the program makes sure that each file in the list is present on the local mirror and is up-to-date, using file size (and optionally md5sum) checks. Any necessary files are downloaded.[/I]

So, those old (previously downloaded packages) are there in my mirror, and listed in the newly downloaded Packages list, debmirror won't delete them.

So I read the man again, and I found this option.
[I]
**"--max-batch=number" : Download at most max-batch number of files (and ignore rest).**[/I]

What does it mean actually? Is this option set maximum no of each package? For example:
*abiword-common_2.6.6-0ubuntu1_all.deb*,
*abiword-common_2.6.4-4ubuntu4_all.deb*, and
*abiword-common_2.6.6-0ubuntu1_all.deb*

If I set the max no to 1, will debmirror keep ONLY the latest (abiword-common_2.6.6-0ubuntu1_all.deb), and delete the rest (abiword-common_2.6.6-0ubuntu1_all.deb and abiword-common_2.6.4-4ubuntu4_all.deb)?

---

### Post by Mehashi on 2009-04-11
Thank you BobSongs! 

This guide is so well written, even I could follow it! I have been wanting to do this for a friend with no internet and now I know how, Thank you!

Your section on pointing apt locally will really help for me with my laptop as well, as it has no wireless and my router is nearly always full, now I can just put the debs on there and not worry anymore!

Thanks again for a well written guide!
[COLOR=Magenta]Domo arigato[/COLOR]!
[COLOR=Magenta]^_^[/COLOR]

---

### Post by Geochelone on 2009-04-11
This is what I got running debmirror in Jaunty

```
Mirroring to /media/Tortoise/Repositories/Jaunty/Canonical/ from http://archive.canonical.com///
Arches: i386
Dists: jaunty,jaunty-backports,jaunty-proposed,jaunty-security,jaunty-updates
Sections: partner
Passive mode on.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/jaunty-backports/Release... ok
[0%] Getting: dists/jaunty-proposed/Release... ok
[0%] Getting: dists/jaunty-security/Release... ok
[0%] Getting: dists/jaunty-updates/Release... ok
[0%] Getting: dists/jaunty/Release... ok
Get Packages and Sources files and other miscellany.
**[COLOR="Red"][ 93%] Getting: dists/jaunty-backports/partner/binary-i386/Packages.bz2... dists/jaunty-backports/partner/binary-i386/Packages.bz2 failed 404 Not Found[/COLOR]**
[ 93%] Getting: dists/jaunty-proposed/partner/binary-i386/Packages.bz2... dists/jaunty-proposed/partner/binary-i386/Packages.bz2 failed 404 Not Found
[ 93%] Getting: dists/jaunty-security/partner/binary-i386/Packages.bz2... dists/jaunty-security/partner/binary-i386/Packages.bz2 failed 404 Not Found
[ 93%] Getting: dists/jaunty-updates/partner/binary-i386/Packages.bz2... dists/jaunty-updates/partner/binary-i386/Packages.bz2 failed 404 Not Found
[ 93%] Getting: dists/jaunty/partner/binary-i386/Packages.bz2... dists/jaunty/partner/binary-i386/Packages.bz2 failed 404 Not Found
Missing: .temp/dists/jaunty/partner/binary-i386/Packages
bzip2 -d <.temp/dists/jaunty/partner/binary-i386/Packages.bz2 >.temp/dists/jaunty/partner/binary-i386/Packages
sh: cannot open .temp/dists/jaunty/partner/binary-i386/Packages.bz2: No such file
Failed: bzip2 -d <.temp/dists/jaunty/partner/binary-i386/Packages.bz2 >.temp/dists/jaunty/partner/binary-i386/Packages
WARNING: releasing 1 pending lock...
+\ 
| UPDATING CANONICAL - INTREPID
+/ 
Mirroring to /media/Tortoise/Repositories/Intrepid/Canonical/ from http://archive.canonical.com///
Arches: i386
Dists: intrepid,intrepid-backports,intrepid-proposed,intrepid-security,intrepid-updates
Sections: partner
Passive mode on.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/intrepid-backports/Release... ok
[0%] Getting: dists/intrepid-proposed/Release... ok
[0%] Getting: dists/intrepid-security/Release... ok
[0%] Getting: dists/intrepid-updates/Release... ok
[0%] Getting: dists/intrepid/Release... ok
Get Packages and Sources files and other miscellany.
[ 83%] Getting: dists/intrepid-backports/partner/binary-i386/Packages.bz2... dists/intrepid-backports/partner/binary-i386/Packages.bz2 failed 404 Not Found
[ 83%] Getting: dists/intrepid-proposed/partner/binary-i386/Packages.bz2... dists/intrepid-proposed/partner/binary-i386/Packages.bz2 failed 404 Not Found
[ 83%] Getting: dists/intrepid-security/partner/binary-i386/Packages.bz2... dists/intrepid-security/partner/binary-i386/Packages.bz2 failed 404 Not Found
[ 83%] Getting: dists/intrepid-updates/partner/binary-i386/Packages.bz2... dists/intrepid-updates/partner/binary-i386/Packages.bz2 failed 404 Not Found
[ 83%] Getting: dists/intrepid/partner/binary-i386/Packages.bz2... dists/intrepid/partner/binary-i386/Packages.bz2 failed 404 Not Found
Missing: .temp/dists/intrepid/partner/binary-i386/Packages
bzip2 -d <.temp/dists/intrepid/partner/binary-i386/Packages.bz2 >.temp/dists/intrepid/partner/binary-i386/Packages
sh: cannot open .temp/dists/intrepid/partner/binary-i386/Packages.bz2: No such file
Failed: bzip2 -d <.temp/dists/intrepid/partner/binary-i386/Packages.bz2 >.temp/dists/intrepid/partner/binary-i386/Packages
WARNING: releasing 1 pending lock...

```

And this is debmirror in Intrepid

```
Mirroring to /home/macrochelodina/Repositories/Jaunty/Canonical from http://archive.canonical.com///
Arches: i386
Dists: jaunty,jaunty-backports,jaunty-proposed,jaunty-security,jaunty-updates
Sections: partner
Passive mode on.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/jaunty/Release... ok
[0%] Getting: dists/jaunty/Release.gpg... ok
[0%] Getting: dists/jaunty-backports/Release... ok
[0%] Getting: dists/jaunty-backports/Release.gpg... ok
[0%] Getting: dists/jaunty-proposed/Release... ok
[0%] Getting: dists/jaunty-proposed/Release.gpg... ok
[0%] Getting: dists/jaunty-security/Release... ok
[0%] Getting: dists/jaunty-security/Release.gpg... ok
[0%] Getting: dists/jaunty-updates/Release... ok
[0%] Getting: dists/jaunty-updates/Release.gpg... ok
Get Packages and Sources files and other miscellany.
dists/jaunty/partner/binary-i386/Packages.gz needs fetch
**[COLOR="Red"][ 94%] Getting: dists/jaunty/partner/binary-i386/Packages.gz... ok[/COLOR]**
Parse Packages and Sources files and add to the file list everything therein.
Cleanup mirror.
deleting pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.12.36-1intrepid2_i386.deb
Download all files that we need to get (4 MiB).
[  1%] Getting: pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87-2jaunty1_i386.deb... ok
Downloaded 4 MiB in 963s at 4.06 kiB/s
Everything OK. Moving meta files.
All done.
+\ 
| UPDATING CANONICAL - INTREPID
+/ 
Mirroring to /home/macrochelodina/Repositories/Intrepid/Canonical from http://archive.canonical.com///
Arches: i386
Dists: intrepid,intrepid-backports,intrepid-proposed,intrepid-security,intrepid-updates
Sections: partner
Passive mode on.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/intrepid/Release... ok
[0%] Getting: dists/intrepid/Release.gpg... ok
[0%] Getting: dists/intrepid-backports/Release... ok
[0%] Getting: dists/intrepid-backports/Release.gpg... ok
[0%] Getting: dists/intrepid-proposed/Release... ok
[0%] Getting: dists/intrepid-proposed/Release.gpg... ok
[0%] Getting: dists/intrepid-security/Release... ok
[0%] Getting: dists/intrepid-security/Release.gpg... ok
[0%] Getting: dists/intrepid-updates/Release... ok
[0%] Getting: dists/intrepid-updates/Release.gpg... ok
Get Packages and Sources files and other miscellany.
dists/intrepid/partner/binary-i386/Packages.gz needs fetch
[ 84%] Getting: dists/intrepid/partner/binary-i386/Packages.gz... ok
Parse Packages and Sources files and add to the file list everything therein.
Cleanup mirror.
deleting project/trace/geochelone-jaunty
Download all files that we need to get (1 MiB).
Downloaded 1 MiB in 30s at 1.4 kiB/s
Everything OK. Moving meta files.
All done.
macrochelodina@macrochelodina-repo:~/Desktop$
```

Is this a bug? Why Jaunty try to fetch Packages.bz2 instead of Packages.gz? I check the repo, there is indeed no bz2, only gz.

I failed to update Canonical repo in Jaunty because of this. In Intrepid, Canonical is updated good.

If this is a bug, somebody with Launchpad account may want to highlight this.

This is from Ubuntu Jaunty Beta.

---

### Post by k3lt01 on 2009-04-11
Hi Geo, its not a bug it seems to be quite deliberate actually. I tried the exact same things ages ago when Gutsy was in Beta (or maybe it was Hardy I can't remember but I did post about it here). Anyway don't bother trying to download the repos for a non production version cause it wont work because they either use another format and/or are incomplete anyway because of the continuous updating that is happening.

---

### Post by Geochelone on 2009-04-12
k3lt01, thanks for the info. Then I guess I really should wait Jaunty goes official. For the time being I will update my repos from Intrepid.

**About duplicate packages in current repo.**

How about I setup an Apache server and host the current repo locally? Then I debmirror from that server. So my question is, will my new repo excludes those old duplicate packages, and results a new repo w/o the dupes?

---

### Post by BobSongs on 2009-04-13
> **Geochelone said:**
> k3lt01, thanks for the info. Then I guess I really should wait Jaunty goes official. For the time being I will update my repos from Intrepid.

**About duplicate packages in current repo.**

How about I setup an Apache server and host the current repo locally? Then I debmirror from that server. So my question is, will my new repo excludes those old duplicate packages, and results a new repo w/o the dupes?
Let's see if I've got this correctly. You want to host Intrepid's repositories on your Apache server. If you place your current Intrepid repository folders on the server and run **debmirror** from there, only the latest updates should be downloaded and added to that set of files. I'm not clear on what "those old duplicate packages" means, exactly. But I imagine you're not wanting a duplicate set of repository files. Make sure **debmirror** knows where to place the files: in the exact name as the folder that has the files ([COLOR=SeaGreen]**/UbuntuRepos**[/COLOR], by default.)

I agree with Kelt03 on this one, Geochelone. The Jaunty repositories are most likely off limits until a stable version is determined. Beta testers can download and upgrade. But debmirror enthusiasts will hit a snag on that one. At this point it really isn't worth the effort. But I will post a note on the tutorial when the release happens: Don't try to run debmirror when the new release is freshly out. That is a frenzy time and it means slower downloads for everyone else. I use the Canadian mirror, and I currently only maintain the tutorial. I no longer need it. But I feel it's important to maintain.

---

### Post by BobSongs on 2009-04-13
> **Mehashi said:**
> Thank you BobSongs! 

This guide is so well written, even I could follow it! I have been wanting to do this for a friend with no internet and now I know how, Thank you!
I'm not a faster learner. I'm not. And I've seen tutorials where authors assume we regularly compile our kernels. Sometimes important steps are either skipped or impatiently referred to ("now recompile your kernel with these switches turned off") :(

My view is that tutorials should take a person by the hand and walk them through such that even a Windows user could, if not too impatient, actually succeed in completing it and maybe even learn a bit on the way.

> **Mehashi said:**
>  Your section on pointing apt locally will really help for me with my laptop as well, as it has no wireless and my router is nearly always full, now I can just put the debs on there and not worry anymore!

Thanks again for a well written guide!
[COLOR=Magenta]Domo arigato[/COLOR]!
[COLOR=Magenta]^_^[/COLOR]
A big "thank-you" from all who've helped put this together. Don't forget that repository DVDs can also be purchased from a couple of suppliers. From time to time I check to see if they are still making these available. (I don't get any profit from those sales.)

---

### Post by Geochelone on 2009-04-15
From **man dpkg-scanpackages**:
***If  more than one version of a package is found only the newest one is included in the output (1).** If they have the same version and only differ in architecture only the first one found is used.*

So I did host Intrepid repo from Apache server, and debmirror it in hope it will exclude everything except the newest (1) version of packages. However, it's not the case with me. There are tons of old version of packages, and debmirror still download them. Luckily it's from 127.0.0.1 and thus blazing fast and unmetered.

Example:

```
! Package bind9-doc (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/bind9-doc_9.5.0.dfsg.P2-1ubuntu3.1_all.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/bind9-doc_9.5.0.dfsg.P2-1ubuntu2_all.deb !
 ! Package bind9-host (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/bind9-host_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/bind9-host_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
 ! Package bind9utils (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/bind9utils_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/bind9utils_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
 ! Package bind9 (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/bind9_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/bind9_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
 ! Package dnsutils (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/dnsutils_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/dnsutils_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
 ! Package libbind-dev (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libbind-dev_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libbind-dev_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
 ! Package libbind9-40 (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libbind9-40_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libbind9-40_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
 ! Package libdns43 (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libdns43_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libdns43_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
 ! Package libisc44 (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libisc44_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libisc44_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
 ! Package libisccc40 (filename /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libisccc40_9.5.0.dfsg.P2-1ubuntu3.1_i386.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Official/pool/main/b/bind9/libisccc40_9.5.0.dfsg.P2-1ubuntu2_i386.deb !
```

I'm thinking of grep the error output and capture the old version of the packages, then rm all of them in single command. Any idea how to get em?

I do this primarily to shave some space from them, and make my repo tidier lol. It is also a good reason to actually learn to use various commands in achieving our targets. I personally learns a ton just from maintaining the repos. And I feel very good about it.

---

### Post by luvr on 2009-04-15
> **Geochelone said:**
> From **man dpkg-scanpackages**:
***If  more than one version of a package is found only the newest one is included in the output (1).** If they have the same version and only differ in architecture only the first one found is used.*

So I did host Intrepid repo from Apache server, and debmirror it in hope it will exclude everything except the newest (1) version of packages. However, it's not the case with me. There are tons of old version of packages, and debmirror still download them.

I'm not really in a position to offer an authoritative answser to this issue, but it seems to me that **debmirror** will download *everything* from its source repository--including multiple versions of the same package, if they are present. The old package versions will probably get deleted from your local copy only if they are no longer present at the source location.

The **dpkg-scanpackages** utility will scan your (local copy of the) repository, and rebuild the index file (which lists all packages available in the repository). However, whenever it finds multiple versions of a particular package, it will register only the newest version in the index file.

So, it's not **debmirror** that will delete old versions of packages (if they're still available at the source location), but it's **dpkg-scanpackages** that will not add them to the index file.

I, too, have been thinking of creating a list of the older packages, so I could subsequently delete them, but I'm not sure yet how I would do it.

---

### Post by k3lt01 on 2009-04-17
> **billyg said:**
> Nice tutorial. I will create one dvd as soon asOne? I think its more like 5 dvds from 7.04-Feisty till the current release.

---

### Post by luvr on 2009-04-18
> **luvr said:**
> I, too, have been thinking of creating a list of the older packages, so I could subsequently delete them, but I'm not sure yet how I would do it.
It looks like I found a way to do it after all: [ADDENDUM: Removing Old Package Versions from your Local Repository.]("http://ubuntuforums.org/showpost.php?p=7097305&postcount=12") Be forwarned that it's kind of a quick'n'dirty hack, though. Use at your own risk!

---

### Post by maison09 on 2009-04-23
Thank you so much for your great work:guitar:

[right][[color=#FFFFFF]_maison de credit_[/color]](http://maisondecredit.com)[/right]

---

### Post by Geochelone on 2009-04-26
Does Jaunty repo (main, i386) contain only firefox-3.0 and xulrunner-1.9? OMG debmirror wiped other packages and left me with those two packages.

However restricted, multiverse, and universe seem OK though.

;_;

---

### Post by nburro on 2009-04-26
> **Geochelone said:**
> Does Jaunty repo (main, i386) contain only firefox-3.0 and xulrunner-1.9? OMG debmirror wiped other packages and left me with those two packages.

However restricted, multiverse, and universe seem OK though.

;_;

Perhaps you are mistakenly mirroring the jaunty-updates repository into your jaunty local mirror location? My local updates/pool/main folder only contains those two sets of packages.

---

### Post by k3lt01 on 2009-04-27
> **Geochelone said:**
> Does Jaunty repo (main, i386) contain only firefox-3.0 and xulrunner-1.9? OMG debmirror wiped other packages and left me with those two packages.

However restricted, multiverse, and universe seem OK though.

;_;The main repo contains what is on the installation cd's "main" repo. I would be leaving it for a few days before starting to download the repo as traffic for updates and cd downloads will still be very high. Give everyone else a chance to at least get the cd etc just like you seem to have already, before you try to get the entire repo.

---

### Post by Geochelone on 2009-04-30
I found that Jaunty's debmirror is much more verbose compared to Intrepid's.

---

### Post by k3lt01 on 2009-04-30
> **Geochelone said:**
> I found that Jaunty's debmirror is much more verbose compared to Intrepid's. I don't understand what you mean with this, care to explain?

---

### Post by BobSongs on 2009-04-30
> **k3lt01 said:**
> [quote=Geochelone;7182313]I found that Jaunty's debmirror is much more verbose compared to Intrepid's.I don't understand what you mean with this, care to explain?[/quote]
Sounds interesting either way. I haven't installed Jaunty, so I'm not sure what this means. I do know that the **debpartial** file has changed names, making the link in the tutorial obsolete and requiring change. That's all fixed now.

Geochelone? Could you provide a screenshot of what you mean?

Thanks.

---

### Post by danboid on 2009-05-07
I've followed this guide and successfully created some DVDs of the Jaunty i386 repo. However, I also wanted to create a separate set of archive DVDs for the Jaunty source debs hence I omitted the --nosource flag from the debmirror command to downloaded the source packages too. I can't for the life of me work out how to use debpartial to just extract and archive the source debs though. I know I prob need to use --dirsrcprefix but what would be the correct value or can I use anything? It has a --merge-source too but what if you just want source debs?

Also, is it possible to use debmirror to download more than one arch at a time if I wanted to download and mirror both i386 and amd64?

Thanks!

Dan

---

### Post by k3lt01 on 2009-05-07
Hi Dan, I cant comment on the first part of your post as I honestly don't now enough about it to comment with any authority. However for the question below in the quote box I'll give you my thoughts.

> **danboid said:**
>  Also, is it possible to use debmirror to download more than one arch at a time if I wanted to download and mirror both i386 and amd64?

With this I think the answer would be a yes you can do it. But I would ask you why would you do it this way anyway? unless of course you are hosting this on your own server that will supply the repos to multiple architectures. From taking a very indepth look at the structure of the "old-releases.ubuntu.com" archive the repos are all contained in the one folder anyway and the "--arch=" command is the one that you need to modify. So instead of having

```
debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg
```

You could have ```
debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=i386,amd64 ~/UbuntuRepos --ignore-release-gpg
```

Please note the above uses Hardy, not Jaunty or Intrepid, coding but it is easily modified to suit.

---

### Post by BobSongs on 2009-05-07
Thanks, k3lt01! If there was anyone I'd trust to take over this thread's management, it's you. ;)

The --arch=i386,amd64 solution should work just fine. **danboid**, feel like being our tester?

---

### Post by danboid on 2009-05-08
Thanks k3lt and Bob!

I'm an IT tech at a large school - we've got a few Linux machines here (mostly in the server room of course) but its Windows everywhere else still but I'm pushing for FOSS where POSS ;) Prob is that not all the machines in the school are amd64 / EMT64 capable. You should run 64-bit Linux where poss and hence my desire to archive/mirror both i386 and amd64.

Dunno if I will get round to testing the i386,amd64 option now as that was something I needed to know BEFORE I went ahead and downloaded both i386 and the source. After I've worked out how to archive the source onto DVDs I'll be deleting both the i386 and the source to make way for the amd64 debs which I'll prob keep on my local HD and keep updated and acessable on the local network.

As you can tell from my previous post- seeing as it was both my first question and comprising the bulk of my post, what I really want to know is how to archive the source. It would seem that (the poorly documented) debpartial expects that you'd only ever want to archive binaries or binaries and source, not just source.

Bob- Yes- I just have 1 folder ~/UbuntuRepos, which contains both the source debs and binaries, so I'd need debpartial to divide it up or, as a last resort, a script that would intelligently delete the binary debs and just leave the src debs- but I'm sure there's more to it than that.

I have been on #ubuntu, #debian and #ubuntu-mirrors asking this very question and nobody has a clue. If I work it out I'll yet you all know here.

---

### Post by k3lt01 on 2009-05-08
> **BobSongs said:**
> Thanks, k3lt01! If there was anyone I'd trust to take over this thread's management, it's you. ;)

The --arch=i386,amd64 solution should work just fine. **danboid**, feel like being our tester?

Thanks for your kind words BobSongs.

I actually tried to test it yesterday and everything seemed ok until I got a message telling me various files were missing. I then tested it with just one architecture and got the same message.I also tested both versions on Warty and I even get the "missing" message with the Warty repositories.

Dan, I get what your thinking now and understand the need for an efficient download. I hope you work out the source vs binary issue soon.

---

### Post by danboid on 2009-05-08
UPDATE:

I have just wrote to the author of debpartial to find out if it does what I want it to do, and if so how?

Bobsongs:

I need to clarify my response about the format of the jaunty mirror tree, as I didn't give enough detail before.

Under ~/UbuntuRepos/dists/jaunty/main I have two folders, binary-i386 and source. Same goes for ~/UbuntuRepos/dists/jaunty/universe, ~/UbuntuRepos/dists/jaunty/restricted and ~/UbuntuRepos/dists/jaunty/multiverse. The same pattern gets repeated under ~/UbuntuRepos/dists/jaunty-backports, ~/UbuntuRepos/dists/jaunty-security and ~/UbuntuRepos/dists/jaunty-updates in that each one of them contains a similar structure of folders (main, universe, multiverse and restricted subfolders with source and binary sub-folders within them) - just like on the 'real' ubuntu mirrors.

---

### Post by BobSongs on 2009-05-08
OK...

~ [SIZE=3][COLOR=DimGray]**Download Test**[/COLOR][/SIZE] ~
[SIZE=3][COLOR=Blue]**Idea**[/COLOR][/SIZE]: include [COLOR=DimGray]**i386**[/COLOR] and [COLOR=DimGray]**amd64**[/COLOR] with [COLOR=DimGray]**sources**[/COLOR].
[SIZE=3][COLOR=SeaGreen]**Result**[/COLOR][/SIZE]: complete success.

When browsing with Nautilus in the UbuntuRepos folder, I opened **dists** followed by **hardy** followed by **main**. These 3 subfolders appeared:

[LIST]
[*]**binary-amd64**
[*]**binary-i386**
[*]**source**
[/LIST]
 Here's the test command (**--nosource** removed, modified text in [COLOR=Red]**red**[/COLOR]):
```
debmirror --md5sum --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse **[COLOR=Red]--arch=i386,amd64[/COLOR]** ~/UbuntuRepos --ignore-release-gpg
```Here's what happened in the Terminal:

```
Mirroring to /home/bob/UbuntuRepos from [ftp://anonymous@archive.ubuntu.com/ubuntu//](ftp://anonymous@archive.ubuntu.com/ubuntu//)
Arches: i386,amd64
Dists: hardy,hardy-security,hardy-updates,hardy-backports
Sections: main,restricted,universe,multiverse
Including source.
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Keeping: dists/hardy/Release
[0%] Keeping: dists/hardy/Release.gpg
[0%] Keeping: dists/hardy-security/Release
[0%] Keeping: dists/hardy-security/Release.gpg
[0%] Keeping: dists/hardy-updates/Release
[0%] Keeping: dists/hardy-updates/Release.gpg
[0%] Keeping: dists/hardy-backports/Release
[0%] Keeping: dists/hardy-backports/Release.gpg
Get Packages and Sources files and other miscellany.
dists/hardy/main/binary-i386/Packages.gz needs fetch
[  0%] Getting: dists/hardy/main/binary-i386/Packages.gz     ###############
dists/hardy/main/binary-i386/Release needs fetch
[  9%] Getting: dists/hardy/main/binary-i386/Release     #
dists/hardy/main/binary-amd64/Packages.gz needs fetch
[  9%] Getting: dists/hardy/main/binary-amd64/Packages.gz     ###############
dists/hardy/main/binary-amd64/Release needs fetch
[ 17%] Getting: dists/hardy/main/binary-amd64/Release     #
dists/hardy/main/source/Sources.gz needs fetch
[ 17%] Getting: dists/hardy/main/source/Sources.gz     #####
dists/hardy/main/source/Release needs fetch
[ 19%] Getting: dists/hardy/main/source/Release     #
dists/hardy/restricted/binary-i386/Packages.gz needs fetch
[ 19%] Getting: dists/hardy/restricted/binary-i386/Packages.gz     #
dists/hardy/restricted/binary-i386/Release needs fetch
[ 19%] Getting: dists/hardy/restricted/binary-i386/Release     #
dists/hardy/restricted/binary-amd64/Packages.gz needs fetch
[ 19%] Getting: dists/hardy/restricted/binary-amd64/Packages.gz     #
dists/hardy/restricted/binary-amd64/Release needs fetch
[ 19%] Getting: dists/hardy/restricted/binary-amd64/Release     #
dists/hardy/restricted/source/Sources.gz needs fetch
[ 19%] Getting: dists/hardy/restricted/source/Sources.gz     #
dists/hardy/restricted/source/Release needs fetch
[ 19%] Getting: dists/hardy/restricted/source/Release     #
dists/hardy/universe/binary-i386/Packages.gz needs fetch
[ 19%] Getting: dists/hardy/universe/binary-i386/Packages.gz     #######################################################
dists/hardy/universe/binary-i386/Release needs fetch
[ 45%] Getting: dists/hardy/universe/binary-i386/Release     #
dists/hardy/universe/binary-amd64/Packages.gz needs fetch
[ 45%] Getting: dists/hardy/universe/binary-amd64/Packages.gz     #######################################################
dists/hardy/universe/binary-amd64/Release needs fetch
[ 70%] Getting: dists/hardy/universe/binary-amd64/Release     #
dists/hardy/universe/source/Sources.gz needs fetch
[ 70%] Getting: dists/hardy/universe/source/Sources.gz     ##################
dists/hardy/universe/source/Release needs fetch
[ 78%] Getting: dists/hardy/universe/source/Release     #
dists/hardy/multiverse/binary-i386/Packages.gz needs fetch
[ 78%] Getting: dists/hardy/multiverse/binary-i386/Packages.gz     ###
dists/hardy/multiverse/binary-i386/Release needs fetch
[ 80%] Getting: dists/hardy/multiverse/binary-i386/Release     #
dists/hardy/multiverse/binary-amd64/Packages.gz needs fetch
[ 80%] Getting: dists/hardy/multiverse/binary-amd64/Packages.gz     ###
dists/hardy/multiverse/binary-amd64/Release needs fetch
[ 81%] Getting: dists/hardy/multiverse/binary-amd64/Release     #
dists/hardy/multiverse/source/Sources.gz needs fetch
[ 81%] Getting: dists/hardy/multiverse/source/Sources.gz     #
dists/hardy/multiverse/source/Release needs fetch
[ 81%] Getting: dists/hardy/multiverse/source/Release     #
dists/hardy-security/main/binary-i386/Packages.gz needs fetch
[ 81%] Getting: dists/hardy-security/main/binary-i386/Packages.gz     ##
dists/hardy-security/main/binary-i386/Release needs fetch
[ 82%] Getting: dists/hardy-security/main/binary-i386/Release     #
dists/hardy-security/main/binary-amd64/Packages.gz needs fetch
[ 82%] Getting: dists/hardy-security/main/binary-amd64/Packages.gz     ##
dists/hardy-security/main/binary-amd64/Release needs fetch
[ 83%] Getting: dists/hardy-security/main/binary-amd64/Release     #
dists/hardy-security/main/source/Sources.gz needs fetch
[ 83%] Getting: dists/hardy-security/main/source/Sources.gz     #
dists/hardy-security/main/source/Release needs fetch
[ 84%] Getting: dists/hardy-security/main/source/Release     #
dists/hardy-security/restricted/binary-i386/Packages.gz needs fetch
[ 84%] Getting: dists/hardy-security/restricted/binary-i386/Packages.gz     #
dists/hardy-security/restricted/binary-i386/Release needs fetch
[ 84%] Getting: dists/hardy-security/restricted/binary-i386/Release     #
dists/hardy-security/restricted/binary-amd64/Packages.gz needs fetch
[ 84%] Getting: dists/hardy-security/restricted/binary-amd64/Packages.gz     #
dists/hardy-security/restricted/binary-amd64/Release needs fetch
[ 84%] Getting: dists/hardy-security/restricted/binary-amd64/Release     #
dists/hardy-security/restricted/source/Sources.gz needs fetch
[ 84%] Getting: dists/hardy-security/restricted/source/Sources.gz     #
dists/hardy-security/restricted/source/Release needs fetch
[ 84%] Getting: dists/hardy-security/restricted/source/Release     #
dists/hardy-security/universe/binary-i386/Packages.gz needs fetch
[ 84%] Getting: dists/hardy-security/universe/binary-i386/Packages.gz     #
dists/hardy-security/universe/binary-i386/Release needs fetch
[ 84%] Getting: dists/hardy-security/universe/binary-i386/Release     #
dists/hardy-security/universe/binary-amd64/Packages.gz needs fetch
[ 84%] Getting: dists/hardy-security/universe/binary-amd64/Packages.gz     #
dists/hardy-security/universe/binary-amd64/Release needs fetch
[ 85%] Getting: dists/hardy-security/universe/binary-amd64/Release     #
dists/hardy-security/universe/source/Sources.gz needs fetch
[ 85%] Getting: dists/hardy-security/universe/source/Sources.gz     #
dists/hardy-security/universe/source/Release needs fetch
[ 85%] Getting: dists/hardy-security/universe/source/Release     #
dists/hardy-security/multiverse/binary-i386/Packages.gz needs fetch
[ 85%] Getting: dists/hardy-security/multiverse/binary-i386/Packages.gz     #
dists/hardy-security/multiverse/binary-i386/Release needs fetch
[ 85%] Getting: dists/hardy-security/multiverse/binary-i386/Release     #
dists/hardy-security/multiverse/binary-amd64/Packages.gz needs fetch
[ 85%] Getting: dists/hardy-security/multiverse/binary-amd64/Packages.gz     #
dists/hardy-security/multiverse/binary-amd64/Release needs fetch
[ 85%] Getting: dists/hardy-security/multiverse/binary-amd64/Release     #
dists/hardy-security/multiverse/source/Sources.gz needs fetch
[ 85%] Getting: dists/hardy-security/multiverse/source/Sources.gz     #
dists/hardy-security/multiverse/source/Release needs fetch
[ 85%] Getting: dists/hardy-security/multiverse/source/Release     #
dists/hardy-updates/main/binary-i386/Packages.gz needs fetch
[ 85%] Getting: dists/hardy-updates/main/binary-i386/Packages.gz     ######
dists/hardy-updates/main/binary-i386/Release needs fetch
[ 89%] Getting: dists/hardy-updates/main/binary-i386/Release     #
dists/hardy-updates/main/binary-amd64/Packages.gz needs fetch
[ 89%] Getting: dists/hardy-updates/main/binary-amd64/Packages.gz     ######
dists/hardy-updates/main/binary-amd64/Release needs fetch
[ 92%] Getting: dists/hardy-updates/main/binary-amd64/Release     #
dists/hardy-updates/main/source/Sources.gz needs fetch
[ 92%] Getting: dists/hardy-updates/main/source/Sources.gz     ##
dists/hardy-updates/main/source/Release needs fetch
[ 93%] Getting: dists/hardy-updates/main/source/Release     #
dists/hardy-updates/restricted/binary-i386/Packages.gz needs fetch
[ 93%] Getting: dists/hardy-updates/restricted/binary-i386/Packages.gz     #
dists/hardy-updates/restricted/binary-i386/Release needs fetch
[ 93%] Getting: dists/hardy-updates/restricted/binary-i386/Release     #
dists/hardy-updates/restricted/binary-amd64/Packages.gz needs fetch
[ 93%] Getting: dists/hardy-updates/restricted/binary-amd64/Packages.gz     #
dists/hardy-updates/restricted/binary-amd64/Release needs fetch
[ 93%] Getting: dists/hardy-updates/restricted/binary-amd64/Release     #
dists/hardy-updates/restricted/source/Sources.gz needs fetch
[ 93%] Getting: dists/hardy-updates/restricted/source/Sources.gz     #
dists/hardy-updates/restricted/source/Release needs fetch
[ 93%] Getting: dists/hardy-updates/restricted/source/Release     #
dists/hardy-updates/universe/binary-i386/Packages.gz needs fetch
[ 93%] Getting: dists/hardy-updates/universe/binary-i386/Packages.gz     ###
dists/hardy-updates/universe/binary-i386/Release needs fetch
[ 94%] Getting: dists/hardy-updates/universe/binary-i386/Release     #
dists/hardy-updates/universe/binary-amd64/Packages.gz needs fetch
[ 94%] Getting: dists/hardy-updates/universe/binary-amd64/Packages.gz     ###
dists/hardy-updates/universe/binary-amd64/Release needs fetch
[ 96%] Getting: dists/hardy-updates/universe/binary-amd64/Release     #
dists/hardy-updates/universe/source/Sources.gz needs fetch
[ 96%] Getting: dists/hardy-updates/universe/source/Sources.gz     #
dists/hardy-updates/universe/source/Release needs fetch
[ 96%] Getting: dists/hardy-updates/universe/source/Release     #
dists/hardy-updates/multiverse/binary-i386/Packages.gz needs fetch
[ 96%] Getting: dists/hardy-updates/multiverse/binary-i386/Packages.gz     #
dists/hardy-updates/multiverse/binary-i386/Release needs fetch
[ 96%] Getting: dists/hardy-updates/multiverse/binary-i386/Release     #
dists/hardy-updates/multiverse/binary-amd64/Packages.gz needs fetch
[ 96%] Getting: dists/hardy-updates/multiverse/binary-amd64/Packages.gz     #
dists/hardy-updates/multiverse/binary-amd64/Release needs fetch
[ 96%] Getting: dists/hardy-updates/multiverse/binary-amd64/Release     #
dists/hardy-updates/multiverse/source/Sources.gz needs fetch
[ 96%] Getting: dists/hardy-updates/multiverse/source/Sources.gz     #
dists/hardy-updates/multiverse/source/Release needs fetch
[ 96%] Getting: dists/hardy-updates/multiverse/source/Release     #
dists/hardy-backports/main/binary-i386/Packages.gz needs fetch
[ 96%] Getting: dists/hardy-backports/main/binary-i386/Packages.gz     ##
dists/hardy-backports/main/binary-i386/Release needs fetch
[ 97%] Getting: dists/hardy-backports/main/binary-i386/Release     #
dists/hardy-backports/main/binary-amd64/Packages.gz needs fetch
[ 97%] Getting: dists/hardy-backports/main/binary-amd64/Packages.gz     ##
dists/hardy-backports/main/binary-amd64/Release needs fetch
[ 98%] Getting: dists/hardy-backports/main/binary-amd64/Release     #
dists/hardy-backports/main/source/Sources.gz needs fetch
[ 98%] Getting: dists/hardy-backports/main/source/Sources.gz     #
dists/hardy-backports/main/source/Release needs fetch
[ 98%] Getting: dists/hardy-backports/main/source/Release     #
dists/hardy-backports/restricted/binary-i386/Packages.gz needs fetch
[ 98%] Getting: dists/hardy-backports/restricted/binary-i386/Packages.gz     #
dists/hardy-backports/restricted/binary-i386/Release needs fetch
[ 98%] Getting: dists/hardy-backports/restricted/binary-i386/Release     #
dists/hardy-backports/restricted/binary-amd64/Packages.gz needs fetch
[ 98%] Getting: dists/hardy-backports/restricted/binary-amd64/Packages.gz     #
dists/hardy-backports/restricted/binary-amd64/Release needs fetch
[ 98%] Getting: dists/hardy-backports/restricted/binary-amd64/Release     #
dists/hardy-backports/restricted/source/Sources.gz needs fetch
[ 98%] Getting: dists/hardy-backports/restricted/source/Sources.gz     #
dists/hardy-backports/restricted/source/Release needs fetch
[ 98%] Getting: dists/hardy-backports/restricted/source/Release     #
dists/hardy-backports/universe/binary-i386/Packages.gz needs fetch
[ 98%] Getting: dists/hardy-backports/universe/binary-i386/Packages.gz     ##
dists/hardy-backports/universe/binary-i386/Release needs fetch
[ 99%] Getting: dists/hardy-backports/universe/binary-i386/Release     #
dists/hardy-backports/universe/binary-amd64/Packages.gz needs fetch
[ 99%] Getting: dists/hardy-backports/universe/binary-amd64/Packages.gz     ##
dists/hardy-backports/universe/binary-amd64/Release needs fetch
[100%] Getting: dists/hardy-backports/universe/binary-amd64/Release     #
dists/hardy-backports/universe/source/Sources.gz needs fetch
[100%] Getting: dists/hardy-backports/universe/source/Sources.gz     #
dists/hardy-backports/universe/source/Release needs fetch
[100%] Getting: dists/hardy-backports/universe/source/Release     #
dists/hardy-backports/multiverse/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/hardy-backports/multiverse/binary-i386/Packages.gz     #
dists/hardy-backports/multiverse/binary-i386/Release needs fetch
[100%] Getting: dists/hardy-backports/multiverse/binary-i386/Release     #
dists/hardy-backports/multiverse/binary-amd64/Packages.gz needs fetch
[100%] Getting: dists/hardy-backports/multiverse/binary-amd64/Packages.gz     #
dists/hardy-backports/multiverse/binary-amd64/Release needs fetch
[100%] Getting: dists/hardy-backports/multiverse/binary-amd64/Release     #
dists/hardy-backports/multiverse/source/Sources.gz needs fetch
[100%] Getting: dists/hardy-backports/multiverse/source/Sources.gz     #
dists/hardy-backports/multiverse/source/Release needs fetch
[100%] Getting: dists/hardy-backports/multiverse/source/Release     #
Parse Packages and Sources files and add to the file list everything therein.
[  0%] Getting: pool/main/a/aalib/aalib_1.4p5-33ubuntu1.diff.gz     #
[  0%] Getting: pool/main/a/aalib/aalib_1.4p5-33ubuntu1.dsc     #
[  0%] Getting: pool/main/a/aalib/aalib_1.4p5.orig.tar.gz     ####
[  0%] Getting: pool/main/a/aalib/libaa1-dbg_1.4p5-33ubuntu1_amd64.deb     #
[  0%] Getting: pool/main/a/aalib/libaa1-dbg_1.4p5-33ubuntu1_i386.deb     #
[  0%] Getting: pool/main/a/aalib/libaa1-dev_1.4p5-33ubuntu1_amd64.deb     ##
[  0%] Getting: pool/main/a/aalib/libaa1-dev_1.4p5-33ubuntu1_i386.deb     ##
[  0%] Getting: pool/main/a/aalib/libaa1_1.4p5-33ubuntu1_amd64.deb     #
[  0%] Getting: pool/main/a/aalib/libaa1_1.4p5-33ubuntu1_i386.deb     #
[  0%] Getting: pool/main/a/abiword/abiword-common_2.4.6-3ubuntu3_all.deb     ###################
[  0%] Getting: pool/main/a/abiword/abiword-gnome_2.4.6-3ubuntu3_amd64.deb     #######################
[  0%] Getting: pool/main/a/abiword/abiword-gnome_2.4.6-3ubuntu3_i386.deb     #######

ETC....

```As this was just a test and I have no intention of downloading 70 Ziggabytes of data (;)), I stopped after a few seconds.

How this monster download would be cut up into DVDs will have to be confirmed. I reviewed the **departial** manual page and believe that removing the **--nosource** switch is important. My **guess** is that the **debpartial** is now run like this (note the sections in bold red text to mark the difference):

```
debpartial --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=hardy,hardy-security,hardy-updates,hardy-backports [COLOR=Red]**--arch=i386,amd64 **[/COLOR]--size=DVD ~/UbuntuRepos ~/UbuntuDVDs
```Compare to the standard **debpartial** command:```
debpartial [COLOR=Blue]**--nosource**[/COLOR] --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=hardy,hardy-security,hardy-updates,hardy-backports --size=DVD ~/UbuntuRepos ~/UbuntuDVDs
```By extension, to create DVDs of just the **i386**, then the **amd64**, these may be the proper debpartial commands:

For **[COLOR=RoyalBlue]i386[/COLOR]**:
```
debpartial --nosource **[COLOR=Red]--arch=i386[/COLOR]** --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=hardy,hardy-security,hardy-updates,hardy-backports --size=DVD ~/UbuntuRepos ~/UbuntuDVDs
```For **[COLOR=Green]amd64[/COLOR]**:
```
debpartial --nosource **[COLOR=red]--arch=amd64[/COLOR]** --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=hardy,hardy-security,hardy-updates,hardy-backports --size=DVD ~/UbuntuRepos ~/UbuntuDVDs
```How **debpartial** would create DVDs for just the sources? Unknown. The **man** page is tough enough to decipher. But specifying just the sources for ISO creation... for that I'll need help.

If any brave downloader wants to do 50 hrs+ downloading ... just to confirm this... you'll get a gold star!

:KS

---

### Post by egalvan on 2009-05-16
I purchased a set of Ubuntu repo DVDs from osdisc.com (among others)

( Great service, by the way. Recommended.)


Is there a way of using these,
to take the place of the large initial download?

I have no way of downloading such large quantities,
but I *am* able to keep them updated.


Thanks.

ErnestG

---

### Post by k3lt01 on 2009-05-16
Yes there is.

1. Check the structure of the disc contents. Use either [old-releases]("http://old-releases.ubuntu.com/ubuntu/") or [archive]("ftp://archive.ubuntu.com/ubuntu/") to check if the discs structure is the same as the official repositories (it should be but check to be sure).

2. Create a folder in your /Home directory and copy the contents of the discs to it. If the disc structure is the same as the repos listed copy the contents of the discs to the folder you created.

3. Follow BobSongs tutorial and it will update your folder.

---

### Post by BobSongs on 2009-05-24
> **egalvan said:**
> <snip>I purchased a set of Ubuntu repo DVDs from osdisc.com (among others)

(Great service, by the way. Recommended.)</snip>
The tutorial includes two different online stores that provide Ubuntu repository DVDs.

I make no income from the sales.

If i did... I would only provide a link to the stores... and the whole tutorial would be ... erased.

Thoughts go thru my ... head....

Muahahahahaaa.

---

### Post by luvr on 2009-05-29
[SIZE="4"][COLOR="DarkRed"]**_The Goal._**[/COLOR][/SIZE]

I’m trying to set up a locally available Ubuntu mirror, from which I can install software on any computer that I manage, without having to download the software packages from the internet onto every computer on which I wish to install them. It is definitely ***not*** my intention to burn the downloaded files to DVD *(or whichever other appropriate medium).*

[SIZE="4"][COLOR="DarkRed"]**_Preparatory Steps._**[/COLOR][/SIZE]

As an initial test run, I decide to select only a small sample from the ***(huge!)*** Ubuntu repositories. I prefer not to perform the *“Big Download”* until I can get my small sample to work. I decide to settle on the *“restricted”* section of the Ubuntu Jaunty Jackalope release—which is some 59 MiB in size, and, therefore, perfectly manageable for my test run.

First, I create a directory in which I can download the repository files:
```
mkdir ~/UbuntuRepos
```

Next, I install the *“debmirror”* package:
```
sudo apt-get install debmirror
```

As **BobSongs** documented in the first post of this thread, I can now issue the following command to download my selected sample from an online Ubuntu mirror:
```
debmirror --nosource --md5sums --passive --host=*online-repository-host* --root=ubuntu \
  --method=http --progress --dist=jaunty --section=restricted --arch=i386 \
  --ignore-release-gpg \
  ~/UbuntuRepos
```

[INDENT]**_Notes:_**
[LIST][*]In the command above, you will have to replace the *“online-repository-host”* with your selected Ubuntu mirror—e.g., with the generic *“archive.ubuntu.com”* or with your national mirror (which, in my case, would be *“be.archive.ubuntu.com”*).
[*]I use *“--method=http”* instead of *ftp,* since the latter apparently won’t work on my national Ubuntu mirror.[/LIST][/INDENT]
With the necessary infrastructure in place, I can add my local mirror to my *“/etc/apt/sources.list”* file, to make it known to the APT system. I add the following line to the top of the file:
```
deb   file:///home/luvr/UbuntuRepos/   jaunty   restricted
```

[INDENT]**_Note:_**

[INDENT]You will need *root* privileges in order to edit the *“/etc/apt/sources.list”* file. For example, if you want to use the *“gedit”* text editor, you will have to run the following command:
```
sudo gedit /etc/apt/sources.list
```
Alternatively, you can start the editor from the GNOME desktop by pressing **<Alt>-<F2>** and running the following command line:
```
gksudo gedit /etc/apt/sources.list
```[/INDENT]

**_Important:_**

[INDENT]Make sure to add the line to the ***_top_ of the file***; if the system finds the same package in multiple places (e.g., once in your local repository, and once in a repository on the internet), it will load it from the **first** location in the *sources.list* file where it finds the package. In other words, if the internet repository is specified *before* the local repository in *sources.list,* then the internet repository will be preferred, and the local repository will not be used.[/INDENT][/INDENT]

Then, I refresh my local package indexes:
```
sudo apt-get update
```

[SIZE="4"][COLOR="DarkRed"]**_Experiment 1: Will APT Use my Local Mirror?_**[/COLOR][/SIZE]

To see if the APT system will actually **use** the packages that I downloaded, I run the following command:
```
sudo apt-get install fglrx-amdcccle
```

This command produces the following output:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot fglrx-kernel-source xorg-driver-fglrx
Suggested packages:
  libamdxvba1
The following NEW packages will be installed:
  dkms fakeroot fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.6MB of archives.
After this operation, 69.0MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

[INDENT]**_Note:_**

[INDENT]Since I don’t actually want to install any packages at this time, I reply ***“N”*** to the question if I want to continue.[/INDENT][/INDENT]

**_My observations:_**
[LIST][*]The output includes the message that *“24.6MB of archives”* will be downloaded from online repositories. In other words, my locally available repository is ignored.
This doesn’t really come as a surprise, since the local repository doesn’t have a digital signature—which was excluded from the download as a result of the *“--ignore-release-gpg”* option that I specified on the *“debmirror”* command. As a result, my local repository will not be *trusted*—i.e., the APT system will ignore it whenever it can, and prefer to download packages from an online, but **trusted** repository instead.
[*]Two packages that are not available in my local repository, will be installed as well: *“dkms”* and *“fakeroot.”* To ensure that they won’t interfere with my further experiments, I decide to install them separately, using the following command:
```
sudo apt-get install dkms fakeroot
```[/LIST]
[SIZE="4"][COLOR="DarkRed"]**_Experiment 2: Will *“debmirror”* Download the Digital Signature if I Ask it to?_**[/COLOR][/SIZE]

Since I want my local mirror to become trusted, I want to ensure that it includes a digital signature—i.e., its *“Release.gpg”* file. Therefore, for my next experiment, I will omit the *“--ignore-release-gpg”* option from the *“debmirror”* command line:
```
debmirror --nosource --md5sums --passive --host=*online-repository-host* --root=ubuntu \
  --method=http --progress --dist=jaunty --section=restricted --arch=i386 \
  ~/UbuntuRepos
```

This command produces the following output:
```
Mirroring to /home/luvr/UbuntuRepos from http://*online-repository-host*/ubuntu/
Arches: i386
Dists: jaunty
Sections: restricted
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/jaunty/Release... ok
[0%] Getting: dists/jaunty/Release.gpg... ok
gpgv: keyblock resource `/home/luvr/.gnupg/trustedkeys.gpg': general error
gpgv: Signature made Wed 22 Apr 2009 11:35:26 PM CEST using DSA key ID 437D05B5
[GNUPG:] ERRSIG 40976EAF437D05B5 17 2 00 1240436126 9
[GNUPG:] NO_PUBKEY 40976EAF437D05B5
gpgv: Can't check signature: public key not found
Release signature does not verify.
Errors:
 Release signature does not verify.
Failed to download some Release or Release.gpg files!
WARNING: releasing 1 pending lock...
```

Clearly, the *“debmirror”* command **does** now download the *“Release.gpg”* file, after which it invokes the *“gpgv”* utility (i.e., the *“OpenPGP signature verification tool”*) to verify the digital signature. The *“gpgv”* utility looks for the appropriate public key in a keyring file named *“trustedkeys.gpg,”* which it expects to find in my *“.gnupg”* directory. Since that keyring file does not exist, the program cannot verify the digital signature, and will return an error. When *“debmirror”* subsequently sees this error, it apparently deletes the *“Release.gpg”* file—which it assumes to be in error.

**_Note:_** 

[INDENT]I could, at this point, decide to download the *“Release.gpg”* file manually, using the following commands:
```
cd ~/UbuntuRepos/dists/jaunty
wget http://*online-repository-host*/ubuntu/dists/jaunty/Release.gpg
```
If I subsequently refresh my local indexes, and rerun the command to install one of the packages from my local mirror, then the system will tell me that it won’t need to download any packages. Indeed, if I execute the commands:
```
sudo apt-get update
sudo apt-get install fglrx-amdcccle
```
then the output includes the following line:
```
Need to get 0B/24.4MB of archives.

```
In other words, nothing will need to be downloaded from the online repositories, but the packages will be read from my local mirror instead.

I prefer an automatic solution, though—where *“debmirror”* will download the *“Release.gpg”* file for me, and be able to verify it.[/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Remedy: Getting *“debmirror”* to Download and Verify the Digital Signature._**[/COLOR][/SIZE]

As I mention above, the *“debmirror”* command attempts to verify the *“Release.gpg”* file against a public key that resides in the *“~/.gnupg/trustedkeys.gpg”* keyring file. The trick to getting *“debmirror”* to accept the digital signature, then, must be, to create this keyring file, and importing the appropriate public key into it.

Fortunately, the *“debmirror”* **man** page hints at a possible solution, in that it contains the following text snippet:
```
Debmirror uses gpgv to verify Release and Release.gpg using the
default keying ~/.gnupg/trustedkeys.gpg. *[...]*

To add the right key to this keyring you can import it from the
debian keyring (in case of the debian archive) using:

   gpg --keyring /usr/share/keyrings/debian-archive-keyring.gpg --export \
       | gpg --import
```

[INDENT]**_Note:_**

[INDENT]Incidentally, this command needs a little tweaking to make it work right—but more on that in a moment.[/INDENT][/INDENT]

So, apparently, the *“/usr/share/keyrings”* directory is the place where the appropriate keyring should be found. Thus, I run the following command to list the files that are located there:
```
ls -l /usr/share/keyrings
```

This produces the following output:
```
total 16
-rw-r--r-- 1 root root 2198 2008-04-20 13:05 medibuntu-keyring.gpg
-rw-r--r-- 1 root root 6713 2008-03-04 05:20 ubuntu-archive-keyring.gpg
-rw------- 1 root root    0 2009-04-20 16:00 ubuntu-archive-removed-keys.gpg
-rw-r--r-- 1 root root 1227 2008-03-04 05:20 ubuntu-master-keyring.gpg
```

To find out which keys are available in, e.g., the *“ubuntu-archive-keyring.gpg”* file, I run the following command:
```
gpg --no-default-keyring --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg --list-keys
```

This command produces the following output:
```
/usr/share/keyrings/ubuntu-archive-keyring.gpg
----------------------------------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>
```

Returning to the error messages that *“debmirror”* produced when I wanted it to include the *“Release.gpg”* file in its download, I notice the *key ID* that it was looking for:
```
gpgv: keyblock resource `/home/luvr/.gnupg/trustedkeys.gpg': general error
gpgv: Signature made Wed 22 Apr 2009 11:35:26 PM CEST using DSA key ID **_[COLOR="DarkRed"]437D05B5[/COLOR]_**
[GNUPG:] ERRSIG 40976EAF437D05B5 17 2 00 1240436126 9
[GNUPG:] NO_PUBKEY 40976EAF437D05B5
gpgv: Can't check signature: public key not found
```

The required key is available in the *“ubuntu-archive-keyring.gpg”* file (it’s the one with *user id* *“Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>”*). Therefore, this is the keyring from which I will build my *“~/.gnupg/trustedkeys.gpg”* keyring file.

Thus, I run the following *(tweaked—see above)* command to create the keyring:
```
gpg --no-default-keyring --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg --export \
    | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```

[INDENT]**_Note:_** 

[INDENT]You can run the following command if you want to verify that the expected keys were loaded into the new keyring file:
```
gpg --no-default-keyring --keyring ~/.gnupg/trustedkeys.gpg --list-keys
```
You should see the same keys listed as for the *“/usr/share/keyrings/ubuntu-archive-keyring.gpg”* file.[/INDENT][/INDENT]

When I rerun the *“debmirror”* command to bring my local mirror up-to-date (including the *“Release.gpg”* file), the digital signature can now be correctly verified:
[LIST]
[*]**Command:**
```
debmirror --nosource --md5sums --passive --host=*online-repository-host* --root=ubuntu \
  --method=http --progress --dist=jaunty --section=restricted --arch=i386 \
  ~/UbuntuRepos
```
[*]**Output from the command:**
```
Mirroring to /home/luvr/UbuntuRepos from http://*online-repository-host*/ubuntu/
Arches: i386
Dists: jaunty
Sections: restricted
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/jaunty/Release... ok
[0%] Getting: dists/jaunty/Release.gpg... ok
Get Packages and Sources files and other miscellany.
[ 53%] Getting: dists/jaunty/restricted/binary-i386/Packages.bz2... ok
Parse Packages and Sources files and add to the file list everything therein.
Download all files that we need to get (1 MiB).
Downloaded 1 MiB in 31s at 2.63 kiB/s
Everything OK. Moving meta files.
Cleanup mirror.
All done.
```[/LIST]
[SIZE="4"][COLOR="DarkRed"]**_Experiment 3: Will APT Use my Local Mirror Now?_**[/COLOR][/SIZE]

Now that I believe that my local mirror is properly **trusted,** I refresh my local indexes again, and I retry the command to install the *“fglrx-amdcccle”* package:
```
sudo apt-get update
sudo apt-get install fglrx-amdcccle
```

This time, the software installation command produces the following output:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  fglrx-kernel-source xorg-driver-fglrx
Suggested packages:
  libamdxvba1
The following NEW packages will be installed:
  fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/24.4MB of archives.
After this operation, 68.2MB of additional disk space will be used.
Do you want to continue [Y/n]?
```
I observe that the packages will not be downloaded from the online repositories, but that they will be taken from my local mirror instead. In other words, I now have a **trusted** local Ubuntu mirror, from which I can install software packages.

[SIZE="4"][COLOR="DarkRed"]**_Wrapping Up._**[/COLOR][/SIZE] 

If you want to create a **trusted** local Ubuntu mirror, from which you can install software packages, then you will need to take the following steps:
[LIST=1]
[*]Create a directory in which you can download the repository files—e.g.:
```
mkdir ~/UbuntuRepos
```
[*]Install the *“debmirror”* package:
```
sudo apt-get install debmirror
```
[*]Create the *“~/.gnupg/trustedkeys.gpg”* keyring, to allow *“debmirror”* to verify the digital signature of the Ubuntu repository:
```
gpg --no-default-keyring --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg --export \
    | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```
[*]Run the *“debmirror”* command to download the repository:
```
debmirror --nosource --md5sums --passive --host=*online-repository-host* --root=ubuntu \
  --method=http --progress --dist=*distribution* --section=*section-list* --arch=*arch-list* \
  ~/UbuntuRepos
```
[INDENT]**_Note:_**

[INDENT]Omit the *“--nosource”* option if you want to download not only the binary packages, but the sources as well.[/INDENT][/INDENT]
[*]Add the following line to the top of the *“/etc/apt/sources.list”* file:
```
deb   file:///home/*username*/UbuntuRepos/   *distribution*   *section-list*
```
[*]Refresh your local indexes:
```
sudo apt-get update
```[/LIST]

Now you can install software packages from your locally available mirror.

Whenever you want to bring your local mirror up-to-date, simply rerun the *“debmirror”* command, and refresh your local indexes again.

[SIZE="4"][COLOR="DarkRed"]**_ADDENDUM: How Do I Set Up a Local *“Medibuntu”* Mirror?_**[/COLOR][/SIZE]

**_Important:_**

[INDENT]Before we go any further, let’s return to a critically important question that **BobSongs** answered in his original post:
> **Q:**
What if I wanted to combine or add in more repositories?
Something like Canonical Commercial? Or MediBuntu?

[B]A:
Don't do it![/B]
*[...]*
The quick way to add files from different servers (such as MediBuntu and Canonical) is to put the additional files in unique folders.
Examples: **~/MediBuntuRepos** and/or **~/CanonicalRepos** (your folder names may vary).
Thus, you will need to create a new directory—e.g., *“~/MediBuntuRepos”*—for your local Medibuntu mirror; do **not** try to add the Medibuntu software packages to your existing *“~/UbuntuRepos”* directory.
I repeat:
[INDENT]**Do _*not*_ try to add the Medibuntu software packages to your existing *“~/UbuntuRepos”* directory!**[/INDENT]
Please reread this statement until you can resist the temptation to try it anyway, or you will destroy your existing Multi-Gigabyte mirror![/INDENT]

**_Note:_**

[INDENT]I assume that you have already added the Medibuntu repository as a software source to your system. If you haven’t, then here’s a quick way to do it now:
[LIST=1][*]Add the following line to your *“/etc/apt/sources.list”* file:
```
deb   http://packages.medibuntu.org/   jaunty   free non-free
```
[*]Run the following command to refresh your local package indexes:
```
sudo apt-get update
```
An error message will be displayed, because the public key for the Medibuntu repository is not available.
[*]Run the following command to install the public key for the Medibuntu repository:
```
sudo apt-get --allow-unauthenticated install medibuntu-keyring
```
[*]Rerun the command to refresh your local package indexes:
```
sudo apt-get update
```
The error message will no longer appear.[/LIST][/INDENT]

The public key for the Medibuntu repository should be present in your *“/usr/share/keyrings”* directory:
```
$ **ls -l /usr/share/keyrings/medibuntu-keyring.gpg**
-rw-r--r-- 1 root root 2198 2008-04-20 13:05 /usr/share/keyrings/medibuntu-keyring.gpg
```

If you attempt to list the public keys available in this file, however, then an error message will appear:
```
$ **gpg --no-default-keyring --keyring /usr/share/keyrings/medibuntu-keyring.gpg --list-keys**
gpg: [don't know]: invalid packet (ctb=2d)
gpg: keydb_search_first failed: invalid packet
```

In fact, the name of the file—*“medibuntu-keyring.gpg”*—is a bit of a misnomer, since the file isn’t really a keyring.
You can use the *“file”* command to try and identify the type of any file—e.g.:
```
$ **file /usr/share/keyrings/ubuntu-archive-keyring.gpg**
/usr/share/keyrings/ubuntu-archive-keyring.gpg: GPG key public ring
$ **file /usr/share/keyrings/medibuntu-keyring.gpg**
/usr/share/keyrings/medibuntu-keyring.gpg: PGP public key block
```
Apparently, the *“medibuntu-keyring.gpg”* file is a *“PGP public key _block_”*—as opposed to *“ubuntu-archive-keyring.gpg,”* which is a *“GPG key public _ring_.”*
[INDENT]**_Note:_**

[INDENT]The *“medibuntu-keyring.gpg”* file is actually a plain text file (though its contents won’t make much sense).
You can open it with any text editor, or view its contents with the *“cat”* command, or with the *“more”* or *“less”* pagers—e.g.:
```
cat /usr/share/keyrings/medibuntu-keyring.gpg
```[/INDENT][/INDENT]

Since the *“medibuntu-keyring.gpg”* file is a public key *block* (instead of a *ring*), you can use the following command to import it into the *“~/.gnupg/trustedkeys.gpg”* keyring file (where *“debmirror”* expects to find it):
```
gpg --no-default-keyring --keyring trustedkeys.gpg \
    --import < /usr/share/keyrings/medibuntu-keyring.gpg
```

[INDENT]**_Note:_**

[INDENT]Importing additional keys into an existing keyring file won’t remove any of the *existing* keys in the keyring; the new keys will simply be *added* to it.[/INDENT][/INDENT]

You can subsequently download the Medibuntu software packages into your new local mirror as follows:
```
debmirror --nosource --md5sums --passive --host=packages.medibuntu.org --root=/ \
  --method=http --progress --dist=jaunty --section=free,non-free --arch=i386 \
  ~/MediBuntuRepos
```

[INDENT]**_Note:_**

[INDENT]It is well worth repeating **again** (*and again, and again,* ...) that you should be **extra careful** to specify the correct directory—e.g., *“~/MediBuntuRepos”*—for your local Medibuntu mirror, or you risk damaging your existing repository mirror![/INDENT][/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_ADDENDUM: What if *“debmirror”* complains because it cannot find the *“Packages.bz2”* file?_**[/COLOR][/SIZE]

See my post entitled [*“ERROR: "debmirror" fails if the online repository does not have a "Packages.bz2" file”*]("http://ubuntuforums.org/showthread.php?p=7536257#post7536257") (later in this thread).

[SIZE="4"][COLOR="DarkRed"]**_ADDENDUM: Why does *“debmirror”* complain about *“duplicate dists”* on the *“Canonical”* repository?_**[/COLOR][/SIZE]

See my post entitled [*“ERROR: "debmirror" cannot download the "Canonical" repository”*]("http://ubuntuforums.org/showthread.php?p=10103252#post10103252") (later in this thread).

[SIZE="4"][COLOR="DarkRed"]**_ADDENDUM: How can I install the Flash Player Plugin from my local mirror, without internet access?_**[/COLOR][/SIZE]

See my post entitled [*“Installing the Flash Player Plugin from a Local Mirror, without Internet Access.”*]("http://ubuntuforums.org/showthread.php?p=9884724#post9884724") (later in this thread).

[SIZE="4"][COLOR="DarkRed"]**_ADDENDUM: How do I set up a Local Mirror with Source Packages only?_**[/COLOR][/SIZE]

See my post entitled [*“How to Create a "Source-Only" Local Mirror.”*]("http://ubuntuforums.org/showthread.php?p=7547157#post7547157") (later in this thread).

[SIZE="4"][COLOR="DarkRed"]**_ADDENDUM: Can I perform a partial download, and control exactly which files will get downloaded?_**[/COLOR][/SIZE]

If you want to limit a *“debmirror”* run, then you can specify the *“--max-batch=number”* parameter, where *“number”* represents the maximum number of files that you wish to download. You **cannot,** however, instruct *“debmirror”* exactly *which* files you want to download, or specify a size limit for the download.

To obtain much more fine-grained control over the files that get selected for download, you will have to learn about some further utilities—as I describe in my post entitled [*“Having Fun with the "debmirror" Dry Run—and Learning Something New Along the Way.”*]("http://ubuntuforums.org/showthread.php?p=8790004#post8790004") (later in this thread).

[SIZE="4"][COLOR="DarkRed"]**_CAUTION: Changing your *“--host”* Parameter May Confuse *“debmirror”*!_**[/COLOR][/SIZE]

**_The Issue._**

[INDENT]When I set up my local mirror, I initially downloaded from my national mirror, *“be.archive.ubuntu.com”*; in other words, I specified my *“--host”* parameter as follows:
```
--host=be.archive.ubuntu.com
```
I started with a small sample that consisted only of the *“restricted”* section—i.e., with the following *“--section”* parameter value:
```
--section=restricted
```
Once that worked, I added in the *“main”* section:
```
--section=main,restricted
```
Unfortunately, my national mirror had rather inconsistent data transfer rates, and caused far too many timeouts, and consequently, the download took much longer than I found acceptable. Therefore, when I got ready to add the *“universe”* section (which is even bigger than *“main”*!), I decided to switch to the generic mirror, *“archive.ubuntu.com,”* to see if that would work any better. My *“--host”* and *“--section”* parameter values, then, looked like this:
```
--host=archive.ubuntu.com --section=main,restricted,universe
```
When I fired up *“debmirror”* again, everything seemed to go fine, so I left the computer alone to complete the download.

Sometime later, when I returned to the computer, I noticed that it had finished the download, but to my horror, it displayed a whole sequence of lines saying that it had **deleted packages from the *“main”* section!** When I wanted to check what had happened to the *“main”* section, … it had apparently vanished—***“debmirror”* had effectively _eradicated_ it!**

I retried the *“debmirror”* command, but that didn’t help any; I did see the following messages, which indicated that the *“Packages”* files for the *“main”* section were being downloaded alright:
```
Getting: dists/jaunty-backports/main/binary-i386/Packages.bz2... ok
Getting: dists/jaunty-proposed/main/binary-i386/Packages.bz2... ok
Getting: dists/jaunty-security/main/binary-i386/Packages.bz2... ok
Getting: dists/jaunty-updates/main/binary-i386/Packages.bz2... ok
Getting: dists/jaunty/main/binary-i386/Packages.bz2... ok
```
Even so, *“debmirror”* refused to download any of the packages from the *“main”* section, but chose to ignore them instead. My local mirror appeared to be badly damaged.

It won’t come as a surprise that I hadn’t made a backup yet—in keeping with the established traditions, I make backups only after the facts... ](*,)
I dreaded the idea of having to start all over again, though—especially since I still had a perfectly good copy of the *“universe”* section; having to redownload just the *“main”* section was bad enough already! :icon_frown:[/INDENT]

**_The Work-Around._**

[INDENT]In addition to the *“dists,”* the *“pool,”* and the *“project”* directories, the *“debmirror”* command will create a fourth, hidden directory in the location that you selected for your local mirror:
```
**$ ls -lA ~/UbuntuRepos**
drwxr-xr-x 7 luvr luvr 4096 2009-06-02 17:35 dists
drwxr-xr-x 6 luvr luvr 4096 2009-06-02 01:04 pool
drwxr-xr-x 3 luvr luvr 4096 2009-06-02 11:38 project
drwxr-xr-x 3 luvr luvr 4096 2009-06-02 11:30 .temp
```
Apparently, *“debmirror”* will download the *“Release”* and *“Packages”* files (plus the *“Sources”* files, if you omit the *“--nosource”* command-line option) there first, to ensure that the copies in their final locations won’t get overwritten until the repository download completes successfully.

You can safely delete this *“.temp”* directory before you run *“debmirror”* again—if the directory doesn’t exist, then *“debmirror”* will simply recreate it. In fact, deleting the *“.temp”* directory was all that it took to repair my local mirror—though, of course, I still had to redownload the complete *“main”* section.[/INDENT]

**_Conclusion._**

[INDENT]If your local mirror appears to malfunction, then it may be a good idea to delete its *“.temp”* directory:
```
cd  ~/UbuntuRepos
rm -R .temp
```
[INDENT]**_Note:_**

[INDENT]If you want to use the graphical desktop environment to delete the—hidden—*“.temp”* directory, then you will have to turn on the *“Show Hidden Files”* option from the Nautilus file browser *“View”* menu.[/INDENT][/INDENT]
If you subsequently retry the *“debmirror”* command, then it should work normally again.

Actually, deleting the *“.temp”* directory is a pretty harmless operation. Whenever you take any action that you suspect may affect the proper operation of the *“debmirror”* command, you may want to delete the *“.temp”* directory as a preventative measure.[/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_References._**[/COLOR][/SIZE] 
[LIST]
[*][Debmirror of ubuntu archive, with valid gpg keys]("http://ilostmynotes.blogspot.com/2008/05/debmirror-of-ubuntu-archive-validating.html")—This actually is the page that helped me tweak the *“gpg”* command to create the keyring that *“debmirror”* needs.
[*][Lockergnome Linux Bug #517179: debmirror: problems since Lenny release]("http://help.lockergnome.com/linux/Bug-517179-debmirror-problems-Lenny-release--ftopict493224.html")—This is the page that taught me about the *“.temp”* directory.[/LIST]

---

### Post by RageAgainstThis on 2009-05-31
I need a little help allowing my laptop to access my local repository via samba.  When I use the wiki advised method "deb smb:///pathtolocalrepository "  i get the following error "The method driver /usr/lib/apt/methods/smb could not be found."   

I have also tried mounting the samba share in an attempt to use the "deb file:///" method.  When I mount the samba share onto the laptop the address in properties points to "/branden_desktop/jaunty_repos/".  Could I somehow mount this location and use apt to see it as a local filesystem? "deb file:///branden_desktop/jaunty_repos /"?  I have tried to mount as is, but did not work.

---

### Post by luvr on 2009-06-01
> **RageAgainstThis said:**
> "The method driver /usr/lib/apt/methods/smb could not be found."
There's an unresolved question about this in launchpad: [Ubuntu question #33505: “Using SMB share in apt sources.list causes error.”]("https://answers.launchpad.net/ubuntu/+question/33505") I believe that there once was a proposal to add SMB to the list of protocols supported by APT, but I'm not sure if this was ever actually done.

> I have also tried mounting the samba share in an attempt to use the "deb file:///" method.
Could you tell us exactly what you did to mount the sambe share? Which command did you use, or which actions did you take from the desktop?

Does your SAMBA share show up in the list of mounted file systems? For example, if you type the following command:
```
mount
```
does the output include a line that refers to your SAMBA share? If so, what's the exact contents of that line?

Can you access the share, and its contents, from the command line or from the desktop? Can you open any of its files?

---

### Post by BobSongs on 2009-06-01
@luvr

Awesome addition! Well documented, AND well formatted! A man after my heart.

I won't copy/paste the post into the tutorial (it's embarrassingly long as it is...), but I will link to it.

You guys are a hoot! :)

---

### Post by RageAgainstThis on 2009-06-01
I actually got the file system mounted correctly using "sudo mount -t smbfs.../desktop/repo"  Though I had to copy the smbfs files over from my local repository for this setup.  I was able to update apt and begin install and download from my local repository using this method.  However, I did encounter an error with the openoffice installation that rendered my OS unusable.  I will get back with you guys on what was going on there after a clean install.

Thanks

---

### Post by amirtha on 2009-06-02
sorry i have no idea thanks

---

### Post by luvr on 2009-06-02
> **BobSongs said:**
> @luvr

Awesome addition! Well documented, AND well formatted! A man after my heart.

I won't copy/paste the post into the tutorial (it's embarrassingly long as it is...), but I will link to it.

You guys are a hoot! :)
Well, thanks! My pleasure; this is the kind cooperation that I'm so fond of: One person works out a solution to a problem, and that's the inspiration that another person needs to start looking for a solution to *his* problem, etc. And in the end, everyone benefits.

That's the wonderful concept of *"Standing on the shoulders of giants standing on the shoulders of giants standing on the shoulders of giants standing..."*

---

### Post by luvr on 2009-06-14
[SIZE="4"][COLOR="DarkRed"]**_The Goal._**[/COLOR][/SIZE]

If you want to set up a local Ubuntu mirror, you can download its contents from an online repository&#8212;as I documented in [an earlier post in this thread.]("http://ubuntuforums.org/showthread.php?p=7367273#post7367273") You will then, however, have to download a huge amount of data&#8212;which may be impractical to you.

To bypass the *&#8220;Big Download,&#8221;* you may prefer to obtain a set of Ubuntu Repository DVDs, and use these to initialise your local mirror instead. Once your local mirror is up and running, you can then keep it up-to-date by periodically rerunning the *&#8220;debmirror&#8221;* command.

[SIZE="4"][COLOR="DarkRed"]**_Purchasing Ubuntu Repository DVDs._**[/COLOR][/SIZE]

In [the initial post of this thread,]("http://ubuntuforums.org/showthread.php?t=352460") **BobSongs** listed some of the vendors from which you can purchase a set of Ubuntu Repository DVDs.

To order your copy, first decide which Ubuntu release you want&#8212;e.g., ***Ubuntu 9.04*** (the *&#8220;Jaunty Jackalope&#8221;*). The vendor may append a second set of numbers to the release, to identify when the DVD contents were brought up-to-date&#8212;e.g., ***&#8220;Ubuntu 9.04-9.06&#8221;*** identifies the Ubuntu 9.04 release, brought up-to-date as of June, 2009.

Also, decide for which CPU *architecture* you want to obtain the repository DVDs: ***i386*** (i.e., the 32-bit version), or ***amd64*** (i.e., the 64-bit version)&#8212;or, perhaps, both.

[INDENT]**_Note:_**

[INDENT]Before you order your set of discs, ensure that your computer meets the system requirements specified by the vendor&#8212;you may, for example, need a DVD drive that can read *Dual Layer DVD±R* media.[/INDENT][/INDENT]

Once you have placed your order, you will simply have to wait until the discs are delivered. *(In my case, the vendor announced that it would take some 10 working days for my order to arrive, but I actually received it after only five or six working days... Nice!)*

[SIZE="4"][COLOR="DarkRed"]**_Loading your Local Mirror from the DVDs._**[/COLOR][/SIZE]

Once you receive the set of discs, you can set up your local mirror, and load it from the discs. First, you will need to create a directory for your mirror&#8212;e.g., *&#8220;~/UbuntuRepos&#8221;*:
```
mkdir ~/UbuntuRepos
```

Next, insert the first DVD into your drive, and wait until your system mounts it (and, most likely, opens a file browser window for it). The DVD should contain two directories (or * &#8220;folders,&#8221;* in GUI-Speak):
[LIST][*]*&#8220;dists&#8221;*&#8212;which can help you identify the values that you will have to specify for the *&#8220;--dist&#8221;* and *&#8220;--section&#8221;* parameters on the *&#8220;debmirror&#8221;* command, later on;
[*]*&#8220;pool&#8221;*&#8212;which contains the actual software packages that you will have to copy into your local mirror.[/LIST]
To list the contents of the *&#8220;dists&#8221;* directory, you can execute the following command:
```
ls /media/cdrom/dists
```
[INDENT]**_Note:_**

[INDENT]If your computer has more than one CD and/or DVD drive (or if the system doesn&#8217;t make the *&#8220;cdrom&#8221;* synonym available for some reason), then you may have to replace the *&#8220;cdrom&#8221;* device designation with some other name; you can identify the appropriate device name on the title bar of the file browser window that displays the DVD contents.
Alternatively, you can, of course, open the *&#8220;dists&#8221;* folder from the graphical desktop environment.[/INDENT][/INDENT]

As an example, the *&#8220;dists&#8221;* directory may contain the following four subdirectories:
[LIST][*]jaunty
[*]jaunty-backports
[*]jaunty-security
[*]jaunty-updates[/LIST]
These are the values that you will have to use for the *&#8220;--dist&#8221;* parameter when you run the *&#8220;debmirror&#8221;* command&#8212;so, e.g.:
```
--dist=jaunty,jaunty-backports,jaunty-security,jaunty-updates
```
Each of these subdirectories will contain another set of subdirectories&#8212;e.g.:
[LIST][*]main
[*]multiverse
[*]restricted
[*]universe[/LIST]
From this list, you can construct the *&#8220;--section&#8221;* parameter for the *&#8220;debmirror&#8221;* command&#8212;e.g.:
```
--section=main,multiverse,restricted,universe
```

Finally, in each of these subdirectories, you will find yet another subdirectory, which identifies the CPU architecture to which the disc set applies&#8212;either, *&#8220;binary-i386&#8221;* or *&#8220;binary-amd64,&#8221;* for the 32-bit or the 64-bit architecture, respectively. This directory corresponds to the *&#8220;--arch&#8221;* parameter for the *&#8220;debmirror&#8221;* command:
```
--arch=i386
```
or:
```
--arch=amd64
```
or even (if you load the disc sets for *both* architectures into your local mirror):
```
--arch=i386,amd64
```

[INDENT]**_Note:_**

[INDENT]You will not, at this point, have to actually *use* these parameter values. Just note them down, so you have them available when you need them, later on.[/INDENT][/INDENT]

Now, run the following command to copy the contents of the *&#8220;pool&#8221;* directory into your local mirror:
```
cp --recursive --verbose /media/cdrom/pool ~/UbuntuRepos
```
Afterwards, you will have to update the *permission* flags on the directories and files that you copied to your harddisk; otherwise, they will remain *read-only,* and you will not be able to further update your local mirror (e.g., to copy the contents of the remaining discs into it). Just run the following command:
```
chmod --recursive --verbose u+w ~/UbuntuRepos/pool
```

Next, insert each of the remaining DVDs in turn, and repeat the copy and *&#8220;chmod&#8221;* commands for each of them:
```
cp --recursive --verbose /media/cdrom/pool ~/UbuntuRepos
chmod --recursive --verbose u+w ~/UbuntuRepos/pool
```

[INDENT]**_Note:_**

[INDENT]You may want to verify if the *&#8220;dists&#8221;* directory on each of the DVDs contains any subdirectories that aren&#8217;t present on any earlier disc. If there are any, then you should add them to the *&#8220;--dist&#8221;* parameter for the *&#8220;debmirror&#8221;* command, as discussed above.
Theoretically, you could even encounter new subdirectories that should be added to the *&#8220;--section&#8221;* parameter for the *&#8220;debmirror&#8221;* command&#8212;though, in practice, I believe that won&#8217;t be very likely to happen.[/INDENT][/INDENT]

**_Adding Packages for a Second CPU Architecture to your Local Mirror._**

[INDENT]After you copy all packages for one CPU architecture (e.g., *&#8220;i386&#8221;*) to your local mirror, you may want to add the packages for the other architecture (e.g., *&#8220;amd64&#8221;*) to it as well. To this end, you can just repeat the copy and *&#8220;chmod&#8221;* commands for each of the DVDs for the second architecture. Some packages are common to both architectures, however; you may, therefore, want to avoid recopying these common packages, to help speed up this operation a little. In other words, you may want to add the *&#8220;--update&#8221;* option to the copy command, to ensure that only new *(or newer versions of existing)* files will be copied over:
```
cp --recursive **--update** --verbose /media/cdrom/pool ~/UbuntuRepos
chmod --recursive --verbose u+w ~/UbuntuRepos/pool
```[/INDENT]

**_Note:_**

[INDENT]Some DVD drives may become somewhat unstable, and report read errors when they are heavily used for relatively long periods of time. If you experience DVD read errors on, e.g., the third or fourth DVD that you are trying to copy in a single session, you may want to power down your computer for a few hours, and then retry. Only if you then keep getting DVD read errors should you assume that there is a problem with the disc.

Also, DVD read errors are almost ***guaranteed*** to occur if you perform these steps on a battery-powered laptop when the battery is running low.[/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Creating the Keyring for your Local Mirror._**[/COLOR][/SIZE]

As I explained in [my earlier post,]("http://ubuntuforums.org/showthread.php?p=7367273#post7367273") you will have to create a particular keyring, to allow *&#8220;debmirror&#8221;* to validate the integrity of your local mirror. Just run the following command *(if you haven&#8217;t already done so on an earlier occasion)*:
```
gpg --no-default-keyring --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg --export \
    | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```

[SIZE="4"][COLOR="DarkRed"]**_OPTIONAL: Taking *&#8220;debmirror&#8221;* for a Test Drive._**[/COLOR][/SIZE]

You are now ready to run *&#8220;debmirror&#8221;* for the first time, to load the control files that will allow you to install software packages from your local mirror. In addition, *&#8220;debmirror&#8221;* will download any updates that may have become available since the DVDs were produced, and it will delete any obsoleted packages.

Since *&#8220;debmirror&#8221;* rather aggressively deletes from your local mirror **any** files that are not present in the online mirror with which it synchronises, large portions of your local mirror may get zapped if you make an error in any of its arguments. Therefore, you may prefer to take it for a test drive before you actually let it manipulate your local mirror. To request such a test drive, you can use the *&#8220;--dry-run&#8221;* parameter on the *&#8220;debmirror&#8221;* command, as follows:
```
debmirror **--dry-run** --nosource --md5sums --passive \
   --host=*online-repository-host* --root=ubuntu --method=http --progress \
   --dist=*dist-list* --section=*section-list* --arch=*arch-list* \
   ~/UbuntuRepos
```
where:
[LIST][*]*&#8220;online-repository-host&#8221;* represents the online mirror with which you want to synchronise your local mirror&#8212;e.g., the generic *&#8220;archive.ubuntu.com&#8221;* or your national mirror (which, in my case, would be *&#8220;be.archive.ubuntu.com&#8221;*).
[*]*&#8220;dist-list&#8221;* represents the *&#8220;--dist&#8221;* value, as discussed above&#8212;e.g.:
```
jaunty,jaunty-backports,jaunty-security,jaunty-updates
```
[*]*&#8220;section-list&#8221;* represents the *&#8220;--section&#8221;* value, also discussed above&#8212;e.g.:
```
main,multiverse,restricted,universe
```
[*]*&#8220;arch-list&#8221;* represents the CPU architecture(s) to which your local mirror applies&#8212;e.g., *&#8220;i386&#8221;* or *&#8220;amd64&#8221;* (or both: *&#8220;i386,amd64&#8221;*).[/LIST]
The actual *&#8220;debmirror&#8221;* command, with all values substituted into it, may, thus, look like this:
```
debmirror --dry-run --nosource --md5sums --passive \
   --host=archive.ubuntu.com --root=ubuntu --method=http --progress \
   --dist=jaunty,jaunty-backports,jaunty-security,jaunty-updates \
   --section=main,multiverse,restricted,universe --arch=i386,amd64 \
   ~/UbuntuRepos
```
As part of its output, the *&#8220;debmirror&#8221;* command will list the updated packages that have become available, and that would be loaded into your local mirror if this were a real run&#8212;e.g.:
```
Getting: pool/main/f/firefox-3.0/abrowser-3.0-branding_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_amd64.deb... ok
Getting: pool/main/f/firefox-3.0/abrowser-3.0-branding_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb... ok
Getting: pool/main/f/firefox-3.0/abrowser_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_amd64.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-3.0-dev_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_amd64.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-3.0-dev_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_amd64.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_amd64.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-dev_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-gnome-support_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-granparadiso-dev_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb... ok
Getting: pool/main/f/firefox-3.0/firefox-trunk-dev_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb... ok
Getting: pool/main/f/firefox-3.0/firefox_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb... ok
```
Furthermore, it will list the files that it considers obsoleted, and that it would delete&#8212;e.g.:
```
deleting pool/main/f/firefox-3.0/firefox_3.0.10+nobinonly-0ubuntu0.9.04.1_all.deb
deleting pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.10+nobinonly-0ubuntu0.9.04.1_i386.deb
deleting pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.10+nobinonly-0ubuntu0.9.04.1_i386.deb
deleting pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.10+nobinonly-0ubuntu0.9.04.1_amd64.deb
deleting pool/main/f/firefox-3.0/firefox-gnome-support_3.0.10+nobinonly-0ubuntu0.9.04.1_all.deb
deleting pool/main/f/firefox-3.0/firefox-trunk-dev_3.0.10+nobinonly-0ubuntu0.9.04.1_all.deb
deleting pool/main/f/firefox-3.0/firefox-3.0_3.0.10+nobinonly-0ubuntu0.9.04.1_amd64.deb
deleting pool/main/f/firefox-3.0/firefox-3.0-dev_3.0.10+nobinonly-0ubuntu0.9.04.1_amd64.deb
deleting pool/main/f/firefox-3.0/abrowser_3.0.10+nobinonly-0ubuntu0.9.04.1_all.deb
deleting pool/main/f/firefox-3.0/abrowser-3.0-branding_3.0.10+nobinonly-0ubuntu0.9.04.1_i386.deb
deleting pool/main/f/firefox-3.0/firefox-3.0_3.0.10+nobinonly-0ubuntu0.9.04.1_i386.deb
deleting pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.10+nobinonly-0ubuntu0.9.04.1_amd64.deb
deleting pool/main/f/firefox-3.0/firefox-dev_3.0.10+nobinonly-0ubuntu0.9.04.1_all.deb
deleting pool/main/f/firefox-3.0/abrowser-3.0-branding_3.0.10+nobinonly-0ubuntu0.9.04.1_amd64.deb
deleting pool/main/f/firefox-3.0/firefox-granparadiso-dev_3.0.10+nobinonly-0ubuntu0.9.04.1_all.deb
deleting pool/main/f/firefox-3.0/firefox-3.0-dev_3.0.10+nobinonly-0ubuntu0.9.04.1_i386.deb
```
If, at this point, you find that *&#8220;debmirror&#8221;* wants to remove whole subdirectories from your local mirror, then you should review the parameter values that you supplied, and correct them as required.

You can repeat the *&#8220;debmirror&#8221;* test run as often as you want, until you are satisfied with the results.

[SIZE="4"][COLOR="DarkRed"]**_Running *&#8220;debmirror&#8221;* for Real._**[/COLOR][/SIZE]

When you&#8217;re ready to let *&#8220;debmirror&#8221;* actually bring your local mirror up-to-date, just run the command **without** the *&#8220;--dry-run&#8221;* option, leaving all other parameters unchanged:
```
debmirror --nosource --md5sums --passive \
   --host=*online-repository-host* --root=ubuntu --method=http --progress \
   --dist=*dist-list* --section=*section-list* --arch=*arch-list* \
   ~/UbuntuRepos
```
The following is an example of an actual *&#8220;debmirror&#8221;* command, with all values substituted into it:
```
debmirror --nosource --md5sums --passive \
   --host=archive.ubuntu.com --root=ubuntu --method=http --progress \
   --dist=jaunty,jaunty-backports,jaunty-security,jaunty-updates \
   --section=main,multiverse,restricted,universe --arch=i386,amd64 \
   ~/UbuntuRepos
```
The output from the *&#8220;debmirror&#8221;* command will be mostly identical to that of the test run; this time, however, it will reallly *perform* the operations that it lists. As a result, your local mirror will have been properly set up and brought up-to-date once the command completes.

[SIZE="4"][COLOR="DarkRed"]**_Updating your APT Sources._**[/COLOR][/SIZE]

With the necessary infrastructure in place, it is now time to add your local mirror to your *&#8220;/etc/apt/sources.list&#8221;* file, to make it known to the APT system. For each of the values that you listed in the *&#8220;--dist&#8221;* parameter on the *&#8220;debmirror&#8221;* command, add a line of the following form to the **top** of the file:
```
deb   file:///home/*username*/UbuntuRepos/   *distname*   *section-list*
```
As an example, if your username is *&#8220;luvr,&#8221;* and with the *&#8220;--dist&#8221;* and *&#8220;--section&#8221;* parameter values as above, these lines will look as follows:
```
deb   file:///home/**luvr**/UbuntuRepos/   **jaunty**             **main,multiverse,restricted,universe**
deb   file:///home/**luvr**/UbuntuRepos/   **jaunty-backports**   **main,multiverse,restricted,universe**
deb   file:///home/**luvr**/UbuntuRepos/   **jaunty-security**    **main,multiverse,restricted,universe**
deb   file:///home/**luvr**/UbuntuRepos/   **jaunty-updates**     **main,multiverse,restricted,universe**
```
[INDENT]**_Note:_**

[INDENT]Depending on your needs and preferences, you may want to leave out the *&#8220;jaunty-backports&#8221;* line. *Backports* are updates that were actually developed for later Ubuntu releases, and that were subsequently made available for the current version, albeit without any form of support.[/INDENT]

**_Note:_**
[INDENT]Remember that you will need *root* privileges in order to edit the *&#8220;/etc/apt/sources.list&#8221;* file. For example, if you want to use the *&#8220;gedit&#8221;* text editor, you will have to run the following command:
```
sudo gedit /etc/apt/sources.list
```
Alternatively, you can start the editor from the GNOME desktop by pressing **<Alt>-<F2>** and running the following command line:
```
gksudo gedit /etc/apt/sources.list
```[/INDENT][/INDENT]

Next, update your local package indexes:
```
sudo apt-get update
```

[SIZE="4"][COLOR="DarkRed"]**_Keeping your Local Mirror Up-To-Date._**[/COLOR][/SIZE]

To keep your local mirror up-to-date, you will periodically have to rerun the *&#8220;debmirror&#8221;* command to resynchronise your mirror  with the online repository, and subsequently update your local package indexes again&#8212;e.g.:
```
debmirror --nosource --md5sums --passive \
   --host=archive.ubuntu.com --root=ubuntu --method=http --progress \
   --dist=jaunty,jaunty-backports,jaunty-security,jaunty-updates \
   --section=main,multiverse,restricted,universe --arch=i386,amd64 \
   ~/UbuntuRepos
sudo apt-get update
```

---

### Post by BobSongs on 2009-06-26
Simply art!

Added to my tutorial.

:D

---

### Post by luvr on 2009-06-29
[SIZE="4"][COLOR="DarkRed"]**_The Problem._**[/COLOR][/SIZE]

I’m trying to set up a local mirror for the Canonical *“Partner”* repository—similar to the local Ubuntu mirror that I documented in [an earlier post in this thread.]("http://ubuntuforums.org/showthread.php?p=7367273#post7367273")

First, I create a directory in which I will download the repository files:
```
mkdir ~/PartnerRepos
```

Next, I perform a *“debmirror”* test run (using the *“--dry-run”* option):
```
debmirror --dry-run --md5sums --passive --host=archive.canonical.com --root=ubuntu \
  --method=http --progress --dist=jaunty --section=partner --arch=i386 \
  ~/PartnerRepos
```

However, instead of running to completion, *“debmirror”* complains about the following error:
```
[ 60%] Getting: dists/jaunty/partner/binary-i386/Packages.bz2...
   dists/jaunty/partner/binary-i386/Packages.bz2 failed 404 Not Found

[ 60%] Getting: dists/jaunty/partner/source/Sources.bz2...
   dists/jaunty/partner/source/Sources.bz2 failed 404 Not Found
```

Apparently, *“debmirror”* expects the online repository to provide *“Packages.bz2”* and *“Sources.bz2”* files—which seem to be missing.

To verify what’s wrong with the online repository, I open a browser, and I navigate to the page from which *“debmirror”* attempts to download the *“Packages.bz2”* file—i.e., to the following URL:
```
http://archive.canonical.com/dists/jaunty/partner/binary-i386/
```
There, I discover that *“debmirror”* is, indeed, correct in reporting that the *“Packages.bz2”* file is missing. There **does,** however, exist a *“Packages.gz”* file—which would work equally well, if only *“debmirror”* were intelligent enough to look for it instead.

[SIZE="4"][COLOR="DarkRed"]**_The Fix._**[/COLOR][/SIZE]

Obviously, the problem would instantly get solved if I could somehow create the *“Packages.bz2”* file in the online repository—but I can’t... :???:

Thus, I will have to find a way to tell *“debmirror”* that the *“Packages.bz2”* file is missing allright, but that it shouldn’t care, and that it should work with *“Packages.gz”* instead.

Fortunately, *“debmirror”* is really a Perl script—which I can study, and possibly even enhance. In the end, here’s how I decide to tackle the issue:
[LIST][*]I will define a new option—*“--nopkgbz2”*—which will make *“debmirror”* ignore the *“Packages.bz2”* file, and download *“Packages.gz”* instead.
[*]If *“debmirror”* is run ***without*** my new *“--nopkgbz2”* option, then it will continue to work as usual—i.e., it will want to download the *“Packages.bz2”* file, and it will create the *“Packages.gz”* and *“Packages”* files from it.
[*]If *“debmirror”* is run ***with*** my *“--nopkgbz2”* option, then it will download *“Packages.gz”* instead, and create the *“Packages”* file from it.[/LIST]
In the end, the patch to implement this *“--nopkgbz2”* option turns out to be fairly simple, and it can be applied as documented next.

[INDENT]**_Note:_**

[INDENT]The patch applies to the *“debmirror”* version that is available with Ubuntu 9.04 (the *”Jaunty Jackalope”*) and with Ubuntu 9.10 (the *”Karmic Koala”*); it does **not** work *(nor is it required)* on the *“debmirror”* version for Ubuntu 8.10 (the *”Intrepid Ibex”*) or earlier.[/INDENT][/INDENT]

**_Applying the patch to the *“debmirror”* script._**

I don’t particularly like applying a patch to a system file in-place; instead, I prefer to copy the affected file to, e.g., my home directory, and apply the patch to the copy. Therefore, the following procedure will apply my patch to a copy of the *“debmirror”* script in the home directory of the user that is currently logged in to the system:
[LIST][*]Execute the following commands to copy the *“debmirror”* script to your home directory:
```
cd
cp /usr/bin/debmirror .
```
[*]Download the *“debmirror_pkgbz2_patch.zip”* file attached to this post. Save it into your home directory (next to your *“debmirror”* copy), and run the following command to unzip it and create the *“debmirror_pkgbz2_patch”* file:
```
unzip debmirror_pkgbz2_patch.zip
```
[*]Execute the following command to apply the patch (from the *“debmirror_pkgbz2_patch”* file) to your copy of the *“debmirror”* script:
```
patch < debmirror_pkgbz2_patch
```[/LIST]
Assuming that the *“patch”* command reports no errors, your *“debmirror”* copy will now implement my new *“--nopkgbz2”* option.

**_Trying out the patched *“debmirror”* script._**

To test the patched *“debmirror”* script, run it from your home directory (i.e., prepend *“~/”* to the command name), and add the *“--nopkgbz2”* option to the command line:
```
~/debmirror --dry-run --md5sums --passive --host=archive.canonical.com --root=ubuntu \
  **--nopkgbz2** \
  --method=http --progress --dist=jaunty --section=partner --arch=i386 \
  ~/PartnerRepos
```

This time, *“debmirror”* should not try to download the (missing) *“Packages.bz2”* file, but address*“Packages.gz”* instead—which should allow the command to complete successfully.

---

### Post by luvr on 2009-07-01
[SIZE="4"][COLOR="DarkRed"]**_The Problem._**[/COLOR][/SIZE]

I set up a local Ubuntu mirror in which I keep **binary** packages, but no *sources.* I would now like to add the **source** packages to my local mirror.

The *“obvious”* way to add the source packages, would be to simply remove the *“--nosource”* option from the *“debmirror”* command line—e.g.:
```
debmirror --md5sums --passive --host=archive.ubuntu.com --root=ubuntu \
  --method=http --progress \
  --dist=jaunty,jaunty-backports,jaunty-proposed,jaunty-security,jaunty-updates \
  --section=main,multiverse,restricted,universe --arch=i386,amd64 \
  ~/UbuntuRepos
```
**HOWEVER,** this method has one major drawback, which becomes painfully clear with a huge repository such as in the given example, which consists of five *“dists”* of four *“sections”* each: There will be a **huge** amount of data to be downloaded, and until **all** source packages are downloaded, my repository will remain in an *“unfinished,”* inconsistent state.

I might be tempted to try and download the source packages in pieces—e.g., specifying only a single *“dist”* and a single *“section”* on the first run, and then expanding the parameters again on successive runs, until all source packages get included—but **I should DEFINITELY NOT do that**: if I omit any *“dist”* or *“section”* (or, for that matter, *“arch”*) value, then all data for the omitted parts will get **erased** from my local mirror, and I will have to *redownload* them later on.

It would be a far better idea to create a **separate** mirror, in which I can download the source packages independently, without affecting my existing (binary) mirror. Fortunately, *“debmirror”* will let me create a **“source-only”** mirror pretty easily—as described next.

[SIZE="4"][COLOR="DarkRed"]**_The Solution: Creating a “Source-Only” Local Mirror._**[/COLOR][/SIZE]

Since I will be creating a new local mirror, I will first create a directory in which I will download the repository files:
```
mkdir ~/UbuntuSources
```

Next, to tell *“debmirror”* to download **only** the **source** packages, and ignore any *binary* packages, I simply set the *“--arch”* parameter to *“none”*—e.g.:
```
debmirror --md5sums --passive --host=archive.ubuntu.com --root=ubuntu \
  --method=http --progress --dist=jaunty --section=restricted --arch=**none** \
  ~/UbuntuSources
```
[INDENT]**_Note:_**

[INDENT]In this example, I download only a small sample from the (**huge!**) collection of source packages that are available in the Ubuntu repositories. Once this small sample is complete, I can expand the *“dist”* and *“section”* parameters step by step, until my *“source-only”* mirror is complete.[/INDENT][/INDENT]
Once my *“source-only”* mirror is loaded with all source packages from the **exact same** *“dists”* and *“sections”* as my binary mirror, I can copy the full contents of its *“pool”* directory to my binary mirror, to create a ***combined** “binary-plus-source”* mirror (or I might prefer to keep the binary and source packages in their own, separate, mirrors).

[INDENT]**_Important:_**

[INDENT]**If** you create a combined (binary-plus-source) mirror, then make sure that you **remove the *“--nosource”* option** from the *“debmirror”* command line whenever you want to bring it up-to-date again! If you ever run *“debmirror”* **with** the *“--nosource”* option again, then the source packages will be ***deleted*** from local the mirror.[/INDENT][/INDENT]

---

### Post by k3lt01 on 2009-07-02
> **luvr said:**
> ```
--dist=jaunty,jaunty-backports,jaunty-proposed,jaunty-security,jaunty-updates \
```
**HOWEVER,** this method has one major drawback, which becomes painfully clear with a huge repository such as in the given example, which consists of **five *“dists”*** of four *“sections”* each: There will be a **huge** amount of data to be downloaded, and until **all** source packages are downloaded, my repository will remain in an *“unfinished,”* inconsistent state.

It may be timely to discuss the "proposed" dist. "Proposed" is just that, a dist that contains packages that are proposed although in no way a certainty for the regular dists. It is in essence a testing area and it is possible using this dist may cause breakage to an otherwise excellent setup.

---

### Post by k3lt01 on 2009-07-05
What happens if I want to maintain a Repository for non i386,amd64 versions of Ubuntu from Hardy onwards? It's not that difficult and only requires minor changes to the normal script. So if you have a PowerPC and want to run Hardy, Intrepid, Jaunty or upcoming versions after they are released you can still have your arch and repository to :popcorn:

Here's the code:
```
debmirror --nosource -m --passive --host=ports.ubuntu.com --root=/ --method=http --progress --dist=**[COLOR="Red"]hardy[/COLOR],[COLOR="Red"]hardy[/COLOR]**-security,**[COLOR="Red"]hardy[/COLOR]**-updates,**[COLOR="Red"]hardy[/COLOR]**-backports,**[COLOR="Red"]hardy[/COLOR]**-proposed --section=main,restricted,universe,multiverse --arch=**[COLOR="Blue"]powerpc[/COLOR]** ~/PortsUbuntu[COLOR="Blue"]**PPC**[/COLOR]Repos --ignore-release-gpg
```

Remember to modify the coloured text to suit your **[COLOR="Red"]distribution (hardy, intrepid, jaunty, etc)[/COLOR]** and **[COLOR="Blue"]architecture (powerpc, sparc, lpia, ia64, hppa, armel) [/COLOR]**

Also remember to make sure you name the Repo destination appropriately so you do not overwrite and inadvertently lose other Repos you have downloaded.

Edit: The size of the PowerPC repo for:
Hardy is 27859 MB.
Intrepid is 26968 MB.
Jaunty is 25322 MB.

---

### Post by silence150 on 2009-10-07
Thanks so much for this guide! 

I had three small problems that might be worth mentioning: : I had to find debpartial from an old distribution and use that. I'm using Hardy myself. 

I downloaded the packages for Jaunty. I tried adding them through KPackageKit, but this didn't work as I had expected. So I added them with apt-cdrom like the guide said to, which worked just fine. 

However, both KPackageKit and Adept failed to handle the DVD switching once I wanted to install something. Synaptic handles the DVD switching.

---

### Post by k3lt01 on 2009-10-08
> **silence150 said:**
> I had to find debpartial from an old distribution and use that. I'm using Hardy myself. Did you try the link in the first post?

---

### Post by BobSongs on 2009-10-09
> **silence150 said:**
> Thanks so much for this guide! 

I had three small problems that might be worth mentioning: : I had to find debpartial from an old distribution and use that. I'm using Hardy myself. 

I downloaded the packages for Jaunty. I tried adding them through KPackageKit, but this didn't work as I had expected. So I added them with apt-cdrom like the guide said to, which worked just fine. 

However, both KPackageKit and Adept failed to handle the DVD switching once I wanted to install something. Synaptic handles the DVD switching.
Sorry; some of the software your referencing is unfamiliar to me. I imagine you're not using Ubuntu, but some derivative such as Kubuntu.

These instructions are specifically for Ubuntu. I'm sorry if they don't meet your needs. While I have enjoyed the K Desktop Environment in the past, its similarity to Windows tends to leave a bad taste in my mouth. Therefore I avoid it if I can.

Thank you for noting that "**KPackageKit**" and "**Adept**" fail to add repository DVDs to the list of available packages. And as you stated **apt-cdrom** at the command prompt does to the trick, proving once again the power of the Linux command line. I'll make a note of that in my tutorial.

---

### Post by dolphin18 on 2009-11-07
ahhh, thx for tutorials...

i try with Karmic... then to many error... ubuntu made many change. 

now install program more complicated if we use Ubuntu Repository DVDs :(

back to jaunty....

---

### Post by k3lt01 on 2009-11-07
> **dolphin18 said:**
> ahhh, thx for tutorials...

i try with Karmic... then to many error... ubuntu made many change. 

now install program more complicated if we use Ubuntu Repository DVDs :(

back to jaunty....
Could you tell us what happened?

---

### Post by dolphin18 on 2009-11-07
> **k3lt01 said:**
> Could you tell us what happened?

example we want to install abiword, the require 5 files. 2 on disk 1 and 3 on disk 2.

Jaunty will take all necessary file on disk 1 then require disk 2, while the Karmic different, Karmic took a file on disk 1 and then ask for the file on disk 2 and back to disk 1 again.

It would be very annoying when you install ubuntu-restricted-extra

---

### Post by k3lt01 on 2009-11-07
I suggest that you load the contents of the disks onto your PC then. I think Luvr has that covered in one of his posts in this thread.

---

### Post by BobSongs on 2009-11-07
> **dolphin18 said:**
> ahhh, thx for tutorials...

i try with Karmic... then to many error... ubuntu made many change. 

now install program more complicated if we use Ubuntu Repository DVDs :(

back to jaunty....
Dolphin: can you download the repositories when using Karmic? Or are you just having difficulty following my tutorial? It would help to have some tutorial-specific issues and not "too many error".

---

### Post by emigrant on 2009-11-07
this is a wonderful tutorial.
thank you very much.

> 
[FONT=Verdana][SIZE=3][COLOR=DarkRed]**Q2: Why don't I skip this mess and download pre-made DVD ISOs?**[/COLOR][/SIZE]
**A1.** Pre-made DVD ISOs are fine for a single, never-to-be-repeated download (if time is an issue). Here's the difficulty: to get updates means downloading the ISOs **again** (sorta time consuming). If a single ISO download is right for you -- use this link: [ftp://ftp.leg.uct.ac.za/pub/linux/ub...-packages-dvd/]("ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/")


btw im running jaunty, so where can i find a pre made DVD?

and why can't Canonical release these type of official pre-made DVDs so that ppl with slow internet may benifit.
[/FONT]

---

### Post by emigrant on 2009-11-07
is it possible to download one DVD perday, without me sitting 23 hours in the internet cafe?

---

### Post by dolphin18 on 2009-11-07
> **k3lt01 said:**
> I suggest that you load the contents of the disks onto your PC then. I think Luvr has that covered in one of his posts in this thread.

Yeah, with limited space in harddisk this tutorial its very usefull

> **BobSongs said:**
> Dolphin: can you download the repositories when using Karmic? Or are you just having difficulty following my tutorial? It would help to have some tutorial-specific issues and not "too many error".

i can download it, i following your tutorial since jaunty and success. i thing ubuntu now different with come of ubuntu software center

in my country. internet is a problem. i need 3 days to download 27GB

---

### Post by dolphin18 on 2009-11-08
> **emigrant said:**
> is it possible to download one DVD perday, without me sitting 23 hours in the internet cafe?

may be if the source provide a jigdo it will be usefull.

---

### Post by BobSongs on 2009-11-13
> **emigrant said:**
> this is a wonderful tutorial.
Well, thanks. It is a patchwork of many different inputs. I just make it look pretty.

> **emigrant said:**
> > [FONT=Verdana][SIZE=3][COLOR=DarkRed]**Q2: Why don't I skip this mess and download pre-made DVD ISOs?**[/COLOR][/SIZE]
**A1.** Pre-made DVD ISOs are fine for a single, never-to-be-repeated download (if time is an issue). Here's the difficulty: to get updates means downloading the ISOs **again** (sorta time consuming). If a single ISO download is right for you -- use this link: [ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/)[/FONT][FONT=Verdana]
btw im running jaunty, so where can i find a pre made DVD?[/FONT]Actually, to be fair, the quote looks more like the following:
> **BobSongs][FONT=Verdana][SIZE=3][COLOR=DarkRed]**Q2: Why don't I skip this mess and download pre-made DVD ISOs?**[/COLOR][/SIZE]
**Answer 1.** Pre-made DVD ISOs are fine for a single, never-to-be-repeated download (if time is an issue). Here's the difficulty: to get updates means downloading the ISOs **again** (sorta time consuming). If a single ISO download is right for you -- use this link: [ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/)

**Answer 2.** Modem connections make this tutorial impossible regardless the O/S. Consider purchasing inexpensive DVD ISOs from an online vendor. Examples are:

[LIST]
[*][**On-Disk.com**]("http://on-disk.com/index.php/cPath/28_135_183")
[*][**OSDisc.com**]("http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html")
[/LIST]
They will provide exactly what you need: Ubuntu ISOs with setup disks - perfect for that off-line PC. These companies will ship these discs right to your door for a small fee (**no affiliation with the author**).[/FONT][/quote]
In other words: it offers **two answers**. Rather than waste your time at an Internet Café, why not spend a few coins and get the DVDs pre-made and shipped? I don't get a penny's profit from these disks. These links and references were added to ensure this tutorial would be full and rewarding in some way to all who come. Try **osdisc.com** for older repositories.

[quote=emigrant said:**
> [FONT=Verdana]and why can't Canonical release these type of official pre-made DVDs so that ppl with slow internet may benifit.[/FONT]

I'm not responsible for what Canonical does or does not do. This tutorial is provided as a service to assist non-Internet Ubuntu users. Canonical already supplies free copies of their O/S, a courtesy above and beyond the call of duty. Complaining here that Canonical does not provide ISO DVDs is unnecessary and beneficial to no-one.

---

### Post by k3lt01 on 2009-11-30
Well it took me a year of Sundays, lol, but I finally have the entire (amd64,i386,powerpc) old-releases repository downloaded and have it replicated as Ubuntu has it in old-releases.ubuntu.com. It must be noted that Dapper is NOT yet available in old-releases yet, it is still very much alive in archive.ubuntu.com.

Because my download script is slightly different to the one in the OP, I have also had to made slight changes to the script in this section, this is mainly to keep all the repository materials within a known folder of my hdd. 

> **BobSongs said:**
> **[SIZE=4][COLOR=DarkOliveGreen]4. Divide into DVD-sized portions[/COLOR][/SIZE]**
[COLOR=DarkSlateGray]**[SIZE=2]Part 1:[/SIZE]**[/COLOR]

[LIST]
[*]**Note:** If you changed repositories in **Step 3** then the following command will require editing:
[/LIST]
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=**[COLOR=Red]hardy[/COLOR]**,[COLOR=Red]**hardy**[/COLOR]-security,**[COLOR=Red]hardy[/COLOR]**-updates,[COLOR=Red]**hardy**[/COLOR]-backports [COLOR=Blue]**--size=DVD**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```1. Replace the red [COLOR=Red]**hardy**[/COLOR] in the code above with your repository choice (i.e., [COLOR=Red]**gutsy**[COLOR=Black], [/COLOR]**intrepid**[/COLOR] or [COLOR=Red]**jaunty**[/COLOR]).
2. If you plan on burning **CDs** instead of **DVDs**, then replace [COLOR=Blue]**--size=DVD**[/COLOR] with [COLOR=Blue]**--size=CD74**[/COLOR] (for 650 megabyte CD-Rs), **or** [COLOR=Blue]**--size=CD80**[/COLOR] (for 700 megabyte CD-Rs)

[COLOR=DarkSlateGray]**[SIZE=2]Part 2:[/SIZE]**[/COLOR]
How many CDs will we need to create? How do we find out? Paste this code in the Terminal and hit Enter:```
ls -l ~/UbuntuDVDs
```If the last folder is **ubuntu[COLOR=Blue]3[/COLOR]** you need to create **[COLOR=Blue]4[/COLOR]** DVDs. If the last folder is **ubuntu[COLOR=Blue]4[/COLOR]** then it will be **[COLOR=Blue]5[/COLOR]** DVDs, and if the last folder is **ubuntu[COLOR=Blue]31[/COLOR]**, you'll need to create [COLOR=Blue]**32**[/COLOR] CDs, and so on.

Having determined the number of physical discs you'll need, use the following as your pattern until all discs are complete (the only change from one to the next is the final number). These represent Hardy Heron's requirements:
```
ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu0
``````
ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu1
``````
ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu2
``````
ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu3
``````
ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu4
```

I have successfully completed the 1st section of the above and later tonight will try to create the DVDs themselves for Warty-i386.

After I have done this I will burn a copy of all the old-releases for safe keeping and storage.

Now to the Canonical repositories for the classic releases. Canonical still lists a "Commercial" section. However, if anyone tries to download the "Commercial" section they will be disappointed because the process will fail and WIPE the relevant repo clean off your hard drive. Why? well it took me a week to figure it out but because there is nothing in the Commercial section anymore the process fails and automatically cleans the repo thinking it is clean. Let the downloader beware a simple change in the repository you are downloading can result in you losing what you already have IF your script is trying to download something that is not available. Please check the release and package files if you intend to take on such a mammoth task. If the relevant release and/or package file is empty or doesn't list anything that section may no longer be available or is being changed.

---

### Post by emigrant on 2009-12-01
by the way, it would be very great, if someonce can upload a finalized DVD.

---

### Post by k3lt01 on 2009-12-01
> **emigrant said:**
> by the way, it would be very great, if someonce can upload a finalized DVD.There would be no use of doing that for any of the current releases as they can and do change weekly if not daily.

As for doing it for an old release considering they are stable you would be better off downloading it via this process. I personally don't have the bandwidth available to upload up to 15gb worth of repositories, on 3 dvds, for something like warty-i386 and each successive version is larger than the previous version.

---

### Post by NorthernSuze on 2009-12-01
Thank-you so much for your excellent instructions. I have the Hardy 8.04.1 DVD collection loaded to ~/ubuntu-repos. To the best of my knowledge I have it set things up as **luvr** explained in post #237;  the dry run looked good.

Question #1 - is there a way of telling from the dry-run how big the initial update will be. 

Question #2 - is there a way of limiting the initial debmirror run to match what is remaining on our bandwidth at the end of the month? (with the plan to resume when the month rolls over.)

I'm a little gun-shy after exceeding our bandwidth a month or five or six this year....:eek:

Suzanne

---

### Post by luvr on 2009-12-02
> **NorthernSuze said:**
> To the best of my knowledge I have it set things up as **luvr** explained in post #237;  the dry run looked good.
That's great to hear!

> Question #1 - is there a way of telling from the dry-run how big the initial update will be.
I cannot verify this at the moment, but doesn't the dry run tell you how much data it would have to download?
Otherwise, you could start up an update *"for real,"* and interrupt it as soon as it works out the amount of data to download.

> Question #2 - is there a way of limiting the initial debmirror run to match what is remaining on our bandwidth at the end of the month?
The only way that I know of to limit a debmirror run, is to specify the *"--max-batch=number"* parameter (where *"number"* represents the maximum number of files that you want to download). That doesn't take into account the *sizes* of the files, though.

---

### Post by emigrant on 2009-12-02
> **BobSongs said:**
> Well, thanks. It is a patchwork of many different inputs. I just make it look pretty.

Actually, to be fair, the quote looks more like the following:

In other words: it offers **two answers**. Rather than waste your time at an Internet Café, why not spend a few coins and get the DVDs pre-made and shipped? I don't get a penny's profit from these disks. These links and references were added to ensure this tutorial would be full and rewarding in some way to all who come. Try **osdisc.com** for older repositories.


I'm not responsible for what Canonical does or does not do. This tutorial is provided as a service to assist non-Internet Ubuntu users. Canonical already supplies free copies of their O/S, a courtesy above and beyond the call of duty. Complaining here that Canonical does not provide ISO DVDs is unnecessary and beneficial to no-one.

thank you very much for the tip :popcorn:

---

### Post by NorthernSuze on 2009-12-02
@luvr:  Thank-you for your prompt reply. I apologize if I'm not quoting/replying correctly - Simple quotes represent the limits of my understanding:)

>  I cannot verify this at the moment, but doesn't the dry run tell you how much data it would have to download? Otherwise, you could start up an update *"for real,"* and interrupt it as soon as it works out the amount of data to download.

Yes, the number is at the end of the command run, and I can't believe I missed it on both dry-runs.

> The only way that I know of to limit a debmirror run, is to specify the *"--max-batch=number"* parameter (where *"number"* represents the maximum number of files that you want to download). That doesn't take into account the *sizes* of the files, though.

Thanks for adding to my knowledge. I'm discovering linux is a candy store with infinite possibilities - and slowly thanks to you, bobsongs, and all the linux gurus so generously sharing time and knowledge - making my own candy is a becoming a reality!;)

Suzanne

---

### Post by BobSongs on 2009-12-04
> **emigrant said:**
> thank you very much for the tip :popcorn:
I'm assuming you'd like a set of Jaunty Jackalope's full DVD repositories?

:p

I found them **here**

[**Ubuntu 9.04 Final Software Repository DVD Set**]("http://on-disk.com/product_info.php/cPath/28_135_183/products_id/867")
[B]
[]("http://on-disk.com/product_info.php/cPath/28_135_183/products_id/867?osCsid=1ba795f66810891a3efe9c57a8658c57")[/B]The price is reasonable.

---

### Post by Sensiva on 2009-12-06
Hello All, first of all I would like to thank everyone who contributed to this golden thread, it saved ALOT of time here at my side :D I tried it on every release of Ubuntu since feisty, and it worked flawlessly except Karmic.

> **BobSongs said:**
> Dolphin: can you download the repositories when using Karmic? Or are you just having difficulty following my tutorial? It would help to have some tutorial-specific issues and not "too many error".

Let me describe it in details. If I want to install a program that needs more than one package, and those packages are located on different DVDs, APT used to fetch then install then ask for the next disc. But with Karmic, after fetching it doesn't install, it prompts for the next discs... etc and then starts installation , the packages currently in the last disc in the drive are installed, then giving an error about the other packages which are located in the previous discs because they are not there. Its not a problem in the discs, I think its APT behavior itself that should be changed. Unfortunately I don't know how to adjust this way of APT in Karmic. but a workaround for this is pointing APT to the local repos already downloaded on the harddrive and not using the created DVDs. I have tested it and worked fine.

I hope I made it clear. I know my English is screwed

If I am right, please give a hint in the first post for Karmic users. If I am wrong let me know why :D

Providing a hint about how to fix this issue is appreciated

Luv Ya All!! :)

/Sensiva

---

### Post by k3lt01 on 2009-12-06
Hi Sensiva, unless your (or anyone else's) hard drive is to small I would keep a local copy and point apt to it instead of using the DVDs. Certainly use the DVDs to transfer the full repository to the hdd and then update from the official Ubuntu repository once a week or so to keep it as Ubuntu has theirs as this would cut download times massively. That's how I am doing things anyway although with concentrating on the old-releases like I have I am so behind the current releases it is going to take me ages to catch up again ;)

---

### Post by Sensiva on 2009-12-07
Hi k3lt01
> **k3lt01 said:**
> Hi Sensiva, unless your (or anyone else's) hard drive is to small I would keep a local copy and point apt to it instead of using the DVDs.

Yup that's what I did :D
> **Sensiva said:**
> But a workaround for this is pointing APT to the local repos already downloaded on the harddrive and not using the created DVDs. I have tested it and worked fine.

But we have a situation :D Till folks at apt fix this issue (or reveal what should be done) we should let people know to avoid complains from others about not working DVDs in Karmic. Plus here at my side, I have many pc's to deploy updates into, I was lucky that those pc's are networked, and one of them has enough space to store the repos but others are not. I hope we get a solution for this.

---

### Post by luvr on 2009-12-07
> **Sensiva said:**
> [...] giving an error about the other packages which are located in the previous discs because they are not there [...]
I have never tried to install from repository CDs or DVDs, but if this behaviour can be confirmed, then it's a pretty nasty bug.

I guess Debian must be affected, too, since that's where this issue must have originated. Has anyone checked if it has already been reported there, perhaps?

---

### Post by Sensiva on 2009-12-07
_**[COLOR=Red]NOTE: [/COLOR]**_[COLOR=Black]This script is no longer working since karmic[/COLOR], I will keep it in this post for educational purpose only.

Hello all, attached a bash script that I wrote which automates the download and build process of the DVDs.

This script do the following:

[LIST=1]
[*]Ask you what Ubuntu release to build the repos for.
[*]What Architecture.
[*]Mirroring method (ftp/http)
[*]The path to the downloaded archive mirror in your harddrive (to update it if you want to)
[*]The path to which ISO files to be stored.
[/LIST]
After downloading the mirror, it will prompt the user for how many DVDs should be built, and then creates another script to add them automatically in your sources list.

Please feel free to suggest any ideas about this script

I am sure it will look so funny and buggy, because I am still a n00b basher, but its working for me at least. If you guys find it worth updating or enhancing and adding it to the tutorial, please DO!

Thanks
/Sensiva

---

### Post by emigrant on 2009-12-07
> **Sensiva said:**
> Hello all, attached a bash script that I wrote which automates the download and build process of the DVDs.

I am sure it will look so funny, because I am still bash n00b, if you guys find it worth updating and adding to the tutorial, please DO!

Thanks
/Sensiva
thank you very much for the script.
how many dvds would this produce? all at once?
and in which format the downloaded file would stay? iso? or some other..?

thanks. :)

---

### Post by Sensiva on 2009-12-07
This script do the following:

[LIST=1]
[*]Ask you what Ubuntu release to build the repos for.
[*]What Architecture.
[*]Mirroring method (ftp/http)
[*]The path to the downloaded archive mirror in your harddrive (to update it if you want to)
[*]The path to which ISO files to be stored.
[/LIST]
After downloading the mirror, it will prompt the user for how many DVDs should be built, and then creates another script to add them automatically in your sources list.

Please feel free to suggest any ideas about this script

---

### Post by emigrant on 2009-12-07
> **Sensiva said:**
> This script do the following:

[LIST=1]
[*]Ask you what Ubuntu release to build the repos for.
[*]What Architecture.
[*]Mirroring method (ftp/http)
[*]The path to the downloaded archive mirror in your harddrive (to update it if you want to)
[*]The path to which ISO files to be stored.
[/LIST]
After downloading the mirror, it will prompt the user for how many DVDs should be built, and then creates another script to add them automatically in your sources list.

Please feel free to suggest any ideas about this script

thanks. is there a way to run this in a windows machine?

---

### Post by Sensiva on 2009-12-07
No it can't be run on windows machine, this script is exactly the same as the first thread, its just hides the complicated commands.

---

### Post by luvr on 2009-12-07
> **Sensiva said:**
> Please feel free to suggest any ideas about this script
Just a thought: You could *default* the release to the one that is currently running. In other words, when the user does not type a value in response to the question about the Ubuntu release, you could automatically assume the currenty running one.

To query the codeword (e.g., *"intrepid,"* *"jaunty,"* *"karmic,"* etc.) for the current release, you can run the following command:
```
lsb_release -cs
```
In a script, you can assign the output of this command to an environment variable, like so:
```
*variable_name*=$(lsb_release -cs)
```
The **$(*command*)** construct will execute the *command* and replace it with its standard output.

---

### Post by Sensiva on 2009-12-07
> **luvr said:**
> Just a thought: You could *default* the release to the one that is currently running. In other words, when the user does not type a value in response to the question about the Ubuntu release, you could automatically assume the currenty running one.

To query the codeword (e.g., *"intrepid,"* *"jaunty,"* *"karmic,"* etc.) for the current release, you can run the following command:
```
lsb_release -cs
```In a script, you can assign the output of this command to an environment variable, like so:
```
*variable_name*=$(lsb_release -cs)
```The **$(*command*)** construct will execute the *command* and replace it with its standard output.

Thanks for the idea and the info. Script updated

---

### Post by k3lt01 on 2009-12-07
Sheesh, I wish I was a smart as you lot.

Seriously BobSongs, Luvr, and Sensiva, you guys all rock :guitar:. I humbly bow down to you all.

---

### Post by Ishachaitanya on 2009-12-11
Re: Howto: Backup and restore your system! 
Backing up by AptonCD and restoring packages offline.
 
 First one have to install aptoncd in the offline computer or the computer which has no internet connection.
 
 The AptonCd can be downloaded with all dependecies in a folder of a internet computer and then can be installed in that internet computer and in any other computer which have no internet connection. To do this one has to be a superuser or administrator with password for the internet computer.
 
 the command is as follows
 
 root@ubuntu:/# apt-rdepends aptoncd 2>&1 | grep "^[a-zA-Z0-9_].*$" > /tmp/x1
 
 apt-rdepends to be installed first in the internet computer if not already installed.
 The above command is for creating a list for all dependencies for aptoncd with the main aptoncd package.
 
 Next commands are
 
 root@ubuntu:/# for f in `cat /tmp/x1` ; do apt-cache show $f | grep Filename | cut -f 2 -d ' ' ; done >/tmp/x2
 
 mkdir mycache 
 [to keep the downloaded aptoncd package with all dependencies in the mycach folder under root]
 
 root@ubuntu:/# cd mycache
 
 root@ubuntu:/mycache# wget -B [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) -i /tmp/x2
 
 [if wget is not already installed then it is to be installed first before executing the above command]
 this command will start downloading packages & all dependencies of aptoncd application.
 
 Now copy the mycache folder to the home directory of the computers which have no internet connection and install it in those computers.
 
 In the internet computer also install the aptoncd and make backup of all packages with upgrades and dependencies and make a CD/DVD/ISO image. Carry them to the computers having no internet connection and by using aptoncd application restore the packages and upgrades with all dependencies.
 
 So by using only one computer with internet one can install applications in other computers having no internet connection at all.

---

### Post by k3lt01 on 2009-12-11
> **Ishachaitanya said:**
> Re: Howto: Backup and restore your system! 
Backing up by AptonCD and restoring packages offline.
 
 First one have to install aptoncd in the offline computer or the computer which has no internet connection.
 
 The AptonCd can be downloaded with all dependecies in a folder of a internet computer and then can be installed in that internet computer and in any other computer which have no internet connection. To do this one has to be a superuser or administrator with password for the internet computer.
 
 the command is as follows
 
 root@ubuntu:/# apt-rdepends aptoncd 2>&1 | grep "^[a-zA-Z0-9_].*$" > /tmp/x1
 
 apt-rdepends to be installed first in the internet computer if not already installed.
 The above command is for creating a list for all dependencies for aptoncd with the main aptoncd package.
 
 Next commands are
 
 root@ubuntu:/# for f in `cat /tmp/x1` ; do apt-cache show $f | grep Filename | cut -f 2 -d ' ' ; done >/tmp/x2
 
 mkdir mycache 
 [to keep the downloaded aptoncd package with all dependencies in the mycach folder under root]
 
 root@ubuntu:/# cd mycache
 
 root@ubuntu:/mycache# wget -B [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) -i /tmp/x2
 
 [if wget is not already installed then it is to be installed first before executing the above command]
 this command will start downloading packages & all dependencies of aptoncd application.
 
 Now copy the mycache folder to the home directory of the computers which have no internet connection and install it in those computers.
 
 In the internet computer also install the aptoncd and make backup of all packages with upgrades and dependencies and make a CD/DVD/ISO image. Carry them to the computers having no internet connection and by using aptoncd application restore the packages and upgrades with all dependencies.
 
 So by using only one computer with internet one can install applications in other computers having no internet connection at all.

That is the long way to go about it. All you need to do is copy the /var/cache/apt/archive folder on the original machine to a thumb drive or another portable usb drive. Then copy the exact same folder to the new machine. Then go to Synaptic> File> Add downloaded packages, tell Synaptic where the downloaded packages are and then select and install them

---

### Post by BobSongs on 2009-12-12
> **k3lt01 said:**
> Sheesh, I wish I was a smart as you lot.

Seriously BobSongs, Luvr, and Sensiva, you guys all rock :guitar:. I humbly bow down to you all.
Luvr and Sensiva do seem to have a handle on their Linux knowledge. I, however, am truly a noob.

This tutorial began when an acquaintance said he wanted to try/learn Linux, but complained of lack of Internet services. Hmm. Giving him a setup CD would be easy, but what about more applications? Handing him .deb files on CDs would not be enough because of missing dependencies. Bleah!!

Then I remembered coming across a brief tutorial about this very issue. When I found it again, its incomplete state was disappointing. Undaunted, it was adapted to Breezy Badger and successfully done.

I found a beefier version of the tutorial, but one that did not get regular attention. :( Ubuntu's releases come every 6 months, fairly fast in comparison to Windows. So following outdated tutorials meant not getting the right results with new releases.

One of the tutorials disappeared and re-appeared, which was also disconcerting. This could be solved by copying the most recent tutorial here, making adjustments for the latest release as well as a bit of a clean up in the formatting.

Then forum members started asking questions: and I had no idea how to respond. That's when I realized I was in over my head. I had to scramble for answers: dig in the man files, ask in other threads, and hope that something could be found elsewhere.

Someone once said to me: "When it comes to Linux, Google is your friend." And Google has made it easy to find answers to difficult questions. We are not the first to encounter difficulties, and we won't be the last. I see this tutorial as a gathering together of ideas from the wider net and from the Ubuntu community. Me? I just kneed the dough! Everyone else supplies the ingredients. They make me look good. :P

---

### Post by luvr on 2009-12-13
> **BobSongs said:**
> Luvr and Sensiva do seem to have a handle on their Linux knowledge. I, however, am truly a noob.
Honestly--my *"Linux knowledge"* didn't *(and still doesn't)* come *"out of the blue,"* you know. As you say:
> I had to scramble for answers: dig in the man files, ask in other threads, and hope that something could be found elsewhere.
That's what I did, and still do, too. Then,
> "When it comes to Linux, Google is your friend."
Anyway, my first experience with Linux dates back from about 1995, when I tried out an early Slackware release. Back in those days, the Slackware CD distribution came with a booklet, which explained a thing or two about Linux, what it was, how it worked, etc., and which eventually grew to become the official *"Slackware Book."* I couldn't get the X Window System to run, so all I was left with was a command-line shell--which I considered an excellent opportunity to learn a few Linux commands (including, e.g, *"vi"* basics), in addition to, among other things, kernel compilation (which I needed to do in order to support the SCSI devices I used back then) and a few details about how GRUB worked.

From then on, I occasionally tried various Linux distributions on and off, learning something new every time, but never seriously considering Linux for my main OS. With Ubuntu 6.06, I could finally imagine getting serious about Linux for the first time, and it wasn't until Ubuntu 7.04 arrived, that I actually began to migrate to Linux.

Linux really is a continuing learning experience--which actually is a huge part of the fun.

---

### Post by alimooghashang on 2009-12-16
hi i have ubuntu 9.10
how to make the full repository DVDs?
how much space i need?
thanks

---

### Post by Sensiva on 2009-12-16
> **alimooghashang said:**
> hi i have ubuntu 9.10

i386 or amd64?
> **alimooghashang said:**
> 
how to make the full repository DVDs?

explained in full details in the first post, read it carefully
> **alimooghashang said:**
> 
how much space i need?

arround 8 dvds may be less

---

### Post by alimooghashang on 2009-12-17
i386
is it possible to do this in windows, or visual interfaces?
not in terminal and so on...

---

### Post by k3lt01 on 2009-12-17
> **alimooghashang said:**
> i386
is it possible to do this in windows, or visual interfaces?
not in terminal and so on...You didn't read the tutorial did you?

Is it possible to do this through Windows? No, not really. I quote

> **BobSongs said:**
> 
 **11. FAQs** answers some frequently asked questions.[INDENT] Q1: How would I do this through DOS/Windows?

[SIZE=3][COLOR=DarkRed]**Question 1: How would I do this through DOS/Windows?**[/COLOR][/SIZE]
[B]
Answer 1.[/B] I... honestly... don't... know. I can't imagine how tedious it would be to try to assemble all this file by file. If you're a dual-booter or you've got faster bandwidth on a Windows machine elsewhere then I understand your dilemma. **debmirror** is the binary that does all the work. I cannot imagine that anyone has made a port for Windows. Until someone shows me a blog that tells Windows users how to accomplish this I suggest looking at the solutions in **Q2**.

**Answer 2.** This is a "round about" way of using a Windows PC where the bandwidth is fast. Try using the Ubuntu setup CD in "Live User Mode". Follow the instructions in this tutorial and use the Windows Hard Drive as your destination. Well, look. I didn't think it would be **easy**, just... sorta... possible.

Is it possible to do this through a visual interface? The terminal is a visual interface. However, if you mean a purpose made GUI then the answer is No not at this time but who knows what will happen in the future.

Not in the terminal and so on...! The terminal is the ideal way to do this so I don't understand the problem.

---

### Post by luvr on 2009-12-18
> **alimooghashang said:**
> i386
is it possible to do this in windows
Not *"out of the box."* However, **debmirror** is a Perl script, and Perl *is* available under Windows, so, at least in theory, with some work, you *might* be able to do it.

I have actually tried to run **debmirror** in Windows, just out of curiosity, but ran into a number of issues that would take far too much work to sort out. With some perseverance, I succeeded in solving the first few problems that I encountered--just to run into the next set of issues. By then, my curiosity was over, so I gave up. I wouldn't want to run **debmirror** in Windows anyway, so why bother?

If you really, *really,* ***really*** want to, you may eventually be able to successfully run **debmirror** in Windows, but be prepared to do a whole lot of googling and experimenting until you get there.

> or visual interfaces?
not in terminal and so on...
Again, not *"out of the box."* You could, of course, develop the necessary scripts, and create an icon for them; that would avoid having to open a terminal and typing the commands yourself--since the scripts would do it for you.
In fact, developing the scripts is a good idea anyway, since you will want to run the same commands whenever you want to update your local mirror; I haven't bothered to hide them behind an icon, though.

---

### Post by Sensiva on 2009-12-18
> **luvr said:**
> 
I have actually tried to run **debmirror** in Windows, just out of curiosity, but ran into a number of issues that would take far too much work to sort out.

How about manually doing what debmirror actually does using GnuWin32 utilities (wget grep awk sed..etc)??

With a batch script, or powershell script, I think it can be done.

---

### Post by luvr on 2009-12-18
> **Sensiva said:**
> How about manually doing what debmirror actually does using GnuWin32 utilities (wget grep awk sed..etc)??

With a batch script, or powershell script, I think it can be done.
Should be doable, indeed--but I won't be the one to do it... I'm just not sufficiently motivated to work on a Windows solution.

Your suggestion did make me wonder about developing an alternative to debmirror under Linux, though. If it can be done using the common utilities, then it should not be all that hard to port the solution to Windows. From my past experience with the GnuWin32 utilities, I do remember that the differences in command-line handling between Linux (bash or dash) and Windows require some modifications when copying over scripts between the two systems, though.

---

### Post by luvr on 2009-12-21
> **Sensiva said:**
> Thanks for the idea and the info. Script updated
Here's another neat little command that I have just discovered:
```
dpkg --print-architecture
```
This command returns the *machine architecture* as the Debian package management software sees it (e.g., *"amd64,"* *"i386,"* etc.). It may simplify how your script determines the default architecture.

---

### Post by Sensiva on 2009-12-21
> **luvr said:**
> Here's another neat little command that I have just discovered:
```
dpkg --print-architecture
```This command returns the *machine architecture* as the Debian package management software sees it (e.g., *"amd64,"* *"i386,"* etc.). It may simplify how your script determines the default architecture.

That's Great! Thank you! Script updated :D

One more thing I really wish to add to that script is checking if the necessary tools are installed, and install them if not. I need to read more about exit codes and stuff in bash.

---

### Post by k3lt01 on 2009-12-21
> **k3lt01 said:**
> Here is a link to an SIL repository that I would really like to download and put on to my hard drive. In this folder they have all the Ubuntu varieties from Breezy to Hardy and even Debian Etch, Sarge and Sid.

[http://packages.sil.org/ubuntu/dists/](http://packages.sil.org/ubuntu/dists/)Just thought I'd let you know that I have got this downloading successfully. Woo Hoo :popcorn: I took a look through the Man pages for debmirror and modified the code, quite a few times, till I finally got it working. I started it on my laptop but will do a complete download on my desktop tonight.

The original problem seemed to stem from the release and package files, that at least is the details debmirror gave with its error report. So I checked the Man pages for debmirror and remembered that Luvr stated in a thread that there was a difference in a previous version of debmirror that meant the new version needed a patch to enable it to download certain files (packages.gz in preference to packages.bz2 from memory). So I uninstalled the Jaunty>Karmic version (debmirror_20070123ubuntu3_all) and installed the Intrepid and earlier version (debmirror_20070123ubuntu1_all). I then added the "--ignore-missing-release" argument to the script and it worked.

I learned 2 lessons today. 1, the latest isn't always the greatest, sometimes you lose functionality by going "bigger and better". 2, I can understand the Man pages, lol.

---

### Post by k3lt01 on 2010-01-12
Has anyone tried using using mirrordir? I have had a little play and it looks really good. However, it literally does mirror an entire directory so if you only want 1, 2 or even 3 dists then you don't want to use mirrordir because you WILL end up with everything on the server.

For those who want to play around check out the [mirrordir man page]("http://manpages.ubuntu.com/cgi-bin/search.py?title=mirrordir").

Now that reading the mirrordir man page has totally blown your mind with excitement and has convinced you to go ahead with trying this you need to do a couple of things. Before I keep going, by reading further and acting on the instructions below YOU take all responsibility for what happens to your system and your consequent Telephone/Internet Bill. Now we have that out of the way you need to:

1. Download and install mirrordir itself along with other required tools to create the DVDs. ```
 sudo apt-get install mirrordir liblockfile-simple-perl liblog-agent-perl ruby mkisofs dpkg-dev libdigest-sha1-perl libruby libzlib-ruby
``` mirrordir is a direct replacement for debmirror. I have them both because debmirror will download what you tell it to download while mirrordir will download the entire directory. Also mirrordir only downloads ftp directories so debmirror is great when you want to do http directories.

2. Create a folder in your /home directory to download the relevant directory into. Mine is setup like so
```
~/Ubuntu/Repositories/archive.ubuntu.com
``` the ~ at the beginning of the code indicates the /home folder. When naming your folders please use names that make sense. I find mimicking the names of the native archives helps me to know what is what on my PC. BobSong's original post has an excellent explanation of the reasoning for naming your folders.

3. In a terminal paste the following command.```
mirrordir -v ftp://archive.ubuntu.com ~/Ubuntu/Repositories/archive.ubuntu.com
``` This will now start downloading EVERYTHING that is in archive.ubuntu.com and place it into your new folder.

NOTES:
1. You **MUST**, repeat ***_MUST_***, direct mirrordir to download into your newly created folder (just like I have indicated in the creation of the folder and the command itself) ***_OTHERWISE YOU WILL DELETE EVERYTHING_*** in your /home folder and over-write it with the contents of archive.ubuntu.com. You have been warned.

2. This method replaces part of steps 1 in BobSongs original post. Everything else works the same. As already explained I use both setups.

3. If you need to stop the download or it drops out you can restart it easily by doing the terminal command again, it will not re-download anything that you already have already completely downloaded instead it will continue on from where it left off.

4. Be aware when Canonical remove a distribution from archive.ubuntu.com mirrordir (and debmirror to for that matter) will delete the now obsolete dist from the folder it is contained in. This means IF you want to keep it you will need to copy the relevant files to a separate folder. To accomplish this I copy the old dist (e.g. Intrepid) to my old-releases.ubuntu.com folder about 1 month before its official End-Of-Life. 2 months after that I run my old-releases.ubuntu.com script to catch any updates I missed in the meantime.

---

### Post by dreamsR4living on 2010-01-20
I have a question about step 4 of Bobsongs tutorial. When I use debcopy, I get messages about a lot ignored files and also 2 non-existence files.

Does that mean that some packages will not be included on the DVDs, which means that I cannot have the full repositories on DVD? Or can these messages be ignored?

Bobsongs, thanks alot for your clear tutorial ;) It helped me out so far!

---

### Post by k3lt01 on 2010-01-20
Can you post the exact messages you get, or a relevant selection, for us to see?

---

### Post by dreamsR4living on 2010-01-22
```
sebastiaan@sebastiaan-desktop:~$ ruby debcopy -l /media/MyBook/UbuntuRepos ~/UbuntuDVDs/ubuntu6
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty/restricted/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty/main/binary-i386/Packages.gz... /media/MyBook/UbuntuRepos/libtotem- not found.
done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty/multiverse/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty/universe/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-updates/restricted/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-updates/main/binary-i386/Packages.gz... /media/MyBook/UbuntuRepos/libtotem- not found.
done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-updates/multiverse/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-updates/universe/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-security/restricted/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-security/main/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-security/multiverse/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-security/universe/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-backports/restricted/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-backports/main/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-backports/multiverse/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-backports/universe/binary-i386/Packages.gz... done
Number of Copied Files: 3124
Number of Ignored Files: 98
Number of Non-existence File: 2

```

This is the output when I use debcopy to create the last (nr. 7) Ubuntu Jaunty repositories DVD. This is the only DVD where I actually get two non-existence files. It is telling "libtotem not found" for 2 times. I also have about 100 ignored files for each of the 7 DVD's. Does this mean that some packages are not downloaded completely, or not at all? Do I have to download all over again?

---

### Post by dreamsR4living on 2010-01-31
Hi, I am trying to install packages from the DVD's in a virtual Ubuntu 9.04 machine, but I am getting Hash Sum mismatches all the time... Is there any way to solve this? I have included a screenshot of the problem.

I am busy to create and test those dvd repositories for two weeks now. I am going to Africa this week to try and set up a computer teaching project, but this hash sum is making me pull my hair out right now. I don't have any internet connection there, so I need these disks to install new packages. 

Is there anyone who can help me out?

---

### Post by k3lt01 on 2010-01-31
> **dreamsR4living said:**
> ```
sebastiaan@sebastiaan-desktop:~$ ruby debcopy -l /media/MyBook/UbuntuRepos ~/UbuntuDVDs/ubuntu6
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty/restricted/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty/main/binary-i386/Packages.gz... /media/MyBook/UbuntuRepos/libtotem- not found.
done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty/multiverse/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty/universe/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-updates/restricted/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-updates/main/binary-i386/Packages.gz... /media/MyBook/UbuntuRepos/libtotem- not found.
done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-updates/multiverse/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-updates/universe/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-security/restricted/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-security/main/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-security/multiverse/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-security/universe/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-backports/restricted/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-backports/main/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-backports/multiverse/binary-i386/Packages.gz... done
Processing /home/sebastiaan/UbuntuDVDs/ubuntu6/dists/jaunty-backports/universe/binary-i386/Packages.gz... done
Number of Copied Files: 3124
Number of Ignored Files: 98
Number of Non-existence File: 2

```

This is the output when I use debcopy to create the last (nr. 7) Ubuntu Jaunty repositories DVD. This is the only DVD where I actually get two non-existence files. It is telling "libtotem not found" for 2 times. I also have about 100 ignored files for each of the 7 DVD's. Does this mean that some packages are not downloaded completely, or not at all? Do I have to download all over again?Sorry I have only just seen your posts. The Packages.gz file is the file that lists what packages are on the dvd iso. If it is telling you that it cannot find libtotem in the Packages.gz file then it is expecting it to be there but it isn't. I would suggest looking for libtotem in your Repo and if it isn't there try to update your Repo download.

> **dreamsR4living said:**
> Hi, I am trying to install packages from the DVD's in a virtual Ubuntu 9.04 machine, but I am getting Hash Sum mismatches all the time... Is there any way to solve this? I have included a screenshot of the problem.

I am busy to create and test those dvd repositories for two weeks now. I am going to Africa this week to try and set up a computer teaching project, but this hash sum is making me pull my hair out right now. I don't have any internet connection there, so I need these disks to install new packages. 

Is there anyone who can help me out?Sorry but even with glasses I cannot read the text in the screenshot

---

### Post by dreamsR4living on 2010-02-01
Thanks for your reaction! 

> I would suggest looking for libtotem in your Repo and if it isn't there try to update your Repo download

I already found libtotem in my offline repositories, so that problem is fixed. 

> Sorry but even with glasses I cannot read the text in the screenshot 

I am sorry for the bad screenshot. Right now I only have the Hash Sum mismatch problem for one file (openoffice.org-common). When I try to install the packages from the Edubuntu add-on disk it also wants to upgrade this package. When this happens, my install aborts and I am left with an unfinished system. I already tried to install the file separately with dpkg -i and dpkg -i --force-all, but also that fails. I have enclosed the part of my terminal output that gives the error below;

```
The following packages will be upgraded:
  language-selector language-selector-common libgnutls26
  openoffice.org-base-core openoffice.org-common openoffice.org-core
  openoffice.org-gtk openoffice.org-math openoffice.org-writer
9 upgraded, 75 newly installed, 0 to remove and 254 not upgraded.
293 not fully installed or removed.
Need to get 0B/131MB of archives.
After this operation, 230MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu 6'
in the drive '/cdrom/' and press enter

Failed to fetch cdrom:[Ubuntu 6]/pool/main/o/openoffice.org/openoffice.org-common_3.0.1-9ubuntu3.1_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
youthcenter1@youthcenter1:~/Desktop$ 
```

Is there any way to ignore this file? Or is there any other way to fix it?

---

### Post by k3lt01 on 2010-02-01
> **dreamsR4living said:**
>  I have enclosed the part of my terminal output that gives the error below;

```
The following packages will be upgraded:
  language-selector language-selector-common libgnutls26
  openoffice.org-base-core openoffice.org-common openoffice.org-core
  openoffice.org-gtk openoffice.org-math openoffice.org-writer
9 upgraded, 75 newly installed, 0 to remove and 254 not upgraded.
293 not fully installed or removed.
Need to get 0B/131MB of archives.
After this operation, 230MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu 6'
in the drive '/cdrom/' and press enter

Failed to fetch cdrom:[Ubuntu 6]/pool/main/o/openoffice.org/openoffice.org-common_3.0.1-9ubuntu3.1_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
youthcenter1@youthcenter1:~/Desktop$ 
```

Is there any way to ignore this file? Or is there any other way to fix it?No you can't ignore the file as far as I am aware, there has been a meesage put at the beginning of this thread about this problem. Basically you need to have all off the repositories on the one disk for a Karmic install as it is a new bug in Karmic systems. If you could use a usb drive (flash or hdd) to keep your repositories on then you will be fine but t this point in time trying to use dvd's isn't working properly. The other thing you could do is copy the dvd's to the computer you are installing them onto if its hdd is big enough to put them all on.

---

### Post by geoffree on 2010-02-04
ABOUT REPOSITORIES...

Ive been trying to enable repositories in my software sources list but cant even find threads that deal only with that subject.  Can you help?  When I 'Reload' repositories I get a list of seven that can't be enabled because theres no public key or they cant be found online. When I try to locate a public key, Im given a list of directories on my hard drive. So? What can I do? Just for clarity, the list is below:
=================================================================================

GPG error: [http://www.fbreader.org](http://www.fbreader.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5FC5445BA702101
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/Release](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/Release)  Unable to find expected entry  multiverse./binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/dists/karmic/backports/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/backports/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.
=============================================================================

I hope you can help.

Thank you,

Geoffree

---

### Post by Sensiva on 2010-02-04
> **geoffree said:**
> 
I hope you can help.

Thank you,

Geoffree

Your question is off-topic, you may start a new thread, mentioning which release of Ubuntu you are running (Jaunty or Karmic...etc) and including your /etc/apt/sources.list. Sure we will be able to help ;)

P.S. deb repos line in sources.list should be in this form (e.g. Karmic)
```
deb http://archive.ubuntu.com/ubuntu karmic main multiverse restricted universe
```

---

### Post by k3lt01 on 2010-02-04
> **geoffree said:**
> ABOUT REPOSITORIES...

Ive been trying to enable repositories in my software sources list but cant even find threads that deal only with that subject.  Can you help?  When I 'Reload' repositories I get a list of seven that can't be enabled because theres no public key or they cant be found online. When I try to locate a public key, Im given a list of directories on my hard drive. So? What can I do? Just for clarity, the list is below:
=================================================================================

GPG error: [http://www.fbreader.org](http://www.fbreader.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5FC5445BA702101
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/Release](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/Release)  Unable to find expected entry  multiverse./binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/dists/karmic/backports/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/backports/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.
=============================================================================

I hope you can help.

Thank you,

GeoffreeHi Geoffree. I agree with Sensiva a little bit. There are many threads on this issue you just need to look a little harder for them or start your own in Absolute Beginners Talk.

I'll give you another hint that will help people to help you and that is to learn how to put things like your sources list etc into a code box. It takes up less space and people will be able to see the whole line easily. To do this you need to type {code} before the text you want in the code box and {/code} after the text you want in the code box. One important thing you need to do is change the { and } for [ and ] otherwise it wont look like this```
 this is what a code box looks like
```it will just look like this {this isn't what a code box looks like}

Now to your question, it is highly possible the OpenOffice ppa has changed so it may be an invalid source now.

Check out these links.
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[http://ubuntuforums.org/showthread.php?t=1310679](http://ubuntuforums.org/showthread.php?t=1310679)

---

### Post by luvr on 2010-02-05
> **geoffree said:**
> GPG error: [http://www.fbreader.org](http://www.fbreader.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5FC5445BA702101

Did you [install the FBReader PGP key]("http://www.fbreader.org/desktop/#debian")? It's documented as follows:
[LIST][*]Download [the key file]("http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc");
[*]As root, run
```
apt-key add geometer.fbreader.org.asc
```[/LIST]
Your other problems must have something to do with incorrectly specified repositories in your *"/etc/apt/sources.list"*; you may want to use your browser to navigate to these locations, and see what you find there.

---

### Post by geoffree on 2010-02-05
Thanks for your suggestions.  I tried to find threads relating to enabling repositories but got back list that included everything but.  Moving on.

Geoffree

---

### Post by geoffree on 2010-02-05
Thank you for replying.  I do know what a code box looks like and how to set out code lists.  I pasted the list of repos I got on the error message (after typing "reload repositories") in order to clarify what I was dealing with.   
I posted as I did after trying to find previous threads relating to repositories.  My search terms had been on the order of: "how to enable repositories"  but I got back a jumble of topics that were totally off subject.  
It seems that the search engines here at Ubuntu are not exactly up to par. Or maybe you could suggest the appropriate way to print terms in order to address more exactly the problem described here and to either find a thread or begin a new one.

An element in the error msg was that the address included '/dists/' though in my 'sources.list', that word wasn't.  That was the truly puzzling part.  I hope that this way of formatting my question will be acceptable.


Thank you,

Geoffree

---

### Post by k3lt01 on 2010-02-05
My comment about the code box was a hint so that we could see the entire line as it appeared, not parts of it with a group of dots in the middle. Sorry if I appeared harsh.

> **geoffree said:**
> An element in the error msg was that the address included '/dists/' though in my 'sources.list', that word wasn't.  That was the truly puzzling part.  I hope that this way of formatting my question will be acceptable.


Thank you,

GeoffreeThe dists section of the line is what you see on the webpages for the repos themselves. Apt etc look for the dists you are using, e.g. Karmic, Karmic-security or Jaunty etc, to do that they need to go to the dists section. All it is is a pathway and it is why that is not actually in your sources.list, if it didn't take the dists pathway then you could end up on a myriad of other folders looking for the files you need. Take a look at the screenshots to see what I mean.

---

### Post by luvr on 2010-02-07
[SIZE="4"][COLOR="DarkRed"]**_The Motivation for this Post._**[/COLOR][/SIZE]

In [an earlier post in this thread,]("http://ubuntuforums.org/showthread.php?p=8421923#post8421923") **NorthernSuze** asked a couple of interesting questions:
[LIST=1][*]Is there a way of telling from the *dry run,* how big the initial update will be?
[*]Is there a way of limiting the initial *&#8220;debmirror&#8221;* run to match what is remaining on our bandwidth at the end of the month?[/LIST]
Following are the immediate answers to these questions:
[LIST][*]Just like the ***real*** run, the ***dry*** run will output a line of text that shows the total size of the download&#8212;e.g.:
```
[COLOR="Navy"]Download all files that we need to get (28061 MiB).[/COLOR]
```
However, the output from a dry run will scroll by so quickly, that it&#8217;s all too easy to miss this line.[/LIST]
[LIST][*]To limit a *&#8220;debmirror&#8221;* run, you can specify the *&#8220;--max-batch=number&#8221;* parameter, where *&#8220;number&#8221;* represents the maximum number of files that you wish to download. This parameter does *not,* however, take into account the actual **sizes** of the files. Consequently, if *&#8220;debmirror&#8221;* happens to select a few huge files, you may end up with a multi-gigabyte download of, say, just five or six files; conversely, if *&#8220;debmirror&#8221;* chooses to download a set of small files, your download may consist of perhaps fifty or sixty files for a total of just a few hundred kilobytes.
[/LIST]
Obviously, while these answers may be helpful to some extent, they won&#8217;t necessarily be perceived as a *complete* solution&#8212;which is why I decided to take a closer look at these issues. The results of my research can be found in this post.

[SIZE="4"][COLOR="DarkRed"]**_Preparatory Steps._**[/COLOR][/SIZE]

If you want to follow along with the experiments described in this post, then I&#8217;m assuming that you have already correctly set up the *&#8220;debmirror&#8221;* program, as documented earlier in this thread.

You will also need to create a directory that will play the role of a new local mirror for the Ubuntu *source* package archive. Thus, you should create a directory named, e.g., *&#8220;UbuntuSources&#8221;* in your home directory&#8212;as follows:
```
cd
mkdir UbuntuSources
```
[INDENT]**_Note:_**

[INDENT]You won&#8217;t have to actually ***download*** the complete software archive into this new directory; instead, it will simply be used for experimentation, possibly *in preparation of* a full download.[/INDENT]

**_Note:_**

[INDENT]For these experiments, I opted for a repository of *source* (as opposed to *binary*) packages, because that turned out to be a little more instructive than a *binary* repository. You *can* adapt the experiments to make them work on a repository of *binary* packages instead, but that, as they say, is *&#8220;left as an exercise for the reader.&#8221;* In fact, you could subsequently make the experiments work even on a *combined* (*binary* plus *source*) repository&#8212;which you can consider a further (and somewhat more advanced) *&#8220;exercise for the reader.&#8221;*[/INDENT][/INDENT]

After you create the appropriate directory, you should use it as the target location on a *&#8220;debmirror&#8221; dry run*&#8212;e.g.:
```
debmirror --dry-run --progress \
   --method=http --host=archive.ubuntu.com --root=ubuntu \
   --dist=karmic,karmic-security,karmic-updates \
   --section=main,multiverse,restricted,universe \
   --arch=none \
   ~/UbuntuSources
```
[INDENT]**_Note:_**

[INDENT]Many of the shell commands in this post will be rather long, and will be split into multiple lines, using the backslash (i.e., **&#8220;\&#8221;**) as the line continuation character. When you enter such commands into a shell, you should either type them on one long line (but *without* the backslashes), or use the backslash as the last character on a line to inform the shell that the command is not yet complete, and that you will continue it on the next line.[/INDENT][/INDENT]

You are now ready to start the experiments&#8212;the first of which will be about finding out how big a full download would be.

[SIZE="4"][COLOR="DarkRed"]**_Experiment 1: How Big Would a Full Download Be?_**[/COLOR][/SIZE]

If you performed the *dry run* as described above, then you will have seen a great number of lines scroll by so fast that you will surely have missed the line that informed you about the total size of the full download&#8212;e.g.:
```
[COLOR="Navy"]Download all files that we need to get (28061 MiB).[/COLOR]
```
Even if you try and scroll back through the output, you will most likely no longer find this line, since it will already have been purged from the buffer maintained by the terminal session, due to the huge amount of text that the command produced.

**_Part 1: Capturing the Output into a File._**

The *&#8220;debmirror&#8221;* command sends its output to its *&#8220;Standard Output Stream&#8221;* (commonly abbreviated as *&#8220;stdout&#8221;*), which is connected to the terminal window by default. The classic way to capture *&#8220;stdout&#8221;* into a file is called *&#8220;Output Redirection,&#8221;* which you activate by means of a **&#8220;>&#8221;** sign followed by the target file name&#8212;e.g., you can send the output from the *&#8220;debmirror&#8221;* dry run to a file named *&#8220;experiment-1.1&#8221;* as follows:
```
debmirror --dry-run --progress \
   --method=http --host=archive.ubuntu.com --root=ubuntu \
   --dist=karmic,karmic-security,karmic-updates \
   --section=main,multiverse,restricted,universe \
   --arch=none \
   ~/UbuntuSources **> experiment-1.1**
```
You won&#8217;t see any output on-screen, because the output will be redirected to the specified file instead.

After this command completes, you can open the file, *&#8220;experiment-1.1,&#8221;* with any text editor, and search for the text *&#8220;Download all files that we need to get&#8221;* to find the total download size.

[INDENT]**_By the way:_**

[INDENT]In addition to the *&#8220;Standard Output Stream&#8221;* (i.e., *&#8220;stdout&#8221;*), there also exists a *&#8220;Standard Error Stream&#8221;* (i.e., *&#8220;stderr&#8221;*), to which programs are expected to output their error messages *(though some programs may choose not to adhere to this convention).* The **&#8220;>&#8221;** redirection operator works only on *&#8220;stdout,&#8221;* and will *not* redirect error messages&#8212;which will continue to appear on-screen.

If you want to redirect the *&#8220;stderr&#8221;* stream, then you should use the **&#8220;2>&#8221;** operator, like so:
```
*command-line* 2> *stderr-destination*
```
In fact, the **&#8220;>&#8221;** notation, to redirect *&#8220;stdout,&#8221;* is a shorthand for  **&#8220;1>&#8221;**&#8212;so, the following are equivalent:
```
*command-line* > *stdout-destination*
```
and:
```
*command-line* 1> *stdout-destination*
```
To redirect **both** *&#8220;stdout&#8221;* **and** *&#8220;stderr,&#8221;* you can, then, use the following construct:
```
*command-line* 1> *stdout-destination* 2> *stderr-destination*
```
Keep in mind, though, that *&#8220;stdout-destination&#8221;* and *&#8220;stderr-destination&#8221;* cannot refer to the same file&#8212;they **must** be different.

To capture both *&#8220;stdout&#8221;* and *&#8220;stderr&#8221;* into a single file, you will have to use the following:
```
*command-line* 1> *stdout-destination* **2>&1**
```[/INDENT][/INDENT]
**_Part 2: Sending the Output into a *&#8220;T Fitting.&#8221;*_**

Instead of simply redirecting the output to a file, you may *&#8220;pipe&#8221;* it through the *&#8220;tee&#8221;* command.

Command *&#8220;piping&#8221;* is the act of connecting two (or more) commands together with a *&#8220;pipe&#8221;* symbol&#8212;i.e., the vertical bar, **&#8220;|&#8221;**&#8212;which will feed the *&#8220;Standard Output Stream&#8221;* from the first command, as input to the second one.

The *&#8220;tee&#8221;* command will read its input (i.e., its *&#8220;Standard Input Stream,&#8221;* or *&#8220;stdin&#8221;*), and create two identical copies of it:
[LIST][*]One copy will go to a file, the name of which should be specified as an argument to the *&#8220;tee&#8221;* command;
[*]Another copy will simply go to the *&#8220;Standard Output Stream&#8221;* of the *&#8220;tee&#8221;* command&#8212;i.e., the terminal window by default.[/LIST]
The command name, *&#8220;tee,&#8221;* is a play of words, derived from the world of plumbing, and refers to the conceptual similarity with a *&#8220;T Fitting.&#8221;*

As an example, you can see the *&#8220;debmirror&#8221;* output scroll by on-screen, while simultaneously copying it to a file named *&#8220;experiment-1.2,&#8221;* as follows:
```
debmirror --dry-run --progress \
   --method=http --host=archive.ubuntu.com --root=ubuntu \
   --dist=karmic,karmic-security,karmic-updates \
   --section=main,multiverse,restricted,universe \
   --arch=none \
   ~/UbuntuSources \
   **| tee experiment-1.2**
```
**_Part 3: *&#8220;Grepping&#8221;* One Leg of the *&#8220;T Fitting.&#8221;*_**

As described above, the *&#8220;tee&#8221;* command will copy its *&#8220;stdin&#8221;* stream to a file and, at the same time, to its standard output stream. Instead of letting the output scroll by on-screen, you can *&#8220;pipe&#8221;* it through yet another command, to post-process it&#8212;e.g., to display only the text lines that you are interested in, and suppress all the rest.

The classic command to search for text strings in a file, is *&#8220;grep&#8221;*&#8212;which reads text from its standard input stream *(or, if specified, from a set of input files),* and outputs only those lines that match a given *&#8220;regular expression.&#8221;*

A *&#8220;regular expression&#8221;* is a particular type of pattern, which describes string formats in an incredibly powerful (albeit awfully cumbersome) notation. A complete description of *&#8220;regular expressions&#8221;* can easily fill a complete book volume *(and then some),* but you can begin to use some of their simpler features without much training.

In the case of the *&#8220;debmirror&#8221;* command, for example, you are likely not all too interested in seeing the complete output scroll by on-screen; instead, what you are really looking for, is the line that contains the text *&#8220;Download all files that we need to get&#8221;*&#8212;you probably won&#8217;t mind if the rest of the output gets suppressed.

The *&#8220;regular expression&#8221;* to identify any text line that contains the string *&#8220;Download all files that we need to get&#8221;* is just the string itself&#8212;in a regular expression, each letter, digit, or space represents simply one occurrence of itself. One typical feature that you may want to use, though, is the *&#8220;start-of-string anchor&#8221;*: the caret&#8212;i.e., **&#8220;^&#8221;**&#8212;in a regular expression does not match any character, but represents the *&#8220;start of the string&#8221;* instead.

Therefore, if you want to search for the text string *&#8220;Download all files that we need to get&#8221;* at the start of a line, you would specify the following *regular expression*:
```
[COLOR="Navy"]^Download all files that we need to get[/COLOR]
```
If you type a *regular expression* on a command line, you should generally enclose it in single quotes; otherwise, the shell will attempt to interpret many of the special characters that usually appear in the expression in unwanted ways&#8212;and, as a result, hopelessly mess up the regular expression before it even gets seen by the command that should process it.

You can now send the *&#8220;debmirror&#8221;* output to a file named *&#8220;experiment-1.3,&#8221;* while simultaneously suppressing all on-screen output except for the one line that you are interested in, as follows:
```
debmirror --dry-run --progress \
   --method=http --host=archive.ubuntu.com --root=ubuntu \
   --dist=karmic,karmic-security,karmic-updates \
   --section=main,multiverse,restricted,universe \
   --arch=none \
   ~/UbuntuSources \
   | tee experiment-1.3 \
   **| grep '^Download all files that we need to get'**
```
[INDENT]**_By the way:_**

[INDENT]The program name *&#8220;grep&#8221;* can be seen as a tribute to the venerable line editor *&#8220;ed,&#8221;* which implements a *&#8220;**g**/re/**p**&#8221;* (i.e., *&#8220;**g**lobal **r**egular **e**xpression **p**rint&#8221;*) command sequence to print all lines that match a given regular expression. In fact, *&#8220;ed&#8221;* was one of the first programs ever that provided an implementation of regular expressions.[/INDENT][/INDENT]

**_Part 4: Eliminating the *&#8220;T Fitting.&#8221;*_**

Chances are, that you don&#8217;t actually care for the complete output from the *&#8220;debmirror&#8221;* command, and that, therefore, there&#8217;s no need to have the *&#8220;tee&#8221;* command copy it into a file.

In other words, you may prefer to simply skip the *&#8220;tee&#8221;* command, and pipe the output directly on to *&#8220;grep&#8221;*&#8212;as follows:
```
debmirror --dry-run --progress \
   --method=http --host=archive.ubuntu.com --root=ubuntu \
   --dist=karmic,karmic-security,karmic-updates \
   --section=main,multiverse,restricted,universe \
   --arch=none \
   ~/UbuntuSources \
   | grep '^Download all files that we need to get'
```
**_Part 5: Less Is More *(more or less).*_**

The *&#8220;more&#8221;* command is a potentially handy utility for paging through text, one screenful at a time. However, as [its man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?more") readily admits:
```
[COLOR="Navy"]This version is especially primitive.  Users should realize that
**less** provides **more** emulation and extensive enhancements.[/COLOR]
```
Because *&#8220;more&#8221;* is rather primitive, a more advanced alternative was developed&#8212;which, in a typical play of words, was dubbed *&#8220;less&#8221;*&#8212;if only to express the idea that *&#8220;less is more.&#8221;*

Thus, if you want to page through text, you will most likely prefer the *&#8220;less&#8221;* utility over *&#8220;more&#8221;*; you could, for example, pipe the *&#8220;debmirror&#8221;* output on to the *&#8220;less&#8221;* command, as follows:
```
debmirror --dry-run --progress \
   --method=http --host=archive.ubuntu.com --root=ubuntu \
   --dist=karmic,karmic-security,karmic-updates \
   --section=main,multiverse,restricted,universe \
   --arch=none \
   ~/UbuntuSources \
   **| less**
```
You will see the first screenful of output, after which the *&#8220;less&#8221;* command waits for further instructions from you. The following are a few of the common commands that you can use to navigate through the text:
[LIST][*]Hit the ***space bar*** to display the next screenful of text;
[*]Hit the ***<ENTER>*** key to scroll forward one single line;
[*]Type a lowercase letter **&#8220;b&#8221;** to scroll backwards one screenful of text;
[*]Type a **&#8220;<&#8221;** sign to jump back to the *start* of the text;
[*]Type a **&#8220;>&#8221;** sign to jump to the *end* of the text.[/LIST]
Obviously, having to keep hitting the space bar until you reach the one line that you are looking for, wouldn&#8217;t be very practical; you will probably want to *search* for the line instead. The command to initiate a search, is the **&#8220;/&#8221;** (*forward slash*) character, which should be followed by the *regular expression* that you want to search for. As soon as you subsequently hit the ***<ENTER>*** key, the search will actually be performed.

Therefore, if you want to search for the text string *&#8220;Download all files that we need to get&#8221;* at the start of a line, you can input the following command to the *&#8220;less&#8221;* utility:
```
/^Download all files that we need to get
```
Finally, when you want to quit the *&#8220;less&#8221;* utility, simply enter a lowercase **&#8220;q&#8221;** command.

[SIZE="4"][COLOR="DarkRed"]**_Experiment 2: What Files Does a *&#8220;debmirror&#8221;* Dry Run Create?_**[/COLOR][/SIZE]

The *&#8220;debmirror&#8221;* dry run will have created a number of subdirectories and files in the *&#8220;~/UbuntuSources&#8221;* directory. You can list the complete contents of this directory with the following command:
```
ls --recursive ~/UbuntuSources
```
In fact, you will be surprised at the number of objects that the *&#8220;~/UbuntuSources&#8221;* directory now contains!

In this experiment, you will find out exactly which files were downloaded into the *&#8220;~/UbuntuSources&#8221;* directory tree by the *&#8220;debmirror&#8221;* dry run, without having to wade through the output from the *&#8220;ls&#8221;* command.

**_Part 1: Finding all Files Created by the *&#8220;debmirror&#8221;* Dry Run._**

There exists an incredibly powerful and versatile command to search for file system objects (like *files* or *directories*) in a directory hierarchy: the *&#8220;find&#8221;* command. As with *&#8220;regular expressions,&#8221;* a complete description of the *&#8220;find&#8221;* command can easily fill a complete book volume *(and then some)*&#8212;but, again as with *&#8220;regular expressions,&#8221;* you can begin to use some of its simpler features without much training.

The first argument that the *&#8220;find&#8221;* command needs, is the name of the directory where you want to start the search. For example, if you want to obtain a full list of files and directories that exist in your *&#8220;~/UbuntuSources&#8221;* directory tree, you can run the following command:
```
find ~/UbuntuSources
```
Note that, even though you instructed the *&#8220;find&#8221;* command to *search* for file system objects in the *&#8220;~/UbuntuSources&#8221;* location, you did *not* specify what you wanted it to ***do*** with any of the objects found. Consequently, the command will simply take its default action&#8212;which is to display the path to each of the objects, one per line.

[INDENT]**_By the way:_**

[INDENT]If, at this point, you&#8217;re curious about the total number of files and directories in your *&#8220;~/UbuntuSources&#8221;* directory tree, then you can pipe the output from the *&#8220;find&#8221;* command on to the *&#8220;wc&#8221;* command, and make it count the number of lines&#8212;like so:
```
find ~/UbuntuSources **| wc --lines**
```
Incidentally, the command name *&#8220;wc&#8221;* stands for *&#8220;word count&#8221;*&#8212;which does not, however, do the command justice, since it will count more than just *&#8220;words.&#8221;*[/INDENT][/INDENT]

To tell the *&#8220;find&#8221;* command that you are interested only in regular files, and that you do not want it to include, e.g., directory entries in its output, you should pass it a *&#8220;-type&#8221;* argument, with a parameter value of *&#8220;f&#8221;* (for *&#8220;regular file&#8221;*)&#8212;like so:
```
find ~/UbuntuSources **-type f**
```
Following is a fragment of the output that may get produced by this command:
```
[COLOR="Navy"].
.
.
/home/luvr/UbuntuSources/.temp/dists/karmic/Release.gpg
/home/luvr/UbuntuSources/.temp/dists/karmic/universe/source/Sources.bz2
/home/luvr/UbuntuSources/.temp/dists/karmic/universe/source/Sources.gz
/home/luvr/UbuntuSources/.temp/dists/karmic/universe/source/Release
/home/luvr/UbuntuSources/.temp/dists/karmic/universe/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic/multiverse/source/Sources.bz2
/home/luvr/UbuntuSources/.temp/dists/karmic/multiverse/source/Sources.gz
/home/luvr/UbuntuSources/.temp/dists/karmic/multiverse/source/Release
/home/luvr/UbuntuSources/.temp/dists/karmic/multiverse/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic/restricted/source/Sources.bz2
/home/luvr/UbuntuSources/.temp/dists/karmic/restricted/source/Sources.gz
/home/luvr/UbuntuSources/.temp/dists/karmic/restricted/source/Release
/home/luvr/UbuntuSources/.temp/dists/karmic/restricted/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic/Release
/home/luvr/UbuntuSources/.temp/dists/karmic/main/source/Sources.bz2
/home/luvr/UbuntuSources/.temp/dists/karmic/main/source/Sources.gz
/home/luvr/UbuntuSources/.temp/dists/karmic/main/source/Release
/home/luvr/UbuntuSources/.temp/dists/karmic/main/source/Sources
.
.
.[/COLOR]
```
You will likely notice that, apparently, just a few unique file names keep showing up in the list&#8212;e.g., *&#8220;Release,&#8221;* *&#8220;Sources,&#8221;* etc. That leads to the next interesting question: exactly *which* unique file names appear in the output?

**_Part 2: Finding the Unique File Names in the Directory Tree._**

So far, you haven&#8217;t given *&#8220;find&#8221;* any instructions on how to *process* the files that it found, so it simply displayed the path to each file&#8212;with a newline character appended, to produce a listing with one entry per line.

You can customise the output format with the *&#8220;-printf&#8221;* argument, which takes a *format string* as its parameter. To output just the file name, with any leading directories removed, you can use the **&#8220;%f&#8221;** format specification, as follows:
```
find ~/UbuntuSources -type f **-printf '%f'**
```
[INDENT]**_Note:_**

[INDENT]Just as with *regular expressions,* it is generally a good idea to enclose a format string in single quotes, to prevent the shell from inappropriately processing many of the special characters that may appear in the format string.[/INDENT][/INDENT]

Even though the above command really does output just the file names, there is one little detail missing: the entries are not followed by newline characters, so the output appears as one long word on a single line. To ensure that each entry gets properly terminated with a newline character, you should add a **&#8220;\n&#8221;** *escape sequence* to the format string, i.e.:
```
find ~/UbuntuSources -type f -printf '%f**\n**'
```
Once you can produce a listing of just the file names, you can reduce it to a list of *unique* names. To that end, you can pass it on to the *&#8220;sort&#8221;* command, with the *&#8220;--unique&#8221;* option to eliminate duplicates:
```
find ~/UbuntuSources -type f -printf '%f\n' **| sort --unique**
```
The resulting output will look something like this:
```
[COLOR="Navy"]Release
Release.gpg
Sources
Sources.bz2
Sources.gz
wkstw1[/COLOR]
```
That last entry, *&#8220;wkstw1,&#8221;* is a file that the *&#8220;debmirror&#8221;* command created, with the file name set to the *host name* of the computer on which the command was run; on your computer, therefore, its name will surely be different. For all practical purposes, you can ignore this file, since it does not really have anything to do with a software archive per se.

The other unique file names are:
[LIST][*]**&#8220;Release&#8221;**&#8212;A high-level description of a software archive, including checksums of some of the other files in the archive.
[*]**&#8220;Release.gpg&#8221;**&#8212;The digital signature for the *&#8220;Release&#8221;* file. If this file is missing, or if the signature cannot be verified or is incorrect, then the software archive cannot be trusted.
[*]**&#8220;Sources&#8221;**&#8212;A detailed listing of all of the *source* packages in a software archive.
[*]**&#8220;Sources.gz&#8221;**&#8212;A *&#8220;gzip&#8221;*-compressed copy of the *&#8220;Sources&#8221;* file.
[*]**&#8220;Sources.bz2&#8221;**&#8212;A *&#8220;bzip2&#8221;*-compressed copy of the *&#8220;Sources&#8221;* file.[/LIST]
[INDENT]**_By the way:_**

[INDENT]The *&#8220;debmirror&#8221;* program will automatically download and verify digital signatures (i.e., *&#8220;Release.gpg&#8221;* files), unless you pass it the *&#8220;--ignore-release-gpg&#8221;* option.[/INDENT]

**_By the way:_**

[INDENT]You can use the *&#8220;gpgv&#8221;* tool if you want to verify a digital signature. First, you will obviously have to locate the digital signature (i.e., the *&#8220;Release.gpg&#8221;* file) that you want to verify&#8212;e.g., using the *&#8220;find&#8221;* command:
```
find ~/UbuntuSources -name Release.gpg -type f
```
You will get a list of files, similar to the following:
```
[COLOR="Navy"]/home/luvr/UbuntuSources/.temp/dists/karmic-updates/Release.gpg
/home/luvr/UbuntuSources/.temp/dists/karmic-security/Release.gpg
/home/luvr/UbuntuSources/.temp/dists/karmic/Release.gpg[/COLOR]
```
To verify, for example, the last signature from this list, you can now run the *&#8220;gpgv&#8221;* utility, passing it the location of the signature file (i.e., *&#8220;Release.gpg&#8221;*) as its first argument, and the signed data file to which the signature corresponds (i.e., *&#8220;Release&#8221;*) as its second argument:
```
gpgv ~/UbuntuSources/.temp/dists/karmic/Release.gpg \
     ~/UbuntuSources/.temp/dists/karmic/Release
```
If all goes well, the program will inform you that the signature is valid:
```
[COLOR="Navy"]gpgv: Signature made Wed 28 Oct 2009 15:23:20 CET using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"[/COLOR]
```[/INDENT][/INDENT]
[SIZE="4"][COLOR="DarkRed"]**_Experiment 3: Concatenating the *&#8220;Sources&#8221;* Files._**[/COLOR][/SIZE]

All of the source packages that belong to the software archive, are described in the *&#8220;Sources&#8221;* files. You can use the *&#8220;find&#8221;* command to list the *&#8220;Sources&#8221;* files, as follows:
```
find ~/UbuntuSources -name Sources -type f
```
The resulting file list will look something like this:
```
[COLOR="Navy"]/home/luvr/UbuntuSources/.temp/dists/karmic-updates/universe/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic-updates/multiverse/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic-updates/restricted/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic-updates/main/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic-security/universe/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic-security/multiverse/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic-security/restricted/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic-security/main/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic/universe/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic/multiverse/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic/restricted/source/Sources
/home/luvr/UbuntuSources/.temp/dists/karmic/main/source/Sources[/COLOR]
```
Instead of processing each of these files separately, you may prefer to combine them into one stream, and continue to work with that&#8212;as documented next.

The traditional command to concatenate files, and send them to *&#8220;stdout,&#8221;* is called *&#8220;cat&#8221;*; if you simply pass the *&#8220;cat&#8221;* command a list of files, then you will see their contents scroll by on-screen, as one long data stream.

Thus, if you want to concatenate, e.g., the *&#8220;Sources&#8221;* files (as listed by the *&#8220;find&#8221;* command above), then you will have to find a way to generate a command line from their names, preceded by the *&#8220;cat&#8221;* command name&#8212;i.e.:
```
[COLOR="Navy"]cat *first-file* *second-file* ... *last-file*[/COLOR]
```
Fortunately, there is a command available that is a perfect fit for this job: the *&#8220;xargs&#8221;* command. By default, the *&#8220;xargs&#8221;* command assumes that its standard input contains a sequence of items, delimited by blanks or newlines. It will construct a command line from:
[LIST=1][*]A *command name* (possibly followed by a set of *initial arguments*), passed to it via the command line;
[*]The sequence of items that it reads from standard input.[/LIST]
Once it has built the command line in this way, it will subsequently execute it.

There is, however, one pitfall when you use *&#8220;xargs&#8221;* in a command pipeline to process the output from the *&#8220;find&#8221;* command: filenames may contain blanks (and even newlines), and these will not properly be parsed. To overcome this issue, you should generally instruct the *&#8220;find&#8221;* command to terminate each filename with a ***null** byte* (instead of a newline)&#8212;i.e., you should pass it a *&#8220;-print0&#8221;* argument. You should then inform the *&#8220;xargs&#8221;* command that its input uses *null bytes* (instead of blanks and newlines) as item separators, by passing it a *&#8220;--null&#8221;* argument.

You can now have the *&#8220;find&#8221;* command list the *&#8220;Sources&#8221;* filenames, separated by *nulls,* and pass the results on to the *&#8220;xargs&#8221;* command to concatenate the files and output them to the terminal window, as follows:
```
find ~/UbuntuSources -name Sources -type f **-print0 | xargs --null cat**
```
Keep in mind that the *&#8220;-print0&#8221;* argument instructs *&#8220;find&#8221;* to separate the filenames with *null bytes* instead of newlines, while the *&#8220;--null&#8221;* argument informs *&#8220;xargs&#8221;* that its input contains *null bytes* as separators. The *&#8220;cat&#8221;* argument is the name of the command that *&#8220;xargs&#8221;* will specify on the command line that it generates; the remainder of the command line will consist of the filenames that were output by the *&#8220;find&#8221;* command.

[INDENT]**_Note:_**

[INDENT]Letting the output from the *&#8220;cat&#8221;* command scroll by on-screen is, obviously, not particularly useful; you may, therefore, wish to redirect it to a file. However, in the following experiments, I will show you how you can further expand the command pipeline, to eventually turn its output into a useful listing that can help you select exactly *which* files you want to download, based on, e.g., their sizes.[/INDENT]

**_Note:_**

[INDENT]If you inadvertently omit the *&#8220;--null&#8221;* argument, while the input stream does use null bytes as separators, then the *&#8220;xargs&#8221;* command will emit the following warning message to its standard error stream:
```
[COLOR="Navy"]xargs: Warning: a NUL character occurred in the input.  It cannot be passed through in the argument list.  Did you mean to use the --null option?[/COLOR]
```
You will likely miss this warning, though&#8212;unless you redirect the standard output stream.[/INDENT]

**_Note:_**

[INDENT]The *&#8220;xargs&#8221;* command supports a *&#8220;--verbose&#8221;* argument&#8212;which will cause it to output the generated command line to its standard error stream, before it actually executes the command&#8212;e.g.:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null **--verbose** cat
```
Again, you will likely miss the *stderr* output, unless you redirect the standard output stream.[/INDENT]

**_By the way:_**

[INDENT]If *(just for testing purposes)* you are interested only in any messages that the *&#8220;xargs&#8221;* command may send to the *stderr* stream, and you don&#8217;t really care about the actual output, then you may redirect the *stdout* stream to *&#8220;/dev/null&#8221;*&#8212;i.e., the *&#8220;data sink&#8221;*:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null --verbose cat **> /dev/null**
```
Any data that you send to the *&#8220;data sink&#8221;* will, in effect, get discarded.[/INDENT][/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Experiment 4: Extracting Selected Lines from the *&#8220;Sources&#8221;* Files._**[/COLOR][/SIZE]

All source packages are documented in the *&#8220;Sources&#8221;* files according to a template. To understand how this template works, you can take a closer look at one of the package definitions; consider, for example, the entry for the *&#8220;zsh&#8221;* package:
```
[COLOR="Navy"]Package: zsh
Binary: zsh, zsh-doc, zsh-static, zsh-dev, zsh-dbg
Version: 4.3.10-5ubuntu1
Priority: optional
Section: shells
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Clint Adams <schizo@debian.org>
Build-Depends: texinfo, groff-base, libncursesw5-dev, texi2html (>= 1.76-3), libcap2-dev [!hurd-i386 !kfreebsd-i386 !kfreebsd-amd64], bsdmainutils, libpcre3-dev, texlive-latex-base | tetex-bin
Architecture: any
Standards-Version: 3.8.3
Format: 1.0
Directory: pool/main/z/zsh
Files:
 64a2bf8be5b5c1d295c7d9e3fe921608 1388 zsh_4.3.10-5ubuntu1.dsc
 031efc8c8efb9778ffa8afbcd75f0152 3467439 zsh_4.3.10.orig.tar.gz
 cf95870f2f56709a7946a0d2506145dc 140918 zsh_4.3.10-5ubuntu1.diff.gz
Homepage: http://www.zsh.org/
Vcs-Browser: http://git.debian.org/?p=private/schizo/zsh.git;a=summary
Vcs-Git: git://git.debian.org/git/private/schizo/zsh.git
Checksums-Sha1:
 09772b8414046fc37576155e60d7bdbc348c442b 3467439 zsh_4.3.10.orig.tar.gz
 986fe381f06c9b580145398064a207c604267098 140918 zsh_4.3.10-5ubuntu1.diff.gz
Checksums-Sha256:
 ace52518f217d0ed14a121763a550338c26e3c7b0e988d61aa67055a6231691c 3467439 zsh_4.3.10.orig.tar.gz
 292545aea5ed73647838c96c1bc288b9811f15c569ffac81595454631050b6f2 140918 zsh_4.3.10-5ubuntu1.diff.gz[/COLOR]
```
If you are interested only in the files that make up the source package, and in their location, then you need consider only the *&#8220;Directory:&#8221;* line and the *file entries* following the *&#8220;Files:&#8221;* heading&#8212;i.e.:
```
[COLOR="Navy"]Directory: pool/main/z/zsh
 64a2bf8be5b5c1d295c7d9e3fe921608 1388 zsh_4.3.10-5ubuntu1.dsc
 031efc8c8efb9778ffa8afbcd75f0152 3467439 zsh_4.3.10.orig.tar.gz
 cf95870f2f56709a7946a0d2506145dc 140918 zsh_4.3.10-5ubuntu1.diff.gz[/COLOR]
```
These lines have the following contents:
[LIST][*]The *&#8220;Directory:&#8221;* line shows the location of the files, relative to the root of the software archive.
[LIST][*]For the *online* repository, the root of the software archive is defined by the *&#8220;--method,&#8221;* *&#8220;--host&#8221;* and *&#8220;--root&#8221;* parameter values that you specified on the *&#8220;debmirror&#8221;* command line&#8212;i.e.:
```
[COLOR="Navy"]--method=http --host=archive.ubuntu.com --root=ubuntu[/COLOR]
```
Combining these values with the relative path, as found on the *&#8220;Directory:&#8221;* line, results in the following location:
```
[COLOR="Navy"]http://archive.ubuntu.com/ubuntu/pool/main/z/zsh[/COLOR]
```
If you actually navigate to this location in a browser, you will see the expected files listed there (among others).
[*]For your local mirror, the root of the archive is defined by the *target directory* that you specified on the *&#8220;debmirror&#8221;* command line&#8212;i.e.:
```
[COLOR="Navy"]~/UbuntuSources[/COLOR]
```
Combining this value with the relative path, gives the following location:
```
[COLOR="Navy"]~/UbuntuSources/pool/main/z/zsh[/COLOR]
```
However, since you performed only a *dry run,* you will not actually find the files there just yet.[/LIST][/LIST]
[LIST][*]Each *file entry* following the *&#8220;Files:&#8221;* heading, is formatted as follows:
[LIST][*]It begins with a space character;
[*]The first data item is the *&#8220;MD5&#8221;* checksum of the file, and consists of 32 hexadecimal digits;
[*]This data item is followed by another space character;
[*]The second data item is the size of the file, in bytes;
[*]Next, there is another space character;
[*]The third, and final, data item is the name of the file.[/LIST]
This precise description of the format of these lines will prove to be an invaluable tool to select and process them later on.[/LIST]
**_Part 1: Selecting the *&#8220;Directory:&#8221;* Lines from the Concatenated *&#8220;Sources&#8221;* Files._**

To select just the *&#8220;Directory:&#8221;* lines from the concatenation of the *&#8220;Sources&#8221;* files, and discard all of the other lines, you can expand the command pipeline with an invocation of the *&#8220;grep&#8221;* command&#8212;which you have already encountered. Just tell *&#8220;grep&#8221;* that you want to find all lines that begin with the word *&#8220;Directory,&#8221;* followed by a colon character (i.e., **&#8220;:&#8221;**) and a space&#8212;i.e.:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   **| grep '^Directory: '**
```
**_Part 2: Selecting the *File Entries* Following the *&#8220;Files:&#8221;* Heading._**

It won&#8217;t come as a surprise that the *&#8220;grep&#8221;* tool is perfectly suited to select the *file entries* as well&#8212;i.e., those lines that begin with a space, followed by 32 hexadecimal digits, and another space.

The regular expression to describe these lines consists of the following elements:
[LIST][*]The *&#8220;start-of-string&#8221;* anchor, followed by a space (i.e., **&#8220;^ &#8221;**)&#8212;to indicate that the line must begin with a space;
[*]An expression that describes a sequence of *&#8220;exactly 32 hexadecimal digits&#8221;*&#8212;as documented below;
[*]Another space&#8212;to ensure that the sequence of hexadecimal digits effectively ends after the 32nd digit; without this trailing space, the lines that contain a ***longer*** sequence of hexadecimal digits will be selected as well (i.e., the file entry lines following the *&#8220;Checksums-Sha1:&#8221;* or *&#8220;Checksums-Sha256:&#8221;* headings).[/LIST]
To match a sequence of 32 hexadecimal digits, you will first have to define how to match a *single* hexadecimal digit, and subsequently specify that such a match must be repeated 32 times.

***_Part 2-1: Matching a hexadecimal digit._***

A *hexadecimal digit* is either one of the decimal digits, *&#8220;0&#8221;* through *&#8220;9,&#8221;* or a letter in the range from either *&#8220;A&#8221;* through *&#8220;F&#8221;* or *&#8220;a&#8221;* through *&#8220;f&#8221;* (uppercase and lowercase letters are considered equivalent).

The full list of hexadecimal digits, then, is:

[INDENT]**0123456789ABCDEFabcdef**[/INDENT]

In a regular expression, you can generally match *&#8220;one of the characters in a list&#8221;* by enclosing the list in square brackets&#8212;i.e., **&#8220;[&#8221;** and **&#8220;]&#8221;**; therefore, the following notation will match one hexadecimal digit:
```
[COLOR="Navy"][0123456789ABCDEFabcdef][/COLOR]
```
Within such a selection expression, you may use character *ranges*&#8212;which consist of the first character in the range, a hyphen (i.e., **&#8220;-&#8221;**), and the last character in the range. As an example, you may replace the list of decimal digits with the range *&#8220;0-9&#8221;*; similarly, you can replace the specified uppercase and lowercase letters with the corresponding ranges. Consequently, the above expression can be rewritten using ranges as follows:
```
[COLOR="Navy"][0-9A-Fa-f][/COLOR]
```
As a further matter of convenience, the class of *hexadecimal digits* occurs frequently enough that a *named* notation was defined for it: **&#8220;[:****xdigit:]&#8221;**&#8212;which has become the usual way to refer to *&#8220;a hexadecimal digit&#8221;* within selection expressions:
```
[COLOR="Navy"][[:xdigit:]][/COLOR]
```
Note that this notation requires *two* pairs of square brackets; the outer pair encloses the selection expression, while the inner pair is an integral part of the character class name.

***_Part 2-2: Using &#8220;Interval Expressions&#8221; as Repetition Operators._***

[INDENT]**_Note:_**

[INDENT]Before you can effectively use *&#8220;Interval Expressions,&#8221;* you will have to understand the distinction between *&#8220;**Basic** Regular Expressions&#8221;* and *&#8220;**Extended** Regular Expressions.&#8221;* Various features, including the *interval expressions* discussed here, are not generally available with *Basic* Regular Expressions, but require the use of *Extended* Regular Expressions instead.

Just to understand how *interval expressions* work, however, you needn&#8217;t worry about *Basic* vs. *Extended* regular expressions. For now, just rest assured that *&#8220;grep&#8221;* really does support the feature&#8212;exactly *how* it implements it, will be explained in due course.[/INDENT][/INDENT]

*&#8220;**Extended** Regular Expressions&#8221;* support several *repetition operators*&#8212;the most general of which are *&#8220;Interval Expressions.&#8221;* Such expressions are enclosed in curly braces&#8212;i.e., **&#8220;{&#8221;** and **&#8220;}&#8221;**&#8212;and can take any of the following forms:
[LIST][*]**&#8220;{n}&#8221;**&#8212;The preceding item is matched ***exactly*** *&#8220;n&#8221;* times;
[*]**&#8220;{n,}&#8221;**&#8212;The preceding item is matched ***at least*** *&#8220;n&#8221;* times;
[*]**&#8220;{,m}&#8221;**&#8212;The preceding item is matched ***at most*** *&#8220;m&#8221;* times;
[*]**&#8220;{n,m}&#8221;**&#8212;The preceding item is matched ***at least*** *&#8220;n,&#8221;* but ***at most*** *&#8220;m&#8221;* times.
[/LIST]
***_Part 2-3: Matching a Sequence of Exactly 32 Hexadecimal Digits._***

As explained above, a single hexadecimal digit can be matched with the *&#8220;[[:****xdigit:]]&#8221;* selection expression. Furthermore *(assuming that you are using **extended** regular expressions),* you can make any item match exactly 32 times by following it with the *&#8220;{32}&#8221;* interval expression. Therefore, a sequence of 32 hexadecimal digits can be matched as follows:
```
[COLOR="Navy"][[:xdigit:]]{32}[/COLOR]
```
You are not yet ready to use this feature with *&#8220;grep,&#8221;* though; first, you will have to learn about *&#8220;Basic&#8221;* vs. *&#8220;Extended&#8221;* Regular Expressions, and how *&#8220;grep&#8221;* implements them.

***_Part 2-4: A Closer Look at &#8220;Extended&#8221; Regular Expressions._***

***Extended** Regular Expressions* provide a full set of features&#8212;including all of the following *repetition operators*:
[LIST][*]*Interval Expressions,* as described above, which are enclosed in curly braces&#8212;i.e., **&#8220;{&#8221;** and **&#8220;}&#8221;**;
[*]The **&#8220;+&#8221;** sign, which is a shorthand for the ***&#8220;{1,}&#8221;*** interval expression&#8212;i.e., the preceding item is matched at least once;
[*]The **&#8220;*&#8221;** sign, which is a shorthand for the ***&#8220;{0,}&#8221;*** interval expression&#8212;i.e., the preceding item is optional, and is matched any number of times;
[*]The **&#8220;?&#8221;** sign, which is a shorthand for the ***&#8220;{,1}&#8221;*** interval expression&#8212;i.e., the preceding item is optional, and is matched at most once.[/LIST]
In addition to these *repetition operators,* the following are also supported:
[LIST][*]The **&#8220;|&#8221;** sign, which is the *&#8220;alternation operator,&#8221;* and matches *either* the item to its left, *or* the item to its right;
[*]Left and right parentheses&#8212;i.e., **&#8220;(&#8221;** and **&#8220;)&#8221;**&#8212;which are used for *grouping* items together.[/LIST]
If you want to remove the special meaning from any of the operators, and match it with a *literal* character instead, then you will have to escape it with a backslash (i.e., **&#8220;\&#8221;**)&#8212;so, for example:
[LIST][*]**&#8220;\{&#8221;** matches a literal left curly brace&#8212;i.e., **&#8220;{&#8221;**&#8212;in the input string;
[*]**&#8220;\}&#8221;** matches a literal right curly brace&#8212;i.e., **&#8220;}&#8221;**&#8212;in the input string;
[*]**&#8220;\+&#8221;** matches a literal plus sign&#8212;i.e., **&#8220;+&#8221;**&#8212;in the input string;
[*]etc.[/LIST]
***_Part 2-5: A Closer Look at &#8220;Basic&#8221; Regular Expressions._***

Of the operators listed above, ***Basic** Regular Expressions* support only the **&#8220;*&#8221;**&#8212;which matches the preceding item zero or more times. As a consequence, if you want to match a literal asterisk, you will have to escape it with a backslash (i.e., **&#8220;\*&#8221;**).

The other operators lose their special meanings, and will be processed as *literal* characters instead&#8212;just like letters, digits, and spaces. In other words, each of the following characters will simply match a single occurrence of itself:
```
[COLOR="Navy"]{ } + ? | ( )[/COLOR]
```
The meaning of an escape sequence that consists of a backslash (i.e., **&#8220;\&#8221;**) followed by one of these characters, is left ***undefined.*** Any program that supports *basic regular expressions,* should come with documentation that explains exactly how it processes such escape sequences.

For example, some programs may simply ignore the backslash, and process the sequence as a literal match with the character following the backslash&#8212;so, e.g., **&#8220;\?&#8221;** will match a single question mark.

Other programs may process both the backslash, and the character following it, as literal matches&#8212;so, e.g., **&#8220;\?&#8221;** will match a single backslash, followed by a question mark.

In fact, any other interpretation is equally valid&#8212;as long as it is properly documented.

***_Part 2-6: A Closer Look at &#8220;grep&#8221; Regular Expressions._***

The *&#8220;grep&#8221;* utility, by default, supports ***Basic** Regular Expressions.* However, *&#8220;GNU grep&#8221;* (which is distributed with Linux systems) makes particularly brilliant use of the escape sequences that are left undefined: any such escape sequence will *activate the special meaning* of the escaped character, as defined for ***Extended** Regular Expressions.*

For example, consider the following regular expression:
```
[COLOR="Navy"][[:xdigit:]]{32}[/COLOR]
```
By default, *&#8220;grep&#8221;* will process this as a ***basic** regular expression*&#8212;it will, therefore, match one hexadecimal digit, followed by a left curly brace (i.e., **&#8220;{&#8221;**), the decimal digits **&#8220;3&#8221;** and **&#8220;2,&#8221;** and finally, a right curly brace (i.e., **&#8220;}&#8221;**).

If you want to activate the special meanings of the curly braces, then (assuming that you are using *&#8220;GNU grep&#8221;*) you should escape them with a backslash&#8212;like so:
```
[COLOR="Navy"][[:xdigit:]]\{32\}[/COLOR]
```
GNU *&#8220;grep&#8221;* will interpret this as matching a sequence of 32 hexadecimal digits.

***_Part 2-7: Finally! The Expanded Command Pipeline to Select the File Entries._***

Unless you are hopelessly confused by now, you are finally ready to build the pipeline to select the *file entries* from the concatenation of the *&#8220;Sources&#8221;* files.

Remember that these lines are described by a regular expression that consists of the following elements:
[LIST][*]The *&#8220;start-of-string&#8221;* anchor, followed by a space (i.e., **&#8220;^ &#8221;**)&#8212;to indicate that the line must begin with a space;
[*]An expression that describes a sequence of *&#8220;exactly 32 hexadecimal digits&#8221;*&#8212;as documented above;
[*]Another space, to ensure that the sequence of hexadecimal digits effectively ends after the 32nd digit.[/LIST]
The resulting command line, then, looks like this:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   **| grep '^ [[:xdigit:]]\{32\} '**
```
***_Part 2-8: Not Yet Confused? You Will Be After This Episode of... &#8220;grep&#8221;!_***

As documented above, *&#8220;grep&#8221;* supports ***Basic** Regular Expressions* by default&#8212;even though *&#8220;GNU grep&#8221;* does provide a mechanism to use all of the features that are defined for ***Extended** Regular Expressions.*

However, as an alternative, *&#8220;grep&#8221;* supports a command-line option to modify its behaviour and make it support ***Extended** Regular Expressions* instead: the *&#8220;--extended-regexp&#8221;* option.

Therefore, the following command makes use of ***Extended** Regular Expressions* to select the detail data lines:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   **| grep --extended-regexp '^ [[:xdigit:]]{32} '**
```
Whether you prefer to use GNU *&#8220;grep&#8221;* ***with*** or ***without*** the *&#8220;--extended-regexp&#8221;* option, is entirely up to you, since the exact same features are supported both ways&#8212;but do make sure that you get the backslash escapes right!

**_Part 3: Selecting Both *&#8220;Directory:&#8221;* Lines and *File Entries* from the *&#8220;Sources&#8221;* Files._**

To select **both** the *&#8220;Directory:&#8221;* lines **and** the *file entries* in one go, you will need the *&#8220;alternation operator&#8221;* (i.e., **&#8220;|&#8221;**)&#8212;which selects any input string that matches *either* the item to the left of the operator, *or* the item to its right.

The following expression, for example, will match both types of lines that were discussed above:
```
[COLOR="Navy"]'^Directory: **|**^ [[:xdigit:]]{32} '[/COLOR]
```
In effect, this expression identifies the lines that **either:**
[LIST][*]*Begin* with the word *&#8220;Directory&#8221;* followed by a *colon* (i.e., **&#8220;:&#8221;**) and a *space,*[/LIST]
**or:**
[LIST][*]*Begin* with a *space* followed by a sequence of *32 hexadecimal digits* and another *space.*[/LIST]
Since the *start-of-string* anchor is common to both subexpressions, you may move it to the front, and use *grouping* (i.e., parentheses) to indicate where exactly the alternation should begin and end&#8212;as follows:
```
[COLOR="Navy"]'^(Directory: **|** [[:xdigit:]]{32} )'[/COLOR]
```
This expression identifies the lines that *begin* with **either:**
[LIST][*]The word *&#8220;Directory&#8221;* followed by a *colon* (i.e., **&#8220;:&#8221;**) and a *space,*[/LIST]
**or:**
[LIST][*]A *space* followed by a sequence of *32 hexadecimal digits* and another *space.*[/LIST]
Similarly, both subexpressions end with a space&#8212;which you may move to the end, *after* the right parenthesis.

Keep in mind that both *alternation* and *grouping* are features of ***Extended** Regular Expressions*; consequently, if you want to use them with GNU *&#8220;grep,&#8221;* you will either have to use the *&#8220;--extended-regexp&#8221;* command-line option, or escape these operators with a backslash.

Armed with this knowledge, you can now adapt the command pipeline as follows, to make it select **both** the *&#8220;Directory:&#8221;* lines **and** the *file entries* that follow the *&#8220;Files:&#8221;* heading:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   **| grep '^\(Directory:\| [[:xdigit:]]\{32\}\) '**
```
[INDENT]**_Note:_**

[INDENT]The command pipeline, as shown here, does **not** make use of the *&#8220;--extended-regexp&#8221;* command-line option. If you wish, you can adapt it to run *with* the option instead&#8212;the results should be identical.[/INDENT][/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Experiment 5: Reformatting the Extracted Lines to Make them Easier to Handle._**[/COLOR][/SIZE]

While the lines that you have just extracted from the concatenated *&#8220;Sources&#8221;* files, contain all the information that you need to identify all files that are present in the software archive *(including their locations),* they are, unfortunately, not formatted in a particularly handy way.

Take, for example, another look at the lines that describe the source files of the *&#8220;zsh&#8221;* package:
```
[COLOR="Navy"]Directory: pool/main/z/zsh
 64a2bf8be5b5c1d295c7d9e3fe921608 1388 zsh_4.3.10-5ubuntu1.dsc
 031efc8c8efb9778ffa8afbcd75f0152 3467439 zsh_4.3.10.orig.tar.gz
 cf95870f2f56709a7946a0d2506145dc 140918 zsh_4.3.10-5ubuntu1.diff.gz[/COLOR]
```
There are two main issues that make this list somewhat impractical to use:
[LIST][*]To fully identify any of the files, you need to consider not just *one,* but *two* lines instead:
[LIST][*]The actual *file entry* shows the name of the file, its size, and its checksum value;
[*]The preceding *&#8220;Directory:&#8221;* heading shows the location of the file *(relative to the root of the software archive).*[/LIST]
[*]The list would be easier on the human eye if it were in a fixed-width columnar format instead.[/LIST]
Thus, the list would be far more manageable if you could reformat it akin to the following:
```
[COLOR="Navy"]           1388 64a2bf8be5b5c1d295c7d9e3fe921608 pool/main/z/zsh/zsh_4.3.10-5ubuntu1.dsc
        3467439 031efc8c8efb9778ffa8afbcd75f0152 pool/main/z/zsh/zsh_4.3.10.orig.tar.gz
         140918 cf95870f2f56709a7946a0d2506145dc pool/main/z/zsh/zsh_4.3.10-5ubuntu1.diff.gz[/COLOR]
```
These lines consist of the following elements:
[LIST][*]A fixed-width, 15-position field for the *file size*;
[*]A space character, to separate the first and second fields;
[*]The *checksum value*&#8212;which is a 32-character field;
[*]Another space character, to separate the second and third fields;
[*]The *path* to the file, relative to the root of the software archive.
Note that this field is composed of:
[LIST][*]The *directory* in which the file is located&#8212;as extracted from the *&#8220;Directory:&#8221;* heading;
[*]A *forward slash* (i.e., **&#8220;/&#8221;**), inserted between the directory and the file name;
[*]The *file name*&#8212;as it occurs on the original *file entry.*[/LIST][/LIST]
As you may have come to expect by now, there exists a great, and surprisingly powerful, tool that allows you to transform the file list in exactly this way.

That tool is called *&#8220;awk&#8221;*&#8212;and is introduced next.

[INDENT]**_By the way:_**

[INDENT]The program name *&#8220;awk&#8221;* is derived from the names of its original authors: Alfred V. *(&#8220;Vaino&#8221;)* **_A_**ho, Peter J. *(&#8220;Jay&#8221;)* **_W_**einberger, and Brian W. *(&#8220;Wilson&#8221;)* **_K_**ernighan.[/INDENT][/INDENT]

**_Part 1: A First Look at *&#8220;awk.&#8221;*_**

The primary goal of *&#8220;awk&#8221;* is, to process text files, line by line, and perform actions on them, according to a set of instructions that you supply.

The instructions that *&#8220;awk&#8221;* understands, generally consist of two parts:
[LIST=1][*]An expression to *select* the lines of text to which the actions must be applied.
This expression can take several forms&#8212;if, for instance, you want to select all lines that match a *regular expression,* then you should enclose that *regular expression* in *forward slashes* (i.e., **&#8220;/&#8221;**).
[*]A list of *actions* that must be performed on the selected lines.
This action list should be enclosed in *curly braces* (i.e., **&#8220;{&#8221;** and **&#8220;}&#8221;**).[/LIST]

To make *&#8220;awk&#8221;* take action on, for example, the *&#8220;Directory:&#8221;* lines (as discussed above), you can use the following notation:
```
[COLOR="Navy"]/^Directory: /[/COLOR]
```
This *selection expression* should be followed with the list of *actions* that must be performed on the selected lines. 

One very simple action is just *&#8220;print&#8221;*&#8212;which prints the selected line, like so:
```
[COLOR="Navy"]/^Directory: / { print }[/COLOR]
```

***_Part 1-1: Selecting and Printing the &#8220;Directory:&#8221; Lines._***

You can now expand the command pipeline, to make *&#8220;awk&#8221;* select and print the * &#8220;Directory:&#8221;* lines (and ignore the *file entries*) like this:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | grep '^\(Directory:\| [[:xdigit:]]\{32\}\) ' \
   **| awk '/^Directory: / { print }'**
```
[INDENT]**_Note:_**

[INDENT]Admittedly, the *&#8220;grep&#8221;* command in this pipeline is redundant, since you could pass the concatenated input files directly on to *&#8220;awk&#8221;* instead, and let that ignore all but the *&#8220;Directory:&#8221;* lines. Still, leaving the *&#8220;grep&#8221;* command in for now, will simplify the next few steps.[/INDENT][/INDENT]

***_Part 1-2: Printing a Field from a Selected Line._***

Clearly, if you simply wanted to print the selected lines, unchanged, then you wouldn&#8217;t need *&#8220;awk&#8221;*&#8212;since *&#8220;grep&#8221;* can take perfect care of this task.

However, whenever *&#8220;awk&#8221;* reads an input line, it will scan it and extract its *fields.* By default, *fields* are delimited by white space (i.e., spaces and tabs); consequently, the *&#8220;Directory:&#8221;* lines will have *two* fields:
[LIST=1][*]The literal string *&#8220;Directory:&#8221;*;
[*]The *(relative)* path to the directory.[/LIST]
To refer to a field, you use the *field operator*&#8212;which is a dollar sign (i.e., **&#8220;$&#8221;**)&#8212;followed by the position of the field by number; thus, *&#8220;$1&#8221;* identifies the *first* field, *&#8220;$2&#8221;* is the *second* field, and so on.

To print just one field, instead of the whole line, you can specify the field on the *&#8220;print&#8221;* command. For example, the *directory path* is the second field on a *&#8220;Directory:&#8221;* line. Therefore, you can produce a listing of the directory paths that occur in the concatenated input files, as follows:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | grep '^\(Directory:\| [[:xdigit:]]\{32\}\) ' \
   **| awk '/^Directory: / { print $2 }'**
```
***_Part 1-3: Saving a Field into a Variable._***

Instead of directly specifying the field on the *&#8220;print&#8221;* command, you can save its value into a *variable,* and subsequently use that&#8212;e.g., using *&#8220;dirname&#8221;* as the variable name:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | grep '^\(Directory:\| [[:xdigit:]]\{32\}\) ' \
   **| awk '/^Directory: / { dirname = $2 ; print dirname }'**
```
***_Part 1-4: Combining and Printing Values from Multiple Lines._***

Next, you may expand the *&#8220;awk&#8221;* command with code to select and process the *file entry* lines as well. Thanks to the line filtering done by the *&#8220;grep&#8221;* command, you can keep the *regular expression* for the *file entry* lines pretty simple&#8212;just select any lines that begin with a space.

The *action* could be as simple as printing the *(relative)* path to the file&#8212;i.e., the concatenation of:
[LIST][*]The *&#8220;dirname&#8221;* value, saved from the preceding *&#8220;Directory:&#8221;* line;
[*]A literal *forward slash* character;
[*]The *file name*&#8212;i.e., the third field from the input line.[/LIST]
It is, then, no longer necessary (or desirable) to print the *&#8220;dirname&#8221;* value while processing the *&#8220;Directory:&#8221;* line.

The command line may, therefore, be updated as follows:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | grep '^\(Directory:\| [[:xdigit:]]\{32\}\) ' \
   **| awk '/^Directory: / { dirname = $2 }   /^ / { print dirname "/" $3 }'**
```
***_Part 1-5: Getting the [I]&#8220;awk&#8221;* Instructions From a File._**[/I]

So far, you entered the *&#8220;awk&#8221;* instructions into a string, delimited by single quotes, directly on the command line. As the instruction list grows, however, this may easily become impractical.

Therefore, it is far more common, and convenient, to save the instructions into a file, and supply that file&#8212;instead of the command line&#8212;as the source from which the instructions are to be read.

Consider, for example, the following code:
```
[COLOR="DarkRed"]/^Directory: /   { dirname = $2 }
/^ /             { print dirname "/" $3 }[/COLOR]
```
If you save this code to a file named, e.g., *&#8220;transform_source_index,&#8221;* then you can specify this file name as the parameter value on a *&#8220;-f&#8221;* argument, in order to get *&#8220;awk&#8221;* to read its instructions from the file&#8212;i.e.:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | grep '^\(Directory:\| [[:xdigit:]]\{32\}\) ' \
   **| awk -f transform_source_index**
```
***_Part 1-6: Making the &#8220;awk&#8221; Script File Executable._***

Once you save the *&#8220;awk&#8221;* instructions to a file, you can inform your system that the file contains executable code, and that *&#8220;awk&#8221;* is the program that should execute it.

First, you will have to set the *&#8220;executable&#8221;* flag on the file, using the *&#8220;chmod&#8221;* command, like this:
```
chmod +x transform_source_index
```
To verify that the file really is *executable* now, you can subsequently list its directory entry, in *long* format, as follows:
```
ls -l transform_source_index
```
The first field of the output line should, then, show three *&#8220;x&#8221;* flags&#8212;e.g.:
```
[COLOR="Navy"]-rw[/COLOR][COLOR="DarkRed"]**_x_**[/COLOR][COLOR="Navy"]r-[/COLOR][COLOR="DarkRed"]**_x_**[/COLOR][COLOR="Navy"]r-[/COLOR][COLOR="DarkRed"]**_x_**[/COLOR]
```

Next, you will have to identify *&#8220;awk&#8221;* as the program to execute the file. To this end, you will have to add a so-called *&#8220;shebang&#8221;* line to the script.

The *&#8220;shebang&#8221;* line must be the ***first*** line of the file, and must have the following format:
[LIST][*]It must begin with a *&#8220;hash&#8221;* sign (i.e., **&#8220;#&#8221;**) and an *&#8220;exclamation mark&#8221;* (i.e., **&#8220;!&#8221;**);
[*]The remainder of the line must specify the *full path* to the executing program&#8212;i.e., in this case, to *&#8220;awk&#8221;*&#8212;followed by a single command-line option flag, if required.[/LIST]
Thus, to compose the *&#8220;shebang&#8221;* line, you will have to determine the *full path* to the *&#8220;awk&#8221;* tool&#8212;using, e.g., the *&#8220;which&#8221;* command:
```
which awk
```
The result of this command should be similar to *&#8220;/usr/bin/awk&#8221;*; then, to complete the *&#8220;shebang&#8221;* line, you will have to append the *&#8220;-f&#8221;* option flag to it&#8212;in order to make *&#8220;awk&#8221;* read its instructions from the file.

The updated version of the *&#8220;transform_source_index&#8221;* script, including the *&#8220;shebang&#8221;* line, will, then, look something like this:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/^Directory: /   { dirname = $2 }
/^ /             { print dirname "/" $3 }[/COLOR]
```
From now on, you can simply execute the *&#8220;transform_source_index&#8221;* file, just like any ordinary program. If, for example, the script file is in your current directory, then you can adapt the command pipeline as follows:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | grep '^\(Directory:\| [[:xdigit:]]\{32\}\) ' \
   **| ./transform_source_index**
```
Thus, to execute the *&#8220;transform_source_index&#8221;* file, you no longer even have to be aware that it is an *&#8220;awk&#8221;* script!

[INDENT]**_Note:_**

[INDENT]The term *&#8220;shebang&#8221;* refers to the first two characters of the line: the *&#8220;ha**_sh_**&#8221;* and the exclamation point&#8212;which, in Unix jargon, is commonly called the *&#8220;**_bang_**.&#8221;*[/INDENT][/INDENT]

**_Part 2: Eliminating the *&#8220;grep&#8221;* Command from the Pipeline._**

The *&#8220;awk&#8221;* script, *&#8220;transform_source_index,&#8221;* is supposed to process two types of lines from its input:
[LIST][*]The *&#8220;Directory:&#8221;* lines;
[*]The *file entry* lines.[/LIST]
So far, you invoked the *&#8220;grep&#8221;* utility to select these lines, and to make sure that all other lines be removed from the input stream that gets passed to *&#8220;awk.&#8221;*

You will not be able to eliminate *&#8220;grep&#8221;* from the command pipeline until you learn how to instruct *&#8220;awk&#8221;* to select the *file entries*&#8212;i.e., the lines that begin with a space, followed by *exactly* 32 hexadecimal digits, and another space. This operation is complicated by the observation that *&#8220;awk&#8221;* does not support *interval expressions.*

***_Part 2-1: A Closer Look at &#8220;awk&#8221; Regular Expressions._***

Traditionally, *&#8220;awk&#8221;* claims to support *&#8220;extended regular expressions&#8221;*&#8212;but, equally traditionally, its view of what constitutes an *&#8220;extended regular expression&#8221;* does **not** include:
[LIST][*]Character classes&#8212;such as *&#8220;[:****xdigit:]&#8221;*&#8212;within selection expressions;
[*]Interval expressions.[/LIST]
Neither of these features are supported by *&#8220;awk.&#8221;*

The lack of support for *named character classes* may be unfortunate, but is not particularly critical&#8212;you can simply replace the *class name* with the list of *individual characters* (or the *ranges* of characters) that belong to the class. As an example, instead of the *&#8220;[:****xdigit:]&#8221;* class, you could use the *&#8220;0-9A-Fa-f&#8221;* construct.

It is much harder, though, to come up with a good alternative for *interval expressions*; if you cannot use these, but you still want to express *&#8220;exactly 32 occurrences&#8221;* of an item, then you will have to explicitly code the item 32 times in a row&#8212;e.g.:
```
[COLOR="Navy"][0-9A-Fa-f][0-9A-Fa-f]...[0-9A-Fa-f][0-9A-Fa-f][/COLOR]
```
(where the ellipsis&#8212;&#8220;...&#8221;&#8212;represents a sequence of yet another 28 *&#8220;[0-9A-Fa-f]&#8221;* selectors).

It should be immediately obvious that a better alternative is sorely needed.

Fortunately, *&#8220;awk&#8221;* provides a built-in function to test the length of a character string. You can, therefore, select and process the *file entry* lines as follows:
[LIST][*]Select the lines that begin with a space, followed by one or more hexadecimal digits, and another space;
[*]Actually *process* the line only if the length of the checksum string (i.e., the first field of the line) is 32.[/LIST]
The new version of the *&#8220;transform_source_index&#8221;* script will, then, look something like this:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/^Directory: /      { dirname = $2 }
/^ [0-9A-Fa-f]+ /   { if ( length ( $1 ) == 32 ) print dirname "/" $3 }[/COLOR]
```
[INDENT]**_Important:_**

[INDENT]In *&#8220;awk&#8221;* (just as in the C programming language), a *single* **&#8220;=&#8221;** sign represents the *assignment* operator, and a *double* **&#8220;=&#8221;** sign&#8212;i.e., **&#8220;==&#8221;**&#8212;is required for the *equality testing* operator.[/INDENT][/INDENT]

This version of the script will select *only* the ***desired*** input lines, and *ignore* the rest. Consequently, it allows you to remove *&#8220;grep&#8221;* from the command pipeline&#8212;like so:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | ./transform_source_index
```
***_Part 2-2: {Optionally} Breaking with the Tradition: GNU &#8220;awk.&#8221;_***

As documented above, *&#8220;awk&#8221;* traditionally lacks support for *character classes* and for *interval expressions.* ***GNU** &#8220;awk&#8221;* (a.k.a. *&#8220;gawk&#8221;*), however, does not strictly adhere to this tradition, and provides a set of options to control how it interprets regular expressions:
[LIST][*]By default, *GNU &#8220;awk&#8221;* **does** support *character classes,* but **not** *interval expressions.*
In addition, *GNU &#8220;awk&#8221;* defines some *non-standard* operators, which it also supports in its default mode of operation (but which will not be discussed here).
[*]With the **&#8220;--posix&#8221;** command-line option, *GNU &#8220;awk&#8221;* supports the full set of POSIX standard features&#8212;including both *character classes* and *interval expressions.*
Its *non-standard* operators, however, are **not** supported in this mode.
[*]With the **&#8220;--traditional&#8221;** command-line option, *GNU &#8220;awk&#8221;* supports *only* traditional *&#8220;awk&#8221;* regular expressions.
Consequently, *character classes* and *interval expressions,* as well as its *non-standard* operators, will be disabled.
[*]With the **&#8220;--re-interval&#8221;** command-line option, *GNU &#8220;awk&#8221;* adds *interval expressions* to its set of supported features.
In other words, all of its operators&#8212;including *character classes,* *interval expressions,* and the *non-standard* extensions, will be enabled.
[*]If you specify both the **&#8220;--traditional&#8221;** and the **&#8220;--re-interval&#8221;** options, then  *GNU &#8220;awk&#8221;* will support *interval expressions* in addition to the traditional *&#8220;awk&#8221;* operators.
Both *character classes* and its *non-standard* operators, however, will be disabled.[/LIST]
***_Part 2-3: Which &#8220;awk&#8221; Implementation Does Ubuntu Use By Default?_***

To find out which *&#8220;awk&#8221;* versions are installed on your system, and which of the installed versions is currently in use, you can use the *&#8220;update-alternatives&#8221;* command, as follows:
```
update-alternatives --query awk
```
Here&#8217;s an example of what this command may report:
```
[COLOR="Navy"]Link: awk
Status: auto
Best: /usr/bin/mawk
Value: /usr/bin/mawk

Alternative: /usr/bin/mawk
Priority: 5
Slaves:
 awk.1.gz /usr/share/man/man1/mawk.1.gz
 nawk /usr/bin/mawk
 nawk.1.gz /usr/share/man/man1/mawk.1.gz[/COLOR]
```
From this output, we conclude that the system uses *&#8220;mawk&#8221;*&#8212;which is an independent, high-performance *&#8220;awk&#8221;* implementation done by Mike Brennan, but which faithfully implements only the *traditional* type of *&#8220;awk&#8221;* regular expressions.

[INDENT]**_Note:_**

[INDENT]To obtain authoritative confirmation about the features that your locally installed *&#8220;awk&#8221;* utility does or does not support, you should query its *&#8220;man&#8221;* page (i.e., its manual in electronic format), like so:
```
man awk
```
This will bring up the local *&#8220;awk&#8221;* manual, and invoke the *&#8220;less&#8221;* pager program *(which you encountered earlier on)* to display it.

You will be presented with, e.g., the *&#8220;mawk&#8221;* manual (if that&#8217;s the *&#8220;awk&#8221;* implementation that your system uses); the *&#8220;Regular expressions&#8221;* section of the manual explains which types of *regular expressions* are supported by the program.[/INDENT][/INDENT]

***_Part 2-4: Installing GNU &#8220;awk&#8221; on Your Ubuntu System._***

If you want to install the *GNU &#8220;awk&#8221;* implementation, *&#8220;gawk,&#8221;* on your system, then you can simply run the following command:
```
sudo apt-get install gawk
```
If you subsequently query the list of *&#8220;awk&#8221;* implementations that are installed on your system, then the first few lines of output should look like this:
```
[COLOR="Navy"]Link: awk
Status: auto
Best: /usr/bin/gawk
Value: /usr/bin/gawk[/COLOR]
```
The *&#8220;awk&#8221;* man page will now document the features of the *&#8220;gawk&#8221;* implementation; its *&#8220;Regular Expressions&#8221;* section has the following to say about *&#8220;interval expressions&#8221;*:
```
[COLOR="Navy"]r{n}
r{n,}
r{n,m}     One or two numbers inside braces denote an _interval_ _expression_.
           If  there  is  one  number in the braces, the preceding regular
           expression _r_ is repeated _n_ times.  If  there  are  two  numbers
           separated  by a comma, _r_ is repeated _n_ to _m_ times.  If there is
           one number followed by a comma, then _r_ is repeated at  least  _n_
           times.
           Interval  expressions  are  only available if either **--posix** or
           **--re-interval** is specified on the command line.[/COLOR]
```
This confirms that your system is now using an *&#8220;awk&#8221;* implementation that does indeed support *interval expressions*&#8212;subject to the restrictions noted.

[INDENT]**_Note:_**

[INDENT]If your system continues to use the *&#8220;mawk&#8221;* implementation after you install *&#8220;gawk&#8221;* (or, alternatively, if you want to switch your system back to *&#8220;mawk&#8221;* instead), then you can invoke the *&#8220;update-alternatives&#8221;* command as follows:
```
sudo update-alternatives --config awk
```
You will be presented with a list of *&#8220;awk&#8221;* alternatives that are available on your system. Either select one of the alternatives by number, or just hit the **<ENTER>** key to keep the currently active option.[/INDENT][/INDENT]

***_Part 2-5: Updating the [I]&#8220;awk&#8221;* Script to Use a Character Class._**[/I]

Assuming that your system is now configured to use *&#8220;gawk&#8221;* (instead of *&#8220;mawk&#8221;*), you can begin to use *character classes* without further ado. Thus, you can update the *&#8220;transform_source_index&#8221;* script to use the *&#8220;[:****xdigit:]&#8221;* character class, like this:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/^Directory: /       { dirname = $2 }
/^ [[:xdigit:]]+ /   { if ( length ( $1 ) == 32 ) print dirname "/" $3 }[/COLOR]
```
No changes whatsoever are required to the command pipeline that runs the script:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | ./transform_source_index
```
***_Part 2-6: Updating the [I]&#8220;awk&#8221;* Script to Use an Interval Expression._**[/I]

Even though *&#8220;gawk&#8221;* does provide support for *interval expressions,* this feature remains **disabled** by default. Indeed, the unchanged command pipeline will produce no output whatsoever if you simply update the *&#8220;transform_source_index&#8221;* script to use an *interval expression* for the *file entry* lines&#8212;like this:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/^Directory: /          { dirname = $2 }
/^ [[:xdigit:]]{32} /   { print dirname "/" $3 }[/COLOR]
```
To make this script work, you will have to force *&#8220;gawk&#8221;* to **enable** *interval expressions,* using either the **&#8220;--posix&#8221;** or the **&#8220;--re-interval&#8221;** command-line option.

You may be tempted to add either of these options to the *&#8220;shebang&#8221;* line&#8212;e.g.:
```
[COLOR="Navy"]#!/usr/bin/awk **--posix** -f[/COLOR]
```
Unfortunately, even though this looks like a great idea, it won&#8217;t work; if you make this modification to the *&#8220;transform_source_index&#8221;* script, and subsequently attempt to rerun the command pipeline unchanged, then *&#8220;gawk&#8221;* will display its *usage* information, to tell you that it couldn&#8217;t make sense of the arguments that you supplied:
```
[COLOR="Navy"]Usage: awk [POSIX or GNU style options] -f progfile [--] file ...
Usage: awk [POSIX or GNU style options] [--] 'program' file ...
.
.
.[/COLOR]
```
Apparently, the system won&#8217;t properly parse the *&#8220;shebang&#8221;* line. This behaviour isn&#8217;t even really a bug, since it is documented in the *&#8220;bash&#8221;* man page; indeed, the *&#8220;COMMAND EXECUTION&#8221;* section of the manual has this to say on the subject:
```
[COLOR="Navy"]If the program is a file beginning with #!, the remainder of the first line
specifies an interpreter for the program.  The shell executes the specified
interpreter on operating systems that do not handle this executable  format
themselves.   The arguments to the interpreter consist of a single optional
argument following the interpreter name on the first line of  the  program,
followed  by the name of the program, followed by the command arguments, if
any.[/COLOR]
```
If you have trouble understanding this (somewhat dense) paragraph, then here&#8217;s an explanation of what it seems to be trying to say:
[LIST][*]You attempt to execute a program, say, by the name of *&#8220;./transform_source_index&#8221;*;
[*]That program is a file that begins with *&#8220;#!&#8221;*;
[*]Therefore, the remainder of its first line (i.e., *&#8220;/usr/bin/awk --posix -f&#8221;*) specifies an interpreter for the program file;
[*]The operating system may execute the program on behalf of the shell, but if it doesn&#8217;t support this operation, then the shell will take over from here;
[*]The name of the interpreter, as specified on the first line of the program (i.e., *&#8220;/usr/bin/awk&#8221;*), may be followed by a *single* argument  (i.e., *&#8220;--posix -f&#8221;*);
[*]The shell will execute the interpreter, *&#8220;/usr/bin/awk,&#8221;* with the following arguments:
[LIST][*]The *single* argument that follows the name of the interpreter on the first line of the program&#8212;i.e., *&#8220;--posix -f&#8221;*;
[*]The name of the program&#8212;i.e., *&#8220;./transform_source_index&#8221;*;
[*]Any command-line arguments that you may have supplied on the command line&#8212;i.e., none, in this case.[/LIST][/LIST]
In other words, the *&#8220;/usr/bin/awk&#8221;* interpreter will be passed the string *&#8220;--posix -f&#8221;* as a *single* argument&#8212;which it doesn&#8217;t understand.

Thus, if you want to pass the *&#8220;--posix&#8221;* option to the script, you should **not** add the option to the *&#8220;shebang&#8221;* line, but supply it on the *command line* instead. You will, therefore, have to modify your command pipeline as follows:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | ./transform_source_index **--posix**
```
[INDENT]**_Note:_**

[INDENT]If you find it highly unfortunate that you now have to supply the *&#8220;--posix&#8221;* command-line option whenever you run the *&#8220;transform_source_index&#8221;* script, then I must agree. After all, the *&#8220;shebang&#8221;* line provides a mechanism that should allow you to hide the specifics of how the script is to be executed&#8212;but now, there&#8217;s this silly little detail that keeps creeping up to bite you, if you don&#8217;t pay attention.[/INDENT]

**_Note:_**

[INDENT]The shell supports a *&#8220;POSIXLY_CORRECT&#8221;* environment variable, which causes some utilities&#8212;including *&#8220;gawk&#8221;*&#8212;to behave strictly according to POSIX standards. You can run the following command to set the environment variable:
```
export POSIXLY_CORRECT=1
```
If you subsequently rerun the command pipeline&#8212;even **without** the *&#8220;--posix&#8221;* option&#8212;in the *current* shell session, then the *&#8220;gawk&#8221;* program will behave in the same way as *with* the option.

You should keep in mind, though, that the *&#8220;POSIXLY_CORRECT&#8221;* environment variable may subtly modify the behaviour of various programs in possibly unexpected ways.[/INDENT]

**_By the way:_**

[INDENT]If you&#8217;re curious, the Linux kernel processes the *&#8220;shebang&#8221;* line in its *&#8220;load_script()&#8221;* function&#8212;the source code of which is located in the *&#8220;linux/fs/binfmt_script.c&#8221;* file.[/INDENT][/INDENT]

**_Part 3: Creating the Reformatted Output File._**

First, to recapitulate, your *&#8220;transform_source_index&#8221;* script currently looks something like this:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/^Directory: /          { dirname = $2 }
/^ [[:xdigit:]]{32} /   { print dirname "/" $3 }[/COLOR]
```
The command pipeline to execute the script, will look like the following:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | ./transform_source_index --posix
```
The result will be a list of files in the Ubuntu source package archive&#8212;where, for each file, the path relative to the root of the software archive will be shown.

It is now time to enhance the script, to make it create output lines according to, e.g., the following format:
[LIST][*]A fixed-width, 15-position field for the *file size*;
[*]A space character, to separate the first and second fields;
[*]The *checksum value*&#8212;which is a 32-character field;
[*]Another space character, to separate the second and third fields;
[*]The *path* to the file, relative to the root of the software archive.[/LIST]
***_Part 3-1: Creating Formatted Output with the &#8220;printf&#8221; Statement._***

To create formatted output, *&#8220;awk&#8221;* supports the *&#8220;printf&#8221;* statement&#8212;which expects the following parameters:
[LIST][*]A *&#8220;format string&#8221;* that specifies what the output should look like.
The *&#8220;format string&#8221;* consists of literal text&#8212;which will be output unchanged&#8212;intermixed with *&#8220;format specifiers&#8221;*&#8212;which will be replaced with data values, according to a given set of rules.
[*]A list of *data values* that will be substituted into the output, according to the *&#8220;format specifiers&#8221;* that occur in the *&#8220;format string.&#8221;*[/LIST]
Additionally, keep in mind that the *&#8220;printf&#8221;* statement will not automatically append a newline character to the output string; to produce a newline, you will explicitly have to code a **&#8220;\n&#8221;** escape sequence.

In the *&#8220;format string,&#8221;* the percent sign (i.e., **&#8220;%&#8221;**) will be used as an introducer to a *&#8220;format specifier&#8221;*; the percent sign should be followed by a *data type specifier*&#8212;e.g., **&#8220;d&#8221;** for a decimal number, or **&#8220;s&#8221;** for a character string.

For example, to report the size of a file, as it appears on a *file entry* line as discussed above, you may code the following statement:
```
[COLOR="Navy"]printf "File size: %d.\n" , $2[/COLOR]
```
This statement will output:
[LIST][*]The literal string *&#8220;File size: &#8221;*;
[*]A decimal number&#8212;which takes the place of the *&#8220;%d&#8221;* format specifier;
[*]A period (i.e., **&#8220;.&#8221;**);
[*]A newline.[/LIST]
The value of the decimal number that gets substituted into the output line, will be taken from the first (and only) value supplied after the *&#8220;format string&#8221;*&#8212;i.e., the second field from the input line.

If you want to output the number into a fixed-width field, then you should insert the desired field width in between the **&#8220;%&#8221;** sign and the **&#8220;d&#8221;** type specifier; for example, the following statement will output the file size, right-aligned, in a fixed-width, 15-position field:
```
[COLOR="Navy"]printf "File size: %**15**d.\n" , $2[/COLOR]
```

Next, if you want to report not only the file *size,* but also its *checksum* value, then you could expand the *&#8220;printf&#8221;* statement like this:
```
[COLOR="Navy"]printf "File size: %15d**; checksum: %s**.\n" , $2 **, $1**[/COLOR]
```
Note that this time, the *&#8220;format string&#8221;* includes **two** format specifiers&#8212;one for a decimal number, and one for a character string&#8212;and, consequently, *two* data values are required following the *&#8220;format string.&#8221;* The first value (i.e., **&#8220;$2&#8221;**&#8212;the *second* input field) will be treated as a decimal number, while the second value (i.e., **&#8220;$1&#8221;**&#8212;the *first* input field) will be interpreted as a character string.

***_Part 3-2: Creating the Final Output Format._***

The final output format includes: the file *size* (in a fixed-width, 15-position field); the *checksum* value; and the *path* to the file (relative to the root of the software archive). You could, then, code the *&#8220;printf&#8221;* statement like this:
```
[COLOR="Navy"]printf "%15d %s %s\n" , $2 , $1 , dirname "/" $3[/COLOR]
```
Note that the third data value is actually a concatenation of three items: the *dirname* value; a forward slash; and the third input field (i.e., the file name). You may, therefore, want to treat the *dirname* and the file name as two separate data items, and join them together with the forward slash in the *format string*&#8212;like so:
```
[COLOR="Navy"]printf "%15d %s %s/%s\n" , $2 , $1 , dirname , $3[/COLOR]
```
Notice how the *format string* now includes **four** *format specifiers,* and that, as a consequence, the *&#8220;printf&#8221;* statement requires *four* data values for substitution into the output.

With these modifications, here is what the *&#8220;transform_source_index&#8221;* script comes to look like:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/^Directory: /          { dirname = $2 }
/^ [[:xdigit:]]{32} /   { printf "%15d %s %s/%s\n" , $2 , $1 , dirname , $3 }[/COLOR]
```
***_Part 3-3: Creating the Master File List._***

Now that the file list is in the appropriate format, it is time for the final step in creating the *&#8220;master file list&#8221;*: *sorting* the file list by, e.g., *descending* file size.

To ensure that the output will be sorted correctly, according to the *numeric* value of the file size, you should force a *numeric sort,* with the sort key in columns 1 through 15.

Furthermore,  you should save the final output into a file&#8212;e.g., *&#8220;master_filelist&#8221;*&#8212;instead of letting it scroll by on-screen.

Following, then, is the updated, and final, command pipeline:
```
find ~/UbuntuSources -name Sources -type f -print0 | xargs --null cat \
   | ./transform_source_index --posix \
   **| sort --key=1,15 --numeric-sort --reverse --unique > master_filelist**
```
[INDENT]**_Note:_**

[INDENT]If you&#8217;re curious about the *biggest* files in the software archive, then you can use the *&#8220;head&#8221;* command to view the first ten lines of the *&#8220;master_filelist&#8221;* as follows:
```
head master_filelist
```
To modify the number of lines that you wish to see, you can use the *&#8220;--lines&#8221;* option&#8212;e.g., to view 20, instead of 10, lines:
```
head --lines 20 master_filelist
```
Similarly, if you&#8217;re curious about the *smallest* files in the archive, then you can use the *&#8220;tail&#8221;* command:
```
tail master_filelist
```
The *&#8220;tail&#8221;* command also supports the *&#8220;--lines&#8221;* option&#8212;e.g.:
```
tail --lines 20 master_filelist
```[/INDENT][/INDENT]
[SIZE="4"][COLOR="DarkRed"]**_Experiment 6: Calculating the Total Download Size of the Software Archive._**[/COLOR][/SIZE]

The *&#8220;master_filelist&#8221;* now lists the contents of the *(online)* software archive; each line identifies one data file, and includes the size of the file. Consequently, you can calculate the *total download size* of the software archive by simply adding together the file sizes found in the *&#8220;master_filelist&#8221;*&#8212;as illustrated by the following piece of *&#8220;pseudo code&#8221;*:
```
[COLOR="Navy"]Initialise the *&#8220;total_bytes&#8221;* variable to zero.
For each input line from the *&#8220;master_filelist&#8221;*:
   Add the *&#8220;file size&#8221;* field to the *&#8220;total_bytes&#8221;* variable.
End For.
The *total download size,* in bytes, is now present in the *&#8220;total_bytes&#8221;* variable.
You can divide it by 1024*1024 if you want to report it in ***MiBs*** instead of *bytes.*[/COLOR]
```
The translation of this approach to *&#8220;awk&#8221;* is fairly straightforward:
[LIST][*]You do not explicitly have to initialise the *&#8220;total_bytes&#8221;* variable to zero; *&#8220;awk&#8221;* will automatically do that for you.
If you still want to perform the initialisation yourself anyway, then you will have to write an action list that *&#8220;awk&#8221;* should run just once, at the very beginning of the run *(even **before** it reads the first line from its input file).* To this end, *&#8220;awk&#8221;* supports a special *selection expression* that consists simply of the word ***&#8220;BEGIN&#8221;***&#8212;like so:
```
[COLOR="Navy"]BEGIN { total_bytes = 0 }[/COLOR]
```
[*]The main action&#8212;i.e., adding the *&#8220;file size&#8221;* field to the *&#8220;total_bytes&#8221;* variable&#8212;must be executed for ***every*** input line. In other words, you will have to write an action list that *&#8220;awk&#8221;* will run for *every* input line. To this end, you can simply ***omit*** the *selection expression.* Therefore, since the *&#8220;file size&#8221;* is the first field of the input line, you end up with something like the following:
```
[COLOR="Navy"]{ total_bytes = total_bytes + $1 }[/COLOR]
```
In fact, this operation is commonly abbreviated as follows:
```
[COLOR="Navy"]{ total_bytes += $1 }[/COLOR]
```
If this expression confuses you, then you may want to read it as: *&#8220;**add** the **first input field** to the **total_bytes** variable&#8221;*; hopefully, then, this wording helps clear up any confusion that may have arisen.[/LIST]
[LIST][*]Finally, after all input lines are processed, you will want to print the calculated value. In other words, you want to create an action list that *&#8220;awk&#8221;* should run just once, at the very end of the run *(even **after** all lines from the input file are processed).* To this end, *&#8220;awk&#8221;* supports a special *selection expression* that consists simply of the word ***&#8220;END&#8221;***&#8212;like so:
```
[COLOR="Navy"]END { print total_bytes / (1024 * 1024) " MiB." }[/COLOR]
```[/LIST]
Putting all these elements together *(and omitting the explicit initialisation of the &#8220;total_bytes&#8221; variable),* you arrive at a command line similar to the following:
```
awk '{ total_bytes += $1 }   END { print total_bytes / (1024 * 1024) " MiB." }' < master_filelist
```
If you run this command line, then you will see the following output:
```
[COLOR="Navy"]27502.5 MiB.[/COLOR]
```
This is the total download size of all data files that are present in the software archive.
[INDENT]**_Note:_**

[INDENT]You may remember the download size reported, earlier on, by the *&#8220;debmirror&#8221;* dry run:
```
[COLOR="Navy"]Download all files that we need to get (28061 MiB).[/COLOR]
```
This size includes not only the *data files* (which are listed in your *&#8220;master_filelist&#8221;*), but also the control files (such as *&#8220;Release,&#8221;* *&#8220;Sources,&#8221;* etc.).[/INDENT][/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Experiment 7: Selecting a Subset of Files for an Initial Download._**[/COLOR][/SIZE]

Depending on your internet connectivity&#8212;and on your patience&#8212;you may decide that downloading some 27 GiBs of data in one go is a bit too much of a good thing. You may, therefore, want to select a *subset* of the files for an initial download. In this experiment, you will study various strategies to build such a subset, and you will calculate the total download size of each subset, to help you determine which one suits you best.

**_Part 1: Subsetting the File List Based on a Regular Expression._**

To select a subset of the files listed in the *&#8220;master_filelist,&#8221;* you may want to use the path and file name as the criterion. For example, if you want to select all input lines that contain the string *&#8220;language-pack,&#8221;* then you can code the following *selection expression* in *&#8220;awk&#8221;*:
```
[COLOR="Navy"]/language-pack/[/COLOR]
```
For each selected line, you may want to take the following actions:
[LIST][*]Print the path and file name&#8212;i.e., the third input field;
[*]Add the file size&#8212;i.e., the first input field&#8212;to the total download size of the selected files.[/LIST]
Finally, at the very end of the run, you can print the calculated download size.

The *&#8220;awk&#8221;* script to take these actions will look something like this:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/language-pack/   { print $3 ; download_size += $1 }
END               { print download_size / (1024 * 1024) " MiB." }[/COLOR]
```
If you save this code to a file named, e.g., *&#8220;subset_filelist,&#8221;* and make this file executable, then you can subsequently run it as follows:
```
./subset_filelist < master_filelist
```
You will see the list of selected files, followed by their total download size:
```
[COLOR="Navy"]pool/main/l/language-pack-gnome-fr-base/language-pack-gnome-fr-base_9.10+20091022.tar.gz
pool/main/l/language-pack-kde-pt-base/language-pack-kde-pt-base_9.10+20091022.tar.gz
pool/main/l/language-pack-gnome-pt-base/language-pack-gnome-pt-base_9.10+20091022.tar.gz
.
.
.
pool/main/l/language-pack-gnome-bo-base/language-pack-gnome-bo-base_9.10+20091022.tar.gz
pool/main/l/language-pack-gnome-lg-base/language-pack-gnome-lg-base_9.04+20090413.tar.gz
pool/universe/s/sword-language-packs/sword-language-packs_0.3ubuntu1.tar.gz
603.068 MiB.[/COLOR]
```
As an added convenience, you may want the script to inform you not only about the total download size, but also about the *number* of files selected. To that end, you may keep track of a counter variable that you increment for each selected file. The shorthand notation to *&#8220;add 1 to a variable&#8221;* uses the **&#8220;++&#8221;** operator&#8212;which results in the following updated *&#8220;awk&#8221;* script:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/language-pack/   { print $3 ; download_size += $1 ; number_of_files ++ }
END               { print download_size / (1024 * 1024) " MiB in " number_of_files " files." }[/COLOR]
```
If you execute this version of the script, then the last line of output will look like this:
```
[COLOR="Navy"]603.068 MiB in 398 files.[/COLOR]
```
There&#8217;s one little detail about this script that might be improved: If you want to redirect the list of selected files to an output file, then the last line will get written to that file as well. You will likely prefer this line to go elsewhere, though.

By default, *&#8220;awk&#8221;* will send its output to the *&#8220;Standard Output Stream.&#8221;* If you want any output to be sent anywhere else, then you will have to use the **&#8220;>&#8221;** *&#8220;output redirection&#8221;* operator&#8212;which must be followed by the name of the output file. Furthermore, in addition to actual file names, *&#8220;awk&#8221;* recognises a number of *special* data streams&#8212;most notably, **&#8220;/dev/stderr&#8221;** to refer to the *&#8220;Standard Error Stream.&#8221;*

Thus, you may send the final output line to the *&#8220;Standard Error Stream&#8221;* as follows:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
/language-pack/   { print $3 ; download_size += $1 ; number_of_files ++ }
END               { print download_size / (1024 * 1024) " MiB in " number_of_files " files." > "/dev/stderr" }[/COLOR]
```
If you subsequently run this script, then you may use output redirection to send the list of selected files to an output file&#8212;e.g.:
```
./subset_filelist < master_filelist > download_filelist
```
The *&#8220;download_filelist&#8221;* will now list the selected files, while the final output line will continue to appear on-screen instead.

[INDENT]**_Note:_**

[INDENT]Keep in mind that the *&#8220;awk&#8221;* *output redirection* operator is ***different*** from output redirection in the shell. The first time that *&#8220;awk&#8221;* processes its **&#8220;>&#8221;** operator to send output to a given file, it will automatically open the file for you&#8212;if the file does not yet exist, then it will be created, but if it *does* exist, then its contents will be deleted. Any subsequent output operations on the file will simply append data to the file.

Also keep in mind that the **&#8220;/dev/stderr&#8221;** name is unique to *&#8220;awk&#8221;*; it does ***not*** refer to any specific physical file or device available on the system.[/INDENT][/INDENT]

**_Part 2: Subsetting the File List by Line Number._**

If you open the *&#8220;master_filelist&#8221;* in a text editor, then you may decide that you want to select a block of lines by *line number.* To this end, *&#8220;awk&#8221;* supports a special form of *selection expression,* like this:
```
[COLOR="Navy"]NR==*fromline*,NR==*toline*[/COLOR]
```
In this expression, *&#8220;fromline&#8221;* represents the line number of the *first* line that you want to select from the input file, and  *&#8220;toline&#8221;* identifies the *last* line to be selected.

[INDENT]**_Important:_**

[INDENT]Remember that the comparison operator for equality requires a *double &#8220;equals&#8221;* sign&#8212;i.e., **&#8220;==&#8221;**&#8212;in *&#8220;awk,&#8221;* and that a *single &#8220;equals&#8221;* sign is reserved for *assignment* instead. It is an incredibly common mistake, even among fairly experienced *&#8220;awk&#8221;* users, to overlook this critical distinction. *(In fact, I got bitten by it while I was preparing this document...)*[/INDENT][/INDENT]

So, to select, say, line numbers 3330 through 3399 from the *&#8220;master_filelist,&#8221;* you could modify the *&#8220;subset_filelist&#8221;* script as follows:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
NR==3330,NR==3399   { print $3 ; download_size += $1 ; number_of_files ++ }
END                 { print download_size / (1024 * 1024) " MiB in " number_of_files " files." > "/dev/stderr" }[/COLOR]
```
If you execute this script, then the final output line will look like the following:
```
[COLOR="Navy"]65.7176 MiB in 70 files.[/COLOR]
```
**_Part 3: Subsetting the File List by File Size._**

You may want to select files based on their *sizes*&#8212;e.g., all files that are greater than 100 KiB, but smaller than 200 KiB. Obviously, since the file list is sorted by *(descending)* file size, you could open the *&#8220;master_filelist&#8221;* in an editor, and look for the block of files that satisfy this condition; once you found them, you could then select them by *line number,* as documented above.

Alternatively, you could simply test the *file size* (i.e., the first input field), and select any files for which this value is *greater* than 100 KiB and *smaller* than 200 KiB:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
($1 > 100 * 1024) && ($1 < 200 * 1024)   { print $3 ; download_size += $1 ; number_of_files ++ }
END                                      { print download_size / (1024 * 1024) " MiB in " number_of_files " files." > "/dev/stderr" }[/COLOR]
```
[INDENT]**_Important:_**

[INDENT]The logical *&#8220;AND&#8221;* operator requires a *double &#8220;ampersand&#8221;*&#8212;i.e., **&#8220;&&&#8221;**&#8212;in *&#8220;awk&#8221;* (as it does in the C programming language).[/INDENT][/INDENT]

**_Part 4: Subsetting the File List by Total Download Size._**

Of course, if you have a specific limit in mind for the *total download size,* then you may simply want to select any file that keeps the total size within your set limit.

In other words, for every file:
[LIST][*]If the current *total download size,* augmented with the current *file size,* remains within the limit, then select the file;
[*]Otherwise, reject the file, since it would cause the total download size to exceed the limit.[/LIST]
Assume, for instance, that you want to download up to 2.5 GiB of data&#8212;i.e., 2.5*1024*1024*1024 bytes, or, if you prefer to perform only integer arithmetic, 5*512*1024*1024 bytes.

You could, then, update your *&#8220;awk&#8221;* script as follows:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
download_size + $1 <= 5 * 512 * 1024 * 1024   { print $3 ; download_size += $1 ; number_of_files ++ }
END                                           { print download_size / (1024 * 1024) " MiB in " number_of_files " files." > "/dev/stderr" }[/COLOR]
```
The output from this script will look something like the following:
```
[COLOR="Navy"]pool/universe/n/nexuiz-data/nexuiz-data_2.5.2.orig.tar.gz
pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu17.tar.gz
pool/main/o/openoffice.org/openoffice.org_3.1.1.orig.tar.gz
pool/multiverse/s/sauerbraten-data/sauerbraten-data_0.0.20090504.orig.tar.gz
pool/universe/o/openarena-data/openarena-data_0.8.1.orig.tar.gz
pool/universe/o/opencv/opencv_1.0.0.orig.tar.gz
pool/universe/libe/libemail-localdelivery-perl/libemail-localdelivery-perl_0.217.orig.tar.gz
2560 MiB in 7 files.[/COLOR]
```
[SIZE="4"][COLOR="DarkRed"]**_Experiment 8: Creating the Download List, Checksum List, and Remaining File List._**[/COLOR][/SIZE]

Now that you can select a subset of files that you want to download, you are ready to actually perform the download. However, before you do so, there are a few additional features that you may want to take into account:
[LIST][*]In addition to the actual *download list,* you may want to create a *checksum list* as well&#8212;i.e., a file that lists your selected files with their checksum values, to allow you to verify that all files are downloaded without errors.
[*]You may also want to save the list of files that you do ***not*** select; then, after you download the *selected* files, you can use this list of *remaining* files to select the next subset.[/LIST]
In other words, you may want to update your *&#8220;awk&#8221;* script to create *three,* instead of just one, output files:
[LIST][*]**&#8220;download_filelist&#8221;**&#8212;which contains the list of selected files, as described above.
[*]**&#8220;checksum_filelist&#8221;**&#8212;which contains the list of selected files, in a format that will allow you to verify the integrity of the files after you download them. Each line of this file must consist of the following items:
[LIST][*]The checksum value&#8212;which is a 32-character string;
[*]A blank space;
[*]An asterisk&#8212;i.e., **&#8220;*&#8221;**;
[*]The path to the file, relative to the *current* directory.[/LIST]
[*]**&#8220;remaining_filelist&#8221;**&#8212;which contains a copy of all input lines that you did *not* select.[/LIST]
Note that, since you will now have to take action on *every* input line, you will want to omit the *selection expression,* and let the *action list* decide which route to take.

Assuming that you want to continue to select files based on a total download size of up to 2.5 GiB, a skeletal version of your new *&#8220;subset_filelist&#8221;* script will, then, look something like this:
```
[COLOR="Navy"]#!/usr/bin/awk -f
{ if (download_size + $1 <= 5 * 512 * 1024 * 1024)
  {
     *# ...code to process **selected** files should go here...*
  }
  else
  {   
     *# ...code to process **remaining** files should go here...*
  }
}
END   { print download_size / (1024 * 1024) " MiB in " number_of_files " files." > "/dev/stderr" }[/COLOR]
```
The code to process *remaining* files is pretty simple: it should just copy the input line, unchanged, to a file named *&#8220;remaining_filelist.&#8221;* Since *&#8220;awk&#8221;* provides a copy of the entire input line in its special **&#8220;$0&#8221;** variable (that&#8217;s *&#8220;dollar zero,&#8221;* not *&#8220;dollar uppercase oh,&#8221;* by the way), that&#8217;s a pretty easy action to take:
```
[COLOR="Navy"]print $0 > "remaining_filelist"[/COLOR]
```
The code to output the name of a *selected* file to the *&#8221;download_filelist&#8221;* is equally simple:
```
[COLOR="Navy"]print $3 > "download_filelist"[/COLOR]
```
Finally, to output a line to the *&#8220;checksum_filelist,&#8221;* you will have to identify the path to the data file relative to the *current* directory&#8212;in other words, you will have to include the *&#8220;UbuntuSources&#8221;* directory level on the path (unless you prefer to enter the *&#8220;UbuntuSources&#8221;* directory whenever you want to verify the checksums).

The complete output line will, therefore, contain the *checksum* value, a *space,* an *asterisk,* the literal * &#8220;UbuntuSources/&#8221;* string, and finally, the *file path* taken from the input line:
```
[COLOR="Navy"]print $2 " *UbuntuSources/" $3 > "checksum_filelist"[/COLOR]
```

Consequently, the final version of the *&#8220;subset_filelist&#8221;* script will look like this:
```
[COLOR="DarkRed"]#!/usr/bin/awk -f
{ if (download_size + $1 <= 5 * 512 * 1024 * 1024)
  {
     print $3 > "download_filelist" ;
     print $2 " *UbuntuSources/" $3 > "checksum_filelist" ;
     download_size += $1 ;
     number_of_files ++
  }
  else
  {   
     print $0 > "remaining_filelist"
  }
}
END   { print download_size / (1024 * 1024) " MiB in " number_of_files " files." > "/dev/stderr" }[/COLOR]
```
[SIZE="4"][COLOR="DarkRed"]**_Experiment 9: Downloading the Selected Files._**[/COLOR][/SIZE]

The list of files that you selected for downloading, is now available in the *&#8220;download_filelist.&#8221;* To actually download them, you will use the *&#8220;wget&#8221;* utility&#8212;which is described in its *&#8220;man&#8221;* page as *&#8220;the non-interactive network downloader.&#8221;*

In general terms, you pass the *&#8220;wget&#8221;* utility a list of files (such as your *&#8220;download_filelist&#8221;*), and supply it with a set of options to adapt its behaviour to your expectations.

Obviously, you will have to tell the *&#8220;wget&#8221;* program where it should look for the list of files that you want it do download; you can do this with its *&#8220;--input-file&#8221;* option&#8212;like so:
```
[COLOR="Navy"]--input-file=download_filelist[/COLOR]
```
Since the input file contains *relative* paths, you will also have to specify the *base URL* from which the files must be downloaded&#8212;i.e., the URL that must be prepended to the relative paths:
```
[COLOR="Navy"]--base=http://archive.ubuntu.com/ubuntu/[/COLOR]
```
By default, *&#8220;wget&#8221;* will download all files into the *current* directory; if you want to download to a different location, then you will have to specify the target location with the *&#8220;--directory-prefix&#8221;* option&#8212;e.g.:
```
[COLOR="Navy"]--directory-prefix=UbuntuSources[/COLOR]
```
Also, by default, *&#8220;wget&#8221;* will download all files directly to the target location, and it will ***not*** create a directory *hierarchy.* Assume, for instance, that the input file contains the following line:
```
[COLOR="Navy"]*pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu17.tar.gz*[/COLOR]
```
The *&#8220;ia32-libs_2.7ubuntu17.tar.gz&#8221;* file will then be downloaded directly into the target location (e.g., *&#8220;UbuntuSources&#8221;*)&#8212;***not*** into its *&#8220;pool/universe/i/ia32-libs&#8221;* subdirectory.

If you *do* want *&#8220;wget&#8221;* to create subdirectories at the target location, then you will have to specify the *&#8220;--force-directories&#8221;* option:
```
[COLOR="Navy"]--force-directories[/COLOR]
```
However, the directory hierarchy created by *&#8220;wget&#8221;* will, then, start at the *host name* from which you download; in other words, the program will download all files into an *&#8220;archive.ubuntu.com&#8221;* subdirectory tree; if you do *not* want this *host name* directory, then you should use the *&#8220;--no-host-directories&#8221;* option:
```
[COLOR="Navy"]--no-host-directories[/COLOR]
```
This time, however, the directory hierarchy will start at the first level *following* the *host name*&#8212;i.e., at the *&#8220;ubuntu&#8221;* directory. If you want to skip this level as well, and you want the directory hierarchy to start one level deeper (i.e., at the *&#8220;pool&#8221;* level), then you will have to use the *&#8220;--cut-dirs&#8221;* option, with the number of levels that you want to skip&#8212;i.e., *&#8220;1&#8221;*&#8212;as its argument value:
```
[COLOR="Navy"]--cut-dirs=1[/COLOR]
```
One further option that you may find useful, is *&#8220;--no-clobber&#8221;*:
```
[COLOR="Navy"]--no-clobber[/COLOR]
```
With this option, *&#8220;wget&#8221;* will refuse to download a file that already exists at the target location; thus, if you accidentally pass *&#8220;wget&#8221;* the same set of file names twice, then the second run will not redownload all the files that you have already gotten.

[INDENT]**_Caveat:_**

[INDENT]If any file gets downloaded only partially, or incorrectly, but you still want to specify the *&#8220;--no-clobber&#8221;* option when you subsequently retry the download, then you will first have to *manually* remove the file. Otherwise, the *&#8220;--no-clobber&#8221;* option will prevent it from being redownloaded.[/INDENT][/INDENT]

With this discussion out of the way, here&#8217;s what the resulting *&#8220;wget&#8221;* command line comes to look like:
```
wget --input-file=download_filelist   \
   --base=http://archive.ubuntu.com/ubuntu/   \
   --directory-prefix=UbuntuSources   \
   --force-directories --no-host-directories --cut-dirs=1   \
   --no-clobber
```
Note that *&#8220;wget&#8221;* will display a nice progress indicator, to show you how the download is proceeding.

[SIZE="4"][COLOR="DarkRed"]**_Experiment 10: Verifying the Checksums of the Downloaded Files._**[/COLOR][/SIZE]

Once the download completes, you can use the *&#8220;md5sum&#8221;* utility to verify if the checksums of the downloaded files match. Just specify the *&#8220;checksum_filelist&#8221;* on the *&#8220;-c&#8221;* option of the *&#8220;md5sum&#8221;* command&#8212;as follows:
```
md5sum -c checksum_filelist
```
If all files were downloaded without errors, then the output from the *&#8220;md5sum&#8221;* utility will look like this:
```
[COLOR="Navy"]UbuntuSources/pool/universe/n/nexuiz-data/nexuiz-data_2.5.2.orig.tar.gz: OK
UbuntuSources/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu17.tar.gz: OK
UbuntuSources/pool/main/o/openoffice.org/openoffice.org_3.1.1.orig.tar.gz: OK
UbuntuSources/pool/multiverse/s/sauerbraten-data/sauerbraten-data_0.0.20090504.orig.tar.gz: OK
UbuntuSources/pool/universe/o/openarena-data/openarena-data_0.8.1.orig.tar.gz: OK
UbuntuSources/pool/universe/o/opencv/opencv_1.0.0.orig.tar.gz: OK
UbuntuSources/pool/universe/libe/libemail-localdelivery-perl/libemail-localdelivery-perl_0.217.orig.tar.gz: OK[/COLOR]
```
If the checksum for any file does not match, then the file must have been downloaded with errors; *&#8220;md5sum&#8221;* will report this condition as follows:
```
[COLOR="Navy"]UbuntuSources/pool/universe/n/nexuiz-data/nexuiz-data_2.5.2.orig.tar.gz: FAILED[/COLOR]
```
To correct this error, you will have to try and redownload the file&#8212;but do remember the *caveat* about the *&#8220;--no-clobber&#8221;* option, above.

Finally, if any file simply could not be downloaded at all, then *&#8220;md5sum&#8221;* will output the following error messages:
```
[COLOR="Navy"]md5sum: UbuntuSources/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu17.tar.gz: No such file or directory
UbuntuSources/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu17.tar.gz: FAILED open or read[/COLOR]
```
If the *&#8220;md5sum&#8221;* encounters any errors, then it will terminate with a summary text like the following:
```
[COLOR="Navy"]md5sum: WARNING: 1 of 7 listed files could not be read
md5sum: WARNING: 1 of 6 computed checksums did NOT match[/COLOR]
```
[SIZE="4"][COLOR="DarkRed"]**_Epilogue: What&#8217;s Next?_**[/COLOR][/SIZE]

You have now successfully downloaded an initial subset of files from the online software archive.

To continue, you may want to select the next subset from the list of files that you saved to the *&#8220;remaining_filelist.&#8221;* You could, for example, replace your original *&#8220;master_filelist&#8221;* with this shorter list, as follows:
```
mv remaining_filelist master_filelist
```
This command moves (or renames) the source file, *&#8220;remaining_filelist,&#8221;* to the target, *&#8220;master_filelist&#8221;*; if the target file already exists *(as is the case in this instance)*, then it will simply be overwritten without warning.

You can subsequently return to [COLOR="DarkRed"]***Experiment 6, 7,***[/COLOR] or [COLOR="DarkRed"]***8***[/COLOR] to select the next batch of files to download.

Alternatively, you can now run the *&#8220;debmirror&#8221;* utility *for real,* and let it download all remaining files from the repository&#8212;e.g.:
```
debmirror --progress \
   --method=http --host=archive.ubuntu.com --root=ubuntu \
   --dist=karmic,karmic-security,karmic-updates \
   --section=main,multiverse,restricted,universe \
   --arch=none \
   ~/UbuntuSources
```
In fact, after you finish downloading all the subsets that you wanted to select, you will have to run this *&#8220;debmirror&#8221;* command just once&#8212;if only to get the control files in place.

[SIZE="4"][COLOR="DarkRed"]**_Final Notes._**[/COLOR][/SIZE]

If you followed along with this post, then it introduced you to some of the incredibly powerful features that any Linux (or Unix) system provides&#8212;such as, *regular expressions,* the *&#8220;grep&#8221;* and *&#8220;awk&#8221;* commands, etc.&#8212;and you learned how they can help you select exactly which files you want to download from an online software repository.

Obviously, much more can be said about these features; if you want to study them further, then the [COLOR="DarkRed"]***&#8220;References&#8221;***[/COLOR] section, below, is an excellent place to start.

There&#8217;s one closely related utility that this post did not discuss: the stream editor, *&#8220;sed.&#8221;* In fact, conventional wisdom has it that there&#8217;s a natural learning sequence that begins with *&#8220;grep,&#8221;* then moves on to *&#8220;sed,&#8221;* and only then arrives at *&#8220;awk.&#8221;* In the context of this post, however, there was no need to talk about *&#8220;sed,&#8221;* and the post is more than long enough already without it. Even so, if you want to become really proficient at the text processing tools available with Unix-like systems, you will certainly encounter the stream editor sooner or later.

[SIZE="4"][COLOR="DarkRed"]**_References._**[/COLOR][/SIZE]

[LIST][*][How to make your own Ubuntu Repository DVDs]("http://ubuntuforums.org/showthread.php?p=2100699#post2100699")&#8212;the initial post in this thread, by **BobSongs.**
[*][How to get "debmirror" to download and validate the "Release.gpg" file]("http://ubuntuforums.org/showthread.php?p=7367273#post7367273")&#8212;one of my earlier posts in this thread.
[*][How to Create a "Source-Only" Local Mirror]("http://ubuntuforums.org/showthread.php?p=7547157#post7547157")&#8212;another one of my earlier posts in this thread.
[*][SecureApt&#8212;Debian Wiki.]("http://wiki.debian.org/SecureApt")
[*][Learning the bash Shell]("http://oreilly.com/catalog/9780596009656"), written by [Cameron Newham]("http://www.oreillynet.com/pub/au/304") and [Bill Rosenblatt]("http://www.oreillynet.com/pub/au/305"), and published by [O&#8217;Reilly Media]("http://oreilly.com").
[*][sed & awk]("http://oreilly.com/catalog/9781565922259"), written by [Dale Dougherty]("http://www.oreillynet.com/pub/au/26") and [Arnold Robbins]("http://www.oreillynet.com/pub/au/459"), also published by [O&#8217;Reilly Media]("http://oreilly.com").
[*][Regular Expression Recipes: A Problem-Solution Approach]("http://www.apress.com/book/view/159059441X"), written by [Nathan A. Good]("http://www.nathanagood.com/Welcome.html"), and published by [Apress]("http://www.apress.com").
[*][A Practical Guide to Ubuntu Linux]("http://www.sobell.com/UB2/index.html"), written by [Mark G. Sobell]("http://www.sobell.com/other/bio.html"), and published by [Prentice Hall]("http://www.informit.com/imprint/index.aspx?st=61089")&#8212;specifically, Chapter 5, *&#8220;The Linux Utilities,&#8221;* Chapter 7, *&#8220;The Shell,&#8221;* Chapter 9, *&#8220;The Bourne Again Shell,&#8221;* and Appendix A, *&#8220;Regular Expressions.&#8221;*
[*][The "more" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?more").
[*][The "less" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?less").
[*][The "find" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?find").
[*][The "wc" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?wc").
[*][The "sort" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?sort").
[*][The "cat" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cat").
[*][The "xargs" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?xargs").
[*][The "grep" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?grep").
[*][The "sed" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?sed").
[*][The "awk" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?awk").
[*][The "head" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?head").
[*][The "tail" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?tail").
[*][The "wget" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?wget").
[*][The "md5sum" man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?md5sum").
[*]Your *local* man pages&#8212;which you can view with the *&#8220;man&#8221;* command (e.g., *&#8220;man more&#8221;*&#8212;*&#8220;man less&#8221;*&#8212;etc.&#8212;and even *&#8220;man man&#8221;*).
[*][Prefixes for binary multiples]("http://physics.nist.gov/cuu/Units/binary.html").
[*][Unix Humour]("http://it.toolbox.com/blogs/bsd-guru/unix-humour-15908").[/LIST]

---

### Post by BobSongs on 2010-02-16
**luvr**

I thank you for each and every one of your posts. You've proven your skill and each of your posts is very well thought-out.

Thank you for adding to the credibility and the strength of this thread.

:)

---

### Post by luvr on 2010-02-17
Heh... I've just noticed that this thread got named [Tutorial of the Week on September 7th, 2009.]("http://ubuntuforums.org/showthread.php?p=7905063#post7905063")

And here I was, thinking that this was far too exotic a topic to be appreciated by *“the world at large...”*

---

### Post by BobSongs on 2010-02-21
> **luvr said:**
> Heh... I've just noticed that this thread got named [Tutorial of the Week on September 7th, 2009.]("http://ubuntuforums.org/showthread.php?p=7905063#post7905063")

And here I was, thinking that this was far too exotic a topic to be appreciated by *“the world at large...”*
I didn't know that this thread won! lol I actually checked for a while and ... gave up looking, figuring it would be ... as you said: **far too exotic**. It's not like we're setting up DVD drivers or some super cool utility.

Thanks for noting the Tutorial of the Week award. I am very pleased that this collaborative effort was selected. Feel free to continue adding more content, as you have. I'll note your latest addition in the first post.

Regards

---

### Post by wyrdrat on 2010-04-23
Further to the problem raised with karmic

> [FONT=Verdana] Sensiva reports that **9.10 Karmic Koala** has an issue with this, stemming from a bug in apt:[/FONT]

I recently asked a question in these forums on this topic and, on advice, submitted a bug report.  Only afterwards did I find this thread while searching for something else.  Just to let people know that if they purchase the 10 DVD set of Ubuntu 9.10 Karmic they will also encounter the apt bug whereby you are constantly swapping disks after each file instead of it getting everything from each disk at a time.  So it seems there is no way to get a workable set of DVDs to install Karmic to offline computers.  Unless anyone knows of a fix for it?

Otherwise, this is a useful tut, just not for Karmic. :(

---

### Post by Sensiva on 2010-04-23
> **wyrdrat said:**
> So it seems there is no way to get a workable set of DVDs to install Karmic to offline computers.  Unless anyone knows of a fix for it?

Otherwise, this is a useful tut, just not for Karmic. :(

Since you already purchased the DVDs, then you have done the most hard work, all you have to do is extracting those DVDs into a directory, Then run debmirror directing it to that directory, it won't download more than 100MB of files, then point apt-get sources.list to that directory and you are done. Doing this on an external USB drive is a good idea, this is how I do it btw.

Good Luck
:D
/**Sensiva**>

---

### Post by wyrdrat on 2010-04-23
Thanks very much for the helpful advice.

Do you think they'll bother to fix apt for Karmic?

Does anyone know if the DVDs or this tutorial work in Lucid yet?

---

### Post by k3lt01 on 2010-04-23
> **wyrdrat said:**
> Do you think they'll bother to fix apt for Karmic?Not with Lucid, an LTS version, coming out in a week.

> **wyrdrat said:**
> Does anyone know if the DVDs or this tutorial work in Lucid yet?I'm sure it will work but its not worth your time starting on Lucid just yet as the repositories are not in final until the full release is made. Any updates made, and yes there can be security updates, will make the initial release versions different to what is available now.

---

### Post by wyrdrat on 2010-05-02
Following Sensiva's advice this is what I did:

Created a directory on the hard disk (you will need about 32GB) called karmicrepository and created subdirectories called main1 - main3, multi1 - multi6, uni1 - uni6 etc.  I then copied all the folders from the pool directory of each DVD into the hard drive directories.  I used the command line tool in terminal

```
cp -R /cdrom/pool/main /karmicrepository/main1
```I found that copying and pasting in Dolphin missed some files.  I then created a Packages.gz file by typing into terminal, having navigated to the karmicrepository directory

```
apt-ftparchive packages ./ ¦ gzip > Packages.gz
```I then opened /etc/apt/sources.list and typed in:

deb file:/karmicrepository ./

Then in terminal:

```
apt-get update
```Now I can use the repository properly.

I know this is the reverse of this tutorial, but I thought it might help anyone who purchased DVDs for Karmic and are unable to use them because of the bug in apt and who do not have an internet connection to the computer they are installing it to.  Of course this doesn't help if you don't have a spare 32gb on your hard drive ...

Incidentally, has anyone tried the Lucid DVDs?  Has the apt bug been fixed?

---

### Post by badman35 on 2010-06-10
BOB why you put 8.04 in the classic RED it still has a good year left in the world??

---

### Post by k3lt01 on 2010-06-10
Probably because it is now an older LTS and Lucid is the main, infact the only, version that is available for download off Ubuntu.com.

Strictly speaking even Dapper is still available as its server support goes for another 12 months. Also if you take a close look at Bobs list it does say 2011 not 2010.

---

### Post by justwarm on 2010-06-23
i am downloading full lucid repository . but when it is become 27.3 gb downloaded it is giving me this message - "tkbros@tkbros-desktop:~$ debmirror --nosource -m --passive --host=in.archive.ubuntu.com --root=ubuntu/ --method=http --progress --dist=lucid,lucid-security,lucid-updates,lucid-backports, --section=main,restricted,universe,multiverse --arch=i386 "/win/softwares2/ubuntu repository's full final" --ignore-release-gpg --timeout=seconds -t 1024 --progress
Mirroring to /win/softwares2/ubuntu repository's full final from [http://in.archive.ubuntu.com/ubuntu//](http://in.archive.ubuntu.com/ubuntu//)
Arches: i386
Dists: lucid,lucid-security,lucid-updates,lucid-backports
Sections: main,restricted,universe,multiverse
Pdiff mode: use
Checking md5sums.
Passive mode on.
Will clean up AFTER mirroring.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/lucid/Release... ok
[0%] Getting: dists/lucid/Release.gpg... ok
gpgv: keyblock resource `/home/tkbros/.gnupg/trustedkeys.gpg': file open error
gpgv: Signature made &#2476;&#2499;&#2489;&#2488;&#2509;&#2474;&#2468;&#2495;&#2476;&#2494;&#2480; 29  using DSA key ID 437D05B5
[GNUPG:] ERRSIG 40976EAF437D05B5 17 2 00 1272561907 9
[GNUPG:] NO_PUBKEY 40976EAF437D05B5
gpgv: Can't check signature: public key not found
Release signature does not verify.
Ubuntu Release file: using Suite (lucid).
[0%] Getting: dists/lucid-security/Release... ok
[0%] Getting: dists/lucid-security/Release.gpg... ok
gpgv: keyblock resource `/home/tkbros/.gnupg/trustedkeys.gpg': file open error
gpgv: Signature made &#2478;&#2457;&#2509;&#2455;&#2482;&#2476;&#2494;&#2480; 22 &#2460;&#2497;&#2472; 2010 01:35 using DSA key ID 437D05B5
[GNUPG:] ERRSIG 40976EAF437D05B5 17 2 00 1277150754 9
[GNUPG:] NO_PUBKEY 40976EAF437D05B5
gpgv: Can't check signature: public key not found
Release signature does not verify.
Ubuntu Release file: using Suite (lucid-security).
[0%] Getting: dists/lucid-updates/Release... ok
[0%] Getting: dists/lucid-updates/Release.gpg... ok
gpgv: keyblock resource `/home/tkbros/.gnupg/trustedkeys.gpg': file open error
gpgv: Signature made &#2478;&#2457;&#2509;&#2455;&#2482;&#2476;&#2494;&#2480; 22 &#2460;&#2497;&#2472; 2010 01:59 using DSA key ID 437D05B5
[GNUPG:] ERRSIG 40976EAF437D05B5 17 2 00 1277195368 9
[GNUPG:] NO_PUBKEY 40976EAF437D05B5
gpgv: Can't check signature: public key not found
Release signature does not verify.
Ubuntu Release file: using Suite (lucid-updates).
[0%] Getting: dists/lucid-backports/Release... ok
[0%] Getting: dists/lucid-backports/Release.gpg... ok
gpgv: keyblock resource `/home/tkbros/.gnupg/trustedkeys.gpg': file open error
gpgv: Signature made &#2476;&#2497;&#2471;&#2476;&#2494;&#2480; 23 &#2460;&#2497;&#2472; 2010 01:57:36  using DSA key ID 437D05B5
[GNUPG:] ERRSIG 40976EAF437D05B5 17 2 00 1277238456 9
[GNUPG:] NO_PUBKEY 40976EAF437D05B5
gpgv: Can't check signature: public key not found
Release signature does not verify.
Ubuntu Release file: using Suite (lucid-backports).
Get Packages and Sources files and other miscellany.
Parse Packages and Sources files and add to the file list everything therein.
Download all files that we need to get (7100 MiB).
Get package files.
[  0%] Getting: pool/universe/o/ocamlagrep/libagrep-ocaml-dev_1.0-11build1_i386.deb... Can't write to 'pool/universe/o/ocamlagrep/libagrep-ocaml-dev_1.0-11build1_i386.deb-2075': Input/output error at /usr/share/perl5/LWP/Protocol.pm line 105. at /usr/share/perl5/LWP/UserAgent.pm line 844.
WARNING: releasing 1 pending lock..."
 so , i can't continue my download. please help me.

---

### Post by Sensiva on 2010-06-23
debmirror has changed, it verifies the Release file using GPG keys

To continue your download you should add this key ID 437D05B5 to your systemby excuting this command in terminal.
```

gpg --no-default-keyring --keyring trustedkeys.gpg --keyserver keyring.ubuntu.com --recv-keys 437D05B5

```That key ID is mentioned in the error message. Now you can resume downloading.

Please BoB add this to your marvelous tutorial.

Thanks
/**Sensiva**>

---

### Post by justwarm on 2010-06-23
thank you very much. sensiva, 
but after entering the code it is showing 
"tkbros@tkbros-desktop:~$ gpg --no-default-keyring --keyring trustedkeys.gpg --keyserver keyring.ubuntu.com --recv-keys 437D05B5
gpg: directory `/home/tkbros/.gnupg' created
gpg: new configuration file `/home/tkbros/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/tkbros/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/tkbros/.gnupg/secring.gpg' created
gpg: keyring `/home/tkbros/.gnupg/trustedkeys.gpg' created
gpg: requesting key 437D05B5 from hkp server keyring.ubuntu.com
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'keyring.ubuntu.com'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0"
so, it is not working .

---

### Post by k3lt01 on 2010-06-23
> **Sensiva said:**
> debmirror has changed, it verifies the Release file using GPG keysSensiva, I have come across this gpg key error with all of my various downloads and it doesn't shut it down. Using the "--ignore-release-gpg" argument which he has wont fail a download if there is a problem in the gpg key

I think the problem is shown with these lines instead.

> **justwarm said:**
> Get Packages and Sources files and other miscellany.
Parse Packages and Sources files and add to the file list everything therein.
Download all files that we need to get (7100 MiB).
Get package files.
[  0%] Getting: pool/universe/o/ocamlagrep/libagrep-ocaml-dev_1.0-11build1_i386.deb... Can't write to 'pool/universe/o/ocamlagrep/libagrep-ocaml-dev_1.0-11build1_i386.deb-2075': **Input/output error at /usr/share/perl5/LWP/Protocol.pm line 105. at /usr/share/perl5/LWP/UserAgent.pm line 844.**
WARNING: releasing 1 pending lock..."I'd like to see that file and know what is wrong on lines 105 and  844.

---

### Post by justwarm on 2010-06-23
here is those files in the  LWP.tar.gz file[ATTACH]161325[/ATTACH]

---

### Post by justwarm on 2010-06-23
so , what should i do now as sensiva's idea also not working.

---

### Post by luvr on 2010-06-23
> **justwarm said:**
> gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
so, it is not working .
In that case, I would create the keyring for *debmirror* from the existing APT keyring, like this:
```
sudo apt-key exportall | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```
If even that doesn't work, then I suggest you open the *"Software Sources"* utility (*"System"* -> *"Administration"* -> *"Software Sources"*), and select the *"Authentication"* tab. Let us know if the key that *debmirror* is looking for, can be found there.

> **k3lt01 said:**
> Using the "--ignore-release-gpg" argument which he has, won't fail a download if there is a problem in the gpg key

I think I'm with **k3lt01** on this one: The *"--ignore-release-gpg"* option should ignore the GPG key.

This may seem like a wild guess, but my first suspicion when getting an error saying
> **justwarm said:**
> Can't write to 'pool/universe/o/ocamlagrep/libagrep-ocaml-dev_1.0-11build1_i386.deb-2075': Input/output error at /usr/share/perl5/LWP/Protocol.pm line 105. at /usr/share/perl5/LWP/UserAgent.pm line 844.
would be a disk-full condition. Does that seem plausible?

---

### Post by mrprowse on 2010-06-23
> **luvr said:**
> In that case, I would create the keyring for *debmirror* from the existing APT keyring, like this:
```
sudo apt-key exportall | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```


Thanks luvr, that fixed the problem for me.

I think the problem was that I was behind a proxy that wasn't letting the hkp://keyserver.ubuntu.com request go through, but I'm not sure.

---

### Post by justwarm on 2010-06-23
yes. i found that key in software sources.
but my disk is not full. there is till now 17.8 gb is free.

---

### Post by luvr on 2010-06-23
> **justwarm said:**
> yes. i found that key in software sources.
but my disk is not full. there is till now 17.8 gb is free.
OK—But then, did you run this command line:
```
sudo apt-key exportall | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```
If so, did it work? Does your *debmirror* command work after that?

---

### Post by k3lt01 on 2010-06-23
> **justwarm said:**
> yes. i found that key in software sources.
but my disk is not full. there is till now 17.8 gb is free.You may have that much left in free space but if I remember correctly Linux leaves a certain percentage so it can work on the file system. So if you have a 200gb disk and you now have only 17.8gb free the disk would "appear" full.

It is strange to me that this is something that has only just occurred. Files contained in / don;t just change themselves so I am leaning towards a full disk scenario like luvr.

Unfortunately I have a full day today and it is 5,45am right now. I will check your attachment when I can later today or tomorrow if your problem isn't fixed yet.

---

### Post by luvr on 2010-06-23
> **justwarm said:**
> but my disk is not full. there is till now 17.8 gb is free.
Just to double-check: I notice that you are downloading into some *“/win”* directory tree—which I would guess is a Windows disk, right? Are you sure, then, that **that** isn't full, either?

---

### Post by k3lt01 on 2010-06-23
> **justwarm said:**
> here is those files in the  LWP.tar.gz file[ATTACH]161325[/ATTACH]

Line 105 of Protocol.pm is
```
            [COLOR="Pink"]open(my $fh, "[/COLOR][COLOR="Red"]>[/COLOR][COLOR="Pink"]",[/COLOR] [COLOR="Lime"]$arg[/COLOR][COLOR="Pink"]) or die "[/COLOR][COLOR="Black"]Can[/COLOR][COLOR="Pink"]'t write to '[/COLOR][COLOR="Lime"]$arg[/COLOR][COLOR="Pink"]': $!";[/COLOR]
``` Now if you take a look at it in the actual file the word "Can't" appears to have a problem (i.e. "Can" is in black while "'t" is in pink. From my limited knowledge of scripting when a line, or word, takes on a colour unless there is an "argument" to change it and that cannot happen part way through a word.

Line 841-844 of UserAgent.pm is
```
    my $response = $self->request($request, $tmpfile);
    if ( $response->header('X-Died') ) {
	die $response->header('X-Died');
```
Looking at the last line and comparing it to the line above, again from my limited knowledge of scripting, the last line is missing a ( before the $response and a )  after the '). Please also note the spacing.

I must say that I am just taking a guess here.

---

### Post by justwarm on 2010-06-24
> **luvr said:**
> OK&#8212;But then, did you run this command line:
```
sudo apt-key exportall | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```If so, did it work? Does your *debmirror* command work after that?


thanks luvr. after entering that code in terminal debmiror goes ok. now my problem is solved.
      thank you again.
 & i also wnats to thanks everyone who also tried to help me.

---

### Post by luvr on 2010-06-24
> **k3lt01 said:**
> You may have that much left in free space but if I remember correctly Linux leaves a certain percentage so it can work on the file system. So if you have a 200gb disk and you now have only 17.8gb free the disk would "appear" full.
You're certainly right that Linux reserves a percentage of the space for system work, but I think that this system-reserved space will be counted as *"in use,"* not as *"free."*

So, in my opinion, if the system tells you that it has 17.8 GB free, then that's 17.8 GB free for you to use, **not** 17.8 GB minus the system-reserved space.

---

### Post by Sensiva on 2010-06-24
Please read that bug [https://bugs.launchpad.net/ubuntu/+source/debmirror/+bug/368949](https://bugs.launchpad.net/ubuntu/+source/debmirror/+bug/368949)

Thanks

---

### Post by k3lt01 on 2010-06-24
I read it and can categorically state that it is not a problem for everyone. It does not affect my system in the way that bug describes. You may also note, you will have to read back through this thread to see it again, that I have played with both debmirror_20070123ubuntu1 and debmirror_20070123ubuntu3 and have never come across the issue described by you or the bug reports OP. I do get the "can't find release gpg" but the download continues as it should in very other manner.

I'm not saying it doesn't exist, although I agree with Rees Cook's marking as invalid even after you reopened it from that state, as very little information exists to help others duplicate it. I think that a little bit more detective work is in order on that bug, and not having it I can't do any, to see why it appears to be a problem on so few a number of systems.

---

### Post by Sensiva on 2010-06-25
It is not on few systems, it happens even on a fresh installs of Ubuntu OS, I used to use debmirror from debian box by copying it into /usr/bin, but since Karmic, debian's version of debmirror has changed as will.

Anyway my debmirror version is 1:2.4.4ubuntu2(lucid)
d726ac4a49729a360dff26082e72c221  /usr/bin/debmirror

Thank you

---

### Post by k3lt01 on 2010-06-25
> **Sensiva said:**
> It is not on few systems, it happens even on a fresh installs of Ubuntu OS,Lets not turn this into a semantic debate.

What I am saying is that the bug report has only 2 confirmed cases that do not complete a download as it should, compare that to the number of people who use debmirror and it is only a few systems. My systems work as they did before except that I get a warning about gpg key yet the systems still download as they should with no difficulty.

> **Sensiva said:**
>  I used to use debmirror from debian box by copying it into /usr/bin, but since Karmic, debian's version of debmirror has changed as will.That will probably be because Debian and Ubuntu devs are often, not always, one and the same person.

May I respectfully suggest you and our new friend do a little detective work and try to add more to the bug report because as it is you are 1 of 3 people that we know of who have this issue. If it is to be fixed properly those that have it will need to help others who don't try to fix it.

---

### Post by Sensiva on 2010-06-25
I will revise again the new man pages of debmirror and do some testing and get back to you.

Btw I am not debating at all, I am just sharing all info I have gathered around so we can come up with a reasonable conclusion :D

Thank you

---

### Post by justwarm on 2010-06-26
I have completely downloaded lucid repository from archive.ubuntu.com  ( it is about 32.8 gb ). so i want to burn it in 8.5 gb dual layer dvds. so can you tell me the code by which i can do that. and how many 8.5 gb dual layer dvds i need as i don't know how much i can write on 8.5 gb dvd .(as i can write maximum 4.4 gb in a 4.7 gb dvd )

---

### Post by justwarm on 2010-06-26
> **luvr said:**
> OK—But then, did you run this command line:
```
sudo apt-key exportall | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```
If so, did it work? Does your *debmirror* command work after that?

can you tell me what was the wrong . so the download stopped at midway .

---

### Post by luvr on 2010-06-26
> **justwarm said:**
> can you tell me what was the wrong . so the download stopped at midway .
I have no idea what went wrong. It *looks* like there was an input/output error while writing to disk—but I cannot, for the life of me, imagine how that could get solved simply by creating the *“trustedkeys.gpg”* keyring.

Creating that keyring will allow *debmirror* to verify the digital signatures on the repository that you download; the inability to verify the signatures, however, has nothing to do with any input/output error that may occur.

... **Except,** now that I think of it, that there will, obviously, be an error *reading* the keyring if it does not exist (after all, reading a nonexistent file cannot possibly succeed, can it?)—but, if *that* really is the problem, then the error message is awfully wrong, since it claims that the problem is in *writing* the package data file that is being downloaded.

---

### Post by k3lt01 on 2010-06-26
> **justwarm said:**
> I have completely downloaded lucid repository from archive.ubuntu.com  ( it is about 32.8 gb ). so i want to burn it in 8.5 gb dual layer dvds. so can you tell me the code by which i can do that. and how many 8.5 gb dual layer dvds i need as i don't know how much i can write on 8.5 gb dvd .(as i can write maximum 4.4 gb in a 4.7 gb dvd )Unfortunately the answer at this time is you can't burn it to a dual layer dvd. I just went searching for the Man pages and they are non-existant so I opened up the source package and took a look at it and it gives you what options you can use which I shall list here for you.
```
== MEDIATYPE

((*MediaType*)) is alias of an absolute integer value for a media
such as CD, DVD. For example, CD74 MediaType is an alias of the absolute
size of 74min CD. debpartial has the following built-in MediaTypes:

(1)FD      - 2HD 1.44M Floppy Disk
(1)CF8     - 8M Compact Flash
(1)CF16    - 16M Compact Flash
(1)CF32    - 32M Compact Flash
(1)CF64    - 64M Compact Flash
(2)MO128   - 128M MO
(3)MO230   - 230M MO
(4)MO640   - 640M MO
(6)CD74    - 74min (650M) CD
(7)CD80    - 80min (700M) CD
(5)MO1.3G  - 1.3G MO
(5)DVD-RAM - (2.6G) DVD-RAM
(8)DVD     - Single Layer (4.7G) DVD-ROM

Each absolute value is 93% of theoretical value because fixed cluster
(or block) size may make the space of written files grow up.
This calculation isn't a perfect solution, but mostly works.
```
Wouldn't it be great if we could work on debmirror so we could get it to burn Blu-Ray disks, you would only need 2 of them. As it is I have all of mine of a 500gb Seagate External hard drive so I don't need disks anymore.

EDIT:Well it seems we may have a way around your little dilemma. You will have to download the source package and adjust at last one parameter. The list above shows what is written into the ruby script as options, down further is where the options are actually formalised in the script.
```
# Media name to maximum size map
#
# SAFE_SPACE is a rate for going down maximum size because fixed
# cluster (block) size may make the space of written files
# grow up.
#
# CD size is caluclated as follows:
#
#
#  74min CD -> ((74m * 60)s * 75) * 2048 (CD-ROM Mode 2, XA Form 1/CD-I)
#  80min CD -> (((79m * 60)s * 75)+(57s * 75) + 74
#                                 * 2048 (CD-ROM Mode 2, XA Form 1/CD-I)
#              (i.e 79m57s74)
#
# A Block can take up 1/75 sec. of audio data, i.e. on a 74 minute CD
# there are 74*60*75=333000 blocks.
#
#
SAFE_SPACE=0.93
SIZEMAP = {
  "FD" => 1440000, 
  "CF8" => 8 * 1024 * 1024,
  "CF16" => 16 * 1024 * 1024,
  "CF32" => 32 * 1024 * 1024,
  "CF64" => 64 * 1024 * 1024,
  "MO128" => 128 * 1024 * 1024,
  "MO230" => 230 * 1024 * 1024,
  "MO640" => 640 * 1024 * 1024,
  "MO1.3G" => 1300 * 1024 * 1024,
  "CD74" => (74 * 60 * 75 * 2048),
  "CD80" => ((79 * 60 * 75) + (57 * 75) + 74) * 2048,
  "DVD-RAM" => 2600000000,
  "DVD"   => 4700000000
}
```Now you need to adjust it so it can burn a dual layer so below the last entry you want it to look like this
```

  "DVD-RAM" => 2600000000,
  "DVD"   => 4700000000,
  "DVD-DL"   => 8500000000
```save it and compile the source. In part 4 of Bobsongs tutorial change th size from DVD to DVD-DL and it will probably work (I wont promise it). You will probably have to add this to the media type in the first code box so make it 
```
(8)DVD     - Single Layer (4.7G) DVD-ROM
(9)DVD-DL  - Dual Layer (8.5G) DVD-ROM
```

---

### Post by luvr on 2010-06-26
> **k3lt01 said:**
> I just went searching for the Man pages and they are non-existant
Apparently, there *does* exist a man page for debpartial—but it is pretty hard to find. It took me a while to find it, but here it is: [*“Digipedia.pl » Manual Linux » debpartial (1)”*]("http://www.digipedia.pl/man/doc/view/debpartial.1/")

According to the man page, you can specify a *“--size”* parameter, instead of a media type; in fact, the media types are simply synonyms for the corresponding size values.

---

### Post by k3lt01 on 2010-06-26
See my edit above

---

### Post by justwarm on 2010-06-27
> **k3lt01 said:**
> Unfortunately the answer at this time is you can't burn it to a dual layer dvd. I just went searching for the Man pages and they are non-existant so I opened up the source package and took a look at it and it gives you what options you can use which I shall list here for you.
```
== MEDIATYPE

((*MediaType*)) is alias of an absolute integer value for a media
such as CD, DVD. For example, CD74 MediaType is an alias of the absolute
size of 74min CD. debpartial has the following built-in MediaTypes:

(1)FD      - 2HD 1.44M Floppy Disk
(1)CF8     - 8M Compact Flash
(1)CF16    - 16M Compact Flash
(1)CF32    - 32M Compact Flash
(1)CF64    - 64M Compact Flash
(2)MO128   - 128M MO
(3)MO230   - 230M MO
(4)MO640   - 640M MO
(6)CD74    - 74min (650M) CD
(7)CD80    - 80min (700M) CD
(5)MO1.3G  - 1.3G MO
(5)DVD-RAM - (2.6G) DVD-RAM
(8)DVD     - Single Layer (4.7G) DVD-ROM

Each absolute value is 93% of theoretical value because fixed cluster
(or block) size may make the space of written files grow up.
This calculation isn't a perfect solution, but mostly works.
```Wouldn't it be great if we could work on debmirror so we could get it to burn Blu-Ray disks, you would only need 2 of them. As it is I have all of mine of a 500gb Seagate External hard drive so I don't need disks anymore.

EDIT:Well it seems we may have a way around your little dilemma. You will have to download the source package and adjust at last one parameter. The list above shows what is written into the ruby script as options, down further is where the options are actually formalised in the script.
```
# Media name to maximum size map
#
# SAFE_SPACE is a rate for going down maximum size because fixed
# cluster (block) size may make the space of written files
# grow up.
#
# CD size is caluclated as follows:
#
#
#  74min CD -> ((74m * 60)s * 75) * 2048 (CD-ROM Mode 2, XA Form 1/CD-I)
#  80min CD -> (((79m * 60)s * 75)+(57s * 75) + 74
#                                 * 2048 (CD-ROM Mode 2, XA Form 1/CD-I)
#              (i.e 79m57s74)
#
# A Block can take up 1/75 sec. of audio data, i.e. on a 74 minute CD
# there are 74*60*75=333000 blocks.
#
#
SAFE_SPACE=0.93
SIZEMAP = {
  "FD" => 1440000, 
  "CF8" => 8 * 1024 * 1024,
  "CF16" => 16 * 1024 * 1024,
  "CF32" => 32 * 1024 * 1024,
  "CF64" => 64 * 1024 * 1024,
  "MO128" => 128 * 1024 * 1024,
  "MO230" => 230 * 1024 * 1024,
  "MO640" => 640 * 1024 * 1024,
  "MO1.3G" => 1300 * 1024 * 1024,
  "CD74" => (74 * 60 * 75 * 2048),
  "CD80" => ((79 * 60 * 75) + (57 * 75) + 74) * 2048,
  "DVD-RAM" => 2600000000,
  "DVD"   => 4700000000
}
```Now you need to adjust it so it can burn a dual layer so below the last entry you want it to look like this
```

  "DVD-RAM" => 2600000000,
  "DVD"   => 4700000000,
  "DVD-DL"   => 8500000000
```save it and compile the source. In part 4 of Bobsongs tutorial change th size from DVD to DVD-DL and it will probably work (I wont promise it). You will probably have to add this to the media type in the first code box so make it 
```
(8)DVD     - Single Layer (4.7G) DVD-ROM
(9)DVD-DL  - Dual Layer (8.5G) DVD-ROM
```

If you don't mind can you please create a debcopy for my usage as i am not familiar with these kinds of works .

---

### Post by justwarm on 2010-06-27
> **luvr said:**
> I have no idea what went wrong. It *looks* like there was an input/output error while writing to disk—but I cannot, for the life of me, imagine how that could get solved simply by creating the *“trustedkeys.gpg”* keyring.

Creating that keyring will allow *debmirror* to verify the digital signatures on the repository that you download; the inability to verify the signatures, however, has nothing to do with any input/output error that may occur.

... **Except,** now that I think of it, that there will, obviously, be an error *reading* the keyring if it does not exist (after all, reading a nonexistent file cannot possibly succeed, can it?)—but, if *that* really is the problem, then the error message is awfully wrong, since it claims that the problem is in *writing* the package data file that is being downloaded.

i want to make one thing clear that before getting the answer from you i have copy pasted my entirely downloaded ubuntu repo ina new location. then i run the command again from that location. & it went fine . so , i continued my download from that location instead of previous. 
           after getting your answer i tried that command from previous location and it was downloading chromium browser instead of ocamlagrep . so, i thought that the problem solved but after when i wanted to delete "/win/softwares2/ubuntu repository's full final" folder everything deleted but only the folder named "/win/softwares2/ubuntu repository's full final/pool/universe/o/ocamlagrep" was not deleted there was still showing input/output error. so i think that there is till now some problem so , that i can not able to delete that folder.

---

### Post by k3lt01 on 2010-06-27
> **justwarm said:**
> If you don't mind can you please create a debcopy for my usage as i am not familiar with these kinds of works .If you can be patient I will give it a go and post the .deb file for BobSongs to link to for everyones use. I cannot promise when it will be done but I will certainly give it a go and I will let everyone know when it is done.

---

### Post by k3lt01 on 2010-06-27
> **justwarm said:**
> If you don't mind can you please create a debcopy for my usage as i am not familiar with these kinds of works .

I won't make any guarantees that this will work. I have done some work on debpartial and if, ***_that is IF_***, you are willing to be a guinea pig you can try this to your hearts content. If you do choose to try it I do want you to let me know what happens either good or bad.

Now I have that disclaimer out of the way I shall continue.

I have attached a tar.gz file named "debpartial.tar.gz" to this post.
EDIT: I have removed it from here but
[ [SIZE="3"]**please go to this post for the NEW UPDATED version that also has Blu-Ray compatibility**[/SIZE]]("http://ubuntuforums.org/showpost.php?p=9532875&postcount=365"). Note: While DVD-DL has been tested and is known to work Blu-Ray as yet has not been tested. I do not see any problems arising but if you decide to test Blu-Ray _**you do so at your own risk**_.

Save it to your desktop, extract-untar to your desktop it and put it in your /usr/bin/ folder, you will need sudo rights to do this and it will over-write your original file.

Then when you get to "Part 4. Divide into DVD-sized portions" of Bobsongs original post I need the code to look like this.
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=lucid,lucid-security,lucid-updates,lucid-backports [COLOR="Blue"]**--size=DVD-DL**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```The blue colour is just to highlight the required modification to your code.

As I said I cannot promise this will work. I haven't tried it and I don't have any need to try it, you asked me to modify it for you. If you choose not to try it that's fine I understand completely. I may give it a go one day when I need to.

---

### Post by justwarm on 2010-06-28
> **k3lt01 said:**
> I won't make any guarantees that this will work. I have done some work on debpartial and if, ***_that is IF_***, you are willing to be a guinea pig you can try this to your hearts content. If you do choose to try it I do want you to let me know what happens either good or bad.

Now I have that disclaimer out of the way I shall continue.

I have attached a tar.gz file named "DebpartialForDualLayerDVD.tar.gz" to this post. Inside it is the modified source and the resulting .deb file as well. You will need to unpack the tar.gz with the archive manager and then install the .deb with gdebi by double clicking on it. I have tested its installation and it does work.

Then when you get to "Part 4. Divide into DVD-sized portions" of Bobsongs original post I need the code to look like this.
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=lucid,lucid-security,lucid-updates,lucid-backports [COLOR=Blue]**--size=DVD-DL**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```The blue colour is just to highlight the required modification to your code.

As I said I cannot promise this will work. I haven't tried it and I don't have any need to try it, you asked me to modify it for you. If you choose not to try it that's fine I understand completely. I may give it a go one day when I need to.

thank you very much for your work. but after installing it when i enter the command "debpartial" it is showing that command is not found . so, i have to manually add debpartial script to /usr/bin folder. after doing this this work fine.
   but there is one more problem that it is showing me that i need 5 dual -layer dvd to burn 32.8 gb . and 9 single layer dvds for the same . while it should take 8 dvds . so , is there any problem ?

---

### Post by k3lt01 on 2010-06-28
Thanks for testing this, I will take a look at the bug you found and see what I come up with. I think mine installed ok as I already had the version BobSongs links to and it updated it.

With regards to the 5 DVD-DL compared to the 9 DVD that is all about the "safety" ratio within debpartial. It is set at 93% of actual size, that is why a single layer will work at 4.4gb instead of the 4.7gb really available.

32.8/7.9 = 4.1 DVD-DL disks
32.8/4.4 = 7.45 DVD single layer disks.

I see what you mean, I didn't adjust any settings for the single layer DVD, so I don't know if this is something I have done or if it was already like this. Have you tried the single layer with the old version? What does the old debpartial say it requires?

---

### Post by justwarm on 2010-06-28
> **k3lt01 said:**
> Thanks for testing this, I will take a look at the bug you found and see what I come up with. I think mine installed ok as I already had the version BobSongs links to and it updated it.

With regards to the 5 DVD-DL compared to the 9 DVD that is all about the "safety" ratio within debpartial. It is set at 93% of actual size, that is why a single layer will work at 4.4gb instead of the 4.7gb really available.

32.8/7.9 = 4.1 DVD-DL disks
32.8/4.4 = 7.45 DVD single layer disks.

I see what you mean, I didn't adjust any settings for the single layer DVD, so I don't know if this is something I have done or if it was already like this. Have you tried the single layer with the old version? What does the old debpartial say it requires?


yea. i have also tried the previous version but both is showing same thing . so,i am confused .
according to bobsongs tutorial i need 8 dvds but debpartial is showing me that i need 9 dvds . so , it is creating me a confusion . so, should i continue with debpartial ?

---

### Post by k3lt01 on 2010-06-28
If you want DVD-DL then you will need to use the modified file, if you are happy to go back to DVD single layers then you will end up using one disk more than you need to. It is up to you. Single layer DVDs are cheap to buy, they are in Australia anyway, while DVD-DLs are still quite expensive in comparison.

I must thank you because even though I probably wont use DVD-DLs, I probably wont use single layers either, you have provided me with another project to use as a learning experience. I will keep working on this to get the bug(s) sorted out. If you keep trying DVD-DLs please keep us informed with how you go and I will work on the script from the feedback you provide.

If anyone else has some feedback for me or hints please let me know and I will see what I can do.

If we can get DVD-DLs working properly I will move onto Blu-Rays.

---

### Post by justwarm on 2010-06-28
> **k3lt01 said:**
> If you want DVD-DL then you will need to use the modified file, if you are happy to go back to DVD single layers then you will end up using one disk more than you need to. It is up to you. Single layer DVDs are cheap to buy, they are in Australia anyway, while DVD-DLs are still quite expensive in comparison.

I must thank you because even though I probably wont use DVD-DLs, I probably wont use single layers either, you have provided me with another project to use as a learning experience. I will keep working on this to get the bug(s) sorted out. If you keep trying DVD-DLs please keep us informed with how you go and I will work on the script from the feedback you provide.

If anyone else has some feedback for me or hints please let me know and I will see what I can do.

If we can get DVD-DLs working properly I will move onto Blu-Rays.
i think you can move onto blu-rays as your previous work was succefull. i created 5 dual-layer dvds with your script . but there was only one problem which i have previously said you .
but now i am facing another problem please check this thread  "[http://ubuntuforums.org/showthread.php?p=9521247#post9521247](http://ubuntuforums.org/showthread.php?p=9521247#post9521247) "

---

### Post by justwarm on 2010-06-28
after adding medibuntu and lucid lynx 's repository locally when i update packagelists via synaptic this is giving this error message "W: GPG error: file: lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"
what is the meaning of this & what should i do now ?

---

### Post by luvr on 2010-06-28
> **justwarm said:**
> The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"
You’re missing the Medibuntu key.

You can install it like so:
```
sudo apt-get --allow-unauthenticated install medibuntu-keyring
```
(In fact, you could leave out the *“--allow-unauthenticated”* option, and confirm that it is OK to install the package without authentication when the system asks you.)

Then, refresh your software repository indexes again:
```
sudo apt-get update
```
The message should be gone now.

Also, if you’re using *“debmirror”* to maintain a local mirror of the Medibuntu repository, you will have to update the *“trustedkeys.gpg”* keyring as well. The easiest way to accomplish this, is with the command that I showed you in an earlier post:
```
sudo apt-key exportall | gpg --no-default-keyring --keyring trustedkeys.gpg --import
```

---

### Post by k3lt01 on 2010-06-28
Luvr has got you covered with your other question. His understanding is much better than mine so I will trust what he says without adding anything further.

> **justwarm said:**
> i think you can move onto blu-rays as your previous work was succefull. i created 5 dual-layer dvds with your script . I meant when I can get it to install properly I will go onto Blu-Ray disks. I didn't change anything apart from adding 2 lines so I want to understand why the installation location has changed from /usr/bin/ to /, yes it does install but the location has changed and I didn't ask it to. So once I have that figured out I will move onto Blu-Ray disks.

---

### Post by justwarm on 2010-06-30
how can i merge medibuntu & canonical commercial repo on a single cd ?

---

### Post by k3lt01 on 2010-06-30
Unless you create a new packages.gz file from the merged and renamed repositories you will have great difficulty. In the first post read and follow section 9. You will also want to look at Luvr's thread which BobSongs links to in that section.

---

### Post by justwarm on 2010-06-30
> **jocose said:**
> Thanks to firefox deciding to freeze, I lost my entire re-edit of this post to correct it, so I'm going to be very brief in this re-post re-edit:

If you're unable to follow the brilliant mirroring and backup to DVD option word for word as BobSongs has so kindly written, here is an alternative:

[Warning: Use this information at your own risk, if you mess up your system  or anything bad happens, I take no blame. Understand what you are doing before you do it. Use this method only if you cannot use BobSongs' excellent instructions. Please do not post about this post in this thread. Has this post helped you? I am glad.]

First, bookmark this thread:
[http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)

Download the packages it mentions within, and download the packages mentioned in BobSongs' first post in this thread, then start with Main:

```
debmirror --nosource -m --passive --host=mirror.you.want --root=ubuntu/ --method=http --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main --arch=i386 ~/UbuntuRepos --ignore-release-gpg --timeout=999
```Replace mirror.you.want in the code above with the mirror you wish to use.  I suggest *not* using ubuntu.com to mirror, but instead a mirror closer to you in your country. Please refer to the Launchpad Mirrors of Ubuntu page for a list of mirrors and an update status: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

When you've finished with the instructions below, and you've mirrored Main, moved the debs, deleted the ~/UbuntuRepos directory following the moving of the deb files to another folder you've created, you may start again with another repo and change --section=main to --section=restricted to mirror restricted, and follow the instructions in this post again, rinse and repeat.

After Main is downloaded, we create a folder in ~/ to move the downloaded deb files to, and run this command:

```
find /start/here -name \*.deb -exec mv {} /to/there/ \;
```Replace /start/here with ~/UbuntuRepos and /to/there with the empty folder you've created. This will MOVE all of the deb files you've mirrored from Main into your new folder. Now you will look at the size of the new folder with the debs. Delete ~/UbuntuRepos once you've verified the debs were moved. It won't all fit on one 4.xGB DVD, so create a second folder and go into the first with Nautilus and switch to List view. Highlight the files with the shift key held down to advance more and more until you have enough to fit on one DVD. Now paste these into the other folder you created. Now compare the sizes of each folder, each should be able to fit on a DVD.

Now open the link I posted above and continue with creating an **autorepo** file for *each* folder of debs you have, and run the autorepo file in each, which will generate a package list for each.

Once this is done for each, you may burn each to a separate DVD and add them the same way as BobSongs mentioned, with apt-cdrom add. With each DVD burned, you may delete the new folders you originally created to move the mirrored Main debs to.

Start again with another repo and do one each time until you have all of them individually mirrored, manually split up between folders, autorepo ran in each one, and burned. Do not burn the DVD without first running autorepo and checking each folder for package lists, you need these on the DVD so they will add properly with apt-cdrom add later.

Done!

With this method, I have not tried downloading ALL of the repos at once and splitting them into several DVDs, when I cannot follow BobSongs' method and use debpartial to complete the process, and I have to use the method here I've described in this post, I download one repo at a time. It's a longer process, but it works.

*Optional*: It may be simpler for some to use aptoncd (available in the repos) after you have mirrored an area and moved the debs to one folder, and use aptoncd to generate the package list and create DVD images for you! I posted the manual cut/paste and autorepo method above, referring to another thread because when I tried aptoncd it created a DVD which was slightly above the size of a DVD and all of the burning applications refused to burn it, so I decided to do the manual splitting of deb files into individual folders and generating a package list manually with autorepo as mentioned in the linked thread.

hey . you have given a brilliant idea . but now i want a inverse command of it . i mean i want to restore my .deb packages to previous locations .

---

### Post by justwarm on 2010-06-30
is there any command available to restore .deb packages (which has been divided iinto dvd sizes by debpartial )in thier previous location ?

---

### Post by luvr on 2010-06-30
> **justwarm said:**
> is there any command available to restore .deb packages (which has been divided iinto dvd sizes by debpartial )in thier previous location ?
I may have misunderstood your question, but I believe that what you're trying to do is exactly what I describe in my post on [How to set up a local Ubuntu mirror from a set of Repository DVDs.]("http://ubuntuforums.org/showthread.php?p=7455095#post7455095")

---

### Post by k3lt01 on 2010-06-30
Just finished working on debpartial (the ruby file not the .deb) and added Blu-Ray compatibility. The Blu-Ray, and DVD-Dual Layer, designations and sizes are:```
[COLOR="Blue"]**DVD-DL**[/COLOR] - Dual Layer (8.5G) DVD-ROM Dual Layer
[COLOR="Blue"]**BD**[/COLOR] - Single Layer (25G) BD-ROM Single Layer Blu-ray Disk
[COLOR="Blue"]**BD-DL**[/COLOR]- Dual Layer (50G) BD-ROM Dual Layer Blu-ray Disk
[COLOR="Blue"]**BDXL100**[/COLOR]- Triple Layer (100G) BD-ROM Triple Layer Blu-ray Disk
[COLOR="Blue"]**BDXL128**[/COLOR]- Quad Layer (128G) BD-ROM Quad Layer Blu-ray Disk
```

So for **DVD-D**ual **L**ayer it will look like this:
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=lucid,lucid-security,lucid-updates,lucid-backports [COLOR="Blue"]**--size=DVD-DL**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```

**B**lu-ray **D**isk (single layer 25gb) will look like this
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=lucid,lucid-security,lucid-updates,lucid-backports [COLOR="Blue"]**--size=BD**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```

**B**lu-ray **D**isk-**D**ual **L**ayer (50gb) will look like this
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=lucid,lucid-security,lucid-updates,lucid-backports [COLOR="Blue"]**--size=BD-DL**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```

**B**lu-ray **D**isk e**X**tra **L**arge (**100**gb) will look like this
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=lucid,lucid-security,lucid-updates,lucid-backports [COLOR="Blue"]**--size=BDXL100**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```

**B**lu-ray **D**isk e**X**tra **L**arge (**128**gb) will look like this
```
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=lucid,lucid-security,lucid-updates,lucid-backports [COLOR="Blue"]**--size=BDXL128**[/COLOR] ~/UbuntuRepos ~/UbuntuDVDs
```

Just remember the "safe size" as with the other disks is 93% so for a BDXL100 you will only get 93GB out of the possible 100GB. Having said that you could quite conceivably fit Lucid amd64, i386 and PowerPC onto 1 BDXL100 disk.

Once I get the .deb installer to work properly I will attach the full package, and I may even rename it to suit as it hasn't been worked on in nearly 7 years.

---

### Post by justwarm on 2010-07-03
> **luvr said:**
> I may have misunderstood your question, but I believe that what you're trying to do is exactly what I describe in my post on [How to set up a local Ubuntu mirror from a set of Repository DVDs.]("http://ubuntuforums.org/showthread.php?p=7455095#post7455095")
yes . i doesn't want to mean that .
i have used this command . 
find /start/here -name \*.deb -exec mv {} /to/there/ \;


so all of my data have been merged . so i want to place back to them in  there previous position .

---

### Post by thahir1986 on 2010-07-22
great thanks for the how to and will try to create my own repository dvd ......

---

### Post by jeffCC on 2010-08-21
Hardy Heron life ended April 2011    

Hey, do you know the guy who emailed me from the year 2038 ?:lolflag:

---

### Post by BobSongs on 2010-09-06
Thanks for catching that error, JeffCC.

Note to self: Do **NOT** edit the page late at night.

It has been fixed.

---

### Post by luvr on 2010-09-20
[SIZE="4"][COLOR="DarkRed"]**_The Issue._**[/COLOR][/SIZE]

You have just created a set of local repository mirrors, and you are ready to edit your *“/etc/apt/sources.list”* file, to make your system use your local mirrors in place of the online repositories.

If you’re anything like me, however, then you won’t be particularly looking forward to editing the file manually; you would, instead, prefer to have your system create the new version of the file for you.

In this post, I will discuss a program that I wrote in Python, and that will do exactly that: It will identify your local mirrors, and automatically replace your *“sources.list”* file with a version that uses them.

[SIZE="4"][COLOR="DarkRed"]**_Preliminary Notes._**[/COLOR][/SIZE]

The program discussed here assumes that your local repository mirrors are all located in a common parent directory. For example, you may have created the following local mirror directories, all in your home directory:
[LIST][*]*“UbuntuRepos”*—Your local mirror of the *Ubuntu* repository.
[*]*“CanonicalRepos”*—Your local mirror of the *Canonical* repository.
[*]*“MedibuntuRepos”*—Your local mirror of the *Medibuntu* repository.[/LIST]
The actual names of the directories don’t matter, and neither does the number of directories, or their location—as long as they are all present in the same parent directory.

The program will create the new *“sources.list”* file from scratch. The original contents of the file will be deleted—even though a backup copy will be saved in the *“sources.list_Saved”* file. However, if the *“sources.list_Saved”* file already exists, then no backup will be made.

[SIZE="4"][COLOR="DarkRed"]**_Obtaining the Program._**[/COLOR][/SIZE]

To obtain the program, download the *“scripts.tar.gz”* file attached to this post, and save it into, e.g., your home directory. Then, execute the following command to unpack it:
```
tar -xvzf scripts.tar.gz
```
The command will create five files:
[LIST][*]*“gen_sources.list_localmirror”*—The Python program that will create the new *“sources.list”* file for you.
[*]*“act_backports,”* *“deact_backports,”* *“act_proposed”* and *“deact_proposed,”*—Four small shell scripts that will make specific edits to the new *“sources.list”* file, as described below.[/LIST]
[INDENT]**_Note:_**

[INDENT]I’m only just learning Python myself, and I added detailed explanations of its operation, and of the Python features that it uses, as comments to the program—if only to deepen my own understanding of the language.[/INDENT][/INDENT]
[SIZE="4"][COLOR="DarkRed"]**_Using the Program._**[/COLOR][/SIZE]

**_Function._**

The program will generate a new APT *“sources.list”* file, which uses local repository mirrors located in a common parent directory.
If any *“-backports”* or *“-proposed”* distributions are present in the repository mirrors, then they will be included in the new file, but they will be deactivated (i.e., their lines will begin with a ***“#”*** character, to turn them into comments).
After it generates the new *“sources.list”* file, the program will refresh the repository software indexes (i.e., it will run a ***“sudo apt-get update”*** command).

**_Usage._**
```
gen_sources.list_localmirror [ -t | --test ] [ <BASE_DIRECTORY> ]
```
**_Options._**
```
-t, --test
```
[INDENT]Perform a test run only.
When this option is specified, the program will display the shell command sequence that it would run in order to generate the new *“sources.list”* file, but it will not actually execute it.[/INDENT]
**_Parameters._**
```
<BASE_DIRECTORY>
```
[INDENT]The path to the parent directory of the local mirrors.
Each of the repository mirrors should be kept in its own subdirectory of this location.
If this parameter is omitted, the base directory will be set to the current user’s home location.
If this parameter specifies an ***absolute** path* (i.e., if it begins with a forward slash), then it will be used unchanged.
If this parameter specifies a ***relative** path,* then it will be interpreted relative to the current user’s home location.[/INDENT]
**_Examples._**

[INDENT]***_Note:_***

[INDENT]To understand the following examples, assume that the current user’s home location is *“/home/username.”*[/INDENT]
***_Example 1:_***
```
gen_sources.list_localmirror
```
[INDENT]This command will look for local repository mirrors in the current user’s home location (e.g., in the *“/home/username”* directory), and generate a new APT *“sources.list”* file to make use of these local mirrors.[/INDENT]
***_Example 2:_***
```
gen_sources.list_localmirror --test
```
[INDENT]This command will look for local repository mirrors in the current user’s home location (e.g., in the *“/home/username”* directory), and display the command sequence that it would have run to generate a new APT *“sources.list”* file, had it been invoked ***without*** the *"--test"* option.[/INDENT]
***_Example 3:_***
```
gen_sources.list_localmirror /LinuxDistros/Lucid/Repositories
```
[INDENT]This command will look for local repository mirrors in the *“/LinuxDistros/Lucid/Repositories”* directory, and generate a new APT *“sources.list”* file to make use of these local mirrors.[/INDENT]
***_Example 4:_***
```
gen_sources.list_localmirror --test /LinuxDistros/Lucid/Repositories
```
[INDENT]This command will look for local repository mirrors in the *“/LinuxDistros/Lucid/Repositories”* directory, and display the command sequence that it would have run to generate a new APT *“sources.list”* file, had it been invoked ***without*** the *"--test"* option.[/INDENT]
***_Example 5:_***
```
gen_sources.list_localmirror LinuxDistros/Lucid/Repositories
```
[INDENT]This command will look for local repository mirrors in the *“/home/username/LinuxDistros/Lucid/Repositories”* directory, and generate a new APT *“sources.list”* file to make use of these local mirrors.[/INDENT]
***_Example 6:_***
```
gen_sources.list_localmirror --test LinuxDistros/Lucid/Repositories
```
[INDENT]This command will look for local repository mirrors in the *“/home/username/LinuxDistros/Lucid/Repositories”* directory, and display the command sequence that it would have run to generate a new APT *“sources.list”* file, had it been invoked ***without*** the *"--test"* option.[/INDENT][/INDENT]
**_Note._**

As noted above, if any *“-backports”* or *“-proposed”* distributions are present in the repository mirrors, then they will be included in the new file, but they will be deactivated (i.e., their lines will begin with a ***“#”*** character, to turn them into comments). To allow you to easily activate or deactivate, there are four small shell scripts included with the program.

To execute the scripts, simply invoke them by name; they do not take any parameters. The scripts make simple edits to your new *“sources.list”* file, and subsequently run a ***“sudo apt-get update”*** command to refresh the repository software indexes.

The following scripts are provided:
[INDENT]***_The “act_backports” Script:_***
```
act_backports
```
[INDENT]Activates the *“-backports”* distributions that it encounters in the *“sources.list”* file.[/INDENT]
***_The “deact_backports” Script:_***
```
deact_backports
```
[INDENT]Deactivates the *“-backports”* distributions that it encounters in the *“sources.list”* file, to undo the effect of the *“act-backports”* script.[/INDENT]
***_The “act_proposed” Script:_***
```
act_proposed
```
[INDENT]Activates the *“-proposed”* distributions that it encounters in the *“sources.list”* file.[/INDENT]
***_The “deact_proposed” Script:_***
```
deact_proposed
```
[INDENT]Deactivates the *“-proposed”* distributions that it encounters in the *“sources.list”* file, to undo the effect of the *“act-backports”* script.[/INDENT][/INDENT]
[SIZE="4"][COLOR="DarkRed"]**_References._**[/COLOR][/SIZE]

[LIST][*][How to make your own Ubuntu Repository DVDs]("http://ubuntuforums.org/showthread.php?p=2100699#post2100699")—the initial post in this thread, by **BobSongs.**
[*][How to get "debmirror" to download and validate the "Release.gpg" file]("http://ubuntuforums.org/showthread.php?p=7367273#post7367273")—one of my earlier posts in this thread.
[*][Dive Into Python]("http://apress.com/book/view/9781590593561"), written by [Mark Pilgrim]("http://diveintomark.org"), and published by [Apress]("http://www.apress.com")—this is the book from which I'm learning Python.
[*][Dive Into Python—Python from novice to pro]("http://diveintopython.org")—the web site where you can read the *“Dive Into Python”* book online.
[*][The Python Programming Language—The Official Website.]("http://www.python.org")[/LIST]

---

### Post by Black_Tanto on 2010-09-21
Good info in the OP.


Can anybody tell me if its possible to download only the apps that are already installed on a particular distro including the apps that it came with.....AptonCD wont work for this because it only downloads apps as deb files for apps you downloaded yourself. I am trying to export the specific apps that one release has and simply ADD it to another. 

Any help please?

I do not want to download the entire repo, just what came on the disk.

---

### Post by luvr on 2010-09-21
> **Black_Tanto said:**
> Can anybody tell me if its possible to download only the apps that are already installed on a particular distro including the apps that it came with
I can't give a complete answer to your question off-hand, but if you want to obtain a list of the packages that are currently installed on your system, then you can run the following command:
```
dpkg --get-selections
```
Then, for each of the packages that appear in the list, you can run the following:
```
sudo apt-get --download-only --reinstall install *package-name*
```
This will download the specified package(s) into the **/var/cache/apt/archives** directory.

---

### Post by luvr on 2010-09-24
[SIZE="4"][COLOR="DarkRed"]**_The Issue._**[/COLOR][/SIZE]

You are trying to install the *Adobe Flash Player Plugin* software package (i.e., *&#8220;flashplugin-installer&#8221;*) on a computer that has only limited internet access. Because of the limited connectivity, you install from a local software repository mirror.

Since you are installing from a local mirror, you are hoping that the software will not need to be downloaded from the internet, but that it will be taken from your local mirror instead.

Your assumption initially appears to be confirmed when you run the following command to perform the installation:
```
sudo apt-get install flashplugin-installer
```
Indeed, the first few lines of output from this command look like this:
```
[COLOR="Navy"]Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following packages will be upgraded:
  flashplugin-installer
1 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
**Need to get 0B/19.9kB of archives.**
After this operation, 0B of additional disk space will be used.[/COLOR]
```
You notice, specifically, the line that reads ***&#8220;Need to get 0B/19.9kB of archives.&#8221;***

From this output line, you draw the conclusion that, as expected, the software packages will *not* be downloaded from the internet, but that the files that you want to install, will be taken from your local repository instead.

However, as the operation continues, you discover that the installer still attempts to download a *&#8220;.tar.gz&#8221;* archive file; this download will, obviously, fail if the computer does not have an active internet connection&#8212;e.g.:
```
[COLOR="Navy"]Setting up flashplugin-installer (10.1.85.3ubuntu0.10.04.1) ...
Downloading...
--2010-09-21 22:04:11--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz
Resolving archive.canonical.com... failed: Name or service not known.
wget: unable to resolve host address `archive.canonical.com'
download failed
The Flash plugin is NOT installed.[/COLOR]
```
This document will explain how you can examine the *&#8220;flashplugin-installer&#8221;* package, and find a way to avoid having the package download the archive file during installation.

[INDENT]**Note:**

[INDENT]This document assumes, as an example, that the local ***Ubuntu*** software mirror is located in the following directory:
```
[COLOR="Navy"]**/LinuxDistros/Ubuntu-10.04/Repositories/Ubuntu**[/COLOR]
```
Likewise, the document refers to a local ***Canonical*** software mirror in the following directory:
```
[COLOR="Navy"]**/LinuxDistros/Ubuntu-10.04/Repositories/Canonical**[/COLOR]
```
If your local mirrors are located elsewhere, then, obviously, you will have to modify the paths to your mirrors accordingly.[/INDENT]

**Note:**

[INDENT]This document is based on my earlier, similar, post on [Installing the Flash Player Plugin](http://ubuntuforums.org/showthread.php?p=9293926#post9293926) from a customised local software repository, but it was updated to a more recent version of the Flash Player Plugin.[/INDENT][/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_1. Getting a Copy of the *&#8220;flashplugin-installer&#8221;* Package._**[/COLOR][/SIZE]

Since you are installing from your local software repository mirror, the *&#8220;flashplugin-installer&#8221;* package should be available in your mirror. To find out where exactly it is located, you can run the following command:
```
apt-cache showpkg flashplugin-installer
```
The first few lines of output from this command look like this:
```
[COLOR="Navy"]Package: flashplugin-installer
Versions:
10.1.85.3ubuntu0.10.04.1 (/var/lib/apt/lists/**_LinuxDistros_Ubuntu-10.04_Repositories_Ubuntu_dists_lucid-security_multiverse_binary-amd64**_Packages) (/var/lib/apt/lists/_LinuxDistros_Ubuntu-10.04_Repositories_Ubuntu_dists_lucid-updates_multiverse_binary-amd64_Packages) (/var/lib/dpkg/status)[/COLOR]
```
This output identifies the directory that contains the package list (i.e., the *&#8220;Packages&#8221;* file) in which the *&#8220;flashplugin-installer&#8221;* package is described:
```
[COLOR="Navy"]**/LinuxDistros/Ubuntu-10.04/Repositories/Ubuntu/dists/lucid-security/multiverse/binary-amd64**[/COLOR]
```
If you list the contents of this directory, then you will see that, apparently, only the compressed copies of the package list, *&#8220;Packages.bz2&#8221;* and *&#8220;Packages.gz,&#8221;* are available. You can open either copy with the *&#8220;Archive Manager,&#8221;* and you will find that they contain a *&#8220;Packages&#8221;* file&#8212;which you can open in the text editor.

[INDENT]**Note:**
[INDENT]As an alternative, you can use the *&#8220;less&#8221;* page viewer to view either copy in a command-line shell window. Just move to the directory that contains the two copies, and then run the following command:
```
less Packages.gz
```[/INDENT][/INDENT]
The *&#8220;flashplugin-installer&#8221;* package is documented in this file under the following heading:
```
[COLOR="Navy"]Package: flashplugin-installer[/COLOR]
```
One of the items in this section is the *&#8220;Filename:&#8221;* line, which looks like this:
```
[COLOR="Navy"]Filename: **pool/multiverse/f/flashplugin-nonfree/*flashplugin-installer_10.1.85.3ubuntu0.10.04.1_amd64.deb***[/COLOR]
```
Thus, the package file name is *&#8220;flashplugin-installer_10.1.85.3ubuntu0.10.04.1_amd64.deb,&#8221;* and the file is located in the following directory:
```
[COLOR="Navy"]**/LinuxDistros/Ubuntu-10.04/Repositories/Ubuntu/pool/multiverse/f/binary-amd64/flashplugin-nonfree**[/COLOR]
```
Copy the file, *&#8220;flashplugin-installer_10.1.85.3ubuntu0.10.04.1_amd64.deb,&#8221;* from this directory to an easily accessible location&#8212;e.g., to your home directory.

[SIZE="4"][COLOR="DarkRed"]**_2. Extracting the Control Information from the Package._**[/COLOR][/SIZE]

To take a look at what a software package actually *does* when you install it, you will have to extract its *control information*&#8212;which includes configuration settings and script files to guide the installation process *(as well as the **un**installation process).*

To extract the *control information* from a Debian package file, you can use the *&#8220;dpkg-deb&#8221;* command, and pass it the *&#8220;--control&#8221;* option. The following command, for instance, will extract the *control information* from your copy of the *&#8220;flashplugin-installer&#8221;* package file:
```
dpkg-deb --control flashplugin-installer_10.1.85.3ubuntu0.10.04.1_amd64.deb
```
This command will not produce any visible output, but it will create a *&#8220;DEBIAN&#8221;* directory, in which it copies the *control information* from the package file. You can run the following command to obtain a list of the extracted control files:
```
ls -l DEBIAN
```
The output will look something like this:
```
[COLOR="Navy"]total 36
-rwxr-xr-x 1 luvr luvr 1457 2010-09-21 01:40 [COLOR="Green"]config[/COLOR]
-rw-r--r-- 1 luvr luvr 1942 2010-09-21 01:40 control
-rw-r--r-- 1 luvr luvr  334 2010-09-21 01:40 md5sums
-rwxr-xr-x 1 luvr luvr 5126 2010-09-21 01:40 [COLOR="Green"]postinst[/COLOR]
-rwxr-xr-x 1 luvr luvr  206 2010-09-21 01:40 [COLOR="Green"]postrm[/COLOR]
-rwxr-xr-x 1 luvr luvr 2505 2010-09-21 01:40 [COLOR="Green"]prerm[/COLOR]
-rw-r--r-- 1 luvr luvr 5438 2010-09-21 01:40 templates[/COLOR]
```
Two of these files are of particular interest:
[LIST][*]**config**
This is the script that will drive the *configuration* of the installation process.
In the case of the *&#8220;flashplugin-installer&#8221;* package, for example, this script will decide if the supporting files will have to be downloaded, or have been made available locally.
[*]**postinst**
This is the script that will take any post-installation steps required to make the installed software fully functional.[/LIST]
These two script files can help you determine which files you will have to make available locally, and where you have to copy them, in order to keep the installer from attempting to download any further files during the installation process.

[SIZE="4"][COLOR="DarkRed"]**_3. Examining the *&#8220;config&#8221;* File._**[/COLOR][/SIZE]

If you open the *&#8220;config&#8221;* file in any text editor, then you will see the following code fragments near the top of the file:
```
[COLOR="Navy"]FLASH_VERSION=**10.1.85.3**
FILENAME=**adobe-flashplugin_${FLASH_VERSION}.orig.tar.gz**
SHA256SUM_TGZ="**cd58b8550aa6c2e99d2b392f854a985e2d73a38d47a0f6d7709b69e9b4dae3e3**"[/COLOR]
```
```
[COLOR="Navy"]db_get flashplugin-installer/local
echo "$SHA256SUM_TGZ  $RET/$FILENAME" \
| sha256sum -c > /dev/null 2>&1 \
|| db_set flashplugin-installer/local **/var/cache/flashplugin-installer**[/COLOR]
```
This code apparently looks for a file named *&#8220;adobe-flashplugin_10.1.85.3.orig.tar.gz&#8221;* in a directory named *&#8220;/var/cache/flashplugin-installer&#8221;*; if it finds the file there, then it will run the *&#8220;sha256sum&#8221;* utility to verify the integrity of the file.

Presumably, if the file is found, and if its checksum matches, then the Flash player plugin will be installed from this local copy; otherwise, the script will force a download from the internet during the installation process&#8212;though it is not yet clear from *which online location.*

[SIZE="4"][COLOR="DarkRed"]**_4. Examining the *&#8220;postinst&#8221;* File._**[/COLOR][/SIZE]

Next, if you open the *&#8220;postinst&#8221;* file in any text editor, then you will find the following code near the top of the file:
```
[COLOR="Navy"]FLASH_VERSION=**10.1.85.3**
FILENAME=**adobe-flashplugin_${FLASH_VERSION}.orig.tar.gz**
SHA256SUM_TGZ="**cd58b8550aa6c2e99d2b392f854a985e2d73a38d47a0f6d7709b69e9b4dae3e3**"
PARTNER_URL=**http://archive.canonical.com/pool/partner/a/adobe-flashplugin/**$FILENAME[/COLOR]
```
This code appears to set up the URL from which the file, *&#8220;adobe-flashplugin_10.1.85.3.orig.tar.gz,&#8221;* will be downloaded *(if no valid local copy of the file is available).*

The file will be downloaded from the following online directory resource:
```
[COLOR="Navy"]**http://archive.canonical.com/pool/partner/a/adobe-flashplugin/**[/COLOR]
```
Incidentally, this is a location within the online ***Canonical*** software repository; if you created a local mirror of this repository, then your system will have downloaded this resource into a local directory&#8212;e.g.:
```
[COLOR="Navy"]**/LinuxDistros/Ubuntu-10.04/Repositories/Canonical/pool/partner/a/adobe-flashplugin**[/COLOR]
```
For easy access, you may want to temporarily copy the *&#8220;adobe-flashplugin_10.1.85.3.orig.tar.gz&#8221;* file from this location to, e.g., your home directory. If you want to do this from the command-line shell, then just move to the directory that contains the file, and run the following command:
```
cp adobe-flashplugin_10.1.85.3.orig.tar.gz ~
```
[INDENT]**Note:**
[INDENT]Alternatively, if you have not set up a local mirror of the ***Canonical*** software repository, you will temporarily need internet access to download the file, e.g., with the following command:
```
wget http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz
```[/INDENT][/INDENT]
[SIZE="4"][COLOR="DarkRed"]**_5. OPTIONAL: Verifying the Checksum._**[/COLOR][/SIZE]

If you wish, you can now verify the checksum of the *&#8220;adobe-flashplugin_10.1.85.3.orig.tar.gz&#8221;* file, with the following command:
```
sha256sum -b adobe-flashplugin_10.1.85.3.orig.tar.gz
```
The output from this command should look like this:
```
[COLOR="Navy"]cd58b8550aa6c2e99d2b392f854a985e2d73a38d47a0f6d7709b69e9b4dae3e3 *adobe-flashplugin_10.1.85.3.orig.tar.gz[/COLOR]
```
In particular, the checksum value (i.e., the 64-character string with which the line begins) should match the ***SHA256SUM_TGZ*** value that you encountered in both the *&#8220;config&#8221;* and *&#8220;postinst&#8221;* scripts.

Alternatively, you can first create a *checksum verification file*&#8212;i.e., a file with the following contents, all on one line:
[LIST][*]The expected checksum of the file that you want to verify&#8212;i.e., the ***SHA256SUM_TGZ*** value, which you can copy from the *&#8220;config&#8221;* and *&#8220;postinst&#8221;* scripts:
```
[COLOR="DarkRed"]cd58b8550aa6c2e99d2b392f854a985e2d73a38d47a0f6d7709b69e9b4dae3e3[/COLOR]
```
[*]A blank space, followed by an asterisk:
```
[COLOR="DarkRed"] *[/COLOR]
```
[*]The name of the file that you want to verify:
```
[COLOR="DarkRed"]adobe-flashplugin_10.1.85.3.orig.tar.gz[/COLOR]
```[/LIST]
(Note that the resulting line is identical to the output from the *&#8220;sha256sum&#8221;* command, above.)
Save this file as, e.g., *&#8220;SHA256,&#8221;* and run the following command:
```
sha256sum -c SHA256
```
This time, the output should look like this:
```
[COLOR="Navy"]adobe-flashplugin_10.1.85.3.orig.tar.gz: OK[/COLOR]
```
[SIZE="4"][COLOR="DarkRed"]**_6. Installing the Flash Player Plugin, without Internet Access._**[/COLOR][/SIZE]

You are now ready to install the Flash Player Plugin from your local software repository mirror, without requiring internet access during the process. Before you do so, you will have to create the *&#8220;/var/cache/flashplugin-installer&#8221;* directory, and copy the *&#8220;adobe-flashplugin_10.1.85.3.orig.tar.gz&#8221;* file into it. Just run the following commands:
```
sudo mkdir /var/cache/flashplugin-installer
sudo cp adobe-flashplugin_10.1.85.3.orig.tar.gz /var/cache/flashplugin-installer
```
You can subsequently install the plugin with, e.g., the following command:
```
sudo apt-get install flashplugin-installer
```
The following output line will, then, confirm that the plugin will be installed from the locally available copy of the *&#8220;adobe-flashplugin_10.1.85.3.orig.tar.gz&#8221;* file:
```
Installing from local file /var/cache/flashplugin-installer/adobe-flashplugin_10.1.85.3.orig.tar.gz
```

---

### Post by klein de usa on 2010-10-31
hi 
this is just what i'v been looking for, but there is one problem for me. is it possible to start and stop the download ? i only have 625 mb a day i can download except between 2am and 7am if i could start downloading them at 2am then stop at 7am and then start them again at 2am the next night with a cron script?

---

### Post by luvr on 2010-11-03
> **klein de usa said:**
> is it possible to start and stop the download ?
You can interrupt the download at any time. Then, when you restart it, it will pick up where it left off.
> i only have 625 mb a day i can download except between 2am and 7am if i could start downloading them at 2am then stop at 7am and then start them again at 2am the next night with a cron script?
There must, indeed, be a way to schedule the download to start at a particular time of day (e.g., 2 AM), and then to interrupt it some time later (e.g., 7 AM). A cron job sounds like a good idea to me, though I'm not sufficiently familiar with cron to give you any advice on it.

---

### Post by emanamini on 2010-11-08
Hey GOOD JOB MEN :-D

---

### Post by luvr on 2010-11-11
[SIZE="4"][COLOR="DarkRed"]**_The Problem._**[/COLOR][/SIZE]

[INDENT]**_Note:_**

[INDENT]This post applies to Ubuntu 10.04 (a.k.a. the *“Lucid Lynx”*) and Ubuntu 10.10 (a.k.a. the *“Maverick Meerkat”*)—which apparently share the same version of the *“debmirror”* utility.
The error also occurs with the *“debmirror”* version that, at the time of writing, is available with the Ubuntu 11.04 (a.k.a. the *“Natty Narwhal”*) pre-release.
Even though the *“debmirror”* version that comes with *“natty”* is different from the version distributed with *“maverick”* and *“lucid,”* the patch that I provide as an attachment to this post, will work on either version of the *“debmirror”* utility.[/INDENT][/INDENT]

I’m trying to set up a local mirror for the Canonical *“Partner”* repository—similar to the local Ubuntu mirror that I documented in [an earlier post in this thread.]("http://ubuntuforums.org/showthread.php?p=7367273#post7367273")

First, I create a directory in which I will download the repository files:
```
mkdir ~/PartnerRepos
```

Next, I perform a *“debmirror”* test run (using the *“--dry-run”* option):
```
debmirror --dry-run --method=http --host=archive.canonical.com --root=ubuntu \ 
   --dist=lucid,lucid-backports,lucid-proposed,lucid-security,lucid-updates --section=partner \ 
   --arch=amd64,i386 --progress ~/PartnerRepos
```

However, instead of running to completion, *“debmirror”* reports an error after it downloads two of the *“Release”* files:
```
[0%] Getting: dists/lucid/Release... ok 
[0%] Getting: dists/lucid/Release.gpg... ok 
[0%] Getting: dists/lucid-backports/Release... ok 
[0%] Getting: dists/lucid-backports/Release.gpg... ok 
Duplicate dist lucid.
```
Apparently, the new *“debmirror”* version assumes that a repository will consist of only one *dist* by default. Thus, it will have to handle the *“Ubuntu”* repository—which includes multiple *dists*—in a special way. However, in doing so, it overlooks the Canonical Partner repository—which also has multiple *dists,* but gets treated as a *“default,”* single-*dist* repository instead.

[INDENT]**_Technical Note:_**

[INDENT]From looking at the *“debmirror”* code, I’m puzzled as to why it would want to restrict repositories to a single *dist* by default. In fact, what the *“debmirror”* command line calls *“dists”* should translate to *“suites”* internally. Conversely, what the code internally calls a *“dist”* corresponds to the *code name* of the distribution—e.g., *“lucid,”* *“maverick,”* *“natty,”* etc.
It is my impression that the code is confused about its own terminology—which shouldn’t really come as a surprise, because of the two different meanings of the term *“dist.”* However, I’m not sufficiently familiar with the internal details of the code to understand how to clear up the confusion.[/INDENT][/INDENT]
[SIZE="4"][COLOR="DarkRed"]**_The Fix._**[/COLOR][/SIZE]

Since *“debmirror”* handles the *“Ubuntu”* repository in a special way, it *must* contain code to test the repository name, to allow it to process the *“Ubuntu”* repository differently from any other (supposedly single-*dist*) repository.

To ensure that it will allow the *“Canonical”* repository to contain multiple *dists,* I developed a fairly simple patch that extends the test for the repository name, to cover not only the *“Ubuntu”* repository, but the *“Canonical”* repository as well. The patch can be applied as described next.

**_Applying the patch to the *“debmirror”* script._**

I don’t particularly like applying a patch to a system file in-place; instead, I prefer to copy the affected file to, e.g., my home directory, and apply the patch to the copy. Therefore, the following procedure will apply my patch to a copy of the *“debmirror”* script in the home directory of the user that is currently logged in to the system:
[LIST][*]Execute the following commands to copy the *“debmirror”* script to your home directory:
```
cd
cp /usr/bin/debmirror .
```
[*]Download the *“debmirror_origin_patch.zip”* file attached to this post. Save it into your home directory (next to your *“debmirror”* copy), and run the following command to unzip it and create the *“debmirror_origin_patch”* file:
```
unzip debmirror_origin_patch.zip
```
[*]Execute the following command to apply the patch (from the *“debmirror_origin_patch”* file) to your copy of the *“debmirror”* script:
```
patch < debmirror_origin_patch
```[/LIST]
Assuming that the *“patch”* command reports no errors, your *“debmirror”* copy will now include my patch.

**_Trying out the patched *“debmirror”* script._**

To test the patched *“debmirror”* script, run it from your home directory (i.e., prepend *“~/”* to the command name):
```
~/debmirror --dry-run --method=http --host=archive.canonical.com --root=ubuntu \
   --dist=lucid,lucid-backports,lucid-proposed,lucid-security,lucid-updates --section=partner \
   --arch=amd64,i386 --progress ~/PartnerRepos
```

This time, *“debmirror”* should not complain about *“duplicate dist”* values, but it should complete successfully instead.

[SIZE="4"][COLOR="DarkRed"]**_See also: Bug Report._**[/COLOR][/SIZE]

I created a bug report about this issue—cfr. [Bug #674153 in debmirror (Ubuntu): “debmirror cannot download Canonical repository, but reports "Duplicate dist" error instead”]("https://bugs.launchpad.net/ubuntu/+source/debmirror/+bug/674153")

---

### Post by klein de usa on 2010-11-14
hi 
luvr you are right cron is the way to do it, starting it isn't the problem stopping it is,
 
starting debmirror:
 
create a bash script with only the big long debmirror command in it, then set up cron to start it at a set time.

stopping debmirror:

you have to creat a bash script that calls killprocess debmirror witch calls a bash script that find the pid # of debmirror and then kills it. 

if anyone should need a complete detailed explanation , i will try my best to explain it. i put this on a headless michine , i can ssh and vnc into it , also have the michine set up to send cli mail with a cron job.

my hope it to get this machine to a better Internet connection lol

---

### Post by luvr on 2010-11-15
> **klein de usa said:**
> if anyone should need a complete detailed explanation , i will try my best to explain it.
I'm sure we would all appreciate it very much if you could document what you did in order to get it to work. Anything that may help others get the most out of their local repository mirrors, is definitely worth documenting here!

---

### Post by Souravampire on 2010-11-15
:KS:KS:KS:KS

Thank you thank you and thank you for this beautiful post.
Cheers.Long live Bobsong and luvr.

:KS:KS:KS:KS

---

### Post by BobSongs on 2010-12-05
**luvr** has indeed added soooo much to this thread that he truly deserves the credit here.

I will forever maintain that I've done nothing original. I've merely taken someone else's tutorial and enhanced it for those who want to copy/paste and get the job done.

**luvr** has an impressive grasp of the Linux system far beyond my extremely limited skills.

But isn't that the beauty of the Linux system? With Windows I was able to pretty much have a handle on most aspects of it. In Linux? One command can have an incredible amount of switches to make it do sooo many things.

So to all who have shared their knowledge and understanding of the software related to this thread: A huuuge thank you is in order. You guys rock. By sharing what you know and understand, you truly carry on the spirit of OpenSource, a concept that took me a few years to grasp but now I embrace enthusiastically.

---

### Post by b.tavakkoli on 2010-12-07
Hi,
Please explain step by step how to install debpartial, because this isn't in maverick repositories, and if i download this manually, it has some dependencies ...

(Also is there any program except debpartial?)

Thanks

---

### Post by tg3793 on 2010-12-24
> **b.tavakkoli said:**
> Hi,
Please explain step by step how to install debpartial, because this isn't in maverick repositories, and if i download this manually, it has some dependencies ...

(Also is there any program except debpartial?)

Thanks

Here is the link to debpartial IN the maverick repositories [http://packages.ubuntu.com/hu/maverick/net/debpartial-mirror](http://packages.ubuntu.com/hu/maverick/net/debpartial-mirror)

If you install it with a package installer it 'should' bring in the dependencies.

---

### Post by tg3793 on 2010-12-24
> **BobSongs said:**
> [FONT=Verdana]Download in passive mode. I think there are four people in the world who know what this means. If you bump into one they'll let you know, and you'll let me know. In the mean time, I keep it in because it works right with it in there.
[/FONT]

It was the lingering of not knowing that kept going in my mind. So I found the answer to what "passive" does in debmirror based on what it does in FTP ... In a nutshell it helps get around firewall based connectivity problems when 'you' are NOT the server. So you are right in saying the important part is that "it works" :-)

Check out the definition of "passive" as it related to FTP here [[COLOR="Blue"]at this site[/COLOR]]("http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html"). I think they did a pretty good job. It's under the section titled "The Two Types of Data Transfers - Active (PORT) and Passive (PASV)".

---

### Post by k3lt01 on 2010-12-31
> **tg3793 said:**
> Here is the link to debpartial IN the maverick repositories [http://packages.ubuntu.com/hu/maverick/net/debpartial-mirror](http://packages.ubuntu.com/hu/maverick/net/debpartial-mirror)

If you install it with a package installer it 'should' bring in the dependencies.debpartial and debpartial-mirror are not th same and do not do the same thing. Best to stick with the information in the original post.

---

### Post by tg3793 on 2011-01-01
Ok [debpartial]("http://packages.ubuntu.com/dapper/debpartial")  and [debpartial-mirror]("http://wiki.debian.org/DebPartialMirror") ... I stand ... err; sit ... corrected :-)

---

### Post by BobSongs on 2011-01-23
*grins*

Yes, the original post does describe how to add debpartial, and yes: it does require a few dependencies. The link is to a .deb file. There's no way around its dependencies.

---

### Post by klein de usa on 2011-08-13
hi 
sometime ago i figured out how to start and stop debmirror with crontab because my Internet connection had a free period from 2am to 7am each morning.

below is a pdf file, my best attempt at explaining how i did it, i am by no means an expert at bash, crontab, or debmirror USE AT YOUR OWN RISK 

but over the last few months i have downloaded 8.04 i386 and 8.04 amd64 with it and am now starting to download 10.04 i386 and 10.04 amd64 on my connection i can down load around 2 to 2.5 gigs a night.

---

### Post by djsmoot on 2011-08-29
I have been trying to create a set of DVDs to use to install multiple systems not connected to the internet.  I am first trying to get this working using a VM that I have set up on my connected PC, so that I can ensure that it works before burning all of the DVDs.  

I followed all of the steps presented and am currently trying to do Step 7 (via the terminal).  I ran sudo apt-cdrom add for each of the DVDs and labeled them Disk[1-10].  The update works fine.
 
When I try to run the upgrade or try to install any new package, I get the error that is shown in this screen capture. I double checked that the files that it is looking for are there in those locations. Does anyone have any idea about what could be causing this?

[IMG]http://i607.photobucket.com/albums/tt153/danasmoot/error.jpg[/IMG]

---

### Post by dcoetzee on 2011-09-14
Hey everyone, I got this working. Here is what I changed:

debpartial is now much harder to find, having been deprecated because it has no maintainer and hasn't been updated since 2003 (but it appears to still work - let them know if you want to help maintain it!). You can still get a copy of the latest version at:

[http://ftp.gnome.org/mirror/cdimage/snapshot/Debian/pool/main/d/debpartial/debpartial_0+20030508.1.tar.gz](http://ftp.gnome.org/mirror/cdimage/snapshot/Debian/pool/main/d/debpartial/debpartial_0+20030508.1.tar.gz)

I also used a for loop to replace the many debcopy statements:
```

for f in ~/UbuntuDVDs/*; do ruby debcopy -l ~/UbuntuRepos $f; done
```You can do something similar for mkisofs, but need to know the number of discs:

```
for f in 1 2 3 4 5 6 7 8 9; do mkisofs -f -J -r -V "Ubuntu 10.04 $f/8" -o ubuntu-10.04-$(date -I)-complete-i386-dvd$f.iso ~/UbuntuDVDs/ubuntu$f; done
```Use maverick in place of lucid for 10.10, and natty in place of lucid for Ubuntu 11.04.

When I ran mkisofs, I got this error for most of the DVDs:

```
genisoimage: Error: ubuntu-dvds/maverick/ubuntu8/pool/main/p/pulseaudio/libpulse-mainloop-glib0_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_i386.deb and ubunt\
u-dvds/maverick/ubuntu8/pool/main/p/pulseaudio/libpulse-mainloop-glib0_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21_i386.deb have the same Joliet name
Joliet tree sort failed. The -joliet-long switch may help you.
```Adding the **-joliet-long** switch fixed this.

I wanted to create both i386 and amd64 DVDs, so I added to debmirror the switch "**--arch=i386,amd64**", and ran debpartial twice, once with the switch "**--arch=i386**" and once with the switch "**--arch=amd64**", each time with different destination directories.

A note about disk space: the packages themselves take up space, and the final ISO files take up space, but the ~/UbuntuDVDs directories do not take up much space at all (they consist entirely of symbolic links into the packages directory). So in all you only need about twice as much space as the packages, not three times.

I haven't tested the final ISOs yet because my only ISOs produced so far are maverick i386 and I have natty amd64, but I'll post again if there's more to figure out.

-- 
Derrick Coetzee
[http://www.eecs.berkeley.edu/~dcoetzee/]("http://www.eecs.berkeley.edu/%7Edcoetzee/")

---

### Post by Mozgoed on 2011-09-17
My programm can help you download Ubuntu repository.
[IMG]http://mozgoed-mgoy.narod.ru/ubuntu/screen.jpg[/IMG]
It's portable. And can be run under:
[LIST]
[*]Windows 2000, Windows XP - .Net Framework 2.0 requaired
[*]Windows Vista, Windows 7 - Nothing needed =)
[*]Ubuntu 10.10 - Mono enviroment. You can run it from terminal with following command "mono ubuntu-repository.exe"
[/LIST]
The newest version available here [http://mozgoed-mgoy.narod.ru/ubuntu/ubuntu-repository.zip]("http://mozgoed-mgoy.narod.ru/ubuntu/ubuntu-repository.zip")

---

### Post by badman35 on 2011-09-19
> **Mozgoed said:**
> My programm can help you download Ubuntu repository.
[IMG]http://mozgoed-mgoy.narod.ru/ubuntu/screen.jpg[/IMG]
It's portable. And can be run under:
[LIST]
[*]Windows 2000, Windows XP - .Net Framework 2.0 requaired
[*]Windows Vista, Windows 7 - Nothing needed =)
[*]Ubuntu 10.10 - Mono enviroment. You can run it from terminal with following command "mono ubuntu-repository.exe"
[/LIST]
The newest version available here [http://mozgoed-mgoy.narod.ru/ubuntu/ubuntu-repository.zip]("http://mozgoed-mgoy.narod.ru/ubuntu/ubuntu-repository.zip")

That's for sharing this with us. I've been working on something likes this for ubuntu off and on for the last year. Again thanks for sharing this with us and thanks for making a english version to..

---

### Post by hans1967 on 2011-12-09
Hi Community, 

I just failed to build a local karmic-mirror of [http://archive.canonical.com](http://archive.canonical.com). 

I am running xubuntu lucid lynx.

I have installed debpartial_0+20030508-0.1_all.deb from a debian-mirror and not the proposed debpartial_0+20030508.1.tar.gz from ubuntu-mirror becauce I did not succeed installing the tarball. 

This command... 

debmirror --nosource -m --passive --timeout=seconds -t 240 --host=http://archive.canonical.com/ --root=/ubuntu --method=http --progress --dist=karmic,karmic-security,karmic-updates,karmic-backports --section=main,restricted,universe,multiverse --arch=i386 ~/ubuntu-karmic-i386 --ignore-release-gpg

...gives following error-messages:

[0%] Getting: dists/karmic/Release... dists/karmic/Release failed 500 Can't connect to http::80 (Bad hostname 'http:')
[0%] Getting: dists/karmic-security/Release... dists/karmic-security/Release failed 500 Can't connect to http::80 (Bad hostname 'http:') 
[0%] Getting: dists/karmic-updates/Release... dists/karmic-updates/Release failed 500 Can't connect to http::80 (Bad hostname 'http:') 
[0%] Getting: dists/karmic-backports/Release... dists/karmic-backports/Release failed 500 Can't connect to http::80 (Bad hostname 'http:') 
Errors:
Download of dists/karmic/Release failed: 500 Can't connect to http::80 (Bad hostname 'http:') 
 Download of dists/karmic-security/Release failed: 500 Can't connect to http::80 (Bad hostname 'http:')  
Download of dists/karmic-updates/Release failed: 500 Can't connect to http::80 (Bad hostname 'http:')  
Download of dists/karmic-backports/Release failed: 500 Can't connect to http::80 (Bad hostname 'http:') 
Failed to download some Release or Release.gpg files! WARNING: releasing 1 pending lock...

root-directory on [http://archive.canonical.com/](http://archive.canonical.com/) IS NOT ubuntu. Typing --root=/ does not help - for first step.   debmirror says it is mirroring from [http://http://archive.canonical.com//debian/]("http://http://archive.canonical.com//debian/&quot;")

perhaps some strings in config-files are wrong?

Thank you for your attention. Perhaps you can help me.

hans1967

---

### Post by hans1967 on 2011-12-09
my problem seems solved:

[http://archive.canonical.com](http://archive.canonical.com) -> pool is empty

BobSongs solution seems to work now with a different internet-mirror.

thank you for your attention,

hans1967

---

### Post by BobSongs on 2011-12-11
Seems the folders have been moved to this location:

archive.canonical.com/dists/

Added to the tutorial how to modify one's **sources.list** if the Ubuntu we're running is old and the repositories can't be accessed as before.

---

### Post by madjohnva on 2012-07-14
Sorry for such a late question folks, but I tried both the old and new url (archive.canonical.com and archive.canonical.com/dists/) for Canonical and neither is working. I have been downloading the Hardy, Maverick and Precise (i386 and amd64) repos from Ubuntu and MediBubtu with no problems. I just can't get Canonical. I am also having a problem with making the index / packages list and public keys. After doing the commands, they want to make one package list of everything I have downloaded and the public key has all of them listed. Yes, I download to one computer (running Maverick) because it is the one I actually use and it is the one that I am using as a server. I also have another desktop running Hardy, and it is the one that runs WXtoIMG. My laptop currently runs Maverick, but I am going to upgrade to Precise. Any thoughts is greatly appreciated. I completely moved away from windows about 4 to 5 months ago, even though I still have another desktop that has both 98SE and Fedora Core 6 (using different drives) on it. Been using Linux distros since around 2001 or 2002, started out with RedHat 9, wasn't till January I tried Debian, then EdUbuntu, and finally settled with Ubuntu. Still consider myself a newbie, so it may take a whole lot of explaining something even simple. Thanks a bushel. John

---

### Post by madjohnva on 2012-07-14
OK folks, I figured out part of my problems. I have to cd to each directory. Still can't get the Canonical repos though. John

---

### Post by madjohnva on 2012-07-16
Disregard about Canonical folks. I'm happy with what I have in my repos now. I even have my repos working over LAN. John

---

