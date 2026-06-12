---
title: "Deciding between VM or dual-boot setup"
date: 2012-05-08
forum: Virtualisation
---

### Post by helix_r on 2012-05-08
I would like to set-up a PC to run ubuntu most of the time, but also need to run XP for specific applications and testing. In the past I would have simply set up a dual boot machine and then restart and boot into windows XP as needed.

However since the machine has multiple cores and significant memory, I think I can use Virtual Box, Xen, or VMWare hypervisors. I am thinking of making Ubuntu the "host" VM and having XP as a guest VM. This would be especially nice for testing/debug/development since it is possible to run applications in both OS's simultaneously. I've never setup a virtual machine before and think that by asking the questions below I can avoid some trial-and-error.

Basically, I need to decide if a dual boot or VM setup is more appropriate for what I want to do.

Here's my questions:
[LIST=1]
[*]I do not always need to have XP running. Do the hypervisors allow me to shut the guest VM down so that the host VM can then immediately use all memory and processor resources? When I then bring up the guest VM, is it easy to provision how much memory and other resources are used by it? Ideally, I'd like to pre-configure this in advance and then toggle the guest VM off/on without thinking about it.


[*]Is it possible or advisable to have the host OS be 64bit and the guest OS be 32bit? Alternatively, if both VM's are 32 bit and I have 8G of RAM, can the hypervisor provision each VM with 4G of RAM when they are running simultaneously?


[*]Which hypervisors are best for set-ups such as I described?
[/LIST]

---

### Post by zandman on 2012-05-08
From my experiences (11.10 and 12.10) and based on what you describe:

- I have a workstation at home with 11.10 on it, 8GB of ram, AMD Phenom quadcore. When traveling i use a Dell Latitude with 3.x GB of ram (there's 4 in it, but only 3.2 or so is recognized). On both i have a 64bit OS, on both i take the WinXP-virtual machine with me.

- Most important things i use XP-Pro (32bit) for are to keep track of my running (Garmin) and having Lego Mindstorms and Parallax BoeBot software available.

- Love the VM-setup (Virtualbox, the Oracle version), because i only need it for 4h per week or so. Instead of having to shut down and reboot i now can have it available instantly.
- And.. when one of the kids wants to mess with the Mindstorms or BoeBot i only have to export the VM from my pc once and then import on theirs and they have it running instantly.

- You set the amount of ram available for the vm in the vm-manager. This is a "one time" setting, but you can adjust it later. On both machines i give XP 1GB of ram, that's more then enough for what i have to do.

- Why would you want to shut the guest OS down? You run XP within your guest os, and there you also still can do things. I jump from XP to Ubuntu and vice versa. I don't notice a performance impact on both machines for Ubuntu when i'm running the XP-vm.

---

### Post by lukeiamyourfather on 2012-05-08
A hypervisor is probably not the best way to go if you plan to spend most of your time in Ubuntu as a desktop system. Hypervisors allow flexibility when dealing with servers but for most desktop users it offers no real benefits and brings many caveats.

I would use VirtualBox which is in the repositories for Ubuntu. VirtualBox runs on a full install of an operating system like a program unlike a hypervisor which runs under all of the operating systems. It allows for near native performance (except for 3D accelerated graphics) by using the hardware virtualization capabilities of most modern processors. The guest can be stopped or started at anytime just like any other program. Guests can be 32-bit or 64-bit if the host is 64-bit. If the host is 32-bit then guests can be only 32-bit.

---

