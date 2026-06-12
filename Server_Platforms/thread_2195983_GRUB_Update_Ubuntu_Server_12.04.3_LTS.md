---
title: "GRUB Update Ubuntu Server 12.04.3 LTS"
date: 2013-12-27
forum: Server Platforms
---

### Post by thufirhawat2 on 2013-12-27
I am a linux dabbler, and by no means an expert, so I apologize if this is a very simple/paranoid question. 

I built a headless NAS about a year ago now with ubuntu precise pangolin, and I originally set it up with 2 X 2TB hard drives using mdadm for RAID1. When I installed the OS, it asked if I would still want to boot after a degraded array event, i.e. a drive goes bad, do you still want the server to boot. I chose yes, as I want to be able to boot and backup my data before attempting repairs.

I have a virtual machine I set up with virtualbox that is in every way identical to my production machine, except the 2 virtual hard drives are 100GB instead of 2TB. I try to update my machine once a week or so, and I test new software and new updates on my virtual machine before updating the production machine, pretty standard practice.

Today, I updated my virtual server and there was a GRUB update. It popped up and said something about the disk GRUB was installed on is no longer available or has a different identifier, which disk(s) did I want to install GRUB on? I chose both hard drives and the RAID array (md0), which were all the options I had. I assume this is how the machine is able to still boot in a degraded RAID array state? However, I was concerned with the message I received during the upgrade install, particularly what I highlighted red. See the code below.

After the upgrade, the virtual server rebooted fine, so I shut it down, took a snapshot, and removed one of the virtual disks to simulate a drive failure. The machine booted and seemed to function fine. I restored everything, and then simulated failing the other virtual disk, everything seemed to boot and function just fine. So I guess I am just being paranoid, but I wanted to check with some of the linux Jedi on here to make sure that my choosing the array (md0) and both of my disks to install GRUB to was the best course of action, (as the output from the install seems to indicate that maybe it wasn't) before I upgrade my production machine. Thanks!

```
Setting up grub-common (1.99-21ubuntu3.14) ...Installing new version of config file /etc/grub.d/00_header ...
Installing new version of config file /etc/grub.d/20_linux_xen ...
Installing new version of config file /etc/grub.d/10_linux ...
Installing new version of config file /etc/grub.d/30_os-prober ...
Setting up grub2-common (1.99-21ubuntu3.14) ...
Setting up grub-pc-bin (1.99-21ubuntu3.14) ...
Setting up grub-pc (1.99-21ubuntu3.14) ...
Installation finished. No error reported.
Installation finished. No error reported.
[COLOR=#ff0000]/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..[/COLOR]
[COLOR=#ff0000]/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..[/COLOR]
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by oldfred on 2013-12-27
Not sure with vitual or RAID but that error is when you try to force grub to install to a partition like sda1 not a drive. Or a drive's MBR when first partition starts too close to MBR. Normal partitions used to start at sector 63 and new one's now start at sector 2048 for alignment with large 4K drives and SSDs. May also occur with gpt drives without bios_grub partition.
So in your virtual install where does grub normally instal?

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by thufirhawat2 on 2013-12-27
Below is the output of the commands you gave me. What I have highlighted in red is I assume the two hard drives it sees, with some kind of presumably system generated identifier. The second command indicates to me that grub is installed directly on the RAID array (md0). Thinking back, I believe I installed grub to the root of md0 when it asked me where to install it, and then it prompted and asked if I wanted to boot in the event of a degraded array and I said yes. 

I always assumed that that meant GRUB would be installed on the array (md0) and on each of the hard drive disks. That way, the system would boot from md0 normally, but then if the array degraded due to a HDD failure, it would instead boot from whichever HDD survived. I never really considered it that much, that was just a quick assumption I made about how it worked and is probably wrong considering I do not know a whole lot about GRUB. 

Does this information give anyone any ideas on what might have happened, and what options I should select for my production server? I could kick myself for not saving my pre-upgrade snapshot, (wasn't thinking) but I have a backup of the VM I guess I could restore and, by process of elimination, determine the optimal way to install the update without encountering that disconcerting message and retaining the functionality I want, but I usually just ask smart people if they happen to have a quick answer first before I do a lot of leg work. Thanks so much for your reply!


```
cody@testserver:~$ sudo debconf-show grub-pc[sudo] password for cody:
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-[COLOR=#ff0000]VBOX_HARDDISK_VB258785d9-c3017482, /dev/disk/by-id/ata-VBOX_HARDDISK_VB379631e0-59eb9680[/COLOR], /dev/disk/by-id/md-name-testserver:0
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
* grub-pc/install_devices_disks_changed: /dev/disk/by-id/ata-[COLOR=#ff0000]VBOX_HARDDISK_VB258785d9-c3017482, /dev/disk/by-id/ata-VBOX_HARDDISK_VB379631e0-59eb9680[/COLOR], /dev/disk/by-id/md-name-testserver:0
* grub2/linux_cmdline_default:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 2
cody@testserver:~$ sudo grub-probe -t device /boot/grub
/dev/md0

```

---

### Post by oldfred on 2013-12-27
It looks like it is showing two places, what is the second?
Not knowing virtual installs is that normal?

---

### Post by thufirhawat2 on 2013-12-30
Ok, so I think I know what happened.... sort of.

I restored a backup of my virtual machine and reran the upgrade, selecting only the RAID array as the installation directory for GRUB, and received the same warning about that being a bad idea. I tested the functionality after degrading the array, and there were no problems. I then restored a snapshot and reran the upgrade selecting only the two partitions (one on each HDD) and received no error, **and** maintained the fail-over functionality as well. I then ran the upgrade on my production server and did not even get prompted about GRUB, and received no error or warning messages. 

So what I think happened was when I moved my virtual server to a new host machine in the past, it must have changed the unique identifiers it creates for HDDs, and so GRUB did not know where to install. My production server did not have this issue, because it has not changed in any way since installation. When I looked at the upgrade text, it looked like GRUB was installed to the partition of each HDD, there were two success messages, so from there, I surmised this was how my test server needed to be as well. Thanks for the replies and useful commands oldfred. I am calling this case closed. Hopefully this thread will save someone a headache in the future!

---

### Post by oldfred on 2013-12-30
Glad you were able to figure it out.

---

