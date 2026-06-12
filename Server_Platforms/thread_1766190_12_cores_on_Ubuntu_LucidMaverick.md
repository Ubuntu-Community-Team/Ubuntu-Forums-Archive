---
title: "12 cores on Ubuntu Lucid/Maverick?"
date: 2011-05-24
forum: Server Platforms
---

### Post by StatsJunkie on 2011-05-24
I am building a computing/research server containing 2 CPUs: 2x Intel Xeon E5645 for a total of 12 cores, and 24GB of RAM. I am looking for a Linux distribution to install on this new system. My current server (single CPU, 2 cores) is running Lucid, and I love it so I am hoping there is some way to overcome the 8 core limit I've read about.

Will I need to do anything special to get Lucid or Maverick to work with all 12 cores on the 64-bit server distro?

---

### Post by StatsJunkie on 2011-05-24
Come to think of it, does this limitation still even exist?

---

### Post by insane_alien on 2011-05-24
should be able to handle 12 cores fine.

that said, i don't know the exact compiler configuration used on ubuntu. If you compile your own the limit is around 256?

it should be fine though.

---

### Post by dtfinch on 2011-05-24
There's a CONFIG_NR_CPUS option in the kernel config. In 7.10 and earlier it was 8. Since either 8.10 or 8.04 it's been 64, at least in the 64 bit kernels. And it might go up to [256 cores](https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/737124) in the near future. The 32 bit kernels might still be limited to 8, judging by [this](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287325), [this](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/623325), and [this](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199526).

---

