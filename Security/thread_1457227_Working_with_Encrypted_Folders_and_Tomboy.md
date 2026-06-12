---
title: "Working with Encrypted Folders and Tomboy"
date: 2010-04-18
forum: Security
---

### Post by Wharf Rat on 2010-04-18
Hello,
Can anyone point me to some documentation that would explain how to work with Tomboy notes?

Tomboy does not really spell out how to keep notebooks in any file other than default location.  Yes, I did read the material and I did try to move the .tomboy folder contents to another non-encrypted location.  


I want to use Tomboy in a Truecrypt container.

Thanks

---

### Post by sharm on 2010-04-19
[http://live.gnome.org/Tomboy/Directories](http://live.gnome.org/Tomboy/Directories)

Let me know if you need more help than this.

---

### Post by Fastjack77 on 2010-06-26
Hi Wharf Rat,

I'm trying to find an easy way to encrypt my notes with Tomboy. If you figure out something, let me know. Meanwhile I'll try to make an automated script that would use seahorse.

---

### Post by sharm on 2010-06-26
> **Fastjack77 said:**
> Hi Wharf Rat,

I'm trying to find an easy way to encrypt my notes with Tomboy. If you figure out something, let me know. Meanwhile I'll try to make an automated script that would use seahorse.

This should be a new thread, but:

[https://bugzilla.gnome.org/show_bug.cgi?id=417316#c12](https://bugzilla.gnome.org/show_bug.cgi?id=417316#c12)

---

### Post by Fastjack77 on 2010-06-26
Thanks sharm,

using your example, I was able to manually encrypt and decrypt my tomboy notes. I made a script to make it easier, but frankly, it sucks to have to do this every time, especially when "Basket" enables encryption for a selected group of notes, using my private key...

Anyhow, here a quick how to:
Install ecryptfs:
```
sudo apt-get install ecryptfs-utils
```

Set the tomboy folder so only you can read, write to, or execute from it:
```
chmod 700 ~/.local/share/tomboy/
```

Mount the folder using ecryptfs:
```
sudo mount -t ecryptfs ~/.local/share/tomboy/ ~/.local/share/tomboy/
```

Unmount:
```
sudo umount ~/.local/share/tomboy/
```

At this point, you can use a simple script to mount/unmount the folder. (script attached - "./crypt-tomboy decrypt" to decrypt, "./crypt-tomboy" to encrypt). For Tomboy's folder by version, check [http://live.gnome.org/Tomboy/Directories](http://live.gnome.org/Tomboy/Directories)

I tried to mount my folder at startup and unmount at log off, but failed miserably. Maybe you'll have better luck than me.

---

