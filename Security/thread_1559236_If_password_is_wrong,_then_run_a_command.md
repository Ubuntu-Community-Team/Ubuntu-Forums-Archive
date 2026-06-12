---
title: "If password is wrong, then run a command"
date: 2010-08-23
forum: Security
---

### Post by dades88 on 2010-08-23
I want that in the phase of "login" and in the phase of "lock screen", if password is wrong, then Ubuntu runs my custom command. is it possible?? How??

P.S. sorry, but I'm Italian and I don't speak the English very well.

---

### Post by triunenature on 2010-08-23
Hey, i know this isn't what you asked for.

But if you are looking for a way to stop brute force. (if thats why you want the custom script)

You may want to look into, [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)

and if you are paranoid,  
```
logfail -l 30
```
that will deny login for 30 seconds after failed attempt.

I don't know how to do a custom script, but maybe one of these options will work!!!

---

### Post by dades88 on 2010-08-24
I want run a script because i want that if password is wrong, then Ubuntu get a Image by cam. So i can see who has tried to login in my laptop.

---

### Post by Lars Noodén on 2010-08-24
My guess:

[PAM](http://packages.ubuntu.com/lucid/libpam0g) allows several methods to be tried before authentication is considered failed.  
It *might* be possible to point to your script there to be called if the other methods fail.

The manual pages [pam(7)](http://manpages.ubuntu.com/manpages/lucid/en/man7/pam.7.html), [pam(5)](http://manpages.ubuntu.com/manpages/lucid/en/man5/pam.5.html), and [pam(3)](http://manpages.ubuntu.com/manpages/lucid/en/man3/pam.3.html), are the authoritative references, but you can find supplementary tutorials.

Be careful not to lock yourself out of your own computer while experimenting.  You may want to first set up an at or cron job to automagically restore working settings.

---

