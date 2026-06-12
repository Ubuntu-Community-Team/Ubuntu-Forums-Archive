---
title: "What are some GRUB alternatives?"
date: 2008-06-10
forum: The Cafe
---

### Post by diablo75 on 2008-06-10
I'm looking for something that's fancy.  I don't want to be bothered with a menu showing 4 different kernels plus their recovery modes, and then XP.  I'd love something more like a GUI with a large icon for each OS, and of course a hotkey to load a different kernel or recovery mode if I have to (which I almost never have to do).

I'd like to make a modification to a system I just put together for an elderly lady.  She just uses the Internet for browsing, and I wanted to save her some money by making her system dual boot with Ubuntu, and that way she'll not have to worry about getting viruses anymore.  But the grub menu stumps her; it's purpose is not very obvious to her, and all the options are intimidating.

What can I try?

---

### Post by Dr Small on 2008-06-10
You do realize that the bootloader loads before the OS. So what you ask is impossible. I only know of LILO, but have never tried it apart from GRUB. Grub is very customizable in my opinion, and you can move things around, change the background on it, etc.

---

### Post by d.kusummmanth@gmail.com on 2008-06-10
> If you really don't like GRUB, a popular alternative is the classic linux loader, LILO.
[http://packages.ubuntu.com/dapper/base/lilo](http://packages.ubuntu.com/dapper/base/lilo)
I'm not sure how exactly to set it up for ubuntu, though.

[[SIZE="4"]Source[/SIZE]]("http://ubuntuforums.org/showthread.php?t=519516")

---

### Post by gn2 on 2008-06-10
One such option is [**[COLOR="DarkOrange"]GAG[/COLOR]**]("http://users.bigpond.net.au/hermanzone/p12.htm").

---

### Post by Rhubarb on 2008-06-10
You could try out grub2, it's the next version of grub that's apparently quite stable.  But I really don't know if it's capable of booting in to windows, and I don't know what it looks like (it supports full graphics mode).

Grub 2 is currently under development, so it's unfinished and may have some nasty bugs.
So you have been warned.

To install grub2:
```
sudo aptitude install grub2
```

I suggest you do a search on the internet for more information about grub2, as it may assist you in configuring it up / making it look pretty.

---

### Post by Dr Small on 2008-06-10
Hey, thanks for that. I will have to try it sometime. It looks interesting! :D

---

