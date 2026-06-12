---
title: "problem building jack for ffado"
date: 2009-03-01
forum: Ubuntu Studio
---

### Post by cheapclouds on 2009-03-01
hi! followed directions from this site:
[http://subversion.ffado.org/wiki/JackForFfado](http://subversion.ffado.org/wiki/JackForFfado)

when i get to the line "$ ./autogen.sh"
i get code that looks like this:
```

jacob@cloud:/usr/jack$ ./autogen.sh
Putting files in AC_CONFIG_AUX_DIR, `config'.
rm: cannot remove `config.guess': Permission denied
ln: creating symbolic link `config.guess': File exists
cp: `/usr/share/libtool/config.guess' and `config.guess' are the same file
libtoolize: cannot copy `/usr/share/libtool/config.guess' to `config.guess'
rm: cannot remove `config.sub': Permission denied
ln: creating symbolic link `config.sub': File exists
cp: `/usr/share/libtool/config.sub' and `config.sub' are the same file
libtoolize: cannot copy `/usr/share/libtool/config.sub' to `config.sub'
rm: cannot remove `ltmain.sh': Permission denied
ln: creating symbolic link `ltmain.sh': File exists
cp: `/usr/share/libtool/ltmain.sh' and `ltmain.sh' are the same file
libtoolize: cannot copy `/usr/share/libtool/ltmain.sh' to `ltmain.sh'
./autogen.sh: 29: aclocal: not found
aclocal $ACLOCAL_FLAGS where $ACLOCAL_FLAGS= failed, exiting...
jacob@cloud:/usr/jack$ 

```

anyone know how to deal with this?

much thanks, 
jacob

---

### Post by moritzheinz on 2009-03-01
You don't have the permission, you have to type "$ sudo ./autogen.sh" to get  the rights for that operation.

---

