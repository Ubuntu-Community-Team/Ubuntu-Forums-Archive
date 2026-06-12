---
title: "ltsp logs me out of the thin-terminal"
date: 2006-09-15
forum: Server Platforms
---

### Post by yemu on 2006-09-15
hi
i've just installed small ltsp server (for three clients), and i noticed that I sometimes get logged out from the terminals with absolutely no reason... 
i'd be grateful for any help 
best regards
y

---

### Post by Kalif on 2006-10-31
Hi!

Since I have been running X remotely on both thinner
and thicker clients, I have seen this particular
problem many times, regardless of operation system
brand:

A web browser, or any other graphical application
eats a lot of memory on your client computer (or
rather the X-server on the client machine eats memory
when you run many simultaneous windows with graphics
in them). When there is no more memory the X-server
on the client crashes and you will soon be refered
to the login prompt.

If this problem is the same as yours, either get
more memory for your client, or enable the nbd-server
on your server and swap over the network. Or plainly
close windows and browser tabs when you do not need
them any more.

Best,
k.

---

### Post by fnjordy on 2006-10-31
This will be easier with Edgy as the network swap systems works out of the box.  I found this happens with Intel i810 graphics adapters because the video memory size is incorrectly determined.  Try forcing the video memory size to 2MB and 16 bits per pixel colour depth in lts.conf:

X_VIDEO_RAM             = 2048
X_COLOR_DEPTH           = 16

I wrote some notes on Dapper:

[http://developer.novell.com/wiki/index.php/Miru_directory_server_post_install_checklist#X11_video_memory](http://developer.novell.com/wiki/index.php/Miru_directory_server_post_install_checklist#X11_video_memory)

and Edgy:

[http://developer.novell.com/wiki/index.php/Edgy/Ocean_post_install_checklist#X11_video_memory](http://developer.novell.com/wiki/index.php/Edgy/Ocean_post_install_checklist#X11_video_memory)

For a resolution 1024x768, video memory = 1024 x (16 bits per pixel / 8 bits per byte) x 768 = 2048 x 768 = 1572864 bytes = 1.5 MB.

---

### Post by drbobit on 2006-11-18
I've got a Wyse S30 thinclient running off a ubuntu 6.06 desktop machine via a wireless network. I've had this problem of the system crashing out to login with just two tabs open. The thinclient has 64mb of ram, if I want a more usable client how much RAM should I looking for a full 256/512?
Also if it's a pure memory issue could switching to a slim line browser like Opera help maybe?...

From a busniess point of view if your working on something and it crashes thats a real pain, is there someway to pursuade the server to keep apps open?

Cheers all...

---

