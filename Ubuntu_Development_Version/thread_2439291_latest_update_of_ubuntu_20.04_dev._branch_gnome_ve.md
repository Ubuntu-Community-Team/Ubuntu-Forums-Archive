---
title: "latest update of ubuntu 20.04 dev. branch gnome version"
date: 2020-03-25
forum: Ubuntu Development Version
---

### Post by mastergilga on 2020-03-25
[COLOR=#242729][FONT=Arial]

Hi!

I am testing ubuntu 20.04 dev branch and everything have worked quite well until today. I have updated my system, rebooted and came to the login screen, very normal to this point. But when I have logged in, there was a blanc screen. Something is now wrong with the nvidia driver, which worked well until today. I know, that this is a experimental version. This post is more a bug-report, than a question. But if anybody has a workaround, please let me know.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My system: ryzen 7 3700x on b450 as rock steel legend msi rtx 2070 gaming z with the recomended 440 driver, gui gnome[/FONT][/COLOR]

---

### Post by Doug S on 2020-03-25
Hi and welcome to Ubuntu forums.

did your update today include a new kernel? Perhaps 5.4.0-18-generic? And have you tried going back to the previous kernel?
It should still be available, but you have to get into grub to select it. For development work, I suggest a long and visible grub time. Myself I rarely want to load the default kernel.

Readers: see also the same question (now closed) on [ask]("https://askubuntu.com/questions/1220226/latest-update-of-ubuntu-20-04-dev-branch").

---

### Post by mastergilga on 2020-03-25
if I am going in the grub menu and load a previous kernel, it loads the save mode. there I can load the open source driver, and then i can log in only with wayland, but this doesn´t work well too, the performance is bad.

ps: the ask-post was mine

---

### Post by Doug S on 2020-03-25
> **mastergilga said:**
> if I am going in the grub menu and load a previous kernel, it loads the save mode. there I can load the open source driver, and then i can log in only with wayland, but this doesn´t work well too, the performance is bad.
To clarify: The old kernel works o.k. the new one doesn't. Is that correct? If yes, then my suggestion is to just wait and try the next kernel. If issues continue then look deeper into it.
(note: I am a server person and not very helpful with desktop stuff.)

---

### Post by mastergilga on 2020-03-26
- the kernel 5.4.0-18 don´t work with the nvidia driver  (both 435 and 440); I am loging in a blanc screen
- same with the 5.4. 0-20
- if I am using the 5.4 0-9 I am logging in, but in graphical savemode, no network; so I change to the open source driver; reboot and then loggig in, but only with the         wayland thing, which is very slow and not optimized, but I can now update my system and it´s in 4k again
- I think the error is caused by the upgrade, which i have done yesterday in the afternoon (I had made the last days every day a upgrade), and it has something to do with gnome and its extensions, but I can´t remember exactly the packages 
-I hope  developers read this post, to solve the problem, april is comming

---

### Post by dino99 on 2020-03-26
Be sure to not only remove but purge the nvidia installed packages and their dependencies if any, to get rid of possible old settings disturbing the video process; then reinstall the appropriate nidia driver for your graphic hardware (see nvidia selected driver on their site).

'journalctl -b' might help you to identify the reason behind that issue.

---

### Post by P-I H on 2020-03-26
I installed Focal Fossa ISO20200325 today on a system with an old Nvidia gpu, GeForce GTX 660. The Nvidia 440.64 driver is used.
The installation worked OK. 
In case you want to check the updates you will find them in /var/log/apt/history.log.

---

### Post by mastergilga on 2020-03-26
finally, its works again,
I have  reseted the hole system und updated, but it seemed, that the problem still there...the nvidia driver still didn´t worked, but recently there was a ubuntu core update and I think it was this package that was responsible for not working with the nvidia driver

---

### Post by mastergilga on 2020-03-26
unfortunately I was too fast with my post, I rebooted and the problem is still there, no signal to my TV, which is my monitor, when i have logged in...I think this will last a while, I will try in a few days again...

---

