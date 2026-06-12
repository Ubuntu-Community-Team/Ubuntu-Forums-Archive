---
title: "error - compile gpac"
date: 2012-03-06
forum: Ubuntu Studio
---

### Post by siavashmusic on 2012-03-06
Hello memners,

i want to compile gpac but i can't !!
what is this error. it's killing me 

```

gcc: error : unrecognized option '--warn-common'
make[1]: *** [libpac.so] Error 1
make[1]: Leaving directory '/usr/local/src/gpac/src'
make[1]: --[lib] Error 2

```


Please give me a good method for fix that .

---

### Post by RaumTrug on 2012-03-06
"--warn-common" is a compiler option, that has apparently been removed from gcc at some version.

you might want to go to the "configure" or "makefile" thingie in the source directory, and search for the option, as I see at the project's trac, you might want to remove "-Wl,--warn-common" at line 550 of "configure", right under "linux)" and try again. maybe it'll work... ;)

---

### Post by siavashmusic on 2012-03-06
where is the "configure" or "makefile" ?!
could you explain me ?

Thank

---

### Post by jejeman on 2012-03-07
In the same directory where the source code is, the very same form where you compile.

---

### Post by siavashmusic on 2012-03-08
Thanks,

but what is it  :
> make[1]: Leaving directory '/usr/local/src/gpac/src'

---

