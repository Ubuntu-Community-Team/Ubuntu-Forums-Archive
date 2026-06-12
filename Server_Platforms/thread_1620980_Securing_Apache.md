---
title: "Securing Apache"
date: 2010-11-13
forum: Server Platforms
---

### Post by trentscott on 2010-11-13
I have a fresh install of Ubuntu Server 10.10 with LAMP and have a few questions on locking down Apache. Note: I'm using this web server to host a personal site, no need to have it open for other people (I'm not a web host).

1. What is the best method for handling permissions on /var/www. Should I chown it to my username or create a group and add myself to it, etc?
2. Are there any vulnerabilities if I connect to my server via port 22 (SFTP) locally (on my network), but port 22 is closed on my router (i.e. external world shouldn't be able to access it)? I don't think there's any issue with this but I might be wrong.
3. I use Subversion to manage the files for my personal website (track changes, etc.) -- should I keep the repo separate from my live copy of my site? If I do that, I'll have to copy all files out of my repo to /var/www to enact a change instead of being able to check it in and have it instantly update. How do people normally do this, is it better practice to keep the repo separate?

Thanks in advance for any help. :)

---

### Post by trentscott on 2010-11-13
Anyone?

---

### Post by SeijiSensei on 2010-11-13
1)  Add yourself to the www-data group.  That's the user and group that the Apache server process runs as.

2)  No.

3)  Maybe use a symbolic link to the repository?  I can tell you without much doubt that most web developers wouldn't know a repository from a suppository.  As for me, I usually maintain two sites: a production site that I try not to touch unless there's a major problem, and a development site that I migrate into production when it's ready.  I don't use CVS/SVN/git for this; I just have multiple top-level directories and symlink to the one that's current.  I obviously also maintain two databases, one for production and one for development.  I just change a couple of entries in a PHP script when I move something in production.

---

### Post by wongo888 on 2010-11-13
If this box will be accessed using a subdomain like ubuntu.example.com then it would probably be better to set up a virtual host for it:

```
$ sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite

$ # Configure your new virtual host
$ vim /etc/apache2/sites-available/mynewsite

$ sudo a2ensite mynewsite
$ sudo /etc/init.d/apache2 restart

```

[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

FWIW, I **do** know what a suppository is although they never mentioned it specifically while I was doing my CS undergrad.

---

### Post by trentscott on 2010-11-14
> **SeijiSensei said:**
> 1)  Add yourself to the www-data group.  That's the user and group that the Apache server process runs as.

2)  No.

3)  Maybe use a symbolic link to the repository?  I can tell you without much doubt that most web developers wouldn't know a repository from a suppository.  As for me, I usually maintain two sites: a production site that I try not to touch unless there's a major problem, and a development site that I migrate into production when it's ready.  I don't use CVS/SVN/git for this; I just have multiple top-level directories and symlink to the one that's current.  I obviously also maintain two databases, one for production and one for development.  I just change a couple of entries in a PHP script when I move something in production.

Great idea with the symlink -- I'll give it a shot.


> **wongo888 said:**
> If this box will be accessed using a subdomain like ubuntu.example.com then it would probably be better to set up a virtual host for it:

```
$ sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite

$ # Configure your new virtual host
$ vim /etc/apache2/sites-available/mynewsite

$ sudo a2ensite mynewsite
$ sudo /etc/init.d/apache2 restart

```

[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

FWIW, I **do** know what a suppository is although they never mentioned it specifically while I was doing my CS undergrad.

Thanks!

---

### Post by James78 on 2010-11-14
For vulnerabilities, bruteforce, dictionary attacks, etc, use fail2ban. Server side, use mod-evasive (libapache2-mod-evasive, which tries to evade DoS attacks), and mod-security2 (libapache-mod-security). I'm not going to go into instructions on how to set these up, but mod-security is tough to figure out, so I'll link you to 2 rulesets to use.

The OWASP Core Ruleset, you can get the latest from SVN here.
[http://mod-security.svn.sourceforge.net/viewvc/mod-security/crs/trunk/](http://mod-security.svn.sourceforge.net/viewvc/mod-security/crs/trunk/)

Atomic Corp free rules
[http://www.atomicorp.com/wiki/index.php/Atomic_ModSecurity_Rules](http://www.atomicorp.com/wiki/index.php/Atomic_ModSecurity_Rules)

I have all these setup on my server, and it blocks all attacks really well. (:

I said I wasn't going to go into specifics, but I went in to many specifics in this thread here, so this will probably help you a TON.
[http://ubuntuforums.org/showthread.php?t=1600727](http://ubuntuforums.org/showthread.php?t=1600727)

---

