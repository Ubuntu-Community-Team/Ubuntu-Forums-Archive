---
title: "autoplay cd's"
date: 2008-09-03
forum: Server Platforms
---

### Post by trash on 2008-09-03
My server is stationary as opposed to my laptop, so i want my speakers attached to the server for some music... How do i get cd's to start playing when inserted?

---

### Post by windependence on 2008-09-04
This might help you:

[https://wiki.ubuntu.com/autorun](https://wiki.ubuntu.com/autorun)

However, this is more of a desktop question and you may get better response in the desktop section. Autoplaying CDs isn't usually a server task.


-Tim

---

### Post by trash on 2008-09-04
this must be an audio cd issue because i am not even able to mount it manually, but i can mount the install cd no problem. I'll look at the automount problem later lol

so has anybody had this audio cd problem on their server?

---

### Post by windependence on 2008-09-04
Yes, you can't mount an audio CD since there is really no file system on it. You can either play it or rip it.

-Tim

---

### Post by trash on 2008-09-04
Thats part of the problem, mount is asking me to specify one. I haven't changed the default fstab and the cdrom is in there. I am having the same problem on my laptop running Xubuntu since i disabled automounting... very odd.

Thats kind of why I was hoping for a cli solution:)

---

### Post by windependence on 2008-09-04
I'm thinking we're going to have to use a command line player of some sort.

-Tim

---

### Post by trash on 2008-09-04
No joy there either. I tried mocp but it sees no music.

However on my laptop vlc will play the cd even though everywhere else on my system it says no cd mounted.

---

### Post by windependence on 2008-09-04
[http://packages.ubuntu.com/hardy/cdcd](http://packages.ubuntu.com/hardy/cdcd)

-Tim

---

### Post by trash on 2008-09-10
> **windependence said:**
> [http://packages.ubuntu.com/hardy/cdcd](http://packages.ubuntu.com/hardy/cdcd)

-Tim

The tria(sp?) on my satellite dish died, got it fixed now:)... thanks for the help but I did a lot of testing and tinkering over the past 5 LOOOONG days and it seems that mocp just won't play wave files no matter what.

Well actually it's not that it won't play them as far as i know because I can't mount any disk that has wave files on them. On my laptop I have the exact same issue, won't mount a disk with wave files but if i go through vlc I can select to play the disk no problem... so now the question is why won't Ubuntu mount a disk with wave audio files?

---

### Post by LRKSFAG on 2008-09-11
[size=2]&#25105;&#39030;&#20804;&#24351;&#65292;&#25509;&#30528;&#39030;[/size][NTN&#36724;&#25215;](http://www.nsk2008.cn/see/193.html)[INA&#36724;&#25215;](http://www.nsk2008.cn/see/196.html)[NACHI&#36724;&#25215;](http://www.nsk2008.cn/see/197.html)[IKO&#36724;&#25215;](http://www.nsk2008.cn/see/198.html)

---

### Post by windependence on 2008-09-11
> **trash said:**
> The tria(sp?) on my satellite dish died, got it fixed now:)... thanks for the help but I did a lot of testing and tinkering over the past 5 LOOOONG days and it seems that mocp just won't play wave files no matter what.

Well actually it's not that it won't play them as far as i know because I can't mount any disk that has wave files on them. On my laptop I have the exact same issue, won't mount a disk with wave files but if i go through vlc I can select to play the disk no problem... so now the question is why won't Ubuntu mount a disk with wave audio files?

Yes, the reason you can't mount it is because the CD has no recognizable file system on it. The only thing that is going to be able to decode it is some sort of media player (like vlc). What you need is a good command line player like mplayer without the GUI, and the correct installed codecs for the files you are trying to play. I don't really have any other ideas for you but this is why you can't mount it.

-Tim

---

### Post by trash on 2008-09-11
AHHH i see! I never think of mplayer to play music so i never even tried it, studid of me since it's working perfectly for video playback! I'll give that a try today, thanks:)

---

