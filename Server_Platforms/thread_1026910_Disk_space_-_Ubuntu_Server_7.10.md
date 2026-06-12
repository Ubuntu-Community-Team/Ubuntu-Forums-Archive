---
title: "Disk space - Ubuntu Server 7.10"
date: 2008-12-31
forum: Server Platforms
---

### Post by cyphur on 2008-12-31
Hi All,

i've used the search here and the google and i'm getting no joy in trying to figure out where my disk space on my / partition is going. 

i have a 7.10 server install with 2 hard drives.

1 40gb = sda
1 200gb= sdb

here is the output of du -h

# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  7.1G  1.7G  82% /
varrun                505M  3.2M  502M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   84K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
/dev/sdb5              46G  181M   44G   1% /home
/dev/sdb6              46G  181M   44G   1% /opt
/dev/sda6              26G  711M   24G   3% /usr
/dev/sdb1              96G  4.1G   87G   5% /var


this machine is used as a file server with Samba running. the shares are in the /var directory. there are no users except root and my user account. this is a small business so just doing folder sharing for the minimal files folks need to access.

I did a 
:/# du -hx --max-depth=1 /
5.9M    /sbin
4.0K    /opt
4.0K    /usr
20K     /tmp
4.0K    /initrd
16K     /lost+found
17M     /boot
108K    /root
4.0K    /srv
12K     /media
0       /dev
5.4M    /etc
4.0K    /home
3.5M    /bin
4.0K    /var
77M     /lib
0       /sys
8.0K    /mnt
0       /proc
109M    /


i'm thinking i'm misunderstanding how the disk usage is calculated on the sda1 partition. i have a 2nd server of the same install but different hard drive sizes and it shows my / usuage at like 850mb.. i'm trying to figure out what is taking up 5-6GB of my sda1 / partition. 

i tried this

find / -type f -size +10000k -exec ls -lh {} \; | awk '{ print $8 ": " $5 }'

with this output

find: /proc/3902/task/3902/fdinfo/4: No such file or directory
find: /proc/3902/fdinfo/4: No such file or directory
/var/cache/apt/pkgcache.bin: 12M
/var/cache/apt/srcpkgcache.bin: 12M
/var/shares/Production/Yield: 25M
/var/shares/Production/Arman/Production: 9.9M
/var/shares/Operations/shaneboom.avi: 13M
/var/shares/Servers/Canopy: 39M
/var/shares/Servers/Canopy: 153M
/var/shares/HR/timeclock/LOGS/SETDTAB.TXT: 14M
/var/shares/HR/HR/hr/background: 15M
/var/shares/HR/HR/background: 15M
/var/shares/HR/background: 15M
/var/shares/Purchasing/DeadmanWalkin: 171M
/var/shares/Purchasing/JOE'S: 11M
/var/shares/Purchasing/MemberDBInstall/SASetup.EXE: 11M
/var/shares/Accounting/Marcy/backup/My: 14M
/var/shares/Accounting/HOWARD/hr/background: 15M
/var/shares/Customer: 19M
/var/shares/Customer: 33M
/var/shares/Customer: 28M
/var/shares/Customer: 78M
/var/shares/Customer: 20M
/var/shares/Customer: 20M
/var/shares/Customer: 72M
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages: 19M
/var/lib/mysql/ibdata1: 10M
/sys/devices/pci0000:00/0000:00:02.0/resource0: 128M
/sys/devices/pci0000:00/0000:00:00.0/resource0: 128M
/proc/kcore: 897M

the shares are showing up but they are on my 2nd hard drive sbd and not on sda.. 

sorry for the newb question, i've 1.7gb freespace .. but i am worried about this not being bigger because this is a production machine.

i've done the apt-get clean / autoclean etc...

any help is much appreciated and if i need to provide additional info please let me know i'll get it quick!

-cyphur

---

