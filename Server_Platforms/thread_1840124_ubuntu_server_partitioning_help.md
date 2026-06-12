---
title: "ubuntu server partitioning help"
date: 2011-09-07
forum: Server Platforms
---

### Post by skd2011 on 2011-09-07
Hi All,

I am new to ubuntu world and seeking help of experts
Iam have purchased 2 sata 1 TB  hard disk to setup ubuntu server with raid 1 this will be my file server
Iam confused in partitioning , plz tell how much parttition should i make with partition size 
Second I wanna partioning in such a manner that if in future my os got crashed i wont loose any data.

Thanks in Advance.

sandeep 
91 9023777985

---

### Post by e79 on 2011-09-07
> **skd2011 said:**
> Iam have purchased 2 sata 1 TB  hard disk to setup ubuntu server with raid 1 this will be my file server
Iam confused in partitioning , plz tell how much parttition should i make with partition size

I'm by no mean an expert at partitioning but I'd say it depends on home many users would need  to have their /home directories (Documents, Music etc) shared  and/or if you want to implement some quotas on the shares.

> **skd2011 said:**
> 
Second I wanna partioning in such a manner that if in future my os got crashed i wont loose any data.

Always backup your valuale data if you can, and if its just a matter that the OS fails, you can always boot up from a live CD to get your data.

Having that said, let's pretend that you alone will use the file server (sharing your home folder) and thus, don't need quotas; I would partition as follow (values are theoretical):

Root (/) : 20-25 GB   ext4
Home(/home): 975 GB    ext4
Swap: 1 - ? GB  (depends on your actual RAM, x 1 or 1.5)  swap

Or if you have more than one users and plan to have their /home shared as well as a central share on another partition for example (with or without quotas):

Root (/) : 20-25 GB  ext4
Home(/home): 375 GB   ext4
Share(/share):  600 GB  ext4
Swap: 1 - ? GB  (depends on your actual RAM, x 1 or 1.5)    swap

But again, I'm not an expert, this is only what I would do.

Hope this helps

---

### Post by papibe on 2011-09-07
The most important things is to separate where the OS resides (which is the / partition), and the data (backups, media files, etc). I personally setup my home server following the typical desktop guidelines:
```
/      15-20 GB
swap   match your RAM.
/home  all the rest.
```
I use my server mainly as:
[LIST]
[*]Download server (transmission-daemon).
[*]Backup server (samba).
[*]File/Media server (nfs).
[/LIST]
I configured all services to use the /home partition.

It always is good to spend a little time designing your partitions. For example, if you want to run a webserver, you may need to a separate /var partition.

What do you have in mind?
What do you want to run?
What services do you want to provide?

Hope it helps,
Regards.

---

### Post by skd2011 on 2011-09-07
Hi 

Thanks alot for your reply
I got the basic idea, but dont you think 25 gb is huge for / root partition, should i go with 10 gb

thanks

---

### Post by skd2011 on 2011-09-07
Hi 

Thanks alot for ur reply

Now i have planned the following partition scheme for my server

/ swap 2 GB
/root 10 GB
/usr 10gb
/var 10 gb
/tmp 100 mb
/home 100 mb

please suggest is it good , should i go with this, i have to complete the server installation today so please reply asap.

Thanks

---

### Post by Entilza on 2011-09-07
You can use LVM and in future resize any partition you need but that's a whole other story :)

If this is just a home file server and not a business server I wouldn't separate so much of the OS directories, this is just a basic server for home?  You already got some good suggestions so I would suggest do what they said.

/  25 Gig  (This contains / /usr/ var/ tmp/ )
/home 950 Gig (The remaining)  

If you don't want to use /home as your data storage then:

/1 Data location (950gig)

/ swap 2 GB

---

### Post by e79 on 2011-09-07
> **skd2011 said:**
> 
/ swap 2 GB
/root 10 GB
/usr 10gb
/var 10 gb
/tmp 100 mb
/home 100 mb
Thanks

As Papibe and Entilza pointed out, il always depends on what you want to achieve and you could always use LVM to resize your partitions in the future. Since this seems to be a file server, either one of our suggestion would be good. Nonetheless, here is what I think about your config :

/ swap 2 GB    <-- Seems ok, means you have at least 2GB of RAM
/root 10 GB     <-- I would stretch that to 15 GB, but that's me
/usr 10gb        <-- Why separating the /usr ?
/var 10 gb        <-- Why separating /var ?
/tmp 100 mb    <-- Unless you know what you're doing here, do not touch this
/home 100 mb   <-- This is really low !

---

### Post by skd2011 on 2011-09-09
Dear All

Thanks alot for your precious replies

one more thing i want to know, i think we have to choose 1 method either LVM or simple raid partitions as describe above. LVM is best. Is am right?

Thanks

---

### Post by Entilza on 2011-09-09
I am using LVM as I like all the features of it, with the ability to resize, etc.  It depends on the use for your server if it is not going to be changing much in the future you don't really need it.

With LVM for example if you have /home separate you can in future add another harddisk to /home without having to repartition /home and losing the data.

So choose based on the future of your server if it's future proofing I would use LVM if it's a dedicated server for one small purpose that won't change much then use simple.

---

### Post by a2j on 2011-09-09
/dev/md0 - swap - 2x ram
/dev/md1 - ext4 / - rest of the drive space

would also work

---

### Post by Vegan on 2011-09-09
I find it expedient to have several machines to be able to maintain backups. This way they can be automatic and idiot proof.

I use my own web server and the gaming box each have a copy of important files.

SAMBA has been helpful in my shop. I have come to appreciate its sophistication. That is because I also have Windows Server here.

Today though everything is a virtual machine.

---

### Post by skd2011 on 2011-09-12
Dear All,

I done the partition on 1 TB as guided 

/ swap 2 gb
/root 20 gb

all rest space to 
/share for Network storage

while mounting i assign 2 gb partition use as swap, /20gb use as ext 4 bootable , and /share as ext 4

Now installation complete and when i run 
mdadm -deatil /dev/md0

i got array size 20 gb only as i assigned to root partition

where my /share partition space gone ?????????????

plz help

waiting for your reply..........

Thanks alot in advance

---

### Post by Entilza on 2011-09-12
post results of:

fdisk -l

df -h

---

### Post by skd2011 on 2011-09-15
Hi,

Need your help again

Now am going to setup another ubuntu server but this server i'll use later for multiple purpose so i wanna do LVM partioning with RAID 1 I have 1 TB 2 HDD. please give partition  layout so that i can proceed.

---

### Post by e79 on 2011-09-15
Have a look here, as it could help you better than I could ;)

[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

[http://blog.linuxniche.net/2010/09/ubuntu-10-04-install-with-lvm-on-raid-1-using-graphical-livecd/](http://blog.linuxniche.net/2010/09/ubuntu-10-04-install-with-lvm-on-raid-1-using-graphical-livecd/)

[http://maxbeatty.com/blog/2010/11/how-to-setup-raid1lvm-on-ubuntu-server/](http://maxbeatty.com/blog/2010/11/how-to-setup-raid1lvm-on-ubuntu-server/)

Cheers

---

### Post by skd2011 on 2011-09-24
Dear E79,

where to mount /share
 i wanna create 2 different partitions 1 for mails backup and 2 for softwares backup
what its mount point should be..........

thanks in advance

---

### Post by e79 on 2011-09-26
Well you could simply create 2 folders in /mnt, like:

```

sudo mkdir /mnt/Mail
sudo mkdir /mnt/Softwares

```Then create 2 new extended partitions (let's say sdc1 and sdd1) on your setup and have them mounted to those folders upon reboot.

You would have to add something like this to you /etc/fstab:

```

/dev/sdc1       /mnt/Mail       ext4    errors=remount-ro 0       1
/dev/sdd1       /mnt/Softwares  ext4    errors=remount-ro 0       1

```

Then setup Samba using these.

---

