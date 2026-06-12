---
title: "Is Ubuntu safe if you have physical access to the machine?"
date: 2014-09-20
forum: Security
---

### Post by toteslegit on 2014-09-20
I found this article which tells you how to reset the root password in case you forget it.

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

Apparently, resetting the root password can be done by anyone as long as they have physical access to the machine.
Is it safe to assume that anyone can perform this on my computer and easily gain access to it?

---

### Post by CharlesA on 2014-09-20
Yes, which is why physical access = root access. If you can't control physical access, there isn't much you can do.

FWIW, Ubuntu doesn't use the root account, but unless your files are encrypted, anyone booting a LiveCD can look at your stuff. No need to reset the root password or anything.

---

### Post by QIII on 2014-09-20
On the other side of the token, physical access = root access with Windows, too.

Some mobo OEMs make mobo-level password protection available and there is usually disk-level password protection. That can give you layered protection.   All can be circumvented by a determined attacker given enough time.  The first can be as simple as clearing the CMOS.  There are forensic applications to find the disk password, which is stored in the disk's firmware and can be extracted in a few minutes.  You can encrypt some or all of your files and even use full disk encryption, but if you forget your password you will have hoisted yourself by your own petard.

---

### Post by CharlesA on 2014-09-20
> **QIII said:**
> On the other side of the token, physical access = root access with Windows, too.

Indeed. Once someone has physical access, it's pretty much game over unless you have your hard drive encrypted.

---

### Post by QIII on 2014-09-20
Disk encryption, in some form, FTW!

---

### Post by toteslegit on 2014-09-20
Thanks for the replies, guys.

---

### Post by HermanAB on 2014-09-21
Encrypt, encrypt, encrypt...

So called full disk encryption is the only protection for data at rest, unless you lock the machine up in a steel box.

---

### Post by Habitual on 2014-09-21
The First Rule of Security: There is No Security without physical security.

---

### Post by jon43 on 2014-09-23
There are ways to make it safe. 

Most motherboards allow you to set a BIOS password. If you do this and disable booting from anything except the intended hard drive, you protect yourself from someone booting up with a live CD or USB stick and viewing things from outside the installed OS. 

They could always clear the CMOS- which is where a case with a good lock on the side panel comes in. Antec makes some sweet Sonata cases with this feature. If you can't open the case to clear the CMOS and all of the secondary boot options are disabled and password protected, you're fairly safe- unless someone is willing to actually destroy the rig physically to gain access. In which case, I doubt much is going to help you.

---

### Post by whitesmith on 2014-09-24
[snip]

My answer to the subject line of your post is no,[snip]

Just today it was revealed that bash is compromised in several variants of Linux (including Ubuntu) that depend on Free Software Foundation's code. [snip] [http://www.huffingtonpost.com/2014/09/24/new-bash-software-bug-m_n_5878398.html](http://www.huffingtonpost.com/2014/09/24/new-bash-software-bug-m_n_5878398.html)). What, me worry?

---

