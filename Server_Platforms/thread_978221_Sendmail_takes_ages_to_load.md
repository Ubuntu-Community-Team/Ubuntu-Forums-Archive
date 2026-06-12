---
title: "Sendmail takes ages to load"
date: 2008-11-10
forum: Server Platforms
---

### Post by codemyster on 2008-11-10
When using Sendmail, in this case through PHP 5, it takes ages to load. The call to mail() (Which, in this case, calls on sendmail), takes an extremely long time to return. The email is successfully sent, but it takes an awfully long time. 

I get the same result from running sendmail from the terminal. It takes upwards of half a minute to get any output whatsoever from the program. Does anyone know what's wrong?

---

### Post by iponeverything on 2008-11-10
I have used postfix and qmail with much success. Both are lean, fast and easy to setup and debug.

I have also done a number of sendmail installs, but it is a bit.. what's a nice way to say it.. feature rich.

---

### Post by codemyster on 2008-11-10
Odd. I've tried a Postfix install a few times and it seems to hang at the first screen asking you which type of configuration you wish to use. It doesn't allow me to get past that screen.

---

### Post by hictio on 2008-11-11
Couple of things I suspect, mainly DNS problems, does sendmail on your box also takes a lot of time to start?
Check your DNS settings, on the file '/etc/resolv.conf', and take a look at the '/etc/hosts' file too.
Does your Ubuntu server box have a FQDN?

---

