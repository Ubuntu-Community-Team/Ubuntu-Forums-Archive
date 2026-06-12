---
title: "Apache LDAP authentication against AD"
date: 2007-03-15
forum: Server Platforms
---

### Post by DaveHartburn on 2007-03-15
Hi,

Can anyone advise on a problem I have authenticating Apache on Linux against an
Active Directory server? I can not authenticate for all users in the domain,
only users in specific branches.

I've found a few resources on line that suggest the following config is correct:
LoadModule ldap_module modules/mod_ldap.so
LoadModule auth_ldap_module modules/mod_auth_ldap.so

<Directory /usr/local/www/htdoc/helpdesk>
  AuthLDAPURL ldap://gciad01/OU=Bldg800,DC=Galleon,DC=local?sAMAccountName
  AuthLDAPBindDN CN=Support,CN=Users,DC=Galleon,DC=local 
  AuthLDAPBindPassword password_removed
  AuthType Basic
  AuthName "Helpdesk"
  require valid-user
</Directory>

The good news is this works for all users in the organisation unit Bldg800,
which is one of the branches under the top level domain Galleon.local. Users are
burried down a subtree, so it can search through an number of levels of
structure.

My active directory has a number of branches under the top level domain, another
one being a container 'Users'. As I would expect, you can not login as a user in
'Users', as it is not part of the Bldg800 OU.

If I change the URL to:
  AuthLDAPURL ldap://gciad01/CN=Users,DC=Galleon,DC=local?sAMAccountName
then people in 'Users' can login, users in Bldg800 can not. Again as I would expect.

I thought the next logical step was to set the URL a level higher:
  AuthLDAPURL ldap://gciad01/DC=Galleon,DC=local?sAMAccountName
However, with this set, nobody can login. The apache error log reports:
[Wed Mar 14 17:12:47 2007] [warn] [client 192.168.19.31] [5559] auth_ldap authenticate: user support authentication failed; URI /helpdesk/phpinfo.php [ldap_search_ext_s() for user failed][Invalid DN syntax]

Does anyone know what this error means? It suggests it can not search down the
whole subtree, is this the case?

Or, is there a general trick to tell LDAP to check all sub-branches of the tree
under the top level directory, something like Galleon.local.*. If not, is it
possible to specify more than one URL?

Any help appreciated.

Dave

---

### Post by aresazi on 2007-06-13
W2K3 AD servers changed a config setting disallowing reading of a whole domain. See [http://support.microsoft.com/kb/326690](http://support.microsoft.com/kb/326690) & [http://msdn2.microsoft.com/en-gb/library/ms675656.aspx](http://msdn2.microsoft.com/en-gb/library/ms675656.aspx)

---

