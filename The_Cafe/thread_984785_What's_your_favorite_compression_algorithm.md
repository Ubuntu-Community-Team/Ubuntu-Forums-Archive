---
title: "What's your favorite compression algorithm?"
date: 2008-11-17
forum: The Cafe
---

### Post by kevdog on 2008-11-17
For compressing files, I leaning towards using bzip2 more often. It combines very well with tar to make an encrypted tarred archive. I find it very confusing that bzip2 isn't installed by default, however maybe there is a specific reason for this?? 

I'm curious to know what others are using for compressing their files.  zip, gzip, 7-zip, or any others?

---

### Post by -grubby on 2008-11-17
Usually I use .zip since almost everyone can open it

---

### Post by cardinals_fan on 2008-11-17
7-zip is my favorite.

---

### Post by FuturePilot on 2008-11-17
I usually use gzip either by itself or along with tar. If I want something more robust I use 7zip.

---

### Post by kernelhaxor on 2008-11-17
my classes prefer tarballs .. so I do that for projects and assignments ..

otherwise I don't hav a favorite ..

---

### Post by Polygon on 2008-11-17
7z cause it has very good compression and open source, unlike rar

---

### Post by hessiess on 2008-11-17
7zip

---

### Post by swoll1980 on 2008-11-17
7-zip ftw

---

### Post by Vadi on 2008-11-17
7zip for windows people (because winzip sucks anyway, and people have to install some kind of dearchiver. Might as well be 7zip).

tar.bz2 on linux since support for that is built-in.

---

### Post by init1 on 2008-11-17
I usually use bzip or lzma

---

### Post by billgoldberg on 2008-11-17
7z, because it's better than the popular choices.

I don't know why people keep using rar or zip.

---

### Post by qazwsx on 2008-11-17
bz2

It is faster than 7z according to my experience (just my experience) and still very close when it comes to compression ratio and sometimes even better.

When *.debs are going to ditch internal gz compression?

---

### Post by Daveski on 2008-11-17
> **Vadi said:**
> 7zip for windows people ...

+1
7Zip is pretty cross-platform and it doesn't scare the Windows users.

---

### Post by snova on 2008-11-17
It is interesting to note the number of people in this thread that prefer 7zip...

Of which I am one. The compression is better, and I'm sick of the "one program for everything" tar/(gz/bz2) combination. 7z allows multiple compression algorithms anyway.

---

### Post by Sorivenul on 2008-11-17
Add another vote for 7z, though I still use tar(.gz/.bz2) a good deal of the time, mainly because it's how others still package their products.

---

### Post by Grant A. on 2008-11-17
7zip

---

### Post by gletob on 2008-11-17
JK>I hate compression .tar all the way<JK

But seriously I like 7z
----------------
Now playing: [Journey - Don't Stop Believin' (Album Version)](http://www.foxytunes.com/artist/journey/track/dont+stop+believin+(album+version))
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by namegame on 2008-11-17
Most of my class assignments are required to be submitted as .tar.gz. Since I'm the most familar with it, it is my favorite.

---

### Post by MaxIBoy on 2008-11-18
I use 7zip wherever I can, and Gzip wherever I have to. There's no need to use Zip, because Gzip is actually usable on any platform that matters. (By the way, I think all three use the same compression algorithm, the DEFLATE algorithm, but with different implementations.)

---

### Post by kevdog on 2008-11-18
How do you envoke 7z properly on the command line? and whats the deal with the encryption?

---

### Post by doorknob60 on 2008-11-18
7 zip and regular tar.gz, depending what I'm doing.

---

### Post by wmcbrine on 2008-11-18
My favorite compression algorithm is static Huffman, because it's the only one I wrote my own implementation of, besides RLE and similar trivial stuff.

My favorite compressed archive *format* to actually use is zip, followed by tar.gz. Others are too exotic (low userbase and/or wonky implementations) for not enough improvement.

---

### Post by tsali on 2008-11-18
I like my compressions algorithms to be a little trashy with heels and too much make-up...

---

### Post by Nepherte on 2008-11-18
> **wmcbrine said:**
> My favorite compression algorithm is static Huffman, [...]
My favorite compressed archive *format* [...]
I already wondered why it took so long.

I prefer tar.gz. Although tar.bz2 gives a better compression ratio, I find tar.gz to extract faster.

---

### Post by jdong on 2008-11-18
Depends what I'm shooting for. Just simple fast archiving like compressing before transferring over the 'net, I'll use tar.gz. bzip2 is better compressing but significantly slower to get in the way of convenience IMO.

For serious archiving where compression ratio counts, like backups, I use 7zip or its primary compression format, lzma, which has been default-installed in Ubuntu since Hardy or so.

---

### Post by ciscosurfer on 2008-11-18
> **kevdog said:**
> ...I'm curious to know what others are using for compressing their files.  zip, gzip, 7-zip, or any others?
It depends on what I want to compress.  More on that [here]("http://en.wikipedia.org/wiki/Data_compression").

> **kevdog said:**
> How do you envoke 7z properly on the command line? and whats the deal with the encryption?```
sudo apt-get install p7zip-full
man 7z
man 7za
```Regarding encryption, from [this page]("http://www.7-zip.org/7z.html"):
> 7-Zip also supports encryption with AES-256 algorithm.  This algorithm uses cipher key with length of 256 bits. To create that key 7-Zip  uses derivation function based on SHA-256 hash algorithm. A key derivation function produces a derived key from text password defined by user. For increasing the cost of exhaustive search for passwords 7-Zip uses big number  of iterations to produce cipher key from text password.> **jdong said:**
> ...For serious archiving where compression ratio counts, like backups, I use 7zip or its primary compression format, lzma, which has been default-installed in Ubuntu since Hardy or so.Curious, the man page and the wikipedia link (which probably takes its cues from the man page anyhow) state the following:

```
Backup and limitations
       DO NOT USE the 7-zip format for backup purpose on Linux/Unix because :
        - 7-zip does not store the owner/group of the file.

       On Linux/Unix, in order to backup directories you must use tar :
        - to backup a directory  : tar cf - directory | 7za a -si directory.tar.7z
        - to restore your backup : 7za x -so directory.tar.7z | tar xf -

       If you want to send  files  and  directories  (not  the  owner  of  file)  to  others
       Unix/MacOS/Windows users, you can use the 7-zip format.

         example : 7za a directory.7z  directory

       Do not use "-r" because this flag does not do what you think.

       Do  not use directory/* because of ".*" files (example : "directory/*" does not match
       "directory/.profile")
```The man page seems to contradict itself.  So, is the jury out on this one?

---

### Post by sirdilznik on 2008-11-18
Add me in to the 7zip crowd.

---

### Post by jdong on 2008-11-18
> **ciscosurfer said:**
> The man page seems to contradict itself.  So, is the jury out on this one?

It means do not use p7zip **alone** to back up a UNIX- style system because the archive format does not encapsulate all the info that a UNIX fs stores, such as ownership, permissions, etc. It then suggests first making a uncompressed .tar, then compressing that .tar in 7zip (it uses a pipe to do this in one go, but conceptually what I described is what's happening). This method is okay because the .tar format correctly represents UNIX crucial attributes and 7z is simply being used to compress the tar file.


If you want to do UNIX backups with 7zip type compression try the default-installed lzma command on recent Ubuntu systems. It is more or less the same LZMA algorithm minus a little bit of windows executable compacting magic, but the syntax is identical to gzip and bzip2's commands which makes it easier for a Linux/Unix guy to remember.

---

### Post by kevdog on 2008-11-19
How do you back up directories with lzma -- the man page is rather scant!

---

### Post by jdong on 2008-11-19
> **kevdog said:**
> How do you back up directories with lzma -- the man page is rather scant!

Well like gzip and bzip2, lzma operates on single files only. You are probably familiar with tar -c**z**vf foo.tar.gz /directory, but what you might not recall is that this is equivalent to:
```

tar -cvf - /directory | gzip > foo.tar.gz

```

Similarly for extraction instead of -xzvf, you can use

```

gzip -dc foo.tar.gz | tar -xvf -

```

This decompresses (-d) and outputs to stdout (-c) and pipes the result to tar, which reads from stdin (-)

Now, when I said lzma is just like gzip, I mean it. Replace everywhere you see gzip with lzma. Same parameters work :). The same applies for the bzip2 command. Now what was the 7zip stuff? 7za -a -si something something something? :)

---

### Post by kevdog on 2008-11-19
jdong

Good stuff

I don't usually invoke gzip like you stated, more like

tar czvf for gzip
tar cjvf for bzip2

Only if lzma Had such a simple interface??

---

### Post by jdong on 2008-11-19
> **kevdog said:**
> jdong

Good stuff

I don't usually invoke gzip like you stated, more like

tar czvf for gzip
tar cjvf for bzip2

Only if lzma Had such a simple interface??

That would require the patching of tar to link with the LZMA library. I believe there do exist patches for this, but we'd rather not make LZMA a requirement for tar at this point, not to mention mess with the codebase of such a critical and estabished tool like tar.

As I mentioned, yes, the -z and -j options are shortcuts for gzip and bzip2, but the command construct I gave is the equivalent -- it's basically what tar does internally when you tell it to use such tools.

---

