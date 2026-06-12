---
title: "Favourite terminal &amp; multiplexor"
date: 2009-03-11
forum: The Cafe
---

### Post by Primefalcon on 2009-03-11
I'm just wondering what everyones favourite terminal is for general useage is and what your favourite multiplexor for terminals is

whether its the gnome terminal, the virtual terminal (ctrl+alt+(f1-f6)) or a specialist one such as terminator....

personaly I tend to like the standard gnome terminal using the screen command to multiplex since using ctrl+c then " brings up a list of custom named terminal windows you can easily see what terminal is for what, such as

[IMG]http://i42.tinypic.com/2e67ic8.png[/IMG]

---

### Post by sujoy on 2009-03-11
when in *boxes or gnome, its urxvt with screen
otherwise i mostly use xmonad, and with a tiler doing the multiplexing, urxvt is enough :)

i run urxvtd + urxvtc though, not urxvt directly ...

---

### Post by MaindotC on 2009-03-11
I didn't even know what this question meant so I did "man screen" and now i'm reading about it.

---

### Post by .Maleficus. on 2009-03-11
urxvt and tiling with dwm works well for me.  In Pekwm, I generally use xfce-terminal with tabs :).  No real need to use screen or anything.
> **sujoy said:**
> when in *boxes or gnome, its urxvt with screen
otherwise i mostly use xmonad, and with a tiler doing the multiplexing, urxvt is enough :)

i run urxvtd + urxvtc though, not urxvt directly ...
I've seen a lot of people do that, is there any particular reason?  Keeps memory usage low I assume?


Edit:  And what did you do to set it up?

---

### Post by zmjjmz on 2009-03-11
> **strAlan said:**
> I didn't even know what this question meant so I did "man screen" and now i'm reading about it.

It might take you a few years.

I use mrxvt and its tabs for multiplexing.

---

### Post by sujoy on 2009-03-11
> **.Maleficus. said:**
> urxvt and tiling with dwm works well for me.  In Pekwm, I generally use xfce-terminal with tabs :).  No real need to use screen or anything.

I've seen a lot of people do that, is there any particular reason?  Keeps memory usage low I assume?


Edit:  And what did you do to set it up?

yea well it saves a few KB/MB :P so why not? since its easy to setup

i have ```
urxvtd -q -f -o &
``` added to my ~/.xinitrc
or you can place it wherever you wish to start it just before the X-session starts. the 'o' option is there to kill the daemon when X is killed.

[here]("http://dpaste.com/12668/") is my .xinitrc as a reference

---

### Post by DoktorSeven on 2009-03-11
xterm + screen.

---

### Post by aeiah on 2009-03-11
just the defaults of gnome-terminal in ubuntu and terminator in crunchbang.

im not scared of the terminal but unless im ssh-ing somewhere or opening up a file with nano i dont really have a need to use it. i do like terminator though. ill probably install it on my regular ubuntu box soon

---

### Post by Dr Small on 2009-03-11
> **zmjjmz said:**
> It might take you a few years.

I use mrxvt and its tabs for multiplexing.
I learned screen in a day. It's relatively simple.

---

### Post by kidux on 2009-03-11
I don't usually have a terminal running for anything, so whatever the default for the DE I'm using is.

---

### Post by MaindotC on 2009-03-13
Yeah I'm like totally lost now.

---

### Post by cb951303 on 2009-03-13
a few months ago, I tried almost all the terminal emulators because I couln't get my numpad work in vt102 mode. Then, I found that none of the terminal emulators support it 100% eventhough a lot of them state it in their feature list. The only one that actually worked was **xterm**. That's my choice.

---

### Post by will1911a1 on 2009-03-13
urxvt.

---

### Post by kaig on 2009-04-04
I've grown fond of terminator: [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)

---

### Post by jimi_hendrix on 2009-04-04
i use gnome terminal

---

