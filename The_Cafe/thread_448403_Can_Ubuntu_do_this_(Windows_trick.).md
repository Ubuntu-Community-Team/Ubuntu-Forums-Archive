---
title: "Can Ubuntu do this (Windows trick.)"
date: 2007-05-19
forum: The Cafe
---

### Post by Sunnz on 2007-05-19
Hides files in a picture:

[http://www.youtube.com/watch?v=q6AQL55zMR4](http://www.youtube.com/watch?v=q6AQL55zMR4)

I was thinking, this trick might fail if the offending picture is opened on a Linux environment... but I don't have a Windows box to test it now...

But would something like cat hidden.tar.gz >> picture.jpg do?

---

### Post by CarpKing on 2007-05-19
Yes, it most definitely can.  

```
cat picturefile.jpg rarfile.rar > newfilethatisNOTtherarfileorpicturefile.jpg
```

I've seen hidden .zip files as well; other archive formats probably work too.

---

### Post by tomaszx on 2007-05-19
Ok. it's work but how can I recovery the file from image? :)

---

### Post by Sunnz on 2007-05-19
Wow, you know, it works with pdf as well!!!

```
cat mul_ing.pdf Archive.zip >> test.pdf
```

tomaszx:
```
unzip secret.jpg
```

or use unrar, gunzip, bunzip2, or tar xf, depends on what compression you use.

---

### Post by pmj on 2007-05-19
Heh, I didn't realize that you could use the command line tools to get the hidden files out. Since file-roller refused to open them, I wrote a script for it.

These hidden files are very popular on some websites, but I guess this "trick" is kind of useless for those that don't visit them.

---

### Post by DoctorMO on 2007-05-19
> something like 'tar' something bazaar

Tar isn't a compression format it's an encapsulation format for multiple files. that is why we use the compression bz2, gzip or one of the many other compression tools but they all use tar (stands for tape backup)

---

### Post by CarpKing on 2007-05-19
File Roller opens them fine, too.  You just have to change the file extension to whatever archive format you have, and open it with right click --> Open with "Archive Manager."

---

### Post by Mateo on 2007-05-19
I don't understand how this works.  this is what I did:

```
cat sample.txt video.mpg > mypicture.jpg
```

but the picure stopped working, nor could I open it in file-roller.  i'm not understanding how this works i think.

---

### Post by PhatStreet on 2007-05-19
> **Mateo said:**
> I don't understand how this works.  this is what I did:

```
cat sample.txt video.mpg > mypicture.jpg
```

but the picure stopped working, nor could I open it in file-roller.  i'm not understanding how this works i think.
From the video description:
> This works by copying the compressed file in binary mode onto the end of the jpeg images. When the picture is opened, the jpg header says the length of the data and ignores everything below (the hidden zip file). When the compression software like 7-zip opens the picture it looks for compatible compression headers and starts reading the file where-ever those begin.
So you have to start with a JPG and copy to a JPG. Apparently Sunnz got it to work with a PDF as well.

Nice trick. :D

---

### Post by reyfer on 2007-05-19
I'm not sure, but isn't this what Steganography is all about? And there are programs for Linux that do it, like Steghide [http://steghide.sourceforge.net/index.php](http://steghide.sourceforge.net/index.php)  and Stego [http://octave-gtk.sourceforge.net/stego/](http://octave-gtk.sourceforge.net/stego/)

---

### Post by FuturePilot on 2007-05-19
> **Mateo said:**
> I don't understand how this works.  this is what I did:

```
cat sample.txt video.mpg > mypicture.jpg
```

but the picure stopped working, nor could I open it in file-roller.  i'm not understanding how this works i think.

You have to do ```
unzip file_name_here.mpg
```or .jpg or what ever you hid them in.
You should get something like this
```
$unzip '/home/nick/Desktop/Not_what_it_looks_like.jpg' 
Archive:  /home/nick/Desktop/Not_what_it_looks_like.jpg
warning [/home/nick/Desktop/Not_what_it_looks_like.jpg]:  55455 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: SoundNotes.ppt          
  inflating: gdb-gnome-theme-manager.txt  
  inflating: gdb-f-spot.txt          

```

Hehe this is cool. Basically steganography

---

### Post by JT673 on 2007-05-19
Wow, I had no idea!

...Shell script time :)...

---

### Post by reyfer on 2007-05-20
Check Synaptic Package Manager, Ubuntu has Steganography tools on its repositories, you have Outguess, Stegdetect, Steghide and Xsteg.

---

