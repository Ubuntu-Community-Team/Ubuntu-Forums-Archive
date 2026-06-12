---
title: "Copy file changes permissions"
date: 2008-08-14
forum: Server Platforms
---

### Post by jmrasor on 2008-08-14
Hi group!

  Problem on a LAMP server called boscoserver running a Windows domain. User logs onto boscoserver as Linux user, does touch me in his home directory, chmods file me to 644. He sees the new file "me" from Windows in his network share. :) He is also a user on another domain controller called testserver, and has a share open there. He copies this 644 file named "me" onto his share on the other domain: it gets permissions 744.:confused:

  All files copied from his share on one domain controller to the other domain controller pick up the u+x bit. How come?

  Copying a 666 file loses the g+w and o+w bits: permissions become 644. That I understand, since create mask = 744.

  Possibly useful things from testparm -v:

        security = user
        unix extensions = Yes
        create mask = 0744
        force create mode = 00
        security mask = 0777
        force security mode = 00
        directory mask = 0755
        force directory mode = 00
        directory security mask = 0777
        force directory security mode = 00

  Any ideas why copying 644 files makes 'em 744?

---

### Post by jmrasor on 2008-08-15
Addendum --

  rsync does this correctly between the two domains, but that's not an option for the casual Windows user.

---

