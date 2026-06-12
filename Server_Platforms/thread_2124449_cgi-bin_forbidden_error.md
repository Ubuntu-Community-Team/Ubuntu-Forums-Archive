---
title: "cgi-bin forbidden error"
date: 2013-03-11
forum: Server Platforms
---

### Post by ade234uk on 2013-03-11
I installed apache2 and perl. Perl seems to be working correctly. 

I created a basic index.pl file, put the file in the cgi-bin and when I visit **[http://localhost/cgi-bin/index.pl](http://localhost/cgi-bin/index.pl)** the webpage is displayed correctly.

However when I goto **[http://localhost/cgi-bin/](http://localhost/cgi-bin/)** I get the forbidden error. You don't have permission to access /cgi-bin/ on this server.

Any ideas how I can solve this issue. 

Checked the apache error.log file and I have the following error message
[Mon Mar 11 05:37:26 2013] [error] [client 127.0.0.1] attempt to invoke directory as script: /home/user1/www/cgi-bin/

---

### Post by ade234uk on 2013-03-11
The problem is not solved. It was suggested to remove the **ScriptAlias /cgi-bin/ /home/user1/www/cgi-bin/ **from the apache default file which I did.

This stopped the 403 forbidden error, however when I ran the perl script it printed the source code in the browser instead of executing the code.

I am back to my original question. How do I get rid of the 403 forbidden error when I access **[http://localhost/cgi-bin/](http://localhost/cgi-bin/)**

---

### Post by ade234uk on 2013-03-11
I have resolved the issue, at last.

---

