---
title: "Apache HTTP Digest Authentication Error"
date: 2007-08-27
forum: Server Platforms
---

### Post by techstop on 2007-08-27
Hi there. I am trying to set up Apache to use HTTP Digest authentication to secure my Mythweb folder. I have stumbled at the final hurdle. I have run htdigest to produce a the appropriate file containing the username : password hash. I have added the lines required to the apache configuration file. I have restarted apache. When I access mythweb externally, I am prompted to enter a username and password, and then I get a "500 Internal Server" error. I see this in the logs;

```
[Tue Aug 21 21:58:51 2007] [crit] [client 61.8.105.85] configuration error:  couldn't check user.  No user file?: /
```

Now, I see in the Apache documentation that this is related to the auth_digest module not being authoritative;

[http://httpd.apache.org/docs/1.3/misc/FAQ.html#authauthoritative](http://httpd.apache.org/docs/1.3/misc/FAQ.html#authauthoritative)

```
Just add the appropriate 'XXXAuthoritative yes' line to the configuration.
```

Brilliant. I love how the documentation tells you to add the "appropriate line" to the configuration, but then doesn't tell you what that line is or what file to add it in. Can anyone help me out here?

Cheers...

---

### Post by gamerteck on 2007-08-27
I was just having the same issue. I changed the AuthType to **"Basic"**. It was set to Digest. Below is a sample of my config file.

First I made sure the password was setup correctly for my authfile

```

sudo htpasswd -c ***[FONT="Arial Black"]<path to auth file>[/FONT]*** ***[FONT="Arial Black"]<username>[/FONT]***

```

My sample config file is:
**/etc/apache2/sites-enable/000-default**
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                AuthType        Basic
                AuthName        "Mythtv"
                AuthUserFile    ***[FONT="Arial Black"]<path to auth file>[/FONT]***
                Require user    ***[FONT="Arial Black"]<username>[/FONT]***
                Options FollowSymLinks
                AllowOverride None
                      </Directory>

```

Hope this fixes your issue!

---

### Post by techstop on 2007-08-27
Thanks for the reply, but I'd rather not use Basic Authentication though, not very secure at all...

---

### Post by gamerteck on 2007-08-27
I think I got it. Check the link below.
***[HTML]http://httpd.apache.org/docs/1.3/mod/mod_auth_digest.html[/HTML]***

First I re-created the auth file:
```

htdigest -c ***[FONT="Arial Black"]<path to auth file>[/FONT]*** MythTV ***[FONT="Arial Black"]<username>[/FONT]***


```
New config file; *Digest* enabled:
**/etc/apache2/sites-enable/000-default**
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                AuthType        Digest
                AuthName        "MythTV"
                AuthDigestFile  ***[FONT="Arial Black"]<path to auth file>[/FONT]***
                Options FollowSymLinks
                AllowOverride none
                Require valid-user
         </Directory>
```

Hope this works for you like it did for me.

I wasn't sure what the difference between Basic and Digest authentication was, so I read up on it here:
[http://httpd.apache.org/docs/1.3/howto/auth.html](http://httpd.apache.org/docs/1.3/howto/auth.html)

Basic auth transmits the password, in clear text, whenever data is transmitted. Not just once but every single time. Yikes, that's scary!

---

### Post by techstop on 2007-08-27
OK, I am actually following the guide here;

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-6de54421fa8d540556099304300e2e86a4a5b029](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-6de54421fa8d540556099304300e2e86a4a5b029)

So I have done all the configuration you have listed. My problem is that I get a "500 Internal Server Error" when accessing MythWeb. According to the Apache documentation I gave a link for, it is because there is not an authoritative module enabled. So, I need to make auth_digest authoritative. That is my question. How do I do this?

---

### Post by gamerteck on 2007-08-27
You need to create a sym link in the **/etc/apache2/mods-enabled** directory
```
ln -s  /etc/apache2/mods-available/auth_digest.load /etc/apache2/modsenabled/auth_digest.load 
```

And of course, restart apache.

---

### Post by techstop on 2007-08-27
We seem to be going around in circles here, that is not the problem. The module is already enabled, it is part of the HOWTO I linked to;

```
barney@myth:/etc/apache2/mods-enabled$ ls -l
total 0
lrwxrwxrwx 1 root root 44 2007-08-18 12:39 auth_digest.load -> /etc/apache2/mods-available/auth_digest.load
lrwxrwxrwx 1 root root 36 2006-11-19 17:42 cgi.load -> /etc/apache2/mods-available/cgi.load
lrwxrwxrwx 1 root root 37 2006-11-19 17:42 php4.conf -> /etc/apache2/mods-available/php4.conf
lrwxrwxrwx 1 root root 37 2006-11-19 17:42 php4.load -> /etc/apache2/mods-available/php4.load
lrwxrwxrwx 1 root root 40 2006-11-19 17:42 rewrite.load -> /etc/apache2/mods-available/rewrite.load
lrwxrwxrwx 1 root root 40 2006-11-19 17:42 userdir.conf -> /etc/apache2/mods-available/userdir.conf
lrwxrwxrwx 1 root root 40 2006-11-19 17:42 userdir.load -> /etc/apache2/mods-available/userdir.load
barney@myth:/etc/apache2/mods-enabled$ ls -A -l /etc/apache2/mods-enabled/ | grep auth_digest
lrwxrwxrwx 1 root root 44 2007-08-18 12:39 auth_digest.load -> /etc/apache2/mods-available/auth_digest.load
barney@myth:/etc/apache2/mods-enabled$
```

I am going to post the contents of the Apache FAQ I linked to in the first post for the benefit of the audience...

> **4.  Why does my authentication give me a server error?**

Under normal circumstances, the Apache access control modules will pass unrecognized user IDs on to the next access control module in line. Only if the user ID is recognized and the password is validated (or not) will it give the usual success or "authentication failed" messages.

However, if the last access module in line 'declines' the validation request (because it has never heard of the user ID or because it is not configured), the http_request handler will give one of the following, confusing, errors:

    * check access
    * check user. No user file?
    * check access. No groups file?

This does not mean that you have to add an 'AuthUserFile /dev/null' line as some magazines suggest!

**The solution is to ensure that at least the last module is authoritative and CONFIGURED.** By default, mod_auth is authoritative and will give an OK/Denied, but only if it is configured with the proper AuthUserFile. Likewise, if a valid group is required. (Remember that the modules are processed in the reverse order from that in which they appear in your compile-time Configuration file.)

A typical situation for this error is when you are using the mod_auth_dbm, mod_auth_msql, mod_auth_mysql, mod_auth_anon or mod_auth_cookie modules on their own. These are by default not authoritative, and this will pass the buck on to the (non-existent) next authentication module when the user ID is not in their respective database. **Just add the appropriate 'XXXAuthoritative yes' line to the configuration.**

In general it is a good idea (though not terribly efficient) to have the file-based mod_auth a module of last resort. This allows you to access the web server with a few special passwords even if the databases are down or corrupted. This does cost a file open/seek/close for each request in a protected area.


---

### Post by gamerteck on 2007-08-27
I read that, i understand what you're trying to do and *had* the exact same issue.

**You need to specify that the file is an AuthDigestFile**
Instead of an **AuthUserFile**.

I'm reaching here but I think AuthUserFile is used with Basic auth and AuthDigestFile is used for Digest auth.

You already set the XXXXAuthoritative by stating that the Authype is Digest. The Authoratative, by default, is on.

Why don't you post your config file so we can see what it looks like.

---

### Post by techstop on 2007-08-27
OK, I have set it up to secure all sites, so this is my config in /etc/apache2/sites-enabled/000-default;

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www
	<Directory />
	#	AuthType	Digest
	#	AuthName	"MythTV"
	#	AuthUserFile	/home/barney/htdigest
	#	Require		valid-user	
	#	BrowserMatch	"MSIE"  AuthDigestEnableQueryStringHack=On
		Options FollowSymLinks
		AllowOverride None
	</Directory>

```

Ignore where I have commented out the lines, I only did that to disable authentication so I could use Mythweb again. apache runs as the user:group barney:barney so presumably it can read the htdigest file OK.

EDIT: I just noticed that I haven't set it to AuthDigestFile as you suggested, I will change that and let you know how I go...

---

### Post by techstop on 2007-08-27
Update:

Thanks for your help, I managed to get it working by doing two things;

1. Changing AuthUserFile to AuthDigestFile

2. moving the htdigest file to /etc/apache2/ instead of my home directory (I had read that the password file should not be in the web server directory, so I thought I would put it in the users home directory. The error logs were showing that the file could not be opened, so I moved it)

So, I got there in the end, cheers... :)

I blame a woefully badly written HOWTO for my troubles, it was full of bad information;

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-6de54421fa8d540556099304300e2e86a4a5b029](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-6de54421fa8d540556099304300e2e86a4a5b029)

1. It suggests putting the password file in the web server root directory
2. It says to use AuthUserFile for Digest Authentication

Plus some bad advice from this HOWTO;

[http://www.mythpvr.com/mythtv/mythweb/secure-howto.html](http://www.mythpvr.com/mythtv/mythweb/secure-howto.html)

That said that apache was running under a user account and not root (therefore I put the password file in the wrong directory)

But now it's all good... :guitar:

---

