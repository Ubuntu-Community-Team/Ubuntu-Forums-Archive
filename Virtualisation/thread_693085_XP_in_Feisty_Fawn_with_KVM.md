---
title: "XP in Feisty Fawn with KVM"
date: 2008-02-10
forum: Virtualisation
---

### Post by jvedie on 2008-02-10
Hi all, i am trying install Win XP Pro 64 on Feisty Fawn with KVM, but I can't resolve 2 problems.

1) When I use this command kvm -m 512 -cdrom /media/cdrom/XP_Pro_64.iso -boot d /home/julien/XP_Pro_64_iso/XP_Pro_64.img, the installation starts and then stops on a simple blue screen with "Setup is starting windows" on the status bar.

I tried to press F7 during the installation. This give me 3 choices for the ACPI configuration : ACPI Multiprocessor x64, ACPI Uniprocessor x64 and Other.
I tried each one, but the result is the same as above.

2) I tried the -no-acpi option in the kvm command, but the installation does not start, instead I have this error message "Enable the local advanced programmable interrupt controller (APIC). The x64-based operating system you are loading does not have APIC enabled. ....".

My BIOS has 2 options : ACPI 2.0 compatibility and ACPI APIC support. Both are enabled.

Do you have any ideas about that ?

Thanks

---

### Post by basbeek on 2008-02-12
Hi,

As far as I know the -noacpi option must work with kvm and Windows XP.
At least, the 32-bit edition SP2 version will work.

You could try the 32-bit version but since I think you don't have the license, try to use qemu instead of kvm. (or kvm -no-kvm does the same)

Good luck

Bas

---

### Post by danielhs on 2008-02-21
I'm seeing the exact same issues in gutsy with KVM-60 installed.

I downloaded kvm-60 from the hardy branch.


Daniel

---

### Post by jvedie on 2008-05-17
Everything work fine with 8.04 (Hardy Heron).

Julien

---

