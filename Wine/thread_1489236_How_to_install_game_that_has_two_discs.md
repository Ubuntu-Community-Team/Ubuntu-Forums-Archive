---
title: "How to install game that has two discs"
date: 2010-05-20
forum: Wine
---

### Post by Keith Fox on 2010-05-20
Maybe this has been answered before but I didn't find any information about: not being able to eject to insert the second disc.  I'm trying to install in Wine a PC game called Swat 4. I have two discs and the first disc installs fine and prompts to insert disc 2... Only I can't eject because the software is actively locking it. I can only eject if I kill the process with "xkill" (GUI click to kill a process).

So is there any configuration I can do to allow ejecting in wine?  Oh and of course the same happens in PlayOnLinux, but you already knew that being that it's only a frontend for Wine.

I was originally just mounting the two image files using Gmount. Same problem I ran into, stuck on "please insert disc 2." I even tried to manually converge the two images into one image file using a terminal command to change bin and cue files to iso using "bchunk" and then extracted the files from the iso's into one common folder and ran a "mkisofs" to create an image from all the files extracted from the two iso images, to create one giant image with all the files in there.  Problem is "mkisofs" has some type of file system where it changes the file names with spaces to underscores and I ran into a missing file error because of it. 

So that's when I decided to just burn the two iso images onto two discs and install old school style. Now you're up to speed with me, help me through this community.

---

### Post by cogadh on 2010-05-21
EDIT - Ack!, I just noticed the directory structure in that screenshot. The next time you ask for help with a game in Wine, you probably should advertise the fact that it is a pirated copy of the game by showing the "Crack" directory to everyone. You not only won't find anyone willing to help you with a pirated game, the mods are probably five minutes from locking this thread for forum rules violations.

---

### Post by Elfy on 2010-05-21
Indeed that is so - closed.

---

