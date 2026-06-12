---
title: "Can't get cgi scripting to work on a LAMP server"
date: 2009-09-08
forum: Server Platforms
---

### Post by Hacker3141 on 2009-09-08
Hello everyone,
I have been running a LAMP server for a couple weeks now, and I am trying to get cgi scripting to work on it. I have added the "ScriptAlias /cgi-bin/ ..." and such to my configuration, and it still does not work. Also, I am running the desktop version of ubuntu (It is a local server). Thanks in advance for all the help.

---

### Post by Hacker3141 on 2009-09-10
Hello?

---

### Post by X-Rated on 2009-09-10
> **Hacker3141 said:**
> Hello?

Hello lol

When you say it doesn't work, what is displayed when you try to access it via browser?
What does the logs says.

bit more info could be helpfull lol

---

### Post by Hacker3141 on 2009-09-11
When I try to access a script through the browser, it says that the link is broken. When I try to access the cgi-bin folder, it says 403 forbidden, which I guess is a good thing. I don't know where the log files are, so it would be awesome if you could tell me.

---

### Post by X-Rated on 2009-09-11
I think your missing the Directory or Location directive. something like this

> ScriptAlias /cgi-bin/ /path/to/cgi-bin/
<Location /cgi-bin >
             SetHandler cgi-script
      Options +ExecCGI
             
Order allow,deny
            Allow from all
</Location>     Don't forget, I think your scripts may also have to be executable.

[http://httpd.apache.org/docs/2.0/mod/mod_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_alias.html)

The log files are usually located /etc/apache2/logs or /etc/httpd/logs


hth

---

### Post by Hacker3141 on 2009-09-11
That is added to /etc/apache2/sites-available/default right?

---

