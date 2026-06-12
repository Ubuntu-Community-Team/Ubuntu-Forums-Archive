---
title: "how to get nfs out of the way to reboot"
date: 2011-11-21
forum: Tutorials
---

### Post by zenrox on 2011-11-21
this howto was created for this issue i was experancing

my /etc/exports looks like this 

/home/zenrox/Videos 192.168.2.0/8(rw,no_root_squash,async,no_subtree_check)
/home/zenrox/Downloads 192.168.2.0/8(rw,no_root_squash,async,no_subtree_check)
/home/zenrox/Music  192.168.2.0/8(rw,no_root_squash,async,no_subtree_check)
/home/zenrox/Pictures 192.168.2.0/8(rw,no_root_squash,async,no_subtree_check)
 
and i mount the other shairs from another pc like this 
my /etc/fstab
192.168.2.3:/home/rjaeangel/Videos /media/rhonda/videos	  nfs	rw,rsize=8192,wsize=8192,timeo=14,intr,bg
192.168.2.3:/home/rjaeangel/Pictures /media/rhonda/pic		nfs	rw,rsize=8192,wsize=8192,timeo=14,intr,bg
192.168.2.3:/home/rjaeangel/Music /media/rhonda/music nfs	rw,rsize=8192,wsize=8192,timeo=14,intr,bg
192.168.2.3:/home/rjaeangel/Downloads /media/rhonda/downloads	nfs	rw,rsize=8192,wsize=8192,timeo=14,intr,bg

now it works as it should
but when i reboot the computer(either) thay hang so i wrote a script
to shutdown the nfs server and umount thoes above shairs and now the pc reboots

my script 

sudo service nfs-kernel-server stop
sudo umount 192.168.2.3\:/home/rjaeangel/Videos
sudo umount 192.168.2.3\:/home/rjaeangel/Pictures
sudo umount 192.168.2.3\:/home/rjaeangel/Downloads
sudo umount 192.168.2.3\:/home/rjaeangel/Music

copy and paste this in to a file and save it as umount(or some other name)

then open a terminal whare the file is located
and type chmod +x umount

then just run the script just before you shutdown,reboot 
thx for reading this howto

---

