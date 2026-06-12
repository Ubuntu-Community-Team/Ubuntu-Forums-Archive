---
title: "Virt-manager : Where is cpu affinity settings?"
date: 2018-11-13
forum: Virtualisation
---

### Post by sfatula on 2018-11-13
Every guide or doc I can find on the internet shows a cpu affinity setting option on the virt-manager gui CPUs screen, but it is not there on xUbuntu 18.04.1. Is the uBuntu version different for some reason? What might I be missing? I probably can set these from command line, but really prefer to use the GUI. The virt-manager changelog shows those settings as being available quite a long time ago at a pretty old version.

---

### Post by TheFu on 2018-11-13
I looked for it under 16.04.5 virt-manager and it isn't there.
I remember seeing it from prior versions too.  Don't know what happened.

I have these versions of libvirt and virt-manager:
```
ii  libvirt0:amd64                              1.3.1-1ubuntu10.24                           amd64        library for interfacing with different virtualization systems
ii  virt-manager                                1:1.3.2-3ubuntu1.16.04.4                     all          desktop application for managing virtual machines
```

---

### Post by KillerKelvUK on 2018-11-14
Wow so I've never ever seen pinning as an option in virt-manager, always done it via virsh but did a quick google and found what you said, loads of references and screen shots of this in virt-manager's processor config, odd!

```

[FONT=monospace]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 17.10
Release:        17.10
Codename:       artful

[/FONT][FONT=monospace][COLOR=#000000]ii  [/COLOR][COLOR=#FF5454]**virt**[/COLOR][COLOR=#000000]-manager                                    1:1.4.0-5ubuntu2.1                                         all          desktop application for managing [/COLOR][COLOR=#FF5454]**virt**[/COLOR][COLOR=#000000]ual machines[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]ii  lib[/COLOR][COLOR=#FF5454]**virt**[/COLOR][COLOR=#000000]0:amd64                                  3.6.0-1ubuntu6.8                                           amd64        library for interfacing with different [/COLOR][COLOR=#FF5454]**virt**[/COLOR][COLOR=#000000]ualization systems[/COLOR]
[/FONT]
```

As you say, cli route using virsh goes something like...

```

virsh vcpupin *name-of-guest*

```

---

### Post by sfatula on 2018-11-14
I have even found some recent ubuntu screenshots that show the pinning. It's just weird. As a new user of virt-manager, it seemed odd. I understand for you long timers you may never have noticed, etc. But it's not a big deal, just thought I was using it wrong somehow since I've never seen a screenshot without it (that I came across). Of course, the internet is not always correct as we know. 

Thanks for the responses.

---

