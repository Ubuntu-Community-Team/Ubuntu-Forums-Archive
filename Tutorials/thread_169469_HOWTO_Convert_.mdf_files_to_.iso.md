---
title: "HOWTO: Convert *.mdf files to *.iso"
date: 2006-05-02
forum: Tutorials
---

### Post by hamil on 2006-05-02
I recently found a program called mdf2iso.
This program lets you convert your Alcohol 120% files to ordinary iso files.
The program is also in the repositories, but that is a version that do not handle big files that well.
If you do have an big file (fex. an DVD), you will have to patch mdf2iso.
The easiest way, if you do want to compile yourself, is to surf to: [mdf2iso at berlios](https://developer.berlios.de/project/showfiles.php?group_id=2545) and download the source.
To find the patch, you will have to enter [ this adress.](http://developer.berlios.de/patch/download.php?id=665)

Open a terminal and type in:
```
gedit large_file.patch
```
In this new document, you will have to paste all the text from the patch page, save and close.
Extract the mdf2iso source with the command: 
```
tar xvfj mdf2iso-0.3.0-src.tar.bz2
```
Now it is time to patch the file:
cd into the mdf2iso directory and:
```
patch -p1 < /DIR/OF/YOUR/large_file.patch
```
This should not give you any output errors.

Then it is time to compile, as usual:
```
./configure
```
```
make
```
```
sudo make install
```


To use mdf2iso, simply use the terminal:
```
mdf2iso /home/myhome/alcohol-dvd.mdf /home/myhome/alcohol-dvd.iso
```

That should be it.. :)

If you do run into any trouble, I have built a .deb package with the patch already appended.. Send me an message.. ;)

---

### Post by Nicram on 2006-12-10
Can't compile it. Could you send me a link when I can download deb file?

---

### Post by Jonathan2007 on 2007-01-13
There is a deb [here]("http://freshmeat.net/projects/mdf2iso/"). It works perfectly for me. From what I have read it is also in some Ubuntu repository.

---

### Post by hamil on 2007-01-13
> **Jonathan2007 said:**
> There is a deb [here]("http://freshmeat.net/projects/mdf2iso/"). It works perfectly for me. From what I have read it is also in some Ubuntu repository.

It used to come without the "largefile patch", which will make it unusable for larger files. Therefore I made this guide, and my own deb file. 

Since I got alot of responses to this posting lately, (PM's) I decided to uploaded the deb here: [FileFactory, mdf2iso deb]("http://www.filefactory.com/file/4379c2/"). Hope it will help some of you!

---

### Post by ScottFW on 2007-01-25
> **hamil said:**
> ...I decided to uploaded the deb here: [FileFactory, mdf2iso deb]("http://www.filefactory.com/file/4379c2/"). Hope it will help some of you!
I'd like to try your deb, but File Factory says "Sorry, this file is no longer available. It may have been deleted by the uploader, or has expired."
Could you send me the deb as an email attachment? I will PM you with my address.

---

### Post by PurplePenguin on 2007-01-27
Better yet, why not post it somewhere permanently?  I've got a webserver that I can toss it on if you'd like.

It'd be a lot better to have it available to everybody all the time than to rely on PMs. :)

---

### Post by Hari5g900 on 2013-02-07
Okay..... I did everything right and converted an mdf file to an iso file but can't open it :(
It says CD ROM is not in ISO 9660 format.
Please help me

---

### Post by pixelanimal on 2013-04-11
I have the same problem i can't open the converted .iso file as usually. The Converted  .iso file is  also 13% smaller than the original .mdf file. My operating system is Version 12.04 (precise)  (64-Bit) Kernel Linux 3.2.0-39-generic CNOME 3.4.2 Hopefully greets

---

