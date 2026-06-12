---
title: "How can I make my Ubuntu Touch mounted as writable?"
date: 2015-12-12
forum: Ubuntu Phone and Tablet
---

### Post by ZICODIAN on 2015-12-12
My Ubuntu Touch installation on the Aquaris E4.5 is set in developer mode. When I run the command [FONT=courier new]sudo mount -o remount,rw /[/FONT] I am presented with the following message:

```
mount: / not mounted or bad option


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

Looking at the [FONT=courier new]dmesg[/FONT] output, I see the following message:


```

dmesg: read kernel buffer failed: Operation not permitted

```

What should I do? I need to get [FONT=courier new]apt[/FONT] installs working.

---

### Post by handaxe on 2015-12-13
Connect your phone to a host computer via USB, with Developer Mode **AND** the screen  unlocked, then fire up a terminal on your computer and execute

```
phablet-config writable-image
```

Your phone will be in RW mode **AFTER** a reboot and you should be able to install packages for testing.

As always, note that rw is not a recommended path and you should mentally accept you may have to reflsh your device at some point if things "go south".

---

### Post by ZICODIAN on 2015-12-20
Hey, thanks for the details there. I've got the phone in developer mode and have it connected via USB with the screen unlocked and I'm running into difficulty with [FONT=courier new]phablet-config writable-image[/FONT]. Specifically, I get the following message:

```
>phablet-config writable-image
error: device not found
error: device not found
Traceback (most recent call last):
  File "/usr/bin/phablet-config", line 423, in <module>
    main()
  File "/usr/bin/phablet-config", line 420, in main
    args.func(adb, args)
  File "/usr/bin/phablet-config", line 143, in _handle_writable_image
    if not is_remote_root(adb):
  File "/usr/bin/phablet-config", line 107, in is_remote_root
    return adb.shell("id -ru").strip() == "0"
  File "/usr/lib/python2.7/dist-packages/phabletutils/device.py", line 144, in shell
    output = check_output(self._cmd % cmd)
  File "/usr/lib/python2.7/dist-packages/phabletutils/device.py", line 30, in check_output

```

When I run [FONT=courier new]adb devices[/FONT], I note that the phone isn't listed. Would you have any ideas on how to proceed? I'm on ADB 1.0.32 with Ubuntu 14.04 and the phone is on Ubuntu 15.04 - armhf (20151118-205525).

---

### Post by ZICODIAN on 2015-12-20
Ok, so it appears the ADB server version was too old. I updated it and the command ran. However, I still don't seem to be able to mount the device as writable. When I run the command [FONT=courier new]sudo mount -o remount,rw /[/FONT] I am presented again with the following message:

```
mount: / not mounted or bad option




       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

Would you have any thoughts on what I could try next?

---

### Post by handaxe on 2015-12-20
The phablet-config command should have done it and it should then boot as writable. No mounting needed.

---

### Post by ZICODIAN on 2015-12-20
Ah, I see you're quite right. [FONT=courier new]sudo apt-get[/FONT] seems to be working just fine now. Thanks!

---

