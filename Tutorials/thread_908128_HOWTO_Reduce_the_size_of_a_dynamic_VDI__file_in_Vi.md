---
title: "HOWTO: Reduce the size of a dynamic VDI  file in VirtualBox"
date: 2008-09-02
forum: Tutorials
---

### Post by abcuser on 2008-09-02
**Edit: I have updated how-to for newer version of Ubuntu and VirtualBox.**

Instructions for:
- Sun xVM Virtual Box 2.2.4
- Windows XP SP3 as VM_host
- Ubuntu 9.04 as VM_guest

1. Install zerofree program:
```
sudo apt-get install zerofree
```

2. Reboot Ubuntu.

3. Press <Esc> to enter grub menu.

4. From grub menu select "recovery mode".

5. Select "root" from Recovery Menu.

6. Check to see disk names:
```
df
```

7. From previous command in left corner there are /dev/... devices in my case /dev/sda1. Mount this disk as read only:
```
mount -n -o remount,ro -t ext2 /dev/sda1 /
```

8. Make zeros:
```
zerofree /dev/sda1
```

9. Shutdown Ubuntu:
```
halt
```

10. From Windows host execute:
```
"C:\Program Files\Sun\xVM VirtualBox\VBoxManage" modifyhd vdi_file.vdi compact
```

Regards,
Abcuser

---

### Post by chowette on 2009-04-15
You can just use the zerofree package. ( In ubuntu 8.10 intrepid ibex ) 

Replace instruction 1 to 6 by

```
sudo apt-get install zerofree
```

zerofree - zero free blocks from ext2/3 file-systems

Regards,
Chowette

---

### Post by abcuser on 2009-04-17
chowette, thanks for update for Ubuntu 8.10. By the way this how-to was written for Ubuntu 8.04 and Virtual Box 1.6.4. Beginning VirtualBox 2.1.x and now 2.2.x compacting VDI image is temporally disabled by developers. Sun has also acquired Innotech in the mean time, so default install host (Windows in case of this tutorial) directories have changed.

The work-around for compacting images is to compact VDI file using command:
"C:\Program Files\Sun\xVM VirtualBox\VBoxManage" clonehd original_file.vdi cloned_file.vdi

Then registering cloned vdi in Virtual Media Manager in VirtualBox GUI.

---

### Post by abcuser on 2009-06-01
Hi,
compact functionality is back in Virtualbox version 2.2.4. So I updated how-to to reflect the newest version of Ubuntu and VirtualBox.
Regards

---

### Post by stuartbh on 2009-11-04
Dear ABCUSER,

I tried your mini "How To" and got:

mount: / is busy

Now, it is notable that my root partition is EXT4, I do not have a separate boot partition, nor a separate swap partition, is this an imperative to using zerofree such that it impels the forgoing described dysfunctional state to become occurring?

I am running "9.10" or karma whatever silly name they called it, and its entirely installed on one partition in a VMware style virtual disk.


Thanks,

Stuart

---

### Post by abcuser on 2009-11-05
Hi,
I have the same problem. I have been asking around on VirtualBox forum and the only known working work aroud solution is to use CloneVDI tool.

Read more: [http://forums.virtualbox.org/viewtopic.php?f=6&t=24025](http://forums.virtualbox.org/viewtopic.php?f=6&t=24025)
Hope this helps

---

### Post by stuartbh on 2009-11-05
> **abcuser said:**
> Hi,
I have the same problem. I have been asking around on VirtualBox forum and the only known working work aroud solution is to use CloneVDI tool.

Read more: [http://forums.virtualbox.org/viewtopic.php?f=6&t=24025](http://forums.virtualbox.org/viewtopic.php?f=6&t=24025)
Hope this helps

I certainly appreciate your most expeditious reply, though it seems perfectly apparent that this is a windows tool, it does me no good. I am testing virtual box under MacOS.

Is there a MacOS or Linux based implementation of it?

Similar misbehaviour seemed to be evident when trying Ubuntu under VMware 3.0, as well, even in single user mode the mount command was dysfunctional.


Thanks,

Stuart

---

### Post by abcuser on 2009-11-15
> **stuartbh said:**
> Is there a MacOS or Linux based implementation of it?
It should run under WINE it is pure 32-bit Windows application.

---

### Post by stuartbh on 2009-11-15
> **abcuser said:**
> It should run under WINE it is pure 32-bit Windows application.

Since you seem to have opted out of answering my query directly, I shall presume that you are inferring there is no Linux port of the utility in the instant case. Although, it seems quite common when you ask a question in the forums that people ignore it and answer the question they prefer to answer. I am not saying you did that, I am just saying you never get a direct answer on forums.

I have attempted to use WINE for different things, many times, and my experiences have been it brings the instability of Windows into the Linux environment. No thank you, I pass entirely. Not to mention that WINE has been alpha or beta or whatever for like 10 years, forget it.

Is there any chance that there is a native utility not unlike this utility for Linux?

How difficult would it be to port it?

Are there plans to port it?


Stuart

---

### Post by abcuser on 2009-11-18
> **stuartbh said:**
> Is there any chance that there is a native utility not unlike this utility for Linux?

How difficult would it be to port it?

Are there plans to port it?
CloneVDI utility is only available on Windows. This utility was written by mpack (forums users name) and he did it in his spare time. He is not Sun's employee.

It is probably not hard to port it to Linux, but he wrote on VirtualBox forum, that he doesn't have enough skills and time to do this. But there is source code published if someone is capable of doing.

Back to main topic:
This problem (mounting disk as read only) is new in Ubuntu 9.10 it looks multiple of applications are using disk in such a way that they lock files. So it is impossible to remount disk in read only mode. The work around would be do kill all processes that are locking disk files and then remount. But I don't know what happens if you kill some important process.

So the only work-around ("ugly") solution to run CloneVDI tool inside Linux host is to run [CloneVDI inside WINE](http://forums.virtualbox.org/viewtopic.php?f=7&t=22437). You could also copy VDI file to Windows box (if you have it) and do the cloning and then copy back to Linux host - sorry no other better solution.

---

### Post by abcuser on 2009-11-18
Hi,
I have filed a bug report to VirtualBox: [http://www.virtualbox.org/ticket/5493](http://www.virtualbox.org/ticket/5493)
I think this is more Ubuntu problem then VirtualBox problem, but let see what developers will say.
Regards

---

### Post by hitman9211 on 2009-11-18
Ya I tried out this 
In this work and don't have any problem

---

### Post by abcuser on 2009-11-18
hitman9211,
what is your version of Ubuntu and what is your version of VirtualBox?

---

### Post by Gordon Fern on 2010-02-01
VirtualBox - Compacting Ubuntu 9.10 guest 

There appears to be a bug in Ubuntu 9.10 that is preventing it going into single user.  This is a workaround I used to achieve the compact.

Under the Ubuntu 9.10 guest.

Under user root
```

$ aptitude install zerofree

```
Shutdown the guest
```

$ shutdown -P now

```
As there appears to be a bug in ubuntu 9.10 that means booting up in recovery is not single user.  (On my system apache2, samba and a plethora of other is still running and prevents the ability to mount the root filing system in the read only mode).  So I used the original installation disk (or iso in my case).

Booting up off the disk I chose the &#8220;Rescue a broken system&#8221; option answered all the language / keyboard questions till I reached the &#8220;Device to use as root filing system&#8221; and chose my installation  /dev/ubuntu-vm/root in my case.  Then chose the &#8220;Execute a shell in the installer environment&#8221;


At the # prompt
```

# mount -n -o remount,ro -t ext4 /dev/ubuntu-vm/root
# /target/usr/sbin/zerofree /dev/ubuntu-vm/root
#halt

```

Stop the VM if still running & remove installation disk / iso image

From the host OS locate the vdi & compact

```

vboxmanage modifyvdi "<myhdisk>.vdi" --compact

```

---

### Post by dracolique on 2012-02-17
Update on this.

My guest OS is Ubuntu server 11.10, and the original guide works just fine... just make sure you are actually at the **root prompt in recovery mode** before trying to remount / read only.

My purpose for doing this was to run zerofree so I could shrink my linux VM image.

At the grub prompt, choose the line that includes "Recovery mode"

Then, when prompted, choose "drop to root shell"

My commands were:

```
mount -o remount,ro /dev/sda2 /
```

```
zerofree /dev/sda2
```

worked like a charm.

---

