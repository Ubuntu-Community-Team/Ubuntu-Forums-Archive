---
title: "Help: How do Remove OS Password for PostgreSQL user postgres"
date: 2017-04-13
forum: Server Platforms
---

### Post by m-dw on 2017-04-13
Before I started messing about today, I was able to issue the command "su postgres" and get a prompt without entering a password.

For reasons I will go into if asked, I have configured a password for the linux user 'postgres' using the passwd program. I now have to enter the password I set when I want to run programs in a shell owned by postgres. However I now realise that I didn't actually need to do that.

[LIST=1]
[*]How can I set the user back to its previous state?
[*]Do I need to?
[/LIST]
[INDENT=2](I run a backup script owned by user postgres which dumps my databases to flat files every night)[/INDENT]

I've tried passwd -d, and it just disabled the login completely.

---

### Post by darkod on 2017-04-13
Hmmm, it's much better security practice to have the password anyway. Can't you easily implement the password in your script and leave the user to have it, rather than removing the password?

Honestly, once set I have never looked for how to remove a password...

---

### Post by m-dw on 2017-04-13
I thought that about the security thing too - that wasn't my motivation. I'll look at handling the password in the script if it fails tonight

---

