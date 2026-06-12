---
title: "security in virtual machines"
date: 2017-01-16
forum: Security
---

### Post by parminides on 2017-01-16
I was surprised (even shocked) when I learned a few years ago that if someone steals your computer and takes out the hard drive, they can easily access to your files without your password, unless they're encrypted.

I've been wondering how it works with files in virtual machines. I run vmplayer (i.e., VMware Player) with various guests, including Ubuntu 16.04. There's a folder with several ubuntu-sxxx.vmdk files, as well as ubuntu.nvram, ubuntu.vmdk, ubuntu.vmsd, ubuntu.vmx, and ubuntu.vmxf (and some other files).

(For the purpose of this thought experiment, assume that the home folder of the *host* system is *not* encrypted.)

Can the files listed above (or others) be used to access the user files of the guest machine without a password (analogous to someone accessing unencrypted files from a hard drive without a password)?

I found some software ([http://www.jihosoft.com/recover-data/virtual-machine-data-recovery.html](http://www.jihosoft.com/recover-data/virtual-machine-data-recovery.html)) that purports to be able to recover data from a virtual machine. It's a different context (recovering data that was accidentally deleted or otherwise lost). It doesn't say whether the virtual machine password is needed.

If one does encrypt the home folder of the virtual machine, will that grant the files in the guest machine the same level of security as encrypting the home folder on the host does (for the files on the host machine)?

---

### Post by SeijiSensei on 2017-01-16
If you encrypt the home folder, and all your VM images are contained in that folder, then they will be encrypted as well.

---

### Post by parminides on 2017-01-16
> **SeijiSensei said:**
> If you encrypt the home folder, and all your VM images are contained in that folder, then they will be encrypted as well.

"(For the purpose of this thought experiment, assume that the home folder of the *host* system is *not* encrypted.)"

---

### Post by Habitual on 2017-01-16
Unencrypted **and** physical access to a guest VM? Yes.

---

### Post by The Cog on 2017-01-16
If a guest VM has its home folder encrypted then it will only store encrypted data in the host's virtual disk file. You will be in the same position as you would be with a physical disk from a machine with an encrypted home folder. You would be unable to read the contents of that home folder.

A malicious host admin might be able to take a snapshot of the guest VM's memory while it's running though, and find unencrypted data or the encryption keys in there.

---

### Post by parminides on 2017-01-16
Thanks for all the replies. It sounds like the consensus is that if the home folder of the host and guest are both unencrypted, then the files on the guest can be read. But if the guest is encrypted and the host isn't, then the guest files cannot be read. That's what I wanted to know.

When I installed the host OS years ago, I didn't encrypt the home folder. I think at the time it was buggy and there were plenty of horror stories about people losing their stuff. I've done upgrades for the last few cycles, so the home folder has remained unencrypted. However, I've done things to protect the files that need protecting over the years, but the home directory in general has remained vulnerable.

---

### Post by HermanAB on 2017-01-17
You can never be rich enough, thin enough, have strong enough encryption or enough memory in your computer.
-- Ancient American Proverb, circa 2000.

---

### Post by parminides on 2017-01-17
> **HermanAB said:**
> You can never be rich enough, thin enough, have strong enough encryption or enough memory in your computer.
-- Ancient American Proverb, circa 2000.

Ha ha! Nonetheless, I'm marking this thread solved!

---

