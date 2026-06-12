---
title: "Lubuntu 17.04 Full Disk Encryption During Install Fails?"
date: 2017-04-26
forum: Virtualisation
---

### Post by mattlach on 2017-04-26
Hey all,

Trying to install a fresh install of Lubuntu 17.04 with full disk encryption into a VirtualBox VM.

I booted up the install disk, started a terminal and ran "sudo swapoff -a", and then started the installer.

After I choose to use the entire disk, and check the encrypt disk option the following happens:

[IMG]https://c1.staticflickr.com/3/2821/33482284503_e1c3b73ffd_z.jpg[/IMG]

So, as it suggests, I check /var/log/syslog, but I can't decipher it myself.

I suspect the following last line I saw might be a hint, but I'm not suite sure what it means:

Apr 27 01:36:04 lubuntu ubiquity: cannot stat '/dev/lubuntu-vg'

The full paste of the log file [is here]("https://pastebin.com/BG5iwv3n").

Does anyone know what might be going on, and how I might fix it?

Thanks,
Matt

---

### Post by ajgreeny on 2017-04-27
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by mattlach on 2017-04-27
> **ajgreeny said:**
> *Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

If you say so.  I had no indication that my issue is virtualization related, but I also haven't tried installing it on bare metal for comparison purposes.

So, has anyone tried installing using full fill encryption in a VM?

---

### Post by mattlach on 2017-04-28
I haven't tested it yet, but I think I might have found the solution [here](https://askubuntu.com/questions/845401/installing-lubuntu-16-10-with-encrytion).

If this solution works it has nothing to do with virtualization, but rather that whomever packaged the lubuntu live disk forgot to have the LVM package installed on it, and it seems as if full disk encryption relies on LVM, and no one ever did a test of the install disk using LVM.

I will update this thread with my success or lack thereof once I get a chance ace to test it.

---

### Post by mattlach on 2017-04-28
> **ajgreeny said:**
> *Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

Based on my above post which shows this to be a installer bug affecting all systems, not just VM's, maybe this should be moved back to the installation subforum for future reference?

---

### Post by mattlach on 2017-04-30
> **mattlach said:**
> I haven't tested it yet, but I think I might have found the solution [here](https://askubuntu.com/questions/845401/installing-lubuntu-16-10-with-encrytion).

If this solution works it has nothing to do with virtualization, but rather that whomever packaged the lubuntu live disk forgot to have the LVM package installed on it, and it seems as if full disk encryption relies on LVM, and no one ever did a test of the install disk using LVM.

I will update this thread with my success or lack thereof once I get a chance ace to test it.

Alright, so installing the LVM2 package before running the installer allows the installer to complete with full disk encryption selected, but the system fails to boot on first boot after the installation, eventually resulting in a busybox window.

Any suggestions?

---

