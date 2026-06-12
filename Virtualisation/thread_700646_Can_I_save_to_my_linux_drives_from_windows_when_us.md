---
title: "Can I save to my linux drives from windows when using KVM?"
date: 2008-02-18
forum: Virtualisation
---

### Post by QwUo173Hy on 2008-02-18
I'm only installing Windows so MS office can be used. I need to be able to save my work back on the host system in a convenient way for this particular user.

Is this possible?

---

### Post by fjgaude on 2008-02-18
I sure do that in VMware Server, the free one. All you need is to use Samba shares, set them up in the host and you should be good to go.

---

### Post by QwUo173Hy on 2008-02-18
Thanks fjgaude. I'll try doing that with KVM tomorrow and see how I get on.

Do I just set up a Samba share on Ubuntu and look for it in the network neighbourhood in Windows?

---

### Post by fjgaude on 2008-02-18
That's right... look for the shares in Network Places, or some such name. Works great, from Windows apps and from Explorer.

You can go the other way by setting your drives in Windows as shares and then using your Ubuntu File Manager to get at them.

Transfers work both ways... give your vm a guest name and put its IP in your Ubuntu hosts file, /etc/hosts, and it becomes easy, command line or file browser.

Let us know if you run into issues.

---

### Post by QwUo173Hy on 2008-02-18
Thank you so much. I will definitely get back to you if I have any issues. Can I ask why you  chose to use VMware and not KVM? I've heard that KVM is faster. I have experience with KVM so I'll probably set that up for him just to make things easier but I am curious of your opinion.

All the best,
Jarlath

---

### Post by fjgaude on 2008-02-18
When I started using virtual machines I didn't know of KVM, but Xen was coming up. Neither seem to be where VMware Server is today. VMware is very mature product, and it's free. So I stay with it. I can't really tell any speed loss from the host once the guest is up and running.

I'm satisfied with VMware and its full support for all my hardware, USBs, drives, printers, scanners, etc., the Tools as it is called.

Let us know if you have any hardware, tool problems.

---

