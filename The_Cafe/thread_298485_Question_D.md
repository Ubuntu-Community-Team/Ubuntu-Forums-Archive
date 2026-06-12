---
title: "Question :D"
date: 2006-11-12
forum: The Cafe
---

### Post by Reiko on 2006-11-12
How can i open in Ubuntu files to view their hexadecimal form.

---

### Post by Christmas on 2006-11-12
I do not know.

---

### Post by Reiko on 2006-11-12
funny :))

---

### Post by Reiko on 2006-11-12
bine mai Danutz

---

### Post by oxEz on 2006-11-12
> **Reiko said:**
> How can i open in Ubuntu files to view their hexadecimal form.

In console you can do: xxd (yourfilehere)

Example: xxd data.dat

If you want to echo the output in another file, just do:

xxd data.dat >> someotherfile 

Hope this helps.

---

### Post by Reiko on 2006-11-12
YEY THANK YOU oxEz

---

### Post by Reiko on 2006-11-12
Now the problem is : How can I modify that object file, in his hexadecimal form. xxd just prints his hexadecimal. So if i make a C "hello world" program and "$ xxd "the compiled file" > executeMe" . I can't run executeMe (with no errors) cuz is a ASCII file. So I want that file to be still binary. And i want to edit it in that form :D thx

---

### Post by DoctorMO on 2006-11-12
You could always write a perl program to insert the correct bytes at given locations.

once you have your mod use patch --binary to store it.

---

### Post by IYY on 2006-11-12
**hexedit** is the program you're looking for.

---

### Post by pmj on 2006-11-13
Try ghex.

---

### Post by Reiko on 2006-11-13
thank you

---

