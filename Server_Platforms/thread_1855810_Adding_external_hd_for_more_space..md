---
title: "Adding external hd for more space."
date: 2011-10-07
forum: Server Platforms
---

### Post by Mattwilkinson on 2011-10-07
Hi,

Is it possible to install an external hard drive on my ubuntu server so i can have more space for websites? The internal hd of my server is really small and would like more space.

Thanks

---

### Post by mikewhatever on 2011-10-07
Does the serve have a USB port? If so, I don't see why not. Create a Linux partition, auto-mount through fstab, plug it in.

---

### Post by DavidBeijer on 2011-10-07
I currently have such a setup running, and it works quite smoothly. Upon connection it just shows up in /dev as sd*, and I have it mounted to /home/media. This setup is fast enough to stream HD movies through samba, so I would not expect any troubles for websites.

---

### Post by WasMeHere on 2011-10-07
default: If the standard USB 2.0 interface is fast enough, that fine. I agree with the previous posts.

1: If you need higher transfer rates of your data to and from your external hard disk, consider eSATA. If you have an extra esata connection on your motherboard, get an eSATA connecting 'card' (it is only a plate with one or two eSATA connectors).

I get about 3 times higher speed for regular hard disks with eSATA compared to USB 2.0.

2: Maybe there is space for a second standard internal disk in your computer case.

3: If you want to be really modern, try a USB 3.0 disk, but that requires a PCI card unless you have a new computer equipped with USB 3.0.

---

### Post by a2j on 2011-10-07
usb would work if that is not a production server hosting websites.
just mount it to /path/to/your/websites and you should be good to go.

---

