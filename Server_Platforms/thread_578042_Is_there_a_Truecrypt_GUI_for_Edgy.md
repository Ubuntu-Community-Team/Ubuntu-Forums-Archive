---
title: "Is there a Truecrypt GUI for Edgy?"
date: 2007-10-16
forum: Server Platforms
---

### Post by DapperMe17 on 2007-10-16
Having investigated Forcefield & EasyCrypt, I don't see any support for Edgy.

Does anyone know if this is accurate?

---

### Post by networkfu on 2007-10-16
i use this one

[http://www.scramdisklinux.org/](http://www.scramdisklinux.org/)

---

### Post by DapperMe17 on 2007-10-17
Thanks, will give it a try!

---

### Post by pablo88 on 2007-10-19
Have just upgraded to 7.10. Upgrade was perfect apart from the loss of EasyCrypt. Re-installed EasyCrypt but it couldn't find the old Crypt, no sweat as I'd backed up all the files from the Crypt anyway. Decided to re-build the crypt. Everything works fine until the very end of the process when a warning message of "Incorrect Password" comes up making the re-creation of the Crypt not possible.

I assume EasyCrypt needs a tweek or two before it is happy on 7.10

It would be nice to know as EasyCrypt is a cracking tool.

-- Pablo

---

### Post by Zetheroo on 2007-10-21
I have the same problem. Upgraded to Gutsy and now EasyCrypt won't let me open my volume. Says Incorrect Password".....????

---

### Post by StevenHarper on 2007-10-30
> **Zetheroo said:**
> I have the same problem. Upgraded to Gutsy and now EasyCrypt won't let me open my volume. Says Incorrect Password".....????

Hi, I am the author and packager of Easy Crypt

The reason you cannot create or open crypts is that you have upgraded you installation of Ubuntu from 7.04 to 7.10 without updating the TrueCrypt installation on your OS.

To fix this, simply re-download the correct DEB from Truecrypts site and then install it.

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

Easy Crypt will then begin to behave.

I am now looking into ways to detect the wrong version of Truecrypt installed on Ubuntu...

Hope this helps

Steve

---

