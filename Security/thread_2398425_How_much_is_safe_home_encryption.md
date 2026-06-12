---
title: "How much is safe /home encryption"
date: 2018-08-11
forum: Security
---

### Post by kaky951357 on 2018-08-11
Hello everyone, I have my home folder encrypted, i choosed this option during the installation of ubuntu 16.04 LTS and i don't know how it works exactly :  1. What software does the ubuntu installer use to encrypt the home folder? 2. After the authentication, the entire folder is decrypted or just the files that i use, if it's just the files are they remain decrypted for the whole session or just during the period when they are used? 3. When i log in to my laptop i type the encryption password that i choosed during the installation of ubuntu,  it logs me into my user account it's also the password to access the root privilege, so basically a single password can decrypt my data, allow access to my user account and to the root privilege, is that normal ? is that safe ? Thank you for trying to help, have a nice day.

---

### Post by TheFu on 2018-08-12
Home directory encryption is a less secure method.  You can look at the raw encrypted files to see the funny names and the file sizes.  This data can be analyzed to provide guesses about the file contents.  Whole drive encryption is considered much more secure because it prevents 99% of unwanted access unless having just HOME directory encryption, which does nothing to prevent someone with a flash drive from being able to boot and modify the system files in just under 1min.

If the user is logged in, then the files are made available to any process that requests them.

Gaining administrative access (i.e. root) using a userid in the sudoers group is common. If you want more security, create a normal userid for daily use and use that.  You can always open a shell and change userids to the one with admin elevation rights via sudo.  Linux is multi-user from the ground up.  You should use it that way if you want more security.  The userid normally used should only have permissions to accomplish only those things necessary for the task at hand and no others.

BTW, if you use any encryption, you need to have perfect know-you-can-recover backups.  If there is any issue with the data, logical or physical, the only hope to get it back if encrypted is to restore from backups.

---

### Post by John_Patrick_Mason on 2018-08-24
Sorry to barge in, but when you mean "funny names" do you mean to say that the filenames of encrypted files are still visible to the world? I thought encrypted data looked like just random bits of 1s and 0s; undecipherable, in other words. Also, if one were to encrypt just the home folder, could someone with sufficient knowledge decrypt the home directory with the help of some kind of security vulnerability in the underlying OS?

---

