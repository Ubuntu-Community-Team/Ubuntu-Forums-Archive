---
title: "Xen server won't run"
date: 2008-06-23
forum: Virtualisation
---

### Post by adam35413 on 2008-06-23
I have tried using several guides to install Xen on my Ubuntu 8.04 server (NOTE: I do not have the x86_64 version, just the x86 version of server installed).  After I used aptitude to install ubuntu-xen-server (which in turn installed the dependencies), I updated/upgraded my system and got the updates for Xen that came out today.  I did not install the   However when I started Xen, the boot process got stuck in what looked like a big error because all that I could see on the screen was what appeared to be a stack trace.

I tried using "acpi=off" as a flag for booting the Xen kernel, but this just lead to the boot process getting dumped into BusyBox after lots of ata errors.  

Has anyone had any experience getting Xen working on 8.04 Server edition?  I am trying to install on a Dell XPS 1530.

---

### Post by v912485 on 2008-06-26
Hi Adam,

Did you manage to get any further? I'm trying to do exactly the same also on a XPS 1530 and it looks to me that some hald module called hald-addon-dell is causing the problem. I'm now looking to disable it and see if I get any further.
One slight difference though, I do have x86_64 version of Ubuntu 8.04 installed.

Allan

---

### Post by ralic on 2008-06-28
Have either of you tried the all_generic_ide option?
I faced similar problems and managed a boot with that option. It wasn't pretty, but at least it booted... I haven't had time to go any further with it though.

---

