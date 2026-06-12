---
title: "Clever .desktop files?????"
date: 2019-01-03
forum: Ubuntu, Linux and OS Chat
---

### Post by giel2 on 2019-01-03
Some of you use custom .desktop files to put items in the menu to do clever things or increase productivity?    Ofcourse I don't mean to simply start an application, but fancy commands that you can start from the menu :-)  I'm curious!

---

### Post by TheFu on 2019-01-04
If you want to increase productivity, don't use menus.  I've setup about 10 keyboard accel chords to perform different tasks without using a menu.  These tasks can be very simple or anything that can be scripted.  Many of those scripted items run automatically every 4 hrs, so the processing doesn't back up.  

For example, I hate commercials in recorded TV, so a few times a day, I'll move TV recorded files (mpeg2) to a different system for processing.  The processing is split into 3 tasks.
* Move the new recordings to a faster system that looks for commercial breaks and marks them as EDL.
* Manually use a video editing tool to load the EDL and video file to correct incorrect cut points. This takes about 30 sec per recorded show. Batch run the removal of the commercials.
* Periodically, check for freshly cut shows, transcode from mpeg2 --> h.264, process captions, translate captions from Spanish to English if English captions aren't included, then bundle everything into a single mkv container and move the file into the correct location for Plex to "own it".

Most of the work is automated, but the manual validation/correction step is necessary. A 1 hour HiDef show takes about 30 minutes of processing, but I don't want to sit and wait around for that when only 30 seconds of my time is needed.  Doing this saves time up front, but also during watching and it saves about 70% of the storage required. It is common for a 1 hr show to use 7-10GB of storage.  Cutting the commercials and transcoding will make the same show under 2G without any viable quality loss.  Taking the transcoding down to 720p can easily get it under 1G in size with minimal artifacts.  My solution is sorta complex because the recordings happen on a different machine than the processing which is different from the final streaming machine.

That's 1 example. I've scripted all sorts of things over the decades.  I'm a heavy user of RSS for news, but have a system pull all those articles local and show them inside a single interface to avoid having to visit 25 different websites.  Plus, because they are local and automatic, what I read or don't read is much more private.  It is easy to take all those articles and drop them onto a tablet for reading off-line, though they are available to me via a VPN to the house from any of my internet connected devices.  All the devices have a single view, so once I've read an article on the tablet, then it isn't shown on the laptop, desktop, or phone. Never having to see a story I've already seen is priceless.  And efficient.

For me, productivity means avoiding menus. Anything that takes my hands away from the keyboard is anti-productive. Actually, I've simplified my GUI to not have any menus at all.  

But everyone is different.  Not all workflows lend themselves to non-GUI techniques.  If I was a webGUI designer, it would be next to impossible to work without using a mouse, I would suspect.

---

### Post by yetimon_64 on 2019-01-04
> **giel2 said:**
> Some of you use custom .desktop files to put items in the menu to do clever things or increase productivity? Ofcourse I don't mean to simply start an application, but fancy commands that you can start from the menu I'm curious!
I do agree with TheFu about menus generally and can launch most of my custom scripting with mouse gestures or keyboard shortcuts etc.

However while using the xfce desktop I find having all my most often used applications and custom scripting available from the panel to be very handy. Xfce desktop lets you create "drawers" full of launchers, "launchers" being desktop config files of course.

My current desktop config file count for the directory ~/.config/xfce4/panel (the location where all config files related to the xfce4 panel are stored) is 249. The vast majority of those config files are for launching custom scripting for controlling various aspects of my desktop. If I have to use the terminal on more than a few occasions to alter some aspect of my desktop environment or if I regularly use a particular application I create or copy a desktop config file for it and add it to the panel for easy access.

I have included a screenshot of 1 of my drawers, specifically for launching a custom scripting package I call "hipafiam" (hidden partition finder and mounter). This is a scripting package I wrote about 4 years ago to show/mount any partitions that I normally would hide from the DE. As a dual booter I don't like any other system or special storage partitions showing in the current DE so I flag them so as to hide them (can easily be set with gparted), but if I want easy access to data in them I launch my custom script "hipafiam" or one of its variants. Hipafiam then mounts the usually hidden partition to a custom location, taking into account any necessary safety checks for partition/device presence/absence and mount status etc.

From left to right in the 1st screenshot ...
1. Is the launcher properties box, from right clicking the icon on the panel, which shows most of the launchers.

2. The drop down menu/drawer, this is where I can click and launch/control my scripting from.

3. The actual custom scripts held in ~/bin/Console/Hipafiam. A custom location that is included in my user's system path.

4. The actual desktop config files that I've created on the panel then copied to the ~/.local/share/applications directory (for backup if the xfce4 panel settings become corrupted or lost; it has happened to me in the past :-)).

A second screenshot shows the top launcher (tux icon) activated, all 3 variants of hipafiam are active showing available volumes for mounting; the smaller nautilus window shows the nautilus devices menu with no volumes available. Note I am running a hybrid DE set up with xfdesktop using applications like nautilus and gnome terminal etc (on Ubuntu trusty 14.04).

Although most of the hipafiam scripting can be controlled with mouse gestures and/or keyboard shortcuts, the drop down panel drawer using desktop config files turns out to be the easiest/quickest option for my usage. Though, with respect to menus, I do tend to hide most of my custom scripting from the DE with the "NoDisplay=true" option within the desktop config files.

Finally: As I am using an install with multiple DEs I have also been able to integrate some of my custom scripts for desktop image setting into the context menus of the xfdesktop and apps like gthumb etc. This was largely possibe by setting the "MimeType=" option within the desktop config files. I have found that being able to manipulate desktop config files is an extremely useful tool indeed.

Cheers, yeti.

---

### Post by giel2 on 2019-01-10
Thank you for your replies!

---

