---
title: "virtmanager/libvirt//kvm/qemu/spice mouse side buttons not working in guest"
date: 2014-09-07
forum: Virtualisation
---

### Post by rperkins on 2014-09-07
Hello
thanks in advance.

[B]Is it possible to get the side buttons on a mouse to work within a guest of kvm/qemu  ?
[/B]
I am using virtmanager to create guests.  On the viewing host I have a mouse that has side buttons that allows me to go 'forward and back' in my browser history.
This does not work in the guests.  I have tried various mouse configurations and remote viewers ( vnc/spice ) .  usb passthrough is not a solution as the VM guests are not always on the same host I am sitting in front of.

I have been using 'xev' to verify that the mouse side buttons are not being registered in the guests.


This is what 'xev' generates when clicking a side button on the bare hardware.  The buttons are 8 and 9. Within a guest 'xev' generates nothing for these buttons
```

ButtonPress event, serial 37, synthetic NO, window 0x4600001,
    root 0x80, subw 0x0, time 256904747, (118,114), root:(183,166),
    state 0x10, button 8, same_screen YES

ButtonRelease event, serial 37, synthetic NO, window 0x4600001,
    root 0x80, subw 0x0, time 256904846, (118,114), root:(183,166),
    state 0x10, button 8, same_screen YES

```


I tried to find the latest source files for the relevant items but this is really gettting outside my level of skill
Here is some source for spice that seems to not include the side buttons.  
[http://cgit.freedesktop.org/spice/qemu/tree/ui/spice-input.c?id=8b3030114a449e66c68450acaac4b66f26d91416](http://cgit.freedesktop.org/spice/qemu/tree/ui/spice-input.c?id=8b3030114a449e66c68450acaac4b66f26d91416)
the qemu vmouse (ps2?) supports 3 buttons and a wheel through a dx? interface
[http://git.qemu.org/?p=qemu.git;a=blob;f=hw/input/vmmouse.c;h=d7b1c76f580a4a9acefa9be447c35516a800517b;hb=HEAD](http://git.qemu.org/?p=qemu.git;a=blob;f=hw/input/vmmouse.c;h=d7b1c76f580a4a9acefa9be447c35516a800517b;hb=HEAD)
qemu hid (usb) supports 3 buttons and a wheel through a dx interface ?
[http://git.qemu.org/?p=qemu.git;a=blob;f=hw/input/hid.c;h=148c003bb29d91f940f024e099b64c8c8581b167;hb=HEAD](http://git.qemu.org/?p=qemu.git;a=blob;f=hw/input/hid.c;h=148c003bb29d91f940f024e099b64c8c8581b167;hb=HEAD)

---

### Post by KillerKelvUK on 2014-09-08
I don't think QEMU emulates anything other than the PS/2 interface for mouse and keyboard...from what I've read the PS/2 interface spec only caters for LEFT,MIDDLE, RIGHT buttons.

---

### Post by rperkins on 2014-09-08
Thanks for the response.  Yes I think it is 3 buttons plus the wheel.  I can get the wheel to work.

I did find a workaround to get a 'back' button working in the browser.  I had to give up the 'middle' mouse button, which  would paste my selection into the active window.
[B]I really would like to get all the buttons working so any additional comments would be great.
[/B]

after finding out which mouse your vm guest is using by running 'xinput list' you can
Run this command in the linux guest to allow the middle mouse button to act as a 'back' button on the browser (firefox,chrome,etc)

```
#!/bin/bash
# uncomment the device you are using
#device="QEMU QEMU USB Mouse"
device="ImExPS/2 Generic Explorer Mouse"
xinput --set-button-map "$device" 1 8 3 4 5 6 7 2 9

```

history on the middle button as paste.  For reference only.  Hopefully it wont muddle up this thread
[http://askubuntu.com/questions/167570/how-does-middle-click-paste-work/167577#167577](http://askubuntu.com/questions/167570/how-does-middle-click-paste-work/167577#167577)

---

