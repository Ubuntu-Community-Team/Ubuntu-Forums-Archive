---
title: "hash sum mismatches in todays updates"
date: 2016-02-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-02-01
Serious hash sum mismatches in todays updates. I will try again.

```

ventrical@ventrical-System-Product-Name:~$ sudo apt-get update
[sudo] password for ventrical: 
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:2 http://archive.ubuntu.com/ubuntu xenial InRelease [227 kB]               
Hit:3 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                
Hit:5 http://archive.ubuntu.com/ubuntu xenial-backports InRelease              
Get:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1,485 kB]   
Err:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages              
  Hash Sum mismatch
Get:7 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,482 kB]    
Get:8 http://ca.archive.ubuntu.com/ubuntu xenial InRelease [227 kB]            
Hit:9 http://ca.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:10 http://ca.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Get:11 http://ca.archive.ubuntu.com/ubuntu xenial/main Sources [1,129 kB]      
Err:7 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages               
  Hash Sum mismatch
Get:12 http://archive.ubuntu.com/ubuntu xenial/main Translation-en [858 kB]    
Get:13 http://ca.archive.ubuntu.com/ubuntu xenial/universe Sources [7,642 kB]  
Get:14 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7,224 kB]
Ign:14 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages         
Get:15 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7,218 kB]
Err:15 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages          
  Hash Sum mismatch
Get:16 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en [4,831 kB]
Get:17 http://ca.archive.ubuntu.com/ubuntu xenial/multiverse Sources [178 kB]  
Get:18 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1,485 kB]
Get:19 http://ca.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,482 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [139 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [135 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7,224 kB]
Get:22 http://ca.archive.ubuntu.com/ubuntu xenial/main Translation-en [858 kB] 
Get:23 http://ca.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7,223 kB]
Err:14 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages         
  Hash Sum mismatch
Get:24 http://ca.archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7,218 kB]
Get:25 http://ca.archive.ubuntu.com/ubuntu xenial/universe Translation-en [4,831 kB]
Get:26 http://ca.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [139 kB]
Get:27 http://ca.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [135 kB]
Fetched 58.2 MB in 2min 44s (354 kB/s)                                         
Reading package lists... Done

```

---

### Post by sammiev on 2016-02-01
Fully updated here with no error messages. 

Updated 3 or 4 hours ago and just tried an update. No new updates available.

---

### Post by QDR06VV9 on 2016-02-01
I see these about once a week..

---

### Post by v3.xx on 2016-02-01
> **runrickus said:**
> I see these about once a week..

So do I.  I also found out if you do another update, they usually disappear.

---

### Post by ventrical on 2016-02-01
> **v3.xx said:**
> So do I.  I also found out if you do another update, they usually disappear.

Thanks all. Yep .. it self corrected.

Regards..

---

### Post by zika on 2016-02-02
Hash mismatch is, simply put, state of repo(s) when new packages are ULed and You hit repo(s) before appropriate hashsum(s) are generated. So, Your computer just report You that there is a difference. Couple of seconds later, sums regenerated and You're good to go.

---

### Post by ventrical on 2016-02-02
> **zika said:**
> Hash mismatch is, simply put, state of repo(s) when new packages are ULed and You hit repo(s) before appropriate hashsum(s) are generated. So, Your computer just report You that there is a difference. Couple of seconds later, sums regenerated and You're good to go.

Thanks for more indepth explanation of this.

Regards..

---

