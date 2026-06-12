---
title: "Hidden Encrypted Ubuntu install?"
date: 2010-03-28
forum: Security
---

### Post by Mr.BlankFace on 2010-03-28
Hello
I've been using my own custom ubuntu livecd because I know that it saves absolutely no data (uses RAM) and I've been using an encrypted usb drive to save all my data.

I would rather install ubuntu to an external hard drive and encrypt it (with some strong encryption using truecrypt or something similar). This way, the existence of the OS is hidden. Is anything like this possible?

I am still learning about encryption so I'm still pretty noobish when it comes to these things so please bear with me.

My main concerns:
-The existence of an Ubuntu install needs to be hidden
-The installation needs to be encrypted

Thank you in advance for your help

---

### Post by mkvnmtr on 2010-03-28
The install disk gives you the option of using first class encryption but I have no idea where you could hide an operating system. Maybe under the bed.

---

### Post by rookcifer on 2010-03-28
> **mkvnmtr said:**
> The install disk gives you the option of using first class encryption but I have no idea where you could hide an operating system. Maybe under the bed.

You can hide an OS inside another OS but, afaik, only Truecrypt can do this.  How to do it, I am not sure, as I do not use truecrypt.  From the truecrypt site:

> **TrueCrypt allows you to create a hidden operating system whose existence will be impossible to prove **(provided that certain guidelines are followed — see below). Thus, you will not have to decrypt or reveal the password for the hidden operating system.

---

### Post by Mr.BlankFace on 2010-03-28
> **rookcifer said:**
> You can hide an OS inside another OS but, afaik, only Truecrypt can do this.  How to do it, I am not sure, as I do not use truecrypt.  From the truecrypt site:

Thanks for your response. I've read this before and it looks like you can only encrypt Windows systems

---

### Post by Soul-Sing on 2010-03-29
You can hide files (and encrypt them) for instance in pictures, but not hide entire systems afaik.

---

### Post by treymul on 2010-04-02
Couldn't you perform the encrypted install to your harddrive and then install the boot partition to a usb drive?  Then there would not be any info about the ubuntu partition that wasn't encrypted on the harddrive.  You could only access the os by using the usb drive and booting from it.

---

### Post by HermanAB on 2010-04-02
Howdy,

Use the alternate installation CD to install the system with LUKS.

---

