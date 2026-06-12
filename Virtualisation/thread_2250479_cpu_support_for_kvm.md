---
title: "cpu support for kvm"
date: 2014-10-28
forum: Virtualisation
---

### Post by jwanutt on 2014-10-28
I have a xeon 1231 cpu and vt-d is enable in bios.  The command 'kvm-ok' is returning that my cpu doesn't support kvm extensions.  this seems strange for a new intel cpu.  Am I doing something wrong? Whats the next best options for creating vm desktop cpu's?

Thanks!

---

### Post by TheFu on 2014-10-29
Check the BIOS settings. Look for "virtualization".
VT-d is for virtual I/O.
For CPU virtualization, you need to enable vt-x (or whatever AMD calls their version). There should be a BIOS setting "enable CPU Virtual extensions" - or something like that.
[http://www.linux-kvm.org/page/FAQ#What_do_I_need_to_use_KVM.3F](http://www.linux-kvm.org/page/FAQ#What_do_I_need_to_use_KVM.3F) provides specific things to verify your CPU is capable and BIOS is configured for virtualization.

BTW, virtualbox does NOT require these to work. In the old days (3+ yrs ago) virtualbox was reported to run faster without vt-x enabled, but will use it if available. If your motherboard vendor was nasty, they could have removed the BIOS setting for VT-x just to screw with you. I've seen this, mostly on laptops.

---

### Post by jwanutt on 2014-10-29
Thanks.  I see the option to enable virtualization and VT-d, I don't see a specific one for vt-x thought?  I would suprised if a newer xeon server grade cpu wouldn't fully support virtualization.  here's a link to the spec's: [http://icecat.us/p/intel/bx80646e31231v3/prozessoren-0735858279123-E3-1231+v3-21995843.html](http://icecat.us/p/intel/bx80646e31231v3/prozessoren-0735858279123-E3-1231+v3-21995843.html).
Is virtualbox much slower now?  I was assuming kvm would be faster.  I'm wanting to create windows vm's for desktop applicaton testing.

---

