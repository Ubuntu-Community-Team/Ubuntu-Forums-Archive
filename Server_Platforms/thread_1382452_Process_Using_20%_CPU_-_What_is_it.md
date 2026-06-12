---
title: "Process Using 20% CPU - What is it?"
date: 2010-01-16
forum: Server Platforms
---

### Post by war59312 on 2010-01-16
Hi,

Installed Ubuntu Server today and I noticed this process is using 20% CPU. See both attachments please.

What is this process and what should I do about it?

I'm new to Ubuntu Server, testing it out on my home grown server.

Thanks,

Will

---

### Post by sliketymo on 2010-01-16
Looks like windows to me.Are you running Ubuntu server in a virtual machine ?

---

### Post by war59312 on 2010-01-16
Negative. I was simply using Webmin from my desktop PC to view my server.

Server is located down stairs in my brother's room, he was sleeping at the time and still is. I'm root, he has no clue about linux.

And now it's using 55% CPU. And been running for over 8 hours now.

Looks like something to do with X and a database.

---

### Post by ephmanjmm on 2010-01-16
I would hazard a guess that you installed a GUI that is using X and gdm.

---

### Post by war59312 on 2010-01-16
> **ephmanjmm said:**
> I would hazard a guess that you installed a GUI that is using X and gdm.Correct, brother wants to learn linux but command line is too hard for him to start at.

So I simply ran:

```
sudo aptitude  install  ubuntu-desktop
```Just installing the main desktop package should not cause this odd CPU usage behavior.

---

### Post by Monotoko on 2010-01-16
Press Ctrl+Alt+F1

then try killing x

```
sudo killx
```

---

### Post by war59312 on 2010-01-16
The problem, is that it happens on every boot up.

---

### Post by falconindy on 2010-01-16
It's the screensaver. Kill 'fuzzyflakes' and it'll behave for the remainder of the idle timeout. If you're using it as a server (with webmin no less), why is there even a GUI on it?

---

### Post by HighCommander540 on 2010-01-17
> **falconindy said:**
> It's the screensaver. Kill 'fuzzyflakes' and it'll behave for the remainder of the idle timeout. If you're using it as a server (with webmin no less), why is there even a GUI on it?

Like he mentioned the GUI is for his brother.

Seriously though, if you have read anything on the forums...You should have expected that you would get a high CPU usage if you installed a GUI. Its just stupid to do.

---

### Post by war59312 on 2010-01-17
> **falconindy said:**
> It's the screensaver. Kill 'fuzzyflakes' and it'll behave for the remainder of the idle timeout. If you're using it as a server (with webmin no less), why is there even a GUI on it?The screen-saver appears to be only using 0.6% when active.

But yeah at this stage it is just for experimenting.

> **HighCommander540 said:**
> Seriously though, if you have read anything on the forums...You should have expected that you would get a high CPU usage if you installed a GUI. Its just stupid to do.OK it's no big deal. Just was wondering. Does not make much sense to me that it uses so much CPU just idle.

---

### Post by HighCommander540 on 2010-01-17
> **war59312 said:**
> The screen-saver appears to be only using 0.6% when active.

But yeah at this stage it is just for experimenting.

OK it's no big deal. Just was wondering. Does not make much sense to me that it uses so much CPU just idle.

It has to be displaying something always. And there is always something going on whether it looks like it or not. If you want a server and you don't want it to be slow don't use a GUI. ;)

---

### Post by falconindy on 2010-01-17
> **war59312 said:**
> The screen-saver appears to be only using 0.6% when active.

But yeah at this stage it is just for experimenting.

OK it's no big deal. Just was wondering. Does not make much sense to me that it uses so much CPU just idle.
gnome-screensaver is **cause**, and xorg spiking is the **effect**. If you kill the screensaver, your CPU will settle back to idle.

---

### Post by Sporkman on 2010-01-18
Never understood the point of screensavers that do computational work. I've always been a blank-screen kind of guy. :)

---

### Post by war59312 on 2010-01-20
> **Sporkman said:**
> Never understood the point of screensavers that do computational work. I've always been a blank-screen kind of guy. :)Same here, now set to blank black screen. :D

Though for desktop I use SETI@home via Boinc screen-saver.

> **falconindy said:**
> gnome-screensaver is **cause**, and xorg spiking is the **effect**. If you kill the screensaver, your CPU will settle back to idle.I hope your right, thanks again.

---

### Post by Skidbladniir on 2010-01-21
GUI's are really complex.  Especially if you have the high graphics settings enabled.  You might try uninstalling Gnome, and installing a lightweight desktop.  A quick Google search will yield many results.

---

