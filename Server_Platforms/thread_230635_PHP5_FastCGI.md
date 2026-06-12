---
title: "PHP5 FastCGI"
date: 2006-08-06
forum: Server Platforms
---

### Post by andrewheard on 2006-08-06
Hi,
I just need to know if the php5-cgi binary supports FastCGI. I know that php4-cgi does but its not mentioned in the php5-cgi description.

Thanks,

Andrew

---

### Post by JoachimDurchholz on 2007-01-18
On Dapper Drake, yes that's the case.

You can test it on your machine with php5-cgi -v; if it says (cgi-fcgi) on the first line, it's FastCgi-enabled.
If it says (cli), it's a command-line version that won't work from any variant of CGI.
If it says (cgi), it will work from CGI but not as FastCgi.
For completeness, there's a fourth version of PHP that is named mod_php (or mod_php4 or libapache_mod_php4), which would say something like (module API) if it were callable from the command line.
Usually, Debian-based distributions will give you cgi-fcgi, cli, and mod_php as alternatives; bare cgi isn't very popular (nor very useful, the cgi-fcgi variant is a superset and doesn't carry disadvantages).

Regards,
Jo

---

### Post by valeriupalos on 2008-05-04
Thanks, that was very useful! :)

---

