---
title: "QEMU/KVM Gaming VM on Ubuntu 16.04 help"
date: 2016-07-07
forum: Virtualisation
---

### Post by billy34 on 2016-07-07
So I'm trying to build a computer around the idea of running Ubuntu 16.04 and running Windows 7 Pro (Then "downgrading" to Windows 10 Pro) on a Virtual Machine. I've even looked into (unsuccessfully) just setting up the Windows 7/10 install on the 2nd hard drive then finding a way to wrap that into a VM and run it from Ubuntu.

*USE* I primarily want to use Ubuntu 16.04. I do a lot of computer diagnostics work as a technician as well as some graphics & audio and it is my preferred environment to work with. I also do play games, though not extremely hard core and like to play them native on Linux when possible. I just put this rig together and plan to add more drives, etc. later on. I've even considered moving to a PCI-E M.2 drive. Overall when it comes to my data (emails, downloads, ISO's, personal information, etc.) I just don't trust Microsoft with more than I have to give them and want to be able to use this system to limit that while still having access to what I need from them.

As for Windows. I do software development on several platforms. Some of which includes developing games for Windows 10 universal apps (Xbox One/Windows 10).

In a perfect world I'd have a shared drive between the two OS's as well, something like FAT32 that I can swap files around if I can't get drag n' drop setup. I want to be able to do my graphics editing in Ubuntu, right now to accomplish this I'm storing all of my save files/graphics/music/etc. on Dropbox which is setup on both systems so I can essentially use it like a share drive.

In the end I'd like to have Ubuntu setup as my host OS with Windows 10 as a VM. Due to the software I will be running on Windows 10 I need it to function as much like a fully usable OS as possible. This includes graphics because not only do I need to test the games I'm working on but I also have some Windows based MMO's I'd like to play that are not playable through Wine.


**On a side note, Windows 10 spying was one of the final straws to push me to into no longer running Windows as my primary OS. If there is a way to "limit" Windows ability to connect to do it's spy reporting through the VM's network controller that's something I'm very interested in once I get this system working right.**

So here's what I'm working with, I'll go into what I've tried and my problems I've had at the end:

Motherboard: ASUS Z9PA-D8 (server board)
Processors: 2x Xeon 2670 (C2 Stepping) "SR0KX"
Trying to dedicate 4 cores, 2 threads each - 8 total threds

Primary GPU for Linux EVGA 960 FTW 4GB
Secondary GPU for Windows ASUS Radeon HD7870 2GB
(I am waiting on an RMA for a XFX HD7990 I'd like to switch this to later)
**With ATI hating on Ubuntu 16.04 and nVidia seeming better for Linux drivers all around this seemed like the logical choice.**

Total Ram 64GB DDR3 Samsung 16000
Total amount I'd like to dedicate for "this" VM is 16GB

My Ubuntu installation is on a 512 GB Toshiba SSD.
I want Windows installed on a PNY 480 GB Gaming SSD, I'd like Windows to use the whole SSD not just a partial image on it.
Right now they are on the same controller but I have considered if needed getting a PCI-E to SSD adapter and passing it through as well, not sure if this would be best.


I currently have this system setup dual screen, one monitor plugged into each card. Later when I can figure out how to get Ubuntu to pass audio through HDMI on the 960 FTW then I'll also have that one hooked up to my TV as a secondary monitor.

The current goal is to have one monitor running Ubuntu and the other running Windows

Currently I do have a KVM switch setup so if needed to for hardware I can change my keyboard & mouse between ports. It's not attached to a monitor yet, just makign my same keyboard & mouse occupy seperate ports so if I have to pass through the USB for the mouse/keyboard so I can still use the same one on Ubuntu.

Right now I have QEMU/KVM setup, that's what I've been trying to use.
I also setup Virt Manager (fail) and Libvert.
Been trying most recently to configure it manually, which got me feeling like I got the closest (yet so far away).

So for manual configuration I started here with this video:
[https://www.youtube.com/watch?v=w-hOr44oBAI](https://www.youtube.com/watch?v=w-hOr44oBAI)

Which is basically supposed to be an updated version of this guide:
[https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)

Which references this site for the VM script:
[http://ubuntuforums.org/showthread.php?t=2229929&page=2](http://ubuntuforums.org/showthread.php?t=2229929&page=2)

So doing this manually here's what I can't figure out:

Using DD to create a VM image (as the guide shows) how I can create it to use a dedicated hard drive for the virtual machine?

Apparently somewhere along the lines I've gotten either directories messed up or commands are just wrong. I can't even get this VM to start. I believe my machine is "prepped" but that's about all.

 The ATI graphics card & audio are both available to stub. I originally tried and failed to use VIFO and didn't even realize I was using something different until I got to the stub part of the current guide. I have GRUB blacklisting the ATI drivers when I boot if that helps to know (part of attempting a different guide)

When I boot my system now the Ubuntu logo appears on the monitor that is plugged into the ATI card (normally I just would see my script running on that monitor as the VM crashed when I tried to set it up with Virt Manager).

Here's my horrible script that I couldn't make sense out of what I was doing:
-------------------------------------------------------------
```

#!/bin/bash

configfile=/etc/vfio-pci1.cfg

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

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 16384 -cpu host,kvm=off \
-smp 4,sockets=1,cores=4,threads=2 \
-bios /usr/share/seabios/bios.bin -vga none \
#-*USB ADDON I DON'T UNDERSTAND*-usb -device usb-host,hostbus=1,hostaddr=$usb1 -device usb-#host,hostbus=1,hostaddr=$usb4 \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=02:00.1,bus=root.1,addr=00.1 \
-device virtio-scsi-pci,id=scsi \
-drive file=/home/owner/vm/windows1.img,id=disk,format=raw,if none -device scsi-hd,drive=disk \
#-drive file=/home/owner/vm/windows.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
#drive file=/home/owner/Share_Test/Windows_Pro_regular.iso,id=isocd,if=none -device scsi-cd,drive=isocd \
#drive file=/media/weatherman/Storage5/OS_ISOs/Windows_7_Pro.iso,id=isocd,if=none -device scsi-cd,drive=isocd \
-boot menu=on

exit 0

```
-------------------------------------------------------------
I am not sure if I'm so far off or what but I've ended up beating my head on my desk so many times I thought it best to turn to those far more experienced in this sort of setup than I am for help.

---

### Post by heiko_s on 2016-07-07
Hello Billy32,

I've written a KVM tutorial here: [https://forums.linuxmint.com/viewtopic.php?f=231&t=212692]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692"). This may help you get started.

Important: It's much better to start with Windows 10 and UEFI boot as described in my tutorial. BUT, I'm not sure your ASUS Radeon HD7870 graphics card supports UEFI - check as described in the tutorial. One more advice regarding my KVM tutorial: use the vfio-pci driver instead of stub as described in my post here: [https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&start=40#p1174032]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&start=40#p1174032")

Windows 7 does NOT work with UEFI, at least not out of the box. I haven't managed to create a bootable UEFI image for Win 7. Since I bought and registered a Win 7 Pro retail edition, I was able to download Win 10 and install from scratch. My license allows the upgrade and I can move from PC to PC (or from VM to VM).

Vice versa, I had better experience with Xen and Win7 than with KVM. I also wrote a how-to on Xen (see [https://forums.linuxmint.com/viewtopic.php?f=231&t=112013]("https://forums.linuxmint.com/viewtopic.php?f=231&t=112013")).

Let me know if the KVM tutorial with Win 10 works.

---

### Post by billy34 on 2016-07-09
Honestly I totally forgot about the whole installing Windows 10 directly with the Windows 7 key. I just had some pretty major surgery and it's kickin my rear but I'll try to get through this.

As far as the stub vs. vifo, I'm not quite sure I know how to undo what I've done but I'll work on that too.

As far as the HD 7870 I know there is an updated EUFI bios, I just can't remember for the life of me if I already upgraded it or not.

---

### Post by MAFoElffen on 2016-07-09
@billy34

Please return to post #1 and edit your post > Advanced edit > Highlight individual segments of commands and/or output > Select the "#" icon to enclose those in code tags.

It is a forums policy... That's up less room on a page, and makes reading those easier. Otherwise, harder to see what may be a problem or not.

---

### Post by KillerKelvUK on 2016-07-09
> **billy34 said:**
> Honestly I totally forgot about the whole installing Windows 10 directly with the Windows 7 key. I just had some pretty major surgery and it's kickin my rear but I'll try to get through this.

As far as the stub vs. vifo, I'm not quite sure I know how to undo what I've done but I'll work on that too.

As far as the HD 7870 I know there is an updated EUFI bios, I just can't remember for the life of me if I already upgraded it or not.

Hi billy34, if you obtained Windows 10 via the free upgrade from Windows 7, 8, 8.1 then unfortunately you can't just install Windows 10 and use your retail license key from Windows 7 to activate it.  Microsoft require you to install Windows 7, activate it and then upgrade to Windows 10...yeah a bit of a ball ache but at least its free right.  Once you have done this Microsoft then register the Windows 7/10 activation against your machine configuration (I think its MAC address of your NIC and CPU architecture), this then basically allows you to do a clean re-install of Windows 10 without having to go the upgrade route should you need to...however you have to keep your guest configuration consistent e.g. if you clone the guest and create a new random MAC address I believe this will break the activation lock-in.

Regards installing Windows 7 with UEFI I didn't think this was as difficult as heiko_s was making out, I've certainly done it in the past but to be fair to heiko_s I wasn't confident enough just to call this out so I decided to give it a quick go.  To my surprise I can't even get past the "start windows" boot screen to get to the installer, some posts on other forums are suggesting the 16.04 KVM video drivers are causing some incompatibility and suggest using the cirrus driver, but this didn't work for me.  Windows 8.1 & 10 work fine still, I use a Windows 10 guest with GFX pass through daily and no issues so this is definitely a Windows 7 only issue.  Have you come across this?

Regards a shared disk between host and guest, my solution is to setup a samba server on the host which provides access to a mount in my storage which is then accessible in a Windows guest as a mapped network drive (smb).  The use case will affect your solution here as read/write performance is likely a consideration but this method works for me.

You can isolate and pass through an entire physical disk to a guest ([https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-Virtualization-Adding_storage_devices_to_guests-Adding_hard_drives_and_other_block_devices_to_a_guest.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-Virtualization-Adding_storage_devices_to_guests-Adding_hard_drives_and_other_block_devices_to_a_guest.html)) however this has some risks which the link spells out, I'd personally recommend you at least try the qcow2 route and see how performance is for you.

Lastly in terms of a guide, there are lots out there but personally I'd put stock into this blog ([http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html)), its by a guy called Alex Williamson who is one of the main dev's at Red Hat working on KVM and he personally has created most of the code that is now in the mainline kernel for vfio and passthrough.  The blog has a 5 part article on how to achieve passthrough and works around common barriers, it uses the vfio-pci driver approach as heiko_s called out but it also shows you how to use virt-manager for GFX passthrough...I still see a lot of people using .sh scripts to move the devices around which is fine if thats your preference but not many call out an alternative which is virt-manager...for me this works perfectly for passthing through my GFX to windows, osx and my dvb-s card to an ubuntu guest.

Best of luck with this, do come back here with any more questions as there are lots of people like heiko_s, MAFoElffen and myself willing to help.

---

### Post by MAFoElffen on 2016-07-09
> **KillerKelvUK said:**
> Hi billy34, if you obtained Windows 10 via the free upgrade from Windows 7, 8, 8.1 then unfortunately you can't just install Windows 10 and use your retail license key from Windows 7 to activate it.  Microsoft require you to install Windows 7, activate it and then upgrade to Windows 10...

Sort of yes and no on that. (insider Group- Still testing Win10 builds and Win Server 2016) Starting with Win10 build 1511, that changed. The install iso for that build (only lasted a matter of a week before they pulled it and replaced it with build 1511b) now starts the install with asking for the product key... At that point it expects only a valid WIN10 product key.  (but there is a way around it.)

If you skip the product key and finsh the install, then go back into the settinggs to activate it, then enter your Win 7-8.1 key ... and it will activate it, with that key. They did that to honor a re-install of Win10, with that previous key. BUT...

I'm not sure what happens with that after July 29th! That is the deadline for the free upgrade. They called the cut-off for the free upgrade to Win10, before their Special Anniversary Update on Aug 2d... I knwo the rest of the link on the prodcut key is the machine ID on the motherboard... So I fear that they might turn that part fully on, on the 30th. I'm seeing some of that checking now, on whether a product key was used on another motheboard. (ones that get fried or rma's.)
> **KillerKelvUK said:**
> Best of luck with this, do come back here with any more questions as there are lots of people like heiko_s, MAFoElffen and myself willing to help.
Agreed.

EDIT-- Tip for this section... If you are going to update your Win VM's... That deadline is this Friday. With each build I test on Win10 and Server 2016 is locking down their security on that. So I've been busy getting snapshots and upgraging my MS VM Guests.

---

### Post by KillerKelvUK on 2016-07-10
Quick update; managed to the Windows 7 installer dialog using legacy seabios and the cirrus display adapter, using OVMF and cirrus doesn't work, so it would seem that until this bug is addressed Win 7 UEFI isn't possible unless you reverse in the UEFI config post legacy install ([https://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](https://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx))

---

### Post by BSDShoes on 2016-07-11
EDIT- nevermind, turned out to be a user error, got it working.

PS- @billy here's my KVM script that can boot win 7.
```

#!/bin/bash
 
configfile=/etc/vfio-pci.cfg
vmname="windows10vm"
 
vfiobind() {
   dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
    
}
 
 
if ps -A | grep -q $vmname; then
   echo "$vmname is already running." &
   exit 1
 
else
 
   cat $configfile | while read line;do
   echo $line | grep ^# >/dev/null 2>&1 && continue
      vfiobind $line
   done
 
# use pulseaudio
export QEMU_AUDIO_DRV=pa
 
cp /usr/share/edk2.git/ovmf-x64/OVMF_VARS-pure-efi.fd /tmp/my_vars.fd
 
qemu-system-x86_64 \
  -name $vmname,process=$vmname \
  -cpu host,kvm=off \
  -machine type=pc-i440fx-2.1,accel=kvm \
  -smp 4,sockets=1,cores=2,threads=2 \
  -enable-kvm \
  -vga none -nographic \
  -monitor stdio \
  -m 8192 \
  -mem-path /run/hugepages/kvm \
  -mem-prealloc \
  -balloon none \
  -rtc clock=host,base=localtime \
  -serial none \
  -parallel none \
  -soundhw hda \
  -device vfio-pci,host=01:00.0,multifunction=on,x-vga=on \
  -device vfio-pci,host=01:00.1 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=dc \
  -device virtio-scsi-pci,id=scsi \
  -drive file=/VM/Windows10.img,id=disk0,format=raw \
  -drive file=/dev/sdb,id=disk1,format=raw \
  -usb -usbdevice host:04d9:a0d1 -usbdevice host:1532:0034 \
  -net nic -net user,hostfwd=tcp::3389-:3389
 
  exit 0
fi
```

---

### Post by MAFoElffen on 2016-07-11
<<I went ahead and put the OP's script in Post #1 within code tags as an example of that to the OP...>>

---

### Post by KillerKelvUK on 2016-07-11
> **BSDShoes said:**
> I can get both Win 7 and Win 10 to work in KVM, KVM works great under 3.16 kernel on Debian or 3.19 on Mint 17.3 using PCI passthrough to my GTX750Ti however with Ubuntu 16.04 and Mint 18 with 4.x kernels I get distorted output to my i3 6100's iGPU since I'm using intel_iommu=on (igfx_off doesn't enable IOMMU).  Using grub line "nouveau.blacklist=1 i915_hd_vgaarb=1 intel_iommu=on".  Any clues in this?

[http://imgur.com/IP9eTSI](http://imgur.com/IP9eTSI) 


Hey, so a new thread is needed altogether for this...

[LIST]
[*]I'm a little confused by you problem statement vs your configuration...you have i915 kernel param's and are passing x-vga=on both of which suggest legacy bios and VGA arbitration hacks are needed yet you are using OVMF instead of seabios and a quick google of your GFX card says its likely UEFI capable.  Is you're whole setup i.e. mobo, host config and GFX UEFI capable and configured?  If not I'd suggest your issue is VGA arbitration related and the screen distortions are the typical result.
[*]Does this issue only occur when you start a guest and not when the host boots with the intel_iommu=on kernel param set?
[*]To confirm the IGD on your i3 is for host only GFX and our GTX750 is for pci passthrough to a virtual machine only?
[/LIST]

---

### Post by billy34 on 2016-07-21
> **MAFoElffen said:**
> @billy34

Please return to post #1 and edit your post > Advanced edit > Highlight individual segments of commands and/or output > Select the "#" icon to enclose those in code tags.

It is a forums policy... That's up less room on a page, and makes reading those easier. Otherwise, harder to see what may be a problem or not.


I apologize but I have no idea exactly what you are asking.

When I go to advanced edit nothing shows up to highlight.

---

### Post by T.J. on 2016-07-21
I am also a developer, and have such a system working, Billy.  I'm happy to share with you all I know.  I tried to post a detailed message, but I received an error. After the hacking, the board or the authentication is clearly still broken.  If you still need help,  please private message me on the board using my profile and we can chat via email instead.  I don't have time to re-type everything I just tried to post only to have it fail again.

Apologies to the forum, but as I see it, it is a matter of getting things accomplished, not fighting or debugging forum problems right now.

---

### Post by Doug S on 2016-07-22
I suppose it is too late now, and sorry for the tangent on this thread, but:

> **T.J. said:**
> I tried to post a detailed message, but I received an error....I don't have time to re-type everything I just tried to post only to have it fail again.When the same occurred for me, on a different thread, I was able to use the browser back button and got my original typing back, which I then copied into a text file.

---

### Post by T.J. on 2016-07-22
I'm posting in small bits because of the forum posting issues. I apologize in advance.  When I recommend something, feel free to disagree or ignore it.  This is just advice based on my own experience or opinion - nothing more or less.

> [LEFT][COLOR=#000000][FONT=Ubuntubeta]*I've even looked into (unsuccessfully) just setting up the Windows 7/10install on the 2nd hard drive then finding a way to wrap that into aVM and run it from Ubuntu.*[/FONT][/COLOR]

[/LEFT]
[LEFT]
I do not recommend doing this, because you run the risk of corrupting the data on the drive.  Windows not only tends to lock the drive during hibernation, but it is less tested than the normal methods of using an image file. 

> 
*[COLOR=#000000][FONT=Ubuntubeta]usic/etc.on Dropbox which is setup on both systems so I can essentially use itlike a share drive.[/FONT][/COLOR]*

[COLOR=#000000][FONT=Ubuntubeta]Like some others suggest, Samba is a good choice.[/FONT][/COLOR][/LEFT]

---

### Post by T.J. on 2016-07-22
> [LEFT][COLOR=#000000][FONT=Ubuntubeta]*Inthe end I'd like to have Ubuntu setup as my host OS with Windows 10as a VM. Due to the software I will be running on Windows 10 I needit to function as much like a fully usable OS as possible. Thisincludes graphics because not only do I need to test the games I'mworking on but I also have some Windows based MMO's I'd like to playthat are not playable through Wine.*[/FONT][/COLOR][/LEFT]
[LEFT]
[COLOR=#000000][FONT=Ubuntubeta]Use VGA passthrough. [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]=) The first step is making sure your motherboard supports IOMMU. You mentioned already that you have a second GPU.[/FONT][/COLOR]

> [COLOR=#000000][FONT=Ubuntubeta]*If there is a way to "limit" Windows ability to connect to do it's spy reporting through the VM's network controller that's something I'm very interested in once I get this system working right.***[/FONT][/COLOR]


Not really, at least without difficulty, unless you are familiar with bridging.  I recommend that you use Windows 10 only for games or projects where no privacy is required.
[/LEFT]
> [LEFT][COLOR=#000000][FONT=Ubuntubeta]*Thecurrent goal is to have one monitor running Ubuntu and the other running Windows*[/FONT][/COLOR][/LEFT]
[LEFT]

[COLOR=#000000][FONT=Ubuntubeta]Easily done.  If I might make one other comment?  [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]Others disagree, but I felt I should mention that [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]I personally do not recommend using an SSD for virtualization.  The fact that [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]a guest is [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]writing to emulated hardware gives a less than optimal [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]write pattern [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]with [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]an SSD&#8217;[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]s [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]limited lifespan.  [/FONT][/COLOR][/LEFT]

---

### Post by T.J. on 2016-07-22
> [LEFT][COLOR=#000000][FONT=Ubuntubeta]*Currently I do have a KVM switch setup so if needed to for hardware I canchange my keyboard & mouse between ports. *[/FONT][/COLOR][/LEFT]
[LEFT]
[COLOR=#000000][FONT=Ubuntubeta]Contrary to popular opinion and a lot of HOWTO docs, you do [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]**not **[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]need a KVM switch or software like synapse.  A local KVM is quite capable of handling switching mouse and keyboard requests between hosts and guests if you set it up properly.[/FONT][/COLOR]
[/LEFT]
> [LEFT]

[COLOR=#000000][FONT=Ubuntubeta]*Right now I have QEMU/KVM setup, that's what I've been trying to use. *[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]*I also setup Virt Manager (fail) and Libvert.*[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]*Been trying most recently to configure it manually, which got me feeling like I got the closest (yet so far away).*[/FONT][/COLOR]

[/LEFT]
[LEFT]I&#8217;ve found that using  libvirt/Virt-Manager causes more problems than it solves, especially if VGA passthrough is a goal.  Libvirt can actually interfere, causing Windows to crash the video driver unless you use UEFI.[/LEFT]

---

### Post by T.J. on 2016-07-22
> [LEFT][COLOR=#000000][FONT=Ubuntubeta]*Using DD to create a VM image (as the guide shows) how I can create it to use a dedicated hard drive for the virtual machine?*[/FONT][/COLOR][/LEFT]
[LEFT]

[COLOR=#000000][FONT=Ubuntubeta]I recommend using qemu-img [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]not dd [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]to create [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]drive images for your guests.


I create my bindings using a systemd script, which I assume you do not need, but I use this as a startup script with a sudo/kdesudo/gksu session for my Windows guest.  Naturally, it will require changes, but hopefully it will help as an example.
[/FONT][/COLOR]
```

#!/bin/sh
export QEMU_AUDIO_DRV=pa

/usr/bin/qemu-system-x86_64 -enable-kvm -m 8192 -cpu host,kvm=off \
-smp 3,sockets=1,cores=3,threads=1 \
-machine q35,accel=kvm \
-device qxl \
-usb \
-device usb-mouse \
-device usb-kbd \
-soundhw hda \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=04:00.1,bus=root.1,addr=00.1 \
-device virtio-blk-pci,scsi=off,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=0 \
-device virtio-blk-pci,scsi=off,addr=0x8,drive=drive-virtio-disk1,id=virtio-disk1 \
-drive file=/usr/local/VM/Games.img,if=none,id=drive-virtio-disk1,format=raw,media=disk \
-drive file=/usr/local/VM/DevMach.qcow2,if=none,id=drive-virtio-disk0,format=qcow2,media=disk \
-netdev tap,id=user.0 \
-device virtio-net-pci,netdev=user.0,mac=52:54:00:58:ba:9c \
-boot order=c \
-usbdevice host:9.2 \
-rtc base=localtime,driftfix=slew


wait

```

[/LEFT]

---

### Post by heiko_s on 2016-08-04
> **billy34 said:**
> Honestly I totally forgot about the whole installing Windows 10 directly with the Windows 7 key. I just had some pretty major surgery and it's kickin my rear but I'll try to get through this.

As far as the stub vs. vifo, I'm not quite sure I know how to undo what I've done but I'll work on that too.

As far as the HD 7870 I know there is an updated EUFI bios, I just can't remember for the life of me if I already upgraded it or not.

About installing Win 10: I downloaded the Win10 ISO and installed it using my win7 key. But note that my Windows 7 is a full-fledged Windows 7 Pro **retail** license that I bought directly from Microsoft at full price ($318). This license allows me to install Windows anywhere I want. If you got Windows pre-installed on a PC, then you're out of luck and not allowed to run it in a VM.

---

### Post by T.J. on 2016-08-08
> **heiko_s said:**
> About installing Win 10: I downloaded the Win10 ISO and installed it using my win7 key. But note that my Windows 7 is a full-fledged Windows 7 Pro **retail** license that I bought directly from Microsoft at full price ($318). This license allows me to install Windows anywhere I want. If you got Windows pre-installed on a PC, then you're out of luck and not allowed to run it in a VM.

Quite correct.  You shouldn't use an OEM license if you want to use Windows in virtualization.  Literally, you can, but you are violating the license if you do.

---

### Post by heiko_s on 2016-10-01
I apologize for reviving an old thread, but there is some good information here and I want to throw in my 2c:

1. The best way to get VGA passthrough working is using UEFI boot (the OVMF BIOS). You need hardware and software that supports UEFI. On the hardware side, the motherboard / BIOS and the graphics card to pass through must support UEFI. On the software side (i.e. Windows), from Windows 8 onwards Microsoft supports UEFI boot. Windows 7 doesn't support UEFI, but there is a way to produce a UEFI bootable image (it's a pain in the neck).

2. I installed Windows 10 from a downloaded image and entered my Windows 7 license key. In my case it worked since I own a full-fledged retail license. If Windows was pre-installed on your PC, the license (OEM license) usually doesn't allow for running that Windows in a VM.

3. I use qemu - libvirt, virt-manager etc. seem to make things more difficult.

4. @T.J.: I may be partly responsible for increased sales of KVM switches. I agree that one doesn't really need a KVM switch, or even Synergy. But it would be great if you could explain in more detail how to configure keyboard and mouse under qemu/kvm in a way I can switch from VM to host and back whenever I want.

5. About SSD: T.J. discourages the use of SSD, arguing reduced lifespan. This may be a valid point, but I like to hear more on that from T.J. or others who could share some light. Here is what I have done so far when using an SSD:

A. I use LVM for all VM storage (and Linux storage except /boot). Performance-wise it works great, once everything is tweaked. For the Windows VM, I create a logical volume (lv) and leave it unformatted. I format that volume when I install Windows (the Windows installer does the formatting).

B. I use the following qemu options:
 -drive id=disk0,if=virtio,cache=none,format=raw,aio=native,file=/dev/mapper/lm13-win10 \
 -drive id=disk1,if=virtio,cache=none,format=raw,aio=native,file=/dev/mapper/photos-photo_stripe \

The first drive definition is a SSD, the second happens to be two striped LVM drives.

C. Once Windows 10 is installed in the VM, I run the following in the admin command prompt:
```
winsat formal
```

During the VM installation, Windows 10 will **not** recognize the SSD. Not only will Windows 10 perform unnecessary disk optimization tasks, but these "optimizations" can actually lead to reduced SSD life and performance issues (see T.J.'s recommendation).

The above command lets Windows 10 run the benchmark (Windows Experience Index) and by doing this it will actually discover the SSD. You can check it in the File Explorer on the Properties -> Tools -> Optimize tab (right click on the SSD drive). For more about this see my how-to here: [HOW-TO make dual-boot obsolete using kvm VGA passthrough]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692")

I've done lots of benchmark tests (see for example [here]("https://forums.linuxmint.com/viewtopic.php?f=231&t=197754")) and while it has been difficult to tweak KVM for optimal performance, I've come to a point where I'm happy for now.

Since there is very little information out there on KVM tuning, I am most grateful for any feedback.

---

### Post by T.J. on 2016-10-03
> I apologize for reviving an old thread, but there is some good information here and Iwant to throw in my 2c:


That is quite all right. I am far more tolerant.  These threads are used as reference, sometimes for years.


> 

1. The best way toget VGA passthrough working is using UEFI boot (the OVMF BIOS). You need hardware and software that supports UEFI.

Not in my experience.  It depends on the hardware you are using, and the time you spend.  I have had much better success with SeaBIOS than the Tiano OVMF.  In fact, SeaBIOS works with both UEFI and non-UEFI capable cards.

> &#8220; On the hardware side, the motherboard /BIOS and the graphics card to pass through must support UEFI.&#8221;

It's helpful, but it is not required.  UEFI can be a very buggy proposition, depending on your firmware.  You definitely want IOMMU support however.



> &#8220;Windows 7 doesn't support UEFI,but there is a way to produce a UEFI bootable image (it's a pain inthe neck).&#8221;

Not true.  Windows 7 SP1 and later supports UEFI.  Original release discs, SP0 &#8211; do not.

> 

&#8220; If Windows was pre-installed on your PC, the license (OEM license) usually doesn't allow for running that Windows in a VM.&#8221;

Quite correct.


> 

&#8220;3. I use qemu -libvirt, virt-manager etc. seem to make things more difficult.&#8221;

It can, but really only if you are trying to use VGA passthrough.  Libvirt has a lot of decent management features.

> 

&#8220;4. @T.J.: I maybe partly responsible for increased sales of KVM switches. I agree that one doesn't really need a KVM switch, or even Synergy. But it would be great if you could explain in more detail how to configure keyboard and mouse under qemu/kvm in a way I can switch from VM to host and back whenever I want.&#8221;

That's easy.  You define an extra QXL display along with defining your mouse and keyboard as USB rather than PS/2. This will enable a separate (usually blank) QEMU monitor window that you can use with the left Ctl+Alt key combination to release back to the host. To go back to the guest, simply click the mouse in the QXL display.  For example:

```
/usr/bin/qemu-system-x86_64 -enable-kvm -m 8192 -cpu host,kvm=off \
-smp 3,sockets=1,cores=3,threads=1 \
-machine q35,accel=kvm \
-device qxl \
-usb \
-device usb-mouse \
-device usb-kbd \
-soundhw hda \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=04:00.1,bus=root.1,addr=00.1 \
-device virtio-blk-pci,scsi=off,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=0 \
-device virtio-blk-pci,scsi=off,addr=0x8,drive=drive-virtio-disk1,id=virtio-disk1 \
-drive file=/usr/local/VM/Games.img,if=none,id=drive-virtio-disk1,format=raw,media=disk \
-drive file=/usr/local/VM/DevMach.qcow2,if=none,id=drive-virtio-disk0,format=qcow2,media=disk \
-netdev tap,id=user.0 \
-device virtio-net-pci,netdev=user.0,mac=<define your own mac address> \
-boot order=c \
-usbdevice host:9.2 \
-rtc base=localtime,driftfix=slew
```

> &#8220;5. About SSD:T.J. discourages the use of SSD, arguing reduced lifespan. This maybe a valid point, but I like to hear more on that from T.J. or others who could share some light.&#8221;

I admit freely that I have not tested this empirically, but given the number of reads and writes, it seems a reasonable assumption that there will be some sacrifice. It could be negligible or it could be quite significant over the life of the SSD.  Frankly, I just don't know.

Virtual machines have no idea what kind of physical drive they are hosted on. A virtualized Windows will not pattern its access for optimal SSD management. Windows in particular does all swap work in a single large file in one place. If you use a drive image, you can expect the host OS to perform some TRIM operations for VM writes. It still occurs to me that these are huge commits being requested without being aware of the drive type.  I would not expect the read and write patterns that you would see with normal filesystem use.  That is why I discourage it, but I have no real proof that it is actually detrimental to the SSD itself. 

 Software engineers tend to learn caution, even if may be unwarranted.

---

### Post by heiko_s on 2017-02-15
@TJ: Time flies but I feel your last post deserves a reply.

1. UEFI vs. Seabios: I guess it depends on what you've got. If one tries to pass through an old GPU that doesn't support UEFI and can't be BIOS-upgraded, then perhaps Seabios is the better way. The reason I suggest UEFI is that the VM can boot faster (it's always primary passthrough), but mainly because of an arbitration issue with Intel IGD graphics. This saves some (many?) users the need to compile the i915 VGA arbitration patch into the kernel.

2. Windows 7 UEFI support: You are correct in that Windows 7 supports UEFI with the SP1 upgrade. However, the original Win7 ISO doesn't allow UEFI boot. I'm not aware of a downloadable Win7 ISO that supports UEFI out of the box. In other words, in order to install Windows 7 using UEFI, one has to "patch" a non-UEFI Win7 ISO to get it going. It can be done, but I haven't succeeded and decided to upgrade to Win 10.

3. virt-manager / libvirt: I'm sure it has its place, but the documentation used to be a nightmare. I run VGA passthrough with a start script like you do - simple and mostly transparent.

4. Switching from VM to host and back without Synergy / KVM switch / etc.: Thanks *1000 - I need to test that. I hope your method also works with UEFI passthrough, without the x-vga=on option in the command.

Out of curiosity: Why do you specify "-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1"? Where are you using these devices? How do you benefit from this?

Sorry for what may be a dumb question, but you seem like someone who can answer that.

---

### Post by T.J. on 2017-02-20
[COLOR=black][FONT=Tahoma]> [COLOR=black][FONT=Tahoma]@TJ: Time flies but I feel your last post deserves a reply.[/FONT][/COLOR]

[COLOR=black][FONT=Tahoma]Thank you. That is quite all right.  As I said earlier, I am more tolerant of old threads, and I am happy to discuss this with you at your leisure.  That said, in the intervening time, I have moved most of my gaming back over to Windows.  I did that for performance testing, and because I have to write Windows code for work.  Sometimes, the more complex tasks are best done directly on hardware, as it can crash VMs and you need real performance metrics.  Although neither side would want to admit it, Windows and Linux actually share a great deal in common, just as much as they have that is different.  Systemd could be reasonably compared to SVCHOST in terms of function.


 Yes, I still use Linux, and I advocate VMs. 

As a programmer, however, I do not feel bound to choose one operating system over another, merely what is most expedient and effective for whatever reasons present themselves at the time. I believe in FOSS, not necessarily just Linux, which has had just as many design hiccups as Windows in its history.  Such is the nature of source code, written by human beings.

> 3. virt-manager / libvirt: I'm sure it has its place, but the documentation used to be a nightmare. I run VGA passthrough with a start script like you do -simple and mostly transparent.

LOL "WAS"?  It still is, in my opinion. I&#8217;m glad you approve of the script.  =)  It&#8217;s nice to know that you have a similar approach.

> 4. Switching from VM to host and back without Synergy / KVM switch / etc.:Thanks *1000 - I need to test that. I hope your method also works with UEFI passthrough, without the x-vga=on option in the command.[/FONT][/COLOR]> 

[COLOR=black][FONT=Tahoma]Well, don&#8217;t thank me overmuch, I found it elsewhere and adapted it for my own use.  There are lots of people out there who are much smarter than I am. My only gift is the experience to take what bits I need, perhaps invent one or two bits of my own, and then get them working together.  The truth is that programming or technology is actually cumulative, and seldom original.

> Out of curiosity: Why do you specify "-deviceioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1"? Where are you using these devices? How do you benefit from this?

That is a line to manually setup the PCI-E host bridge driver for use with the card. It is used with the Q35 chipset, instead of the 440fx that some others prefer. The Qemu documentation can provide more information than I could. 

> Sorry for what may be a dumb question, but you seem like someone who can answer that.


Not at all.  It&#8217;s always a pleasure to be of service.  Thank you for the ego-boost, BTW.  There are no really dumb questions, only a desire to learn, and generally, that is a good thing.  I&#8217;m quite happy to chat with you at length on other subjects as well if you like. If we spend a lot of time chatting, at some point, I might suggest social media rather than the Ubuntu forums, as it is more expedient, and because Ubuntu has strict policies regarding some issues.  If that is something you would like, please send me a personal message on the forum.[/FONT][/COLOR]
[/FONT][/COLOR]

---

