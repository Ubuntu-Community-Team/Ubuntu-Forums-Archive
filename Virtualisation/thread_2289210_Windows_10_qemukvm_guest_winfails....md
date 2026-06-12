---
title: "Windows 10 qemu/kvm guest win/fails..."
date: 2015-08-02
forum: Virtualisation
---

### Post by KillerKelvUK on 2015-08-02
Starting a thread on the successes or otherwise with Windows 10 qemu/kvm guests, please share your results/recommendations....

I current run Windows 7 Ultimate in a qemu/kvm guest using legacy Seabios...this is primarily my corp desktop.  I qualified for the free upgrade to Windows 10 so I've been playing around with various solutions pre and post official release.

[B]Windows 10 Pre-Release (Insider Previews / Technical Previews)

[/B]
[LIST]
[*]Very early Tech Prev seemed to work fine using the available virtio drivers from redhat.
[*]However the later Insider Preview releases caused me some headaches
[LIST]
[*]Various forum searches showed others having similar issues with solutions ranging from setting CPU types to 'kvm64' to using 'Virtio SCSI' controllers.
[*]I personally had success after changing disk controllers ([https://me.m01.eu/blog/2015/03/windows-10-kvm-and-iscsi/](https://me.m01.eu/blog/2015/03/windows-10-kvm-and-iscsi/))
[/LIST]
[/LIST]

[B]Windows 10 Official-Release (clean installation from .iso file)
[/B]

[LIST]
[*]Used the media creation tool MS released to download the installation media (.iso)
[*]Used the latest OVMF build from here [https://www.kraxel.org/repos/jenkins/edk2/](https://www.kraxel.org/repos/jenkins/edk2/)
[*]Configured the guest to copy my host CPU specs and set the topology for 1x socket, 2x cores, 2x threads.  (lshw: Intel(R) Core(TM) i7-4790S CPU @ 3.20GHz)
[*]Used the IDE bus for the windows .iso installation media and the virtio drivers (grabbed the latest from [https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download))
[LIST]
[*]NOTE: I used the win8.1 amd64 virtio drivers, no complaints or issues noticed thus far
[/LIST]

[*]This pretty much gives me a functional Windows 10 qemu/kvm guest which seems as per-formant as my Windows 7 legacy.
[/LIST]

The problem is you can't just activate the Windows 10 clean installation using the Windows 7 Product Key...Microsoft want you to upgrade your earlier version to qualify for the free Windows 10 copy (see [http://www.howtogeek.com/224342/how-to-clean-install-windows-10/](http://www.howtogeek.com/224342/how-to-clean-install-windows-10/))

[B]Windows 10 Official-Release (upgrade from Windows 7)
[/B]

[LIST]
[*]Firstly, the Windows 10 upgrade tool in the taskbar of my Windows 7 guest said my hardware wasn't compatible because of the 'Redhat Display Adapter'
[LIST]
[*]You have to force the issue here by using the media creation tool and creating either an .iso (as per above) or a USB installer, either is fine just execute the setup program from the media to bypass the upgrade tool
[/LIST]

[*]So this is where I start getting issues
[/LIST]
[INDENT][COLOR=#ff0000]EDIT (2nd Aug @ 19:43)[/COLOR][/INDENT]

[LIST]
[*=1]So I attempted a clean install of Windows 7 first, turns out that Win7 boot is buggy when using OVMF as it consistently powers off shortly after the windows boot logo appears.  I can't find the trigger for the bug but by altering the CPU config for the guest you can get a successful boot i.e. switch the processor type after each failed boot...however rebooting after a successful boot seems to causes the issue again...I just keep switching guest processor settings to workaround this.
[*=1]Anyways for this test I persisted, completed the install and got to Win7 desktop...applied the virtio drivers etc but didn't do any windows updates.
[*=1]I used the .iso install media I created from the prior tests and ran the executable
[*=1]The installer does its stuff, completes its first pass to 100% (copying files I think)...then it reboots...
[*=1]The (re)boot up looks like windows 10 but then I get a black screen and all activity ceases i.e. no io, cpu cycles etc.
[*=1]I force a restart which (re)boots into Windows 7 and the Windows 10 Upgrade dialogue appears saying "The installation failed in the SAFE_OS phase with an error during BOOT operation."
[/LIST]
[INDENT]
[COLOR=#ff0000]EDIT (3rd Aug @ 20:18)[/COLOR][/INDENT]

[LIST]
[*=1]Okay so now I'm completely battered...
[*=1]I've tried pretty much every variation/combination of OVMF, SeaBIOS, Q35, i440FX, no virtio drivers, virtio drivers...the same error message presents mid Windows 10 installation which points back to a driver issue.
[*=1]I have a Macbook Pro which I run Parallels on for a Win desktop too, I'd previously upgrade my Windows 8.1 installation to Windows 10 without issue so I moved my Windows 7 vm onto that and upgraded it...without issue.
[*=1]*Work around* found
[*=1]To be fare the setuperr.log on the Windows 10 install contained a lot of detail that I'm sure the right forum could have appraised but I haven't explored that and likely wont.
[*=1]SIDE NOTE:  In all my testing with Win7 i could never get Windows Update to work...just kept checking for updates.  This was a new problem which I never experienced when using Win7 for my daily tasks, I'm speculating here but I think that MS must check as part of the Windows Update process whether the Product Key as been through an update to Windows 10 previous or not.  The reason being is that to test the whole process prior to using kvm/qemu I revived an old physical machine I had spare, put a clean Windows 7 on it, activated and then upgraded it.
[/LIST]

CONCLUSION:  For me I'm writing off an upgrade of Windows 7 using kvm/qemu.  I've successfully done this using Parallels on my Mac so will move this installation on their, which means I can move my Windows 8.1 installation off my Mac and onto kvm/qemu...which will be my next test.
[INDENT]
[COLOR=#ff0000]EDIT (8th Aug @ 16:44)[/COLOR][/INDENT]

[LIST]
[*=1]Maybe someone could try the solution okky found for Windows 8.1 below for upgrading their Windows 7 guest, please post back results if you do.
[/LIST]

[B]Windows 10 Official-Release (upgrade from Windows 8.1)

[/B][INDENT][COLOR=#ff0000]EDIT (8th Aug @ 16:31)[/COLOR][/INDENT]

[LIST]
[*=1]So a kind forum member (okky-htf) posted their solution for upgrading Windows 8.1 to Windows 10 and its worked for me.  See post #2 in this thread for the full details ([http://ubuntuforums.org/showthread.php?t=2289210&p=13334367#post13334367](http://ubuntuforums.org/showthread.php?t=2289210&p=13334367#post13334367))
[*=1]Summary is to change the CPU type to (core2duo), add a feature flag (nx) and to hide KVM from the guest, then complete the upgrade...once finished you can revert the changes.
[LIST]
[*=1]QEMU:  -cpu core2duo,+nx,kvm=off
[*=1]Libvirt:
[/LIST]
[/LIST]
[INDENT=5]```

<features>
  <acpi/>
  <kvm>
    <hidden state='on'/>
  </kvm>
</features>
<cpu mode='custom' match='exact'>
  <model fallback='allow'>core2duo</model>
  <feature policy='require' name='nx'/>
</cpu>

```[/INDENT]

[LIST]
[*=1]Its possible the 'kvm=off' is superfluous as I'd guess okky is using this as he has an Nvidia VGA passthrough solution.  If someone else attempts without this please post a reply with the results.
[/LIST]

CONCLUSION:  So the forum has done it again, proves the power of community if you ask me.

---

### Post by okky-htf on 2015-08-07
Hi, KillerKelvUK!

Just want to share my experience which I think we have similarities. I know it sounds silly, but try changing the CPU model to "core2duo,+nx,kvm=off" just before executing the update. Yes, you read that right, "core2duo" My Windows 8.1 always crashed when trying to update to Windows 10, something saying about thread not safe. After I changed the CPU model to "core2duo,+nx,kvm=off" the update went smoothly. After I successfully updated to Windows 10, I changed back the CPU model to "host,kvm=off" and it never crashes again when booting.

For the sake of completeness, here's my QEMU script.

```

#!/bin/bash


# QEMU name and PID
OPTS="-name windows-10-pro"
OPTS="$OPTS -pidfile /tmp/windows-10-pro.pid"


# Processor
OPTS="$OPTS -cpu host,kvm=off"
OPTS="$OPTS -smp 8,sockets=1,cores=4,threads=2"
OPTS="$OPTS -enable-kvm"


# Machine
OPTS="$OPTS -machine type=pc-i440fx-2.1,accel=kvm"
#OPTS="$OPTS -machine type=q35,accel=kvm"


# The following setting enables S3 (suspend to RAM). OVMF supports S3
# suspend/resume. Disable when using Q35
OPTS="$OPTS -global PIIX4_PM.disable_s3=0"


# Memory
OPTS="$OPTS -m 16G"
OPTS="$OPTS -mem-path /dev/hugepages"
OPTS="$OPTS -mem-prealloc"
OPTS="$OPTS -balloon none"


# Hardware clock
OPTS="$OPTS -rtc clock=host,base=utc"


# Sound hardware
QEMU_PA_SAMPLES=128
export QEMU_AUDIO_DRV=pa
OPTS="$OPTS -soundhw hda"


# Graphic card passthrough (Gigabyte GeForce GTX 980 G1 Gaming)
OPTS="$OPTS -device vfio-pci,host=01:00.0,multifunction=on"
OPTS="$OPTS -device vfio-pci,host=01:00.1"


# USB 3.0 passthrough (NEC/Renesas)
OPTS="$OPTS -device vfio-pci,host=03:00.0"


# USB 2.0 passthrough (NEC)
OPTS="$OPTS -device vfio-pci,host=0a:01.0"


# Keyboard layout
OPTS="$OPTS -k en-us"


# Boot priority
OPTS="$OPTS -boot order=c"


# OVMF
OPTS="$OPTS -drive if=pflash,format=raw,readonly,file=/data/machines/windows-10-pro/ovmf/OVMF_CODE-pure-efi.fd"
OPTS="$OPTS -drive if=pflash,format=raw,file=/data/machines/windows-10-pro/ovmf/OVMF_VARS-pure-efi.fd"


# System drive
OPTS="$OPTS -drive id=disk0,if=none,cache=unsafe,format=raw,file=/data/machines/windows-10-pro/disks/disk0-system.img"
OPTS="$OPTS -device driver=virtio-scsi-pci,id=scsi0"
OPTS="$OPTS -device scsi-hd,drive=disk0"


# 1st Game drive
OPTS="$OPTS -drive id=disk1,if=none,cache=none,aio=native,format=raw,file=/dev/disk/by-id/ata-Hitachi_HDS721050CLA660_JP1570FR1ZWP7K"
OPTS="$OPTS -device driver=virtio-scsi-pci,id=scsi1"
OPTS="$OPTS -device scsi-hd,drive=disk1"


# 2nd Game drive
OPTS="$OPTS -drive id=disk2,if=none,cache=none,aio=native,format=raw,file=/dev/disk/by-id/ata-Hitachi_HDS5C3020ALA632_ML0220F30NX2DD"
OPTS="$OPTS -device driver=virtio-scsi-pci,id=scsi2"
OPTS="$OPTS -device scsi-hd,drive=disk2"


# Windows 10 Pro installer
OPTS="$OPTS -drive id=cd0,if=none,format=raw,readonly,file=/data/iso/OS/Windows10Pro/Windows_10_Professional_64_Bit.iso"
OPTS="$OPTS -device driver=ide-cd,bus=ide.0,drive=cd0"


# Virtio driver
OPTS="$OPTS -drive id=virtiocd,if=none,format=raw,file=/data/iso/VirtIO/virtio-win-0.1.105.iso"
OPTS="$OPTS -device driver=ide-cd,bus=ide.1,drive=virtiocd"


# OVMF emits a number of info / debug messages to the QEMU debug console, at
# ioport 0x402. We configure qemu so that the debug console is indeed
# available at that ioport. We redirect the host side of the debug console to
# a file.
#OPTS="$OPTS -global isa-debugcon.iobase=0x402 -debugcon file:/tmp/windows_10_pro.ovmf.log"


# QEMU accepts various commands and queries from the user on the monitor
# interface. Connect the monitor with the qemu process's standard input and
# output.
OPTS="$OPTS -monitor stdio"


# A USB tablet device in the guest allows for accurate pointer tracking
# between the host and the guest.
OPTS="$OPTS -device piix3-usb-uhci -device usb-tablet"


# Network
OPTS="$OPTS -netdev tap,vhost=on,ifname=$VM,script=/usr/local/bin/vm_ifup_brlan,id=brlan"
OPTS="$OPTS -device virtio-net-pci,mac=52:54:00:xx:xx:xx,netdev=brlan"


# Disable display
#OPTS="$OPTS -vga qxl"
OPTS="$OPTS -vga none"
OPTS="$OPTS -serial null"
OPTS="$OPTS -parallel null"
#OPTS="$OPTS -monitor none"
OPTS="$OPTS -display none"
#OPTS="$OPTS -daemonize"


# QEMU Guest Agent
OPTS="$OPTS -chardev socket,path=/tmp/qga.sock,server,nowait,id=qga0"
OPTS="$OPTS -device virtio-serial"
OPTS="$OPTS -device virtserialport,chardev=qga0,name=org.qemu.guest_agent.0"


sudo taskset -c 0-7 qemu-system-x86_64 $OPTS

```

For the record, my distro is Arch Linux. Good luck!

---

### Post by KillerKelvUK on 2015-08-08
Hi okky, thanks for the share...have made the changes to my 8.1 guest and attempting this now...fingers crossed \\:D/

---

### Post by KillerKelvUK on 2015-08-08
Hey hey hey...okky rocks, it worked first time after making the changes.  Thank you kind person!

---

### Post by okky-htf on 2015-08-10
Hi, glad it worked for you too!
I think I still save the Windows 8.1 image before the upgrade, let me try it with just "core2duo" tonight. 
Just as you have suspected, the "kvm=off" flag is a workaround for my NVIDIA GPU, I need it so I can passthrough it without NVIDIA driver block it.
As for the "+nx" flag, it was there after a lot of googling trying to work out the crash, probably not needed also.

---

### Post by chaseadam on 2015-08-13
Has anyone had success with the QEMU guest agent in win 10?

---

### Post by Athanassios_Bakali on 2015-08-14
hello everyone, I managed to update my 8.1 VM to Windows 10, by just setting the CPU type to core2duo and the CPU count to 2.

After the update was over I was able to restore the number of CPU's to 8. I also tried to change the CPU type to Haskel, Nehalem and kvm64 without any success. Each time the VM boots it shuts down with an error complaining about an uncaught thread exception.

Anyway, the final result is that it works so thanks a lot guys for the help.

---

### Post by KillerKelvUK on 2015-08-15
> **chaseadam said:**
> Has anyone had success with the QEMU guest agent in win 10?

Been wanting to give guest agent a try for a while so thought I'd use you as my excuse ;)

As this is new to me I'll explain what I did to make me think I have it working...


[LIST]
[*]Installed the windows qemu guest agent package from the fedora virtio drivers located here [https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download)
[*]Used virt-manager and added the guest agent channel 'org.qemu.guest_agent.0' as a pty device, the libvirt xml looks like this...
[/LIST]
```

    <channel type='pty'>
      <target type='virtio' name='org.qemu.guest_agent.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='2'/>
    </channel>

```
[LIST]
[*]When the guest is run the source path for the channel is created which for me was pointing to '/dev/pts/7'
[*]used socat on my host to connect to the serial device so I can interact with the guest agent.  My command was 'sudo socat /dev/pts/7 -'  the "-" on the end was important but I don't understand its significance yet.
[*]That was it, the below is me issuing some commands into the agent from my host...
[/LIST]
```

kelvin@blackserver:~$ sudo socat /dev/pts/7 -
{"execute": "guest-info"}
{"return": {"version": "0.12.1", "supported_commands": [{"enabled": true, "name": "guest-set-vcpus"}, {"enabled": true, "name": "guest-get-vcpus"}, {"enabled": true, "name": "guest-network-get-interfaces"}, {"enabled": true, "name": "guest-suspend-hybrid"}, {"enabled": true, "name": "guest-suspend-ram"}, {"enabled": true, "name": "guest-suspend-disk"}, {"enabled": true, "name": "guest-fstrim"}, {"enabled": true, "name": "guest-fsfreeze-thaw"}, {"enabled": true, "name": "guest-fsfreeze-freeze"}, {"enabled": true, "name": "guest-fsfreeze-status"}, {"enabled": true, "name": "guest-file-flush"}, {"enabled": true, "name": "guest-file-seek"}, {"enabled": true, "name": "guest-file-write"}, {"enabled": true, "name": "guest-file-read"}, {"enabled": true, "name": "guest-file-close"}, {"enabled": true, "name": "guest-file-open"}, {"enabled": true, "name": "guest-shutdown"}, {"enabled": true, "name": "guest-info"}, {"enabled": true, "name": "guest-set-time"}, {"enabled": true, "name": "guest-get-time"}, {"enabled": true, "name": "guest-ping"}, {"enabled": true, "name": "guest-sync"}, {"enabled": true, "name": "guest-sync-delimited"}]}}
{"execute": "guest-shutdown"}

```

I couldn't get the binary 'qemu-ga' to connect and interact in the same way as 'socat', this is likely user error as I'm still learning this.  Also a lot of the online material says that the virtio-serial device will be created under '/dev/virtio-ports/' (e.g. [http://wiki.qemu.org/Features/QAPI/GuestAgent](http://wiki.qemu.org/Features/QAPI/GuestAgent)) however I could not replicate this, instead it was the virt-manager console which populated the source path for the channel device (/dev/pts/7) when the guest was started.

[s]Final point is that fedora have released updated virtio drivers for windows 10 so I'd start with these, for the above I was still using the 105 release and installing the win8.1/amd64 drivers.[/s]  EDIT:  Mis-read the changelog, there is an updated virtio driver set but this isn't a win10 release.

---

### Post by mauorrizze2 on 2015-08-19
Quick report about another successful upgrade from Windows 8.1 to Windows 10 with additional problems.

Thanks to okky-htf's post I've also managed to get the Windows 10 Upgrade started (from Win8.1, having a bluescreen during after the first reboot).
But I got stuck after the next reboot. He starts "Installing features and drivers", reboots suddenly without a message or bluescreen after staying a while at 32% / 6% and afterwards he reverts the installation.

What I did: change CPU to core2duo, tried both 4 cores and 2 cores
What might have helped: changing to my original setup directly after the next reboot (using core2duo exactly for one bootup) or updating the virtio scsi, network and serial drivers from 0.1.100 to 0.1.109.

Other data: i440fx mainboard, virtio-blk hdd, AMD GPU passthrough, no kvm-hiding needed

Now I can log in to Windows 10... thanks!

---

### Post by Bai Shi on 2015-09-16
Hi KillerKelvUK,

Thank you so much for your detailed documentation about Windows 10 in KVM. I have struggled with it for a week and it seems there is very little discussion about this topic.

Anyway I would like to post my success with upgrading from Windows 7 to Windows 10 in KVM.

I set my processor to be core2duo, +nx and Storage to be on IDE bus. I tried to upgrade using virtio driver it will go BSOD when rebooted. Upon that stage, I tried to switch all different kind of drivers and none of them can successfully revive Windows 10.

I had one other try, I used Virtualbox to boot Windows 7 and upgrade from there. And when it can successfully upgrade to Win10, it will show Invalid Boot Device error when switching back to KVM no matter what driver is used.

I was about to give up but one last try using IDE emulation in Win7 before any part of the upgrading took place. And the upgrading process was perfect.

FYI my disk configuration is as follows:
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source dev='/dev/baishi/win10'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>

My conclusion, it seems that during upgrading, Windows tried to disable some drivers (especially virtio driver for Win7) and the KVM SATA driver is not proper enough for Windows to prepare proper SATA driver in Win10 and thus it will fail to boot up.

Just documenting my experience and hope it can help some other poor soul.

---

### Post by okky-htf on 2015-11-14
I've just upgraded last night to Windows 10 Threshold 2 (November Update) and ran a BSOD and some issues. I've detailed it [here]("https://www.redhat.com/archives/vfio-users/2015-November/msg00164.html") at vfio-users mailing list. Basically I need to *again* change my CPU model back to core2duo and revert it back to host after the upgrade. But I need to completely remove the display driver using Guru3D Display Driver Uninstaller to get my VM up and running again. Hope it helps.

---

### Post by dramaekrs on 2015-12-24
Can't seem to use the QXL driver because it's incompatible to Windows 10. I have tried qxl-0.1-21. Does anybody now the correct driver?

---

### Post by KillerKelvUK on 2015-12-24
> **dramaekrs said:**
> Can't seem to use the QXL driver because it's incompatible to Windows 10. I have tried qxl-0.1-21. Does anybody now the correct driver?

Think you're using a way old driver, source all virtio and qxl drivers from here... [https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download).  Note there are separate drivers if using Win7 vs Win8 and above so you need the qxldod variant.  Also download the 'latest' drivers, not the stable...'stable' was too old for me prev and caused issues that the 'latest' resolved.

Been running Win10 with qxl since Win10 went GA so this def works so just a driver combo problem for you.

p.s. the changelog on the link says the prior virtio release #[COLOR=#000000]0.1.110-2 included [/COLOR][COLOR=#000000]qxl-win-unsigned-0.1-24...the unsigned means Windows will bitch about the install as such but they should operate properly.  That said I haven't upgraded in a while as I'm perfectly stable using the [/COLOR]virtio-win-0.1.110 release.

Best of luck and happy holidays.

---

### Post by heiko_s on 2015-12-28
Thanks for this great thread, and okky - thanks for the qemu script! I used to run Win 7 on Xen for about 3 1/2 years without issues. But when I replaced my guest GPU and put the former guest GPU to work as host GPU, it was time to give kvm a try.

I decided for a clean install of Windows 7, but failed when Windows stopped at the Windows logo screen. Finally I got the Windows 10 ISO and from there on everything went smooth.

Too bad I didn't see this thread earlier, perhaps it would have helped with installing Windows 7.

With regard to the virtio drivers, I'm still a little puzzled. So far I installed only vioscsi, viostor, and NetVM. Do I need the rest of them? If yes, how do I install them (I assume via device manager in Windows, but which driver goes where?)? Here is the complete list of available drivers:

NetKVM/: Virtio Network driver
viostor/: Virtio Block driver
vioscsi/: Virtio SCSI driver
viorng/: Virtio RNG driver
vioser/: Virtio serial driver
Balloon/: Virtio Memory Balloon driver
qxl/: QXL graphics driver for Windows 7 and earlier. (build virtio-win-0.1.103-1 and later)
qxldod/: QXL graphics driver for Windows 8 and later. (build virtio-win-0.1.103-2 and later)
pvpanic/: QEMU pvpanic device driver (build virtio-win-0.1.103-2 and later)
guest-agent/: QEMU Guest Agent 32bit and 64bit MSI installers
qemupciserial/: QEMU PCI serial device driver


Sorry to post this here, but you seem to be the ones who could answer this.

---

### Post by KillerKelvUK on 2015-12-28
@heiko_s, well done with the successful switch to KVM and passthru. The virtio drivers are only needed if your guest is configured to use the virtual hardware the driver is intended for.  To explain, if you weren't passing through a physical GPU the recommended virtual GFX hardware would be QXL for a Windows guest...as such you'd need the associated driver from the .iso which for a Win7 guest would be the qxl/: variant or for a Win8/10 guest it would be the qxldod/: variant.  Other configurations e.g. memory ballooning would need to the Balloon/: driver and if you wanted to use Qemu Guest Tools then you need to install the Guest Agent which is guest-agent/:.

If you are uncertain whether you've installed all the required drivers I'd simply open the Windows Device Manager and look for any item which displays either as an unknown piece of hardware or shows the yellow warning triangle.  Just 'Update Driver' and point to the virtio .iso to search.

---

### Post by heiko_s on 2015-12-28
@KillerKelvUK: Thanks for your quick reply - you answered my question. I thought I might be running inefficient Microsoft-supplied drivers, but it looks like I have the latest virtio drivers. Did some Passmark benchmarks and found an issue with the sequential READ speed of my Samsung EVO 850: ~95 MB/s - that sucks (write speed is a 450 MB/s). Will open a new thread.

---

### Post by sven-hanslik on 2016-07-20
That took really long time: about 30 hours from 99% to the round progress cake meter and then about 3 more hours until the whole thing was done. Maybe because I ran it on a x131e (intel i3) laptop with rather low specs. I used the following command (leave out the -vga and -soundhw part): 
qemu-system-i386 -cpu core2duo,+nx -enable-kvm -m 3048 -vga std -daemonize -soundhw ac97 /media/sdc1/win10.qcow2
I tried with kvm=off but that gave an error, and without -enable-kvm it was all just very slow. After the Upgrade I replaced the core2duo,+nx part with "host" and added also some cores=, sockets=, threads= and began disabling eyecandy on the guest win10. Of course, I still have a copy of the win7 before the upgrade. 
Das hat richtig lang gedauert: ca 30 Stunden von den 99% installing bis zu dem "kuchendiagramm", und dann nochmal 3 Stunden. Vergesst nicht, eine Kopie von dem Windows7 vor dem Upgrade zu behalten, auch, falls der Upgrade irgendwie schiefgeht. 
Thanks

---

### Post by aeltester on 2016-08-16
sadly, nothing seems to have changed, still. running newest windows 10 edu N with <cpu match='exact'><model fallback='allow'>core2duo</model><topology sockets='x' cores='y' threads='1'/></cpu> where x matches either 2,2 or 1,4 works.

neither   <cpu mode='host-model'><model fallback='forbid'/><topology sockets='x' cores='y' threads='1'/></cpu>
nor   <cpu mode='host-passthrough'><feature policy='disable' name='lahf_lm'/></cpu>

seem to work on my xeon server. a vm this slow is next to useless.

EDIT: This seems to work after all:

<cpu mode='host-passthrough'>
<feature policy='require' name='vmx'/>
</cpu>

---

