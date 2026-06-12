---
title: "Ubuntu 8.10 - autofs-ldap"
date: 2009-02-17
forum: Server Platforms
---

### Post by scix on 2009-02-17
I've installed and configured autofs-ldap using this guide: [https://help.ubuntu.com/community/AutofsLDAP](https://help.ubuntu.com/community/AutofsLDAP).

But when I try to start /etc/init.d/autofs at the server I'm getting the following error message: "no automount maps defined".

I've also configured /etc/default/autofs to use LDAP

```

LDAPURI="ldap://localhost/"
LDAPBASE="ou=auto.master,ou=automount,ou=admin,dc=skole,dc=lk,dc=local"

```

Anyone with any idea why this isn't working?

---

### Post by bigbrovar on 2009-02-17
am sure you are using nfs right? have u mapped your auto.master in /etc/aust.master to indicate which directory u want to automount and also create a map called autohome which would contain were u want to automount the directory from

here is how my auto.master looks like
```

# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).

/home   /etc/auto.home
```

indicating that i want the home dir to be automount from

my auto.home which contains
```

            -rsize=8192,wsize=8192,async,bg    fileserver.myserveraddress.:/srv/home.aust/&


```

---

### Post by scix on 2009-02-17
I'll try that, but isn't LDAP supposed to set those settings?

```

dn: ou=auto.master,ou=automount,ou=admin,dc=example,dc=com
ou: auto.master
objectClass: top
objectClass: automountMap
  
dn: cn=/home,ou=auto.master,ou=automount,ou=admin,dc=example,dc=com
cn: /home
objectClass: top
objectClass: automount
automountInformation: ldap:ou=auto.home,ou=automount,ou=admin,dc=example,dc=com --timeout=60 --ghost

```

---

### Post by scix on 2009-02-18
Can I use autofs to mount a to a directory inside a home dir?

Like 


/home/$USER/PrivateShare
/home/$USER/PublicClassDir

---

