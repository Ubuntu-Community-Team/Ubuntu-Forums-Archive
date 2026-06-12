---
title: "remote-viewer (spice) has wrong keyboard mapping"
date: 2013-11-02
forum: Virtualisation
---

### Post by TheFu on 2013-11-02
I am stuck and could use some ideas to resolve this.
Certain keys are not being passed through the spice client program to the remote desktop.  These include the single-quotes and double-quotes. I havnt noticed any other keys not working. It is an issue from the windows remote-viewer (spice) client.

*havnt = have not* (see, no single-quotes available) ;)

It does not happen from an Ubuntu **spicec** client or from NX clients or when ssh'ed in.
The KVM host is 12.04.3 and so are all the client VMs.

spice-virt-viewer-x64-0.5.7.msi is the program installed onto a Win7 Home x64 system.
NX and rdp from this same machine works perfectly from a keyboard standpoint. All the same hardware works to show the single- and double-quotes, just not inside the _spice-remote viewer_ window.

Ideas?

I feel sorta dumb that I can't figure this out.  Googling hasn't helped.  Since this is a spice-only issue, from a specific client, I doubt the console settings or X/Windows keymap are involved.  The only language used is English, though I would love to support Spanish and German characters eventually.

---

