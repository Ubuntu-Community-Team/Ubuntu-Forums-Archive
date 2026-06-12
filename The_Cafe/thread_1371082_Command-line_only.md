---
title: "Command-line only"
date: 2010-01-03
forum: The Cafe
---

### Post by CJ Master on 2010-01-03
I thought it would be fun trying out pure command-line linux. I have some questions though.

1) Anyway to set my resolution in command line to 1440x900?
2) I saw screenshots where the screen was split, how did they do that?
3) What's framebuffer and how do I enable it?
4) What are some good command-line apps to do normal activities?

Thanks :P

---

### Post by &#32 Greg on 2010-01-03
> **CJ Master said:**
> I thought it would be fun trying out pure command-line linux. I have some questions though.

1) Anyway to set my resolution in command line to 1440x900?
2) I saw screenshots where the screen was split, how did they do that?
3) What's framebuffer and how do I enable it?
4) What are some good command-line apps to do normal activities?

Thanks :P

[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

Browse there, you'll get a lot of help.

The screen is split with a multiplexer- most likely GNU Screen, although tmux and dvtm also are there. The framebuffer is a graphics layer that can be used to watch videos from off the CLI (without X). Some good apps include GNU Screen (Multiplexer), Emacs (text editor, EVERYTHING), LaTeX (documents), elinks (web browser), fbi (image viewer), mpd/ncmpcpp (music), mplayer (video), htop (system monitor), finch (IM), irssi (IRC), tty-clock (clock), mutt (email), mc (file browser), and of course vitetris (tetris).

---

### Post by CJ Master on 2010-01-03
Cool. Can a web browser use framebuffer to show pages normally, not just text? And is there anyway to watch youtube videos online like that? I'm guessing not :P

---

### Post by hellion0 on 2010-01-03
2) Screen is one way to do that.

4) Elinks (web browser), Centerim (instant messaging), Irssi (IRC client), mc (file manager/browser), cplay (music player), mplayer (media player (use "-vo fbdev" flag to watch vids in framebuffer)), fbi (image viewer), htop (system monitor), alsamixer (volume control), iftop (network monitor) <- these see use on my CLI-only system.

---

### Post by &#32 Greg on 2010-01-03
> **CJ Master said:**
> Cool. Can a web browser use framebuffer to show pages normally, not just text? And is there anyway to watch youtube videos online like that? I'm guessing not :P

links -g has limited framebuffer support.

As far as youtube, you're better off using a CLI youtube downloader and then watching in mplayer.

---

