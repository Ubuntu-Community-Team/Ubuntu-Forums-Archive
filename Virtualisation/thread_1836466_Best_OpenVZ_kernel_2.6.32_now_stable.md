---
title: "Best OpenVZ kernel 2.6.32 now stable"
date: 2011-08-31
forum: Virtualisation
---

### Post by narcisgarcia on 2011-08-31
[http://openvz.org/pipermail/announce/2011-August/000250.html](http://openvz.org/pipermail/announce/2011-August/000250.html)
> == Stable: RHEL6 ==

This is to announce that RHEL6-based kernel branch
(starting from kernel 042stab035.1) is now marked
as stable, and it is now the recommended branch to use.

We are not aware of any major bugs or show-stoppers
in this kernel. As always, we still recommend to test
any new kernels before rolling out to production.

New features of RHEL6-based kernel branch (as compared to
previous stable kernel branch, RHEL5) includes better
performance, better scalability (especially on high-end
SMP systems), and better resource management (notably,
vSwap support -- see [http://wiki.openvz.org/VSwap](http://wiki.openvz.org/VSwap)).

RHEL6 kernels can be downloaded from
[http://wiki.openvz.org/Download/kernel/rhel6](http://wiki.openvz.org/Download/kernel/rhel6)

== Frozen: 2.6.27, 2.6.32 ==

Also, from now we no longer maintain the following
kernel branches:

   * 2.6.27
   * 2.6.32

No more new releases of the above kernels are expected.
Existing users (if any) are recommended to switch to
other (maintained) branches, such as RHEL6-2.6.32 or
RHEL5-2.6.18.

This change does not affect vendor OpenVZ kernels
(such as Debian or Ubuntu) -- those will still be
supported for the lifetime of their distributions
via the usual means (i.e. bugzilla.openvz.org).

== Development: none ==

Currently, there are no non-stable kernels in development.
Eventually we will port to Linux kernel 3.x, but it might
not happen this year. Instead, we are currently focused
on bringing more of OpenVZ features to mainstream Linux
kernels.

Regards,
   OpenVZ team.

**Does somebody know if it's better to convert RPM package or to compile Ubuntu Lucid's source with the patch?**

---

### Post by bodhi.zazen on 2011-08-31
> **narcisgarcia said:**
> [http://openvz.org/pipermail/announce/2011-August/000250.html](http://openvz.org/pipermail/announce/2011-August/000250.html)


**Does somebody know if it's better to convert RPM package or to compile Ubuntu Lucid's source with the patch?**

It is best to use a supported distro, such as Centos or rhel or proxmox or Debian (if the openvz kernel is in the debian repos).

Second best is to apply the patch yourself to the kernel source. This often fails as most distros patch the kernel and thus the patch may or may not work as expected (at least that has been my experience when attempting to apply the patch for many years of openvz).

If all else fails, you can try extracting the rpm.

[http://www.cyberciti.biz/tips/how-to-extract-an-rpm-package-without-installing-it.html](http://www.cyberciti.biz/tips/how-to-extract-an-rpm-package-without-installing-it.html)

You can then review the contents and manually install them onto your system.

As a last resort, you can try converting the rpm with alien, usually the post install scripts fail with the openvz kernel.

I think a better question is why pound a square peg through a round hole ?

There is nothing wrong with a Centos or Scientific host , or proxmox if you want Debian.

But openvz is poorly supported in the Ubuntu community, and thus when you have a problem, with a custom kernel, you are going to be on your own. This is not so good when running openvz.

If you insist on using Ubuntu, you really should look at LXC which is better supported on Ubuntu.

---

### Post by narcisgarcia on 2011-08-31
Thanks, it's a very good response, and I needed it.

---

