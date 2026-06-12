---
title: "Extremely peculiar behaviour on Ubuntu VM"
date: 2018-06-20
forum: Virtualisation
---

### Post by hypomania2 on 2018-06-20
Hello everyone,

I have been experiencing an extremely peculiar behaviour with my VM's running on Virtual Box. The host is Windows 7 machine, fresh install). I have a fresh VB install and fresh Ubuntu image 18.04. The settings are as follows:


4 CPU cores, PAE/NX enabled (I am running Intel Xeon E5 2640 v4 with 10 cores on the host)


4 GB of ram (out of 32 GB on host)


VT-x + Nested Paging enabled


50 GB fixed storage allocation, using SATA controller, HOST I/O cache enabled, "solid state drive" ticked (I have two 500 GB Samsung 850 Evo SSD's in AHCI mode on the host)




The problem is that it barely works. Every third time I try to boot it, it freezes on the "Ubuntu" loading screen, forcing me to power off the machine. When it boots, it's **extremely** slow. It's slow in a sense that when I type in a wrong command in the terminal, it takes ~30 seconds for the system to recognize the command as wrong and say "command not found". Using apt-get install fetches the files very quickly, but the unpacking part takes ages, maybe ~1 minute per a file to unpack, totaling in 20 minutes to install php5, which is a 25mb package. The GUI is very responsive. It seems like it's just any drive I/O operation is being slow. However, my I/O speed and usage tests say otherwise - I/O usage is at 0-1% in System Monitor. Running ```
sudo hdparm -Tt /dev/sda
``` gives "Timing cached reads" 9363 MB/sec, "Timing buffered disk reads" 1192 MB/sec.


I have tried reinstalling VB, reinstalling the host OS, creating a new image from scratch, importing an image. My friend has **an identical** hardware and software setup, he doesn't have this issue. It only started happening recently and I honestly have no idea about what's going on, I am out of ideas.


Any advice or suggestion is more than welcome!

P.S I am installing a new image right now, the minimal version has taken 4 hours so far, and it's still installing.. Is it a VB's or my system's fault?

---

### Post by QIII on 2018-06-20
Moved to Virtualisation for a more appropriate fit.

---

### Post by &amp;KyT$0P# on 2018-06-20
What VirtualBox version and how did you install it?

Is something else eating up your host's resources?

Is there a specific reason you need the VM's virtual disk to be a SSD?

---

### Post by LHammonds on 2018-06-20
> **hypomania2 said:**
> I have been experiencing an extremely peculiar behaviour with my VM's running on Virtual Box. The host is Windows 7 machine, fresh install). I have a fresh VB install and fresh Ubuntu image 18.04.
Not sure what is going on.  Ubuntu Server VMs (no GUI) are working fairly well for me under VirtualBox on Windows 10.  The VM behaves about the same on my VMware ESXi servers as it does on my PC via VirtualBox.

I'm using VirtualBox 5.2.12 and Ubuntu Server 18.04 LTS (alternative ISO, not the "live" ISO)

LHammonds

---

### Post by CharlesA on 2018-06-20
I'm running Ubuntu 16.04 on KVM with no issues. Have you tried booting a livecd and seeing if it behaves the same?

[Could also try ye ol dd test]("https://www.thomas-krenn.com/en/wiki/Linux_I/O_Performance_Tests_using_dd"):

```
dd if=/dev/zero of=/tmp/test bs=1M count=10240 oflag=direct
```

This is what I get on my 16.04.4 VM on a RAID-1 SSD via KVM:

```
charles@Titan:~$ dd if=/dev/zero of=/tmp/test bs=1M count=10240 oflag=direct
10240+0 records in
10240+0 records out
10737418240 bytes (11 GB, 10 GiB) copied, 1.89344 s, 5.7 GB/s

```

---

### Post by hypomania2 on 2018-06-21
VB 5.2.12, installed through .exe installer. No particular reason for it being an SSD, I thought that would optimize performance.

Anyway, I fixed the problem by "Use host I/O cache" on the SATA controller.

---

### Post by hypomania2 on 2018-06-21
I fixed the problem by "Use host I/O cache" on the SATA controller, must dislike the dual SSD setup :)

---

### Post by hypomania2 on 2018-06-21
Saved the command ;)

Insane speed though, I am not getting anything above 450 MB/s

---

### Post by LHammonds on 2018-06-21
Good to know hypomania2.

Was also curious about the ye old dd test on my servers...but one test would not yield accurate results since there are many VMs in use so I ran it multiple times and on different versions.

**Ubuntu Server 16.04.4 LTS** on VMware ESXi (SAS RAID5) (shared by many VMs)
Command: ```
dd if=/dev/zero of=/bak/test bs=1M count=3240 oflag=direct
```
Results after multiple runs: ```
3397386240 bytes (3.4 GB, 3.2 GiB) copied, 17.7719 s, 191 MB/s
3397386240 bytes (3.4 GB, 3.2 GiB) copied, 14.3560 s, 237 MB/s
3397386240 bytes (3.4 GB, 3.2 GiB) copied, 18.6472 s, 182 MB/s
3397386240 bytes (3.4 GB, 3.2 GiB) copied, 17.3100 s, 196 MB/s
```

**Ubuntu Server 18.04 LTS** on VMware ESXi (SAS RAID5) (shared by many VMs)
Command: ```
dd if=/dev/zero of=/bak/test bs=1M count=2240 oflag=direct
```
Results after multiple runs: ```
2348810240 bytes (2.3 GB, 2.2 GiB) copied, 18.4878 s, 127 MB/s
2348810240 bytes (2.3 GB, 2.2 GiB) copied, 11.4518 s, 205 MB/s
2348810240 bytes (2.3 GB, 2.2 GiB) copied, 9.59828 s, 245 MB/s
2348810240 bytes (2.3 GB, 2.2 GiB) copied, 9.40841 s, 250 MB/s
```

**Ubuntu Server 18.04 LTS** on a Win10 PC via VirtualBox (SATA) (No other VMs running which means more consistent results)
Command: ```
dd if=/dev/zero of=/bak/test bs=1M count=2000 oflag=direct
```
Results after multiple runs: ```
2097152000 bytes (2.1 GB, 2.0 GiB) copied, 31.7891 s, 66.0 MB/s
2097152000 bytes (2.1 GB, 2.0 GiB) copied, 31.9287 s, 65.7 MB/s
2097152000 bytes (2.1 GB, 2.0 GiB) copied, 28.8840 s, 72.6 MB/s
2097152000 bytes (2.1 GB, 2.0 GiB) copied, 28.4221 s, 73.8 MB/s
```

LHammonds

---

