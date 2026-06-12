---
title: "VMware Server Tips..."
date: 2007-12-21
forum: Virtualisation
---

### Post by jayson.rowe on 2007-12-21
These are just some Random Notes I have collected over the past few months that will help create a nice VMware Server setup.

**Optimize Windows guest operating systems**

Just like a physical machine, your virtual machine can suffer from the same effects of drive fragmentation, so schedule defrag to run at non-critical times to help keep your disk structure organized.

You can always free up resources in windows, and increase security by turning off un-needed, non-critical services. Many of these services will not be needed in a virtual environment:
[LIST]
[*]Alerter
[*]Clip Book
[*]Computer Browser
[*] DHCP Client (Unless using DHCP IP addresses)
[*]Fast User Switching Compatibility (Windows XP)
[*]IMAPI CD-Burning COM Service (Windows XP)
[*]Indexing Service (Unless needed)
[*] Internet Connection Firewall (ICF) / Internet Connection Sharing
[*]IPSEC Services
[*]Messenger
[*]Network DDE
[*]Network DDE DSDM
[*]Network Location Awareness (NLA)
[*]Print Spooler (May be needed in some cases)
[*]Remote Desktop Help Session Manager
[*]Remote Registry (May be needed)
[*]Routing and Remote Access (May be needed)
[*]Smart Card
[*]SSDP Discovery Service
[*]System Restore Service (Windows XP)
[*]Telnet (May be needed)
[*]Themes
[*]Uninterruptible Power Supply
[*]Windows Audio (Windows XP)
[*]Windows Image Acquisition (WIA)
[*]Windows Time (May be needed)
[*]Wireless Zero Configuration
[/LIST]

Make sure to turn off Desktop Wallpaper, Screensavers and any un-needed visual effects in Windows. You will not need shadow effects, font anti-aliasing and be sure to run off Minimize/Maximize animations. You can turn off &#8220;Show window contents while dragging&#8221; as well. All of these will reduce CPU workload while interacting with the Virtual Machine.

If you are running Windows XP, you may want to disable the System Restore feature. Doing so will unlock disk space, CPU and I/O resources. It is also a good idea to disable any power management features as well, as these are usually unneeded in a virtual environment as well.

**Optimize Linux guest operating systems**

Linux guest operating systems are greatly affected by the System clock of the kernel. Linux 2.6 defaults to a 1000Hz clock tick rate, and that will put a strain on the virtual environment, and can cause problems with system time keeping. Linux 2.4 does not have this problem as the clock runs at 100Hz. If running Linux 2.6 based virtual machines, re-compile the kernel to run at 100Hz, or use one of the newer kernels (2.6.22+) which use the No HZ dynamic clock. Centos offers community developed VMware Kernels with the 100Hz option already compiled in. If you are running Ubuntu as a guest, install the "Server" kernel as it is built with the CONFIG_HZ=100 option as default. 

The following kernel boot parameters will help performance and stability using Linux 2.6 as a guest:

```
noapic nolapic apci=off clocksource=acpi_pm elevator=noop
```

APCI/APIC support must be enabled if you plan on using SMP virtualization in the guest, setting the clock to PIT has shown to have better time keeping than other clock sources, your mileage may vary. Setting elevator to noop will enable the host operating system to better schedule I/O as it has an overview of the whole system as opposed to just one virtual machine.

It is very likely that your Linux virtual machines running on VMware Server are servers themselves. Most Linux servers do not require X-Windows. When possible, do not install a graphical desktop -- just use the character-based console. Your Linux virtual machine will require much less resources.

If you do need a graphical desktop, then use a light-weight window manager such as WindowMaker, IceWM, Fluxbox or if you need more features with a little less bloat, XFCE is a great alternative to GNOME.

Just like Windows guests, when optimizing your Linux virtual machines, make sure that you disable or remove unnecessary daemons, services and background tasks.

**VMX Options to improve General Guest OS Performance**

The following options will help get the most performance out of your guest environment:

```
MemTrimRate = &#8220;0&#8243;
sched.mem.pshare.enable = &#8220;FALSE&#8221;
MemAllowAutoScaleDown = &#8220;FALSE&#8221;
```

The above options will disable memory trimming and sharing.

**Optimize Linux host operating systems**

 

As a host OS, Linux CAN have the reverse problem as Linux Guests when it comes down to the Kernel System clock. While Linux 2.6 defaults to 1000Hz, many distributions (notably, Debian, SuSE, and Ubuntu) compile their kernels at 250Hz to offer a balance of throughput and desktop interactivity. 250Hz is considered by some to be too low for a VMware Host OS as it can cause some &#8220;rtc: lost some interrupts&#8221; errors to show up  in your logs. It is recommended to use a Kernel with the 1000Hz option enabled. You can compile your own, or if running Ubuntu 7.04 there is a &#8220;Low Latency Kernel&#8221; in the repositories that works quite well as a VMware host. DO NOT run a &#8220;Real Time&#8221; kernel as this might work well for a Single VM on a Host doing nothing else (which is seldom the case), Multiple VM&#8217;s will suffer.

 

If you are using Linux as the host for VMware Server, you may notice performance issues in relation to I/O, here are some pointers when configuring a VMware server:

 Use a RAID array if at all possible, RAID 1+0 will have the best performance and reliability, set block size to 64K and make Ext3/Ext2 aware of this: set blocksize to 4096 as virtual disks will use large blocks regardless, if you have used 64K strips specify stride as 8 or 16. 

```
mke2fs -b 4096 -R stride=8 <device>
```

If you have a stable power source, consider using ext2 or data=writeback option on ext3 partions, this will have a significant performance increase at the cost of data loss if you lose power.

Make sure to have sufficient memory in the virtual machine as well as the host operating system, if you are using swap your performance on I/O will drop significantly.

On the host operating system, consider using **deadline **I/O scheduler which is enabled by adding this line to the kernel boot parameters:

```
elevator=deadline 
```

The **noop **I/O scheduler is great fo the guest if it is running Linux 2.6; using the **noop **scheduler enables the host operating system to better optimize I/O resource usage between different virtual machines.

This can be added by adding this line to the kernel boot parameters of the guest:

```
elevator=noop
```

Read ahead on the hard drive should be set to an optimal value, this can be changed by executing:

```
 blockdev &#8211;setra <read ahead in bytes> <device>
```

I have found an optimal value is between 16384 and 32768.

The following virtual memory & I/O subsystem tunables (/etc/sysctl.conf) are useful, they help significantly with I/O performance:

```
vm.swappiness = 0
vm.overcommit_memory = 1
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10
vm.dirty_expire_centisecs = 1000
dev.rtc.max-user-freq = 1024
```

Disabling the kernel from over committing memory and only using swap when physical memory has been exhausted helps overall performance (vm.swapiness). The maximum user frequency covers how fast a virtual machine can set it&#8217;s tick count to. The vm.dirty options tune how the VM subsystem commits I/O operations to disk, you may not want to tune these values if you do not have a stable power source.

Although I can't even remember all the sources, Thanks to all the folks who figured this stuff out before I did :-) I found this info all over the web at various times in different articles and/or blogs.

EDIT:
Here are some updates for Hardy:

I have found that NO_HZ (Tickless Kernel) really sucks for VMware, but it is possible to disable it!

Simply edit your /boot/grub/menu.lst, and find:

```
# defoptions=quiet splash
```

and change it too&#8230;

```
# defoptions=quiet splash nohz=off
```

---

### Post by bodhi.zazen on 2007-12-21
Thank you for the tips jayson.rowe

I am going to sticky this.

---

### Post by jayson.rowe on 2007-12-24
> Optimize Linux guest operating systems

Linux guest operating systems are greatly affected by the System clock of the kernel. Linux 2.6 defaults to a 1000Hz clock tick rate, and that will put a strain on the virtual environment, and can cause problems with system time keeping. Linux 2.4 does not have this problem as the clock runs at 100Hz. If running Linux 2.6 based virtual machines, re-compile the kernel to run at 100Hz, or use one of the newer kernels (2.6.22+) which use the No HZ dynamic clock. Centos offers community developed VMware Kernels with the 100Hz option already compiled in.

Just wanted to add that if you are running Ubuntu in a Virtual on VMware-Server you can achieve this by installing the "Server" kernel as it's already compiled with the CONFIG_HZ=100 option.

Will add this to the original post, but wanted to post here to bring it to your attention.

I always keep a "Virtual" of the current Ubuntu running so I can test stuff w/o breaking my main installs, and this does make a difference!

---

### Post by dcstar on 2007-12-28
I found that a vm install of Ubuntu had the clock running way out of whack on my vmware server install, but this fixed it:

[http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html](http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html)

I also found that I had to do this to get USB devices working in the vm installs:

[http://ubuntuforums.org/showthread.php?t=642107](http://ubuntuforums.org/showthread.php?t=642107)

And once I added in things like the Sound devices to each vm, all of that worked too!

I have also found that creating a separate (fast fs) partition for the vm image files can significantly increase performance, for example I have put mine on a Reiserfs partition with the following fstab entry:
```
/dev/hda8   /vmware reiserfs     notail,noatime,nodiratime  0  0
```
This has the small file handling off, and it won't do pointless (and therefore wasteful) directory updates when things are accessed.

---

### Post by yottabit on 2008-01-14
David, great idea to run a "fast" fs for your VM disk images, but I would suggest using XFS instead of Reiser. XFS specializes in huge files, whereas Reiser specializes in small files (even though its large file access time is still quite good). I have also had far less problems with filesystem corruption while using XFS... I have lost 3 server filesystems to Reiser (v3).

J

---

### Post by dcstar on 2008-01-18
> **yottabit said:**
> David, great idea to run a "fast" fs for your VM disk images, but I would suggest using XFS instead of Reiser. XFS specializes in huge files, whereas Reiser specializes in small files (even though its large file access time is still quite good). I have also had far less problems with filesystem corruption while using XFS... I have lost 3 server filesystems to Reiser (v3).


I did a test setting up an XFS partition and copying my VMs to it, I then did startup tests for all my VMs on the XFS partition and compared them to the times using my Resierfs partition and they were all almost identical! (XFS fractionally faster on some).

I don't know if there would be any difference in write-intensive use, but both XFS and Reiserfs perform well on my setup (80 & 160G IDE hard disks, 4G RAM for lots of cache space) - certainly better than FAT32 (really slow) and (IIRC) better then EXT3.

---

### Post by discodan on 2008-03-02
Hi Jason,

Thanks for this great post.  I'm a very recent convert from the Windows server world.

Would you please direct me to the file that has the "kernel boot parameters"?

thank you,

---

### Post by timseal on 2008-03-04
> **discodan said:**
> Hi Jason,

Thanks for this great post.  I'm a very recent convert from the Windows server world.

Would you please direct me to the file that has the "kernel boot parameters"?

thank you,

I'm going to butt in and answer this with ```
/boot/grub/menu.lst
``` - partly because I'm rude, but mostly because it's an easy way to subscribe to this thread :)

-tim

---

### Post by discodan on 2008-03-04
Hey thanks!  That's what I needed!

I also made the mistake of creating my guest OS on a dynamic vmdk split into 2GB chunks.  I was able to convert this to a static vmdk using vmware-vdiskmanager from the terminal.  Then I updated the .vmx to point to the new vmdk.

I just wanted to point this out for any other folks learning about this for the first time.

---

### Post by timseal on 2008-03-04
> I also made the mistake of creating my guest OS on a dynamic vmdk split into 2GB chunks.

Why is that a bad idea?  I would have thought that it would improve performance, if anything.  (not that I'm a vmware expert or anything.)
oh, edit, is it the 2GB chunking that's bad, or the dynamic bit?

-tim

---

### Post by discodan on 2008-03-04
RE: the dynamic .vmdk...  maybe you;re right.  I'm not 100% sure myself.

Essentially, I found a post on the VMware website that mentioned poor performance on Guest Virutal Machines when running on an Ubuntu 7.10 Host.  

I won't go thru the gory details, but basically I found this thread, and another thread on Vmware's forums that described a recipe for improved performance on Ubuntu Vmware Hosts.

The instructions on the Vmware forums recommened changes to the Guest VM settings:

Use a static size vmdk, and set CPUs to 1 even if you have a Dual / Quad Core CPU.

So, last night I implemented a bunch of changes all at once and noticed significant impovement in the responsiveness of the guest OS.  

Here's the list of changes:

On Ubuntu Host:  added elevator=deadline to menu.lst
Converted Vmdk to static Size
Set Guest OS to use 1 CPU

I'm still looking for the vmware thread.  If I find it, I'll update this post with the URL.

Hope this helps,

-disco-

---

### Post by dcstar on 2008-03-05
> **timseal said:**
> Why is that a bad idea?  I would have thought that it would improve performance, if anything.  (not that I'm a vmware expert or anything.)
oh, edit, is it the 2GB chunking that's bad, or the dynamic bit?


Some filesystems have limits on maximum file size (like FAT), so they may require the 2GB sections, but this will (usually) incur extra overheads in operation - and therefore lessen overall performance compared to a single file.

Dynamic will use the disk space more efficiently, but also has additional overhead when it needs to grow compared to a static file - it's a trade off between potentially using disk space unnecessarily versus a slightly slower system that may also need a VMware defrag occasionally to work at its best.

If you have the space use static, if you have a half-decent filesystem use a single file - then your VMware VM should (in theory) perform at its best, but the difference may not be that significant so don't lose any sleep over it....   :grin:

---

### Post by primski on 2008-03-13
Hello,

great tips, each and every one of them.

recently I was having some problems with one of my VM's, it keeps hanging with kernel panic every now and then, didn't manage to debug it yet.

As I was looking for a solution to autoreboot on kernel panic, and for some reasons the 'panic=15' option in grub's menu.1st file, disappeared after a while, and the machine didn't autoreboot. I think some updates messed it up.

Finally i made this nifty little script which i run in cron on host system every 15 minutes. Basically it just pings the vm and if it doesn't respond it restarts it.

if anyone is in need of such script, it can be downloaded [here]("http://www.studentskidom.si/tools/vmrestarter.tar.gz")

---

### Post by Snille on 2008-04-25
Hi Jayson,
I have been using VMW Server 1.0.4 form some time, running on 7.10 server with 3 guests (1 Win server, 1 Ubuntu and 1 FreeBSD).

Now I'm going to reinstall my Host with 8.04 (I don't want to upgrade). I have quad core Intel, and 8 Gb of Ram, so i will be using the 64Bit Ubuntu server of course.

My question is, is it a bad idea to run a RT kernel even when you have multiple cores? Should I instead run the "Low latency" kernel here to? For the moment in 7.10 I'm running the "server" kernel, the reason being that I simply didn't know better. :) My guests are not really working that hard... But I'm going to add a File server to the guests, so it's going to be some more work coming for the Host... 

Of course I have the "Real time clock" problems on all guests... But the "workarounds" has been set in place for this to work ok.

Thank you for your tips, they have been very helpful so far.

---

### Post by dmatrix on 2008-05-05
I am using Ubuntu Vmware Server 8.04 for my host and Ubuntu JeOS 8.04 for my guests.

The notes here suggest using a 1000hz for a Linux host and 100hz for a guest. Ubuntu 8.04 uses a 2.6.24 kernel and the server kernel defaults to 100hz and Jeos virtual kernel defaults to 250hz, but there is also the CONFIG_NO_HZ=y set in each kernel. Are these settings fine on 8.04's 2.6.24 kernel or should they be set to what is noted?

---

### Post by Eil on 2008-05-05
You should also shut off NTP and other timekeeping services on guest OSes since virtualized systems always get their time from the host.

---

### Post by cnd on 2008-07-10
Hopefully this will help someone:  I run Dual Xeon HP Proliant machines (8g RAM) with multiple (from 3 to 12) vm guests.  My host O/S usually encounters memory problems after 3 days or so, and the OOM Killer picks of random vm guests.  My guess is that a kernel bug allocates "free" host ram to disk cache, but doesn't understand how to give it back when needed.

I spent 2 weeks doing extreme testing.  I tested Vmware Server 1.0.1 through 1.0.5, and 2.0.

RedHat AS4 and AS5 both 32bit and 64bit always OOM kill.  AS5 runs vmware 2.0 300% slower than 1.0.5.

Ubuntu 7.10 - would not recognize more than 3.5g of the 10g RAM in my server.  One install also OOM killed (sorry to be vague; my notes+memory are bad - I think it was a 64bit install)

SLES inexplicably doesn't install on Proliants properly.

openSUSE 10.3 (X86-64) - the only distro I have ever found that works without OOM-killing guests (so far - 3 months without a problem running 7 guests).

I stuck mostly to distros that vmware themselves said were "supported" as hosts.  I recall testing a few others as well (forgot names!).

There may well be a kernel setting or host/guest tweak to prevent OOM death.  I didn't find one.  Turining off the OOM killer generally kills the entire host.  I attempted to patch the OOM code source (on RedHat) where I thought the bug was present, but I had no luck.

Hopefully folks with similar problems have been led here by google and some of my bad luck might save you time!

Cheers.

---

### Post by factotum218 on 2008-12-20
A brilliant post that is exactly what I have been looking for.
I'm in the process of possibly switching over completely and permanently with a virtual system for InDesign, Fireworks, and Illustrator. I've been searching for ways to make it as slim as possible without removing any key features that I might need.

Ubuntu may not be my distribution of choice, but once again here we have another great example of one of the finest user communities out there.

Thank you.

---

### Post by discodan on 2008-12-21
Here's a quick status update:

I am have recently finished converting all servers (excluding firewalls) in my office from physical servers to virtual servers.  The system has been up for 4 weeks now and no major issues.  Here are the specs:

2 VMware hosts both running Ubuntu 7.10 64bit with Quad core processors, 8GB RAM, and 3ware Raid 10 arrays.

Host #1:

Guest OS1:  Windows Server 2003:  Roles:  Domain Controller, DHCP, DNS, WINS
Guest OS2:  Windows Server 2003:  Roles:  Application Server
Guest OS3:  Windows Server 2003:  Roles:  File Server
Guest OS4:  Windows XP:  Roles:  Monitors Temp in Server Room
Guest OS5:  Windows XP:  Roles:  Spare PC for the employees who need remote access via RDP

Host #2:

Guest OS1:  Windows Server 2003:  Roles:  Domain Controller, DHCP, DNS, WINS
Guest OS2:  Windows Server 2003:  Roles:  Application Server
Guest OS3:  Windows Server 2003:  Roles:  File Server
Guest OS4:  Windows Server 2003:  Roles:  MySQL
Guest OS5:  Windows Server 2003:  Roles:  SymantecAV Management Console

The biggest obstacle for me was time sync.  This was crucial for the DC to DC and file server to file server synchronization we have setup.

The solution for me was to disable the Intel EIST in the bios on both motherboards.  Then I setup Host#1 as an NTP server pointing to pool.ntp.org.  Then I pointed the ntp client on Host#2 to Host#1, finally, I installed a 3rd party NTP client on each Win32 Guest.  This disabled Microsoft's W32Time service and replaced it with it's own.  I found this to be much more reliable than Microsoft's attempt at NTP.

Here's a link to the website for the NTP client I'm using in case it is helpful.  It's free and appears to be nothing more than a win32 port of ntpd.

[http://www.meinberg.de/english/sw/ntp.htm](http://www.meinberg.de/english/sw/ntp.htm)

On a side note:  I'm still running vmware 1.04.  I'm a bit scared to switch to version 2.0 since everything is running smoothly as is.

If anyone wishes to share their experience with vmware 1 to 2 upgrade.  That would be great.

thanks,

-disco-

---

### Post by dcstar on 2010-02-27
> **discodan said:**
> 
.........
I also made the mistake of creating my guest OS on a dynamic vmdk split into 2GB chunks.  I was able to convert this to a static vmdk using vmware-vdiskmanager from the terminal.  Then I updated the .vmx to point to the new vmdk.


Something to add to a old thread:

I have found that the 2GB chunks are very handy for one reason - backups.

I use the **unison** package to backup my VMs to an external USB drive, and it basically needs free space on the destination equal to the file size it is updating.

With 2GB chunks I only need ~2GB of free space to complete the backup process, with one large VM file I need a lot more free space.

It is also much easier to back up a few 2GB files that may have been changed than one humongous nGB VM file that will always have to be backed up since your VM last changed.....   ;-)

---

### Post by AlexanderDGreat on 2011-06-04
Anyone know how to optimize performance on VMware Player 3.0 running on Ubuntu 10.04 LTS?

---

