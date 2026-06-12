---
title: "HowTo: Disable Ubiquity from bootup on liveUSB"
date: 2015-02-23
forum: Tutorials
---

### Post by inexplikibled on 2015-02-23
Hello all. In searching the web for a revertible method of disabling Ubiquity from auto starting on boot of a live USB stick, I have come up empty... So here's what I figured out on my own and it works in Xubuntu 14.10 32bit. 

Before I begin, these are the steps I personally took to do this. Please reply if you have done this using these steps on any other Ubuntu variant, and/or any other architecture. This is for my future reference and for anyone else who finds it useful!

1. Create your bootable USB with the Startup Disk Creator application in Ubuntu or a variant and select the option for Stored In Reserved Extra Space. It doesn't matter how large you make this.
2. Insert you newly created live USB drive in a computer capable of booting from USB and select the startup option in your computer's boot menu for your usb drive. Boot into Xubuntu.
3. At the Install screen, click Try Xubuntu
4. Once you are in the desktop, open a terminal and enter: ```
sudo mv /etc/init/ubiquity.conf /home/xubuntu/.
```
This will move the Ubiquity startup script from /etc/init/ and place it in the live user's home folder so that the changes can be reverted.
5. Reboot and confirm that Xubuntu boots straight to the desktop.
Done!

To restore ubiquity on boot:
1. Boot into the live desktop again, if you're not there already.
2. Open a terminal and enter: ```
sudo mv /home/xubuntu/ubiquity.conf /etc/init/.
```
This will restore default bootup behavior to automatically run Ubiquity at boot.

Thats all!

---

