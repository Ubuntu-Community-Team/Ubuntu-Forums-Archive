---
title: "How to set up LAMP using Perl?"
date: 2009-05-21
forum: Server Platforms
---

### Post by ItecKid on 2009-05-21
So, I have my LAMP set up with PHP, which works great.  If I point my browser at localhost/hello.php, I get my hello world program.

Problem is, my PHP skills leave much to be desired.  So how can I get Perl working alongside PHP here?  That is to say, right now, if I point my browser at localhost/hello.cgi, all I get is the raw script, rather than the output.  I did this:

```

sudo apt-get install libapache2-mod-perl2 libapache2-mod-perl2-doc

```

and restarted apache, but their seems to be extra steps required to get this working correct?

Thanks for any help you can provide.

BTW, running Ubuntu 9.04.

---

### Post by ItecKid on 2009-05-21
Ok, so, incredibly stupidly, I forgot to 

```

chmod 700

```

on my .cgi file.  However, now when I try to run it, I get error 403 Forbidden.

Any one can help with this?

---

### Post by BkkBonanza on 2009-05-21
What is the ownership of the cgi file? What user does apache run as? Make sure that the apache user has exec rights for the file.

---

### Post by ItecKid on 2009-05-21
The file is stored in a root-protected directory (/var/www, same directory as PHP files) so I did

```

chmod ogu+x

```

But still get error 403.

---

