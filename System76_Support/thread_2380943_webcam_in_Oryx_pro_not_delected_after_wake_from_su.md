---
title: "webcam in Oryx pro not delected after wake from suspend"
date: 2017-12-24
forum: System76 Support
---

### Post by monkeybrain20122 on 2017-12-24
Hi, as the title said the webcam is not detected  (e.g cheese and skype report there is no webcam) after laptop wakes from sleep (always detected in fresh session) Press fn + f10 it works again.

Before suspend
```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b5a7 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

After wake from suspend
```

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

The second device is missing.

OS is Ubuntu 16.04.3, it has a gtx1070 with Nvidia driver 387.26 

Is there a way to modify the script from [this thread]("https://ubuntuforums.org/showthread.php?t=2380045&p=13721671#post13721671") to wake up the webcam?

Thanks.

---

### Post by monkeybrain20122 on 2017-12-24
This is getting more intriguing. webcam apparently fails being detected only when waking up from the first suspense but after restoring it with fn+f10 it is detected when wakes up in subsequent suspenses.

This is what happens:

Shut down laptop, then power on, boot into a fresh session. Check webcam, it is detected. 

Now close the lid of the laptop to put it t sleep. Wait for 5-10 minutes, open the lid to wake up laptop. Check webcam, it is not detected, it is missing from lsub, skype and cheese report there is no webcam. 

Press fn+ f10, now webcam is detected again

Close the lid and put the laptop to suspense again and wait for 5-10 minutes then wake up the laptop. This time webcam does work.

In fact webcam is detected after all subsequent suspensses as long as the laptop remains in the same session (ie no reboot)

---

### Post by untrustytahr on 2017-12-25
FWIW,  I would just stick with the fn f10 toggle.  If you're really determined to break,...er, fix it, you could probably do a modprobe on the module to get everthing working again (probably uvcvideo).

---

### Post by monkeybrain20122 on 2017-12-26
I found same issue with logging out and logging in, webcam only fails to be detected for the first logout-login, after doing fn+f10 webcam is detected for subsequent logout-logins as long as the computer doesn't reboot.

---

