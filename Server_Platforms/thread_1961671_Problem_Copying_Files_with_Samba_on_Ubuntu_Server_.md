---
title: "Problem Copying Files with Samba on Ubuntu Server 11.04"
date: 2012-04-19
forum: Server Platforms
---

### Post by djspx on 2012-04-19
Hello everyone,
My first post here and of course it's because of a problem I'm encountering with samba.
I decided to use one of my older computers as a media server and I thought, what better than Ubuntu Server and Samba so my clients can all connect to it as well.

I have installed Ubuntu Server 11.04, for some reasons this old P4 won't run any newer version, actually it won't respond when booting a 3.x kernel, only a 2.x kernel.
Anyways I'm fine with that.

The real problem I'm facing is while using Samba for file transfers.
I have my 2 TB Western Digital green drives that were previously in my desktop running WIndows 7.  I have placed them in the server, and I can auto-mount then fine using ntfs-3g.  I have also setup sAMBA on the server, and it's working great, as long as the file is under about 4gb.

I know that there is a limit of 4gb on files when using fat32, but these are NTFS drives.

Let me give an example.  I am copying an .mkv file which is 8 gb.

I use my win 7 desktop so logon the Samba share.  I Cut the file from one share and paste to another share.  The two shares are on two physical drives in the server.
Let's call one drive mkv and the other divx.
So I try to copy an 8gb file from the divx drive to the mkv drive.
It will start up fine, and I see the file growing in size, so the copy is working. WHen it gets to exactly 4194304 kb the file will stop copying and timeout.
This happened to every single mkv I have tried to move.

I know it's a samba problem because i can log onto SSH and cp * /divx /mkv
and it will move all the files properly and not stop at 4194304 kb.

I have updated Samba, but I'm sure there is some sort of config I'm not aware of setting this hard limit, as it's happening to every file I try to transfer and only through Samba.

If anyone can help me, please do, thanks!

---

### Post by djspx on 2012-04-19
I think I should have posted this in the server platform forum.  If a moderator could kindly move this over there for me.
Thanks

---

### Post by dcstar on 2012-04-20
> **djspx said:**
> I think I should have posted this in the server platform forum.  If a moderator could kindly move this over there for me.
Thanks

If **you** want a thread moved then **you** Report the post. No moderators read the thousands of posts every day here.

---

### Post by s.fox on 2012-04-20
Thread moved to [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") at request of original poster.

---

