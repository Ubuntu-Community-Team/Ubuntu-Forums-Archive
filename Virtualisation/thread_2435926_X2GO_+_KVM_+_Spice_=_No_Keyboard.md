---
title: "X2GO + KVM + Spice = No Keyboard"
date: 2020-01-28
forum: Virtualisation
---

### Post by ilsa2 on 2020-01-28
Hi all,

I have a Debian 10 host running an Ubuntu 18.04 guest under KVM.  I am managing/interacting with it using VMM and have configured the VM to use Spice.

I am able to use the VM fine when I am directly using the host, however I am usually accessing said host remotely via X2Go.  (I refuse to use VNC since it's horribly insecure, and there's nothing stopping someone from looking at my screen while I am remoted in)

When I use X2Go, keyboard just doesn't work.  Mouse works fine.  If I switch from Spice to VNC, then everything works fine but I lose all the goodies like clipboard sharing, etc.

If I manually run virt-viewer on the command line and connect to the VM, I get the following:
```
(virt-viewer:20822): vnc-keymap-WARNING **: 12:05:57.069: Unknown keycode mapping 'empty+aliases(qwerty)'.
Please report to gtk-vnc-list@gnome.org
including the following information:

  - Operating system
  - GDK build
  - X11 Server
  - xprop -root
  - xdpyinfo
```

And I get the following error every time I press a key:
```
(virt-viewer:20822): GSpice-CRITICAL **: 12:06:04.499: send_key: assertion 'scancode != 0' failed
```

Does anyone have any recommendations for correcting this?

---

### Post by TheFu on 2020-01-28
Use a lite, supported, DE - that is NOT Gnome3.  XFCE, LXDE, Mate or most of the WM-only methods work well.  The fact that gnome3 isn't supported is documented on the x2go website. 

Also, don't confuse connections through virt-manager via SPICE with anything related to x2go. They are completely different.

---

### Post by ilsa2 on 2020-01-28
I forgot to mention... I am not using Gnome.  I am using XFCE on both the host and the target.

I don't know what you mean about the second part.  I am connecting to the host via X2Go, and while in that session I am opening virt-viewer (or virt-manager), and accessing the VM on that host.  So somewhere along that pathway from My Current Machine -> X2Go on KVM Host -> virt-viewer to KVM Guest, the mapping is... getting lost somehow?

---

### Post by TheFu on 2020-01-28
> **ilsa2 said:**
> I forgot to mention... I am not using Gnome.  I am using XFCE on both the host and the target.

I don't know what you mean about the second part.  I am connecting to the host via X2Go, and while in that session I am opening virt-viewer (or virt-manager), and accessing the VM on that host.  So somewhere along that pathway from My Current Machine -> X2Go on KVM Host -> virt-viewer to KVM Guest, the mapping is... getting lost somehow?

Gnome2 (which XFCE uses) is fine. It is Gnome3 that really wants to be directly on hardware.  I know the GNU project has been working on a remote desktop between Gnome3 systems for a while. Perhaps 20.04 will include it and it will work?

Nested remote desktops?  Why?  x2go uses ssh tunnels and ssh key-based authentication and does excellent compression.  The only time I use virt-manager is when setting up or modifying a VM.  The rest of the time, I'll use x2go directly into the destop client.  Most of my VMs are for servers, so no desktop/GUI.  

SPICE uses the QXL video drivers, which I doubt x2go supports.  I'm on 16.04 here and the keyboard mapping under SPICE has always been a little off for me. Don't know if that is just for the 16.04 release or my hardware or something else.  

Anyway, that's something else to try. Don't use SPICE, go directly into the client VM.

---

### Post by ilsa2 on 2020-02-12
I COULD do that, and I already have, but it doesn't solve what I was trying to accomplish.  

On Mac or Windows, you can remote into the box and resume your work, doing virtually everything you need to without issues, workarounds, or compromises.  It doesn't matter if you're running VM.  RD just works. Apparently Linux just isn't there.

---

### Post by TheFu on 2020-02-12
> **ilsa2 said:**
> I COULD do that, and I already have, but it doesn't solve what I was trying to accomplish.  

On Mac or Windows, you can remote into the box and resume your work, doing virtually everything you need to without issues, workarounds, or compromises.  It doesn't matter if you're running VM.  RD just works. Apparently Linux just isn't there.

x2go does reconnect and pick up exactly with the programs where they were AND 50 other users can connect either to the same session as read-only to watch or have their own sessions using their own account on the same machine - for free.  Reconnecting x2go sessions are client agnostic.  I do this multiple times every week, sometimes from different continents.

People use remote connections to/from Linux million and millions of times a day.  I routinely access about 30 systems multiple times every week and manage those systems from thousands of miles away, securely, without issue.  I've been doing this for about 25 yrs along with thousands of other capabilities that Linux and Unix-like systems provide. Expecting any OS to behave like another is asking for frustration.  But if thinking the Unix way is possible, almost always a more efficient method is possible.

Google found this about gnome3 and the Gnome project's remote desktop efforts: [https://wiki.gnome.org/Projects/Mutter/RemoteDesktop](https://wiki.gnome.org/Projects/Mutter/RemoteDesktop)

I directly run virt-manager on my desktop to manage VM settings on the different VM servers. virt-manager connection use ssh tunnels.

Seems there is a way to connect using A--> B --> C, but you'd prefer to use A --> C --> B?  Hardly seems like a big deal, especially since both connections use ssh and don't need any different WAN firewall rules.

Or do I misunderstand the issue still?

---

