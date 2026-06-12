---
title: "Can Xen Provide my Solution?"
date: 2008-01-14
forum: Virtualisation
---

### Post by yottabit on 2008-01-14
Any Xen experts lurk here?

I have two requirements for a new virtualized environment, and I'm really hoping Xen will fit the bill since VMware Server, and I believe KVM, will not:

[LIST=1]
[*]RAID Support: can I use Linux soft-RAID on the native OS (dom0)? How about support for soft-RAID controllers such as Promise cards?
[*]Access to native (dom0) PCI resources: one OS we need to virtualize is a win32 server for fax serving. This application requires access to a PCI card that handles the incoming and outgoing faxes from our phone system. Will Xen/dom0 allow direct access to a PCI card from within a VM? (VMware Server will not...)
[/LIST]

Thanks everyone! I really would like to use Xen to replace these 6 servers... otherwise I will be stuck with using a win64 server as the native OS for VMware Server, and having the fax server on the native OS... talk about a pig!!

J

---

### Post by fjgaude on 2008-01-14
I've been around this forum for about a year and there has been about two Xen posts... no experts.

The best way to find out if Xen will do what you wish is to try it:

[http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories)

It's not too hard to install. Good luck and please let us know how you do.

---

