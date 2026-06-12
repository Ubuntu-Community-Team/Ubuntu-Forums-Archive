---
title: "Need Graphical Terminal"
date: 2019-07-09
forum: Server Platforms
---

### Post by snakyjake on 2019-07-09
How do I install a graphical terminal for Ubuntu Server?

If there's more than one, what are the important differences?

What I want is for Ubuntu Server to boot straight into a *graphic* terminal.  I don't need desktop/window management, but if it's required for a graphical terminal, then I'd rather have one that I won't notice is there.

Why do I want a *graphical* terminal?  Because its the only way I can get the resolution I want in a VirtualBox host.

Host:  Windows 10
Guest:  Ubuntu Server 

Symptoms:
[IMG]https://i.imgur.com/FtjtbC3.png[/IMG]

Thank you.

---

### Post by cruzer001 on 2019-07-10
Xwindow system?

Not sure if that's what you are after, but here it is.

[https://en.wikipedia.org/wiki/Comparison_of_X_window_managers](https://en.wikipedia.org/wiki/Comparison_of_X_window_managers)

I set up a basic server as a host using xorg, xdm and spectrwm.

Did this a few weeks ago.

[https://ubuntuforums.org/showthread.php?t=2421162&highlight=](https://ubuntuforums.org/showthread.php?t=2421162&highlight=)

---

### Post by mastablasta on 2019-07-10
> **snakyjake said:**
> 
Why do I want a *graphical* terminal?  Because its the only way I can get the resolution I want in a VirtualBox host.


did you install guest virtualbox additions?

otherwise just install i3 if you are OK with tabs (it takes up really low resources) or icewm or openbox if you prefer desktop windows.

---

### Post by snakyjake on 2019-07-10
> **mastablasta said:**
> did you install guest virtualbox additions?

Yes, I installed VirtualBox Guest Additions:
```
$ lsmod | grep vboxguest
vboxguest	331776	1

```

[IMG]https://i.imgur.com/XZW3h2b.png[/IMG]

I believe the VirtualBox issue with the virtual screen display size/resolution has to do with TTY or KVM, and is not a "graphical" interface.  

Jake

---

### Post by TheFu on 2019-07-10
If you are seeing **any** windowing at all, then you have a graphical setup.
You can see which modes are available with **xrandr** and control them that way.  There are a few other *randr tools with easier interfaces.  I like lxrandr - simple, easy to use.

I'm confused by the mention of virtualbox, but seeing KVM.  Only 1 hypervisor should be installed on physical hardware and nested virtualization shouldn't be attempted by non-experts.

And just to be clear - the guest additions are installed inside the Guest VM, not the hostOS.

---

### Post by snakyjake on 2019-07-10
> **TheFu said:**
> I'm confused by the mention of virtualbox, but seeing KVM.  Only 1 hypervisor should be installed on physical hardware and nested virtualization shouldn't be attempted by non-experts.

I changed the VirtualBox System Acceleration Paravirtualization Interface = None.

> **TheFu said:**
> And just to be clear - the guest additions are installed inside the Guest VM, not the hostOS.

Yes, I believe I have VirtualBox Guest Additions installed in the VirtualBox Guest (Ubuntu Server is the Guest VM, Windows 10 is the Host):
```
$ lsmod | grep vboxguest
vboxguest	331776	1
```

Jake

---

### Post by snakyjake on 2019-07-10
> **TheFu said:**
> You can see which modes are available with **xrandr** and control them that way.  There are a few other *randr tools with easier interfaces.  I like lxrandr - simple, easy to use.

```
$ lxrandr
(lxrandr:1851): Gtk-WARNING **: 16:18:06.339: cannot open display:
```

<eom>

---

### Post by TheFu on 2019-07-10
Ah ... I think I understand your setup.  You are doing things in a strange way.  Servers don't have a GUI.  They text resolution is controlled by grub and normally 80x25 or 132x50 characters are used.  There is no copy/paste in doing this. Might want to check out the "scale" controls for the VM window.  Also, since there isn't any text copy/paste, would be good to practice up on file and command redirection into files.

Servers should be managed 99.99999999% of the time using ssh.  From Windows, most people use putty as an ssh client.  It allows copy/paste in a reasonable way between the windows and different guests.  Normally, only a complete noob would install X/Windows onto a Linux server. It just isn't done for a number of reasons. There are exceptions for the GUI on a server, but not many.  If you want a GUI on Linux, install a desktop like LUbuntu/Xubuntu or Ubuntu-Mate.  Avoid the heavy desktops like Gnome3 or KDE inside a VM.  Virtualized systems don't work with with heavy graphics.

Also, the guest additions usually aren't used by Linux server installs. They provide mostly end-user/GUI features which just aren't needed/wanted.  The guest additions have some security problems too.

Another item - the paravirt interface. You probably want to use virtio, if that is an option.  Disabling it will have performance impacts on the host and the guest.  I don't use virtualbox. Below is what KVM (a different hypervisor used by enterprises) shows with virtio NIC and HBA:
```
$ lshw -c network
  *-network               
       description: Ethernet interface
       product: [B]Virtio network device
[/B]       vendor: Red Hat, Inc.

```and for the disk controller ... ```

  *-scsi
       description: SCSI storage controller
       product: **Virtio block device**
       vendor: Red Hat, Inc.

```

So, on the ubuntu server, **sudo apt install openssh-server  fail2ban**.
Ensure the vbox networking is setup for "Bridged", not host-only or NAT.  If you had to change the networking in vbox, reboot the ubuntu server. Otherwise, continue ... 

On Windows, open putty and connect to the ubuntu server IP on the LAN using your ubuntu userid.  Now you can select text with the left mouse button and paste it with the right.  You can resize the window, change the fonts all inside putty.  This doesn't add the bloat of a GUI, it doesn't drastically slow down your VM or your host and it doesn't introduce all the security problems that come with running a GUI on a Unix system.

If you want a more convenient and more secure system, setup ssh-keys for authentication between Windows and Linux.  I bet there are at least 100 guides for that.  Using passwords is so, so, so, 1995.  Passwords are bad for security. If you can easily type a password, it is bad.

I'm 95:5 that this is really what you need, but only 50:50 that this is what you want.  I run lots of virtual machines around the world.  99.999999% of the time, access for management is via ssh.  About once a year across all the systems, I'll need direct console access for 1 box.  ssh is how system administration is performed for Unix.

---

### Post by mastablasta on 2019-07-12
you can also install ajenti (webgui) and then access the virtual server via browser. ajenti provides a terminal window in browser.

---

### Post by TheFu on 2019-07-12
> **mastablasta said:**
> you can also install ajenti (webgui) and then access the virtual server via browser. ajenti provides a terminal window in browser.

I've always had an issue with webgui stuff used for administration needs. It fails my "smells bad" test.  To use any admin tool securely, it would need to be blocked from all external connections and only allow "localhost" connections.  That would be accomplished via an ssh-tunnel, so the idea that using a web-based terminal would make any sense fails in my mind.  I already have to have ssh into the machine for basic security of the web-admin tool.  Seems overly convoluted.  

But that's me.   You do you.  More options is good.

---

