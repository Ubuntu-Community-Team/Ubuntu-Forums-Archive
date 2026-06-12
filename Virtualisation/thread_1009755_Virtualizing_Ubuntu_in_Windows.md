---
title: "Virtualizing Ubuntu in Windows"
date: 2008-12-13
forum: Virtualisation
---

### Post by Arukas on 2008-12-13
Here's a question I am not for sure about.

If my host OS is Windows, and I run a guest OS, such as ubuntu.  Then if I surf the Web using Ubuntu, is it still as secure? or is it comproised my having windows running as the host os?

Or is it just the same as running firefox in windows normally?

---

### Post by bodhi.zazen on 2008-12-13
> **Arukas said:**
> Here's a question I am not for sure about.

If my host OS is Windows, and I run a guest OS, such as ubuntu.  Then if I surf the Web using Ubuntu, is it still as secure? or is it comproised my having windows running as the host os?

Or is it just the same as running firefox in windows normally?

With Virtualization the host and guest are kept as separate as possible.

So it is best to think of the guest as a stand alone machine.

So yes, running Ubuntu is , IMO, more secure then Windows. I am sure you will get varying opinions depending on who you ask, but this is after all an Ubuntu site :)

---

### Post by Greyed on 2008-12-13
> **Arukas said:**
> If my host OS is Windows, and I run a guest OS, such as ubuntu.  Then if I surf the Web using Ubuntu, is it still as secure? or is it comproised my having windows running as the host os?

Or is it just the same as running firefox in windows normally?

When you're browsing in the VM the Windows machine is effectively a router at that point.  It is used to pass traffic to and from the VM, nothing more.  So if there are any security issues with the Windows networking stack you may have to worry about those.  However, from the browser level, yes, it is the same as running it on a native Linux box.

---

### Post by Dedoimedo on 2008-12-14
Hi,

In general, virtualization does not replace good security practices. Although it is difficult for guest os to break through to the host, it is possible, especially if you use features like samba sharing, shared folders etc.

Ubuntu is safer and you'll be much better off using it, when it comes to web security, although in general, if you know what you're doing, it makes no difference.

Dedoimedo

---

