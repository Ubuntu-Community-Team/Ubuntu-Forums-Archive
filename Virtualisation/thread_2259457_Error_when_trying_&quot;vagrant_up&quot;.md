---
title: "Error when trying &quot;vagrant up&quot;"
date: 2015-01-04
forum: Virtualisation
---

### Post by Matthew2D on 2015-01-04
I entered "vagrant up" in the terminal and got this:

```

Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'hashicorp/precise32' is up to date...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 => 2222 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
The guest machine entered an invalid state while waiting for it
to boot. Valid states are 'starting, running'. The machine is in the
'poweroff' state. Please verify everything is configured
properly and try again.

If the provider you're using has a GUI that comes with it,
it is often helpful to open that and watch the machine, since the
GUI often has more helpful error messages than Vagrant can retrieve.
For example, if you're using VirtualBox, run `vagrant up` while the VirtualBox GUI is open.
```

I tried doing it with the VirtualBox GUI open and got the same thing.
Also if I try to start it in the GUI I get this:

```
Failed to open a session for the virtual machine FlarumVm.
Failed to load VMMR0.r0 (VERR_SUPLIB_WORLD_WRITABLE).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console Interface: IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}
```

Any suggestions? Thanks! (BTW I have virtualization enabled in the bios)

---

