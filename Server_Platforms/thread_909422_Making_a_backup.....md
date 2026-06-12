---
title: "Making a backup...."
date: 2008-09-03
forum: Server Platforms
---

### Post by hockey97 on 2008-09-03
Hi I just got my external usb hard drive in the mail. I was told a while back to use clonezilla.

what I am trying to do is I have 2 computers one is old and the other is new.

the new computer has windows. the old has a dual boot with ubuntu and windows xp.

I want to copy the partician of the ubuntu of the old computer and place it on the new computer.

I plan to install ubuntu on the new computer and erase windows os.

I plan to make my new computer the main server and my old computer which I personally use to be used as a backup.


any ideas or suggestions/tips I could use before I start this process????

---

### Post by HermanAB on 2008-09-03
You'll find that it is easier and faster to install the latest version of Ubuntu rather than trying to copy an old version.

Cheers,

Herman

---

### Post by hockey97 on 2008-09-03
my old computer does have the latest ubuntu version.

I am trying to setup  a server system. I want my new computer to be the main since I don't use the new computer much. The new computer has 80gb hard drive.

I have a 60gb and a 300gb hard drive on my old computer.

so I want to make the new computer a main server.

I  just want to copy  what I have on the ubuntu hard drive and be able to transfer this OS/setup easily on any other computers that installed ubuntu.

currently I am read to start this backing up proccess.


I don't know how to use clonezilla. How can I make the backup and then also restore this backup to my computer???

any tutorial???

I saw on clonezilla website that they have a live cd don't understand if I have to put this on a cd or what???

---

### Post by hockey97 on 2008-09-03
What's the best way to backup your hard drive and will this also backup mysql databases also???

would like to know if I have to burn the program onto a cd??

---

### Post by hockey97 on 2008-09-04
Is their any tutorials on using clonszilla???

I need to backup my stuff soon as possible.

any ideas???

---

### Post by Biochem on 2008-09-05
I personnaly use dd with gzip or 7zip (If I need to split the image to put on cds) to backup hard drive

read 
man dd
man gzip
man 7zip

The best thing about dd and gzip is that they are always part of live cd (ubuntu and knoppix at least) so it's less of an assle than having to get a clonezilla disk in a panic.

@ HermanAB
it may be faster to do a clean install to get the base system. But when you took time to customize a bunch of configuration files, compiled a bunch of software and are happy with your system it may take a while to recreate all that. IMHO it's better to have a backup to restore the system in just a couple of hours rather than build from a fresh install that takes a couple of weeks.

---

### Post by hockey97 on 2008-09-06
ok I will take a look at the man of each.

I would also like to know if I should backup system files.

I want to know if I should backup system files.


I plan to save all programs and files and would like to save all files of the programs so I don't have to install anything.

I want to backup 2 system files one for one computer and another for another computer.

I already experience my computer getting corrupted. I had to start all over and yes it is  a pain.

I want to avoid this pain in the future.

---

