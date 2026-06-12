---
title: "Fileserver, best practise."
date: 2010-03-16
forum: Server Platforms
---

### Post by loofi on 2010-03-16
Hi

I am working on a setup for a company based on Ubuntu 10.04 when it is finished. The solution will be of 2 HP Proliant 110 which is set up with the server variant of Ubuntu. Each server has 4 pieces of internal disks and to share files with Samba. The idea is that the one server to be passive and just have replicated content from server No. 1 (Nightjob via rsync)

What I am looking for is some qualified opinions on how to set up the mount and Samba. I would like to use EXT3/EXT4. Share out each disk as a separate directory. (Projects, Common, etc.). The clients are of Win XP, and Windows 7 in a Workgroup, so i would prefer not to apply all users to Samba. Presumably there will be a dedicated user (Force user) to write to the share.

Is there anyone who can give me some feed back on how this tends to be set up in such scenarios? 

Shall I use umask=000 and mount as default, mount as a dedicated user? Any thoughts. The server is for a small 4 people company. Security thoughts? 

If I've forgotten something important please ask.

best 
joakim

---

### Post by BobVila on 2010-03-16
I think you'll find that sharing each disk individually isn't a great idea. I know you've got a backup server, but it seems smarter to raid the disks for a bit of internal fault tolerance.

---

