---
title: "Posted form variables on local server"
date: 2007-03-02
forum: Server Platforms
---

### Post by Sitix on 2007-03-02
Hello,

I have a LAMP server installed, with everything up and running properly. Though, there is one problem. As soon as I want to use a form, ie <form action="<? echo $PHP_SELF; ?>" method="post" name="form" id="form">, it doesn't remember the variables of the form, for the next page to be processed.

So I can read stuff from my mysql database, but I can't insert any information.

I tried $_GET['variable'] and $variable, but it does nothing. It doesn't even give a mysql error. If ($_POST['submit']){} doesn't work, while submit is true, since there is a hidden field called submit with a value in the form. So, there is no other option than a server side problem.

Can someone help me out?

---

### Post by tturrisi on 2007-03-02
post the code that does not work.

---

### Post by kidders on 2007-03-02
Hi there,

> **Sitix said:**
> As soon as I want to use a form, ie <form action="<? echo $PHP_SELF; ?>" method="post" name="form" id="form">, it doesn't remember the variables of the form, for the next page to be processed.

So I can read stuff from my mysql database, but I can't insert any information.

I tried $_GET['variable'] and $variable, but it does nothing.The HTTP method in your example is POST, not GET. It's also worth noting that the use of superglobals like $PHP_SELF is outdated ... <?=$_SERVER['PHP_SELF']?> is preferable, although that's probably not the cause of your trouble.

Try **print_r($_POST);** after your form submission, and see what you get.

---

### Post by Sitix on 2007-03-02
@kidders: yes sorry, I typed $_GET but I meant $_POST... :P my mistake. The code says $_POST though.

Okay, thanks to your print_r($_POST); I found out how I did something my computer thinks is wrong. Apparently there is something in my PHP version (or so) that doesn't like the way I program normally. I found a way to make it work.

I think it has something to do with the PHP version. I still wonder why it doesn't work the old way, as it does work on my external server.

Anyway, thanks for your help!

---

### Post by kidders on 2007-03-02
> **Sitix said:**
> I think it has something to do with the PHP version. I still wonder why it doesn't work the old way, as it does work on my external server.Yeah... the various PHP versions aren't necessarily backward compatible, and a lot also depends on php.ini settings, etc. It's good practice not to cling to archaic coding styles for too long (the developers usually describe the motivations behind notational changes, to help you write code with the best chance of working for as long as possible), and to code in a way that is as tolerant as possible of variations in server configuration.

Glad you sorted it out. :-)

---

