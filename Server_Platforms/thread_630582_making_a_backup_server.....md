---
title: "making a backup server...."
date: 2007-12-03
forum: Server Platforms
---

### Post by hockey97 on 2007-12-03
HI I now have my main server up and running, I have an extra computer brand new,  so I have 2 computers one is a server, and so will be the new one.

I want to make it possible so I want to make the new computer have ubuntu server ect,  and be able to make an exact copy of the database and  stuff like the main server.

so I want to have a main server but when it is down I want to be able to flip to my back up server to host my website.

how can I do that?

also in ubuntu 7.10 how can I make a backup of it, so I wont lose any information nor system files, I last time experienced a total lost of information took me a couple months to get back to where I left off.

I want to make sure it wont happen again.

---

### Post by gubemton on 2007-12-03
If you want to be able restore directly from an image to to a hard drive [Mondo]("http://packages.ubuntu.com/gutsy/utils/mondo") might be a good choice. For just backing up /home and /etc [BackupPC]("http://packages.ubuntu.com/gutsy/utils/backuppc") is a great option.

---

### Post by hockey97 on 2007-12-04
thanks for the info I will look into that.

I now got a php problem with my uploading script.

I got this error  failed to open stream: Permission denied

with using the  move_uploaded_file function. 

I googled around and foun some post's about it saying it's a permission issue.

so I check my files and folders for my website and it had the chmod 777  command.

I don't know how I could fix this,  I am trying to upload a pic to a directory in my web page folder.

is their any other places I need to config the permissions??

---

### Post by smileypaul on 2007-12-04
rsync -e ssh -avzr --progress /source username@ip:/destination

make sure to edit the rsync.d file to set up the destination.

The above requires openssh to be installed.

---

### Post by hockey97 on 2007-12-04
can you explain /source username@ip:/destination  that part.

is the source username my user name in my main system, I am using ubuntu 7.10  so the user name  that I made for ubuntu system I should use it at  where you specified username .  The ip address would be my internal one right?  and  the destiation would be the directory  where  I want the files to be saved in right?

---

### Post by simongibson on 2007-12-04
Yes - using rsync is a good option - Consider using snapshot - a script to automate the process
I do this to create a hot swap server that can be used if the main one fails.
The snapshot script will need tweaking to also copy the files to the proper target location in addition to the sequenced backup copies.
Simon

---

### Post by hockey97 on 2007-12-05
I got this error failed to open stream: Permission denied

with using the move_uploaded_file function. 

in php.

how can I fix this?? I google it and found posts saying that it's a permission problem, but I chmod 777 my webpage folders.

what else is their to be done??

how can I fix this problem, I am trying to have a php page to be able to upload a picture to a directory.

---

