---
title: "Virtualbox ubuntu-desktop on wayland do not work but gnome-session does work"
date: 2021-06-14
forum: Virtualisation
---

### Post by heavyblack1 on 2021-06-14
Hello i discovered problem in Vbox i have GTX 960 ubuntu 20.04 21.04.
In gdm if I  chose gnome wayland it works but  in ubuntu desktop it doesn't some times no icons or i cannot scroll throw all apps.First i thought i t is ubuntu 21.04 or wayland problem but than i discovered both ubuntu 20.04 and 21.04 in ubuntu-desktop  have same issue it seem it doesn't affect gnome-session .

[ATTACH=CONFIG]288656[/ATTACH]

[ATTACH=CONFIG]288657[/ATTACH]

---

### Post by slickymaster on 2021-06-14
Thread moved to **Virtualisation**

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by ActionParsnip on 2021-06-14
I suggest you use a non-compositing session in VMs like XFCE or LXDE. It'll mean the guest system impacts the host less.
Make sure you install the VirtualBox guest additions as well

---

### Post by heavyblack1 on 2021-06-20
i have VirtualBox guest additions but i said gnome-session works ubuntu-gnome package dont

---

### Post by MAFoElffen on 2021-06-21
I see that no one has really answered you...Welcome.

Some people would ask: "And?" (Do you want to use Wayland?)

I'm thinking most people do not "want" to address this, it has many heads to it, and it is not an Ubuntu thing, nor a problem with Ubuntu. Your observation is not really and Ubuntu Question, but rather how Oracle VirutualBox supports Xorg or Wayland Graphics.

Virtualbox supports Xorg XServer Very well. Why? Because in the 33 years that I have been involved with using and supporting XServer, it basically works the same. It's understood. It's known. It's popular. Many Linux Distributions use Xorg XServer for the Linux Graphics Layer, between the Linux Core, and The Graphical Desktop.

Wayland was new just under 7 years ago. I'm not saying the problem is because it is new...
RE: [Oracle VirtualBox Ticket #13471: VB Video driver should support Wayland]("https://www.virtualbox.org/ticket/13471")
> *"We are aware of this and working on it, but there is currently no estimate for when it will be done as we have many other things to work on too."*
That was their answer for 4 years... Their approach to that was to sit on it. Members of Oracle are the upper members, support and contributors to Xorg. Their answer to this ticket, was finally to use workarounds by using Guest Additions, disable 3D graphics Acceleration, enable 2D Graphics. (Not to fully support it.) It was not a full solution, nor did it work well. That is for their VBoxVGA driver, that supported Linux distros generally as legacy.

Add that there are Now, 3 Graphics drivers for VBox: VBoxVGA, VMSVGA, VBoxSVGA.

Each has it's own personalities, and what they work with and have problems with... Which will cause a black screen, even when mixed with how they are applied and mixed with other VM options... Such as booting from BIOS or EFI within the VM...

So, if you want to use Wayland on VBox, be a bit more specific about what your setup is, and what you want to do. Their are options to make it work... But using Xorg as graphics in a VBox VM Guest, opens more options to you. Or use the VMSVGA driver with Guest additions.

Just be aware that the Guest Additions for 6.1.6 are broken for Linux Guests and will break your graphics (all on it's own). This Ticket is still open and not fixed:
RE: [Oracle VirtualBox, Ticket #19496: Virtualbox 6.1.6 guest screen resize broken]("https://www.virtualbox.org/ticket/19496")

---

### Post by QIII on 2021-06-21
From the above, it seems VBox may not be very friendly with Wayland.

I spun up a fresh installation of Hirsute in KVM just now.

```
loginctl show-session 2 -p Type
Type=wayland

```

It's working just fine using KVM/libvirt/QEMU.  KVM may not be as straight-forward as VBox appears to be from the start, but it is a much better choice in my opinion.  It might be worth the investment of your time in learning how to use it and doing virtualization with it rather than VBox.

---

### Post by MAFoElffen on 2021-06-21
> **QIII said:**
> From the above, it seems VBox may not be very friendly with Wayland.

I spun up a fresh installation of Hirsute in KVM just now.

It's working just fine using KVM/libvert/QEMU.  KVM may not be as straight-forward as VBox appears to be from the start, but it is a much better choice in my opinion.  It might be worth the investment of your time in learning how to use it and doing virtualization with it rather than VBox.
@QIII:
Agreed. KVM is definitely more friendly with a lot of things over VirtualBox. KVM is a (Linux) Type 1 hypervisor and VBox is a (Multi-Platform) Type 2 (software virtualization) hypervisor. 

What I learned in the past when I was a Forums Moderator supporting this section, is that members using this section, some of those posting in this section are not actually running Linux as a Host OS, and are here asking about running their Ubuntu Guests better. This section covers a lot of "combinations." The OP hasn't yet said what his Host OS is. (LOL)

---

### Post by TheFu on 2021-06-22
The hostOS would be good to know.
I'm a convert from vbox to KVM/libvirt too. Never regretted that change, but spice is pretty amazing as a fast desktop protocol - both local and remote. Spice only works with KVM VMs.  I did some testing with SPICE and both X11 and Wayland a few months ago. For some reason, I think Wayland worked fine after I was all done testing. Initially, I thought it was broke, but I was most definitely mistaken.

---

