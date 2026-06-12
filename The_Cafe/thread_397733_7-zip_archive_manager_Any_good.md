---
title: "7-zip archive manager?? Any good?"
date: 2007-03-31
forum: The Cafe
---

### Post by billdotson on 2007-03-31
I am using Windows right now as I haven't got around to correcting my GRUB menu.lst so that I can boot Ubuntu and I downloaded the 7-zip archive manager and installed it.  I opened it up and it seems simple enough.. choose what you want to compress and then hit archive.  For a folder you have the choice of either  7z, zip or tar compression with 7z having 3 possible compression methods: LZMA, PPMd and BZip2.  Zip has 3 compression methods as well: deflate, deflate64 and BZip2.  If you choose a file then you have two more archive types that you can use.  Gzip and BZip2.  GZip only has one compression method and that is deflate while BZip2 has only one compression method and that is BZip2.  

My question is do each of these archiveal formats have their own disadvantages and advantages or are say the zip, gzip, bzip2 and tar just included for compatibility with programs and OSes that don't recognize a 7z archive?  I am wondering which archival format to use and what to choose for the dictionary size, word size, compression format, whether or not to have a solid archive, whether or not to create a sfx archive (sfx?) and wqhat to choose for update mode.  I would like someone to explain if it is not too much trouble, when to use which archive type, etc. as I would prefer to learn and not just copy what people say.

Thanks!

---

### Post by FoolsGold on 2007-03-31
The following text is blatantly stolen from Rhapsody's post located at: [http://ubuntuforums.org/showthread.php?t=393310&page=3](http://ubuntuforums.org/showthread.php?t=393310&page=3) , mainly because it's good info and he probably won't mind. :)

------

Here's my take on the compression formats.

Zip

FOSS extraction: Yes
FOSS archiving: Yes
Compression ratio: Low
Software support: Very high
Description: Zip is one of the oldest and most well-known formats. It's not very flexible or very good at compression, but support (though the permissively licensed zlib) is near universal across operating systems and platforms. It's a very good 'baseline' format, but there are better formats for compression or archiving.

RAR

FOSS extraction: Limited, only up to RAR 2.0
FOSS archiving: No
Compression ratio: High
Software support: Medium
Description: RAR is the most well-known competitor to Zip. It has the advantages of being more flexible and having much better compression than Zip, but archiving and (generally) extraction require code under proprietary licensing conditions, making it somewhat unpopular among users for FOSS operating systems.

gzip

FOSS extraction: Yes
FOSS archiving: Yes
Compression ratio: Low
Software support: High
Description: Essentially, gzip is very similar to Zip. It has about the same compression ratio and compression speed. The main difference is that gzip is normally used in a tar container, giving it flexibility more similar to RAR. With the relatively high software support and the fact that it's an open standard, it'd seem like the perfect replacement for Zip, but it hasn't caught on much outside of the Linux world.

bzip2

FOSS extraction: Yes
FOSS archiving: Yes
Compression ratio: Medium-high
Software support: Medium-high
Description: bzip2 is typically used in a tar container (like gzip) and thus has about the same level of flexibility. The big difference between the two is that bzip2 has a much higher compression ratio (not far off RAR) making it a good choice for FOSS users who want better compression. Like gzip though, it hasn't caught on much outside of the Linux world despite being an open standard with good support. Incidentally, bzip (the predecessor to bzip2) actually had better compression as it used arithmetic coding rather than Huffman coding, but this had to be changed due to arithmetic coding being rather patent-encumbered (a situation which looks set to continue for some time).

7z

FOSS extraction: Yes
FOSS archiving: Yes
Compression ratio: Very high
Software support: Medium
Description: 7z is a relative newcomer, but has quickly gained support due to an excellent compression ratio (generally even higher than RAR), plenty of features, and the fact that everything related to it is licensed under the relatively permissive LGPL. With the file format being stable now and software support fairly good, it looks like 7z could be the compression format to topple RAR someday.

Personally, I tend to use gzip or bzip2 for my compression needs. I don't like people using RAR, as it seems rather unnecessary these days. 7z is better if you really need high compression, but why do most people even need such compression? Hard drive space is cheap and abundant these days, and broadband internet connections are hardly more expensive. If you're transferring data on a peer-to-peer basis, gzip should be all you need.

------

---

### Post by STREETURCHINE on 2007-03-31
deleted same article from above.........

i use 7zip in windows and gzip with linux

---

### Post by billdotson on 2007-03-31
So, if I was to be using an archive format to backup the contents of my Steam install folder, something that I wouldn't be using very often 7z would be the best as it has the best compression?  For something like ISOs of Linux distros I assume I would use zip, as rar isn't fully supported with FOSS and I would need to decompress those if I wanted to burn one of those ISOs to a disk, so I wouldn't want to be waiting a long, long time to do so.

I still do not know what these options mean though: for 7zip the compression method options of LZMA, BZip2, or PPMd and for Zip the different methods are deflate, deflate64, and BZip2.  How do I know which compression method to use?      Also, the dictionary and word size I don't know what to set them on and I also do not know what update mode to use (options: add and replace files, update and add files, freshen existing files and synchronize files) whether to use an sfx archive or not or when to enter certain parameters.

---

### Post by prizrak on 2007-03-31
7-zip is actually very good the best archive manager I have seen to date on Windows.

---

### Post by Ux64 on 2008-06-08
> **prizrak said:**
> 7-zip is actually very good the best archive manager I have seen to date on Windows.

Actually I think that the Windows version GUI has some usability issues. I have reported those years a go. And alas, no fix yet.

I'm looking for proper UI for Ubuntu.

Here's thread for it.

[http://ubuntuforums.org/showthread.php?t=782897](http://ubuntuforums.org/showthread.php?t=782897)

---

### Post by LaRoza on 2008-06-08
> **Ux64 said:**
> 
Here's thread for it.

[http://ubuntuforums.org/showthread.php?t=782897](http://ubuntuforums.org/showthread.php?t=782897)

Since there is a support thread for you question, and this thread is old, this thread will be closed to keep the information up to date.

---

