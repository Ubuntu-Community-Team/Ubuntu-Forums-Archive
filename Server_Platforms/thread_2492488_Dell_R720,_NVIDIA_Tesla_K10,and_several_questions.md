---
title: "Dell R720, NVIDIA Tesla K10,and several questions"
date: 2023-11-13
forum: Server Platforms
---

### Post by isprins on 2023-11-13
Hi, I have a Dell R720 that I installed a NVIDIA Tesla K10 in. I am currently running TrueNAS scale on that.
That according to dmesg needs 
470.xx Legacy drivers.

My question is, in the event that there's no response from the TrueNAS support, or the 470.xx Legacy drivers can't be installed without borking the TrueNAS system.. 

Can ubuntu server run, qbittorrent, radarr,sonarr,bazarr,lidarr and Jellyfin? Is the K10 GPU supported by Ubuntu?
I also have 2 different zfs pools with important data, so it must be possible to handle those too.
How bout Backblaze?

---

### Post by MAFoElffen on 2023-11-13
I do not use Backblaze, but have been supporting NVidia for 20 years now. Almost as long for ZFS (since 2005), and all 4 of my machine here are ZFS-On-Root... My Workstation, Server, Laptop, and My Rasp Pi4. Here's my laptop.
```

mafoelffen@Mikes-ThinkPad-T520:~/Downloads/ISO$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                                                                        USED  AVAIL     REFER  MOUNTPOINT
backups                                                                                     224G  1.20T       96K  /zfs-backups
backups/BACKUPS                                                                             224G  1.20T       96K  none
backups/BACKUPS/ubuntu_2204                                                                 224G  1.20T       96K  /zfs-backups
backups/BACKUPS/ubuntu_2204/images-vm                                                       224G  1.20T       96K  /zfs-backups/images-vm
backups/BACKUPS/ubuntu_2204/images-vm/2023-07-25                                            224G  1.20T      224G  /zfs-backups/images-vm/2023-07-25
bpool                                                                                       431M  1.33G       96K  /boot
bpool/BOOT                                                                                  430M  1.33G       96K  none
bpool/BOOT/ubuntu_2204                                                                      430M  1.33G      430M  /boot
dpool                                                                                      3.02M   829G       96K  /dpool
dpool/DATA                                                                                  192K   829G       96K  none
dpool/DATA/ubuntu_2204                                                                       96K   829G       96K  /dpool
hpool                                                                                      57.3G   326G       96K  /home
hpool/USERDATA                                                                             57.2G   326G       96K  none
hpool/USERDATA/root_2204                                                                   2.86G   326G     2.86G  /root
hpool/USERDATA/ubuntu_2204                                                                 54.4G   326G     54.4G  /home
kpool                                                                                       487G   475G       96K  /kpool
kpool/QEMU-KVM                                                                              487G   475G       96K  none
kpool/QEMU-KVM/ubuntu_2204                                                                  487G   475G       96K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                                                              215G   475G      215G  /home/mafoelffen/Downloads/ISO
kpool/QEMU-KVM/ubuntu_2204/images                                                           271G   475G      253G  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt                                                          548K   475G      548K  /etc/libvirt/
maf1_pool                                                                                  3.21G  23.4G       24K  legacy
maf1_pool/buckets                                                                            24K  23.4G       24K  legacy
maf1_pool/containers                                                                        390M  23.4G       24K  legacy
maf1_pool/containers/maf1-alpine1                                                          5.93M  23.4G     51.0M  legacy
maf1_pool/containers/maf1-archlinux1                                                       39.9M  23.4G      418M  legacy
maf1_pool/containers/maf1-centos1                                                          45.0M  23.4G      307M  legacy
maf1_pool/containers/maf1-gentoo1                                                          40.8M  23.4G     1.26G  legacy
maf1_pool/containers/maf1-jammy1                                                            201M  23.4G      367M  legacy
maf1_pool/containers/maf1-oracle1                                                          46.8M  23.4G      363M  legacy
maf1_pool/containers/maf1-tumbleweed1                                                      11.3M  23.4G      143M  legacy
maf1_pool/custom                                                                             24K  23.4G       24K  legacy
maf1_pool/deleted                                                                          2.66G  23.4G       24K  legacy
maf1_pool/deleted/buckets                                                                    24K  23.4G       24K  legacy
maf1_pool/deleted/containers                                                                 24K  23.4G       24K  legacy
maf1_pool/deleted/custom                                                                     24K  23.4G       24K  legacy
maf1_pool/deleted/images                                                                   2.66G  23.4G       24K  legacy
maf1_pool/deleted/images/00e5b3ea1e45441e3826e870870546b1b910b650c3f528955bfeaefc4f7abacb   387M  23.4G      387M  legacy
maf1_pool/deleted/images/489888eff0432135a2085d7daebfa3961bf8298b095b0a5b95d180c623604ca5  48.8M  23.4G     48.8M  legacy
maf1_pool/deleted/images/4986c7046800680c80bbbb066851495558576d014c6a280fe1caf950672208ab   319M  23.4G      319M  legacy
maf1_pool/deleted/images/4daf768f17e5b8c31474c59e13e70f2ffceed8d48862b41379dac633ca56e0c0   266M  23.4G      266M  legacy
maf1_pool/deleted/images/56f03bca1f77ec709f5f248e702334d3a37ae9e86bfc184ebb64f62fa3219df6  1.26G  23.4G     1.26G  legacy
maf1_pool/deleted/images/98b92c0a39f0c1c972a8b9f09126bd9592705ecbb9689a422908059382deff69   134M  23.4G      134M  legacy
maf1_pool/deleted/images/c14665acda2842525ec9b080baba17c3ac43225fc045ea1e52df939562c84b31   273M  23.4G      273M  legacy
maf1_pool/deleted/virtual-machines                                                           24K  23.4G       24K  legacy
maf1_pool/images                                                                             24K  23.4G       24K  legacy
maf1_pool/virtual-machines                                                                   24K  23.4G       24K  legacy
rpool                                                                                      22.4G   458G       96K  /
rpool/ROOT                                                                                 22.4G   458G       96K  none
rpool/ROOT/ubuntu_2204                                                                     22.4G   458G     7.98G  /
rpool/ROOT/ubuntu_2204/srv                                                                   96K   458G       96K  /srv
rpool/ROOT/ubuntu_2204/tmp                                                                  396K   458G      396K  /tmp
rpool/ROOT/ubuntu_2204/usr                                                                 3.32G   458G       96K  /usr
rpool/ROOT/ubuntu_2204/usr/local                                                           3.32G   458G     3.32G  /usr/local
rpool/ROOT/ubuntu_2204/var                                                                 11.1G   458G       96K  /var
rpool/ROOT/ubuntu_2204/var/cache                                                            610M   458G      610M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                                                             96K   458G       96K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                                                             6.35G   458G     6.19G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService                                              112K   458G      112K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager                                               460K   458G      460K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt                                                          104M   458G      104M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker                                                        96K   458G       96K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg                                                        59.2M   458G     59.2M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs                                                          104K   458G      104K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                                                              656M   458G      656M  /var/log
rpool/ROOT/ubuntu_2204/var/mail                                                              96K   458G       96K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                                                            3.05G   458G     3.05G  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                                                            336K   458G      336K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                                                              452M   458G      452M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                                                               96K   458G       96K  /var/www

```
As you can see, I have mine segmented out for ease of migrations and backups. 

Why do you say NVidia driver 470? NVidia says the last driver that support the Tesla K Series was 440. The product list for 470 does not support Tesla Kx series.

---

### Post by isprins on 2023-11-14
There are others that get that error message, so I don't know why.
[https://www.truenas.com/community/threads/nvidia-legacy-drivers-and-tesla-k10.108879/](https://www.truenas.com/community/threads/nvidia-legacy-drivers-and-tesla-k10.108879/) It could be that truenas is quirky or something.

---

### Post by MAFoElffen on 2023-11-14
Post #3 there answered you with the right information... But didn't explain himself. You do not load the driver (which seems to be too new a driver anyways, but). What you do is...

This is the same for any Linux Distro.

On the host, first turn on IOMMU to create IOMMU groups. Then you create a vfio.conf module file to both blacklist the drivers that that GPU device would use, so that it remains unclaimed by the host, then load the vfio module with it's module load option pointing to the Device ID of the GPU.

Then you create the VM with it using that pci passthrough... Once confirmed that "that" device is seen inside that VM, then you install and load the driver inside the VM.

I used to use the NVidia binaries straight from them, for many years, but years ago... For the past 8 years or so, I just use the Ubuntu packaged NVidia drivers.

---

