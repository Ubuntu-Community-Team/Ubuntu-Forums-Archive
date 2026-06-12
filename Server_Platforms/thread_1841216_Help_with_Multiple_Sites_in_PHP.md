---
title: "Help with Multiple Sites in PHP"
date: 2011-09-09
forum: Server Platforms
---

### Post by Atsuisofu on 2011-09-09
So I have a LAMP install with 11.04 I havent used a server for years and I am running an ubuntu GUI server using 11.04 with LAMP so I am not remembering what I did back in the day to have my default site stay at /var/www/ and also have another site /home/user/public_html. But the second site will be able to be accessed from a browser as MYSERVERIP/~user I remember ding this when I was younger but I cannotfro the life of me remember how to do this. Any help would be much appreciated.


~Regards

---

### Post by Wim Sturkenboom on 2011-09-09
I think you need to read up on virtual hosts; does that ring a bell?

---

### Post by Wayne_V on 2011-09-09
user public directories can be configured with:

$ sudo a2enmod userdir

see 'man a2enmod' and /etc/apache2/mods-available

---

