---
title: "A help to the community?  New user info..."
date: 2008-12-14
forum: The Cafe
---

### Post by Nixie Pixel on 2008-12-14
A lot of people here have helped me get on my feet running Ubuntu (Hardy and Intrepid), and I wanted to give back to the community in my own way.  I can't really give the technical advice needed to make a difference here in the forum, so I'm creating a little repository of information that will, hopefully, help people who were in my position as a brand-new Linux/Ubuntu user.

I also want to help people find interesting, fun games that they can play on Linux.

My first goal is to gather information about what people do when they first install Ubuntu.  I tried asking this in the support forum, but the message got washed away rather quickly.  Can anyone here point me to a newbie guide for post-installation tweaks?  I have a few of my own, but there must be something a little more comprehensive out there.

My first blog post on Linux, if you're interested =D :

[[COLOR="RoyalBlue"]An Ubuntu girl in a Windows world...[/COLOR]]("http://nixiepixel.com/blog/blog7.php/welcome")

Thanks again,

~Nix

---

### Post by shadowdude1794 on 2008-12-14
Very nice blog post, and welcome to the community! If you want something that can configure some of little things, Ubuntu tweak is an excelent tool. Also if you haven't already gotten it, CCSM is great for messing with compiz-fusion's settings.

---

### Post by 73ckn797 on 2008-12-14
Here is a link to installing OpenOffice 3.0 in Ubuntu. It is how I did it and it works everytime. I have been using Ubuntu since August 2008 and understand what a newbie has to deal with.

[http://ubuntuforums.org/showthread.php?p=6090196#post6090196](http://ubuntuforums.org/showthread.php?p=6090196#post6090196)

Here are the details to copy to your web site:

> I have installed OO 3.0 on my desk and laptops with Hardy and Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic.

Went to [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US) 

Selected the English (in my case) version: OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org

Created a directory in /home/name/whatever. 
edit: name = your name (directory created during Ubuntu installation) (whatever = Oo30 (that is what I named it) There is actually another sub-directory created so you could just extract to your home folder or even to the desktop. Once installation is completed you can delete the folder. With in that folder will be a DEBS and desktop-integration sub-directories.

Extracted files using File Roller (default Gnome compression utility) to the created directory. Double click on file downloaded will open in File Roller.

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon if you do not like the default short-cut name.

---

### Post by 73ckn797 on 2008-12-14
> **Nixie Pixel said:**
> A lot of people here have helped me get on my feet running Ubuntu (Hardy and Intrepid), and I wanted to give back to the community in my own way.  I can't really give the technical advice needed to make a difference here in the forum, so I'm creating a little repository of information that will, hopefully, help people who were in my position as a brand-new Linux/Ubuntu user.

I also want to help people find interesting, fun games that they can play on Linux.

My first goal is to gather information about what people do when they first install Ubuntu.  I tried asking this in the support forum, but the message got washed away rather quickly.  Can anyone here point me to a newbie guide for post-installation tweaks?  I have a few of my own, but there must be something a little more comprehensive out there.

My first blog post on Linux, if you're interested =D :

[[COLOR=RoyalBlue]An Ubuntu girl in a Windows world...[/COLOR]]("http://nixiepixel.com/blog/blog7.php/welcome")

Thanks again,

~Nix


Nice web site. I will contribute what I can to help out. It really will not be that much but it will be, I hope, what you are looking for. 

Welcome to Ubuntu.................):P

---

### Post by MikeTheC on 2008-12-14
Looks really cool and well thought-out. Additionally, you are an excellent writer. I will be happy to help. Either post here or PM me with what you are looking for, and within what knowledge I have, I will answer what I can.

---

### Post by Joeb454 on 2008-12-14
Nice post :) I even made a comment, which was quite a long comment for me actually :p

I look forward to reading more

---

### Post by aschwerin.moses on 2008-12-14
Well.. i would suggest u to install these software's (to name a few) if u have'nt yet..

**startupmanager** (helps u manage how ubuntu must start)
**gparted** (a disk manager like in windows)
**ntfs-3g ntfs-config** (helps u auto mount NTFS partition)
**nautilus-wallpaper** (can right click on a picture in click on "Set as wallpaper" which is'nt the default option in Nautilus)

---

### Post by magmon on 2008-12-14
Ugh, tell them how to install java. Its always like a friggin 60 step process getting runescape to work xD

---

### Post by Joeb454 on 2008-12-14
> **aschwerin.moses said:**
> 
**ntfs-3g ntfs-config** (helps u auto mount NTFS partition)


Check the link in my sig, I wrote a how-to guide on that ;) Also ntfs-3g is installed by default now :D

> **magmon said:**
> Ugh, tell them how to install java. Its always like a friggin 60 step process getting runescape to work xD

Surely it's just ```
sudo apt-get install sun-java6-bin
``` or installing [ubuntu-restricted-extras]("apt://ubuntu-restricted-extras")

---

### Post by magmon on 2008-12-14
Lol joeb, it should be. But I always have to go into synaptic and install all the java junk then go into add/remove menu and add all the java junk after I run that before EVERYTHING works xD. No complaints, it still beats vista.

---

### Post by dannytatom on 2008-12-15
Nice post, Nixie. :)

The first thing I do after doing a fresh install is get [finch]("http://developer.pidgin.im/wiki/Using%20Finch"), [lynx]("http://lynx.isc.org/") and [irssi]("http://www.irssi.org/about").  That way, if I screw something up and am without a graphical interface, I can still get some help. :O

Btw, all 3 are in the repositories, so you can just do an apt-get install on 'em.

---

### Post by dannytatom on 2008-12-15
whoops, double post.

---

### Post by Nixie Pixel on 2008-12-15
Wow, thanks for all the replies!  The response has been greater than I anticipated.  

I think that with all of your continued help I can make these newbie guides very useful!

---

### Post by Nixie Pixel on 2008-12-17
I haven't written any guides yet, but I did finish a post I had been thinking about regarding how new users view Linux.  Hopefully it may help a bit, or at least generate some thought.  Let me know what you think!

[Ubuntu sucks.  I hate Linux!  (No, not really)]("http://nixiepixel.com/blog/index.php/ubuntu-sucks-i-hate-linux")

Thanks,

~Nix

---

### Post by carnadi88 on 2008-12-17
> **Nixie Pixel said:**
> A lot of people here have helped me get on my feet running Ubuntu (Hardy and Intrepid), and I wanted to give back to the community in my own way.  I can't really give the technical advice needed to make a difference here in the forum, so I'm creating a little repository of information that will, hopefully, help people who were in my position as a brand-new Linux/Ubuntu user.

I also want to help people find interesting, fun games that they can play on Linux.

My first goal is to gather information about what people do when they first install Ubuntu.  I tried asking this in the support forum, but the message got washed away rather quickly.  Can anyone here point me to a newbie guide for post-installation tweaks?  I have a few of my own, but there must be something a little more comprehensive out there.

My first blog post on Linux, if you're interested =D :

[[COLOR="RoyalBlue"]An Ubuntu girl in a Windows world...[/COLOR]]("http://nixiepixel.com/blog/blog7.php/welcome")

Thanks again,

~Nix

Nice site. Welcome to Linux.

---

### Post by Nixie Pixel on 2008-12-19
Thanks for all the encouragement!

My first "help" post is up.  Let me know if you think it is useful, and how it can be improved?

Thanks!

[[COLOR="RoyalBlue"]Nixie's Ubuntu Linux - A Travel Guide for Visitors from Windows[/COLOR]]("http://nixiepixel.com/blog/blog7.php/nixie-s-ubuntu-linux-a-travel-guide-for-")

---

### Post by handy on 2008-12-19
Welcome too. :-)

You may find this site helpful:

***_[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)_***

---

### Post by vikramaditya on 2008-12-19
Nice blog, nixie, and well written.  What part of SoCal are you in?  I lived in Hawthorne during the upper Oligicene, long before marauding pods of "disenfranchised" inner-city thugs claimed it as their own. ;)

---

### Post by Nixie Pixel on 2008-12-20
Sorry, I am in NorCal...did I mistakenly put SoCal somewhere??

---

### Post by magmon on 2008-12-20
Tell them to install Realplayer for rmvb video files. Took me forever to figure that one out.

---

### Post by Nixie Pixel on 2009-01-31
I would love to update the guide a little bit, and have an idea for what would be useful.  Can anyone here tell me a way to troubleshoot kernel panics that would make sense to a Windows user?  I've had a real hard time finding help on how to do that, and understanding what tools, if any, are available to assist with it.

---

