---
title: "lampify feisty the way ubuntu does it ?"
date: 2007-05-11
forum: Server Platforms
---

### Post by aktxyz on 2007-05-11
Hi,
Can someone tell me how to lampify a plain ubuntu server install, the same way that the ubuntu installer does it if you check [x] lamp near the end of the install

sudo apt-get install apache2
sudo apt-get install mysql5

does not seem to get me the same thing !

-- Thanks, Andrew

---

### Post by 65536 on 2007-05-11
[see here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server")
follow these guide to install apache mysql and php

---

### Post by Selmer79 on 2007-05-12
Ooh! That guide was AWESOME! I found so much nice stuff there! :)

---

### Post by aktxyz on 2007-05-15
Yeah, there are plenty of instructions on how to install mysql, apache, phpN, etc out there.

What I really want is the EXACT same thing you get when you choose LAMP at the end of the install..

---

### Post by jonallport on 2007-05-16
sudo tasksel

pick LAMP Server

That's what happens during a vanilla install.

---

