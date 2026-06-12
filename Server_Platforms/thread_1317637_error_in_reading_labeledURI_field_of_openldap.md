---
title: "error in reading labeledURI field of openldap"
date: 2009-11-06
forum: Server Platforms
---

### Post by tanveer on 2009-11-06
Hi,
OK I studied with openldap for a while and faced a problem that is I have implemented a test ldap server and can communicate with it via PHP. I can fetch all data from openldap except one which is labeledURI under objectClass inetOrgPerson. I dont know why? In error log its giving me this error:

[PHP]PHP Notice:  Undefined index:  labeledURI in /var/www/html/test.php on line 17 [/PHP]
and below is my code and ldif file of openldap:



[PHP]## DEFINE DIT ROOT/BASE/SUFFIX ####
## uses RFC 2377 format

## dcObject is an AUXILLIARY objectclass and MUST
## have a STRUCTURAL objectclass (organization in this case)
## this is an ENTRY sequence and is preceded by a BLANK line

dn: dc=example,dc=com
dc: example
description: test domain
objectClass: dcObject
objectClass: organization
o: example, Inc.

## FIRST Level hierarchy - people
## uses mixed upper and lower case for objectclass
## this is an ENTRY sequence and is preceded by a BLANK line

dn: ou=people, dc=example,dc=com
ou: people
description: All people in organisation
objectclass: organizationalunit

## SECOND Level hierarchy
## ADD a single entry under FIRST (people) level
## this is an ENTRY sequence and is preceded by a BLANK line
## the ou: Project Management is the department name

dn: cn=J Stefan,ou=people,dc=example,dc=com
objectclass: inetOrgPerson
cn: J Stefan
homephone: 514-111-2222
mail: j_stefan@example.com
labeledURI: http://p2.example.com/~j_stefan   
description: Group Owner
ou: Project Management

dn: cn=John Abrus,ou=people,dc=example,dc=com
objectclass: inetOrgPerson
cn: John Abrus
homephone: 514-443-1163
mail: jabrus@example.com
labeledURI: http://p1.example.com/~jabrus
description: Group Member
[/PHP]

and the php file code:

[PHP]
<?php

$conn= ldap_connect ("ldapserver-ip-here") or die ("cant connect");
$r = ldap_bind($conn) or die ("could not bind");
$result=ldap_search ($conn,"ou=people,dc=example,dc=com", "(cn=*)") or die ("sorry");

$info = ldap_get_entries($conn,$result);

for ($i=0;$i<$info["count"];$i++)
{
 echo "CN  = ". $info[$i]["cn"][0] . "<br>";
 echo "Desc = ". $info[$i]["description"][0] . "<br>";
 echo "Mail= ". $info[$i]["mail"][0] . "<br>";
 echo "URL = ". $info[$i]["labeledURI"][0] . "<br>";
 echo "phone = ". $info[$i]["homephone"][0] . "<br>";
}

echo "number of entries found=" . ldap_count_entries($conn,$result) . "<p>";

ldap_close($conn);
?>[/PHP]

Any suggestions. Thanks in advance.

---

