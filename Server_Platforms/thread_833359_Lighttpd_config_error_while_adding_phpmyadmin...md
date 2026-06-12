---
title: "Lighttpd config error while adding phpmyadmin.."
date: 2008-06-18
forum: Server Platforms
---

### Post by OoteR on 2008-06-18
Hello all,

I followed this tutorial: [http://stateless.geek.nz/2005/06/27/debian-lighttpd-and-phpmyadmin/](http://stateless.geek.nz/2005/06/27/debian-lighttpd-and-phpmyadmin/)

This is on a debian etch box, but it should still work, the locations all appear to be the same.

and am getting the following error: 
```

/etc/init.d/lighttpd restart
Stopping web server: lighttpd.
Starting web server: lighttpd2008-06-18 14:37:05: (configfile.c.768) source: /etc/lighttpd/lighttpd.conf line: 167 pos: 12 invalid character in variable name 
2008-06-18 14:37:05: (configfile.c.824) configfile parser failed at: ( 
 failed!

```

this is the line it's whining about:
```

...
alias.url = ( "/mysql" => "/usr/share/phpmyadmin/" )

```

I tried using += to no avail.. :/  Anyone have any suggestions? I double checked and phpmyadmin appears to be there.. so I THINK that is the correct settting, but lighttpd doesnt think so..

---

### Post by brambles on 2008-07-06
Just tried this ( copy and paste) and realised that the quotation marks were wrong type. Have other problems with this but will need to wait till morning :)

Ciao M

---

### Post by brambles on 2008-07-07
Have this all ok now. Did sudo dpkg-reconfigure phpmyadmin and chose lighttpd as webserver (previously had apache installed) and bingo! all ok.

I couldn't connect to moodle database either so had to create a simple script in /etc/lighttpd/conf-available and enable using lighty-enable-mod.


cat /etc/lighttpd/conf-available/50-moodle.conf 
alias.url += ( 
	"/moodle" => "/usr/share/moodle",
)

Cheers, M

---

