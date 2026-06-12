---
title: "[Solved] Silly question re. zsync but how much did I download?"
date: 2016-03-31
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2016-03-31
I've been using zsync to keep an iso updated:```
07:03 AM ~ $ zsync http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso.zsync
#################### 100.0% 92.6 kBps DONE      

reading seed file xenial-desktop-amd64.iso: ****************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read xenial-desktop-amd64.iso. Target 82.7% complete.      
downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
################---- 82.8% 79.3 kBps         A   

downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
################---- 82.9% 85.1 kBps         A   

downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
#################--- 87.7% 97.1 kBps         TA  

downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
#################--- 88.2% 102.3 kBps 19:06 ETA  read: Connection reset by peer
#################--- 88.2% 95.9 kBps         

downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
#################--- 88.7% 95.4 kBps         A   

downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
##################-- 92.9% 0.3 kBps         TA   
##################-- 93.7% 0.6 kBps         TA   
##################-- 94.9% 0.6 kBps         A    
###################- 96.0% 98.5 kBps         A   

downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
###################- 99.9% 96.3 kBps            

downloading from http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso:
#################### 100.0% 80.5 kBps DONE       

verifying download...checksum matches OK
used 826265600 local, fetched 173555991
08:22 AM ~/ZSYNC $ 
```What do
*used 826265600 local*
and
*fetched 173555991*
mean?

Does the first line mean the size of the iso on my system is currently 787.99 MB ((787.98828125/1024)/1024)?

Does the second line mean that I've downloaded 16.55 MB ((173555991/1024)/1024) this time?

---

### Post by sudodus on 2016-03-31
826265600 (local) + 173555991 (fetched) = [COLOR="#0000FF"]999821591[/COLOR] (total number of bytes, probably some extra bytes for handshaking, package management and such things)

ls -l xenial-desktop-amd64.iso
-rw------- 1 sudodus sudodus [COLOR="#0000FF"]999292928[/COLOR] mar 30 17:25 xenial-desktop-amd64.iso

---

### Post by vasa1 on 2016-03-31
Okay, this like what I see:```
10:58 AM ~/ZSYNC $ ll
total 1951868
-rw------- 1 vasa1 vasa1 999292928 Mar 30 17:25 xenial-desktop-amd64.iso
-rw------- 1 vasa1 vasa1 999292928 Mar 29 17:34 xenial-desktop-amd64.iso.zs-old
10:58 AM ~/ZSYNC $ 

```So I'm I correct in thinking that to get the latest sync done, 16.55 MB were used?

---

### Post by sudodus on 2016-03-31
173555991 bytes = 174 MB = 173555991/1024/1024 Mibibytes = 165.5 Mibibytes

---

### Post by vasa1 on 2016-03-31
> **sudodus said:**
> 173555991 bytes = 174 MB = 173555991/1024/1024 Mibibytes = 165.5 Mibibytes
Oops!
Thank you!

---

### Post by howefield on 2016-03-31
You get an idea of how much it needs to download (in percentage terms) at the top of the output after zsync reads the seed file, in this case it has 82.8% of the target so needs to download 17.2% of the updated file.

---

### Post by vasa1 on 2016-03-31
> **howefield said:**
> You get an idea of how much it needs to download (in percentage terms) at the top of the output after zsync reads the seed file, in this case it has 82.8% of the target so needs to download 17.2% of the updated file.

Thanks!

I'll mark this Solved.

---

