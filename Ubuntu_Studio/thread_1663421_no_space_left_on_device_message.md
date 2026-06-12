---
title: "no space left on device message"
date: 2011-01-09
forum: Ubuntu Studio
---

### Post by hanker77 on 2011-01-09
I am getting a "No space left on device" message.

running a df -h and i get the following
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5              27G   15G   11G  58% /
none                  1.5G  324K  1.5G   1% /dev
none                  1.5G   96K  1.5G   1% /dev/shm
none                  1.5G  104K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1              24G   19G  4.9G  80% /media/FED2F54BD2F508A3
/dev/sda1             100M   25M   76M  25% /media/System_Reserved
/dev/sdc1             1.9T 1020G  844G  55% /media/New Volume

note i have ubuntu studio 10.04 and i have noticed that after receving this message if I delete a file from my home folder /home/user1 I can then save a file. In some cases I cannot even open a new program or mount a drive since it looks like that no space is available... 
is there any restriction might be defined by default? I have also checked users quotas and they are not enabled.

any clue is very appreciated.
thanks!

---

### Post by Alex1200GS on 2011-01-19
What's the output of **df -i**?

---

