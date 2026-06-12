---
title: "How are the alias created in postfix?"
date: 2007-04-07
forum: Server Platforms
---

### Post by mickbuntu on 2007-04-07
Hello,

I am trying to setup a pop3 and a smtp email server using postfix and dovecot. But I am having some problems and could use some help.

1.  How does one make an alias  for most servers it is like: pop.weebhost.com and smtp.webhost.com.  Sometimes even mail.webhost.com

For me it only works if I set it to:  webhost.com for smtp and pop3. Basically  how do others add the additions before the sites name?

Thanks

---

### Post by mickbuntu on 2007-04-07
Nevermind I found out it is not on the server level even. But it has to do with the actual  register.

---

### Post by r00tintheb0x on 2007-04-08
aah, my forte... it creates them in /etc/alias/virtual.

---

### Post by MJN on 2007-04-08
Mickbuntu was talking about DNS aliases...

(besides which, I'm not sure where your /etc/alias/virtual fits in, unless that's a location you've specified yourself! ;))

Mathew

---

### Post by mickbuntu on 2007-04-13
Funny,

Ubuntu forums never showed me got replies like to Thank You still. :-)


EDIT: EDIT:  I did it on zoneedit  itself pretty easy too good service.  You just set your ip to the   say: mail.mysite.com, pop.mysite.com and so on.

---

