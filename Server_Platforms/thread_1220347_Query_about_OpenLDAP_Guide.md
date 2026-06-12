---
title: "Query about OpenLDAP Guide"
date: 2009-07-22
forum: Server Platforms
---

### Post by tomgibson on 2009-07-22
I have been following this OpenLDAP guide at [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760) which covers setting up Ubuntu Server as an LDAP and Samba domain controller, however although the guide is excellent and goes into detail on almost every point, it is somewhat out of date in that it relates to 7.10 which is no longer recieving standard support. Because of this I have been attempting to adapt it for use with 9.04, however I am completely stumped :confused: at the following step, which refers to editing the slapd.conf file (which after googling I gather is now deprecated and hence no longer present in current ubuntu releases):-

"

While in the file we need to change another line. Find the line that says "access to attribute=userPassword,shadowLastChange" and change it to:
```
access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
```"

I have determined from this page [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html) that I should be using ldapmodify to make the change instead, however I have no idea whatsoever how the syntax for this works, and despite making several educated guesses I am no closer to understanding how to do this. Oh and perhaps I should add that I am less than clear as to what the quoted step achieves, and what problems would be caused by leaving it out. If anyone could point me in the direction of some info on how to resolve this, or suggest the correct syntax to modify the relevant entry(s?) in the database to reflect the change that this conf change would have effected, I would be most grateful!

Many thanks!

---

