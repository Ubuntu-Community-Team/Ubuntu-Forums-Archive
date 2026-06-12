---
title: "Kathor's Linux Diary"
date: 2008-06-07
forum: Testimonials &amp; Experiences
---

### Post by K7522 on 2008-06-07
Kathor&#8217;s Linux Diary

Prelude
Many people write diaries about a wide variety of things, lately I have seen many in the gaming community. I've decided to begin a diary here about my experiences throughout my Ubuntu career. Welcome to my Ubuntu life. I will be editing the OP until there are too many characters, then start a new post! Feel free to reply with any questions or comments regarding how I fixed a problem I had or anything. My contact information is on my account on the forums.

Hello, I&#8217;m Kurt and you&#8217;ll be following my journey here into the world of Linux. I have previous experience in Windows, Fedora and Ubuntu. Hopefully we&#8217;ll all learn some things in this journey, what is good and mistakes not to make. What does and does not work in the process of installation, drivers and learning some of the terminal commands together.
I begin today, 20080606 with my Linux diary because I wanted to see exactly what I do to my computer over a course of three months or more. We start with a fresh computer with two hard drives, a 250gb HD for OS and a 1tb for files. Since I have a girlfriend who uses the computer I will be setting it up as a dual boot system for her ease.

	Ensure you have your Windows CD and Key, proceed to [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download) and download the proper image. Burn the ISO to a CD. At the time of this installation, I used Gutsy Gibbon, 7.10. Hardy Heron, 8.04 had been released already which is an LTS (Long Term Support) but I didn&#8217;t care to download the new ISO. I doubt the processes that follow will change much if at all.

	Begin by installing Windows, the process is fairly simple as you don&#8217;t have to partition any drives. I will be excluding this in the diary since I&#8217;ve already installed Windows on the computer. The installation took about 15 minutes by hand, and an additional 60 minutes automated. I then had to install drivers for my motherboard, sound card, video card and Ethernet card for them all to work properly taking an additional 30 minutes at most followed by a restart. I then installed SP1 and SP2 taking another two hours and a reboot.

I start the Ubuntu 7.10 boot CD in Windows, and it asks for a reboot. On reboot, it gives me an option to boot Ubuntu or Windows. I select windows. The load time was about 4 minutes, as the computer gathered information from the CD to load the OS. 
On first glance I like the look of it and there is an icon on the desktop named Install to put the new OS on the HD. I select it, and a window opens up for my language selection. Select English, and click Forward. The next screen is a map of the world, I click on the map to zoom in then select Chicago, since I&#8217;m in -6 time zone. Clicking Forward again brings me to a keyboard layout selection. I&#8217;m in U.S. English, which is preselected and I hit Forward.

The next step, 4 of 7 is to prepare the disk using partitions. Since I have Windows installed I select Manual and hit Forward. The computer scans the disk and gives me  a list of devices, format like below. My sda device is my 1tb file hard drive.
To format your partitions, follow instructions on the page by clicking on the HD you want and using the easy GUI.
```

Device . . . . .Type . .Mount Point . . Format? . .Size . . . . .Used
/dev/sda
 . /dev/sda1 . .ext3 . ./media/sda1 . . [ ] . . . .106 . . . . . MB 9 MB
 . /dev/sda2 . .ntfs . ./media/sda2 . . [ ] . . . .1048470 MB . .unknown
/dev/sdb
 . /dev/sdb1 . .ntfs	/media/sdb1 . . .[ ] . . . .104857 MB . . unknown
 . /dev/sdb2 . .ext3	/ . . . . . . . .[X] . . . .139253 MB . . unknown
 . /dev/sdb5 . .swap . . . . . . . . . .[ ] . . . .5938 MB . . . 0 MB

```
	Ubuntu senses that Windows is installed and asks if I want to import documents and settings for the accounts. Since it&#8217;s a fresh install I couldn&#8217;t care less, and skip this option by clicking Forward. The next step, 6 of 7 inquires, &#8220;Who are you?&#8221; this is going to be my name, login and password including the name of the computer. I enter these. Remember, this is going to be your primary log in for the computer. I put in my full name up to for grins since the task bar will show the full name. The login and computer name will autofill, but you can change these if you wish.

	Step 7 confirms everything I&#8217;m about to do, and I click Forward for the computer format and installation. Since I&#8217;m typing this at the time of installation on another computer I can&#8217;t accurately say how long it would take but I can&#8217;t see it being more than 8-10 minutes even with the manual HD partitioning. The partition and system installation took about 10 minutes, and then prompted for a computer restart. I selected restart then pulled the disk from the drive at the automated prompt.
	
Now at boot the computer asks me to select one of a few options Ubuntu on normal safe mode, memory check or Windows XP. I select Ubuntu on normal and the computer loads in under two minutes to the login screen. If the screen stays black for a while just wait, as first boots can sometimes take a long time. Booting the computer to Ubuntu won&#8217;t take as long as the first.

	Use your login selected at the beginning and boot up into your fresh installation of Linux.

	I received two pop-ups immediately, telling me there are updates available and that restricted drivers are available. I select the restricted drivers first and it asks for a password. Entering my pass opens a box informing me that I can enable better support for my NVIDIA 8800 GTX and I proceed to do so, since I heard these needed to be enabled to do some fun desktop features. It downloads a file automated and informs that changes are applied. I close these, and open the update manager bypassing the reboot prompts. There are many packages to update so just skim them over and select Install Updates. If you want to update to 8.04 (Hardy Heron) you can do so in this window after downloading the package files. I decide not to because I hear there are some difficulties getting the proper drivers working for NVIDIA to enable the nice desktop effects.

	Downloading these files including installation took about 15 minutes for 219 packages to download. The servers must be decent; my download rate ran from 550 to 650 kB/s. While these files worked, I took the time to load Pidgin (Applications/Internet/Pidgin) and add my AIM, MSN, Y! and ICQ information. I also loaded Firefox, the icon is a fox circling the globe on the top bar, and went to [http://www.skype.com/download/skype/linux](http://www.skype.com/download/skype/linux) for my internet phone. Click Download Now, then select Ubuntu 7.04+ and click OK when it says Open With gdebi-gtk (default). A package installer opens, leave it there. There you must wait for the other 219 downloads to finish, so let the window sit open until the others complete, then you can click Install Package.

	My first Ubuntu freakout, at 06062008 2300 I attempted to watch a video previously downloaded on my file drive, Smallville an avi file. Totem Movie Player opened and the computer locked up for about 2 minutes. The computer resumed with a new window, Search for suitable codec? Apparently you can&#8217;t run AVI files out of the box. I click Search, it searches and opens a new box named Install multimedia codecs. 3 options come up with popularity scale from 1-5 stars. I check the top selection at 5 stars and again I have to wait for the other installs to complete, so much for watching a movie.

	The computer locked up as Totem opened until the Search for suitable codecs? Window opened. On this freakout I was running the following:
 . . . .One instance of Firefox
 . . . .Update Manager at Applying Changes stage
 . . . .Package Installer idle to install Skype
 . . . .One instance of Totem Movie Player
	This time I decided to be patient, and waited for all my changes to finish and installed Skype, then my multimedia codecs. 

	Reopening Totem with the file caused it to lock up the system again, gave me the same error needing codecs and I decided to just install the other two &#8216;1 star&#8217; codec packs. This allowed the video to begin properly and did not cause the computer to lock up at all. This must have been from searching the computer for codecs. 

I expected to need to install audio codecs, but I can hear the file just fine.

	Exited Firefox and received a weird error, I just exited the window and Firefox. Reopened Firefox because of the update and it opened fine, restarted it just incase and it worked fine.

	Called testing center on Skype for checking my mic, but I didn&#8217;t hear myself so I need to get that fixed. Restarting the computer to apply all of the updates, maybe they will fix the mic. 

	Annoying boot sounds, need to get those turned off. I recognize the Restricted Drivers button in the top right and click it, the driver is enabled and in use. Good!

 I figured I should go head and update to 8.04, Hardy Heron. Again since I don't feel like downloading the CD I'm about to update it with the installation with the GUI. If it doesn't work, I'll have to download the ISO and load it up that way. Let's begin by going to System/Administration/Update Manager.  Hit Check to make sure I'm currently up to date then click Upgrade to get ready for 8.04. It popped up a Release Notes box, hit Upgrade and brought up a new window for upgrading.

The primary reason I've decided to go ahead and go to 8.04 is because I want this to be both a diary and somewhere for others to look for help. 7.10 is no longer supported, and 8.04 is the new LTS so here we go. 65 pages removed, 197 new and 869 upgraded. Downloading 667 MB at about 17 minutes. It's downloading at about 850 kb/s.

I remembered that I need to set up my printer, hopefully the settings will stay when the upgrade finishes. I went to System/Administration/Printing. I hit New Printer and it opened a new window. I'm a bit lost as to what to pick since my printer is on my network so I just tried AppSocket/HP JetDirect. I typed in the local IP and it brought up a new window to select what kind of printer I have. I put down the wrong internal IP but once I double checked I fixed it in Settings, and printed a test page, it worked.

Only 2 minutes remaining on 'Getting new packages' for the Distribution Upgrade, which is about how long left on my Smallville episode. Installing the upgrades shows 20 minutes left, time to start the next episode of Smallville. There isn't a lot I want to do right now as I don't know what's going to transfer over when I finish the 8.04 update, but I do want to figure out why my mic isn't working. I might as well update my port on the router for Azureus real fast.

Now for my audio issues. I recall mentioning the log on sound being loud and obnoxious, so my first stop is System/Preferences/Sound. I go to the Sounds tab and turn those off. Now for my mic, on Devices I show using CA0106 (Alsa mixer). I clicked Test on the Sound Capture: and didn't hear anything. Here's what I got:

ALSA &#8211; Advanced Linux Sound Architecture . . . . No Sound
OSS &#8211; Open Sound System . . . . No Sound
PulseAudio Sound Server . . . . ERROR
 . . . . gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused
Test Sound - I heard a weird beep.
Silence &#8211; No Sound, not unexpected.

Still have 6 minutes left on the update to 8.04. I closed the sounds setting and left the Sound Capture on ALSA setting. Maybe the default in 8.04 will set up properly for my mic. We'll find out as I'm going to watch some of Smallville until it's done. I tried to bookmark the diary in Firefox but it opened a blank window, very odd I'll see what happens after the 8.04 update. I started noticing audio is starting to get off at about 20 minutes on Totem, I'm not sure what to do with it yet, perhaps try a new video program.

The update to 8.04 is complete and honestly I'm happy. It went fast and easy, I think it took about 2 hours total, finished it at 20080607 0200. There are so many things I'd like to do, I think I'll start here in 8.04 with Compiz. This quite possibly could be the most fun thing about Linux, so I go to System/Administration/Synaptic Package Manager. I searched for Compiz and noticed quite a few things are installed already. I didn't know quite how to get to it, so I installed fusion-icon and emerald to check those out. Emerald didn't really have much to do with setting up Compiz, and I couldn't figure out the other one so I went ahead and uninstalled them.

I found this website, [http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200-p2](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200-p2) and it worked out perfect! I had absolutely no errors or problems setting up compiz. The last time I installed Ubuntu (7.10), it took me days to get everything figured out.

The update to 8.04 fixed the error with Firefox making bookmarks, which reminds me I need to install plugins for watching movies at collegehumor.com. I searched in Synaptic Package Manager for Firefox, and found Gnash and flashplugin-nonfree so I downloaded those. They worked fine for youtube.com and collegehumor.com. I decided to install Firestarter, a front end to the already installed firewall for Ubuntu, this done in Synaptic.

That's it for configuring Ubuntu tonight. Tomorrow I need to figure out the following:
 . . . . Get my mic working
 . . . . Finish configuring Compiz
 . . . . Set up Skype, Azureus and Pidgin to start on bootup using System/Preferences/Sessions
 . . . . Only one program can access my audio. I need to find out why and fix.
 . . . . Get my mic to work.

---

### Post by wolfen69 on 2008-06-07
good read. good luck with it.

---

### Post by chewearn on 2008-06-07
Ubuntu 7.04 is Feisty Fawn, while Gutsy Gibbon is 7.10.  You got either the version number, or the distribution name wrong.

---

### Post by wolfen69 on 2008-06-07
> **AstalaVista said:**
> Ubuntu 7.04 is Feisty Fawn, while Gutsy Gibbon is 7.10.  You got either the version number, or the distribution name wrong.

huh? does version number matter? :lolflag:

---

### Post by K7522 on 2008-06-07
> **AstalaVista said:**
> Ubuntu 7.04 is Feisty Fawn, while Gutsy Gibbon is 7.10.  You got either the version number, or the distribution name wrong.

Ahh you're right! Thanks for noticing, I ran cat /etc/issue and it shows ubuntu 7.10 \n \l so it is Gutsy Gibbon! I'll edit my original post thanks for noticing!

> **wolfen69 said:**
> if i had your bad luck, i would give up computers.

You have no idea how bad it's about to get. I've set up Linux before and had some huge problems with drivers. Let's hope it goes smoother this time around and get some fixes posted for others!

---

### Post by K7522 on 2008-06-07
06072008
Morning again! I'm still playing with Compiz, and set up Evolution mail. It went pretty fast, just clicked the letter on the top bar and entered the information based on my email. I added transparency to the background of Terminal. I went to Edit/Profiles and started a new one. Made sure to set “Profile used when launching a new terminal:” to my new one with transparency.

I installed Scribus with Synaptic, something that looked interesting for my writing needs when I was searching the net.

I've been toying with settings and found out some stuff with graphics that I don't particularly like. Perhaps the readers here will be able to help out. I've downloaded a few themes for Emerald and honestly I'll probably end up writing something of my own I like more. While that in itself isn't my problem, this is. Changing the color on the panel background via right click/Properties does change the background color, but not the color of the buttons on the bar. For that, you have to go to System/Preferences/Appearances. The only problem is changing the colors there edit the windows in the desktop along with the panels. I want a way to edit the panels, buttons and everything, without it changing the window colors on the rest of the desktop. It seems to me so many programs do all kinds of things to edit how Gnome looks, but there isn't an all intuitive program that I've found yet.

I don't know why but for some reason my download rate in Azureus is a bit off, I changed some things around but it didn't help much. I tried Deluge but it seemed to like to crash so I checked around and decided to just try Azureus again. I made sure every torrenting client was off the computer before reinstalling it all used via Synaptic. On the bright side it seems to be downloading at a higher pace once I changed a few settings like activating more than one connection per IP. Just needed to play with it apparently.

Decided to install screenlets-manager with synaptic and downloaded some at gnome-look.org. Went pretty easy and only took about 10 minutes to download and get everything the way I wanted. 

I want to take the time to say that this install so far has gone the smoothest I've ever had in Linux. I've only run Fedora and Ubuntu before, but they've always taken a very long time to get things working. It's been a breeze so far and I'm excited to say this is going well. I haven't fixed my mic yet, so let's hope that isn't a headache. It works fine in Windows so it's going to have to be something to do with settings.

I'm getting some artifacts in videos the past few videos I'm not sure if it's the file or the Totem video client, it even might be the codecs. I'm going to have to check that out.

I remembered how I used to watermark movies over my entire desktop, so I had to go set that up. I downloaded xwinwrap from somewhere online and installed mplayer with synaptic so that I could do it. For ease, I saved the following command into an easy to access text file:
```

xwinwrap -ni -o 0.4 -fs -s -nf -sp -- mplayer -wid WID -quiet '/MEDIA FILE'

xwinwrap [-g] [-ni] [-argb] [-fs] [-s] [-st] [-sp] [-a] [-b] [-nf]
       [-fl] [-o OPACITY] -- COMMAND ARG1...

 -g       geometry
 -ni      no input
 -argb    argb ?? Alpha, Red, Green, Blue ??
 -fs      fullscreen
 -s       sticky
 -st      skip taskbar
 -sp      skip pager
 -a       above
 -b       below
 -nf      noFocus
 -o       opacity=#   Between 0 and 1

```
I still haven't done some things I need to on the computer, so here's my list for tomorrow:
 . . . . Get my mic working
 . . . . Figure out why I'm getting artifacts on video, audio goes off after about 20 minutes as well
 . . . . Figure out how to get more control over my panels
 . . . . Find a native program for programming, highlighting context and the like. Don't need it, but it makes life easier.
 . . . . Find a nice screensaver

---

### Post by K7522 on 2008-06-08
Third day and I must say I've been slacking a bit on getting my mic to work. I know it's going to be hard as hell to figure. I downloaded a GUI for Alsa mixer in Synaptic, my Mic sliders were very low so I turned it all the way up. I tried making a call to the test center in Skype but there was an error attaching to my audio card. I'm going to have to figure that out before I can work on my mic. Somehow I feel like this is only the beginning of my troubles.

A post here; [http://ubuntuforums.org/showthread.php?p=4526153](http://ubuntuforums.org/showthread.php?p=4526153) states the following.
First of all: Ubuntu Hardy uses PulseAudio to manage its sound. This has numerous benefits, including full functionality of USB headsets, networked sound (e.g. having sound from one computer played on another), among other stuff.

Secondly: Skype particularly is configured to use ALSA and nothing else. In fact, it goes so far as to prevent PulseAudio's ALSA-to-PulseAudio plugin from working. As a result, Skype can only grab your sound card when it needs to use it, and release it when it doesn't. Therefore you have two choices: Let PulseAudio grab the sound card and allow all other sound to reach the sound card through PulseAudio's mixing, or, let Skype grab the sound card.

So basically Skype in ALSA doesn't play well with PulseAudio, which is what Ubuntu uses. The time I spend now will be used to try to get Skype to work simultaneously with other audio programs. I will be running Rhythmbox with music going through this entire endeavor. I begin by following the how-to here, [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739) but it failed to fix the problem. It did get an interesting plugin for PulseAudio in my hotbar though, so I won't be reversing the effects of what was done there.

My setup in System/Preferences/Sound is now at PulseAudio Sound Server for all except the last, Default Mixer Tracks. The how-to said to set your sound card's name but it wasn't an option. It's currently at CA0106 (ALSA Mixer)

I followed the posts here, [http://ubuntuforums.org/showpost.php?p=4526841&postcount=10](http://ubuntuforums.org/showpost.php?p=4526841&postcount=10)  / [http://ubuntuforums.org/showpost.php?p=4526648&postcount=9](http://ubuntuforums.org/showpost.php?p=4526648&postcount=9) / all without success as well.

I honestly have no idea what to do to fix this, and I'm tired of trying right now. I also have no idea how I'm going to get control over panel configuration beyond editing the look of my windows and I'm a bit too frustrated to figure that out as well. I also found out that logging out before closing Skype fully bugs it out and even with killall and kill commands the file won't terminate (viewed by command &#8220;ps ax | grep skype&#8221;)

---

### Post by Sinkingships7 on 2008-06-09
I can confidently suggest Geany for your programming needs.

Make sure you have build-essential installed
```
sudo aptitude install build-essential
```
and then
```
sudo aptitude install geany
```

---

### Post by mdsmedia on 2008-06-10
K7522,

Thanks for a really interesting and possibly helpful thread.

I'm running Dapper on my notebook, and a seemingly continually partially upgraded Gutsy on my desktop.

In the next few days (weeks?) I'm planning to clean install probably Gutsy on my desktop, Windows in VM (fingers crossed)....and if all successful do the same on my notebook.

I will also try installing on my USB drive, because both my desktop and notebook drives are reasonable small and currently dual-boot.... so there is not much space for experimentation. My desktop isn't critical, so I'll use it to experiment.

My desktop demands don't appear as great as yours, so far, but the more I play the more demands I'll place on the system.

Here's to the ability to play.

---

### Post by stchman on 2008-06-10
Kathor, I have found this to be the best method to install Ubuntu.

1.  Create free space.  Boot up the LiveCD and fire up gparted.
2.  Create about 40GB (if you have that much) of free space by deleting and repartitioning.
3.  Select install.
4.  When prompted tell the installer to use the largest continuous free space.
5.  Continue the install.
6.  You should be up an running in about 20 minutes.

I have used this method on at least 7 different machines and Ubuntu always works excellent.

I have not tried installing Ubuntu through Windows, wubi, vmware, etc. so I cannot comment on those.

I would have selected Hardy over Gutsy.  Reason is that the nvidia-glx-new package is only 100.xx for Gutsy and 169.12 for Hardy.  The 8800GT needs the 169.12 to run properly.

Also don't do the upgrade route.  I have never had any luck with that.

---

### Post by K7522 on 2008-06-10
I recently found an old .bin/.cue file on my file drive, and found out there was no direct way to mount it. I had to follow the guide here, [http://techbycolin.com/?p=130](http://techbycolin.com/?p=130) but it didn't work so I just took care of it in windows.

I set up samba for the computer using [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) as a guide, also set up ssh

Don't forget to do &#8220;sudo /etc/init.d/ssh start&#8221; so that sshd starts when you boot 'nux!

I had a rough time getting samba to work properly not the program itself but my smb.conf file. I pretty much had to write one based on some of the comments on the net. Here it is below.

```
[global] 
workgroup = mshome 
netbios name = kurt-desktop 
server string = %h 
log file = /var/log/samba/log.%m 
max log size = 1000 
invalid users = root 
wins support = no 
dns proxy = no 
guest account = nobody 
security = user 
encrypt passwords = yes 
guest ok = yes 
username map = /etc/samba/smbusers 
panic action = /usr/share/samba/panic-action %d 

[homes] 
path = /home 
available = yes 
browseable = yes 
guest ok = no 
writeable = no 

[sda2] 
path = /media/sda2 
available = yes 
browseable = yes 
guest ok = no 
writeable = yes
```

I also enabled remote access with VNC by going to System/Preferences/Remote Desktop.

I had some problems earlier with gaining access to some commands under System/Administration so I had to add gksu to the beginning of the commands in there. Go to System/Preferences/Main Menu and right click on the item you have problems with, and set gksu at the beginning of the command.

I had to open ports with Firestarter to get everything to work properly, so now I have ports open for Azureus, Samba, VNC, three other ports in a range open I can't recall why. I'll have to find out and note accordingly.

Got a green bar, artifact if you will trying to play a .avi file today, had to install and use VLC and fixed it by a post here [http://ubuntuforums.org/showpost.php?p=1787013&postcount=2](http://ubuntuforums.org/showpost.php?p=1787013&postcount=2) stating &#8220;Settings > Preferences > Video > Output Modules (check the Advanced options in the bottom right hand corner) > Change "Video Output Module: Default" to "Video Output Module: X11 Video Output"&#8221; 

> **Sinkingships7 said:**
> I can confidently suggest Geany for your programming needs.

Make sure you have build-essential installed
```
sudo aptitude install build-essential
```
and then
```
sudo aptitude install geany
```

Thanks for the suggestion, I've just installed it and I definitely like what I see, I'll be keeping it and see how it goes over the next few days when I find the time to write something.

> **mdsmedia said:**
> K7522,

Thanks for a really interesting and possibly helpful thread.

I'm running Dapper on my notebook, and a seemingly continually partially upgraded Gutsy on my desktop.

In the next few days (weeks?) I'm planning to clean install probably Gutsy on my desktop, Windows in VM (fingers crossed)....and if all successful do the same on my notebook.

I will also try installing on my USB drive, because both my desktop and notebook drives are reasonable small and currently dual-boot.... so there is not much space for experimentation. My desktop isn't critical, so I'll use it to experiment.

My desktop demands don't appear as great as yours, so far, but the more I play the more demands I'll place on the system.

Here's to the ability to play.

I haven't gotten around to trying VM yet, keep me in the loop on how it works out. I hope to bring even more demand to my system soon when I start playing a few games I missed, and trying to get them to work under Linux. Here's to hoping it isn't a living hell.

> **stchman said:**
> Kathor, I have found this to be the best method to install Ubuntu.

1.  Create free space.  Boot up the LiveCD and fire up gparted.
2.  Create about 40GB (if you have that much) of free space by deleting and repartitioning.
3.  Select install.
4.  When prompted tell the installer to use the largest continuous free space.
5.  Continue the install.
6.  You should be up an running in about 20 minutes.

I have used this method on at least 7 different machines and Ubuntu always works excellent.

I have not tried installing Ubuntu through Windows, wubi, vmware, etc. so I cannot comment on those.

I would have selected Hardy over Gutsy.  Reason is that the nvidia-glx-new package is only 100.xx for Gutsy and 169.12 for Hardy.  The 8800GT needs the 169.12 to run properly.

Also don't do the upgrade route.  I have never had any luck with that.

That's basically how I did it, installing Gutsy though. I did end up going through the upgrade process though, and with the OS being almost completely barebones it worked flawlessly. I had a problem upgrading before, it probably has something to do with my video settings (as it took a long time to get it to work on my previous install). I am currently under a fully up to date OS. My kernel is 2.6.24-18-generic under 8.04 Hardy Heron.

Currently my problems lie more in audio than anything. I haven't tried messing with it since the one day, and rightfully so to keep my sanity. What I have done I posted in comment #7, [http://ubuntuforums.org/showpost.php?p=5143496&postcount=7](http://ubuntuforums.org/showpost.php?p=5143496&postcount=7) and haven't touched it further. Skype is currently uninstalled since it has no use whatsoever with my current configuration.

I must say I'm quite happy with Azureus right now. Over the past two days I've been averaging about 1mb/sec down and a considerable upload speed. Some of these I've been burning to CD's for friends. I've been using DVD-R's since the packages are so huge. Unfortunately my laptop is the only DVD-RW I have in the house, so the projects have been streaming across a wireless connection. Makes it go a bit slow, takes about an hour to burn a disk of about 4.5 GB but I've just been going to do other things.

---

### Post by hyper_ch on 2008-06-17
it's been quite a while since you wrote last time... so things going well?

---

### Post by K7522 on 2008-06-19
It has indeed been a while. I'll post what I've had in queue;

I decided to try setting up VMware, but running vmware-install.pl was giving me a hastle, not sure why as I've already had to install the prereqs for previously installed programs. I decided to install Alien which is a program that translates rpm files to deb (among other packages) to transfer the VMware file to a deb. I installed that and epic failed. I found this page, [http://ubuntuforums.org/showpost.php?p=4357442](http://ubuntuforums.org/showpost.php?p=4357442) which went through step by step to properly config VM to work on the computer. When I first tried to use the vmware-install.pl again it said there was a previous installation already there, so I had to run &#8220;rm -rf /etc/vmware&#8221; in terminal to get it to work.

Since I'm going to be setting up XP in VM to see how that goes, I changed my grub to only wait 2 seconds before going directly into Ubuntu by doing &#8220;sudo gedit /boot/grub/menu.lst&#8221; and changing &#8220;timeout&#8221; to 2

After getting VMware up it went without a hitch. I'm installing Windows XP right now and may install Fedora just for giggles. Not sure yet, but I definitely want to play with it a bit. It's a big option that I may endorse. If it's easy to get to for the girlfriend I may just format that other partition for more space for Ubuntu.

I finished installing windows under VMware, works great once you get VMTools installed, just have to right click on the specific virtual tab and click Install VMware Tools. Haven't tested gaming under VMware but I'm very skeptical.

I've been working hard on a few clients' websites, and just received two new offers that I'm looking at. While I'll have a much more detailed post later, maybe when I get time tonight, quite simply I installed Apache2 since my hosting service is giving me issues, and I've begun having problems with samba. The computer can be seen on the windows PC, but attempting it gives a "The network path was not found." error, I think it has something to do with samba and apache2 not playing nice together. I haven't had time to bug that out or any of my other problems as of yet. More information tonight.

---

### Post by hyper_ch on 2008-06-19
I'm afraid to disappoint you but apache2 and samba do not interfere with each other...

Do you use static IPs on your home network?

---

### Post by K7522 on 2008-06-21
I do have static IP's, this computer's been leased it's current IP for the past few  months. I'd stay for more information but... paintball this morning! Oorah

---

### Post by hyper_ch on 2008-06-21
paintball ;)

---

### Post by K7522 on 2008-06-23
Out of pure chance I decided to check my firewall and sure enough, I had erased the Samba ports for reasons still unknown to myself. Hyper_ch was correct in his post above, referenced below.

> **hyper_ch said:**
> I'm afraid to disappoint you but apache2 and samba do not interfere with each other...

I honestly feel silly, almost sheepish that it was so simple as erasing the firewall rule.

I've been way too busy with web development to mess with much of my OS. Suffice to say it's working flawlessly for what I need it right now. I still haven't tried to get Skype working with other audio programs yet, I still think it's going to be rough on me. I've had to use my laptop for skype communications. Also, waiting for wine to get working with Age of Conan, currently going to Windows for that. More when I'm not as busy.

---

### Post by hyper_ch on 2008-06-23
for skype just add the medibuntu repos... works like a charm.

---

### Post by K7522 on 2008-06-23
Wow how easy was that?

> **hyper_ch said:**
> for skype just add the medibuntu repos... works like a charm.

I did a search online for medibuntu and got to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) where there were repos to install. I did that, and went to Skype to redownload the .deb for skype. Come to find out I didn't even need to, the repo had already reinstalled the package. I had to reupdate my computer as things were &#8220;out of date&#8221; ie didn't exist. Then I ran the test call, didn't hear myself so I opened up Skype and disabled it automatically changing my mic in volume and went to volume control.

Went to Edit/Preferences and turned everything on so I could see, turned up CAPTURE Feedback in Playback and turned up everything in Recording. I then had to go to Options and change Shared Mic/Line in to Mic in and it worked fine. It only pipes out the left ear, which is fine I'll be able to run my music through the right. That's all the fun I have time for today on my Ubuntu setup, and honestly there's not much left to do besides game installations. I've been keeping track of Age of Conan off and on in WineHQ.org but nothing's come up yet that will allow you to play it in 'nux. Hopefully it will come around soon.

EDIT: Skype doesn't work when other audio programs are going, but it's a start.

---

### Post by K7522 on 2008-07-25
I really haven't had much time to toy with Ubuntu, just keeping it up to date sometimes takes a conscious effort, that being clicking the update icon in the top right.

I leave for some time September 8, and I've been burying my head deep in coding trying to keep my mind off of what is about to happen.

Skype still doesn't play well with other audio, and it also only outputs to left side speaker (headphones) but again I haven't had time to toy with it.

---

### Post by steveneddy on 2008-07-26
I just don't understand why you installed an old version and you were trying to set it up while at the same time updating to Hardy?

Why not just cut to the chase and install Hardy out of the box?

---

### Post by steveneddy on 2008-07-27
> **hyper_ch said:**
> for skype just add the medibuntu repos... works like a charm.

Yes - and don't forget the restricted extras also.

---

### Post by K7522 on 2008-07-27
> **steveneddy said:**
> I just don't understand why you installed an old version and you were trying to set it up while at the same time updating to Hardy?

Why not just cut to the chase and install Hardy out of the box?

I had an old CD and wanted to see if install and update would work before downloading the new ISO and using another CD. It worked, so that's how I left it. 

> **steveneddy said:**
> Yes - and don't forget the restricted extras also.

I'm not sure what you're suggesting, a different .deb to add functionality?

---

### Post by steveneddy on 2008-07-27
If you have all of the repositories enabled in

System > Administration > Software Sources

then in terminal type

```

sudo apt-get install ubuntu-restricted-extras


```

Also, look at my sig and there are two links there for Ubuntu Guide and Ubuntu Resources.

Those are two very important links that you should bookmark for future reference. Just FYI.

---

### Post by Sef on 2008-07-27
> If you have all of the repositories enabled in

System > Administration > Software Sources


To be more exact:

System > Administration > Software Sources > Ubuntu Software > enable universe and multiverse

There are other repositories, but you do not need them.

---

### Post by K7522 on 2008-08-03
Ahh, yes I had those enabled already, I think I had to for an install somewhere, can't quite recall.

---

### Post by K7522 on 2008-08-17
Wow it's been a long time since I posted a proper update here, let's go for it.

I've been doing a lot of programming lately, PHP mostly which isn't particularly OS specific. I love using Geany. I used Notepad++ in Windows, there are a few things I like in that that Geany doesn't have, but I figure it's working out well for me.

I just finished working on a completely automated shell script with a bit of assistance from Perl and the community here. It ended up being about 150 lines which is the first programming I've done outside PHP and HTML I've ever done. It's a bit messy and I'm sure it could have been done a lot easier and with fewer lines but I enjoyed doing it.

As far as my OS, I'm starting to get tired of the offwhite window color, but I haven't gotten around to changing it yet. I love the six desktops I have in Ubuntu, it's wonderful for programming. You can never have enough deskspace I'm finding.

I wanted to set up System Monitor to CTRL+ALT+DEL so here's what I did:
System->Preferences->Keyboard Shortcuts
Desktop -> Logout and hit BACKSPACE to remove the shortcut.
```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

Sometimes Firefox wants to crash, but restarting it restores all the windows/tabs that I have up.

Skype! Oh the joy of Skype...
I hate thee.
I haven't tried to get it to run with other sounds, whenever someone calls I have to shut down anything that's picked up sound (even Firefox when I run vids) and it's very annoying.
As far as it running only one ear, it still does unless I pull the plug out about 1/4 the way, then Skype will project both ears.

Everything except Skype projects to both ears with it plugged in all the way. Everything including Skype projects to both ears when it's pulled out about 1/4.

Any thoughts on that would be helpful.

So I've decided to edit my look and feel, I am currently working on my icons. Then I'll get my cursor and background changed. My icons for volumes (hard drives, CD's and the like) aren't showing up, although I know they exist as you can see in the 'places'. I need a way to manually adjust those icons.

I downloaded quite a few icon sets actually from gnome-look.org and this one looks the most complete and best for the look I'm going for. Each one of these themes would forgo skinning these volumes.

[Screenshot]("http://img515.imageshack.us/img515/2744/iconsvt4.png")

I installed a new mouse theme. Downloaded the file, extracted it to folder form. Right click on desktop -> Change Desktop Background -> Theme -> Customize -> Pointer, then drag and dropped the folder and clicked install.

The install didn't work everywhere. I had to go to terminal, type cssm to open up my compiz-fusion settings. Go to General -> Cursor Theme and typing in my new cursor. It worked fine after that.

I don't like one of the cursors in this theme, so I'm going to figure out how to change that.

---

### Post by K7522 on 2008-08-17
Being fairly new to writing in bash, I wrote this "simple" script to duplicate icon images from one filetype to another in 16x16, 22x22, 32x32, 48x48, 64x64 and 128x128. It is 264 lines and can be easily adapted for other mass copy/delete functions.

I came to this because I wanted to set a particular icon to a filetype, but I didn't know what size it used so why not just change them all? Well, it took some time, but not as much time as coding this. It helped me learn a few things in coding these kinds of things. Comments welcome.

I know, I put in next to no comments (only two) and I normally put more. Not sure why I didn't or haven't yet. I think I'm in code overload, I just tried to CTRL+S to save this edit.

```

#!/bin/bash
# For use in ~/.icons/your_icon_folder

function vars {
inputfile="Define input file."
outputfile="Define output file."
deletefile="Define a file to delete."
deletefolder="Select the folder file is under."
folder="Select the folder file is under."
delete_directory_input=""
duplicate_directory_input=""
main_directory_input=""
ETC=""
if [ "$menu" = "0" ]; then
main_directory
else
  if [ "$menu" = "1" ]; then
  duplicate_directory
  else
    if [ "$menu" = "2" ]; then
    delete_directory
    else
    main_directory
    fi
  fi
fi
}

function delete {
if [ "$deletefile" = "Define a file to delete." ]; then
echo -e "You have not defined a file to delete."
get_deletefile
else
  if [ "$deletefolder" = "Select the folder file is under." ]; then
  echo -e "You have not defined a folder for the file."
  get_deletefolder
  else
  echo -e "Deleting files."
  if [ -e ./16x16/$deletefolder/$deletefile ]; then
  rm ./16x16/$deletefolder/$deletefile
  else
  echo -e "File does not exist in 16x16, moving on."
  fi
  if [ -e ./22x22/$deletefolder/$deletefile ]; then
  rm ./22x22/$deletefolder/$deletefile
  else
  echo -e "File does not exist in 22x22, moving on."
  fi
  if [ -e ./32x32/$deletefolder/$deletefile ]; then
  rm ./32x32/$deletefolder/$deletefile
  else
  echo -e "File does not exist in 32x32, moving on."
  fi
  if [ -e ./48x48/$deletefolder/$deletefile ]; then
  rm ./48x48/$deletefolder/$deletefile
  else
  echo -e "File does not exist in 48x48, moving on."
  fi
  if [ -e ./64x64/$deletefolder/$deletefile ]; then
  rm ./64x64/$deletefolder/$deletefile
  else
  echo -e "File does not exist in 64x64, moving on."
  fi
  if [ -e ./128x128/$deletefolder/$deletefile ]; then
  rm ./128x128/$deletefolder/$deletefile
  else
  echo -e "File does not exist in 128x128."
  fi
  echo -e "Complete. Press [Enter] to continue."
  read ETC
  menu="2"
  vars
  fi
fi
}

function delete_directory {
clear
echo -e "Icon Modifier | Deletion Directory"
echo -e "  1) $deletefile"
echo -e "  3) $deletefolder"
echo -e "  5) Run"
echo -e "  7) Return to Main Directory"
echo -e "  0) Quit"
echo -e ""
echo -e "Select one."
read delete_directory_input
if [ "$delete_directory_input" = "1" ]; then
get_deletefile
else
  if [ "$delete_directory_input" = "3" ]; then
  get_deletefolder
  else
    if [ "$delete_directory_input" = "5" ]; then
    delete
    else
      if [ "$delete_directory_input" = "7" ]; then
      main_directory
      else
        if [ "$delete_directory_input" = "0" ]; then
        clear
        exit
        else
        echo -e "Unrecognized choice. Please select again."
        delete_directory
        fi
      fi
    fi
  fi
fi
}

function duplicate {
if [ "$inputfile" = "Define input file." ]; then
echo -e "You have not defined an input file."
get_inputfile
else
  if [ "$outputfile" = "Define output file." ]; then
  echo -e "You have not defined an output file."
  get_outputfile
  else
    if [ "$folder" = "Select the folder file is under." ]; then
    echo -e "You have not defined a folder for the file."
    get_folder
    else
    echo -e "Duplicating files."  
    if [ -e ./16x16/$folder/$inputfile ]; then
    cp ./16x16/$folder/$inputfile ./16x16/$folder/$outputfile
    else
    echo -e "File does not exist in 16x16, moving on."
    fi
    if [ -e ./22x22/$folder/$inputfile ]; then
    cp ./22x22/$folder/$inputfile ./22x22/$folder/$outputfile
    else
    echo -e "File does not exist in 22x22, moving on."
    fi
    if [ -e ./32x32/$folder/$inputfile ]; then
    cp ./32x32/$folder/$inputfile ./32x32/$folder/$outputfile
    else
    echo -e "File does not exist in 32x32, moving on."
    fi
    if [ -e ./48x48/$folder/$inputfile ]; then
    cp ./48x48/$folder/$inputfile ./48x48/$folder/$outputfile
    else
    echo -e "File does not exist in 48x48, moving on."
    fi
    if [ -e ./64x64/$folder/$inputfile ]; then
    cp ./64x64/$folder/$inputfile ./64x64/$folder/$outputfile
    else
    echo -e "File does not exist in 64x64, moving on."
    fi
    if [ -e ./128x128/$folder/$inputfile ]; then
    cp ./128x128/$folder/$inputfile ./128x128/$folder/$outputfile
    else
    echo -e "File does not exist in 128x128."
    fi
    echo -e "Complete. Press [Enter] to continue."
    read ETC
    menu=1
    vars
    fi
  fi
fi
}

function duplicate_directory {
clear
echo -e "Icon Modifier | Duplicate Directory"
echo -e "  1) $inputfile"
echo -e "  2) $outputfile"
echo -e "  3) $folder"
echo -e "  5) Run"
echo -e "  7) Return to Main Directory"
echo -e "  0) Quit"
echo -e ""
echo -e "Select one."
read duplicate_directory_input
if [ "$duplicate_directory_input" = "1" ]; then
get_inputfile
else
  if [ "$duplicate_directory_input" = "2" ]; then
  get_outputfile
  else
    if [ "$duplicate_directory_input" = "3" ]; then
    get_folder
    else
      if [ "$duplicate_directory_input" = "5" ]; then
      duplicate
      else
        if [ "$duplicate_directory_input" = "7" ]; then
        main_directory
        else
          if [ "$duplicate_directory_input" = "0" ]; then
          clear
          exit
          else
          echo -e "Unrecognized choice. Please select again."
          duplicate_directory
          fi
        fi
      fi
    fi
  fi
fi
}

function get_deletefile {
echo -e "What file are we deleting?"
read deletefile
delete_directory
}

function get_deletefolder {
echo -e "What folder are we using?"
read deletefolder
delete_directory
}

function get_folder {
echo -e "What folder are we using?"
read folder
duplicate_directory
}

function get_inputfile {
echo -e "What file are we copying?"
read inputfile
duplicate_directory
}

function get_outputfile {
echo -e "What file are we creating?"
read outputfile
duplicate_directory
}

function main_directory {
clear
echo -e "Icon Modifier | Main Directory"
echo -e "  1) Copy a file."
echo -e "  2) Delete a file."
echo -e "  0) Quit"
echo -e ""
echo -e "Select one."
read main_directory_input
if [ "$main_directory_input" = "1" ]; then
duplicate_directory
else
  if [ "$main_directory_input" = "2" ]; then
  delete_directory
  else
    if [ "$main_directory_input" = "0" ]; then
    clear
    exit
    else
    echo -e "Unrecognized choice. Please select again."
    main_directory
    fi
  fi
fi
}

# Run the program.
vars

```

Yes... I could have used elif, if I knew it existed at the time of writing this.

---

### Post by K7522 on 2008-08-19
I bought a new phone, Samsung Instinct, and Sprint has released the development files for applications which is heavily reliant on Java. All of the utilities are for winblows, I'm going to take a look at some of the code in there and see if I can't get it going to unix.

Ubuntu, unsurprisingly won't even recognize that the device is plugged in. It does have an 8gb microSD card in it so I'm very excited to see what we can get done.

As is, Instinct has no IM application (Trillian, Pidgin, etc.) so if nobody has something up in the time it takes me to get my Ubuntu happy with my Instinct I may take that on!

kthxbai

Oh, having lots of fun with my new unlimited internet (and irritating my significant other too!) So if anyone is interested in assisting in any java projects hollar on AIM, it's listed on my account. Email would work too at [email]lanweni@hotmail.com[/email]

Off to mess with stuff!

---

### Post by GIJ0E69 on 2008-08-31
Eye Balls, Click Sir! What's up Devil Dawg!!!! Hooo ******* rahhhh!!! Ubuntu is freggin! great! its like getting ****** up by D.I.'s on the quarter deck @ MCRD....lol...... I still see that you put <Year><Month><Date> still in place haha...I have been out for about 3 years now...I was staioned @ Yuma Arizona MOS was 3112 lol

---

### Post by K7522 on 2009-03-01
Forever, it's been forever! Six months in fact. Wow, how much has happened since then... I guess I should start where I left off.

I never did work on that phone. I still have it, and I only have one issue with it, and that is the inability to multitask. It can only run one function at a time. I guess I've gotten way too busy, and things have been falling by the wayside.

I finally calmed down on modifying Ubuntu. In fact, I haven't even upgraded to the latest versions. Instead I invested my time away from the computer. Yes, indeed, I saw the sun, and it was indeed as bright and painful as everyone says.
:lolflag:

I've invested a lot of time in C++ lately, trying to relearn it. you tend to forget things over time. I've also been investing time again into websites, [www.heislen.com](www.heislen.com) is my personal website I'm running with xampp. I love how far the website is coming, though I really need to decide on what I want to do with it, and stick to that kind of content. Right now it's just pretty much anything that's on my mind at the time.

I've been building a new business with my time too, ontop of finishing college. All these things added up one can see why I literally forgot about all of you wonderful people.

Maybe I'll start toying with Ubuntu again so I'm not so off topic! :)

---

### Post by K7522 on 2009-03-02
My first relevant listing here in a while, it's going to be short though.

I decided to upgrade my desktop to 8.10, since it doesn't have a CD drive at the moment I downloaded the iso, moved the files in isolinux to the home directory and renamed isolinux.cfg to syslinux.cfg.

I dragged it all and booted to the USB drive and it worked like a charm.

Fresh install of Ubuntu! YAY. I activated my nVidia drivers, downloaded ccsm for compiz and that was it. Literally, easiest install I've ever had. It even recognized my wireless and wired network connections without issue. I also downloaded the medibuntu repos so that Skype would work.

I also want to install a Windows on VM so that I can play with some stuff there. I haven't done that yet, I still haven't gathered all of the windows files yet.

I figured I would put it on the laptop too, but I'm having some issues there. It boots to the USB device, and I choose run Ubuntu without changes and after the scrolling bar loading Ubuntu, the screen goes white where it would normally display the desktop. The sounds are on, and I can hear the booting sounds. The white fades to black over time. I'm not sure what the issue is yet, I've attempted it with both 32 and 64 bit versions. (Prefer 64). 

So here's to figuring it out.

I'd like to make a very strong point.
Rhythmbox + Last.FM account
= All my great music, and 200GB newly freed space.

---

### Post by solwic on 2009-03-02
> **K7522 said:**
> 
I figured I would put it on the laptop too, but I'm having some issues there. It boots to the USB device, and I choose run Ubuntu without changes and after the scrolling bar loading Ubuntu, the screen goes white where it would normally display the desktop. The sounds are on, and I can hear the booting sounds. The white fades to black over time. I'm not sure what the issue is yet, I've attempted it with both 32 and 64 bit versions. (Prefer 64). 

So here's to figuring it out.

I'd like to make a very strong point.
Rhythmbox + Last.FM account
= All my great music, and 200GB newly freed space.

Sounds like a video driver problem.  The white screen could (usually does) mean incorrect video drivers, and I imagine it fades to black because the screensaver/power manager kicks in.  

Good luck.  :)

---

### Post by K7522 on 2009-03-02
> **jrock612 said:**
> Sounds like a video driver problem.  The white screen could (usually does) mean incorrect video drivers, and I imagine it fades to black because the screensaver/power manager kicks in.  

Good luck.  :)

Thanks, it slowly fades to black and there's a weird square pattern that's lighter as it fades away than the rest of it. I imagine I'll have to take a look at finding out what drivers it loads, and (maybe) forcing different drivers to load perhaps... thanks for the idea, I have no idea where to start, I didn't find anything similar that's clearly defined when I googled (which is what I inteded this thread for, very clearly defining issues and fixes for them so that I and others can benefit from it in the future.)

---

### Post by solwic on 2009-03-02
> **K7522 said:**
> Thanks, it slowly fades to black and there's a weird square pattern that's lighter as it fades away than the rest of it. I imagine I'll have to take a look at finding out what drivers it loads, and (maybe) forcing different drivers to load perhaps... thanks for the idea, I have no idea where to start, I didn't find anything similar that's clearly defined when I googled (which is what I inteded this thread for, very clearly defining issues and fixes for them so that I and others can benefit from it in the future.)

You have an nVidia card?  When you get the white screen, try pressing ALT+F1 or ALT+F2 (can't remember which it is).  One (or both) of them will bring you to a terminal.  Try running this command (you'll need an Internet connection):

```
sudo apt-get install nvidia-180-kernel-source nvidia-180-modaliases nvidia-glx-180
```

That should install the nVidia 180.11 drivers from the repos.  Once they're installed, reboot and see what it does.

Please keep in mind that I'm no Linux expert, and that this is only what I would try if I were faced with your problem.  

Also, does the video card/screen work with any other OS (Windows, Mac, whatever)?  Just to rule out hardware failure, you know.  :)

Anyway, good luck!

---

### Post by K7522 on 2009-03-02
It's definitely not a hardware issue, it's software. I can boot Linux with safe mode graphics, but I don't see anything in System -> Admin -> Hardware Drivers when I go on there.

I ran "lspci" to find:

00:02.0 VGA compatable controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

I'm doing some searches on the internet with that new data, not turning anything up yet though unfortunately. Also, I didn't find the 180's in the repos, 177 was the highest I found.

---

### Post by solwic on 2009-03-02
> **K7522 said:**
> It's definitely not a hardware issue, it's software. I can boot Linux with safe mode graphics, but I don't see anything in System -> Admin -> Hardware Drivers when I go on there.

I ran "lspci" to find:

00:02.0 VGA compatable controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

I'm doing some searches on the internet with that new data, not turning anything up yet though unfortunately. Also, I didn't find the 180's in the repos, 177 was the highest I found.

That's odd...the 180's are in my repos.  You using 8.10, right?

Did you double check the command?  I pasted it from my TIPS file, which is how I run it.  Maybe you missed a space or something?  

Unless it's because I have the medibuntu repos enabled.  I noticed I couldn't get skype through apt-get until I added medibuntu.

Maybe that's it.

[www.medibuntu.org](www.medibuntu.org)

Might try posting in the General Help forum, if you haven't already.  Those guys know way more than I do.  :P

Good luck.  I hope you get it working.  :)

---

### Post by K7522 on 2009-03-02
Yeah I considered posting there, but I like my little corner of the forums!

I'll have to try installing medi, I had to for skype on my desktop (this computer I'm typing on) too. I'm afraid this is a bit out of my hands though here.

---

### Post by K7522 on 2009-03-03
I'm not giving up, but I'm putting it off. I just can't seem to break this thing right now.

---

### Post by K7522 on 2009-03-03
I've posted in the Help forum without much success yet:

Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > General Help

[http://ubuntuforums.org/showthread.php?t=1085281](http://ubuntuforums.org/showthread.php?t=1085281)

Here's  my latest post. Just updating my journal here more than anything. If anyone has ideas feel free to throw them out here.

--- My Latest Post ---

I managed to install Envy, and installed some drivers.
sudo apt-get install envyng-qt envyng-core
sudo envyng -t

When I boot, it warns:
(EE) No devices detected

But at least it allows me to boot into a safe graphics mode this time, so it's a step ahead of where I was. Any help would be most appreciated!

Here is my xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Driver    "nvidia"
EndSection
```

Here is my Xorg.0.log:

```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  3 13:39:18 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 9

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x0000e140/8
(--) PCI: (0@0:2:1) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xd0400000/1048576
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.12  Thu Jul 17 18:36:30 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.5.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.5.0, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.1.0
    ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 4.1
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 131008 kB
(II) VESA(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 169 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16b (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16c (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16d (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16e (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 16f (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 170 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 171 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 14d (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 15c (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 14b (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 15a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 107 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 11a (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 11b (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 169
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 169
    LinNumberOfImagePages: 169
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 106
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 106
    LinNumberOfImagePages: 106
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 135
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 135
    LinNumberOfImagePages: 135
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 67
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 67
    LinNumberOfImagePages: 67
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 152
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 152
    LinNumberOfImagePages: 152
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 254
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 254
    LinNumberOfImagePages: 254
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0008295
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 203
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 203
    LinNumberOfImagePages: 203
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 2047 64KB banks (131008kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 131008 kB
(II) VESA(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7f0ac79be000,
    physical address = 0xc0000000, size = 134152192
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(WW) VESA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.0.99
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event9"
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 0.15.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event10"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event4"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Sony Vaio Keys
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event5"
(II) Sony Vaio Keys: Found 1 mouse buttons
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sony Vaio Keys: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sony Vaio Keys: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Sony Vaio Keys: xkb_layout: "us"
(**) Sony Vaio Keys: YAxisMapping: buttons 4 and 5
(**) Sony Vaio Keys: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Tue Mar  3 13:39:21 2009: 5870 X: client 4 rejected from local host ( uid=0 gid=0 pid=5891 )
AUDIT: Tue Mar  3 13:39:35 2009: 5870 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5893 )
AUDIT: Tue Mar  3 13:39:35 2009: 5870 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5894 )
AUDIT: Tue Mar  3 13:39:35 2009: 5870 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5895 )
```

---

### Post by K7522 on 2009-03-03
Well, I got it to load properly now. I had to edit xorg.conf to the following code. I did a lot before too, so to narrow it down I think I'm going to reinstall fresh, edit this and see what happens. Then I can install the packages I did before one by one to find exactly what has to happen.

Section "Device"
BoardName "Mobile Intel GM45 Express Chipset"
Driver "intel"

---

### Post by K7522 on 2009-03-03
I did a fresh install of Ubuntu 8.10 64 bit on my VGN-FW270J. I found out that the stuff is NOW supported, but it wasn't at release, so I had to reinstall my xorg junk for this chip.

sudo apt-get remove --purge xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel

sudo vi /etc/X11/xorg.conf

add in Section "Device":

BoardName "Mobile Intel GM45 Express Chipset"
Driver "intel" 

Save and restart.

Can't forget simple-ccsm for Compiz configurations :)

---

### Post by K7522 on 2009-03-04
I found a cool new toy, it's called devilspie.

I went to System -> Preferences -> Sessions
I added a 'startup' file to it, which is just a bash script in my ~/startup/ folder.
Well, with all the programs I wanted started, it got messy fast. So I found this solution.

Devilspie is a program that will do many things to windows as soon as they start, depending on limitless possibilities!

devilspie can be downloaded from Synaptic, and there is a fully functioning GUI to use with it found here: [http://code.google.com/p/gdevilspie/](http://code.google.com/p/gdevilspie/)

I went into gdevilspie and told it to move programs to different viewports (desktops) based on the program name.

Now you can have all those startups and keep your primary clean!

-----

Oh by the way, on post #6 I mentioned xwinwrap, you can actually get that here: [http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap)

---

### Post by K7522 on 2009-03-05
I can never be doing too many things at once. I usually have a lot going on, this is why I love xwinwrap.

Here's an example.

Max Payne movie on xwinwrap, Saosin - Voices on the video player.

I love .. love love love love love multitasking.

---

### Post by K7522 on 2009-03-05
I finally got tired of Transmission last night and got Vuze (the new Azureus apparently), and I was able to cap my download rate for all night, instead of the 20-50kb/s that I was getting with Transmission with the same port and torrents

Vuze is a bit bloated and it's hard to get to the old torrent look, but once I found it, there's no going back. I love this thing.

---

### Post by K7522 on 2009-03-06
Oooops... I forgot to hit POST let's try it again... 

I AM A CARAFE OF UBUNTU NOW! But... what's a carafe?

LOOKY What I found

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

To output what packages you have installed (or have had and uninstalled) information to a file in your home directory you would use,

```
dpkg --get-selections > installed-software
```

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

```
dpkg --set-selections < installed-software
```

followed by

```
dselect
```

---

### Post by longtom on 2009-03-07
"saved"....thanks!

List of excellent tips grows....:D

---

### Post by K7522 on 2009-03-07
I don't know if I mentioned this yet in the diary, but Conky is a great way to keep track of what your computer is doing.

```
background yes
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 22
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT

${font Aerial:style=Bold:pixelsize=12}SYSTEM${font Snap.se:size=8} ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph cccccc ffffff}

RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}

SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}


${font Aerial:style=Bold:pixelsize=12}FILESYSTEM ${font Snap.se:size=8}${hr 1}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

Storage: ${alignr}${fs_free /media/DATA} / ${fs_size /media/DATA}
${fs_bar 4 /media/DATA}

${font Aerial:style=Bold:pixelsize=12}NETWORK ${font Snap.se:size=8}${hr 1}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 cccccc ffffff} ${alignr}${upspeedgraph eth0 25,107 cccccc ffffff}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${font Aerial:style=Bold:pixelsize=12}Rhythmbox ${font Snap.se:size=8}${hr 1} 
Status:  $alignr${exec conkyRhythmbox --datatype=ST}
Artist:  $alignr${exec conkyRhythmbox --datatype=AR}
Album:  $alignr${exec conkyRhythmbox --datatype=AL}
Title:  $alignr${exec conkyRhythmbox --datatype=TI} 
Position: $alignr${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}
```

I installeed the Conky Rhythmbox Python script to get the Rhythmbox to work, works with Last.FM streams, which is what is playing in the picture. Link below for that. [http://ubuntuforums.org/showthread.php?p=5843297](http://ubuntuforums.org/showthread.php?p=5843297)

The install how-to is linked here for Conky. [http://ubuntuforums.org/showthread.php?p=6365702](http://ubuntuforums.org/showthread.php?p=6365702)

Screenshot taken with Shutter (In Repos)

---

### Post by K7522 on 2009-03-07
I forgot to upload an image of the Conky setup I have.

I posted this stuff in a different place in the forums too, but I like to keep this stuff consolidated. Here's the link for the other post, page 604. [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by K7522 on 2009-03-08
I was installing Vista in VBox, but having some issues with networking.

Come to find out, I had to run 'Install Guest Additions...' in the 'Devices' tab for the VBox's AMD Ethernet protocols to work with Vista. 

I'm rebooting the VBox right now to see if it will see the network.

It saw the network, I can't get as big of a resolution that I did before the reboot, it installed some video drivers as well. I don't really car about that though, the machine is actually reacting a bit faster now, closer to a native install.

Then I'll need to install Quickbooks... yay *sigh*

---

### Post by K7522 on 2009-03-11
One of my friends runs Ubuntu (Yeah, I got him to go over).

He decided to get back into WoW, and he needed to install WOTLK. When mounted on Ubuntu, there were files missing, he has another desktop that dual boots windows.

We plugged the CD into Windows and started installing as I tried to figure it out, here's what we did.

I set the drive to share on the network in windows.

```
sudo apt-get install smbfs
```

```
mkdir ~/mnt
```

```
sudo mount -t cifs //IP_OF_WINDOWS_MACHINE/F ~/mnt -o username=USERNAME,noexec
```

Run the installer... then

```
sudo umount ~/mnt
```

I don't know if you can do this from ubuntu to ubuntu, I did not try.

---

### Post by K7522 on 2009-03-12
I've been infected with malware!

bwahahha!

---

### Post by K7522 on 2009-03-18
I found a nice little trick to turn up the brightness (gamma) on the screen.

xgamma -gamma 1.00 (1.0 is regular, can go above and below it. I'm using 1.3)

---

### Post by K7522 on 2009-04-25
I will be doing a fresh install of the brand new 9.04 Jaunty Jackalope on my desktop and bringing here all of the fun (and pain) the install puts me through.

I always feel like a fresh install is nice to get rid of the junk we put in those great spots we'll remember (but forget in a month anyways).

I will be installing via a USB flash drive, and writing down on my laptop all of the steps I took in the installation of Ubuntu and any additional software.

Offhand I can think of only a few things that I'll want installed.
Compiz
Wine
Ventrilo
vbox
Adobe Flex Builder
Adobe CS3
Adobe Premiere Pro
wow-icon-scalable.svg
gtk-RecordMyDesktop

can't think of anything else offhand. I'll have to check my xwinwrap information earlier in this post for  getting that going at some point.

---

### Post by K7522 on 2009-04-27
I've been getting a strange error listed below. The internet seems to suggest a RAM issue for the fella listed here.

[http://www.usenet-forums.com/linux-general/75107-nmi-received-dazed-confused.html](http://www.usenet-forums.com/linux-general/75107-nmi-received-dazed-confused.html)

```

Apr 27 19:00:58 kurt-9 kernel: [  495.059996] Uhhuh. NMI received for unknown reason 3d on CPU 0.
Apr 27 19:00:58 kurt-9 kernel: [  495.059999] Do you have a strange power saving mode enabled?
Apr 27 19:00:58 kurt-9 kernel: [  495.060001] Dazed and confused, but trying to continue
```

Above is the error in my /var/log/syslog.

The stuff isn't exactlyt he same, but I'm going to run a ram test and see if that solves my issue. I'm not going to be all that happy if a ram stick went out.

---

### Post by K7522 on 2009-05-14
It's been a while since I've written here. I've been learning this Adobe Flex language, it's interesting.

I've decided to toy with my startup script some, here's what I've come up with.

I'm weird, I like the default desktop and colors, and I definitely like how I don't have two thousand programs starting when I boot the machine. That said, I've got only one script loaded into my startup applications, (System -> Preferences -> Startup Applications). That is named [KURT] Startup Script. It runs a script at ~/Scripts/startup.

This script runs everything that I want to load when I start Ubuntu. I can change things at will by just commenting out what I decide I don't want anymore. Being able to look to just a single file for all of that is convenient!

My issue is I wanted to link some files on a mount that did not mount on boot. Well, as I said before I don't like making changes to what loads on boot unless it's in this script. I added a check for the folder and the mount.

I came to realize as I was testing the mounting functionality of this script that I had to comment out many of the lines of code because I did not want it attempting to load these programs over and over. My solution was to do an if/else statement to grep the program. If it was running, move on. I added a loop to do this because I didn't see sense in copy and pasting if/else statements for each individual file.

I realize that there may be a better way of getting the information for the while command than how I did it, but this is how I figured it out and this works without any errors so it's what I'm going to use!

```

#!/bin/bash
mountDir="/media/DATA"
mountPar="/dev/sdb1"
logFile="/home/kurt/Scripts/startupLog"
proGrep=""
proGrepGet=""
proC=""
proCGet=""

## Programs
## proNum must be equal to the number of programs loading.
## suffix "g" is the command to grep to see if the program is running.
## suffix "c" is the command to use to start the program.
proNum="3"
pro1g="pidgin"
pro1c="pidgin"
pro2g="lampp"
pro2c="echo PASSWORD | sudo -S /opt/lampp/lampp start"
pro3g="conky"
pro3c="conky -c /home/kurt/Scripts/conky"

## First we check if the drive is mounted.
if [ $(mount | grep -c $mountDir) != 1 ]
then
	echo -e "\t$mountDir is not mounted." >> $logFile
	## If it is not mounted, check if the folder exists.
	if [ ! -x $mountDir ];
		then
			## If the folder does not exist, create it.
			echo -e "\t$mountDir folder does not exist. Creating." >> $logFile
			echo PASSWORD | sudo -S mkdir $mountDir
		else
			## If the folder exists, move on.
			echo -e "\t$mountDir folder exists." >> $logFile
	fi
	## Mount the drive to the folder.
	echo PASSWORD | sudo -S mount -t ntfs $mountPar $mountDir
else
	echo -e "\t$mountDir is mounted." >> $logFile
fi

## This ensures the X Desktop is fully loaded, mainly to ensure that
## Conky loads properly. 
sleep 15

while [ $proNum -gt 0 ]
do
	proGrep="pro`echo $proNum`g"
	proGrepGet=${!proGrep}
	proC="pro`echo $proNum`c"
	proCGet=${!proC}
	
	## If program is not loaded, load it. If it is, move on.
	if [ $(ps ax | grep -v grep | grep -c $proGrepGet) == 0 ]
	then
		echo -e "\tLoading $proGrepGet." >> $logFile
		$proCGet &
	else
		echo -e "\t$proGrepGet is already loaded." >> $logFile
	fi
	## Drop a number to go to the next command.
	proNum=$[$proNum-1]
done

exit 0

## rhythmbox %U
## evolution --component=mail
## skype
## devilspie

```

---

### Post by K7522 on 2009-05-17
I forgot to copy my lampp virtual host information when I reformatted, so I figure I'll post the howto found [here]("http://ubuntuforums.org/showpost.php?p=2579023&postcount=4").

Put your virtual hosts in the /opt/lampp/etc/extra/httpd-vhosts.conf file.

To make XAMPP actually look for the extra Apache settings (i.e. virtual hosts), make sure that the followiong lines are uncommented in your httpd.conf file

```
# Virtual hosts
Include etc/extra/httpd-vhosts.conf

# Various default settings
Include etc/extra/httpd-default.conf

# XAMPP
Include etc/extra/httpd-xampp.conf
```

After that, give Apache a restart

```
sudo /opt/lampp/lampp stopapache
sudo /opt/lampp/lampp startapache
```

Sometimes it'll kick back errors if the directories don't exist. Also, I used to always have typos. That'll also cause Apache to fart on your configs and not start.

---

### Post by K7522 on 2009-05-18
I decided to start playing Left4Dead again to take up some of the time I've freed by quitting WoW. I had to do a few roundabout things to get this to work properly, but I only have one issue now unresolved.

I followed the instructions listed here to the dot.
[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam)

I'll go over it briefly.

If you havent already, install wine.
```
sudo apt-get wine
```

Download Steam, I have below both the direct link to the current file at the time of this writing, and also the website incase the first link ever expires.
[http://storefront.steampowered.com/download/SteamInstall.msi](http://storefront.steampowered.com/download/SteamInstall.msi)
[http://steampowered.com](http://steampowered.com)

You then need to install wine-gecko. The guide I followed seemed to have an outdated way of installing wine-gecko. I see the package in my Synaptic, so you may be able to use a 
```
sudo apt-get install wine-gecko
```
If that does not work, try adding the Wine repos. You can do that here.
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Once Steam is downloaded, it shouldn't take long, go to the directory and run it with the following command.
```
msiexec /i SteamInstall.msi
```

You should go through the installation process as normal there and be allowed to use the program.

My next post will cover optimum settings that I've found for Left4Dead, I've been toying with it and the ingame console command net_graph 3.

---

### Post by K7522 on 2009-05-18
First off, you need to kill pulseaudio when playing Steam games. The issue is, pulseaudio likes to restart itself!

Go to System -> Preferences -> Sound.
I set everything here to ALSA, the issue is you don't want it set to PulseAudio or Autodetect because it may try to go over to that, and since you're about to kill it, you still want system sounds! I like music...

You then need to find the line "autospawn = yes" and change it to "autospawn = no"
This needs to be changed in /etc/pulse/client.conf. Edit it with your favorite tool, I use the following command to do so:
```
sudo geany /etc/pulse/client.conf
```

Check to see if PulseAudio is running.
```
ps ax | grep -v grep | grep -c pulseaudio
```

If the above command returns anything over 0, run the following.
```
killall pulseaudio
```

Then try running the ps ax command again to make sure it's killed (and stayed dead!)

That covers the sound (and crashing issues) in Source games. The next issue we need to address is slow play.

My Left 4 Dead desktop link has one thing added, that is WINEDEBUG=-all. I don't know if that has had any effect on gameplay, but I read it somewhere so I threw it in. My link is as follows:
```
env WINEDEBUG=-all WINEPREFIX="/home/kurt/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 500
```

Once ingame, video settings are VERY important.
Film Grain Amount: **NULL**, as low as it can go.

In Advanced Settings:
Filtering Mode did not affect my framerate.
Wait For Vertical Sync: I did not need this, so **DISABLE**. I do not know if this will affect framerate beyond the regular loss.
Multicore Rendering: **DISABLED**
Shader Detail: **LOW**
Effect Detail: High
Model / Texture Detail: High
Paged Pool Memory Available: High

I run an Aspect Scale of 16:10 and Resolution of 1440 x 900, with a Display Mode of Run in a window.

To ensure that the game will play normally, go to System -> Preferences -> Appearance. Go to Visual Affects and click None. Yes, you're turning off Compiz. Sorry folks. Having Compiz on will decrease your FPS anywhere from 5-15. It's still playable with it on, but hey why sacrifice gameplay on an easy little thing like that? Turn it back on when you're done and get your wobbly windows back.

---

### Post by K7522 on 2009-05-19
On post #56, I noticed that Lampp was not starting with my startup script.

I narrowed the issue down to the following line:
```
pro2c="echo PASSWORD | sudo -S /opt/lampp/lampp start"
```

I decided to toy wit it, and I came to it. Since I'm running it in a bash script, I actually have to echo my password AFTER the command for this to work properly. This is because it's attempting to use the command 'echo' instead of the command 'sudo' first, and while both of these work when manually typing this into the terminal, the following is required in a bash script:
```
pro2c="sudo -S /opt/lampp/lampp start | echo PASSWORD"
```

---

### Post by K7522 on 2009-05-20
In post 59 of this thread I said that you have to disable Compiz for framerate to work properly. It seems like, actually, you can just disable transparent desktop and it will work fine. Interesting!

---

### Post by K7522 on 2009-05-21
4,000 reads! WOOT! I don't really have anything to say in this post, Ubuntu is working flawlessly, I don't really have anything to modify, change, fix or anything at this time.

---

### Post by K7522 on 2009-09-12
It's been quite a while since I've posted more useful information here, so perhaps I should get on that again. 

I wrote a script to back up all of the websites on my server and keep them for 7 days. If you ever want to keep the files older than 7 days, you can move them out of that folder or change the find line.

I just set this in ~/Scripts and installed it in my cron, details on how to do so can be found here: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) I decided to set it to 0300.

```

#!/bin/bash

# Setting Environment Variables
export BACKUP_FOLDER="/path/to/backup/folder"
export WEBSITE_FOLDER="/path/to/web/folder"
export LOG_FOLDER="/path/to/log/folder"
export SQL_USER="CHANGE ME"
export SQL_PASS="CHANGE ME"
export DATE="`date +%F`"

## Move to the working directory.
cd $BACKUP_FOLDER

## Dump the SQL database.
mysqldump --user="$SQL_USER" --password="$SQL_PASS" --all-databases > mysql-$DATE.sql

# Tar the website folder and the dumped .sql file.
tar -cpzf Websites-$DATE.tar.gz mysql-$DATE.sql $WEBSITE_FOLDER

## Clean up the folders.
# Remove any tar files older than one week.
find $BACKUP_FOLDER -type f -mtime +7 -exec rm {} \;
# Remove any remaining .sql files.
rm -f $BACKUP_FOLDER/*.sql

echo "backups-website : Nightly Backup Successful : $DATE" >> $LOG_FOLDER/backups.log

exit 0

```

---

### Post by K7522 on 2009-09-12
I modified my startup script that I posted a few pages ago, the script now is much cleaner, easier to use and read. I place this in System > Preferences > Startup Applications. I would rather manually add my programs here and be able to edit this file than to have a bunch of entries in the Startup Applications.

```
#!/bin/bash

## Setting Environment Variables
export mountDir="/media/DATA"
export mountPar="/dev/sdb1"
export mountPartitionType="ntfs"
export LOG_FILE="~/Scripts/startup.log"
export proVar="1"
export password=""

export pro1="skype"
export pro2="conky -c ~/Scripts/conky"

function mount {
## First we check if the drive is mounted.
 if [ $(mount | grep -c $mountDir) != 1 ]
 then
 	echo "$mountDir is not mounted." >> $logFile
 	## If it is not mounted, check if the folder exists.
 	if [ ! -x $mountDir ];
 		then
 			## If the folder does not exist, create it.
 			echo "$mountDir folder does not exist. Creating." >> $logFile
 			echo $password | sudo -S mkdir $mountDir
 		else
 			## If the folder exists, move on.
 			echo "$mountDir folder exists." >> $logFile
 	fi
 	## Mount the drive to the folder.
 	echo PASSWORD | sudo -S mount -t ntfs $mountPar $mountDir
 else
 	echo "$mountDir is mounted." >> $logFile
 fi
}

## This ensures the X Desktop is fully loaded, so programs load properly.
sleep 15

function startprogs {
## Here we start the listed programs if they are not running.
while [ $proVar != 0 ]
do
	proC="pro`echo $proVar`"
	proCGet=${!proC}
	set -- $proCGet
	proGrep=$1
	
	if [ -z "$proCGet" ]
	## If there is no command to load, exit. If there is, move on.
	then
		proVar="0"
	else
		## If program is not loaded, load it. If it is, move on.
		if [ $(ps ax | grep -v grep | grep -c "$proGrep") == 0 ]
		then
			echo "Loading $proGrep." >> $LOG_FILE
			$proCGet &
		else
			echo "$proGrep is already loaded." >> $LOG_FILE
		fi
		proVar=$[$proVar+1]
	fi
done
}

# mount
## This ensures the X Desktop is fully loaded, so programs load properly.
# sleep 15
startprogs
echo "Finished Loading" >> $LOG_FILE
echo "--------------------" >> $LOG_FILE
exit 0

```

---

### Post by K7522 on 2009-09-13
I always just copied the full command of xwinwrap... but.. WHY!?

I created this script, it's quick and easy.

```
#!/bin/bash

echo -ne "Input file to be played: \n"
read -e video
xwinwrap -ni -o 0.4 -fs -s -nf -sp -- mplayer -wid WID -quiet "$video"

```

---

### Post by K7522 on 2009-09-15
I just spent the last hour making what could be the BEST script ever.

This will randomly set your desktop to a BSOD image. Chance, duration and file names are variables at the top. As long as the BSOD image is in your ~ directory, this code will work unchanged. There are permission issues when using find to / and while it is just as easy to do a sudo, there is no need.

 ```
#!/bin/bash

## Coded by K7522. http://ubuntuforums.org/member.php?u=498158[
# To install this to your cron:
# $ crontab -e
# Scroll to bottom, and add: 1 * * * * /path/to/this/file
# Press <CTRL> X
# Press Y
# Press <ENTER>

# What is the chance you want receive a BSOD hourly? 1/#
export chance="10"
# The name of your BSOD photo.
export bsod="bsod10247or.jpg"
# Time to remain with BSOD screen in seconds.
export duration="60"

export bsod_loc=`find ~ -name $bsod`

function success {
# First we capture the current desktop image.
export originalScreen=`gconftool-2 --get /desktop/gnome/background/picture_filename`
# Now we save it in a seperate variable just in case.
export originalScreenSave="$originalScreen"

if [ $bsod_loc != "" ];
  then
  # File exists, use it.
  gconftool-2 -t string -s /desktop/gnome/background/picture_filename $bsod_loc
  sleep $duration
  gconftool-2 -t string -s /desktop/gnome/background/picture_filename $originalScreenSave
  else
  # The BSOD desktop file does not exist, we must exit.
  exit 0
fi
}

function test {
number=$RANDOM
let "number %= $chance"
if [ $number = "1" ];
  then
    success
  else
    exit 0
fi
}

test
exit 0
```

---

### Post by K7522 on 2009-09-15
Oh and here's a BSOD desktop image!

---

### Post by longtom on 2009-09-15
> **K7522 said:**
> Oh and here's a BSOD desktop image!

This is beautiful.  I forgot about the richness of that blue....*sniff

---

### Post by K7522 on 2009-09-23
I haven't had much in the way of "fixing" in Ubuntu, not that it takes much to fix anything that's wrong anyway, most of it is just simple scripting to adjust your personal settings...

I do have one thing that I haven't worked on yet. I have a Netbook, a Toshiba NB205 and I have not yet figured out how to get bluetooth to work on it. I haven't really studied the matter honestly, but once I do I will post my findings here.

I did upload a video to YouTube of my current desktop settings, one thing I noticed was a vsync issue while recording, this was on the original before I modified it by any compression, I think the issue may be in the transparencies of the desktop, and is something I'd like to fix. [COLOR="Red"]I'm marking the video NSFW because of the skydome and music, it is R rated.

NSFW [/COLOR]http://www.youtube.com/watch?v=QiRDLLYjyTM

---

### Post by K7522 on 2009-10-17
I've been ultra busy lately with school and work, I found myself needing to work on school in multiple computers. What's the best way to do that, I thought? USB possibly but what kind of fun is that? So I am currently using OpenGoo ([http://www.opengoo.org](http://www.opengoo.org)). "It is a complete online solution focused on improving productivity, collaboration, communication and management of your teams." It works great for my stuff.

EDIT: By the way, OpenGoo is easy to set up on ubuntu and no additional setup required (besides your Apache, MySQL, and basic web server setup of course.)

Oh... been playing Lax too! This following video really pumps me up to play, it's a great short vid that shows off what Lax is all about.

[http://www.youtube.com/watch?v=6YW44NdLN0o](http://www.youtube.com/watch?v=6YW44NdLN0o)

---

### Post by K7522 on 2010-01-22
My friend put up a server which required a few processes to start on boot. While yes you can edit /etc/rc.local file to manage startup programs on servers, this one checks to ensure there aren't redundant mounts or program starts. This can also be put in your startup programs on desktops to start all of your personal programs. In this I have a demo of conky and cairo-dock. loading, a drive mounted and two folders mounted. $mntEnd and $proEnd needs to be at the highest number on your load list, for instance if you have five things mounting from 1-5, then $mntEnd needs to be 5. If you have 1-4 and then 6, your $mntEnd needs to be 6. This allows you to comment out for instance $pro1 and it still continues to $pro2 unhindered... but it needs to know when to stop!

I tried putting as much detail in possible in the comments to allow others to learn from the code.

I only ask the 'written by' statement remains and credit given if the script is modified and re-released.

```
#!/bin/bash

## Written by Kurt H.
## Setting Environment Variables.
## The sudo password for proper function of script.
export password=""
export logFile="/home/USER1/dump/scripts/logs/startup.log"

function mountFolders {
## Variables for the mountFolders function.
## WARNING! If you are not mounting a hard drive, do not include mntPart variable.
mntVar="1" ## 0 to disable function, 1 to enable function
mntEnd="5"

mntSrc1="/opt/lampp/htdocs"
mntDest1="/home/USER1/htdocs"

mntSrc2="/opt/lampp/htdocs/whiskeyrichards"
mntDest2="/home/USER2/htdocs"

mntSrc3="/dev/sdb1"
mntDest3="/media/data"
mntPart3="ntfs"

## Here we mount the listed folders if they are not already mounted.
while [ $mntVar -gt 0 ] && [ $mntVar -le $mntEnd ]
do
	## The reason we have to run the next two parts is because we want to go down the list, doing
	## mntSrc1, then mntSrc2, etc. This was the easiest way to accomplish the task. The next two
	## lines are a bit confusing to the basic user. This creates a variable named mntS and give
	## it a value. That value is mntSrc plus the value of $mntVar at the end. The
	## beginning of the script has the value set to one, so mntS is mntSrc1. You can see that's
	## one of our variables that we need, but it's just the name.
	mntS="mntSrc`echo $mntVar`"
	mntD="mntDest`echo $mntVar`"
	mntP="mntPart`echo $mntVar`"
	## Now that mntS has the name of the variable we are going to use, we have to get the value of
	## that variable, the following command creates a new variable. The value of that variable is
	## the value of the variable named in mntS. In the case of the beginning of the script, If 
	## mntSrc1 is 'hello' then mntSGet will also be 'hello'.
	mntSGet=${!mntS}
	mntDGet=${!mntD}
	mntPGet=${!mntP}
	## If the function does not exist, there is no reason to attempt to run it, so we skip it and
	## go to the next one (up to and including $mntEnd, see the while statement).
	if [ -z "$mntSGet" ]
	then
		mntVar=$[$mntVar+1]
	else
		## Here, we know that there is a variable, it does exist and it does have a value. So we need
		## to continue with our function and see if these folders are already mounted to their proper
		## places. If they are not mounted, we need to go ahead and do so.
		if [ $(mount | grep -c $mntDGet) != 1 ]
		then
			echo "$mntDGet is not mounted." >> $logFile
			## The mount does not exist, now we need to check if the destination folder exists.
			if [ ! -x $mntDGet ]
			then
				## The folder does not exist, create it.
				echo "$mntDGet folder does not exist. Creating." >> $logFile
				echo $password | sudo -S mkdir $mntDGet
			else
				## The folder exists, move on.
				echo "$mntDGet folder exists." >> $logFile
			fi
			## We have ensured that the directory is not mounted. We have ensured that the
			## folder does indeed exist. Now we need to mount the directory to the folder.
			## We need to check if this is a mounted folder or a mounted drive.
			if [ -z "$mntPGet" ]
			then
				echo $password | sudo -S mount --bind $mntSGet $mntDGet
			else
				echo $password | sudo -S mount -t $mntPGet $mntSGet $mntDGet
			fi
		fi
		## To make sure we don't try to mount the same thing over and over, we add one to the
		## value of mntVar here. This has to be within this if statement to ensure that the script
		## does not loop with no end.
		mntVar=$[$mntVar+1]
	fi		
done
}

function startProgs {
## Variables for the startProgs function.
proVar="1" ## 0 to disable function, 1 to enable function
proEnd="2"

pro1="conky -c /home/USER1/dump/scripts/conky"
pro2="cairo-dock -o"
## Here we start the listed programs if they are not running.
while [ $proVar -gt 0 ] && [ $proVar -le $proEnd ]
do
	## See mountFolders function for an explanation on the next two lines.
	proC="pro`echo $proVar`"
	proCGet=${!proC}
	## Since the variables are programs with options, we need to make sure that we have just the
	## program name when doing the grep. This pulls the first word from the variable and puts it
	## in the variable $proGrep.
	set -- $proCGet
	proGrep=$1
	
	if [ -z "$proCGet" ]
	## If there is no program to load, go to next program. If there is, continue loading this one.
	then
		proVar=$[$proVar+1]
	else
		## We check to see if the program is already loaded via grep. If the program is not yet
		## running then we load it. If it is already running, we skip to the next program.
		if [ $(ps ax | grep -v grep | grep -c "$proGrep") == 0 ]
		then
			echo "Loading $proGrep." >> $logFile
			$proCGet &
		else
			echo "$proGrep is already loaded." >> $logFile
		fi
		## To make sure we don't try to mount the same thing over and over, we add one to the
		## value of proVar here. This has to be within this if statement to ensure that the script
		## does not loop with no end.
		proVar=$[$proVar+1]
	fi
done
}

mountFolders
## This sleep ensures the X Desktop is fully loaded for desktop users, so programs load properly.
sleep 15
startProgs
echo "Finished Loading" >> $logFile
echo "--------------------" >> $logFile
exit 0
```

---

### Post by K7522 on 2010-01-23
I hate linux.




















It just works. No issues that take more than a 'sudo apt-get install'.

It also does exactly what you tell it to, and it's predictable.

---

