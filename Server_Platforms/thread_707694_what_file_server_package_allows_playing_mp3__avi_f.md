---
title: "what file server package allows playing mp3 / avi from server?"
date: 2008-02-25
forum: Server Platforms
---

### Post by bluepowder7 on 2008-02-25
noob question time!

if i want to set up my file server to store all my mp3 files and all my avi / mpeg files, and then be able to play them while i'm sitting at my laptop without having to copy the file over, is there any special package or setting i need to use?

i'm just starting out, and i THINK that samba is the tool for normal file serving, but is what i'm trying to do going to work with samba?  or am i looking at a streaming setup of some kind?

the other files that are going to be stored on the server are documents, images, etc - stuff that's "static", so to speak.

---

### Post by jhetrick62 on 2008-02-25
Samba can handle that as long as your connection is decent.

Jeff

---

### Post by bluepowder7 on 2008-02-25
cool, thanks!  i thought i'd need to set up or install some special app that will ensure that the file chunks come in the right order so that the music or movie plays from beginning to end, it receiving a chunk from the middle followed by a chunk from the front followed by the closing credits followed by the intro etc. (kinda like torrents do).

i've got NFS working now (just got it running a few hours ago, moving files over to the server as we speak), so if that will also work fine, then i'll be happy.

---

