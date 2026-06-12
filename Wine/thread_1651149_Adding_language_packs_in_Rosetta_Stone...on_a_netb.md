---
title: "Adding language packs in Rosetta Stone...on a netbook"
date: 2010-12-22
forum: Wine
---

### Post by md328 on 2010-12-22
I am running Rosetta Stone v 3.4.5 under Wine on a Asus 1001px netbook with Ubuntu 10.04 netbook ed. Everything seems to work fine as far as the program itself, but I cannot for the life of me figure out how to install the language packs from the .iso files that I have. Has anybody done this before?

---

### Post by md328 on 2010-12-22
Ok since I posted that 15 minutes ago, I found something that might help me:
[http://ubuntuforums.org/archive/index.php/t-619250.html](http://ubuntuforums.org/archive/index.php/t-619250.html)

Specifically matts31415's post:

"I was trying to get rosetta stone to work in wine and could not get the ISO of the language disk to be recognized by the rosetta stone program or by wine in general.

mkdir /mnt/virtual

mount -o loop /path/to/languageCD.iso /mnt/virtual

go to the wine configuration window (Applications > Wine > Configure Wine)

Go to the Drives tab

Click Add...

Set the path to /mnt/virtual

click Show Advanced button

set Type: cdrom

thats it. launch your app and it should recognize your mounted iso as a cd

for me the key was setting that drive type to cdrom in the wine cfg
axelsvag"

The problem I am having is that I have no virtual directory under mnt. I am a relative newbie to linux and the terminal, and I wasn't sure what the first two lines he wrote were referring to...

Anybody know?

---

### Post by md328 on 2010-12-22
tried running the mkdir /mnt/virtual command in the terminal

got this error: "cannot create directory `/mnt/virtual': Permission denied"

is there a way around this?

---

### Post by md328 on 2010-12-22
I hate to keep answering myself here. but I have read other places that a way to get around the previously mentioned roadblock is to log in as root. While I've never done this, I know how to get in and out of root. I'll wait another few hours before I do this (hopefully I'll get a response).

---

### Post by md328 on 2010-12-22
nevermind. I solved it. It's called Google folks, it's amazing what you can find there. haha.

and "sudo" was what I was looking for, duh. I apologize if you wasted your time reading this. But thank you if you at least looked at me thread

-Mike

---

### Post by Mia1990 on 2010-12-22
Gmount is a gui tool for mounting .iso files as a cd rom and it works really good the wine website say's not to run wine as [root]("http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014")

---

### Post by DonJuan4076 on 2011-08-09
Hi so I am having the same trouble at the first poster. I also am having trouble following what to do to fix my problem. Could you please post a step by step how to use language packs on a netbook. Thank you

---

