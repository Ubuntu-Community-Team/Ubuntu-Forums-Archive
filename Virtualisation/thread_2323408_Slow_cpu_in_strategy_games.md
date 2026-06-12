---
title: "Slow cpu in strategy games?"
date: 2016-05-05
forum: Virtualisation
---

### Post by lance12 on 2016-05-05
So I've been using a kvm gpu pass-through windows for about 4 months now and I've run into a problem. I've been able to play almost any game i want close to native speeds, except for strategy games. (rome total war, planetary annihilation, war for the overworld). 
 
my setup is:
mother board- Gigabyte   GA-990FXA-UD3
cpu- 6300 amd fx 6 core
host graphics- some old amd, not sure witch one
guest graphics- gtx 970

the guest os is on an Samsung ssd in qcow2 format.

my qemu code:

 #!/bin/bash

sudo qemu-system-x86_64 -enable-kvm -m 4G -cpu phenom,kvm=off \
-smp 4,sockets=1,cores=4,threads=1 \
-machine q35,accel=kvm \
-device qxl \
-bios /usr/share/seabios/bios.bin \
-vga none \
-drive file=/media/lance/windows/win-7.img,if=virtio,format=raw,media=disk \
-drive file=/dev/sdb,if=virtio,format=raw,media=disk \
-boot order=d \
-usbdevice host:0a5c:21e8 \-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=04:00.1,bus=root.1,addr=00.1,multifunction=on \
-rtc base=localtime \

let me know if I need to provide more info and any help or information would be greatly appreciated.

---

### Post by houstonbofh on 2016-05-05
What does the load look like on the Linux side?  I think you are "spending" more CPU on the Linux side then the 3 cores you have left.  The RTSs are more CPU then GPU in many cases.

---

### Post by lance12 on 2016-05-05
So using top from my linux side my linux uses very little cpu. but the qemu task uses any where from 6% to 140%(?) but sits around 20%. this is just on start up and idle of my windows so maybe something is wrong with my set up?  on my windows side i see it using 0-15% cpu on idle.

When playing dungeons 2 my top shows 360% cpu by the qemu task, and my windows task manager shows 60% cpu.

---

### Post by houstonbofh on 2016-05-05
If you have 6 actual cores, you can go to 600% and be fully loaded.  If it is hyper-threading, or has the AMD shared fpu in Bulldozer cores, you may have half that.
Try setting it to dual core and see if it clears up.

---

### Post by lance12 on 2016-05-06
Okay, so I tried setting it to a duo core and that didn't help much. Then I switched it to use all 6 cores for shits and giggles and it actually worked. for now. so it shows qemu using around 400% from top while playing the game and the game is smooth and actually working. so far i've only tested this on one game so I plan to do more testing but my guess is that setting it to 6 cores just gives the vm access to all of the core with out locking them up or anything. so the vm and the host share it. thats what I've gathered so far, I could be wrong. 

would changed the threads do anything?  I'm also thinking about upgrading to the fx 9590 (8 core), how much would that affect the vm vs using the 6300 (6 core) ?

---

### Post by houstonbofh on 2016-05-06
More CPU is more CPU...  Never a bad thing. :)  I am happy with KVM on my FX-8320E.

---

### Post by lance12 on 2016-05-06
That was my other thought was to just go for the 8320, its a lot cheaper and not far behind on performance. I'm surprised by the number of people doing the kvm pass-through. 

Well thanks for the help :) and I'll update this if I find anything new.

---

