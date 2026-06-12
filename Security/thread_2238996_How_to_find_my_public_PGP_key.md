---
title: "How to find my public PGP key"
date: 2014-08-11
forum: Security
---

### Post by p.callan on 2014-08-11
Have been playing around with "Passwords and keys" in 14.04 today. Managed to create a PGP key but how do I find the public part of this key so that I can share it with others?? Installed Kleopatra because it's a key manager but it doesn't seem to have the function of displaying the public key to me...  Thanks for speedy help.

---

### Post by Habitual on 2014-08-11
terminal > ```
gpg --list-keys
```

---

### Post by Dennis N on 2014-08-11
To see your entire public key so that you can share it, you need to export it:

show key on terminal:
```
gpg --armor --export UID
```
UID is the email address associated with the key.

save key to a file mykey.asc
```
gpg --armor -o mykey.asc --export UID
```
you can copy and paste the terminal output of the key into an email or send the file to share it.

---

### Post by p.callan on 2014-08-11
I haven't been using the terminal because it's too messy and complicated and I can't keep track of things. 

I uploaded my keys in "Passwords and keys" to the Ubuntu site, and then used Kleopatra to find them there, and export them to an .asc file.
I then opened this file in gedit and there was my public key.

Note to future readers: I used a 4096bit key, which takes a good while to be generated and to be found by Kleopatra so don't fret over long waiting times, and don't generate new keys because it didn't seem to work the first time. I think maybe it's collecting enropy.

---

### Post by Lars Noodén on 2014-08-11
The terminal probably  is the easy way to do it. ;) That's how I've been doing it.  

However, using "Passwords and Keys" aka Seahorse, you can select the key by clicking on it, then go to the top of the display until the menu "File" appears.  Then choose "Export" and in the export menu find the pulldown menu in the lower right where you can choose "Armored PGP keys".  Then export to a file.  You can then distribute that exported public key.  (The so called armor is ASCII encoding which allows you to also copy and paste the key as well.)

---

