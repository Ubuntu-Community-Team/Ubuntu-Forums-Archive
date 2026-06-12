---
title: "JUST upload files to U1"
date: 2013-11-10
forum: Ubuntu One (CLOSED)
---

### Post by ben-brand on 2013-11-10
This is kind of driving me crazy, more so because I feel I should be able to figure this out.

I have a set of files that I JUST want to upload to U1, more an offload from my network. I do not want to synchronize them as that keeps a copy locally, defeating my purpose.

I have tried:

1) Create a folder in my storage space via the web interface and then manually upload the files to that folder via the the same web interface. BUT, the files are always synced back to my local U1-directory. The "more" drop down does not have an option to stop this behavior on that folder. 

2) Create a folder locally and start some files being synched. I then go to the web interface using the drop down "more" to "stop sync". But that then deletes the folder from my storage space. 

What else can I do. It would seem that just uploading some files to my storage and leaving them there must be trivial there but I cannot figure it out. I do not want to go back to drop box for this ....

What am I doing wrong? Is this even possible?

thanks
Ben

---

### Post by Irihapeti on 2013-11-10
I've done this, if I remember correctly, by creating a folder outside of your Ubuntu One folder and syncing it, maybe with only one file in it. Once that's done, go to the Ubuntu One panel and uncheck the "sync locally?" box. Once you've done that, you can upload files to it and they won't sync to your machine.

This only works with folders outside of your Ubuntu One folder.

---

### Post by ben-brand on 2013-11-10
Hi thanks, that is the #2 option I tried but that did not work. The folder is deleted from my Cloud when I uncheck "sync locally". To me this would also seem a very logical approach but it does not seems to work. 
cheers
Ben

---

### Post by Irihapeti on 2013-11-10
What version of Ubuntu are you running? (Just in case that makes a difference)

---

### Post by ben-brand on 2013-11-11
Hi, I am using 13.04 at the moment.

---

### Post by Irihapeti on 2013-11-11
That might be making a difference. I use 12.04.

I may get the chance to do some tests on a 13.10 install later (don't have 13.04).

---

### Post by ben-brand on 2013-11-11
Thanks, be great if you could help me out. This is driving me crazy ... ;-)

---

### Post by Irihapeti on 2013-11-11
I managed to test using 14.04 (development release, but probably not much different from 13.10 at this stage). No problems with choosing which folders to sync.

I did find a setting that you might have overlooked. Open the U1 control panel on your computer and choose the "Settings" tab. At the bottom, make sure that the "Automatically sync all new cloud folders to this computer" box is unchecked, and then click on "Apply these settings". You should then be able to add a folder using your browser and not have it sync to the computer.

---

### Post by ben-brand on 2013-11-12
Hi, just checked but both  "automatically ... " are unchecked in the settings TAB.

I do not understand why on the web control panel if you say  "stop sync" from the drop down it deleted that folder. It is as if U1 does not want me to store anything not being synced both up and down, regardless of any setting on either end.

thanks
Ben

---

### Post by ben-brand on 2013-11-12
OK, I think I found a work around.

1) create a empty folder locally, not residing in Ubuntu One home folder
2) in the U1 client, add that directory but make sure "sync locally?" is not checked
3) you can now delete the local folder
4) in the web interface you can now upload files to that folder, they will not be synced back down.

At the moment it seems to remain intact, but I might be relying on a current bug that you can delete the local folder. It does seem inconsistent that the folder in U1 remains intact where it was based on that local folder now gone. In any case this is all a bit confusing and needs some revisiting I feel.

thanks
Ben

---

