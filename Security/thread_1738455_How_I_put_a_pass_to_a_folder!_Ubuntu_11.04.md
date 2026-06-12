---
title: "How I put a pass to a folder?!? Ubuntu 11.04"
date: 2011-04-24
forum: Security
---

### Post by Nichijou on 2011-04-24
SO, How i put a password to a folder in Ubuntu 11.04 ???  :confused:

---

### Post by withjigs on 2011-04-24
You cannot assign password to a particular directory.
You can try securing it by assigning appropriate access permissions using:chmod

Also, you can make it hidden by starting its name with a .(dot)

Or you can use TrueCrypt, which encrypts data and you have to provide your password to view the data again.

Let me know how it goes!

---

### Post by HermanAB on 2011-04-25
Cryptkeeper.

It is in the repos.

---

### Post by Nichijou on 2011-04-27
> **withjigs said:**
> You cannot assign password to a particular directory.
You can try securing it by assigning appropriate access permissions using:chmod

Also, you can make it hidden by starting its name with a .(dot)

Or you can use TrueCrypt, which encrypts data and you have to provide your password to view the data again.

Let me know how it goes!

Hey thanks to both,the folder with the dot at the start really helps,but how i can see it?:P

---

### Post by FuturePilot on 2011-04-27
> **Nichijou said:**
> Hey thanks to both,the folder with the dot at the start really helps,but how i can see it?:P

Ctrl+H. But I wouldn't rely on this for security. This is security by obscurity which is not really secure at all.

---

### Post by CoffeeRain on 2011-04-27
```
ls -a
``` shows the hidden files in Terminal.

---

### Post by SecretCode on 2011-04-27
Hiding the files is not a good idea at all.

Truecrypt means formatting and mounting entire volumes of a fixed size.

Cryptkeeper - with the underlying encfs encrypting filesystem - is the way to go. Very easy to use. [Ubuntu Unleashed: Howto: Encrypt your private files with Encfs & Cryptkeeper Gnome applet](http://www.ubuntu-unleashed.com/2007/08/howto-encrypt-your-private-files-with.html)

---

### Post by Nichijou on 2011-04-28
huh... but the cryptkeeper do not function at all...:(

---

### Post by SecretCode on 2011-04-28
What do you mean? It works for me, so you'll have to be a bit more specific.

---

### Post by Nichijou on 2011-04-28
cuz when i try to open the program it does not open....

---

### Post by bodhi.zazen on 2011-04-28
> **Nichijou said:**
> cuz when i try to open the program it does not open....

First, the main reason people ask this question is they are new to Linux and do not understand how Linux permissions work.

Linux permissions essentially password protect files and directories.

```
chmod 770 $HOME
```

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Each user should have a unique log in account and if you desire a private home directory.

Permissions will not protect access from root or a live CD. If you need more then standard linux permissions use encryption.

Cryptkeeper has a bug in 11.04 with Unity

[https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/758449](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/758449)

---

### Post by SecretCode on 2011-04-29
> **Nichijou said:**
> cuz when i try to open the program it does not open....

I'm not using 11.04 and wasn't aware of the bug bodhi.zazen pointed out. How cryptkeeper is supposed to work is that it creates an icon in the notification area; a left-click on this icon allows you to create a new encfs folder or mount one you've created - this is when you will be prompted for the password.

For 11.04 you could try the solution mentioned here: [https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071/comments/8](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071/comments/8)

There are other ways to use encfs but I don't know of any that are as simple as cryptkeeper (when it works...)

---

