---
title: "Fingerprint GUI and encrypted home"
date: 2012-02-01
forum: System76 Support
---

### Post by ahowe42 on 2012-02-01
I'm using Fingerprint GUI 1.03 on Ubuntu 11.10.  The fingerprint reader works fine for elevating privileges with sudo, or when I need to remove/install packages.  When I try to log on using it, however, I get an error that my home folder is encrypted (it is), and that the fingerprint software doesn't have the password.

Is storing the decryption key on a usb drive/dongle really the only way to get this to work?

Andrew

---

### Post by isantop on 2012-02-01
I believe the answer to your question is that for security reasons, that would be the only way to get it to work. 

I should point out though, that the Fingerprint Readers are currently unsupported, and that we don't expect full support until 12.04.

---

### Post by ahowe42 on 2012-02-07
Thanks Ian.  I have a hardware-encrypted USB drive (corsair padlock), which I'll try this with.

Andrew

---

### Post by ahowe42 on 2012-02-07
But the USB device is not mounted if I'm not logged in, so how can this possibly work...?

---

### Post by isantop on 2012-02-07
I'm not sure how this is set up or how it works on a technical level, since we don't currently support the fingerprint readers in 11.10 (the lack of system integration causes problems). On top of that, encrypted Home Folders are a somewhat experimental setup, and we don't officially support using them as well.

---

### Post by Dave_L on 2012-02-08
> **isantop said:**
> ...encrypted Home Folders are a somewhat experimental setup, and we don't officially support using them as well.

Do you support full-disk encryption?

---

### Post by isantop on 2012-02-08
We don't officially. You're free to try to install it, and doing so won't void your warranty. However, in the event of software problems, one of the first things we recommend on these system is trying running the system without the encryption, as the software that controls it is still pretty experimental, and is known to cause issues with other aspects of the system. This is particularly true of setups using full-disk encryption.

---

### Post by 1976MrEMan on 2012-08-10
Hi, I'm using 12.04 and I get the same error message when I try to use my finger scan to log in. Any easy way to remedy this?

---

### Post by isantop on 2012-08-10
> **1976MrEMan said:**
> Hi, I'm using 12.04 and I get the same error message when I try to use my finger scan to log in. Any easy way to remedy this?

Unfortunately, no. Fingerprint login is incompatible with Encrypted Home Folders.

---

### Post by mapman88 on 2012-08-15
I upgraded my gazp6 to 12.04 a couple months ago. Now when I log in I have a message to use my fingerprint reader (picture of a finger swiping the reader on the bottom of my screen. I took a look around today and cant figure out how to install the gui for it.

Can you tell me where to go to download, or give a sudo instruction?

thanks,

---

### Post by isantop on 2012-08-16
> **mapman88 said:**
> I upgraded my gazp6 to 12.04 a couple months ago. Now when I log in I have a message to use my fingerprint reader (picture of a finger swiping the reader on the bottom of my screen. I took a look around today and cant figure out how to install the gui for it.

Can you tell me where to go to download, or give a sudo instruction?

thanks,

If you have that, then it's already installed. just look in your dash for the "Fingerprint GUI" application.

---

