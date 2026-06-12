---
title: "Machine will no longer recognize windows bootable USB"
date: 2018-04-16
forum: Windows
---

### Post by googeek on 2018-04-16
So, I think what may have happened was the whole MBR got messed with or something...windows was updating and she lost power....but my baby used to be dual boot and then one day I came home and started her up and she just beeped and screamed at me about no bootable devices. I managed to wipe her and install nix but now she won't recognize a windows bootable disk at all.(I know the drive works; it's the one I've used on her before and I've tested it on another machine) No matter how I configure bios.(she beeps crazily in BIOS) I'm scared to flash the bios. She's totally fine with nix 100 percent. Is there some basic  thing I'm missing?

---

### Post by yancek on 2018-04-16
While you are booted to Ubuntu, insert the usb in question and go to the /media/user directory and take a look at the contents.  If you don't understand, post the contents here using the ls -l command on the t directory or post an image.  If you've used the windows usb before, then you know how to set it to first boot priority in the BIOS, correct?

---

