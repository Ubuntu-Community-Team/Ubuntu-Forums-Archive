---
title: "tar"
date: 2006-05-19
forum: Server Platforms
---

### Post by rensu on 2006-05-19
could someone tell me why I can't tar -xvvzf this file:
tomahawk-1.1.2-bin.tar.gz

---

### Post by jazzmuzik on 2006-05-19
x means you are extracting. Permission problem? Out of disk space?

---

### Post by ashrack on 2006-05-19
[QUOTE=rensu]could someone tell me why I can't tar -xvvzf this file:
tomahawk-1.1.2-bin.tar.gz[/QUOTE] 
Mind being a little more specific its like saying my cat wont eat.

---

### Post by rensu on 2006-05-19
sudo tar -xvvzf tomahawk-1.1.2-bin.tar.gz 

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by jazzmuzik on 2006-05-19
Maybe it was already gunzipped. Try

sudo tar -xvvf tomahawk-1.1.2-bin.tar.gz

---

### Post by it.henrik on 2006-05-19
Have you checked the md5? ... 

from apaches webpage " It is good practice to verify the integrity of the distribution files."

and I can extract the one I dl:ed just fine ... it also says "Please note that the tar.gz archives contain file names longer than 100 characters and have been created using GNU tar extensions. Thus they must be untarred with a GNU compatible version of tar."

but most likely its a corrupted archive.. just dl it again

---

### Post by it.henrik on 2006-05-19
[QUOTE=jazzmuzik]Maybe it was already gunzipped. Try

sudo tar -xvvf tomahawk-1.1.2-bin.tar.gz[/QUOTE]

*doh* 

didnt notice the z :) 

good point there

---

### Post by rensu on 2006-05-19
Nevermind I just downloaded them into my Windows computer and extracted there and uploaded to linux computer then.

---

