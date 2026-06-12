---
title: "[SOLVED] Enemy Territory PunkBuster"
date: 2008-08-06
forum: Server Platforms
---

### Post by kihjin on 2008-08-06
I've been nearly tearing my hair out trying to figure out why I couldn't get PunkBuster to work. I thought it had something to do with modifications to cfg scripts. 

Finally I decided to do a completely fresh install and enable punkbuster without doing anything else.

```

kyle@eris:~$ etded +set sv_punkbuster 1
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/kyle/.etwolf/etmain
/home/kyle/enemy-territory/etmain/pak2.pk3 (22 files)
/home/kyle/enemy-territory/etmain/pak1.pk3 (10 files)
/home/kyle/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/kyle/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/kyle/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Bypassing CD checks
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: ------------
Alias: ----
IP: -------------
Started tty console (use +set ttycon 0 to disable)
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
execing preset_high.cfg
Hitch warning: 1447 msec frame time
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
PunkBuster Server: Corrupt or Mismatched PB Server Files (FE14)
... forever

```

What the heck is going on here? I haven't touched any of the files. They are outdated, YES, but, this doesn't seem like the correct error for that. 

```

kyle@eris:~$ ls -l enemy-territory/pb/
total 4384
drwxr-xr-x 2 kyle kyle     139 2008-08-06 21:04 htm
-rw-r--r-- 1 kyle kyle   38448 2008-08-06 21:04 pbag.so
-rw-r--r-- 1 kyle kyle   38448 2008-08-06 21:04 pbags.so
-rw-r--r-- 1 kyle kyle      87 2008-08-06 21:04 pbcl.db
-rw-r--r-- 1 kyle kyle 1089188 2008-08-06 21:04 pbcl.so
-rw-r--r-- 1 kyle kyle 1089188 2008-08-06 21:04 pbcls.so
-rw-r--r-- 1 kyle kyle    6197 2008-08-06 21:04 PB_EULA.txt
-rw-r--r-- 1 kyle kyle      87 2008-08-06 21:04 pbsv.db
-rw-r--r-- 1 kyle kyle 2053284 2008-08-06 21:04 pbsv.so
-rw-r--r-- 1 kyle kyle  152836 2008-08-06 21:04 pbweb.x86
kyle@eris:~$ ls -l enemy-territory/pb/htm
total 2580
-rw-r--r-- 1 kyle kyle   46541 2008-08-06 21:04 la001347.htm
-rw-r--r-- 1 kyle kyle  655956 2008-08-06 21:04 lc001152.htm
-rw-r--r-- 1 kyle kyle 1113258 2008-08-06 21:04 ls001149.htm
-rw-r--r-- 1 kyle kyle   66640 2008-08-06 21:04 ma001347.htm
-rw-r--r-- 1 kyle kyle  275182 2008-08-06 21:04 mc001152.htm
-rw-r--r-- 1 kyle kyle   79213 2008-08-06 21:04 wa001347.htm
-rw-r--r-- 1 kyle kyle  385305 2008-08-06 21:04 wc001152.htm
kyle@eris:~$ md5sum enemy-territory/pb/*
e32a36232d60067627dc3abfe09d105d  enemy-territory/pb/pbag.so
e32a36232d60067627dc3abfe09d105d  enemy-territory/pb/pbags.so
20e258d9e733b58dd859d84557717977  enemy-territory/pb/pbcl.db
b5b879b04b5173b64408f98828edaa1a  enemy-territory/pb/pbcl.so
b5b879b04b5173b64408f98828edaa1a  enemy-territory/pb/pbcls.so
2b1e3d4853dc61ff3ceb8cdea7d75bd3  enemy-territory/pb/PB_EULA.txt
20e258d9e733b58dd859d84557717977  enemy-territory/pb/pbsv.db
f368a002a9fc737ccdf1c5a40904a65e  enemy-territory/pb/pbsv.so
74964cd7c3f107a66f7380e95d019669  enemy-territory/pb/pbweb.x86
0eb23ef4cbab9fccdae31993408be060  enemy-territory/pb/htm/la001347.htm
aad88787d0678d952adf4fe50404e963  enemy-territory/pb/htm/lc001152.htm
7c21b56aaa9d264bb342c46337592c67  enemy-territory/pb/htm/ls001149.htm
066dba683cfe81ffc6fc78da94231162  enemy-territory/pb/htm/ma001347.htm
0a2702d8b58cfb1a167fe9678f1571a6  enemy-territory/pb/htm/mc001152.htm
dc3127ee719bfce2ded42ca39aee1bc2  enemy-territory/pb/htm/wa001347.htm
d3e163d071d19e1587179a9a989f5707  enemy-territory/pb/htm/wc001152.htm

```

I'm going to try and re-download the game... maybe that will fix this. But, the installer "verifies" the archive, if the archive was corrupted it should have picked it up there...

---

### Post by kihjin on 2008-08-06
Turns out that when I had first ran etded, punkbuster files were copied from the main directory into ~/.etwolf/pb

So, the solution to get rid of that error on a fresh install was

mv ~/.etwolf/pb .

Sigh.

---

