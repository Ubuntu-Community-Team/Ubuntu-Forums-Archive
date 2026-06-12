---
title: "ACPI Error"
date: 2010-07-04
forum: Server Platforms
---

### Post by zhangr on 2010-07-04
I've installed "Lucid Lynx" (Server) on an Intel Server Board S5000VSA. And these days, It always freeze after working normally 1~3 days. I've installed logcheck to track log files, there's 2 lines in kern.log:
ACPI Error: Field [CPB3] at 96 exceeds Buffer [NULL] size 64 (bits) (20090903/dsopcode-596)
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_._OSC] (Node ffff88011fc25c60), AE_AML_BUFFER_LIMIT

Nothing else interesting. Any one can point out what's wrong with it? I've installed kvm/qemu on this box, but has not configured yet, since I know kernel module kvm_intel can't be loaded since my board or cpu doesn't support "vmx" (grep "^flags.* vmx" /proc/cpuinfo). Help me, please.:frown:

---

