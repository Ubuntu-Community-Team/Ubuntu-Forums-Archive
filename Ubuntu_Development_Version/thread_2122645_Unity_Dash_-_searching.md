---
title: "Unity Dash - searching"
date: 2013-03-05
forum: Ubuntu Development Version
---

### Post by Budovi on 2013-03-05
Have anyone noticed this bug? It has to be caused by recent updates.

Ubuntu Unity Dash search is really unusable now. It can search by most used apps but it have to be relevant. Prioritizing = OK, this is mess.

For example, lets search GIMP:

g: Home Folder > Text Editor > VLC media player > Files > GIMP Image Editor > Software & Updates > GParted Partition Editor ....
gi: Firefox > Home Folder > Text Editor > Code::Blocks IDE > VLC media player > Rhytmbox Music Player > Files ....
gim: Firefox > Home Folder > Empathy Internet Messaging > Files > Archive Manager > GIMP Image Editor > Image Viewer ....
gimp: Home Folder > Files > GIMP Image Editor > Unity Tweak Tool > Time & Date > Simple Scan ....

REALLY?

Considering raising bug against this... It is really crappy, before it was just like two letters and enter, now??! Whole "GIMP Image Editor" do not cause to be GIMP at first place.

Btw: Old bug about internet connection makes me mad because this is maybe 5th post I had to completely rewrite, because resending request just clean up editor instead posting topic / post.

---

### Post by ventrical on 2013-03-05
Your right. I put in scr for 'screenshot' and I get everything else but!!

File a bug and I'll second it.

---

### Post by mc4man on 2013-03-05
It is just as you say - g gets gimp in the row, then it's gone until gimp (but still back in row
I guess there are more important things afoot.. (nexus7, rolling, mir, whatever.

---

### Post by Budovi on 2013-03-05
Ok, did not find this bug reported (yes, but resolved 3 years ago :D ) so here it is:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1148183](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1148183)

---

### Post by tjeremiah on 2013-03-05
i like to be able to search for pictures in my picture folder using the picture lens :o  or type in a file name and it appears without me having to preload it first (if I dont open it in the folder first, it doesnt show in the dash). I'm with you on this one. Dash needs better searching.

---

### Post by ventrical on 2013-03-06
> **Budovi said:**
> Ok, did not find this bug reported (yes, but resolved 3 years ago :D ) so here it is:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1148183](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1148183)


+1 click!

but appears only to affect 32bit as my 64bit installs are working correctly.

---

### Post by Budovi on 2013-03-06
I'm using 64bit version :)

---

### Post by alphacrucis2 on 2013-03-06
> **ventrical said:**
> Your right. I put in scr for 'screenshot' and I get everything else but!!

File a bug and I'll second it.

Curious. scre does work for screenshot but also shows scribus, kate and xterm. Weird. 64 bit here

---

### Post by castrojo on 2013-03-06
> **Budovi said:**
> Considering raising bug against this... It is really crappy, before it was just like two letters and enter, now??! Whole "GIMP Image Editor" do not cause to be GIMP at first place.

Please report bugs on this, it's likely libcolumbus landing and maybe? being broken: [http://www.iloveubuntu.net/error-tolerant-exciting-libcolumbus-library-landed-raring-default](http://www.iloveubuntu.net/error-tolerant-exciting-libcolumbus-library-landed-raring-default)

---

### Post by suolakurkku on 2013-03-06
I just did a fresh install of Ubuntu 13.04 (64-bit) from the daily image. Everything else seems to be working fine except Unity Dash. It seems to be stuck at "searching" and the bottom icons (lenses or whatever) seem to be missing. Other Unity features like HUD and the launcher work just fine. Even the social Dash responds to input as it should. Has anyone else had these problems with the Dash? Or just happen to know a solution for this?

Here's some screenshot's to illustrate the problem:
Dash Home (no input) [http://imgur.com/0xSyM6E](http://imgur.com/0xSyM6E)
Dash Home (with input) [http://imgur.com/mpvU7R9](http://imgur.com/mpvU7R9)
Dash Social (with input) [http://imgur.com/AvEyF56](http://imgur.com/AvEyF56)

Thanks!

EDIT: Solved the problem myself. Apparently I didn't have any lenses installed . I had to install them manually o_O. What a weird bug.

---

### Post by mcellius on 2013-03-06
I was having the same problems, but the updates I just grabbed seem to have fixed the problem.  (You may have to logout or restart.)

---

### Post by mcellius on 2013-03-06
The latest updates - I just updated - seem to have fixed this problem for me.

---

### Post by celluloid on 2013-03-06
This is definitely libcolumbus causing issues.
I was seeing this issue with "skype" - however I can confirm updating about an hour ago seems to fix it.
The "fuzzy" searching with typos is really good now :)

---

### Post by Budovi on 2013-03-06
I changed status on launchpad to Fix Released.

---

### Post by cariboo on 2013-03-06
Merged two similar threads.

---

