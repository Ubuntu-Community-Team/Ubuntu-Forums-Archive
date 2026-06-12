---
title: "help with apache2 and authentication"
date: 2009-02-07
forum: Server Platforms
---

### Post by meomike2000 on 2009-02-07
this is my first setup that has needed me to use authentication to make a set of pages private. I have set up my password file and added a <Directory></Directory> into the configuration specifying the directory. the log in and authentication works. the box that pops up asking for my username and password is very generic but all seems to work. i tested it with correct username and password and with alternate username and password combos and it works. 

but i have a couple questions, #1. can that generic box be changed to something more appealing, and if so can somebody lead me to some help with that.

the #2 question. after i have entered my username and password and allowed access to the directory and its contents, why if i leave there and then go back does it not ask for username and password again, it just goes straight to the page again.

thanks in advance, mike......

also this is on an ubuntu 8.04 box.

---

### Post by inphektion on 2009-02-07
You can use "AuthName" to add a message to the box.  I think that's the best you can do.
the only way to do #2 is which scripts in pages like .php or .cgi, etc.

---

### Post by meomike2000 on 2009-02-07
that is what i was thinking, any idea where i can find help with a php script that can handle authentiction. i have one that authenticates username and password. but only because it checks what is enter into both fields against some values that i have loaded into another script that is included in the script file. i dont know if that is the proper way or not.....

thanks mike.....

---

### Post by jimv on 2009-02-08
I'm not a PHP programmer, but it seems that if you're just using one user, you could hardcode the username/login into the code on your login page.  Since the page gets processed by Apache, you shouldn't have to worry about anyone ever being able to look at the code and see your login/password.

Not the best idea if you're going to want more than one user, but I don't see why not if you just want to secure it for you.

---

### Post by inphektion on 2009-02-08
just google for php login session and such.  tons of examples, you'll surely find what suits your needs.

---

### Post by meomike2000 on 2009-02-13
i used php with database authintication. username and passwords are stored in a database. thanks of the help.

---

