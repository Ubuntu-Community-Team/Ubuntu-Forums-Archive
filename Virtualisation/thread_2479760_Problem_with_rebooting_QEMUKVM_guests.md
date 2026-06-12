---
title: "Problem with rebooting QEMU/KVM guests"
date: 2022-10-05
forum: Virtualisation
---

### Post by Irihapeti on 2022-10-05
I run several QEMU/KVM guests on a host machine with Xubuntu 22.04

Since I changed to 22.04 from 20.04 – a fresh install, not an upgrade – I've had problems with rebooting guests. The guest terminates (as far as I can tell) but the graphics don't turn off and the mouse pointer just flickers. The guest CPU pins at 100%. The only way to stop it is to use force-stop in the Virtual Machine Manager menu. This is largely an inconvenience on a Linux guest, but much more of a worry with a Windows guest which might decide to react badly. So far, guests (including the Windows 10 guest) have restarted normally, but this is clearly not an ideal situation. Sometimes a Linux guest will behave normally if I reboot over ssh, but that isn't guaranteed, either. It seems to make no difference whether the guests are server installs or have a GUI.

Obviously, I should report a bug (or add "affects me, too" to an existing one), but I have no idea which package I should be reporting against. Could someone point me in the right direction? Or maybe even tell me what I might need to investigate to fix it myself.

---

### Post by TheFu on 2022-10-06
I had a similar issue a few years ago, different release obviously.  Installing the acpid and acpi-support packages into each VM seemed to fix it.
If those are already installed, I don't have a possible answer. Sorry.

---

### Post by Irihapeti on 2022-10-06
Thanks. I don't know whether those are installed or not, so that gives me something to have a look at.

---

