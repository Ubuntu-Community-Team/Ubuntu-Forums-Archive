---
title: "Opening pgp files"
date: 2010-01-14
forum: Security
---

### Post by ubunboy on 2010-01-14
Hi

After upgrading to 9.10 I am having trouble opening my old files encrypted with pgp. My keyring is still on the computer as I did an update and not a clean install. The problem is that I get a message saying that there is no pgp/mime program installed to open the file. Which program should I install to fix this? 

Thanks

---

### Post by tubbygweilo on 2010-01-14
ubunboy, 
What program did you use to encrypt your files?

---

### Post by ubunboy on 2010-01-15
I am really not sure. It was the program installed on 8.10 and 9.04. I just did a right click on the file and choose encrypt. This option is however not in 9.10. That is what makes me confused... I have tried to find out what was used on the previous releases, but I have had no luck - so I tried here:D

---

### Post by FuturePilot on 2010-01-15
```
sudo apt-get install seahorse-plugins
```
Press Alt+F2 and type 
```
nautilus -q
```
Press Alt+F2 again and type
```
nautilus
```

That will get the option back in the right click menu and allow you do decrypt your files.

---

### Post by ubunboy on 2010-01-15
Sweet stuff! Thank you so much=)

I am learning all kinds of new things from you guys at this forums! 

Thanks again!

---

