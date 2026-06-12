---
title: "sendmail and php"
date: 2006-02-06
forum: Server Platforms
---

### Post by Compact on 2006-02-06
I've got apache 2.2.x in a ubuntu server. I've got 2 virtualhost and i want that when php send a mail from the virtualhost host1.example.com the mail came from host1.example.com and when php send a mail from host2.example.com the mail came from host2.example.com. How can I do it? 

Sorry about my english :-?

---

### Post by MJN on 2006-02-06
Can you not just alter the From: field in the relevant PHP mail command?

E.g.

**mail($mailto, $subject, $message, "From: \"host1.example.com \" <$email>" );**

Presumably the pages on each virtual host are different? Or, if not, you could just make the relevant mail page on each host different.

Mathew

---

### Post by Compact on 2006-02-08
Is there another way? like changing the sendmail config filw or something like this, because i use a lot of php scripts (like gallery) and it has a lot of places where i should change it. Thanks for your time.

---

