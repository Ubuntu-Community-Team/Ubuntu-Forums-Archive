---
title: "VMWare Unity + Ubuntu"
date: 2009-01-17
forum: Virtualisation
---

### Post by Zuldan on 2009-01-17
VMWare Unity + Ubuntu
Ok well I thought I'd give Ubuntu a go via VMware.

1. Installed VMware Workstation 6.5.1 (latest build). (Reboot)
2. Installed Ubuntu 8.10. (Reboot)
3. Installed VMware Tools (yes to all compile options). (Reboot)

When I try to enable Unity I get the following message.

"The virtual machine cannot enter Unity mode. Check that Unity is supported for this guest operating system and that the latst version of VMware Tools is installed."

If I run /usr/bin/vmware-user I get the following

"Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine"

I thought I had done something wrong so I created another brand new virtual machine on another PC and used the 32bit version this time. I get the exact same problem.

Surely this sort of stuff is supposed to work out of the box?

Note: vmware-toolbox works pefectly fine.

---

### Post by Zuldan on 2009-01-17
Wow I got it working. I ran sudo vmware-config-tools.pl (and yes to compile everything) and it worked.

But now everytime I reboot Ubuntu I have to run vmware-config-tools so get Unity working. Is there a way around this?

---

### Post by Dedoimedo on 2009-01-18
Get the vmware tools running on startup.

See mostly the second half of this tutorial:
[http://www.dedoimedo.com/computers/vmware-tools.html](http://www.dedoimedo.com/computers/vmware-tools.html)

Dedoimedo

---

### Post by Zuldan on 2009-01-18
> **Dedoimedo said:**
> Get the vmware tools running on startup.

See mostly the second half of this tutorial:
[http://www.dedoimedo.com/computers/vmware-tools.html](http://www.dedoimedo.com/computers/vmware-tools.html)

Dedoimedo

Well VMware tools is running when the system starts. The problem is I have to re-compile them everytime I want to use the Unity part in VMware Tools.

I have now installed UBuntu on 4x VMwares (different hosts) and all 4 have the same problem. This must be a major flaw that everyone is having?

---

