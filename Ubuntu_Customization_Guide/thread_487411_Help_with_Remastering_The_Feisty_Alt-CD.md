---
title: "Help with Remastering The Feisty Alt-CD"
date: 2007-06-29
forum: Ubuntu Customization Guide
---

### Post by Igtenio on 2007-06-29
I apologize if this's the wrong place to post this, but I wasn't sure where exactly to place it.

Recently, I've been dabbling with making a Remastered CD of the Feisty 7.04 Alternate CD.

The basics of what I want to do are take a Command-Line installation, put KDE-Core on top of it, then add Firefox, Thunderbird, Synaptic, APTonCD, NTFS-3G, and NDISWrapper, along with their dependencies.

Being on Dialup, it isn't even remotely easy doing so, because not only do I have to play the waiting game, but unless I want to sort the dependencies myself, I have to download them through APT-GET, which means I need to watch and make sure it stays connected, whereas with a Download Manager it could just start back up by itself if I get disconnected.

I finally got all the packages I need together, and went about trying to follow the guide for remastering the Alternate CD _[here](https://help.ubuntu.com/community/InstallCDCustomization)_, on the Ubuntu Community Documentation. It's out of date, but I figured, hey, it couldn't be that different.

It says, first off, that while it uses /opt/cd-image, you can do it anywhere. So, after dicking with permissions a bit, I decide to just do it in my Home directory, under the folder "Iggybuntu". So instead of being in "/opt/cd-image", it's in "/home/igtenio/Iggybuntu/cd-image".

I'm going along, everything's alright, I edit a few references from dapper to feisty, change the location from /opt/ to the folder in Home, et cetera and so on...I try to use that script it links to on another page to strip out the packages I'm not using, and I'm a bit surprised that it only seems to leave a hundred megs or so of packages, but I figure that, with all the extra packages, maybe the Command-Line installation only uses 100 or so megs of packages.

And then it just all fell apart at the end. From "Building the repository with apt-ftparchive" and down, it just fell apart. I'd make the files, editing the necessary portions, and when I tried to run the script at the bottom of that section, it kept trying to use /opt/ instead of ~/Iggybuntu/, despite the fact that I went through it with a fine-tooth comb and made sure that *nothing* pointed to /opt/.

I ended up adding the right directories and files to /opt/, and it seemingly worked, but when I went to install the CD, it wouldn't even bring up the options(You know, Install Server, Install Command-Line System, et cetera).

This probably sounds like a horribly open-ended question, but what do I do? Do I try it again, running as root instead of a regular account and doing it in opt, and sticking as close to the page as I can, minus the changes from dapper to feisty? I'd really rather not use dapper for this, since I've already downloaded all the packages for feisty, and it'd take absolutely forever to not only download new packages, but download the dapper install CD(Around 40 hours for me, and I rarely get to download for more then 8 or so a day).

Thanks for any help you can give me.

**Edit**: Well, I just realized I messed it up a bit more then I'd thought, by putting the files into cd-image, instead of build... ~_~ I guess I get to try again tomorrow, but any advice you can give me on the above?

---

### Post by Igtenio on 2007-07-12
Er, I realize it's not exactly Kosher, but I don't take issue with bumping this after a while.

To be honest, I've basically given up. I'd like to customize it, but it seems like all the documentation is for older versions. I've found a couple of scripts and programs online claiming to help customize, but they seem to either not work for the new versions, even if I go through and make corrections, or offer limited customization when it comes to the InstallCD.

I'd highly appreciate any help that anyone can offer me on messing with the Feisty InstallCD. Even if it was just links.

---

