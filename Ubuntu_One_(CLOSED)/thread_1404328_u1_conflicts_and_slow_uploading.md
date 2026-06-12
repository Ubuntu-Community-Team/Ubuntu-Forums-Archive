---
title: "u1 conflicts and slow uploading"
date: 2010-02-11
forum: Ubuntu One (CLOSED)
---

### Post by traceydecker82 on 2010-02-11
Hello. This is my first post, so I am not that great with the lingo. Bare with me!

I keep getting u1conflicts in my Moneydance backup. For example, I am usually doing something in Moneydance daily. However, when I went to open it up yesterday, it didn't save anything from the previous 3 days. The last 3 days worth were u1.conflict. Moreover, this is the only computer that we do the Moneydance transactions on. 

My other question is about the speed it is taking to upload all my pictures. Granted, I do have A LOT of pictures (3000+), but it is taking forever to upload them. When U1 is running, it takes all of the bandwidth. My husband already posted something about limiting the bandwidth problems. What I am wondering though is if there is a way to get all my pictures backed up faster? I have been trying to back them up for about a week now. In 6 hours, it only backed up 115 files of over 3000, and that is using up all of our bandwidth.

Thanks in advance! Any help is appreciated!

---

### Post by joshuahoover on 2010-02-11
> **traceydecker82 said:**
> Hello. This is my first post, so I am not that great with the lingo. Bare with me!

I keep getting u1conflicts in my Moneydance backup. For example, I am usually doing something in Moneydance daily. However, when I went to open it up yesterday, it didn't save anything from the previous 3 days. The last 3 days worth were u1.conflict. Moreover, this is the only computer that we do the Moneydance transactions on. 

This isn't behaving right. I'd like to get to the bottom of what is causing the u1conflict files to occur even when you're not making changes to the files and only have the one computer. If you can do the following, it will help us determine what the problem might be:


[LIST=1]
[*]Quit the Ubuntu One client
[*]Open (or create if it doesn't exist):  ~/.config/ubuntuone/syncdaemon.conf 
[*]Add the following 2 lines to this file and save: 
[main] 
 log_level = DEBUG 
 
[*]Correct the u1conflict files (decide whether to keep the u1conflict files or the originals)
[*]Start the Ubuntu One client
[*]Create a new bug report by right-clicking on the Ubuntu One client and selecting "Report a problem"
[*]Attach  ~/.cache/ubuntuone/log/syncdaemon.log and  ~/.cache/ubuntuone/log/syncdaemon-exception.log to the bug report
[/LIST]

> **traceydecker82 said:**
> 
My other question is about the speed it is taking to upload all my pictures. Granted, I do have A LOT of pictures (3000+), but it is taking forever to upload them. When U1 is running, it takes all of the bandwidth. My husband already posted something about limiting the bandwidth problems. What I am wondering though is if there is a way to get all my pictures backed up faster? I have been trying to back them up for about a week now. In 6 hours, it only backed up 115 files of over 3000, and that is using up all of our bandwidth.

Thanks in advance! Any help is appreciated!

There is a known performance issue when trying to synchronize a lot of files, no matter how big or small those files may be. We are working on fixing this and hope to have it released soon.

Thank you,

Joshua

---

### Post by mickcalcara on 2010-02-16
traceydecker82, I use Moneydance too and Ubuntu One. I have corrupted Moneydance files before due to possibly saving frequently. I eventually set Moneydance to write the backup files to the Ubuntu One folder. The main file sits in a non-Ubuntu One folder. 

Joshua, maybe you can elaborate on this. Can performing frequent saves to a file that is being sync'd up cause any potential for corruption in the file being sync'd  or the sync process?  

thanks.

---

### Post by joshuahoover on 2010-02-17
> **mickcalcara said:**
> Joshua, maybe you can elaborate on this. Can performing frequent saves to a file that is being sync'd up cause any potential for corruption in the file being sync'd  or the sync process?  

No, there shouldn't be corruption of files that are frequently saved. In the past we've had users get conflicts on files that were saved frequently but this should not occur. If it happens to you, please file a bug with debug mode turned on.

Thank you,

Joshua

---

