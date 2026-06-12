---
title: "POST data is empty"
date: 2006-05-07
forum: Server Platforms
---

### Post by yoyek on 2006-05-07
Hallo,

At first - im new to Ubuntu and Linux in general. Sorry for my bad english also.

I have installed Ubuntu for php scripts testing. Then i have installed [Xampp server bundle]("http://www.apachefriends.org/en/xampp-linux.html") (php 5.1.2, apache 2.2.0).

Problem:
After submitting html form to php script $_POST array is empty. Form has correct method setted.

Firstly i thought that it is firefox problem, so i submitted this form with Konqueror and Opera. Still print_r() says that my $_POST array is empty.

Then i thought that it's PHP problem, although I did'nt change php.ini at all. I've checked bug [17897](http://bugs.php.net/bug.php?id=17897), [19365](http://bugs.php.net/bug.php?id=19365), [32109](http://bugs.php.net/bug.php?id=32109), [33741](http://bugs.php.net/bug.php?id=33741) and [32375](http://bugs.php.net/bug.php?id=32375). Then I installed PHP 5.1.4 (from dotdeb packages). Still with no success. I also chack php.ini settings for "variables_order".

Then I start to think that maybe problem lays in apache. So I installed another version of apache (2.0.54) - I did not touch any .conf file. Still no success. I read somwhere that problem may be in AddInputFilter and AddOutputFilter httpd.conf directives for php files, but none of them exist in my config.

So... now I think that problem lays in linux. And as a total newbee in linux system I don't know what to check. Maybe some core configuration files for web/net services are configured inproperly (I did not change anything by hand).

I dont know how to check which version of ubuntu I have.

Please help me.

---

