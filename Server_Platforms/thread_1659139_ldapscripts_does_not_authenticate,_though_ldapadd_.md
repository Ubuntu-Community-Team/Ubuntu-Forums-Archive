---
title: "ldapscripts does not authenticate, though ldapadd works"
date: 2011-01-03
forum: Server Platforms
---

### Post by m00dawg on 2011-01-03
ldapscripts seems to be authenticating oddly but I am not sure why. Running 'ldapadd' works without issue:

<code>root@domainator:~# ldapadd -D cn=root,dc=example,dc=home -W
Enter LDAP Password: 
<CTRL-D>
root@domainator:~# 
</code>

However:

<code>
root@domainator:~# ldapaddgroup test
>> 01/03/11 - 22:16 : Command : /usr/sbin/ldapaddgroup test
ldap_bind: Invalid credentials (49)
ldap_bind: Invalid credentials (49)
Error adding group test to LDAP
Error adding group test to LDAP
</code>

Here's various parts of my /etc/ldapscripts/ldapscripts.conf:

<code>
SERVER="domainator"
BINDDN="cn=root,dc=example,dc=home"
BINDPWDFILE="/etc/ldapscripts/ldapscripts.passwd"
SUFFIX="dc=example,dc=home" # Global suffix
GSUFFIX="ou=Groups"        # Groups ou (just under $SUFFIX)
USUFFIX="ou=Users"         # Users ou (just under $SUFFIX)
MSUFFIX="ou=Computers"      # Machines ou (just under $SUFFIX)
GIDSTART="10000" # Group ID
UIDSTART="10000" # User ID
MIDSTART="20000" # Machine ID
</code>

/etc/ldapscripts/ldapscripts.passwd permissions are root:root, 0400 and I have quadruple checked my password is correct.

Is there anything I am missing here? Or is there a way to print out debugging from ldapscripts so I know what commands it is generating?

---

### Post by woodman231 on 2011-01-03
In the "ldapscripts.conf" file try setting your server as: "ldap://domainator"

Also try "BINDPWD = "password" instead of the BINDPWDFILE at least as a test to see if it works out better for you.  Good luck.

Thanks,
Sean W.

---

### Post by m00dawg on 2011-01-04
Not a bad thought. I tried both options (both individually and together) and still ended up with this:

<code>
root@domainator:~# ldapaddgroup test
>> 01/04/11 - 14:08 : Command : /usr/sbin/ldapaddgroup test
ldap_bind: Invalid credentials (49)
ldap_bind: Invalid credentials (49)
Error adding group test to LDAP
Error adding group test to LDAP
</code>

Really troublesome I can't get more info from ldapscripts. Is there perhaps any other tool I can use to administer LDAP that tends to work well under Ubuntu.

I have to say, having this be my 3rd attempt at using LDAP, I can only imagine how complicated X.500 directory services are :)

---

### Post by m00dawg on 2011-01-04
Hah spoke to soon :) There's at least 3 I am going to evaluate as alternatives. Here are some I found just by doing 'apt-cache search ldap':

cpu
ldap-account-manager
ldaptor

Hopefully one of these does the trick. I was actually looking for a more friendly interface anyway so that other less command-line savvy admins can still make LDAP changes.

*crosses fingers*

---

