---
title: "Cryptsetup has very limited cipher options in 9.04"
date: 2009-05-29
forum: Security
---

### Post by jbrown96 on 2009-05-29
I've been doing a lot of work recently on my encrypted backup system. I've decided to change keys and overwrite everything, then start again. I'm having a problem creating the encrypted drives though. I've been using Mandriva and tried this same thing, and it didn't support the ciphers either.

Here's what I want to do:
```
sudo cryptsetup luksFormat -h sha256 -c xts-serpent-essiv /dev/sdb
``` However, I can't use anything that has xts or essiv in it. I've tried using aes as well, and it won't work. I've tried changing the order (serpent-xts-essiv, etc.), and that didn't help either. I know that I've run this exact same command on previous versions, but it won't work now. The best part is that I can open encrypted devices that use xts-serpent-essiv, but can't create them.

Does anyone know what to do? I couldn't find any packages to enable this, and I haven't found any modules to load (besides dm-crypt, aes, xts). 
In /proc/crypto, I even have an entry for aes(xts). 

Thanks.

---

### Post by rookcifer on 2009-05-30
> **jbrown96 said:**
> I've been doing a lot of work recently on my encrypted backup system. I've decided to change keys and overwrite everything, then start again. I'm having a problem creating the encrypted drives though. I've been using Mandriva and tried this same thing, and it didn't support the ciphers either.

Here's what I want to do:
```
sudo cryptsetup luksFormat -h sha256 -c xts-serpent-essiv /dev/sdb
``` However, I can't use anything that has xts or essiv in it. I've tried using aes as well, and it won't work. I've tried changing the order (serpent-xts-essiv, etc.), and that didn't help either. I know that I've run this exact same command on previous versions, but it won't work now. The best part is that I can open encrypted devices that use xts-serpent-essiv, but can't create them.

Does anyone know what to do? I couldn't find any packages to enable this, and I haven't found any modules to load (besides dm-crypt, aes, xts). 
In /proc/crypto, I even have an entry for aes(xts). 

Thanks.

I think you have the commands slightly reversed.

Try:
```

cryptsetup -c serpent-xts-plain -s 256 luksFormat /dev/sdb
```

I am not sure if a hash can be specified for xts-plain.  No examples I see anywhere online define a hash.  For instance, on aes-cbc-essiv, you often see "SHA256" appended to it.  If aes-xts-plain defaults to SHA-1, then you are probably better off using:

```
aes-cbc-essiv:sha256
```

That way you will have a better hash.  LUKS will default to SHA-1, which has already been partially broken.  Your encryption is only as strong as the weakest link.

Basically, what I am saying is that even though xts might be better than cbc, if it uses a weak hash, it won't matter. cbc-essiv will be better with an SHA256 hash than xts with a weak SHA1.

---

### Post by jbrown96 on 2009-05-30
Thanks rookcifer. That worked perfectly. ```
sudo cryptsetup -c serpent-xts-essiv:sha256 /dev/sdb
``` and I confirmed it with ```
sudo cryptsetup luksDump /dev/sdb
``` I really have no idea why cryptsetup uses such stupid syntax. It makes no sense to combine all the cipher options at once because it's all (command successful) or nothing (your kernel doesn't support this). There's no useful feedback; it wouldn't even tell me that I was specifying the cipher at the wrong point.

---

### Post by HermanAB on 2009-05-30
Howdy,

The easiest way to do this is to install luks-tools and run the wizard gnome-luks-format, or download my wizards here: [http://aeronetworks.ca/luks-usb-howto.html]("http://aeronetworks.ca/luks-usb-howto.html") and modify them a bit to do what you want.

---

