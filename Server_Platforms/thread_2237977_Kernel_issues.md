---
title: "Kernel issues"
date: 2014-08-05
forum: Server Platforms
---

### Post by Athanasios_Rigas on 2014-08-05
Hi,

I am running Ubuntu server 14.04 edition on a dedicated machine. After few days i saw (using Logwatch) in server's logs the following entries:
```

2 Time(s): *BAD*gran_size: 128K chunk_size: 128M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 128K chunk_size: 1G num_reg: 10 lose cover RAM: -512M 
2 Time(s): *BAD*gran_size: 128K chunk_size: 256M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 128K chunk_size: 2G num_reg: 10 lose cover RAM: -1536M 
2 Time(s): *BAD*gran_size: 128K chunk_size: 32M num_reg: 10 lose cover RAM: -18M 
2 Time(s): *BAD*gran_size: 128K chunk_size: 512M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 128K chunk_size: 64M num_reg: 10 lose cover RAM: -18M 
2 Time(s): *BAD*gran_size: 16M chunk_size: 2G num_reg: 10 lose cover RAM: -1010M 
2 Time(s): *BAD*gran_size: 16M chunk_size: 64M num_reg: 10 lose cover RAM: -18M 
2 Time(s): *BAD*gran_size: 1M chunk_size: 128M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 1M chunk_size: 1G num_reg: 10 lose cover RAM: -512M 
2 Time(s): *BAD*gran_size: 1M chunk_size: 256M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 1M chunk_size: 2G num_reg: 10 lose cover RAM: -1536M 
2 Time(s): *BAD*gran_size: 1M chunk_size: 32M num_reg: 10 lose cover RAM: -18M 
2 Time(s): *BAD*gran_size: 1M chunk_size: 512M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 1M chunk_size: 64M num_reg: 10 lose cover RAM: -18M 
2 Time(s): *BAD*gran_size: 256K chunk_size: 128M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 256K chunk_size: 1G num_reg: 10 lose cover RAM: -512M 
2 Time(s): *BAD*gran_size: 256K chunk_size: 256M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 256K chunk_size: 2G num_reg: 10 lose cover RAM: -1536M 
2 Time(s): *BAD*gran_size: 256K chunk_size: 32M num_reg: 10 lose cover RAM: -18M 
2 Time(s): *BAD*gran_size: 256K chunk_size: 512M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 256K chunk_size: 64M num_reg: 10 lose cover RAM: -18M 
2 Time(s): *BAD*gran_size: 2M chunk_size: 128M num_reg: 10 lose cover RAM: -16M 
2 Time(s): *BAD*gran_size: 2M chunk_size: 1G num_reg: 10 lose cover RAM: -512M 
...
...
...

```

I have asked from my host provider to replace RAM and update the BIOS, but unfortunately the problem persists. 
Should i worry about the above errors? If yes, is there something to do in order to tackle the above issue?
Many thanks in advance.

Kind regards

---

### Post by Gyokuro on 2014-08-07
Hi

I have seen such errors in the past (MTRR-errors) and I would suggest you that you file an Ubuntu kernel bug report - are you aware that you are receiving this error since the last kernel update or does the problem persist since the release of Trusty? You should check your syslog/dmesg log.

- HTH

---

### Post by Athanasios_Rigas on 2014-08-08
Hi,

How do i file a bug report?

-anarchos78

---

### Post by QIII on 2014-08-08
Hello!

Could you give us the specs on your machine?  I see a couple of MTRR errors reported on Launchpad (but some are old...).

It could be that you need a BIOS/EFI update, you need to change the amount of memory reserved for a GPU, etc.

---

### Post by Gyokuro on 2014-08-08
Hi

To fill a bug report follow the mentioned steps in the wiki: [https://wiki.ubuntu.com/Kernel/Bugs](https://wiki.ubuntu.com/Kernel/Bugs)

but at first and as QIII mentioned try whether there are BIOS/EFI updates are available and to change the amount of reserved GPU memory (often it helps to lower it) and in  case nothing helps fill the bug report.

- HTH

---

### Post by Athanasios_Rigas on 2014-08-08
@[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1323068")Gyokuro
Hi,

Unfortunately the problem still here after BIOS update. I didn't got the GPU memory part. I have installed Ubuntu (v14.04) on a dedicated (rack) machine. I don't think that there is any GPU unit in there (not sure). As for the problem, i have noticed it since the initial installation. I have already installed a newer kernel version: 3.14.0-031400rc6-generic but the problem persists. Any ideas?

---

### Post by Gyokuro on 2014-08-09
Hi

What I mean with the GPU memory is that there is a setting in your BIOS to change the VGA RAM size for the integrated GPU chip - how it's called depends on your board/bios. Does the problem persist if you using a kernel from kernel.org (3.16) as I think you have enough knowledge to compile it yourself and in case the problem remains it's faster to post a bug report at kernel.org ([https://bugzilla.kernel.org/](https://bugzilla.kernel.org/)). Sorry for no better help but this errors are quite rare.

---

### Post by Athanasios_Rigas on 2014-08-09
OK i will upgrade kernel and see how it goes.

---

