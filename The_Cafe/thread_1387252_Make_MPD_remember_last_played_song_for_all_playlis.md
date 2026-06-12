---
title: "Make MPD remember last played song for all playlists"
date: 2010-01-21
forum: The Cafe
---

### Post by teresaejunior on 2010-01-21
[FONT=Arial][SIZE=4]We need people to test my script!!![/SIZE][/FONT][FONT=Arial]
[B]
This tutorial has been removed, 'cause modified mpdpss a lot and now doesn't need a tutorial anymore, now if you go to [http://code.google.com/p/mpdpss](http://code.google.com/p/mpdpss), you can download a .deb package for installing it more easily! Also it now has an optional GTK+ interface! For that "sudo apt-get install zenity", and run 'mpdpss -g'[/B]
[/FONT][FONT=Arial]
Hi to all MPD users in Ubuntu!

This thread is for you who would like the Music Player Daemon to remember the last played song whenever you load a playlist!

MPD saves your current playlist position in a state_file, so when you restart it, you will get to play from the file you stopped before. But this is available only for the current playlist. I also found a little difficult for my mother to switch playlists in ncmpcpp. So I wrote a script for ourselves and now have rewritten it from scratch and adapted it for everybody!

[/FONT][FONT=Arial][SIZE=4]
Help and Get Help![/SIZE][/FONT][FONT=Arial]

I need volunteers to test it! Also this thread will be open if you need help, if something was unclear, to give suggestions...
Also visit us at [http://code.google.com/p/mpdpss/](http://code.google.com/p/mpdpss/) to check for new releases (which will be available when users report issues)!
[/FONT]

---

### Post by jpeddicord on 2010-01-22
Moved to Multimedia & Video, since this is not a tutorial.

---

### Post by teresaejunior on 2010-01-22
> **jpeddicord said:**
> Moved to Multimedia & Video, since this is not a tutorial.

I do respect your decision, but isn't Multimedia & Video for requesting help? I mean, I want people to test it, but this is a HowTo.

Thanks for your understanding!

---

### Post by jpeddicord on 2010-01-22
> **teresaejunior said:**
> I do respect your decision, but isn't Multimedia & Video for requesting help? I mean, I want people to test it, but this is a HowTo.

Thanks for your understanding!

The Multimedia & Video forum is not just for requesting help, though I could move this to the Cafe if you would like. To qualify for Tutorials & Tips, it must actually be a tutorial and not just a script or application to download.

---

### Post by teresaejunior on 2010-01-22
Would you move that for me then? Thanks!

---

### Post by jpeddicord on 2010-01-22
> **teresaejunior said:**
> Would you move that for me then? Thanks!

Done. :)

---

### Post by teresaejunior on 2010-01-31
[B]NOBODY HERE TO TEST IT??? CAN'T BELIEVE IT!!!

News! :p
[/B]
Added GTK+ graphical interface with the help of Zenity and running mpdpss with the option -g! Download now!!!
[http://code.google.com/p/mpdpss](http://code.google.com/p/mpdpss)

for the graphical interface: sudo apt-get install zenity
then run it as mpdpss -g

---

### Post by Barrucadu on 2010-01-31
Nice script; if I didn't already use randomly-generated dynamic playlists (by one of my many MPD utilities), I'd be tempted to try it.

---

### Post by teresaejunior on 2010-01-31
OK, thanks!

---

### Post by teresaejunior on 2010-02-02
Created a .deb package for easy installation!!!

Download it and install it by clicking on it (depending on your DE), or by running:

```
sudo dpkg -i package_name.deb
```

---

### Post by nilarimogard on 2010-02-02
The link [http://mpdpss.googlecode.com/p/mpdpss](http://mpdpss.googlecode.com/p/mpdpss) is wrong. It should be [http://code.google.com/p/mpdpss/](http://code.google.com/p/mpdpss/)

P.s.: I'll give it a try right now!

---

### Post by nilarimogard on 2010-02-02
OK so I've used it with ncmpcpp, and it correctly saves and loads playlists but it doesn't remember the last played song. What am I doing wrong?

---

### Post by teresaejunior on 2010-02-02
OK, thanks for reporting the link!

It looks like the last mpc upgrade in the repositories (from 04-01) has changed the output of "mpc playlist". I had a dist-upgrade a few days ago and couldn't test it anymore. Thanks for reporting. I'm workin hard on it and hope to have news ASAP. Thanks!

---

### Post by teresaejunior on 2010-02-02
> **nilarimogard said:**
> OK so I've used it with ncmpcpp, and it correctly saves and loads playlists but it doesn't remember the last played song. What am I doing wrong?

You were right! Debian has recently upgraded mpc. So now, please download the new [.deb package]("http://mpdpss.googlecode.com/files/mpdpss_1.5.1_all.deb") and try again! Remember that first you save a playlist with it, then later it brings back to the file you were listening to!

---

### Post by nilarimogard on 2010-02-03
Yes, now it works. Thank you!

---

### Post by nilarimogard on 2010-02-03
I made a post and a short video with Mpdpss in action: [Mpdpss Makes MPD Remember Last Played Song For All Playlists]("http://www.webupd8.org/2010/02/mpdpss-makes-mpd-remember-last-played.html")

---

### Post by teresaejunior on 2010-02-03
Thanks for your video!

---

