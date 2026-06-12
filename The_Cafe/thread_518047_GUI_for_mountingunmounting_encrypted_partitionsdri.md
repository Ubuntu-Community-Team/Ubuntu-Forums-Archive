---
title: "GUI for mounting/unmounting encrypted partitions/drives?"
date: 2007-08-05
forum: The Cafe
---

### Post by bash on 2007-08-05
I have an external USB Harddrive which I encrypted with the "standard" Linux encryption sheme (luks aes). 

Now I do have 4 partitions on that drive, so I get 4 nice pop-ups when I plug the harddrive into my computer. But for one all pop-ups say the same thing. So there is no way for me to tell for which partition im currently asked a password for.

And more importantly, lets say I plug the USB harddrive and only mount partition 1. Now maybe 20 minutes later I also want to mount partition 2. Now I can either enter a (for me) tedious set of commands in the CLI or if I want to do it graphically I have to first unmount all devices, then plug the harddrive out and in again, wait for the pop-ups to come again and then mount the partitions I want.

As you see this is quite an unfriendly and unconvenient process. So I think something like a GUI manager for encrypted partitions/devices should exists. Maybe similar to the network manager. Where you got a nice tray icon and you can select which partitions or drives you want to mount or unmount.

I tried looking for something like that but the closest I could find is [this](http://sourceforge.net/projects/cryptomaster). But its buggy, old, broken and doesn't seem to be developed anymore. So as I know there are quite a few capable coders here or people who want to do something I think this could be a nice little program to write.

---

