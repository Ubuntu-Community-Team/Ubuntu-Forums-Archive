---
title: "Permissions and FTP"
date: 2008-01-25
forum: Server Platforms
---

### Post by theolster on 2008-01-25
My problem...
I play in a band and want to share a lot of our recordings with the other band memebers.  I have two users on my server, me and theband.  FTP is fine for both users. I want to be able to access /home/theband from my home directory ie. /home/me/theband

I think I need to us a symbolic link, but I keep screwing it up!

One thing is I've probably got a permissions issue of some sort.  Any files/folders I add to /home/me/theband I want to have rw privileges but I wan the user 'theband' to have only read privs, so they can download stuff but not delete it.

Any ideas?

---

### Post by Vinno on 2008-01-25
Then change the owner of the /theband/ stuff to you as owner and group to the band and make it read only.

chown me:theband /home/theband/*
chmod o=rwx,g=rx,o=rx /home/theband/*

---

