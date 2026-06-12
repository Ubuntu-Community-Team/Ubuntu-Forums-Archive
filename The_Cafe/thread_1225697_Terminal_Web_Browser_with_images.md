---
title: "Terminal Web Browser with images?"
date: 2009-07-28
forum: The Cafe
---

### Post by Jimleko211 on 2009-07-28
Are there any web browsers on the command line that supports the viewing of images?

Also, what are the names of the IM clients and the media players (like Banshee or Rythym box)

---

### Post by kerry_s on 2009-07-28
> **Jimleko211 said:**
> Are there any web browsers on the command line that supports the viewing of images?

Also, what are the names of the IM clients and the media players (like Banshee or Rythym box)

links2 ? **sudo apt-get install links2**

do you mean im for the cli ? i use centerim on mine.
as for player in the cli i'll just usually use aplay from alsa.

---

### Post by Jimleko211 on 2009-07-28
I've tried Links2, it doesn't support images, I'm afraid :(

---

### Post by y-lee on 2009-07-28
See [A day without X]("http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/")

---

### Post by PurposeOfReason on 2009-07-28
> **Jimleko211 said:**
> I've tried Links2, it doesn't support images, I'm afraid :(
Does too. Run it as links2 -g.

---

### Post by mrgnash on 2009-07-28
I like cmus for a terminal application that supports a music library a-la Banshee. Love Banshee itself, but it's a bit heavy for my current system.

---

### Post by Sublime Porte on 2009-07-28
> Are there any web browsers on the command line that supports the viewing of images?

The site mentioned above (A day without X) has a link to a browser, but when you say terminal, do you mean a terminal emulator inside X? Because they won't display in a terminal emulator, only in a tty console, which has a framebuffer enabled.

---

### Post by Jimleko211 on 2009-07-28
> **Sublime Porte said:**
> The site mentioned above (A day without X) has a link to a browser, but when you say terminal, do you mean a terminal emulator inside X? Because they won't display in a terminal emulator, only in a tty console, which has a framebuffer enabled.
Yeah, that's what I mean.  But links2 -g worked.

---

### Post by MikeTheC on 2009-07-28
Links2 works fine here, but I still prefer Firefox.

---

### Post by chris4585 on 2009-07-29
For IMing bitlbee is the best IMO, use it with irssi.  For music I use moc, its awesome IMO.  Also a little info on links2, using the option -g it will work in a console if your video card supports framebuffering, its a way of displaying a GUI without xorg installed.  You can also watch videos with mplayer using framebuffer.

If you're interested in doing stuff without x, you should try INX, INX is Not X.

[http://inx.maincontent.net]("http://inx.maincontent.net")

Its a livecd and a full distro that is built off of Ubuntu and has all sorts of cli goodies.

---

### Post by mrgnash on 2009-07-30
Just wondering if anyone else has encountered the problem where links2 doesn't seem to save any of your login details between sessions, or sometimes even within the same session (due to not storing cookies or something I suppose)?

---

### Post by dragos240 on 2009-07-30
> **Jimleko211 said:**
> Yeah, that's what I mean.  But links2 -g worked.

Also. xlinks2

---

### Post by sertse on 2009-07-30
links2 -g is xlinks2. I latter I think its a symlink? to the former.

yea, links2 doesn't have cookie support. It's not elinks :P. Now, if someone would remerge the projects...

+1 INX suggestion.

---

### Post by kk0sse54 on 2009-07-30
elinks - my favorite cli web browser
finch - CLI version of pidgin

---

### Post by Dullstar on 2009-07-30
I honestly question why do that in the terminal.

---

### Post by hanzomon4 on 2009-07-30
> **Dullstar said:**
> I honestly question why do that in the terminal.

Because its fun! and if you run a cool wm Like Awesome wm with xcompmgr it just looks so cool.

---

### Post by mrgnash on 2009-07-31
> **hanzomon4 said:**
> Because its fun! and if you run a cool wm Like Awesome wm with xcompmgr it just looks so cool.

Yes, plus links2 is insanely fast. That's why I wish it supported cookies and javascript.

---

### Post by thejart on 2009-08-04
links2 is supposed to support (some) javascript, but i can't get it to work.  i've installed from the repositories and built it myself to no avail.

has anyone had success getting javascript running on links2?

---

### Post by Viva on 2009-08-04
links2 is awesome. It seems to have some problems with emerald though.

---

### Post by unknownPoster on 2009-08-04
> **Dullstar said:**
> I honestly question why do that in the terminal.

Some of us pride ourselves on having absolutely minimal systems.

---

