---
title: "run X11/lxc in window within a host."
date: 2015-05-16
forum: Virtualisation
---

### Post by odror on 2015-05-16
VMs (KVM wirtualbox) run in a windowed environment in the host.

Is it possibly for lxc to have (its own x11 server) running in a window in the host (like all the VMs)

I know that I can used xnest. Xnest uses the host X11 server. I would the lxc to have it own server. I would like to used the lxc as a virtual desktop.  So that I can connect to it from the WAN.

In other words I would like the host and lxc to have separate xservers (Running simultaneously) and be able to have a windowed desktop manager (i.e. lightdm) of the lxc guest within the host.

---

### Post by TheFu on 2015-05-17
X/Windows client/server works backwards of what is intuitive.  The "server" runs on the machine you sit behind. The "client" runs on the remote machine.  So if you want to run any GUI application "inside the lxc container", just use 
**ssh -X userid@lxc-name /path/to/program**
That command will set the DISPLAY correctly automatically and it will run the remote command "there", while displaying it "here". We are using ssh to tunnel the X/Windows traffic for security reasons. X/Windows protocols bring all sorts of security concerns and really aren't wise to run on a LAN anymore.  The X/Windows security model is basically a joke. Wikipedia does a good job explaining the C/S aspects too. [https://en.wikipedia.org/wiki/X_Window_System_protocols_and_architecture](https://en.wikipedia.org/wiki/X_Window_System_protocols_and_architecture)

If you want to run remote commands inside any system (real or VM or container) over the WAN, take a look at x2go (or any NX-based solution).

---

### Post by odror on 2015-05-17
> **TheFu said:**
> 

If you want to run remote commands inside any system (real or VM or container) over the WAN, take a look at x2go (or any NX-based solution).

That is exactly what I want. I would like to run nxserver of Nomachine 4 in a container. Unlike x2go it uses a streaming technology. The nxserver needs an Xserver within the container.  I prefer not to use a VM because of the overhead.

---

### Post by TheFu on 2015-05-17
> **odror said:**
> That is exactly what I want. I would like to run nxserver of Nomachine 4 in a container. Unlike x2go it uses a streaming technology. The nxserver needs an Xserver within the container.  I prefer not to use a VM because of the overhead.

I've never used NoMachine's server, but I have run FreeNX and x2go inside VMs on systems that don't have ANY GPU at all. They work. What is the issue?  Just load the dependencies and it should work.  I don't have time to test this today, but find it interesting enough that I'll add it to my huge item list of things-to-do. There are good reasons to want to run select desktop apps in containers, definitely.

---

### Post by naisanza on 2016-05-02
> **TheFu said:**
> I have run FreeNX and x2go inside VMs on systems that don't have ANY GPU at all. They work.

Did you have it running in a headless Ubuntu Server? That's what I'm trying to get to work is in a headless Ubuntu 16.x server.

The X server and gdm/lightdm fails to start because of tty and vt requirements.

With a vanilla LXC container and `ubuntu-gnome-desktop` installed, the first failure is with `/dev/tty0 not found`

Created a symlink `/dev/tty1 --> /dev/tty0`

The second error is it `Cannot open virtual console 7 `

And I'm stuck on the second error right now

---

### Post by odror on 2016-05-02
I do not think it can run in a headless mode. The sever and the client need to run nvidia and cuda-toolkit with the same version

---

### Post by MAFoElffen on 2016-05-04
ifaik-- Cuda Remotely? Cuda can work headless, but would required the Virt hypervisor host to physically have a capable NVidia GPU and passed through, outside the hypervisor (PCI pass-through) to that GPU(s). (such as to a Tesla Card. They are GPU processing cards.) Only way I know around that, is for a VM host to be running NVidia Grid. (which does not work with KVM, rather is a VMware targeted solution).

To display the output from a Cuda program... can be on anything... you do something in your program... usually crunching lots of calculations and display the result as you programmed how you are showing that result... Virtualization is that the processing is done on the host running the VM guest in the hypervisor. Display of that guest output is displayed remotely in a host displaying that remote guest session. <-- You nderstand that concept right? A hypervisor such as KVM is not distributed processing. The "client" is dumb and could be even a diskless terminal, or an Android phone.  But if that result is graphical...(?)

Are your programming specifically a graphics app? Where processing and display of that is Cuda specific? (animation) Or something that is distributed processing capable? (Those examples would be stretching the limits of virtualization) They don't have to be the same version, just have the same capabilities, which you set target version for your target environment from within Cuda. Right? Meaning if the server is newer, it can be targeted to an older version client, but not the other way around.

---

