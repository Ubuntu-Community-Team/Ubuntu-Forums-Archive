---
title: "HOWTO: Share Firefox &amp; Thunderbird profiles on a Windows 7 - Ubuntu 11.04 dual boot"
date: 2011-09-07
forum: Tutorials
---

### Post by harlequin_ on 2011-09-07
Hi everyone,

I'll try to write the instructions down for having a single profile for Firefox (or/and) Thunderbird on a PC which has Ubuntu and Windows 7 installed. The assumption here is, however, that you automount your Windows partition when you boot into Ubuntu, okay?

For quite some time I've been using a dual boot setup for Windows 7 and Ubuntu 11.04 (win for gaming from time to time). In total I used to have four separate profiles on these two systems, and it was a bit of a mess, especially in Firefox, when looking for a bookmark that is present on Ubuntu Firefox profile when I'm on WIN7. Anyway, you get the idea. It is not nice. It is a nightmare if you are obsessed with unnecessary things on your PC (i'm waiting for the great day for win to be unnecessary :d).

Anyway. I was looking for a method that would enable me to just have one single profile for each of these applications that I can access and configure from either system. So you bookmark something in Firefox in Ubuntu, and when you boot in WIN7 it's there. You send a mail from WIN7, you boot into Ubuntu and that mail is right there in your sent folder. That is what I wanted. If that is also what you want, keep on reading.

Well, of course there are already tutorials avaiable for such a need. Some are:

[http://ubuntuforums.org/showthread.php?t=203524](http://ubuntuforums.org/showthread.php?t=203524) 
[http://www.savagereactor.co.uk/linux/fedora/ff_tb_shared_profile.html](http://www.savagereactor.co.uk/linux/fedora/ff_tb_shared_profile.html)
[http://blog.shevin.info/2007/05/share-thunderbird-and-firefox-data.html](http://blog.shevin.info/2007/05/share-thunderbird-and-firefox-data.html)

But these, I don't know.. Some require using profilemanager. Some are much more complicated than they need to be. There are many. Anyway, I found one that (almost) directly meets my desires with a few basic terminal commands (don't be afraid ubuntu beginners!! I promise you can do it):

[http://blog.nikolaidis.com/2007/10/30/dual-boot-your-bookmarks-and-email-on-ubuntu-710-guty-gibbon/](http://blog.nikolaidis.com/2007/10/30/dual-boot-your-bookmarks-and-email-on-ubuntu-710-guty-gibbon/)

Now, if you just do the things written here it won't work. Because if you follow these instructions, all you will end up doing is having a soft link to your WIN7 profiles in your Ubuntu 11.04 profile folders. That is not what you want. You want to replace the profiles created by Ubuntu with links that point to your profiles in Windows 7 (the other way around would be possible if you could as easily access to your Ext4 Ubuntu partition from your NTFS Windows partition). So when you change something in Ubuntu regarding these two applications, it will change in Windows partition too. And when you change something (eg. add a bookmark to Firefox), because you have the profile linked in the Ubuntu system to the partition you automounted, you'll have it in Ubuntu too. Anyway. Too much talk. What you need to do:

NOTE: It is advisable that you get a backup of all the profiles (or profile folders) mentioned below before you start doing this. These steps are really simple but it's always nice to have backups, we all do mistakes. If you do a mistake, don't panic and just use your backed up profiles and have them restored in their original directories)

1 - Launch both Firefox and Thunderbird at least once in both Ubuntu and Windows 7. Just launch so that automatically a profile is created for each in both systems.

2 - Configure your system so that you automount Windows when you boot into Ubuntu. You can follow the perfect guide [here]("http://computerandu.wordpress.com/2011/05/12/how-to-mount-a-windows-partition-on-linux-automatically-on-each-start-up/")

3- Open a terminal in Ubuntu and type
```

ln -s /<path_to_your_windows7_partition>/Users/<username>/Application\ Data/Thunderbird/Profiles/<windows7_thunderbird_profile_id>.default/ /home/<username>/.thunderbird/
```Don't forget to replace <path_to_your_windows7_partition>, <username> and <windows7_thunderbird_profile_id> with your own names/ids.

4- Now go to your ".thunderbird" folder in your 

/home/<username>/

directory. It's a hidden folder (hence the "." at the beginning of it) so you need to Ctrl+H to see it (or go to "view" on the top panel and click "show hidden files"). Now you should be able to see your ".thunderbird" folder. In it, you will see two profiles. One is the link that you just created with the command above, and the other is your Thunderbird profile created in Ubuntu. Delete the second one (you can tell which is which by the folder icon. The one you should delete is the one that looks like a regular folder rather than a link). 

5- Open profiles.ini in the same folder (/home/<username>/.thunderbird/) with a text editor, and change the line

```
Path=<deleted_profile_name>.default
```to

```
Path=<linked_profile_name>.default
```Save and close the file. Now when you launch Thunderbird, and you should see what you would see when you open Thunderbird from Windows. Change anything, send a mail, recieve a mail.. Open Windows, and it will be there. Do something in Windows, open Ubuntu, it will be there.

Same with Firefox. You need to apply exactly the same procedure, but the folder locations are different. So you need to account for that in the above command. For Firefox, the procedure would go like

1 - ```
ln -s /path_to_your_windows7_partition/Users/<username>/Application\ Data/Mozilla/Firefox/Profiles/<profile_id>.default/ /home/<username>/.mozilla/firefox/
```Again, after you do this, delete the Firefox profile created in Ubuntu (it is in /home/<username>/.mozilla/Firefox). Open "profiles.ini" with a text editor, and again change the corresponding 

```
Path=<deleted_profile_id>.default
```to 
```

Path=<linked_profile_id>.default
```Don't forget to replace the <profile_ids>  in the above codes with your corresponding profile IDs. Save and close the file. When you launch Firefox now, you should have all your bookmarks, settings etc in your Windows 7 Firefox profile. All of it.. And of course the best part is when you change anything from either of the systems, it is "synced" in the other system.

That's it. 
This is my first howto: and I'll make this a better tutorial as soon as I have some more time. Still, hope it helps.

---

### Post by truckmuffler on 2013-05-15
Many thanks, Harlequin_.

This was exactly the function I wanted to implement and following your instructions worked perfectly for me.

Cheers,
John

---

### Post by truckmuffler on 2013-05-26
After submitting previous thanks, made a change to fstab to get my Windows partition to auto-mount, so had to update the profile link.
Found it much easier to edit the profile.ini file to set Relative=0 and enter the new path directly in the path field.

Still grateful to _Harlequin for giving me the confidence to start messing around, but hope this helps others too.

---

### Post by harlequin_ on 2013-08-06
Yes, that indeed is a more elegant approach to set Relative=0 and enter directly the path to the mounted partition. Now I'm using your method :-)

---

