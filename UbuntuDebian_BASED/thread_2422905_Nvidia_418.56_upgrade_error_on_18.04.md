---
title: "Nvidia 418.56 upgrade error on 18.04"
date: 2019-07-14
forum: Ubuntu/Debian BASED
---

### Post by bdlabitt on 2019-07-14
Sort of in a broken state with an Nvidia update.  Not even sure how I got there, but I'd appreciate some help fixing this.
Synaptic shows the following error:
```
 nvidia-driver-418 depends on libnvidia-gl-418 (= 418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev); however:  Package libnvidia-gl-418:amd64 is not installed.


dpkg: error processing package nvidia-driver-418 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.27-3ubuntu1) ...
dpkg: dependency problems prevent configuration of libnvidia-ifr1-418:amd64:
 libnvidia-ifr1-418:amd64 depends on libnvidia-gl-418; however:
  Package libnvidia-gl-418:amd64 is not installed.


dpkg: error processing package libnvidia-ifr1-418:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnvidia-ifr1-418:i386:
 libnvidia-ifr1-418:i386 depends on libnvidia-gl-418; however:
  Package libnvidia-gl-418:i386 is not installed.


dpkg: error processing package libnvidia-ifr1-418:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-driver-418
 libnvidia-ifr1-418:amd64
 libnvidia-ifr1-418:i386
```

I tried to fix this using  sudo apt --fix-broken install.  Did not work.  
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cuda-command-line-tools-9-2 cuda-compiler-9-2 cuda-cublas-9-2 cuda-cublas-dev-9-2 cuda-cudart-9-2 cuda-cudart-dev-9-2 cuda-cufft-9-2
  cuda-cufft-dev-9-2 cuda-cuobjdump-9-2 cuda-cupti-9-2 cuda-curand-9-2 cuda-curand-dev-9-2 cuda-cusolver-9-2 cuda-cusolver-dev-9-2
  cuda-cusparse-9-2 cuda-cusparse-dev-9-2 cuda-documentation-9-2 cuda-driver-dev-9-2 cuda-gdb-9-2 cuda-gpu-library-advisor-9-2
  cuda-libraries-9-2 cuda-libraries-dev-9-2 cuda-license-9-2 cuda-memcheck-9-2 cuda-misc-headers-9-2 cuda-npp-9-2 cuda-npp-dev-9-2
  cuda-nsight-9-2 cuda-nvcc-9-2 cuda-nvdisasm-9-2 cuda-nvgraph-9-2 cuda-nvgraph-dev-9-2 cuda-nvml-dev-9-2 cuda-nvprof-9-2
  cuda-nvprune-9-2 cuda-nvrtc-9-2 cuda-nvrtc-dev-9-2 cuda-nvtx-9-2 cuda-nvvp-9-2 cuda-samples-9-2 cuda-toolkit-9-2 cuda-tools-9-2
  cuda-visual-tools-9-2 libllvm7 libllvm7:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-418 libnvidia-gl-418:i386
The following NEW packages will be installed:
  libnvidia-gl-418 libnvidia-gl-418:i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/49.2 MB of archives.
After this operation, 236 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 976704 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb (--unpack):
 new libnvidia-gl-418:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb (--unpack):
 new libnvidia-gl-418:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb
 /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How does one get out of this mess?  Is there a transition package that should clean this up, or just wait for a while until Ubuntu issues the new Nvidia packages automatically?

---

### Post by CatKiller on 2019-07-14
From the looks of it, you're trying to switch branches of the Nvidia driver while you still have an existing branch installed, and using repositories from another distro to do so. Both of those are bad ideas.

If you want to use newer Nvidia drivers than the ones that are in the main repositories, the [graphics drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) is the one to use, although that is planned to be unnecessary soon with those drivers coming through the updates repository.

Before installing a new branch of the Nvidia driver you must first get rid of the old branch, otherwise you get version conflicts exactly like the one you're experiencing. ```
sudo apt purge nvidia*
``` should do it. Then you can install the new one.

---

### Post by bdlabitt on 2019-07-14
Thanks, I'll try that and report back.

---

### Post by bdlabitt on 2019-07-15
Hmm, unsuccessful so far.  ```
$ sudo apt purge nvidia*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-331-dev' for glob 'nvidia*'
Note, selecting 'nvidia-384-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-vulkan-icd:i386' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-i386:i386' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-396' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-410' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-418' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-384-updates' for glob 'nvidia*'
Note, selecting 'nvidia-settings-updates' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver' for glob 'nvidia*'
Note, selecting 'nvidia-367-updates' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-utils' for glob 'nvidia*'
Note, selecting 'nvidia-387-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-343-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-dev' for glob 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-346-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-utils-396' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-410' for glob 'nvidia*'
Note, selecting 'nvidia-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-331-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-396' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-410' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-nsight' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-396' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-410' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-396' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-410' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-nonglvnd' for glob 'nvidia*'
Note, selecting 'nvidia-375-dev' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-375-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-390' for glob 'nvidia*'
Note, selecting 'nvidia-driver-396' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia*'
Note, selecting 'nvidia-367-dev' for glob 'nvidia*'
Note, selecting 'nvidia-driver-410' for glob 'nvidia*'
Note, selecting 'nvidia-driver-418' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source' for glob 'nvidia*'
Note, selecting 'nvidia-378-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-361-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-343' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-367' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-375' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-384' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-387' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-390' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-396' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-headless-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-396' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-headless-410' for glob 'nvidia*'
Note, selecting 'nvidia-headless-418' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-381-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-343' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-367' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-375' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-384' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-387' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-390' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-396' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-367' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-375' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-378' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-381' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-387' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-396' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-375' for glob 'nvidia*'
Note, selecting 'nvidia-378' for glob 'nvidia*'
Note, selecting 'nvidia-381' for glob 'nvidia*'
Note, selecting 'nvidia-384' for glob 'nvidia*'
Note, selecting 'nvidia-387' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-390' for glob 'nvidia*'
Note, selecting 'nvidia-396' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-410' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-418' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Note, selecting 'nvidia-kernel-common-418' instead of 'nvidia-kernel-common'
Note, selecting 'nvidia-utils-418' instead of 'nvidia-smi'
Note, selecting 'nvidia-utils-418' instead of 'nvidia-utils'
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-driver' is not installed, so not removed
Package 'nvidia-legacy-304xx-driver' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-340xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-304xx-kernel-dkms' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-driver-libs' is not installed, so not removed
Package 'nvidia-driver-libs-nonglvnd' is not installed, so not removed
Package 'nvidia-driver-libs-i386:i386' is not installed, so not removed
Package 'nvidia-vulkan-icd:i386' is not installed, so not removed
Package 'nvidia-libopencl1-390' is not installed, so not removed
Package 'nvidia-libopencl1-396' is not installed, so not removed
Package 'nvidia-libopencl1-387' is not installed, so not removed
Package 'nvidia-343-uvm' is not installed, so not removed
Package 'nvidia-libopencl1-304' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-dev' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361-dev' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-dev' is not installed, so not removed
Package 'nvidia-375-dev' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-libopencl1-375' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-367' is not installed, so not removed
Package 'nvidia-opencl-icd-375' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-compute-utils-396' is not installed, so not removed
Package 'nvidia-compute-utils-410' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-dkms-396' is not installed, so not removed
Package 'nvidia-dkms-410' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-driver-396' is not installed, so not removed
Package 'nvidia-driver-410' is not installed, so not removed
Package 'nvidia-driver-418' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-396' is not installed, so not removed
Package 'nvidia-headless-410' is not installed, so not removed
Package 'nvidia-headless-418' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-396' is not installed, so not removed
Package 'nvidia-headless-no-dkms-410' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-kernel-common-396' is not installed, so not removed
Package 'nvidia-kernel-common-410' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-kernel-source-396' is not installed, so not removed
Package 'nvidia-kernel-source-410' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'nvidia-utils-396' is not installed, so not removed
Package 'nvidia-utils-410' is not installed, so not removed
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-gl-410 : Depends: libnvidia-gl-418 but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```  So I tried 'apt --fix-broken install', which did not fix the problem.
```
$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cuda-command-line-tools-9-2 cuda-compiler-9-2 cuda-cublas-9-2 cuda-cublas-dev-9-2 cuda-cudart-9-2
  cuda-cudart-dev-9-2 cuda-cufft-9-2 cuda-cufft-dev-9-2 cuda-cuobjdump-9-2 cuda-cupti-9-2
  cuda-curand-9-2 cuda-curand-dev-9-2 cuda-cusolver-9-2 cuda-cusolver-dev-9-2 cuda-cusparse-9-2
  cuda-cusparse-dev-9-2 cuda-documentation-9-2 cuda-driver-dev-9-2 cuda-gdb-9-2
  cuda-gpu-library-advisor-9-2 cuda-libraries-9-2 cuda-libraries-dev-9-2 cuda-license-9-2
  cuda-memcheck-9-2 cuda-misc-headers-9-2 cuda-npp-9-2 cuda-npp-dev-9-2 cuda-nsight-9-2
  cuda-nvcc-9-2 cuda-nvdisasm-9-2 cuda-nvgraph-9-2 cuda-nvgraph-dev-9-2 cuda-nvml-dev-9-2
  cuda-nvprof-9-2 cuda-nvprune-9-2 cuda-nvrtc-9-2 cuda-nvrtc-dev-9-2 cuda-nvtx-9-2 cuda-nvvp-9-2
  cuda-samples-9-2 cuda-toolkit-9-2 cuda-tools-9-2 cuda-visual-tools-9-2 libllvm7 libllvm7:i386
  libnvidia-cfg1-418 libnvidia-encode-418 libnvidia-encode-418:i386 libnvidia-fbc1-418
  libnvidia-fbc1-418:i386 nvidia-utils-418 xserver-xorg-video-nvidia-418
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-418
The following NEW packages will be installed:
  libnvidia-gl-418
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/32.2 MB of archives.
After this operation, 165 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 976640 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb (--unpack):
 new libnvidia-gl-418:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Have any recommendations? 

 For some reason, libnvidia-gl-410 is dependent on libnvidia-gl-418!  I removed that file.  Now the purge of nvidia works.  And finally sudo apt --fix-broken install works.  Now to try to install Nvidia-418 again.  Currently running nouveau.  Is the recommended package the Nvidia driver metapackage from nvidia-driver-418(open source)?

---

### Post by bdlabitt on 2019-07-15
Or should I install (in synaptic) nvidia-driver-418 metapackage?

---

### Post by CatKiller on 2019-07-15
I would remove whichever source you had that was pulling in Pop!OS packages and replace it with the PPA before you try to install the drivers. The metapackage is the same whether you install it through Synaptic or the Additional Drivers tool.

---

### Post by bdlabitt on 2019-07-15
There seems to be a problem with nvidia-driver-418 metapackage.  Starting from a nouveau "non-broken" system.  Synaptic popped up a window.  "An error occurred, the following details are provided" ```
E: /tmp/apt-dpkg-install-P2JY8E/00-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb: new libnvidia-gl-418:amd64 package pre-installation script subprocess returned error exit status 2E: /tmp/apt-dpkg-install-P2JY8E/01-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb: new libnvidia-gl-418:i386 package pre-installation script subprocess returned error exit status 2

```  The detailed error is: ```
(Reading database ... 976178 files and directories currently installed.)Preparing to unpack .../00-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /tmp/apt-dpkg-install-P2JY8E/00-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb (--unpack):
 new libnvidia-gl-418:amd64 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../01-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /tmp/apt-dpkg-install-P2JY8E/01-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb (--unpack):
 new libnvidia-gl-418:i386 package pre-installation script subprocess returned error exit status 2
Selecting previously unselected package libnvidia-ifr1-418:amd64.
Preparing to unpack .../02-libnvidia-ifr1-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking libnvidia-ifr1-418:amd64 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package libnvidia-ifr1-418:i386.
Preparing to unpack .../03-libnvidia-ifr1-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
Unpacking libnvidia-ifr1-418:i386 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-compute-utils-418.
Preparing to unpack .../04-nvidia-compute-utils-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-compute-utils-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-kernel-source-418.
Preparing to unpack .../05-nvidia-kernel-source-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-kernel-source-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-kernel-common-418.
Preparing to unpack .../06-nvidia-kernel-common-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-kernel-common-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-dkms-418.
Preparing to unpack .../07-nvidia-dkms-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-dkms-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-utils-418.
Preparing to unpack .../08-nvidia-utils-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-utils-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-driver-418.
Preparing to unpack .../09-nvidia-driver-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
Unpacking nvidia-driver-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../10-nvidia-settings_390.77-0ubuntu0.18.04.1_amd64.deb ...
Unpacking nvidia-settings (390.77-0ubuntu0.18.04.1) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-P2JY8E/00-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb
 /tmp/apt-dpkg-install-P2JY8E/01-libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nvidia-kernel-source-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
dpkg: dependency problems prevent configuration of nvidia-driver-418:
 nvidia-driver-418 depends on libnvidia-gl-418 (= 418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev); however:
  Package libnvidia-gl-418:amd64 is not installed.


dpkg: error processing package nvidia-driver-418 (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-utils-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Setting up nvidia-kernel-common-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
update-initramfs: deferring update (trigger activated)
Setting up nvidia-settings (390.77-0ubuntu0.18.04.1) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up nvidia-compute-utils-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
Warning: The home dir /nonexistent you specified can't be accessed: No such file or directory
Adding system user `nvidia-persistenced' (UID 117) ...
Adding new group `nvidia-persistenced' (GID 127) ...
Adding new user `nvidia-persistenced' (UID 117) with group `nvidia-persistenced' ...
Not creating home directory `/nonexistent'.
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Setting up nvidia-dkms-418 (418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-418.56 DKMS files...
Building for 5.0.0-21-generic
Building for architecture x86_64
Building initial module for 5.0.0-21-generic
Done.


nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-21-generic/updates/dkms/


nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-21-generic/updates/dkms/


nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-21-generic/updates/dkms/


nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-21-generic/updates/dkms/


depmod...


DKMS: install completed.
dpkg: dependency problems prevent configuration of libnvidia-ifr1-418:amd64:
 libnvidia-ifr1-418:amd64 depends on libnvidia-gl-418; however:
  Package libnvidia-gl-418:amd64 is not installed.


dpkg: error processing package libnvidia-ifr1-418:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnvidia-ifr1-418:i386:
 libnvidia-ifr1-418:i386 depends on libnvidia-gl-418; however:
  Package libnvidia-gl-418:i386 is not installed.


dpkg: error processing package libnvidia-ifr1-418:i386 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.130ubuntu3.8) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-21-generic
Errors were encountered while processing:
 nvidia-driver-418
 libnvidia-ifr1-418:amd64
 libnvidia-ifr1-418:i386



```
Back to a broken system.  It seems that the meta-package nvidia-driver-418 in Synaptic is broken, i.e., it does not contain all the dependencies.  How can I successfully install nvidia-418?
  [ATTACH=CONFIG]283625[/ATTACH] 
 What is strange, is that it is a partial install.  Nvidia X Server Settings, thinks that the driver version is 418.56.  Am I missing a transitional package?  How would I find it?

---

### Post by CatKiller on 2019-07-15
Well, that's still trying to use your Pop!OS packages. Purge the nvidia stuff again, and also any libnvidia stuff that didn't get removed, remove whatever's giving you Pop!OS packages, and then run ```
sudo apt clean
``` to clear out your cached package files.

Then add the PPA and try again. You'll need to run ```
sudo apt update
``` whenever you make changes to your repositories lists.

---

### Post by bdlabitt on 2019-07-15
This is a System76 laptop.  I had their ppa enabled.  It has been useful to ensure everything worked.  I didn't realize that the ppa was now pulling in pop!os packages.  Hmm, maybe I need to contact them to "fix" the dependency issue.  It's that or purging System76 stuff and going vanilla Ubuntu.

---

### Post by CatKiller on 2019-07-15
Ah, OK. I thought this *was* a vanilla install, and you'd added a Pop!OS repository.

I've never used their flavour, so I can't help you with that part of it, or tell you anything about the differences. An all Pop!OS setup *should* be internally-consistent, but I have no idea whether it actually is because I've never used it.

In this case, this is the issue ```
dpkg-divert: error: mismatch on package when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-418' found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
```

You've still got some 340 stuff there when you're trying to install 418, which gives the version mismatch. You need to get rid of all the old branches.

---

### Post by bdlabitt on 2019-07-15
I'll try your suggestion.  Is it sufficient to uncheck the ppa or do I have to do a ppa-purge?

---

### Post by bdlabitt on 2019-07-15
To my knowledge, I never added a popos repo.  However, this is a System76 laptop.  I bought it before PopOS was a gleam in their eyes.  However, System76 always had a repo to ensure the drivers needed to support their product line was available.  Has it now become popos?  Perhaps.

---

### Post by wildmanne39 on 2019-07-15
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

### Post by CatKiller on 2019-07-15
I edited my previous post while you were writing this one, with the next step.

Having a Pop!OS repository in vanilla Ubuntu would be bad. Using the graphics drivers PPA in Pop!OS might be equally bad: I don't know either way.

---

### Post by bdlabitt on 2019-07-15
> **CatKiller said:**
> Ah, OK. I thought this *was* a vanilla install, and you'd added a Pop!OS repository.

I've never used their flavour, so I can't help you with that part of it, or tell you anything about the differences. An all Pop!OS setup *should* be internally-consistent, but I have no idea whether it actually is because I've never used it.

In this case, this is the issue ```
dpkg-divert: error: mismatch on package when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-418' found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
```

You've still got some 340 stuff there when you're trying to install 418, which gives the version mismatch. You need to get rid of all the old branches.
I can't find any selected 340 stuff.  Using a search of nvidia*340, I see 20 packages, none of which are selected.  Hard to purge stuff that is invisible!

---

### Post by CatKiller on 2019-07-15
> **bdlabitt said:**
> I can't find any selected 340 stuff.  Using a search of nvidia*340, I see 20 packages, none of which are selected.  Hard to purge stuff that is invisible!

Yes, it is :)

Maybe try looking for just 340. I *think* that ```
apt list --installed *340*
``` will show everything that's currently installed that contains the string 340.

---

### Post by bdlabitt on 2019-07-15
Finally unbroken again and back to nouveau.  No nvidia, or libnvidia, or cuda files.  Searching for 340 shows nothing is selected.  Searching for dkms shows there is an unselected package called nvidia-dkms-390 which is a transitional package for nvidia-dkms-418.  Do I need the package nvidia-dkms-340?

A search on [https://packages.ubuntu.com/search?keywords=nvidia-dkms-340&searchon=names](https://packages.ubuntu.com/search?keywords=nvidia-dkms-340&searchon=names) shows no hits on nvidia-dkms-340.  Maybe they called it something different then?

So if I am following you correctly, you are not sure if I should purge-ppa for system76?  You sounded uncertain.

---

### Post by CatKiller on 2019-07-15
> **bdlabitt said:**
> So if I am following you correctly, you are not sure if I should purge-ppa for system76?  You sounded uncertain.

I think that you shouldn't: you're already using a newer kernel than you would be if you were using vanilla Ubuntu. Stick with all the Pop!OS stuff rather than trying to bring in stuff for Ubuntu.

If you've managed to get rid of all the old nvidia stuff, you *should* be OK to try installing the new stuff again. If it fails again, try to find where the mismatch is.

I think ```
dpkg-divert --list
``` shows which package has caused a file to be diverted.

---

### Post by bdlabitt on 2019-07-15
This certainly has been a bit frustrating.  apt list --installed *340* doesn't show anything.
I then re-installed nvidia-340, now apt list shows the 3 packages, libcuda1-340, nvidia-340, and nvidia-opencl-icd-340.  After that, I purged *nvidia*.  Now apt list --installed shows: libcuda1-340.  Purging libcuda1-340 gives me a clean slate.  (A blank listing.)

Installing nvidia-418 just doesn't work, with or without nvidia-340 installed.  As far as I can tell the errors are all contained in:
```
Do you want to continue? [Y/n] Y(Reading database ... 976704 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb (--unpack):
 new libnvidia-gl-418:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb (--unpack):
 new libnvidia-gl-418:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_i386.deb
 /var/cache/apt/archives/libnvidia-gl-418_418.56-0ubuntu1pop1~1558036981~18.04~059304e~dev_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Installing libnvidia-gl-410 does not help with installation.  Installing nvidia-340 does not help either.  Uninstalling both, does not help with nvidia-418 installation.  In dependency hell, and using apt.  I thought apt was designed to fix this...  It usually takes 10-15 minutes to get back to "unbrokeness" for each experiment.  Working with video drivers is still a royal PIA.

---

### Post by CatKiller on 2019-07-15
You definitely don't want to be *installing* 340. Your error message shows that it's the **nvidia-340** package that's messing up your 418 install. You should only be installing 410 if you want to *keep* 410. You need all the libraries, drivers and kernel modules to all be on the same version. Otherwise it doesn't work.

---

### Post by bdlabitt on 2019-07-15
All the way back to nouveau again.  I was just about to start a support ticket on System76.  I then tried this from the command line:
```
$ sudo apt-get install system76-driver-nvidia
``` did the installation completely.  This is supposed to install the latest supported Nvidia driver (from System76).  It worked!  [Solved]  I tried doing this originally, while in synaptic, with the same package and it failed spectacularly.

No broken packages!  Updated to 418.56, which is good enough for me.  Apparently the other packages were not complete - or they made faulty assumptions about where one started from.  All good now.

---

### Post by CatKiller on 2019-07-15
Awesome! Glad you got it working.

You mark the thread solved with the Thread Tools at the top of the page, which should help people to find solutions that work.

---

