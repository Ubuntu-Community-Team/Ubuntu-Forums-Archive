---
title: "KUbuntu 20.04 in a VM (KVM and Virtualbox)-Screen resolution issue"
date: 2020-09-20
forum: Virtualisation
---

### Post by LVDave on 2020-09-20
I've installed KUbuntu 20.04 in both a KVM and Virtualbox environment, and find that after install these installs have a default
screen resolution of 800x600, which on my 1440x900 laptop looks like hell. I've found that going into system-settings/display-configuration and changing it from 800x600 to 1440x900 and hitting "apply" takes the resolution to my "fullscreen" for a second then snaps back to the 800x600, although the display configuration window still shows 1440x900, until I close the display configuration window. This of course is when KVM/VB vm is set to "fullscreen".. I've also seen the same thing on various DE's on 18.04 and, as I recall 16.04 also. It used to work fine on 14.04. Is this a bug or just dumb programming?

Thanks
Dave Frandin

---

### Post by TheFu on 2020-09-20
For Virtualbox, use the guest additions for a more seamless integration.

For KVM/libvirt, be certain to choose QXL drivers and the spice protocol. This works for local and remote virt-viewer connections.

I don't know how KDE works for resolutions, but the normal Linux methods would be to use **xrandr** to set resolution, then add that same command+options to your ~/.xprofile file.  Here's what mine looks like:
```
xrandr --output DVI-D-0 --mode 1920x1200
```

---

### Post by LVDave on 2020-09-20
I can't check the VB install right now, but it turns out on the KVM vm, the vm setup shows the video IS QXL and "Channel Spice" and "Display Spice"... Will try the xrandr snippet above...

---

### Post by wildmanne39 on 2020-09-20
Thread moved to virtualisation sub-forum.

---

### Post by TheFu on 2020-09-21
> **LVDave said:**
> I can't check the VB install right now, but it turns out on the KVM vm, the vm setup shows the video IS QXL and "Channel Spice" and "Display Spice"... Will try the xrandr snippet above...

You'll need to modify that line for your system. Both the mode and the output device. On my kvm 20.04 system, this is the line that works:
```
xrandr --output Virtual-1  --mode 1680x1050
```

I'm on a 1920x1200 host (desktop), but sometimes use a laptop.

My connection script is this:
```
#!/bin/bash
GO=regulus
if [[ $HOSTNAME == "hadar" ]] ; then
    # For local connection on hadar
    /usr/bin/virt-viewer -a -d  $GO &
else
    # For remote connections on the LAN
    /usr/bin/virt-viewer --connect qemu+ssh://hadar/system $GO &
fi
```
hadar is the vm-host system, but I have others and don't want to be bothered to remember virsh connection incantations.

But to be honest, almost always I'll use remote X11 rather than virt-viewer.  Virt-viewer **is** faster thanks to spice, but much less convenient.  For example:
```
ssh -X regulus "libreoffice ~/TODO/GTD-Todo.xls" &
```
or
```
ssh -X regulus "firejail thunderbird " &
```
or
```
ssh -X cirrus "chromium-browser $@ " &
```

but most common, I just get a terminal onto different systems:
```
xterm -geometry 80x25+1010+150 $XTERM_OPTS -e ssh -X istar &
xterm -geometry 80x25+980+610 $XTERM_OPTS -e ssh -X romulus &
xterm -geometry 80x25+0+0 $XTERM_OPTS -e ssh -X hadar &
xterm -geometry 80x25+2+670 $XTERM_OPTS -e ssh -X regulus &
```
From each of these, most GUI programs can be launched to be run from each system.

---

### Post by LVDave on 2020-09-22
That "xrandr --output Virtual-1  --mode 1680x1050" did the same thing when I changed the "mode" to 1440x900 for  my screen. Goes to full screen then snaps back to 800x600.... *something* really wants to keep this vm at 800x600.. Not really sure how the rest of your very informative reply applies to my problem.

Thanks

---

### Post by TheFu on 2020-09-22
> **LVDave said:**
> That "xrandr --output Virtual-1  --mode 1680x1050" did the same thing when I changed the "mode" to 1440x900 for  my screen. Goes to full screen then snaps back to 800x600.... *something* really wants to keep this vm at 800x600.. Not really sure how the rest of your very informative reply applies to my problem.

Thanks

Sometimes the answer we seek isn't the answer we need. That was the point for the ssh -X stuff. You don't need a full desktop most of the time, just the program window to be displayed on the local machine. Of course, only you can judge which method is truly workable.

---

### Post by SeijiSensei on 2020-09-22
Make sure you've installed the Guest Additions and run the VBoxLinuxAdditions.run script on the Linux VM.

Shut down the VM, then open the VBox manager and go the VM's Settings page.  Choose Display, then VBoxSVGA. VirtualBox will complain and say "invalid settings detected."  Ignore that warning, save the settings, and boot the VM. Now go the Display settings in Kubuntu System Settings.  You should now see a much longer list of supported resolutions.

---

