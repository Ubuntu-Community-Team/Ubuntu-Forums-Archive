---
title: "login failure to poweroff"
date: 2013-05-04
forum: Security
---

### Post by slowday on 2013-05-04
My box only connects to the internet and no home networks. Usually when not in use I shut it down, sometimes I leave it running and unattended for one reason or another. It's these times when I'm away that concern me, is there a way to change the login to power off after three attempts?

---

### Post by Stonecold1995 on 2013-05-04
While I can't answer your primary question (shutting off after three incorrect password guesses), I may still be able to help.

Are you worried about intruders from the internet?  Or physical access?  If you are afraid of hackers, you don't have to be.  Ubuntu is very secure and unless you're running sensitive software which can allow outside access (SSH, web servers, etc), no matter how many times someone tries to guess your password that way, they won't get in.

If you are afraid of physical access, the only thing you can do is encrypt your drive.  As someone in another thread said, think of your computer as a flash drive with a few extra features.  If you want it to be secure, you have to encrypt everything.  If it's not encrypted, then your user password provides absolutely no protection.  Someone can easily power down your computer, boot into a live CD (or if you have a BIOS password set, simply take out the hard drive), and read the unprotected data from there.

One last thing: if your password is so weak that you worry about someone getting in in three tries, I suggest you change your password!

---

