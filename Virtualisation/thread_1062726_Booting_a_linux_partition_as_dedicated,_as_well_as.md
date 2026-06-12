---
title: "Booting a linux partition as dedicated, as well as virtual?"
date: 2009-02-07
forum: Virtualisation
---

### Post by Fzang on 2009-02-07
I was wondering if I could either create a dedicated or a wubi partition and then boot it through VMware or VirtualBox **inside windows**? I'm not using linux for actual work... more like customization and exploring. Also, it's a laptop so suspend/hibernate doesn't always work as one might want and a VMs suspend option would be godlike for me

---

### Post by dcstar on 2009-02-07
> **Fzang said:**
> I was wondering if I could either create a dedicated or a wubi partition and then boot it through VMware or VirtualBox **inside windows**? I'm not using linux for actual work... more like customization and exploring. Also, it's a laptop so suspend/hibernate doesn't always work as one might want and a VMs suspend option would be godlike for me

I know VMware Server VMs can access "real" partitions, but it is not recommended because then you have the potential situation of two OSs having access to the same files when **all** OSs expect sole access to these things.

There are posts in this forum (and many others, I expect) where people have stuffed up things in a major way by doing this sort of thing.

---

