---
title: "[SOLVED] Found new home dir?"
date: 2008-03-16
forum: Security Discussions
---

### Post by treymul on 2008-03-16
Hey guys, I found a new home dir on my computer that I didn't create and I cannot access.  It says that it is owned by root.  Is this normal, does it belong to an app that I have, or is this a problem?

---

### Post by treymul on 2008-03-16
sorry, meant to mention it is called tmpS3bpMc.  Does that tell ya'll anything?

---

### Post by pana.corbului on 2008-03-17
You can check your /etc/passwd to see of there is any suspicious user, and you could 'sudo rm -rf /home/tmpS3bpMc'

---

### Post by MarnickV on 2008-03-17
I'm not really a pro in these kind of things, but "tmpS3bpMc" seems weird enough to take a deeper look.. :)

---

### Post by The Tronyx on 2008-03-17
What services do you run?  LAMP, SSH, FTP?  Is your machine used for anything other than desktop use i.e. a server of some kind?  Is it on any kind of public network?  What ports are open on your machine?

---

### Post by treymul on 2008-03-17
No services that you mentioned.  I just installed ubuntu a few weeks ago on my new laptop.  I have done nothing but surf the web and burn a few cds since then.  I have installed and uninstalled quite a bit of stuff (like media players and such) looking for stuff that I like.  I checked for open ports just the other day on GCR(I think that is what the website is called) and everything looked good.  I will check it again when I get home.  Is there a better way to check my open ports?

---

### Post by The Cog on 2008-03-17
Can you post the utput of these two commands for starters?
```
ls -l /home
grep tmpS3bpMc /etc/passwd
```

---

### Post by treymul on 2008-03-17
Just checked again with SheildsUp and all ports are showing "Stealth".  Here are the outputs that were asked for:

ls -l /home
total 12
drwx------ 52 xxxxx   yyyyyyy 4096 2008-03-17 19:38 xxxxx
drwxr-xr-x 34 yyyyyyy yyyyyyy 4096 2008-03-16 21:19 yyyyyyy
drwx------  3 root    root    4096 2008-03-16 12:48 tmpS3bpMc

The grep command returns nothing.

I also checked the last logins and there were no entries except me and reboot.

---

### Post by The Cog on 2008-03-18
That is odd. I assume user yyyyyy is your original installed user. User xxxxxx is odd because his home belongs to group yyyyyy instead of his own. 

The tmp folder is very unusual, but might just be the result of a script getting confused. You can have a look in it by launching a root privileged file manager with this command:
**gksudo nautilus**

The grep command returning nothing means that tmpS3bpMc has not been installed as a user.

---

### Post by treymul on 2008-03-18
You are correct, yyyyy is the original installed user, xxxxx is another user login I created without root authority.  As far as the home locale, that might be from me trying to change some user groups or permissions(remember I am new to this).  I have opened the file in question with root authority ( sudo nano) and it appears to be a blank file.  I guess that means I can just remove it, right?

---

### Post by The Cog on 2008-03-18
You mean it's an empty directory? In that case, I would probably put it down to a screw-up by a script while you were doing something as root (or under sudo) as there is no user of that name either. 

Do check the directory s really empty first, by turning on the showing of hidden files with Ctrl-H.

---

### Post by treymul on 2008-03-18
I will check that when I get home.  I just hit 'ctrl+H' at any time after I boot, or do I need to do it at a specific time?

---

### Post by The Cog on 2008-03-18
Any time. It's there in the menus too - View->Show hidden files

---

### Post by treymul on 2008-03-19
I think I figured it out, I opened it with nautilus and its a copy of my home dir.  I think it was created with sbackup.  Does that make sense?

---

