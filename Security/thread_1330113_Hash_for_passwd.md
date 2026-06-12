---
title: "Hash for passwd"
date: 2009-11-18
forum: Security
---

### Post by sharpdust on 2009-11-18
Hello, I am writing a script that tries to authenticate a user based on the hash in passwd.

The command I'm doing is:
```
getent passwd myname | cut -d : -f 2
```
which does result in giving me a hash. However, I have no idea how it's hashed.
I am trying to write this in PHP, however my guess of it being MD5 was not correct.
```
if (md5($thePassword) == shell_exec (getent passwd myname | cut -d : -f 2))
```
is not passing.

---

### Post by Sarmacid on 2009-11-18
The first command isn't giving me a hash, since the it's actually stored in the shadow file. I'm guessing the password in Ubuntu is hashed with sha256, so you'd need to use that algorithm and add the salt, which I am also not sure what is.

---

### Post by sisco311 on 2009-11-18
```
man 3 crypt
```

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

i.e. if the encrypted password is:

$[COLOR="Blue"]6[/COLOR]$[COLOR="Red"]IvDBXNzu[/COLOR]$QxgkvzfgkntyaxjCS5jOUlmSeSs1tF2nbK1y8cu9inIDVCgvidOAhKRo/i677bB.IrHvM3tsgTI3g2.ao9VUO/

[COLOR="Blue"]6[/COLOR] = SHA-512
[COLOR="Red"]IvDBXNzu[/COLOR] = salt

once you know the encryption method and the salt you can use crypt to encrypt a string. 

in python:
```
print crypt.cript("password", "\$6\$IvDBXNzu\$")
```

the PHP code should be similar.

---

