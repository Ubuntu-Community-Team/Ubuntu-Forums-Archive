---
title: "Compression"
date: 2010-12-22
forum: The Cafe
---

### Post by sefs on 2010-12-22
1) With the plethora of compression formats 7z bz2, gzip, lzma etc, is tar still relevant?

2) I realize that I can only split files via the compress dialog, when I select 7z. Why not for the others.

I've created a small poll to see what is the favorite compression format (generally) among the forum.  I also understand that each format has it's place, but we are talking generally here.

---

### Post by Spice Weasel on 2010-12-22
.7z, because it's a free format and more widely supported than most of the others listed.

Otherwise .gz or .tar.bz2 (if what I'm compressing would only be used by users of UNIX-like operating systems).

---

### Post by Paddy Landau on 2010-12-22
> **sefs said:**
> 1) With the plethora of compression formats 7z bz2, gzip, lzma etc, is tar still relevant?
Yes, tar is used by many scripts. If you want (for example) to bzip2 a folder, you need tar.

> **sefs said:**
>  2) I realize that I can only split files via the compress dialog, when I select 7z. Why not for the others.
I don't know. Tar does allow splitting, but not on the dialogue.

---

### Post by lykwydchykyn on 2010-12-22
tar is not a compression format.  It's a program for combining many files into one.  The resulting file can then be compressed using any compression scheme you want.

Modularity is nice.

---

### Post by NightwishFan on 2010-12-22
XZ, which is a newer type of LZMA.

---

### Post by Barrucadu on 2010-12-22
xz has very good compression, though takes a little longer to compress and decompress than, say, gzip.

---

### Post by NightwishFan on 2010-12-22
True. I rated the decompression "passable" so I decided to migrate to it from lzma and gzip. It seems to be faster than bzip2 even if I use the multi-threaded implementation, and xz being multi-threaded itself seems to be an eventual goal.

---

### Post by Superkoop on 2010-12-22
I voted for .zip simply because it's the mostly widely spread and usable in my experience. Otherwise I use gzip for my own uses, but usually I only compress things when others will be using it, if it's for my own use size is never really an issue.

---

### Post by RiceMonster on 2010-12-22
Usually use .zip, because then pretty much anybody can open it. It's not because I think it's the best option or anything.

---

### Post by 3Miro on 2010-12-22
> **RiceMonster said:**
> Usually use .zip, because then pretty much anybody can open it. It's not because I think it's the best option or anything.

+1. I often send files to friends in the Windows world, with zip I know they can open it. If I send them tar, they may or may not be able to do so.

---

### Post by uRock on 2010-12-22
> **RiceMonster said:**
> Usually use .zip, because then pretty much anybody can open it. It's not because I think it's the best option or anything.
Same here. It "just works" for everyone.

---

### Post by cokicd on 2010-12-22
arc for personal use ([http://www.freearc.org/](http://www.freearc.org/))
7z to share with others

---

### Post by sefs on 2010-12-22
Things get confusing when you see that in windows. You can use say the 7z _**archive format**_ but have choices for the _**algorithm**_ used - bzip2, lzma, lzma2 (xz in linux) - to generate the compressed file in this format.

You can also go with bzip2 and the usual roundup like gzip ect as the _**archive format**_ which would used _**algorithms**_ specific to them.  

I suppose in the file roller app on linux when you choose 7z what you are really getting is the lzma compression _**algorithm**_ used by default.

---

### Post by cokicd on 2010-12-22
arc for personal use ([http://www.freearc.org/](http://www.freearc.org/))
7z to share with others

---

### Post by The Real Dave on 2010-12-22
If it's for myself, tar.gz. If the file is going to a friend, or member of family, it'll be .rar, because I know they'll be using WinRAR. Other than that, I use .zip, seeing as just about anyone can open it.

---

### Post by Little Bones on 2010-12-22
.zip out of ease of use for my Windows using friends

---

### Post by Austin25 on 2010-12-22
I couldn't decide on .tar or .tar.gz so I went with .tar.gz because it compresses farther.

---

### Post by MisterGaribaldi on 2010-12-23
In those rare situations where I have to compress something (or maybe group files together into an archive) I usually still use ZIP because it's the most cross-platform supported.

But most of the time the only "compressed" files I traffic in are lossy-compressed JPEGs and PNGs.

---

### Post by Hur Dur on 2010-12-23
It depends.

If I am aiming for great compression, I prefer .arc or .uha or .bh.

For everyday use, I prefer .tar.bz2

---

### Post by ve4cib on 2010-12-23
> **sefs said:**
> 1) With the plethora of compression formats 7z bz2, gzip, lzma etc, is tar still relevant?

Absolutely.  Many compression algorithms (like bz2 and gz) can only operate one a single file.  Tar just strings a bunch of files into a single, larger, uncompressed lump.

If you wanted to gzip an entire directory without tar you'd need to create a separate .gz file for every file in the directory.  With tar you can make a single, larger file out of the whole directory, and then compress that single file.

Note however that tar is not a compression format.  It's an archive format (specifically Tape ARchive) with no built-in compression.


As for the poll, most of the time I'll use .zip just because I know everyone can open it.  For assignments I'm e-mailing to profs I'll often use .tar.gz or .tar.bz2 since I know they'll be running the assignment submissions on Unix/Linux boxes (I'm a Comp Sci student), but most everything else is .zip.

I used to use .rar all the time at work.  It was just what we used to send files to clients.  But since I stopped working to go back to school (and in the process stopped using Windows) I've stopped using .rar entirely.

---

### Post by Grenage on 2010-12-23
If multiple people - zip.
If it's for Windows+Linux (for me) - rar.
If it's for Linux - tar.gz.

---

### Post by miegiel on 2010-12-23
> **3Miro said:**
> +1. I often send files to friends in the Windows world, with zip I know they can open it. If I send them tar, they may or may not be able to do so.

I used to do that too until a while ago. For fun I tried opening a *.tar.gz* in my bare windows 7. And guess what, it just opened like a regular *.zip*. Since then I've just been mailing people *.tar.gz*'s. :D Occasionally I get a confused reply and need to suggest they double click it in the file browser.

I consider it revenge for people sending me empty emails with the message in an attached *.doc* that force me to read a simple message in an office clone or *.ppt*'s that I can't open at all.

---

### Post by BrokenKingpin on 2010-12-23
Why do people still use rar... I honestly do not get it?

---

### Post by ErikNJ on 2010-12-23
> **Grenage said:**
> If multiple people - zip.
If it's for Windows+Linux (for me) - rar.
If it's for Linux - tar.gz.

I do the same except I don't use rar.  Gzip for me and zip for general distribution.

---

### Post by Paddy Landau on 2010-12-23
> **miegiel said:**
> I used to do that too until a while ago. For fun I tried opening a *.tar.gz* in my bare windows 7. And guess what, it just opened like a regular *.zip*. Since then I've just been mailing people *.tar.gz*'s. :D Occasionally I get a confused reply and need to suggest they double click it in the file browser.

I consider it revenge for people sending me empty emails with the message in an attached *.doc* that force me to read a simple message in an office clone or *.ppt*'s that I can't open at all.
LOL, it seems Windows is slowly catching up.

I thought that OpenOffice could open PPT? I sometimes get Publisher files, though, that OO cannot open.

---

### Post by miegiel on 2010-12-23
> **BrokenKingpin said:**
> Why do people still use rar... I honestly do not get it?

What I don't like about rar is the license. And now I think of where I bump into rar's, it's usually in places where you can find loads of software to download (legal here, but illegal in most countries). I've understood rar's have some kind of parity, which is useful if you need to repair a corrupted archive. I assume people who don't care about linux because windows is "free" too, won't care about rar's license either. But I have no idea why they'd have so many corrupted archives that they love rar.

> **Paddy Landau said:**
> LOL, it seems Windows is slowly catching up.

I thought that OpenOffice could open PPT? I sometimes get Publisher files, though, that OO cannot open.

Hmm, I only get publisher files that I can't open.

---

