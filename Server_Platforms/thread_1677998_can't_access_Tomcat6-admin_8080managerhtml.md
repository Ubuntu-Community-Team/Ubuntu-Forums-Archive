---
title: "can't access Tomcat6-admin :8080/manager/html"
date: 2011-01-29
forum: Server Platforms
---

### Post by muddywater on 2011-01-29
Setting up a sandbox server at home.
First time.
Been using Ubuntu since 7.4
So far:
Ubuntu Server 10.4 LTS
openssh
tomcat6(incl. -admin etc.)
sun-java
   I'm currently remotely administering both inside and outside my routered LAN with puTTY and WinSCP (for sftp)through openssh from a Win7.  
   Slightly off topic, any security recommendations for granting permission to the sftp user to access specified root files would be appreciated (ie /tomcat/webapps  for sftp transfer of html content/directory trees .war files etx.)

The problem I'm having is accessing :8080/manager/html

I am able to reach the tomcat:8080 "it works"

I have tried nearly every possible variation of /conf/tomcat-users.xml

when I attempt to access :8080/manager/html through firefox I get a discrete username and password prompt with a Tomcat Manager header. 
 
when I enter the un/pw it returns the prompt almost immediately.

If I cancel it I get a 401. 

I have tried several un/pw combo's - all the same.
I am wondering if it may be a
permission issue with the user having read access to the root/conf file. 

Any suggestions greatly appreciated,
mw

---

