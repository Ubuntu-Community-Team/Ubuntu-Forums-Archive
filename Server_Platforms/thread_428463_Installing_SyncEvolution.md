---
title: "Installing SyncEvolution"
date: 2007-04-30
forum: Server Platforms
---

### Post by CybaCowboy on 2007-04-30
Hi,


Can someone please point me in the direction for instructions to installing "SyncEvolution", for use with the Evolution e-mail client?

Thanks!


[i]
Edit: I've downloaded "syncevolution-0.5-evolution-2.8.1.tar.gz" from the SynceEvolution page and copied the folder "sheduleworld_1", however when I get to step one of the instructions:

> **NinjitsuStylee said:**
> 
Open the extracted folder for syncevolution and find the "etc" directory.  Inside you'll find another directory called scheduleworld_1.  Copy this to your /home/.sync4j/evolution directory (so that it becomes /home/.sync4j/evolution/scheduleworld_1)


There is no ".sync4j" folder found at /home/.sync4j/evolution and Ubuntu does not allow me to manually create this folder!


The instructions I am referring to can be found at:
[http://ubuntuforums.org/showthread.php?t=190938](http://ubuntuforums.org/showthread.php?t=190938)
[/i]

---

### Post by maddentim on 2007-05-03
I have used this tutorial successfully.  Setting up the config files is the trickiest part.  You can just cut and paste the commands to get it installed.

EDIT: forgot the link!

[http://ubuntuforums.org/showpost.php?p=2532774&postcount=55](http://ubuntuforums.org/showpost.php?p=2532774&postcount=55)

---

### Post by Th3sandm4n on 2007-08-23
Thanks for the easy tutorial, did everything fine but when I try to sync I get:
> 18:00:05 GMT -6:00 [INFO] - Synchronization URL: [http://sync.scheduleworld.com/funambol/ds](http://sync.scheduleworld.com/funambol/ds)
18:00:05 GMT -6:00 [INFO] - Preparing synchronization of addressbook...
18:00:05 GMT -6:00 [INFO] - Preparing synchronization of calendar...
18:00:05 GMT -6:00 [INFO] - Preparing synchronization of todo...
18:00:09 GMT -6:00 [ERROR] - Client not authenticated
18:00:09 GMT -6:00 [ERROR] - Error in preparing sync: 

Any idea?

---

### Post by psykar on 2007-09-28
Same problem here... Have you found a solution to your problem?

---

### Post by Th3sandm4n on 2007-09-28
Ya I found a solution, I had put in my OLD scheduleworld password (the number one) instead of the updated one I had made. :(
Now it works fine, except that it can't sync TO Google Calander, just FROM it. But that's not that big of a deal. I just had Google Calander as a midway point in case I didn't have my laptop or my desktop. As long as those sync fine, I'm okay.

---

