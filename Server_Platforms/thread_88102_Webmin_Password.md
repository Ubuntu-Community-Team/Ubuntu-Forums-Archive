---
title: "Webmin Password"
date: 2005-11-09
forum: Server Platforms
---

### Post by Rollo Tamasi on 2005-11-09
Hi guys, fairly simple problem here....
I just installed Webmin, now i need to change the password. I presume i do this thru the terminal by modifying a password file, could someone please give me some directions. Thanks

---

### Post by tonysathre on 2005-11-09
/etc/passwd is the password file. just run a cat /etc/passwd | grep webmin

---

### Post by bluefrog on 2005-11-10
sudo updatedb
whereis webmin   (certainly in /etc/webmin)
locate changepass.pl
../../changepass.pl /etc/webmin root newpassword

restart webmin just in case, don't remember if it takes the change on the fly

james

---

