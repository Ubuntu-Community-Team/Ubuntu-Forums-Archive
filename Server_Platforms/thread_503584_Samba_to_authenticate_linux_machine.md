---
title: "Samba to authenticate linux machine"
date: 2007-07-18
forum: Server Platforms
---

### Post by Koybe on 2007-07-18
Hello,

I have a samba server in a mixed Linux/Windows Network. It works as a PDC for windows machine. Is there a way I can authenticate linux users on their machine with the samba authentication? I guess I need to use windbind, but I don't know how to set samba on the client machine.

Please don't answer me about LDAP, I know it's a better solution but I don't have enough time to implement it at the moment as I don't know many thing about it.

Thanks in advance.

---

### Post by merkur2k on 2007-07-20
Well you can try this: [http://ubuntuforums.org/showthread.php?t=5409](http://ubuntuforums.org/showthread.php?t=5409) but its specifically for a windows nt domain controller, i have no idea how far you will get with a samba pdc.
I know you dont want to hear it, but LDAP really is the correct solution, and it sounds like youre gonna hafta learn something in either case.

---

