---
title: "How can I fix a &quot;mysql&quot; installation mistake?"
date: 2007-01-22
forum: Server Platforms
---

### Post by dvarsam on 2007-01-22
Hello!

I decided to install **mysql-server-5.0**.

But on the Terminal window, I forgot to type:

[color=blue]apt-get install mysql-server-5.0[/color] [color=red]--prefix=/usr/local/mysql[/color]

And instead, I simply typed:

[color=blue]apt-get install mysql-server-5.0[/color]

I forgot to add the "--prefix..." option!

_Questions_:

1. How can I correct this?
2. Where is MySQL currently installed? - i.e. on which directory?

[quote=dvarsam]**The following packages were installed:**

1. libdbd-mysql-perl_3.0006-1_i386.deb
2. libdbi-perl_1.51-2_i386.deb
3. libmysqlclient15off_5.0.24a-9_i386.deb
4. libnet-daemon-perl_0.38-1.1_all.deb
5. libplrpc-perl_0.2017-1.1_all.deb
6. mysql-client-5.0_5.0.24a-9_i386.deb
7. mysql-common_5.0.24a-9_all.deb
8. mysql-server-5.0_5.0.24a-9_i386.deb[/quote]

Please help me fix this...
Thanks.

P.S.> Also, when I try to install "**apache2**", using the following command:

[color=blue]apt-get install apache2 --prefix=/usr/local/apache2 --enable-module=so[/color]

I get the following error:

[color=red]E: Command line option --prefix=/usr/local/apache2 is not understood[/color]

_Question 3_:
What is wrong in this case?

---

### Post by dvarsam on 2007-01-22
Has the "[color=blue]--prefix[/color]" option been dropped...?

And replaced with what option instead?

Thanks.

---

