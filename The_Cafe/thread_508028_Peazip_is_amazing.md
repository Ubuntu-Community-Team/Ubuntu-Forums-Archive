---
title: "Peazip is amazing"
date: 2007-07-23
forum: The Cafe
---

### Post by bread eyes on 2007-07-23
[http://en.wikipedia.org/wiki/Peazip](http://en.wikipedia.org/wiki/Peazip)

---

### Post by bread eyes on 2007-07-23
What, no one thinks this is way better then File Roller or Ark?

---

### Post by mostwanted on 2007-07-23
[I installed it]("http://sourceforge.net/project/downloading.php?groupname=peazip&filename=peazip_1.8.2.bin.LINUX.GTK2.i586-1.deb&use_mirror=mesh") to see what the fuss was about. I must say its Gnome integration is quite messy, leaves visual artefacts all over the place and I don't know what to look for in it that File-roller doesn't already have. Perhaps you can tell us why you think it's is amazing?

---

### Post by bread eyes on 2007-07-23
> **mostwanted said:**
> [I installed it]("http://sourceforge.net/project/downloading.php?groupname=peazip&filename=peazip_1.8.2.bin.LINUX.GTK2.i586-1.deb&use_mirror=mesh") to see what the fuss was about. I must say its Gnome integration is quite messy, leaves visual artefacts all over the place and I don't know what to look for in it that File-roller doesn't already have. Perhaps you can tell us why you think it's is amazing?

It looks nice and it has a more complete gui.

---

### Post by ice60 on 2007-07-23
i think it's suppose to have a good encryption algorithm which only it uses, i think i remember reading that.

---

### Post by hardyn on 2007-07-23
does anybody know of a program that will allow a zip to spanned across many volumes? commanline or gui?

---

### Post by ice60 on 2007-07-23
> **hardyn said:**
> does anybody know of a program that will allow a zip to spanned across many volumes? commanline or gui?
peazip does this - "Features archive volume spanning" is that the same??
[http://sourceforge.net/projects/peazip/](http://sourceforge.net/projects/peazip/)

i found the person who does the crypto on peazip here -
[http://home.netsurf.de/wolfgang.ehrhardt/index.html](http://home.netsurf.de/wolfgang.ehrhardt/index.html)

don't know how useful that is though lol

---

### Post by bread eyes on 2007-07-23
> **ice60 said:**
> peazip does this - "Features archive volume spanning" is that the same??

Ya

---

### Post by Giorgio tani on 2007-07-26
Hi, thank you very much for taking interest in PeaZip; I hope to can answer to some questions asked in this thread.

Volume spanning: PeaZip, through Pea executable, can perform spanning/merging of files in volumes of custom sizes, and can save/check checksum or hash information of each volume in a separate file (in this way keeping compatibility to similar applications, like HJSplit); integrity check algorithms ranges from CRC32 to Whirlpool hash.
A very similar single pass volume spanning is available as option for .pea archives, while handling archives supported through POSIX-7z instead a different mechanism, provided by p7zip itself, is used.

Encryption: .pea format was designed to support authenticated encryption, to guarantee both message integrity and privacy (AES in EAX mode), moreover it allows flexible integrity check schemes chosing different integrity check or hash algorithm for objects (the input objects getting archived) and volumes (the output object, one or more volumes). Using different formats will result in using different schemes of encryption: .7z uses AES256; .zip, through p7zip, can be encrypted with zipcrypto algorithm, weak, or since version 1.8 using 7z 4.47 AES256, WinZip >=9 AE standard, can be used (this is the default in PeaZip, you should use zipcrypto only for compatibility with old zip utilities).

GUI issues: I know PeaZip is quite a new project, and it is developed using Lazarus/FreePascal, that is a quite new development environment, so expect most of the issue to go while both projects get more mature.
GTK1 support in Lazarus is generally jet very good, so the GTK1 version of the application can be expected to run in any environment without graphic issues, but I know it's less nice than GTK2 version (and what is even more important, GTK2 dialogs are far better); it's still provided to be used on older machines or where GTK2 version fails or for people still liking GTK1.
GTK2 support is getting quickly better, however I still have display issues on some out of the box configurations for some distributions, expecially about stringgrid component; the boxes where it runs better at this moment are those with Debian 4 and Ubuntu 6.10/6.06, then on Suse 10.2 and older, where it runs quite well. 
About the installation (or for the portable version, the first time you run the executable), on most of recent distributions, also small ones, all dependencies are usually satisfied, however on some distributions it may be required to install some gtk/gdk related libraries.

---

### Post by DoctorMO on 2007-07-26
whats wrong with tar | split | encrypt on the cli?

---

### Post by Kayne on 2007-07-26
> **DoctorMO said:**
> whats wrong with tar | split | encrypt on the cli?
It's on cli.

---

### Post by Giorgio tani on 2007-07-26
> **DoctorMO said:**
> whats wrong with tar | split | encrypt on the cli?
Nothing, in fact talking of cli one of the reason I started writing PeaZip is that I find something 'wrong' in the dichotomy between cli and gui worlds.
What I wanted and tried to do is a gui archiver program allowing me to export jobs as command line and then edit them with the full control the cli gives, leaving a first (boring to do with the cli) part to the gui and the fine-grained part to the cli for most experience users, certainly smarter than a gui frontend in exploiting the cli syntax to do the job they need with maximum freedom.
I think this way may show to less experienced users that there is no need to be scared by cli, which can become an easy to enter world and a much more flexible than gui tool to use when needed.
At the same time, I hope to have done something useful for advanced users too, which need to focus less on trivial and mnemonic details and can focus more on logic, in other world they can start editing a well formed cl template spending time more on how they want the job done rather than on how they can get the job work, like 'does that switch exist?' or 'how should I write that?' and so on...
I also wrote the PeaZip frontend and the Pea backend binaries (other ones are all native console applications) to be accessible from command line, in order to allow experienced users to employ them in pipes with other programs, since basically I belive cli should be the common basis of any well thought tool.

---

### Post by Joe_Bishop on 2008-01-26
> **bread eyes said:**
> It looks nice and it has a more complete gui.
:lolflag:
it differs very much from other gtk/gnome applications. It's authors should learn HIG, and then look at the any gnome application.

---

### Post by ~LoKe on 2008-01-26
I've never had a problem with the cli...but whatever.  Always happy to see another application.

---

### Post by Polygon on 2008-01-26
i tried peazip but for some of the dialogs the font is too big for the little button, so i only see half of the word.

---

### Post by Giorgio tani on 2008-01-28
Hi, earlier today I published PeaZip 1.11.
Updates are in the frontend for p7zip (4.57), UPX (3.02) and for FreeArc, a new promising GPL project for a compressor which supports recovery records and strong encryption (AES, Serpent, Twofish, Blowfish).
Also, I added a tool for checksum/has multiple files with multiple (selectable) algorithms at once, supporting Adler32, CRC16/24/32/64, eDonkey/eMule, MD4/MD5, Ripemd160, SHA1/224/256/384/512, and Whirlpool512.
Unfortunately the issue of not resizeable comboboxes which are difficult to read with some fonts is not yet fixed, I have to stay tuned on the IDE development to find a fix or a workaround for it.

---

### Post by Langleyo on 2008-03-31
An absolute gem of a program, been hunting around for a cross platform
zip/rar extractor for a while when I stumbled upon Peazip. Doubtless there are others but this works fine on Ubuntu on my Toshiba laptop as well as under windows XP. Very simple to use, it gets my vote. Nice and ergonomic.

I recommend this to all my buddies.


Molto Grazie Giorgio! We need more do-ers like you! :)

---

