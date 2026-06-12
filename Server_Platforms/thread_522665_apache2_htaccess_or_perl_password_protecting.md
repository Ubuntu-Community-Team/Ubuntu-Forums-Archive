---
title: "apache2 htaccess or perl password protecting"
date: 2007-08-10
forum: Server Platforms
---

### Post by rbprogrammer on 2007-08-10
which is the better way to password protect a directory in the [FONT="Courier New"]cgi-bin[/FONT]? should i use apache2's .htaccess or just create like a perl module and load it in every script that i would want protection.

i have a directory in the [FONT="Courier New"]cgi-bin[/FONT] called [FONT="Courier New"]administration[/FONT], and i want everything in there password protected; no matter how many subfolders and files stem from that folder, i want it protected.

whats to best way of doing this?

---

### Post by kidders on 2007-08-12
Hi there,

> **rbprogrammer said:**
> whats to best way of doing this?I suppose the *best* way is a way that doesn't require you to tweak each and every one of your files & directories, to have the password protection work. Two possibilities occur to me, off the top of my head...

**.htaccess**
This is nice, because it's well-documented, straightforward, and works with certain apache modules that can integrate its authentication schemes with other things on your system.

[B]mod_rewrite
[/B]Sometimes it's nice to have the added flexibility of involving your own scripts in the authentication process. (Hopefully, my little ASCII diagram looks okay on your end!) If you were to use mod_rewrite to force any request below cgi-bin/administration to go through index.cgi, you could do just that.

You would rewrite requests like cgi-bin/administration/script1.cgi to cgi-bin/administration/index.cgi/script1.cgi.


[FONT=Courier New][SIZE=1][COLOR=DarkRed]/var/www/htdocs/[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=DarkRed]www.myhost.com[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=1][/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=1][COLOR=DarkRed] |[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=1][COLOR=DarkRed]      +-cgi-bin[/COLOR][/SIZE][/FONT]
[/INDENT][FONT=Courier New][SIZE=1][/SIZE][/FONT][INDENT][INDENT][FONT=Courier New][SIZE=1][COLOR=DarkRed]     |[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=1][/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=DarkRed]     +-administration[/COLOR][/SIZE][/FONT]
[/INDENT][/INDENT][FONT=Courier New][SIZE=1][/SIZE][/FONT][INDENT][INDENT][INDENT][FONT=Courier New][SIZE=1][COLOR=DarkRed]     |[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=1][/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=DarkRed]+-***index.cgi***[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=1][/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=DarkRed]+-script1.cgi[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=1][/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=DarkRed]+-subdir[/COLOR][/SIZE][/FONT]
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT][INDENT][FONT=Courier New][SIZE=1][/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=DarkRed]     |[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=1][/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=DarkRed]+-script2.cgi[/COLOR][/SIZE][/FONT]
[/INDENT][/INDENT][/INDENT][/INDENT][FONT=Courier New][SIZE=1][/SIZE]
[/FONT]

Either option would allow new scripts added below cgi-bin/administration to become password-protected, simply by being there, rather than having to be altered to protect themselves, if you know what I mean.

---

