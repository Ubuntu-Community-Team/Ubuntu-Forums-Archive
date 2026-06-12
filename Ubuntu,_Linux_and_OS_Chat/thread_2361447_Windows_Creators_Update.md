---
title: "Windows Creators Update"
date: 2017-05-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Floppyjoe on 2017-05-16
A few days ago I updated a Windows 10 implementation on one of my 32 bit computers. This update created a new partition on this dual boot computer and borked my linux partitions.

I ended up having to run a program from a terminal of a GParted boot-up disk called "parted". This parted program rescued my Linux partitions and afterwards I had to reinstall grub as well.

What gives Microsoft the right to damage a persons computer in such a way? It took me six or so hours of searching and trying fixes to repair the damage.

Someone should sue them for doing stuff like this.

---

### Post by lisati on 2017-05-16
Not a support request.
*Thread moved from **Installation & Updgrades** to **Ubuntu, Linux and OS Chat**.*

---

### Post by Habitual on 2017-05-16
Microsoft Windows assumes it is the only OS on the disk?
Any "foreign" code it deems inappropriate to the functioning of the Windows Operating System gets overwritten.
This operation may be buried in the EULA somewhere.

Sometimes it's good just to vent. :)

---

### Post by QIII on 2017-05-16
> **Floppyjoe said:**
> What gives Microsoft the right to damage a persons computer in such a way?

You do when you install it.

---

### Post by TheFu on 2017-05-16
Back when I dual booted, I would notice that Windows updates about once a year would trash my grub setup. Of course, it never happened at a convenient time - I was always trying to head out to teach a class and needed THAT machine to come with me.  

Once I saw the Windows-update running at shutdown and decided it would be fine to boot up fresh in a new location. That was a terrible idea. Couldn't get my computer working until I had returned home about 6 hrs later.

From that failure, I decided it was best to power down the system 2 hours before I needed to leave, so any corrective action could be taken.  It is much easier now.  Just boot from any live-CD/flash and run **update-grub**.  That should handle it 95% of the time, at least for non-UEFI booting. I don't have any UEFI systems. Been putting that off.

Still, I find it even easier to stop dual booting and run Windows inside a VM.  No risk of it trashing grub or any other booter. Virtualization really is the only safe way to run Windows7. There isn't **any** safe way to run Win8-Win10, IMHO.

---

### Post by LostFarmer on 2017-05-16
On my old desktop due to the boot manager I was using, installing Linux or using a partitioning program would bork my boot manager. Who gave the linux programs the right to change the sector of the logical volume partition tables.  All OS's will sometimes make a change that will require some work to get back a working system.

---

### Post by Floppyjoe on 2017-05-16
> **TheFu said:**
> 

Still, I find it even easier to stop dual booting and run Windows inside a VM.  No risk of it trashing grub or any other booter. Virtualization really is the only safe way to run Windows7. There isn't **any** safe way to run Win8-Win10, IMHO.

Can you run Windows 10 in a virtual machine while still having it registered, or move your registered Windows 10 to a virtual machine?

---

### Post by QIII on 2017-05-16
If you have a retail license and the installation media, you can install it as you wish as long as you do not have it installed at any time on more machines than you have licenses for (typically one).  There is also a limit to the number of times you can move to a different machine, but you can usually call Microsoft so they will let you install it some more:  again, typically only one machine at a time.  A VM counts as a machine.

You cannot move an OEM license to a VM, even if that is on the same physical machine.

---

### Post by Floppyjoe on 2017-05-16
> **QIII said:**
> If you have a retail license and the installation media, you can install it as you wish as long as you do not have it installed at any time on more machines than you have licenses for (typically one).  There is also a limit to the number of times you can move to a different machine, but you can usually call Microsoft so they will let you install it some more:  again, typically only one machine at a time.  A VM counts as a machine.

You cannot move an OEM license to a VM, even if that is on the same physical machine.

My machine had Windows 7 and I upgraded it to Windows 10. So I am assuming since I downloaded the installation media that I could not run a registered version in a VM then?

---

### Post by TheFu on 2017-05-16
> **Floppyjoe said:**
> My machine had Windows 7 and I upgraded it to Windows 10. So I am assuming since I downloaded the installation media that I could not run a registered version in a VM then?

Those are questions for Microsoft. They would be the final word on their licenses.  I was reviewing the EULA this week and very happy I didn't touch Win10 and blocked all Win7 updates that tried to force a new EULA on me.  I'm just lucky that I have ZERO use for Win10 and only limited use for Win7.

---

### Post by sp40140 on 2017-05-18
When I moved to linux, I was doing dual boot. But since I found that I don't need windows much at all. And since I got quad core cpu (c2q), I have  been running windows in VMs. It causes no issues at all.
In today's world you don't need dual boot machines as long as you are running a cpu from last 10 years. You can do very well with vms.

Nobody gives MS right to do this.
They TAKE the right because they can. Honestly, out of how many users of Windows, how many are like you! Not a pleasant thought but that's what counts.

With big (in fact.. any) companies, you make them listen with your wallet.

---

