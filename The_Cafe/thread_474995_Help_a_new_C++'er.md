---
title: "Help a new C++'er"
date: 2007-06-15
forum: The Cafe
---

### Post by medicineman24 on 2007-06-15
I just started learning to code a few days ago.  I wrote this (attached w/ source) and when I try to repeat the program with "goto loop;" and "loop:" the program skips the user input for the class name.  Why is this? How can I fix this?

Thanks in advance
Suggestions and criticism welcome (:

---

### Post by Erunno on 2007-06-15
Don't use goto. Ever. Unless you are an experienced programmer who knows exactly what he's doing stay away from it. Don't touch it with a ten-foot pole. Best erase the knowledge of it. If your program needs goto (especially in C++) the design is screwed.

---

### Post by medicineman24 on 2007-06-15
ok... I'll try to rework it

---

### Post by medicineman24 on 2007-06-15
Ok it wasn't the goto statement but I'll still take your advice.  The "getline (cin, nameofclass)" wasn't repeated so I changed it to "cin >> nameofclass" and it works! 

Does the getline ever get repeated?

---

### Post by Sp4cedOut on 2007-06-15
goto is considered bad programming practice.  I would also recommend not using it.

---

### Post by Cheese Sandwich on 2007-06-15
Ditto on no goto.

---

