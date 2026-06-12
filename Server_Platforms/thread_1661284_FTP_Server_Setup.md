---
title: "FTP Server Setup"
date: 2011-01-06
forum: Server Platforms
---

### Post by mpreissner on 2011-01-06
So I'm a Linux beginner...
 
I'm running Server 10.04. So far I've set up a Samba file server that I can access as a network drive from my local network. I now want to set up an FTP server that will take a user to their home directory, but include the same shared directory from my Samba share. So basically, each user will have their own private directory, plus a link to a community directory. I tried setting up a symlink, but that didn't work right through a browser. I also need to make sure the folder permissions are set properly so users can create new directories in their home directories and upload files - using a browser interface like Windows Explorer.
 
Any quick-and-dirty suggestions? Thanks!

---

### Post by mpreissner on 2011-01-06
To clarify:
 
Each user has their own home directory (/home/[username]) with the following four directories in it:
 
Documents
Video
Music
Pictures
 
I'd like to add a fifth directory - it's the root of my samba file share located at /srv/samba/Share.  The goal is that each user will have a private Docs/Vids/Music/Pics folder, plus access to the Share, which will have community accessible files.

---

