---
title: "Allow www-data to create directories"
date: 2014-09-01
forum: Security
---

### Post by anon8 on 2014-09-01
How would I, with security in mind, allow *www-data* to create directories within */var/www/html/assets/img* and its sub-directories?

  I have a PHP script that automatically creates directories with 777 permissions, but *www-data* currently doesn't have the required permissions to allow that.

---

### Post by TheFu on 2014-09-02
Danger Will Robinson - mixing php, with 777 permissions seems like a mostly bad,bad, bad idea.  

So - I used to suggest that you learn about userids, groups and permissions for files and directories.  This is the core of Linux security and extremely important to avoid being hacked.  For php-based webapps - it is 1000x more important. "Critical" is the term I'd use.  Anyway - seems that tutorial didn't explain WHY, so it wasn't too useful. The WHY is easy to understand with the appropriate background - without it - well - it is all Greek to everyone except experienced people.

In the spirit of teaching a man to fish .... 
* [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)
* [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - (free) Linux Command Line Book - nice chapter on permissions ... after enough background information has been provided first.

So ... if you just want the exact command to type and don't care how is removes 80% of the security for your webserver - fine. Ask.  The botnet guys would love to have another server in the C&C group.

Think I'm being overly dramatic? Here's what happens to cracked servers:
[http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/)

---

### Post by thnewguy on 2014-09-02
Either make www-data the owner of the directory you want it to be able to writ to, or make the directory's group www-data.

For example, you could do something like this:
```

chown -R www-dat[COLOR=#000000]a /var/www/html/assets/img
chmod 755 /var/www/html/assets/img

```

As TheFu said above, using permissions like 777 on anything is a bad idea. Make sure the proper user has ownership of the directory and give them (and only that user) write access to the location.[/COLOR]

---

### Post by bashiergui on 2014-09-03
> Think I'm being overly dramatic? Here's what happens to cracked servers:
[http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/)LOL 4 hours. I actually considered doing something similar to my own servers earlier today.> How would I, with security in mind... Let's ask WHY. Why do you want to create the directories? What are you trying to accomplish?

---

### Post by Habitual on 2014-09-04
Is there ***ever*** a good reason for 777?
the exception being /tmp

---

### Post by TheFu on 2014-09-04
/tmp has +t set, so it really isn't 777.

For certain values of "good", I've had to set 777 permissions for some specific applications, running on secure networks, completely disconnected from any other network, with trusted end-users.

For an internet connected machine ... I suppose if you'd like to make a directory more hackable, sure - go ahead.  I'd rather see ACLs (which I avoid like ebola!) used before going to 777 permissions.

---

### Post by Habitual on 2014-09-04
I should have clarified "ever" as I meant internet-facing hosts.

IMHO, 777 is NEVER a good idea on one and it NEVER "fixes" anything.

---

