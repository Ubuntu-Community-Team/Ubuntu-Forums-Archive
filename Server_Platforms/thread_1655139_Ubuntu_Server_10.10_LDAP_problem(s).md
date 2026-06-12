---
title: "Ubuntu Server 10.10 LDAP problem(s)"
date: 2010-12-29
forum: Server Platforms
---

### Post by anotherli on 2010-12-29
I'm trying to install/set up LDAP on my Ubuntu box. I'm very new to it so I'm using different guides.
I've installed 
slapd, ldap-utils, and db4.2-util so far.
Following the instructions on:
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

It tells me to edit my slapd.conf file but that file doesn't exist.
So right now I'm bouncing back and forth between having to edit a non-existing file and getting
ldap_bind: Invalid credentials (49) errors.
Yes, I realize that I can create my own file but that gives me a bunch of other problems. What should I do. Is there a guide somewhere that actually works? Been at this for over a week and nothing helps.
Should I abandon 10.10 and get something else? Going crazy here. Please help!

EDIT: Oh yeah, many guides tell me that installing slapd should open a initial configuration wizard. This never happens. Maybe the .conf-file is created at that time.

---

### Post by spynappels on 2010-12-29
There are issues installing LDAP on versions of Ubuntu after 8.04 (I think) and manual fettling is required. Do a search for LDAP Ubuntu 10.04 and you will find a couple of threads on the boards, dealing with this specifically, and the instructions should work on 10.10 also.

---

### Post by anotherli on 2011-01-03
Think I got it worked out now. Can't say what I did different though :( sorry.
On to the next problem!

---

