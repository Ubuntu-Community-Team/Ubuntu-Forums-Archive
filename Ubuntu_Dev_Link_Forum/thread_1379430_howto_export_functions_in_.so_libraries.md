---
title: "howto export functions in *.so libraries"
date: 2010-01-12
forum: Ubuntu Dev Link Forum
---

### Post by Vahagn_IV on 2010-01-12
Hi all,

I am trying to convert one windows program to Linux. 
 The question is:
 what is linux equivalent for

extern "C"    int (__declspec(dllexport))someFunction(char* someparam)

Thanks in advance.

---

### Post by Emanuele_Z on 2010-01-16
In Linux (as usual) it's easy and you have 3+ ways to do it.
[list]
[*]If you just declare them
```

extern "C"

```
is ok.
[*]Or you can create an export/mapfile fo feed the linker with telling it exactly which symbols to export/hide. [http://publib.boulder.ibm.com/infocenter/tpfhelp/current/topic/com.ibm.ztpf-ztpfdf.doc_put.cur/gtpl2/cre8expfl.html#cre8expfl](http://publib.boulder.ibm.com/infocenter/tpfhelp/current/topic/com.ibm.ztpf-ztpfdf.doc_put.cur/gtpl2/cre8expfl.html#cre8expfl) (you can create the file by hand). Another link is [http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html) , section -Wl or -Map. Another link: [http://people.redhat.com/drepper/dsohowto.pdf](http://people.redhat.com/drepper/dsohowto.pdf) (section 2.2.5).
[*]Or you can used the gcc flag
```

-fvisibility

```
[http://gcc.gnu.org/wiki/Visibility](http://gcc.gnu.org/wiki/Visibility)
[/list]
Btw, the
```

(__declspec(dllexport))

```
Is just a mere macro to usually force the compiler to produce *stdcall* calling convention. In Linux AFAIK we only use *cdecl* ( [http://en.wikipedia.org/wiki/X86_calling_conventions](http://en.wikipedia.org/wiki/X86_calling_conventions) ).
Have fun!

Cheers,

---

### Post by Vahagn_IV on 2010-01-16
Emanuele_Z, thanks.

---

### Post by Emanuele_Z on 2010-01-21
Hi,

to be precise, the calling convention applies to *i386* arch.
For *x86-64* Windows and Linux follow 2 slightly different conventions: Linux follows AMD ABI calling convention, instead, as usual, M$ way is to slightly diverge from it from no apparent reason...sigh...
Anyway, given more registers in *x86-64*, a lot of variables are passed into them, instead of being put onto the stack then read (as happens with *i386* convention). So even just for this reason (and believe me there are many more) *x86-64* is faster than *i386*.

Cheers,

---

