---
title: "File search using Hyper-V"
date: 2019-01-09
forum: Virtualisation
---

### Post by 79schultz on 2019-01-09
I am quite new to Ubuntu. I am trying to learn how it all works. I have installed Ubuntu 18.04.1 LTS on Hyper-V on my Windows 10 Pro machine so I can start learning more about it. One thing I have learned using Putty on our SMEServer is how fast you can find a file. How can I find a file on my Windows 10 machine using Terminal in Ubuntu on Hyper-V? Windows 10 searches are pathetically slow.

---

### Post by slickymaster on 2019-01-09
Thread moved to **Virtualisation** for a better fit

---

### Post by TheFu on 2019-01-09
If you are searching inside Windows, that seems to be a Windows question, better asked elsewhere.  
Nothing to do with virtualization.

For finding files quick on any Linux there is a tool called **locate** which is part of the updatedb package (or sometimes the mlocate package).  This is a shell command that looks for filenames. No GUI. It is very fast.

If you need a more thorough search took, there are many. I use **recoll**, but know that the recoll indexes can become huge. There are other options, but I've only looked at them for setting up server-based searching.  That doesn't fit what most desktop end-users like you would want.

The issue with both those tools is that indexing has to be performed before the search, so any new files won't be indexed until the next indexing task runs, usually daily.

If you need to search new files since the last indexing was performed, then you can use the 'find' command.  It scans the entire directory structure you set in the options, which can be slow.  If I know there's a file, but it is new, so not yet indexed, I'll use a find command like this ```
 find . -ctime -1 -iname "*part-of-the-filename*" -print 
``` to find it.  If I need to look inside, I'll include the "strings" command. ```
 find . -ctime -1 -iname "*part-of-the-filename*" -exec strings {} | egrep "regex" \;  
```   To understand complex commands, there are websites like [https://explainshell.com/](https://explainshell.com/) until you learn to read manpages.

If you are asking how to use Linux to search Windows. You can't unless the storage is shared and included in the indexes for the Linux tools.

Or am I missing the question completely?

---

### Post by 79schultz on 2019-01-09
Thank you for your reply and the suggestions. 

In my 'File' hierarchy I can see and open the Windows shared drives. I would like to search those shared drives with the *locate* command. 


I'm still new to this forum, couldn't figure out how to add a screenshot, but my shared drive is drive D:. In the File app I can open it no problem.

---

### Post by TheFu on 2019-01-09
I don't think **locate** will "see" unreal mounts, like happen when using the file manager GUI.  If you mount it using the fstab, then you can configue the /etc/updatedb.conf file to scan it.

I don't know how hyper-v shares storage, but you can always share it using CIFS shares and mount it using a CIFS-client from inside Linux.  Basically, you treat both machines like they are physical machines.

---

