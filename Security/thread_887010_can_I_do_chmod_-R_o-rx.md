---
title: "can I do chmod -R o-rx / ?"
date: 2008-08-11
forum: Security
---

### Post by magiver on 2008-08-11
Hi

I installed vsftp to give my girlfriend access to my music folder so she can download some mp3s she wanted.
In the process, I realized that she can read and execute almost any file in my system, including my home directory.
What I've done so far is chmod -R o-rx myUser and I created a ftp group and a soft link to my music directory in her home so she can get access to my mp3s but not the rest of my home folder. 
The question is, can I do a chmod -R o-rx / ?

not that i don't trust her or anything like that, but your firefox history is something you don't what to show (and you know what I'm talking about!).

thank for your time.

---

### Post by Mister.Vash on 2008-08-11
I think you might be looking at it the wrong way.  Instead of having to lock down everything on your system to prevent access to your data or files, you might want to set it up so that the ftp account can't go to those places.  Vsftp is  a pretty powerful took, you might take a look at some examples to see how other folks have set this up, this is one that comes to mind

[http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html](http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html)

Basically, the idea is that you lock the user into a certain area, and they can't get out and see other things - it can even be used so that via ftp, the files would be read only, but a specific folder could be create where items could be deleted or removed

---

### Post by magiver on 2008-08-11
Sounds just like what I need.
Can I make a soft link to a folder in my home directory using this settings?

---

### Post by magiver on 2008-08-11
Sounds just like what I need.
Can I make a soft link to a folder in my home directory using this settings?

---

### Post by Mister.Vash on 2008-08-12
I don't think the soft links will work, but a mount will, you just need to pay attention to the permissions.

Here another link, pretty simple, just note the bit about making persistent across reboots
[http://www.vinno.net/linux/server/chroot-mount-trick](http://www.vinno.net/linux/server/chroot-mount-trick)

---

### Post by hyper_ch on 2008-08-12
I'd install mysecureshell and lock her in a chroot of your music files and give her, except for 1 upload folder, read-only privileges. Then she can use WinSCP or another sftp compatible program.

---

