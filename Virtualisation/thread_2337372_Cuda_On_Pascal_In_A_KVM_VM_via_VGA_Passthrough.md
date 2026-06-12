---
title: "Cuda On Pascal In A KVM VM via VGA Passthrough"
date: 2016-09-17
forum: Virtualisation
---

### Post by redger on 2016-09-17
I've just purchased a new Pascal video card, in part for deep learning applications. I wanted to be able to use the card in a VM (because this all runs on my one and only server along with lots of other stuff including windows games)
BUT I didn't want the card to attach to my monitor (I've run out of ports on the monitor on my desk), I want to address the vm using Spice as "normal" for a vm

Initially I tried installing from the repositories, but that just resulted in blank screens ... not very helpful, so experimented until i could get it to work

These 2 links were key for me .. plus some other general investigation and experimentation
[http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html]("http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html")
[https://www.pugetsystems.com/labs/hpc/Install-Ubuntu-16-04-or-14-04-and-CUDA-8-and-7-5-for-NVIDIA-Pascal-GPU-825/]("https://www.pugetsystems.com/labs/hpc/Install-Ubuntu-16-04-or-14-04-and-CUDA-8-and-7-5-for-NVIDIA-Pascal-GPU-825/")

This assumes you are able to create a VM and pass a video card to it. In my case I created a kubuntu vm using virt-manager (libvirt), WITHOUT passing the video card initially.
I used the q35 motherboard and UEFI bios ... which meant the VM needed to be modified BEFORE the install ( extra check-box on last dialog of virt-manager create)

Then, once the vm was installed, I shut it down and used **virsh edit** to go in and change the xml.
Add this at the top (replace the existing first line), it allows you to send arguments directly to qemu, which we need because Ubuntu's version of libvirt is just a little too old
```
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
```

Then add these lines just before the </domain> tag at the end```
  <qemu:commandline>
    <qemu:arg value='-cpu'/>
    <qemu:arg value='host,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1fff,kvm=off,hv_vendor_id=some4321text'/>
  </qemu:commandline>
```
Note that the "hv_" parameters are Windows specific "enlightenments" ... I just add them for consistency when creating vms for nvidia gpu passthrough. You only NEED the "value=....,kvm=off,vendor_id=some4321text" not the "hv_" elements.

Now you can attach the nVidia video card and restart the vm. The above qemu lines hide the hypervisor from the nvidia driver and add some windows performance optimisations (see above).

Once you have a VM, you've ensured the packages are up to date and it's running with the video card attached you'll need to blacklist the nouveau driver by creating a new file at **/etc/modprobe.d/blacklist-nouveau.conf**  with the following contents```
blacklist nouveau                                                                                                                                          
options nouveau modeset=0
```

The rebuild intiramfs by executing the following```
sudo update-initramfs -u
```

Now reboot so the nouveau driver is not loaded, and check after reboot with ```
lsmod |grep no
```

Download the latest nVidia driver from here [https://www.nvidia.com/Download/index.aspx?lang=en-us]("https://www.nvidia.com/Download/index.aspx?lang=en-us"). I saved the driver "run" file to **~/Downloads/cuda**NOTE that you will want to download the "run" version NOT the deb files !!

FROM THIS POINT FORWARD IT'S BEST TO SHUT DOWN THE WINDOW MANAGER (the gui) SO THERE ARE NO CONFLICTS. If using virt-manager gui there are menu options to send <ctl><alt><f2> etc., so do that to get to a command line and then execute one of the following (depending on the flavour you're running eg. KDE uses SDDM, Unity and Mate use LIGHTDM)```
sudo service sddm stop
sudo service lightdm stop
```
That should stop the display manager and your gui session so that the nvidia routines have a clear path to install without conflict

Now **MANUALLY** install nVidia driver. NOTE THAT OPTIONS ARE !!!!!CRITICAL!!!!!, other than the logfile name which you may want to change```
sudo sh NVIDIA-Linux-x86_64-367.44.run --no-opengl-files --log-file-name=~/Downloads/cuda/NVIDIA-driver-install.log --dkms -a
``` 

That should work and to have created a new "nvidia" module. There's an extra step though, for some reason the nvidia specific entries in /dev are not always created so you'll need the following code to run at startup (I created a new script and execute it from **/etc/rc.local**). The script contents (as supplied by nVidia in their cuda installation guide)```
#!/bin/bash

/sbin/modprobe nvidia

if [ "$?" -eq 0 ]; then
  # Count the number of NVIDIA controllers found.
  NVDEVS=`lspci | grep -i NVIDIA`
  N3D=`echo "$NVDEVS" | grep "3D controller" | wc -l`
  NVGA=`echo "$NVDEVS" | grep "VGA compatible controller" | wc -l`

  N=`expr $N3D + $NVGA - 1`
  for i in `seq 0 $N`; do
    mknod -m 666 /dev/nvidia$i c 195 $i
  done

  mknod -m 666 /dev/nvidiactl c 195 255

else
  exit 1
fi

/sbin/modprobe nvidia-uvm

if [ "$?" -eq 0 ]; then
  # Find out the major device number used by the nvidia-uvm driver
  D=`grep nvidia-uvm /proc/devices | awk '{print $1}'`

  mknod -m 666 /dev/nvidia-uvm c $D 0
else
  exit 1
fi
```

Now reboot and check that[LIST=1]
[*]The "nvidia" module is loaded (use lsmod |grep nv)
[*]The "nvidia" module is attached to the video card (use "lspci -vn")
[*]The nvidia devices have been created in /dev (use 'ls /dev/nv*)', you should see 3 nvidia entries
[*]Execute **cat /proc/driver/nvidia/version** and check the version of the nvidia driver loaded (should be the one you downloaded and installed
[/LIST]

If that all worked ok you're ready to install cuda itself

Download the latest cuda (I need the latest because I have a very recent model card) from [https://developer.nvidia.com/cuda-toolkit]("https://developer.nvidia.com/cuda-toolkit")  In my case I downloaded V8 beta (the latest at time of writing)

Once again it's probably best to shut the gui session down eg. sudo service lightdm stop) ... probably not necessary, but it's a whole lot better to be "safe" and maximise the probability of success.

Start by installing the dependencies for the nVidia components (thanks to Puget systems for this) ```
sudo apt install dkms build-essential ca-certificates-java default-jre default-jre-headless fonts-dejavu-extra freeglut3 freeglut3-dev java-common libatk-wrapper-java libatk-wrapper-java-jni  libdrm-dev libgl1-mesa-dev libglu1-mesa-dev libgnomevfs2-0 libgnomevfs2-common libice-dev libpthread-stubs0-dev libsctp1 libsm-dev libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxi-dev libxmu-dev libxmu-headers libxshmfence-dev libxt-dev libxxf86vm-dev lksctp-tools mesa-common-dev  x11proto-core-dev x11proto-damage-dev  x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev libgles2-mesa-dev 
```

Now install the toolkit and samples (note that the toolkit must be installed as root)```
sudo sh ~/Downloads/cuda/cuda_8.0.27_linux.run --silent --toolkit --toolkitpath=/usr/local/cuda-8.0 --override  --no-opengl-libs
sh ~/Downloads/cuda/cuda_8.0.27_linux.run --silent --samples --samplespath=~/Downloads/cuda/cuda-8.0_samples --override  --no-opengl-libs
```. I found it necessary to change the ownership of the samples with ```
sudo sh chown -R <me>:<me> ~/Downloads/cuda
```

Then we need to add the libraries to **~/.bashrc** by adding the lines```
export PATH=/usr/local/cuda-8.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64:$LD_LIBRARY_PATH
```

You might want to reboot again at this point, just be sure (no big deal since its a vm).

After rebooting. Open a new terminal session and
[LIST]
[*]check the path (echo $PATH)
[*]check that the toolkit installed ok by executing the following which should display toolkit information```
nvcc -V
```
[/LIST]

Assuming that worked ok, we can now compile all the samples

First we need to update some peculiarities of the nvidia supplied code (thanks to Puget systems for this code)```
# Fix Host config so GCC doesn't cause errors when compiling
sudo sed -i '/unsupported GNU version/ s/^/\/\//' /usr/local/cuda-8.0/include/host_config.h
# Fix hard coded driver id in Samples 
sudo find /usr/local/cuda-8.0/samples -type f -exec sed -i 's/nvidia-3../nvidia-367/g' {} +
```

Compile the samples (assuming you saved the downloads to ~/Downloads/cuda and used the above commands)```
cd ~/Downloads/cuda/cuda-8.0_samples/NVIDIA_CUDA-8.0_Samples/
make
```

Once that all completes (it takes a while, there are lots of them), execute```
~/Downloads/cuda/cuda-8.0_samples/NVIDIA_CUDA-8.0_Samples/1_Utilities/deviceQuery/deviceQuery
```. You should see a summary of the card like this```
~/Downloads/cuda/cuda-8.0_samples/NVIDIA_CUDA-8.0_Samples/1_Utilities/deviceQuery/deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

Detected 1 CUDA Capable device(s)

Device 0: "GeForce GTX 1070"
  CUDA Driver Version / Runtime Version          8.0 / 8.0
  CUDA Capability Major/Minor version number:    6.1
  Total amount of global memory:                 8112 MBytes (8505589760 bytes)
  (15) Multiprocessors, (128) CUDA Cores/MP:     1920 CUDA Cores
  GPU Max Clock rate:                            1785 MHz (1.78 GHz)
  Memory Clock rate:                             4004 Mhz
  Memory Bus Width:                              256-bit
  L2 Cache Size:                                 2097152 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(131072), 2D=(131072, 65536), 3D=(16384, 16384, 16384)
  Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 65536
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  2048
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
  Run time limit on kernels:                     No
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Domain ID / Bus ID / location ID:   0 / 2 / 6
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 8.0, CUDA Runtime Version = 8.0, NumDevs = 1, Device0 = GeForce GTX 1070
Result = PASS

```

At this point it's all done ! BE AWARE that the sample routines using opengl will fail

With any luck spice is still the main video driver, and the cuda routines are ready for use.

---

### Post by KillerKelvUK on 2017-06-08
Hey, sorry for the necropost but hoping you might be still getting reply alerts for this thread as I'm hoping you might be able to help with my current predicament?

I have a GTX 970 passthu to an Ubuntu 16.04.2 guest and am running the Nvidia 756 proprietry drivers with CUDA 8.0.  I've SSH access to the vm and can clearly see the GTX is being claimed by the nvidia driver and both the nvidia-smi and cuda's queryDevice binaries return accurate and expected results.  So as far as this goes everything is working...except I cannot for the life of me get a terminal login prompt on the monitor attached the GTX's HDMI out.  I use the server varient and so have no desktop installed, I get grub output to the monitor which is great but then a blank screen all the way but the OS is functional as like I say SSH works.

There are loads of posts about GTX 970 and blank/black screen and believe me I've tried every combination of suggested fixed but nothing seems to work.  Did you experience anything similar with your pascal cards that you could offer some advice around?

Lastly, thank you for posting this thread, it helped me get Cuda working and made that part rather simple.

---

### Post by redger on 2017-06-25
hi m8, have logged back in eventually :)

What is your use case ? The instruction above do not install any video drivers for the nvidia card .... so not expecting any output to turn up there. My use case was to access via Spice 

Have you install the full suite of nVidia drivers (your note implies you have ... just wanting to verify) ?

I haven't experienced this problem and imagine the posts you've already reviewed offer more insight than I have :)   Do you know where the terminal messages are going if not to the monitor ? Maybe create a test VM, similar but with desktop installed to see what it does differently - difficult to imagine this is a consequence of the CUDA install, seems more likely to be something about the nVidia drivers and the default terminal session.
Did the nVidia proprietary drivers install without error ?

---

### Post by redger on 2017-06-26
Follow up questions ... have you considered using a container rather than hardware virtualisation ? Much lower overhead. The card would need to be bound and unbound to vfio-pci as required. 
I considered the idea for a while when looking at LXD desktops .... but stopped when I discovered I would have to move to a non-LTS release of Ubuntu .... but based on your sig this is not an issue for you

---

### Post by KillerKelvUK on 2017-06-26
Hey redger, I was experimenting with mining ethereum, which has now moved into production using the aforementioned 970 as well as a newly bought 1070, if your interested these with overclock reach 49.7 MH/s, stock is around 43 MH/s.

I could work around the lack of TTY it was more about not being beaten which drove my posts :-) Originally I was installing the nvidia-375 driver package and then installing cuda via the network deb approach but now i'm just doing the full cuda run file (driver and toolkit), this wasn't the cause of my problems though just answering your query.

Turns out the problem is because of some poor support in the nvidia drivers for the efi framebuffer which when loaded from grub exposes an nvidia bug that requires a VGA console (however I suspect this isn't experienced by all, just a select luck few like myself). So switching from grub to the EFI Stub Loader resolved this and I get full TTY and DE support under my 970 and 1070 depending on my passthrough configuration.

I've not even started to look at passthrough with containers, would that require my host to load the nvidia modules for the cards or does vfio (or its container equivalent) stay?  Nice little research project next I think :-)

---

