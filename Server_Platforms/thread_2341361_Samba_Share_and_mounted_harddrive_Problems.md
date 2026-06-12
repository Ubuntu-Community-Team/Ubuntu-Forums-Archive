---
title: "Samba Share and mounted harddrive Problems"
date: 2016-10-27
forum: Server Platforms
---

### Post by firetech2 on 2016-10-27
So I decided to switch from windows server to Ubuntu server a few weeks ago, and I made a samba share that I can access from my windows 10 machine but when I move a file from windows to my share the file is transferred to the folder but on the wrong HDD

Ubuntu is installed on /dev/sdb      /dev/mapper/server--vg-root

 and the other drive/partition is /dev/sda1 and is mounted to /srv/sambashare

when I trasfer a file from my windows 10 machine to sambashare and go to my Ubuntu server and write df -h the file is using space on /dev/mapper/server--vg-root

I probably just missed a little detail but i can't find an answer on google the helps me solve this

[B]Samba conf lines


[/B][sambashare]
comment = Film og Serier
path = /srv/sambashare
read only = no
create mask = 0777
guest ok = yes
hide files = /lost+found/

Sorry for my bad English not my native language :)

---

### Post by firetech2 on 2016-10-27
ok don't mind my stupid question it's working without any configuration i just misread the tables -.- *dooh*

---

