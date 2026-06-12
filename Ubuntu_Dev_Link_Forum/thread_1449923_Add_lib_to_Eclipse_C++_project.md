---
title: "Add lib to Eclipse C++ project"
date: 2010-04-08
forum: Ubuntu Dev Link Forum
---

### Post by commander figor on 2010-04-08
Just installed U 9.10 and added most current Eclipse, CDT, and installed the GCC compiler.
 
I've created a simple Hello World project (one line) and then just as a test added "audio" to the project settings GCC C++ linker libraries dialog, and "/usr/lib" to the library path dialog. Did not include "lib" or "so" in the lib file name.
 
Yet on compile I get error "cannot find -laudio". I'm a newbie (obvious). Appreciate anyone's help in advance!
 
:confused:
 
 
SOLUTION: Create symbolic link file that does not include revision number in file name. Best explained here:
 
[http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/shared-libraries.html](http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/shared-libraries.html)

---

