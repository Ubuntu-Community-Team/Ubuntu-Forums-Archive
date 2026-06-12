---
title: "VGA display resolution"
date: 2010-06-01
forum: Server Platforms
---

### Post by TNHarleyRider on 2010-06-01
Would someone please point me in the direction of how to change the display resolution on Ubuntu server version 9? I am talking about the actual VGA port on the back of the server. I am NOT talking about anything related to XWindows or a SSH session. This is a text based display.
 
When I installed Ubuntu Server 9 on my server I picked a larger display resolution than I really want.
 
Thanks,
TN Harley Rider

---

### Post by arrrghhh on 2010-06-01
A google search of "screen resolution, ubuntu server" turns up [this](http://ubuntuforums.org/showthread.php?t=352663)

However, if you're using Grub2 the method may be different...

Another quick search yields: ```
add this to /etc/default/grub:

GRUB_GFXMODE=1024x768

then run sudo update-grub2

```

Not sure if it works, just found it in a forum.

---

### Post by VcDeveloper on 2010-10-29
> **arrrghhh said:**
> A google search of "screen resolution, ubuntu server" turns up [this]("http://ubuntuforums.org/showthread.php?t=352663")

However, if you're using Grub2 the method may be different...

Another quick search yields: ```
add this to /etc/default/grub:

GRUB_GFXMODE=1024x768

then run sudo update-grub2

```Not sure if it works, just found it in a forum.

Running 10.10 Server (NOT Desktop) in a VBox 3.2.10 and tried the link but don't have a menu.lst, the variable only worked at the boot prompt, also tried [this]("http://ubuntuforums.org/showpost.php?p=4731819&postcount=10") link from the VBox forum (he told me this was an old post) but ends up the same as there is no menu.lst.

.....has anyone successful changed the resolution?

......also is there a way to install a minimum xorg server just so I can control the resolution?

---

### Post by VcDeveloper on 2010-10-29
Actually I 99% [successfully solved it here]("http://ubuntuforums.org/showthread.php?p=10042410#post10042410")

---

### Post by Spice Weasel on 2010-10-29
To add the args go to the line that looks something like this (in /boot/grub/grub.conf or /boot/grub/menu.lst). You will need to be root:

```
    kernel /boot/vmlinuz-2.6.35.6-46.fc14.i686 ro rhgb quiet
```Add a space and the vga=XXX line on the end.

---

### Post by arrrghhh on 2010-10-29
What was wrong with
```
add this to /etc/default/grub:

GRUB_GFXMODE=1024x768

then run sudo update-grub2
``` for grub2?

---

### Post by Spice Weasel on 2010-10-29
Apparently that only changes the resolution on the GRUB prompt, but anyway, I've been doing it the kernel args way for years and never had any problems.

---

### Post by arrrghhh on 2010-10-29
> **Spice Weasel said:**
> Apparently that only changes the resolution on the GRUB prompt, but anyway, I've been doing it the kernel args way for years and never had any problems.

Interesting... Well from the looks of it VcDeveloper is working towards an almost-complete solution.

---

### Post by VcDeveloper on 2010-10-29
> **Spice Weasel said:**
> To add the args go to the line that looks something like this (in /boot/grub/grub.conf or /boot/grub/menu.lst). You will need to be root:

```
    kernel /boot/vmlinuz-2.6.35.6-46.fc14.i686 ro rhgb quiet
```Add a space and the vga=XXX line on the end.

Yea, I found that last night, but I only had the grub.cfg file.  I running 10.10 and I'm guesting they made changes to this version they way grub do things, because in this file it says not to edit because there are templates in /etc/grub.d and setting from /etc/default/grub that generates this menu.

I changed it any way for now until I can find how this is done, just in case in the future I may need to make changes that will rewrite it.

---

