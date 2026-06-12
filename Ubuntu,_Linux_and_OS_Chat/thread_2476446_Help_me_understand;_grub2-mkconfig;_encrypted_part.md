---
title: "Help me understand; grub2-mkconfig; encrypted partitions; not support request"
date: 2022-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by issh on 2022-06-26
Hello.
I have been learning .rpm based systems (openSUSE, RedHat Enterprise, Fedora.) I'm not understanding a situation I encountered and why my "solution" worked. Maybe someone can point out why it worked the way it did or to documentation that explains it.
os-prober and grub2-mkconfig failed to detect and configure a Windows installation entry for GRUB2.
I have an openSUSE system which has 2 hard disks, one with a Windows 10 installation and the other with openSUSE. openSUSE uses GRUB2 and grub2-mkconfig instead of update-grub as it is in Debian based systems such as Ubuntu. To detect the Windows .efi partition one would run os-prober and then grub2-mkconfig*. However, in this situation it would fail due to the presence of a VeraCrypt partition on the Windows disk which is exFAT when decrypted. I didn't know that was causing the issue at the time and documentation was leading me to repair a supposed bad superblock with fdisk and fsck. If I had done this the data would have been lost. This was mostly just a test setup, so no problem there.

First, I mounted the primary Microsoft NTFS partition at /dev/sda3 to /run/media/ak/*
Second, I mounted the Windows EFI partition at /dev/sda1 to /mnt
Third, I decrypted the VeraCrypt exFAT partition at /dev/sda5 and mounted it to /media/veracrypt5 at position 5
Then, I ran os-prober.
Finally, I ran grub2-mkconfig -o /boot/grub2/grub.cfg
It completed without error.
Help understanding what I did here would be great. With the errors which are seen below, why was this required for os-prober and grub2-mkconfig to complete without error? I was guessing a bit, but I thought the order, position, and decryption and mounting of the VeraCrypt exFAT partition was the issue. I was about to use fdisk and fsck to correct a possible bad superblock, but I thought, "No, has to be the encrypted partition and the position order of the mounting." Another question I have is, when I update or upgrade openSUSE Leap again and I get a new kernel and zypper runs os-prober and grub2-mkconfig, will this mean that unless I follow this procedure again I won't get be able to see the Microsoft entry in the GRUB2 bootloader again? os-prober and grub2-mkconfig will fail again unless I follow this procedure regarding the VeraCrypt partition? I guess I will find out. Also, some things I noticed which I did wrong... I didn't specify where to mount /dev/sda3 and I shouldn't have mounted /dev/sda to /media. 
Regards.

```
ak@box:~> lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0   2.7T  0 disk
&#9500;&#9472;sda1   8:1    0   100M  0 part
&#9500;&#9472;sda2   8:2    0    16M  0 part
&#9500;&#9472;sda3   8:3    0   2.6T  0 part
&#9500;&#9472;sda4   8:4    0   509M  0 part
&#9492;&#9472;sda5   8:5    0 164.3G  0 part
sdb      8:16   0   2.7T  0 disk
&#9500;&#9472;sdb1   8:17   0   300M  0 part /boot/efi
&#9500;&#9472;sdb2   8:18   0   2.7T  0 part /var
&#9474;                                /home
&#9474;                                /tmp
&#9474;                                /root
&#9474;                                /opt
&#9474;                                /boot/grub2/x86_64-efi
&#9474;                                /usr/local
&#9474;                                /srv
&#9474;                                /boot/grub2/i386-pc
&#9474;                                /.snapshots
&#9474;                                /
&#9492;&#9472;sdb3   8:19   0  15.6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  
ak@box:~> sudo mount /dev/sda1 /mnt
ak@box:~> sudo os-prober
/dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
ak@box:~> sudo grub2-mkconfig -o /boot/grub2/grub.cfg
Generating grub configuration file ...
Found theme: /boot/grub2/themes/openSUSE/theme.txt
Found linux image: /boot/vmlinuz-5.14.21-150400.22-default
Found initrd image: /boot/initrd-5.14.21-150400.22-default
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
/usr/sbin/grub2-probe: error: ../grub-core/kern/fs.c:121:unknown filesystem.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
/usr/sbin/grub2-probe: error: ../grub-core/kern/fs.c:121:unknown filesystem.
done

```

```
ak@box:~> lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0   2.7T  0 disk
&#9500;&#9472;sda1   8:1    0   100M  0 part
&#9500;&#9472;sda2   8:2    0    16M  0 part
&#9500;&#9472;sda3   8:3    0   2.6T  0 part
&#9500;&#9472;sda4   8:4    0   509M  0 part
&#9492;&#9472;sda5   8:5    0 164.3G  0 part
sdb      8:16   0   2.7T  0 disk
&#9500;&#9472;sdb1   8:17   0   300M  0 part /boot/efi
&#9500;&#9472;sdb2   8:18   0   2.7T  0 part /var
&#9474;                                /home
&#9474;                                /tmp
&#9474;                                /root
&#9474;                                /opt
&#9474;                                /boot/grub2/x86_64-efi
&#9474;                                /usr/local
&#9474;                                /srv
&#9474;                                /boot/grub2/i386-pc
&#9474;                                /.snapshots
&#9474;                                /
&#9492;&#9472;sdb3   8:19   0  15.6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  
ak@box:~> sudo mount /dev/sda /media
mount: /media: wrong fs type, bad option, bad superblock on /dev/sda, missing codepage or helper program, or other error.

```

```
ak@box:~> lsblk
NAME           MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda              8:0    0   2.7T  0 disk
&#9500;&#9472;sda1           8:1    0   100M  0 part /mnt
&#9500;&#9472;sda2           8:2    0    16M  0 part
&#9500;&#9472;sda3           8:3    0   2.6T  0 part /run/media/ak/365075B850757F83
&#9500;&#9472;sda4           8:4    0   509M  0 part
&#9492;&#9472;sda5           8:5    0 164.3G  0 part
  &#9492;&#9472;veracrypt5 254:0    0 164.3G  0 dm   /media/veracrypt5
sdb              8:16   0   2.7T  0 disk
&#9500;&#9472;sdb1           8:17   0   300M  0 part /boot/efi
&#9500;&#9472;sdb2           8:18   0   2.7T  0 part /home
&#9474;                                        /var
&#9474;                                        /root
&#9474;                                        /tmp
&#9474;                                        /boot/grub2/x86_64-efi
&#9474;                                        /usr/local
&#9474;                                        /srv
&#9474;                                        /opt
&#9474;                                        /boot/grub2/i386-pc
&#9474;                                        /.snapshots
&#9474;                                        /
&#9492;&#9472;sdb3           8:19   0  15.6G  0 part [SWAP]
sr0             11:0    1  1024M  0 rom  
ak@box:~> sudo os-prober
/dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
ak@box:~> sudo grub2-mkconfig -o /boot/grub2/grub.cfg
Generating grub configuration file ...
Found theme: /boot/grub2/themes/openSUSE/theme.txt
Found linux image: /boot/vmlinuz-5.14.21-150400.22-default
Found initrd image: /boot/initrd-5.14.21-150400.22-default
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
done

```

---

### Post by TheFu on 2022-06-27
I know nothing about windows.
What file system(s) do the linux system(s) use?  The stock lsblk is poor, use this command instead:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Some file systems, like ZFS and BTRFS will lie to us.

I ran SuSE for about a year in the early 2000s. At that time, it was a fine OS and wasn't surprising to me in anyway way that I recall. In 2006-ish, I moved a desktop to Ubuntu and basically SuSE hasn't been my main OS since, though I do run a few BSD and Debian systems.  Ubuntu LTS was the right mix for my needs of support length, current versions of packages, and comfort.  Sure, there are things in almost every Ubuntu release since 11.04 that I didn't like, but compared to the base needs for 5 yrs of no-hassle support/patching and using slightly newer versions of most packages than Debian-stable does, I can get passed the foolishness of some other Canonical choices like pulse-audio, wayland, snaps, and systemd.

---

### Post by grahammechanical on 2022-06-27
I know nothing about OpenSuse. What I know about Linux comes from being an ordinary home user of Ubuntu which provides the user with a script that runs grub-mkconfig for us (update-grub). Apart from curiosity I have no need to understand the inner workings of Grub. When I do want to learn something about Grub I go to the Grub 2 manual. And reading that is enough to convince me not to be curious.

[https://www.gnu.org/software/grub/manual/grub/html_node/index.html](https://www.gnu.org/software/grub/manual/grub/html_node/index.html)

[https://linuxhint.com/grub2_mkconfig_tutorial/](https://linuxhint.com/grub2_mkconfig_tutorial/)

Regards

---

### Post by tea for one on 2022-06-28
Grub will only find a working Windows installation.
I imagine that, if any sort of encryption is active, then Grub will deem it as "not working"

There are quite a few threads in the forum pages where Bitlocker was creating Ubuntu installation and Grub difficulties.

---

