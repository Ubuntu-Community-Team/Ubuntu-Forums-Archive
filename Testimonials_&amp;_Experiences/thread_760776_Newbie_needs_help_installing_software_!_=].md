---
title: "Newbie needs help installing software ! =]"
date: 2008-04-20
forum: Testimonials &amp; Experiences
---

### Post by KevinBoy1111 on 2008-04-20
Hey Ubuntu users.

I just switched from XP to Xubuntu 7.10

So far i love it !

But I can´t figure out some things !


1) Installing a dock   (The package manager doesnt have AWN)

2) Increasing default text size in Firefox

3) Decreasing screen resolution permanently (it swaps back once i reboot !)

4) Installing shockwave 




Thats pretty much it for now.
Thx to everyone who worked on this project !
It saved my old eMachines celeron d with 256 mb of ram!

---

### Post by finer recliner on 2008-04-20
1) [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

2) edit > preferences... > content tab > font size

4) i think shockwave is obsolete or it is bundled with flash now. 
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by Sinkingships7 on 2008-04-20
In the future, could you please direct your questions with setup to Absolute Beginner Talk?

Thank you, and I hope you enjoy your new machine! :)

---

### Post by wolfen69 on 2008-04-20
for screen resolution:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by finer recliner on 2008-04-20
> **wolfen69 said:**
> for screen resolution:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

please be aware that this command will reconfigure more things than just your resolution settings (like keyboard and monitor configurations). I would back up your current /etc/X11/xorg.conf just to be cautious. and never run commands that you do not understand.

---

