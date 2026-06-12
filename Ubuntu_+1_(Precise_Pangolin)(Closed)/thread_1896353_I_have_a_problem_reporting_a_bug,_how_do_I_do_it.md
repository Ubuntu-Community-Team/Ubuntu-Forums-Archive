---
title: "I have a problem reporting a bug, how do I do it?"
date: 2011-12-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mdurham on 2011-12-16
I type in a terminal > ubuntu-bug linux
after some scanning for files or whatever, this is followed by > The problem cannot be reported:

This is not an official Ubuntu package. Please remove any third party package and try again.
Whet do you think this means, and how do I report a bug?
Cheers, Mike

---

### Post by castrojo on 2011-12-16
Are you using the normal kernel package or did you install your own?

---

### Post by mdurham on 2011-12-16
> **castrojo said:**
> Are you using the normal kernel package or did you install your own?

normal 3.1.0-2 I can't use any kernal after that, that's what I want to report.

---

### Post by mc4man on 2011-12-16
ubuntu-bug linux should work, have you tried repeating the command a couple of times?

---

### Post by mdurham on 2011-12-16
> **mc4man said:**
> ubuntu-bug linux should work, have you tried repeating the command a couple of times?

Repeating the command doesn't help. Each time it goes into "collecting information" and asks for a password, then, reports that "it's not an official Ubuntu package" etc.

---

### Post by ronacc on 2011-12-16
perhaps he needs to use linux-generic  since that is how the package is named . if that don't work try linux-image . see screenshot .

---

### Post by jbicha on 2011-12-16
apport (ubuntu-bug) first checks to see if you're using the latest version available in the repositories and fails if you're not. I can see how this can make kernel bugs difficult to file.

I've not tried this but I wonder what would happen if you just reported the bug using [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug) and then run this command:

apport-collect bugnumber (substitute the bug number you just filed)

Alternatively, ask in #ubuntu-kernel for their advice on how to report this.

---

### Post by mdurham on 2011-12-16
Thanks jbicha, I'll try your suggestions. It does make it difficult/silly if you have to use the broken kernel to report it as broken.
Cheers, Mike

---

### Post by lisati on 2011-12-16
> **mdurham said:**
> It does make it difficult/silly if you have to use the broken kernel to report it as broken.
Cheers, Mike
This reminds me of the BIOS error message "Keyboard not detected. Press F1 to continue."

Good luck, and feel free to keep us posted on how you get on.

---

### Post by cariboo on 2011-12-16
@mdurham, I reported the kernel panic problem, if you want you can add your me too, to bug #[lpbug]905606[/lpbug]. I chrooted / on the install that was kernel panicing, and used the apport-cli tool to gather the needed information, that is attached to the bug report.

---

