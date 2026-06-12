---
title: "hardware profiles for virtualbox"
date: 2008-08-24
forum: Virtualisation
---

### Post by PeteCox on 2008-08-24
Hi,

I'm trying to use ubuntu as a guest from a Windows XP host using a physical partition (vmdk).

This enables me to boot into Windows when necessary (e.g. for work) but make use of my existing linux system.

It seems to work, aside from some problems with the display driver. (I haven't tried audio much)

Virtualbox resets my xorg.conf file with its own display code (meaning I would manually have to re-configure the display and the nvidia driver)

Regardless, I have to run the guest additions installer after each time I have run ubuntu non-virtualized (e.g. on the raw machine) - otherwise the auto-resize and mouse integration doesn't work.

I'm not sure what gets reset each time...

Is there some easy way ubuntu can detect whether it's running in virtualization and use the special display config for virtualbox or detect it's running on real hardware and use native nvidia acceleration? (Maybe with support for sound and networking etc too?)

Thanks,

Pete.

---

### Post by Technical on 2010-03-28
Any help?
I have the same issue and want hardware profiles.

---

