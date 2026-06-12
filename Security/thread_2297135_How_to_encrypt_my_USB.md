---
title: "How to encrypt my USB"
date: 2015-10-01
forum: Security
---

### Post by jean_pierre2 on 2015-10-01
Hi,  What would be the most secured way of encrypting my USB?  Thank you

---

### Post by kurt18947 on 2015-10-01
I'm not certain about how secure these methods are - they're certainly better than nothing and I suspect enough to keep casual snoopers/thieves at bay.

1) Install 7zip. It will appear as an option in the Nautilus file manager. Based on what I've read, 7zip files encrypted with 256 bit AES (be sure to encrypt the file names as well) are pretty secure. A useful point here is that 7z files are cross platform.

2) The "disks" utility includes an option to encrypt removable drives if you wish to encrypt the entire drive. 

3) Cryptkeeper can be used for create encrypted folders on a flash drive.  Edit:  I'm using Ubuntu-gnome and the system tray launcher works as expected. I'm not sure about Ubuntu/Unity, there may be a 'tweak' required there.

I'm sure there are other stronger more secure options available but these seem adequate for my purposes.

---

### Post by markodd on 2015-10-12
You should've given more info.. Do you plan to use your USB In linux' systems only or Windows/Mac as well? 

If linux only, then on unity you can encrypt using "Disks". That's what I do and I find it pretty good. 

If windows/mac, then use some truecrypt alternative. I think people are using Veracrypt nowadays? Not sure, do you search and let us know!

Since there're now stories of people being forced to decrypt their data, I'd suggest creating a fake folder with fake info or whatever, just in case you do need to show something. Veracrypt supports that.

---

### Post by recepserit on 2015-10-21
What do you planing Jean? You can try TrueCrypt

---

### Post by HermanAB on 2015-10-23
First, you need to do a Threat and Risk Analysis...

Who is your adversary?
Your little kid sister: Use 7-zip encryption
Your local WUG*: Use Veracrypt or GPG
Your local LUG: Use LUKS
A nation state government: Use LUKS or GPG and then move to Russia

* Windows User Group
;)

---

