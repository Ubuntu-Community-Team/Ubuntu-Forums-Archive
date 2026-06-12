---
title: "how to mount encrypted _loop file_ easily"
date: 2010-12-08
forum: Security
---

### Post by vahtenberg on 2010-12-08
Hello!

I've created luks encrypted fs in a file. And it works great via loop-mount but i want to make its usage more comfortable. So is it possible to make ecnrypted file discoverable by nautilus (that is i want to see one among other mountable drives). 
tech notes: 
[LIST]
[*]file encrypted by passhprase
[*]i _don't_ want to enter the password (and mount the file) during boot phase
[*]i'm using ubuntu 10.10
[/LIST]

Thanks

---

### Post by TheFr00n on 2010-12-08
Disclaimer: I am by no means any sort of expert on anything. Except perhaps drinking. I am good a that.

Having said that, it occurs to me that what you want to do would defeat the object of having an encrypted drive. You want it to be encrypted and secure, yet simultaneously so easy to use that all a person would have to do to access it would be to sit at your computer.

Why bother encrypting it, then? 

I'm not being sarky, it's a real question.

---

### Post by vahtenberg on 2010-12-08
Of course, I want nautilus to ask password before mounting ;)

AFAIK, nautilus automagically does it for encrypted drives. But i don't want to encrypt the whole partition. I need to encrypt just a few files. By the way, i know about encfs which works perfectly in the userspace but one doesn't hide structure of files so it's inappropriate.

---

### Post by TheFr00n on 2010-12-08
Oh ok.

Why not just hide your porn with your spreadsheets, like the rest of us? :D

Seriously, though, hope someone else can help you with this. I have no clue.

---

### Post by vahtenberg on 2010-12-10
bump

---

### Post by vahtenberg on 2010-12-10
Found hack: just add next line to the /etc/rc.local
```

losetup /dev/loop0 /home/user/.crypt

```,
and you'll see removable disk in the nautilus.

But have no idea how to force nautilus to create file under /dev/mapper/ with a proper name.

---

