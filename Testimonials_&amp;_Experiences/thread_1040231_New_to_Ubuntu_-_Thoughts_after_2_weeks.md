---
title: "New to Ubuntu - Thoughts after 2 weeks"
date: 2009-01-15
forum: Testimonials &amp; Experiences
---

### Post by Kingpong on 2009-01-15
I have installed Ubuntu on a virtual machine and played around with it about a month ago. I thought it was complete enough to use as an everyday machine. I ordered up the new parts for a machine and went to town to create a dual boot machine. The main purpose for the Vista OS is that I still would like to game occasionally or at least have the ability to do so. I have an AMD Quad core processor and using onboard video with an 80GB drive that I split in half for each partition.  So far I have the Ubuntu 64 installed and running on a 40GB partition. I am waiting for my Vista software to arrive and install on the other partition. I also have an internal 640GB drive installed for data only. My hope is that this drive will be able to be viewed in Vista and Ubuntu.  

Some things have impressed me while others have frustrated me.  Here is a list of random experiences from my first two weeks. 

-Conky
Very easy to install and get going and it provides a very useful and entertaining desktop.  I have a basic config file created by using the forums here.  I will definitely be spending more time playing with it to get the weather to display properly.  The forums on here have easily given me enough knowledge to get this working.  I know there are some instruction sites out there but I find the examples posted (with screenshots) the most beneficial for me to understand.

-Web Camera
I have been very impressed with how all of my hardware works without going out and getting drivers.  The web camera worked the first time I plugged it in but has not worked since.  I know in windows where to look and see the camera is recognized by the OS.  No luck here I have tried some command lines that I read about and I can see it there but applications are not seeing it at all. 

-Installing new hard drive
I thought this would be pretty easy but I was wrong.  Having to create a mount point and edit the fstab file took me a couple of hours to get the drive to recognize.  It seems that after a couple of reboots the drive is finally starting to appear like I wanted it to. 

-Video playback
I have tried several different files and was experiencing some pixilation.  I was getting really pissed but found out it was the actual file.  I tried some other files and eventually I found the settings that worked under Multimedia so I think I am over this problem.

-Ripping DVD
This is still an issue.  I was hoping to be able to rip some DVD's I have to .avi and play them on the computer.  Homemade discs and movies I would like to rip are not working right.  I have tried k9copy, VLC and handbrake but either the sound or the video qualities are off or the machine locks up.   I would like to try MythTV and see if I can get a capture card to work.  I was hoping these files would be placed on the data drive and used for Myth or Media Center on my Vista install.  

-Wireless
I installed a wireless USB Linksys adapter when I move the computer to another room.  No need to go out to find the correct drivers, no need to install a program to configure the wireless, it just worked. This was very nice to see.

-Overall
The system is not running any faster than a Vista system would run with my hardware. It is fun to configure things and play with the cool desktop animations but some things should be easier than they are. Configuring the new hard drive should have been an easier install.

---

### Post by Titan8990 on 2009-01-15
> -Installing new hard drive
I thought this would be pretty easy but I was wrong. Having to create a mount point and edit the fstab file took me a couple of hours to get the drive to recognize. It seems that after a couple of reboots the drive is finally starting to appear like I wanted it to.

This was only because it was your first time. It takes me less than 5min and you will get the hang of it as well.

> -Video playback
I have tried several different files and was experiencing some pixilation. I was getting really pissed but found out it was the actual file. I tried some other files and eventually I found the settings that worked under Multimedia so I think I am over this problem.

There is a great multimedia guide as a sticky in the multimedia forums.

> -Overall
The system is not running any faster than a Vista system would run with my hardware. It is fun to configure things and play with the cool desktop animations but some things should be easier than they are. Configuring the new hard drive should have been an easier install.


Ubuntu is far less resource heavy than Vista. Didn't you say you were running in a VM?

---

### Post by LowSky on 2009-01-15
To rip a dvd try out acidripper. It a great GUI based program that has plent of option for ripping a DVD. It can encode to most formats.

to install

```
sudo apt-get install acidripper
```

---

### Post by Joeb454 on 2009-01-15
Moved to Testimonials & Experiences.

With regards to installing Vista after Ubuntu, you'll need to reinstall grub, because Windows will overwrite it, and you won't be able to boot into Ubuntu.

Fortunately, it's pretty easy to do (make sure you have an Ubuntu CD).

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by solwic on 2009-01-15
> **LowSky said:**
> To rip a dvd try out acidripper. It a great GUI based program that has plent of option for ripping a DVD. It can encode to most formats.

to install

```
sudo apt-get install acidripper
```

Actually that code is dead, there's no such package.  And apt-cache search acidripper didn't turn up any results, either.  

Maybe it's been removed from the repositories?

---

### Post by Kingpong on 2009-01-15
> **Titan8990 said:**
> This was only because it was your first time. It takes me less than 5min and you will get the hang of it as well.



There is a great multimedia guide as a sticky in the multimedia forums.




Ubuntu is far less resource heavy than Vista. Didn't you say you were running in a VM?

I was running VM to check it out before purchasing new hardware.  I think it gets to a point where I am not going to see the returns of the hardware with 8GB of ram. 

The hard drive installation is still more confusing than it should be.  Without these forums I would not have been able to do it.

---

### Post by lancest on 2009-01-15
'acidrip' exits in repositories. I use it alot- great program.

---

### Post by Vince4Amy on 2009-01-15
> 
-Web Camera
I have been very impressed with how all of my hardware works without going out and getting drivers. The web camera worked the first time I plugged it in but has not worked since. I know in windows where to look and see the camera is recognized by the OS. No luck here I have tried some command lines that I read about and I can see it there but applications are not seeing it at all.

Which apps are you using with this, this is the main reason I choose 8.04 if I'm going to use Ubuntu at all.

[https://bugs.launchpad.net/ubuntu/intrepid/+source/libv4l/+bug/260918/+viewstatus](https://bugs.launchpad.net/ubuntu/intrepid/+source/libv4l/+bug/260918/+viewstatus)

---

### Post by solwic on 2009-01-15
> **lancest said:**
> 'acidrip' exits in repositories. I use it alot- great program.

Ahhh...acidrip, not acidripper.  

I see it now.  

Thanks for the clarification.  :)

---

### Post by 3rdalbum on 2009-01-16
I hear a lot of people say "I want to rip my DVDs to .avi".

AVI is not a video codec - it's just a container format. An AVI file specifies exactly how video tracks and audio tracks should be combined into a single file. The actual video and audio codecs you use can be pretty much anything.

Container formats include: AVI, MOV (Quicktime), MPG, Ogg
Video codecs include: Theora, Sorenson, DivX, MPEG-4, H264

So, you could theoretically have a DivX video track inside an AVI or Ogg file, or you could have a Theora video track inside a Quicktime movie.

This information I've just given you will help you use Acidrip, and might shine some light on why you're getting bad results with your DVD ripping. At the moment I'm doing some DVD ripping and I'm using H264 video and MP3 audio inside an AVI container. The video bitrate I used was 5mbps (megabits per second) but if you want better quality you should probably use 10mbps. Audio should be 128kbps or 160. MPEG-4 or DivX (or Xvid) are also good choices for video codec.

---

