---
title: "Ubuntu Desktop with LAMP"
date: 2008-09-03
forum: Server Platforms
---

### Post by omniware on 2008-09-03
Hi guys, I am new to linux so far this is the best Linux OS I've ever installed compare to Redhat, Fedora and Centos. Anyways, just installed Ubuntu Desktop 8.04 and installed LAMP as well.  I got pretty much everything working except that I cannot upload files into /var/www/myfolder. I don't think there's a problem with my vsftpd.conf as I can upload on my /home/user/. Any help is greatly appreciated.

---

### Post by MNA_Novice on 2008-09-03
have you checked the permissions on that target folder?

---

### Post by omniware on 2008-09-03
hi there, thanks for prompt reply.  Can you tell me how to do that? I am new to linux. I did chown user /var/www, but didn't help. BTW I am also from Sac. Thanks!

---

### Post by MNA_Novice on 2008-09-03
Well, within the Gnome GUI help, we find:

6.6.16.1.&#8195;Changing Permissions for a File

To change the permissions of a file, perform the following steps:

   1.Select the file that you want to change. 

                
   2.Choose File &#9656; Properties. The properties window for the item is displayed.

                
   3.Click on the Permissions tab.

                
   4.To change the file's group, choose from the groups the user belongs to in the drop-down selector.

                
   5.For each of the owner, the group, and all other users, choose from these permissions for the file:

                  
None
No access to the file is possible. (You can't set this for the owner.)

Read-only
The users can open a file to see its contents, but not make any changes.

Read and write
Normal access to a file is possible: it can be opened and saved.

                          


                
   6.To allow a file to be run as a program, select Execute

                

6.6.16.2.&#8195;Changing Permissions for a Folder

To change the permissions of a folder, perform the following steps:

   1.Select the folder that you want to change. 

                
   2.Choose File &#9656; Properties. The properties window for the item is displayed.

                
   3.Click on the Permissions tab.

---

### Post by MNA_Novice on 2008-09-03
From Ubuntu Documentation:

[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html")

From some other folks:

[http://www.psychocats.net/ubuntu/permissions]("http://www.psychocats.net/ubuntu/permissions")

On Prism:

[http://www.prism.gatech.edu/~mflaschen3/UbuntuBook/AppA_Ubuntu_Book.html]("http://www.prism.gatech.edu/~mflaschen3/UbuntuBook/AppA_Ubuntu_Book.html")

I **can** tell you that once you've used CD to change to the target directory, you can use "ls -l" to show permissions of all the files within...

then figure out the correct permissions and chmod them.

hope this helps some... I'm *still* a linux newbie here... but coming from a Mac OS X (terminal isn't so scary) as well as Windows support background, it's just another OS - albeit a significantly better and cooler one than anything MS has put out by far!! I'm loving linux the more I work with it... but no-one's replied to *my* easy question, unfortunately. Maybe you have an idea on this one?

[http://ubuntuforums.org/showthread.php?p=5721582#post5721582]("http://ubuntuforums.org/showthread.php?p=5721582#post5721582")

---

### Post by chocbar31 on 2008-09-03
Try this:

Code:
sudo chown YOURUSERNAME /var/www

Look here: [http://ubuntuforums.org/showthread.php?t=485681]("http://ubuntuforums.org/showthread.php?t=485681")

---

### Post by omniware on 2008-09-03
> **MNA_Novice said:**
> Well, within the Gnome GUI help, we find:

6.6.16.1.&#8195;Changing Permissions for a File

To change the permissions of a file, perform the following steps:

   1.Select the file that you want to change. 

                
   2.Choose File &#9656; Properties. The properties window for the item is displayed.

                
   3.Click on the Permissions tab.

                
   4.To change the file's group, choose from the groups the user belongs to in the drop-down selector.

                
   5.For each of the owner, the group, and all other users, choose from these permissions for the file:

                  
None
No access to the file is possible. (You can't set this for the owner.)

Read-only
The users can open a file to see its contents, but not make any changes.

Read and write
Normal access to a file is possible: it can be opened and saved.

                          


                
   6.To allow a file to be run as a program, select Execute

                

6.6.16.2.&#8195;Changing Permissions for a Folder

To change the permissions of a folder, perform the following steps:

   1.Select the folder that you want to change. 

                
   2.Choose File &#9656; Properties. The properties window for the item is displayed.

                
   3.Click on the Permissions tab.

Thanks. I thought you have to login as root to perform this via gnome. These folder owns by root so the group, tabs and properties are grayed out. Could it be done via terminal? I am using remote SSH. Regards!

---

### Post by omniware on 2008-09-03
> **chocbar31 said:**
> Try this:

Code:
sudo chown YOURUSERNAME /var/www

Look here: [http://ubuntuforums.org/showthread.php?t=485681]("http://ubuntuforums.org/showthread.php?t=485681")


This works! sudo chmod +rw /var/www

Thank you all!
Cheers :)

---

### Post by windependence on 2008-09-04
Just keep in mind that neither of these suggestions is a great idea if you have your web server open to the internet. Making your doc root readable and writable is a big security risk.

The proper way would have been to set up a group that would have write access and add your user to that group.

-Tim

---

### Post by fballem on 2008-09-04
> **omniware said:**
> Thanks. I thought you have to login as root to perform this via gnome. These folder owns by root so the group, tabs and properties are grayed out. Could it be done via terminal? I am using remote SSH. Regards!

Actually, you don't want to log in as root. If you open a terminal and type 'gksudo nautilus', this will open up Nautilus with root permissions. If the terminal commands are simple and I'm comfortable that I understand them, then I'll use 'chown' and 'chmod'. If I have any doubts, then I'll gksudo nautilus and go from there.

By the way, to change the group associated with a file or directory, use chgrp. The other syntax elements are the same as chown.

Hope this helps,

---

### Post by omniware on 2008-09-04
> **windependence said:**
> Just keep in mind that neither of these suggestions is a great idea if you have your web server open to the internet. Making your doc root readable and writable is a big security risk.

The proper way would have been to set up a group that would have write access and add your user to that group.

-Tim


Thanks for your concern about the security issue. My other question is would it be good to run Unbuntu desktop as a web server?  The reason why I have installed Ubuntu desktop because I cannot get the xserver to work, it failed during installation.  I have downloaded 4 different ISOs from different location, tried it on three different  boards including Intel S5000PAL, S5397WAG2NRF and D865GBF. I'm not even using the RAID controller. Just wanted this xserver installed on SATA drive.

The Ubuntu desktop works fine during the installation.

---

### Post by omniware on 2008-09-04
> **fballem said:**
> Actually, you don't want to log in as root. If you open a terminal and type 'gksudo nautilus', this will open up Nautilus with root permissions. If the terminal commands are simple and I'm comfortable that I understand them, then I'll use 'chown' and 'chmod'. If I have any doubts, then I'll gksudo nautilus and go from there.

By the way, to change the group associated with a file or directory, use chgrp. The other syntax elements are the same as chown.

Hope this helps,

Thanks! I will give this a try:)

---

