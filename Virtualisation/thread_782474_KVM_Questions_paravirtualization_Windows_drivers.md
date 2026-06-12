---
title: "KVM Questions: paravirtualization? Windows drivers?"
date: 2008-05-05
forum: Virtualisation
---

### Post by HarvesterOfBeer on 2008-05-05
I'm running Hardy AMD64 (BE-2300). I've gotten KVM installed, and have set up and run a XP Pro VM. That works ok, but I have some questions for the hive mind:

[LIST=1]
[*]What do I need to do to enable paravirtualization as an option when creating new machines with virt-manager?
[*]Are there Windows guest drivers (a la VMWare)? If so, can somebody point me to them?
[*]I tried setting up a Hardy i686 guest (AMG64 host), and I get through the initial boot of the ISO ok, but it hangs when starting the live GUI...any ideas?
[*]Is there support in KVM for doing VM snapshots like VMWare allows?
[/LIST]

Thanks!

---

### Post by David Cartwright on 2008-05-05
Some suggestions:
1. Make sure that virtualization is enabled in the BIOS. At least with Intel motherboards my experience is that virtualization is often turned-off in the BIOS, so you might be using QEMU only rather than QMEU/KVM. Due to the speed and functional advantages of KVM, this is not a good thing!

2. Some step-by-step instructions on Windows paravirtual network drivers here:
[http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers]("http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers")

3. Info on using the latest Intel network drivers rather than paravirtual drivers can be found here:
[http://www.linux-kvm.com/content/how-do-you-use-e1000-option-a-windows-guest]("http://www.linux-kvm.com/content/how-do-you-use-e1000-option-a-windows-guest")

4. Rather than just snapshots, KVM supports live migration across disparate hardware. More info on that here:
[http://kvm.qumranet.com/kvmwiki/Migration]("http://kvm.qumranet.com/kvmwiki/Migration")

cheers ... david

---

### Post by HarvesterOfBeer on 2008-05-06
> **David Cartwright said:**
> Some suggestions:
1. Make sure that virtualization is enabled in the BIOS. At least with Intel motherboards my experience is that virtualization is often turned-off in the BIOS, so you might be using QEMU only rather than QMEU/KVM. Due to the speed and functional advantages of KVM, this is not a good thing!


I can see the virtualization flag when I look at the /proc output on the host, so I think we're ok there. I'll reboot the box tonight and check the BIOS.

Is there a special kernel I need to run (a la Xen) to use paravirtualization in KVM?

> 
2. Some step-by-step instructions on Windows paravirtual network drivers here:
[http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers]("http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers")

3. Info on using the latest Intel network drivers rather than paravirtual drivers can be found here:
[http://www.linux-kvm.com/content/how-do-you-use-e1000-option-a-windows-guest]("http://www.linux-kvm.com/content/how-do-you-use-e1000-option-a-windows-guest")



I've looked through those pages...they seem to imply that running bridged networking (which I'm doing) is the fastest, followed by paravirtualized drivers, then e1000, then whatever the default is. Confirm?

> 
4. Rather than just snapshots, KVM supports live migration across disparate hardware. More info on that here:
[http://kvm.qumranet.com/kvmwiki/Migration]("http://kvm.qumranet.com/kvmwiki/Migration")

cheers ... david

Live migration is slick, but in this case I have only one host. I want to be able to set up a base machine, snapshot it, test some things, and then quickly revert back to the clean state. I could backup the whole file, but that's a little cumersome with a 30GB XP image...

Did I just miss something on that page?

Thanks!

-HoB

---

### Post by David Cartwright on 2008-05-06
> **HarvesterOfBeer said:**
> I can see the virtualization flag when I look at the /proc output on the host, so I think we're ok there. I'll reboot the box tonight and check the BIOS.

Yes, because even though your CPU supports hardware virtualization doesn't necessarily mean that it is enabled in the BIOS.

> **HarvesterOfBeer said:**
> Is there a special kernel I need to run (a la Xen) to use paravirtualization in KVM?

No special kernel needed. That's another of the huge advantages of KVM.

> **HarvesterOfBeer said:**
> I've looked through those pages...they seem to imply that running bridged networking (which I'm doing) is the fastest, followed by paravirtualized drivers, then e1000, then whatever the default is. Confirm?

The software drivers you use for each VM are a separate issue to the bridge networking on your host. Hence, the article by Haydn Solomon about creating an emulated e1000 NIC is relevant with various types of host networking, including bridge networking.

> **HarvesterOfBeer said:**
> Live migration is slick, but in this case I have only one host. I want to be able to set up a base machine, snapshot it, test some things, and then quickly revert back to the clean state. I could backup the whole file, but that's a little cumersome with a 30GB XP image...

You can use the command line utility **virsh** to create snapshots. I gather you have checked the Ubuntu doc on KVM here:
[https://help.ubuntu.com/community/KVM]("https://help.ubuntu.com/community/KVM")

but the best documentation I have found on virsh is here:
[http://fedoraproject.org/wiki/Docs/Fedora8VirtQuickStart#head-4719f3d9bcb5697d28df06eb674235c0fcea2fd1]("http://fedoraproject.org/wiki/Docs/Fedora8VirtQuickStart#head-4719f3d9bcb5697d28df06eb674235c0fcea2fd1")

see the section **Managing Virtual Machines from the command line with `virsh`**.

You could also use QEMU to create snapshots, but clearly virsh and virt-manager are where KVM management is heading.

---

### Post by quad3d@work on 2008-05-06
> **David Cartwright said:**
> Yes, because even though your CPU supports hardware virtualization doesn't necessarily mean that it is enabled in the BIOS.

You'll be surprised.... had to upgrade couple Optiplex 740s at work in order for AMD-V to work. It's not even a BIOS option for you to choose in those Dells...

---

### Post by artichoke on 2009-06-24
More recent (permanent?) link: [http://fedoraproject.org/wiki/Virtualization_Quick_Start](http://fedoraproject.org/wiki/Virtualization_Quick_Start)

---

### Post by juancarlospaco on 2009-06-24
**Here is all that are you asking for :**

**[http://www.convirture.com/wiki/index.php?title=Installation#Ubuntu_8.10]("http://www.convirture.com/wiki/index.php?title=Installation#Ubuntu_8.10")**

---

