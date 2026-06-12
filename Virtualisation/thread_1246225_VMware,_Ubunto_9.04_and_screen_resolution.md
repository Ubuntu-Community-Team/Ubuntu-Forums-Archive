---
title: "VMware, Ubunto 9.04 and screen resolution"
date: 2009-08-21
forum: Virtualisation
---

### Post by grigglestone on 2009-08-21
Someone set an Ubuntu image up for me. The max screen resolution I seem to be able to get is 1180x885 .. and it is showing 0 Hz for the refresh rate!

I would like to get up to a resolution of around 1400x1050.

I have seen many articles about setting screen resolutions for regular display options, but nothing seems to work for me when trying with my VMware image. I take a VM snapshot, edit the xorg.conf file, reset X (using "sudo /etc/init.d/gdm restart") and I still don't see my newly specified resolutions.

a) Has anyone done this with VMware/Ubuntu 9.04
b) What did you have to do (dummy's guide would be great as I'm new to VMware & Ubuntu)

thanks, David

---

### Post by SolarOnline on 2009-08-21
Maybe it's out of range. 

Try checking here: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by fjgaude on 2009-08-22
First off, I've not been able to install VMware Server 1.09 in my Ubuntu 9.10.

As for screen resolution, in a guest you don't do that. All is automatic if you set Edit/Preferences/Display to Autofit window/guest. Works for me on 9.04, 8.10, 8.04 and earlier.

---

### Post by celthunder on 2009-08-23
> **grigglestone said:**
> Someone set an Ubuntu image up for me. The max screen resolution I seem to be able to get is 1180x885 .. and it is showing 0 Hz for the refresh rate!

I would like to get up to a resolution of around 1400x1050.

I have seen many articles about setting screen resolutions for regular display options, but nothing seems to work for me when trying with my VMware image. I take a VM snapshot, edit the xorg.conf file, reset X (using "sudo /etc/init.d/gdm restart") and I still don't see my newly specified resolutions.

a) Has anyone done this with VMware/Ubuntu 9.04
b) What did you have to do (dummy's guide would be great as I'm new to VMware & Ubuntu)

thanks, David

a.  Yes, I have ubuntu in vmware atm and I have vista in a vmware when i boot to ubuntu, both get the highest resolution my monitor accepts.  The refresh rate of 0 is normal and it's set to that no matter what linux distro you use with vmware.

b.  Check the vmware display setup for your virtual machine, you can set maximum display resolution per monitor in there might be set lower than what you want.

---

### Post by grigglestone on 2009-08-27
Issue resolved .. 2 steps:

1) As per [http://communities.vmware.com/thread/167759](http://communities.vmware.com/thread/167759) .. needed to set the max width and height in the .vmx file

2) Then to get any particular setting my little heart desired (within the bounds of what I had set above) I used: [http://communities.vmware.com/docs/DOC-1820](http://communities.vmware.com/docs/DOC-1820), ending up with a xorg.conf that looked like that show below. Of course you also need to a) sudo to change xorg.conf, b) restart your guest in order for the new settings to be picked up and c) use the Display settings to select your odd resolution.

Section "Device"
    Identifier  "VMware SVGA"
    Driver      "vmware"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device      "VMware SVGA"
    Monitor     "vmware"
    # Don't specify DefaultColorDepth unless you know what you're
    # doing. It will override the driver's preferences which can
    # cause the X server not to run if the host doesn't support the
    # depth.
    Subsection "Display"
        # VGA mode: better left untouched
        Depth       4
        Modes       "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       8
        Modes       "1400x1050" "1585x1132"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       15
        Modes       "1400x1050" "1585x1132"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1400x1050" "1585x1132"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1400x1050" "1585x1132"
        ViewPort    0 0
    EndSubsection
EndSection

Section "InputDevice"
  Driver "vmmouse"
  Identifier "VMware Mouse"
  Option "Buttons" "5"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "IMPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier      "vmware"
    VendorName      "VMware, Inc"
    HorizSync       1-10000
    VertRefresh     1-10000
    ModeLine        "1585x1132" 100 1585 1600 1700 1800 1132 1200 1300 1400
EndSection

---

