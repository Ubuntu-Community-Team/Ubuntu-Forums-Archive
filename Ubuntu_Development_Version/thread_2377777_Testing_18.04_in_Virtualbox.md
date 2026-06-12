---
title: "Testing 18.04 in Virtualbox"
date: 2017-11-16
forum: Ubuntu Development Version
---

### Post by sports fan Matt on 2017-11-16
I'm late to the party, but testing Bionic in Virtual box.

---

### Post by ajgreeny on 2017-11-16
Which version; the default Ubuntu with gnome DE or another?

I have Ubuntu and Xubuntu versions running very sweetly, both also in VBox, so far with no major problems or show-stoppers.

---

### Post by sports fan Matt on 2017-11-16
I think with Gnome DE but not sure, how can I check? And the same here, no major issues, but as we know, it's subject to change.

---

### Post by Irihapeti on 2017-11-16
This command

```
echo $DESKTOP_SESSION
```

should tell you. (Just discovered it yesterday)

---

### Post by sports fan Matt on 2017-11-16
It said Ubuntu and yes with gnome DE.

---

### Post by vasa1 on 2017-11-16
> **ajgreeny said:**
> Which version; the default Ubuntu with gnome DE or another?
...
The other thing to share (for each login session) is whether the user is on Wayland or Xorg.

I'm wondering just how many applications some of us take for granted, will run on Wayland: conky, xdotool, wmctrl, some color pickers ...

---

### Post by w00sterf1 on 2017-11-21
I've been running a Vm under Virtualbox since 16.10 which I've upgraded to 17.04 -> 17.10 and now 18.04. 

I'm running Enlightenment and Cinnamon DE's and both have worked flawlessly. The only thing out of the ordinary is the fact I'm running a ZFS based root file system, which is not something which can be done from the installation mediums, you have to do a bit of hands-on work to get it up and running but when it is, it is running a like a charm. 

```
wooster@Benny-Hill:~$ echo $DESKTOP_SESSION
enlightenment
wooster@Benny-Hill:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu Bionic Beaver (development branch)
Release:        18.04
Codename:       bionic
wooster@Benny-Hill:~$ uname -a
Linux Benny-Hill 4.13.0-17-generic #20-Ubuntu SMP Mon Nov 6 10:04:08 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
wooster@Benny-Hill:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
udev                    2.4G     0  2.4G   0% /dev
tmpfs                   483M  7.3M  476M   2% /run
rpool/ROOT/ubuntu        81G  5.0G   76G   7% /
tmpfs                   2.4G  4.0K  2.4G   1% /dev/shm
tmpfs                   5.0M  4.0K  5.0M   1% /run/lock
tmpfs                   2.4G     0  2.4G   0% /sys/fs/cgroup
usr01                   131G     0  131G   0% /datapool
rpool/home               76G  128K   76G   1% /home
rpool/home/wooster      113G   38G   76G  33% /home/.ecryptfs/wooster
rpool/home/root          76G  128K   76G   1% /root
rpool/srv                76G  128K   76G   1% /srv
usr01/Pictures          215G   84G  131G  39% /usr01/Pictures
rpool/var/games          76G  128K   76G   1% /var/games
rpool/var/nfs            76G  128K   76G   1% /var/lib/nfs
rpool/var/log            76G  5.0M   76G   1% /var/log
rpool/var/spool          76G  128K   76G   1% /var/spool
rpool/var/tmp            76G  128K   76G   1% /var/tmp
tmpfs                   483M  4.0K  483M   1% /run/user/1000
/home/wooster/.Private  113G   38G   76G  33% /home/wooster
wooster@Benny-Hill:~$ sudo zpool status
  pool: rpool
 state: ONLINE
  scan: scrub in progress since Tue Nov 21 22:14:06 2017
    303M scanned out of 43.1G at 4.81M/s, 2h31m to go
    0 repaired, 0.69% done
config:


        NAME                                           STATE     READ WRITE CKSUM
        rpool                                          ONLINE       0     0     0
          ata-VBOX_HARDDISK_VB506fcb1c-834ddfaa-part1  ONLINE       0     0     0


errors: No known data errors


  pool: usr01
 state: ONLINE
  scan: scrub in progress since Tue Nov 21 22:14:11 2017
    942M scanned out of 120G at 16.2M/s, 2h4m to go
    0 repaired, 0.77% done
config:


        NAME                                       STATE     READ WRITE CKSUM
        usr01                                      ONLINE       0     0     0
          raidz3-0                                 ONLINE       0     0     0
            ata-VBOX_HARDDISK_VB0ca2b272-3d414999  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VB19ee3c6e-df1f8f2f  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VB1ce908fd-ddf74f24  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VB529668c2-d5088edf  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VB82689ea5-3e0944ad  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VB91668a5b-96a163c7  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VBa7fb1aa2-5ec77442  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VBb4ac0fa8-2b1c2466  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VBeb275e5a-62515aca  ONLINE       0     0     0
            ata-VBOX_HARDDISK_VB2f9af305-c28a2d81  ONLINE       0     0     0
        spares
          pci-0000:00:14.0-scsi-0:0:3:0            AVAIL
          pci-0000:00:14.0-scsi-0:0:0:0            AVAIL
          pci-0000:00:14.0-scsi-0:0:1:0            AVAIL
          pci-0000:00:14.0-scsi-0:0:2:0            AVAIL


errors: No known data errors



```

---

### Post by mc4man on 2017-11-22
> **Irihapeti said:**
> This command

```
echo $DESKTOP_SESSION
```

should tell you. (Just discovered it yesterday)
Because of a fallback routine there's no absolute guarantee that session name accurately reflects expected, so more complete would be like

```
echo $DESKTOP_SESSION $XDG_SESSION_TYPE

```

---

