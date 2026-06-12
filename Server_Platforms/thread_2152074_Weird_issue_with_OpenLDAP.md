---
title: "Weird issue with OpenLDAP"
date: 2013-06-06
forum: Server Platforms
---

### Post by nicklinn on 2013-06-06
This issue has been causing me to pull my hair out for the last several hours.  From what I can tell my config is the same as my development server which does work properly.

When attempting to connect using SASL the system returns:
ldap_sasl_interactive_bind_s: Local error (-2)

With no other messages.  slapd log as follows:
Jun  6 16:34:44 UnidemSales slapd[15038]: => access_allowed: search access to "" "objectClass" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [1] attr objectClass
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: access to entry "", attr "objectClass" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: to all values by "", (=0)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: *
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [2] applying +0 (break)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [2] mask: =0
Jun  6 16:34:44 UnidemSales slapd[15038]: => dn: [2]
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [2] matched
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [2] attr objectClass
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: access to entry "", attr "objectClass" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: to all values by "", (=0)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: *
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [1] applying read(=rscxd) (stop)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [1] mask: read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => slap_access_allowed: search access granted by read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => access_allowed: search access granted by read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => access_allowed: read access to "" "entry" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [1] attr entry
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: access to entry "", attr "entry" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: to all values by "", (=0)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: *
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [2] applying +0 (break)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [2] mask: =0
Jun  6 16:34:44 UnidemSales slapd[15038]: => dn: [2]
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [2] matched
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [2] attr entry
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: access to entry "", attr "entry" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: to all values by "", (=0)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: *
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [1] applying read(=rscxd) (stop)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [1] mask: read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => slap_access_allowed: read access granted by read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => access_allowed: read access granted by read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => access_allowed: result not in cache (supportedSASLMechanisms)
Jun  6 16:34:44 UnidemSales slapd[15038]: => access_allowed: read access to "" "supportedSASLMechanisms" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [1] attr supportedSASLMechanisms
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: access to entry "", attr "supportedSASLMechanisms" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: to value by "", (=0)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: *
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [2] applying +0 (break)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [2] mask: =0
Jun  6 16:34:44 UnidemSales slapd[15038]: => dn: [2]
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [2] matched
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_get: [2] attr supportedSASLMechanisms
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: access to entry "", attr "supportedSASLMechanisms" requested
Jun  6 16:34:44 UnidemSales slapd[15038]: => acl_mask: to value by "", (=0)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= check a_dn_pat: *
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [1] applying read(=rscxd) (stop)
Jun  6 16:34:44 UnidemSales slapd[15038]: <= acl_mask: [1] mask: read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => slap_access_allowed: read access granted by read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => access_allowed: read access granted by read(=rscxd)
Jun  6 16:34:44 UnidemSales slapd[15038]: => access_allowed: result was in cache (supportedSASLMechanisms)
Jun  6 16:34:45  slapd[15038]: last message repeated 5 times

Anyone have any idea what is going on?

---

