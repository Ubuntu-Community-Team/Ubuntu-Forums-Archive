---
title: "VirtualBox 4.0.8 doesn't detect usb devices"
date: 2011-06-16
forum: Virtualisation
---

### Post by cybo on 2011-06-16
i installed virtualbox and windows xp in it. unfortunately it doesn't show any of my usb devices. i looked up online and it seems to be the problem with the latest realease. the problem that i'm having is that i can't understand any of the solutions since i'm not very good at working with ubuntu. it is sort of a hobby for me. is there anybody out there facing the same problem? would you be kind and offer some help or a simplified explanation. i would really appreciate it.

thanks.

---

### Post by JKyleOKC on 2011-06-16
First, open a Terminal window and enter this command: ```
grep vboxusers /etc/group
```You should see something like this as a response:
```
vboxusers:x:122:jk
```However the number may be different, and the "jk" (my user name) will be replaced by your own user name if all is well. If there's nothing following the number, or no response at all, you'll have a bit more work to do.

That command simply looks into the "group" file searching for the default vbox group, which is normally created automatically when you install VBox. If there's no response at all, the group was not created; more troubleshooting will be required. If you get the response but your user name is missing, then you need to add yourself to the vboxusers group. Unfortunately I'm using Xubuntu rather than Ubuntu itself, and the commands dealing with users and groups are a bit different between the two window managers involved. I'm sure that someone else will chime in and tell you how, though.

If the command above does show that you're already in the vboxusers group, repeat it with "plugdev" instead of "vboxusers" to see if you're authorized to use USB devices. The chance are that you are, or they would not work in Ubuntu either.

A final thing to check involves the USB settings within the VM itself. Open Vbox, be sure the VM is powered down so that you have access to the settings, and open the USB dialog within the Settings area. It should have an area that lists the filters in use, which may be empty. If it is, click the topmost button in the stack of buttons immediately to the right of the list area, to create an empty filter. This should result in the USB devices appearing in the Devices menu when you start the VM.

I'm not using version 4 of vbox myself; I found its changes unattractive, so stayed with version 3, now up to 3.2.12. However I believe that the instructions I've given will still apply to your system...

---

### Post by cybo on 2011-06-17
@JKyleOKC
thanks for the help. my name wasn't added to the group. i had to do that and then created a new usb filter. nothing worked at first. i had to reboot my machine which made everything to work. thanks a lot, i really appreciate it.

---

### Post by JKyleOKC on 2011-06-17
You're quite welcome. Glad it worked!

---

