---
title: "folders, permissions, and moodles, oh my!"
date: 2006-09-08
forum: Server Platforms
---

### Post by uncleclinto on 2006-09-08
Okay kids,

I really really thought I was through bugging y'all, but my limited understanding of Linux's drastic differences from windows strikes again.

I installed my moodle (finally).  Now, I think I found where the files are stored (var/lib instead of var/www).  Why that is I don't know.  The problem is, the folder's contents are blocked from graphic access because I am not the folder's "owner".  Why the hell not?  It's my folder.  I understand that Linux wants me to do all access to my files through a command prompt, but did it ever occur to the stupid penguin that I may be using a graphical editor through Samba, like Dreamweaver?  Hey, I may have a cool banner or two that I made in Fireworks that would be really nice to drag and drop.  That's why I bothered to install a desktop on my LAMP server (so I wouldn't have to mess with the command prompt every time I wanted to make an adjustment).  

Could someone please please help this designer (not developer) change his folder permissions computer wide so he can actually access them and drag and drop and maybe make his moodle look half as cool as it does on his WINDOWS SERVER?

---

### Post by uncleclinto on 2006-09-10
Okay,

Please, someone help.  :(   I need to know how to change the permissions on the folder "var/lib/moodle" so that I can open it in the graphical desktop environment, drag my custom graphics in there, and place them in the appropriate sub-directories so they'll show up on my moodle.  Basically, I want it to work like folders in windows.  Should I ask this question in the desktop NG, even though this desktop environment is on my server?

please help

---

### Post by scxtt on 2006-09-10
[size=4]insulting the penguin == no help.[/size]

:evil:

[chmod,chown,chgrp] will allow you to change permissions of a file - read up on them (i.e. **man chmod**)

using sudo will allow you to view any files on your computer, so try something like **sudo nautilus** or **sudo konqueror**

---

### Post by BoneKracker on 2006-09-11
First a bit of a lecture, then some help:

I understand your frustration, but you are not using Windows any more.  Unix-like operating systems don't work like Windows, and that's a good thing.  Don't expect them to.

It's probably a good idea to spend a little time learning how to use some of the basic functions of your new operating system before trying to set up a server, install new software, etc.  Some aspects of GNU/Linux are just like Windows, and you can leverage your experience.  Some aspects are very different, and you must put yourself in "student mode" and do a little work first before you can reap the benefits.

File permissions is an important access/security feature of an operating system, but it has been dummied down so much in Windows that it's essentially ineffective as configured by default.  This arises from the fact that Windows was historically neither networked nor multi-user and therefore had no need of such controls which users must be educated to understand.  Then, with a user base thusly spoiled and resistant to security measures that inhibit their free access, they had to hamstring half the security features of NT to make it XP.  

In XP, you're either administrator or not administrator (and just about everybody is the administrator).  This NT-based OS has much greater capabilities (similar to unix-like systems), but they are hidden from view of the average user.  When a user has administrative privileges, they are free to access, change or delete any file on the computer.  Windows tries to reduce the likelihood of this by hiding some files from view or making them "read only" so you don't accidentally delete them.  This does nothing to protect you from somebody who WANTS to delete or change them.  So if you're online and somebody sniffs your password, hacks your machine and assumes your identity, they have total control -- and that's a bad thing.

Ok, now the help:

So you need to learn about permissions.  This is one of the first thing every user needs to learn.  One way is to read the manual for each of the three commands described in the earlier post.  (Go to the terminal and type "man " and the command.

But I think that these manual pages will be too confusing for you.  If you haven't done so yet, I suggest that you read through the documentation that is designed for new users.  Explore (fully) the menu items under "System->Help".

Once you understand the system, you'll see how easy it is.  There are gui tools to help.  Of course, the easiest way is the command line.  After using these commands a few times you won't even have to think about it and it's much faster than clicking on a bunch of buttons:

```
sudo addgroup moodlers
sudo adduser myusername moodlers
sudo chown -r root:moodlers /var/lib/moodle/*
sudo chmod -r 770 /var/lib/moodle/*
```

That creates a new user group called "moodlers" (anything is fine), adds you to the group (replace "myusername" with your username), changes the file ownership for all the files in all directories within /var/lib/moodle to be owner="root" and group="moodlers", and restricts access (of all types) to only root or members of group "moodlers".

If you are absolutely the only one who will access these files, then you don't need to create the group, you can skip the first two lines and replace moodlers with your username.

---

### Post by uncleclinto on 2006-09-11
Okay, point taken.

[LIST=1]
[*]I'm sorry for insulting the penguin.
[*]I'm only here because the people over at apache made me feel like a moron for asking questions about my windows-apache server.
[*]I really have no desire to learn linux as a primary operating platform.
[*]I am way out of my element and can't play with the big kids (sorry).
[*]You've made your point.  I'll just go back to windows with my tail between my legs and muddle through my own problems.
[*]If I could have figured this out with the user guide, I would be here ranting like an idiot.
[*]chown says my var/lib/moodle folder doesn't exist, but I can see it.
[*]I'm getting a beer and starting over.
:-| :-| [/LIST]

---

### Post by scxtt on 2006-09-12
> chown says my var/lib/moodle folder doesn't exist, but I can see it.keep in mind that there is a BIG difference between:

var/lib/moodle

-- and --

[size=4]**/**[/size]var/lib/moodle

you most likely want /var/lib/moodle ...

---

### Post by BoneKracker on 2006-09-13
Don't get discouraged.

Most of the time when I get error messages of that "no such file or directory" type, it's because I forgot to type "sudo" first.

And scxtt's right...

"var/lib/moodle" starts looking for var from whatever your current directory is now (like maybe /home/you?)

"/var/lib/moodle" starts looking for var from the root /


Why?  

So when you're sitting in your home directory working on a document that's at, say
```
/home/you/docs/work/projects/instructional

```and you want to move down one directory to ```
/home/you/docs/work/projects/instructional/graphics
```
you only have to type
```
cd graphics
```
instead of```

cd /home/you/docs/work/projects/instructional/graphics
```

In general, files that have something to do with each other are usually stored together, so this makes it simpler (faster, less error) for programs to operate on data files, call related programs, and so on.  As above, it also makes it easier for a user to work on several related files.

---

### Post by uncleclinto on 2006-09-15
Okay,

chown and chmod seem like very valuable commands to learn, and I'm sure I'll learn all about them as I tinker with ubuntu.  For the time being, here's the simple solution to my problem that I picked up elsewhere:

"sudo nautilus"

That's all I needed.  A simple way to view and access my files graphically with administrative priveleges.  

Tux and I are tight again.

---

### Post by BoneKracker on 2006-09-18
Yeah, that'll work.  But you still need to know what the buttons and check-boxes actually do.  When the instructions for something say "set permissions 644" on a folder, will you know what that means in terms of check-boxes to click?

Even easier, you can install a script that will run nautilus as root from the menu.  Or you can put a little file browser right on your panel that will do it.

In fact, you can install a script that will let you right-click on anything you want and "run as root".

---

