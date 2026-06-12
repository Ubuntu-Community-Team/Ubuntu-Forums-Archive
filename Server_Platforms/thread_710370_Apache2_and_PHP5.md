---
title: "Apache2 and PHP5"
date: 2008-02-28
forum: Server Platforms
---

### Post by callgary on 2008-02-28
PHP Scripts run from the /var/www folder run OK.  Scripts placed in the /usr/lib/cgi-bin folder generate an Internal Server Error.  script ended prematurely......

Should I relocate my cgi-bin folder to the www folder??  If so how??

How should the cgi-bin folder be setup and used??

Thanks
Gary

---

### Post by faulkes on 2008-02-28
> **callgary said:**
> PHP Scripts run from the /var/www folder run OK.  Scripts placed in the /usr/lib/cgi-bin folder generate an Internal Server Error.  script ended prematurely......

Should I relocate my cgi-bin folder to the www folder??  If so how??

How should the cgi-bin folder be setup and used??

Thanks
Gary

the cgi-bin directory is specifically setup for varies types of content
via the AddHandler directive.  Typically these are files that end in .cgi

If you want to run .php files in /cgi-bin you need to edit /etc/apache2/apach2.conf

```

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi
    AddHandller cgi-script .php

    #
    # For files that include their own HTTP headers:
    #
    AddHandler send-as-is asis

```

IIRC that is the proper way to do it, although I have to ask why you wish
to keep your php files outside of /var/www

Faulkes

---

### Post by callgary on 2008-02-28
dear Faulkes

The textbook example I was following had me put the script there.  It is a basic lesson on PHP.  All the other lessons had me put the scripts and the html page that called it in folders under /var/www

I just wanted to understand more about the cgi-bin folder and how it is configured and used.

My ubuntu server hosts my web page and I want to include PHP scripting as one of the skills I become proficient in.

thanks for the help

---

### Post by callgary on 2008-02-28
PS Hey Faulkes

Is there two Ls in "AddHandller cgi-script .php" in your post???

Gary

---

### Post by callgary on 2008-02-28
I made the change you suggested only with one L
"AddHandler cgi-script .php"

No help.  I still get Error 500 Internat Server Error.

I will run all my scripts in the WWW folder structure

---

### Post by callgary on 2008-02-28
Bad news the change killed the scripts that were running OK in www.

It said 403 forbidden.  You don't have permission to run scripts on this server.

I backed out the change and scripts in the www folders are back working

You showed me what NOT!!! to do.

Thanks
Gary

---

### Post by faulkes on 2008-02-28
> **callgary said:**
> Bad news the change killed the scripts that were running OK in www.

It said 403 forbidden.  You don't have permission to run scripts on this server.

I backed out the change and scripts in the www folders are back working

You showed me what NOT!!! to do.

Thanks
Gary

Interesting.

Yes, I did make a typo there with the two l's however.

403 forbidden, well, I'm not one to shy away from admitting I might have
been wrong in what I suggested.

However, as for the textbook (which I don't know which one), experience 
from coding PHP for quite awhile, most people and most installs of php files
reside in /var/www (or /var/www/sitename if its a virtual host, etc..)

Faulkes

---

### Post by rapiscan on 2008-02-28
CGI (Common Gateway Interface) is a standard that allows outside applications to communicate with your webserver (apache).  In this case, the external application that you want to interface with is PHP.  However, you don't have PHP setup to run as CGI with Apache, you have the PHP module installed.  When PHP is a module, you can think of it as being embedded into apache, which is different than CGI.

In case anyone is interested in running PHP as CGI, here is some more info: [http://us.php.net/security.cgi-bin](http://us.php.net/security.cgi-bin)

---

