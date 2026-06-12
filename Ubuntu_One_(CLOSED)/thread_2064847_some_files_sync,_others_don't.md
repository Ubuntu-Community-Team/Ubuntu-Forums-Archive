---
title: "some files sync, others don't"
date: 2012-09-30
forum: Ubuntu One (CLOSED)
---

### Post by markMDW on 2012-09-30
On both my Ubuntu 10.04 and 12.04 machines I have access to UbuntuOne from the File Manager.  Lots of the files I've posted to the UbuntuOne cloud from the web browser don't show up there.  It seems things don't synchronize properly between the files I have on the cloud according to the web, and according to what the File Manager shows.

I've also noticed from the File Manager that some of the file icons have a check mark in it.  Does anyone know what this means?  I imagine it has something to do with synchronization.   If I right click I can't add or remove those checkmarks.  What are they for.

Also, from the File Manager alone, my files don't seem to synchronize between my laptop and desktop.  For example, from both machines I have access to a particular folder from the File Manager.  However, the 12.04 machine has a subdirectory that's viable in it.  On the other machine that subdirectory doesn't even exist according to File Manager.  I forget which machine placed what and how.  How do I make that folder visible to me anywhere and everywhere (but not publish it to the whole world).  It has a little checkmark on the icon; I thought that means it's synchronized. 


Also, I have a UbuntuOne application from the 12.4 machine, but not the 10.04 machine.  It says from the Ubuntu Software Center on both machines that this is installed, but I only have an available application.   Is there supposed to be a UbuntuOne Application on my 10.04 machine (Ubuntu Software Center says there is), or was the actual application invented later for 12.04? 

After using UbuntuOne for several years I'm still trying to figure out how to access all my files from all computers using the several methods of placing files there (File Manager, Web and UbuntuOne Application).  It's frustrating to find that my files availability are subject to how I put them there in the first place, or by which computer put them there, and I still don't understand.

update:
One last thing, there is a folder called "Shared With Me" that has a lock icon on it.  I tried to place files into the folder using the File Browser, hopefully to share everywhere I am ...well, it's locked and I can't place any files in it.  I can't unlock it.  BTW, I did find that my 12.04 laptop sees all the files I've placed from everywhere that I still recall placing; the problem seems to be with the 10.04 machine.

I use UbuntuOne mainly because it syncs my Tomboy Notes perfectly! :KS

---

### Post by markMDW on 2012-09-30
Ubuntu 10.04 without Unity.  The fix:

It turns out that the 12.04 UbuntuOne "application" is a setting or preference in 10.04.  I found the program not under the applications menu but under the Preferences menu and in the "Control Panel".  Unity doesn't have Applications, Settings, Preferences, Control Panels etc to search through.. it just has that bar, and that was where I was clicking.   I guess if it's going to be in two places in 10.04 they should put it in a third place to cover all three bases; Applications was where I was looking.   No wonder the Unity bar is becoming more and more popular.  Putting everything almost everywhere leads to confusion and too many places to look for things.

I found that the fix is within a setting in the UbuntuOne "Dialog" within the control panel (if you have it installed from Ubuntu Software Center).. or under preferences below:

System> Preferences>UbuntuOne 
then click the [Services] tab
    ...it may take several minutes for the dialog box to switch over to the services tab; it's busy not locked up.
then "checkmark the [File Synchronization] box
    ..reboot

my missing files slowly came back.

Now I'm wondering if its safe the edit the files from UbuntuOne, or If I have to copy them to another folder, edit them, then copy them back to avoid corrupting them.

I'm happy, my files appear to be syncing again.

BTW, I thought the whole purpose for UbuntuOne was to have all your files posted there available everywhere you go by all the applications [i.e. File Browser] that uses it.  Didn't figure it was an extra Option you had to find and checkmark.  I've got tons go gigabytes on my local machine available.  The reason I use it is to synchronize file, not to get a few extra "free" megabytes of local capacity I don't need.  :lolflag:

Anyway, my files are syncing..  good news!

---

