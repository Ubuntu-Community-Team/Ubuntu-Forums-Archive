---
title: "SE Linux in Intrepid?"
date: 2008-12-16
forum: Security
---

### Post by Sealbhach on 2008-12-16
Hi, 
I was just wondering about SE Linux and what I would need to do to get it working. 

I saw on a [guide]("http://ubuntu-tutorials.com/2008/03/18/how-to-install-selinux-on-ubuntu-804-hardy-heron/") that in Hardy you just

```
sudo apt-get install selinux
```

and it removes AppArmor and applies SE Linux policy.

I was just wondering is it worthwhile doing this? Pros and cons? Also, is AppArmor enabled by default?



.

---

### Post by PmDematagoda on 2008-12-16
First off, you can't use both Apparmor and SELinux, it must be either one or the other. And there isn't really a "best" security system out of the two, both of them have their advantages and disadvantages.

The pros(only one pro I can see) of SELinux:-
1) It gives you the ability to exert a lot of control over programs with the policies, more so than Apparmor does.

The cons(again, only one) of SELinux:-
1) It is more difficult to use and configure than Apparmor is.

---

### Post by HermanAB on 2008-12-16
Hmm, SELinux is designed for government/military/spook use.  If are not a soldier or a spook, then don't bother with it.  SELinux can be used to maintain separation between data with differing security classifications.

So, APArmour is probably what you want.

---

### Post by Sealbhach on 2008-12-16
> **HermanAB said:**
> Hmm, SELinux is designed for government/military/spook use.  If are not a soldier or a spook, then don't bother with it.  SELinux can be used to maintain separation between data with differing security classifications.

So, APArmour is probably what you want.

Thanks, and is AppArmor already enabled or do I have to do something to make it active?


.

---

### Post by PmDematagoda on 2008-12-16
> **Sealbhach said:**
> Thanks, and is AppArmor already enabled or do I have to do something to make it active?


.

It is already enabled, but by default it does not cover a large scope, for more information on AppArmor you can refer bodhizazen's how-to which is a sticky here.

> Hmm, SELinux is designed for government/military/spook use. If are not a soldier or a spook, then don't bother with it.
That is not necessarily true, SELinux is also used by businesses and organisations who have valuable information. But this does not mean that it cannot be used on a desktop.

---

### Post by bodhi.zazen on 2008-12-16
> **Sealbhach said:**
> Thanks, and is AppArmor already enabled or do I have to do something to make it active?


.

If wish, I wrote an intro to Apparmor , and it is a sticky. I suggest you start there.

If you want to take selinux for a spin, I suggest Fedora. If you like selinux it is easy (IMO) to set up on Ubuntu.

---

### Post by kuradoberi121 on 2008-12-16
[img]http://www.top1gaming.com/cosplay/shaiya-1.jpg[/img] See the answer [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-153.html).  Want to see [[color=#800080]more pics[/color]](http://www.top1gaming.com/cosplayer.php)? Show yourself  on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/index.php?gid=27)**Recommend:**[[color=orange]LineAge 2 Elf [/color]](http://www.top1gaming.com/coscontent-105.html)[[color=orange]Rin Tohsaka [/color]](http://www.top1gaming.com/coscontent-83.html)

---

