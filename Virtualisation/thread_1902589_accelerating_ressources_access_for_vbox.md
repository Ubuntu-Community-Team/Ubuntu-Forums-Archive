---
title: "accelerating ressources access for vbox"
date: 2011-12-31
forum: Virtualisation
---

### Post by yayou on 2011-12-31
Hi everybody,

I'm a winamp-addict and I wanted to listen to my music on winamp installed on windows guest with vbox. But when I do that, I have some little audio bugs called I think, xruns. I would like to accelerate virtualbox access to host ressources. I noticed that when I used pulseaudio as audio server on vbox, I had many xruns. Then, I tried alsa in place of pulseaudio and realize that things were better as I had less xruns. But I wanted to avoid then totaly.
When I worked on my old laptop Dell Vostro 1000 (AMD Athlon X2, 2 Gio) I had this bugs but I thought that it was the computer who were lacking power. Now I have a Asus G74S (i7, 4 Gio, 3 Go video memory) and I have the same frequency of xruns (which surprised me). I thought with this powerful computer things should go faster.I think that perhaps with a good re-configuration, or a good trick I could listen music fluently from my windows guest on vbox. I typed a command (hdparm -T /dev/sda) found on the site linuxmao.org, and this is what I had:

Timing cached reads:   14802 MB in  2.00 seconds = 7407.32 MB/sec

The site said that we must have less than 60 ms to avoid xruns.

If I can do that, I will no longer boot on windows 7 since winamp is the only reason why I boot on windows.

Thanx a lot for giving me attention.

---

### Post by samigina on 2012-01-01
Using Vbox for Winamp?

Why dont use wine?

Or one of the linux native players?

---

### Post by yayou on 2012-01-02
Thanx samigina for reacting. First, I don't use vbox for winamp. I use it because I think virtualisation is a very great technology that every computer scientist should use. So I use it because I love it and using it to listen music is just a great opportunity for me to avoid booting my windows 7.
Why not using wine? Because there are still some bugs with winamp.
Why not using native software? Because none of them can give me the liberty I have with winamp (playlist and library management, plugins,...).

---

