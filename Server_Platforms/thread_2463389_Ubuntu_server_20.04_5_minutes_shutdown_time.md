---
title: "Ubuntu server 20.04 5 minutes shutdown time"
date: 2021-06-10
forum: Server Platforms
---

### Post by deepakdeshp on 2021-06-10
Hi ,
Ubuntu server 20.04 with all patches applied sometimes takes more than 5.5 minutes to shutdown. The error message is about the swap. Any more information I can give?

---

### Post by LHammonds on 2021-06-10
> **deepakdeshp said:**
> Hi ,
Ubuntu server 20.04 with all patches applied sometimes takes more than 5.5 minutes to shutdown. The error message is about the swap. Any more information I can give?
#1 - What is the exact error message?
#2 - Is it a partition or file swap?  Output of "swapon -s"
#3 - Specific version of Ubuntu would be nice.  Output of "uname -a" and "lsb_release -a"
#4 - Is your application requiring more RAM than you have and thus overusing the swap and maxing it out too?  Output of "free" while under normal use.
#5 - Have you checked the HD for errors such as examining the S.M.A.R.T. data if IDE or SCSI (if enabled in BIOS), etc.?
```

lsblk
sudo smartctl -a /dev/sda > /tmp/sda_smart.txt

```

LHammonds

---

### Post by scorp123 on 2021-06-10
> **deepakdeshp said:**
>  The error message is about the swap.... 

Not really much to go by, your description is too vague. Could you post a screenshot or a picture so we can see what's happening or see what you see?

---

### Post by deepakdeshp on 2021-06-10
[SIZE=1]> **LHammonds said:**
> #1 - What is the exact error message?
#2 - Is it a partition or file swap?  Output of "swapon -s"
#3 - Specific version of Ubuntu would be nice.  Output of "uname -a" and "lsb_release -a"
#4 - Is your application requiring more RAM than you have and thus overusing the swap and maxing it out too?  Output of "free" while under normal use.
#5 - Have you checked the HD for errors such as examining the S.M.A.R.T. data if IDE or SCSI (if enabled in BIOS), etc.?
```

lsblk
sudo smartctl -a /dev/sda > /tmp/sda_smart.txt

```

LHammonds
Thank you. This is a virtual machine. There is some delay because of the mysql message below but most of the delay is due to the swapfile message below.
The system  message is [I]stopjob is running on mysql community server

[/I][/SIZE][COLOR=#000000][SIZE=1][COLOR=#292929][FONT=medium-content-serif-font, Georgia, Cambria, Times New Roman, Times, serif]*a swa*[/FONT][/COLOR][COLOR=#292929][FONT=medium-content-serif-font, Georgia, Cambria, Times New Roman, Times, serif]*pjob is running on /swapfile swapfile.img*[/FONT][/COLOR][/SIZE][/COLOR]
[SIZE=1]
```
 lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
uma@ubuntu:~$ swapon -a
uma@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
uma@ubuntu:~$ swapon -s
Filename                Type        Size    Used    Priority
/swapfile                                  file        1048572    1024824    -2
/swap.img                                  file        4194300    163620    -3
uma@ubuntu:~$ uname -a
Linux ubuntu 5.4.0-74-generic #83-Ubuntu SMP Sat May 8 02:35:39 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
uma@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
fd0      2:0    1   1.4M  0 disk 
loop0    7:0    0  55.5M  1 loop /snap/core18/1997
loop1    7:1    0    99M  1 loop /snap/core/11081
loop2    7:2    0  55.4M  1 loop /snap/core18/2066
loop3    7:3    0 131.6M  1 loop /snap/docker/796
loop4    7:4    0  99.2M  1 loop /snap/core/11167
loop5    7:5    0  26.1M  1 loop /snap/heroku/4048
loop6    7:6    0  25.9M  1 loop /snap/heroku/4037
loop7    7:7    0    95M  1 loop /snap/juju/16423
loop8    7:8    0    95M  1 loop /snap/juju/16337
loop9    7:9    0  70.4M  1 loop /snap/lxd/19647
loop10   7:10   0  67.6M  1 loop /snap/lxd/20326
loop11   7:11   0  32.1M  1 loop /snap/snapd/11841
loop12   7:12   0  32.1M  1 loop /snap/snapd/12057
sda      8:0    0    41G  0 disk 
&#9500;&#9472;sda1   8:1    0     1M  0 part 
&#9492;&#9472;sda2   8:2    0    41G  0 part /
sr0     11:0    1  93.2M  0 rom  
sr1     11:1    1  1024M  0 rom  


  
```
smartctl isnt supported on vmware vm. The SMART report of the host system is attached.[/SIZE]

---

### Post by deepakdeshp on 2021-06-10
> **scorp123 said:**
> Not really much to go by, your description is too vague. Could you post a screenshot or a picture so we can see what's happening or see what you see?
The error message disappeared and I didnt note it down. I have posted it above.

---

### Post by LHammonds on 2021-06-10
Did not see anything amiss with the smart data although that is never 100% conclusive evidence there is not a problem.  It just helps identify if it "does" find errors.

You skipped over #4 regarding the all-important "usage" of swap for your system using the "free" command.

You need to know if your application(s) are wanting more RAM than you have allocated.  You really do not want your swap file being utilized.  It is only there as an emergency catch to keep your system running in the event you do not have enough RAM for a specific task.

If you check the "free" command periodically throughout the day during the busy times, you will get a good idea as to the use of the swap file.

Still not sure about the actual cause of the issue.  Have to wonder if its trying to prepare for a hibernate and cannot because the swap is smaller than the RAM.  But we would need to know the amount of RAM the system has....which I have not seen yet but I can see that you have 2 swap files...a 1G and 4G which totals 5G.  Might be a good idea to just create a single file, set it as active and remove the other two....but before you make any chances, you really need to know if you are low on system RAM and overusing the existing swap space.  If so, allocate more RAM....if you cannot, you may need to increase swap space but utilizing swapspace for RAM severely impacts performance.

LHammonds

---

### Post by deepakdeshp on 2021-06-10
I deleted the 1 GB /swapfile and will observe the swap usage . IMHO the swap usage shoudnt affect the shutdown time. Or will it?

```
  sudo swapon --showNAME      TYPE SIZE   USED PRIO
/swap.img file   4G 577.3M   -2
uma@ubuntu:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:          1.4Gi       1.1Gi        80Mi        47Mi       264Mi       128Mi
Swap:         4.0Gi       576Mi       3.4Gi


  
```

A stop job is running on swap.img is active for 2 minutes 45 seconds as I shut down.

---

### Post by MAFoElffen on 2021-06-11
To others, the OP noted this is not running on "Metal."
> **deepakdeshp said:**
> [SIZE=3]smartctl isnt supported on vmware vm. The SMART report of the host system is attached.[/SIZE]
Point #1:
So this is a [COLOR=#ff0000]VMware VM[/COLOR] running on what? vSphere? ESXi? VMware Player? VMware Workstation? And what is the Virtual Host system specs and the OS it is running?

Could you please post the VM configuration? Especially the allocated VCPUs and the memory you allocated it... for example the VM config file in ESXi is a text file "<VM_name>.vmx". It would help if the people trying to help you knew the box/container it was constrained within.

Point #2:
Rule of thumb is to set swap at 1.5 times the allocated memory. So 1GB would assume your only running it in less than 400MB allocated memory? Or did you just not make a large enough swap?

---

### Post by deepakdeshp on 2021-06-14
> **MAFoElffen said:**
> To others, the OP noted this is not running on "Metal."

Point #1:
So this is a [COLOR=#ff0000]VMware VM[/COLOR] running on what? vSphere? ESXi? VMware Player? VMware Workstation? And what is the Virtual Host system specs and the OS it is running?

Could you please post the VM configuration? Especially the allocated VCPUs and the memory you allocated it... for example the VM config file in ESXi is a text file "<VM_name>.vmx". It would help if the people trying to help you knew the box/container it was constrained within.

Point #2:
Point #1
Rule of thumb is to set swap at 1.5 times the allocated memory. So 1GB would assume your only running it in less than 400MB allocated memory? Or did you just not make a large enough swap?

Point #1
It is a vmware running under vmware workstation. I have alloted 1.9 GB RAM 4 CPUs to the vm.  The host CPU is 8 core Ryzen 3500U. The host OS is Mint 20.1 which is based on Ubuntu Linux 20.04.

Point #2

The typical memory usage is as follows.

```
  free -m              total        used        free      shared  buff/cache   available
Mem:           1829        1142         166          63         520         446
Swap:          4095         614        3481


 
```

---

### Post by MAFoElffen on 2021-06-14
I allocate 2 or more vcpu's. You're good there for what you seem to be doing.

On your memory allocation for the VM, add more. It shows you are hitting your memory threshold and using your swap. Y0ur swap is a fallback/safeguard to running out of memory. Right? 

Just saying. Play with reallocating more memory available to the VM and find a good balance.

What are the processes showing in TOP during that?

---

