---
title: "vmware on ubuntu 9.04 is driving me to insanity"
date: 2009-05-22
forum: Virtualisation
---

### Post by RealG187 on 2009-05-22
i am running vmware server 2 on ubuntu 9.04 and it is driving me insane. first off as you may notice i am not using any capital letters, that is because vmware stole my modifier keys, when i press shift nothing happens. caps lock doesn't work or nothing but they work in the vm.

second off i cannot connect to a bridged network. i can connect to a host only which has some use, but i need a bridged.

finally the one that pisses me off the most is that when i try to access a folder in the guest it says access denied. and when i make a folder in the guest the host -ubutnu - does the same.

edit- i made the thread on kfn as well
[http://kubuntuforums.net/forums/index.php?topic=3104070.0](http://kubuntuforums.net/forums/index.php?topic=3104070.0)

---

### Post by pytheas22 on 2009-05-22
In my experience VMware server 2 for Linux is a total disaster, for the reasons outlined [here]("http://trickeries.com/347/to-the-makers-of-vmware-20-for-linux-wtf-go-to-hell/").  VMware server 1 was fine, but the latest version does a lot of stupid, stupid things.

Unless you need VMware specifically, I'd give VirtualBox a try.  Just download the .deb file from [the site]("http://www.virtualbox.org/wiki/Downloads") and double-click it to install.  It's much easier to use than VMware server 2, and host networking is very easy to configure (instructions [here]("http://www.ubuntugeek.com/host-interface-networking-made-easy-in-virtualbox-210.html"))--if this isn't the kind of networking you want, please explain in more detail what you need.

If you really want to use VMware, there's a post that might help you fix the [keymapping]("http://blogs.unbolt.net/index.php/brinley/2008/11/12/vmware-server-2-0-breaks-keyboard-mappin-10") problem.

---

### Post by RealG187 on 2009-05-22
i need vmware, all my vms are in vmware format. i did the keymap thing and the keys map fine, in vmware but for some reason it stole my shift, super/winkey, and i think control. alt still works...

---

### Post by pytheas22 on 2009-05-22
Unfortunately I don't have much experience with VMware, so I don't think I can give you any more advice other than to google.  Hopefully someone else will come along.

Also, you can [convert your VMware virtual machines]("https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool") to run in VirtualBox without much work.

---

### Post by RealG187 on 2009-05-23
how long does converting take -question mark-

does it convert the disk images too -question mark-

i used vmware work station once and there was a cool feature where you could drag a file from the desktop on the host to the desktop in the guest -in brackets, or vice versa- and it would transfer it, does virtual box do that -question mark-

---

### Post by RealG187 on 2009-05-23
I converted one of my VMs as a test and it hans on boot

---

### Post by pytheas22 on 2009-05-23
> how long does converting take -question mark-

It depends on the size of the disk image, but it should only be a few minutes.

> does it convert the disk images too -question mark-


Yes.
> 
i used vmware work station once and there was a cool feature where you could drag a file from the desktop on the host to the desktop in the guest -in brackets, or vice versa- and it would transfer it, does virtual box do that -question mark-

I've never heard of this but it might be possible if you install 'Guest Additions' (which are the equivalent of 'VMware Tools').

---

### Post by RealG187 on 2009-05-23
Okay I see something called "Seamless mode" so maybe that's it, but I cannot even get the VM to boot. I don't think it likes the "change in hardware" (virtual hardware)

---

### Post by pytheas22 on 2009-05-23
Seamless mode is just for allow the windows in the guest operating system to be controlled by the window manager of the host, rather than being confined to their little box.

Are your virtual machines all Windows?  If so, you may indeed have issues with Windows not liking the switch in virtual hardware, but I think you can work around this using the 'Hardware Profiles' feature (I think that's what it was called in XP; maybe it's different in Vista and Windows 7).  I'll try to find you a link to this tomorrow.

---

### Post by RealG187 on 2009-05-24
I have one for Windows 98, 2000 Server, and XP Pro.

---

### Post by jpkotta on 2009-05-24
I recently switched to VirtualBox, because the VMWare kernel modules wouldn't compile anymore and other annoyances.  But I had worked around the keyboard problem before the switch.  I ran VMWare in Xephyr, which is an X server that runs as an X client, that way it mucks up the keymap of Xephyr instead of the main X server.

Add this to your ~/.bashrc
```
function daemon
{
    (exec "$@" >&/dev/null &)
}
alias startvmware="daemon Xephyr :11 -screen 1272x993 && DISPLAY=:11 daemon vmware"
```

Then start VMWare with
```
startvmware
```

---

### Post by pytheas22 on 2009-05-24
> I cannot even get the VM to boot

Does the VM start to boot at all and then hang?  If so, at which point does it hang?  Can you boot the VM into Windows safe mode?  Does each of your three VMs behave the same way?

---

### Post by RealG187 on 2009-05-24
On Windows 2000 it hangs after the loading bar that says "Press F8 for advanced startup options", it never gets to this screen
[img]http://procomputerservice.nl/sub/windows/img/bootscreen%2020.png[/img]

Safe mode does not work...

---

### Post by pytheas22 on 2009-05-24
> On Windows 2000 it hangs after the loading bar that says "Press F8 for advanced startup options", it never gets to this screen

Do you have any better luck if you disable ACPI and the network adapter before booting the virtual machine?  Also, I assume you have enough RAM assigned to the VM, but it wouldn't hurt to double check.

---

### Post by RealG187 on 2009-05-25
It has 900 MB ram and I disabled the network card and it still won't start...

---

### Post by pytheas22 on 2009-05-26
hmmm, I'm not sure what's wrong and Google doesn't have any more suggestions.  I don't really have any more ideas other than to rebuild your virtual machines using VirtualBox, or post a new thread and hope to get attention from someone who's more knowledgeable about VMware.

You could also try [converting the VMware machines to run on KVM]("https://help.ubuntu.com/community/KVM/FAQ#How%20to%20convert%20VMware%20machines%20to%20virt-manager?"), but there's no guarantee that would work better than VirtualBox, plus KVM is not as intuitive to use as VMware or VirtualBox (although it's more powerful if you're willing to invest the time to learn it).

---

### Post by RealG187 on 2009-05-26
I think I found the solution to my permissions problem
```
[incoming]
    path = /home/mpg/Desktop/Incoming
    browseable = yes
    read only = no
    guest ok = yes
    force user = mpg
```
For some reason before I removed the last line there, I used the same smb.conf file as before I reinstalled, I put the line back and it works, I haven't tried in VMWare but Virtualbox now can share file between the host without permission issues.

Funny, before I tried putting files on from a real computer and it was fine...

So I think the only issue is the keymap. My Windows 2000 VM is corrupted so I had to reinstall it anyways, so I am reinstalling it on Virtualbox.

---

### Post by RealG187 on 2009-06-07
Okay I have decided to stick with VMWare. Virtualbox opened up more problems which I don't need.

I just need to get a bridged network working again on VMware and stop to SOB from stealing my modifier keys. Once I get VMWare working on 9.04 I will never update again. I had 8.10 and everything was perfect, updating to 9.04 was the biggest mistake of my life!

---

### Post by rocket777 on 2009-06-08
I'm using vmplayer on a vm that I copied from a windows 2k system (win2k as host and as the guest). 

It worked flawlessly. I'm on a newly installed 9.04 host, with all the updates, but both are 32 bit os.

If I recall, server and player can't both exist on the same computer, so one could run server only to create new vms, and then transfer them to the system with player (or just create vm config files by hand or using those websites that create them).

At the least, _I would try to use your vm under player_ to see if that works.

In my case, I even had a running win2k system, with mapped disk devices (e.g. Y: pointing to //machine/share/....) and it came up running, though it did ask a few questions, like did I copy this system. I was quite surprised that this all worked so well.

The only thing I really had trouble with was with windows file shares, which due to my use of all static IPs on a 192.168... type of local lan, required that ubuntu needed for me to put the local host/ip pairs into the /etc/hosts file - I guess because I have no locally running nameserver. But that aside, it worked beautifully under player. I'm using the latest player which I dloaded just last week, 2.5 or some such.

---

### Post by RealG187 on 2009-06-08
Does VMWare player steal your modifier keys? Does sound work?

---

### Post by RealG187 on 2009-06-23
I found that running "setxkbmap" (I made a launcher on my desktop, I think I tried it the first time in the terminal) makes the modifier keys work in the host again. People say this is a temporary fix and is annoying, but it is not as annoying as having to restart!

---

### Post by Diegovr on 2009-06-23
I have updated from linux kernel 2.6.28-11-generic to 2.6.28-13-generic, re run again vmware-config.pl to re configure vmware as normal I do when ubuntu upgrades from a new kernel, and this is generating the following error:

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-13-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.28-13-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config6/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config6/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:49:
/tmp/vmware-config6/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/numa_64.h:5,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/numa.h:4,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/acpi.h:28,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/fixmap_64.h:15,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/fixmap.h:7,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config6/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:49:
/tmp/vmware-config6/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/pda.h:8,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/current.h:19,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config6/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:71:
/tmp/vmware-config6/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config6/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config6/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config6/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config6/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config6/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config6/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config6/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

I tried to look for any fix on google, but looks like still there's not any fix for this new kernel, and vmware doesn't have anything on its site, indeed.

And yes, wmware 1 was great, wmware 2 SUCKS !!!!!

---

### Post by pytheas22 on 2009-06-23
Diegovr: I tried googling for those error messages as well but not much came up.  My advice would be to use an older kernel until this is sorted out better.

---

### Post by bodhi.zazen on 2009-06-23
I am sorry you are having problems with vmware.

As has been advised, consider using an older working kernel, a vmware supported host OS, or an alternate to vmware such as virtualbox or KVM (or OpenVZ).

---

### Post by dcstar on 2009-07-23
> **Diegovr said:**
> I have updated from linux kernel 2.6.28-11-generic to 2.6.28-13-generic, re run again vmware-config.pl to re configure vmware as normal I do when ubuntu upgrades from a new kernel, and this is generating the following error:

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-13-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.
.........
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

I tried to look for any fix on google, but looks like still there's not any fix for this new kernel, and vmware doesn't have anything on its site, indeed.

And yes, wmware 1 was great, wmware 2 SUCKS !!!!!

I believe that this is fixed by the VMWare kernel patch (vmware-update-2.6.27-5.5.7-2) as listed in the big "HOWTO"

---

### Post by RealG187 on 2009-07-23
Which how to?

I have 2.6.28-13-generic last I checked...

---

### Post by BryanPearson on 2009-08-03
Have you tried the following for keyboard issues while using VMware Server?

just add to /etc/vmware/config:
xkeymap.nokeycodeMap = "TRUE"

---

### Post by jocampo on 2009-08-03
I am using VirtualBox now for all my labs and tests; tired of VMware and all the bugs. VirtualBox is easier to use and more stable, in my opinion. Of course, Jaunty has been out for not so long so, as a rule, I never upgrade or move to most recent Operating System so quick... same should apply to Windows. It's better to wait 1 year or so if you are running something critical on your box.

I am currently running a Headless Ubuntu server (no GUI at all) with VirtualBox 2.4 on top; like you, tried to run most recent VirtualBox version and found some issues so I went one version down. My specs: Pentium 2.8Ghz, 3gb RAM and two hard disks, one for Ubuntu and the other one for /home (last one is 7200rpm) Ohh my! ... is fast as lighting. I control everything via command prompt and redirect graphical console via RDP to any of my other laptops.

Give VirtualBox a chance. Version 2.4 runs good on Jaunty, with virtualbox additions of course. Only thing I've not tried yet is simulate Windows clusters, but everything else runs smoothly.

---

### Post by RealG187 on 2009-08-03
> **BryanPearson said:**
> Have you tried the following for keyboard issues while using VMware Server?

just add to /etc/vmware/config:
xkeymap.nokeycodeMap = "TRUE"Yes, that's for a different issue, that's for preseing keys and having the wrong ones processed in the guest. The problem I had was modifer keys not working at all in the host.

---

### Post by RealG187 on 2009-08-03
> **jocampo said:**
> I am using VirtualBox now for all my labs and tests; tired of VMware and all the bugs. VirtualBox is easier to use and more stable, in my opinion. Of course, Jaunty has been out for not so long so, as a rule, I never upgrade or move to most recent Operating System so quick... same should apply to Windows. It's better to wait 1 year or so if you are running something critical on your box.

I am currently running a Headless Ubuntu server (no GUI at all) with VirtualBox 2.4 on top; like you, tried to run most recent VirtualBox version and found some issues so I went one version down. My specs: Pentium 2.8Ghz, 3gb RAM and two hard disks, one for Ubuntu and the other one for /home (last one is 7200rpm) Ohh my! ... is fast as lighting. I control everything via command prompt and redirect graphical console via RDP to any of my other laptops.

Give VirtualBox a chance. Version 2.4 runs good on Jaunty, with virtualbox additions of course. Only thing I've not tried yet is simulate Windows clusters, but everything else runs smoothly.
I want my home folder on a different partition, but I want it to be NTFS so I can access it from my Vista dual boot.

How did you get RDP on Ubuntu? I have been trying for ages...

---

### Post by jpkotta on 2009-08-03
> **RealG187 said:**
> I want my home folder on a different partition, but I want it to be NTFS so I can access it from my Vista dual boot.

How did you get RDP on Ubuntu? I have been trying for ages...

It's in the rdesktop package.  It's the client; I've never heard of an RDP server for Linux.

There are ext2/3 drivers for Windows.  Unfortunately, there are several and I don't know which is the best, nor do I have much experience with them.  Personally, I would try that route before putting my /home on NTFS.

---

### Post by bodhi.zazen on 2009-08-03
> **RealG187 said:**
> I want my home folder on a different partition, but I want it to be NTFS so I can access it from my Vista dual boot.

You can not put your HOME partition on either a FAT or NTFS partition as these partitions do not understand permissions.

So while Linux can RW to these types of permissions, the permissions of critical files withing $HOME are not supported, thus $HOME can not be on FAT or NTFS.

---

### Post by RealG187 on 2009-08-04
> **jpkotta said:**
> It's in the rdesktop package.  It's the client; I've never heard of an RDP server for Linux.

There are ext2/3 drivers for Windows.  Unfortunately, there are several and I don't know which is the best, nor do I have much experience with them.  Personally, I would try that route before putting my /home on NTFS.The EXT drivers don't work.

EXT2IFS asks me to format the partition, defeating the purpose and EXT2FSD causes random Bad Pool Header BSODs, I have to have my files on a partition Windows and Linux understand natively.

---

### Post by bodhi.zazen on 2009-08-05
Use a FAT or NTFS partition, just on the Ubuntu (Linux) side do not mount it as /home

Mount it in /mnt/data , /media/data , or /home/your_user/data

---

### Post by RealG187 on 2009-08-06
> **bodhi.zazen said:**
> Use a FAT or NTFS partition, just on the Ubuntu (Linux) side do not mount it as /home

Mount it in /mnt/data , /media/data , or /home/your_user/dataI would like to have the files in my home folder on the partition, that way I can use the home folder.

I think I know a way that might work.

So if I mount the NTFS partition to /media/data and my home folder is /home/mpg then I would make /home/mpg/Documents a symbolic link to /media/data/Documents, /home/mpg/Desktop to /media/data/Desktop etc.

I would do this for 
Documents
Pictures
Videos
Music
Desktop
and maybe Ubuntu One (I dont think the client likes [symbolic links]("http://ubuntuforums.org/showthread.php?t=1208239") though...)

Anything stored just under /home/mpg would be on the EXT partition so hopefully all the files that need the EXT permissions are there...

---

### Post by bodhi.zazen on 2009-08-06
I think that will work.

---

### Post by dcstar on 2009-08-07
> **RealG187 said:**
> Which how to?

I have 2.6.28-13-generic last I checked...

In the mega-thread at the top of the forum there is a link to this:

[http://ubuntuforums.org/showthread.php?t=966070](http://ubuntuforums.org/showthread.php?t=966070)

You install the patch and things work.

---

### Post by xser on 2009-08-07
Were you ever able to get bridged networking running?  I am not able to at the moment.  (VMware server 2.0.1 on jaunty)  I can only get NAT working.

---

### Post by RealG187 on 2009-08-07
> **xser said:**
> Were you ever able to get bridged networking running?  I am not able to at the moment.  (VMware server 2.0.1 on jaunty)  I can only get NAT working.No, I never got it working (congrats on your first post here, I noticed that).

The main thing that was bugging me was it "stealing" my modifier keys, but that issue has kinda been resolved...

---

### Post by istong on 2009-08-09
> **RealG187 said:**
> I have one for Windows 98, 2000 Server, and XP Pro.
 
I just installed vmware server v2.01 *tar.gz file from vmware directly) on my ubunto 9.04 and it seemed to install fine but when I try to start a VM it gives an error as follows:
 
Failed to initialize monitor device.
Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

 
 
Please let me know how you got it working :)

---

