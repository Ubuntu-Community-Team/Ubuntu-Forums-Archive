---
title: "Virtualbox bypass &quot;Close Virtual Machine&quot; box"
date: 2008-03-14
forum: Virtualisation
---

### Post by jonthysell on 2008-03-14
I'm running VirtualBox OSE 1.5.0 on a 64bit Gutsy host with a WinXP guest.

I usually keep the virtual machine open so I can test things in IE (and use flash without a kludgey hack).

Whenever I shutdown Ubuntu, VirtualBox always throws up a "Close Virtual Machine" prompt with either "save snapshot" or "shutdown".

Does anyone know how to set a default answer so there's no prompt? That way when I hit shutdown in Ubuntu, I can leave the computer and know that it'll shutdown?

The prompt pops up under other windows, so sometimes I don't see it and I leave my computer, only to find out later that it's still running (trying to save electricity here).

Thanks.

---

### Post by Hero of Time on 2008-03-15
From the User Manual, I found the following option to use in the shutdown script:
```
VBoxManage controlvm "VM name" savestate
```
That works like a charm, it saves the state of the VM for you to continue next time you start the VM. You can also use poweroff or acpipowerbutton to shutdown the VM directly.

---

### Post by jonthysell on 2008-03-17
Thanks!

The command works, but where do I put it? I tried making a shutdown script and placing links in rc0.d and rc6.d, but they won't run until after gdm is finished.

---

### Post by Hero of Time on 2008-03-17
You have to add it in the /etc/acpi/power.sh script I think. Check what the shutdown button calls in order for the system to shutdown, then put the command at the beginning.

---

