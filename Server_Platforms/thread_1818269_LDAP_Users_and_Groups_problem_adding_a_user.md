---
title: "LDAP Users and Groups problem adding a user"
date: 2011-08-04
forum: Server Platforms
---

### Post by sgiessle on 2011-08-04
I have Ubuntu 10.04.2 (Linux 2.6.32-33-server on x86_64) with OpenLDAP 2.4.21 and Webmin1.550. I converted my ldap database from another system with the older style schema (OpenLDAP 2.3.3 with slightly older Webmin version 1.480) and no longer use slapd.conf, but the newer slapd.d format. It all works fine except for one thing. When I add a new user, it lets me type in the additional LDAP fields:

[IMG]http://www.as.wvu.edu/~steveg/before_user_added.png[/IMG]

but when I click the Create button, all the fields get jumbled together in the Title/Position box with a diamond question mark delimiting the fields:

[IMG]http://www.as.wvu.edu/~steveg/after_user_added.png[/IMG]

Has anyone seen this before? Any idea what would cause that? I am at a loss.

Modifying existing users (which have the Additional fields displaying correctly) also has the same result - it moves the fields all into the one Title/Position box with the diamond shapes with question marks inside between each entry. Is it a problem with my schema files? I tried reverting to the older shema files and slapd.conf and it still did the same thing on the new system. I am really at a loss. Thanks in advance for any insights you all may have.

Here is also the output of ldapsearch for that user (host and samba ids are sanitized):

# bclowner, people, host.com
dn: uid=bclowner,ou=people,dc=host,dc=com
cn: bobo Clown
uid: bclowner
uidNumber: 1013
loginShell: /bin/bash
homeDirectory: /home/bclowner
gidNumber: 100
userPassword:: Kg==
objectClass: posixAccount
objectClass: shadowAccount
objectClass: person
objectClass: inetOrgPerson
objectClass: sambaSamAccount
ou: Circus
o: Big Top
sambaNTPassword: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
sambaLMPassword: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
sambaSID: sanitized
sambaPrimaryGroupSID: sanitized
sambaAcctFlags: [UD         ]
title:: Q2lyY3VzIENsb3duAEJBIGluIGNsb3duaW5nAFRoZSBCaWcgVGVudAAwMDAtMDAwLTAwMD
 AAYmNsb3duQGhvc3QuY29t
givenName: bobo
sn: Clown
gecos: bobo Clown

# search result
search: 2
result: 0 Success

Previously added users that show the fields properly have "description:" and then the field listed for each Additional LDAP field. Also shouldn't the "title" be visible in plain human readable text here? - it looks like it encrypted it somehow - similar to a password hash. The older system works fine and the fields are all readable and in their proper locations. But the new system just doesn't work right. Any ideas anyone?

Steve

---

### Post by sgiessle on 2011-08-04
Thank you Jesus! Here is the answer to the problem:

[http://sourceforge.net/tracker/index.php?func=detail&aid=3365284&group_id=17457&atid=117457](http://sourceforge.net/tracker/index.php?func=detail&aid=3365284&group_id=17457&atid=117457)

I hope this helps someone else that might have encountered this problem. I applied the patch (actually I just edited the file and added the one missing line) and it worked!

Steve

---

