---
title: "On startup - prompt asking for apache certificate password doesn't accept input"
date: 2010-11-29
forum: Server Platforms
---

### Post by psyncho on 2010-11-29
Can switch to another tty but can't restart apache due to the port already being bound (suppose I could change ports for apache config after startup but that's pretty ugly and clearly not the right way to address the problem

---

### Post by psyncho on 2010-11-29
Now I see a ureadahead error with exit status 4 - not sure if or how that may be related.

---

### Post by TSJason on 2010-11-29
You need to remove the passphrase from the certificate's key file in your production environment. Basically something like this:

```
cp server.key server.key.encrypted
openssl rsa -in server.key.encrypted -out server.key
```

It should prompt you to enter the passphrase and write out the new server.key file sans the passphrase.

---

### Post by psyncho on 2010-11-29
> **TSJason said:**
> You need to remove the passphrase from the certificate's key file in your production environment. Basically something like this:

```
cp server.key server.key.encrypted
openssl rsa -in server.key.encrypted -out server.key
```

It should prompt you to enter the passphrase and write out the new server.key file sans the passphrase.

I'm aware of that being an option, but if memory serves, in prior setups I was simply able to enter the password on startup and everything was fine. The tty7 however is completely unresponsive - I can't even type in the password. 

Since, I've removed encryption from my apache setup, restarted the computer, then added encryption back in, and then restarted apache, entered the password for the key, and everything was fine. It's only on rebooting the entire machine that I get this problem. 

Is there really no way around this other than removing the password? I'd like to keep it for security reasons in case the machine get's hacked - so no one can spoof others as my server using my key and certificate

---

### Post by TSJason on 2010-11-29
Hmm. Well, I would probably try taking out the "splash" and "quiet" options from grub, and then run "update-grub" before rebooting again to test it.

---

### Post by psyncho on 2010-11-29
Apparently it's the script starting services (upstart?) which is set to not accept input, thus I can't type in the pswd for apache key.

See: 
[http://ubuntuforums.org/archive/index.php/t-774692.html](http://ubuntuforums.org/archive/index.php/t-774692.html)

and 
[https://bugs.launchpad.net/ubuntu/maverick/+source/apache2/+bug/582963](https://bugs.launchpad.net/ubuntu/maverick/+source/apache2/+bug/582963)

unfortunately, their fix of adding stty sane to the apache2 startup script doesn't help me

---

