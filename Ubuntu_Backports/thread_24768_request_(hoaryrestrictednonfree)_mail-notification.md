---
title: "request (hoary/restricted:nonfree): mail-notification-1.1"
date: 2005-04-08
forum: Ubuntu Backports
---

### Post by alexp on 2005-04-08
Hello,

I'd like you to add [mail-notification]("http://www.nongnu.org/mailnotify/") *with SSL/TLS support enabled* to the backports repository. Please note that the package itself is already in hoary (universe), but SSL/TLS support has been disabled by the Debian package maintainer due to licensing issues.

Unfortunately, there seems to be no hope that this [issue]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=286672") will ever change, as the developer is unwilling to change the package license to be Debian-compatible, and the debian-legal department is unwilling to use a [not-so-strict interpretation]("http://www.gnome.org/%7Emarkmc/openssl-and-the-gpl.html") of certain parts of the GPL ](*,).

However, without the ability to securely connect to the mail server, this package is rendered useless for most people. As such, I'd like to suggest the following:

One should add the package to backports, slightly changing the package name (eg. adding -nonfree or -ssl to it) and putting a small note into the package description and the README (or README.Debian/Ubuntu/whatever) file which describes the situation and licensing problems which may arise with the installation. I'd happily help with that, but I have no experience with deb packaging (though I could write an ebuild :twisted: for the Gentoo refugees). Still, I'll try to help wherever possible -- just ask.

I know that the developer himself maintains deb packages with SSL/TLS enabled, but installing them via dpkg is a far-from-perfect solution, as the Ubuntu update-manager almost immediately complains about available updates for the package.

Regards,
Alexander Papaspyrou

---

### Post by nocturn on 2005-04-08
[QUOTE=alexp]Hello,

I'd like you to add [mail-notification]("http://www.nongnu.org/mailnotify/") *with SSL/TLS support enabled* to the backports repository. Please note that the package itself is already in hoary (universe), but SSL/TLS support has been disabled by the Debian package maintainer due to licensing issues.

Unfortunately, there seems to be no hope that this [issue]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=286672") will ever change, as the developer is unwilling to change the package license to be Debian-compatible, and the debian-legal department is unwilling to use a [not-so-strict interpretation]("http://www.gnome.org/%7Emarkmc/openssl-and-the-gpl.html") of certain parts of the GPL ](*,).

However, without the ability to securely connect to the mail server, this package is rendered useless for most people. As such, I'd like to suggest the following:

One should add the package to backports, slightly changing the package name (eg. adding -nonfree or -ssl to it) and putting a small note into the package description and the README (or README.Debian/Ubuntu/whatever) file which describes the situation and licensing problems which may arise with the installation. I'd happily help with that, but I have no experience with deb packaging (though I could write an ebuild :twisted: for the Gentoo refugees). Still, I'll try to help wherever possible -- just ask.

I know that the developer himself maintains deb packages with SSL/TLS enabled, but installing them via dpkg is a far-from-perfect solution, as the Ubuntu update-manager almost immediately complains about available updates for the package.

Regards,
Alexander Papaspyrou[/QUOTE]


Debian legal can be insane about such things...
I read the clauses and the reply of the mail-notification author, there is no problem whatsoever with enabling SSL in it since it neither incorporates nor redistributes OpenSSL, it links against it.

---

### Post by alexp on 2005-04-08
nocturn,

> I read the clauses and the reply of the mail-notification author, there is no problem whatsoever with enabling SSL in it since it neither incorporates nor redistributes OpenSSL, it links against it. 

Well, I don't see the problem either -- especially since openssl ***already is*** part of Ubuntu. Alas, the debian package maintainer does not seem to share our opinion; and as hoary (universe) seems to use the debian vanilla deb, this won't ever change.

Regards,
Alexander

---

### Post by KillerKiwi on 2005-07-31
Found a deb

[http://kitalpha.homelinux.net/debian/mail-notification-ssl_1.1-4_i386.deb](http://kitalpha.homelinux.net/debian/mail-notification-ssl_1.1-4_i386.deb)

---

