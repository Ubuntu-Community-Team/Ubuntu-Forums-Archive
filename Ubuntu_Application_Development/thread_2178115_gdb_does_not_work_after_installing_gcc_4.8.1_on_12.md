---
title: "gdb does not work after installing gcc 4.8.1 on 12.04: &quot;Unable to find dynamic linke&quot;"
date: 2013-10-02
forum: Ubuntu Application Development
---

### Post by vincegata on 2013-10-02
[COLOR=#333333][FONT=UbuntuRegular]Hi,

I installed gcc 4.8.1 on Ubuntu 12.04 (I had to add ppa to do that) now gdb displays the following message:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Unable to find dynamic linker breakpoint function. GDB will be unable to debug shared library initializers and track explicitly loaded dynamic code.Could not load shared library symbols for 5 libraries, e.g. /usr/lib/x86_64-linux-gnu/libstdc++.so.6. Use the "info sharedlibrary" command to see the complete listing. Do you need "set solib-search-path" or "set sysroot"?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I did google and I found this article to best answer my question:[http://www.fayewilliams.com/2013/01/31/gdb-unable-to-find-dynamic-linker-breakpoint-function/](http://www.fayewilliams.com/2013/01/31/gdb-unable-to-find-dynamic-linker-breakpoint-function/)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]however I still do not understand what to do. Could someone help. THX![/FONT][/COLOR]

---

