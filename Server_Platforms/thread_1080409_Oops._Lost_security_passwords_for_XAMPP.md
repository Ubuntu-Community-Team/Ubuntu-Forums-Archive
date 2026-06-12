---
title: "Oops. Lost security passwords for XAMPP"
date: 2009-02-25
forum: Server Platforms
---

### Post by anthonie on 2009-02-25
Hi all,

I did something very stupid. Just before I got moved from one office to another building, I have installed a fresh XAMPP bundle. Because of the network in the old office, I have set all the passwords through the XAMPP interface. After that I had lots of other tasks at hand, so no time to play with programming. But now I am settled in my new office, I had to continue working on some php projects. However, in the mean time, the paper with all the passwords was lost, either during the moving or some other way.

All short: Is there a way to reset the passwords for XAMPP/MySQL and PhpMyAdmin without having to reinstall the whole bundle again?

Advise appreciated.

Regards,
Anthonie

---

### Post by mike_g on 2009-02-26
Sounds like you need to reset the mysql root password.
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix)

---

### Post by darnielng on 2009-06-19
> **anthonie said:**
> Hi all,

I did something very stupid. Just before I got moved from one office to another building, I have installed a fresh XAMPP bundle. Because of the network in the old office, I have set all the passwords through the XAMPP interface. After that I had lots of other tasks at hand, so no time to play with programming. But now I am settled in my new office, I had to continue working on some php projects. However, in the mean time, the paper with all the passwords was lost, either during the moving or some other way.

All short: Is there a way to reset the passwords for XAMPP/MySQL and PhpMyAdmin without having to reinstall the whole bundle again?

Advise appreciated.

Regards,
Anthonie
Hi anthonie

It's very simple, took me quite a while.

Run the "sudo /opt/lampp/lampp security" again.

It will prompt you to reset your XAMPP login passowrd. Your Ubuntu host root account will overwrite it.

Sometimes I wish Linux help and adivse would come of an easier answer. Instead of redirecting to another to run 10-20 commands and dig ourselves deeper into the problem.

Cheers.

---

### Post by mrhelionprime on 2013-03-13
Dear Darnielng,
thank you very much for the tip,
I reseted my pw in just 20sec

Briliant

---

