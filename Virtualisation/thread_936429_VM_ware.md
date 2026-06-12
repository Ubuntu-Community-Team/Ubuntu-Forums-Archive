---
title: "VM ware"
date: 2008-10-02
forum: Virtualisation
---

### Post by Captain Cole on 2008-10-02
Has anybody have experience with VM ware. i stopped by and talked to our ISP. they recommended it as a possible link between Ubuntu & the Windows format which the music was recorded onto the Ipod.

---

### Post by Madman6510 on 2008-10-02
The old VMWare was pretty good, and had some pretty nice features, but for some reason I can't get the new one to work right. I'd reccomend Virtualbox for a virtulisation program, if you're looking for one.

---

### Post by Paqman on 2008-10-02
I used VMWare server a while back, it was pretty good. You'll always take a huge performance hit when you're running a VM though.

What format is your music in? It might be possible to re-encode it into something a bit more friendly.

---

### Post by Captain Cole on 2008-10-02
is there a program to convert ogg files into mp3 files.

---

### Post by Paul41 on 2008-10-02
I may be misunderstanding you but it sounds like you ripped your music on a windows machine for a ipod and now you are using Ubuntu. Are you just looking for a way to make mp3 files in Ubuntu so you can use them on your ipod? Most of the the music players in Ubuntu that I know of will encode as mp3 if you set them that way.

---

### Post by Captain Cole on 2008-10-02
how can i do that?

---

### Post by Paul41 on 2008-10-03
The first thing you will need to do is make sure you have the packages installed for restricted formats.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Then in which ever player you are using there should be a option in the menus to rip as mp3. If you want help finding it let us know what player you are using and someone should be able to help you find it. If you want a suggestions on what to use I like Banshee.

---

### Post by Captain Cole on 2008-10-03
I am using amarok. compared to amarok would you say that banshee was better?

---

### Post by HermanAB on 2008-10-03
You can convert between music formats using sox:
find . -name \*.ogg -print -exec sox {} {}.mp3 \;

Cheers,

Herman

---

### Post by Paul41 on 2008-10-03
> **Captain Cole said:**
> I am using amarok. compared to amarok would you say that banshee was better?

A lot of people really like amarok. I have never used it because it is a KDE and I use GNOME.  If you are happy with Amarok I would stay with that.

---

