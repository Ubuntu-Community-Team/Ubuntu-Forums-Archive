---
title: "I just got to use SLiM Today..."
date: 2010-01-29
forum: The Cafe
---

### Post by Psumi on 2010-01-29
[https://launchpad.net/~stemp/+archive/xfce/+packages](https://launchpad.net/~stemp/+archive/xfce/+packages)

From There, I installed SLiM, and on next reboot, I was greeted with a nice X11 login screen for debian. It really works wonders for those trying to get around gnome dependencies.

Also, has anyone noticed these issues with midori?

-- When you hit the back button sometimes, midori crashes (regardless if you use the back arrow or the key combination.)

-- Can't tell midori to not remember download history.

-- Quick Edit for vBulletin never loads. (May be a webkit issue)

-- When you click an area on the webpage after typing in an address (and maybe switching from another tab) it takes several clicks before you can use the up/down arrow keys (on the keyboard) to scroll the page.

-- Sometimes, the page will go to the top randomly when scrolling the page, even seconds or a minute has passed since loading completed.

---

### Post by juancarlospaco on 2010-01-29
Im using Slim, im using Midori.

All Webkit browsers 100/100 on AcidTest got some problems like you say on webpages,
i think is something on the poor coded page, too much pages contain several errors.
It cant handle APT:url links, erase private data works for me.

---

### Post by Psumi on 2010-01-29
> **juancarlospaco said:**
> Im using Slim, im using Midori.

All Webkit browsers 100/100 on AcidTest got some problems like you say on webpages,
i think is something on the poor coded page, too much pages contain several errors.
It cant handle APT:url links, erase private data works for me.

Yeah, it's too bad, and too bad that karmic doesn't have slim in its repos (but lucid does.)

---

### Post by juancarlospaco on 2010-01-29
*I installed from Jaunty repo...*

---

### Post by spupy on 2010-01-29
What are the advantages of SLiM over console login + startx?

---

### Post by llawwehttam on 2010-01-29
> **spupy said:**
> What are the advantages of SLiM over console login + startx?
 
It looks nice and doesn't scare noobs away. 
You don't want people thnking:
Arrrrrgh ive broken the interwebs!!!!

---

### Post by ~sHyLoCk~ on 2010-01-29
I used this in ~/.bashrc , but now I use slim to choose sessions, still trying to figure out how I can create a session manager for xdm and then I'll switch to xdm!
```
#if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
#  startx
#  logout
#fi
```

---

### Post by spupy on 2010-01-29
> **llawwehttam said:**
> It looks nice and doesn't scare noobs away. 
You don't want people thnking:
Arrrrrgh ive broken the interwebs!!!!

But I want to scare the noobs! I want them to fear my machine.
"I better not touch this... thing, or it will eat me."

---

### Post by Psumi on 2010-01-29
> **~sHyLoCk~ said:**
> I used this in ~/.bashrc , but now I use slim to choose sessions, still trying to figure out how I can create a session manager for xdm and then I'll switch to xdm!
```
#if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
#  startx
#  logout
#fi
```

sudo apt-get install wdm.

WDM uses XDM configuration, just in its own WDM folder.

---

### Post by Grifulkin on 2010-01-29
I use slim on my Desktop and Laptop, on my netbook I use CDM which is a tiny bash script.  It was in the AUR and it seems nice.  Very nice little session manager.   But yeah I much prefer to see something cool at startup rather than console login + startx.

---

### Post by RiceMonster on 2010-01-29
IMO DMs are a waste of time unless you're using GNOME or KDE, inwhich you need them for shutdown, restart, etc to work.

---

### Post by Psumi on 2010-01-29
> **RiceMonster said:**
> IMO DMs are a waste of time unless you're using GNOME or KDE, inwhich you need them for shutdown, restart, etc to work.

So what should I edit to make startx run at startup?

---

### Post by spupy on 2010-01-29
> **RiceMonster said:**
> IMO DMs are a waste of time unless you're using GNOME or KDE, inwhich you need them for shutdown, restart, etc to work.

Yeah, I see the login thrice a month. I don't really need a login manager.
Also, when I use startx, I find it informing to go to tty1 and look at the output of all graphical programs.
But that is just me.

---

### Post by ~sHyLoCk~ on 2010-01-29
> **Psumi said:**
> So what should I edit to make startx run at startup?

Err see my previous post

---

### Post by Psumi on 2010-01-29
> **~sHyLoCk~ said:**
> Err see my previous post

So I should put...
```
#if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
#  startx
#  logout
#fi
```

into bashrc at the end? without the #s?

---

### Post by n0dix on 2010-01-29
> **Psumi said:**
> So I should put...
```
#if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
#  startx
#  logout
#fi
```

into bashrc at the end? without the #s?

Yes, without. In yours  ~/.bashrc, is different to bashrc.

---

### Post by NoaHall on 2010-01-29
Oh, and of course edit it if you want it to start on tty7 or whatever.

---

### Post by Psumi on 2010-01-29
> **NoaHall said:**
> Oh, and of course edit it if you want it to start on tty7 or whatever.

How do I do that?

---

### Post by juancarlospaco on 2010-01-29
I read on some forum that WDM is a modified version of XDM.
Slim is nice, you can use .png and .jpg for themez

---

### Post by Psumi on 2010-02-03
> **Psumi said:**
> How do I do that?

No one replied to this I see. VERY helpful.

---

### Post by ~sHyLoCk~ on 2010-02-03
> **Psumi said:**
> No one replied to this I see. VERY helpful.

What do you expect? This is community Cafe of ubuntu forum, tech support is not at it's finest here. Anyway edit this: $(tty) = /dev/tty1 to tty7

---

### Post by Psumi on 2010-02-03
> **~sHyLoCk~ said:**
> What do you expect? This is community Cafe of ubuntu forum, tech support is not at it's finest here. Anyway edit this: $(tty) = /dev/tty1 to tty7

I thought it was more involved because of the "logout" line. Because it makes me think I won't be able to login because I'll be logged out as soon as startx runs.

---

### Post by MooPi on 2010-02-18
> **spupy said:**
> But I want to scare the noobs! I want them to fear my machine.
"I better not touch this... thing, or it will eat me."
This is how I scare the noobs away
[[IMG]http://i559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/th_xdmlogin.jpg[/IMG]]("http://s559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/?action=view&current=xdmlogin.jpg")

---

### Post by n0dix on 2010-02-18
> **MooPi said:**
> This is how I scare the noobs away
[[IMG]http://i559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/th_xdmlogin.jpg[/IMG]]("http://s559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/?action=view&current=xdmlogin.jpg")

:twisted:really great, :twisted: 
seems they gone to hell if don't match the password.

---

### Post by MooPi on 2010-02-18
Another login favorite
[[IMG]http://i559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/th_AgentLogin.jpg[/IMG]]("http://s559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/?action=view&current=AgentLogin.jpg")
Officially scary

---

### Post by n0dix on 2010-02-18
This worst than the first one. ;)

---

### Post by falconindy on 2010-02-18
> **RiceMonster said:**
> IMO DMs are a waste of time unless you're using GNOME or KDE, inwhich you need them for shutdown, restart, etc to work.
Unnecessary. If you want to launch Gnome from startx, use this as your exec line in .xinitrc:
```
exec ck-launch-session gnome-session
```

---

