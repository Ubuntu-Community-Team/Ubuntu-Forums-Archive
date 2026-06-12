---
title: "Why I ditched Ubuntu (Linux)"
date: 2012-11-07
forum: Testimonials &amp; Experiences
---

### Post by risingknee on 2012-11-07
Okay, this was my 4th attempt with Ubuntu. Probably not last but for the next year I'm going to use primarily Windows.

What happened this time?
I'm (un)lucky to have iPod nano 6. I wasn't able to transfer music to it using Ubuntu. I have tried :
[LIST]
[*]using wine to install iTunes
[*]run virtual machine with XP and iTunes on it
[*]use apps from Ubuntu Software Center
[/LIST]
Since I don't add new music to the iPod very often I decided to install Windows on another partition.

My girlfriend likes to watch movies with subtitles. All I had to do on Windows was setup eg. VLC (but there is plenty of other programs which can handle it). It wasn't that easy on Ubuntu. I've tried with Parole, xine and a few others. Some didn't displayed subtitles at all, on others subs were disappearing after 10-20 minutes of playing a movie or were characters encoding was messed up. Since then we watch movies on her PC and mine I use only for watching show she isn't interested in.

My PC is quite old and I'm using Xubuntu 12.10 in it. When I download programs from Ubuntu Software Center I have to go through all categories (Accessories, Office etc.) to find freshly downloaded app. Sometimes it's not even listed there so I go back to USC to find hint on what I need to type in terminal in order to launch it. Sometimes even that fails and I have to Google on how to launch the app.

I was using Shotwell for managing photos. What surprised me the most was that when I was browsing through pictures and DELETE key wasn't deleting pictures. What's more there was no option for deleting file at all. I've found out that it was posted as a ug on Launchpad couple of years ago. Finally I've decided to use gThumb it looks worse than Shotwell but at least it offers removing files.

I wont write about how long I've tried (and failed) to find drivers for my laptop's camera. 

Today I've downloaded new album which I wanted to have on my iPod. After downloading it I've found out that my NTFS partition wasn't mounted...
[LIST=1]
[*]Quick googling for reminding how to use mount. Success? No, partition was visible  but I wasn't able to write on it
[*]Quick googling for CHOWN; trials, errors and nothing...
[*]Google advised to install ntfs-config; unmounted partition, mounted again. No progress.
[*]Idea! Let's copy mp3s to usbstick and then from Windows import it to iTunes! The same problem: not able to write on (FAT16) usbstick. Damn!
[*]I was about to shutdown Ubuntu and download album again on Windows but I've decided to give it one more try. After opening folder to which NTFS partition was mounted (magicaly) I was able to save files there.
[/LIST]

Don't get me wrong: I love Ubuntu, philosophy behind it and it's community but there are these little things which makes it extremely hard for me to use it. 

But that was it. I had enough. I need a break.

---

### Post by Tamlynmac on 2012-11-07
> risingknee

Thank you for sharing your feedback.

I see no need to argue or make any attempt to diminish your choice. Just use what works for you. Hopefully, you'll return in the future to try again.

Good Luck.

---

### Post by MadmanRB on 2012-11-07
Next time dont buy apple

---

### Post by mastablasta on 2012-11-08
> **risingknee said:**
> My girlfriend likes to watch movies with subtitles. All I had to do on Windows was setup eg. VLC (but there is plenty of other programs which can handle it). It wasn't that easy on Ubuntu. I've tried with Parole, xine and a few others. Some didn't displayed subtitles at all, on others subs were disappearing after 10-20 minutes of playing a movie or were characters encoding was messed up. Since then we watch movies on her PC and mine I use only for watching show she isn't interested in.

 
 
aside from proprietary hardware issues and software search issue (which relaly bothers me as well) i would just like to comment on this.
 
what bothers me here a bit is why didn't you use VLC in Ubuntu as well ?
 
 
i use a very simple and light photo viewer (image view or somthing like that). Gwenview wasn't good as it hogged resources. when you turned arround the photos it would remember the "change" and attempt to save it later. anyway i think digiKam is a good photo manager with plenty features.

---

### Post by Linuxisfast on 2012-11-08
You see Apple users don't ditch their machines simply because they can't run myriads of Windows programs or hardware on it, I admire that.

---

### Post by jerome1232 on 2012-11-08
What bugs me is complaints about imaginary features that are missing.

Shotwell: When I press the Delete key, the selected images get moved to trash. (12.04 LTS but you don't seem to be talking about a regression bug)

Subtitles: The very program you mentioned worked for you in Windows is an open source media player that is very popular in Linux.

iPod: Proprietary mp3 player is proprietary, I would curse apple before I would curse Linux for that one. If they would make a Linux iTunes this wouldn't be an issue now would it? The virtual machine idea would work, I'm guessing you got confused about how to give the guest control of a usb device, which btw isn't a Linux specific issue, it's a you not being familiar with Virtualbox issue.

Your mounting an ntfs partition, Taking a wild but likely stab, you didn't shutdown Windows properly or you hibernated Windows, in both cases it won't show up in Ubuntu until you boot windows again and properly shutdown, again not really a Linux specific issue, it's actually protecting you from damaging the ntfs partition. I use an ntfs partition extensively for sharing my data across Ubuntu and Win7.

Regarding your complaint about menu digging, Xubuntu has a search feature, I can't give specifics because I don't use Xubuntu but I remember it being in the application launcher.

Frequent these forums when you have problems like this, do your googleing and then talk to us, Ubuntu has a great community and we could've helped you with all of these issues.


When I first tried Ubuntu (back on Breezy Badger) I must of given up 4 or 5 times before everything started clicking, now I spend more than 90% of my time in Ubuntu. When steam for linux matures I may spend 99.99% of my time in Ubuntu. If Ubuntu just doesn't suit you, then just use what works for you man, if you really like the idea of Ubuntu, keep it around as a dual boot and come back when you feel a little less stressed out.

---

### Post by eric-yorba on 2012-11-08
> **risingknee said:**
> I was using Shotwell for managing photos. What surprised me the most was that when I was browsing through pictures and DELETE key wasn't deleting pictures. What's more there was no option for deleting file at all.

That's simply incorrect.  Shotwell places deleted photos into its own trash bin.  That way it's a bit more difficult to accidentally remove photos you didn't intend to.  From there, the files can be deleted permanently.

All of this is explained in [the Shotwell documentation]("http://yorba.org/shotwell/help/delete.html").

---

### Post by pqwoerituytrueiwoq on 2012-11-08
i use xubuntu 12.10
> **risingknee said:**
> 
My girlfriend likes to watch movies with subtitles. All I had to do on Windows was setup eg. VLC (but there is plenty of other programs which can handle it). It wasn't that easy on Ubuntu. I've tried with Parole, xine and a few others. Some didn't displayed subtitles at all, on others subs were disappearing after 10-20 minutes of playing a movie or were characters encoding was messed up. Since then we watch movies on her PC and mine I use only for watching show she isn't interested in.
i watch stuff with subtitles, never has any issues in [vlc](apt:vlc) or [smplayer](smplayer), just check the menus (and right click video works) for toggling audio and subtitle tracks
> **risingknee said:**
> 
My PC is quite old and I'm using Xubuntu 12.10 in it. When I download programs from Ubuntu Software Center I have to go through all categories (Accessories, Office etc.) to find fre[QUOTE=risingknee;12342925]shly downloaded app. Sometimes it's not even listed there so I go back to USC to find hint on what I need to type in terminal in order to launch it. Sometimes even that fails and I have to Google on how to launch the app.
[/QUOTE]
i use [synaptic](synptic) and apt-get usually, but i know what i am looking for and when i don't i use the software center, i also check alternative.net for suggestions
> **risingknee said:**
> 
I was using Shotwell for managing photos. What surprised me the most was that when I was browsing through pictures and DELETE key wasn't deleting pictures. What's more there was no option for deleting file at all. I've found out that it was posted as a ug on Launchpad couple of years ago. Finally I've decided to use gThumb it looks worse than Shotwell but at least it offers removing files.

> **risingknee said:**
> 
I wont write about how long I've tried (and failed) to find drivers for my laptop's camera. 
most will just work, the one on my laptop does, just needed a UI for it, like [camorama]("apt:camorama") or [cheese]("apt:cheese")

---

### Post by mastablasta on 2012-11-09
> **pqwoerituytrueiwoq said:**
>  
i use [synaptic]("http://synptic") and apt-get usually, but i know what i am looking for and when i don't i use the software center, i also check alternative.net for suggestions

 
i think what they ment is that after the programme is installed they can't find it. for example in Unity or KDE you would just type it's name into search box and it iwll popout. while in XFCE you would need to go through the menues to see where the installation put it. which can be a bit annoying.

---

### Post by vasa1 on 2012-11-09
> **mastablasta said:**
> ... while in XFCE you would need to go through the menues to see where the installation put it. which can be a bit annoying.

[http://docs.xfce.org/xfce/xfce4-appfinder/usage](http://docs.xfce.org/xfce/xfce4-appfinder/usage)

---

### Post by linuxcoffeelover on 2012-11-10
HI when using virtualbox if there is any usb device you want to use you need to have the check box for usb devices checked especially if your going to be using an ipod or a usb drive ipod, phone, etc... and after installing something from the software center I like to look at the list of commands you can use for the program that was just downloaded or look at the man pages for it. or try linux mint its ubuntu based linux mint 7 was the first distro i used before i know how to really use ubuntu. oh i miss that leave a message feature but that's beside the point, but as stated it's what ever works for you.

hope you try it again soon.

---

### Post by offgridguy on 2012-11-10
I can sympathize with risingknee,  Probably not one single issue, but a combination of things that led to his decision.

---

### Post by stinkeye on 2012-11-10
A lot of us that choose to run Linux will put up with "these little things"
because we understand a lot of "these little things" occur due to the way certain companies try to lock you in to their ecosystem.
The more your locked in the more money they can squeeze from you.

In the end it's your decision but these sort of posts annoy me, especially
when looking at your profile you find this is your first and only post.

---

### Post by nothingspecial on 2012-11-10
[http://ubuntuforums.org/showthread.php?t=1921679](http://ubuntuforums.org/showthread.php?t=1921679)

Closed.

---

