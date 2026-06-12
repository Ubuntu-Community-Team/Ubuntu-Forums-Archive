---
title: "Need Help: Bugzilla cannot authenticate using Windows AD with LDAP"
date: 2013-02-22
forum: Server Platforms
---

### Post by RLTF on 2013-02-22
Hi All, 
 
Would appreicate if anyone can help me out here, issue as below: 
 
Bugzilla version ==4.2.5
Ubuntu Server 12.03.02 LTS
 
LDAP settings as below: 
LDAPserver 
==> ldap.serverdc01.CN.mycompany.com
LDAPbinddn
==> CN=bugzilla,OU=aaa,OU=bbb,OU=ccc,DC=xxx,DC=yyy,DC=COM: passwd
LDAPBaseDN
==>OU=aaa,OU=bbb,OU=ccc,DC=xxx,DC=yyy,DC=COM
LDAPuidattribute
==>sAMAccountName
LDAPmailattribute
==>mail
 
Create an windows login account on windows domain controller ==>bugzilla as indicate above.
 
When try to login using my windows account, got the following err: 
 
Could not connect to the LDAP server(s) 
ldap.serverdc01.CN.mycompany.com
 
Traceback:
at Bugzilla/Auth/Verify/LDAP.pm line 188 Bugzilla::Auth::Verify::LDAP::ldap(...) called at Bugzilla/Auth/Verify/LDAP.pm line 162 Bugzilla::Auth::Verify::LDAP::_bind_ldap_for_search(...) called at Bugzilla/Auth/Verify/LDAP.pm line 60 Bugzilla::Auth::Verify::LDAP::check_credentials(...) called at Bugzilla/Auth/Verify/Stack.pm line 62 Bugzilla::Auth::Verify::Stack::check_credentials(...) called at Bugzilla/Auth.pm line 72 Bugzilla::Auth::login(...) called at Bugzilla.pm line 345 Bugzilla::login(...) called at /var/www/bugzilla/index.cgi line 40
 
Could not figure out what wrong with my LDAP settings or is it something else ?
 
Thanks
 
RLTF

---

### Post by albandy on 2013-02-22
If it's an A.D. try using the port 3268

---

### Post by RLTF on 2013-02-22
Try both port 389 and 3268 still no luck with same error message.
 
Also would like to double check if there anything else need to be configure on the windows AD beside create an domain user account ?
 
Thanks.

---

### Post by albandy on 2013-02-22
Have you tried using the ip instead of the dns name?

---

### Post by RLTF on 2013-02-22
Try IP address with/without port#...still not work but got new err as below: 
 
==> The username or password you entered is not valid.
==> Please press Back and try again.
 
Thanks.

---

### Post by albandy on 2013-02-22
> **RLTF said:**
> Try IP address with/without port#...still not work but got new err as below: 
 
==> The username or password you entered is not valid.
==> Please press Back and try again.
 
Thanks.

You can use an application called LDAPBROWSER to do the tests:
[http://www.novell.com/communities/files/Gawor_ldapbrowser_282.zip](http://www.novell.com/communities/files/Gawor_ldapbrowser_282.zip)

---

### Post by RLTF on 2013-02-22
I did download a free LDAP browser 
 
[http://www.ldapbrowser.com/download.htm#lb](http://www.ldapbrowser.com/download.htm#lb)
 
and have check over and over again could not find out anything wrong
 
LDAPserver 
==> ldap.serverdc01.CN.mycompany.com
LDAPbinddn
==> CN=bugzilla,OU=aaa,OU=bbb,OU=ccc,DC=CN,DC=yyy,DC= COM: passwd
LDAPBaseDN
==>OU=aaa,OU=bbb,OU=ccc,DC=CN,DC=yyy,DC=COM
LDAPuidattribute
==>sAMAccountName
LDAPmailattribute
==>mail

---

### Post by RLTF on 2013-02-22
Found something new again, just notice from LDAPbinddn heading state enter syntax
 
==> (e.g. cn=default,cn=user: password)
 
so I put the passwd right after the user account : 
 
CN=bugzilla: passwd,OU=aaa,OU=bbb,OU=ccc,DC=CN,DC=yyy,DC=com
 
instead of 
 
CN=bugzilla,OU=aaa,OU=bbb,OU=ccc,DC=CN,DC=yyy,DC=com: passwd (as suggest in old ver)
 
then again I got new error mesg:
 
Failed to bind to the LDAP server. The error message was: 80090308: LdapErr: DSID-0C090334, comment: AcceptSecurityContext error, data 525, vece
Traceback:
at Bugzilla/Auth/Verify/LDAP.pm line 168
Bugzilla::Auth::Verify::LDAP::_bind_ldap_for_search(...) called at Bugzilla/Auth/Verify/LDAP.pm line 60
Bugzilla::Auth::Verify::LDAP::check_credentials(...) called at Bugzilla/Auth/Verify/Stack.pm line 62
Bugzilla::Auth::Verify::Stack::check_credentials(...) called at Bugzilla/Auth.pm line 72
Bugzilla::Auth::login(...) called at Bugzilla.pm line 345
Bugzilla::login(...) called at /var/www/bugzilla/index.cgi line 40

---

### Post by RLTF on 2013-03-04
Hi, 

Anyone can help me out here ?

Still stuck......

---

