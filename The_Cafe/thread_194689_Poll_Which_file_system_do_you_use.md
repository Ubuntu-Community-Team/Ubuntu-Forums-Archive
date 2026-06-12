---
title: "Poll: Which file system do you use"
date: 2006-06-11
forum: The Cafe
---

### Post by disturbed1 on 2006-06-11
I use JFS because it works the best for me.

I don't use ReiserFS because it seems to only work the best with many small files, EXT2/3 are too slow, and XFS.....I haven't read enough about it.

---

### Post by John.Michael.Kane on 2006-06-11
I use ext2 no swap.

---

### Post by tribaal on 2006-06-11
Hum... no ReiserFS option?

ext3 then...

- trib'

---

### Post by disturbed1 on 2006-06-11
[quote=tribaal]Hum... no ReiserFS option?

ext3 then...

- trib'[/quote] 
Ooops anyway to add that in?

---

### Post by benuski on 2006-06-11
I'm too lazy to change from the Ubuntu default, so i use Ext3... I would think about using XFS but it doesn't work with GRUB.  And also I use FAT32 from all of my media, mp3/ogg and the like, so I can give it to my friends, work it on my windows partition, etc.

---

### Post by briancurtin on 2006-06-11
reiser since you didnt make an option for it.

---

### Post by Rhapsody on 2006-06-11
ext3. I considered ReiserFS and XFS, but I went with ext3 since it was my first time on Linux, and everyone else was using it. I may give XFS (or Reiser4 when it's finished) a try in the future.

---

### Post by Sheinar on 2006-06-11
ReiserFS here.

---

### Post by andrecasteliano on 2006-06-11
ReiserFS

---

### Post by fluffington on 2006-06-11
EXT3, 'cause it's the default, and I don't know enough about the differences to have an opinion on the subject.

---

### Post by Lucho on 2006-06-11
For Ubuntu, I use reiserfs. It was recomended to me by the developer of
the Brazilian distro Kurumin, and well, it works. I figure that if it can take
my noob abuse, it´s a good file system.
      On the other hand, with Debian Etch, I decided to experiment a little:
Jfs for my root partition, and Xfs for my home partition. I work with video
editing, so I was curious about Xfs, and I wanted to see if Jfs´ lower CPU
usage could impact system performance. The result? Performance, as
might be expected, doesn´t measurably change, but everything *feels*
snappier and more responsive. 
              But then again, Debian Sarge/Etch *always* outperformed 
Breezy/Dapper, at least on my machine.

---

### Post by disturbed1 on 2006-06-11
That's why I use JFS, lower CPU usage, quicker to copy from drive a to drive a, and from drive a to drive b, faster boot time too since it doesn't take as long to initialize. I've used XFS in the past (3 or so years ago), but at that time it just wasn't stable enough. I actually lost a bit of data due to the way it journals, but that has all been improved since then. I remember the first time I used XFS, I forgot about GRUB not being able to boot to XFS and didn't make a small /boot partition in EXT3 ](*,)

ReiserFS has just always been a dog on my systems. Even EXT2/3 out perform Reiser. But then again, Reiser was went for servers that have loads and loads of small files.

Here's a good benchmark article.
[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

---

### Post by BoyOfDestiny on 2006-06-11
reiserfs

---

### Post by warp99 on 2006-06-12
ReiserFS. :D

---

