---
title: "Server for GPU computing constantly losing driver connection"
date: 2016-10-16
forum: Server Platforms
---

### Post by mullba on 2016-10-16
I'm running Ubuntu Server 14.04 with Nvidia Driver 370 and Cuda 7.5.  It takes forever to get it set up and working (which is why I'm still on 14.04) and it will randomly have an issue with the driver that make it unusable.  Any reboot of the server has a chance of losing the ability to use the card.  I can use the server for weeks without issue, then reboot and the system won't recognize the card.  

Nvidia-SMI gives the following error:
    ```
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```

Running lspci shows the card is there and working fine. 
    ```
17:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev ff)
17:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev ff)
```

Again, the only solution I've found is reinstalling everything (including the OS) from scratch.

Any suggestions on how to fix this would be GREATLY appreciated.

---

