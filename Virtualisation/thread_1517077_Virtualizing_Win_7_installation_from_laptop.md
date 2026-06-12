---
title: "Virtualizing Win 7 installation from laptop"
date: 2010-06-24
forum: Virtualisation
---

### Post by mydoghasworms on 2010-06-24
I have a special need. I created a vdi from the Windows 7 installation that came with my laptop. I only copied the first 35GB of /dev/sda (which is what I reduced the Win partition to). The problem is that after having turned that into a vdi, I can't boot it, because my laptop now has GRUB installed (for Ubuntu; I am dual booting), so that's what I've got.
GRUB (in the vdi) obviously tries to find the ext4 Linux partition where its files are residing, but they aren't actually there.
I'd like to avoid having to first reinstall the Windows MBR (I don't  have an installation disk anyway, only an HP recovery partition), and  copying the whole thing again.
Is there a way to install GRUB _**in**_ Windows, so I can actually boot Windows using GRUB, without needing a Linux partition, and without needing NTLDR?

---

### Post by mydoghasworms on 2010-07-09
Sorry, I don't like bumping, but I was hoping someone has an answer for this.

---

### Post by JustinR on 2010-07-09
You could use the Ubuntu live CD in VirtualBox to reinstall grub to your VDI using the sudo install-grub command (I believe thats what the command is).

Or if you are a more advanced user you could (at your own risk) use your existing Windows partition in VirtualBox, instead of creating a big VDI file.

---

