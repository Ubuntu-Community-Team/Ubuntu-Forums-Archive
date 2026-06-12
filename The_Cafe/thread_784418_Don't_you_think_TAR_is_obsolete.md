---
title: "Don't you think TAR is obsolete?"
date: 2008-05-06
forum: The Cafe
---

### Post by descentspb on 2008-05-06
Well, it does the archiving job, but it takes very long time to just view the contents! That's not normal for an archiver, cause i have very large tars of my backups and i should wait for a couple of minutes to just view the contents and choose what i need to restore.

Please, share your opinion about how this can be solved. Thanks.

P.S. bz2 and gz are great, no questions to them.

---

### Post by StOoZ on 2008-05-06
if its aint broken,dont fix it.
I dont have any issues with tar files.

---

### Post by descentspb on 2008-05-06
I think you misunderstood me. I believe that the tar architecture was introduced long ago when everyone was using tapes for storage. Since that time, you should read the whole tar file to be able to view all its contents. Maybe i'm not right, but i'm looking for an answer.

---

### Post by ASULutzy on 2008-05-06
tar does something entirely different than bz2 and gz, hence why they are used in combination.

tar simply archives files, it does not compress them. Tar is used to take a whole bunch of files and stick them into one big file. After that is done the file is compressed using some compression algorithm, like bz2 or gz. So to say that tar is obsoleted because of bz2 or gz doesn't make much sense.

Though that does beg the question, why can't we all just use .7z? It's open source, and it does both archiving and compression. I can't think of a reason off the top of my head, but maybe someone else on the forums can.

---

### Post by ASULutzy on 2008-05-06
Oh, I found the answer.

7z does not preserve the owner/group of the file like tar does. Guess that's why we still use tar!

edit: And if you are looking for the reason why it takes so long to open a large .tar.bz2 or .tar.gz file, it's because (as my friend explained to me) the metadata is stored along with each file, and because tar is wrapped inside bzip2 or gzip, the metadata is compressed as well, and you have to decompress the whole archive to read the metadata or to read a single member, or whatever. He went on to contrast that to .zip, on the opposite end of the spectrum you have ZIP, which not only stores the metadata separately, it also compresses each file independently so you can read a single file out of a ZIP archive without having anything to do with the others. Just read the position and length out of the header, seek, and start decompressing But because every file is compressed independently, the compression ratio isn't as good as it could be

I'm not smart enough to explain things, but he was ;)

---

### Post by descentspb on 2008-05-06
yes, sure, it does not do any compression, but i'm not talking about compression. Tar is great in all its functionality, but when you open a large tar file through the archive manager, you should wait till the system reads all the file to be able to look through the contents. Even in the obsolete zip you can view the contents quickly.

---

### Post by descentspb on 2008-05-06
ok, we have the reason. And noone is going to fix this, isn't he? :) Are we going to live with tape-like tar archives in the XXI century? Maybe the developers should just add an option to tar (which is almost used with -j or -z options for compression) to make this not to happen?

---

### Post by ASULutzy on 2008-05-06
Perhaps the compression ratio is the driving factor here, where .tar.bz2 or .tar.gz wins out over .zip?

---

### Post by descentspb on 2008-05-06
maybe, but an ability to bypass that would be very handy. I don't really need very high compression ratios in my case, and if the resulting 1 GB file would be a couple of megs larger, but would open instantly i would be happy :)

---

### Post by riven0 on 2008-05-06
If I'm not mistaken, you're asking to view the contents of the tar quickly. In that case wouldn't going through the terminal be faster, like doing: **tar tzvf archive.tar.gz | less**? Or am I completely missing the question here???

---

### Post by Kingsley on 2008-05-06
How can tar be obsolete? New updates come out for it every year.

---

### Post by billgoldberg on 2008-05-06
Tar is great.

But if I need to archive files, I like to compress them while I'm at it.

And from what I've heard .7z is the best at that for the moment.

---

### Post by insane_alien on 2008-05-06
tars sole purpose: to bodge files together into one and maintain permissions.

job done. 

how can it be obsolete if it performs its sole function perfectly?

---

### Post by descentspb on 2008-05-06
that's not faster, that't the same (if not slower) in speed. I have tared my whole /home directory and that's a huge amount of files and data. It takes tar a couple of minutes to list its contents even in the console.

---

### Post by ASULutzy on 2008-05-06
I was under the impression that he meant grabbing a single file out of the tar.gz or .tar.bz2 without decompressing all of it... Sort of like what you can do with a .zip file

---

### Post by gsmanners on 2008-05-06
Slow and obsolete are two different problems. If you need a listing for a large archive in a hurry, feel free to create a separate file with just the listing (which is what most people do).

---

### Post by descentspb on 2008-05-06
Ok, insane_alien. And if you bodge files together it would be nice if you are provided with easy access to each of the files, wouldn't it? And now i don't have an easy access

---

### Post by descentspb on 2008-05-06
I called it obsolete, cause i thought that its slowness lies in its architecture and is based on the history of tar, when it was used for tapes (linear data access). 

Edit: And about the listing, that's nice but complicated. I want tar to give me a possibility to choose, for tar itself to make such a listing automatically, and embed it into the archive. And for the ubuntu archive manager, or any other similar program to read this embedded file list, if it exists.
Or any other way to make it read the metadata quicker, cause i think tar should be a great archiver, not only a file merger.

---

### Post by ASULutzy on 2008-05-06
I wouldn't call it obsolete, though I would say that compressing the meta data separately at the cost of slightly larger file size might be desirable to some users.

---

### Post by descentspb on 2008-05-06
Exactly. My whole archive weighs 1000 mb, and the bz2 compressed text file with all the contents, their sizes and permissions weighs 430 kb. I'm sure it's not critical for 99% of the users.

---

### Post by Phenax on 2008-05-06
"Why can't tar be more like $x?"
Because tar isn't $x.

---

### Post by init1 on 2008-05-06
> **billgoldberg said:**
> Tar is great.

But if I need to archive files, I like to compress them while I'm at it.

And from what I've heard .7z is the best at that for the moment.
It has the best compression ratio, but it's also one of the slowest.

---

### Post by Polygon on 2008-05-06
maybe tar just isnt the best format for your backups. Why not just use zip 7z, rar, ace, or any of those other formats which have 'easier' access to the metadata then tar does?

---

### Post by macogw on 2008-05-06
> **descentspb said:**
> yes, sure, it does not do any compression, but i'm not talking about compression. Tar is great in all its functionality, but when you open a large tar file through the archive manager, you should wait till the system reads all the file to be able to look through the contents. Even in the obsolete zip you can view the contents quickly.

You are asking the wrong question!  When you have just a .gz or .bz2, it's a *single* file, compressed.  When you have .tar.gz or .tar.bz2 or just .tar it's a bunch of files archived and *maybe* compressed (if .tar.gz or .tar.bz2).  If file-roller is slow on uncompressed tars, that's file-roller's fault.  It has *nothing* to do with tar's format.

---

### Post by toupeiro on 2008-05-06
Almost every major enterprise backup solution still uses tar under the hood.  Veritas/symantec, legato, arcserv..  Why?  Because tar by itself *NOT* compression, its an archive, and can be line copied incredibly fast.  Hardware compression is much more efficient.

If its not broke, don't fix it?  Is it obsolete?  I dont see how it could be.

---

### Post by maybeway36 on 2008-05-06
I think the system has to decompress the tar/gz or tar/bz2 file before it can read its contents, hence the wait. Have you tried not compressing your tar files?

---

### Post by zmjjmz on 2008-05-06
.tar.gz has never been slow for me.  Even on my 400MHz Celeron.

---

### Post by descentspb on 2008-05-07
Hmm. I don't have access to my linux system now, but i've tried to make a tar (without compression) in windows at work, and it seems that a tar without compression is read quickly. So this problem appears when using bz2 or gz compression. I think that it should be dealt with. Maybe it is a problem of the ubuntu archive manager?

---

### Post by forrestcupp on 2008-05-07
> **descentspb said:**
> Hmm. I don't have access to my linux system now, but i've tried to make a tar (without compression) in windows at work, and it seems that a tar without compression is read quickly. So this problem appears when using bz2 or gz compression. I think that it should be dealt with. Maybe it is a problem of the ubuntu archive manager?

You haven't been reading this thread well.  It is meant to be that way.  With bz2 and gz, they opted for greater compression ratios over speed.   They aren't meant to be fast, they're meant to be great compressors.  They got their great compression ratios by compressing everything together, which means that it all has to be uncompressed before you can view it.  That isn't something you need, but that doesn't mean that there isn't a demand for high compression at all.

You said yourself that you don't need compression, so you need to just tar without compression.

---

### Post by Dr Eigen on 2008-05-07
If this is such a huge issue for you, why don't you compress then tar?



Personally, I'd be mortified if tar went the way of the dodo.  The lack of strange metadata structures is its power.  Nothing like a corrupted lookup table to ruin your day.

---

### Post by tubezninja on 2008-05-07
Add me to the list of people who say, if you feel it's obsolete, then simply don't use it.

If however, you feel compelled to use it, then it isn't obsolete, is it? :)

I'll say this much: for a particular application we're developing where I work, tar is indispensable and quite useful.  A lot of digital archive projects would be dead in the water if it suddenly went away.

---

### Post by FuturePilot on 2008-05-07
TAR is what holds .debs together. Ever open a .deb with File Roller? It's interesting. But without TAR there is no .deb. Just something to think about. ;)

---

### Post by descentspb on 2008-05-07
I regret giving that name to the thread :) Well, it has been proven here that tar **is not** obsolete. And now needless to say, tar does its job perfectly. It is just slow in reading the contents **only** when cooperating with GZip or Bzip2, cause it needs the be decompressed first. The question is fully answered, thanks to everyone.

P.S. But that would be still really nice if the ubuntu archive manager could view the tar.bz2 (or .gz) contents quickly :)

Edit: shame on ubuntu archive manager! Even the windows total commander can view the contents of the tar quicker than it! The UAM opens my .tar file's contents for 25 seconds, and the TC does it only with 4 secs. The same .tar, but also compressed with bzip2 the UAM opens for 3 minutes. My TC can't open tar.bz2 to compare.

---

### Post by sixdrift on 2008-05-07
What would be *nice* in a modern archiver (something better than Archive Manager) is first that it did not work sequentially. I *think* right now it works sequentially, first uncompressing the entire tarball to get back to tar file, and then getting the listing of files from the tarfile. If a decompressor were integrated inline so that you only decompressed blocks of the tarball and then used the tar or USTAR headers to begin listing files as the blocks were decoded, you would have snappier response times. However, I am unsure how the compressor/decompressor works and not sure if that is entirely possible.

---

### Post by 7x1x on 2009-10-26
What about compressing everything with bz2 first followed by making the tar. This will result in slightly larger sizes but quicker access times with meta-data being separate for each file. Writing a script  would be the easiest way to achieve this.

In retrospect replying was probably a bad idea with the title of the thread.

---

### Post by dragos240 on 2009-10-26
> **7x1x said:**
> What about compressing everything with bz2 first followed by making the tar. This will result in slightly larger sizes but quicker access times with meta-data being separate for each file. Writing a script  would be the easiest way to achieve this.

You do realize that you woke this thread from it's deep sleep right?

---

### Post by kevdog on 2009-10-26
lzma or lz is actually now the king of compression algorithms -- and not 7z.  7z I believe is proprietary anyway -- hence the knock.

---

### Post by Xbehave on 2009-10-26
> **7x1x said:**
> What about compressing everything with bz2 first followed by making the tar. This will result in slightly larger sizes but quicker access times with meta-data being separate for each file. Writing a script  would be the easiest way to achieve this.
If you compress files individually then tar them, your compression sucks.
tar is a simple tool and it does that well, if you want to be able to browse individual files in a compressed archive then it's not the tool you want.

If you want raw speed for decompressing a file, (like gzip does) then you just want sequential access which has the downside that you have to decompress all the files up to the one you want to read it. I believe something like zip is dictionary based so it can read files in any order (but will be slower for raw compress/decompression)

ATM the fasted compression program is [nanoZIP]("http://compressionratings.com/i_nanozip.html"), it seams to use a mix of the above to methods (which means it will not allow you to read any file until all of those before it have been read).

I'm no compression expert but it seams that if you want to be able to access subsets of a compressed archive you need to use a worse compression algorithm giving you bigger files and, slower total decompression.

tl;dr only lame compression lets you read random files from an archive so it will never replace current algorithms.

> **kevdog said:**
> lzma or lz is actually now the king of compression algorithms -- and not 7z.  7z I believe is proprietary anyway -- hence the knock.
1) 7z is oepn
2) lz is an OOOOLD method, most modern algorithms are based on it but are a significant improvement.
3) 7z (and most current gen formats* use lzma)

*I believe a notable exception is .deb

---

### Post by FuturePilot on 2009-10-26
> **kevdog said:**
> lzma or lz is actually now the king of compression algorithms -- and not 7z.  7z I believe is proprietary anyway -- hence the knock.

Um, 7zip is open source. [http://www.7-zip.org/]("http://www.7-zip.org/")

> 7-Zip is open source software. Most of the source code is under the GNU LGPL license.

---

### Post by kevdog on 2009-10-26
Sorry I did mispeak about the open source comment -- so I do apologize.  I did however run across the interesting article discussing the merits/pitfalls of various compression algorithms.

[http://linuxgazette.net/162/lindholm.html](http://linuxgazette.net/162/lindholm.html)


Also how is 7zip open source compliant if only a portion of the source code is released under the GPL?  I'm really kind of confused about that statment.  What part of 7zip isn't GNU LGPL compliant?

---

### Post by Xbehave on 2009-10-26
> **kevdog said:**
> Sorry I did mispeak about the open source comment -- so I do apologize.  I did however run across the interesting article discussing the merits/pitfalls of various compression algorithms.

[http://linuxgazette.net/162/lindholm.html](http://linuxgazette.net/162/lindholm.html)


Also how is 7zip open source compliant if only a portion of the source code is released under the GPL?  I'm really kind of confused about that statment.  What part of 7zip isn't GNU LGPL compliant?
The RAR plugin, because its a plugin it gets away with it

---

### Post by Mateo on 2009-10-26
zip is the best format.

---

### Post by toupeiro on 2009-10-26
Isn't there enough things to fix out there rather than try to find a solution to a solution that isn't broke?

Why tar?  because its versatile, compressible by several compression tools, widely supported by many, many operating systems, versatile with shell piping a.k.a. very, very scrip table, just about EVERY backup application in the industry can (and does) use it with some sort of additional compression, just because tar means Tape Archive, doesn't mean you have to put it on tape...  If you like zip, zip a tar file and get over it. :)

---

### Post by juancarlospaco on 2009-10-26
**.TAR is part of .DEB **  :)

---

