---
title: "NVIDIA drivers updated now running in low graphics mode"
date: 2010-05-28
forum: System76 Support
---

### Post by |Porsche on 2010-05-28
Hello,
I updated my system last night and saw that some NVIDIA drivers were updated. Today, I was greeted with a nice message stating something about running in low graphics mode. I knew how to fix the issue when I manually installed the proprietary drivers, but now that it all happens from the repositories I have no idea.

Has anyone experienced the same issue? I have a panp6. Any ideas on how to fix?

Below are some lines from the log.

```
May 28 17:44:55 hostname kernel: [   50.908616] nvidia: module license 'NVIDIA' taints kernel.
May 28 17:44:55 hostname kernel: [   51.473142] nvidia 0000:01:00.0: power state changed by ACPI to D0
May 28 17:44:55 hostname kernel: [   51.473150] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 28 17:44:55 hostname kernel: [   51.473158] nvidia 0000:01:00.0: setting latency timer to 64
May 28 17:47:12 hostname kernel: [  189.829533] nvidia: probe of 0000:01:00.0 failed with error -1
May 28 17:51:49 hostname kernel: [   38.668618] nvidia: module license 'NVIDIA' taints kernel.
May 28 17:51:49 hostname kernel: [   39.233196] nvidia 0000:01:00.0: power state changed by ACPI to D0
May 28 17:51:49 hostname kernel: [   39.233206] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 28 17:51:49 hostname kernel: [   39.233215] nvidia 0000:01:00.0: setting latency timer to 64
May 28 22:13:54 hostname kernel: [   34.432117] nvidia: module license 'NVIDIA' taints kernel.
May 28 22:13:54 hostname kernel: [   35.008259] nvidia 0000:01:00.0: power state changed by ACPI to D0
May 28 22:13:54 hostname kernel: [   35.008270] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 28 22:13:54 hostname kernel: [   35.008281] nvidia 0000:01:00.0: setting latency timer to 64
May 28 22:18:27 hostname kernel: [  105.749138] nvidia: module license 'NVIDIA' taints kernel.
May 28 22:18:27 hostname kernel: [  106.310548] nvidia 0000:01:00.0: power state changed by ACPI to D0
May 28 22:18:27 hostname kernel: [  106.310561] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 28 22:18:27 hostname kernel: [  106.310570] nvidia 0000:01:00.0: setting latency timer to 64
May 28 22:23:28 hostname kernel: [  408.469619] nvidia: probe of 0000:01:00.0 failed with error -1
```

---

### Post by |Porsche on 2010-06-01
The issue disappeared after I remove nvidia-195-kernel-source, remove nvidia-195-modaliases, reinstall nvidia-current, and reinstall nvidia-kernel-common.

I think I installed the packages I removed earlier when I was troubleshooting.

---

