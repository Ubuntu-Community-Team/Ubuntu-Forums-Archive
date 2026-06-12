---
title: "Slow boot / job dev_tmp hang 24.10"
date: 2024-08-15
forum: Ubuntu Development Version
---

### Post by MyMurry on 2024-08-15
Hello,

I tried the actual daily of Ubuntu 24.10. And the boot hang at job dev_tmp for 1:30min.

sudo dmesg | grep tpm
[    1.193715]  tpm_tis_remove+0xaa/0x100
[    1.193719]  tpm_tis_core_init+0x235/0x850
[    1.193722]  tpm_tis_init.part.0+0xc1/0x140
[    1.193726]  tpm_tis_plat_probe+0xc6/0x110
[    1.194019] tpm_tis: probe of MSFT0101:00 failed with error -1
[    3.906777] systemd[1]: Expecting device dev-tpmrm0.device - /dev/tpmrm0...

---

### Post by MyMurry on 2024-08-15
systemctl mask dev-tpmrm0.device

Now it boot fast. For which package can I report this? Systemd?

---

### Post by Claus7 on 2024-08-17
Hello,

going to synaptic and typing systemd and choosing the systemd package for its installed files, I came across this: /usr/bin/systemctl

so I think that you have the answer.

Regards!

---

