---
title: "Downloading my backups into a windows computer"
date: 2012-04-02
forum: Ubuntu One (CLOSED)
---

### Post by Mazate on 2012-04-02
Hola

Due to my main computer's motherboard being very elderly, it finally gave up the ghost a few weeks ago.  Unfortunately, the only computer I have access to at the moment is a windows computer that I can't install Ubuntu on.  All of my files are on my ubuntu one backup and I need to be able to at download my music and documents into that computer so I can use them.  Ideally I'd like to be able to use an FTP client or something but is there a way to do this other than doing it one file at a time on the ubuntu one website?

---

### Post by papibe on 2012-04-02
Hi Mazate.

Have you tried the Ubuntu One Windows client? Check it out [here]("https://one.ubuntu.com/downloads/windows/").

Regards.

---

### Post by Mazate on 2012-04-02
Yeah I tried that but it appears that in the windows version of Ubuntu One, it only allows me to backup my windows folders to U1 but doesn't appear to give me access to any files that are from my Ubuntu backup.  I could be doing something wrong but I've looked and haven't been able to find any opportunity to download to my windows computer from my Ubuntu backup.

---

### Post by 23dornot23d on 2012-04-02
maybe because they are stored differently - possibly need a way to view the 
different formated partitions that they reside on from windows .....

could try one of these viewers for windows to see linux partitions and see if it helps
as Ubuntuone could store the files ext3/4 ?

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by Mazate on 2012-04-03
These are two different computers, not two OS's on one computer.

---

### Post by papibe on 2012-04-03
Probably 23dornot23d's idea has to do with taking the hard drive out, and connect it to your Windows machine using an USB enclosure. Then you could use that software to browse the disk and copy what you need.

Regards.

---

### Post by 23dornot23d on 2012-04-03
If both computers are desktop machines ...... 

You could take the drive from the old machine and add it as a second drive in the windows machine ..... 

but if that is not possible or if one is a laptop .....  

A USB enclosure would allow the same task to be done.

(I was not sure with Ubuntuone if the reason you could not get to the Linux files to
download was due to the Windows machine not being able to see them .....on a 
file system that may not be viewable because its not set up that way.)

Forgive me if the way Ubuntuone stores Linux files is to a [COLOR=Red]**fat32 system or NTFS**[/COLOR] file
system ...... 

Because if it stores them to **[COLOR=Red]ext3/4 as I would expect[/COLOR]** ..... 

Then even if you connect using windows

I cannot see how you could view them ..... across a network connection with a Windows system that cannot see ext3/4 files normally ......

I believe Ubuntuone is a filesystem you view over the Net ....... and you want to view a
linux backup drive ......

Whichever way you do it you still need to be able to see ext3/4 .....

I think on a Windows machine you need some extra software to see the Linux files.
unless its changed since the last time I used one and they are now becoming Linux Friendly ....


Anyway just trying to give some useful advice ..... if it means nothing ignore it .....

---

### Post by duanedesign on 2012-04-06
When adding a new machine to your Ubuntu One account the files you are currently syncing should sync to the new computer. Have you added both machines to the same account? You should be using the same email and password that you used on the previous computer. Under the Devices tab you should see both machines listed. Check the Folders tab and make sure the folders you want have the Sync Locally option checked.

We generally do not recommend using Ubuntu One as a backup solution. Because Ubuntu One syncs files, not uploads them. So if you edit or remove a file from one computer, that file gets edited or removed from all computers. This can produce unexpected results if one is expecting a static back up.

---

