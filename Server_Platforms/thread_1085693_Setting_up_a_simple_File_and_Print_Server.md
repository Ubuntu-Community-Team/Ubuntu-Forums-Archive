---
title: "Setting up a simple File and Print Server"
date: 2009-03-03
forum: Server Platforms
---

### Post by ooofence on 2009-03-03
Good Morning all :D,

I have wanted to use one of my old boxes (HP Pavilion 501n) as a simple file and print server for my home network and since recently discovering Linux, I am looking to use ubuntu.  I have the following computers/printers:

2 running XP on wireless
1 running XP on Wired
1 laptop running Vista on Wireless
1 HP 7960 Printer 
1 Actiontec (Verizon FiOS) Router (which is also my gateway)
1 DLink Router (acting as an access point)

I want to hook the HP printer to the HP Pavilion (via usb)to act as a network printer.  The Pavilion will have two 40gb hard drives.  I really don't need a lot of bells and whistles, just a simple server to store music and pictures for everyone to have access to and private folders for me and my wife to store documents and the ability to print via laptop from anywhere in the house.

After reading many of the forums and online guides, it seems that ubuntu with Samba and CUPS is the best way to go, but please note, I am a half step above a newbie and while I am not afraid of the command line, I am not comfortable with it at all.  The server will be headless.  My questions are as follows:

1. Would I be better served using RAID or using one of the HD's as a dedicated /Home?
2. What would be the best software to use to remote into the server once it is headless?
3. ubuntu or ubuntu server? (Again, I would be more comfortable with GUI but will learn the command line as needed)
4. Proper configuration to allow a general folder for music and then setting up private folders for owners only.

Please please, if there is a thread that has covered this already, let me know the link and I will work from there first.

Thank you for all your help/suggestions :D

---

### Post by yeats on 2009-03-04
I'll go ahead and caution you that this is a pretty ambitious project if you're not comfortable on the command line.  Having said that, it's a great way to learn.  I would do one at a time and start with the print server, myself.  I would go with Ubuntu server (if not straight up Debian, from which Ubuntu is derived).  All "Debian print server" tutorials you find on the web will be relevant, with minor differences in versions of the programs you install.

Regarding your other questions:

> 1. Would I be better served using RAID or using one of the HD's as a dedicated /Home?

Depending on what sorts of files you're storing, either should work fine for your needs.  The advantage of RAID is redundancy (which might matter if the hardware is older and the files you're storing are important enough to you).

> 2. What would be the best software to use to remote into the server once it is headless?

The CUPS web interface is installed automatically and can be accessed by going to [hostname/ip]:631.  Otherwise, openssh (you would want openssh-server installed on the server and puTTY ([http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)) on any XP machines where you would want access to the server.

> 
3. ubuntu or ubuntu server? (Again, I would be more comfortable with GUI but will learn the command line as needed)

Ubuntu server actually comes with an optional GUI, but in most server situations you don't want that because then the admin tools consume as many resources as the server programs.

> 
4. Proper configuration to allow a general folder for music and then setting up private folders for owners only.

Once you have the software installed, adding users and directories is very simple (though Samba is a lot of work to learn and configure).  Try Using Samba ([http://books.google.com/books?id=yQ9DjzjZO_EC]("http://books.google.com/books?id=yQ9DjzjZO_EC")).


Hope that helps, and good luck.

---

### Post by ooofence on 2009-03-04
Thank you for your advice.  I will be putting the server together this weekend so I will post a follow up on all successes and failures.  Only saving grace I think I have is that the box will be started fresh, with Linux only...so if I break the install before I have it set up properly I wont have to worry about losing anything.:popcorn:

---

### Post by happyhacker on 2009-03-04
Try Webmin as an excellent GUI for controlling the server. I now hook my laptop into the network when I get to the office and control the server remotely that way. Soon I shall configure remote access.

---

### Post by cagey_cretin on 2010-08-20
I haven't been able to share a printer from either Hoary or Hardy. Every permutation of every tutorial I've tried results in the same thing: nothing. Everything else in the world, I can do with Ubuntu.

It's really really funny, because sharing a printer was the first networking tool I learned with M$. Oh, and the same machines on the same IPs with the same hardware running FC work and play well with regards to printing.

If the only OS I was running were Ubuntu, it would just be easier to buy a powered print server and thake the stinkin' OS out of the loop. I'm just sayin'...

---

