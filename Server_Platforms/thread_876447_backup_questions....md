---
title: "backup questions..."
date: 2008-07-31
forum: Server Platforms
---

### Post by hockey97 on 2008-07-31
Hi I am planning on buying an external hard drive.

I want to backup my ubuntu partician.

Ok here is what I want to do. I want to make an exact copy of my partician and be able to run it with ubuntu in it off the copy.

I have 2 computers one is currently my original one which has 2 os on it one windows xp and another ubuntu with the server and also my website files.

what I plan to do is use a external hard drive to backup my partician so that if somthing goes wrong I can just replace the currpted partician with the backup one which is the exact same one.
I also want to be able to transer the copied partician from one computer to another. I got a new computer which I don't use much. This new computer I plan to use as the main server. No ubuntu is installed on the new computer just windows xp.

I want to install ubuntu but would want to use the exact same partician from what I have on my orignal computer.

I also plan to back the hard drive everyday at the end of the day should I use avast to scan the computer before I make a backup?? 

Here is a sum up: computer1 is old (original) this computer has windows xp and ubuntu on it with the servers and my website and use it for personal use.

Computer2 is the new computer and has windows xp. 

I want to copy the partician exactly from the ubuntu os on computer1(original) to computer2 (new computer) and have it run without needing to reinstall programs like apache2 ect.

The reason I can't keep reinstalling stuff it that it takes time to do and I am one person. So to have a partician with everything like apache2 ect, on how I config it(set it up) I want to instantly just copy the partician of ubuntu over to my new computer and have it working.

Now I would like to know what you guys do for backups???

How would you also backup your mysql database??

Also what would you suggest me to buy. for an external hard drive and also is their somthing I have to know if it's capadable.

I seen sata external hard drive with use connection, would it just use a usb connection just like flash memory?

I have one computer that dosen't support sata but supports usb, would it work on that computer also??

Sorry for all these questions.

I am getting close to start my website just now working on security and how to keep hackers out and also  making a backup system.

If you have any other suggestions like on how I should backup my system please do tell.

I just already made my website a while back ago and my windows xp found my linux (ubuntu) partician and decided to reformat it to ntfs which all my data got deleted I tried recovering it but it was no use so I started all over.

I want to prevent this from happening again.

---

### Post by tamoneya on 2008-07-31
if you want identical partitions you should probably be using the dd command.  it can do byte for byte copies.

[http://www.netadmintools.com/html/dd.man.html](http://www.netadmintools.com/html/dd.man.html)

---

### Post by hockey97 on 2008-08-01
ok if I use the dd would it copy the whole partician byte by byte.

Then how would  you install the partician would grub see that this is a partician or recovery backup??

I want to use the same partician for 2 computers and use it as a backup.

Also if I do make a backup copy byte by byte of the whole partician would I also backup mysql database??

I am currently working on security of my server and website and really need to know a good method of backup data.

Thanks I will look into the dd command. I just want to make sure if I do make  a copy will I be able to have grub see this as a partician and not like somthing like a flash drive since the external hard drive will be usb.

---

### Post by cariboo on 2008-08-01
Partimage may be a better solution for what you want to do. DD as the previous poster said will do a byte for byte copy of your partition, including free space, whereas partimage will not include the free space in the image. Using either program will make a duplicate of everything in the partiton if all your files are in / then you don't have to worry about missing anything. Partimage is in the repositories.

Jim

---

### Post by windependence on 2008-08-01
Just FYI cariboo, almost anything can be done with dd including not taking the free space. :)

-Tim

---

### Post by hockey97 on 2008-08-01
ok I will use that program then.  I currently have a head ach lol.

I would like to know that when I do that partician copy would I also copy the data in the mysql databases ??

so when you mean everything it would also copy all servers software and databases ect.

If so.. if I make an exact copy of my old computers ubuntu partician well that is my only partician that I have ubuntu and servers and my website.

Would I be able to install ubuntu on my new computer and instead of making a new partician I just use the copied partican just copy it over to my new computer hard drive . Would this work??

Or would hardware drivers interfear?? 

Also would external hard drive would you recommend that is good for backups and would work easly with ubuntu (meaning no bugs with ubuntu)

I plan to get a sata external hard drive usb. My old computer has a usb connector and also my new computer has a usb connection. I just want to know if it matters if it's sata hard drive or not.

I have desktop type comptuers.

Thanks for the help.

---

