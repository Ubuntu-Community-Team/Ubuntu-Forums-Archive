---
title: "Ubuntu, VMWare, Windows, Quickbooks.  Work?  Stable?"
date: 2014-08-01
forum: Virtualisation
---

### Post by jamal4 on 2014-08-01
I've been running a separate Windows machine just to host Quickbooks for a while now.  I'd like to see if it will work on VMWare/Windows with Ubuntu.  Does anybody know if this will work?  If so can I expect rock solid stability?  I currently run Centos 6.5 to host a file, email, web server.  I'd like to switch to Ubuntu to host those + the VMWare Windows.  I'm wondering if it will work and be stable.

Thanks.

---

### Post by ian-weisser on 2014-08-01
Well, I have run Virtualbox + XP + Quickbooks on an Ubuntu host for years.
It's been rock solid, though the host hardware is rather weak so it's a bit (annoyingly) slow.
So sure, it will work and be stable.

However, my primary QB install is _always_ on a dedicated, low-risk,  low-complexity, off-network machine with frequent backups. Basic risk management: The potential cost of data failure/theft/recovery is high (payroll and tax payments must be *on time*, no matter what) so I keep the risk of failure/theft/loss low.

I use the VM for my secondary install, so I can analyze the company file copy at home.

---

### Post by mooreted on 2014-08-01
I've been running a Windows 7 VmWare VM for years for things like TurboTax. I have never had a problem. You need lots of RAM and a fast processor for a smooth experience, but it's been rock solid for me.

---

### Post by TheFu on 2014-08-02
Virtualization is a well-worn path now.  Stability is a given these days with the well-know VM technologies.  We dumped VMware-every thing 2+ yrs ago here and have never missed any of it. KVM rocks, completely.

On properly sized hardware, with properly configured VM settings, for office-productivity applications, running inside a VM is the same (99.9999%) of running on dedicated hardware.  I don't think of VMs as being special and actually use most physical servers as VM hosts only.  Heck, I even run Windows Media Center inside a KVM VM, primarily for recording TV from 4 tuners concurrently, but Quicken also run inside that VM (limiting MS-Windows installs is a core value here).

For years, I did run Quicken under WINE, but not everything worked and some screens would be empty. Running inside a VM, it has never been any different than running on a native, physical box.

---

