---
title: "ubuntu kernel: [  729.529501] [UFW ALLOW] ,[UFW AUDIT]"
date: 2011-12-26
forum: Server Platforms
---

### Post by ryzingsrinivas on 2011-12-26
Hi ,

     In our ubuntu server 10.10 ,we are getting below logs .Every day i  need to restart server ,other wise it will not accessible.Some times ,i  need to restart two times.
   When i ping google.com  ,it was very slow .some times  host not reachable .After reboot ,it will ping as good.


I am using Uncomplicated firewall(UFW). i am opening ports as,ufw allow 8098/tcp .


Dec 26 16:35:15 ubuntu kernel: [  729.529501] [UFW ALLOW] IN=eth0 OUT=  MAC=e0:69:95:77:a7:30:d8:5d:4c:c1:46:af:08:00 SRC=122.177.146.51  DST=192.168.1.108 LEN=52 TOS=0x00 PREC=0x00 TTL=120 ID=12974 DF  PROTO=TCP SPT=13871 DPT=8098 WINDOW=8192 RES=0x00 SYN URGP=0
Dec 26 16:35:38 ubuntu kernel: [  752.395639] [UFW AUDIT] IN=eth0 OUT=  MAC=e0:69:95:77:a7:30:d8:5d:4c:c1:46:af:08:00 SRC=122.177.146.51  DST=192.168.1.108 LEN=52 TOS=0x00 PREC=0x00 TTL=120 ID=13050 DF  PROTO=TCP SPT=13872 DPT=8098 WINDOW=8192 RES=0x00 SYN URGP=0
Dec 26 16:35:38 ubuntu kernel: [  752.395668] [UFW ALLOW] IN=eth0 OUT=  MAC=e0:69:95:77:a7:30:d8:5d:4c:c1:46:af:08:00 SRC=122.177.146.51  DST=192.168.1.108 LEN=52 TOS=0x00 PREC=0x00 TTL=120 ID=13050 DF  PROTO=TCP SPT=13872 DPT=8098 WINDOW=8192 RES=0x00 SYN URGP=0
Dec 26 16:35:47 ubuntu kernel: [  761.030564] [UFW AUDIT] IN=eth0 OUT=  MAC=e0:69:95:77:a7:30:d8:5d:4c:c1:46:af:08:00 SRC=122.177.146.51  DST=192.168.1.108 LEN=52 TOS=0x00 PREC=0x00 TTL=120 ID=13073 DF  PROTO=TCP SPT=13873 DPT=8098 WINDOW=8192 RES=0x00 SYN URGP=0
Dec 26 16:35:47 ubuntu kernel: [  761.030593] [UFW ALLOW] IN=eth0 OUT=  MAC=e0:69:95:77:a7:30:d8:5d:4c:c1:46:af:08:00 SRC=122.177.146.51  DST=192.168.1.108 LEN=52 TOS=0x00 PREC=0x00 TTL=120 ID=13073 DF  PROTO=TCP SPT=13873 DPT=8098 WINDOW=8192 RES=0x00 SYN URGP=0
Dec 26 16:35:47 ubuntu kernel: [  761.098056] [UFW ALLOW] IN=eth0 OUT=  MAC=e0:69:95:77:a7:30:d8:5d:4c:c1:46:af:08:00 SRC=122.177.146.51  DST=192.168.1.108 LEN=52 TOS=0x00 PREC=0x00 TTL=120 ID=13076 DF  PROTO=TCP SPT=13874 DPT=8098 WINDOW=8192 RES=0x00 SYN URGP=0


The above logs are coming for another ports also.

How my sever is accessable always ,with out rebooting on  daily basis.
Please hep me
--
Srinu

---

