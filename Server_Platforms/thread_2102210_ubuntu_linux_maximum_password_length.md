---
title: "ubuntu linux maximum password length"
date: 2013-01-06
forum: Server Platforms
---

### Post by Vegan on 2013-01-06
anyone know what the maximum password length for Ubuntu is capable of?

I created a password tool and had to dial it down as some forums could not even use 128-bit passwords

now the program can do 96-bit which fits more forums

---

### Post by thnewguy on 2013-01-06
Since passwords are stored as hashes I don't think there is a theroetical limit. However, in practice, I suspect the passwd command would stop you at 255 or 1023 characters.

---

### Post by Vegan on 2013-01-06
MD5 is big enough for a TOP SECRET grade password

I was more concerned over using a high grade password

---

