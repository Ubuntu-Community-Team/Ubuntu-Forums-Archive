---
title: "Installation doesn't ask to encrypt home folder on 18.04"
date: 2018-07-31
forum: Security
---

### Post by Paddy Landau on 2018-07-31
I am used to Ubuntu (and Lubuntu) installations asking if I want to encrypt my home folder. However, I've just installed Lubuntu 18.04 on a computer, and it didn't do this. Thus, the home folder remains unencrypted.

I tried Ubuntu 18.04.1 on VirtualBox to find the same problem.

Furthermore, prior to 18.04.1, creating a new user using Users and Groups ([FONT=lucida console]users-admin[/FONT]) gave an option, "Encrypt home folder to protect sensitive data." On 18.04, this option is missing.

This seems to be a bug. :(

[LIST]
[*]Do you have any information about this matter?
[/LIST]

[LIST]
[*]Is there a guide to how to encrypt my home folder, or to create a new user with an encrypted home folder?
**EDIT:** I just found [a guide to encryption]("https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html"), which says that ecryptfs is buggy and that full-disk encryption is preferred. But full-disk encryption wipes any existing OS such as Windows. (Another sad face)
[/LIST]
Thank you

---

### Post by TheFu on 2018-07-31
Encryption of HOME has been removed due to a number of issues. Security and performance were at the top.
The 18.04 Release Notes clearly say this.  

Not a bug. Working as designed.

---

### Post by Paddy Landau on 2018-08-01
Thanks. I see that now, we're supposed to use either of:

[LIST]
[*]**Full-disk encryption**
This is a no-go for most users, because it wipes any existing OS such as Windows. There is an [alternative full-system encryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption"), which plays nicely with other OS's (and even encrypts [FONT=lucida console]/boot[/FONT], which the existing method doesn't), but it has two significant flaw (specifically, it's not easy to install for a newcomer to Linux, and manual intervention is required each time the kernel is updated). I've [raised a request]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457"); please visit if you agree with the idea.
[*]**fscrypt**
This is also a no-go, because of an [existing bug]("https://bugs.launchpad.net/ubuntu/+source/fscrypt/+bug/1768340"), which (from what I can see) seems to be taking a low priority.
[/LIST]
So, it's problem, because right now Ubuntu doesn't have an encryption that's considered reliable.

For now, I've manually [implemented ecryptfs]("https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html"). But, I look forward to a decent resolution to this matter.

---

### Post by TheFu on 2018-08-01
For most users, I'd suggest they install Linux with FDE, then  put Windows into a virtual machine.  If you care about security, don't run Windows physically on any hardware.  I have Win7 media center running in a VM.

If you need high-end GPU support, then setup PCI passthru for a 2nd video card into the Windows VM. On a difficulty scale, this is probably about the same as manually setting up disk encryption on a dual-boot system. Of course, the hardware has to be supported for this and most laptops need not bother.

---

### Post by DuckHook on 2018-08-01
Hi Paddy. Another option that might work for you is to encrypt only a private directory, not all of /home, then, move all sensitive stuff (keys, docs, data, mail and cache contents, etc) into it and symlink back to the expected places in /home: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Pros: avoids almost all of the downsides that caused devs to deprecate /home encryption, allows easy maintenance updates, not too hard to implement.
Cons: slightly slower login, a lot of fine relinking required with every pristine version upgrade, marginally less secure than full /home encryption.

---

### Post by Paddy Landau on 2018-08-02
> **TheFu said:**
> …  put Windows into a virtual machine.
If you have sufficiently capable hardware, absolutely I agree with you. But the vast majority of users wouldn't have the faintest idea of how to go about this. My hardware, unfortunately, isn't strong enough to support Windows in a VM, and anyway I need to go into Windows only once a month.

> **DuckHook said:**
> … encrypt only a private directory, not all of /home, then … symlink back to the expected places in /home
Nice idea. I've already used ecryptfs to encrypt the home folder, and once we have a better method, I'll replace ecryptfs with the better method. It'll do for now!

What I want to do is harden the [full-system encryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption"), so that it "just works". Unfortunately, I have neither the time nor the skill to rewrite the installation process, but I can at least modify the installation so that maintenance becomes hassle-free.

---

### Post by TheFu on 2018-08-02
If you are worried about security, anything less than FDE is a waste.  Further, FDE needs to be protected against the "evil maid attack" by you keeping the boot storage on your person 100% of  the time, even when showering. Booting shouldn't be possible without that external storage by anyone.

Running Windows in a VM doesn't take much. I used to do it on 2008 hardware.  Any Core2 Duo or better easily handles that ... so anything with about 2500 passmarks. More is better, but I'd done it on systems like that.  There are thousands of youtube videos showing how to accomplish it. I used to teach Windows people how to do it, so it can't be THAT hard.

---

### Post by Paddy Landau on 2018-08-08
> **TheFu said:**
> … anything less than FDE is a waste.
In the UK, it's gradually becoming required.
> **TheFu said:**
> Running Windows in a VM doesn't take much.
Sure, but it's still too much for my aging computer. I can run Lubuntu fairly well in VirtualBox, as long as I don't run anything else in the host, but Ubuntu crashes VirtualBox if I do more than barely anything (!), and Windows is too sticky toffee to even bother.

---

