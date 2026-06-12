---
title: "Secondary password or PIN for user authorization"
date: 2011-02-08
forum: Security
---

### Post by phantom22 on 2011-02-08
Is there a possibility for second password? So that you log in with a primary that is strong to protect your system from offline disk access, but installing updates and returning to the desktop from sleep mode can be done with a short PIN?  Is this a feature, perhaps with a different distro?

Being security conscious, I have my user directory encrypted with ecryptfs. I protect my keyring with a really tough password, but my user password (and so my encrypted files) aren't as safe as I'd like.  I would like to just use the same tough password, and have PAM unlock my keyring when I log in, but I rue the idea of having to punch in a gigantic password for simple admin tasks.  As I understand it, the kernel protects memory in RAM from unauthorized access, so a shorter password wouldn't be susceptible to back door attacks like brute forcing a password hash after lifting it from the disk.  Even with a four digit pin, the ability of a evil doer to take over your console when you step away would be limited.  If they shutdown your computer and read your harddrive, the pin would be stored in the encrypted home directory, protected by a much larger/harder to crack password.

Thanks for helping!
-Jordan

---

