---
title: "Migrating a file server from Win7 to Ubuntu and permissions"
date: 2015-06-09
forum: Security
---

### Post by spacexion on 2015-06-09
Hi everybody,

I've got at home a desktop PC that I'm using both as a home file-server and media-center.

At the moment the configuration is quite simple:[INDENT]- OS  is Windows 7
- Files are located over 4 HDD, all formatted as NTFS
- Permissions are managed through NTFS only (share permissions: "everyone" > read+write).
- All the PCs in the LAN are in the same workgroup
- My own account has full control on file-server data and is also admin on all PCs in the LAN
- My wife's account has full rights access on some shared folders and read-only on others
- there is no guest access at all
- LAN clients are mixed: Windows, Linux and Android.[/INDENT]

Today I want to migrate this file-server to Ubuntu, and change a little bit the permissions configuration. I want to have a new local admin on the server  with full access, and my usual account, which logs in remotely from the LAN clients, as read-only. My wife's account should stay unchanged, keeping write permissions on the folders which belong to her, and read-only on the others.

I'm a little bit worried because I'm not sure about what will happen to the NTFS permissions that are already in place, when I will run Ubuntu on this machine.
I'm trying to understand if I will be able to keep a similar system and LAN configuration as today with Windows with a minimal effort, or if I should schedule  some major changes.
 
So my questions are:[INDENT]- Should it be better if I also migrate all my HDD to EXT4 instead of NTFS? Is this a more reliable and manageable solution? Or can I keep NTFS without any risks?
- If I keep NTFS, how could I manage permissions? Is it possible directly within Ubuntu? 
- Is it possible to manage NTFS permissions remotely, through a share mounted on a Windows machine?[/INDENT]

Any suggestion will be greatly appreciated! Thanks a lot!

---

### Post by cariboo on 2015-06-09
If you keep the partitions formatted as NTFS, you are going to run into problems if there is any file corruption, as you need Windows to fix the problem. If you are going to use Ubuntu server, it would be best to backup the files you want to keep and reformat the partitions as ext4. Ubuntu uses a wrapper to access NTFS, so you are just adding an extra layer that again may cause problems down the road.

---

