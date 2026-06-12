---
title: "Lost permissions on a remote server"
date: 2007-05-10
forum: Server Platforms
---

### Post by argux on 2007-05-10
I couldn't find a place to post this question, so I decided to post it here. It's not an ubuntu-specific question, so if the moderator thinks this is inappropriate here, please move the thread to wherever it fits.

I have this free hosting account in godaddy, where I was trying to install the vanilla forum. On the instructions it said to change the permissions on some directories, which I tried to do using gftp. For some reason, it failed. I tried with ncftp, and it could never open a connection to my server (kept asking me for the username, specifying the user and password didn't help). So I tried with ftp. It seemed to do the trick. But now, those directories have no permissions at all. It's d--------- for all four of them. So I can't delete them, can't open, can't even change the permissions. As far as I know, only root could delete such a directory, right?

I could just create a different directory and try again there, but now what will happen to these dirs? Will they remain there for all eternity? And, more important, why did this happen?

---

