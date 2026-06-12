---
title: "Securing semi-sensitive information"
date: 2006-10-19
forum: Server Platforms
---

### Post by bunnynuts on 2006-10-19
I'm running 6.06 from cli, have apache2 from the repository along with php5. I'll be receiving information from those who visit my website and I want to make sure it is kept confidential. The information from multiple respondents will be captured in an xml file. I would like any advice as to how I can protect his xml file (where to store, encryption etc...). Additionally, I'd like to encrypt my apache2 log files so that if the server was compromised the ip addresses of respondents could not be obtained. 

I'm currently looking into truecrypt and EncFS, but I'm not certain whether I could encrypt an existing directory (/var/log/apache2) or if the www-data user would be able to write to the encrypted volume. I'm fairly-well in the dark as to how to best accomplish this and any and all help/suggested tools will be greatly appreciated.

Thanks for your time.

---

### Post by wieman01 on 2006-10-19
According to what I know from my good old days as a programmer the most efficient way to keep data confidential is to store it in a database (MySQL or PostgreSQL) and enable encryption of tables/fields. You can do it for passwords for instance but this is basically possible for all kinds of data/strings.

Let me know if you need more help. Both MySQL & PostgreSQL are very powerful.

---

### Post by bunnynuts on 2006-10-20
Unfortunately, due to the software I will be using the use of mySQL won't be an option. I really would like a way to secure the xml file that is generated though. If you have any thought I could the help. Additionally, instead of encrypting the log files, is it possible to tell apache to not write the log?

Thanks

---

### Post by wieman01 on 2006-10-20
Yes, I am pretty sure you can turn off the log-files. Have not used Apache in ages but you'll find the option somewhere in the configuration files.

As for the XML files... I have written a piece of software a couple of years back that would encrypt data before it was stored in a database. But I was using Java with the corresponding Security package and I imagine that's no option for you either.

Another thing would be to use some kind of encryption software like TrueCrypt that encrypts data "on the fly". What you basically do is you mount and encrypted volume (key, password, etc.) and write data to it. Once you don't need it anymore, you simply close/unmount it. That's secure.

[http://www.truecrypt.org/]("http://www.truecrypt.org/")

---

### Post by bunnynuts on 2006-10-20
Thank you for the information, I've been looking into truecrypt, have used in on a usb, but was not sure if it could be written to on the fly. One last question, if someone were to gain access to the truecrypt container while it is mounted would they automatically have access to it or would they need to know the password?

Thanks for your time

---

### Post by wieman01 on 2006-10-20
> **bunnynuts said:**
> Thank you for the information, I've been looking into truecrypt, have used in on a usb, but was not sure if it could be written to on the fly. One last question, if someone were to gain access to the truecrypt container while it is mounted would they automatically have access to it or would they need to know the password?
Basically the container stays open to everyone, however, if you set the right folder permissions (chown, chgrp, chmod) nobody else will be able to access it. Even if someone got access to your system that person would have to have the corrsponding permissions.

Of course if root gets access, there is little you can do. But I see your point, in that respect Truecrypt is not perfect. That's why I said a database such as MySQL, etc. is the best option.

---

