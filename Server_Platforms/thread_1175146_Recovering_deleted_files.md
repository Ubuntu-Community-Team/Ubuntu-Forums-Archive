---
title: "Recovering deleted files"
date: 2009-05-31
forum: Server Platforms
---

### Post by rwslippey on 2009-05-31
I'm running Ubuntu Server LTS.... I was working on my server and deleted a user that had an html directory with my entire website. I need some help getting my php and html files back. No I didn't make a backup... but thats going to be the first step when I get it all working again. I'm curious if ubuntu Server has maybe a trash bin somewhere where the files could be stored. Any ideas and help is greatly appriciated...

Thanks 

Rob

---

### Post by LepeKaname on 2009-05-31
What kind of filesystem are you using? (ext3, ext2, ...etc?) The default is ext3... so if that is the case, first, unmount the partition. In case you can't (because is root), then try using other HDD or a Linux live CD, and execute any of these two options:

# Dump anything: (takes longer and generate large files)
strings /dev/hda2 > big_text_file

# other faster option (-50 means copy only 50 lines before/after) 
grep --binary-files=text -50 "textToSearch" /dev/hda2 > output

Note: do not write anything to that partition until you recover all the important files.

I hope it help you.

---

### Post by rwslippey on 2009-05-31
Yes it is an ext3 however it is on a logical volume, does this make a difference?

So if I understand correctly I would basicly run what you suggested from another installation or a live CD. Like I said in my post prior.. the help is greatly appriciated.

I can't believe I was that dumb to delete what took me weeks to build. .PHP included.... well I guess this is the learning curve, a backup would be great right about now.

---

### Post by Agent ME on 2009-05-31
Boot from a LiveCd to make sure you don't overwrite anything on the server. If you've added any files since deleting the one file it's somewhat likely you may have overwritten it.
While in the LiveCd, you want to install photorec, a file recovery program. It is included in the _[testdisk package](apt://testdisk)_.
Next, attach another storage device to the server to recover files onto. (You can't save the recovered files onto the same file-system that they're being recovered off of because they'd get overwritten.)
Then, start a terminal and type "sudo photorec" into it. It's pretty straight forward: pick the partition to recover from, pick the directory to save files to, and set it to only search free space.
When it's done, all discovered files will be inside the directory you set. Note that their filenames are not the original, but guessed based off of their contents. The extensions should be somewhat close.

---

### Post by rwslippey on 2009-06-02
Well thank you both for the great information. Worked perfectly. File names didn't come in but I found everything I needed... and a lot more I might add.... 


Now brings the question... what is the best alternative for backups. and so my search begins  Thanks again, you'll never truely understand how much time that saved me....:D

---

