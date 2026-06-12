---
title: "Encrypting Files"
date: 2010-09-08
forum: Security
---

### Post by jonny75904 on 2010-09-08
I recently upgraded to Ubuntu 10.04.  I love the passwords and keys application, but was somewhat surprised at the lack of a context menu in gnome to encrypt a file.

In general, I cannot find how to encrypt files using the keys I generate. Maybe I'm missing something?  Probably,  I just thought since Ubuntu comes with OOB key generation it would have OOB encryption capabilities.

I've read about seahorse and other ways to ADD encryption, I'm just wondering if ubuntu does it natively.  It'd be a good idea to add to brainstorms, right click and encrypt.

---

### Post by FuturePilot on 2010-09-08
```
sudo apt-get install seahorse-plugins
```

Alt+F2

```
nautilus -q
nautilus
```

Right click file > Encrypt

---

### Post by anomie on 2010-09-08
[QUOTE=jonny75904]I'm just wondering if ubuntu does it natively.  [/QUOTE]

I'd argue that "native" is subjective (in the context of a GNU/Linux distro), but that's another topic. ;)

A default Ubuntu install should include both openssl and (I think) gnupg. The former provides a CLI for encryption via enc(1), where you can utilize several popular symmetric ciphers. The latter's CLI is gpg(1); it supports symmetric ciphers, but is much more commonly used for asymmetric encryption / signatures. 

There are probably GUIs to slap on both of those, but I'm not familiar with them.

---

### Post by rileinc on 2010-09-09
> **jonny75904 said:**
> I recently upgraded to Ubuntu 10.04.  I love the passwords and keys application, but was somewhat surprised at the lack of a context menu in gnome to encrypt a file.

In general, I cannot find how to encrypt files using the keys I generate. Maybe I'm missing something?  Probably,  I just thought since Ubuntu comes with OOB key generation it would have OOB encryption capabilities.

I've read about seahorse and other ways to ADD encryption, I'm just wondering if ubuntu does it natively.  It'd be a good idea to add to brainstorms, right click and encrypt.They removed it because some people thought these options in the right-click menu may be too 'advanced' for novices. See the 100 paper cuts entry on it: [https://bugs.launchpad.net/hundredpapercuts/+bug/393645](https://bugs.launchpad.net/hundredpapercuts/+bug/393645)

If you want the 'encrypt' and 'sign' options back, simply install seahorse-plugin from synaptic (or just follow post #2), and they will reappear in your right click menu.

I occasionally use these options and find them to be *very* useful. I thought it was stupid to remove them altogether (instead of shuffling into an 'advanced' submenu); but whatever, you have an easy fix.

---

### Post by rookcifer on 2010-09-09
FuturePilot has your answer.  Install seahorse-plugins.  Then you can merely right click any file and pick the recipient you want to encrypt it to (it will list all keys on your keyring to choose from).

If you want to encrypt files symmetrically (that is with only a password), you can do it from the command line like:

```
gpg -c file
```

---

### Post by Dart00 on 2010-10-09
Wow. I think im a advance Ubuntu user...If you know what "Encrypt" and "Sign" do and exactly what they are good for and how to use them via good and command like you automatically get the Advanced Ubuntu User award lol. These can be a handful to master but once you do they are all you need for data privacy and security basically.

Its impossable for new users to work with gpg and openssl from the command line. Once you learn how to use them, its a pain in the butt to use them from the command line, even to encrypt a few files occasionally, you have to open a terminal, cd to the folder, run the commands, hope all goes well lol.

Sea-horse makes things simpler...it puts "most" of the command line options in a "easy to use" GUI. The problem is your hit with "most" of the commands, which can be oodles! And "easy to use" can be very intimidating, you "still" need to do your homework.

I found a few Nautilus scripts that seemed like a good simple replacement for sea-horse, but in the end, one would not even work right and the other lacked way to much functionality....The answer....

I designed my own nautilus script!

I started as a lil project and then it kinda grow, I was able to add more options, but still keep it very easy to use. Its also very speedy.

You download a installer and just follow the few prompts and then you have the Nautilus script from your right click scripts context menu. :) You can encrypt files with a 1-2 clicks depending on how you configure it.

It hope it helps the Ubuntu community.

[http://gnome-look.org/content/show.php/Turbo-Secure?content=133380](http://gnome-look.org/content/show.php/Turbo-Secure?content=133380)

I will be making a Nautilus script that will let you "sign" files, but its a lil tricky, i need to think of a easier way to script it....Ill get it eventually.

---

### Post by rookcifer on 2010-10-09
> **Dart00 said:**
> Wow. I think im a advance Ubuntu user...If you know what "Encrypt" and "Sign" do and exactly what they are good for and how to use them via good and command like you automatically get the Advanced Ubuntu User award lol. These can be a handful to master but once you do they are all you need for data privacy and security basically.

Its impossable for new users to work with gpg and openssl from the command line. Once you learn how to use them, its a pain in the butt to use them from the command line, even to encrypt a few files occasionally, you have to open a terminal, cd to the folder, run the commands, hope all goes well lol.

Sea-horse makes things simpler...it puts "most" of the command line options in a "easy to use" GUI. The problem is your hit with "most" of the commands, which can be oodles! And "easy to use" can be very intimidating, you "still" need to do your homework.

I found a few Nautilus scripts that seemed like a good simple replacement for sea-horse, but in the end, one would not even work right and the other lacked way to much functionality....The answer....

I designed my own nautilus script!

I started as a lil project and then it kinda grow, I was able to add more options, but still keep it very easy to use. Its also very speedy.

You download a installer and just follow the few prompts and then you have the Nautilus script from your right click scripts context menu. :) You can encrypt files with a 1-2 clicks depending on how you configure it.

It hope it helps the Ubuntu community.

[http://gnome-look.org/content/show.php/Turbo-Secure?content=133380](http://gnome-look.org/content/show.php/Turbo-Secure?content=133380)

I will be making a Nautilus script that will let you "sign" files, but its a lil tricky, i need to think of a easier way to script it....Ill get it eventually.

Interesting project.  However, I must say that CAST5 and Blowfish algorithms are not really "low" in strength.  No one has ever come close to breaking them in a practical sense, and they have been analyzed for many years.  In reality, all of the algorithms included in the kernel are well tested and still secure.  (Though I guess relative to AES or Serpent-256 they might be weaker, but still using them will not compromise security).

---

