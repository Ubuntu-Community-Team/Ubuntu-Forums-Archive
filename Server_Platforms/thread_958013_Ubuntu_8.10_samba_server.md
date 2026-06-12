---
title: "Ubuntu 8.10 samba server"
date: 2008-10-24
forum: Server Platforms
---

### Post by confused311 on 2008-10-24
First lets me say this i am a NOOB i have had a little expiernce with ubuntu desktop and liked it enough to try something different. I would like to set up a file sharing server that would allow the folloing: 4 user id's each with their own assigned folder with quota, that they would be locked into, and a 5th general folder for media vissible to all 4 users with in their given folder, dare i say it(like a windows short cut).

---

### Post by lykwydchykyn on 2008-10-24
What operating system are the clients running?  Are they all on the same network as the server, or is this for remote use?

You can do all this no problem.  
 - You probably want to use SAMBA if you have windows clients, or NFS if it's just ubuntu machines
 - SAMBA has a special "homes" share feature that will share the home directories of all users on the system and make each directory available only to the respective user.  NFS can be similarly configured, by sharing (or "exporting" in NFS parlance) /home.
 - You can create a shared folder, give it read/write permissions to everyone on the system, and make symbolic links (a.k.a. soft links or symlinks) to it in everyone's home directories.  
 - Quotas can be set on the filesystem level.  It's best if you make /home a separate partition, I believe.  I have never set up quotas, so I'll leave that to someone else to advise on.

---

### Post by confused311 on 2008-10-25
All clients are currently xp but i would like to phase them out to ubuntu desktop over time.

---

