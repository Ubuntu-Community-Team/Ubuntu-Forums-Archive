---
title: "wayland now default"
date: 2017-08-21
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-08-21
The login options will reflect & actually now work right.

---

### Post by Frogs Hair on 2017-08-21
I noticed elevated permission problems after updates and rebooted to look at the session menu.

---

### Post by amano on 2017-08-22
Mind to elaborate?

---

### Post by Frogs Hair on 2017-08-22
I could not open applications such as synaptic that required elevated permissions. When i rebooted noticed the new Ubuntu X session.

---

### Post by ventrical on 2017-08-22
New session menu is :

Ubuntu
Ubuntu on Xorg
Gnome
Gnome on Xorg

Synaptic not working here either.

---

### Post by dino99 on 2017-08-22
@#4

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1712089](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1712089)

---

### Post by Frogs Hair on 2017-08-22
> **ventrical said:**
> New session menu is :

Ubuntu
Ubuntu on Xorg
Gnome
Gnome on Xorg

Synaptic not working here either.

I see Gnome Classic, Ubuntu, and Ubuntu on Xorg. This is a two day old installation.

---

### Post by ventrical on 2017-08-22
> **Frogs Hair said:**
> I see Gnome Classic, Ubuntu, and Ubuntu on Xorg. This is a two day old installation.

On today's daily install I only have :
Ubuntu
Ubuntu on Wayland

Regards..

uh.. will try an update.

---

### Post by ventrical on 2017-08-22
> **Frogs Hair said:**
> I see Gnome Classic, Ubuntu, and Ubuntu on Xorg. This is a two day old installation.

Did you install gnome-classic manually?

---

### Post by Frogs Hair on 2017-08-22
> **ventrical said:**
> Did you install gnome-classic manually?

No , though it seems redundant if the bottom panel can be added with an extension anyway.

Edit:   don't see it in synaptic either.

---

### Post by ventrical on 2017-08-22
> **Frogs Hair said:**
> No , though it seems redundant if the bottom panel can be added with an extension anyway.

Edit:   don't see it in synaptic either.

So perhaps the Uni-Dock, classic and gnome-shell are working concurrently with each other in a 3D array ... uhh .. yes.. as I see it anyways .. without using any virtual  functions either. [s] Then gnome on wayland would be the standalone project you see., [/s]
correction:
Actually it is working on wayland this way so it may be using v-chip functions or jockeying between x11 and wayland.

regards..

---

### Post by Frogs Hair on 2017-08-22
I removed the entry . 

```
d-book@ubuntu:~$ cd /usr/share/xsessions
d-book@ubuntu:/usr/share/xsessions$ ls
gnome-classic.desktop  ubuntu-xorg.desktop
d-book@ubuntu:/usr/share/xsessions$ sudo rm gnome-classic.desktop



```

---

### Post by amano on 2017-08-22
> **Frogs Hair said:**
> I could not open applications such as synaptic that required elevated permissions. When i rebooted noticed the new Ubuntu X session.

Well, the elevation is still possible but gksu and pkexec don't work with wayland. So you need a (longer) elevation command on wayland:

type in the terminal both commands:

```

xhost +si:localuser:root
sudo synaptic

```

For maximum security you might add the following command after closing synaptic:

xhost -si:localuser:root

That closes the potential attack vector that you opened by granting a whole gui program root access to the X server (xwayland probably in this case).

So this is the interim solution for some programs (gparted, synaptic, ubiquity) until they are ported to wayland (using proper PolicyKit integration). 

If they are not ported (certainly not in time for Artful, if at all) this might be the (clunky) way for the future.

---

### Post by Chanath on 2017-08-22
Do you really think Wayland is better than X? Don't you have a hard time getting working apps for so many years working in Wayland?

---

### Post by amano on 2017-08-22
[QUOTE=Chanath]Do you really think Wayland is better than X? Don't you have a hard time getting working apps for so many years working in Wayland? [/QUOTE]

Define “better“. X is a security nightmare with a design from the 80s and people want to move away from that for years and years.

But it is well known and tested and has probably fewer bugs.

I am certain that Canonical dropped Unity for not being able to move away from X in the forseeable future. MIR was far from stable, closed hardware driver support far away, vulkan support not even started. And porting Unity 8/Mir to Wayland would have taken a lot of time as well.

---

### Post by JonPaul on 2017-08-22
```

xhost +si:localuser:root
sudo synaptic

```

Thank you for this tip!

---

### Post by amano on 2017-08-22
Yw ;)

There should be an official shorter command via a script, someone (omg ubuntu?) suggested the “sugo“ name for the script. Sugo for the wayland pasta ;)

---

### Post by mc4man on 2017-08-22
> **amano said:**
> 
```

xhost +si:localuser:root
sudo synaptic

```

For maximum security you might add the following command after closing synaptic: blah, blah



Once running the xhost command you just open synaptic as usual, i.e. thru the icon or with command of
synaptic-pkexec

Using sudo synaptic is poor practice..
(- if you got that idea from Omg Ubuntu then just another example of a blog not paying attention to what they copy from elsewhere.

---

### Post by mc4man on 2017-08-22
> **ventrical said:**
> On today's daily install I only have :
Ubuntu
Ubuntu on Wayland

Regards..


That's all one should see in an Ubuntu install. The gnome* login options come from installing gnome-session which is not needed unless one wants the gnome version of settings, ect..

---

### Post by ventrical on 2017-08-23
> **mc4man said:**
> That's all one should see in an Ubuntu install. The gnome* login options come from installing gnome-session which is not needed unless one wants the gnome version of settings, ect..

Thats what I thought.

Thanks..

---

### Post by Chanath on 2017-08-23
> **amano said:**
> X is a security nightmare with a design from the 80s and people want to move away from that for years and years.

Are there a reasons to say X is a security nightmare? What type of security breaches you are talking about?

---

### Post by harry332 on 2017-08-23
Well until this issue is fixed I do the following.
When I need to use synaptic or gparted, I open a new session on Xorg.
If I do not need those apps, I can open a Wayland session.

---

### Post by amano on 2017-08-23
This issue won't be fixed in wayland since it is a upstream design decision. And synaptic and gparted won't be ported anytime soon.

If changing the session is faster than typing xhost +si:localuser:root , it is a good workaround then.

---

