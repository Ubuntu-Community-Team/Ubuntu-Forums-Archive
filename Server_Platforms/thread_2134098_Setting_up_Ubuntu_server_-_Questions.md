---
title: "Setting up Ubuntu server - Questions"
date: 2013-04-10
forum: Server Platforms
---

### Post by AvengerX9 on 2013-04-10
Hi there,

Okay so I need to set up a new server and I need help with securing it cause last time it got hacked and messed up. Im going with Ubuntu server, but which one should I install. The 12.04.2 LTS or 12.10 ?

This thread will be my step by step installation of a Ubuntu webserver for a newbie and I appreciate all the help I can get.

Thanks for reading and thanks for helping! :)

System:

```

  *-cpu
       description: CPU
       product: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
       vendor: Intel Corp.
       physical id: e
       bus info: cpu@0
       version: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
       slot: CPUSocket
       size: 1600MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
       configuration: cores=4 enabledcores=4 threads=4



             total       used       free     shared    buffers     cached
Mem:          7950       1721       6228          0        110       1215
-/+ buffers/cache:        395       7554
Swap:         8151          0       8151



```

---

### Post by p-dh on 2013-04-10
I would encourage you to install the LTS. You will get 5 years of on-going support - security, applications, etc. As a server, you usually do not need the extras found in the interim releases. Plus, with support for non-LTS going to 9 months (starting with 13.04), you will need to update much more frequently, mainly for features that you won't need.
I just updated 10.04 to 12.04 on my server. So, I'm good until April, 2017 - at which point I'll need to upgrade my hardware and install everything again.

Peace,
Paul :cool:

---

### Post by AvengerX9 on 2013-04-10
Okay thanks! I'll go with the 12.04 then. I will post back in this thread more information on the progress of a webserver installation :)

---

### Post by AvengerX9 on 2013-04-10
Okay, well I made a USB stick and have now choosen languages etc, but I get an error. **Failed to load the preconfiguration file**

> The file needed for preconfiguration could not be retrieved from file:///cdrom/pressed/ubuntu-server-seed. The installation will proceed in non-automated mode.

I click continue and **Installation step failed**

> An installation faile. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Load debconf preconfiguration file

I click continue and it takes me back to the Ubuntu installer mail menu.

So what now? I have hardly started before I get the first error. Please help! :)

Thanks

---

### Post by wickedpuppy on 2013-04-10
May I know how you prepared the usb?

---

### Post by AvengerX9 on 2013-04-10
Thanks! I burned it to a dvd instead and it seems to work better now, but I get a problem with the kernel modules. It says it cannot find the kernel modules and says if I continue without it will probably fail. So how should I solve this one ?

EDIT: Its not better, just different. I cannot install because of the kernels. Even if I continue with or without them the installer just takes me back to the installer main menu.

For a webserver is this version of Ubuntu the best or can I choose the desktop edition ? Whats the difference ?

Thanks

---

### Post by AvengerX9 on 2013-04-10
> **wickedpuppy said:**
> May I know how you prepared the usb?

I prepared the USB by using the LiLi USB creator ([instructions]("https://help.ubuntu.com/community/Installation/FromUSBStick")) and it failed like 4 times so I found another USB creator ([instructions]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")) which also failed so I burned it to a DVD which fails too :)

---

### Post by mastablasta on 2013-04-10
> **AvengerX9 said:**
> Thanks! I burned it to a dvd instead and it seems to work better now, but I get a problem with the kernel modules. It says it cannot find the kernel modules and says if I continue without it will probably fail. So how should I solve this one ?

EDIT: Its not better, just different. I cannot install because of the kernels. Even if I continue with or without them the installer just takes me back to the installer main menu.


You image could be bad. Have you checked the md5sum?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
> 
For a webserver is this version of Ubuntu the best or can I choose the desktop edition ? Whats the difference ?

Desktop has desktop grpahical interface as well as graphical applications. server has more server applicaitons by default. and no graphical environemnt.

> **AvengerX9 said:**
> I prepared the USB by using the LiLi USB creator ([instructions]("https://help.ubuntu.com/community/Installation/FromUSBStick")) and it failed like 4 times so I found another USB creator ([instructions]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")) which also failed so I burned it to a DVD which fails too :)
your downloaded image is probably bad. 


also see this: [http://www.ubuntu.com/download/help/install-ubuntu-server](http://www.ubuntu.com/download/help/install-ubuntu-server)

---

### Post by AvengerX9 on 2013-04-10
Your right. The file was corrupt and downloaded again. Burned to a dvd and installing now. So far so good :) 32% installing core packages

---

### Post by AvengerX9 on 2013-04-10
Is it supposed to take hours ?

---

### Post by sandyd on 2013-04-10
moved to server platforms

---

### Post by AvengerX9 on 2013-04-10
Now its ready, but it has a very slow response in terminal when I write a command such as sudo apt-get install apache2 it came up with a line "building dependency tree 0%" and 5 minutes later it started on 1% and now its been stuck on the line "preconfiguring packages" for another 2-3 minutes.

Took me about 10 minutes to install Apache2!!

Whats going on here ? Please help!! :)

---

### Post by CharlesA on 2013-04-10
If you are at a terminal still, run *top* and see what it says.

---

### Post by AvengerX9 on 2013-04-10
Okay, just waiting now for the webadmin to finish installing. Been doing for the last 30 minutes. Mysql took about an hour! :) On the other computer it was way faster than this.

---

### Post by AvengerX9 on 2013-04-10
Okay, I somehow aborted the installation of webmin for now and I typed top and I get a big list with lots of numbers. The server load says 0.30 - 1.59 - 1.89

---

### Post by sandyd on 2013-04-10
What hardware are you running Ubuntu Server on?

---

### Post by AvengerX9 on 2013-04-10
```


  *-cpu
       description: CPU
       product: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
       vendor: Intel Corp.
       physical id: e
       bus info: cpu@0
       version: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
       slot: CPUSocket
       size: 1600MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
       configuration: cores=4 enabledcores=4 threads=4


```

```

             total       used       free     shared    buffers     cached
Mem:          7950       1721       6228          0        110       1215
-/+ buffers/cache:        395       7554
Swap:         8151          0       8151


```

---

### Post by AvengerX9 on 2013-04-10
It complains about it cannot find a FQDN so its using localhost or 127.0.0.1 instead. Can that be the reason?

When running *top* again I see there are a list of CPU's on the top which are **0%us | 0%sy | 0%ni | 100%id | 0%wa | 0%hi | 0%si | 0%ST**

I can hardly login now on my last attempt. After typing the password it stays for minutes then I get the message "System information disabled due to load higher than 4.0"

---

### Post by CharlesA on 2013-04-10
> **AvengerX9 said:**
> It complains about it cannot find a FQDN so its using localhost or 127.0.0.1 instead. Can that be the reason?

That message is just informational and means you haven't set the ServerName directive in apache. That wouldn't cause the machine to take a long time to install, though.

Is you run this, what does the load averages say?

```
uptime
```

---

### Post by AvengerX9 on 2013-04-10
> **CharlesA said:**
> 

Is you run this, what does the load averages say?

```
uptime
```


The average load is 2.14 | 1.88 | 2.05

---

### Post by CharlesA on 2013-04-10
Check top again and pay attention to the %CPU line and how many tasks are running and how many are sleeping.

---

### Post by AvengerX9 on 2013-04-10
Hi there,

There is 1 running and 97 sleeping and the %CPU line is almost like last time. Almost all are 0.0% except the one in the middle that says **ID** which is around 90-100% and the next one called **WA** jumps up to 25-30% alot.


Found this

> 
2c. CPU States
       The CPU states are shown in the  Summary  Area.  They  are  always
       shown  as  a  percentage  and are for the time between now and the
       last refresh.

        us  --  User CPU time
          The time the CPU has spent running users'  processes  that  are
          not niced.

        sy  --  System CPU time
          The  time  the  CPU  has  spent  running  the  kernel  and  its
          processes.

        ni  --  Nice CPU time
          The time the CPU has spent running users'  proccess  that  have
          been niced.

        wa  --  iowait
          Amount of time the CPU has been waiting for I/O to complete.

        hi  --  Hardware IRQ
          The  amount  of  time  the  CPU  has  been  servicing  hardware
          interrupts.

        si  --  Software Interrupts
          The  amount  of  time  the  CPU  has  been  servicing  software
          interrupts.

        st  --  Steal Time
          The  amount  of  CPU  'stolen' from this virtual machine by the
          hypervisor for other tasks (such  as  running  another  virtual
          machine).


but there is no explanation for the middle stats called ID which is on about 100% all the time

---

### Post by CharlesA on 2013-04-10
id is idle.

What is the load now?

---

### Post by AvengerX9 on 2013-04-10
75% Idle and 25% iowait. Trying to install postfix from webmin. Takes forever :)

2.36 - -2.16 - 1.82

---

### Post by CharlesA on 2013-04-10
> **AvengerX9 said:**
> 75% Idle and 25% iowait. Trying to install postfix from webmin. Takes forever :)

2.36 - -2.16 - 1.82

How the.

Try running this:

```
sudo iostat
```

---

### Post by AvengerX9 on 2013-04-10
I get Iostat command not found - I will try install sysstat

---

### Post by CharlesA on 2013-04-10
> **AvengerX9 said:**
> I get Iostat command not found - I will try install sysstat

That works. Something is definitely bogging the machine down. On a quad core, the load when installing software shouldn't be that high.

---

### Post by AvengerX9 on 2013-04-11
Here are the output from *iostat*

It says 
```

Linux 3.5.0-23-generic (truckstop24) * *04/11/2013 * * *_x86_64_ * * * *(4 CPU)

avg-cpu: *%user * %nice %system %iowait *%steal * %idle
* * * * * *0.07 * *0.02 * *0.02 * 13.31 * *0.00 * 86.58


Device: * * * * * *tps * *kB_read/s * *kB_wrtn/s * *kB_read * *kB_wrtn
sda * * * * * * * 2.41 * * * * 7.23 * * * 331.96 * * 286004 * 13128726
sdb * * * * * * * 0.01 * * * * 0.05 * * * * 0.00 * * * 2082 * * * * *0
sdc * * * * * * * 0.01 * * * * 0.05 * * * * 0.00 * * * 2106 * * * * *0
dm-0 * * * * * * *3.77 * * * * 7.10 * * * 331.97 * * 280617 * 13129232
dm-1 * * * * * * *0.01 * * * * 0.03 * * * * 0.00 * * * 1148 * * * * *0


```

and the *top*

```
top - 13:37:34 up 10:57,  2 users,  load average: 0.74, 0.78, 0.77
Tasks: 106 total,   1 running, 105 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8140992k total,   917240k used,  7223752k free,    83324k buffers
Swap:  8347644k total,        0k used,  8347644k free,   560940k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      20   0 24328 2296 1360 S    0  0.0   0:01.34 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.38 ksoftirqd/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.16 migration/0
    7 root      RT   0     0    0    0 S    0  0.0   0:00.08 watchdog/0
    8 root      RT   0     0    0    0 S    0  0.0   0:00.07 migration/1
   10 root      20   0     0    0    0 S    0  0.0   0:00.21 ksoftirqd/1
   11 root      RT   0     0    0    0 S    0  0.0   0:00.07 watchdog/1
   12 root      RT   0     0    0    0 S    0  0.0   0:00.12 migration/2
   14 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/2
   15 root      RT   0     0    0    0 S    0  0.0   0:00.07 watchdog/2
   16 root      RT   0     0    0    0 S    0  0.0   0:00.07 migration/3
   17 root      20   0     0    0    0 S    0  0.0   0:00.47 kworker/3:0
   18 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/3
   19 root      RT   0     0    0    0 S    0  0.0   0:00.07 watchdog/3
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs
   23 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:1
   25 root      20   0     0    0    0 S    0  0.0   0:00.28 sync_supers
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default
   27 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd
   28 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff
   30 root      20   0     0    0    0 S    0  0.0   0:00.07 khubd
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 md
   34 root      20   0     0    0    0 S    0  0.0   0:00.01 khungtaskd
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0
   36 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd
   37 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark
   39 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto
   49 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld
   51 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
   52 root      20   0     0    0    0 S    0  0.0   0:00.03 scsi_eh_1
   53 root      20   0     0    0    0 S    0  0.0   0:00.09 scsi_eh_2
   54 root      20   0     0    0    0 S    0  0.0   0:00.01 scsi_eh_3
   55 root      20   0     0    0    0 S    0  0.0   0:00.02 scsi_eh_4
   56 root      20   0     0    0    0 S    0  0.0   0:00.01 scsi_eh_5
   60 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:5
   63 root       0 -20     0    0    0 S    0  0.0   0:00.00 binder
   82 root       0 -20     0    0    0 S    0  0.0   0:00.00 deferwq
   83 root      20   0     0    0    0 S    0  0.0   0:00.78 kworker/1:1
   84 root       0 -20     0    0    0 S    0  0.0   0:00.00 charger_manager
   85 root       0 -20     0    0    0 S    0  0.0   0:00.00 devfreq_wq
  149 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/3:1
  177 root      20   0     0    0    0 S    0  0.0   0:00.66 kworker/2:1
  256 root       0 -20     0    0    0 S    0  0.0   0:00.00 kdmflush
  273 root       0 -20     0    0    0 S    0  0.0   0:00.00 kdmflush
  282 root      20   0     0    0    0 S    0  0.0   0:01.06 jbd2/dm-0-8
```

---

### Post by AvengerX9 on 2013-04-11
I wonder if there is a chance that the disk partitioning I did before the install may have caused some of this ?


in that case here is the output of fdisk -l

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  2930277167  1465138583+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021e1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      499711      248832   83  Linux
/dev/sdb2          501758  1953523711   976510977    5  Extended
/dev/sdb5          501760  1953523711   976510976   8e  Linux LVM

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086295

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048      499711      248832   83  Linux
/dev/sdc2          501758  3907028991  1953263617    5  Extended
/dev/sdc5          501760  3907028991  1953263616   8e  Linux LVM

Disk /dev/mapper/truckstop24-root: 991.4 GB, 991449579520 bytes
255 heads, 63 sectors/track, 120536 cylinders, total 1936424960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/truckstop24-root doesn't contain a valid partition table

Disk /dev/mapper/truckstop24-swap_1: 8547 MB, 8547991552 bytes
255 heads, 63 sectors/track, 1039 cylinders, total 16695296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/truckstop24-swap_1 doesn't contain a valid partition table


```

---

### Post by CharlesA on 2013-04-11
Run top while trying to install something and watch the output. It should tell you what is using the CPU.

As far your drives, they look like normal drives, not advanced format drives, so I don't think that is the problem.

---

### Post by AvengerX9 on 2013-04-11
I dont know what to install  :P Any ideas ? Just did *sudo aptitude update && sudo aptitude dist-upgrade* and the aptitude came up with 30% cpu for a second, same with apt-get and dpkg-deb with around 25%

You can see the site in my sig. You will probably notice how slow it just by loading a page or two

---

### Post by AvengerX9 on 2013-04-11
The dist-upgrade is still going on

```

top - 19:22:15 up 16:42,  2 users,  load average: 3.19, 2.24, 1.46
Tasks: 112 total,   1 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.1%sy,  0.0%ni, 73.1%id, 26.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8140992k total,  2821716k used,  5319276k free,   147104k buffers
Swap:  8347644k total,        0k used,  8347644k free,  1665164k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
23827 www-data  20   0  280m  67m 4252 S    1  0.8   0:00.58 apache2
    1 root      20   0 24328 2296 1360 S    0  0.0   0:01.37 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:01.02 ksoftirqd/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.17 migration/0
    7 root      RT   0     0    0    0 S    0  0.0   0:00.12 watchdog/0
    8 root      RT   0     0    0    0 S    0  0.0   0:00.08 migration/1
   10 root      20   0     0    0    0 S    0  0.0   0:00.42 ksoftirqd/1
   11 root      RT   0     0    0    0 S    0  0.0   0:00.10 watchdog/1
   12 root      RT   0     0    0    0 S    0  0.0   0:00.14 migration/2


```

---

### Post by AvengerX9 on 2013-04-11
Just restarted now and its also very slow in starting up and it hangs on for a long time on this part

Begin: Running /scripts/init/bottom ... done
[94.326728] Adding 8347644k swap on /dev/mapper/truckstop24-swap_....

also now after staying on that line for 3-4 minutes or more I get this

[I]The disk drive for /boot is not ready yet or not present
continue to wait, or press S to skip mounting or M for manual recovery

Userspace bootsplash [fail][/I]

---

### Post by CharlesA on 2013-04-11
Huh. How did you do the partitioning? It looks like you have LVM setup judging from the fdisk you posted earlier.

What happens if you hit s to skip? It probably won't boot, though.

---

### Post by AvengerX9 on 2013-04-11
> **CharlesA said:**
> Huh. How did you do the partitioning? It looks like you have LVM setup judging from the fdisk you posted earlier.

What happens if you hit s to skip? It probably won't boot, though.

Honestly when I did the partitioning I had no idea what I was doing! I just wanted fresh disks with no windows so first I was trying to format them all before I went any further


the reboot takes more than forever now and it seems like there is some kind of an interface there? Those flashing ubuntu balls. Do you think I would be better of to just do a re-install ?

---

### Post by AvengerX9 on 2013-04-11
I will do it all over again booting now from my Ubuntu disc. Thing is that allready the first steps in the installation the computer is slow. Yesterday I spent between 3-4 hours just for the installation.

---

### Post by CharlesA on 2013-04-11
> **AvengerX9 said:**
> I will do it all over again booting now from my Ubuntu disc. Thing is that allready the first steps in the installation the computer is slow. Yesterday I spent between 3-4 hours just for the installation.

Wow. There is no way a dual core machine with 8GB of ram should take that long to either boot up or do a fresh install.

Are you sure there aren't any hardware problems?

I would suggest installing the server edition and see if it runs any better.

---

### Post by AvengerX9 on 2013-04-11
Its the server edition I'm running :) I used the desktop on my old computer which was working very good, but I think it was compromised. So I wanted the server edition next time. Just deleted all of my disks and partitions now and made a fresh start.

I just wonder though. when I was in the partition manager in setup there was one disk and the manager wouldn't let me choose whether the partitions should be logical or primary. I was able to choose that on 2 out 3 disks.:confused:

---

### Post by AvengerX9 on 2013-04-11
Just got an error again. *"Unable to install GRUB in /dev/sda Executing 'grub-install /dev/sda' failed. This is a fatal error."* Why does that happen ?

---

### Post by AvengerX9 on 2013-04-11
Now I have tried installing with the partition stuff both manually and with the LVM things and it seems to go faster during the rest of the installation when I choose to setup manually. Do I need the LVM stuff?

---

### Post by CharlesA on 2013-04-11
> **AvengerX9 said:**
> Now I have tried installing with the partition stuff both manually and with the LVM things and it seems to go faster during the rest of the installation when I choose to setup manually. Do I need the LVM stuff?

Personal choice imo. If you aren't adding drives often you can do fine without LVM. I don't use it on my server because it added more complexity for me.

---

### Post by AvengerX9 on 2013-04-11
Well I think I found out whats wrong. One of the three disks are f....  cause everytime that disk in involved somehow everything slows down so I have now left it unformatted and see if it improves. If I can complete the installation now then I'll remove it.

---

### Post by AvengerX9 on 2013-04-11
Just got through the installation like 20X faster than last time I completed it. And booted and ready to login in less than a minute compared to last time with up to 10minutes :) Yeahh! So far so good!

---

### Post by CharlesA on 2013-04-11
Sounds like a plan. Was the drive just dead or was it having issues with reads/writes?

---

### Post by AvengerX9 on 2013-04-11
I don't really know that yet. Probably read/write problems cause thats the disk I used yesterday when I was experiencing the problems with everything going slow. After lots of failure installations I figured out that one drive was causing it because the installation went fast at those times I didnt include it. I think its working, but not here. I might use it on a windows computer or something :P

Thanks for the help by the way. I will sure need help again cause I'm still a newbie with linux :)

---

