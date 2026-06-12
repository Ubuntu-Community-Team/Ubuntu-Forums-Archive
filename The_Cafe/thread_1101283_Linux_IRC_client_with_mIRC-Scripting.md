---
title: "Linux IRC client with mIRC-Scripting"
date: 2009-03-20
forum: The Cafe
---

### Post by SpriteSODA on 2009-03-20
Hi guys, I'm not sure if this is the right forum to ask, but I can't seem to find a better place. 

Is anyone here familiar with a Linux IRC client that can run mIRC scripts?
I know that I can run it with Wine but it too problematic as I need it for a dedicated server.

---

### Post by Eisenwinter on 2009-03-20
No. Only mIRC can run mIRC scripts.

If you're desparate to use mIRC, you can run it under WINE, you will need to get a few native DLLs (use winetricks for that) in order to be able to open the scripts editor.

---

### Post by SpriteSODA on 2009-03-20
my problem is that my dedicated server doesnt have a screen or anything, i access it through ssh

---

### Post by jimi_hendrix on 2009-03-20
> **SpriteSODA said:**
> my problem is that my dedicated server doesnt have a screen or anything, i access it through ssh

may i recommend irssi?

---

### Post by Bachstelze on 2009-03-20
> **SpriteSODA said:**
> my problem is that my dedicated server doesnt have a screen or anything, i access it through ssh

You can use VNC.

> **jimi_hendrix said:**
> may i recommend irssi?

I didn't know irssi could run mIRC scripts...

---

### Post by Eisenwinter on 2009-03-20
> **HymnToLife said:**
> I didn't know irssi could run mIRC scripts...
It can't.

But it supports Perl scripting.

---

### Post by SpriteSODA on 2009-03-20
> **HymnToLife said:**
> You can use VNC.



I didn't know irssi could run mIRC scripts...

how do i make it a VNC? its a fedora 9 server.

---

### Post by jimi_hendrix on 2009-03-20
> **HymnToLife said:**
> I didn't know irssi could run mIRC scripts...

for the no monitor part

---

### Post by Dr Small on 2009-03-20
In regards to the lack of a monitor, use SSH, connect to the dedicated server, launch screen, and open IRSSI, the best IRC client available :) VNC is too laggy for my likings, just to open a display to view a IRC client.

---

### Post by Mehall on 2009-03-20
> **Dr Small said:**
> In regards to the lack of a monitor, use SSH, connect to the dedicated server, launch screen, and open IRSSI, the best IRC client available :) VNC is too laggy for my likings, just to open a display to view a IRC client.

Agreed, and there are TONS of irssi scripts out there.

---

### Post by SpriteSODA on 2009-03-20
i'm afraid it wont work for me, i have bots with scripts and i must run them :(
how do i launch screen?

---

### Post by Dr Small on 2009-03-20
> **Mehall said:**
> Agreed, and there are TONS of irssi scripts out there.
Ditto
[http://scripts.irssi.org/](http://scripts.irssi.org/)

---

### Post by Dr Small on 2009-03-20
> **SpriteSODA said:**
> i'm afraid it wont work for me, i have bots with scripts and i must run them :(
how do i launch screen?
Bot scripts should *never* be run client side anyhow. If you're running a bot, you should also have a server on the planet somewhere that can run it.

As for screen, just type:
```
screen
```

Launch IRSSI, and when you want to detach screen, press:
```
CTRL+a d
```

When you want to reattach screen, run:
```
screen -r
```

---

### Post by SpriteSODA on 2009-03-20
Well, I didn't code those bots, but I must use them. I have a linux server, so I can't run the mIRC there. I don't want to purchase a WINDOWS VNC server just for the mirc.

---

### Post by Bachstelze on 2009-03-20
> **SpriteSODA said:**
> Well, I didn't code those bots, but I must use them. I have a linux server, so I can't run the mIRC there. I don't want to purchase a WINDOWS VNC server just for the mirc.

You can use VNC on a Linux server, I have two of them. However, this is not the right place to ask about setting it up on Fedora.

---

### Post by SpriteSODA on 2009-03-20
is it a serious hussle?

---

### Post by conundrumx on 2009-03-20
Setting up VNC is easy.  However, the **Ubuntu** forums are probably the wrong place to seek help for **Fedora**.  As far as your problem; if you can't (or won't) run mIRC in Wine then you're SOL.  Your only options are Wine or Virtualization, no *nix client supports mIRC scripts.

---

### Post by Mrenigma on 2010-03-12
hi Guys i'm a new Linux "ubuntu" user i dont know any thing but i install it and wana learn on it but i have a problem i really need to Run the "mIRC" on it but i can't install wine :-s thats my problem can i have some help? 

this is the error
root@enigma-laptop:/home/enigma/Desktop# apt-get install WINE
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package WINE
root@enigma-laptop:/home/enigma/Desktop#

---

### Post by Tibuda on 2010-03-12
> **Mrenigma said:**
> hi Guys i'm a new Linux "ubuntu" user i dont know any thing but i install it and wana learn on it but i have a problem i really need to Run the "mIRC" on it but i can't install wine :-s thats my problem can i have some help? 

this is the error
root@enigma-laptop:/home/enigma/Desktop# apt-get install WINE
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package WINE
root@enigma-laptop:/home/enigma/Desktop#

it should be lower case.

---

### Post by Sam on 2010-03-12
All packages names are lowercase.
```
sudo apt-get install wine
```

---

### Post by samalex on 2010-03-12
> **Mehall said:**
> Agreed, and there are TONS of irssi scripts out there.

I agree.  irssi won't run mIRC scripts, but it shouldn't be hard to either rewrite mIRC scripts for irssi or find canned scripts that do the same thing.  Personally I think irssi is more powerful, but I haven't done any IRC scripting in YEARS.

Sam

---

