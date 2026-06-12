---
title: "Wrong shell when logging in via SSH using LDAP/Kerberos"
date: 2012-06-19
forum: Server Platforms
---

### Post by multikaos on 2012-06-19
As the title reads, I'm successfully able to log in via SSH to my LDAP/Kerberos machines. However i get a /bin/sh shell instead of my proffered /bin/bash.

I've been using this guide that I followed very closely:
[http://www.rjsystems.nl/en/2100-d6-kerberos-openldap-provider.php]("http://www.rjsystems.nl/en/2100-d6-kerberos-openldap-provider.php")

If I log in locally, through the console, to one of the machines, I get the bash shell. However, if I try setting the loginShell attribute to something like /bin/laksdjf or even /bin/sh I still get the bash shell.

So it seems like that attribute is completely ignored. Does anyone have a clue why this might be happening?

The machine that runs Kerberos and OpenLDAP uses Debian 6.0.4 (Squeeze), the same version is run on the clients I'm logging in to.

---

### Post by multikaos on 2012-07-20
I'm going to bump this up since i'm still having the same problem.

---

### Post by sudodus on 2012-07-20
Probably the debian server is set to run sh, when you log in via ssh. I don't know where to change that setting, but let us hope that someone who knows will show up :-)

What happens if you start bash at your ssh terminal?

```
bash
```

---

### Post by luvshines on 2012-07-21
How did you setup the LDAP client for ssh ?
From the link you have posted, it explains the setup of KDC with openLdap backend only
You must have also setup some nss_ldap configs too, right ? Some configs in your /etc/ldap.conf file

---

### Post by kennethconn on 2012-07-21
```
However, if I try setting the loginShell attribute to something like
 /bin/laksdjf or even /bin/sh I still get the bash shell.
```
 
What is the loginShell attribute displaying when you do an ldapsearch (for the user you are logging in as)?

---

### Post by multikaos on 2012-07-31
Sorry for not replying earlier, I've been AFK for a while.

sudodus: If i run bash it happily starts. So it's just a matter of what shell is getting run when I log in with ssh.

luvshindes: There's a link to the client side part of that guide further down the page. [here it is]("http://www.rjsystems.nl/en/2100-d6-kerberos-openldap-client.php").
I've followed that guide as well very closely.

kennethconn: The loginShell attribute displays whatever I've set it to. In my example that you are quoting, it's set to /bin/laksdjf. However I see now that I've messed up in the example. I still get sh, not bash.

I still haven't found a way around this so I keep entering bash manually after log in, which is of course not optimal.

---

### Post by luvshines on 2012-07-31
What is the login shell displayed if you do```
getent passwd <ldap-user>
``` on the console

---

### Post by kennethconn on 2012-07-31
Then I would say you are not logging in (via SSH) to the LDAP server, just the local machine (which just happens to be the server that LDAP is installed on).

---

