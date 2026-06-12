---
title: "chmod +s /usr/bin/wodim"
date: 2009-10-16
forum: The Cafe
---

### Post by afeasfaerw23231233 on 2009-10-16
May I ask what's this command for?
chmod +s /usr/bin/wodim
From here:
[http://ubuntuforums.org/showthread.php?t=1062163](http://ubuntuforums.org/showthread.php?t=1062163)

After I run this chmod command k3b doesn't report the error message "cdrecord has no permission to open the device".

---

### Post by Xbehave on 2009-10-16
[chmod]("http://en.wikipedia.org/wiki/Chmod") = change permissions
+s = [set-user-ID]("http://en.wikipedia.org/wiki/Setuid") (run the program with the permission of the user that owns the file (normally you run the program with your permissions)
[/usr/bin/wodim]("http://en.wikipedia.org/wiki/Wodim") is a CLI tool to burn disk

Put them together and it means that wodim will always run with root permissions and so is allowed to access the disc for writing. 

Theoretically this could give an attacker root, if a vulnerability was ever found in wodim, however this is unlikely and they still need to login on your comptuer to run the wodim command.

---

### Post by afeasfaerw23231233 on 2009-10-16
thanks

---

