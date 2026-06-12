---
title: "Help in finding one's way around server setups."
date: 2020-01-28
forum: Server Platforms
---

### Post by Arunomi on 2020-01-28
Hi I'm trying to find my way around server setups but I can't find a solution that fits my problems.

I know how I would want it but I can't seem to find what I need to setup to realise it.

So I thought that I could throw the question in this forum.

I have some old hardware I'm planning on using to make a server that for the most part only will be a fileserver. It should handle my files so I can access them from my Ubuntu laptop and my windows 10 and 8 computers. 

There should be some security around the files so that if I by accident delete them I can undo that delete. 
There should be some compressed backups that I can store externally.
I would want some fix so that when I browse a folder with images it makes thumbnail for them but it shouldn't take 20 min to generate 500 thumbnails.
 
Then I'm planing on exploring nextcloud to replace some of the Google services that I have on my phone. 

So if any one could point me in the right direction I would be grateful. 

Best regards arunomi

---

### Post by TheFu on 2020-01-29
What is "old hardware?"

Samba, NFS, ssh, sftp, scp are how I'd start after setting up the storage and backups.  
If you are new to Linux, some background skills are necessary.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) There isn't any point-n-click solution for this stuff. It is all CLI, text config files.

---

