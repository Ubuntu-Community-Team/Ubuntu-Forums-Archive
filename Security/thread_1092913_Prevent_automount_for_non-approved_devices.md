---
title: "Prevent automount for non-approved devices"
date: 2009-03-10
forum: Security
---

### Post by cryogen on 2009-03-10
I have an ubuntu server in a scientific research lab that occasionally doubles as a workstation for people to check their e-mail, look up reference papers and such while taking data.  Data is transferred from the instruments to a removable medium, typically a flash drive or zip disk (yes, we still have some of those!) and then onto the network for proper handling.  What I'm wanting to do is implement something that only allows certain removable drives to be mounted on the linux system.  That is, as a security and as a data loss prevention measure I want users to only be able to mount whitelisted storage devices.  Preferably, the serial number of the disk or some other unique identifier can be used to do this.

To clarify, I do _**not**_ want to disable USB or automount completely.  I want to prevent unknown storage devices from being mounted so nothing can be transferred to them.

My question is, how can I do something like this in Linux?  I'm sure it's possible, but I've never tried anything like this before.  I've been googling for several days and haven't found anything useful so I was hoping someone here could help out.

On a related note, does anyone know of a free software project that does something similar for windows (I have some of those to admin too and need to do the same thing).  I've found some proprietary solutions, but I'd like to use free software if at all possible.

---

### Post by HermanAB on 2009-03-11
The Gnome Policykit Wizard can do what you want.  It is in the System menu.

Cheers,

Herman

---

### Post by Nxion on 2009-03-11
> **HermanAB said:**
> The Gnome Policykit Wizard can do what you want.  It is in the System menu.

Cheers,

Herman

I have been looking for something similar, thanks :)

---

### Post by cryogen on 2009-03-12
Nice.  Thanks for pointing that out.  I'll go have a look and see if I can make it work.  I had been considering hacking together something with pam_usb, but that would have been a rather ugly hack.  Thanks again!

---

