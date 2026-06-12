---
title: "Input/output error on Sun SPARC E450"
date: 2007-04-28
forum: Sun Sparc Users
---

### Post by rdmapes on 2007-04-28
Good Morning,
I have a SPARC E450 w/ 5 HD's. I did not configure any arrays on the maching. I thought that it may be easier to recover my data if I had the HD's contain my needed partitions.  I am running the machine as a webserver w/ MySQL for a preventative maintenance db. Seems to still function, but these errors inhibit what I can do on the machine. 
Recently while trying to run desc user in MySQL I received the following error:

ERROR 1 (HY000): Can't create/write to file '/tmp/#sql_3038_0.MYI' (Errcode: 30)

I started poking around as some of my shell cmd's starting returning these errors.

-bash: /usr/bin/passwd: Input/output error

So, I think to myself WTFO. I checked the syslog and here is what I found.

Apr 28 09:14:02 clchvtsparc kernel: [1156148.960694]     ASC=0x4 ASCQ=0x2
Apr 28 09:14:02 clchvtsparc kernel: [1156148.960712] end_request: I/O error, dev sda, sector 39305386
Apr 28 09:16:36 clchvtsparc kernel: [1156302.373855] sd 0:0:0:0: Device not ready: <6>: Current: sense key=0x2

I have been searching around the forum and did not seem to find my issue. I will do some more searching here and else where. Is this something fdisk may fix, or a re-boot? I have not seen this before. Any info would be greatly appreciated.
If more information is needed please ask the questions so I can provide what is needed to help me better understand this one.

Thanks,
Ron

---

### Post by erm67 on 2007-04-28
I bet your scsi controller uses the esp driver.
I have the same problems sometimes with my Ultra 2 and the esp driver it appears that the only solution is to use a 2.4.x kernel (not compatible with ubuntu) or hope that the incoming 2.6.22 solves the problem see my previous post.

I don't have my sparc box here but google says that:
```

root@ubuntu:~# echo 1 >> /sys/bus/scsi/devices/0\:0\:0\:0/scsi_disk\:0\:0\:0\:0/allow_restart 

```
could help , the device number should be that of your disks of course.

SCSI errors explained:
[http://en.wikipedia.org/wiki/KCQ](http://en.wikipedia.org/wiki/KCQ)

---

### Post by rdmapes on 2007-04-28
erm67,
OK, I took a look at the code which you posted. From the log it appears to me that your code does not need to be altered. I poked around as well and  I believe sda is 0:0:0:0. Here is the response I get when I use it. 
I logged in remotely with ssh -X root@X.X.X.X

root@clchvtsparc:/sys/bus/scsi/devices# echo 1 >> /sys/bus/scsi/devices/0\:0\:0\:0/scsi_disk\:0\:0\:0\:0/allow_restart

-bash: /sys/bus/scsi/devices/0:0:0:0/scsi_disk:0:0:0:0/allow_restart: Permission denied

After I got this I looked around some more and thought maybe I can restart another disk to test, but decided not to as I do not want more confusion.
Maybe I am not figuring things right so I took a look at dmesg log to confirm and see this.  

[   92.314080] sd 0:0:0:0: Attached scsi disk sda

If I am on track and correct why am I receiving permission denied?

Thanks,
Ron

---

### Post by erm67 on 2007-04-28
> **rdmapes said:**
> erm67,
-bash: /sys/bus/scsi/devices/0:0:0:0/scsi_disk:0:0:0:0/allow_restart: Permission denied
you need to be root to issue such powerful commands to the kernel,  it is not dangerous however. If you were logged in as root than this is strange, root never gets a permission denied.
> sd 0:0:0:0: Device not ready: <6>: Current: sense key=0x2
This error means that the drive is waiting for a restart command, and by default on linux allow_restart is set to 0 i.e. not allow restart of scsi disks, thus your drive will wait forever a restart. Your disk is probably fine.

---

### Post by rdmapes on 2007-04-28
erm67,
Sure enough, I am remote so I used ssh as root to login. I followed the link from your last post to check out the codes. Cool page I bookmarked the page for future reference. 
Do I have to be at the main console in front of the machine to run the cmd? 

I will continue to tinker and see what I can come up with.

Thanks,
Ron

---

### Post by erm67 on 2007-04-28
> **rdmapes said:**
> 
Do I have to be at the main console in front of the machine to run the cmd? 

no, but try that too if you have one :) 
try also:
cat /sys/bus/scsi/devices/0:0:0:0/scsi_disk:0:0:0:0/allow_restart

to see its actual value

Just a curiosity, are you using the esp driver?
dmesg|grep esp

---

### Post by rdmapes on 2007-04-28
erm67,
Here is what I retrieved out of the dmesg log. I don't see the esp driver you mentioned. The other command also did not work the results are below.
[   85.838903] SCSI subsystem initialized
[   85.860389] sym0: <875> rev 0x14 at pci 0005:00:04.0 irq 5,198
[   85.947052] sym0: No NVRAM, ID 7, Fast-20, SE, parity checking
[   85.954475] sym0: SCSI BUS has been reset.
[   85.954506] scsi0 : sym-2.2.3
[   85.955994] sym1: <875> rev 0x14 at pci 0005:00:04.1 irq 5,199
[   86.042865] sym1: No NVRAM, ID 7, Fast-20, SE, parity checking
[   86.050258] sym1: SCSI BUS has been reset.
[   86.050288] scsi1 : sym-2.2.3
[   86.051842] sym2: <875> rev 0x3 at pci 0001:00:02.0 irq 5,7e6
[   86.138497] sym2: No NVRAM, ID 7, Fast-20, SE, parity checking
[   86.145762] sym2: SCSI BUS has been reset.
[   86.145788] scsi2 : sym-2.2.3
[   86.147358] sym3: <875> rev 0x3 at pci 0001:00:03.0 irq 5,7e0
[   86.233964] sym3: No NVRAM, ID 7, Fast-20, SE, parity checking
[   86.241222] sym3: SCSI BUS has been reset.
[   86.241247] scsi3 : sym-2.2.3

Here is what I get back.

root@clchvtsparc:~# cat /sys/bus/scsi/devices/0:0:0:0/scsi_disk:0:0:0:0/allow_restart

cat: /sys/bus/scsi/devices/0:0:0:0/scsi_disk:0:0:0:0/allow_restart: No such file or directory

A strange little world I have got myself into. 

Ron

---

### Post by erm67 on 2007-04-28
sym1 sym2 sym3
symbios driver and controller

at least is not a permission denied :-)

take a look to all the files in the /sys/scsi directory those are not really files but the linux way to communicate with the kernel, reading them you can see the kernel parameters and writing to them you set the parameters.
Just like /etc/system on solaris.

Next week I am gonna test debian with a 2.4.x kernel on my sprac box to see if it is true that 2.4.x works better with old machines.

---

### Post by rdmapes on 2007-04-28
erm67,
I looked for the /sys/scsi, but it is not on the machine.  I did a locate on scsi and found most if the drivers residing in /lib/modules/2.6.17-10-sparc64-smp/kernel/drivers/scsi.
True, it could be worse. At least the machine is still functioning.
Would it be a problem if I re-boot? Everything should come back in theory. No one is using it at this time. In the future I am sure I will need to figure this out.
Let me know your thoughts on the restart?

Ron

---

### Post by rdmapes on 2007-04-29
erm67,
Well, I wondered down to the office as I was not having much luck remotely. Poked around, backed up all my data and did a restart. The server came back clean without fail. What I did do is add 4 hard drives to the machine and loaded mdadm and configured two raid arrays.
I also migrated the MySQL db to one array and will move the backup data & backup scripts to the other when I have it completed. Modified the /etc/mysql/my.cnf to reflect the location. WHAM I am in business, at least for a while anyway.
I am playing with mdadm on an old ALR7200 I have to make sure I am comfortable with the raid stuff. 

Thanks for the feedback and help. Good luck with your code.

Enjoy,
Ron

---

