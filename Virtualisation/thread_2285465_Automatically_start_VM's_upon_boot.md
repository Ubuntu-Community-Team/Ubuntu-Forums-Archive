---
title: "Automatically start VM's upon boot"
date: 2015-07-06
forum: Virtualisation
---

### Post by number2wo on 2015-07-06
Hey

The request is simple, I'm just fairly new, so not sure how to work around it.

I'm running Ubuntu 14.04 with Xen running to virtualize 2x PV Guest VM's.
My issue is, how I tell my system to initialize my 2 VM's upon boot (that is the primary system).

Current setup is:
I have edit'd /etc/rc.local with 2 commands, *xl create -c /etc/xen/VM1.cfg *& *xl create -c /etc/xen/VM2.cfg, *to initialize the VM's, however only VM1 is initializ'd, because it's 1st in the sequence.
I'm assuming that VM2 isn't initializ'd because it's trying to run the 2nd command in the same session as VM1 was initializ'd in, but since it jumps into VM1's console after initialization, it's not able to execute the 2nd command.

The question is: How do I initialize both VM's upon boot? I assume there are other ways, perhaps better options to perform this?

Sincerely, number2wo

---

### Post by TheFu on 2015-07-07
I haven't used Xen in a few years, but in the old days (xm) a symlink of the VM settings into an autostart/ directory was all that was needed. This was somewhere under /etc/xen/ ...  VMs where started alphabetically, so you may want to change the resulting link-name to control that too.  I used numbers.

Google found this: [http://support.citrix.com/article/CTX133910](http://support.citrix.com/article/CTX133910) and [http://wiki.xenproject.org/wiki/VM_Startup](http://wiki.xenproject.org/wiki/VM_Startup)

---

