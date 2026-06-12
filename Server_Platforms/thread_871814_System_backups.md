---
title: "System backups"
date: 2008-07-27
forum: Server Platforms
---

### Post by rgotten on 2008-07-27
I have ubuntu server 8,04 installed and use webmin as a gui to do manitanence work on the server (which is on a closet), i would like to do backpus of the server so if it brakes, be able to do  quick restore of the system. 
To start i have to mention that i have my system on RAID, and so far deleting a complete hard drive has work nicely to reconstruct the ARRAY, but i know i ned solid backups. 

Questions: 

1)What should i use for backups and can this be done thru webmin.
2)I was planning to connect and external hard drive and do backups there also, how can this be done
3)I plqn to also do backpus over the internet on an incremental way of my files that are more important, can this be done

Thanks

rgotten

---

### Post by MJN on 2008-07-29
I think the reason your post has gone without a response for over a day is a reflection that your question is somewhat broad. Backups are an area that receive much discussion and so I recommend you searching through the archives for previous discussions and if you've still got specific unanswered queries then post back with them - we can then work with you to address them.
 
Mathew

---

### Post by amenszer on 2008-07-29
I agree with MJN, the question is a bit broad.

But this article may give you some ideas:
[http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")

---

### Post by rgotten on 2008-08-10
Sorry for not answering earlier, i was out of town. 
I just want something reliable were if there is a crash of my office server, it can easily be restore. My server is on a closet and i use Webmin to access it. Reading i see that Webmin has a module for "Bacula", i have seen other people talking about rsync, amanda, etc. I want something that after the first backup, it can do incremental backups so it is faster and save space. I am also planbning to do this backup to an external hardrive and maybe a second one remotly thur the internet

Any help??

Thanks

rgotten

---

### Post by scorp123 on 2008-08-10
I have used them all ... "bacula", "amanda", and what not.

Call me stupid, but I don't trust a tool which isn't there "out of the box" if the worst of all possible scenarios happens, e.g. total system failure and reinstallation from scratch. Those tools are not there. It's a fact. So how in the world do you plan to get your stuff back if the necessary tools are not even there? "apt-get install" ... Yes, good idea. But what if there is no Internet connection and you simply cannot download and install anything? What if your only "weapon" is a simple Ubuntu Live CD and therefore you can only use the tools which are already on the CD and *nothing* else ... ?

The answer is simple: You have to use tools such as "tar" and "gzip". Those tools are pretty much *ALWAYS* installed on any Linux, BSD and commercial UNIX release I can think of. Heck, even Windows tools such as WinRAR and WinZIP can read *.tar.gz files.

In other words: Learn how to use "tar" and "gzip" in your sleep and especially on the command line and you will pretty much always get your data back somehow, even on other computers and on other operating systems if it needs to be.

"How to backup your stuff UNIX-style"
[http://linuxmint.com/forum/viewtopic.php?t=3969](http://linuxmint.com/forum/viewtopic.php?t=3969)

---

### Post by sebald on 2008-08-10
Yes, broad question.

I like to backup to hard drives on other machines myself, in DVD-size chunks, maximum (except whole partition backups)

Start with the [backup guide in Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/backups.html"). 

Bacula looks a bit forbidding, but worth investigating of course.

From [Full Circle Magazine]("http://fullcirclemagazine.org"), issue 12, see the "Backup with Partimage" article - and get the PartedMagic bootable disk that includes it, OR [SystemRescueCD]("http://sysresccd.org") which includes it and other useful tools like ability to mount Samba shares. Partimage does whole partition copies like dd, but doesn't copy the free space. Slick.

Mondo is available from the Ubuntu universe, and backs up a live filesystem on the same machine, but somehow the disks it creates haven't booted on my system and haven't figured it out. Slick setup if I can make the disks boot!

---

### Post by rgotten on 2009-04-05
You guys are rigth, my question is to broad..this is what i am looking to do: 
1) on my ubuntu sever i store word, pdf and excel filesand documents,(from my windows client computer thru samba to my ubuntu server) i would like to do daily automatic backups into either an external hard drive conected to the server or to a NAS (network attach storage)in the network, and for extra security to another NAS at a diferent location thru the internet..What is recomended to do this..

2) in relation to the server iself, can i do a live cd with everything install in it or is better to created an image so if there is a crash either instal again the live cd with everything installed or the ubuntu cd and then install partimage and restore an image for example??

Your help is appeciated

rgotten

---

