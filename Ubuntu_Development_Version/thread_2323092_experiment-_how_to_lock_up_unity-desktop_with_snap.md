---
title: "experiment- how to lock up unity-desktop with snap"
date: 2016-05-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-05-02
Using the unity-desktop on yakkety current cycle do the following:

Open terminal: Ctrl+Alt+t

Drop to root:
THEN

```

snap install notes

```

After this is complete go to unity dash (not panel) and you will find Notes app.

Click it.

If the app runs successfully you should be able to go to top left corner and hover and should see a maximize button. Click the maximize button. You should not be able to use unity-desktop nor should you be able to use any tools on the top panel.

Regards..

---

### Post by mc4man on 2016-05-02
Not really "locked', just notes has no conception of unity panel or launcher occupying the desktop when maxed 
Tap super button, you can open any other launcher app on top of maxed notes. From dash you could open another instance or 2 of notes & then go to a noted spread from launcher

---

### Post by ventrical on 2016-05-02
> **mc4man said:**
> Not really "locked', just notes has no conception of unity panel or launcher occupying the desktop when maxed 
Tap super button, you can open any other launcher app on top of maxed notes. From dash you could open another instance or 2 of notes & then go to a noted spread from launcher

Well.. that worked ok. hehe :) 

regards..

---

### Post by ventrical on 2016-05-02
I installed the teatime-unity app but can't find it in the dash.

---

### Post by moteprime on 2016-05-15
@ventrical I'm also struggling to install teatime-unity. I have installed it, but it's showing either.
It's not to be found using Synaptic searching in the repos?

---

### Post by ventrical on 2016-05-15
Still looking into this. It is still early in yakkety and these things will happen.

Regards..

---

### Post by moteprime on 2016-05-15
@ventrical Oh. I'm on 16.04, having the same problem.
teatimer are in software center, i installed it but it's not showing up in the dash and Synaptic can't seem to find it in the repositories.

---

### Post by mc4man on 2016-05-15
It's a poorly done snap that seems to be a combo of snap & desktop app. So the python script that runs it looks to wrong location & even if started the timer function doesn't work, see screen, clicking on Start Timer does nothing.
From a user perspective nothing to be done as /snap is a read-only filesystem

---

### Post by moteprime on 2016-05-15
How come this is even in the software center?
Should i report a bug on it?

So to install it i should get the PPA from launchpad?

---

### Post by grahammechanical on 2016-05-15
Confirm.

/snap/teatime-unity/current/command-teatime.wrapper has

```
exec "$SNAP/usr/share/teatime/teatime.py" "$@"
```

But teatime.py is at /snap/teatime-unity/current/usr/share/teatime/teatime.py

Even when I get into the directory I am getting "command not found." It does have permission to execute. By now my eggs must be hard boiled.

Regards.

---

### Post by mc4man on 2016-05-15
> **mc4man said:**
> It's a poorly done snap that seems to be a combo of snap & desktop app. So the python script that runs it looks to wrong location & even if started the timer function doesn't work, see screen, clicking on Start Timer does nothing.
From a user perspective nothing to be done as /snap is a read-only filesystem

Oops - figured out how to use (pretty stupid of me). You have to set a time first, then start timer, don't know what I was thinking, maybe like a stopwatch which it isn't.

---

### Post by mc4man on 2016-05-15
If you wanted to see it (the snap version, note it's in the teatime ppa also)  you'd do this - 
```
sudo mkdir -p /usr/share/teatime
```
```
sudo cp /snap/teatime-unity/2/usr/share/teatime/window.ui /usr/share/teatime/
```

To start, either from cli - 
```
/snap/teatime-unity/2/usr/share/teatime/teatime.py
```

or for launcher icon
```
cp /snap/teatime-unity/2/usr/share/applications/teatime.desktop ~/.local/share/applications/
```
```
gedit ~/.local/share/applications/teatime.desktop
```
Edit the Exec= line to - 

```
Exec=/snap/teatime-unity/2/usr/share/teatime/teatime.py
```
Otherwise one would need to wait until the snap dev fixes as one can't alter any snap files that are in /snap

---

### Post by moteprime on 2016-05-18
@mc4man  LoL, yes it's i little weird getting it to work the first time.

---

### Post by mc4man on 2016-05-18
> **moteprime said:**
> @mc4man  LoL, yes it's i little weird getting it to work the first time.
I'm thinking it *may* be possible to edit a file(s) in /snap if one first unmounts the snap. All snaps are auto mounted on bootup/login as loop devices so one could unmount in disks. 
Not in a position to check as I've just finished (maybe..) removing all traces of snap on my install here, a bit of a chore as it's all over the place. (fstab, systemd, apparmor, ect.

---

### Post by moteprime on 2016-05-19
@mc4man
The 'snap' thing are a hole new thing for me, this teatime are the first encounter i have with it.
But thanks. :-)

---

### Post by ventrical on 2016-05-19
> **mc4man said:**
> I'm thinking it *may* be possible to edit a file(s) in /snap if one first unmounts the snap. All snaps are auto mounted on bootup/login as loop devices so one could unmount in disks. 
Not in a position to check as I've just finished (maybe..) removing all traces of snap on my install here, a bit of a chore as it's all over the place. (fstab, systemd, apparmor, ect.

That was a big surprise!

Regards..

---

