---
title: "Ubuntu and Mysql unicode"
date: 2009-07-08
forum: Server Platforms
---

### Post by Alon123 on 2009-07-08
I have moved my MYSQL server from windows to work on ubuntu 9 server

the server is working great but when i try to insert text in hebrew its write ???????...

how can i fix this ??

---

### Post by masux594 on 2009-07-08
I don't understand.. It write "???" in database or when you try to read the field, you read "???"..?

Sysc, A

---

### Post by Alon123 on 2009-07-08
Actualy when the program write to the database (.net application that runing on windows...)
its write ?????? to the database
but if i try to write directly to the database (via mysql GUI tool ) even in hebrew its ok.

---

### Post by masux594 on 2009-07-08
Windows version? do u have the hebrew fonts installed into winzoz? I'm a developer, and i know that there's 2 kind of character.. The first need 1 byte[normal characters], the second needs 2 byte [hebrew and other special characters].. In Pascal [the language with i work] there's 2 kind of data, "String" and "WideString".. The problem that u have is that the variable or methods that u call doesen't support the 2 bite characters.. So, I don't know about .net, but try to focus the searches in this way.. I Hope i help u!

Sysc, A

---

### Post by Alon123 on 2009-07-09
Hi 

I checked the settings for MYSQL and  I changed the charecter from latin1 to utf8

now it working ...

---

