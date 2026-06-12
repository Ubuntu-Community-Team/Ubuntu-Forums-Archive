---
title: "vmware-to-qemu with ubuntu host, uefi-arch guest"
date: 2015-03-18
forum: Virtualisation
---

### Post by ivo-welch on 2015-03-18
my host is a standard ubuntu 14.10 .

I have an arch vmware guest installation that boots from EFI (GPT) in the VMware vmplayer .  It runs fine, but I would rather run an open vm emulator.  I started with

     # apt-get install qemu-img ovmf .

it is qemu version 2.1.0.

next, I did

     $ qemu-img convert Virtual\ Disk.vmdk disk1.img

if only not to mess up my working vmware player guest after I fail.  Then I tried various versions of

     $ qemu-system-x86_64 -L /usr/share/seabios/ -m 4096 -hda disk1.img

with and without -L varieties.  alas, it says "Booting from Hard Disk" and then goes on vacation.

am I missing something obvious?  I have read for the last 2 hours various documents on the web about qemu and migration (many of which are out of date).

or is this simply a bridge to far?  (will uefi support be integrated into qemu?)

---

### Post by ivo-welch on 2015-03-18
I now suspect this is a GPT (either EFI or BIOS) problem with qemu.  I get the same error in an arch install.

---

### Post by redger on 2015-03-19
The Ubuntu versions of EFI are not necessarily the latest ... for instance the one supplied with 14.04 LTS doesnt' work for me

You might want to try the "pure efi" build from here - [https://www.kraxel.org/repos/jenkins/edk2/]("https://www.kraxel.org/repos/jenkins/edk2/").  
Extract OVMF-pure-efi-fd from the rpm and copy to /usr/share/ovmf and create a "reference" copy as OVMF.fd (take a copy of Ubuntu version first &#8211; just in case). Then create a link or copy in /usr/share/qemu

Then define the "-bios" parameter to qemu pointing to the new copy of OVMF-pure-efi-fd

check your  other qemu parameters

---

