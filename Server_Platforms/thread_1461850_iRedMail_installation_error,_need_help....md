---
title: "iRedMail installation error, need help..."
date: 2010-04-24
forum: Server Platforms
---

### Post by s3w47m88 on 2010-04-24
Heya,
     So I'm installing and configuring my first server using RackSpace CloudServers running Ubuntu Karmic Koala (9.10) and I'm now installing iRedMail. The installation runs successfully until I recieve this error:

```
The following packages have unmet dependencies:
  mysql-server-5.0: Depends: mysql-server-core-5.0 (>= 5.1.30really5.0.83-0ubuntu3) but it is not going to be installed
E: Broken packages
< ERROR > Installation failed, please check the terminal output.
```

I understand this is telling me there is some software that iRedMail (or something iRedMail is dependant upon) that needs installed. Is this correct? And if so, what is i needing installed and how do I do that (aptitude install *example-package*?)?

Thanks!

---

### Post by windependence on 2010-04-24
```
sudo apt-get update
sudo apt-get install mysql-server-5.0 mysql-server-core-5.0
```

Before you do that though, you may want to read up on the install instructions to see what other dependencies will be needed and you can install them all at once before you start the iRedMail install again.

-Tim

---

### Post by s3w47m88 on 2010-04-24
Hey Tim,
      Thanks for the reply, so I'm not sure what to be looking for regarding "reading up". Can you enlighten me?

      I ran the install you posted and here's the result I got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mysql-server-5.0: Depends: mysql-client-5.0 (>= 5.1.30really5.0.83-0ubuntu3) but it is not going to be installed
E: Broken packages
```

---

### Post by windependence on 2010-04-24
Did you do the update first?

Try the install this way:

```
sudo apt-get install mysql-server
```

And let apt resolve the dependencies.


-Tim

---

### Post by windependence on 2010-04-24
Here is some additional help:

[http://cloudservers.mosso.com/index.php/Ubuntu_9.04_-_iRedMail_Installation](http://cloudservers.mosso.com/index.php/Ubuntu_9.04_-_iRedMail_Installation)

[http://code.google.com/p/iredmail/wiki/Installation_on_Ubuntu](http://code.google.com/p/iredmail/wiki/Installation_on_Ubuntu)

[http://www.howtoforge.com/iredmail-mail-server-with-ldap-postfix-roundcube-squirrelmail-dovecot-clamav-spamassassin-amavisd-ubuntu-8.04](http://www.howtoforge.com/iredmail-mail-server-with-ldap-postfix-roundcube-squirrelmail-dovecot-clamav-spamassassin-amavisd-ubuntu-8.04)

Hope this helps.

-Tim

---

