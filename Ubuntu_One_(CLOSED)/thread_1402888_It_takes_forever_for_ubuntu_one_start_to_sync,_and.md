---
title: "It takes forever for ubuntu one start to sync, and sometimes fail."
date: 2010-02-09
forum: Ubuntu One (CLOSED)
---

### Post by markinf on 2010-02-09
Seriously, it takes a LONG TIME, over 1h+ to ubuntuone start to sync. And sometimes it just fails? Is it only me or this happening with someone else?

EDIT:
Right know is not even syncing anymore. It just doesnt sync. I add files/folder and it doesnt sync.

EDIT2:
After ~1h30min it's STARTING TO UPDATE. This is not acceptable, serious. Ubuntu ONE Should UPDATE right away it detects file has changed/added.

---

### Post by feydrutha on 2010-02-10
I am also unable to sync my ubuntu one folder today... on two different laptops i cannot get any files to be updated, although it sometimes says it is updating my files when I hover over the icon.

I have been using ubuntu one regularly (as recently as the last weekend) and had not experienced this problem before.

---

### Post by Mia1990 on 2010-02-12
ubuntu one loads slow on start up for me it's sync's fine for now before a update i couldn't get on to sync and after a update it started working but loaded slow.

---

### Post by joshuahoover on 2010-02-15
> **Mia1990 said:**
> ubuntu one loads slow on start up for me it's sync's fine for now before a update i couldn't get on to sync and after a update it started working but loaded slow.

Apologies for the slow performance. We were experiencing some server side problems that should now be fixed. There are still some performance related issues we're working on fixing but the slow startup and updates should be fixed now.

Thank you,

Joshua

---

### Post by vollmey on 2010-02-15
> **joshuahoover said:**
> Apologies for the slow performance. We were experiencing some server side problems that should now be fixed. There are still some performance related issues we're working on fixing but the slow startup and updates should be fixed now.

Thank you,

Joshua

Seems to be working much better for me.  Thanks !!  :)

---

### Post by lz1dsb on 2010-02-23
I'm experiencing this problem at the moment. I have few folders in the UbuntuOne directory. This morning I put some new files in the one of th subfolders and until now the files are not synchronized. When I click the UbuntuOne icon, it shows me "Your files are up to date." When I hover the mouse pointer over the icon, I get "Updating files...". Also the newly pasted files have a red dot with something like the X in it. When I'm in the UbuntuOne folder there's a button Connect. I've pressed it several times, but it isn't changing. So I guess that my synchronization problem is that I'm not connected. How to debug this? I've restarted the UbuntuOne agent several times... I'm using a virtual machine running Ubuntu 9.04 Jaunty Jackapole.


Regards,
Boyan

---

### Post by lz1dsb on 2010-02-23
All right, restarting the machine did solve the issue but partially. Now I have one file which is still not synchronized. I'll leave it during the night, to check if it would synchronize. So I'm confused by the way UbuntuOne should work. I thought that dropping a file into the UbuntuOne folder, or its subfolders should trigger the synchronization. Well this doesn't happen always. It would have been nice If I could have a manual function to synchronize. And also the indication during the sync process isn't very informative at all...

Cheers,
Boyan

---

### Post by joshuahoover on 2010-02-23
> **lz1dsb said:**
> I'm experiencing this problem at the moment. I have few folders in the UbuntuOne directory. This morning I put some new files in the one of th subfolders and until now the files are not synchronized. When I click the UbuntuOne icon, it shows me "Your files are up to date." When I hover the mouse pointer over the icon, I get "Updating files...". Also the newly pasted files have a red dot with something like the X in it. When I'm in the UbuntuOne folder there's a button Connect. I've pressed it several times, but it isn't changing. So I guess that my synchronization problem is that I'm not connected. How to debug this? I've restarted the UbuntuOne agent several times... I'm using a virtual machine running Ubuntu 9.04 Jaunty Jackapole.


Regards,
Boyan

Hi Boyan,

I'm not sure what's causing these issues. If you want, you can hop on Freenode IRC at #ubuntuone and ask for joshuahoover or rye there for some real time support. If you can't do that, then you're next best bet is to file a bug report by right-clicking on the Ubuntu One client applet and selecting "Report a problem". This will include some debug files we can look at to help you get back up and running. 

Thank you,

Joshua

---

### Post by patua on 2010-02-23
I'm having the same problem here. The changes I made to the U1 folder still haven't been replicated in the server.

By the way, I use tomboy notes and I also can't access my notes online, nor syncronize them with my tomboy client!!

---

### Post by lz1dsb on 2010-02-24
Hi Joshua, 
I just filed a bug #526878. 

Cheers, 
Boyan

---

### Post by markinf on 2010-02-26
I still have the problem. Ubuntu one updates files only when it feels like :'/

---

### Post by joshuahoover on 2010-03-01
> **markinf said:**
> I still have the problem. Ubuntu one updates files only when it feels like :'/

Sorry to hear this is still an issue. Did you file a bug? If so, can you let me know the number so I can make sure it gets attention? 

Whether you've filed a bug or not, can you do the following to help provide us with more debug information?

1. Quit the Ubuntu One client
2. Open (or create if it doesn't exist): ~/.config/ubuntuone/syncdaemon.conf
3. Add the following 2 lines to this file and save:
[main]
log_level = DEBUG

4. Open the Ubuntu One client
5. Try to reproduce the problem you're experiencing
6. File a new bug by right-clicking on the Ubuntu One client and select "Report a Problem"
7. Attach ~/.cache/ubuntuone/log/syncdaemon.log to the bug report

Also, I'm on #ubuntuone on Freenode IRC, Monday-Friday 14:00-22:00 UTC if you'd like more real time help.

Thank you,

Joshua

---

### Post by nutznboltz on 2010-10-02
@joshuahoover Thanks for the pointers, 

running
```
tail -f ~/.cache/ubuntuone/log/syncdaemon.log
```
increased my confidence that something is happening. :)

I was surprised to see that a large directory tree had been copied into itself as if I had dragged a folder into itself, but how can anybody do that?  I don't remember issuing any recursive command line copy requests either.

I used the web UI to delete the folder-inside-the-folder.  Now my local desktop client is busy erasing files.

---

### Post by tubunu on 2011-09-14
I have a 23KB Calc file that I need to update whenever I make change to the data in it and it takes around 5min to upload it, why so long? Am I missing something? Thanks.

---

### Post by tubunu on 2011-10-23
> **tubunu said:**
> I have a 23KB Calc file that I need to update whenever I make change to the data in it and it takes around 5min to upload it, why so long? Am I missing something? Thanks.

Can anyone shed some light on this? Maybe I'm not doing it right...?

---

### Post by theSshow on 2011-10-26
Don't know if anyone is still experiencing problems, but when I try to upload a file via the client on 11.10 it seems to be taking forever.

The command line seems to indicate that the file has finished uploading: 
```
$ u1sdtool --current-transfers
Current uploads:
  path: /home/XXX/Ubuntu One/XXX.zip
    deflated size: 41745048
    bytes written: 41745048
Current downloads: 0

```

But the Ubuntu One control panel still says "File Sync in progress...".  Moreover, the file is not there when logging in to Ubuntu One via the browser.

---

