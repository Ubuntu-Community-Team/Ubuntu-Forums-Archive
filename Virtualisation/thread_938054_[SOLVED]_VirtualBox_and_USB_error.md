---
title: "[SOLVED] VirtualBox and USB error"
date: 2008-10-04
forum: Virtualisation
---

### Post by lian1238 on 2008-10-04
Hi guys

I've installed VirtualBox and love it! But can't get USB to work. With I go to settings, I get the following error.
```

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

```
 How do I enable USB?

Thanks.

---

### Post by howefield on 2008-10-04
Run the following command

```
echo "none /proc/bus/usb usbfs devgid=$(grep plugdev /etc/group | sed 's/plugdev:x:\(.*\):.*/\1/'),devmode=664 0 0" | sudo tee -a /etc/fstab
```

Taken from this thread

[http://ubuntuforums.org/showthread.php?t=828927](http://ubuntuforums.org/showthread.php?t=828927)

---

### Post by lian1238 on 2008-10-04
Thanks for the useful link!
Didn't work at first. I had to run **sudo /etc/init.d/vboxdrv setup** also.
Now it works like a charm! I can print now! I'm so happy, I danced around like a mad man. Woo hoo! :D

---

### Post by howefield on 2008-10-04
> **lian1238 said:**
> I'm so happy, I danced around like a mad man. Woo hoo! :D

Whatever floats your boat :D:D:D

---

