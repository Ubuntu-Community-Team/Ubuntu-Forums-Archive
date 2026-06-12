---
title: "33 GB Wine - help please."
date: 2009-07-15
forum: Wine
---

### Post by mystmaiden on 2009-07-15
I'm running Wine 1.0 (from synaptic) and Ubuntu 8.04 . I recently did a reformat and had to reload everything. In the course of events this evening I had a lot of trouble loading poser - in the end I'm pretty sure some things loaded several times though I couldn't see them looking in the files even with 'show hidden files' checked. I've had some troubles with installers of late not showing the install screens but still installing things. 

And here's where I made the colossal blunder. I forgot that you have to uninstall with the terminal, and just deleted the files. Now its still taking up this huge chunk of my hard drive and slowing things down badly. 

Now when I run uninstaller in the terminal I get:

```
mystmaiden@hal:~$ uninstaller
err:winedevice:ServiceMain driver L"TPkd" failed to load
mystmaiden@hal:~$ 
```And of course when I click on Poser 5 - 'file not found'.

Will purging wine solve this or is there another solution?

mystmaiden

---

### Post by Mia1990 on 2009-07-15
well let's just see what's in your wine dir do sudo nautilus from the terminal then go to file system home user name then do a ctrl h to show hidden files then wine dir and see what is installed be careful not to move or delete anything as your running in super user mode and it is really easy to mess ubuntu up

---

### Post by mystmaiden on 2009-07-16
Thanks much for the reply, Mia! I took a look and it was pretty messed up so I backed out of there and went to the terminal, purged wine and started over. Its all working now. I discovered a bit of a trash problem while I was at it, cleaned that out and freed up even more space.

myst

---

### Post by Mia1990 on 2009-07-17
> **mystmaiden said:**
> Thanks much for the reply, Mia! I took a look and it was pretty messed up so I backed out of there and went to the terminal, purged wine and started over. Its all working now. I discovered a bit of a trash problem while I was at it, cleaned that out and freed up even more space.

myst

I had a feeling it was all messed up most of the time it is just better to start over.
good luck

---

