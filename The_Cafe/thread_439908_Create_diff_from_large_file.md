---
title: "Create diff from large file"
date: 2007-05-11
forum: The Cafe
---

### Post by el3ktro on 2007-05-11
Hello,
I'm wondering if it is possible to create a diff from a large file. The situation is as follows: Someone created a custom Ubuntu 7.04 boot CD to be able to boot Ubuntu on an Averatec 2460 laptop. The only difference between the original Ubuntu Live CD and the new Live CD is ONE single kernel module. It would be nice if someone didn't have to download the whole Live CD, but only the small part which is different from the original Ubuntu Live CD.

So short question: Is there a tool which checks the differences between two files and creates a (binary) diff file and which enables me to assemble this custom file by applying the diff to the original file?

Tom

---

### Post by heimo on 2007-05-11
Not sure if it'll work nicely with .iso files, but you could try with bsdiff or xdelta.
[http://packages.ubuntu.com/feisty/utils/bsdiff](http://packages.ubuntu.com/feisty/utils/bsdiff)
[http://packages.ubuntu.com/feisty/utils/xdelta](http://packages.ubuntu.com/feisty/utils/xdelta)

---

### Post by Arne.F on 2007-05-13
I have already tested xdelta3. It produce a very large file so you can also download the whole image.
The reason is that the replaced file is inside of the squashfs image on the cd. Because this file is compressed it is complete different for an delta compare.

The only way to do itself is an already working system with installed uck. Here it is possible to exchange files inside of the squashfs and the initrd. The crashing modul was inside of both files.

Arne

---

