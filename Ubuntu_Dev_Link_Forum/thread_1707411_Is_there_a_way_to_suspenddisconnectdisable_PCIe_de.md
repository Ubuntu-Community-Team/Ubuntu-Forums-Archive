---
title: "Is there a way to suspend/disconnect/disable PCIe device"
date: 2011-03-15
forum: Ubuntu Dev Link Forum
---

### Post by PocketHercules on 2011-03-15
I am working in a hardware development environment where I have a PCIe card that contains a reprogrammable FPGA on it.  The FPGA contains the PCIe core logic that talks to the bus, including relevant PCIe configuration information.  Whenever I need to reprogram the FPGA, the kernel panics, because the PCIe core logic talking to the bus was reprogrammed and for some brief moment in time, the cards PCIe link is in some unknown state.  Is there a way (i.e., some Linux commands or some other method) for me to be able to disconnect/disable the PCI device from the bus so that I can reprogram the FPGA, than reconnect/reenable the device after the FPGA has been reprogrammed?

Please assume that the configuration space of the PCIe device is identical before and after the FPGA is reprogrammed.  I just cannot guarantee what the bus sees in the "in-between" state.  Any help would be greatly appreciated.

---

### Post by Ibidem on 2011-03-17
'apropos pci' doesn't show anything really pertinent (setpci does other stuff), and Google seems to not know of a relevant tool.
I'd suggest 
```
sudo modprobe -r <driver>
##flash and wait
sudo modprobe <driver>
```

---

