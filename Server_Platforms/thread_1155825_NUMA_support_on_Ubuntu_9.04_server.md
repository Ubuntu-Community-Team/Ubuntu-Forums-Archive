---
title: "NUMA support on Ubuntu 9.04 server"
date: 2009-05-11
forum: Server Platforms
---

### Post by khachik_nazaryan on 2009-05-11
Hello everybody

I have an issue with enabling NUMA on Ubuntu 9.04 server.  I found some "useful" links in internet and it doesn't seem that anybody had any experience with NUMA on Ubuntu 9.04.  I have experience with NUMA on Ubuntu 8.10 server (and even <8.10) and there was no problem, so I think 9.04 is not non-numa system.

Please help me to enable NUMA on Ubuntu 9.04 server.  Below you can find the info about my machine.  Let me know if any other info is needed.


# uname -a
Linux my_server 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

# numactl --show
libnuma: Warning: /sys not mounted or no numa system. Assuming one node: No such file or directory
physcpubind: 0 1 2 3 4 5 6 7 
No NUMA support available on this system.

# numactl --hardware
libnuma: Warning: /sys not mounted or no numa system. Assuming one node: No such file or directory
available: 1 nodes (0-0)
libnuma: Warning: /sys not mounted or invalid. Assuming one node: No such file or directory
node 0 cpus:
node 0 size: <not available>
node 0 free: <not available>
libnuma: Warning: Cannot parse distance information in sysfs: No such file or directory
No distance information available.


Thanks in advance,
Khachik

---

### Post by lesar on 2009-06-22
> **khachik_nazaryan said:**
> Hello everybody

I have an issue with enabling NUMA on Ubuntu 9.04 server.  I found some "useful" links in internet and it doesn't seem that anybody had any experience with NUMA on Ubuntu 9.04.  I have experience with NUMA on Ubuntu 8.10 server (and even <8.10) and there was no problem, so I think 9.04 is not non-numa system.

Please help me to enable NUMA on Ubuntu 9.04 server.  Below you can find the info about my machine.  Let me know if any other info is needed.


# uname -a
Linux my_server 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

# numactl --show
libnuma: Warning: /sys not mounted or no numa system. Assuming one node: No such file or directory
physcpubind: 0 1 2 3 4 5 6 7 
No NUMA support available on this system.

# numactl --hardware
libnuma: Warning: /sys not mounted or no numa system. Assuming one node: No such file or directory
available: 1 nodes (0-0)
libnuma: Warning: /sys not mounted or invalid. Assuming one node: No such file or directory
node 0 cpus:
node 0 size: <not available>
node 0 free: <not available>
libnuma: Warning: Cannot parse distance information in sysfs: No such file or directory
No distance information available.


Thanks in advance,
Khachik
I have the same problem too.
soo I have to downgrade to previous version
my system now is:
#uname -a
Linux ubu 2.6.27-14-server #1 SMP Wed Apr 15 20:14:25 UTC 2009 x86_64 GNU/Linux
#numactl --show
policy: default
preferred node: current
physcpubind: 0 1 
cpubind: 0 1 
nodebind: 0 1 
membind: 0 1 
# numactl --hardware
available: 2 nodes (0-1)
node 0 cpus: 0
node 0 size: 2047 MB
node 0 free: 922 MB
node 1 cpus: 1
node 1 size: 2047 MB
node 1 free: 802 MB
node distances:
node   0   1 
  0:  10  20 
  1:  20  10 

all work well.
I have 2 opteron 246 64 bit
4 gb ram
Asus k8n-dl
if I upgrade my sistem, numa stop work.
I write to konow if other have the same problem.
Can anyone help?
best regards

---

### Post by mlang on 2009-07-07
Check and see if its on in the kernel, looks like the desktop version doesnt have numa enabled.  Not sure about server.

grep -i numa /boot/config*
 config-2.6.28-11-generic:# CONFIG_NUMA is not set

(to fix this you have to the options and rebuild the kernel.)

Just as an aside this kills memory performance on opterons(shanghai, istanbul) and intel nehelams

---

### Post by lesar on 2009-07-20
thanks for your support.
now on grep -i numa /boot/config*
I have:
/boot/config-2.6.27-14-generic:CONFIG_NUMA=y
/boot/config-2.6.27-14-generic:CONFIG_K8_NUMA=y
/boot/config-2.6.27-14-generic:CONFIG_X86_64_ACPI_NUMA=y
/boot/config-2.6.27-14-generic:# CONFIG_NUMA_EMU is not set
/boot/config-2.6.27-14-generic:CONFIG_ACPI_NUMA=y
/boot/config-2.6.27-14-server:CONFIG_NUMA=y
/boot/config-2.6.27-14-server:CONFIG_K8_NUMA=y
/boot/config-2.6.27-14-server:CONFIG_X86_64_ACPI_NUMA=y
/boot/config-2.6.27-14-server:# CONFIG_NUMA_EMU is not set
/boot/config-2.6.27-14-server:CONFIG_ACPI_NUMA=y
I'm on Intrepid and numa work.
At this moment I cannot try a new upgrade.
Now I have to do a job. after my job is closed I try a new upgrade and do a new check on grep -i numa /boot/config*
I think will do it on 15/09/2009 (dd/mm/yyyy)
If I found solution to numa problem I will post a new message.
thanks

---

### Post by windependence on 2009-07-20
Not such a bad thing staying at the earlier version. 9.04 is very new and personally, I have not had good luck with it. Most all my server installs are still 8.04. The latest and greatest isn't always the best. In fact, it seems like the desktop distros are becoming just like Windoze, more bloated with each release. It's really a shame in my mind. Linux used to be small and simple. </rant OFF>

-Tim

---

### Post by lesar on 2009-10-26
I try one more time and cannot upgrade to ubuntu 9.04
on type >  grep -i numa /boot/config*
/boot/config-2.6.27-15-server:CONFIG_ACPI_NUMA=y
/boot/config-2.6.27-15-server:CONFIG_K8_NUMA=y
/boot/config-2.6.27-15-server:CONFIG_NUMA=y
/boot/config-2.6.27-15-server:# CONFIG_NUMA_EMU is not set
/boot/config-2.6.27-15-server:CONFIG_X86_64_ACPI_NUMA=y
and every work well (numa too)
if I upgrade then 
my kernel become 2.6.28-16 and numa not work anymore
so I downgrade.
I have try some bios change but this is not the solution
Anyone have a fix to this problem?

---

### Post by lesar on 2009-11-14
I have test a live cd of Ubuntu 9.10 and numa work well. :D
so I try to upgrade ->9.04->9.10
in 9.04 I have make this test for numactl (I write to show the problem in numactl for ubuntu 9.04):
 >numactl --show
  physcpubind: 0 1
No NUMA support available on this system.
 >numactl --hardware
  available: 1 nodes (0-0)
node 0 cpus:
node 0 size: <not available>
node 0 free: <not available>
No distance information available.
 [[...]]("javascript:void(0);")
>grep -i numa /boot/config*
/boot/config-2.6.20-15-generic:CONFIG_NUMA=y
/boot/config-2.6.20-15-generic:CONFIG_K8_NUMA=y
/boot/config-2.6.20-15-generic:CONFIG_X86_64_ACPI_NUMA=y
/boot/config-2.6.20-15-generic:# CONFIG_NUMA_EMU is not set
/boot/config-2.6.20-15-generic:CONFIG_ACPI_NUMA=y
/boot/config-2.6.20-16-generic:CONFIG_NUMA=y
/boot/config-2.6.20-16-generic:CONFIG_K8_NUMA=y
/boot/config-2.6.20-16-generic:CONFIG_X86_64_ACPI_NUMA=y
/boot/config-2.6.20-16-generic:# CONFIG_NUMA_EMU is not set
/boot/config-2.6.20-16-generic:CONFIG_ACPI_NUMA=y
/boot/config-2.6.20-16-server:CONFIG_NUMA=y
/boot/config-2.6.20-16-server:CONFIG_K8_NUMA=y
/boot/config-2.6.20-16-server:CONFIG_X86_64_ACPI_NUMA=y
/boot/config-2.6.20-16-server:# CONFIG_NUMA_EMU is not set
/boot/config-2.6.20-16-server:CONFIG_ACPI_NUMA=y
/boot/config-2.6.22-15-server:CONFIG_ACPI_NUMA=y
/boot/config-2.6.22-15-server:CONFIG_K8_NUMA=y
/boot/config-2.6.22-15-server:CONFIG_NUMA=y
/boot/config-2.6.22-15-server:# CONFIG_NUMA_EMU is not set
/boot/config-2.6.22-15-server:CONFIG_X86_64_ACPI_NUMA=y
/boot/config-2.6.27-15-server:CONFIG_ACPI_NUMA=y
/boot/config-2.6.27-15-server:CONFIG_K8_NUMA=y
/boot/config-2.6.27-15-server:CONFIG_NUMA=y
/boot/config-2.6.27-15-server:# CONFIG_NUMA_EMU is not set
/boot/config-2.6.27-15-server:CONFIG_X86_64_ACPI_NUMA=y
/boot/config-2.6.28-16-generic:# CONFIG_NUMA is not set
/boot/config-2.6.28-16-server:# CONFIG_NUMA is not set

---

### Post by Vegan on 2009-11-14
I think Linux is SMP by default, NUMA is not as efficient with small numbers of processors.

With 2 processors, I would not worry about it.

---

### Post by lesar on 2009-11-17
No it is a problem: DB2 do not start without numa in my serer.
But i have solve the problem:
I have upgrade to 9.04 -> 9.10 and lost my raid1 (mdadm) (someone have enable dmraid on 9.10 and it hide mdadm raid)
so I use clonezzilla to come back in ubuntu 8.10 then i restore my raid using mdadm command and reupgrade 9.04 ->9.10
but this time i do not click restart when finish to upgrade. I do a 
>sudo apt-get remove dmraid 
and in /boot/grub/menu.lst on every kernel row I added nosplash nodmraid so my row is now
kernel        /boot/vmlinuz-2.6.31-14-server root=/dev/md0 ro quiet nosplash nodmraid
This fix my upgrade problem:
>sudo numactl --show
policy: default
preferred node: current
physcpubind: 0 1 
cpubind: 0 1 
nodebind: 0 1 
membind: 0 1 

>sudo numactl --hardware
available: 2 nodes (0-1)
node 0 cpus: 0
node 0 size: 2047 MB
node 0 free: 14 MB
node 1 cpus: 1
node 1 size: 2047 MB
node 1 free: 8 MB
node distances:
node   0   1 
  0:  10  20 
  1:  20  10 
numactl work fine
minor problem:
eclipse ganimede do not work anymore
fix:
create a file like this:
#!/bin/sh
export GDK_NATIVE_WINDOWS=1
/var/www/.../eclipse/eclipse //<- this is the path to your eclipse exe

vpn do not work:
have to reinstall vpnclient-linux-x86_64-4.8.02.0030-k9-AMD64_ONLY_by_t3x with new kernel patch (2.6.31-14-server)

db2 do not start anymore:
so I found in a games web site a package with libstdc++5 but I think thisi is better:
[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)
then
>sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_amd64.deb
db2 work fine :popcorn:

---

