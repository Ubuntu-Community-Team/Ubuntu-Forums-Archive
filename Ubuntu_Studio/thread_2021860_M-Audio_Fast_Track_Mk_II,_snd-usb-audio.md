---
title: "M-Audio Fast Track Mk II, snd-usb-audio"
date: 2012-07-09
forum: Ubuntu Studio
---

### Post by hamnstar on 2012-07-09
Hi all, I tried installing a MBox mini2 (yes different from the DI box in the title...) and followed the below guide:
[http://www.zamaudio.com/?p=97](http://www.zamaudio.com/?p=97)
this had me compile a new snd-usb-audio kernel module.

after realizing that the driver listed there was old as dirt, tried modifying some of the source to get it to compile ---which it did----- but however it doesnt actually do anything, so when i modprobe'd it in, it still didnt work.

Now, as that was a borrowed soundcard, I thought I would just ditch it and pick up a M-Audio Fast Track II, as I've had good luck with M-Audio products so far.  However, I think i totally borked my snd-usb-audio module, and I dont know how to revert it...

sample from dmesg:

```
[ 3343.960043] usb 2-2: new full-speed USB device number 5 using uhci_hcd
[ 3344.422941] snd_usb_audio: Unknown symbol usb_alloc_urb (err 0)
[ 3344.422957] snd_usb_audio: Unknown symbol usb_free_urb (err 0)
[ 3344.422982] snd_usb_audio: Unknown symbol usb_alloc_coherent (err 0)
[ 3344.423004] snd_usb_audio: Unknown symbol usb_ifnum_to_if (err 0)
[ 3344.423037] snd_usb_audio: Unknown symbol usb_register_driver (err 0)
[ 3344.423084] snd_usb_audio: Unknown symbol usb_interrupt_msg (err 0)
[ 3344.423126] snd_usb_audio: Unknown symbol usb_submit_urb (err 0)
[ 3344.423149] snd_usb_audio: Unknown symbol usb_free_coherent (err 0)
[ 3344.423175] snd_usb_audio: Unknown symbol usb_driver_claim_interface (err 0)
[ 3344.423188] snd_usb_audio: Unknown symbol usb_control_msg (err 0)
[ 3344.423215] snd_usb_audio: Unknown symbol usb_set_interface (err 0)
[ 3344.423229] snd_usb_audio: Unknown symbol usb_deregister (err 0)
[ 3344.423246] snd_usb_audio: Unknown symbol usb_string (err 0)
[ 3344.423268] snd_usb_audio: Unknown symbol usb_get_descriptor (err 0)
[ 3344.423290] snd_usb_audio: Unknown symbol usb_unlink_urb (err 0)
[ 3344.423304] snd_usb_audio: Unknown symbol usb_reset_configuration (err 0)
[ 3344.423314] snd_usb_audio: Unknown symbol usb_kill_urb (err 0)
[ 3344.423324] snd_usb_audio: Unknown symbol snd_usbmidi_create (err 0)
[ 3344.423350] snd_usb_audio: Unknown symbol snd_pcm_format_name (err 0)
[ 3344.423363] snd_usb_audio: Unknown symbol snd_usbmidi_disconnect (err 0)
```

so basically, I knew just enough to tinker and make the problem worse :)

Help:confused: 

PS: Ubuntu Studio 12.04

---

### Post by hamnstar on 2012-07-09
SOLVED!!! I simply (read: painstakingly figured out how to) recompile the snd-usb-audio drivers from the ubuntu source (via repository), modprobed it back in and im back in business.

---

