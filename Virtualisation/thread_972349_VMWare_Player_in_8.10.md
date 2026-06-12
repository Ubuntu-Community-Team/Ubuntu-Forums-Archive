---
title: "VMWare Player in 8.10"
date: 2008-11-05
forum: Virtualisation
---

### Post by ve7mdl on 2008-11-05
Hi all,

I installed VMWAre Player 2.5.0 in Ubuntu 8.04 (64-bit) and was able to run a couple of Windows VMs very well.  When I upgraded to 8.10, I can't seem to get a CTRL-ALT-DEL to the virtual machine.  I have tried to disable the key combinations in Keyboard Shortcuts, but it looks like Ubuntu does not pass CTRL-ALT-DEL on to the VM.  Is there anything I can do to fix the problem?

                           ....Erik.

---

### Post by ve7mdl on 2008-11-06
Problem solved.

The DEL key on the numeric key pad (with CTRL-ALT) works!

---

### Post by pbneves on 2008-11-08
I have the same problem in my laptop.

But i haven't the enter key on the numeric keypad!!

Any help will be nice.

Thanks

---

### Post by hurtquake on 2008-11-08
Try Ctrl+Alt+PrtSc

---

### Post by techmba on 2008-11-08
I upgraded to 8.10 on a HP nw8440 laptop and now i have 3 issues with VMplayer 2.5 (with WinXP VM):

1. CTl-Alt-Del or Ctl-Alt-Ins/Prt screen does not work. The only thing that works is to hook in an external USB key board and then login. Is there anything else i can do to login w/o using an external keyboard ? 

2. USB drives are no longer getting mounted in WinXP. The behavior that is see is that the USB drive gets discovered and after a few seconds, the drive gets mounted back on the Ubuntu host. I searched the forums but did not see any posts. The usb config entries in the vmx file are:

usb.present = "TRUE"
usb.autoConnect.device0 = ""
usb.autoConnect.device1 = ""
usb.generic.autoconnect = "TRUE"
usb.generic.skipSetConfig = "TRUE"
usb.autoConnect.device2 = ""
usb.autoConnect.device3 = ""

This was working fine in Ubuntu 8.04 + VMplayer 2.0.5. Could you please recommend any trouble shooting steps ? 

3. Finally, arrow keys have stopped working. I'll search the forums to see if there are any workarounds. But if you can please point me to the right solution, i'd greatly appreciate it.

Thanks!

---

### Post by techmba on 2008-11-08
I found the solution for the Ctl-alt-delete issue and the arrow key issue at [http://communities.vmware.com/thread/177688](http://communities.vmware.com/thread/177688) :) (Thank you - BassKozz)

The solution is to add "xkeymap.nokeycodeMap = true" to ~/.vmware/config or to /etc/vmware/config

echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config

Now to fix the USB external hard drive issue ...

---

### Post by Fhernd on 2008-11-15
Hi!

If 'echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config' does not exist in the user folder.

Add the line '*xkeymap.nokeycodeMap = true*' to '*config*' file through:

Alt + F2 -> *gksu gedit gksu gedit /etc/vmware/config*

Bye!

---

