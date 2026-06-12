---
title: "PHP GD &amp; cURL support"
date: 2006-03-08
forum: Server Platforms
---

### Post by Bunro on 2006-03-08
Hopefully there is somebody that can help me out.

I need the following support switch on.
- GD support in PHP at least version 2.0 or up.
- PHP cURL support=OFF and would like to switch to On.

What I did is sudo gedit /etc/php4/apache2/php.ini
In this file I uncommented extension=gd.so
My question is this enough or do I need to install a gd software package?

And I did not find any parameter/ switch in php.ini to set the PHP cURL support=On.

Regards, Robert

PS. I installed the following packages via sudo apt-get install
Ubuntu 5.10
Apache2 version: 2.0.54
PHP version: 4.40-3ubuntu1
MySQL version: 4.0.24

---

### Post by gmclachl on 2006-03-08
HI,
         apt-get install php4-gd php4-curl 

  Should do it. 

 George

---

### Post by Bunro on 2006-03-08
Hi George,

It is magic! What a fast answer.
And it is working!!!

I have one last question:
My MySQL server is running as MYSQL_MODULE_TYPE: external do I need to change this and if so how do I do it.

Thanks again!

Regards, Robert

---

### Post by gmclachl on 2006-03-09
Hi,
       It should be ok, just make sure you have enabled mysql support in php.

   apt-get install php4-mysql 

  George

---

### Post by Bunro on 2006-03-16
Thanks George,

For your answer.
Sorry for my late reaction. 

Regards, Robert

---

### Post by lufky on 2006-08-25
Dear George...i've done this command (like you have writen before) unfortunately i got different respond with Robert ](*,) . 

[B]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4-gd[/B]

please give some advice how to solve this problem..thank you

---

### Post by Kurt` on 2006-08-25
They're not in the main repositories.

Follow this guide: [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Then, after # apt-get update'ing, you should be able to install it with the command you tried before.

After that, # /etc/init.d/apache2 reload, and you're good to go. :)

---

