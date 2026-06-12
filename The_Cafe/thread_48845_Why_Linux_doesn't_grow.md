---
title: "Why Linux doesn't grow"
date: 2005-07-14
forum: The Cafe
---

### Post by _stijn007 on 2005-07-14
Hi,

I found an interesting blog-entry [(click)](http://weblogs.mozillazine.org/asa/archives/008499.html) on Slashdot about why FireFox had an enormous growth and Linux anything but that. The author discusses some possible causes such as loss of files and settings when you migrate, dependencies, confusion because of the many programs that in fact do the same and of course comfort: /home instead of 'My Documents'.

I have been using Ubuntu for a couple of months already and I also face most of these problems (except for the confusion). Even though there have already been some intiatives to solve the other problems (e.g. XPde) but these haven't broken through (yet). Are you people at Ubuntu working on these issues ?

Kind regards,

Stijn

---

### Post by kvidell on 2005-07-14
[QUOTE=_stijn007]Hi,

I found an interesting blog-entry [(click)](http://weblogs.mozillazine.org/asa/archives/008499.html) on Slashdot about why FireFox had an enormous growth and Linux anything but that. The author discusses some possible causes such as loss of files and settings when you migrate, dependencies, confusion because of the many programs that in fact do the same and of course comfort: /home instead of 'My Documents'.

I have been using Ubuntu for a couple of months already and I also face most of these problems (except for the confusion). Even though there have already been some intiatives to solve the other problems (e.g. XPde) but these haven't broken through (yet). Are you people at Ubuntu working on these issues ?

Kind regards,

Stijn[/QUOTE]
 /home is more like C:\Documents and Settings\$USER than My Documents
Gnome and KDE I believe create a Documents and Desktop directory in /home/ when prompted.

And it's not that hard to make them yourself if you want to.
I've also never had an issue with migrating settings.
If I really care about it, I can make a backup of everything in /etc. There's also the dotted files in my home directory. Backing up the dotted files will backup personal settings, /etc/* will backup global settings.

It's not really all that difficult, I don't think. I haven't been at this stuff _that_ long.
- Kev

---

### Post by Adrenal on 2005-07-14
Also, keep in mind that while Firefox is small downloadable program, Linux is an entire os.
You can download firefox, if you like it, great, if you don't, you can return to what you're used to. You don't _have_ to learn anything.
Linux on the other hand, is different. For one, its a relatively huge download, for another, it is, in many ways, entirely different to windows. And, if you find it complicated, you can't just close a window and return to what your used to.

---

### Post by Knome_fan on 2005-07-14
Wow, I just looked at the homepage of Asa Dotzler and I'm shocked:
Pitr lives!
[http://weblogs.mozillazine.org/asa/](http://weblogs.mozillazine.org/asa/) (look at photo)
[http://ars.userfriendly.org/cartoons/?id=20050709](http://ars.userfriendly.org/cartoons/?id=20050709) (look at Pitr)

---

### Post by super on 2005-07-14
Asa's article links to this one at OS news:
[http://www.osnews.com/story.php?news_id=11179&page=1](http://www.osnews.com/story.php?news_id=11179&page=1)

I hate to say it but I agree with a lot of what is said in the article. :neutral:

---

### Post by Knome_fan on 2005-07-14
[QUOTE=super]Asa's article links to this one at OS news:
[http://www.osnews.com/story.php?news_id=11179&page=1](http://www.osnews.com/story.php?news_id=11179&page=1)

I hate to say it but I agree with a lot of what is said in the article. :neutral:[/QUOTE]

I hate to say it, but the osnews article is by far the worst article I read in ages and it's running against strong competition.

The article features not one sane argument but makes up for that with namecalling, insults, untruths and unfounded allegations. 
To put it mildly, the article is a sickening piece of crap and the only excuse for it might be the authors age.

---

### Post by Kvark on 2005-07-14
"Why Linux doesn't grow" ...linux does grow, and it grows extreamly fast if you select any point in time and count in percentage of what it had a year before that point in time.


About programs, it would help to never show "GIMP". but instead "GIMP Image Editor" as the menu already does with some of the programs but not all. Even if the users don't know what "Evolution" is they do know what "Evolution e-mail" is.


As for migrating users' data. Ideally there should be 3 partitions on a dual boot system.

1. Contains windows system and programs.
2. Contains linux system and programs.
3. Contains users' data. All /home/user/, C:\Documents and Settings\user\My Documents\ and other folders containing a user's data would point to this partition.

That way users can easily access their data normally from both systems.

---

### Post by Brunellus on 2005-07-14
[QUOTE=Kvark]"Why Linux doesn't grow" ...linux does grow, and it grows extreamly fast if you select any point in time and count in percentage of what it had a year before that point in time.


About programs, it would help to never show "GIMP". but instead "GIMP Image Editor" as the menu already does with some of the programs but not all. Even if the users don't know what "Evolution" is they do know what "Evolution e-mail" is.


As for migrating users' data. Ideally there should be 3 partitions on a dual boot system.

1. Contains windows system and programs.
2. Contains linux system and programs.
3. Contains users' data. All /home/user/, C:\Documents and Settings\user\My Documents\ and other folders containing a user's data would point to this partition.

That way users can easily access their data normally from both systems.[/QUOTE]

All fine and dandy, but you've assumed that a computer has been set up from the start as a dual-boot Windows/Linux machine.  

The truth of it all is that, for most switchers, C:\Documents and Settings\user is located on the Windows (ONLY) partition, and that would be unfortunately in NTFS, which is read-only at the moment.

---

### Post by macgyver2 on 2005-07-14
[QUOTE=Adrenal]
Linux on the other hand, is different. For one, its a relatively huge download, for another, it is, in many ways, entirely different to windows. And, if you find it complicated, you can't just close a window and return to what your used to.[/QUOTE]
 
That's where LiveCDs bridge the gap...maybe 75% of the way. A user can try it out and if (s)he doesn't like it (s)he can return to what (s)he was used to with a mere reboot (and if the user is coming from windows, that's a skill (s)he's quite familiar with anyway :) ).
 
The issue with LiveCDs is that they don't really show any of the "behind the scenes" stuff. However, if you're interested in migrating your parents/children/significant other/goldfish to Linux, and will be the one administering the system for them, then a LiveCD is perfect.
 
Now, if the goal is to advertise Linux to others who will be maintaining their own systems... A good solution could be a special LiveCD that has a fully-functional desktop system *and* and _in-depth_, _hands-on_ demo that deals with system maintenance and administration tasks. A better word than "demo" would be "simulation". A simulation (hands-on) of everyday "behind the scenes" administration tasks along with a simulation (again, hands-on...that's important) of what it's like to install and configure a typical package...all without actually making any changes or installs. A LiveCD like that would help to extend the bridge over the gap by immersing a potential user more fully in, well, "The Linux Experience".

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=macgyver2]
The issue with LiveCDs is that they don't really show any of the "behind the scenes" stuff. [/QUOTE]

The problem with the Live CD is that it runs slower, and that its harder to add needed codecs.

---

