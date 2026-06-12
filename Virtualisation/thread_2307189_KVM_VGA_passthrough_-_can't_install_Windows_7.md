---
title: "KVM VGA passthrough - can't install Windows 7"
date: 2015-12-22
forum: Virtualisation
---

### Post by heiko_s on 2015-12-22
I decided to upgrade my GPU and switch from Xen to kvm.

Hardware:
CPU~Hexa core Intel Core i7-3930K (-HT-MCP-) speed/max~1207/5700 MHz Kernel~3.19.0-41-generic x86_64 Up~1:20 Mem~20682.9/32180.0MB HDD~8871.8GB(30.2% used) Procs~290 Client~Shell inxi~2.2.28

Host GPU: Nvidia Quadro 2000 with Nvidia proprietary drivers under Linux
GPU for Windows guest: Gigabyte GTX 970 (Nvidia)

The GTX 970 supports UEFI and I tried to use OVMF.

I also installed Qemu 2.1.2 (ppa:jacob/virtualisation) to allow -cpu host,kvm=off (needed for Nvidia cards).


This is where I got stuck:

I can't boot the **Windows 7**.ISO, no matter what I try. At the very best I'm getting the "Starting Windows" screen with the Win logo. The screen switches to the GTX 970 just fine. 

Here is the important part of my boot script:
```
cp /usr/share/edk2.git/ovmf-x64/OVMF_VARS-pure-efi.fd /tmp/my_vars.fd

qemu-system-x86_64 \
  -enable-kvm \
  -m 4096 \
  -cpu host,kvm=off \
  -vga none \
  -device vfio-pci,host=02:00.0,multifunction=on \
  -device vfio-pci,host=02:00.1 \
  -device vfio-pci,host=00:1a.0 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -device virtio-scsi-pci,id=scsi \
  -drive file=/media/heiko/tmp_stripe/OS-backup/ISOs/Win7.iso,id=isocd,format=raw,if=none -device scsi-cd,drive=isocd \
  -drive file=/dev/mapper/lm13-win7,cache=none,if=virtio \
  -drive file=/media/heiko/tmp_stripe/OS-backup/ISOs/virtio.iso,id=virtiocd,format=raw,if=none -device ide-cd,bus=ide.1,drive=virtiocd

```

Can anyone point me to the right direction?

---

### Post by heiko_s on 2015-12-23
Following the Windows 7 disaster, I installed Windows 10. It was a breeze. Everything seems to work just fine. Need to run some tests and fine tune. Installation of the latest Nvidia drivers didn't pose a problem. I can boot Windows 10, close and reboot without issues. I just hope it delivers performance wise. Else it will be a real bummer.

I use Windows to work with Lightroom to process photos. I will report back once I have some performance data. I'm curious to see how it performs compared to Xen.

---

### Post by heiko_s on 2015-12-28
Although I did NOT succeed in installing Windows 7 using qemu-kvm, I marked the thread as solved. I can live with Windows 10, and the shorter boot time using the OVMF UEFI boot outweigh the disadvantages of setting up and getting used to Windows 10. Performance-wise I do not notice a difference between Xen and kvm, or between Windows 7 and Windows 10, but I want to run some tests so I can compare.

---

### Post by heiko_s on 2015-12-30
I ran the Passmark 8 benchmarks and discovered a few issues, in particular slow SSD / disk performance. I managed to overcome that by many trials and errors.

For what it's worth, here the VM start command:
```
qemu-system-x86_64 \
  -name $vmname,process=$vmname \
-machine type=q35,accel=kvm \
  -cpu host,kvm=off \
  -smp 10,sockets=1,cores=5,threads=2 \
  -enable-kvm \
  -m 20G \
  -mem-path /dev/hugepages \
  -mem-prealloc \
  -balloon none \
  -rtc clock=host,base=utc \
  -vga none \
  -nographic \
  -serial null \
  -parallel none \
  -device vfio-pci,host=02:00.0,multifunction=on \
  -device vfio-pci,host=02:00.1 \
  -device vfio-pci,host=00:1a.0 \
  -device vfio-pci,host=08:00.0 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=c \
  -device virtio-scsi-pci,id=scsi \
  -drive id=disk0,if=virtio,cache=none,format=raw,file=/dev/mapper/lm13-win10 \
  -drive id=disk1,if=virtio,cache=none,file=/dev/mapper/photos-photo_stripe \
  -drive id=disk2,if=virtio,cache=none,file=/dev/mapper/media-photo_raw \
  -net nic,model=virtio,macaddr=00:16:3e:00:01:02 -net tap
```

Any suggestions for improvements are welcome!

---

### Post by KillerKelvUK on 2015-12-31
Hey, what were the SSD performance issues?  Would be interested if you were to elaborate a little...I'm playing around again with my old GTX 650 i.e. but run all my VM's off SSD.  Way back I had a windows install using LVM but I switched to qcow2 still on SSD and haven't noticed any issues since.  Have you looked at variations of this previous?

---

### Post by heiko_s on 2016-01-01
I got extremely low throughput for my Samsung EVO 850 250GB SSD, see bottom green graph below. The top red graph is a comparison to my Xen VM, but using the "old" and "slower" Sandisk Extreme 120GB SSD.

[IMG]http://www.pbase.com/merhav/image/162215834.jpg[/IMG]

After I applied the -machine type=q35,accel=kvm throughput figures jumped. Here the benchmark:

[IMG]http://www.pbase.com/merhav/image/162222121/large.jpg[/IMG]

Yesterday I reinstalled the entire Windows VM and made sure drivers are all installed, hopefully the correct ones. Now I get ~500 MB/s for sequential read. The benchmark right above was done before the reinstall, but with the q35 option.

I was able to influence the results via different start options, but no option but -machine q35 solved the sequential read issue.


I'm using LVM and I'm not sure about qcow2. LVM allows me to access the Windows partitions from within Linux, in read-write when Windows is off, and read-only when it's running. This is important to me as I use Linux utilities for remote backup. Also, my main system is Linux and I need to access all my data (photos and the occasional video). I'm running two websites where I need to upload photos from time to time. Emails etc. are all done from Linux.

Unless qcow2 can be easily mounted in Linux, it's a no go. Any ideas on that? (I must say I never explored that option.)

---

### Post by KillerKelvUK on 2016-01-03
Wow that's a big difference by changing the machine type, will try that in my vm and see if it reports same improvements (fingers cross).

I use linux as my main/host and I store all my files here, for anything that needs to span OS boundaries  I use a samba server on the host to create network shares so essentially my Windows vm has a mapped drive allowing it access to the files it needs that are stored on the host.  There are tools available that allow the offline management of qcow2 disks but as to whether these will give you the same functionality you have with your current set-up I'm not sure. ([http://libguestfs.org/guestfs-faq.1.html#what-is-libguestfs](http://libguestfs.org/guestfs-faq.1.html#what-is-libguestfs))

I know when I started with lvm virt-manager couldn't then operate with it so it was a manual task creating the xml for libvirt, has that improved now do you know or are you still having to code this in by hand?

---

### Post by heiko_s on 2016-01-06
To be honest, I tried libvirt and virt-manager a year ago and was quite disenchanted, to say it politely. I hate XML - why make things complicated?

In short, I modified my Xen start script and run the guest using qemu-system-x86_64 ... in a batch file. Everything works fine except -runas, which I don't like very much. Right now I start the guest with root privileges, as I haven't got much choice. I believe the issue with runas has to do with privileges, but then I saw on the development mailing list that there is a bug. Don't know.

I wrote a little tutorial for Linux Mint, should work exactly the same for Ubuntu. See [http://forums.linuxmint.com/viewtopic.php?f=231&t=212692&p=1109634#p1109634]("http://forums.linuxmint.com/viewtopic.php?f=231&t=212692&p=1109634#p1109634").

---

