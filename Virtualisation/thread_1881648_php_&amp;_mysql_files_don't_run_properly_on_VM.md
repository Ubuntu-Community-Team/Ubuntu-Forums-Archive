---
title: "php &amp; mysql files don't run properly on VM"
date: 2011-11-15
forum: Virtualisation
---

### Post by BobDull on 2011-11-15
Hello,

Using Ubuntu 11.10 as my main machine.

Using Ubuntu 11.04 on my virtual machine.

I wrote a very simple php file that takes input in the first .php file, creates a table in an sql database, and when the user presses submit it stores it in that table and then calls a loop to print the data out. 

This works fine on my Ubuntu 11.10 LAMP setup. 

I took the exact same files into my 11.04 Virtual Machine, which has a LAMP setup as well and its updated. I wrote some code to check what happens when I "CREATE TABLE", and that is where the sql is getting hung up. So, since it never creates the tables, it can't complete the query to access them since they don't exist.

Any ideas why it would be having troubles calling CREATE TABLE ?

Thanks!

P.S. I'm sure you will want more information/need more to help me. Feel free to flame me just let me know what else I need to throw up here to help you help me.

---

