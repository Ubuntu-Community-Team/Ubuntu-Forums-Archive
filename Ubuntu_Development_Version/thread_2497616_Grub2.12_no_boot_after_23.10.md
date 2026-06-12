---
title: "Grub2.12 no boot after 23.10"
date: 2024-05-12
forum: Ubuntu Development Version
---

### Post by maskedlinux on 2024-05-12
Its worth to discuss that, maybe again.
I saw the security flaws lastly and thinked okay, maybe its that, but who knows.

After some digging, i saw, that every image with Grub2.12 can't be booted on my device. That tells me, all devices past 2012 aren't functional to run with actual flavours from 23.10 and newer.

I dont know if there is a backport if the issue is for uefi only, because the guides say, legacy is over.

---

### Post by oldfred on 2024-05-12
I am not having any issue with Kubuntu 24.04
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ grub-install --version [/COLOR]
grub-install (GRUB) 2.12-1ubuntu7 
[COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsb_release -a [/COLOR]
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 24.04 LTS 
Release:        24.04 
Codename:       noble
[/FONT][FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ echo $DESKTOP_SESSION [/COLOR]
plasma

[/FONT]

```

---

