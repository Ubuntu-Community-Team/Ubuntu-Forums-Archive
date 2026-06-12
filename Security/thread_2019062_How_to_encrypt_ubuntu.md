---
title: "How to encrypt ubuntu?"
date: 2012-07-07
forum: Security
---

### Post by Tetrohedron on 2012-07-07
For the past few months, I have been playing with linux oses. Now that I  have a better idea about what I want from my computer, I am going to  set up a dual boot with Windows 7 and Ubuntu. I generally consider my  Windows 7 partition to be my public everybody have fun and use my  computer partition, and my linux partition a bit more of a private  playground for my various computer projects. As such, I would like to  encrypt Ubuntu.

If possible, I would really like to use truecrypt to do this. It seems  state of the art and frankly I like the idea of it. However, I don't  want to encrypt my whole system. I am not a black hat, or a criminal, or  a government spook. I don't need it. I just want some privacy and the  satisfaction of knowing that nobody can crack into my Ubuntu os (not  that I am expecting anybody to try).

What are my options?

---

### Post by Soul-Sing on 2012-07-07
Then create a container via truecrypt on Ubuntu.
Or use ecryptfs, creating a private area for "important" stuff.

---

### Post by na5h on 2012-07-07
Also, you can simply choose to encrypt your home folder during the installation of Ubuntu...it can also be done afterwards:
[http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/](http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/)

---

### Post by Ashtechsmith on 2012-07-07
For the past few months, I have been playing with linux oses. Now that I  have a better idea about what I want from my computer, I am going to  set up a dual boot with Windows 7 and Ubuntu. I generally consider my  Windows 7 partition to be my public everybody have fun and use my  computer partition, and my linux partition a bit more of a private  playground for my various computer projects. As such, I would like to  encrypt Ubuntu.

If possible, I would really like to use truecrypt to do this. It seems  state of the art and frankly I like the idea of it. However, I don't  want to encrypt my whole system. I am not a black hat, or a criminal, or  a government spook. I don't need it. I just want some privacy and the  satisfaction of knowing that nobody can crack into my Ubuntu os (not  that I am expecting anybody to try).

---

### Post by Soul-Sing on 2012-07-07
Then create a container via truecrypt on Ubuntu.
Or use ecryptfs, creating a private area for "important" stuff.

---

### Post by na5h on 2012-07-07
> **Soul-Sing said:**
> Then create a container via truecrypt on Ubuntu.
Or use ecryptfs, creating a private area for "important" stuff.

Yup...just check out the beginner's tutorial on truecrypt:
[http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

---

### Post by rookcifer on 2012-07-07
All Trucerypt will do is create a container that you can move files in and out of.  You cannot encrypt the filesystem or partitions.  TC has this option for Windows, but not Linux.  So TC is fine if you have individual files you want to keep in an encrypted container.

If you want to encrypt /home, you can do this during the Ubuntu install or you can switch over later by using encyptfs.

If you want to encrypt the entire Ubuntu install you will need the alternate install CD and will need to setup LUKS from there.

---

### Post by Tetrohedron on 2012-07-07
Wait, I thought that the truecrypt system encrypt thing could be set up in such a way as you could do a dual boot.  I thought it might be possible to use a linux os as the hidden operating system.  Not so?

Also, when I had my first distro, Fedora, there was an option to encrypt the system during instillation.  I miss that.  Ubuntu should allow the same thing.

---

### Post by Soul-Sing on 2012-07-08
> I don't want to encrypt my whole system. 

Mind what you gave us to start with, so the support/answers goes via your input/information.....

---

