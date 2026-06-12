---
title: "I made a compile script"
date: 2008-07-15
forum: The Cafe
---

### Post by collinp on 2008-07-15
Ok, I don't know if this is the right place to put this, or if this has been done before (im sure it has), but I made a script to automatically compile and install anything that uses standerd compile/install commands (./configure, make, make install). So if you get tired of manually compiling everything, here is your solution.

---

### Post by LaRoza on 2008-07-15
There is a bug ;)

This will ensure it won't go to the next command if there is an error on a previous one.

Of course, it could be made more useful with more options.

```

./configure && make && sudo make install && echo "Compile finished"

```

---

### Post by collinp on 2008-07-15
Heh, im pretty new to scripting, so thanks, ill correct it.

EDIT: fixed it

---

