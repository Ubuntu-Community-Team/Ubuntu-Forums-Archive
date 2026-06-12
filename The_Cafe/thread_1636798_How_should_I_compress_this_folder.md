---
title: "How should I compress this folder?"
date: 2010-12-03
forum: The Cafe
---

### Post by Dustin2128 on 2010-12-03
I've got a 8Gb folder (lotro, can't get the downloader working with linux) on a friend's windows laptop, and I've got a 4GB flash drive to work with at present. I need to either compress it into a small enough one to fit or use a program that separates it into smaller compressed files.

---

### Post by NightwishFan on 2010-12-03
No compressor will get that down to 4gb. Try split:
```
man split
```

Help:
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Split_and_Reassemble_files](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Split_and_Reassemble_files)

As far as compressing the split parts, try XZ. I use that for everything.

---

### Post by Dustin2128 on 2010-12-03
> **NightwishFan said:**
> No compressor will get that down to 4gb. Try split:
```
man split
```Help:
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Split_and_Reassemble_files](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Split_and_Reassemble_files)

As far as compressing the split parts, try XZ. I use that for everything.
I've got to do the compression and splitting on the windows machine unfortunately. Any idea how I'd do that?

---

### Post by NightwishFan on 2010-12-03
Easier by far:
[http://www.linglom.com/2008/10/12/how-to-split-a-large-file-using-7-zip/](http://www.linglom.com/2008/10/12/how-to-split-a-large-file-using-7-zip/)

---

### Post by Dustin2128 on 2010-12-03
> **NightwishFan said:**
> Easier by far:
[http://www.linglom.com/2008/10/12/how-to-split-a-large-file-using-7-zip/](http://www.linglom.com/2008/10/12/how-to-split-a-large-file-using-7-zip/)
Looks pretty easy, but how would I put them back together once I'm back on my linux machine, the same instructions that were on the linux tutorial?

---

### Post by NightwishFan on 2010-12-03
I believe you can just extract the normal file. It should make say a file called: file.7zip and a bunch of files called file.7zip.001 002 and so on, just install pz7ip (command line program), and right click the "file.7zip" (in Nautilus File Browser) and hit extract here. (Ensure both pieces are in the same directory).

This is how it should work anyway. I would dig a little first as I only know the theory.

---

### Post by cammin on 2010-12-03
Like NightwishFan said, 7zip will automatically span the files when uncompressing if it can find them.

You can also cat the files together if you used 7zip, since it just splits the files. (still need 7zip to decompress it)
 It comes in handy if you want to keep the compressed file around as a backup without having to re-compress it.

cat part1 part2 > whole_file

This trick doesn't work with Rar, and I don't think it works on .zip files, either.

---

