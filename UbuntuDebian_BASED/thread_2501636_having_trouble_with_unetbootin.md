---
title: "having trouble with unetbootin"
date: 2024-10-15
forum: Ubuntu/Debian BASED
---

### Post by cryofreeze666 on 2024-10-15
1) trying to install minerstat os to a ssd
2) place ssd in an enclosure
3) connect enclosure to computer
4) selected msos-v1-4-10-k50-n520-a2030.zip as the disk image
5) enclosure only shows up under usb drive heading
6) ran program

ok so after all of that, its not giving me an iso image, its just extracting the files to the drive and that's it.  i can open the ssd, see the files, right click, delete them if i want.  i already tried it, i wanted to make sure my assumption was right.  i shouldn't be able to access the files to image files with my skill with ubuntu.  plus before i deleted the files i installed in the computer the drive was for, it went straight to bios.  

by what i've read, it's supposed to be similar to etcher by being able to make iso images from zipped files.  did i misunderstand something, since it only seems to be extracting the files to the drive and not creating the image?

---

### Post by bobunderwood99 on 2024-10-15
The zip file is a compressed file that contains the minerstat os img file.

Edit - I looked at the Minerstat OS [ install instructions](https://minerstat.com/help/how-can-i-set-up-msos) - rather poorly worded and confusing.

I guess Etcher will extract the img (not iso) file from the zip file and write it where desired.

I suggest you follow the instructions exactly using Etcher.

---

### Post by cryofreeze666 on 2024-10-17
i would love to try etcher, but i haven't had any luck installing the prpgram in 20.04.  it works pretty good in windows, it wouldn't install in 7, had to install 10.  lucky me i have copies of both.  looks like minerstat is going the way of the setting sun.  i can't find any forums for minerstat to ask what i am doing wrong, or see if i can get the instructions clarified.

i thought i had followed the instructions, problem is, I THINK, obviously i don't know, i downloaded the version i copied with etcher in windows, and i think the site auto downloaded for windows and the computer said no kernel when i tried to use the ssd.  so i tried downloading the program with linux, took it to the windows machine with etcher on it, and that's where i started getting to know my bios so well.  oh yeah, did something stupid too, i left the ssd in the enclosure still nothing.  following the instructions of the you tube guy who recommended the enclosure approach, to trick programs into thinking bootable thumb drive.  When i finally get that computer working.  

then i went downloaded unetbootin

1) dual loaded win 10 to use ethcher, didn't get a usable copy
2) used unetbooten with the zip file, nothing.  even decided that id give unzipped a try, yeah that didn't work either.
3) must have watched 10 or 12 videos on how to install minerstat to a ssd, very little variance.
4) watched a couple of videos on unebootin, it's as simplistic as etcher.
5) beginning to think the minerstat people don't know how to install their own stuff.
6)also beginning to think that the video people editted something out, that's common sense to them, but me with little experience not so much.  

guess i'm going to search the web after i find something like hive os to install, or at least something that actually will install on linux.

---

### Post by bobunderwood99 on 2024-10-17
Try using the Windows machine with Etcher installed to flash the external SSD with the Minerstat img.

1) Download the Minerstat zip (mining os not windows mining) to the win box.

2) Plug the extSSD into the win box. Be sure windows can "see" it (the extSSD).

3) Follow steps 3-6 under 2.1 Windows - Flashing msOS to USB or SSD/HDD
 
4) Plug extSSD into mining box and try to boot off it (fingers crossed).

If no go, the next approach is manual - using dd (disk destroyer - actually data definition).

---

### Post by nicolasdentremont on 2024-10-17
The way I normally make bootable USB drives in Ubuntu is with the dd command. It's worked well for me so far.

The last time I made a bootable USB was for Arch Linux about a month ago and I used:

```
 sudo dd if=/path/to/your.iso of=/dev/sdx bs=4M status=progress oflag=sync
```

Where /path/to/your.iso is the path you your ISO file and /dev/sdx is the drive you want to use.

---

### Post by cryofreeze666 on 2024-10-18
nicolasdentremont, i've only been using linux for 3 months, and just recently got directions to to manuals and websites to interpret script.  so let me see if i understand that line correctly.

sudo= root access for want of a beter way to put it
dd= data dump if i remember right or something like that
if= = looks like an old if/ then opener statement to me
/= i can't remember, but it looks like it's being used to establish the pathway.  example /home/a/b/downloads (assuming i default to download here)
of= =would that be similar to the then statement?
/= opening another pathway
dev = i have no clue
sdx= destination drive location?

after sdx i'm clueless about what you typed means

i would love to be a command line trooper, but i unfortunately have to travel at a pace that isn't giving me enough time to learn as thoroughly as i would like.  if i can get this program up and running, to give me an idea of the passive income from the nvidia 3k series, and the amd 6k series as a base.  with a 1050 ti for the monitor.  that is going to tell me whether or not i spend 6 to 10k more on gpu's for that computer, and whether or not i schedule building 2 more 12 gpu computers over the up coming year.  

that timetable being said.  i have to understand that line you typed, if i ever wish to learn anything while i'm in the process of hurrying up to wait.

---

### Post by cryofreeze666 on 2024-10-18
bobunderwood went here for my downloads, [https://minerstat.com/msos-archive](https://minerstat.com/msos-archive) after your last post to me.  it seemed like the main gui didn't like running on it's own judging by what i could guess of the folders and files in the program.  it seemed like those needed either windows or a linux kernal installed first.  don't get me wrong it showed img files that i couldn't open, but the program wouldn't boot.  

also the directions you sent me had the step that had me manually configuring the os, by setting up the miners configuration in the dashboard then copy and pasting them to the os.  i've been trying to create the iso, connect to the dashboard, then auto detect the worker.  the video seemed pretty painless, yeaaaaaaaaaah

decided to download the most recent, that looks like it was built off the 22.04 version.  in case i decide to up my game, and use 7k series gou's.

---

### Post by bobunderwood99 on 2024-10-18
Did you follow my instructions exactly (using the latest version of MsOS)?

If so, did the mining computer successfully boot into MsOS (based on Ubuntu 22.04)?

...
Look at ```
man dd
```

---

### Post by cryofreeze666 on 2024-10-20
ok, before i force you into divergence out of frustration BOBUNDERWOOD99, i need to explain.  since last week i've been stealing time to post  and try to work on that worker, it's been a bad couple weeks.  

hadn't gotten to try your new directions yet, was telling you the results of what happened when i tried following the instructions from the link in the previous post, not this most recent.  

i was also telling/ showing you the archive where i was going for the downloads to find the program that is an o.s. not a window.  that was the extent of that last post, trying to keep you informed.

no i still haven't had time to work on it seriously, just took 10 minutes to pay you the courtesy of explaining myself.  i'm hoping that next weekend, i can devote two whole days to this.

also, remind me to tell you about the e=mail i receieved from minerstat.

---

### Post by bobunderwood99 on 2024-10-21
Hello,

OK - no worries - whenever you're ready.

I hope your weeks get better.

---

### Post by cryofreeze666 on 2024-10-26
ok, software obviously not my strongest point.  building these things from scratch (hardware), an open air rig takes me 4-6 hours, including building the chassis/ case.  i can build anything.  
   newest update, i finally gave up on minerstat os.  tryed the next recommended program in the forum list.  rave os.  it's causing me less problems, because the only thing i'm dealing with right now seems to be hidden files.  haven't tried loading it because i have to manually load the config file from the dashboard.  took a screen shot of the instructions and the open file side by side because including the instructions for using the pathway to find the file to install the config file i'm to or three steps from the end.  the next file after the config file that i have to do, also isn't showing up, so i say again, i am assuming i'm dealing with hidden files.  the question is how would i open hidden files in /dev/sdb  the enclosure holding my ssd.

---

### Post by yancek on 2024-10-26
/dev/sdb refers to a physical device.  Using LInux, there will generally be a filesystem created on a partition on the device, something like sdb1, sdb2, etc.  What is on this device?  Do you have a Linux filesystem on it or non-Linux?  Have you created a mount point to access the drive or partition filesystem?  Have you then mounted it?  Do you see anything on sdb, files or directories?  If you can access the device in a file manager, you should have an option to View Hidden files.

---

### Post by bobunderwood99 on 2024-10-26
cryofreeze666,

I find the instructions to [install Rave OS]("https://raveos.com/installation.html") even more confusing than MinerStat.

Did you try my procedure from post #4?

If you did but got stuck, on which step did you have trouble?

---

### Post by cryofreeze666 on 2024-10-27
bobunderwood99, no i didn't.  i was looking at the month and a half i had spent trying to install it, and decided enough was enough.  but i will show you the instructions i was following so you can see what i am currently stuck.  i haven't tried installing the os yet, because i need to manually place the file in the config file for my worker.

here are the instructions i was following, 
[https://raveos.com.ru/en/installation](https://raveos.com.ru/en/installation)

i am in the instructions for "preparation for installation", everything went smoothly till i hit the second from the last instruction.  couldn't post the screen shot the window that pops up is asking for a url, that will only give the instructions i posted the link to above, not the shot of the instructions and the folders in the ssd to that point.
   
also i wont be able to do the network[IMG]https://raveos.com.ru/en/installation[/IMG] settings instructions, because i can't see that folder either.

---

### Post by cryofreeze666 on 2024-10-27
yancek, the operating system i'm trying to instal is debian based, called rave os.  it is on the ssd, but i haven't installed the ssd because there is no point if i can't install the worker configurations and the network configurations.  

i have been using this computer to set up the drive for that computer

CPU: 6-Core AMD FX-6300 (-MCP-) speed/min/max: 1405/1400/3500 MHz 
Kernel: 5.15.0-124-generic x86_64 Up: 1d 8h 06m 
Mem: 3576.3/24011.3 MiB (14.9%) Storage: 232.89 GiB (19.4% used) Procs: 281 
Shell: bash 5.0.17 inxi: 3.0.38 

so none of that is going to be in the workers os

---

### Post by bobunderwood99 on 2024-10-27
Hello,

No screenshot available. I assume you're using the instructions at [https://raveos.com/installation.html](https://raveos.com/installation.html) under "Prepare your OS Drive".

Those instructions will work only if the mining computer is running Windows.

Where are you stuck?

---

### Post by cryofreeze666 on 2024-10-29
ok, rave os is installed, whoot, whoot, *happy fat man butt shake dance (with my tongue sticking out the corner of my mouth to make it extra creepy).  now i have an e-mail in to raveos personally, it's stuck in the help screen saying root@rig:/# 
whatever that means.  took me less than 2 hours of spare time to get this far.  lets see what happens next.

i asked in other forums about whether or not i needed to unzip the file before flashing and got no answer, evidently it's a some you do some ya don't kind of thing.  it just depends on the flash tool i guess?  but theirs was an unzip before using the flash tool, had to reinstall win10 to use it.  that was really very annoying, now i gottta wipe and reinstall ubuntu.  

so not solved yet, but it seems like i am closer.  i just need them to tell me what i need to enter at the root thing i mentioned at the start of this particular post.

---

### Post by bobunderwood99 on 2024-10-29
What makes you think you should reinstall Ubuntu on the mining computer?

---

### Post by cryofreeze666 on 2024-11-13
sorry i wasn't clear, my mining computer didn't get ubuntu or windows installed on it.  i just meant i have to remove windows from this computer and reinstall ubuntu, because i'm still hating on windows, and talking about it at every oportunity.

---

