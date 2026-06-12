---
title: "Ubuntuone offline syncing"
date: 2009-11-27
forum: Ubuntu One (CLOSED)
---

### Post by psypher on 2009-11-27
Hi ubuntuone team, i need some assistance with OFFLINE syncing.

I need to be able to upload all my files (30GB+) once and then copy the U1 folder to several machines (rsync -avz -e ssh Ubuntu\ One/* 192.168.0.1:"Ubuntu\\ One" so that I don't have to download it again to all those machines, completely unfeasible to do so. 

I have tried copying the matadata over (rsync -avz -e ssh .local/share/ubuntuone/* 192.168.0.1:.local/share/ubuntuone) as well but as soon as i reconnect u1 it re-downloads some the files and marks them as conflict.

And if you delete those .conflict files, hoping that they download, they delete the original files??? Not that doing that is feasible either.

So is there any way to do this and if not I suggest this is something that should be seriously considered. Like right click and "sync to local lan client" or something. Not all people can afford huge amounts of bandwidth to constantly download all the files to all machines in the U1 group and this will save ubuntu bandwidth costs as well. I understand that this could be a future feature to be added which is fine, but at this time I need some way to do this manually.

Thanks


EDIT:
Tried the rsyncing again. 1st deleted all files in local/share/ubuntuone/ and "Ubuntu One" on destination PC then did rsync of metadata and then the files to Ubuntu One folder. Load up U1 client and let it sync. Still don't understand how U1 decides that some files are conflicts and some aren't. there seems to be no rhyme or reason as to how U1 randomly marks files as conflict.

---

### Post by psypher on 2009-12-12
Bump!

---

### Post by piojunbabia on 2009-12-13
I believe that you cant download if that machine/pc is not connected to your Ubuntu One account, in other words, you need to let that certain computer connected to your U1 account for it to donwload. IMHO. Thank you

---

### Post by psypher on 2009-12-13
all machines involved are connected to ubuntu one

---

### Post by piojunbabia on 2009-12-13
okay, sorry no idea.. :(

---

### Post by psypher on 2010-02-19
bump pls!

---

