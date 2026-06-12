---
title: "Truecrypt Installation"
date: 2008-11-30
forum: Security
---

### Post by dbrine on 2008-11-30
I am running 8.10 and trying to install Truecrypt 6.1. Need help installing please. I've never had this manhy problems before. thanks

---

### Post by monsterthrash on 2008-11-30
I just did this myself and, yeah, it's a pain.  After you download and extract the archive, do:

```
sudo ./truecrypt-6.1-setup-ubuntu-x86
```

Choose to install the .deb and scroll through the license agreement.  Now, you may get a list of missing dependencies (I assume this is where you're stuck).  Do an *apt-get install* on the list of dependencies it gave you.  If, after you do that, you still get another list of dependencies, do:

```
sudo apt-get -f install
```

It's important to run that line *without* any packages listed, just run it as-is.  After that, Truecrypt should be installed and ready to use.  Type *truecrypt -h* for options.

---

### Post by tubbygweilo on 2008-12-01
I access Truecrypt via  Applications > Other > TrueCrypt and it works for me.

---

### Post by dbrine on 2008-12-01
worked great, thanks for the help

---

### Post by bodhi.zazen on 2008-12-01
Solved:

Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by marcgh on 2009-01-27
If I just may come in:
I am using TrueCrypt for some time now in XP.

I was really surprised it aslo exists for Ubuntu.
I tried the install in Intrepid.....perfect.
I can now open the fully encrypted disk in XP from in Ubuntu. This saves me a lot of booting from one to another and back.

This Intrepid is amazing me every day a bit more!

---

### Post by shqip on 2009-01-27
Why doesn't Ubuntu comes with an encryption solution when you first install the OS like fedora? Basically to give you an option if you want to chose to encrypt or not.

---

### Post by bodhi.zazen on 2009-01-27
> **shqip said:**
> Why doesn't Ubuntu comes with an encryption solution when you first install the OS like fedora? Basically to give you an option if you want to chose to encrypt or not.

You have this option in Ubuntu as well, it is on the Alternate CD (rather then the desktop).

9.04 offers an encrypted /home on both desktop and alternate CD (using this option now).

---

### Post by kevdog on 2009-01-28
If monsterthrash could actually write up the steps that he performed in a formal writeup, listing the dependency packages that he needed to install --- It would be a great help to everyone!!

---

### Post by rastignac44 on 2009-02-03
> **kevdog said:**
> If monsterthrash could actually write up the steps that he performed in a formal writeup, listing the dependency packages that he needed to install --- It would be a great help to everyone!!

And perfect for a solved problem thread.

---

