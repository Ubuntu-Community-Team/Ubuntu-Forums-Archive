---
title: "Virt install no console output"
date: 2010-11-28
forum: Virtualisation
---

### Post by Dreetnp on 2010-11-28
I want to install Debian on ubuntu with KVM.
I'm using virt-manager to install the debian guest OS.
This is my command:

> virt-install --connect qemu:///system --name=Debian1 --ram=256 --vcpus=1 --check-cpu --file=/kvm/debian1.img --file-size=2 --bridge=br0 --accelerate --cdrom=/home/dries/Downloads/debian_full.iso --os-type=linux --os-variant=debianEtch --hvm

This works, an install window pops up to configure the debian os.

But my main goal is to do this on ubuntu server where there is no GUI available, so I add the '--nographics' command to my code.

The OS starts up but the only thing on my console is this:

> Starting install...
Creating domain...  
Connected to domain Debian1
Escape character is ^]

When I connect with Virsh I get the same:

> Connected to domain Debian1
Escape character is ^]

If I check the debian OS with virsh it says 'running'

Thanks in advise. ;)

---

### Post by gdahlm on 2010-11-28
look into the --serial tcp option for virt-install in the man page to configure the serial console.

---

### Post by Dreetnp on 2010-11-29
> **gdahlm said:**
> look into the --serial tcp option for virt-install in the man page to configure the serial console.
Thank you for the reply.

I experimented with the --serial option but nothing really worked.
I could tell the --serial command did something, for example if I created a telnet connection on a random port (2222) with "--serial tcp,host=:2222,mode=bind,protocol=telnet" I could connect to it with putty, so it's definitely configured. But I still couldn't get any output.

If I connect with the console with the virsh console-command I could not get any output either.

While trying this a question popped up. I know that a console connection is the most basic connection but could it be that the problem lies with debian? It might not support that kind of output? Or am I wrong?

---

### Post by gdahlm on 2010-11-29
yes you will need an installer that supports a serial console.

I tend to just give up, install with a graphics card and then add in a serial console to avoid the need for a VNC connection at a later date.

---

