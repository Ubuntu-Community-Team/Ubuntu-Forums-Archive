---
title: "How to allow file saving to www directory?"
date: 2009-09-17
forum: Server Platforms
---

### Post by UbuKunubi on 2009-09-17
Thanks for taking the time to read this.

My server expired (on-board NIC failure), so I'm having to use my Jaunty desktop to host my site.

I have apache up, running, and configured (i can see the 'It works!' message via my web address), but I need to simply be able to save files from my current user to the /var/www directory.

How can i change the permissions of the user to do this?

I have tried chown, sudo chown, and all the usual combinations that i find to normally work, but when I try to save my new index.html from my desktop I get the error:You do not have the necessary permissions to save the file.

Thanks for any help/advice/pointers,
Ubu

---

### Post by wojox on 2009-09-17
I 

```
chmod 700 
```

www, it gives owner complete access and everyone else none.

---

### Post by Bachstelze on 2009-09-17
> **wojox said:**
> I 

```
chmod 700 
```

www, it gives owner complete access and everyone else none.

That's a very bad idea..

@OP: What you can do is:

```
sudo chown -R $USER:www-data /var/www
sudo chmod -R 750 /var/www
```

It will give read-wxrite access to yourself, rea-only access to Apache so it can read your files and serve them, and no access to everyone else.

---

### Post by UbuKunubi on 2009-09-17
> **Bachstelze said:**
> That's a very bad idea..

@OP: What you can do is:

```
sudo chown -R $USER:www-data /var/www
sudo chmod -R 750 /var/www
```

It will give read-wxrite access to yourself, rea-only access to Apache so it can read your files and serve them, and no access to everyone else.

Will that effect mod-python?
I have a script that works on files there.

Thanks for the sample - I assume I replace $USER with my user name?

---

### Post by Bachstelze on 2009-09-17
> **UbuKunubi said:**
> Will that effect mod-python?
I have a script that works on files there.

Please elaborate. What does "work" mean here?

> **UbuKunubi said:**
> Thanks for the sample - I assume I replace $USER with my user name?

It should work as is, but you can of course replace it with your username too.

---

### Post by UbuKunubi on 2009-09-17
> **Bachstelze said:**
> Please elaborate. What does "work" mean here?



It should work as is, but you can of course replace it with your username too.

By working there I mean I have a mod-python program that reads input from a web page form and posts messages into a webpage- a message board.

---

### Post by Bachstelze on 2009-09-17
> **UbuKunubi said:**
> By working there I mean I have a mod-python program that reads input from a web page form and posts messages into a webpage- a message board.

Then just [font=monospace]chmod 770[/font] the files Apache needs to have write access to.

---

### Post by UbuKunubi on 2009-09-17
> **Bachstelze said:**
> Then just [font=monospace]chmod 770[/font] the files Apache needs to have write access to.

Excellent!

Many thanks for you help.

---

