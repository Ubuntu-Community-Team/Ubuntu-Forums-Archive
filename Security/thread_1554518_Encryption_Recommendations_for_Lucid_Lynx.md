---
title: "Encryption Recommendations for Lucid Lynx"
date: 2010-08-16
forum: Security
---

### Post by dawnview on 2010-08-16
I've been looking around trying to find the setup instructions for encrypted file systems and encrypted folders on Lucid, but most of the documentation I've found it quite old.

I'm running UNR, and I've tried Truecrypt, which I'm familiar with from using it on Windows, but it doesn't seem to run. I'm looking at other options such as ecrypt-fs, dm-crypt, etc, but can't quite make out what's the best bet.

I have a few requirements:

1) I don't want the user's home directory automatically encrypted/decrypted at login.

2) I want a tool I can use to encrypt data on a USB drive as well as on the HDD.

3) I'm agnostic about filesystem encryption versus something FUSE-based. If I understand correctly, encrypting a partition would require root to mount and decrypt, so perhaps FUSE is better for my purposes.

Any suggestions or resources you can point me to?

Thanks,
Paul

---

### Post by bodhi.zazen on 2010-08-17
You can use Truecrypt , but not encrypt the entire installation.

You can use LUKS, LUKS is cross platform as well.

You can use ecryptfs . If you want a graphical front end, use cryptkeeper

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

[http://www.zimbio.com/Linux/articles/dX62jx_2vIn/Add+CryptKeeper+fly+encrypted+folders+Linux](http://www.zimbio.com/Linux/articles/dX62jx_2vIn/Add+CryptKeeper+fly+encrypted+folders+Linux)

you have many other options, what about the above tools do you not understand or what feature do they lack ?

---

### Post by wacky_sung on 2010-08-17
Personally i use Cryptkeeper and it is the best plus easiest way of creating a encrypted folder in which you can set more than 20 character of passwords.Beside that, the encrypted folder/directory will disappear from the folder you have created and reappeared after you wanna used it again.It help to keep suspected eyes away from your encrypted folders.

---

### Post by dawnview on 2010-08-18
Thanks for the suggestion [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"). I installed ecryptfs-utils on my system and created a user with an encrypted home directory (changed my mind about the encrypted home directory). I'm also using encfs to create separately encrypted folders with different passphrases, that don't auto-decrypt at login. I suppose I could use ecryptfs for this part too, but I think I prefer encfs since it uses FUSE.

My main problem before was really with documentation. There are so many tools and the documentation is often quite old (though perhaps not out of date). So I just decided to try these two options, and they worked so I'm going with them.

---

### Post by bodhi.zazen on 2010-08-18
you are most welcome, glad you got it sorted.

---

