---
title: "Loading, please wait..."
date: 2010-02-04
forum: Server Platforms
---

### Post by mntgoat on 2010-02-04
We have some Ubuntu x64 8.04 servers that sometimes get stuck when rebooting.
The only thing we see on the screen is "Loading, please wait" and some stuff below. 
I am attaching a picture of the monitor. 

We have this specific server set to reboot constantly while we try to figure out the issue however we don't know where to start, can we look at logs at this point (probably not since the hard drives aren't mounted yet), can we add debug info? 

Any suggestions would help, other than "why are you rebooting" :-)

Thanks,

--Carlos

---

### Post by Rich78 on 2010-02-04
Can you run dmesg and see what the errors are?

I understand that they boot sometimes?

---

### Post by Demented ZA on 2010-02-04
i agree with Rich78. If that doesn't yeild results, try checking the memory and hard drive. Corruption of either can also cause intermittent problems.

Safest would be to boot an Ubuntu Livecd image, and run disk check from Gparted. You can also run memtestX86 before you boot into the live cd, (after language selection)

---

### Post by ibuclaw on 2010-02-04
dmesg is only useful for the current booted session.

To get messages from a previous bootup, look at the /var/log/messages file.

It should be in date and time format too, for easier cherry picking.

Regards
Iain

---

### Post by mntgoat on 2010-02-04
I haven't checked dmesg but I don't think it will help since we have to reboot to get it to come out of that state.

And yes it does reboot sometimes.

I'll check /var/log but I don't know if anything will be there since almost nothing has started at the point where it freezes.

--Carlos

---

### Post by ibuclaw on 2010-02-04
It's always worth checking, just incase anything *is* written, but making itself too obvious.

Assuming that it is getting stuck in the initrd stage, you could try making a backup, then create a new one.

```

cp /boot/initrd-`uname -r` /boot/initrd.bak
update-initramfs -u -k `uname -r`

```

If you require to debug this stage of the system boot, suggest you look in /usr/share/initramfs-tools

If the errors happen before this stage, it could be a hardware issue. Does any extra messages get outputted when you turn "quiet" off in the kernel boot params?

Regards
Iain

---

### Post by Rich78 on 2010-02-04
There are a lot of topics started with this issue so I'm sure one of them have covered your issue.

I did a quick google for "ubuntu loading please wait" and got quite a bit of info.

It could be anything really, but some people found a reinstall solved the issue.  Others reported issues with 64bit compatibility on their machines...

---

### Post by mntgoat on 2010-02-04
> **ibuclaw said:**
> It's always worth checking, just incase anything *is* written, but making itself too obvious.

Assuming that it is getting stuck in the initrd stage, you could try making a backup, then create a new one.

```

cp /boot/initrd-`uname -r` /boot/initrd.bak
update-initramfs -u -k `uname -r`

```If you require to debug this stage of the system boot, suggest you look in /usr/share/initramfs-tools

If the errors happen before this stage, it could be a hardware issue. Does any extra messages get outputted when you turn "quiet" off in the kernel boot params?

Regards
Iain


Thank you for all those suggestions. We'll start trying them and I'll post results.

--Carlos

---

