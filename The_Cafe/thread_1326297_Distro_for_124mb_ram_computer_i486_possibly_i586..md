---
title: "Distro for 124mb ram computer i486 possibly i586."
date: 2009-11-14
forum: The Cafe
---

### Post by dragos240 on 2009-11-14
I got an old laptop. The battery is 100% DEAD, and the adapter is really flaky. One millimeter out of place and it shuts off. However. I managed to install damn small linux on it. I just don't like DSL, I don't mind the graphics. It is just missing so much. I want something with the 2.6 kernel, that has a stable dhcp client. Something like arch. What would be good?

---

### Post by pwnst*r on 2009-11-14
sounds like a fire waiting to happen.

---

### Post by Grifulkin on 2009-11-14
Tinycore

---

### Post by Sealbhach on 2009-11-14
> **dragos240 said:**
>  It is just missing so much. I want something with the 2.6 kernel, that has a stable dhcp client. Something like arch. What would be good?

How much disk space have you got?

.

---

### Post by dragos240 on 2009-11-14
> **sealbhach said:**
> how much disk space have you got?

.

12gb

---

### Post by Grifulkin on 2009-11-14
Tinycore.

[This]("http://tinycorelinux.com/")

---

### Post by Warpnow on 2009-11-14
Just do an ubuntu minimal install and install a lightweight WM or XFCE on top. I've ran XFCE on a machine with 64mbs and it ran rather decently.

---

### Post by dragos240 on 2009-11-14
Arch seems to work on it. What's the best DE for this.

---

### Post by &#32 Greg on 2009-11-14
> **dragos240 said:**
> Arch seems to work on it. What's the best DE for this.

There's no best DE or WM, but you might want to look at ones like xmonad, dwm, and evilwm.

---

### Post by dragos240 on 2009-11-14
> **&#32 Greg said:**
> There's no best DE or WM, but you might want to look at ones like xmonad, dwm, and evilwm.


I meant what's the best DE or WM for my system. Light but functional.

---

### Post by lykwydchykyn on 2009-11-14
> **dragos240 said:**
> I meant what's the best DE or WM for my system. Light but functional.

Not that I've done benchmarks, but I've found JWM to be one of the lightest that still sports a panel and menu.  What kind of WM do you like?

---

### Post by sigurnjak on 2009-11-14
I did install on 4 gb hd and p2 266 with 96 mb of ram and did ubuntu minimal cli install and then added LXDE . It was quite usable .Sys monitor was showing 100 % cpu usage but only 55 mb of ram  used  with very little swap used . Afterward it all comes down to your app choices .

---

### Post by dragos240 on 2009-11-14
> **lykwydchykyn said:**
> Not that I've done benchmarks, but I've found JWM to be one of the lightest that still sports a panel and menu.  What kind of WM do you like?

I usually use GNOME DM.

---

### Post by xuCGC002 on 2009-11-14
Try using IceWM.

---

### Post by earthpigg on 2009-11-14
> **dragos240 said:**
> I usually use GNOME DM.

LXDE.

using LXDE, you can still use lots of your familiar gnome stuff with little hassle -- "users-admin" (of ubuntu fame) for one example. "alacarte" (of ubuntu fame) menu editor for another.

and honestly? if you are willing to play around enough, no reason you couldn't get ubuntu running on that thing with LXDE or -pick your wm/de-.



what do you intend to use the computer for?

---

### Post by Warpnow on 2009-11-14
LXDE, IceWM, or XFCE. All have fairly intuitive panels. XFCE is not as lightweight, but not heavy either. It also has much better settings support. Its a fair trade off, I think. As long as you leave compositing off it should work fine.

---

### Post by Grifulkin on 2009-11-14
FVWM2, IceWM, Fluxbox, Openbox, and many more take your pick.

---

### Post by -grubby on 2009-11-14
A 486 with 124 MB of RAM and a 12 GB hard drive? No.

---

### Post by driftertx on 2009-11-14
If you're just wanting a server that runs via command line for file storage. [www.freebsd.org](www.freebsd.org) Not a user friendly OS for people who dont understand how to use vi and manuals though :)

---

### Post by corsakh on 2009-11-15
> **dragos240 said:**
> Arch seems to work on it. What's the best DE for this.
You don't need to go nuts with something like dwm, system should be fine to run openbox, fluxbox or fvwm. Try awesome if you like tiled managers.

ps Maybe give Enlightenment a go, but I doubt it.

---

### Post by gn2 on 2009-11-15
[Antix]("http://antix.mepis.org/index.php/Main_Page") might be worth a try.

---

### Post by XubuRoxMySox on 2009-11-15
> **dragos240 said:**
> I meant what's the best DE or WM for my system. Light but functional.

Openbox with it's right-click menu is very functional and minimal. If you want a DE, LXDE is by far the lightest weight DE out there. But for me it was very buggy. But it qualifies in the lightweight and functional department.

-Robin

---

### Post by longtom on 2009-11-15
> **-grubby said:**
> A 486 with 124 MB of RAM and a 12 GB hard drive? No.

This.  When I was the extremely proud owner of a 486 DX 66 it had a huge hdd of 212MB and I boosted it to 32 Meg Ram (if memory serves me right..)

What kind of 486 is this?

---

### Post by markp1989 on 2009-11-15
> **dragos240 said:**
> Arch seems to work on it. What's the best DE for this.

I would recommend openbox + fbpanel or tint

if you go with openbox, use obmenugen to generate the menus as the default openbox one misses a few programs.

---

### Post by dragos240 on 2009-11-15
> **longtom said:**
> This.  When I was the extremely proud owner of a 486 DX 66 it had a huge hdd of 212MB and I boosted it to 32 Meg Ram (if memory serves me right..)

What kind of 486 is this?

Nvm. It's a i586. That's why I put 486 OR 586.

---

### Post by kk0sse54 on 2009-11-15
TinyCore, Slitaz, NetBSD, FreeBSD, (~)Slackware, Crux, hell even a Debian netinstall would probably work. You have plenty of options and there's a lot more than what I just randomly listed here. Personally I'd find a distro that I'm comfortable with use JFS as a filesystem and throw on DWM with some light weight apps.

> I got an old laptop. The battery is 100% DEAD, and the adapter is really flaky. One millimeter out of place and it shuts off.

In all honesty though, perhaps you should consider retiring this one

---

### Post by dragos240 on 2009-11-15
> **C!oud said:**
> TinyCore, Slitaz, NetBSD, FreeBSD, (~)Slackware, Crux, hell even a Debian netinstall would probably work. You have plenty of options and there's a lot more than what I just randomly listed here. Personally I'd find a distro that I'm comfortable with use JFS as a filesystem and throw on DWM with some light weight apps.



In all honesty though, perhaps you should consider retiring this one

Well..... We found the problem. Something came loose on the inside. We can fix it...... if we can open it up. Thinkpad disassembly is a pain!

---

### Post by longtom on 2009-11-16
> **gn2 said:**
> [Antix]("http://antix.mepis.org/index.php/Main_Page") might be worth a try.

I tried AntiX before.  Also I believe it is a nice OS I do not consider it as lightweight as some other, similar distros (TinyCore, Slitaz, Puppy...).

---

### Post by Icehuck on 2009-11-16
You said Arch works on this machine therefore it's at least i686.

---

### Post by megamania on 2009-11-16
Not trying to hijack the thread - I was looking for something similar, but for a PowerPc eMac with 128MB ram.

Anybody knows of a lightweight distro that runs off a live cd (I need to attempt a data recovery with photorec)?

---

### Post by longtom on 2009-11-16
> **megamania said:**
> Not trying to hijack the thread - I was looking for something similar, but for a PowerPc eMac with 128MB ram.

Anybody knows of a lightweight distro that runs off a live cd (I need to attempt a data recovery with photorec)?

Pretty much all of them run of a CD.  SliTaz and Puppy are the 2 I have used before and both did the trick....

---

### Post by megamania on 2009-11-16
> **longtom said:**
> Pretty much all of them run of a CD.  SliTaz and Puppy are the 2 I have used before and both did the trick....
Thanks, but I can't see a PowerPc version for those two distros... Am I missing something?

---

### Post by longtom on 2009-11-16
> **megamania said:**
> Thanks, but I can't see a PowerPc version for those two distros... Am I missing something?

Ah - sorry - missed that PowerPC bit.  However - maybe one or two of [those](http://penguinppc.org/about/distributions.php) might do the trick.

---

### Post by dragos240 on 2009-11-16
> **Icehuck said:**
> You said Arch works on this machine therefore it's at least i686.

Is the first intel centrino processor an i686?

---

### Post by -grubby on 2009-11-16
> **dragos240 said:**
> Is the first intel centrino processor an i686?

Centrino started in 2003. The first i686 processor was released in 1995. So yes, it is.

---

### Post by t0p on 2009-11-16
OP: I know you were asking about desktop environment and window managers and the like: but I'd like to suggest that you run the machine with *no* GUI.  You can do pretty much anything from the command-line, even watch videos!  There are several threads in the forums on how to do stuff from the command-line, Google is, as always, your friend.  Your little laptop would be blisteringly fast without a GUI.  And it would be a good experience.

---

