---
title: "Help with installing Trac/Svn/Apache"
date: 2011-07-13
forum: Server Platforms
---

### Post by Scrier on 2011-07-13
Hi, 

I have been trying to install this using the following guide [http://trac.edgewall.org/wiki/Ubuntu-11.04-Subversion](http://trac.edgewall.org/wiki/Ubuntu-11.04-Subversion). All goes well until the **Set up trac** under Apache part. Now first of all, never done this before so I assume its understood which file he is talking about. I tried the file under /var/apache2/sites-available/000-default and added the following 2 parts to the end of the file:
> <Location /projects> #set up Trac handling
    SetHandler mod_python
    PythonHandler trac.web.modpython_frontend
    PythonOption TracEnvParentDir /home/<user>/projects/trac
    PythonOption TracUriRoot /projects
</Location>
and
> <Location "/trac/login">
    AuthType Basic
    AuthName "Trac"
    AuthUserFile /home/<user>/projects/trac/.htpasswd
    Require valid-user
</Location>
The next step with *sudo htpasswd -c .htpasswd admin* I did under /home/<user>/projects/trac/.htpasswd.

After a restart here I get an error 500 that I do not have permissions to */home/<user>/projects/trac* when accessing from the web. And here I am lost and begging for help cause I have run out of ideas.

---

