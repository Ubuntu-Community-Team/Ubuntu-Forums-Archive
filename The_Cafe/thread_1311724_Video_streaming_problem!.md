---
title: "Video streaming problem!"
date: 2009-11-02
forum: The Cafe
---

### Post by Blacklightbulb on 2009-11-02
Help urgent!

Whenever I'm using youtube or megavideo the video streams (in youtube) but I can't use the controls. I can't pause it, rewind, forward...etc nothing works.

It's not a plugin clash. I already tried the firefox optimization thread!

I'm using Ubuntu 64bit btw and the Adobe alpha flash player 10.

---

### Post by Blacklightbulb on 2009-11-02
It's ain't urgent no more. Using wine + windows firefox but I'd like to solve the problem so if anyone will please, Thanks! :D

---

### Post by NoaHall on 2009-11-02
Hm. Try opening a new tab while the video is open, move to the new tab, then switch back to the one with the video, see if you can use it.

---

### Post by Blacklightbulb on 2009-11-02
> **NoaHall said:**
> Hm. Try opening a new tab while the video is open, move to the new tab, then switch back to the one with the video, see if you can use it.

No unfortunately doesn't work.

Now even with wine some video streaming features such a maximizing the screen don't work :(

Also perhaps useful. Once I try to modify flash settings by right clicking the video the pop up window freezes along with the video.

---

### Post by Blacklightbulb on 2009-11-02
On further analysis I think it has something to do with the point being stuck in another frame from the control frame if you get what I mean.

---

### Post by Excedio on 2009-11-02
I too am having this problem. I am running the same version of Adobe as well.

---

### Post by Blacklightbulb on 2009-11-02
> **Excedio said:**
> I too am having this problem. I am running the same version of Adobe as well.

Problem solved:

Follow these steps:
1. Download adobe flash 10 player from adobe labs.
2. Go into synapic and completely remove flash plugin non-free.
3. Extract the downloaded plugin and move it to /usr/lib/mozilla/plugins using sudo mv ot whatever.
4. Reboot

THREAD SOLVED!
Thanks Everyone!

---

### Post by Excedio on 2009-11-02
Awesome...i'll give it a shot when I get home. :-)

---

### Post by HappyFeet on 2009-11-02
> **Blacklightbulb said:**
> Problem solved:

Follow these steps:
1. Download adobe flash 10 player from adobe labs.
2. Go into synapic and completely remove flash plugin non-free.
3. Extract the downloaded plugin and move it to /usr/lib/mozilla/plugins using sudo mv ot whatever.
4. Reboot

THREAD SOLVED!
Thanks Everyone!
Use the [64bit]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") flash plugin if you are using 64bit ubuntu. Just put the extracted file into /usr/lib64/mozilla/plugins.

---

### Post by Excedio on 2009-11-02
Not working for me...*sigh*

Should I also remove flashplugin-installer?

---

