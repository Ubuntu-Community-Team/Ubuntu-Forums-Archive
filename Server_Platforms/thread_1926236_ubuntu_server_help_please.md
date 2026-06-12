---
title: "ubuntu server help please"
date: 2012-02-15
forum: Server Platforms
---

### Post by chuwy5_19 on 2012-02-15
so i installed the newest server onto my desktop pc so i can use it has a saving work horse for my laptop and i finely got it directly connected to the wireless router so its connected via cat5 and the laptop is via wifi, the prob is i cant figure out how to get the laptop to connect to the server iv tried using the putty program and am really confused. the server does have the web and so does the laptop how do i get the 2 to see echother? and the next thing once that gets resolved is it also has a 2nd drive in it i would like to have access to that has well thank you in advanced.

---

### Post by papibe on 2012-02-15
In order to connect using Putty, you need to install the ssh server package on the server.

Here's how:
```
sudo apt-get install openssh-server
```

On the other hand, to share directories so you can see them on Windows' network file exploret folder, you need to install the package samba on the server:
```
sudo apt-get install samba
```
Hope it helps, tell us how it goes.
Regards.

---

### Post by chuwy5_19 on 2012-02-15
i appologies i should of said my laptop is also ubuntu as well the newest version as well. and also when i was installing the server i told it to install all the stuff possible so ssh is on there allready should i do the samba still?

---

### Post by azmyth on 2012-02-15
Both computers are Linux? I'd use NFS. Probably best to google on how to set it up. Basically you create a mount point(s) and then mount whatever directory you want to the mount point then you can share amongst two computers.

---

### Post by tamkt on 2012-02-16
If laptop is windows, you can use winscp. But installed ssh.

---

### Post by bubylou on 2012-02-16
If you installed all the packages that were offered on install than you should have openssh and samba. Samba will require some editing in the config file. Start here and save this main [page]("http://ubuntuforums.org/") for future reference. You can access the server from an Ubuntu Desktop by typing  ssh username@host. Putty is for windows clients. Also just curious but why did you install all the packages from the install?

---

### Post by chuwy5_19 on 2012-03-06
so i finely got it to work so i can access it from my pc yea but im trying to figure out how i can enable it to let me store stuff on it. also once that part has been solved i also need help on how to get it to mount the second drive that the server has it has 2 drives but is only looking at the one (the one it was installed on) any help would be great

---

### Post by papibe on 2012-03-06
Could you post the content of this file?
```
/etc/fstab
```
and also the result of those commands?
```
sudo fdisk -l

sudo blkid 

```
Regards.

Explanation: In order to mount the missing disk/partition at boot, time you need to edit the file /etc/fstab (add a new line). The other commands will provide the necessary information to create the line.

---

### Post by chuwy5_19 on 2012-03-06
so i did that but i gues im confused the fstab command you had me do did nothing. the other to brought somthing up but how do you copy it from putty?

---

### Post by papibe on 2012-03-06
Select the output of the commands on Putty's terminal using your mouse. The selection will be automatically put in your clipboard. Then paste it on the browser using Ctrl+V as usual.

Regards.

---

### Post by chuwy5_19 on 2012-03-06
ok nother qs were do i find thatin putty to make it do that? sorry im still a newbe

---

### Post by chuwy5_19 on 2012-03-06
where do i find that in putty? sorry still a newb

---

### Post by papibe on 2012-03-06
Here's how: [How to copy and paste to and from a PuTTY window]("http://www.youtube.com/watch?v=yFFbxSsiSms").

Regards.

---

### Post by Catalyph on 2012-03-06
If your Laptop is also Ubuntu,
then open a terminal window
type 
ssh [IP of UBUNTU Server] 

you should get user and password prompt, use the p/w and lg for the Ubuntu server you used.

once SSH in you can do the following commands

$ cat /etc/fstab 

$ sudo fdisk -l 

copy the contents that shows up into a reply.

if you want to see the folders on your network you need to add them to the Samba config file.
Or you can install webmin on the ubuntu server which makes config easier for new users, it will give your server a web interface, you add services and configure ftp and samba and shares and users and stuff like that 

On the Ubuntu server:

$ sudo wget[ http://www.webmin.com/download/deb/webmin-current.deb]("http://www.webmin.com/download/deb/webmin-current.deb")
$ sudo dkpg -i web (then hit tab key to fill in the rest of the .deb file name)
$ sudo apt-get -f install

then you should be able to access webmin from a web browser on your network 
{server_IP}:10000
eg: 192.168.0.199:10000

---

### Post by chuwy5_19 on 2012-03-06
ok so i was able to make my laptop have a login with it but i forgot to tell it to make a file for it i gues cues all it is givving me is <$> and i can type and give it comands but how do i give it sudo control or even root access?

i figured out how i can copy from that termanal but the putty is still not working like that utube video so i cant copy from it.

---

### Post by chuwy5_19 on 2012-03-06
ok figured it out i think so this is the first one 


chuwy@chuwys-network:~$ /etc/fstab
-bash: /etc/fstab: Permission denied
chuwy@chuwys-network:~$ sudo /etc/fstab
[sudo] password for chuwy: 
chuwy is not in the sudoers file.  This incident will be reported.
chuwy@chuwys-network:~$ 


here is the next one


chuwy@chuwys-network:~$ sudo fdisk -1
[sudo] password for chuwy: 
chuwy is not in the sudoers file.  This incident will be reported.
chuwy@chuwys-network:~$ su
Password: 
root@chuwys-network:/home/chuwy# fdisk -1
fdisk: invalid option -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

root@chuwys-network:/home/chuwy# 


heres the last one


root@chuwys-network:/home/chuwy# blkid
/dev/sda1: UUID="8542ac51-9840-40ad-a123-eddb2b539a08" TYPE="ext2" 
/dev/sda5: UUID="20d282d5-9f0e-4cba-aaee-49227daa9807" TYPE="crypto_LUKS" 
/dev/sdb1: UUID="2bf3c051-da72-435a-832d-c6ece906905b" TYPE="ext4" 
/dev/sdb5: UUID="38d70e25-f490-416e-a541-abef72abf71a" TYPE="swap" 
/dev/mapper/sdb5_crypt: UUID="4qkC6L-wbzY-hjDd-a1dE-eJX8-coG6-6Xzsu1" TYPE="LVM2_member" 
/dev/mapper/chuwys--network-root: UUID="35507137-9def-48b2-a69b-3317e61efb4d" TYPE="ext4" 
/dev/mapper/chuwys--network-swap_1: UUID="856d7bfc-815f-4843-a19f-958b4026a5fe" TYPE="swap" 
root@chuwys-network:/home/chuwy# 



ok so now what

---

### Post by papibe on 2012-03-06
We are almost there.

To display the content of /etc/fstab do this:
```
cat /etc/fstab
```
The parameter of fdisk is an 'l' (as in lima) not a '1' (number one).

Regards.

---

### Post by chuwy5_19 on 2012-03-06
chuwy@chuwys-network:~$ su
Password: 
root@chuwys-network:/home/chuwy# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/chuwys--network-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=8542ac51-9840-40ad-a123-eddb2b539a08 /boot           ext2    defaults        0       2
/dev/mapper/chuwys--network-swap_1 none            swap    sw              0       0
root@chuwys-network:/home/chuwy# 

the other one is 


root@chuwys-network:/home/chuwy# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f380d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482256895   241127424   83  Linux
/dev/sda2       482258942   488396799     3068929    5  Extended
/dev/sda5       482258944   488396799     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007557b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      499711      248832   83  Linux
/dev/sdb2          501758    78123007    38810625    5  Extended
/dev/sdb5          501760    78123007    38810624   83  Linux

Disk /dev/mapper/sdb5_crypt: 39.7 GB, 39741026304 bytes
255 heads, 63 sectors/track, 4831 cylinders, total 77619192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sdb5_crypt doesn't contain a valid partition table

Disk /dev/mapper/chuwys--network-root: 38.7 GB, 38692454400 bytes
255 heads, 63 sectors/track, 4704 cylinders, total 75571200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/chuwys--network-root doesn't contain a valid partition table

Disk /dev/mapper/chuwys--network-swap_1: 1002 MB, 1002438656 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1957888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/chuwys--network-swap_1 doesn't contain a valid partition table
root@chuwys-network:/home/chuwy#

---

### Post by papibe on 2012-03-06
I'm afraid I wasn't expecting that. You have either an encrypted file system or/and a LVM ? (both of which I'm not familiar with).

Did you take one of those option while installing the server?

Regards.

Hopefully someone else with more experience will pitch in.

---

### Post by chuwy5_19 on 2012-03-08
i did indeed i choose the encript one but on acsendent on the week end i will redow it with out incrypting it and go from there once i do that would it be easer if you can log into it? 


thank you

---

### Post by papibe on 2012-03-08
I would gladly help you again. Once you reinstall your system, just post those commands again, and we'll figure it out.

Regadards.

---

