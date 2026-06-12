---
title: "VMware: unable to change virtual machine power state"
date: 2008-06-21
forum: Virtualisation
---

### Post by Blind Tiger on 2008-06-21
After a successful install of VMware server from the partner repos, and a successful install of XP Pro guest OS, I have encountered a problem after updating my linux headers through software auto update.  I cannot power on my XP virtual machine  now.  The error log is:

> Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
End of error message.

I have read a few forum threads involving similar errors that either involve ownership or reloading the vmware kernel module.  I'm not sure which solution is best and therefore do not want to try anything that would potentially compound my problem.  Any ideas?

---

### Post by diablo75 on 2008-06-21
Open a terminal window and type:

```
sudo vmware-config.pl
```

And hit Enter (over and over and over) to select all the default options.  When it gets to the question asking if you want to type in your serial number, type No.  It's not necessary.

That's about it.  I think you have to create some symbolic links as well.  To do this type:

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
```
and then
```
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

Now try it.  Type "vmware" and press enter.  If it works, sweet!  If not, let us know what it says.

---

### Post by Blind Tiger on 2008-06-21
After trying to re-execute the config script, I get the  following:
> ~/vmware/vmware-server-distrib/bin$ sudo ./vmware-config.pl
Making sure services for VMware Server are stopped.

sh: /etc/init.d/vmware: not found
sh: /etc/init.d/vmware: not found
Unable to stop services for VMware Server

Execution aborted.

---

### Post by jmori on 2008-06-28
hey, i was wondering if you managed to solve your problem? my ubuntu kernel just upgraded and now i cant access my virtual machine. :(

---

### Post by Blind Tiger on 2008-06-28
Actually, the situation has deteriorated!  Since I couldn't sort out this error, I tried virtualbox, got 1/3 way through an XP install, and it appeared to hang, so I cancelled the install.  I tried an uninstall of virtualbox, but was not successful due to some conflict with vmware's dependencies.  So I deleted my xp machine, and rebooted, after which point my data partition no longer mounted.  I tried every last bit of tech solutions to try to salvage it, but the drive has unrepairable bad sectors and is now en route to warranty replacement!!

---

### Post by jmori on 2008-06-29
that is terrible. Hopefully i wont have any problems like that, i was going through the forums and i found this topic that kinda gave me some more ideas.

[http://ubuntuforums.org/showthread.php?t=837299](http://ubuntuforums.org/showthread.php?t=837299)

Nothing working yet for me tho. But im hoping for someone that can give me a good solution =S (i'm slightly new to ubuntu and vmware)

---

### Post by AzureCerulean on 2008-08-14
you may want to check the permissions on the VM directories and files...

also try starting vmware as root.

my permissions are set to root:root & 777 


chmod -R 777 ./vmware 
chown -R root:root  ./vmware

./vmware being the directory containing your virtual machine(s)

(though I am not sure that is the best. but it is working now)

---

### Post by Blind Tiger on 2008-08-15
That may have worked!  But ultimately I nuked my drive before having the chance to do anymore troubleshooting.  Yet today I have achieved success.  I received my returned rma'd drive from WD warranty services and did a clean install of Hardy last weekend.  I then installed VMware 1.0.6, created and installed an XP Pro vm, but experienced bridged networking failure.  So I tried using NAT adapter, (vmnet8), which worked for internet connectivity, but my Sonicwall Global VPN couldn't acquire an ip address.

So then I installed Virtualbox 1.6 with XP Pro vm guest and, since Vbox defaults to NAT, I experienced the same vpn issue.  I then spent a big chunk of time tyring to create a manual network bridge for Vbox, but had no success (I think this is due to the fact that although VMware's bridging wasn't working, it still had my eth0 tied into the bridge so it was unavailable for me to use with Vbox).  

In the end, I successfully established a vpn from XP within Vbox to my office workstation using Sonicwall Global VPN.  This was done using the default NAT network setting/adapter in Vbox and Enabling NAT Traversal in the Advanced settings of Sonicwall's GVC web administration page.

Yahooooo!!!

---

### Post by headhunter_unit23 on 2008-09-09
Hmm,

I might be wrong, but it looks like a similar problem I had on gentoo a few days ago.

To have it work I had to recompile my kernel with the following option set:

# Kernel hacking
#
CONFIG_TRACE_IRQFLAGS_SUPPORT=y
# CONFIG_PRINTK_TIME is not set
# CONFIG_ENABLE_WARN_DEPRECATED is not set
# CONFIG_ENABLE_MUST_CHECK is not set
# CONFIG_MAGIC_SYSRQ is not set
**# CONFIG_UNUSED_SYMBOLS is not set**
# CONFIG_DEBUG_FS is not set
# CONFIG_HEADERS_CHECK is not set
# CONFIG_DEBUG_KERNEL is not set
# CONFIG_SLUB_DEBUG_ON is not set
CONFIG_DEBUG_BUGVERBOSE=y
# CONFIG_SAMPLES is not set
CONFIG_EARLY_PRINTK=y
CONFIG_X86_FIND_SMP_CONFIG=y
CONFIG_X86_MPPARSE=y
CONFIG_DOUBLEFAULT=y

May be worth trying for those that have the same issue when trying to power on their vms.

---

