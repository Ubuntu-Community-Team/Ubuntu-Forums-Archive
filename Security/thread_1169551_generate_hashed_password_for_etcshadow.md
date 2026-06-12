---
title: "generate hashed password for /etc/shadow"
date: 2009-05-25
forum: Security
---

### Post by PoolSnoopy on 2009-05-25
Hi all,

does anyone know how to generate the hash used in /etc/shadow if the sha512 algorithm is used? for md5 I found that
```

openssl passwd -1 -salt <salt> <passwd>

```
will work fine. I'm using ubuntu 9.04 server and it seems that here sha512 instead of md5 is used. how can I generate a proper hash here?
a command line or php solution would be highly appreciated.

thanx a lot in advance!

---

### Post by t00l on 2009-05-25
```
<?php
echo hash('sha512', 'The quick brown fox jumped over the lazy dog.');
?>
```

Works for PHP5 >= 5.1.2

---

### Post by PoolSnoopy on 2009-05-25
well it's not quite as simple. :-) I would have figured that out myself. first of all the hash in /etc/shadow is salted and moreover the whole hash is kind of base64-encoded. but not the same way as for example mime-attachments in mails.

---

### Post by t00l on 2009-05-25
Well then, my fault. Still, [maybe this would help]("http://blog.loftninjas.org/2009/03/11/generating-sha512-passwords/") ;>
I've got blowfish in my OS so can't compare my results with any Ubuntu SHA512 psswd.

---

### Post by PoolSnoopy on 2009-05-25
thanx for that tip, but unfortunately it's not exactly what I need. :-( if I could provide the "salt" then it would be the perfect solution.

---

### Post by koenn on 2009-05-25
have you tried mkpasswd ?
```
 mkpasswd [OPTIONS]... [PASSWORD [SALT]]

```

The version I have doesn't show sha512 as an available algorithm, but Im using 8.04  - maybe they updated mkpasswd along with the change in shadow ?

or, 
a very elaborate workaround could be to use pwconv - depends on what exactly you're trying to do

---

### Post by sisco311 on 2009-05-25
> **koenn said:**
> have you tried mkpasswd ?
```
 mkpasswd [OPTIONS]... [PASSWORD [SALT]]

```

The version I have doesn't show sha512 as an available algorithm, but Im using 8.04  - maybe they updated mkpasswd along with the change in shadow ?


yep:
```
mkpasswd -m sha-512 password salt
```

---

### Post by koenn on 2009-05-25
cool.

---

### Post by sisco311 on 2009-05-25
python:
```
python -c "import crypt, getpass, pwd; print crypt.crypt('password', '\$6\$SALTsalt\$')"
```

:)

---

### Post by PoolSnoopy on 2009-05-26
thank you so much.

the python solution works perfectly. the mkpasswd does not work with the salt given in /etc/shadow.

---

### Post by sisco311 on 2009-05-26
> **PoolSnoopy said:**
> thank you so much.

the python solution works perfectly. the mkpasswd does not work with the salt given in /etc/shadow.

in mkpasswd the salt must not  contain  prefixes  such  as $1$.

i.e.
$6$SALTSALT$PASSWORD
```
mkpasswd -m sha-512 password SALTSALT 

```

you specify the method with the -m flag 

in crypt
```
If  salt is a character string starting with the characters "$id$" fol&#8208;
       lowed by a string terminated by "$":

              $id$salt$encrypted

       then instead of using the DES machine,  id  identifies  the  encryption
       method  used  and  this  then  determines  how the rest of the password
       string is interpreted.  The following values of id are supported:

              ID  | Method
              &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
              1   | MD5
              2a  | Blowfish (not in mainline glibc; added in some
                  | Linux distributions)
              5   | SHA-256 (since glibc 2.7)
              6   | SHA-512 (since glibc 2.7)

       So   $5$salt$encrypted   is   an   SHA-256   encoded    password    and
       $6$salt$encrypted is an SHA-512 encoded one.

       "salt" stands for the up to 16 characters following "$id$" in the salt.
       The encrypted part of the password string is the actual computed  pass&#8208;
       word.  The size of this string is fixed:

       MD5     | 22 characters
       SHA-256 | 43 characters
       SHA-512 | 86 characters

       The  characters  in  "salt"  and  "encrypted"  are  drawn  from the set
       [a&#8211;zA&#8211;Z0&#8211;9./].  In the SHA implementation the entire key is significant
       (instead of only the first 8 bytes in MD5).

```
[PHP]crypt('password', '\$6\$SALTSALT\$')"[/php]

for more info:
```
man mkpasswd
man 3 crypt
```

---

### Post by PoolSnoopy on 2009-05-26
ubuntu 9.04 comes with mkpasswd 4.7.30 and if I enter
```

mkpasswd -m sha-512 password saltsalt

```
I get
```

Wrong salt length: 8 byte(s) when 16 expected.

```
but I'm very happy with the python or php version. now I can use single-signon in web applications, too.

---

### Post by cdenley on 2009-05-26
> **PoolSnoopy said:**
> ubuntu 9.04 comes with mkpasswd 4.7.30 and if I enter
```

mkpasswd -m sha-512 password saltsalt

```
I get
```

Wrong salt length: 8 byte(s) when 16 expected.

```
but I'm very happy with the python or php version. now I can use single-signon in web applications, too.

That is a bug in mkpasswd. It has been fixed in the next ubuntu release (9.10). Variable length salts are supported for SHA-512 password hashes, but mkpasswd didn't support them.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523387](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523387)
[http://changelogs.ubuntu.com/changelogs/pool/main/w/whois/whois_4.7.33/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/w/whois/whois_4.7.33/changelog)

---

