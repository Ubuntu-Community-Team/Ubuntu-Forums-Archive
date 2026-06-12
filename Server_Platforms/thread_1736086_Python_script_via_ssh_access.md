---
title: "Python script via ssh access"
date: 2011-04-22
forum: Server Platforms
---

### Post by abottrill on 2011-04-22
Hi guys,
Not sure if this is quite the right place to post this.
Bit of an odd one. I have some Python scripts that work fine when sat in front of my computer at my desk at work but when I access by box via ssh they fail to work and I get this error.
"error while loading shared libraries: libstdc++.so.5" 
It is a 64-bit ubuntu 10.04 install

Any one got any ideas why this happens or what I can do to beable to run python scrips via ssh?

Andy

---

### Post by bmathis on 2011-04-22
[http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000]("http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000")

---

### Post by abottrill on 2011-04-26
Thanks I found a couple of suggestions like this by googling the error but i don't understand why it will work when sat at the machine but not when accessing via ssh?

---

### Post by abottrill on 2011-05-25
Solved it turns out I had python installed twice once on the machine and once on the usernames home directory that I was sshing in to rmove the usernames copy and all works fine. :D

---

