---
title: "Kolab Webadmin: Could not bind to LDAP server: Invalid Credentials"
date: 2009-07-11
forum: Server Platforms
---

### Post by gkaragoulis on 2009-07-11
Hello everyone,

I just installed Kolab server on Ubuntu Jaunty from apt-get, and i followed the steps and ran kolab_bootstrap -b and all that but when I go to the web administration interface I get a login screen with this error on it:

```
Could not bind to LDAP server: Invalid Credentials
```

I checked my syslog and I get this output (my domain is kara.home):

```
Jul 11 01:34:05 server kolabd: L Error: Unable to bind to `cn=manager,cn=internal,dc=kara,dc=home', LDAP Error = `Invalid credentials'
Jul 11 01:34:10 server kolabd: L Error: Unable to bind to `cn=manager,cn=internal,dc=kara,dc=home', LDAP Error = `Invalid credentials'
```

From the research I've done so far, I'm guessing this is because my LDAP server is not set up correctly with the kolab schema, but that's about all I can guess.

Does anybody out there know why this happens or is willing to help me troubleshoot this?  Help is appreciated; I'll be working on this all weekend if I have to.

---

### Post by tmcastberg on 2009-11-19
Partly resolved. Authentication errors were for me that I had not started saslauthd.

I am still getting "Could not bind to LDAP server: Invalid Credentials" in the Kolab-webadmin interface, however I don't have any errors in any logfile.


-----

Have you found any resolution to this?

I'm seeing exactly the same problem in kolab webadmin and the following in syslog

```

Nov 19 16:13:36 taurus kolabd[29716]: Kolab is starting up
Nov 19 16:13:36 taurus cyrus/master[29720]: about to exec /usr/lib/cyrus/bin/imapd
Nov 19 16:13:36 taurus cyrus/imap[29720]: executed
Nov 19 16:13:36 taurus cyrus/imap[29720]: accepted connection
Nov 19 16:13:36 taurus cyrus/imap[29720]: badlogin: localhost [127.0.0.1] plaintext manager SASL(-1): generic failure: checkpass failed
Nov 19 16:13:39 taurus kolabd[29716]: Y Error: Unable to authenticate with Cyrus admin interface, Error = `'
Nov 19 16:14:39 taurus cyrus/master[29698]: process 29720 exited, status 0

```

I've installed Karmic amd64 server. I can't understand how this package can have passed any quality control...

---

### Post by tmcastberg on 2009-11-19
The error with kolab-webadmin was that /etc/kolab/session_vars.php was not configured. I took the values from kolab.conf and problem was sorted.

---

### Post by spikyjt on 2009-11-19
In my experience, the kolab packages are broken, but installing the OpenPKG system as per kolab recommendation, on an Ubuntu server, results in a very stable and easy to configure system.

---

### Post by tmcastberg on 2009-11-20
I was thinking about that but like with zimbra it annoys me to have packages that conflict with system packages. I'd rather that the mail/ldap/apache/imap packages are under package management, especially since there can be dependency issues without some packages (and I don't want to manually disable them).

---

### Post by blknite on 2010-07-26
I have been struggling with Kolab configuration for a few days now (getting close thanks to great posts like this.  I want to thank all of you who post useful ideas and information. I new to Kolab and you are cutting days off my configuration.

Cheers :popcorn:

---

### Post by DiaBase on 2011-01-08
I see the same kind of "L" errors listed by **gkaragoulis **thousands of times in many of my server logs.  Based on this thread and other inquiries elsewhere on the net there it appears that the Kolab Webadmin package has been neglected for years and is the only taking up repository space while providing frustration to Ubuntu users.   

I appreciate **spikyjt**&#8217;s suggestion and will try installing Kolab using the OpenPKG system.  I&#8217;d previously resisted this approach because I wanted to have the advantage of being able to keep my system updated using the Ubuntu repository.   I even went so far as to reinstall a fresh copy of Ubuntu three times as I tried different fixes for all the problems with this package.  I believe that it would be helpful if the Kolab Webadmin repository packages were just removed if they are not going to be maintained.

---

