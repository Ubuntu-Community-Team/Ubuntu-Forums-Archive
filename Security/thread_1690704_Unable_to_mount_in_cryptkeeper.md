---
title: "Unable to mount in cryptkeeper"
date: 2011-02-18
forum: Security
---

### Post by smithark on 2011-02-18
hello guys,
     i am using cryptkeeper 0.9.4 on Ubuntu 10.10. but now i am unable to mount a folder in my documents i had encrypted. while trying to do so i get the following error message:

"The encrypted folder could not be mounted because the mount point is not empty"

i tried googling. but i just got one relevant result:
[http://ubuntuforums.org/archive/index.php/t-1533378.html](http://ubuntuforums.org/archive/index.php/t-1533378.html)

but it didnt help me. can anyone help me out? where is the problem?

cryptkeeper is wonderful program. however, i couldnt find a solution for my problem.

---

### Post by smithark on 2011-02-18
sorry for the double posting....

---

### Post by cariboo on 2011-02-18
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by openwater on 2011-08-29
> **smithark said:**
> hello guys,
     i am using cryptkeeper 0.9.4 on Ubuntu 10.10. but now i am unable to mount a folder in my documents i had encrypted. while trying to do so i get the following error message:

"The encrypted folder could not be mounted because the mount point is not empty"

i tried googling. but i just got one relevant result:
[http://ubuntuforums.org/archive/index.php/t-1533378.html](http://ubuntuforums.org/archive/index.php/t-1533378.html)

but it didnt help me. can anyone help me out? where is the problem?

cryptkeeper is wonderful program. however, i couldnt find a solution for my problem.
I was having the same issue and resolved it easily.  
-open the encrypted directory using the file browser
-delete any folders that still reside in it
-remount it using cryptkeeper!
all your files and folders will be there.  Sometimes when the drive is unmounted it seems to leave "ghost directories" of what you have in there.  delete those so the folder appears blank and it will remount fine with no loss of data.  cheers!

---

### Post by rickfitz on 2012-02-17
I had this same error message, and found there was no available space on the disk partition. Deleted a file, and all worked fine.

---

### Post by SolusDraco on 2012-06-01
> **openwater said:**
> I was having the same issue and resolved it easily.  
-open the encrypted directory using the file browser
-delete any folders that still reside in it
-remount it using cryptkeeper!
all your files and folders will be there.  Sometimes when the drive is unmounted it seems to leave "ghost directories" of what you have in there.  delete those so the folder appears blank and it will remount fine with no loss of data.  cheers!

Great thx, it`s working for me!

---

### Post by poolhustler on 2012-07-02
Hi I have just installed cryptkeeper on my computer. I have Ubuntu 12.04 installed.  The icon with a lock on it shows in the dock on the left side but when I click on it nothing happens. Does anybody know what I should do to get it to work?

---

### Post by rickfitz on 2012-07-02
Yes, it's a bug. It doesn't show up in the notification area, so you can't access it.

Easily resolved: see [bug 963522 comment #3]("https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/963522/comments/3").

To summarise: 
[LIST=1]
[*]Install and run 'dconf-editor'. 
[*]Add an extra string 'Cryptkeeper' under Desktop > Unity > Panel. Or just replace the existing list of allowed apps with 'all'.
[*]Log out and back in to make the change active.
[/LIST]

Works for me. (I used the 'all' option.)

---

### Post by fonsi2099 on 2013-03-07
> **SolusDraco said:**
> Great thx, it`s working for me!



I was having the same issue and resolved it easily.
-open the encrypted directory using the file browser
-delete any folders that still reside in it
-remount it using cryptkeeper!
all your files and folders will be there. Sometimes when the drive is unmounted it seems to leave "ghost directories" of what you have in there. delete those so the folder appears blank and it will remount fine with no loss of data. cheers! 

thank you this worked for me very fine too !!!

Ubuntu 12.10

---

