---
title: "Seamless VM desktop integration with Libvirt VGA Passthrough?"
date: 2017-02-17
forum: Virtualisation
---

### Post by dsjstc on 2017-02-17
I'm running a triple-head Ubuntu 16.10 system with a virtualized Windows 7 guest using VGA passthrough.  That means the Windows guest has its own dedicated display adapter, so it can have high-performance 3D.  In order to get VGA passthrough, I had to switch hypervisors from VirtualBox to Qemu/KVM/Libvirt.  If these concepts are new to you, [here's some terminology]("http://thundersuntech.blogspot.com/2017/02/virtualization-vga-passthrough-concepts.html").

The main thing that I miss is VirtualBox's (relatively) seamless fullscreen monitor/keyboard/mouse integration.  Mouse cursor on the monitor that has a Windows desktop?  Mouse/keyboard captured.  Mouse cursor not on a Windows Desktop?  Clicks and keystrokes go to the host.  Just switched?  Clipboard is persistent.  Awesome.

VGA passthrough is a different animal.  The UX feels like two totally separate physical machines sharing a box.  I physically change the input on my monitor.  Physically switch keyboard and mouse to the VM. No clipboard integration at all.  It's just icky, there's no fluid UX between the machines at all.  

I'm here for suggestions and/or discussion on whether there's a way to improve integration of the VGA-Passthrough VM with the Linux desktop. H[ere's one idea that occurred to me]("http://askubuntu.com/questions/884496/libvirt-vga-passthrough-clone-display-to-virtual-display-device"), but I'd really like to hear other suggestions.

---

### Post by wildmanne39 on 2017-02-17
*Thread moved to **Virtualisation**.*

---

### Post by ODTech on 2017-02-17
> **dsjstc said:**
> I'm running a triple-head Ubuntu 16.10 system with a virtualized Windows 7 guest using VGA passthrough.  That means the Windows guest has its own dedicated display adapter, so it can have high-performance 3D.  In order to get VGA passthrough, I had to switch hypervisors from VirtualBox to Qemu/KVM/Libvirt.  If these concepts are new to you, [here's some terminology]("http://thundersuntech.blogspot.com/2017/02/virtualization-vga-passthrough-concepts.html").

The main thing that I miss is VirtualBox's (relatively) seamless fullscreen monitor/keyboard/mouse integration.  Mouse cursor on the monitor that has a Windows desktop?  Mouse/keyboard captured.  Mouse cursor not on a Windows Desktop?  Clicks and keystrokes go to the host.  Just switched?  Clipboard is persistent.  Awesome.

VGA passthrough is a different animal.  The UX feels like two totally separate physical machines sharing a box.  I physically change the input on my monitor.  Physically switch keyboard and mouse to the VM. No clipboard integration at all.  It's just icky, there's no fluid UX between the machines at all.  

I'm here for suggestions and/or discussion on whether there's a way to improve integration of the VGA-Passthrough VM with the Linux desktop. H[ere's one idea that occurred to me]("http://askubuntu.com/questions/884496/libvirt-vga-passthrough-clone-display-to-virtual-display-device"), but I'd really like to hear other suggestions.

I'm the opposite, i prefer the seperation of host and guest so i use network shares for the odd file transfer and i have a sperate desk for the VM monitor and input devices.

For those like you that prefer a seamless experience i've heard not just one user mention synergy. It used to be free but is now a commercial product so you will have to pay for it. I don't know if synergy will help with the clipboard issue but i assume it will.
As for file transfers just set up a shared network folder instead of VB's shared folders.

---

### Post by DuckHook on 2017-02-17
Perhaps this is because the two concepts are incompatible.

The reason and justification for passthrough is to separate the guest from the host whereas the reason and justification for non-passthrough is to have the guest contained within the host. This conceptual differentiation between the two approaches is pretty fundamental to the behaviour of each.

The idea behind passthrough, especially when it comes to graphics, is to offload the GPU tasks of a VM to a separate physically distinct card so that it can run at full bare metal speed and efficiency while the host card is reserved for host tasks. This means that you could have *two* GPU-intensive apps running concurrently&#8213;say, a game in the Windows guest while the host is grinding away at animation or rendering a 3-D model. Conceptually, this could even be extended to more GPUs than just two.

But if you want seamless integration, then you are really asking to shift the VM paradigm in the opposing direction&#8213;to share common resources and only "pretend" that they are separate machines.

You can't have both paradigms acting concurrently any more than you can push by pulling.

There are ways to increase the *convenience* of the passthrough paradigm:

[list=1]
[*]You could use a high-quality kvm switch so that changing Keyboard/Video/Mouse can be made with the press of a button.
[*]You could also display the two Video streams concurrently in one of those new-fangled monitors capable of Picture in Picture, or Split Screen.
[*]You could install some form of VNC/remote-desktop server in the guest and have the host display a remote-desktop window. Try out X2Go. Since the host is not doing the actual rendering, this might even give you reasonable framerates.
[/list]
But the whole VBox seamless experience defeats the purpose of passthrough and I suspect the only way to make it work involves the very compromises that passthrough was meant to overcome.

BTW, it is possible to get very close to the "seamless" VBox experience using spice and spice-vdagent in KVM. This will support arbitrary window resolutions, interactive resizing, clipboard sharing, drag & drop, and shared common files between guest and host. But this works only with a conventional VM and not with passthrough.

---

### Post by dsjstc on 2017-02-18
> **DuckHook said:**
> You can't have both paradigms acting concurrently any more than you can push by pulling.

I think your entire premise is predicated on conflating "GPU" with "display adapter."  The fact that many people see the two as one is the precise source of the poor user experience that I'm trying to work around.

Thanks for your comments!

---

### Post by DuckHook on 2017-02-18
> **dsjstc said:**
> I think your entire premise is predicated on conflating "GPU" with "display adapter."  The fact that many people see the two as one is the precise source of the poor user experience that I'm trying to work around.:confused:

Perhaps I'm especially dense today, but I fail to understand your point.

---

### Post by KillerKelvUK on 2017-02-18
So have been running 16.04 dual head for quite a while now and have GFX passthrough with a Windows 10 guest for probably all the same reasons as you do.  The "integration" aspect again is very much along the same lines, I want the near native performance of a dedicated GFX workhorse but inside a VM running in Ubuntu.  I've used Synergy now for a long time and I really like the simplicity e.g. seamlessly move from one desktop to another by pushing the mouse cursor off a specific desktop edge and into another...clipboard sharing ive found *can* be temperamental but nothing that would cause me to not recommend the software.  The support aspect to Synergy (as technically it is a paid software) is pretty lame, whilst I got direct email responses they were "sorry for the delay we're recruiting new support staff" but then a month or so later those new recruits followed up.  Most of the support I've used is plain old google and trial-and-error and its certainly possible that certain keystrokes wont map into a Synergy session e.g. the dedicated calculator button on my Logitech K800 (so yeah no great shakes).  You can try out the Synergy nightly builds which are publicly available ([https://symless.com/nightly](https://symless.com/nightly)) although as a minimum I'd expect features to be restricted e.g. encrypted connections etc.

Slightly off topic but have you looked at ddcutil to automate the switching of monitor inputs via DDC/CI commands on the monitors I2C bus?  Livbirt has a "hooks" feature which allows you to run scripts for specific VM's at different stages of their startup/shutdown cycle, using this I automate the switch of one monitor input to the VM's GFX head...a simple nugget which gives you more of that *seamless* feel.

---

