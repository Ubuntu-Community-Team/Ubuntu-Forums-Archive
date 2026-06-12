---
title: "VirtualBox Mouse Capture"
date: 2008-04-28
forum: Virtualisation
---

### Post by haloony on 2008-04-28
Hey Guys,
I am trying to test Xfce, and I decided to test it out on Xubuntu. I thought that this was the perfect opportunity to try out virtualization. So, I downloaded a Xubuntu 8.04 iso. After some tweakage and troubleshooting, I got it to run and boot from within VirtualBox. However, I soon realized that I could not control the mouse. The keyboard, on the other hand, worked fine. I did some research on the issue, and I found out that mouse capture does not work without installing guest additions. After more obstacles, I was able to install the guest additions by running ```
sudo sh ./VBoxLinuxAdditions.run
```
After the installation process, I needed to restart, and I did. However, after rebooting, I had to remount the xubuntu image, and this reset the virtual machine. This resetting, undid, I believe, everything I did. Even with all this, I think I was doing something fundamentally wrong the entire time.
    I could not mount the guest additions iso because the Xubuntu installation iso was already mounted. So, to get around this, I used an online storage service, and transferred the iso. I also had to do all of this with the keyboard because the mouse was not working at all. Is the mouse supposed to work to some degree, and that the guest additions changes the way it works, or is it that the guest additions enables the mouse altogether. Any feedback will be appreciated

---

