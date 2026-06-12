---
title: "Nvidia Drivers on 18.04 Server Unmet dependencies"
date: 2019-04-03
forum: Server Platforms
---

### Post by rubylaser on 2019-04-03
It's been years since I've managed to screw up a server like this, but today was my lucky day.  I picked up a cheap 1050GTX to try to use GPU decoding/encoding for my Plex Docker container.  I installed the nvidia-docker2 package, but quickly realized that I didn't have a working driver.  So, I tried to install the nvidia-driver-390 package.  The install went halfway through, and failed.  Unmet dependencies.  I have tried to fixed this, but I can't seem to resolve the issue.  Here is where I am currently at. This is on 18.04 Server 64-bit. Any ideas are greatly appreciated.

```

root@loki:~# apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libnvidia-compute-390
The following NEW packages will be installed:
  libnvidia-compute-390
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
119 not fully installed or removed.
Need to get 0 B/20.6 MB of archives.
After this operation, 85.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 137763 files and directories currently installed.)
Preparing to unpack .../libnvidia-compute-390_390.116-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libnvidia-compute-390:amd64 (390.116-0ubuntu0.18.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libnvidia-compute-390_390.116-0ubuntu0.18.04.1_amd64.deb (--unpack):
 trying to overwrite shared '/etc/OpenCL/vendors/nvidia.icd', which is different from other instances of package libnvidia-compute-390:amd64
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-compute-390_390.116-0ubuntu0.18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2019-04-03
rubylaser; Hummmm ...


Long time no see :P

Anything useful from:
```

apt policy libnvidia-compute-390

```
to try and isolate "different from other instances of package" ?

[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by rubylaser on 2019-04-07
I know... It's been a long time.  Work and life has kept me very busy.  I need to get back here more frequently.  I really enjoy trying to help others out.

Thanks for the reply :)  I did get this fixed. To start, I have a full backup of this system. I tried all sorts of things: diverting the driver, removing individual packages, viewing the policy, etc.  Nothing worked.  It was screwed up pretty badly. So, I forced the packages, and then completely removed them, and cleaned up afterward (**Not the recommended method if someone is reading this...**)

```

dpkg --force-all -P nvidia-390 nvidia-compute-utils-390 nvidia-dkms-390 nvidia-prime nvidia-settings nvidia-opencl-icd-340 nvidia-opencl-icd-384 nvidia-kernel-source-390 nvidia-kernel-common-390 libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390 libnvidia-decode-390 libnvidia-encode-390  libnvidia-fbc1-390 libnvidia-ifr1-390
apt purge --autoremove '*nvidia*'
apt --fix-broken install
apt update
apt upgrade
apt autoremove
apt autoclean

```

Then, I just installed the Nvidia driver directly from their .run file.
```

wget https://download.nvidia.com/XFree86/Linux-x86_64/418.43/NVIDIA-Linux-x86_64-418.43.run
chmod +x ./NVIDIA-Linux-x86_64-418.43.run
./NVIDIA-Linux-x86_64-418.43.run

```

Now, it's working like a charm :)
```

root@loki:~# nvidia-smi
Sun Apr  7 12:03:03 2019
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 418.43       Driver Version: 418.43       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1050    Off  | 00000000:02:00.0 Off |                  N/A |
| 35%   25C    P0    N/A /  75W |      0MiB /  2000MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+


+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```

---

