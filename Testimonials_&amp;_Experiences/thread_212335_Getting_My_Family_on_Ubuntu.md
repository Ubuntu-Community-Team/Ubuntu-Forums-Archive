---
title: "Getting My Family on Ubuntu"
date: 2006-07-09
forum: Testimonials &amp; Experiences
---

### Post by SuperMike on 2006-07-09
I wanted to share with you how I got my family on Ubuntu. Each one in my family has their own PC. Most of them (except mine) are slow 500+Mhz systems. 

BEFORE THE MOVE

* Switched their IE and Outlook Express to Firefox and Thunderbird, telling them it's more secure. They got hooked on that and liked the features. I showed them the advantages of tabbed browsing (like on news sites) and also how to put junk mail controls on mail.

* I put ClamAV on my wife's Windows system. I watched it carefully. I also ran all the home computers through my 'tinyproxy' which I had installed on my system. We also use a firewall at home. Unfortunately, even with those controls, and one day when my proxy was down while I was reworking my PC, my young son goes to my wife's system and downloads a skateboard game that turned out to be a trojan EXE virus. If I had my EXE download blocking with my tinyproxy filter turned on, I would have prevented it. Unfortunately this opened the doorway for a whole range of viruses on the system and it got out of control.

* After that incident on my wife's PC, I convinced her that we need to give up on Windows. She agreed, to my surprise.

THE MOVE TO UBUNTU

* I installed Ubuntu on her system but did a series of changes to speed it up without taking too much away. Instead of OpenOffice, which, by the way is still installed on her system, I told her to prefer to use Abiword and Gnumeric because they are much faster but have a little bit less features. Next, I removed Nautilus from launching (it's still installed, though) and switched things over to Thunar (which is now part of XFCE, I think). I kept gnome-panel, but I made it look as close as I could to Windows 95 and even gave her a Windows 9x-looking Start Menu. (This start menu is on gnome-looks.org if you do a search on "Hopi".) I replaced icons for gcalctool with galculator and gedit with mousepad. I also made it such that she has no Nautilus desktop and therefore cannot put icons on it, which she didn't mind. I set her background color by editing a file. Last, I removed some inittabs (3 of the 6 she had enabled), and I also removed her need to use the GDM -- just boots into a login prompt and her .bash_profile calls startx.

* That set of steps sped her system up a little more than her Windows 98 she was running, but not by a huge amount. Still, it's a step in the right direction.

* I installed Automatix and put the codecs on her system so that she could play MP3s, proprietary media, and watch DVDs.

* After I had her on this, my son started messing with this and wanted his setup to be like hers, so I did it. I also installed zsnes for him and showed him how to download Super Nintendo games and play them.

* In the end, all are okay with the change so far, except my wife is nervous about what will happen when she wants to sign up with a college for her Master's Degree and start taking courses online. For that, I may have to give her an tsclient/rdesktop connection to a Windows PC, perhaps.

ONE REFUSED TO MOVE TO LINUX

* My daughter, however, is a MySpace fan and because of this she doesn't want Linux. She said she wants something that can play all those proprietary media formats flawlessly -- Windows.

SUMMARY
========

- DVD playback: too bad you can't do it by default from Ubuntu on all DVDs. It's not a fault of Ubuntu, though. It's a fault of the DVD creators.

- Proprietary Media: Something's got to be done about this. We shouldn't have to be held hostage by this stuff, having to download illegal hacks to get around it. Do you think perhaps Bill Gates, along time ago, thought that Proprietary Media will be the thing that puts the nail in widespread Linux adoption by the masses? I do.

- Users of Proprietary Media. It's not just the media, per se, but the big sites that use this stuff, like MySpace, Yahoo, and many online training companies and courseware that colleges put out.

- Xubuntu was a little too weird for my tastes. That's why I only use bits and pieces of it (thunar, mousepad) and stick with gnome-panel. I customize a default Ubuntu desktop.

- Noobs who love Windows don't like having to use something new, so they like a customized gnome-panel arrangement that looks almost like what they had. Unfortunately to pull this off cleanly, you have to do some hacks in gconf-edit, use a background bitmap on gnome-panel, and put some buttons with transparent GIFs on them in order to make it almost look the same. I wish it weren't this way, but it is.

- It's too bad there aren't enough exciting games on Linux for little kids like the kind you can funnel through zsnes. We had to download proprietary ROMs, unfortunately. I was impressed, however, with zsnes's quality and performance on a 533Mhz system -- it was stunning!

- There's no PowerPoint knockoff in the GTK2+ platform that runs about as fast as the Gnome Suite: Abiword and Gnumeric. If I go KDE, that's a whole other set of libraries that have to be installed and running in memory, and that will surely dog my wife's system. I do see the 'S5' presentation platform as very promising, but unfortunately there's no GTK2+ editor for that yet.

---

### Post by GuitarHero on 2006-07-09
If you want games for little kids maybe try Edubuntu?  Don't  know what kind of stuff it has on it...

---

### Post by nalmeth on 2006-07-11
There are in fact a lot of linux games that might cater to you and your family.

Check the [UDSF (scroll down to games area)]("http://doc.gwos.org/index.php/Main_Page"), or check sites like:
happypenguin.org/
gaming.gwos.org/ (affiliated with UDSF)

Out of curiosity, what kinds of formats are preventing your daughter from using Ubuntu? I hope it's not a DRM web she's getting intangled in!

Cool success story though, thanks for sharing it!

---

### Post by SuperMike on 2006-07-15
Wow, Eric Clapton (Guitar Hero)! I didn't know that you used Ubuntu. I've been blessed by God or something to meet your acquaintance. :p

---

### Post by mips on 2006-07-17
SuperMike,

Try this thread to optimise ubuntu:

[http://www.ubuntuforums.org/showthread.php?t=189192](http://www.ubuntuforums.org/showthread.php?t=189192)

Prelinking alone makes a big difference in speed.

---

### Post by PatrickMay16 on 2006-07-17
> After I had her on this, my son started messing with this and wanted his setup to be like hers, so I did it. I also installed zsnes for him and showed him how to download Super Nintendo games and play them.
Excellent! Give him a cheap little USB gamepad with at least 8 buttons for use with Zsnes. If you haven't already, that is.

---

### Post by Indras on 2006-07-31
My wife is quite into Myspace as well, and, to humor her, I made my own page and trolled around for a bit.  I haven't run into anything yet that doesn't render properly or won't open.  I'm curious what your daughter is trying to use that it won't let her.  If anything, she might be excited to see all of the video and image editing tools available in Ubuntu's repos, so she can make her own page layouts.

BTW: I use Swiftfox and the plugins installed by automatix.

---

### Post by aleska on 2006-08-01
Great conversion story!  Mine is actually similar, although my kids are still young enough that they don't really use the computer yet.  
For me the biggest challenge was my wife.  Several years ago, I had "convinced" her to try to make the switch to Linux on her pc.  When I say convinced, I basically made the change without really getting her buy-in.  I've now been married long enough that I know that approach doesn't work for anything!  ;) Anyway. "we" went the way of RedHat.  Long and short of that, it was a disaster.  I wasn't particularly pleased with the speed, and my wife didn't like having to use OO for wordprocessing, didn't like the netscape mail client (vs outlook), and overall she was not happy.  So we switched back to windows.
Years went by...without an upgrade to her pc hardware...
I tried my best to keep her system secure and functional over the years.  I fought an endless battle against spyware and viruses, rotating through many different anti-spyware and anti-virus tools.  I even wiped her system clean and did a complete XP reinstall when things seemed "normal" yet performance was horrible.  This is where the transition steps began...
I explained that frankly she had some old hardware and that Outlook was a memory hog and she could get much better performance if she switched from a client program to a browser-based mail like gmail.  Timed well with her desire to change email addresses as she was getting overloaded with spam.  So, we set her up a gmail account.  She took to it quickly.  Loved that she could check her email from any of our pc's (her pc doubles as the ktichen TV through a ViewSonic video adapter...in case you were curious about that).  I noticed that she really wasn't ever using word or excel, so I wasn't too worried about whether the linux equivalent would perform well or not.  
Well, over the months of using her pc basically for browser (Firefox) and playing music, she was still having major performance problems.  
I switched my own pc over to Ubuntu Linux and showed her how much faster everything works now.  I also showed her everything that substitutes the windows equivalent...   Then, one day, after she waited for five minutes just for her pc to launch Firefox, she came to me and asked, "do you think I should try Linux on my pc?".    
I was actually a bit nervous to do it...what if her pc is too old even for Linux?  So, I posted a question on the boards here giving her pc specs [http://www.ubuntuforums.org/showthread.php?t=215393](http://www.ubuntuforums.org/showthread.php?t=215393) The one response I got basically said, why not give it a try?  That was all I needed.  I crossed my fingers, installed Ubuntu, installed automatix, quickly mounted our network storage device (where we house all our files, music, etc.), chose a simple theme no background, and voila, she now has a pc that works way better than it did with windows.  She is actually very happy; and I ask her almost everyday how she likes linux, so I know.  It certainly isn't super fast for her (b/c her machine is so old and slow); but, it is way faster than what she was experiencing with XP.  
Hooray!!!!

---

### Post by paulmerchant on 2006-08-01
Great story. I'm going to start converting my family, too, once school starts next month and the games get put away. Like you I'm a bit worried about my wife's studies. It looks like her upcoming stat class is requiring a Windows only program. Perhaps in the future classes won't require Windows. It just seems wrong.

---

### Post by srunni on 2006-08-02
Just use Wine. Most of the time, it isn't a problem. If you have to , Cedega (WineX) is also available, but it costs money and is mainly used for games (but it has been known to emulate applications that Wine couldn't). As a last resort, Qemu is always available, though it does get annoying to have to go through two boots to get to one program :(

---

### Post by mips on 2006-08-03
> **aleska said:**
> So, I posted a question on the boards here giving her pc specs [http://www.ubuntuforums.org/showthread.php?t=215393](http://www.ubuntuforums.org/showthread.php?t=215393) 

I responded to that thread with some suggestions.

---

### Post by hscottyh on 2006-08-04
> **SuperMike said:**
> 
* My daughter, however, is a MySpace fan and because of this she doesn't want Linux. She said she wants something that can play all those proprietary media formats flawlessly -- Windows.


My daughter is on MySpace all the time and helps other kids setup their sites. And she does it with Ubuntu! Yes, some of the sites are a little quirky with it, but not the ones she designs. If one is a little flaky, I tell her she can always boot into windows; but she always says, "No, they should have set it up right". 

Gotta love it!

---

### Post by AmandaKerik on 2007-02-01
If she's using Firefox she can get a geeky powertrip by changing her friend's layouts with Stylish :D
I, personally, get a kick out of it...

Who knows, in a year she may be designing sites for people... for money!

---

