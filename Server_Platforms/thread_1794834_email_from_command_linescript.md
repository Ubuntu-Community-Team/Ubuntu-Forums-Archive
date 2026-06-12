---
title: "email from command line/script"
date: 2011-07-01
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-07-01
Hi guys

Ive recently been learing to script on a ubuntu server 11.04 virtual machine.
Is there a way to send an email from a batch script.
I want to send the output from a script to an email address, possibly a couple of email addresses depending on the output.

Is this possible.

---

### Post by Cheesehead on 2011-07-01
I use the 'nail' command (from the 'heirloom-mailx' package) for this purpose.

---

### Post by bigmonmulgrew on 2011-07-01
Thanks for the quick reply.
Its gonna be about a week till i get chance to test this but i will post my results then

---

### Post by ruffEdgz on 2011-07-01
If you installed **mailutils** and also configured **postfix** correctly, you can use the following command for emailing through bash:
```

echo "This is a test" | mail -s "test1" noname@example.com

```
or 
```

echo "This is another test" >> ./test.file
mail -s "test2" noname@example.com < ./test.file

```
There are other ways but those are two of the types I have used myself.

---

