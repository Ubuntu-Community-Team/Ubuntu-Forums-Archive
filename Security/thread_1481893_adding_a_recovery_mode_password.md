---
title: "adding a recovery mode password"
date: 2010-05-13
forum: Security
---

### Post by Legion81 on 2010-05-13
I recently installed Ubuntu and noticed when I load 'Recovery Mode' from Grub, I am not asked for a password. Since you can change the login password from there, is there a way to add a password to this?

I would like to be prompted for a password before the recovery mode starts.

Thanks.

---

### Post by cdenley on 2010-05-13
> **Legion81 said:**
> I recently installed Ubuntu and noticed when I load 'Recovery Mode' from Grub, I am not asked for a password. Since you can change the login password from there, is there a way to add a password to this?

I would like to be prompted for a password before the recovery mode starts.

Thanks.

If you set a root password, you would be prompted for it, but this is strongly discouraged and there are other ways to get a root shell from the grub menu. You can set a grub password, but they can still boot another OS from USB or CD/DVD to mount your filesystem and access all your files or change any passwords. You can disable booting to anything but a hard drive in BIOS and set a BIOS password, but they can still reset your BIOS using a jumper on your motherboard. Protecting from physical access is pointless. The only real protection you have is encryption.

---

### Post by frostschutz on 2010-05-13
While it's true that it's not a protection against someone who has hands on access to the machine, it doesn't mean that you have to present them with a big flashing sign that says 'press here to get all my data'. A simple password may not protect you from everything but it's good enough to keep the average Jimmy out.

---

### Post by OpSecShellshock on 2010-05-13
In that case a BIOS password is a better option than setting a root password, since it doesn't cause as many other problems.

The main thing to do is identify the area of concern, though, and realistically assess the risk of that happening. Is there sensitive data stored in plain text on the computer? How often is the computer unattended by the owner but still in the presence of other people? If the biggest worry is having the password changed from recovery mode, it can probably be changed again from recovery mode when the legitimate user returns. So it all depends.

---

### Post by Bachstelze on 2010-05-14
> **OpSecShellshock said:**
> In that case a BIOS password is a better option than setting a root password, since it doesn't cause as many other problems.

Setting a root password does not cause any problems, really. The main reason it's generally not recommended here is because a lot of Ubuntu users are inexperienced and seek to use it in ways that would dramatically weaken the system's security (for example, to be logged in as root all the time). If used properly, however, a root password certainly does not cause any problems. A lot of other OSes are using one, and no one in their right mind would say they're more insecure or have more problems than Ubuntu.

---

### Post by Legion81 on 2010-05-14
> **cdenley said:**
> If you set a root password, you would be prompted for it, but this is strongly discouraged and there are other ways to get a root shell from the grub menu. You can set a grub password, but they can still boot another OS from USB or CD/DVD to mount your filesystem and access all your files or change any passwords. You can disable booting to anything but a hard drive in BIOS and set a BIOS password, but they can still reset your BIOS using a jumper on your motherboard. Protecting from physical access is pointless. The only real protection you have is encryption.

What other ways are there to get to a root shell from Grub? I've only been using Ubuntu for a week or two, so I'm not too familiar with it yet.

---

### Post by Legion81 on 2010-05-14
> **Bachstelze said:**
> Setting a root password does not cause any problems, really. The main reason it's generally not recommended here is because a lot of Ubuntu users are inexperienced and seek to use it in ways that would dramatically weaken the system's security (for example, to be logged in as root all the time). If used properly, however, a root password certainly does not cause any problems. A lot of other OSes are using one, and no one in their right mind would say they're more insecure or have more problems than Ubuntu.

I don't log in as root and I'm trying to make my computer "safer" than it already is. So how could I make a password required to load recovery mode?

---

