---
title: "Subversion help"
date: 2005-02-17
forum: Server Platforms
---

### Post by alexmcmorris on 2005-02-17
Greetings,

First of all, I am a complete newbie--This is my first real Linux install.  Anyway, I need some help getting my machine set up to serve a subversion repository.

I read the wiki but it doesn't seem to be up to date.  I fail right off the bat with:
apt-get install libapache2-svn
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package libapache2-svn

I do have subversion and apache2 installed and I found something somewhere on the web about modifying some inetd stuff (remember I'm a newb so I don't know what any of that junk I did was... nor do I remember exactly what I changed but if I come across it in my travels I will rip it out)  Then I tried running svnserve in daemon mode but it said the port was already in use so I assume some of the inetd stuff did something... just not everything.

So I need some guidance for setting up a subversion server... and how that ties into apache... and what the network configuration files are... but that's a huge one so if you can just point me to some good basic general linux information for that I would be most appreciative!

Thanks a ton!
Alex

---

### Post by randy on 2005-02-21
If you are new at this your probably better off setting subversion up to run over ssh.  It's much easier to setup.  All you have to do is make a short script to start subversion at bootup, if your not using xinetd.

---

### Post by alexmcmorris on 2005-02-24
Is that just running it in daemon mode?  I can put that in a start up script or whatever but it still whines that the port is already bound.  I'll go and pull it out of the inetd stuff and see if that clears up the port.

I've noticed quite a few differences between Ubuntus general file system organization than most other distros.  Now I'm trying to get Apache PHP MySQL and Mediawiki running.  Apache was a no brainer and I've installed PHP but when I try to configure stuff I can't find the config files... I still have no idea where PHP is in the Ubuntu world :(

I guess I'll look around here for some more specific information I'm getting all of my frustration from the Apache and PHP mainsites.

Thanks

---

### Post by deuce868 on 2005-02-25
Ubuntu is like debian. The file system is the same. 

For apache:
/etc/apache/httpd.conf

web root is /var/www

PHP4
/etc/php4/apache/php.ini

make sure you install the package php4-mysql if you install mysql-server

As for subversion, make sure you kill all instances before trying to restart it with a script.

---

### Post by alexj on 2005-05-01
I am running SVN under Ubuntu 5.04. I have done it in 3 steps:

1) getting everything Subversion through Synaptic (se apache2 status by looking at localhost, make sure it has SVN)
2) creating subversion repository svnadmin - create <path>, see Subversion Book Administration -> creating repository
3) editing apache2.conf (NOT httpd.conf), as described in Subversion Book, restarting apache2

will post details if that is not enough

---

### Post by fng on 2005-05-23
more details please :)

---

### Post by LordHunter317 on 2005-05-23
[QUOTE=alexmcmorris]I read the wiki but it doesn't seem to be up to date.  I fail right off the bat with:
apt-get install libapache2-svn
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package libapache2-svn[/quote]I believe this package is in universe, so you'll have to enable that repository.

[quote=randy] If you are new at this your probably better off setting subversion up to run over ssh. It's much easier to setup. All you have to do is make a short script to start subversion at bootup, if your not using xinetd.[/quote]You don't need to run a subversion server to use svn+ssh.

---

### Post by Flannel on 2005-06-21
Hi guys, I've been trying to set up subversion to work with Apache2 for a little bit now, done a moderate amount of research, and finally got fed up with whatever changes I had made, and decided to start from scratch again.  So I uninstalled and reinstalled to get fresh config files and such (just subversion and the apache module).

I used apt to get the things specified (libapache2-svn, and then subversion itself), and have only thus far created a repository (/var/devel/svn because it seemed right, although I have no idea how 'proper' that path is, can't seem to find an explanation of what stuff goes where, but that's not really important) and have changed one config file: /etc/apache2/mods-enabled/dav_svn.conf.  I changed it the way the file instructs you to, and am getting this error in my apache log:
> [Tue Jun 21 20:08:13 2005] [error] [client 192.168.1.100] (20014)Error string not specified yet: Can't open file '/var/devel/svn/format': Permission denied
[Tue Jun 21 20:08:13 2005] [error] [client 192.168.1.100] Could not fetch resource information.  [500, #0]
[Tue Jun 21 20:08:13 2005] [error] [client 192.168.1.100] Could not open the requested SVN filesystem  [500, #13]
[Tue Jun 21 20:08:13 2005] [error] [client 192.168.1.100] Could not open the requested SVN filesystem  [500, #13] 
I've gotten to the point where my svn repository is owned by nobody:nogroup, and I disabled all forms of authentication (as you'll see), but I still get that exact same error.  Any help (and other guidance, such as who that repository should be owned by, and all that other fun stuff) would be much appreciated.

And just since more information is never a bad thing, here is my dav_svn.conf file:
> # dav_svn.conf - Example Subversion/Apache configuration
#
# For details and further options see the Apache user manual.

# <Location URL> ... </Location>
# URL controls how the repository appears to the outside world.
# In this example clients access the repository as [http://hostname/svn/repos](http://hostname/svn/repos)
<Location /svn>

  # uncomment this to enable the repository
   DAV svn

  # set this to the path to your repository
   SVNPath /var/devel/svn

  # The following allows for basic http authentication.  Basic authentication
  # should not be considered secure for any particularly rigorous definition of
  # secure.

  # to create a passwd file
  # # rm -f /etc/apache2/dav_svn.passwd 
  # # htpasswd2 -c /etc/apache2/dav_svn.passwd dwhedon
  # New password: 
  # Re-type new password: 
  # Adding password for user dwhedon
  # #

  # Uncomment the following 3 lines to enable Basic Authentication
  # AuthType Basic
  # AuthName "Subversion Repository"
  # AuthUserFile /etc/apache2/dav_svn.passwd

  # Uncomment the following line to enable Authz Authentication
  # AuthzSVNAccessFile /etc/apache2/dav_svn.authz

  # Uncomment the following three lines allow anonymous read, but make
  # committers authenticate themselves

  # <LimitExcept GET PROPFIND OPTIONS REPORT>
  #  Require valid-user
  # </LimitExcept> 

</Location>

---

### Post by deuce868 on 2005-06-22
You svn repository needs to be writable by the web user which is www-data. Change the ownership on that directory like so:

chown -R www-data:www-data /var/devel/svn

---

### Post by Flannel on 2005-06-22
It already was.  The guys over at #svn are stumped, but are pretty sure it has something to do with SELinux, offering me this link.
[http://subversion.tigris.org/faq.html#reposperms](http://subversion.tigris.org/faq.html#reposperms).

Of course, Ubuntu doesnt have a chcon command, and I couldn't come up with any useful documentation regarding security context.

I have a generic Ubuntu installation, but I did find that I had libselinux1 installed.  I don't know if that qualifies at SELinux being implemented, or if thats just for some programs to use.

Thanks again.

---

### Post by sundancer on 2005-07-05
subversion works here...
Here are my settings:

```

# /etc/apache2/sites-enabled/default
<Location /svn>
                AuthType basic
                AuthName "SVN :: LDAP Login"
                AuthLDAPURL ldap://localhost/ou=people,BLANKED
                <LimitExcept GET PROPFIND OPTIONS REPORT>
                        Require valid-user
                </LimitExcept>
</Location>

```

```

# /etc/apache2/mods-enabled/dav_svn.conf
<Location /svn>
  # Uncomment this to enable the repository,
  DAV svn
  # Set this to the path to your repository
  SVNParentPath /var/lib/svn
</Location>

```

```

# Load mod_dav_svn when apache starts
LoadModule dav_svn_module /usr/lib/apache2/modules/mod_dav_svn.so
LoadModule authz_svn_module /usr/lib/apache2/modules/mod_authz_svn.so

```

Then I created repositories under /var/lib/svn using the following command:
```

su www-data -c svnadmin create testrepo

```

Everythings working right.

---

