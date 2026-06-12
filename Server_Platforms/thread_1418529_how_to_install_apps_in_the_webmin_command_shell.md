---
title: "how to install apps in the webmin command shell?"
date: 2010-02-28
forum: Server Platforms
---

### Post by waloshin on 2010-02-28
How to confirm an install of software in webmins command shell. When you type Y it wont let you.

---

### Post by junke1990 on 2010-02-28
can you give us more info?

what are you doing?

sudo apt-get install webmin?

dpkg -i webmin_vX.deb??

---

### Post by stlsaint on 2010-02-28
you just log into server and use apt-get or aptitude to install package. Then webmin will notice it.

---

### Post by waloshin on 2010-02-28
> **stlsaint said:**
> you just log into server and use apt-get or aptitude to install package. Then webmin will notice it.

But when I do that in the webmins command shell it doesnt automatically install you have to typoe y and it doesnt reconize y as yes.

---

### Post by stlsaint on 2010-02-28
> **waloshin said:**
> But when I do that in the webmins command shell it doesnt automatically install you have to typoe y and it doesnt reconize y as yes.

What do you mean webmin command shell. I have never used webmin for my server so im not fully understanding what it is your asking about.

---

### Post by ant4177 on 2011-07-07
Type "--assume yes" at the end of the command to override the y/n.

---

