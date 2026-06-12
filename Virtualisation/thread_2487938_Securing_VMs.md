---
title: "Securing VMs"
date: 2023-06-18
forum: Virtualisation
---

### Post by mikodo on 2023-06-18
Hello everyone!  I am not doing VMs right now, only reading. I have read more than once in this forum, the importance of 'Securing VMs'. 

So, I have started looking and see similar suggestions as in this page: 

 [https://www.computerworld.com/article/2769235/securing-your-virtual-environment.html](https://www.computerworld.com/article/2769235/securing-your-virtual-environment.html) 

 What should be added to or taken away from that list?  Thanks

---

### Post by ajgreeny on 2023-06-18
I suspect a large majority of that should be taken away, as you put it.  Did you even notice that it was written in 2009, 14 years ago, so is at least now incredibly outdated and probably fairly meaningless in many ways, though do not take this as the final thought on the subject.

Will Xubuntu or some other OS be your host machine ?
Which hypervisor will you be using for the VMs; VirtualBox, VmWare, or the better choice in my opinion, KVM/QEMU?
What OS will you be using for the VMs; Linux distros or Windows?  If Windows you should definitely use an antivirus of some sort but if Linux there's no point.

---

### Post by mikodo on 2023-06-18
Thanks for the reply.

No, I didn't notice that it was an old post. (I never look to see when the pages are posted. I guess I need to start).

So; I plan to have Debian Stable as my host OS, with one of my VMs being Xubuntu. I plan not to have Windows installed, (virtually or on hard-disk). I have been reading about KVM/QEMU and I think I want to use it now. I have used VirtualBox before, and still see LXC Containers as too geeky for me and not with a lot of documentation.

I only glossed over the anti-malware stuff. 

Thanks again.

---

