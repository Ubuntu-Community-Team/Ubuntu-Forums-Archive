---
title: "SAMBA and ldap"
date: 2011-11-22
forum: Server Platforms
---

### Post by veggis on 2011-11-22
Someone know what to do with this error

```
Global symbol "$SID" requires explicit package name at /usr/share/doc/smbldap-tools/configure.pl line 350
```


and how to add sudo user to ldap-users? Because now I cant log in as root or sudo users only as ldap users, and not ldap admin.......


regards

---

### Post by HermanAB on 2011-11-23
Hmm, playing with authentication has its problems.

You would need to boot into single user mode to get into your system and fix things.

---

### Post by luvshines on 2011-11-25
> **veggis said:**
> Someone know what to do with this error

```
Global symbol "$SID" requires explicit package name at /usr/share/doc/smbldap-tools/configure.pl line 350
```


and how to add sudo user to ldap-users? Because now I cant log in as root or sudo users only as ldap users, and not ldap admin.......


regards

**Edited:** Was thinking of creating LDAP user with uidNumber 0 and using it as fake root but then remembered that the PAM would be having pam_succeed >500 restriction and would disallow login :(

---

### Post by Qutaibah on 2011-12-10
same problem :(


when I am trying 

 sudo perl /usr/share/doc/smbldap-tools/configure.pl 
while
Samba - Primary Domain Controler


the error

qutaibah@ubuntuserver:~$ sudo perl /usr/share/doc/smbldap-tools/configure.pl 
Global symbol "$SID" requires explicit package name at /usr/share/doc/smbldap-tools/configure.pl line 350.
Execution of /usr/share/doc/smbldap-tools/configure.pl aborted due to compilation errors.
qutaibah@ubuntuserver:~$ 



:(

---

### Post by luvshines on 2011-12-11
Did you try what the configure.pl script says just above the 350 line:> # Put your own SID. To obtain this number do: \"net getlocalsid\".
# If not defined, parameter is taking from \"net getlocalsid\" return

Are you able to run 'net getlocalsid' command ?

If yes, then maybe you can simply change line 350 as> 
SID=\"<SID-returned-by-getlocalsid>\"

---

### Post by cleverghost on 2011-12-13
I am also having the same problem as above, though I have populated the SID field with the output from:


```
sudo net getlocalsid
```

and it still gives me this:

```
Global symbol "$SID" requires explicit package name at /usr/share/doc/smbldap-tools/configure.pl line 350.
Execution of /usr/share/doc/smbldap-tools/configure.pl aborted due to compilation errors.
```


Trying to get samba, openldap, and phpldapadmin to run together for a document server.

---

### Post by luvshines on 2011-12-14
On my system, though I didn't run the script till the end, but just to find out the errors, ran it as 'perl configure.pl'

Fixed the following to get it working> 
## On lines 314 and 315, added a \ before the $ in the end

# \$Source: /opt/cvs/samba/smbldap-tools/configure.pl,v **[COLOR="Red"]\$[/COLOR]**

# \$Id: configure.pl 26 2010-11-15 14:28:01Z mm1 **[COLOR="red"]\$[/COLOR]**

## On lines 527 and 532, added \ before the "
# Allows not to use smbpasswd (if with_smbpasswd=**[COLOR="red"]\"0\"[/COLOR]** in smbldap.conf) but

# Allows not to use slappasswd (if with_slappasswd=**[COLOR="red"]\"0\"[/COLOR]** in smbldap.conf)

That should work I guess.

---

### Post by nnr on 2012-03-01
hello everybody

I have the same problem with  configure.pl from smbldap-tools.I have tried all solution that I find on the web but no result.
I still have this message
"
Global symbol "$SID" requires explicit package name at /usr/share/doc/smbldap-tools/configure.pl line 350
did someone find soltuion?
thanks

---

### Post by fadec on 2012-04-07
[SIZE=2]Final solution is:
[/SIZE]
[LIST=1]
[*][SIZE=2]sudo net getlocalsid [/SIZE]
[*][SIZE=2]Substitute with given SID (for e.g. SID for domain DC0 is: S-1-5-21-1038398530-1857452570-2395030447) $SID[/SIZE]
[*][SIZE=2]Do corrections as proposed above:[/SIZE]
[/LIST]
[SIZE=2]## On lines 314 and 315, added a \ before the $ in the end
# \$Source: /opt/cvs/samba/smbldap-tools/configure.pl,v **[COLOR=Red]\$[/COLOR]**
 # \$Id: configure.pl 26 2010-11-15 14:28:01Z mm1 **[COLOR=red]\$[/COLOR]**

 ## On lines 527 and 532, added \ before the "
 # Allows not to use smbpasswd (if with_smbpasswd=**[COLOR=red]\"0\"[/COLOR]** in smbldap.conf) but
 # Allows not to use slappasswd (if with_slappasswd=**[COLOR=red]\"0\"[/COLOR]** in smbldap.conf)                      


In my case (Ubuntu server 11.10) in p.3 last two lines were correct already[/SIZE][SIZE=2].[/SIZE]

NB Don't do any comments around lines mentioned above with in the configure.pl - it will take to another mistake(s).

---

