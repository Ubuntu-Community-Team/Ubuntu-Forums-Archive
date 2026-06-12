---
title: "Apache PHP5 doesn't work after forum troubleshooting"
date: 2011-02-15
forum: Server Platforms
---

### Post by Rhett Allen on 2011-02-15
Trying to run a php script from my var/www/ folder in firefox prompts to open the file.

I found many troubleshooting threads with no success.

I used the Ubuntu Software Center to install 
*Apache2
*PHP5
*libapache2-mod-php5

"sudo a2enmod php5"

open var/www/index.html = "It Works!"

"sudo /etc/init.d/apache2 restart" = "[OK]"

"sudo chmod ugo+rwx /var/www"

create test.php in /var/www "<?php phpinfo(); ?>"

Firefox>Tools>ClearRecentHistory>Cache

open var/www/test.php = open file prompt

???

Troubleshooting:

"sudo a2enmod php5" = "already enabled"

"ls /etc/apache2/mods-enabled/" = 
alias.conf            authz_user.load  dir.load          php5.load
alias.load            autoindex.conf   env.load          reqtimeout.conf
auth_basic.load       autoindex.load   mime.conf         reqtimeout.load
authn_file.load       cgi.load         mime.load         setenvif.conf
authz_default.load    deflate.conf     negotiation.conf  setenvif.load
authz_groupfile.load  deflate.load     negotiation.load  status.conf
authz_host.load       dir.conf         php5.conf         status.load

restart computer


Am I missing something?

---

### Post by James78 on 2011-02-15
"open var/www/test.php = open file prompt"

Opening the file directly? Ya, that's not going to work. If Apache indeed is supposed to parse PHP pages (and it is), then opening the file in your browser is only asking your browser to parse the page, which is fine for HTML, but not server side PHP. You're essentially installing Apache for a server, then not using it to serve the pages.

Go to "localhost/test.php" in your browser to see the PHP page.

Now, when you said 'open var/www/index.html = "It Works!"', if you actually meant that's where the file was being served from (because your DocRoot is /var/www), and you were going to "localhost" in your browser, then we have a whole other problem to deal with.

---

### Post by Rhett Allen on 2011-02-15
Ouch. My pride.

Thank you for taking the time to answer.

I suppose I had a system set up on my other computer and had long forgotten such fundamental details.

Oh well; as is my life with programming.

---

### Post by James78 on 2011-02-15
It's alright, we all make mistakes once in awhile. ;) Glad it's solved.

---

