---
title: "Prob with LDAP auth and HTTP"
date: 2008-10-31
forum: Server Platforms
---

### Post by stonneway on 2008-10-31
Chaps, I know this isn't strictly a Ubuntu issue but I thought that someone here may know the soltuion to the issue I'm having.

I have the following code setup in an apache config file to restrict access to trac sites on the server via LDAP group membership. 

This works fine, with one slight exception. When we change the membership of the ldap group (in active directory), we have to restart Apache on the linux box. A reload doesnt work, it has to be a restart. If we dont, then the changes to the group aren't recognised. It's as though the membership of the group is cached on the linux box and that cache is never updated. 

It's not a massive issue at the moment, but will be a management pain-in-the-rear when the sites are used by more and more external users.

Any ideas? Code is as follows.

<Location /url/to/page>
  SetHandler mod_python
  PythonInterpreter main_interpreter
  PythonHandler trac.web.modpython_frontend
  PythonOption TracEnv /trac/environ/site
  PythonOption TracUriRoot /url/to/page

  AuthName "Authentication"

  AuthType Basic
  AuthBasicProvider ldap

  AuthzLDAPAuthoritative on

  AuthLDAPBindDN "CN=LDAP USER,CN=Users,DC=mydomain,DC=local"
  AuthLDAPBindPassword passwordgoeshere
  AuthLDAPURL "ldap://ldapserver.mydomain.local:389/DC=mydomain,DC=local?sAMAccountName?sub?(objectClass=*)" NONE
  AuthLDAPGroupAttributeIsDN on
  require ldap-group CN=testgroup,OU=Security Groups,OU=My OU,DC=mydomain,DC=local

  Require valid-user
</Location>

---

