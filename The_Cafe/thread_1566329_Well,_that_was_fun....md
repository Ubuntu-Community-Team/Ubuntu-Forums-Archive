---
title: "Well, that was fun..."
date: 2010-09-02
forum: The Cafe
---

### Post by TNT1 on 2010-09-02
I tried dual booting with pinguy 64 bit... Grub dead, Lucid "gone" wheeee!!! What fun...

1x fresh 10.04 install later, here we are... Lucky for me I backed up first... Oh well, I was all excited about pinguy, but it's not for me...

I'll just run PAE kernel till april, and the fresh install 64bit natty...

---

### Post by DougieFresh4U on 2010-09-02
What were the issues with pinguy os?
I'm running it on a triple boot system

---

### Post by pinguy on 2010-09-02
You must of been using the old version that had a bug with grub.
To fix it.
```
sudo update-grub
```

The new version is 10.04.1.2 and can be found here: [http://pinguy-os.sourceforge.net/](http://pinguy-os.sourceforge.net/)

---

### Post by TNT1 on 2010-09-02
> **DougieFresh4U said:**
> What were the issues with pinguy os?
I'm running it on a triple boot system

It ran through the entire install, the gave an unknown error, dropped to live cd, and that was that.

I like it, it's a neat OS, guess I'll have to got find the .2 release as pinguy suggests...

---

### Post by TNT1 on 2010-09-02
> **pinguy said:**
> You must of been using the old version that had a bug with grub.
To fix it.
```
sudo update-grub
```The new version is 10.04.1.2 and can be found here: [http://pinguy-os.sourceforge.net/](http://pinguy-os.sourceforge.net/)


I assume it's 10.04.1, I only downloaded it from the site two days ago.

---

### Post by pinguy on 2010-09-02
> **TNT1 said:**
> I assume it's 10.04.1, I only downloaded it from the site two days ago.

Ahh, OK. If you got it two days ago then it is the new one. Also you can't encrypted the home partition before you install it or it will fail to install. This is something I am looking into and should be fixed when 10.10 comes out. You can encrypt the home partition once it's installed just not before.

---

### Post by TNT1 on 2010-09-02
> **pinguy said:**
>  Also you can't encrypted the home partition before you install it or it will fail to install. This is something I am looking into and should be fixed when 10.10 comes out. You can encrypt the home partition once it's installed just not before.

Ah, right, that would probably explain it, that and then me tinkering with things to get it to install, completely buggered it.

Oh well, could have been worse, coulda been a windows install that got fried on my work machine, woulda had to call the company it people, and only get a machine back next week sometime, downgraded to xp or some garbage.

Will try the pinguy again... 

(also now I have aptoncd and remastersys'd my setup one time, I'm now ready for anything):P)

---

### Post by TNT1 on 2010-09-02
> **pinguy said:**
> You must of been using the old version that had a bug with grub.
To fix it.
```
sudo update-grub
```The new version is 10.04.1.2 and can be found here: [http://pinguy-os.sourceforge.net/](http://pinguy-os.sourceforge.net/)

Look there: [http://ubuntuforums.org/showthread.php?t=1564935&page=4](http://ubuntuforums.org/showthread.php?t=1564935&page=4)
It's 10.04.1.1

So I'll go find the .2 .iso then. Thanks.:D

---

