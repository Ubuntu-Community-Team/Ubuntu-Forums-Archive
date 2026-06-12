---
title: "Ubuntu 10.04 host | Win7 64 Guest | High CPU on guest"
date: 2012-04-20
forum: Virtualisation
---

### Post by cocamoxb on 2012-04-20
Hello all. I recently moved a Windows 7 64-bit Enterprise disk image to a VMDK via the VMware converter tool and began using it in VirtualBox 4.1.12. I have it setup and it works but when running any program at all in the guest it becomes almost unusable. I also have a natively created Windows 7 64-bit Pro guest which runs just fine. I have selected all the same options in both guest configurations and there is still no difference. 

I suspect that there is something with Windows 7 64-bit Enterprise that doesn't meld well with VB drivers or VB isn't handling the Windows 7 requests or processes well.:confused:

Below are the variables that I've attempted to little or no success. I have also attached the log and screen shots that may be relevant. If you have any ideas, they would be most appreciated. Thank you.

Symptoms:
Booting Win7 64-bit VM boots to Windows animated splash screen - fairly quick
Transition from Animated Boot screen to black screen - 60-120 seconds
Windows background with "Welcome" screen and spinning blue circle - 30-60 seconds
Login screen  to desktop after credentials input - 10-15 seconds
Desktop to all startup programs - 20-45 seconds
Launching Outlook\other program - 45-120 seconds & screen refresh is VERY slow


**Host:** Ubuntu 10.04 64
**Guest:** Windows 7 64-bit Enterprise SP1

_Virtualbox_

System:
Base Memory:4096 MB
Boot Order:CD/DVD-ROM, Hard Disk
CPU: 1 [COLOR=Red]*(Attempted 2 with no change)*[/COLOR]
Acceleration:VT-x/AMD-V, Nested Paging *[COLOR=Red](Removed Nested Paging to no improvement)[/COLOR]*

Display:
Video Memory:64 MB [COLOR=Red]*(Tried 64 & 128MB)*[/COLOR]
Acceleration:2D Video, 3D [COLOR=Red]*(Enabled & Disabled both)*[/COLOR]
Remote Desktop Server:Disabled

Storage:
SATA Controller
  SATA Port 0: T400.corporate.net.vmdk (Normal, 298.09 GB)
IDE Controller
  IDE Secondary Master (CD/DVD):VBoxGuestAdditions.iso (48.42 MB)

Audio: [COLOR=Red]*(Disabled & Enabled)*[/COLOR]
Host Driver:ALSA Audio Driver
Controller:Intel HD Audio

Network: [COLOR=Red]* (Disabled & Enabled)*[/COLOR]
Adapter 1:Intel PRO/1000 MT Desktop (Bridged adapter, eth0)

---

### Post by CharlesA on 2012-04-20
It shouldn't be having any problems. I've converted a few Win7 Pro boxes to VBox and they have performed fine.

Does the same thing happen if you try safe mode?

---

### Post by cocamoxb on 2012-04-20
> **CharlesA said:**
> It shouldn't be having any problems. I've converted a few Win7 Pro boxes to VBox and they have performed fine.

Does the same thing happen if you try safe mode?


Yes, safe mode functions about the same, given that there are so many limited resources used.

---

### Post by CharlesA on 2012-04-20
Have you just tried cloning the machine instead of using the vmware converter?

---

### Post by cocamoxb on 2012-04-20
> **CharlesA said:**
> Have you just tried cloning the machine instead of using the vmware converter?

I have not. I have the hard drive with the native Win7 on it but I haven't found a good way to clone it vs. convert it.

If you have a good process, please let me know. I'd love to try it. Thanks.

---

### Post by CharlesA on 2012-04-20
I use clonezilla to image the drive, then restore it to a VM.

---

### Post by cocamoxb on 2012-04-21
> **CharlesA said:**
> I use clonezilla to image the drive, then restore it to a VM.

Charles,

My physical disc with Win7 is 320gb but only about 30gb used. Have you ever restored a Clonzilla image to a smaller VM disc? I'd like to restore the image to a Vbox dynamic virtual disc if possible.

---

### Post by CharlesA on 2012-04-21
As long as the virtual disk is set to something at least that large, even as dynamic, you can restore to it.

As far as I know Clonezilla is unable to restore to a smaller drive.

---

### Post by cocamoxb on 2012-04-21
Thank you. I will give it a shot.

---

### Post by Dedoimedo on 2012-04-23
Can you run process explorer from sysinternals inside windows to figure out what is causing all the interrupts and such?

Likewise on the host, can you run:

"strace -c -p <vbox pid>" for about 1-2 min while it's using high cpu and then report the output here? The top 10 lines will be sufficient.

Cheers,
Dedoimedo

---

### Post by cocamoxb on 2012-04-24
> **CharlesA said:**
> As long as the virtual disk is set to something at least that large, even as dynamic, you can restore to it.

As far as I know Clonezilla is unable to restore to a smaller drive.


Charles,

I used clonezilla and restored to a VM but I get the famous BSOD with the failed self repair. I'm guessing it's because the HDD driver mapping MS does.

Have you been able to resolve that?:confused:

---

### Post by cocamoxb on 2012-04-24
> **Dedoimedo said:**
> Can you run process explorer from sysinternals inside windows to figure out what is causing all the interrupts and such?

Likewise on the host, can you run:

"strace -c -p <vbox pid>" for about 1-2 min while it's using high cpu and then report the output here? The top 10 lines will be sufficient.

Cheers,
Dedoimedo


Dedoimedo, here is the output you requested. Also, see attached the Win7 Process Explorer screen shot. I eagerly look forward to your thoughts.

 ](*,)

Thank you kindly.



```
  PID TTY      STAT   TIME COMMAND
 3257 ?        Sl     0:02 /usr/lib/virtualbox/VirtualBox
3313 ?        Sl     0:13 /usr/lib/virtualbox/VirtualBox --comment Win7-VM --startvm bf33fc43-a935-4670-ad3e-59ec54243383 --no-startvm-errormsgbox


Process 3313 attached - interrupt to quit
Process 3313 detached
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 99.24  294.488040         720    408806           poll
  0.33    0.987239           4    236056           writev
  0.19    0.558512          15     36445         1 ioctl
  0.16    0.467012          20     23635      1916 futex
  0.04    0.113414          32      3562           mmap
  0.03    0.101508           0    480820    338332 read
  0.01    0.032628           5      5958           mprotect
  0.00    0.007654           1      5374           write
  0.00    0.000093           0       245       245 inotify_add_watch
  0.00    0.000038           0      5299           sched_yield
  0.00    0.000000           0        75        35 open
  0.00    0.000000           0        54           close
  0.00    0.000000           0        51        36 stat
  0.00    0.000000           0        40           fstat
  0.00    0.000000           0         1           lstat
  0.00    0.000000           0        18           lseek
  0.00    0.000000           0        39           munmap
  0.00    0.000000           0         3           brk
  0.00    0.000000           0         3           rt_sigaction
  0.00    0.000000           0         4           access
  0.00    0.000000           0        28           uname
  0.00    0.000000           0         1           semop
  0.00    0.000000           0         1           fcntl
  0.00    0.000000           0         1           unlink
  0.00    0.000000           0         4           getuid
  0.00    0.000000           0         4           getgid
  0.00    0.000000           0         3           geteuid
  0.00    0.000000           0         2           getegid
  0.00    0.000000           0        75           gettid
  0.00    0.000000           0         1           restart_syscall
------ ----------- ----------- --------- --------- ----------------
100.00  296.756138               1206608    340565 total
```





```
Process 3257 detached
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 77.21    0.071996           3     22281      1222 futex
 21.61    0.020148           1     19769           poll
  0.55    0.000516           0     11497           writev
  0.32    0.000302           0      4815           mmap
  0.20    0.000190           0     21750     15217 read
  0.10    0.000093           0      7177           write
  0.00    0.000000           0         1           open
  0.00    0.000000           0        14           close
  0.00    0.000000           0       699           stat
  0.00    0.000000           0      5718           mprotect
  0.00    0.000000           0         2           munmap
  0.00    0.000000           0         3           rt_sigaction
  0.00    0.000000           0        68           sched_yield
  0.00    0.000000           0         3           uname
  0.00    0.000000           0         1           unlink
  0.00    0.000000           0         1           restart_syscall
  0.00    0.000000           0       297       297 inotify_add_watch
------ ----------- ----------- --------- --------- ----------------
100.00    0.093245                 94096     16736 total
```

---

### Post by CharlesA on 2012-04-24
> **cocamoxb said:**
> Charles,

I used clonezilla and restored to a VM but I get the famous BSOD with the failed self repair. I'm guessing it's because the HDD driver mapping MS does.

Have you been able to resolve that?:confused:

I haven't run into that problem. Are you using an IDE controller or SATA controller on the VM?

---

### Post by cocamoxb on 2012-04-24
> **CharlesA said:**
> I haven't run into that problem. Are you using an IDE controller or SATA controller on the VM?

I've tried SATA & SAS as the controller for the VM. The original physical drive was a SATA but I'm not sure how Windows used it. I can't even get to safe mode due to the hardware driver not functioning. I get the BSOD for safe mode.

---

### Post by CharlesA on 2012-04-24
Try setting it as IDE and seeing it it'll boot. It's probably throwing an "inaccessible boot device" error at you.

---

### Post by cocamoxb on 2012-04-25
> **CharlesA said:**
> Try setting it as IDE and seeing it it'll boot. It's probably throwing an "inaccessible boot device" error at you.

I tried with SATA, ISCSI, SAS, & IDE as the controller type all with the VDI from the Clonezilla restore and no beans.

Any other ideas would be appreciated. Again, thank you kindly.

---

### Post by Dedoimedo on 2012-04-28
Sorry for getting back to you so late.

Looking at your output, system calls poll take a long time while you have a huge number of read errors. Can you please try the following now:

"strace -e trace=read -s 512 -o somefile -p <vbox pid>"
"strace -e trace=poll -s 512 -o somefile -p <vbox pid>"

Then please attach here or post first 10-15 lines of each. I want to figure out why so many errors or such long calls. That could explain the issues.

Dedoimedo

---

### Post by cocamoxb on 2012-04-30
> **Dedoimedo said:**
> Sorry for getting back to you so late.

Looking at your output, system calls poll take a long time while you have a huge number of read errors. Can you please try the following now:

"strace -e trace=read -s 512 -o somefile -p <vbox pid>"
"strace -e trace=poll -s 512 -o somefile -p <vbox pid>"

Then please attach here or post first 10-15 lines of each. I want to figure out why so many errors or such long calls. That could explain the issues.

Dedoimedo


I have attached the read & poll files as requested.


**note** - I have since upgraded from 10.04LTS to 12.04LTS. The over all Windows 7 guest VM boot and speed has improved but when running Outlook in the guest the video refresh and general performance of the video seems to be the general issue.





READ output:


read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, "\1\0\0\0\0\0\0\0", 16)        = 8
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(14, 0x7fff15737c00, 16)            = -1 EAGAIN (Resource temporarily unavailable)
read(27, "\372", 1)                     = 1







POLL output:


poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 0) = 0 (Timeout)
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 98) = 1 ([{fd=14, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 52) = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 48) = 0 (Timeout)
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 0) = 0 (Timeout)
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 0) = 0 (Timeout)
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 0) = 0 (Timeout)
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 99) = 1 ([{fd=14, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 0) = 0 (Timeout)
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 71) = 0 (Timeout)
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 99) = 1 ([{fd=14, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 0) = 0 (Timeout)
poll([{fd=14, events=POLLIN}, {fd=18, events=POLLIN}, {fd=20, events=POLLIN}, {fd=23, events=POLLIN}, {fd=26, events=POLLIN}, {fd=13, events=POLLIN}, {fd=27, events=POLLIN}, {fd=33, events=POLLIN}, {fd=25, events=POLLIN}], 9, 91) = 1 ([{fd=14, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])
poll([{fd=13, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=13, revents=POLLOUT}])
poll([{fd=13, events=POLLIN}], 1, -1)   = 1 ([{fd=13, revents=POLLIN}])

---

### Post by Dedoimedo on 2012-05-01
I will have to ask you to redo that strace thing.
Only while it's running, also run lsof -p <vbox pid>.
I want to see what exactly correspond to file descriptor 14.

Thanks,
Dedoimedo

---

### Post by cocamoxb on 2012-05-01
> **Dedoimedo said:**
> I will have to ask you to redo that strace thing.
Only while it's running, also run lsof -p <vbox pid>.
I want to see what exactly correspond to file descriptor 14.

Thanks,
Dedoimedo


As requested. The lsof file is to large to include, but I believe this is the line you're looking for. Please let me know.



VirtualBo 6773 username   **14u**  0000                0,9           0     5775 anon_inode

---

### Post by Dedoimedo on 2012-05-02
Yup, it is. It seems, perhaps VB is trying to read data that does not exist but is referenced in the system disk structure in wrong locations, which is why you get those anonymous inodes, and probably the timeouts, hence the cpu load. Looks like a conversion process gone wrong. Was the vmdk sparse perhaps before you converted it? Any special things you've done there?

I'd take this to VB forum, just in case.

Regards,
Dedoimedo

---

### Post by cocamoxb on 2012-05-02
> **Dedoimedo said:**
> Yup, it is. It seems, perhaps VB is trying to read data that does not exist but is referenced in the system disk structure in wrong locations, which is why you get those anonymous inodes, and probably the timeouts, hence the cpu load. Looks like a conversion process gone wrong. Was the vmdk sparse perhaps before you converted it? Any special things you've done there?

I'd take this to VB forum, just in case.

Regards,
Dedoimedo



Dedoimedo,

I can't thank you enough for all your help. 

First, I used the IDE Merge tool, then used the VMware converter, then loaded it into VBox with the SCSI controller.

I also have a VDI that I created with a Clonezilla image restore but that just boots to a BSOD. I just got the Win7 ISO that I'm going to try to use the "repair" feature with and see if that works.

I've been trying to get this working for quite some time now so I hope I'll get it working.

---

### Post by cocamoxb on 2012-05-02
> **cocamoxb said:**
> Dedoimedo,

I can't thank you enough for all your help. 

First, I used the IDE Merge tool, then used the VMware converter, then loaded it into VBox with the SCSI controller.

I also have a VDI that I created with a Clonezilla image restore but that just boots to a BSOD. I just got the Win7 ISO that I'm going to try to use the "repair" feature with and see if that works.

I've been trying to get this working for quite some time now so I hope I'll get it working.

I have resolved all my issues by following the instructions in this link:

[http://www.justandrew.net/2009/10/stop-0x0000007b-on-p2vd-windows-7.html](http://www.justandrew.net/2009/10/stop-0x0000007b-on-p2vd-windows-7.html)

and making my Virtualbox controller = IDE with PIIX4 and then matching these settings in the Windows7 Registry:

Aliide = 3
Amdide =3
Atapi = 0
Cmdide = 3
iaStorV = 3
intelide = 0
msahci = 3
pciide = 3
viaide = 3


I can't believe this has been such a struggle! Amazing! Thank you again to both Charles and Dedoimedo!! ):P

---

### Post by CharlesA on 2012-05-02
Wow, that's a hell of a workaround. Glad you got it sorted.

---

### Post by Dedoimedo on 2012-05-02
Good to see you figured it out.
Remember, one strace is worth 45 min of foreplay :)
Dedoimedo

---

