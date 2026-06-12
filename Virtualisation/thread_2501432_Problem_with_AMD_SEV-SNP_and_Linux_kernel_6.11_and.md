---
title: "Problem with AMD SEV-SNP and Linux kernel 6.11 and QEMU 9.1.5"
date: 2024-10-07
forum: Virtualisation
---

### Post by dmiladin on 2024-10-07
[COLOR=#1F2328][FONT=-apple-system]Hi everyone,
[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]Sorry to bother you here, but does anybody know the solution to the problem of booting an SEV-SNP VM with Linux kernel 6.11 on the host and QEMU 9.1.5. The kernel is downloaded and installed from [here]("https://kernel.ubuntu.com/mainline/v6.11/").
[/FONT][/COLOR]Ubuntu used is 24.04.1 LTS

[COLOR=#1F2328][FONT=-apple-system]QEMU command:[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]qemu-system-x86_64 -enable-kvm \
        -smp 4 \
        -m 8192M,slots=5,maxmem=10240M \
        -cpu EPYC \
        -machine q35 \
        -no-reboot \
        -netdev user,id=vmnic \
        -device virtio-net-pci,disable-legacy=on,iommu_platform=true,netdev=vmnic \
        -drive if=pflash,format=raw,unit=0,file=[COLOR=var(--color-prettylights-syntax-storage-modifier-import)]$OVMF_CODE[/FONT][/COLOR][FONT=-apple-system],readonly=on \
        -drive if=pflash,format=raw,unit=1,file=[COLOR=var(--color-prettylights-syntax-storage-modifier-import)]$OVMF_VARS[/COLOR] \
        -drive file=./ubuntu-base.qcow2,if=none,id=disk0,format=qcow2 \
        -device virtio-scsi-pci,id=scsi0,disable-legacy=on,iommu_platform=true \
        -device scsi-hd,drive=disk0 \
        -machine confidential-guest-support=sev0 \
        -object sev-snp-guest,id=sev0,cbitpos=51,reduced-phys-bits=1 \
        -nographic \
        -monitor pty \
        -monitor unix:monitor,server,nowait

[/FONT]
[COLOR=#1F2328][FONT=-apple-system]I have bult the QEMU from the official QEMU repo (master branch) and used the instruction from this [repo]("https://github.com/AMDESE/AMDSEV/tree/snp-latest"). But I get this error:[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]qemu-system-x86_64: kvm_set_user_memory_region: KVM_SET_USER_MEMORY_REGION2 failed, slot=2, start=0xffc84000, size=0x37c000, flags=0x2, guest_memfd=-1, guest_memfd_offset=0x0: Invalid argument
[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]I have also tried QEMU 9.1.0 but I get the same error.
[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]Thanks.
[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]Kind regards,
Danko[/FONT][/COLOR]

---

