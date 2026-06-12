---
title: "Synchronisation Problem"
date: 2011-05-09
forum: Ubuntu One (CLOSED)
---

### Post by ChristosHDJ on 2011-05-09
Hi everyone. I have just installed the new version of Ubuntu - 11.04, which I think is excellent.

Problem:
--------
I am operating on two separate computers, one at home and one at the uni. I have activated the Ubuntu One (U.O.) synchronisation app and I have chosen two folders to be in complete sync with U.O. I have chosen to sync the same folders on my other computer(uni) as well. I worked at the uni today and when I came home thinking that everything would be synced, I found that I had the previous version of whatever I had worked on. 

I would suspect that the last version of whatever I have worked on at the uni hasn't been uploaded, but the thing is that the files are as if I never touched them today. In other words it's no synchronisation has taken place at all. 

Truth is that I was able to download all files from U.O. when I installed Ubuntu 11.04, so I know it works just fine. I know that I must be doing something wrong but I don't know what that is. 

I'd appreciate a response on this.

Thanks!

---

### Post by duanedesign on 2011-05-10
> I would suspect that the last version of whatever I have worked on at the uni hasn't been uploaded, but the thing is that the files are as if I never touched them today. In other words it's no synchronisation has taken place at all. 

Are the new files you changed at Uni showing up on [https://one.ubuntu.com/files?](https://one.ubuntu.com/files?) That will help us figure out which machine we should investigate. Are the files not getting from the Uni machine to the cloud, or are the files not getting from the cloud to your home box?

Something else you might check is what happens if you change a file at home, does it show up at the Uni machine?

thank you,
duanedesign

---

### Post by ChristosHDJ on 2011-05-10
Thanks for the reply.

I am at the uni now. 

I was able to see the folder tree at [https://one.ubuntu.com/files?](https://one.ubuntu.com/files?), but all folders are empty, except the Pictures folder which is still not fully synced. At the same time the ubuntu one app looks like it is trying to upload and sync the documents file but nothing seems to be changing. 

I have two folders synced. One of them is "Pictures" and the other is "Documents". 
Now the story is like this:
1. When I first synced them I was at the uni. Everything was fine.
2. Went home, installed Ubuntu 11.04.
3. Synced the same folders - "pictures" and "Documents" with Ubuntu one.
4. Received a warning message saying that this being the first time files from both folders - uni's and home's - will be merged. 
5. Clicked Ok. Everything worked just fine. 

Problem:
=======
1. Didn't wokr at home at all.
2. Came at the uni. Worked at the uni. Received multible messages saying that everything is synced. Folders were even appearing with the green tick above them.
3. Went home to keep working. Waited for Ubuntu one to sync. 
4. Nothing changed. It was as if I never worked at the uni.
5. Made some simple changes at home. Added some pictures in the picture folder and in some others.
6. Came at the uni today. Found the changes I had made yesterday locally. I couldn't find the folders I had synced from home.
7. Received your reply. Entered the  [https://one.ubuntu.com/files?](https://one.ubuntu.com/files?) online where I found that I can see the "Pictures" folder fully synced. The "Documents" folder contains only the tree of the folders contained. Nothing more.

Hope all these will be helpful. For the time being I will stop the sync and free the server space (from the uni). Then I will try to sync everything at home again today. I will make a backup just in case.

Cheers,

--C

---

### Post by duanedesign on 2011-05-11
can you check your computers to see if anything is in this file.

~/.cache/ubuntuone/log/syncdaemon-exceptions.log

You may need to type Ctrl + h or View --> Show Hidden Files to see the .cache directory in your $Home.

thank you,
duanedesign

---

### Post by ChristosHDJ on 2011-05-16
Found the log file. Useful information inside it. Got What you were trying to find out. 

I sorted the problem out though. I deleted everything from the server and uploaded it again from the uni. Since I synced the machine at home through U.O. everything's been working just fine.

Nice to know where to look for problems though.

Thanks. Cheers,    ;)

Christos

---

### Post by duanedesign on 2011-05-16
Please feel free to post messages here on the forums for help. I am also on IRC alot.
network: irc.freenode.net
channel:  #ubuntuone

glad yuo got it going!
duanedesign

---

