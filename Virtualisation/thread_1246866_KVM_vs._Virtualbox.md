---
title: "KVM vs. Virtualbox"
date: 2009-08-22
forum: Virtualisation
---

### Post by Levander on 2009-08-22
About to upgrade to Jaunty.  Wondering if I should go with KVM or Virtualbox for a guest Vista install.

Reading around, even on the desktop KVM is running on, it looks like you can only get to the guest OS using rdesktop?  Is this true?  I'm using a really old version of Ubuntu and Virtualbox now, and I'm looking directly at the Windows desktop, don't have to go through rdekstop at all.

rdesktop slows down access to the remote desktop quite a bit doesn't it?

I've seen people mention Virtualbox is faster than KVM.  Anyone know the architectural reasons why?

I've seen Virtualbox lets you access hardware accelerated graphics in a Windows guest.  Does KVM let you do that?

---

### Post by bodhi.zazen on 2009-08-23
> **Levander said:**
> About to upgrade to Jaunty.  Wondering if I should go with KVM or Virtualbox for a guest Vista install.

Either will work.

> Reading around, even on the desktop KVM is running on, it looks like you can only get to the guest OS using rdesktop?  Is this true?

No. KVM has a built in VNC server and your guest will run in a window, just like virtualbox. I think you are getting your information from virsh, which is a command line front end for KVM.

> I'm using a really old version of Ubuntu and Virtualbox now, and I'm looking directly at the Windows desktop, don't have to go through rdekstop at all.

See above.

> rdesktop slows down access to the remote desktop quite a bit doesn't it?

How so ?

> I've seen people mention Virtualbox is faster than KVM.  Anyone know the architectural reasons why?

Personally I think KVM is faster. Google search benchmarks.

> I've seen Virtualbox lets you access hardware accelerated graphics in a Windows guest.  Does KVM let you do that?

No, Virtualbox has better graphics and better desktop integration then KVM.

---

### Post by Levander on 2009-08-23
> **bodhi.zazen said:**
> No, Virtualbox has better graphics and better desktop integration then KVM.

How does Virtualbox have better graphics and desktop integration?

---

### Post by Levander on 2009-08-23
> **bodhi.zazen said:**
> 
> 
rdesktop slows down access to the remote desktop quite a bit doesn't it?
How so ?


Because of the extra network layer introduced between rdesktop and the desktop itself.  Is rdesktop fast enough to watch movies?

---

### Post by bodhi.zazen on 2009-08-23
> **Levander said:**
> How does Virtualbox have better graphics and desktop integration?

See the VirtualBox additions. There is no equivalent in KVM.

> **Levander said:**
> Because of the extra network layer introduced between rdesktop and the desktop itself.  Is rdesktop fast enough to watch movies?

I don't know, I do not run Windows, and I would advise against running anything demanding of graphics or audio on Virtualization at the moment.

---

