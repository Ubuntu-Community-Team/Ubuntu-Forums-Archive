---
title: "Multiple hard drives to choose from in Virtualbox"
date: 2010-09-07
forum: Virtualisation
---

### Post by speedracer2010 on 2010-09-07
Hello all. I just got my first virtualbox up and running and found I have a small problem. I have two physical hard drives in my tower case. The first hard drive holds the operating system and everything associated with it. The second drive is a data disc. What I would like to do is run my program (accounting for instance) in the virtual box but tell it to store the data on the second physical hard drive where the data IS. I tried the 'manager' and got to the hard drives and the data file/folder/directory with the correct data folder and clicked add but nothing happened. CAN/IS this possible? IF so what steps do I need to take to accomplish this? Thanks...

---

### Post by howefield on 2010-09-07
Shared Folders ?

[http://www.virtualbox.org/manual/ch03.html#id2654839](http://www.virtualbox.org/manual/ch03.html#id2654839)
[http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

Also can be seen in the video tutorials here...

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

As a side issue, you can also run your VM from your second disk, for better performance.

---

### Post by speedracer2010 on 2010-09-07
Thanks for the quick reply I will play with it and see what develops.....Have you used this function yourself?

---

### Post by howefield on 2010-09-07
> **speedracer2010 said:**
> Have you used this function yourself?

Yes, Ubuntu host with XP guest and works very well. I generally only use the feature to access/transfer files between host/guest. My reasons for using a windows VM are few.

---

### Post by speedracer2010 on 2010-09-07
I believe I ran into a small snag. As I stated earlier the HOST is on physical hard drive 1 and the data on physical hard drive 2. It states in the reference you provided under shared folder "shared folders must physically reside on the host and the shared with guest. This is NOT the way I am configured. As I read it I would have to move/copy the data to a folder on the OS drive and then set up from there. Unfortunately, the changes to the data on the OS drive will not be made to the data drive. While this may not seem a problem IF I need to go back and use the 'other' OS the data would be out of sync. I hope this makes sense to you as I may not be explaining it the best. SO, am I screwed or can this still somehow be made to work. Thanks..

---

### Post by lbrty on 2010-09-08
> **speedracer2010 said:**
> I believe I ran into a small snag. As I stated earlier the HOST is on physical hard drive 1 and the data on physical hard drive 2. It states in the reference you provided under shared folder "shared folders must physically reside on the host and the shared with guest. This is NOT the way I am configured. As I read it I would have to move/copy the data to a folder on the OS drive and then set up from there. Unfortunately, the changes to the data on the OS drive will not be made to the data drive. While this may not seem a problem IF I need to go back and use the 'other' OS the data would be out of sync. I hope this makes sense to you as I may not be explaining it the best. SO, am I screwed or can this still somehow be made to work. Thanks..

What data are you speaking about? Please clarify. As I understand it, you are working in the virtual machine and would like to save the data from within the virtual machine to the 2nd hard drive. Did I summarize it correctly?

---

### Post by howefield on 2010-09-08
> **speedracer2010 said:**
> SO, am I screwed or can this still somehow be made to work. Thanks..

No, you are not.

I read that as the shared folder needs to be accessible by the host, not necessarily on the same physical drive.

I have a similar setup as you, ext4 disk with Ubuntu on it, and another which is ntfs and is used primarily for data.

I have shared a folder on the ntfs drive that the XP guest sees perfectly.

Set the folder you want to share in the VM settings dialogue. Then map the drive in your guest accordingly. (Right click the My Computer icon on the desktop and select Map Network Drive)

As per the screenshot, "Linux on Vboxsvr (Z: )" is a shared folder that doesn't reside on the same physical disk as the host system. Applications read and write from it perfectly.

---

### Post by TNT1 on 2010-09-08
Shared folders should work. Virtualbox sets them up as networked drives, so any drive/location the host sees should be accessible.

---

### Post by speedracer2010 on 2010-09-08
So, IF I understand correctly, I can create a folder on my NON VM - ntfs data drive <DATA> and then copy the individual data folders (accounting data, database data, scanned document data, etc. all within THEIR own folders) INTO this DATA folder. Then in the VM I create a link to this <DATA> folder. Now, once that's done when each program runs within the VM would I be able to select in the 'global' or 'preferences' the place that I want to save the data to <DATA> (<Quicken>) or can I go to 'save' and click on the link to the <DATA> folder can I then select WITHIN this folder the individual programs data folder? Or is it just going to put it in <DATA> as one lump? Again, I hope this makes sense.. THANKS for the assist.... Please keep the answers coming...

---

### Post by howefield on 2010-09-08
If I read you correctly, I'd say you've got it.

Once you have set the data folders up and mapped them across to your VM, you would tell the applications where the folders are, and hopefully they are not so rigid that they won't be able to use folders outside their default expectation.

To be honest, you just got to get in there and give it go.

---

### Post by speedracer2010 on 2010-09-09
THANK YOU..... THat did the trick.

---

### Post by howefield on 2010-09-09
Thanks for the update, good to know you got it sorted.

---

