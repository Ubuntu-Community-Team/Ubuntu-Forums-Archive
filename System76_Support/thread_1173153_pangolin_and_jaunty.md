---
title: "pangolin and jaunty?"
date: 2009-05-29
forum: System76 Support
---

### Post by formol on 2009-05-29
hi,

I've two major problems with my pangolin running on Jaunty.

- I got "grub error 2" every 10 or 15 boot. 

- When Ubuntu is running, I'm unable to watch movie on a shared folder on another Ubuntu machine on my network. Or when I try to watch video online, it stop or freeze.I suspect a kind of driver instability for the wifi.

---

### Post by thomasaaron on 2009-05-29
> - I got "grub error 2" every 10 or 15 boot.

That means the system is having difficulty to find one of the necessary grub files for booting the computer. Could be caused by a rickety image or upgrade. Or it could be caused by hard drive problems. More than likely, it is a rickety image or upgrade.
> 
- When Ubuntu is running, I'm unable to watch movie on a shared folder on another Ubuntu machine on my network. Or when I try to watch video online, it stop or freeze.I suspect a kind of driver instability for the wifi.

Try using VLC to watch the movie. It has a more sophisticated buffering system than Totem movie player. The stream could be bottle-necking somewhere. Lot's of possibilities.

---

### Post by formol on 2009-05-29
grub error 2 : 
> Could be caused by a rickety image or upgrade. Or it could be caused by hard drive problems. More than likely, it is a rickety image or upgrade
it happen all the time with jaunty, what can I do to prevent it?

for the video problem on my home network, there is a problem with all player on my pangolin, not only with vlc.  when it happen, all my network connection on the laptop is down for like 5 minutes, then access to internet and network re-appear.
I also had unusual instability with normal internet access on my pangolin, sometime, it all stop, i don't know why.  that's why I suspected a wifi driver instability.  should I try the backport?

---

### Post by thomasaaron on 2009-05-29
You could try re-installing grub on your machine...
[http://knowledge76.com/index.php/Restore_Grub](http://knowledge76.com/index.php/Restore_Grub)



Also, go ahead and install backports...
sudo apt-get install linux-backports-modules-jaunty

---

### Post by betrunkenaffe on 2009-06-02
On this grub thing, what is grub error 3? I get that every time but she boots fine other than that. Happens on both my Jaunty machines so I thought was just Jaunty..

---

### Post by thomasaaron on 2009-06-02
You shouldn't be getting it. Here's a list of grub error messages. Looks like it may not be finding something it is looking for on the disk.

[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

Did you try re-installing grub per the above instructions?

---

### Post by betrunkenaffe on 2009-06-02
> **thomasaaron said:**
> You shouldn't be getting it. Here's a list of grub error messages. Looks like it may not be finding something it is looking for on the disk.

[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

Did you try re-installing grub per the above instructions?

Not yet, thanks for the link. I'll be looking into it when I have more time. Perhaps in a week when I go on holiday :)

---

