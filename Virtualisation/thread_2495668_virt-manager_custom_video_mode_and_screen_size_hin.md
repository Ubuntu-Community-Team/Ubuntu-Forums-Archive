---
title: "virt-manager custom video mode and screen size hint?"
date: 2024-02-26
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2024-02-26
In VirtualBox, it's possible to specify a [custom video mode]("https://www.virtualbox.org/manual/ch03.html#efividmode") that could be used by GRUB and provide screen size hint for the login screen.  I used this to make GRUB, TTYs, login screen, and graphical session all have the same resolution.

How to set custom video mode and screen size hint in virt-manager?

Host and guest are both Xubuntu 22.04.  The guest is UEFI without secure boot, and has VirtIO video with Spice+egl-headless displays.

Not seeking dynamic resizing of the guest screen with the viewing window, only looking to specify a different fixed resolution that the guest (mostly) automatically uses by default.

---

### Post by #&amp;thj^% on 2024-02-26
**All resolutions** might not be listed, but it should change automatically based on the size of the graphical console window: (Not what you asked for, that's just how it works)
Virtual Machine Manager > VM > View > Scale Display > Auto resize VM with window > Enable

Also this needs to be on the host>>"spice-vdagent"

---

### Post by TheFu on 2024-02-27
Once a VM is setup, don't use virt-manager. Use virt-viewer instead, which I think accepts the typical X/Windows -g options.  I know with Spice and QXL, we can resize the window easily and inside the guest, we can use xrandr to set display sizes.

I don't really use full desktops inside my VMs, since it is more convenient to run a specific tool through an **ssh -X tunnel** and specify the desired geometry on that command line like any X/Windows client program would support.  I prefer remotely run programs to fully integrate into my desktop.
For example, 
```
xterm -geometry 80x22+0+630 $XTERM_OPTS -e ssh -X deneb &
```

The geometry option is built-into XLIb, so any GUI programs that don't support it means the developers went out of their way to remove the support.  I.e. they suck.

Some programs translate their own size and position information.  Like Brave Browser, 
```
/opt/brave.com/brave/brave-browser \
   --window-position="97,0" \
   --window-size="1683,1153" &
```

Or you can use xdotool to place and resize a window based on the class or title.
```
xdotool search --name "Mozilla Firefox" windowmove 170  0
xdotool search --name "Mozilla Firefox" windowsize 1600  815
```

That's 3 different examples. BTW, the firefox instance is running on a different system and those xdotool commands work on the local X/Server.

I have no clue if Wayland supports it or not.

---

### Post by &amp;KyT$0P# on 2024-02-27
> **1fallen said:**
> it should change automatically based on the size of the graphical console window: (Not what you asked for, that's just how it works)
Virtual Machine Manager > VM > View > Scale Display > Auto resize VM with window > Enable

Also this needs to be on the host>>"spice-vdagent"

Actually that does help on my Debian 11 / Trinity Desktop guest, where the custom GRUB resolution was already working, so I could go View > Resize to VM at the GRUB screen, then install [FONT=Courier New]spice-vdagent[/FONT] on the guest and rebooted, then could select the "Auto resize VM with window" option and after rebooting the guest again the resolution seems to be working as desired.  Thanks 1fallen! :KS

* Spoke too soon.  After powering the guest off, its main resolution reverts back to 1024x768 at next boot :( Even though [FONT=Courier New]xrandr[/FONT] reports that the correct resolution is in use.  Only when rebooting the guest from within the guest does the resolution then work as expected.

> **TheFu said:**
> you can use xdotool to place and resize a window based on the class or title.
```
xdotool search --name "Mozilla Firefox" windowmove 170  0
xdotool search --name "Mozilla Firefox" windowsize 1600  815
```

Thanks TheFu for the suggestion.  If I understand correctly, I could use this method to manually set the main graphics resolution, then save the resulting window size for virt-manager using dconf-editor ([FONT=Courier New]/org/virt-manager/virt-manager/vms/[COLOR="#FF0000"]<UUID of the VM>[/COLOR]/vm-window-size[/FONT]) if it isn't already?

---

### Post by TheFu on 2024-02-28
I've never, ever, used dconf-editor. Wouldn't know what to do with it.

The key to understand is there are 2 completely different sides to resolutions in the VM.  1 is for the window that provides the border around the active area and the other is inside the VM where programs run.  These are completely separate and both have to be handled.

xrandr would be used inside the VM of the guest machine. It may be necessary to run it when a new GUI login-session happens, every time.  That's why we have ~/.xinitrc files.

---

### Post by &amp;KyT$0P# on 2024-02-29
Had partial success with [this method]("https://ubuntuhandbook.org/index.php/2021/05/custom-screen-resolution-ubuntu-wayland-xorg/"): It works perfectly for TTYs, and the correct resolution is now an available option in xfce4 Display settings (which selecting that option does work, but only for the logged-in user).  However, no luck with the login screen, it still switches to 1024x768.

Since I wouldn't expect that to affect GRUB resolution, also tried the [FONT=Courier New]GRUB_GFXMODE[/FONT] and [FONT=Courier New]GRUB_GFXPAYLOAD_LINUX=keep[/FONT] settings, but they aren't working for the desired non-standard resolution.
(As a test, also tried 1440x900, which *is* listed in output of running [FONT=Courier New]videoinfo[/FONT] at the GRUB command line, and that does the expected change.)

---

### Post by TheFu on 2024-02-29
Grub resolution doesn't impact X11 resolution.

---

### Post by &amp;KyT$0P# on 2024-03-04
Although less than ideal, I decided to live with a 1440x900 GRUB for now, as 1440x900 is "close enough" to the desired resolution.

> **halogen2 said:**
> Had partial success with [this method]("https://ubuntuhandbook.org/index.php/2021/05/custom-screen-resolution-ubuntu-wayland-xorg/"): It works perfectly for TTYs, and the correct resolution is now an available option in xfce4 Display settings (which selecting that option does work, but only for the logged-in user).  

That link is the key to setting custom guest resolution in all contexts other than GRUB.

After applying that boot parameter, the login screen (LightDM + lightdm-gtk-greeter) can be fixed by creating a file [FONT=Courier New]/etc/X11/xorg.conf.d/custom_res.conf[/FONT] with the following contents -
```
Section "Monitor"
  Identifier "Virtual-1"
  Option "PreferredMode" "[COLOR="#FF0000"]WIDTH[/COLOR]x[COLOR="#FF0000"]HEIGHT[/COLOR]"
EndSection
```

replacing [COLOR="#FF0000"]WIDTH[/COLOR] and [COLOR="#FF0000"]HEIGHT[/COLOR] with the actual custom dimensions.  This also automatically applies in the user session without needing to touch xfce4 Display settings.

(Haven't tested to see what happens here if the guest uses a Wayland-based display manager & greeter instead of LightDM for the login screen.)

Because GRUB resolution is slightly less than preferred resolution, to maximize the time the preferred resolution is in effect, I also enabled [early KMS]("https://wiki.archlinux.org/title/Kernel_mode_setting#Early_KMS_start") by adding [FONT=Courier New]virtio_gpu[/FONT] to [FONT=Courier New]/etc/initramfs-tools/modules[/FONT]

Thanks again TheFu for steering me toward using guest OS native methods! :KS

---

