---
title: "Virus Guard on VM?"
date: 2008-05-19
forum: Virtualisation
---

### Post by Darksci on 2008-05-19
So do I need to install an antivirus and firewall on a Windows XP VM running on Ubuntu? And do I need to install Windows critical updates as well?

Theres no possible way for any window problems to effect Ubuntu either is there?

---

### Post by bradmkjr on 2008-05-19
Here is my overview of Antivirus information regarding Virtualization, this maybe of some help in general:
[http://x86virtualization.com/x86-virtualization/antivirus-software-and-virtualization-faq.html](http://x86virtualization.com/x86-virtualization/antivirus-software-and-virtualization-faq.html)

to directly answer your questions:

> So do I need to install an antivirus and firewall on a Windows XP VM running on Ubuntu?

It is up to you, if you plan on using the system online for extended lengths of time, if you plan on actualy doing real work on it, that may involve sensitive information, such as banking, or if you don't want to have to rebuild the virtual machine from scratch when a virus destroys it, then yes run antivirus.

If you are using it to play windows games, won't be doing any business on it, and want the fastest performance possible, then feel free to live on the edge and take risks, to enjoy the most out of your games.


>  And do I need to install Windows critical updates as well?
How long do you think you will be using it, do the updates fix any problems you are having, and do you want to waste that part of your life that you will never get back waiting for those updates?

> Theres no possible way for any window problems to effect Ubuntu either is there? 
Virtual machines, currently are the most secure method of isolated computing available, eventually someone may write a virus to exploit a loophole in virtualization technology, but until then you should be safe. Remember, what you will notice is the potential for cpu usuage to goto 100% and remain there until the VM is stopped if there is a virus or endless loop executed.

Also if you decide to mount network shares, shared folders, or mount your ubuntu drive inside the VM, viruses could delete files randomonly from those locations, so be careful moving files between virtual machines and the host system. My suggestion is e-mail them to yourself, on a gmail or yahoo account, as that ensures they pass a rather complete virus scan.

Good Luck, and Enjoy Virtualization,
Bradford Knowlton
[http://x86Virtualization.com](http://x86Virtualization.com)

---

