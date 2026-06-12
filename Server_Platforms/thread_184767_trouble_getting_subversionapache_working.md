---
title: "trouble getting subversion/apache working"
date: 2006-05-30
forum: Server Platforms
---

### Post by deuce868 on 2006-05-30
I am trying to follow this:
[http://www.phpcult.com/docs/index.php/Configuring_Apache_2_and_Subversion](http://www.phpcult.com/docs/index.php/Configuring_Apache_2_and_Subversion)

to get a working setup of Subversion with Apache. I've setup Subversion before with svnserver, but thought I would try to go the apache route to play with. 

I have setup the /home/svn with the etc folder and an initial project in the /home/svn called aliasmanager.

> 
# ls /home/svn
aliasmanager  etc

#ls /home/svn/etc
group  passwd  svnpasswd


My virtual host looks like this:
> 
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName deuce868.homelinux.com
        DocumentRoot /var/www/
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        <Location /dev>
                DAV svn
                SVNParentPath /home/svn/
                #The ACL file for individual projects in svn.
                AuthzSVNAccessFile /home/svn/etc/svnpasswd
                Satisfy Any
                Require valid-user
                AuthType basic
                AuthName "Linux powered"
                #Authentication file for SVN (create/modify using htpasswd)
                AuthUserFile /home/svn/etc/passwd
                AuthGroupFile /home/svn/etc/group
        </Location>
</VirtualHost>


Ok, now onto the problem. (old problem solved so now a new one)
When someone just uses the url /dev it gives them an access denied instead of a list of subversion repos that are in that directory. Is there any way to list those repos that are available to them instead?

---

### Post by hdpc on 2006-06-28
I am getting Access Forbidden.  Error 403.

---

