---
title: "docs for encryption how the Ubuntu installer does it"
date: 2022-03-20
forum: Security
---

### Post by Skaperen on 2022-03-20
i want to manually set up encryption to work the same way it gets setup by the Ubuntu installer, with the differences i need, which are:

  1.  full disk encyption of an additional disk, /dev/sdc, not /dev/sda

  2.  not started at boot time.  started by a script i will write that will be manually run soon after each boot.  the prompt for the passphrase is to be when this setup script is run.

i will do an ordinary install of Xubuntu 22.04 after that flavor comes out.  then i will configure the other disk for security (e.g. any system files) and run the setup script, entering the passphrase at that time. the first time i will partition it (one partition) then populate it (rsync from an external disk for a couple hours).

so, i am looking for the appropriate documentation that tells me how to do this kind of encryption.  i have looked around the net and found a few different ways.  i don't know how to identify which is correct.  and they seem to all assume i will have the installer prepare it when i want to do it manually, possibly before the install.

---

