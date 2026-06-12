---
title: "Ubuntu"
date: 2005-08-19
forum: Server Platforms
---

### Post by soon82 on 2005-08-19
can somebody tell that, what is i386, alpha, openbsd, freebsd...

is it ubuntu is a i386...

Once i wanna to download some package... I had confuse about these...

Thank you

---

### Post by Velox Letum on 2005-08-19
It depends on which architecture that you downloaded for. If you downloaded for x86 then it is i386. OpenBSD and FreeBSD are a different type of operating system similar to Linux.

---

### Post by matthew on 2005-08-20
[QUOTE=soon82]can somebody tell that, what is i386, alpha, openbsd, freebsd...

is it ubuntu is a i386...

Once i wanna to download some package... I had confuse about these...

Thank you[/QUOTE]

The things you listed are as follows:

i386 is a short way to say "computer processors based on the Intel 386 family" which include the modern Pentium 3, Pentium 4, Pentium M as well as anything else that is compatible such as most current AMD processors.

The alpha is a different type of computer processor. If you don't know what it is, you don't have one.

openbsd and freebsd are both versions of an operating system based on unix, much like Linux is.

Ubuntu is a distribution of Linux that also includes lots of other good software and support to make a great operating system. Ubuntu linux will run on many different type of computers.

What type of computer do you own? What specifically do you want to do with it?

---

### Post by Velox Letum on 2005-08-20
[QUOTE=matthew]Ubuntu linux will run on many different type of computers.[/QUOTE]

Indeed, and instead of spending lots of money on obedience school, I loaded Ubuntu 5.04 onto my pet.

---

### Post by koggo on 2005-08-22
[QUOTE=Velox Letum]Indeed, and instead of spending lots of money on obedience school, I loaded Ubuntu 5.04 onto my pet.[/QUOTE]
 o_O

---

### Post by soon82 on 2005-08-22
i'm install ubuntu 5.04 on my Pentium 4 Computer... 

I would like to download the xmail source from [www.xmailserver.org](www.xmailserver.org)...

There got a lot of i386, alpha, openbsd, freebsd and so on...

i don't know which type suitable for me...

thank you... for yours

---

### Post by koggo on 2005-08-22
[QUOTE=soon82]i'm install ubuntu 5.04 on my Pentium 4 Computer... 

I would like to download the xmail source from [www.xmailserver.org](www.xmailserver.org)...

There got a lot of i386, alpha, openbsd, freebsd and so on...

i don't know which type suitable for me...

thank you... for yours[/QUOTE]
 i386 :)

---

### Post by az on 2005-08-22
Just enable universe and install it from there.  Use synaptic to add the universe repository and then refresh your package list.  Them when you search for it, you will find and be able to install xmail with two clicks.


kurn@ubuntu:~$ apt-cache search xmail
courier-faxmail - Courier Mail Server - Faxmail gateway
gdesklets-data - displays and sensors for gdesklets
php-mail-mime - PHP PEAR module for creating and decoding MIME messages
xmail - Advanced, fast and reliable ESMTP/POP3 mail server
xmail-doc - Documentation for xmail
xmailbox - A version of xbiff with animation and sound effects
kurn@ubuntu:~$ apt-cache show xmail
Package: xmail
Priority: extra
Section: universe/mail
Installed-Size: 732
Maintainer: Radu Spineanu <radu@timisoara.roedu.net>
Architecture: i386
Version: 1.20-5
Replaces: mail-transport-agent, pop3-server, finger-server
Provides: mail-transport-agent, pop3-server, finger-server
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libstdc++5 (>= 1:3.3.4-1), debconf (>= 0.5.0)
Conflicts: mail-transport-agent, pop3-server, finger-server
Filename: pool/universe/x/xmail/xmail_1.20-5_i386.deb
Size: 200292
MD5sum: d27981ef0a2d5314faf082dd7576d78e
Description: Advanced, fast and reliable ESMTP/POP3 mail server
 XMail is an Internet mail server featuring an SMTP, POP3 and finger server.
 It's incredibly easy to set up and has lots of features including :
 multiple domains, virtual users and spam protection.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by soon82 on 2005-08-23
[QUOTE=azz]Just enable universe and install it from there.  Use synaptic to add the universe repository and then refresh your package list.  Them when you search for it, you will find and be able to install xmail with two clicks.


kurn@ubuntu:~$ apt-cache search xmail
courier-faxmail - Courier Mail Server - Faxmail gateway
gdesklets-data - displays and sensors for gdesklets
php-mail-mime - PHP PEAR module for creating and decoding MIME messages
xmail - Advanced, fast and reliable ESMTP/POP3 mail server
xmail-doc - Documentation for xmail
xmailbox - A version of xbiff with animation and sound effects
kurn@ubuntu:~$ apt-cache show xmail
Package: xmail
Priority: extra
Section: universe/mail
Installed-Size: 732
Maintainer: Radu Spineanu <radu@timisoara.roedu.net>
Architecture: i386
Version: 1.20-5
Replaces: mail-transport-agent, pop3-server, finger-server
Provides: mail-transport-agent, pop3-server, finger-server
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libstdc++5 (>= 1:3.3.4-1), debconf (>= 0.5.0)
Conflicts: mail-transport-agent, pop3-server, finger-server
Filename: pool/universe/x/xmail/xmail_1.20-5_i386.deb
Size: 200292
MD5sum: d27981ef0a2d5314faf082dd7576d78e
Description: Advanced, fast and reliable ESMTP/POP3 mail server
 XMail is an Internet mail server featuring an SMTP, POP3 and finger server.
 It's incredibly easy to set up and has lots of features including :
 multiple domains, virtual users and spam protection.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu[/QUOTE]
 How to enable the universe and install from there

when i type the command apt-cache search xmail

it is nothing come out.....

may be i misunderstanding ..

can you help me further more...

thank you...

---

### Post by koggo on 2005-08-25
Open Synaptic.
Search for 'xmail'.
Mark all the xmail packages for installation.
Click 'Apply'.

Voila!

You may also want to try PHPxmail ( [https://sourceforge.net/projects/phpxmail](https://sourceforge.net/projects/phpxmail) )

Mark.

---

