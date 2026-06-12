---
title: "ubuntu goes into coma in vmpalyer"
date: 2015-03-10
forum: Virtualisation
---

### Post by matt18 on 2015-03-10
Ello all. It seems i have very very poor luck with vmplayer and any ubuntu install. I currently have Lubuntu installed in vmplayer. Everything works great until i leaave for about 10 minutes and ubuntu goes to sleep. Usually when i wake up an ubuntu in vmplayer, it shows the login window to reactivate the desktop. Nope, it shows my desktop but it is completly froozen and in a coma. cant do anything. Xubuntu does the same thing. regular ubuntu seems to be ok, its just lubuntu and xubuntu. thanks

---

### Post by matt18 on 2015-03-12
has any one else experienced this issue? it seems that lubuntu and xubuntu do this. But ubuntu does not. Even if i install the lxde or xcf environment in ubuntu 14.04, it does not lock or freeze up.

thanks.

---

### Post by oldos2er on 2015-03-12
Moved to Virtualisation.

---

### Post by TheFu on 2015-03-13
Sorry - no answer from me. Just wanted you to know that people have read and considered the posted issue.

I don't let VM hosts sleep (and don't use VMware Player).  If you think about what that means to a VM, you can see the danger.  The VM is happily working along, BAM - mid-instruction, stopped.  When it comes up, the clock is all different, network connections are gone, . Something bad happened. What to do?

I have paused a guest-VM, then hibernated the hostOS (a laptop).  That way the guest is prepared. It should be possible to make the hostOS sleep scripts go through each running VM and tell them to pause. Don't know the VM-player commands, but with virsh ... the **virsh suspend domain** then save that to a file with **virsh save domain state-file** is what I'd use.

Perhaps someone else with experience can comment?

IME - most people lurking here run virtualbox, kvm, or Xen with just a few people using VMware player, workstation on desktops.
Sorry.

---

### Post by sammiev on 2015-03-13
I'm running VMware player on Ubuntu 14.04 which is set never to sleep but all my Linux OS that are setup in the VM can and return from sleep with just a password. Not seeing the problems you are having and I have 2 versions of xubuntu installed.
Wish I could be more help but check your power settings.

---

