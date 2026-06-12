---
title: "Music File Organization Help"
date: 2008-04-26
forum: The Cafe
---

### Post by Changturkey on 2008-04-26
Alright, so my "Music" Folder just went all berserk and all the music files were either improperly tagged or zero-byted. Not sure if it was Picard's fault, but I have a backup collection. Only problem is this collection is sorted in to Folders by Artist/Album, which I do not like. Is there a program/script I can use to get all the mp3s out of a folder, including subdirectories? I just don't want to copy/paste like over 9000 times.

---

### Post by red_Marvin on 2008-04-26
You want to move a group of files from a tree of folders into one giant folder?

---

### Post by Changturkey on 2008-04-26
Yes, basically.

---

### Post by red_Marvin on 2008-04-26
I've written a little python script, basically what it does is:
If you have the following files:
s-folder/folder1/filea
s-folder/folder1/fileb
s-folder/folder2/filec
s-folder/folder2/filed
s-folder/folder2/filea

and you run the program (in the terminal) as *./treeflatten.py s-folder t-folder*

it will copy the files in the following manner:

s-folder/folder1/filea -> t-folder/filea-1
s-folder/folder1/fileb -> t-folder/fileb
s-folder/folder2/filec -> t-folder/filec
s-folder/folder2/filed -> t-folder/filed
s-folder/folder2/filea -> t-folder/filea

It should do the trick, I have tested it on some dummy files.

---

### Post by SuperSon!c on 2008-04-26
i'm grabbin that for possible future use.  thanks red.

---

