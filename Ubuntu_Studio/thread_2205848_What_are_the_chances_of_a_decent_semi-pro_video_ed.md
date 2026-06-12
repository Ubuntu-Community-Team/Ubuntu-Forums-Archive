---
title: "What are the chances of a decent semi-pro video editor?"
date: 2014-02-16
forum: Ubuntu Studio
---

### Post by halfbeing on 2014-02-16
Does anyone have any idea as to the chances of a usable semi-pro video editor coming along? By semi-pro I mean at the very minimum that you can separate audio and video tracks.

Openshot is decent and usable for simple amateur jobs where one clip straightforwardly follows another, but when it comes to anything more complicated I have always come to grief. Cinelerra is very fussy about its media and is prone to crashing. It won't work properly with media created by my Android phone, and I have to export everything twice: once to a format readable only by VLC and then, using VLC, to a format readable by other applications, which is very time consuming and even then produces flaky results which don't, for instance, play properly on VLC for Mac. This is very frustrating. I also find the Cinelerra interface completely counter-intuitive and very hard to use. For example I can't even find a way to split a clip like I am used to in DAWs and other NLEs.

Meanwhile LiVES insists on transcoding every clip it imports. With an NLE you should be able to import your stuff and work on it straight away, not wait for several hours while an application unnecessarily hogs your processor. I have no idea why the developers of LiVES have made such a strange decision. As with Cinelerra, it means that everything has to be transcoded twice instead of once. As a consequence I have never actually tried working with LiVES because I haven't had the time or the patience to wait for it to transcode the imported media.

All this means that for anything but the simplest jobs I have no choice but to fire up an old desktop machine with Windows on it to use a Windows-native NLE, but this is not an ideal solution. Is there any hope that the situation with regard to video editing in (non-big expensive studio) Linux will improve?

---

### Post by jejeman on 2014-02-16
Kdenlive served me well on:
- documentary (no efects, just plain edit and titleing, DV)
- music video  (effects, multiple composited tracks, full HD)

For non FLOSS solutions there is Lightworks.

---

### Post by cub on 2014-02-17
As jejeman I use Kdenlive for all my video editing. I tried to learn Cinelerra but gave up and others have said what you just stated, that it's difficult and crash a lot. Lightworks might be interesting but has to be installed manually.

So, IMHO, Kdenlive would be the way forward.

---

### Post by shaunthesheep on 2014-02-20
Try Lightworks [http://lwks.com](http://lwks.com) used to edit films such as* Braveheart, King's Speech, Wolf of Wallstreet*. Available as deb file and tested on Ubuntu.

---

### Post by uwe-bungto on 2014-02-24
> **shaunthesheep said:**
> Try Lightworks [http://lwks.com](http://lwks.com) used to edit films such as* Braveheart, King's Speech, Wolf of Wallstreet*. Available as deb file and tested on Ubuntu.

I'll second that, it's also available on Windoze and soon on the Mac, so it is portable.

---

### Post by guraknugen on 2014-02-25
I'd say Lightworks too, even if I didn't try it myself. Why? Because it was only available in 64-bit, and I don't have hardware for that (yet). Maybe there is a 32-bit version available now, but I doubt it.
Lightworks will probably be open source in the future, but the main priority right now seems to be to make it available for other operating system than Windows. Last time I heard, it was available as deb and rpm, and I think it's tested on Ubuntu and Fedora. Next goal seems to be MacOS X.

---

