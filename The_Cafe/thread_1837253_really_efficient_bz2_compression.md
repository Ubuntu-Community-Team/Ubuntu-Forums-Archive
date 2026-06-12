---
title: "really efficient bz2 compression"
date: 2011-09-01
forum: The Cafe
---

### Post by chrisbay90 on 2011-09-01
Finished a tutorial excercise for Uni. Decided to compress and upload it to a remote server for safe keeping. Lazily compressed entire folder. Was shocked to see it compress 10.00mb -> 0.45mb

What is bz2 optimised for? I tested out various other algorithms and they all seemed to produce 4-5mb files.

I'll attach a sample for you to check out. Forgive the sloppy programming it is 2am local time and I coded it all at the last minute.

---

### Post by sffvba[e0rt on 2011-09-01
I often smiley when I am using apt-get or pacman or what ever terminal application to install/upgrade and I see the size of the download vs the size that will be used on disc... It is awesome :D


404

PS - I think I can see it in apt-get too... could be mistaken... but pacman in frugalware does give the info and it is insane how  optimized it is :)

---

### Post by jerenept on 2011-09-01
Text files are usually quite compressible. I downloaded a 4GB RAR file that contained a 13 GB text file.

---

### Post by donkyhotay on 2011-09-01
> **chrisbay90 said:**
> What is bz2 optimised for? I tested out various other algorithms and they all seemed to produce 4-5mb files.


[url=http://en.wikipedia.org/wiki/Bz2]
I'm certain the answer can be found here.[/url]

---

### Post by chrisbay90 on 2011-09-01
> **not found said:**
> I often smiley when I am using apt-get or  pacman or what ever terminal application to install/upgrade and I see  the size of the download vs the size that will be used on disc... It is  awesome :grin:
 
 
 404
 
 PS - I think I can see it in apt-get too... could be mistaken... but  pacman in frugalware does give the info and it is insane how  optimized  it is :smile:
 
 As do I.
 
> **jerenept said:**
> Text files are usually quite compressible. I  downloaded a 4GB RAR file that contained a 13 GB text file.

That they are. What is surprising is the varience in compression from method to method. Seems theres is a variation of 40k-40000k
There is one very big 9.2mb text file with about 20-30k of repeating text. It should shrink dramatically, however most of the compression methods don't seem to handle it so well, while some do.

> **donkyhotay said:**
> [URL="http://en.wikipedia.org/wiki/Bz2"]
I'm certain the answer can be found here.[/URL]

Looks interesting.

```

ls -l
total 17264
-rw-r--r-- 1 chris chris 4261933 2011-09-02 11:40 C (2).cbz
-rw-r--r-- 1 chris chris 4261933 2011-09-02 11:40 C (2).jar
-rw-r--r-- 1 chris chris  503272 2011-09-02 11:40 C (2).tar.bz2
-rw-r--r-- 1 chris chris 4232562 2011-09-02 11:40 C (2).tar.gz
-rw-r--r-- 1 chris chris   42409 2011-09-02 11:40 C (2).tar.lzma
-rw-r--r-- 1 chris chris   42512 2011-09-02 11:41 C (2).tar.xz
-rw-r--r-- 1 chris chris 4261933 2011-09-02 11:41 C (2).zip

```

---

### Post by sffvba[e0rt on 2011-09-01
lzma seems to be very good at what it does...


404

---

### Post by FuturePilot on 2011-09-01
> **not found said:**
> lzma seems to be very good at what it does...


404

lzma is deprecated. xz is the replacement.

---

### Post by sffvba[e0rt on 2011-09-01
> **FuturePilot said:**
> lzma is deprecated. xz is the replacement.

Oh dear... I didn't know... been reading up on it after this thread to see if it is possible to get a comparison of the efficiency of the different formats and nowhere was this mentioned...


404

---

### Post by NightwishFan on 2011-09-01
xz is my favourite for pretty much everything but I might switch to bz2 because some programs offer support for opening .bz2 compressed files without me decompressing. Plus there is a program called pbzip2 for multi-threaded compressing.

---

