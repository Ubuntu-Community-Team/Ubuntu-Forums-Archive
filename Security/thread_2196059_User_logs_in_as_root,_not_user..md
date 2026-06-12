---
title: "User logs in as root, not user."
date: 2013-12-27
forum: Security
---

### Post by Tristan_Williams on 2013-12-27
I have build a system using the minimal installation method.

I have an admin user "tristan401" and a normal user with sudo priviledges "Tristan"
tristan401 is the root user, so when I log in, it shows this:
```
root ~ #
```
This is exactly what I want.

My problem is with the normal user "Tristan"

I want tristan to be an actual normal user with sudo priviledges, but for some reason, Tristan gets logged in as root, but not as root.
The system starts in command line mode.
I log in as normal user "Tristan" and type:
```

startxfce4

```

and get a bunch of output that basically says "Permission denied"

So I type:
```

sudo !!

```

and everything works fine. 

But I go and open thunar, and at the top it says "Warning, you are using the root account. You may harm your system."

What the genuine poop?!?!?!

This user IS NOT in the "root" group. Only in the "sudo" group.

Please help. I have already screwed one system because I continued to use it as the Tristan/root mixed user... I dont want to go through that again.

Thanks in advance

---

### Post by Tristan_Williams on 2013-12-27
I fixed the issue. 
All I did was delete and re-create the user... Other than that I have no idea what caused it or fixed it...

---

### Post by deadflowr on 2013-12-28
Anytime you run a sudo you become root for that one command.
However, that one command in this case happens to be an X session.
Same thing applies if you try running gksudo nautilus(if in normal ubuntu,as an example)
If you run that, you'll have root during the time the nautilus file manager is open, including any actions you take from the file manager during the session. ( open a text editor and edit a file, you'll have root level usage)

Why startxfce4 doesn't work is something, I myself, don't know a thing about.
startx, alone has always worked well enough for me.

---

