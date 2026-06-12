---
title: "ppolicy en LDAP"
date: 2011-06-07
forum: Software
---

### Post by opc31199 on 2011-06-07
Hola a todos,

Tengo configurado mi LDAP en ubuntu 10.10 y necesito implementarle las politicas de contraseñas. cargo el modulo de ppolicy

dn: cn=module{0},cn=config
changetype: modify
add: olcModuleLoad
olcModuleload: ppolicy

y sin problemas. 

Defino mi politica creandola en una OU 

dn: ou=policies,dc=mpcfg,dc=co,dc=cu
objectClass: organizationalUnit
objectClass: top
ou: policies

dn: cn=default,ou=policies,dc=mpcfg,dc=co,dc=cu
cn: default
objectClass: top
objectClass: device
objectClass: pwdPolicy
objectClass: pwdPolicyChecker
pwdAttribute: 2.5.4.35
pwdMinAge: 86400
pwdMaxAge: 7776000
pwdExpireWarning: 604800
pwdGraceAuthnLimit: 3
pwdMinLength: 10
pwdCheckQuality: 2
pwdCheckModule: check_password.so
pwdMaxFailure: 6
pwdLockout: TRUE
pwdLockoutDuration: 180
pwdFailureCountInterval: 120
pwdInHistory: 4
pwdAllowUserChange: TRUE
pwdMustChange: TRUE
pwdSafeModify: FALSE

Ahora como defino el overlay del ppolicy ya que no estoy usando el fichero slapd.conf?

Alguna idea?

Gracias...

---

