---
title: "Precise and Nvidia"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by manzdagratiano on 2012-03-10
Now that I have upgraded my Vaio to Precise as well, the old demons from Nvidia come to haunt me.

Initially, upon booting, nvidia would load sometimes and sometimes not, resulting in a fallback to Vesa (since nouveau is blacklisted by nvidia). I have the following card:

```

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GT] (rev a1)

```

and the latest nvidia package:

```

manjul@cybertron:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.20-0ubuntu1
  Candidate: 295.20-0ubuntu1
  Version table:
 *** 295.20-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status

```

Upon inspecting **Xorg.0.log** and **kern.log**, I found the message, at times of crash:

```

Mar 10 14:03:38 cybertron kernel: [   40.708533] NVRM: The NVIDIA GPU 0000:0100.0 (PCI ID: 10de:0426) installed
Mar 10 14:03:38 cybertron kernel: [   40.708535] NVRM: in this system is not supported by the 295.20 NVIDIA Linux
Mar 10 14:03:38 cybertron kernel: [   40.708536] NVRM: graphics driver release. Please see 'Appendix A -
Mar 10 14:03:38 cybertron kernel: [   40.708537] NVRM: Supported NVIDIA GPU Products' in this release's README,

```

while when the driver does **not** crash:

```

Mar 10 14:06:59 cybertron kernel: [   28.732342] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.20  Mon Feb  6 21:07:30 PST 2012

```

The former is obviously not true since **a)** the driver does work, and **b)** nvidia's website lists the 295.20 driver as the recommended driver for my card.

Has anyone else seen this issue, and is there an existing bug report? (A search does not reveal this particular issue, mainly because I do not know the cause).

At the moment, I have **uninstalled the plymouth-theme-* packages**, which do not play well with nvidia anyway, and the driver seems to be loading fine. However, **since this issue is intermittent**, I will have to test a few more reboots to see if `plymouth-themes' was the cause of conflict (I know plymouth has had its issues, but I do not wish to jump to a hurried conclusion and `blame the maid for the obvious theft').

---

### Post by ronacc on 2012-03-10
try uninstalling whatever driver Ubuntu has installed and hand install the 295.20 driver direct from nvidia . That was a bug early on , the 173 legacy driver was being installed where it didn't belong but I thought they had that fixed . Anyway hand installing the correct driver should work , if not you may have a hardware problem .

---

### Post by manzdagratiano on 2012-03-10
I'll try that... Reinstalling the drivers directly from the repositories had not worked. It seems unlikely to be a hardware problem since I never got this problem up until yesterday when I upgraded to Precise, and this machine has been running Ubuntu with Nvidia since Jaunty.

---

