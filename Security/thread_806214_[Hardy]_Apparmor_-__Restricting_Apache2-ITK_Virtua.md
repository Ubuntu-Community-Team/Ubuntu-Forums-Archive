---
title: "[Hardy] Apparmor -  Restricting Apache2-ITK VirtualHosts"
date: 2008-05-24
forum: Security
---

### Post by cookie971 on 2008-05-24
Hey,

I'm setting up a shared hosting solution, with apache2-mpm-itk for user management and libapache2-mod-chroot to chroot /var/www/ and I'm having trouble enforcing the a policy idea, here are the fundamentals:

1. 1 User per Vhost with a home directory in /var/www/$vhostuser

2. Allowed PHP (libapache2-mod-php5) and all the libs and PEAR libs available.

3. Allowed Perl (libapache2-mod-perl2) and all the CPAN libs with it.

Now the above I can manage, but I have a problem enforcing the following policy:

* Recursivly deny scripts and applications within the /var/www/$user/ to read/write/execute/link outside their directory other than the PHP/Perl Libs, Binaries and MySQL databases.

* Restricting Apache2-ITK to setuid vhost to root

How can I do this ?

Cookie971

---

### Post by cookie971 on 2008-05-30
any ideas ? anyone ?

---

