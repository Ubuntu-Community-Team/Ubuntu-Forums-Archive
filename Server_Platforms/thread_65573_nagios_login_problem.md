---
title: "nagios login problem"
date: 2005-09-14
forum: Server Platforms
---

### Post by oly on 2005-09-14
hi, having problems setting up nagios i have installed it on a server at school, which has apache2 i can get to the secure login page, but it does not accept the username and password.

the username being nagiosadmin, and password being one i chose during install.

i have tryed reinstalling as well but to no avail, can anyone suggest some possible causes, i am trying to access it on the localhost machine.

---

### Post by John.Michael.Kane on 2005-09-18
I hope this helps you.. 

[http://www.bynkii.com/networking/archives/2004/10/installing_and.html](http://www.bynkii.com/networking/archives/2004/10/installing_and.html)
[http://nagios.sourceforge.net/docs/1_0/installweb.html](http://nagios.sourceforge.net/docs/1_0/installweb.html)

---

### Post by oly on 2005-09-19
thanks for the links, i tried adding this to apache.conf (using apache2)

ScriptAlias /usr/lib/cgi-bin/nagios/ /usr/sbin/
<Directory "/usr/sbin/">
    AllowOverride AuthConfig
    Options ExecCGI
    Order allow,deny
    Allow from all
</Directory>

Alias /etc/nagios/ /usr/lib/nagios/
<Directory "/usr/lib/nagios/">
    Options None
    AllowOverride AuthConfig
    Order allow,deny
    Allow from all
</Directory>

how ever this seems to make little difference and is likely wrong, the paths in the ubuntu version of nagios are all very different i have tried to correct them the best i can but am going on guess work mainly so could be wrong.

like i am unsure what the cgi-bin folder is, i have guessed /usr/lib/cgi-bin/nagios/
i am also unsure where /usr/local/nagios/share maps to ?

can any one help or perhaps post the relevant config for ubuntu ?

---

### Post by cypherphreak on 2006-11-28
I know this post is over a year old but thought I would post a resolution for the people still having problems. If anyone had any problems they should run 

htpasswd -c /etc/nagios2/htpasswd.users nagiosadmin

---

### Post by geep on 2007-01-24
FYI

make sure the virtual host settings are correct


example:

        Options ExecCGI

        AllowOverride AuthConfig
        Order Allow,Deny
        Allow From All

        AuthName "Nagios Access"
        AuthType Basic
        AuthUserFile /etc/nagios/htpasswd.users
        Require valide-user


htpasswd /etc/nagios/htpasswd.users nagiosadmin

when you go to the virtual host you should get a prompt to enter a username / password 

if you still have problems with nagios itself check cgi right in the cgi.cfg file


hope it helps

---

