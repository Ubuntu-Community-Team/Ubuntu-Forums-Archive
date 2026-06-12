---
title: "fin Unused Functions with GCC"
date: 2015-02-03
forum: Ubuntu Application Development
---

### Post by cranberries2 on 2015-02-03
Hi all, 
I should reduce code size somehow. The first way which comes to my mind is to find unused functions. I just explored the way of finding unused functions. It says that "-Wunused" parameter should be added to the end of compile command as follows ; 

clearmake -C gnu -Wunused  bla bla ..

But it didn't work. Compiler does not know this param. Could you please help about the way of finding unused functions with gcc.

Thanks in advance for the replies,
Cranberries

---

