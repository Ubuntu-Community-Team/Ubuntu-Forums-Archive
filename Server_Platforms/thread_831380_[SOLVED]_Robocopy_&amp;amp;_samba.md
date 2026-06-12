---
title: "[SOLVED] Robocopy &amp;amp; samba"
date: 2008-06-16
forum: Server Platforms
---

### Post by weryl on 2008-06-16
Hi,

I've recently set up a home server on ubuntu and i successfully configured samba to share /data on my windows home network. I can access, modify and create files from CPUs on winxp.

The problem is that when i try to backup my files using robocopy from winxp, every single file is considered "newer" and is uploaded again on the server, erasing the previous copy. I've tried running my script multiple times and the files on my ubuntu server are always considered outdated.

I've been using this script for a few months on several windows machines so i know theres no problem there. Has anyone had similar problems?

Thanx alot,

Mike

Edit:
So it seems that the problem comes from the fact that FAT32 and EXT2 systems use different time precisions. I corrected my script by using robocopy /m (+ some other stuff).

---

### Post by prodigiousfool on 2008-07-20
Just to let you know, in case you don't want to have the Archive Attribute set, I was able to get around it by setting the robocopy /FFT. That seemed to fix it for me. 

```
robocopy.exe "F:\Entertainment" "Z:\Entertainment" /FFT /MIR /XF *.db /XD "lost+found" "Mythbusters" /XO /V /NDL /NS /NP
```

Thanks for your resolution though, it made me go back through and figure out why this was happening!

---

