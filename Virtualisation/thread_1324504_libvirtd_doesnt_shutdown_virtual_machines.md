---
title: "libvirtd doesnt shutdown virtual machines"
date: 2009-11-12
forum: Virtualisation
---

### Post by falstaff on 2009-11-12
Hello,

I setup an Ubuntu 9.10 server with libvirtd. I configured a machine, set it up with Ubuntu 9.10 as well via virt-manager from my client. I had to install acpid to bring the shutdown button of virt-manager to work. But when I shutdown the host, the client is just destroyed, not properly halted. How can I fix that? (I checked it by doing a echo `date` > /root/time in the stop part of a init.d script. The file is never created. Also the host machine shutdown real fast, ~2-3sec!). How should it work? Should the KVM process itself fire the acpi event or should libvirtd talk to the KVM processes?

ATM I use a solution documented here [http://docs.google.com/Doc?id=drjq7vn_0ctn8k3dd]("http://docs.google.com/Doc?id=drjq7vn_0ctn8k3dd")

But it can't be that the default virtualization solution doesnt provide a working shutdown solution, can it? Did anyone have the same problem?

Thanks
falstaff

---

### Post by mystic_drifter on 2010-03-11
I'm having the same problem on a 8.04 host, and currently using some scripts to shutdown the domains prior to host shutdown :(

Have you managed to make it work without the help of customised script?

---

### Post by DuronForever on 2010-03-13
With kvm as the virtualisation solution, it doesn't even support reboot (which ought to be trivial to fix, really -- a shutdown followed by a start after the vm actually stops). I suspect xen might allow a reboot signal to be communicated kernel to kernel, and there is no equivalent in kvm, being that there is no reboot switch in hardware.

An rc script that upon the server going into shutdown or reboot sends a shutdown command to any running domains, then waits n seconds or until everything's dead, and then continues would probably be the neatest way of doing this, and it might be worth making that a part of the standard libvirt package once it's properly developed.

It still won't help with non-acpi clients, which is why you need the wait max n seconds by default (otherwise shutdown hangs entirely on the server, which sucks), and because of that requirement it'll be a problem for really slow clients. But overall, it would make virtualisation on ubuntu easier to deal with, and clients would be subject to fewer randomised Issues.

The script linked to earlier is not Open Source, as far as I can tell (unless anything on google docs automatically goes GPL), so would be unsuitable for direct inclusion. It does seem to work, although the save state process is incredibly slow, apparently -- a 128M memory VM already takes ages to do. The script being sequential doesn't help there -- depending on what exactly is the bottleneck, it might be faster to save states for multiple domains simultaneously.

---

### Post by flickerfly on 2011-01-05
Is there any new information on this issue now that 10.10 is out and it is 10 months later? 

Also, is this why virt-manager can't take these actions?

---

### Post by sdowney717 on 2011-01-05
wow, this is still a problem. I remember from over a year ago  it was doing this.
why not go with vbox 4.0? has usb 2.0 now.
With vbox, you can save the machine state. Then when you restart, it comes back in less than 10 seconds.

---

### Post by flickerfly on 2011-01-06
Further research shows that with a simple 'sudo apt-get install acpid' (not just acpi) on the guest machine the shutdown process works as expected rather than destroying (aka forced power-off) the machine. Apparently certain parameters in the xml config of the machine may also need to be set to identify acpi compatibility.

A reboot still is not performed when requested, but I understand this can be scripted around if desired.

I'd not move to VBox because I'm already well invested in the current solution and a conversion isn't worth the effort, especially since these machines shouldn't be going up and down very often in a production environment. That would be a much bigger problem. This is minor.

I also have some concern about VBox related to who has control of it (see the MySQL drama) and the separate license for Extension packs (the PUEL) which are required for USB 2, PXE, etc. It is only GPL on the base. I hesitate when the first hit is free. Otherwise, I recognize it as a valid and interesting virtualization technology.

---

### Post by ravenswood1000 on 2012-02-18
Installed acpid. Still just shuts down the vm's

---

### Post by jwxie on 2013-03-03
> sudo apt-get install acpid

works for me like a charm! thanks!

---

### Post by wildmanne39 on 2013-03-05
Old thread closed!

---

