---
title: "LVM encrypted disk &amp; encrypted /home in Lubuntu Vivid complicated or buggy"
date: 2015-02-26
forum: Ubuntu Development Version
---

### Post by sudodus on 2015-02-26
***Encrypted home with cryptswap works again*** :KS

See this bug report, [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

[HR][/HR]
I tested the Lubuntu Vivid beta 1 ***desktop*** ISO file corresponding to the testcase with LVM encrypted disk and encrypted home. It is also reported in the qa-tracker (for Entire Disk).

The computer is an hp Probook 6450b laptop with Intel i5 cpu:

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02218879](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02218879)

Trying to use the whole drive with encrypted LVM and encrypted home, It complained about existing swap (which is zram), so I had to turn it off with

```
sudo swapoff -a
```

and restart Ubiquity. It complained that partman failed:

ubi-partman failed with exit code 141. Further information may be found in /var/log/syslog. Do you want to try ...

The installled system worked, but there is no swap, which is an error.

I ***wiped*** the drive (wrote zeros to the first megabyte using ***mkusb*** (***dd***)) and ***made*** an MSDOS ***partition table*** using ***gparted***.

Then I tried again with Ubiquity, and succeeded: The installed system works, and there is swap.

```
tester@tester-HP-ProBook-6450b:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
tester@tester-HP-ProBook-6450b:~$ uname -a
Linux tester-HP-ProBook-6450b 3.18.0-13-generic #14-Ubuntu SMP Fri Feb 6 09:56:10 UTC 2015 i686 i686 i686 GNU/Linux
tester@tester-HP-ProBook-6450b:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3842        539       3302         54         21        321
-/+ buffers/cache:        196       3646
Swap:         3887          0       3887
tester@tester-HP-ProBook-6450b:~$ sudo lsblk -fm
[sudo] password for tester: 
NAME                     FSTYPE      LABEL UUID                                   MOUNTPOINT NAME                       SIZE OWNER GROUP MODE
sda                                                                                          sda                      111,8G root  disk  brw-rw----
&#9500;&#9472;sda1                   ext2              6b065cac-806b-4331-ba22-e5633b57e68c   /boot      &#9500;&#9472;sda1                     243M root  disk  brw-rw----
&#9500;&#9472;sda2                                                                                       &#9500;&#9472;sda2                       1K root  disk  brw-rw----
&#9492;&#9472;sda5                   crypto_LUKS       ddf9ae0c-df0a-4d73-bf58-c5bf044953c2              &#9492;&#9472;sda5                   111,6G root  disk  brw-rw----
  &#9492;&#9472;sda5_crypt           LVM2_member       msAG9Y-npSX-0olr-20In-bsB5-JY5Y-BrJIpg              &#9492;&#9472;sda5_crypt           111,6G root  disk  brw-rw----
    &#9500;&#9472;lubuntu--vg-root   ext4              768127d4-a05e-4999-8a6f-4af174577ec2   /              &#9500;&#9472;lubuntu--vg-root   107,8G root  disk  brw-rw----
    &#9492;&#9472;lubuntu--vg-swap_1 swap              12781f84-baab-4964-811c-7692e6707c1d   [SWAP]         &#9492;&#9472;lubuntu--vg-swap_1   3,8G root  disk  brw-rw----
sr0                                                                                          sr0                       1024M root  cdrom brw-rw----
tester@tester-HP-ProBook-6450b:~$ 

```

-o-

- Should I report a bug? In that case, against which package?

I have seen threads at our Ubuntu Forums, where people complain about this method (encrypted disk and encrypted home).

- Please test if you have also difficulties with ***other flavours*** of Ubuntu :-)

---

### Post by sudodus on 2015-03-04
See this link

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1425681/comments/12](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1425681/comments/12)

Skipping 'encrypted home inside encrypted disk with LVM' makes things much easier to get working. My tests today indicate, that the Lubuntu
alternate test-case works with this small modification. We need not even unmount any partition earlier than the installer wants to do it.

I just tested that it works with very different original partition tables (GPT and several partitions of various kinds)

- the 64-bit alternate Lubuntu Vivid installer works
- the 32-bit alternate Lubuntu Vivid installer works

in a Toshiba laptop with an Intel i5 processor [http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

I modified the test-cases for encryption only at these places:

***'No' for encrypted home directory*** # Changed from 'Yes'. This is the most important modification.

***'Yes' unmount mounted partitions in the target drive*** # Additional item which is important.

***'No' to install grub boot loader to master boot record. Instead select the target drive for the bootloader manually***. # Changed from 'Yes'. This is optional but I recommend it because the automatic choice often creates problems for me.

Here are the [not yet modified] test-cases:

[Alternate Install (Encryption) in Lubuntu Alternate amd64 for Vivid Daily        ]("http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/90074/testcases/1439/results")
[Alternate Install (Encryption) in Lubuntu Alternate i386 for Vivid Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/90075/testcases/1439/results")

Please test that these test-cases work with the modifications that I suggest above (where ***'No' for encrypted home directory*** is the most important one) :-)

---

### Post by dino99 on 2015-03-04
Sorry but i have no clue about encrypted disk/partition.
But what is the point to encrypt a partition if the LVM disk is already encrypted ?

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> 

Please test that these test-cases work with the modifications that I suggest above (where ***'No' for encrypted home directory*** is the most important one) :-)

Yes .. this is where I had a problem... I will have to try and emulate it, but with Lubuntu.

Regards..

---

### Post by sudodus on 2015-03-04
> **9d9 said:**
> Sorry but i have no clue about encrypted disk/partition.
But what is the point to encrypt a partition if the LVM disk is already encrypted ?

If you want to help, you can simply follow a test-case, and modify it according to my suggestions in post #2.

The point to encrypt home is to hide things from other users of a computer (users that would be allowed to boot into it).

---

### Post by ventrical on 2015-03-04
@sudodus

I downloaded the 32bit alternate from tha qa tracker. Very slow download.

I must apologize but I have been so busy.

  I plan to try and do a test case on this MB [http://www.motherboards.org/mobot/motherboards_d/ASUS/P4S533-E/](http://www.motherboards.org/mobot/motherboards_d/ASUS/P4S533-E/)

which is older 32bit P4 but very robust.

Would you please list a four or five point test case I can try. (I will get back at this later-errands). Or I will just try then what you recommended above in your previous posts.

Regards..

---

### Post by sudodus on 2015-03-04
> **ventrical said:**
> @sudodus

I downloaded the 32bit alternate from tha qa tracker. Very slow download.

I must apologize but I have been so busy.

  I plan to try and do a test case on this MB [http://www.motherboards.org/mobot/motherboards_d/ASUS/P4S533-E/](http://www.motherboards.org/mobot/motherboards_d/ASUS/P4S533-E/)

which is older 32bit P4 but very robust.

Would you please list a four or five point test case I can try. (I will get back at this later-errands). Or I will just try then what you recommended above in your previous posts.

Regards..

Test-cases that I suggest
[HR][/HR]
1. I modified the test-case for encryption only at these places:

***'No' for encrypted home directory*** # Changed from 'Yes'. This is the most important modification.

***'Yes' unmount mounted partitions in the target drive*** # Additional item which is important.

***'No' to install grub boot loader to master boot record. Instead select the target drive for the bootloader manually***. # Changed from 'Yes'. This is optional but I recommend it because the automatic choice often creates problems for me.

Here is the [not yet modified] test-case for the Lubuntu 32bit alternate installer

[Alternate Install (Encryption) in Lubuntu Alternate i386 for Vivid Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/90075/testcases/1439/results")

[HR][/HR]
2. Try the testcase without modifications

I would consider you to be a wizard, if you succeed without any modifications or tweaks. But who knows, you are a very experienced tester :-D

[HR][/HR]
3. Try with encrypted home but without encrypted disks and LVM

Boot several times into the installed system. Check that the cryptswap survives :-P
[HR][/HR]
4. Try with encrypted disk and encrypted home according to the following modifications (with detours to another text screen).

```

When the alternate installer has started, at the screen 'Set up users and
passwords', it is time to modify the partition table.

ctrl+alt+F2

Check drives and partitions:

blkid
df

Unmount if a partition in the target drive is mounted

umount /dev/sdxy  # Maybe this command *here* (early enough) will be enough? No swap :-(

where x is a for the first drive and y is 1 for the first partition

Change:

wget http://phillw.net/isos/linux-tools/small-images/msdos-part-tbl.img
dd if=/dev/zero of=/dev/sdx bs=1024 count=1024  # wipe first Mibibyte
dd if=msdos-part-tbl.img of=/dev/sdx  # MSDOS partition table, no partition
blkid -c /dev/null  # check that it was successful

ctrl+alt+F1

and continue with the installer!
...
Is it enough with only the following? (Maybe sometimes, not always)

If/when the installation stops check at ctrl+alt+F4

If complaints that /dev/sda1 is mounted

ctrl+alt+F2

umount /dev/sda1

ctrl+alt+F1

and continue with the installer
...
Install the bootloader ... answer No
and select it manually

/dev/sdx

and continue. It is close to the finish now.
...
___________________________________________________________

According to the additional commands above, encryption works including
encrypted disk with LVM and encrypted home with cryptswap. But it seems
encrypted swap works only during the first session of the installed system.
After update/upgrade and even after only a simple reboot cryptswap does
not survive, but it is possible to create a 'normal' swap system using the
LVM-mapped swap, and it survives update/upgrade and reboots. This swap is
subject to disk encryption so reasonably safe.

sudo mkswap /dev/mapper/altLubuCrypt--vg-swap_1

and point to it by swapping the comment marks in /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/altLubuCrypt--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=dc48c7d3-53fe-4d73-b1e2-ac9e99f923ad /boot           ext2    defaults        0       2
/dev/mapper/altLubuCrypt--vg-swap_1 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0

Is it an easy or difficult bug, that cryptswap does not survive? If
difficult it might be a good idea to re-design this alternate test-case
for encryption to use only encrypted disk with LVM (not also encrypted
home with cryptswap). Furthermore it would also make the end result similar
to all the Ubuntu flavour desktop test-cases for encryption.

```
[HR][/HR]
5. Try with Lubuntu Vivid 32-bit desktop iso file and the attached very preliminary test-case (a pdf file).

---

### Post by ventrical on 2015-03-04
I will try with older machine first , then perhaps LenvoThinkpad.

Regards..

edit:

notes- grub-install /dev/dm-0 failed

I tried an install with another flavor a couple days ago (without lvm-encrypt) and got the same message.

 I think it is buggy hard ware onold machine or I forgot to disable Plug n' Play :)

 I used test case from qa link . I have to try again before I try your suggest.

Regards..

---

### Post by sudodus on 2015-03-04
I'm looking forward to your results :-)

---

### Post by ventrical on 2015-03-04
Other note:

I chose continue without grub and:

'need to boot manually with the /vmlinuz kernel on partition /dev/mapper/ubuntu--vg-root and root
=/dev/mapper/ubuntu--vg-root passed as a kernel argument'.

edit:

Ok.. just realized that BIOS is reporting that the CD is Master and hdd is slave + bad memory stick so I have to tweak it out :)

---

### Post by sudodus on 2015-03-04
You must enter the device address for the target drive, typically

**/dev/sda**

for the bootloader. Otherwise you will get problems. What I avoid is automatic selection of the target, which often points to the live drive (where I have the installer).

---

### Post by sudodus on 2015-03-04
I tested Lubuntu Vivid 32-bit alternate according to
[HR][/HR]3. Try with encrypted home but without encrypted disks and LVM

Boot several times into the installed system. Check that the cryptswap survives :razz:

[HR][/HR]
Lo and behold, cryptswap disappears also without encrypted disk. It is there when rebooted after installation, but after the next reboot it is gone.

A (new?) bug [IMG]http://iso.qa.ubuntu.com/modules/qatracker/misc/bug.png[/IMG] is found. But how should I report it? Against which package? Can it be confirmed?

---

### Post by sudodus on 2015-03-04
It seems to be an old bug: [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

I found what I think is this bug in a system installed from the Lubuntu Vivid alternate 32-bit daily iso file.

vivid-alternate-i386.iso

cryptswap is there when I reboot from the installer, but the second time I reboot it is gone.

```

/etc/crypttab:
cryptswap1 UUID=b66610ce-376c-42cf-8d02-8983f2a40d70 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

blkid:
/dev/sda1: UUID="63725e48-ebeb-4c33-a023-d34191a6b2bd" TYPE="ext4" PARTUUID="ef7fb1de-01"
/dev/sda5: PARTUUID="ef7fb1de-05"

modified /etc/crypttab:
# <target name>    <source device>        <key file>    <options>
cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

Hint to the developers: It works with the modified crypttab :-)

So it seems that the device information is wrong in /etc/crypttab. Maybe it would be better to have to PARTUUID than the device /dev/sda5.

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> You must enter the device address for the target drive, typically

**/dev/sda**

for the bootloader. Otherwise you will get problems. What I avoid is automatic selection of the target, which often points to the live drive (where I have the installer).


 Still get :

notes- grub-install /dev/dm-0 failed

CentOS 6 installs just perfectly (that was just a test case).

The two test cases I used were from the qa tracker. On this older machine they will not install GRuB .
Thats two fails.


 I'll check your method.

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> Test-cases that I suggest
[HR][/HR]
1. I modified the test-case for encryption only at these places:

***'No' for encrypted home directory*** # Changed from 'Yes'. This is the most important modification.

***'Yes' unmount mounted partitions in the target drive*** # Additional item which is important.

***'No' to install grub boot loader to master boot record. Instead select the target drive for the bootloader manually***. # Changed from 'Yes'. This is optional but I recommend it because the automatic choice often creates problems for me.


But I do not see the option where it will allow to select bootloader manually.... I'm still looking..

---

### Post by ventrical on 2015-03-04
> **ventrical said:**
> But I do not see the option where it will allow to select bootloader manually.... I'm still looking..

Ahhh .. got it ! :) This is a logic bug. In my own case I assume that If I choose 'no' that I will loose my install - it doesn't report at first that I have the option to set the /dev/sda manually. (so it is natual to try again and assume  install is wasted .. and also you can go back and re-install software - so original install is not wasted, hence saving time.

Regards..

---

### Post by ventrical on 2015-03-04
The install went great here after selecting the "NO' grub , then, choose /dev/sda and then it installs grub automatically. This is with the qa test case of  Guided encrypt LVM and home.

During bootup it came up with notice about crypsetup to  Wait, Skip or Manually seledt... I just watied and it booted just fine onto Lubuntu desktop.

```

ventrical@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1019MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.7
          size: 2400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: SiS645DX Host & Memory & AGP Controller
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:d8000000-dbffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:d7000000-d7ffffff memory:e0000000-febfffff
           *-display:0
                description: VGA compatible controller
                product: R300 [Radeon 9500]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:16 memory:f0000000-f7ffffff ioport:d800(size=256) memory:d7800000-d780ffff memory:effe0000-efffffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: R300 [Radeon 9500 PRO] (Secondary)
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:e0000000-e7ffffff memory:d7000000-d700ffff
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2/3 SMBus controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:e600(size=32)
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a400(size=16)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:9 memory:d6000000-d6000fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:21 memory:d5800000-d5800fff
        *-usb:2
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:22 memory:d5000000-d5000fff
        *-usb:3
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32 maxlatency=80
             resources: irq:23 memory:d4800000-d4800fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:e0:18:bb:0f:89
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.27 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
             resources: irq:19 ioport:8800(size=256) memory:d4000000-d4000fff memory:dffc0000-dffdffff
        *-multimedia
             description: Multimedia audio controller
             product: CMI8738/CMI8768 PCI Audio
             vendor: C-Media Electronics Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_cmipci latency=32 maxlatency=24 mingnt=2
             resources: irq:17 ioport:8400(size=256)
     *-scsi
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom:0
             description: DVD reader
             product: DVD-ROM GDR8161B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 0100
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: SCSI CD-ROM
             product: Drive/F5E
             vendor: CD-ROM
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr1
             version: 0.26
             capabilities: removable audio
             configuration: ansiversion=5 status=nodisc
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ventrical@ubuntu:~$ 

```

```

ventrical@ubuntu:~$ uname -a
Linux ubuntu 3.19.0-7-generic #7-Ubuntu SMP Thu Feb 26 20:18:34 UTC 2015 i686 i686 i686 GNU/Linux
ventrical@ubuntu:~$ 
ventrical@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
ventrical@ubuntu:~$ 

```

---

### Post by ventrical on 2015-03-04
..and..

```

ventrical@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        764        236          8         29        403
-/+ buffers/cache:        332        668
Swap:         1023          0       1023
ventrical@ubuntu:~$ sudo lsblk -fm
[sudo] password for ventrical: 
NAME               FSTYPE   LABEL UUID                                   MOUNTPOINT NAME                 SIZE OWNER GROUP MODE
fd0                                                                                 fd0                    4K root  disk  brw-rw----
sda                                                                                 sda                114.5G root  disk  brw-rw----
&#9500;&#9472;sda1             ext2           7fce1a4d-d3ca-4a79-8922-4844a918596a   /boot      &#9500;&#9472;sda1               243M root  disk  brw-rw----
&#9500;&#9472;sda2                                                                              &#9500;&#9472;sda2                 1K root  disk  brw-rw----
&#9492;&#9472;sda5             crypto_L       323a113e-3b22-4d08-9af9-e19d1e4c0425              &#9492;&#9472;sda5             114.3G root  disk  brw-rw----
  &#9492;&#9472;sda5_crypt     LVM2_mem       gW3hu6-JiA5-Xw7l-ihE1-c2Ev-SzRK-0xkuNq              &#9492;&#9472;sda5_crypt     114.3G root  disk  brw-rw----
    &#9500;&#9472;ubuntu--vg-root
                   ext4           55e94774-d9a3-4fc0-bf1a-c492e565ae48   /              &#9500;&#9472;ubuntu--vg-root
                                                                                                       113.3G root  disk  brw-rw----
    &#9492;&#9472;ubuntu--vg-swap_1
                   swap           2bd8098e-69e9-4bdd-9057-4219166957f7                  &#9492;&#9472;ubuntu--vg-swap_1
                                                                                                           1G root  disk  brw-rw----
      &#9492;&#9472;cryptswap1 swap           9cbfa9c4-cb4f-4b52-9ca2-7eeff5026878   [SWAP]           &#9492;&#9472;cryptswap1     1G root  disk  brw-rw----
sr0                                                                                 sr0                 1024M root  cdrom brw-rw----
sr1                                                                                 sr1                 1024M root  cdrom brw-rw----
ventrical@ubuntu:~$ 

```

---

### Post by ventrical on 2015-03-04
Only bug I see (so far) is that vivid-alternate-i386.iso will not automatically detect the target hdd during install of GRub.

Regards..

---

### Post by sudodus on 2015-03-04
Great, it seems to work for you :-)

I agree, the alternate installer is not always easy to understand. Some options are hidden ;-)

What is working for you?

What happens with cryptswap after a second reboot? It is lost for me (as you can see, it seems I'm affected by  [https://bugs.launchpad.net/ubuntu/+s...ls/+bug/953875]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875"))

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> Test-cases that I suggest
[HR][/HR]
1. I modified the test-case for encryption only at these places:

***'No' for encrypted home directory*** # Changed from 'Yes'. This is the most important modification.

***'Yes' unmount mounted partitions in the target drive*** # Additional item which is important.

***'No' to install grub boot loader to master boot record. Instead select the target drive for the bootloader manually***. # Changed from 'Yes'. This is optional but I recommend it because the automatic choice often creates problems for me.

Here is the [not yet modified] test-case for the Lubuntu 32bit alternate installer

[Alternate Install (Encryption) in Lubuntu Alternate i386 for Vivid Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/90075/testcases/1439/results")

[HR][/HR]
2. Try the testcase without modifications

I would consider you to be a wizard, if you succeed without any modifications or tweaks. But who knows, you are a very experienced tester .

I think the main bug is not auto-installing grub to the hdd. The other thing seems to be the message after bootup and after entering passphrase .. it will query, Wait, Skip or manual and , of course , choose wait. Thats it :)

So you had solution to first problem so you are the wizard :) Me? I just waited:) lol

Regards

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> Great, it seems to work for you :-)

I agree, the alternate installer is not always easy to understand. Some options are hidden ;-)

What is working for you?

What happens with cryptswap after a second reboot? It is lost for me (as you can see, it seems I'm affected by  [https://bugs.launchpad.net/ubuntu/+s...ls/+bug/953875]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875"))

oy .. Ok .. will check.

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> Great, it seems to work for you :-)

I agree, the alternate installer is not always easy to understand. Some options are hidden ;-)

What is working for you?

What happens with cryptswap after a second reboot? It is lost for me (as you can see, it seems I'm affected by  [https://bugs.launchpad.net/ubuntu/+s...ls/+bug/953875]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875"))

Every second boot!

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> I tested Lubuntu Vivid 32-bit alternate according to
[HR][/HR]3. Try with encrypted home but without encrypted disks and LVM

Boot several times into the installed system. Check that the cryptswap survives :razz:

[HR][/HR]
Lo and behold, cryptswap disappears also without encrypted disk. It is there when rebooted after installation, but after the next reboot it is gone.

A (new?) bug [IMG]http://iso.qa.ubuntu.com/modules/qatracker/misc/bug.png[/IMG] is found. But how should I report it? Against which package? Can it be confirmed?

Yes .. I can confirm every second boot I can get a working encrypted desktop. Otherwise I get blackscreen and no response to keyboard input.

---

### Post by sudodus on 2015-03-04
> **ventrical said:**
> Yes .. I can confirm every second boot I can get a working encrypted desktop. Otherwise I get blackscreen and no response to keyboard input.

So it works in an old computer with Intel(R) Pentium(R) 4 CPU 2.40GHz but not in my Toshiba with Intel i5.

What could cause the difference?

I have an old Dell with Intel(R) Pentium(R) 4 CPU 2.8 GHz. I'll test in that computer.

Edit: Did you check for cryptswap? You can also check with

```
swapon -s
```

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> So it works in an old computer with Intel(R) Pentium(R) 4 CPU 2.40GHz but not in my Toshiba with Intel i5.

What could cause the difference?

I have an old Dell with Intel(R) Pentium(R) 4 CPU 2.8 GHz. I'll test in that computer.

Edit: Did you check for cryptswap? You can also check with

```
swapon -s
```

cryptswap comes up on the opening logon after I enter passphrase. It tells me that it cannot find cryptswap and queries , Wait, Skip, Manual.. I just wait and it boots up ... but I tired your code:

```

swapon -s

```

and it reported  nothing but it's there.

---

### Post by ventrical on 2015-03-04
I am making a loose assumption that there is somthing in the grub.conf file that is causing this (or one of the grub files) because of the way every second boot to get a login.

---

### Post by ventrical on 2015-03-04
Not there..

```

ventrical@ubuntu:~$ swapon -a
swapon: stat failed /dev/mapper/cryptswap1: No such file or directory
ventrical@ubuntu:~$ 

```

---

### Post by sudodus on 2015-03-04
Interesting that every second boot gets a login. What if you try the fix from post #13

```
modified /etc/crypttab:
# <target name>    <source device>        <key file>    <options>
cryptswap1 [COLOR=#ff0000]/dev/sda5[/COLOR] /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> Interesting that every second boot gets a login. What if you try the fix from post #13

```
modified /etc/crypttab:
# <target name>    <source device>        <key file>    <options>
cryptswap1 [COLOR=#ff0000]/dev/sda5[/COLOR] /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```

You mean completely overwrite:

```

sda5_crypt UUID=323a113e-3b22-4d08-9af9-e19d1e4c0425 none luks,discard
cryptswap1 UUID=2bd8098e-69e9-4bdd-9057-4219166957f7 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

with the  above you suggested?

---

### Post by sudodus on 2015-03-04
[TABLE]
[TR]
[TD]John Hupp suggested:[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD][syscon-hh (syscon-kono)]("https://launchpad.net/%7Esyscon-kono")             wrote             on 2014-04-20:[/TD]
[TD="class: bug-comment-index"]           [ #3]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/comments/3")[/TD]
[/TR]
[/TABLE]
                               A possible workaround inside the script "/usr/bin/ecryptfs-setup-swap" could be:

 ```
# Add crypttab entry

  echo "cryptswap$i UUID=$uuid /dev/urandom swap,offset=8,cipher=aes-cbc-essiv:sha256" >> /etc/crypttab
```

 Please test the supplement "offset=8" as a sufficient space to avoid the UUID will be overwritten.

 Alternativily it should be tested to use the Option "skip" instead.

(I haven't tried it yet.)

---

### Post by ventrical on 2015-03-04
I'll get at it later :)

Regards..

---

### Post by sudodus on 2015-03-04
> **ventrical said:**
> You mean completely overwrite:

```

sda5_crypt UUID=323a113e-3b22-4d08-9af9-e19d1e4c0425 none luks,discard
cryptswap1 UUID=2bd8098e-69e9-4bdd-9057-4219166957f7 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

with the  above you suggested?

I have only one comment line and one used line in /etc/crypttab, your second line, and I would replace UUID=2bd8098e-69e9-4bdd-9057-4219166957f7 with the current device. In my case /dev/sda5 works, but if it is on sdc, it should be /dev/sdc5. I think the method by *syscon-hh* is general (and portable).

---

### Post by ventrical on 2015-03-04
> **sudodus said:**
> I have only one comment line and one used line in /etc/crypttab, your second line, and I would replace UUID=2bd8098e-69e9-4bdd-9057-4219166957f7 with the current device. In my case /dev/sda5 works, but if it is on sdc, it should be /dev/sdc5. I think the method by *syscon-hh* is general (and portable).

I did your method. Same thing. Every second boot. No cryptswap still.

---

### Post by sudodus on 2015-03-05
I tested in my old Dell with Intel(R) Pentium(R) 4 CPU 2.8 GHz. And I had the same result as in my Toshiba with Intel i5. It boots to a working session (I can log in and run every time), but cryptswap works only the first time in the installed system. After the next reboot it is gone.

I tried and it seems to me, that the supplement "offset=8" should be added to the line in **/etc/crypttab**. It would be a working bug-fix for ***ecryptfs-setup-swap*** in the package ***ecryptfs-utils***.

For the record I remind of what John Hupp suggested in comment #37 [of the bug report 953875]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875"):

[TABLE="class: cms_table"]
[TR]
[TD][syscon-hh (syscon-kono)]("https://launchpad.net/%7Esyscon-kono")             wrote             on 2014-04-20:[/TD]
[TD="class: cms_table_bug-comment-index"]           [#3 of the bug report 1310058 ]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/comments/3")[/TD]
[/TR]
[/TABLE]

It is too late to edit /etc/crypttab. Instead the script to set up cryptswap should be changed (add the option **offset=8**)

> A possible workaround inside the script "/usr/bin/ecryptfs-setup-swap" could be:

 *******
# Add crypttab entry
  echo "cryptswap$i UUID=$uuid /dev/urandom swap,offset=8,cipher=aes-cbc-essiv:sha256" >> /etc/crypttab
*******
 Please test the supplement "offset=8" as a sufficient space to avoid the UUID will be overwritten.


This works for me :-)

See the whole bug report 1310058 [ecryptfs-setup-swap hints after reboot]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/")

---

### Post by ventrical on 2015-03-05
> **sudodus said:**
> I tested in my old Dell with Intel(R) Pentium(R) 4 CPU 2.8 GHz. And I had the same result as in my Toshiba with Intel i5. It boots to a working session (I can log in and run every time), but cryptswap works only the first time in the installed system. After the next reboot it is gone.

I tried and it seems to me, that the supplement "offset=8" should be added to the line in **/etc/crypttab**. It would be a working bug-fix for ***ecryptfs-setup-swap*** in the package ***ecryptfs-utils***.

For the record I remind of what John Hupp suggested in comment #37 [of the bug report 953875]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875"):

[TABLE="class: cms_table"]
[TR]
[TD][syscon-hh (syscon-kono)]("https://launchpad.net/%7Esyscon-kono")             wrote             on 2014-04-20:[/TD]
[TD="class: cms_table_bug-comment-index"]           [#3 of the bug report 1310058 ]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/comments/3")[/TD]
[/TR]
[/TABLE]

It is too late to edit /etc/crypttab. Instead the script to set up cryptswap should be changed (add the option **offset=8**)



This works for me :-)

See the whole bug report 1310058 [ecryptfs-setup-swap hints after reboot]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/")


> A possible workaround inside the script "/usr/bin/ecryptfs-setup-swap" could be:

 *******
# Add crypttab entry
  echo "cryptswap$i UUID=$uuid /dev/urandom swap,offset=8,cipher=aes-cbc-essiv:sha256" >> /etc/crypttab
*******
 Please test the supplement "offset=8" as a sufficient space to avoid the UUID will be overwritten. 

But here again we have insufficient information for other users. For example. "cryptswap$i UUID=$uuid". Does he mean to enter that exactly as it is  or does the  ($uuid) mean the actual uuid ?? because in programming (older) the $ character would equal a value and I assume it is the actual uuid. Also because I had changed my UUID to /dev/sda5 as suggested. So do I need to convert back to original uuid?

So my question is .. did you paste it to "/usr/bin/ecryptfs-setup-swap" as is, or did you have the actual uuid numbers ??

Regards..

---

### Post by sudodus on 2015-03-05
> **ventrical said:**
> But here again we have insufficient information for other users. For example. "cryptswap$i UUID=$uuid". Does he mean to enter that exactly as it is  or does the  ($uuid) mean the actual uuid ?? because in programming (older) the $ character would equal a value and I assume it is the actual uuid. Also because I had changed my UUID to /dev/sda5 as suggested. So do I need to convert back to original uuid?

So my question is .. did you paste it to "/usr/bin/ecryptfs-setup-swap" as is, or did you have the actual uuid numbers ??

Regards..

I 'pasted it as is' or actually added **offset=8** to the relevant line, with the shell variables, which work in the shell-script ***ecryptfs-setup-swap***

Then I recreated swap with ***mkswap***, modified the swap entry in **/etc/fstab** to match it and ran ***ecryptfs-setup-swap***

After that I have a persistent cryptswap. It survives reboots :-)

---

### Post by sudodus on 2015-03-05
I think the following text will be used for the modified test-cases for Lubuntu alternate i386 and amd64 installers.

```

Alternate Install (Encryption) in Lubuntu Alternate i386 for Utopic Daily (archived)
You are currently on: Ubuntu ISO Testing

DownloadLink to the download information
Alternate Install (Encryption)Detailed information on the testcase
Hide Testcase

Proceed in your native language if you wish. Instructions will remain in English

Boot up the image
    System boots to 'Select Language'
Select Install Ubuntu and press Enter
    System displays 'Select Location'
Select location and press Enter
    The default for your location and language should already be selected.
Select the layout you wish to use on the keyboard and press Enter
    The default for your location and language should already be selected.
Add a hostname for the machine and press Enter
    You should be prompted for your name
Type in your name and press Enter
    You should be prompted for a user name
Type in your user name and press Enter (you can accept the default if you wish).
    You should be prompted to enter a password
Add a password and press Enter
    You should be prompted to confirm ( If you entered a weak password, confirm that you want to keep it or select no and enter a stronger one).
Confirm password and press Enter
    You should be asked if you wish to encrypt your home directory
Select [No] for encrypted home directory and press Enter  # Changed from yes to no
    You should see confirmation of your time zone
Verify that the pre-selected time zone is correct or select your time zone and press Enter
    You may be informed that 'the following disks have mounted partitions'. If the intended target drive is affected, you must
Select 'Yes' to unmount partitions that are in use  # New dialogue screen
    You are informed that your installation medium is ... and what you can and cannot do with that drive.
'Continue'  # New dialogue screen
    You will be presented with formatting options
Select Guided - use entire disk and set up encrypted LVM and press Enter
    You should see an option to select a disk to install on
Select the disk to use and press Enter
    You should be asked to confirm the action
Select Yes to accept the changes and press Enter
    You should be asked to enter an encryption passphrase
Enter an encryption passphrase and press Enter
    You should be asked to confirm your passphrase
Confirm your encryption passphrase by entering it again and press Enter
    You should be asked to specify an amount of the volume group to use for guided partitioning
Specify an amount of the volume group to use for guided partitioning and press Enter
    You should see a request to confirm writing the changes to disk
Select Yes to accept the changes and press Enter
    You should see a request for http proxy information
Input http proxy info or press Enter
    Wait for a while - The install may seem like it has locked at a percentage but is actually working in the background. You can check and see if it is working by switching to tty4 (ctrl + alt + f4).

Select 'No' to install grub boot loader and select it manually. # Changed from yes to no
Enter /dev/sdx
where x is the target drive letter (often a) and continue.

    You should see a request to confirm date and time
Select Yes to setting your clock to utc and press Enter
    You should be requested to remove the CD / USB key
Remove the CD / USB key and press Enter
    This should then reboot the machine
Log in and check the desktop is installed
    You should be able to log in and the desktop should be displayed
Ask the machine to reboot
    Machine should reboot
Login and check the system installed correctly
    Menus should be displayed

If all actions produce the expected results listed, please submit a 'passed' result.
If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.

```

***Edit***: It will be marked up with high-lighting, links etc. and the comment text after # removed.

---

### Post by ventrical on 2015-03-05
> 
Select Yes to accept the changes and press Enter
    You should see a request for http proxy information

***Leave empty for none. That means do not put any info in the dialog box. Hit the tab key to 
highlight <continue> and press <Enter>***

Input http proxy info or press Enter
    Wait for a while - The install may seem like it has locked at a percentage but is actually working in the background. You can check and see if it is working by switching to tty4 (ctrl + alt + f4).

Select 'No' to install grub boot loader. *** A dialog box with your partition information will
come up and you can choose target drive from there.*** and select it manually. # Changed from yes to no
Enter /dev/sdx
where x is the target drive letter (often a) and continue.



  I filled in some addendums with *** ... ***

Regards..

---

### Post by sudodus on 2015-03-05
I sent a mail with you suggestions to Lars Noodén, who is editing the testcases via bazaar now :-)

---

### Post by Elfy on 2015-03-05
waiting on a testcase admin now ...

---

### Post by ventrical on 2015-03-05
> **Elfy said:**
> waiting on a testcase admin now ...

> 
 			 				Select Yes to accept the changes and press Enter
    You should see a request for http proxy information

***Leave empty for none. That means do not put any info in the dialog box. Hit the tab key to 
highlight <continue> and press <Enter>***

Input http proxy info or press Enter
    Wait for a while - The install may seem like it has locked at a  percentage but is actually working in the background. You can check and  see if it is working by switching to tty4 (ctrl + alt + f4).

Select 'No' to install grub boot loader. *** A dialog box with your partition information will
come up and you can choose target drive from there.*** and select it manually. # Changed from yes to no
Enter /dev/sdx
where x is the target drive letter (often a) and continue.

  I just thought that the <Select no to install grub loader> can lead some astray at first , without an explanation. There is :
1. A natural tendency to install grub anyways, fail or no fail.
2. That it is assumed that the installer will finish without installing grub (as it is not made immediately clear after choosing not to install grub that the option to select a disk is offered - so there is a logic hole presented in the dialog content.

Thanks all of you.

Regards..

---

### Post by sudodus on 2015-03-05
I agree, ventrical. 

We try to cover up for that in the test-case instructions. But the general long-term solution is to improve the dialogue in the alternate installer (and I guess in the similar installers for Ubuntu Server and Ubuntu mini.iso). And it would be a good idea to create a bug report for it (or if it fits into an existing bug report, to add it there).

*Edit*: It would be even better, if enough developer work could be focused on the alternate installer, so that the automatic selection of target for the bootloader would work well. But one of the cryptswap bug reports is from March 2012, and that might have higher priority ...

---

### Post by ventrical on 2015-03-05
Thanks sudodus.

It is extremely important to have a working, coherent and comprehensive alternate.iso (such as that we have been testing) because there is a trend for younger students to work with older hardware and be able to have some rock solid form factors to experiment on. It is equally important the instructional content be clear, concise and succinct covering all of the possible loops and supposition errors. White hot programming inspiration is too difficult to deploy on phones and tablets. They are more analgolus to executive toy playthings and not rock solid desktop terminals which will always be in demand. There is a large market for older hardware/desktops for noobs and experimenters. And a lot of that older hardware has virtual features that newer hardware does not always have. What better OS to use as a benchmarker than Lubuntu alternate.

Regards..

---

### Post by sudodus on 2015-03-06
Thanks ventrical,

I'll post a copy of and a link to your post (#44) in the Lubuntu mailing lists for inspiration :-)

---

### Post by ventrical on 2015-03-06
:)

---

### Post by sudodus on 2015-03-06
[COLOR=#4b0082]**[B]*Edit***:[/B] This method was broken by fixes to  make it work without cryptswap with systemd (tested March 11, 2015). I tried with offset=1024,  but it did not help. Something else is also broken :sad:  I tested if the method at the very end of the post works, but failed both with 'Encrypted disk with LVM', and when used alone,  in other words when the only encryption is 'Encrypted home'.[/COLOR][HR][/HR]**Warning: this method is neither convenient nor safe **- long commands must be typed into a text screen, and those commands will overwrite the partition table. But if you really want both kinds of encryption it might be worth the effort, and if you have only one drive in the computer (except the installer on CD/DVD/USB) you can relax :-)
[HR][/HR][I][B]
Lubuntu alternate installer - with some tweaks is it possible to install a system with 'encrypted disk' and 'encrypted home'[/B][/I]

When the alternate installer has started, at the screen 'Set up users and passwords', it is time to modify the partition table.
[B][I]
ctrl+alt+F2[/I][/B]

Check drives and partitions:

```
blkid
df
```

***Unmount*** if a partition in the target drive is mounted:

```
[SIZE=3]umount /dev/sdxy[/SIZE]
```

where x is a for the first drive and y is 1 for the first partition, typically /dev/sda1

***Change*** the partition table:

```
[SIZE=3]wget http://phillw.net/isos/linux-tools/small-images/msdos-part-tbl.img

dd if=/dev/zero of=/dev/sdx bs=1024 count=1024  # wipe first Mibibyte

dd if=msdos-part-tbl.img of=/dev/sdx  # MSDOS partition table, no partition

blkid -c /dev/null  # check that it was successful[/SIZE]
```

***ctrl+alt+F1***

and continue with the installer!
...
...
...
***Install the bootloader*** ... answer ***No***
and select it manually

**/dev/sdx**

where x is the drive letter, where you want to install the bootloader, often the same drive as you installed Lubuntu, typically a (/dev/sda)

and continue. It is close to the finish now.
...


[HR][/HR]
With the additional commands above, encryption works including encrypted  disk with LVM and encrypted home with cryptswap. But it seems encrypted  swap works only during the first session of the installed system. After  only a simple reboot cryptswap does not survive, but it is possible to  create a 'normal' swap system using the LVM-mapped swap, and it survives  update/upgrade and reboots. This swap is subject to disk encryption so  reasonably safe except for other users with their own user ID in the  same computer.


[HR][/HR][I][B]
This creates 'normal swap inside the encrypted disk'[/B][/I]

Identify the swap mapper and use it with mkswap. I used the computer  name altLubuCrypt, which is part of the swap mapper device name.
```
sudo blkid
sudo mkswap /dev/mapper/altLubuCrypt--vg-swap_1
```

and point to it by swapping the comment marks in /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/altLubuCrypt--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=dc48c7d3-53fe-4d73-b1e2-ac9e99f923ad /boot           ext2    defaults        0       2
/dev/mapper/altLubuCrypt--vg-swap_1 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
```

[HR][/HR]
***This creates encrypted swap*** and protects against other users with their own user ID in the same computer.

There is a fix, that can make the installed cryptswap survive. You must [COLOR=#ff0000]***do it the first time you start the installed system***[/COLOR], that is while cryptswap is still alive.

Add the option offset=8 to the file /etc/crypttab:

```
[SIZE=3]sudo sed -i s/,cipher=/,offset=8,cipher=/ /etc/crypttab[/SIZE]
```

[HR][/HR]
Don't get me wrong. I read the bug report [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1310058]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058"), and I see that there are many comments that point forward to squashing the bug.

**Disclaimer: **This post describes a work-around method that works today with  Lubuntu Vivid. It does not contain what will be used to squash the bug.
[HR][/HR]
[COLOR=#4b0082]***Edit***: The method above was broken by fixes to make it work without cryptswap with systemd (tested March 11, 2015). I tried with offset=1024, but it did not help. Something else is also broken :-( [COLOR=#4b0082]I tested if the method at the very end of the post  works, but failed both with 'Encrypted disk with LVM', and when used  alone,  in other words when the only encryption is 'Encrypted home'.[/COLOR][/COLOR]
> ** Branch linked: lp:~ubuntu-branches/ubuntu/vivid/ecryptfs-utils/vivid-proposed

-- You received this bug notification because you are subscribed to the bug report.
[https://bugs.launchpad.net/bugs/953875](https://bugs.launchpad.net/bugs/953875)

Title: Encrypted swap no longer mounted at bootup Status in eCryptfs: Fix Released

Status in ecryptfs-utils package in Ubuntu: Fix Committed

Status in ecryptfs-utils source package in Vivid: Fix Committed

Bug description: SUMMARY
=======
During installation with "encrypt my home folder" mode, a broken /etc/crypttab gets created which defines a non-existing swap device (usually "cryptswap1") with a UUID. This will also be put into /etc/fstab. As after installation the UUID does not exist, such systems don't have any actual swap.

UPGRADE FIX
===========
An upgrade to Ubuntu 15.04 ("vivid") will detect and comment out these broken swap devices from /etc/fstab and /etc/crypttab. If you actually want to use those, do these steps:

- Find the swap device that was meant to be used in "sudo fdisk -l" (it should say "Linux swap" in the last column), remember the device name (something like "/dev/sda5")

- Find the UUID in /etc/crypttab (the long alphanumeric ID after UUID=)

- Run "sudo mkswap -U 1234... /dev/sda5", replacing "1234" with the above UUID, and /dev/sda5 with the device name from step 1.

- Edit /etc/crypttab to append ",offset=1024" in the fourth (last) column of the cryptswap1 line; ensure that there is *no space* between the "cipher=aes-cbc-essiv:sha256" and the appended option. If there is a leading "#" in the file, remove that too.

- If there is a leading "#" in /etc/fstab in the line starting with /dev/mapper/cryptswap1 line, remove that.

- Run "sudo update-initramfs -u".

---

### Post by sudodus on 2015-03-07
> **Elfy said:**
> waiting on a testcase admin now ...

Elfy, are you satisfied with the changes to the alternate testcase now? Will there be another discussion and edits with the testcase admin? When can we expect the modified testcase to be available via the QA tracker? I hope it is possible to get it within a week from now ;-)

---

### Post by Elfy on 2015-03-07
It's waiting for Lars not me ;)

The plot has also thickened ...

---

### Post by sudodus on 2015-03-09
Martin Pitt has started to solve the problems with cryptswap for 'Encrypted home'. Maybe our activities made a difference, but I think a complication with systemd made the situation acute, and created a need for at least a simple fix:

See post #39 and following in this bug report

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

'This is a lot worse now that systemd actually complains about the missing device and blocks the boot on it for 90s.'

For some reason he suggests a bigger offset (8-->1024), maybe because it increases the speed?

---

### Post by ventrical on 2015-03-09
> **sudodus said:**
> Martin Pitt has started to solve the problems with cryptswap for 'Encrypted home'. Maybe our activities made a difference, but I think a complication with systemd made the situation acute, and created a need for at least a simple fix:

See post #39 and following in this bug report

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

'This is a lot worse now that systemd actually complains about the missing device and blocks the boot on it for 90s.'

For some reason he suggests a bigger offset (8-->1024), maybe because it increases the speed?

Interesting .. I'm just catching up...

---

### Post by sudodus on 2015-03-12
[SIZE=4]'Encrypted disk' and '[/SIZE][SIZE=4][SIZE=4]Encrypted /home' work together in Lubuntu 14.04.1 LTS[/SIZE]

[/SIZE]Cryptswap for 'Encrypted home' in 'Encrypted disk' works in the ***Lubuntu desktop installer*** according to the following instructions.

```

# Setting up cryptswap for 'Encrypted home' in 'Encrypted disk'
# in the Lubuntu desktop installer

# ***tested in 14.04.1 LTS - works :-)***
# tested in 14.04.2 LTS - does not survive reboots
# tested in Vivid - does not survive reboots (running ***initramfs*** according to the end of post #47 makes the boot stop in Busybox)

# Run in the live session before running the installer

sudo swapon -s
sudo swapoff -a
sudo swapon -s

# Run the installer with 'Encrypted disk' and 'Encrypted home'

# Run in the installed system after reboot

sudo lsblk -fm              # overview in maximized terminal window
sudo swapon -s              # probably no active swap, otherwise swapoff
grep swap /etc/fstab        # inspect the swap lines in fstab
# the lubuntu--vg-swap_1 entry should be active (not preceded by #)
sudo nano /etc/fstab        # edit if necessary
sudo swapoff -a

sudo mkswap /dev/mapper/lubuntu--vg-swap_1   # identify and select target

sudo swapon /dev/mapper/lubuntu--vg-swap_1
sudo swapon -s              # optional (check that swap works)

# Automatic editing:
sudo sed -i s/,cipher=/,offset=1024,cipher=/ /usr/bin/ecryptfs-setup-swap

# Manual editing (alternative, not necessary after automatic editing)
sudo nano /usr/bin/ecryptfs-setup-swap       # add the option offset=1024
# See the link
# https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1310058/comments/3

sudo /usr/bin/ecryptfs-setup-swap  # maybe confusing output, but works

sudo blkid                  # optional (check)

sudo mv /etc/crypttab /etc/crypttab.tmp
sudo bash -c 'tail -n1 /etc/crypttab.tmp > /etc/crypttab'  # only one line

 
# Edit so the 'cryptswap' is active but not 'lubuntu--vg-swap_1'
# and there should be only one line with 'cryptswap' in fstab

sudo nano /etc/fstab  # important !!!

sudo reboot  # Reboot and check that cryptswap works

sudo swapon -a  # maybe turn on cryptswap manually even when it is in /etc/fstab

```

---

### Post by sudodus on 2015-03-12
[COLOR=#4b0082]I tested in Lubuntu Vivid desktop if the method at the very end of the post #47 works, but it failed both with 'Encrypted disk with LVM', and when used  alone,  in other words when the only encryption is 'Encrypted home'.[/COLOR]

I also tested (in Vivid) variations of the commands between those of post #47 and post #52, but without success. I can make the cryptswap survive the first reboot, but not after that.

***Encrypted home seems really badly broken in Vivid*** (at least in Lubuntu Vivid).

---

### Post by sudodus on 2015-03-16
I have to wait for a  loooooooooooooooong time (90 seconds), but after that I can ***re-create cryptswap*** with the following script in Lubuntu Vivid i386 daily build (installed with the desktop installer). This cryptswap works only once, and must be re-created after reboot.

```
#!/bin/bash

swpdev=$(grep '# swap was on' /etc/fstab|cut -d ' ' -f 5)
uuid=$(cut -d ' ' -f 2 /etc/crypttab |cut -d = -f 2)
sudo mkswap -U "$uuid" "$swpdev"
sudo blkid -c /dev/null
sudo swapon -a
sudo swapon -s
```

---

### Post by ventrical on 2015-03-16
Hi Sudodus.

 I do not mean to be picky , but,

> 
Encrypted disk and Encrypted home work together in Lubuntu 14.04.1 LTS


makes me think of 'homework' when I first read it. Could I kindly suggest that you put a '/' before home as in /home?

Thanks 
Regards..

---

### Post by sudodus on 2015-03-16
Well, if it makes you happy, I'll edit the title too :-D

By the way, it would be nice if you can ***test 'Encrypted /home' with another flavour*** (not Lubuntu) to check if the problem affects only Lubuntu or all flavours.

---

### Post by ventrical on 2015-03-16
> **sudodus said:**
> Well, if it makes you happy, I'll edit the title too :-D

By the way, it would be nice if you can ***test 'Encrypted /home' with another flavour*** (not Lubuntu) to check if the problem affects only Lubuntu or all flavours.

:) ... ok... I'm not trying to be picky ... I am happy with all ubuntus:)

Lots of work still .. will check xubuntu for encrypt of /home. It is the most stable of the pack from a testing standpoint ..

Regards..

---

### Post by ventrical on 2015-03-16
I am here so far:

edit:

It would not allow me to untic encrypt LVM. It locked in.

---

### Post by ventrical on 2015-03-16
It appears to be systemic.

---

### Post by ventrical on 2015-03-16
and..

---

### Post by sudodus on 2015-03-17
Nice that you tried Xubuntu :-)

0. Did you try Vivid daily?

1. I guess that the home folder was encrypted like it should.

2. I conclude that cryptswap failed (the 'Swap not available' message in post #59).

3. Did you try any tweaks, or did you 'only' run according to what is available in the installer?

---

### Post by ventrical on 2015-03-17
> **sudodus said:**
> Nice that you tried Xubuntu :-)

0. Did you try Vivid daily?

1. I guess that the home folder was encrypted like it should.

2. I conclude that cryptswap failed (the 'Swap not available' message in post #59).

3. Did you try any tweaks, or did you 'only' run according to what is available in the installer?

No tweaks. Vivid xubuntu/daily-live/current/  .

  I may completely delete that hdd and try again  with all partitions removed. I usually do not have any problems with xubuntu - so perhaps it may be something that I did or did not do.

> 
2. I conclude that cryptswap failed (the 'Swap not available' message in post #59).


I tired some of your codes but  was called away to errands (so could not complete). One note- as it did not present the Fix.skip,manual option after bootup.



Regards..

---

### Post by sudodus on 2015-04-19
***Encrypted home with cryptswap works again.***

See this bug report, [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

ISO testing result for Lubuntu Vivid

 [http://iso.qa.ubuntu.com/qatracker/milestones/338/builds/92211/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/338/builds/92211/testcases/1439/results)
 step 1 OK: cryptswap works when rebooting after installation.
step 2 OK: no long delay when rebooting again.
step 3 OK: cryptswap works when rebooting again. I provoked using swap, and it seems to work correctly.
step 4 OK: cryptswap works when rebooting again. I provoked using swap, and it seems to work correctly.

 Encrypted home with cryptswap works again. Thank you Martin Pitt :smile:

---

