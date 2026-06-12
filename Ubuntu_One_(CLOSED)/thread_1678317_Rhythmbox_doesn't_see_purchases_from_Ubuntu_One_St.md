---
title: "Rhythmbox doesn't see purchases from Ubuntu One Store."
date: 2011-01-30
forum: Ubuntu One (CLOSED)
---

### Post by adrian.ratnapala on 2011-01-30
How to I get Rhythmbox see music I bought from the Ubuntu One store?  I am using Maverick on an amd64.  Read on for the context of this question. 

I am not sure if this forum is the right place to complain about bugs and misfeatures, but the Ubuntu One Music store is an almost-working service that looks completely broken.  I'll explain my own problem, but it is related to 
[LIST]
[*] this thread [http://ubuntuforums.org/showthread.php?t=1641616](http://ubuntuforums.org/showthread.php?t=1641616)
[*] and this thread [http://ubuntuforums.org/showthread.php?t=1633322](http://ubuntuforums.org/showthread.php?t=1633322).
[/LIST]

1) If I use Rhythmbox to pay money for a song, the payment happens but the download appears to fail (0% downloaded for *hours*).

2) I accidentally find that the songs actually have appeared in my Ubuntu One storage under "Purchased Music".  No clue how to get them into my local FS or to Rhythmbox, except by manually downloading each file.

3) I find out that they actually are on my local system but hidden!  (In ".ubuntuone/Purchased from Ubuntu One").

4) This directory is so obscure that even Rhythmbox can't find it.  If I restart the player, there is no sign of the songs in my Library, and if I got to "My Downloads" in the UbuntuOne store, it just says "Transferring to your Ubuntu One storage".

5) I can't even navigate manually within Rhythmbox to the hidden directory.  I have to actually symlink it to some non-hidden name and then navigate.  

Now I love a good symlink, but this is hardly a slick user experience.  I think every step 1-5 represents a distinct bug or misfeature.

Cheers.

---

### Post by ahkond on 2011-02-17
For me it's worse; my purchased songs do not appear in my ~/.ubuntuone/Purchased from Ubuntu One folder.  That folder is empty.  

Apparently I just wasted $33 on music I will not be able to play.  Thanks ubuntu!

---

### Post by howefield on 2011-02-17
Thread moved to *"Ubuntu One"* forum.

---

### Post by ahkond on 2011-02-17
Update: 24 hours later my songs have appeared in Rhythmbox, for no apparent reason.  I took no further steps. Maybe it simply takes 1 day for songs to appear.  

???

---

### Post by Aikar on 2011-03-12
Ok I just learned about a weird quirk...

they download to ~/.ubuntuone/Purchased From Ubuntu One/
but Rythymbox looks for them in ~/.local/share/ubuntuone/Purchased From Ubuntu One/

So I simply moved my files to diff location (HDD) and made both locations a symlink
[Tyrial] ------ [10:04 AM] ------ [aikar] ------ [~/.ubuntuone]
>>> ls -l
total 8.0K
drwxr-xr-x  2 aikar aikar 4.0K 2011-03-12 10:04 ./
drwxr-xr-x 65 aikar aikar 4.0K 2011-03-11 23:58 ../
lrwxrwxrwx  1 aikar aikar   32 2011-03-12 10:04 Purchased\ from\ Ubuntu\ One -> /media/altmedia/Music/UbuntuOne//

---

