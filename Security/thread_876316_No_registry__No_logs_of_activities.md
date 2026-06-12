---
title: "No registry / No logs of activities"
date: 2008-07-31
forum: Security
---

### Post by 35k4fL0wn3 on 2008-07-31
I want my Ubuntu installation to have **zero** traces of any activity carried out in past sessions, as if every new started session were the first one.

Will working with a Guest account with no writing permissions in the OS' drive partition achieve that?

If I do that, will I (using the Guest account) be able to save documents in a different partition/drive such as a USB (encrypted) stick, without traces of this ever having been done?

---

### Post by Yannick Le Saint kyncani on 2008-07-31
> **35k4fL0wn3 said:**
> I want my Ubuntu installation to have **zero** traces of any activity carried out in past sessions, as if every new started session were the first one.

You could have an init script mount /home/guest as a tmpfs, that's what I do on a eeepc : when the sdhc for /home is no present, I create a /home/me directory as a tmpfs.

You could also set /var/log and /tmp as tmpfs filesystems.

---

### Post by 35k4fL0wn3 on 2008-07-31
> **Yannick Le Saint kyncani said:**
> You could have an init script mount /home/guest as a tmpfs, that's what I do on a eeepc : when the sdhc for /home is no present, I create a /home/me directory as a tmpfs.

You could also set /var/log and /tmp as tmpfs filesystems.

0.0 Forgive my ignorance, please care to enlighten me, I am a Windows user (I am going to install Linux for the first time). Links / references on how to do that? Restricted Guest account is not sufficient?

---

### Post by Yannick Le Saint kyncani on 2008-07-31
> **35k4fL0wn3 said:**
> 0.0 Forgive my ignorance, please care to enlighten me, I am a Windows user (I am going to install Linux for the first time). Links / references on how to do that? Restricted Guest account is not sufficient?

Hum, well, there are no restricted guest account in linux.

This may be easier :

- Open a terminal (accessories -> terminal i think)

- Edit the fstab : sudo nano /etc/fstab
Add this line :
none  /home/guest  tmpfs  mode=0777  0 0

- This is insecure (everyone has some access to the guest account, but it's easier to setup).

- Now the guest account should start anew at every boot. Beware that all its files will be kept in ram though (except when you move them on the usb key).

May it help.

---

### Post by daleus on 2008-08-04
If you're saving to USB stick, why not use a Live CD, or customize one to have the packages you want.

Just a thought.

---

