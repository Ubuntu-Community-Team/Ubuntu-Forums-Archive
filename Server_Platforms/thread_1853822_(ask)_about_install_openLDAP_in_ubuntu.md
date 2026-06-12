---
title: "(ask) about install openLDAP in ubuntu"
date: 2011-10-03
forum: Server Platforms
---

### Post by kaos_kutang on 2011-10-03
hello boss,
I want to install openLDAP in ubuntu . .
I already read how to install LDAP in  [http://www.openldap.org/doc/admin24/quickstart.html](http://www.openldap.org/doc/admin24/quickstart.html)

But when I follow the configuration as same as in that web, there is an  error show up in the terminal. Herewith the error which I get when I  type 
" ./configuration "

configure: error: MozNSS not found - please specify the location to the  NSPR and NSS header files in CPPFLAGS and the location to the NSPR and  NSS libraries in LDFLAGS (if not in the system location) . .
now, I have nspr and nss files, but what I must do with that files ??

Can you help me what I must do to resolve this problem ??
:confused::confused:


best regards . .

---

### Post by nyu2007 on 2011-10-03
Hi,

Searching first will help you more

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html")

---

### Post by kaos_kutang on 2011-10-03
[B]but when I type "sudo apt-get install slapd ldap-utils", 
there is some error pop up in terminal 'E: unable to locate package slapd'


another command that I already use is 'sudo apt-get install openldap', but there is same error like
'E : unable to locate package openldap' . .

actually, that's command should be fine right ?? 
[/B]

---

### Post by nyu2007 on 2011-10-03
It seem you can not see apt source.
Could you go out internet or you can sudo apt-get update without errors?

---

