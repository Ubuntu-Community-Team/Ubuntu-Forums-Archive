---
title: "Is it possible to use Xorg in single user mode?"
date: 2010-08-03
forum: The Cafe
---

### Post by dragos240 on 2010-08-03
I'm curious, since Xorg was designed to be used in multi-user mode which is init 3.

---

### Post by wesleybailey on 2010-08-03
Ok, let us try this again. 

Is your question. Since Xorg is already running in multi-user what is the purpose of level 3?

Init level 3 allows multi-user command line access.

Sorry if this isn't what you are looking for, but you question is confusing me..

Cheers

---

### Post by dragos240 on 2010-08-03
Yes. And init 1 is single user.

I know that already

---

### Post by wesleybailey on 2010-08-03
Nm

---

### Post by dragos240 on 2010-08-03
Xorg was designed to run on the multi-user runlevel. I didn't know if it was possible to run X on single user mode.

EDIT: What's this doing in the cafe?

---

### Post by wesleybailey on 2010-08-03
Just my two cents worth, but I don't think it would be easy or possible to boot X in init 1(single user mode).

I would think that X would require libraries or dependent programs that are only available in multi-user mode.

Source: 6 years running linux

---

### Post by dragos240 on 2010-08-03
Yeah. I would have thought so.

---

