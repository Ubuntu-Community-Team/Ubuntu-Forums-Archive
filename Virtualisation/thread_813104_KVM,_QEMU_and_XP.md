---
title: "KVM, QEMU and XP"
date: 2008-05-30
forum: Virtualisation
---

### Post by rolodoom on 2008-05-30
I haven't been able to install XP on qemu using KVM . It doesn't boot after xp installer copies files.

I read something about an APIC trouble but don't know.

Any suggestions??

---

### Post by igwk on 2008-05-30
Start kvm with the -no-acpi command-line option.  Apparently if you have ACPI enabled in the virtual machine, it tries to write to a ACPI register a lot and causes the VM to run slowly because kvm has to virtualize the ACPI registers.  A Windows XP guest seems to run just fine without ACPI enabled.  For reference, I'm running WinXP under kvm on hardy with the following command-line:

kvm -hda ~/vm/winxp_vm.qcow2 -cdrom /dev/cdrom -m 768 -soundhw es1370 -no-frame -no-acpi -localtime &

Hope that helps!

---

