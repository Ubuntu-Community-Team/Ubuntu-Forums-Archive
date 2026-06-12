---
title: "Openbox 3.5 released"
date: 2011-08-03
forum: The Cafe
---

### Post by urukrama on 2011-08-03
For all you Openbox lovers: Openbox 3.5 has been released. Download it [here](http://openbox.org/wiki/Openbox:Download). The changelog is fairly brief:

[list]* New alt-tab dialog shows windows in a vertical list. 
* Improved Xinerama support. 
* Allow icons in menus. 
* Theme options for prompt dialogs (osd.button.unpressed.*, osd.button.pressed.*, osd.button.focused.*) 
* Addresses bug #4877, #4596, #4617, #4752, #4663, #4662, #4586, #2319, #4341, #4519, #4543, #4503, #4355, #4072, #3702, #4284 
* Lots of additional bug fixes and performance improvements.[/list]

---

### Post by medic2000 on 2011-08-03
As an openbox fan and faithful user i applaud this update! Openbox the ultimate desktop experience!

---

### Post by TeoBigusGeekus on 2011-08-03
> **medic2000 said:**
> As an openbox fan and faithful user i applaud this update! Openbox the ultimate desktop experience!

+1

> **urukrama said:**
>  
* Allow icons in menus. 


Hmm... wouldn't that make openbox -a tiny bit I admit- slower?

---

### Post by mips on 2011-08-03
Will check it out when it hits the Arch repos ;)

---

### Post by urukrama on 2011-08-03
> **TeoBigusGeekus said:**
> Hmm... wouldn't that make openbox -a tiny bit I admit- slower?

Openbox already had icons in menus, just not the root menu. The client menu, which had icons in earlier versions, was not noticeably slower to load than the root menu.

---

### Post by TeoBigusGeekus on 2011-08-03
> **urukrama said:**
> Openbox already had icons in menus, just not the root menu. The client menu, which had icons in earlier versions, was not noticeably slower to load than the root menu.

Alright, cool!!!
I love openbox...

---

### Post by el_koraco on 2011-08-03
Gotta say, two weeks with CrunchBang, and I can safely claim I've never used such a user friendly WM or DE as Openbox.

---

### Post by Lightstar on 2011-08-03
> **TeoBigusGeekus said:**
> +1


Hmm... wouldn't that make openbox -a tiny bit I admit- slower?

As long as we can customize and put that option on or off, I'd be happy with icons.  If it does get slower, turn it off, yeah?

I'm pro-options!
I love linux for that.

---

### Post by drawkcab on 2011-08-03
I used to be such an xfce fan.  Nowadays Openbox & LXDE get the job done quite nicely and I have little use for xfce except for Thunar.

---

### Post by jwmollman on 2011-08-09
> **drawkcab said:**
> I used to be such an xfce fan.  Nowadays Openbox & LXDE get the job done quite nicely and I have little use for xfce except for Thunar.

I agree. I'm always switching between Xfce and Openbox (with tint2) on my netbook.

I do love Thunar as a file manager with Openbox, but when I install it, it brings in so many other Xfce packages with it totaling some 35MB or so (can't remember off the top of my head). Is there a way to install Thunar without all of those dependencies, and just use the file manager as a file browser, or is all those things required? I don't need things like xfce4-panel with Openbox.

---

### Post by Madspyman on 2011-08-09
Nice Openbox is the best.

---

### Post by el_koraco on 2011-08-09
> **jwmollman said:**
> I agree. I'm always switching between Xfce and Openbox (with tint2) on my netbook.

I do love Thunar as a file manager with Openbox, but when I install it, it brings in so many other Xfce packages with it totaling some 35MB or so (can't remember off the top of my head). Is there a way to install Thunar without all of those dependencies, and just use the file manager as a file browser, or is all those things required? I don't need things like xfce4-panel with Openbox.

If you-re using a Debian based distro, use the command

```
sudo apt-get install --no-install-recommends thunar
```

---

### Post by XubuRoxMySox on 2011-08-09
Will the new one work in Lucid? I'm having to stay with LTS releases.

I Loved Openbox on Crunchbang 9.04 back about um, a year and a half ago now I guess. Ultralight, right-click simplicity!

[FONT="Comic Sans MS"]**[COLOR="Purple"]-Robin[/COLOR]**[/FONT]
(signing just to tweak some people who complained about me signing my posts, lol)

---

### Post by jwmollman on 2011-08-09
> **el_koraco said:**
> If you-re using a Debian based distro, use the command

```
sudo apt-get install --no-install-recommends thunar
```

Wow, it's as easy as that? Thanks!

I do remember a command like that when trying out LXDE a while back, when I didn't want all the packages that came with it.

---

### Post by el_koraco on 2011-08-09
> **jwmollman said:**
> Wow, it's as easy as that? Thanks!

I do remember a command like that when trying out LXDE a while back, when I didn't want all the packages that came with it.

It tells the package manager to include only the necessary stuff. No idea how much it will pull along, though. Edit: just checked it out, you'll avoid installing these:

```
Recommends: hal
  Recommends: dbus-x11
  Recommends: gamin
  Recommends: xfce4-panel
  Recommends: xfce4-panel
  Recommends: thunar-volman
  Recommends: xdg-user-dirs

```

---

### Post by el_koraco on 2011-08-09
> **dixiedancer said:**
> Will the new one work in Lucid? I'm having to stay with LTS releases.


People have installed it on Squeeze, so it should work. And as I've seen on the site, it has a short list of dependencies.

---

