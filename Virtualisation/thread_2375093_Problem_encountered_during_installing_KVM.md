---
title: "Problem encountered during installing KVM"
date: 2017-10-21
forum: Virtualisation
---

### Post by satimis on 2017-10-21
Hi all,

Host - Ubuntu 16.04 desktop

I follow below document to install KVM
Installation of KVM
Virtualization (Ubuntu 16.04 » Ubuntu Server Guide)
[https://help.ubuntu.com/lts/serverguide/virtualization.html](https://help.ubuntu.com/lts/serverguide/virtualization.html)

Installation went through without problem with Virt_Manager installed.

On Terminal:
&#10219; virt-manager```

WARNING:root:Error setting up logfile: No write access to directory /home/satimis/.cache/virt-manager

```

'Virtual Machine Manager' started

&#10219; ls -ald /home/satimis/.cache/virt-manager/```

drwxr-x--x 2 root root 4096 Oct 22 08:58 

```

Whether I need changing it to satimis:satimis ?

&#10219; virsh list```

 Id    Name                           State
----------------------------------------------------

```

Whether after having installed guests then it will show detail there ?

&#10219; virsh start web_devel```

error: failed to get domain 'web_devel'
error: Domain not found: no domain with matching name 'web_devel'

```

&#10219; virsh autostart web_devel```

error: failed to get domain 'web_devel'
error: Domain not found: no domain with matching name 'web_devel'

```

What shall I replace web_devel with ?

Please advise.  Thanks

Regards
satimis

---

### Post by TheFu on 2017-10-22
Don't run virt-manager as root - EVER.  You'll need to clean up the existing root-owned config files before moving forward.

In general, it is a bad idea to use root/sudo with a GUI program, with very, very, very few exceptions.

---

### Post by satimis on 2017-10-22
> **TheFu said:**
> Don't run virt-manager as root - EVER.  You'll need to clean up the existing root-owned config files before moving forward.

In general, it is a bad idea to use root/sudo with a GUI program, with very, very, very few exceptions.
Hi,

Could you please explain in more detail how to get around it?  Thanks

Which document shall I follow to install KVM?

Regards
satimis

---

### Post by TheFu on 2017-10-22
**sudo rm -rf ~/.cache/virt-manager/**

---

### Post by satimis on 2017-10-22
> **TheFu said:**
> **sudo rm -rf ~/.cache/virt-manager/**
Run;

&#10219; sudo rm -rf ~/.cache/virt-manager/

&#10219; virt-manager

Virt-manager starts without complaint.

Thanks

satimis

---

### Post by TheFu on 2017-10-22
Don't run GUI programs with sudo.  THAT is the lesson here, especially when you don't understand file/directory permissions.  virtualization doesn't require root.

---

### Post by satimis on 2017-10-22
> **TheFu said:**
> Don't run GUI programs with sudo.  THAT is the lesson here, especially when you don't understand file/directory permissions.  virtualization doesn't require root.
Noted and thanks

satimis

---

