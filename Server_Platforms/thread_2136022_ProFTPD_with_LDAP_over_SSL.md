---
title: "ProFTPD with LDAP over SSL"
date: 2013-04-16
forum: Server Platforms
---

### Post by CheezItMan on 2013-04-16
**<solved below>**
Does anyone have experience with authenticating via Active Directory with proFTPd?  

I've tried the following setup, but it's unable to connect.  I know LDAP over SSL works as I have numerous webservers using LDAP to authenticate over port 636.  

> 

<IfModule mod_ldap.c>
          LDAPServer dc1.mydomain.org:636
          # I've also tried LDAPServer ldaps://dc1.mydomain.org


          LDAPAttr uid sAMAccountName


          LDAPAuthBinds on


          # User information


          LDAPBindDN "cn=domainuser,ou=General,ou=users,dc=mydomain,dc=org" "****"


          LDAPUsers "ou=users,dc=mydomain,dc=org" "(sAMAccountName=%v)"


          # ID's to use when not using the ones from AD


          LDAPDefaultGID 1111


          LDAPDefaultUID 1111


          # Override the use of AD id's with the default values set.


          # Handy when using this setup with a web server that needs read and write


          # access to the files and directories uploaded.


         LDAPForceDefaultGID on
          LDAPForceDefaultUID on


          # Switch on the functionality to generate user homes.


          LDAPGenerateHomedir on 0775


          CreateHome on 0775


          # Overide homedir values from AD

          LDAPGenerateHomedirPrefix /home


          LDAPForceGeneratedHomedir on
</IfModule>




---

### Post by CheezItMan on 2013-04-17
Ok, I found a solution on the ProFTPd forums.

> 
[COLOR=#000000]*<IfModule mod_ldap.c>*[/COLOR]
[COLOR=#ff0000][B]*LDAPServer ldaps://dc1.mydomain.org/??sub*
[/B][/COLOR][COLOR=#000000]*# I've also tried LDAPServer ldaps://dc1.mydomain.org*[/COLOR]


[COLOR=#000000]*LDAPAttr uid sAMAccountName*[/COLOR]


[COLOR=#000000]*LDAPAuthBinds on*[/COLOR]


[COLOR=#000000]*# User information*[/COLOR]


[COLOR=#000000]*LDAPBindDN "cn=domainuser,ou=General,ou=users,dc=mydomain,dc= org" "****"*[/COLOR]


[COLOR=#000000]*LDAPUsers "ou=users,dc=mydomain,dc=org" "(sAMAccountName=%v)"*[/COLOR]


[COLOR=#000000]*# ID's to use when not using the ones from AD*[/COLOR]


[COLOR=#000000]*LDAPDefaultGID 1111*[/COLOR]


[COLOR=#000000]*LDAPDefaultUID 1111*[/COLOR]


[COLOR=#000000]*# Override the use of AD id's with the default values set.*[/COLOR]


[COLOR=#000000]*# Handy when using this setup with a web server that needs read and write*[/COLOR]


[COLOR=#000000]*# access to the files and directories uploaded.*[/COLOR]


[COLOR=#000000]*LDAPForceDefaultGID on*[/COLOR]
[COLOR=#000000]*LDAPForceDefaultUID on*[/COLOR]


[COLOR=#000000]*# Switch on the functionality to generate user homes.*[/COLOR]


[COLOR=#000000]*LDAPGenerateHomedir on 0775*[/COLOR]


[COLOR=#000000]*CreateHome on 0775*[/COLOR]


[COLOR=#000000]*# Overide homedir values from AD*[/COLOR]

[COLOR=#000000]*LDAPGenerateHomedirPrefix /home*[/COLOR]


[COLOR=#000000]*LDAPForceGeneratedHomedir on*[/COLOR]
[COLOR=#000000]*</IfModule>*[/COLOR]


---

