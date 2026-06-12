---
title: "security question on keeping passwords"
date: 2007-01-11
forum: Server Platforms
---

### Post by at0mic on 2007-01-11
Hi,

Whats the best method for keeping passwords for a company? Such passwords include email, system logins, websites, etc. What is the best practise on this? Is sacrificing convenience and keeping a physical copy the only solution ?

What can Linux offer in this area?

---

### Post by apjone on 2007-01-12
> **at0mic said:**
> Hi,

Whats the best method for keeping passwords for a company? Such passwords include email, system logins, websites, etc. What is the best practise on this? Is sacrificing convenience and keeping a physical copy the only solution ?

What can Linux offer in this area?


password protected document maybe

---

### Post by Grim76 on 2007-01-13
I use truecrypt to keep a log of some essential passwords people would need to have if I get hit by a bus.  I use it because there is a linux verion of TC, and windows .

---

### Post by at0mic on 2007-01-15
there are a billion tools to "recover" passwords for items like ms word docs. completely insecure. Best i can think of at this moment is multiple layers of security like user permssions, encryption and password protection

---

### Post by maggotbrain on 2007-01-15
Personally, I have been using [PasswordSafe]("http://passwordsafe.sourceforge.net/") and [MyPasswordSafe]("http://www.semanticgap.com/myps/"). I feel more comfortable using these apps for storing passwords than a password protected document. Both are encrypted using the Blowfish crypto algorithm, for what that is worth to you. I have migrated several companies from sharing a password protected Excel spreadsheets, and they seem happy with the application. While not truly multi-user, they can be used in a small to moderately(~2-15) sized IT department.

---

### Post by at0mic on 2008-05-07
ive since tried a few and found axcrypt to be above and beyond most options for simplicity and true encryption. windows only tho.

[http://www.axantum.com/AxCrypt/](http://www.axantum.com/AxCrypt/)

---

