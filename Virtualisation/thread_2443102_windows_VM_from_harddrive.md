---
title: "windows VM from harddrive"
date: 2020-05-11
forum: Virtualisation
---

### Post by yaminb on 2020-05-11
I currently have a separate drive that runs Windows 10. I rarely boot into it, but there are times it has.

I've been researching, and there appears to be a way to run windows directly from that separate drive as a VM.

[https://www.linkedin.com/pulse/use-your-windows-10-instantly-inside-ubuntu-linux-from-pavic](https://www.linkedin.com/pulse/use-your-windows-10-instantly-inside-ubuntu-linux-from-pavic)

It seems pretty easy and straight forward.
Does anyone have any experience doing this? Any issues?

Other specific questions:
[LIST=1]
[*]I assume snapshots wouldn't work. Is there a way to disable the option to snapshot in the vmdk for that VM (not for any virtual machine, just for this one)
[*]How would I 'shutdown' windows when done with the VM? (power off?)
[LIST=1]
[*]The article mentions disable hibernate. But what happens if I don't make make changes to the windows and just choose shutdown from windows. I don't care if some extra HD space is used for windows.
[/LIST]

[*]I assume I can play with the CPU/RAM dedicated to the VM.
[/LIST]

Thanks,

---

### Post by yaminb on 2020-05-11
kinda moot, I tried to get it up and running. It doesn't boot in the VM.

---

### Post by DuckHook on 2020-05-11
I would be greatly surprised if anyone could get such a setup working and outright unbelieving if they characterize it as "easy and straightforward".

Windows does not like being fooled. It is tied in very tightly to the bare metal partly as a security measure but also because that's how proprietary software makes you pay for more licenses. If you could easily trick it into running in a VM in the way you ask, it would be easy to port it to any number of VMs. From Redmond's perspective, this is Not A Good Thing.

Windows will tolerate being run within a VM if that is how you installed it to start with, but it's not designed to be an easily portable OS like Linux. Once it's been installed on bare metal, I don't know of any reliable way to port it.

---

