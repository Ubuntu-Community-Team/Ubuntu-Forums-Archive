---
title: "nvidia-smi has failed because it couldn't communicate..."
date: 2017-11-14
forum: System76 Support
---

### Post by johnrz862 on 2017-11-14
I'm running Ubuntu 16.04 on my System76 machine with a GeForce GTX 750 Ti. I was trying to install CUDA when I realized the driver wasn't properly installed.

I've tried multiple approaches to installing the driver, including nvidia runfiles, software-properties and the System76 drivers [https://launchpad.net/system76-driver](https://launchpad.net/system76-driver), but in all cases, when I run nvidia-smi afterward I get the same error:
```
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```

When I run lspci, I see (among other things):
```
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)
```

I can't run any of the CUDA samples.

Any suggestions would be greatly appreciated. I've burned way too much time on this.

---

