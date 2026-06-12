---
title: "Sync Virtual Machine over Local Network"
date: 2019-09-21
forum: Virtualisation
---

### Post by MrRubik on 2019-09-21
I'm fairly new to Ubunu. I love it and it's my new daily driver. But I still need Windows for some things, such as Office, which I am handling with VirtualBox. I need to have a Windows 10 VM on my desktop and another on my laptop. I already have a Windows 10 VM set up and configured on my laptop just like I want it. My question is this. Is it possible to somehow use the same virtual machine on both computers? I understand that it would be slow using the VM over the network. But I'm wondering if it's possible to use it on my laptop, and then have it sync the VM's state to my desktop. And then when I use it on my Desktop, it syncs the state to my laptop. This way both desktop and laptop will be using the latest state of my VM. I hope I have explain this okay. Any help is greatly appreciated. Thanks.

---

### Post by TheFu on 2019-09-21
There are many possible answers to this. Some are tied to the hypervisor being used and backend storage technique.  If you are new to Unix, most are beyond your skill, I'm afraid.

Live migration is the technical term for doing what you've described. It requires shared storage.  [https://www.linux-kvm.org/page/Migration](https://www.linux-kvm.org/page/Migration)

And that leaves out the licensing issues that always comes with Windows.

Ceph, sheepdog, DBRB are storage mirroring methods/tools.  Using them on a laptop would be something I'd never do.
[https://docs.ceph.com/docs/mimic/rbd/libvirt/](https://docs.ceph.com/docs/mimic/rbd/libvirt/)
[https://github.com/sheepdog/sheepdog](https://github.com/sheepdog/sheepdog)
[http://www.admin-magazine.com/Articles/Live-Migration](http://www.admin-magazine.com/Articles/Live-Migration)

**rsync** is another option, but it has issues with very large files - anything over 2-4G in size. Isn't Win10 about 60GB these days?  You can always just copy the files back and forth, assuming you use simplistic file-based storage.  The only real trick is to ensure that the VM setups on both systems use exactly the same settings.  Windows is very picky that way. Linux systems care much less.

Have you considered using a remote desktop?  If you use **KVM+libvirt** with **spice** display drivers for the Win10 VM, then you can remotely access it from anywhere internet access is available. On the same LAN, it is very near native performance. Over a WAN, the network bandwidth and VPN overhead will determine what level of performance is possible.  Any remote access to any MS-Windows installation would need a VPN to secure the network connection.  For Linux systems and VMs, there are other, easier-to-use, options.  I usually use **x2go** from the internet into a Linux desktop (running in a VM), then run an LAN-only RDP remote desktop to connect to Windows.  Can't watch video or hear audio, but for typical MS-Office stuff, it works great. If you run Linux desktop versions, like libreoffice, it is faster.

On the same LAN, you can use **ssh -X** to run a program on another Unix machine, but have the display window on your local workstation. This works over a WAN connection, but X11 isn't very bandwidth efficient for WAN use.

I move Linux VMs around with little worry about losing access on the new system. Moved about 20 earlier this year. But whenever I need to relocate a Windows VM, it is much, much, harder.  I've needed to move a Win7 VM from a Linux host to a different Linux host for about 6 months now. I've done it 2 other times.  The last time, I had to do a **sysprep** on Windows before the move would work. That also forced a phone call to MSFT to get the license key enabled.  That VM will be archived in January, likely never to be used again, but I might need it once a year for a few days (taxes).

---

### Post by SeijiSensei on 2019-09-21
If the VirtualBox image resides on a network server, then you could access the image from multiple locations.  From experience, this method can make the VM too slow and unresponsive. (Also, since it's Windows, you could only launch it on one machine at a time to avoid licensing issues.)

You could write a script that uses the [VBoxManage]("https://www.virtualbox.org/manual/ch08.html#vboxmanage-clonevm") command-line tool to [clone]([URL="https://www.virtualbox.org/manual/ch08.html#vboxmanage-clonevm") the VM or use the [Import/Export]("https://www.virtualbox.org/manual/ch01.html#ovf") options. Creating the clone and moving it to the other machine would require some scripting on your part.

By the way, LibreOffice read and writes files in the Microsoft formats like docx and xlsx. Maybe you don't need Windows as much as you think you do.

---

### Post by MrRubik on 2019-09-21
Thank you both for the valuable information. The Fu, you always provide some great answers and I'm appreciative of your help. I am running a special super slim version of Windows 10 in my VM, so my entire Windows installation is 14GB. I do this to increase the performance of my Windows machine under the VM, since I only need the basic features (mainly Office & Rufus and a few others). So does my installation being 14GB change your answer at all? I think 14GB is small enough to copy over my network pretty fast. But due to the apparently complicated nature of what I'm trying to do, I think I may end up just having a separate VM on each machine (laptop and desktop), and then I can use shared folders and cloud storage to zip my files back and forth. Or I may end up doing as Fu suggested and doing all of this over remote desktop. Thank you all for your help.

---

### Post by lammert-nijhof on 2019-09-23
I use Virtualbox and I activated my Windows 7 system on my laptop and copied it afterwards to my desktop. Now I run and update Windows 7 on both laptop and desktop! I have done the same for Windows 10 (Evaluation Copy). I installed and activated Windows XP in early 2011 in a VM and XP has run over time on 3 different desktops (Pentium 4, Phenom II and Ryzen 3) and 2 laptops (Athlon TK55 and i5-2520M). I think Windows, allows you to move an activated VM to another Host Machine, they have too otherwise all server farms, assigning the VMs dynamically to a host machine based on load or after a HW failure, would collapse.

I use rsync to sync the user data between laptop and desktop and for me it works, since I only update a few small files each week, The biggest are Linux ISO files. 

I update my VMs on laptop and desktop independently of each other, since one processor is a 4-core and the other a 2-core. If not I have to adapt each time the number of processors, update the hex network adapter address, the host names and edit the conky file differences. I prefers to run the update.

---

### Post by tasket on 2020-02-28
For a local storage config that can be easily synced (at the block level) with another machine, utilizing an LVM thin pool seems ideal. Setting up an LVM thin pool is pretty easy compared to some of the  alternatives (clustered remote storage with protocol plugins, etc...  painful to setup and ssslow).

When I was writing my LVM [backup]("https://github.com/tasket/wyng-backup") tool, I came across some thin LVM syncing tools like this one: [https://github.com/davidbartonau/lvm-thin-sendrcv](https://github.com/davidbartonau/lvm-thin-sendrcv)

Performance wise, its basically 100% local disk storage, and probably faster than using a VMDK or VDI type of image file. Syncing thin LVM – with a properly thin_lv aware tool – is also very fast since it doesn't even have to look at or compare any data which hasn't changed since the last sync.

---

### Post by CelticWarrior on 2020-02-28
> **lammert-nijhof said:**
> I use Virtualbox and I activated my Windows 7 system on my laptop and copied it afterwards to my desktop. Now I run and update Windows 7 on both laptop and desktop! I have done the same for Windows 10 (Evaluation Copy). I installed and activated Windows XP in early 2011 in a VM and XP has run over time on 3 different desktops (Pentium 4, Phenom II and Ryzen 3) and 2 laptops (Athlon TK55 and i5-2520M). I think Windows, allows you to move an activated VM to another Host Machine, they have too otherwise all server farms, assigning the VMs dynamically to a host machine based on load or after a HW failure, would collapse.

I use rsync to sync the user data between laptop and desktop and for me it works, since I only update a few small files each week, The biggest are Linux ISO files. 

I update my VMs on laptop and desktop independently of each other, since one processor is a 4-core and the other a 2-core. If not I have to adapt each time the number of processors, update the hex network adapter address, the host names and edit the conky file differences. I prefers to run the update.


You're supposed to have Windows licenses for each instance. And you can't obtain new licenses for XP or 7 now.

---

### Post by lammert-nijhof on 2020-03-01
I only have one instance. I changed the setup and only the desktop Windows 10 is updated by Microsoft nowadays. I lost too much time otherwise updating each of the 25 updatable VMs twice. I do an incremental backup with ZFS from desktop to laptop, so I have one bit-identical instance stored on two different locations. On my desktop I also use Raid-1 for other stuff, so I could have stored the same instance on 3 locations. Dependent on the HW I use that instance from the location, that is available, like in any redundant VM-Server setup, that runs desktop VMs. :) :)

Note that ex-lease PCs mostly do come with PRO licences, that allow more flexibility with respect to its usage with virtual machines.

---

