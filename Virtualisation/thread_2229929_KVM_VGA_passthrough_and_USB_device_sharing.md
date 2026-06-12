---
title: "KVM VGA passthrough and USB device sharing"
date: 2014-06-16
forum: Virtualisation
---

### Post by jwbrase on 2014-06-16
I'm looking at setting up a KVM* virtual machine using a passed through video card for its display. Most mention I've heard of such setups involves having two sets of keyboard, mouse, and monitor, one for the host, and one for the guest. However, I only have one monitor, and while I do have extra keyboards and mice, the keyboard shelf on my desk only really has room for one of each.

The monitor issue is easiest to solve, as my monitor has multiple inputs. Problem solved.

The keyboard and mouse issue is a bit hairier. I have a KVM** switch, and could use it along with USB passthrough, but I'm not sure what happens when both outputs of a KVM** switch are plugged into separate USB ports on the same machine. Does USB passthrough work by port or by device? I rather suspect that the machine will simply see the same keyboard and mouse disconnecting on one USB port and reconnecting on another, and won't be able to have them go to the host when it sees them on one port and to the guest when it sees them on the other. Furthermore, I have another physical machine on the same desk, and would prefer to keep the KVM** switch for multiplexing between the two physical machines, rather than between VMs on one machine.

In cases where virtualization software presents a guest with an emulated display adapter whose output is displayed in a window on the host, there's generally some mechanism whereby clicking in that window redirects mouse and keyboard input to the guest, and then a hotkey returns input focus to the host. Obviously, for VGA passthrough, there's not going to be a window on the host's display adapter to click in, so is there any kind of "Virtual KVM** switch" available for KVM guests with VGA passthrough, whereby a hotkey can switch input focus between the host and guest?

---

### Post by TheFu on 2014-06-16
After re-reading your post a 2nd time, I'm still having trouble understanding "why" you want to do this.  For sharing a PC with multiple people, there are better solutions.  For sharing 1 PC with multiple OSes, there are other/better ways.

The only real reason to have video-card-passthru is where the GPU processing power is needed from a guestOS ... that is usually a requirement for games or a high-end CAD system.  The VGA passthru does NOT require that the other input devices on the VM also be separate from the hostOS.

Do you see my confusion?  Can you please clarify?

USB passthru is by device identifier. It usually works well, but sometimes it doesn't work at all.

Oh - and KVM videocard passthru is highly experimental (i.e. unstable according to the research I'd done).  videocard passthru under Xen is reported to be stable for appropriate hardware - VT-d, BIOS support, chipset support, custom kernel built and specific video card models.

For KVM - [http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM](http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM) explains much.
and [http://www.linux-kvm.org/page/VGA_device_assignment](http://www.linux-kvm.org/page/VGA_device_assignment)

I hope this all makes sense.  I have NOT attempted it, but others on this forum have ...

If/when you get it working, please post back here with details on HW, configs for BIOS, kernel, and OS settings.

---

### Post by jwbrase on 2014-06-16
> **TheFu said:**
> After re-reading your post a 2nd time, I'm still having trouble understanding "why" you want to do this.  For sharing a PC with multiple people, there are better solutions.  For sharing 1 PC with multiple OSes, there are other/better ways.

The only real reason to have video-card-passthru is where the GPU processing power is needed from a guestOS ... that is usually a requirement for games or a high-end CAD system.  

As to why, I have a Radeon (the last one I'll ever buy) whose Linux drivers turned out to be complete crap (I bought it against my better judgment, but had seen good reviews of its stability on Linux). I had to replace it as the main video card on my machine to have a stable system, so now my options are to either put it to use on a Windows machine or sell it. The Windows desktop in our home doesn't have the spare wattage on the power supply to handle the card, and I have a spare Windows 7 license lying around, so I'm going to try to set up a gaming VM. If it works, great, if it doesn't, I'll find a Windows user to sell the card to.

> The VGA passthru does NOT require that the other input devices on the VM also be separate from the hostOS.

That's what I was hoping to hear, but the articles I've been able to find on setting up a VM with VGA passthrough generally assume that one will set it up in a multi-seat configuration. If I'm setting things up single seat, how do I manage switching input focus between the host and the guest?

> 
Oh - and KVM videocard passthru is highly experimental (i.e. unstable according to the research I'd done).  videocard passthru under Xen is reported to be stable for appropriate hardware - VT-d, BIOS support, chipset support, custom kernel built and specific video card models.

I've already had a look at doing it with Xen. Unfortunately, the primary GPU for the machine doesn't like Xen. I didn't even get as far as setting up a guest to try passthrough with. So it's KVM or nothing.

---

### Post by jwbrase on 2014-06-19
> **TheFu said:**
> If/when you get it working, please post back here with details on HW, configs for BIOS, kernel, and OS settings.

I've got it half working: The card gets passed through to the VM and is detected by Windows, but the Catalyst installer crashes and/or hangs consistently when trying to detect the hardware.

---

### Post by bzLem0n on 2014-06-19
I have VGA passthrough working with KVM + virt-manager and have used Xen for it as well in the past. To install the AMD video driver first download the appropriate driver from amd.com.  As I assume you've seen the "Catalyst Control Center" part does not like to install when run in passthrough so what I do is manually install only the video driver.  To do this run the downloaded driver installer to extract the full software bundle (I chose "Desktop/AMD" as the folder) and then once the initial extraction completes, when the "Catalyst Install Manager" window comes up asking you to choose your language cancel the install.  Next open Windows device manager, right click on the video card and select "Update Driver Software", choose "Browse my computer for driver software" and select the folder which for me was "Desktop/AMD/14-4-win7-win8-win8.1-64-dd-ccc-whql/Packages/Driver/Display/WB6A_INF."  I haven't bothered looking in to installing the rest of the Catalyst software as I find no need for it yet video and gaming works fine so far.

Also on this topic in my setup I use a Aten CS692 HDMI KVM so I have one keyboard, mouse, and monitor and I just switch back and forth between gaming on Windows and working on Xubuntu with the push of a button.  I passed through one of the three USB chips on the motherboard entirely to windows to use for keyboard, mouse, and whatever else I choose to plug in.

I intend to write up a guide to using KVM and virt-manager for VGA passthrough in the next few days but in the mean time one bit of advice is to install the gplpv drivers with Xen after installing Windows or install the virtio drivers DURING the Windows on KVM install.

---

### Post by jwbrase on 2014-06-21
> **bzLem0n said:**
> Next open Windows device manager, right click on the video card and select "Update Driver Software", choose "Browse my computer for driver software" and select the folder which for me was "Desktop/AMD/14-4-win7-win8-win8.1-64-dd-ccc-whql/Packages/Driver/Display/WB6A_INF."  I haven't bothered looking in to installing the rest of the Catalyst software as I find no need for it yet video and gaming works fine so far.

No joy. The driver installs fine, but the device doesn't come up on reboot, and device manager reports a code 43.

I used [these]("https://wiki.debian.org/VGAPassthrough") instructions, plus some additions to get the HDMI audio on the card to stop interfering with a bus reset at VM startup (I have to manually futz around with virsh every time I cold boot the VM to get it to launch).

---

### Post by bzLem0n on 2014-06-23
I have an issue with those Debian wiki instructions regarding not having to pass the pci device id to the pci-stub driver at boot.  The method I use is based on the following link [http://blog.ktz.me/?p=403](http://blog.ktz.me/?p=403)  which requires passing the device id to the pci-stub driver at boot and blacklisting the radeon driver.  This means that you can't use the device under the linux host unless you reboot without the devices passed to the pci-stub driver, although you may be able to rmmod the pci-stub driver.

---

### Post by jwbrase on 2014-06-26
> **bzLem0n said:**
> I have an issue with those Debian wiki instructions regarding not having to pass the pci device id to the pci-stub driver at boot.  The method I use is based on the following link [http://blog.ktz.me/?p=403](http://blog.ktz.me/?p=403)  which requires passing the device id to the pci-stub driver at boot and blacklisting the radeon driver.

I'm already blacklisting the radeon driver, as it doesn't play well with the proprietary Nvidia driver running on my other card, and fglrx is not only blacklisted but totally removed. So I don't believe I actually need PCI-stub for the GPU itself (though I do have it set up to use PCI-stub at the moment), as there's no driver for the card that is installed and unblacklisted.

The thing that makes me need PCI-stub is that there's an HDMI audio output on the card, which the Intel HD Audio driver tries to grab (and I can't blacklist the driver because it also operates my motherboard audio). If the audio driver has the HDMI device, it interferes with the VM taking control of the video device.

But even with PCI-stub, there's something weird going on that causes the VM to fail to start unless I tweak things with virsh before cold-starting it.

> This means that you can't use the device under the linux host unless you reboot without the devices passed to the pci-stub driver, although you may be able to rmmod the pci-stub driver.

A big part of the reason I'm trying to use the device under virtualization is because it's not suitable for the host (what with fglrx hanging fairly routinely).

---

### Post by heiko_s on 2014-06-27
I think you mentioned a few issues here.

1. USB passthrough or use under the VM: You can pass through a USB PCI controller to KVM and use a KVM switch, which is what I do. Another alternative that works well for others is Synergy - see [http://synergy-project.org]("http://synergy-project.org"). Make sure that your network bridge is set up properly.

2. I agree that the AMD installer can mess up things. As an alternative to installing the driver manually under Windows, you can also run the installer to unpack the files, then select some manual/user defined installation and ONLY install the driver without the Catalyst software - that should work too.

3. VGA passthrough: You need to bind the graphics card (for the VM) to pciback or pci-stub. Under KVM its probably best to use pci-stub using the initramfs method, this way the graphics card gets bound to pci-stub before the graphics driver or the audio driver loads.

4. The Debian wiki as a source of information is probably outdated. The best source of information on KVM VGA passthrough I found is here: [https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768"). I've wrote the following how-to on Xen VGA passthrough for Linux Mint (Ubuntu) that may also provide some ideas (see step 11 for the initramfs method, though under KVM and pci-stub the commands are a bit different): [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013"). Somewhere on that thread (towards the end) I also posted the KVM configuration.

Good luck!

---

### Post by jwbrase on 2014-06-28
> **heiko_s said:**
> I think you mentioned a few issues here.

1. USB passthrough or use under the VM: You can pass through a USB PCI controller to KVM and use a KVM switch, which is what I do. Another alternative that works well for others is Synergy - see [http://synergy-project.org]("http://synergy-project.org"). Make sure that your network bridge is set up properly.

I'm not entirely keen on passing through USB controllers. Synergy looks like it's directed at a bit of a different use case than mine, but it looks like it still might work for me. But first I have to get the Radeon actually working under virtualization.

> 
2. I agree that the AMD installer can mess up things. As an alternative to installing the driver manually under Windows, you can also run the installer to unpack the files, then select some manual/user defined installation and ONLY install the driver without the Catalyst software - that should work too.

That's basically what I'm doing, and the driver installs fine, but then seems to be unable to actually bring the card up when the VM is rebooted.

> 
3. VGA passthrough: You need to bind the graphics card (for the VM) to pciback or pci-stub. Under KVM its probably best to use pci-stub using the initramfs method, this way the graphics card gets bound to pci-stub before the graphics driver or the audio driver loads.

For the GPU itself, I don't think that's necessary (but I have pci-stub in place anyway) as I have no unblacklisted graphics driver suitable for the card installed on the host. I need and have the cards HD audio device bound to pci-stub, as otherwise a driver I can't blacklist takes control of the audio device. 

> 
4. The Debian wiki as a source of information is probably outdated. The best source of information on KVM VGA passthrough I found is here: [https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768"). I've wrote the following how-to on Xen VGA passthrough for Linux Mint (Ubuntu) that may also provide some ideas (see step 11 for the initramfs method, though under KVM and pci-stub the commands are a bit different): [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013"). Somewhere on that thread (towards the end) I also posted the KVM configuration.

I used the Debian wiki directions as they seem to be written for a setup closest for my own (I don't know, for example, to what degree the Arch forum directions are specific to Arch, whereas Debian forms the base of Ubuntu. Likewise, the Debian directions are directed at KVM rather than Xen, and KVM is what I'm using).

And as far as actually getting the card passed through per-se, everything seems to be working. Windows detects the card, and I can install the drivers if I don't use the Catalyst installer, but the drivers fail to actually operate the card.

---

### Post by heiko_s on 2014-06-29
@jwbrase:

1. Synergy is perfectly suitable for that - in fact it is designed to support this application. Think of your Windows VM and your Linux host as 2 different PCs that happen to run on the same hardware, connected via an Ethernet bridge. As long as the LAN speed (Ethernet bridge) is sufficient - my Xen installation runs at 10 Gigabit/s on the bridge - you won't notice any delay. Many VGA passthrough users use synergy to control their two desktops (host and VM), and you can set it up so that moving the mouse over the right (or left) edge switches to between host and VM.
KVM may have the option to identify USB devices and "pass" them to the guest, but that wouldn't do much good since you want to use only one keyboard and mouse. Anyway, I'm not familiar enough with KVM to provide further instructions on that.

2. Is it the infamous "Error 43" issue under Windows? I've seen that too, and it depends on both the hardware and the KVM (or Xen) version and kernel release. It might be also misconfiguration. To get any further on that, you would need to share your KVM guest configuration and hardware specs such as motherboard, CPU, BIOS release and settings with regard to VT-d /AMD-Vi, and - very important - your GPU model.
Make absolutely certain that VT-d (or AMD-Vi / IOMMU) is enabled in the BIOS, as it typically isn't. Don't confuse with VT-x, that's something different (should also be enabled, however).
One issue with certain AMD graphics cards is that the VM reboot doesn't properly reset them, so when Windows starts it will skip using the AMD graphics card and use the virtual VGA adapter.

3. I've never seen a VGA passthrough where you DON'T bind the graphics card to pciback or pci-stub. I think it's a precondition for KVM (or Xen) to be able to pass the card to the guest. In any case, it won't do any harm to try it. Me and many others have been successful using the initramfs method described in my how-to under step 11 (see link in previous post). You would enter in the /etc/initramfs-tools/modules file something like this:
```
# For the AMD 7770 card:
pci_stub ids=1002:683d,1002:aab0
```

The process of identifying the vendor and model IDs for pci-stub is described in the Archlinux thread.

4. The Debian wiki may or may not work with your hardware and Ubuntu release, things keep changing all the time. VGA passthrough with KVM is rather new, but the developers are very active and thus KVM's progress on that front is quite impressive. Archlinux is one of the most up-to-date Linux distributions around, and many developers as well as advanced users are using it. The OP of the KVM VGA passthrough thread alias nbhs is very knowledgeable with both Xen and KVM, and today you'll find plenty of Ubuntu users posting on that thread to get advise. I personally never even used Archlinux and still find it absolutely relevant for getting my VM run on Ubuntu or Linux Mint. Moreover, notice the posts of "aw" who is one of the developers of KVM. His insight knowledge and replies to my questions have saved me days (or more) of research, if I ever would have found the answer myself.
On a sidenote: Archlinux has the best documentation of any Linux distribution I've seen.

Last not least the Debian wiki uses virt-manager. While I'm sure that some people may find virt-manager useful, I have had only bad experiences with it. I personally don't have the time nor the patience to figure out what virt-manager does or doesn't do behind the scenes, and since its documentation is lacking (to say the least), I have given up on it.

Instead of a fancy GUI I use a little shell script that I can easily and quickly adopt to my needs:
```
#!/bin/bash

configfile=/etc/vfio-pci.cfg

vfiobind() {
	dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
   
}

modprobe vfio-pci

cat $configfile | while read line;do
	echo $line | grep ^# >/dev/null 2>&1 && continue
		vfiobind $line
done

# Startup Windows 7 guest

sudo qemu-system-x86_64 \
-bios /usr/share/qemu/bios.bin -vga none \
-name win7 \
-cpu host \
-smp 6,sockets=1,cores=3,threads=2 \
-enable-kvm \
-m 4G \
-rtc clock=host \
-vga none \
-serial null \
-parallel null \
-monitor none \
-display none \
-k en-us \
-machine type=q35,accel=kvm \
-boot order=cd \
-device ahci,id=ahci \
-device virtio-scsi-pci,id=scsi \
-drive file=/dev/vm/win7amd,cache=none,if=virtio \
-drive file=/home/user/Win7.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-drive file=/home/user/virtio-win-0.1-74.iso,id=virtiocd -device ide-cd,bus=ide.2,drive=virtiocd \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=pcie.0 \
-device vfio-pci,host=00:1a.0,bus=pcie.0 \
-net nic,model=virtio,macaddr=00:16:3e:00:0a:01 -net tap

exit 0

```

I'm passing through my AMD 7770 graphics card which is identified with PCI ID 01:00.0 and 01:00.1 (sound part). The 00:1a.0 is a USB controller for my keyboard and mouse (I use a KVM switch).
-drive file=/home/user/virtio-win-0.1-74.iso,id=virtiocd -device ide-cd,bus=ide.2,drive=virtiocd is the driver CD for the virtio drivers under Windows.

In addition to the startup script above you need to configure the PCI devices to pass through as well as the pci-stub IDs. I also had to add the following to prevent Passmark to BSOD:
```
echo "options kvm ignore_msrs=1" >> /etc/modprobe.d/kvm.conf
```

More on the qemu-system-x86_64 CLI options see [http://qemu.weilnetz.de/qemu-doc.html]("http://qemu.weilnetz.de/qemu-doc.html").

P.S.: Running qemu-system-x86_64 as sudo may not be needed, but I hadn't had the time to setup a special VM user (or make sure everything runs under my regular user account).

Hope it helps.

---

### Post by jwbrase on 2014-06-29
> **heiko_s said:**
> and you can set it up so that moving the mouse over the right (or left) edge switches to between host and VM.

It's late, so I'll just address this one point: This is exactly why I said Synergy *isn't* targeted at my use case. I only have one monitor (with two inputs), so edge switching isn't exactly what I want. However, there's an option to use scroll lock to lock the mouse to one screen, and that plus edge switching should provide more or less what I'm looking for (though I'd rather have something more along the lines of scroll lock or some other hotkey switching input between host and VM directly).

---

### Post by heiko_s on 2014-06-29
> **jwbrase said:**
> It's late, so I'll just address this one point: This is exactly why I said Synergy *isn't* targeted at my use case. I only have one monitor (with two inputs), so edge switching isn't exactly what I want. However, there's an option to use scroll lock to lock the mouse to one screen, and that plus edge switching should provide more or less what I'm looking for (though I'd rather have something more along the lines of scroll lock or some other hotkey switching input between host and VM directly).

I also have only one monitor. Regarding edge-switching, keyboard shortcuts, etc., it's a matter of what you feel comfortable with. I haven't played too much with Synergy but all in all I was impressed. Hope you find something that works for you.

---

### Post by rewt2 on 2014-09-10
Moved my discussion to: [http://ubuntuforums.org/showthread.php?t=2243570&p=13120364#post13120364](http://ubuntuforums.org/showthread.php?t=2243570&p=13120364#post13120364)

---

### Post by bvanlangevelde on 2015-01-12
Question: How do I add a physical disk to the vm using the script mentioned by heiko_s?
I have a hard drive containing all my games and I would like to assign it to one of the vm's.

---

