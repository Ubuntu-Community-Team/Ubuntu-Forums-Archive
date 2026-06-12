---
title: "does anyone know if the new nano works with linux?"
date: 2008-09-15
forum: The Cafe
---

### Post by markp1989 on 2008-09-15
i just ordered my self one of the new nanos, 16gb

has any one tried using it with ubuntu?

---

### Post by vanadium on 2008-09-15
nano still works for me. When I type "nano" at the prompt, it appears. Didn't know there was a new version, though :lolflag:

---

### Post by plb on 2008-09-15
Nope, but I wouldn't get my hopes up. Seems when all the new ipods are released, people around here always go out and buy them then have problems getting them to work under Linux. Maybe this won't be the case this time, but it does seem to be an ongoing trend at least for a couple of months.

---

### Post by swisscow on 2008-09-15
I have one of the new classics. Just plugged it in, job done. GTKPod and Amarok work fine.

---

### Post by god0fgod on 2008-09-15
> **vanadium said:**
> nano still works for me. When I type "nano" at the prompt, it appears. Didn't know there was a new version, though :lolflag:

lol Exactly what I was thinking.

---

### Post by markp1989 on 2008-09-26
my ipod nano 4th gen arrived to day (though it be specific so you smart asses dont make any nano text editor jokes, lol) 

tried to use gtkpod, but under ipod model it doesnt have the the ipod nano 4th generation listed.

any help?

thanks

---

### Post by picpak on 2008-09-26
> **swisscow said:**
> I have one of the new classics. Just plugged it in, job done. GTKPod and Amarok work fine.

Amarok took a little more work for me, but yes, they work great.

---

### Post by billgoldberg on 2008-09-26
> **markp1989 said:**
> i just ordered my self one of the new nanos, 16gb

has any one tried using it with ubuntu?

What the hell is a nano?

I presume you don't mean the text editor or the prefix meaning 10 to the -9th.

---

### Post by will1911a1 on 2008-09-26
Glad I'm not the only one who thought he was referring to the text editor.

---

### Post by sloggerkhan on 2008-09-26
I thought it was about the via processor at first.

---

### Post by myusername on 2008-09-26
the new ipod nanos were just released. your gonna have to wait a while if you want it to work with linux (if it does at all) just start going to ipod compatible music players websites (like amarok, gtkpod etc.) and see if they have any updates released (cause they probably aren't in the repos)

---

### Post by markp1989 on 2008-09-26
i can get rhythmbox and gtkpod to see the ipod, but its mounted readonly, any help?

---

### Post by SuperSonic4 on 2008-09-26
Can you get into it as user/root and change the permissions to read and write? Or just try deleting the iTunes lock file (or similar) in /media/iPod/iPod Control or something?

---

### Post by nick09 on 2008-09-26
Try Songbird with the Ipod addon. My 80GB 6th Gen Classic works great with the exception of album art; plus you can restore your ipod via Songbird and do not end up deleting the games that come with it.:)

---

### Post by markp1989 on 2008-09-26
> **SuperSonic4 said:**
> Can you get into it as user/root and change the permissions to read and write? Or just try deleting the iTunes lock file (or similar) in /media/iPod/iPod Control or something?

i tried runing pcmanfm as root, and then chenging permision, but it wont let me, 

i also tried a chown, and chmod, both as sudo, and still i get a permision denied warning!

---

### Post by zmjjmz on 2008-09-26
You should check what filesystem it's formatted as.
I bet they format it HFS+ initially, so you're going to need to take it to a Windows computer and reformat it fat32 (but you'd still need the appropriate iPod files, so you would need to use iTunes on Windows instead of just mkfs on Linux)

---

### Post by markp1989 on 2008-09-26
> **zmjjmz said:**
> You should check what filesystem it's formatted as.
I bet they format it HFS+ initially, so you're going to need to take it to a Windows computer and reformat it fat32 (but you'd still need the appropriate iPod files, so you would need to use iTunes on Windows instead of just mkfs on Linux)

i have already done that, i attached it to my sisters pc , so its  formated as FAT32

---

### Post by zmjjmz on 2008-09-26
> **markp1989 said:**
> i have already done that, i attached it to my sisters pc , so its  formated as FAT32

Try connecting it while it's in disk mode.
I think you can get it there by putting it on hold, then rebooting it, and while it's rebooting hold down select+play/stop.

---

### Post by ceb0 on 2008-10-01
Amarok worked (nearly) fine with my new nano.  I had to tell it that it was a 3rd gen though.  Only problem is that i have album artwork in cover flow, but not while the song is playing, and not scrolling at the bottom of the menu.  similar to [http://amarok.kde.org/forum/index.php/topic,15750.0.html](http://amarok.kde.org/forum/index.php/topic,15750.0.html)

I haven't had to plug it into a windows/mac box to set it up either - hopefully it will never have to go near a windows machine, let alone itunes.

---

