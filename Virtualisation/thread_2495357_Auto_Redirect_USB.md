---
title: "Auto Redirect USB?"
date: 2024-02-15
forum: Virtualisation
---

### Post by Quarkrad on 2024-02-15
I have set my wife up a qemu vm running ubuntu mate on which I have installed Zoom for her.  On her ubuntu 22.4 host (this could be confusing in that both the host and the vm are ubuntu mate 22.04) I have a script that runs a bash sh file that launches the vm, which in turn auto starts Zoom.  The bash sh file on the host looks like:

```
#!/bin/bash
export LIBVIRT_DEFAULT_URI="qemu:///system"
/usr/bin/virsh start ubuntuvm
/usr/bin/virt-viewer -f -w -a ubuntuvm
```

Currently this works as I would like - the script launches a *full screen* Zoom screen for her.  My Desktop does not have a webcam and I have just installed one and it works OK.  My issue is that by launching vm this way I am not redirecting the relevant host usb port so the vm does not see the webcam.  In virtual manager I can see that the webcam usb port is called *USB C270 HD WEBCAM [046d:0825] at 1-3 *- I was just wondering if there is *some magic* that can be added to my bash sh file that would auto connect/redirect this usb port?  This is not a show stopper in that my wife could redirect manually, but if possible, I would like it all to be auto if possible.

---

