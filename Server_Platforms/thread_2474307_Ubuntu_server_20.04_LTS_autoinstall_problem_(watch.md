---
title: "Ubuntu server 20.04 LTS autoinstall problem (watchdog did not stop!)"
date: 2022-04-26
forum: Server Platforms
---

### Post by blendski on 2022-04-26
Hello,
I have a problem related to Ubuntu server 20.04 and unfortunately I am not able to handle it.
I am trying to automate the process of installing ubuntu on a single board computer and for this purpose I decided to use a local "cloud-init" (modified for ubuntu - autoinstall):
[https://ubuntu.com/server/docs/install/autoinstall](https://ubuntu.com/server/docs/install/autoinstall)
Based on the documentation, I prepared the user-data file and then repackaged the Ubuntu server 20.04 image using the script:
[https://github.com/covertsh/ubuntu-autoinstall-generator](https://github.com/covertsh/ubuntu-autoinstall-generator)
After repackaging I got a custom iso image and uploaded it to a flash drive.
After booting from the pendrive, the installation process starts correctly and the system is installed along with the guidelines from the "user-data" file. Unfortunately, after the installation is complete, an error message is displayed requiring a manual reboot of the device (attachment).
```

[COLOR=#006400][FONT=Monaco]watchdog[1]: watchdog0: watchdog did not stop!
shutdown[1]: Could not detach loopback /dev/loop1: Device or resource busy
shutdown[1]: Failed to finalize loop devices, ignoring[/FONT][/COLOR]

```
I'd like to add that this is exactly the moment when, during the installation of a standard ubuntu, a message appears asking to pull out the memory stick and press "Enter" to continue.
Has anyone experienced this and is there any way to get rid of it or to restart the computer automatically after the installation is complete?

---

