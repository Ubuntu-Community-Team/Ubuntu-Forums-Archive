---
title: "VMWare will not power on machine"
date: 2008-08-07
forum: Virtualisation
---

### Post by Ekos on 2008-08-07
I installed workstation and built a Windows XP virtual PC, but when I start it the machine gives me this message.

Version mismatch with vmmon module: expecting 161.0, got 167.0.
You have an incorrect version of the `vmmon' kernel module.
Try reinstalling VMware Workstation.

I attempted to fix with this...

 sudo apt-get install build-essential -y && sudo vmware-config.pl

No good though, has anyone encountered this problem and can offer assistance? I am using the latest ubuntu 8.04LTS

Thanks

---

### Post by overdrank on 2008-08-07
Hi and welcome, I have moved the thread to  Virtualization forum for better support. :)

---

### Post by Ekos on 2008-08-08
Although nobody answered, I figured it out. I cleared any traces of the old software. I then re-installed the latest VMWare Server and it worked. I think I had a new kernel vs older software. Not quite sure.

---

