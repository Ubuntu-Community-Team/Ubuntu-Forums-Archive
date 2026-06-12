---
title: "Gnome Shell randomly close session by force"
date: 2017-03-10
forum: Ubuntu Development Version
---

### Post by fthx on 2017-03-10
Hi,

I start from another solved thread.

[QUOTE="Harry332"]The forced logout issue is not the same bug.
It is about session dying because gdm couldn't start correctly.
That is why you do not see the wayland session option when logging in.
Another remarkable difference is that if you still log in (gnome  session) you cannot shut down the session anymore nor log in as another  user.
There is no window with the shut down - restart - log in options.
And soon the session ends (forced) with another log in loop.[/QUOTE]

Gnome Shell disconnects user randomly. When icons are enabled on desktop, sometimes they are missing at startup and crash will happen soon. Some minutes ago, I did have the Wayland option at gdm step, but crash happened too. And, if I remember correctly, crash happens with lightdm too.

Logs talk about gnome-session :
```
Unrecoverable failure in required component org.gnome.SettingsDaemon.Sharing.desktop
```

Hardware : Intel Skylake CPU, switchable graphics Intel mode (Nvidia dGPU)
Drivers : happens with nouveau or nvidia proprietary.

---

### Post by harry332 on 2017-03-10
Bruce Pieterse has already made a bug report about this issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1670089](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1670089)

---

### Post by harry332 on 2017-03-15
I haven't experienced this bug any more lately.
So, do you see still see this fthx?

---

### Post by fthx on 2017-03-15
Oooooooh YES !
Very frequently, some buggy startups in a row, good startups in a row, randomly.

I updated latest gjs and gsd packages this afternoon, I'll see if it changes something.
I saw few somewhat maybe related bugs in freedesktop bugs (when I searched for "systemd"), but I'm not able to connect all these stuffs.

---

### Post by jbicha on 2017-03-15
I heard one person say that it felt to him like the updated gjs has less of a memory leak. If gnome-shell runs out of memory, then it won't work too well!

Anyway, if you're still experiencing this problem, please report it to GNOME.

---

### Post by fthx on 2017-03-16
[https://bugzilla.gnome.org/show_bug.cgi?id=780145](https://bugzilla.gnome.org/show_bug.cgi?id=780145)

---

### Post by fthx on 2017-03-16
finally dup of :
[https://bugzilla.gnome.org/show_bug.cgi?id=774813](https://bugzilla.gnome.org/show_bug.cgi?id=774813)
(SOLVED patch included)

---

### Post by jbicha on 2017-03-16
Oh ok, I uploaded a patched [gnome-settings-daemon]("https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.23.92-0ubuntu2") to zesty now. So when it's available, see if that helps.

I had a different problem with gnome-initial-setup that the patch was supposed to solve but it didn't. :(

---

### Post by fthx on 2017-03-16
There's a patched Ubuntu version of gnome-settings-daemon (*ubuntu2).
I upgraded it, time (and me !) will tell.

---

### Post by dino99 on 2017-03-16
even without that patched version, this problem seems have gone since 2 days now (with a few new opened sessions)

---

### Post by fthx on 2017-03-18
since the patch, I did not get any bad session.

---

