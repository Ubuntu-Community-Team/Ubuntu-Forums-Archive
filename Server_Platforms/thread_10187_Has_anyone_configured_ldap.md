---
title: "Has anyone configured ldap"
date: 2005-01-05
forum: Server Platforms
---

### Post by wcarty on 2005-01-05
Has anyone successfully configured ldap on ubuntu linux. I'm looking for some good documentation on how to configure ldap so I can use centralized logins.

---

### Post by jdodson on 2005-01-05
[QUOTE=wcarty]Has anyone successfully configured ldap on ubuntu linux. I'm looking for some good documentation on how to configure ldap so I can use centralized logins.[/QUOTE]

hope this helps:

[http://www.openldap.org/doc/admin22/](http://www.openldap.org/doc/admin22/)

[http://www.openldap.org/doc/admin/quickstart.html](http://www.openldap.org/doc/admin/quickstart.html)

nice web way to admin an ldap server(make sure to secure it) - [http://www.phpldapadmin.com/](http://www.phpldapadmin.com/)

nice way to explore ldap stuff via a java app(i actually used this it is nice, not as an admin, as a ldap script writer to navigate over the trees) - [http://jxplorer.org/](http://jxplorer.org/)

google and sourceforge are your friends :mrgreen:

---

### Post by goedson on 2005-01-06
[QUOTE=wcarty]Has anyone successfully configured ldap on ubuntu linux. I'm looking for some good documentation on how to configure ldap so I can use centralized logins.[/QUOTE]

Maybe this can help you:

[http://people.debian.org/~torsten/ldapnss.html](http://people.debian.org/~torsten/ldapnss.html) 

I've used it to configure an LDAP server in Debian Sarge.

---

### Post by wcarty on 2005-01-06
Thanks Guys. I was able to get the ldap server up and running in no time. :D

---

### Post by unixnorks on 2005-11-10
I followed all the steps given in the links provided and .......

After i type ./configure 
an error occurred...

configure: error: BDB/HDB: BerkeleyDB not available

Hope anyone can give me some idea what im going to do... I congrats ***wcarty*** for have been successfully run the ldap... :cool: 


Any help is highly appreciated..

---

### Post by unixnorks on 2005-11-11
oh well, i solved my first problem now...

the first thing i did was: cd /etc/apt/
and then ~~> vi sources.list

#deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
#deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-updates main restricted

then i uncomment them all...

and on the root login terminal i executed this command...

$:\apt-get update
$:\apt-get upgrade


then i went back to the synaptic package manager and i install the libdb4.1++-dev.. and yes i successfully installed now my openLDAP

but still doesnt help me meet the answer to my problem :(:( 

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$


I would like to ask to anyone if those people loging on the client side will be authenticated through the server and how can i configure that way? 

For now I used my localhost as my server and i want to test by adding a new user to my server(slapd) How to do that?... And also I want to check if I can log-on to my PC using those users i added in the slapd..

I hope to hear from a kindhearted one...thanks with anticipation for your help..

:smile:

---

### Post by RaiL on 2005-11-12
Thanks for your help guys!

---

### Post by unixnorks on 2005-11-14
Well, your welcome but i hope you will share your experiences to us..:D

---

