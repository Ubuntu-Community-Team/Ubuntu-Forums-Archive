---
title: "Why isn't there more talk about Nautilus"
date: 2005-06-04
forum: The Cafe
---

### Post by Curlydave on 2005-06-04
I think I've heard nautilus mentioned about once here/in the wiki/IRC. Why does noone mention this? I've been messing with it, and it's an extremely useful tool; it's like "Computer", but it lets you actually change things.

---

### Post by bored2k on 2005-06-04
[QUOTE=Curlydave]I think I've heard nautilus mentioned about once here/in the wiki/IRC. Why does noone mention this? I've been messing with it, and it's an extremely useful tool; it's like "Computer", but it lets you actually change things.[/QUOTE]
 Because here we mostly deal with bugs and helping others. Since nautilus is so straightforward , we don't need to mention it. It's learnign curve is just as low as it gets.

---

### Post by Curlydave on 2005-06-04
I mean why I've never heard that it existed, it's not in the menus etc.

---

### Post by bored2k on 2005-06-04
[QUOTE=Curlydave]I mean why I've never heard that it existed, it's not in the menus etc.[/QUOTE]
 Places > Home :? ?
Your file manager **IS** Nautilus, it just has its name changed so users could know what it is without having to know even more terminology.

In your "Computer" manager, click Help > About.

---

### Post by Curlydave on 2005-06-04
Hmmm. Then why does it block me out of my files when I use "Computer"?

---

### Post by bored2k on 2005-06-04
[QUOTE=Curlydave]Hmmm. Then why does it block me out of my files when I use "Computer"?[/QUOTE]
 What ?

As a regular user, you can manipulate everything inside your "HOME" folder. All the other stuff can only be touched as root.

---

### Post by somuchfortheafter on 2005-06-04
also for the verion of nautilus that looks more like explorer from windows enter the command 
nautilus --browser 
i may be wrong but i think it makes browsing to different directions easier considering it has an adress bar but w/e

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=bored2k]What ?

As a regular user, you can manipulate everything inside your "HOME" folder. All the other stuff can only be touched as root.[/QUOTE]

unless you use this command:

gksudo nautilus

---

### Post by benplaut on 2005-06-04
[QUOTE=poofyhairguy]unless you use this command:

gksudo nautilus[/QUOTE]
BEWARE OF ROOT!

with sudo nautilus, you can delete ANYTHING on your system, and make it unbootable (that's a bad thing, really bad).

NEVER use sudo nautilus unless you know EXACTLY what you want to do...

i have already messed up an install by incorectly using sudo nautilus...   :-x

---

### Post by Lovechild on 2005-06-04
[http://thunar.xfce.org/wiki/](http://thunar.xfce.org/wiki/) seems to be favored for replacing nautilus in Ubuntu, at least jdub seems to like it.. personally I try to avoid filebrowsing all together.

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=benplaut]BEWARE OF ROOT!

with sudo nautilus, you can delete ANYTHING on your system, and make it unbootable (that's a bad thing, really bad).

NEVER use sudo nautilus unless you know EXACTLY what you want to do...

i have already messed up an install by incorectly using sudo nautilus...   :-x[/QUOTE]

Never use sudo nautilus, it can mess up your ICEauthority file. Always use gksudo for graphical apps.

And yes....you can really hurt yourself in sudo nautilus. With that, you are as powerful as most people are in Windows normally (run a few spyware scans and you will know how badly the average Windows machine is screwed). But I hide important files in places where only root can go (and therefore gksudo nautilus) so that if I mess up my home user my files aren't gone.

---

### Post by Curlydave on 2005-06-04
I prefer not to rummage through my drive deleting and messing with system files, but that's just me. (and I don't see how running sudo nautilus when I need to move some files around will suddenly spawn spyware into my system; i'm not following the comparison there.)

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=Curlydave]I prefer not to rummage through my drive deleting and messing with system files, [/QUOTE]

Me neither. I never touch important stuff unless I'm trying to break things. But I DO have a certain folder with all of my best information in it in /home/ that my default user can only look at- never delete or destroy. When I need to edit/add files to this folder, I use gksudo nautilus

[QUOTE=Curlydave]but that's just me. (and I don't see how running sudo nautilus when I need to move some files around will suddenly spawn spyware into my system; i'm not following the comparison there.)[/QUOTE]

Sorry. Confused a little I guess. I was saying two different things. 

A. Don't use sudo for graphic apps. Use gksudo instead.

B. The fact that most Window's users run in administrator mode (or sudo in Ubuntu) all the time is the reason that programs can install themselves without the user ever giving a lick of permission.

---

### Post by Curlydave on 2005-06-04
Ohhh, I follow now. Thanks for all of the information btw, I appreciate it. And yea, I meant gksudo for that, that's what I've been using. Now that I have a shortcut to that, it seems silly to root it all; it's no big deal to enter a password every once in a while. I guess I'm just having a hard time getting used to this.

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=Curlydave]Ohhh, I follow now. Thanks for all of the information btw, I appreciate it. And yea, I meant gksudo for that, that's what I've been using. Now that I have a shortcut to that, it seems silly to root it all; it's no big deal to enter a password every once in a while. I guess I'm just having a hard time getting used to this.[/QUOTE]

Its cool. It took me a while too. But the I realized that the password thing is great. My best files are safe behind a password. And if an app needs a password that shouldn't (say firefox) then I know something is up. It is safer. 

Now after doing it this way for a year, the biggest thing that bugs me about the Window's world is such a lack of a fine turned multi-use desktop experiance. The fact that my mom needs to run as an admin to do quicken hurts me. It wouldn't if XP had something as elegant as gksudo. (run as doesn't work, I tried).

---

