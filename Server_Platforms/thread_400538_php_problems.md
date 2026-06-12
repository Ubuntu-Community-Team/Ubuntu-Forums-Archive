---
title: "php problems"
date: 2007-04-03
forum: Server Platforms
---

### Post by djearwig on 2007-04-03
Thanks for taking the time to read this; I really appreciate any help.

I have installed a LAMP server running Ubuntu 6.1.
I also installed phpLDAPadmin, to administer my LDAP accounts.
However; much to my surprise, when I put the phpLDAPadmin files into my /var/www/ folder and pointed my browser at them, I discovered the php scripts aren't working.  The funny this is, they were.  I had the test.php page and when I pointed my browser to it, it displayed the information that I was expecting.  Now when I point to php files, all i get are php scripts.

Another wacky point, the output of this : php -r 'echo "PHP Works!\n";'
Is this: eric@ubuntu-server:/etc/samba$ php -r 'echo "PHP Works!\n";'
PHP Works!

So, I am completely confused at the moment and am humbly asking for a little guidance.

Thank you

---

### Post by djearwig on 2007-04-04
So, I guess that I will try to compile the php source and see if that fixes the problem...

---

### Post by djearwig on 2007-04-04
Well, that didn't fix it...

---

### Post by az on 2007-04-04
Do you have the appropriate libapache2-mod-php5 package installed (assuming you are using apache2 and php5)

---

### Post by djearwig on 2007-04-04
Yes, the apache2 php5.conf and php5.load are in the mods-enabled folder.

---

