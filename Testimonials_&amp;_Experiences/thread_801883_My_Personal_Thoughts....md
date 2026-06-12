---
title: "My Personal Thoughts..."
date: 2008-05-21
forum: Testimonials &amp; Experiences
---

### Post by e.honda on 2008-05-21
I dual booted Ubuntu 7.10 awhile back with my 2.0cpu Pentium 4 XP desktop running at 1gig of ram with plenty of storage space. It's an old rig and I didn't expect it to be fast because it was a dual boot.

But now I nstalled Xubuntu 8.04 couple days ago on my gateway laptop running at 512mb of ram and plenty of storage space. I've been told that it was light-weight and fast. So far it's slow. I'm a power user when it comes to surfing the web and it's not just that. I also navigate through the system files i.e system folders, text editor(gedit), programs, and such. Also there seems to be some sort of lag time when it comes to copying and pasting text between firefox and gedit. Firefox uses 40-50mb with a few tabs open according to the system-monitor. Is this normal?...possible memory leak?

I'm very surprised that windows firefox including windows explorer is faster than Xubuntu and Ubuntu. In windows, it's nothing but click click click and I'm there. I'm sure you agree with me on that. In ubuntu/xubuntu click wait, click wait, click wait... I feel no disappointment between v7.10 and 8.04 except the fact that it's slow but I can still work with it. I've disabled a lot of services that I don't need hoping that it would improve system performance, but I was wrong-it only improved the boot process afaik. I did a run down on each and every one of the services with sysv-rc-conf, bum, and the default service manager. 

Boot up process is FAST but surfing the web with firefox 3 beta 5 is slowing me down on Xubuntu. Not only that it also includes opening system files, text editor, and what have you. I don't plan on downgrading firefox to v2.0... because I'm afraid that I won't get the proper automatic update patches. I''ve tweaked firefox 3(beta 5) with all the settings and config that I can think of, so far it's the same. I've tried different alternative browsers, some seem to be fast but does not have the security features and addons that firefox provides :\

So far fedora core, redhat, xubuntu, and ubuntu are the only distros I've worked with. I have heard good ratings from slackware and the BSD family, maybe I'll give that a try in the near future. I switched to linux mainly because of security and performance. So far security is tight in linux, but performance is lacking. Microsoft windows security is weak but has blazing performance. Why can't I have both? pfff...Anyway I'm still going to work with xubuntu/ubuntu and see how it goes in the long run. Reason why is because it has about all the application softwares that I use in windows(cygwin) which is a very good thing and I'm going to continue on working side by side with ubuntu. But in the near future I would like to expect better performance, if possible. Believe me or not and you can flame me for this but I think Ubuntu is going to be the next microsoft in terms of popularity.

---

### Post by jrusso2 on 2008-05-21
Ubuntu is far from being the best performing Linux.  Debian, Slackware, Arch and Gentoo all offer better performance.

---

### Post by lisati on 2008-05-21
> **jrusso2 said:**
> Ubuntu is far from being the best performing Linux.  Debian, Slackware, Arch and Gentoo all offer better performance.

I might be mistaken but I thought that Ubuntu was a derivative of Debian....

---

### Post by ukripper on 2008-05-21
That is why there is choice in Linux world unlike w*****s, if ubuntu is not best suited for you, try other thousands of linux distros which can suit your needs.

---

### Post by 3rdalbum on 2008-05-21
You're comparing an operating system from 2002 with one from 2008. Just as Windows 98 runs faster than XP, and XP runs faster than Vista, XP generally runs faster than Ubuntu. That's assuming that you're not using performance-sapping anti-virus on XP.

The other thing I'll ask is: Do you have the correct drivers for your graphics card? If you run with basic "vesa" (unaccelerated) graphics, everything will feel ultra-slow. If scrolling or moving a window feels slow and draggy, then you should check that you have accelerated graphics. For the record, lack of graphics card drivers causes exactly the same problem on Windows :-)

---

### Post by e.honda on 2008-05-21
> **3rdalbum said:**
> You're comparing an operating system from 2002 with one from 2008. Just as Windows 98 runs faster than XP, and XP runs faster than Vista, XP generally runs faster than Ubuntu. That's assuming that you're not using performance-sapping anti-virus on XP.

The other thing I'll ask is: Do you have the correct drivers for your graphics card? If you run with basic "vesa" (unaccelerated) graphics, everything will feel ultra-slow. If scrolling or moving a window feels slow and draggy, then you should check that you have accelerated graphics. For the record, lack of graphics card drivers causes exactly the same problem on Windows :-)
Output of lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```
In Xubuntu I don't think it's a graphics card issue. Moving windows and scrolling is no problem. Opening and working with files, folders, and surfing the net is slow, that's what I was trying to say. According to system-monitor(resources), the system is using up half of my memory, that's why I think it's slow. Don't know if that's normal or not. Firefox 3b5 is using 40-50mb with a few tabs open, don't know if that's normal either. 

I had to depart gedit which I like very much...with leafpad. Leafpad doesn't have some features that gedit has, but I can still work with it + it's lightweight. AbiWord is an excellent program that I can work with, but a bit slow(searching for an alternative).

Totem player is good when watching movies, but uses a lot of my cpu(searching for an alternative). Thunderbird, I can't complain-it's perfect. Truecrypt, EncFS, gnupg, and such encryption programs is A++

And As for the internet, I know it's not my ISP. I'm running on wireless with a 60-65% connection with wicd. Even with the default network-manager the connection is about the same. In windows, I get 100% connection. But anyway, I can still work with it as long as it's not like dial-up.

---

### Post by Buddy's Pal on 2008-05-21
As others have suggested, something may not be right in your setup. Most Ubuntu users I've spoken with find it faster than Windows XP and waaaay faster than Vista. That has been my experience too.

Best of luck sorting out whatever is slowing down performance of your system.

---

### Post by Sef on 2008-05-22
> I might be mistaken but I thought that Ubuntu was a derivative of Debian....

Ubuntu is derived from Debian.

---

