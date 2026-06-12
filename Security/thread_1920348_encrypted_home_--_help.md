---
title: "encrypted /home -- help"
date: 2012-02-04
forum: Security
---

### Post by kr651129 on 2012-02-04
So I have an encrypted home directory and my a friend spilled a drink on my laptop.  The hard drive is fine but I need the data off of it.  I don't have a lot of money so I've salvaged an old laptop until I can save some money.  I put BSD on it since it requires less resources than Ubuntu.  The problem is I need to decrypt the contents of my HDD.  I have the hardware needed to plugin the SATA drive into a USB but I don't know what to do after this.  Thoughts?

Thanks!

---

### Post by haqking on 2012-02-04
> **kr651129 said:**
> So I have an encrypted home directory and my a friend spilled a drink on my laptop.  The hard drive is fine but I need the data off of it.  I don't have a lot of money so I've salvaged an old laptop until I can save some money.  I put BSD on it since it requires less resources than Ubuntu.  The problem is I need to decrypt the contents of my HDD.  I have the hardware needed to plugin the SATA drive into a USB but I don't know what to do after this.  Thoughts?

Thanks!

Use a Live CD

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually)

If you dont know the passphrase then no comment ;-)

Peace

---

### Post by kr651129 on 2012-02-04
Awesome, thanks.  I have the passphrase I just needed to know how to do this.  Thanks :)

---

### Post by haqking on 2012-02-04
> **kr651129 said:**
> Awesome, thanks.  I have the passphrase I just needed to know how to do this.  Thanks :)

no worries you are welcome.

If you get it sorted then come back and mark your thread as solved using thread tools, or if you issues with it then post back.

Good luck

Cheers

---

### Post by kr651129 on 2012-02-04
Haven't had the chance to try it out yet, but while were on the subject you don't know how to decrypt the data inside of BSD do you?

---

### Post by OpSecShellshock on 2012-02-05
If there's enough space on the old hard drive you could probably just make an unencrypted copy of the encrypted data, then mount the drive after booting to BSD and copy over the clear version.

The initial copy job could be done either by booting to live CD as suggested or by just booting from the old hard drive (might be painfully slow if the system is old, but it's likely something you'll only have to do once). Could also consider one of the more resource-light Ubuntu-based distributions like Lubuntu or Xubuntu if Ubuntu is more familiar to you than BSD. You'd be amazed at what archaeological curiosities I've been able to get those to run on.

---

### Post by haqking on 2012-02-05
> **kr651129 said:**
> Haven't had the chance to try it out yet, but while were on the subject you don't know how to decrypt the data inside of BSD do you?

same way, use BSD live mode then mount the encrypted directory aslong as you know the credentials

---

### Post by kevdog on 2012-02-06
Just a quick followup.  I too also have an encrypted /home partition.  Everything is running great.  I am in possession of the password -- like a 40 digit number of something.  I vaguely remember at install time that this number could be regenerated if it was lost.  I don't remember the process.  Could you help me with this?

---

### Post by uRock on 2012-02-07
> **kevdog said:**
> Just a quick followup.  I too also have an encrypted /home partition.  Everything is running great.  I am in possession of the password -- like a 40 digit number of something.  I vaguely remember at install time that this number could be regenerated if it was lost.  I don't remember the process.  Could you help me with this?
Enter the following in a terminal. ```
ecryptfs-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase
```[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase)

---

