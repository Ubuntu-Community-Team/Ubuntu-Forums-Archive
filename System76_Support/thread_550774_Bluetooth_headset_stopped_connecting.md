---
title: "Bluetooth headset stopped connecting"
date: 2007-09-14
forum: System76 Support
---

### Post by imhavoc on 2007-09-14
About the same time I got my Darter Ultra 2 notebook, I ordered a bluetooth headset to use with it and my phone. (I ordered one that would pair with multiple hosts.)

The system worked well, until about the time of the last kernel upgrade.

here are the results of attempting to connect to the headset:

 - the headset pairs fine. It shows up when scanned for.
 - running [FONT="Fixedsys"]btsco -v MACaddress[/FONT] gives the following results:
```

btsco v0.42
Error: control open (hw:1): No such device
Error: Can't find device. Bail

```
 - running [FONT="Fixedsys"]sudo modprobe snd-bt-sco[/FONT] results in:
```

FATAL: Error inserting snd_bt_sco (/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/snd-bt-sco.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
 - after this, [FONT="Fixedsys"]dmesg | tail[/FONT] shows:
```

[  160.008000] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[  160.008000] snd_bt_sco: Unknown symbol snd_ctl_add
[  160.008000] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[  160.008000] snd_bt_sco: Unknown symbol snd_pcm_new
[  160.008000] snd_bt_sco: disagrees about version of symbol snd_card_register
[  160.008000] snd_bt_sco: Unknown symbol snd_card_register
[  160.008000] snd_bt_sco: disagrees about version of symbol snd_card_free
[  160.008000] snd_bt_sco: Unknown symbol snd_card_free
[  160.008000] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[  160.008000] snd_bt_sco: Unknown symbol snd_ctl_new1
[  160.008000] snd_bt_sco: disagrees about version of symbol snd_card_new
[  160.008000] snd_bt_sco: Unknown symbol snd_card_new
[  160.008000] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[  160.008000] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[  160.008000] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[  160.008000] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[  160.008000] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[  160.008000] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed

```

I can still use Bluetooth to connect to the phone with a data link and move files on and off, but I can't connect to the Bluetooth sound device.

Any ideas?

---

### Post by raijinsetsu on 2007-09-14
Try reinstall that btsco program. It looks like it was compiled off of an older kernel.

---

### Post by imhavoc on 2007-09-14
The same version is installing.

what's the easiest way to roll back the kernel and all of the libraries?... or is that going to just make a mess of things?

---

### Post by raijinsetsu on 2007-09-14
Your previous kernel should not have been over-written. You have to change your default grub session from your new kernel to you old kernel. This can be done by editing "/boot/grub/grub.conf" and changing the argument for "default=X". X should probably be 1 before you change it, and 3 after. 2 and 4 should be recovery consoles. Then you can run "grub-install /dev/hda" assuming that's your boot device.

Hope this helps.

---

### Post by imhavoc on 2007-09-14
odd.... what's the kernel that shipped with my Darter one month ago? 2.6.20-??

---

### Post by imhavoc on 2007-09-16
Somehow, the 2.6.20-15 image got removed when the system updated to 2.6.20-16. I don't recall deleting them, and I'm not in the habit of removing that kind of stuff.

Anyway, I restored the two ...-15 files, but when I boot to the -15 image, the Xserver complains and won't start.

I did manage to get a command line, and the bluetooth headset does connect fine with the -15 kernel booted.

thoughts on the best way to proceed?

---

### Post by raijinsetsu on 2007-09-17
What does Xserver complain about?

---

### Post by imhavoc on 2007-09-25
today's update fixed the broken bluetooth module. "magically," my headset connected the first time I tried it today.

all is well!

---

### Post by thomasaaron on 2007-09-26
Hmmm...

Updates: You've gotta hate them. You've gotta love them.

---

### Post by imhavoc on 2007-09-26
Most of the pain I've had with Linux over the years has been with new kernels breaking things -- especially VMware.

I seriously toyed with "pinning" all of my kernel and kernel-related modules to keep them from getting updated a week (or so) before the update that broken my bluetooth.

I do enjoy the added benefits that come with updated kernel releases, but I have found that the benefits of minor updates have very rarely been worth the pain of having to recompile the custom modules that they break.

On the flip side, I don't have to wait 6-10 months after a major OS release for "Service Pack 2" to make it usable!

---

