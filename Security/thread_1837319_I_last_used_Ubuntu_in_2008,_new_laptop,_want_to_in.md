---
title: "I last used Ubuntu in 2008, new laptop, want to install 11.10 fully encrypted"
date: 2011-09-01
forum: Security
---

### Post by marywadcum on 2011-09-01
So I've never encrypted a drive before. I've used TrueCrypt to create container files, etc. I've decided to forego Windows and install Ubuntu instead on my brand new laptop. I travel internationally a lot. I decided since I'll be starting from scratch with Ubuntu and since I'm planning on going through U.S / Chinese immigration a lot over the next year.. How can I install Ubuntu 11.10 from scratch on a brand new laptop and encrypt the entire drive? What is the best, easiest foolproof way that even a noob (like me) can do it?

Thank you very much. I want to do this installation this weekend when I have a few hours to backup all of my files. Thank you again!

---

### Post by bodhi.zazen on 2011-09-01
Short story is you can not.

There is no full disk encryption for Linux, /boot must be available unencrypted, although some move it to a flash drive.

Truecrypt will not work with Linux, and LUKS will not work with Windows.

So pick your poison, window or linux, or one will not be encrypted.

You likely do NOT need to encrypt the entire OS, just use an encrypted data partition. You may use either Truecrypt or LUKS for that.

---

### Post by marywadcum on 2011-09-01
> **bodhi.zazen said:**
> Short story is you can not.

There is no full disk encryption for Linux, /boot must be available unencrypted, although some move it to a flash drive.

Truecrypt will not work with Linux, and LUKS will not work with Windows.

So pick your poison, window or linux, or one will not be encrypted.

You likely do NOT need to encrypt the entire OS, just use an encrypted data partition. You may use either Truecrypt or LUKS for that.

Thanks for the reply. This makes a lot of sense. So I'd just like to encrypt all personal data and not necessarily /boot and other generic Linux files. What's the best way to encrypt just my personal data and files?

I'm really a noob. I used Ubuntu briefly back in 2008. That's my only time ever using any Linux system.

---

### Post by cariboo on 2011-09-01
If you are a new user, I'd suggest you install 11.04, as 11.10 just went beta, and there are still quite a few bugs that need to be fixed before the release in October.

---

### Post by bodhi.zazen on 2011-09-01
> **marywadcum said:**
> Thanks for the reply. This makes a lot of sense. So I'd just like to encrypt all personal data and not necessarily /boot and other generic Linux files. What's the best way to encrypt just my personal data and files?

I'm really a noob. I used Ubuntu briefly back in 2008. That's my only time ever using any Linux system.

My personal preference is to use LUKS, but you might like cryptkeeper, it has a graphical interface and is in the repos.

If you need access from windows and linux, LUKS or Truecrypt, either.

---

