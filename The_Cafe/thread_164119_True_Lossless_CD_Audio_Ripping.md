---
title: "True Lossless CD Audio Ripping?"
date: 2006-04-22
forum: The Cafe
---

### Post by benbruscella on 2006-04-22
Is it actually possible to have lossless CD Audio Ripping?  If so, could someone please let me know what I am doing wrong here?  

**Step 1 - "ID the original CD disc ID"**
```

cd-discid /dev/cdrom
a00b2a0e 14 150 16830 34092 47540 56385 76782 89420 101355 114730 127330 150755 165475 177730 195192 2860

```


**Step 2 - "Rip Entire CD from command line"**
```

cdparanoia -B 1-14 
ls -al
-rwxrwxrwx 1 root root  39231404 2006-04-22 19:39 track01.cdda.wav
-rwxrwxrwx 1 root root  40600268 2006-04-22 19:41 track02.cdda.wav
-rwxrwxrwx 1 root root  31629740 2006-04-22 19:42 track03.cdda.wav
-rwxrwxrwx 1 root root  20803484 2006-04-22 19:43 track04.cdda.wav
-rwxrwxrwx 1 root root  47973788 2006-04-22 19:45 track05.cdda.wav
-rwxrwxrwx 1 root root  29724620 2006-04-22 19:46 track06.cdda.wav
-rwxrwxrwx 1 root root  28071164 2006-04-22 19:47 track07.cdda.wav
-rwxrwxrwx 1 root root  31458044 2006-04-22 19:49 track08.cdda.wav
-rwxrwxrwx 1 root root  29635244 2006-04-22 19:51 track09.cdda.wav
-rwxrwxrwx 1 root root  55095644 2006-04-22 19:55 track10.cdda.wav
-rwxrwxrwx 1 root root  34621484 2006-04-22 19:57 track11.cdda.wav
-rwxrwxrwx 1 root root  28823804 2006-04-22 19:59 track12.cdda.wav
-rwxrwxrwx 1 root root  41070668 2006-04-22 20:02 track13.cdda.wav
-rwxrwxrwx 1 root root  45570044 2006-04-22 20:05 track14.cdda.wav

```

**Step 3 - "Create Audio CD from wav's using k3B"**

**Step 4 - "ID the backup CD"**
```

cd-discid /dev/cdrom
a00b2a0e 14 150 16830 34092 47540 56385 76782 89420 101355 114730 127330 150755 165475 177730 195192 2860

```

At this point, everything looks great!  The disc ID is correct, it is recognised by all audio players, so I was reasonably happy.  However, I wrongly assumed that if I ripped track 1 again from the backup CD, the data would be exactly the same:

**Rip Track 01 again Using CDParanoia"**
```

cdparanoia 1
ls -al
-rwxrwxrwx 1 root root 39231404 2006-04-22 20:47 cdda.wav

```

The file size of the backup CD track 1 rip is the same as the original CD track 1 rip, which is cool!  

So, why would the md5sum be different?

**md5sum the original CD track rip**
```

md5sum track01.cdda.wav
de0804b91f726669b7d223d73f7e1627  track01.cdda.wav

```

**md5sum the backup CD track rip**
```

md5sum cdda.wav
251dc9938d71f0ef142af3e12f5c815b  cdda.wav

```

What am I doing wrong?

Is md5sum the correct way to compare the data in these 2 files?  

What is the procedure for true lossless audio ripping? :)

---

### Post by benbruscella on 2006-04-22
After some more reading, I used shntool for comparison..

Original:
```

shntool len track01.cdda.wav
    length     expanded size   cdr  WAVE problems filename
     3:42.30       39231404    ---   --   -----   ../track01.cdda.wav
     3:42.30       39231404 B                     (total for 1 file, 1.0000 overall compression ratio)

```

Backup:
```

shntool len cdda.wav
    length     expanded size   cdr  WAVE problems filename
     3:42.30       39231404    ---   --   -----   cdda.wav
     3:42.30       39231404 B                     (total for 1 file, 1.0000 overall compression ratio)

```

Original:
```

shntool md5 track01.cdda.wav
9d71eb30836bbc60a3b875c26363fff8  [shntool]  ../track01.cdda.wav

```

Backup:
```

shntool md5 cdda.wav
3fcf8443cbee5df26958973a5aa50ec9  [shntool]  cdda.wav

```

Gotta go read some more...

---

### Post by PsychoTrauma on 2006-04-22
I dont think true lossless ripping is possible with linux atm, possibly using wine and eac (exact audio copy) would work but i'm not sure. There is variables you need to take into account such as the read offset of your drive. You'll probably be interested in [this]("http://www.hydrogenaudio.org/forums/index.php") forum since they have a very active lossless croud.

---

### Post by Kimm on 2006-04-22
I'm pretty sure Banshee can rip CD's to flac, which is a lossless codec

---

### Post by PsychoTrauma on 2006-04-22
I might be reading too much into what the op wanted but what I took from the post was he wanted a exact backup of his music. This is not possible with banshee because it doesn't take into account silence between tracks and the read and write offset of the drive doing the ripping and burning. So the file may sound exactly the same but the md5sum would be different and it wouldn't be a exact copy. Not to mention banshee adds a two second gap between each track.

As far as I know there is only two programs that can do a exact rip one is eac (windows only) and plextools (also windows only and only works with plextor drives).

---

### Post by Kvark on 2006-04-22
If you want an *exact* copy of a CD then burn directly from one disk to the other or make an .iso image and burn from that. In some cases I think you must use something like [CloneCD]("http://www.slysoft.com/en/clonecd.html") to get an *exact* result. But I don't know of any linux alternative(haven't looked for it) and it is illegal in some countries because it can clone copy protected disks too.

But if all you want is true lossless audio ripping then use the flac format, it's lossless.

---

### Post by PsychoTrauma on 2006-04-22
It seems there is someone writing a nice exact audio copy like program for linux. Might be of interest to the OP.  The link to the forum post is [here]("http://www.hydrogenaudio.org/forums/index.php?showtopic=38418&hl=linux").

---

### Post by The Soundophiliac on 2006-04-22
I think grip uses cdparanoia to rip audio. Cdparanoia is a library or something for just your needs and from what I read from their website ([http://www.xiph.org/paranoia/)](http://www.xiph.org/paranoia/)), it seems that it does just about everything software can do to insure an exact rip. Grip is a nice one altogether.

---

### Post by PsychoTrauma on 2006-04-22
The problem with cdparanoia is it's next to useless on a drive that caches (which is most modern drives). It's useless because it will read the cache instead of the cd when comparing files in paranoid mode.

---

