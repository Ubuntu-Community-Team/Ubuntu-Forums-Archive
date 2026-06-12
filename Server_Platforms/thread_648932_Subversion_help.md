---
title: "Subversion help"
date: 2007-12-24
forum: Server Platforms
---

### Post by barnjo on 2007-12-24
I'm trying to set up a subversion repository with http access. Its now almost working, but i want to make it so that I can have anonymous read access but require a password for write access.

At the moment my dav_svn.conf file looks like this:

```
# dav_svn.conf - Example Subversion/Apache configuration
#
# For details and further options see the Apache user manual and
# the Subversion book.
#
# NOTE: for a setup with multiple vhosts, you will want to do this
# configuration in /etc/apache2/sites-available/*, not here.

# <Location URL> ... </Location>

#Lots of comments

#</Location>

<Location /svn>
	DAV svn
	SVNParentPath /var/svn

	AuthType Basic
	AuthName "Subversion Repository"
	AuthUserFile /etc/apache2/dav_svn.passwd
	Require valid-user

	<LimitExcept GET PROPFIND OPTIONS REPORT>
		Require valid-user
	</LimitExcept>
</Location>
```

Anyone know whats wrong?

---

### Post by quux on 2007-12-24
Hi,

what you want to do is described in the SVNBook as Example 6.3 in "Per-directory access control" [(Link)]("http://svnbook.red-bean.com/en/1.4/svn.serverconfig.httpd.html#svn.serverconfig.httpd.authz.perdir"). 

For an explanation of the Authz config file format see "Path-based authorization" [(Link)]("http://svnbook.red-bean.com/en/1.4/svn.serverconfig.pathbasedauthz.html"). Note the ```

[/]
* = r
``` for giving read-access to all users.

---

### Post by barnjo on 2007-12-24
I've managed to grant anonymous reading by removing the first instance of Require valid-user in my conf file.

But one things still bugging me, if I point my browser to localhost/svn/repo I get shown the repo fine, if I point my browser to localhost/svn I get a Forbidden message.

I know my svn folder has www-data as the owner

Any help?

---

### Post by barnjo on 2007-12-25
My permssions are still messed up.

If I need write access it first of all asks for my ubuntu usernames password ten aks for a username and password which it checks for in the htpasswd generated file:

```
jonathan-barnes-computer:svnhelp jonny$ svn import myproject http://192.168.2.3/svn/myproject -m "Initial import"
Authentication realm: <http://192.168.2.3:80> Subversion Repository
Password for 'jonny': 
Authentication realm: <http://192.168.2.3:80> Subversion Repository
Username: barnjo
Password for 'barnjo': 
Adding         myproject/trunk
Adding         myproject/trunk/README
Adding         myproject/branches
Adding         myproject/tags

Committed revision 1.
```

Why is it asking for the password for 'jonny'?

---

