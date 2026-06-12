---
title: "Is this software available for Linux?"
date: 2007-09-23
forum: The Cafe
---

### Post by Bart_D on 2007-09-23
These guys

[http://www.mackichan.com/](http://www.mackichan.com/)

offer in their "Products" section, a software called Scientific Word.  I tried it out for Windows  and liked it.  I was wondering if there is a Linux version available?  If not, is there an equivalent piece of software that Linux offers.

I've found that it is faster than using LaTeX (for me atleast).  I would want to be able to produce TeX documents and was able to do this with a snap using Scientific Word so would really like to be able to do this with Ubuntu/Xubuntu.  I am open to using something else, if it exists in Linux, as long as it doesn;t bog me down the way LaTeX did.....cause I wasted hours upon hours formatting in notepad to make it look the way I wanted it to.

---

### Post by matthew.lns1 on 2007-09-23
Try to run it with WINE. Sometimes that works.

---

### Post by ingolemo on 2007-09-23
Have you tried LyX? Is that the kind of thing you're after, or are your needs more specific?

---

### Post by Bart_D on 2007-09-23
It certainly appears that LyX would do.  HOWEVER, I don;t have access to my Ubuntu box right now so can't check Synaptic but [http://www.lyx.org/download/](http://www.lyx.org/download/) says that it is only available for Windows/Mac?

---

### Post by Frak on 2007-09-23
Go for the official mirrors, not the ports, also try
```
sudo aptitude install lyx
```
May work

---

### Post by Bart_D on 2007-09-29
Ok, I'm going to give this is try soon but from the LyX website, I read that certain OTHER packages are required to install LyX.  It goes through a bunch of stuff listed as "Required Software"...all free but my question is whether I require all that software in Linux------>Ubuntu Fiesty?

---

### Post by Frak on 2007-09-29
> **Bart_D said:**
> Ok, I'm going to give this is try soon but from the LyX website, I read that certain OTHER packages are required to install LyX.  It goes through a bunch of stuff listed as "Required Software"...all free but my question is whether I require all that software in Linux------>Ubuntu Fiesty?
Those "other" software are called **Dependencies**, and they are automatically installed with it if you install via apt-get or aptitude.

Compiling from source can be a pain-in-the-***, if you don't have much experience with it.

---

### Post by Bart_D on 2007-09-29
So, should

```
sudo aptitude install lyx
```

be sufficient to get everything needed?  I am quite new to Linux.

---

### Post by Frak on 2007-09-29
> **Bart_D said:**
> So, should

```
sudo aptitude install lyx
```

be sufficient to get everything needed?  I am quite new to Linux.
Yes :)

We're all new, no matter how much time has passed. I think only the dev's actually fully understand how Linux and Ubuntu work.

---

### Post by lennartack on 2007-09-29
> **Bart_D said:**
> So, should

```
sudo aptitude install lyx
```

be sufficient to get everything needed?  I am quite new to Linux.
Yes, that will do everything. Alternatively you van run the program "Synaptic" from the system menu, search for it and install it. If you want to install a program, also try to find it in synaptic first.

---

### Post by Bart_D on 2007-09-29
Thanks! Yeah I'm pretty comfortable doing that.  I guess I;ll try one of these 2 methods.

---

