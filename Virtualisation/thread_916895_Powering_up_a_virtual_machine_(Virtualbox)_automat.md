---
title: "Powering up a virtual machine (Virtualbox) automatically - without logging in"
date: 2008-09-11
forum: Virtualisation
---

### Post by OmahaVike on 2008-09-11
Hello,

I have automatic login on my hardy box disabled, thus presenting a GUI login screen when the machine is booted.

What I would like to do is...  during the bootup process, to start up a virtual machine in virtualbox without a particular user logging in.

[underlying problem]
In the event my physical host loses power, the BIOS is set to respond by booting the machine once power is restored.  Once the boot process has completed, I'm hoping there is a way to boot one of my virtual machines.
[/underlying problem]

Is this possible without a user logging in?

Thanks much for any and all feedback.

---

### Post by tuxxy on 2008-09-11
Do you mean the user shouldnt be logged into virtual machine? if so have you setup the accounts on the virtual machine to provide this.

---

### Post by OmahaVike on 2008-09-11
Thanks for the quick reply tuxxy, and I apologize for the vague description.

The guest is essentially being used as a server, so the user problem only exists at the host level.

---

