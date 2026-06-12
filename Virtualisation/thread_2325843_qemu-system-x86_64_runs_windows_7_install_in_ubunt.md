---
title: "qemu-system-x86_64 runs windows 7 install in ubuntu 15.04 but not in 15.10 or 16.04"
date: 2016-05-26
forum: Virtualisation
---

### Post by PhilTroy on 2016-05-26
Hi!

I have been using qemu - kvm for several years in different versions of ubuntu (lubuntu).  I am trying to migrate from 15.04 to 16.04 and am having a problem.  In particular, on my machine (a samsung series 9 with dual core i7 processor and 8gb ram) the following commands worked in 15.04 but do not work in 15.10 and 16.04.  FYI, I tested them on a clean machine, where I have created a 60GB image file in its own partition..  In particular, I am using the command to start installing windows 7 and it works in a clean install of 15.04 (yesterday) but not in 15.10 (yesterday) or 16.04 (the day before).  I do not get any error messages in my xterminal when running this and do not know how to check for windows error messages.  




```
echo "*** Installing windows 7 virtual machine - Step 2"


echo "*** Try command for slow mouse"
export SDL_VIDEO_X11_DGAMOUSE=0


echo "*** # Note: Remember that when using spicec, you need to specify the tcp address of the host, and not the guest"
sudo qemu-system-x86_64 \
  -enable-kvm \
  -machine pc,accel=kvm \
  -cdrom  /home/Archives/Software/OperatingSystems.Windows7HP.64/Windows7HP64_Install.iso \
  -boot d \
  -net nic,macaddr=56:44:45:30:31:34 \
  -net user \
  -cpu host \
  -vga qxl \
  -spice port=5900,disable-ticketing \
  -uuid 8373c3d6-1e6c-f022-38e2-b94e6e14e170 \
  -smp cpus=2,maxcpus=3 \
  -m 6144 \
  -name DrPhilSS9AWin7VM \
  -hda /mnt/Windows7Image/Windows7Guest.img \
  -localtime \
  -k en-us \
  -usb \
  -usbdevice tablet&
sleep 10
spicy --host 127.0.0.1 --port 5900
```
[B]
With respect to the xml for this virtual machine, I have not been able to find any, and am wondering whether xml is not created since I am passing all of the parameters on the command line.  I do know that I did not create xml for this virtual machine.

[/B]Phil

---

### Post by MAFoElffen on 2016-05-26
First, go ack to Post #1 > Advanced Edit > Highlight your output and select the "#" code tag icon to enclosed your output in code tags. This is a forum policy for all output and commands. Saves space and makes it easier to follow.

Next, p[lease post your xml config file for that VM guest (within codes tags).

---

### Post by PhilTroy on 2016-06-04
Hi!

I formatted the code as requested - is there anyone who can help me with this?

FYI, by creating the virtual machine under 15.04, I am now able to run it in 16.05, but, it would be helpful to be able to create the virtual machine (i.e. an installation of windows 7 into an image file) directly in 16.04.

Thanks . . .

Phil

---

### Post by MAFoElffen on 2016-06-04
Thanks.

To be clear at what you are saying: 
- You are installing Windows (version unknown) as a QEMU guest to run on 16.04(?)
So you say you can install under 15.04 ... but not under 15.10 nor 16.04. Right?

Is that QEMU (with KVM enabled) or full KVM?

Could you post something about "the how" you are trying to install? I see you qemu install script ... pointed to an install iso of "Windows7HP64_Install.iso" ... <-- Is that an HP specific iso?

---

### Post by PhilTroy on 2016-06-05
Hi!

It is Windows 7 Home Premium 64 bit with Service pack 1

I am doing the install from the command line using the code included in my first message, i.e. by directly invoking qemu-system-x86_64 with a list of parameters.  I did it this way as it makes it easy to replicate exactly.  Before running that code I created a 60gb image file ( [COLOR=#000000][FONT=Ubuntu Mono]/mnt/Windows7Image/Windows7Guest.img ).

Once I successfully install under 15.04, I can and do totally reinstall Lubuntu with 16.04 and I am able to run windows 7 from that image file with a similar qemu-system-x86_64 command.

If I start in 15.10 with a clean slate, or in 16.04 with a clean slate, the windows install freezes right after the loading files screen leaves and the colorful windows screen displays, before prompting me for the input needed to continue windows 7 installation.

Thanks . . .

Phil[/FONT][/COLOR]

---

### Post by Toolybird on 2016-06-05
Confirmed. I'm hitting this too..

The problem is due to the qxl graphics card. if you change it to cirrus then the Windows 7 installation will proceed without hanging.

Of course, this is unsatisfactory as I'm trying to get away from VirtualBox and need the qxl graphics for the best kvm graphics experience.

This seems relevant:

[http://serverfault.com/questions/776406/windows-7-setup-hangs-at-starting-windows-using-proxmox-4-2](http://serverfault.com/questions/776406/windows-7-setup-hangs-at-starting-windows-using-proxmox-4-2)

It would be interesting to see what's different in your xml for the vm created in 15.04 compared to the one in 16.04.

---

### Post by PhilTroy on 2016-06-06
Hi Toolybird

Thank you very much for responding.

I am wondering whether it is possible to install using cirrus and then change it after the installation is done?  Would you please let me know if you try that?

Also, if you tell me how to obtain an xml file of my configuration I will (but it is not clear to me if there is one since I used the command line to use qemu/kvm

THANK YOU VERY MUCH!

Phil

---

### Post by Toolybird on 2016-06-06
I've tried installing with cirrus then changing it back to qxl. Sadly, it still hangs in the same spot.

Now that I think about it, you are running qemu directly from the command line so there is no xml as per typical libvirt setups. (I'm using virt-manager gui).

It's still interesting that you can create an image under 15.04 and run it successfully under 16.04. It suggests that once the qxl driver is installed in the guest, everything is fine. I can't find a way to install the qxl driver when the qxl hardware is not present. Apparently, it is possible to create a Windows 7 installation iso with 3rd party drivers pre-loaded. I might give this a shot.

---

### Post by PhilTroy on 2016-06-06
Hi Toolybird

Thanks again for responding.

On your side, you might wish to try the approach used to change disk drivers to virtio.  If I remember correctly, you install with the non-virtio drivers.  Then you restart the virtual machine with a second (typically small) virtual disk drive specified to use virtio, and with a cd-rom i(when using the command line it is very easy) with the drivers for virtio.  When you login, you go into device manager and set the drivers for the second disk to vitio.  On the third boot, you tell qemu that both drives are to use virtio.  On the fourth boot, you remove the second drive.

FYI, I have posted a bug report for this problem in ubuntu - maybe you can try to find that and indicate you have had a similar problem.  It really needs to be fixed.

All the best . . .

Phil

---

### Post by Toolybird on 2016-06-06
Okay, I have found a workaround. It's not ideal but it works for me:

1.  install Win 7 with cirrus graphics, shut down vm
**2.  add a second graphics adapter as qxl**
3.  boot vm and install the qxl driver
4.  shut down vm and remove the cirrus adapter

PhilTroy, you should be able to adapt your procedure to use this method.

In summary, there is a bug somewhere in qxl that prevents booting Win 7 when the qxl driver is not installed.

---

### Post by thomas-kreuzer on 2016-07-28
> **Toolybird said:**
> In summary, there is a bug somewhere in qxl that prevents booting Win 7 when the qxl driver is not installed.
This is a bug in qemu [1,2] and affects all vga drivers, except cirrus

1: [https://bugs.launchpad.net/qemu/+bug/1581936](https://bugs.launchpad.net/qemu/+bug/1581936) 
2: [http://git.qemu.org/?p=qemu.git;a=commit;h=94ef4f337fb614f18b765a8e0e878a4c23cdedcd](http://git.qemu.org/?p=qemu.git;a=commit;h=94ef4f337fb614f18b765a8e0e878a4c23cdedcd)

---

