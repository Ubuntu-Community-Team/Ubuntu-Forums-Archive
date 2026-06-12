---
title: "Ubuntu server 14.04 partition"
date: 2014-10-20
forum: Server Platforms
---

### Post by chrhelling on 2014-10-20
Hi, im not new to ubuntu but I'm new to the server part of the game :)

I'm currently trying to set up a ubuntu server 14.04 and its no problem to set it up but to what i want I'm stuck :/

I'm trying to set the partition and to have everything as bootless and operating system on one hdd and programs and files on another.
Or everything on one hdd and everything that gets saved and if i install a program it will save all files on another hdd. say like boot files is on C: and i install lamp it and a sftp server it will put all its files to D:. how can i do this?

[LIST]
[*]**root partition** (/). D:
[*]**boot partition** (/boot). C:
[*]**home partition** (/home) D:
[*]**swap partition **C:
[/LIST]
can anyone help me and point me in the right way?
hoping for some quick response and thank ya all :D

---

### Post by jdeca57 on 2014-10-20
You might want to reconsider this because boot and swap partitions tend to be very small and in essence you put everything on the second drive you call D:. The linux way would be (given that there is sufficient space) to mount / on the /dev/sda (C: ) and to mount the data on /dev/sdb (D: ) There is more: you can use partitions (sdb1, sdb2...) to divide data. Remember: / (root) is everything, and that includes /home and all the programs and data.

---

### Post by chrhelling on 2014-10-20
Ok, so with that you mean i can install it as normal on 1 hdd with all the partition. then later change where thing get saved? like lamp and get important (the WWW folder) to webpages and create folder trees to use at sftp?

---

### Post by nerdtron on 2014-10-20
> **chrhelling said:**
>  say like boot files is on C: and i install lamp it and a sftp server it will put all its files to D:. how can i do this?

[LIST]
[*]**root partition** (/). D: 
[*]**boot partition** (/boot). C: 
[*]**home partition** (/home) D: 
[*]**swap partition **C: 
[/LIST]
can anyone help me and point me in the right way?

I'm having the impression that what you really want is to separate the data of the application and not the applications themselves.
For example, you want lampp, sftp or for example mysql installed in C: and then all their data - web pages of lammp, files of sftp, and database of mysql - are on the D drive.

If this is the case, (a case that is recommended) then you just install the application as normal and let them get installed in C, then you just need to configure your application to point their data to the new location you want which D.

---

### Post by nerdtron on 2014-10-20
> **chrhelling said:**
> Ok, so with that you mean i can install it as normal on 1 hdd with all the partition. then later change where thing get saved? like lamp and get important (the WWW folder) to webpages and create folder trees to use at sftp?

Actually yes. You can change where the default www gets saved (or rather moved).

---

### Post by jdeca57 on 2014-10-20
Yes, depending on space you put everything on one drive, the C: (it will be /dev/sda or something like it) and make partitions on the other drive for the data. After you assign them and mount them it seems like there is only one file system - but the data are stored on another drive.

---

### Post by chrhelling on 2014-10-20
> **nerdtron said:**
> I'm having the impression that what you really want is to separate the data of the application and not the applications themselves.
For example, you want lampp, sftp or for example mysql installed in C: and then all their data - web pages of lammp, files of sftp, and database of mysql - are on the D drive.

If this is the case, (a case that is recommended) then you just install the application as normal and let them get installed in C, then you just need to configure your application to point their data to the new location you want which D.


exactly what i mean!!! like everything runs on one hdd and the date is on the other one.
if this is possible i would like to know how :)

is it like: install the whole ubuntu server with all partition on 1 hdd. then later change the location of saved files?
cause like i said I'm not new to linux but like i want a server distort total terminal is a bitt new for me :P

if that is possible i know what I'm gonna search and look for next! :D :D :D

---

### Post by nerdtron on 2014-10-20
Each application have their own configuration files which you'll pretty much need to study, and their syntax can differ too.
Just a head's up, for LAMP, specifically Apache, you edit the "ServerRoot" on its configuration file to change the root directory of webpages. Ffor mysql, you edit the /etc/my.cnf file and define the custom directory in the "datadir=" line. On Sftp, the save directory is a bit hard to explain.
Anyway links:
LAMP: [https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04)
SFTP: [https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server](https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server)

Goodluck.

---

### Post by chrhelling on 2014-10-20
> **nerdtron said:**
> Each application have their own configuration files which you'll pretty much need to study, and their syntax can differ too.
Just a head's up, for LAMP, specifically Apache, you edit the "ServerRoot" on its configuration file to change the root directory of webpages. Ffor mysql, you edit the /etc/my.cnf file and define the custom directory in the "datadir=" line. On Sftp, the save directory is a bit hard to explain.
Anyway links:
LAMP: [https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04)
SFTP: [https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server](https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server)

Goodluck.

okei so i install this with terminal onliy option with another drive? never done! ;) just to  say! :) but hey man can you give me an
ordered list of what to do or send me to the right guide? i can say i hooped over to around 7 or 8 guide before this and can't wait!!!! 


just say 
1. how can i get my "total server on dev/sda ? and all the data and i mean all on sdb2?!!! ?

just to say you have a windows tipping over to linux player that find mac more comfortable and find mac the final solution to my web dev and i need a linux based server!! help me here guys! ubuntu server is the way to go i think! ?

---

### Post by nerdtron on 2014-10-20
> okei so i install this with terminal onliy option with another drive? never done! :wink: just to  say! :smile: but hey man can you give me an
ordered list of what to do or send me to the right guide? i can say i  hooped over to around 7 or 8 guide before this and can't wait!!!!
Several guides are lurking in the internet. Best way to learn is to experiment.

> just say 
1. how can i get my "total server on dev/sda ? and all the data and i mean all on sdb2?!!! ?
Same as how you do in windows. Just format sdb2 so that it would be usable, then create a folder as a mount point for it. Next point your application to use that folder.

> just to say you have a windows tipping over to linux player that find  mac more comfortable and find mac the final solution to my web dev and i  need a linux based server!! help me here guys! ubuntu server is the way  to go i think! ?

Two things you need to learn here. System administration (installing, preparing the server, editing partitions, mounting drives, backups) and Applications administration like configuring the application to the environment you need.

In both you need to be familiar with the command line and be familiar with linux. You can start reading by downloading the free PDF here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by chrhelling on 2014-10-20
> **nerdtron said:**
> Several guides are lurking in the internet. Best way to learn is to experiment.


Same as how you do in windows. Just format sdb2 so that it would be usable, then create a folder as a mount point for it. Next point your application to use that folder.



Two things you need to learn here. System administration (installing, preparing the server, editing partitions, mounting drives, backups) and Applications administration like configuring the application to the environment you need.

In both you need to be familiar with the command line and be familiar with linux. You can start reading by downloading the free PDF here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)



i can say no problem install it like it should but i would like to know a guidec or a how to get C: drive to do the boot and the D: drive to do the save? best and pluss would be the guide!!

---

### Post by chrhelling on 2014-10-20
okey i like it guys!! but lets keep it simple! gonna install ubuntu server on one hdd now ;) after that i gunner install hamachi logmein server for now ;) no questions asked! i need a sftp server that control all of D: drive ad under document and all that :) can you just post some how to if you find some? ... I'm stuck? :/ btw by now I'm currently a mac user since I'm a web designer... so post this for mac OS X mac or the new yosrmite :) tnx my friends :D :D

---

### Post by nerdtron on 2014-10-20
Is the D drive ready?
Don't call it D drive already, I think it will be /dev/sdb now. Create a partition on it and format it. Then we can proceed.
If it is connected already, we should see it on the following commands:
```
 lsblk
sudo parted -l
```

Doesn't care if mac or windows, we're dealing with ubuntu server here.

---

### Post by Bucky Ball on 2014-10-20
*Thread moved to **Server Platforms**.*

---

### Post by chrhelling on 2014-10-21
yes /dev/sdb is ready to go :) installed and up and running :) now how do i get files on the other hdd?

---

### Post by nerdtron on 2014-10-21
Is it already mounted? What's the path?

SFTP is already installed if you installed the package openssh-server. The next step a user for sftp and set it's home directory to the new drive.

```
 sudo mkdir /path/to/new/drive 
sudo adduser -d /path/to/new/drive newuser
sudo chown -R newuser:newuser /path/to/new/drive 
```

Now newuser can just log-in to the server using like filezilla, or the command line sftp and then start uploading files. The folder they be saved is the /path/to/new/drive.

---

