---
title: "LDAP Authentication problem"
date: 2009-05-20
forum: Server Platforms
---

### Post by Darryl Moore on 2009-05-20
I've written some scripts for automating LDAP client and server setting up. I thought it was all working well, but I just tried to set up a new 9.04 client using LDAP for authentication and it doesn't work.

When I run getent with passwd shadow or group, from the client I get back exactly what I should

 when I run 

   ldapsearch -xLLL -b "dc=moores,dc=ca" uid=melinda 

it returns:


dn: uid=melinda,ou=People,dc=moores,dc=ca
uid: melinda
cn: Melinda Moore
homeDirectory: /home/melinda
uidNumber: 1001
objectClass: account
objectClass: posixAccount
objectClass: top
objectClass: shadowAccount
gidNumber: 100
gecos: Melinda Moore
loginShell: /bin/bash


 exactly like it should

when I log into the gui as only user who has local authentication I get a list of all the LDAP users in the drop down box on the menu bar.

Given all this you might be inclinded to think I had set this up properly, however if I try to log in as a LDAP user to gnome or a tty, or I try to ssh into the box, instead of loggin in, I get the message unknown user id.

The nsswitch entries for passwd shadow and group are all "files ldap". the pam.d/common-* entries are all left as the package installation had them (which from previous experience worked) so does anyone have any idea where I might look to see why this is not working?

I'm pulling my closely shaven head of hair out here and the missing handfuls of scalp are begining to become irritating.

cheers,
darryl

---

### Post by Darryl Moore on 2009-05-20
Well, nobody's replied, but that's ok. upon further investigation I found that when I was making LDAP requests over the network for authentication I was not supplying the right admin password so they kept being rejected. I reset my password with "echo password > /etc/ldap.secret" which apearently I did not do right the first time. I was still a little stymied when that did not immeadiately fix it. After a reboot, all was well again though.

---

