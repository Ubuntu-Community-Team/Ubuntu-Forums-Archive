---
title: "Virtualbox OSE vs Vmware"
date: 2009-08-03
forum: Virtualisation
---

### Post by ubudog on 2009-08-03
Which is better?

---

### Post by jocampo on 2009-08-03
> **ubudog said:**
> Which is better?

Depends!

If you are going to test Microsoft cluster capabilities, I would suggest VMware. So far, I've not found a workaround to setup a Windows20003/2008 Active/Passive cluster in order to test MS-SQL2005.

To setup single machines (linux or windows) VirtualBox should do the trick. I also find VirtualBox easier to work with and with better performance. I just recently setup VirtualBox in a headless Ubunty server and I am really please with the results. I connect via laptop and I modify, start or shutdown virtual machines via console (secure shell)

My preference is VirtualBox

---

### Post by Simian Man on 2009-08-03
Virtualbox, but not the OSE version, the real one.

---

### Post by ubudog on 2009-08-03
> **jocampo said:**
> Depends!

If you are going to test Microsoft cluster capabilities, I would suggest VMware. So far, I've not found a workaround to setup a Windows20003/2008 Active/Passive cluster in order to test MS-SQL2005.

To setup single machines (linux or windows) VirtualBox should do the trick. I also find VirtualBox easier to work with and with better performance. I just recently setup VirtualBox in a headless Ubunty server and I am really please with the results. I connect via laptop and I modify, start or shutdown virtual machines via console (secure shell)

My preference is VirtualBox

Thanks!  I'll get VirtualBox:)

---

### Post by jocampo on 2009-08-03
ubudog

Setup your host with lot of RAM! VirtualBox is memory hungry. For each VirtualMachine (if you're planning to install XP or VISTA) assign 512MB of RAM at least so you can get decent performance. And do not forget to download and install virtualbox additions; helps a lot for a better mouse integration and overall performance

Enjoy your virtualization adventure ;-)

---

### Post by ubudog on 2009-08-03
> **jocampo said:**
> ubudog

Setup your host with lot of RAM! VirtualBox is memory hungry. For each VirtualMachine (if you're planning to install XP or VISTA) assign 512MB of RAM at least so you can get decent performance. And do not forget to download and install virtualbox additions; helps a lot for a better mouse integration and overall performance

Enjoy your virtualization adventure ;-)

Thanks!:D

---

### Post by chrisinspace on 2009-08-03
+1 for VirtualBox.  It performs well, is easy to use, and has a lot of cool features like Seamless Mode.  That said, I really just use it for a sandbox.  At work, I run VMWare to create virtual production servers.  It has a lot of enterprise-level functionality that isn't available in VirtualBox.

---

### Post by jocampo on 2009-08-03
> **chrisinspace said:**
> +1 for VirtualBox.  It performs well, is easy to use, and has a lot of cool features like Seamless Mode.  That said, I really just use it for a sandbox.  At work, I run VMWare to create virtual production servers.  It has a lot of enterprise-level functionality that isn't available in VirtualBox.

Very well said! I use VirtualBox as a sandbox also. But I wish VirtualBox could expand its enterprise capabilities. Maybe in a future they can release a separate version, more enterprise-level focused.

---

