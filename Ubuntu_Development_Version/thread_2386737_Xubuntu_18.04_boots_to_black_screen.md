---
title: "Xubuntu 18.04 boots to black screen"
date: 2018-03-09
forum: Ubuntu Development Version
---

### Post by rattskjelke on 2018-03-09
Well I thought I would try Xubuntu 18.04 beta on a live USB but it won't boot to the desktop.

This is on an old HP Pavilion g7. It has an AMD A4 and Radeon.

It boots enough to check the media and shows no errors but the "try without installing" mode won't get all the way to the desktop.
I get a black screen with a slightly lighter bar across the top, that might be an empty Xfce panel, and no mouse cursor.
I tried the usual boot paramaters for fixing black screen like nomodeset and but nothing helps. 
I can Ctrl-Alt-F1 to the terminal but then I don't know what to check for.

---

### Post by flocculant on 2018-03-09
We appear to have an issue that makes getting to the desktop a long wait - how long did you wait?

---

### Post by kerry_s on 2018-03-09
yeah, start up is slow for live. i have a hp pavilion g6, but mines intel.

---

### Post by rattskjelke on 2018-03-09
I waited about 2 or 3 minutes and nothing. Then I booted it again and left for about 20 minutes and when I came back I had the desktop. I didn't time it to see exactly how long it takes.

Does it take that long when installed or is it just the live image?

---

### Post by kerry_s on 2018-03-09
> **rattskjelke said:**
> I waited about 2 or 3 minutes and nothing. Then I booted it again and left for about 20 minutes and when I came back I had the desktop. I didn't time it to see exactly how long it takes.

Does it take that long when installed or is it just the live image?

i have it in vm & it still seems like it takes a long time, i have the xubuntu core version.
just go for it. ;)

---

### Post by flocculant on 2018-03-10
> **rattskjelke said:**
> I waited about 2 or 3 minutes and nothing. Then I booted it again and left for about 20 minutes and when I came back I had the desktop. I didn't time it to see exactly how long it takes.

Does it take that long when installed or is it just the live image?

What we've seen is that the first boot takes some time - penultimate boots are fine.

---

### Post by flocculant on 2018-03-10
This is possibly an issue with bluez activating service [lpbug]1754836[/lpbug]

That's causing a 75s wait.

---

### Post by #&amp;thj^% on 2018-03-10
> **flocculant said:**
> This is possibly an issue with bluez activating service [lpbug]1754836[/lpbug]

That's causing a 75s wait.

I noticed that also I just disabled the whole shebang "service 'org.bluez' ", and that was after just a brief delay from the live installer to a desktop.
But I also confess that I  have not tried to restart "bluez.service" yet.

---

### Post by flocculant on 2018-04-11
This appeared to be an issue with fontconfig - new fixed release recently - not seeing the slow boot to live nor on first login post install.

---

### Post by VMC on 2018-04-11
> **1fallen said:**
> I noticed that also I just disabled the whole shebang "service 'org.bluez' ", and that was after just a brief delay from the live installer to a desktop.
But I also confess that I  have not tried to restart "bluez.service" yet.

I have no need no bluez anything. I need to check logs looking for 'bluzes' to see for myself. I never thought of using 'org.bluez'. Good idea.

---

### Post by Yellow Pasque on 2018-04-11
If you have no need for bluetooth, you should probably just uninstall bluez/blueman/pulseaudio-module-bluetooth packages

---

### Post by flocculant on 2018-04-12
> **Temüjin said:**
> If you have no need for bluetooth, you should probably just uninstall bluez/blueman/pulseaudio-module-bluetooth packages

Is what I do indeed.

---

