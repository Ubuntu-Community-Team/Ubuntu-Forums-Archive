---
title: "Mapping UNIX Groups to Windows Groups"
date: 2010-10-12
forum: Server Platforms
---

### Post by twitterritter on 2010-10-12
Hello,

I am currently trying to set up a Samba domain server. In the Samba-HOWTO-Collection I found an
example file.(Point 3.3.3.1)
In the explanations of the example below, the author says I need to map UNIX Groups to NT Groups.

He writes a shell-script of how one could do it, but when I copy it and then execute it, I get the error:

Bad option: rid=512
Bad option: rid=513
Bad option: rid=514

The other groups do get mapped, just the Domain Admins, Domain Users and Domain Guests dont.

_This is the shell from the HOWTO_:


[I]#!/bin/bash
#### Shell-Skript f &#776;r sp &#776;tere Verwendung aufbewahren

net groupmap modify ntgroup="Domain Admins" unixgroup=ntadmins rid=512[/I] [I]
net groupmap modify ntgroup="Domain Users" unixgroup=users rid=513
net groupmap modify ntgroup="Domain Guests" unixgroup=nobody rid=514

net groupmap add ntgroup="Designers" unixgroup=designers type=d rid=1112[/I] [I]
net groupmap add ntgroup="Engineers" unixgroup=engineers type=d rid=1113
net groupmap add ntgroup="QA Team"
unixgroup=qateam
type=d rid=1114
[/I]
_And this is my own:_

[I]#! /bin/bash
###### Shell-Skript aufbewahren

# Windows-Bekannte Gruppen zusweisen[/I] [I]
net groupmap modify ntgroup="Domain Admins" unixgroup=ntadmins     rid=512
net groupmap modify ntgroup="Domain Users" unixgroup=users    rid=513
net groupmap modify ntgroup="Domain Guests" unixgroup=nobody    rid=514

#Arbofilia + Coecoceiba Gruppen dazufügen[/I] [I]
net groupmap add ntgroup="Arbofilia" unixgroup=arbofilia    type=d rid=3005
net groupmap add ntgroup="Coecoceiba" unixgroup=coecoceiba    type=d rid=3009
[/I]

---

### Post by Zeosa on 2010-10-12
the rid value isn't a valid option for 'modify', only for 'add'.

for run 'net groupmap list' to see what those groups are already mapped to, if you need to modify them you don't include the 'rid' option...


net groupmap modify ntgroup='Domain Admins'  unixgroup='ntadmins'

---

### Post by twitterritter on 2010-10-13
Thanks that was it:

the Domain Admins, Domain Users and Domain Guests were not mapped so I was able to add them by replacing the "modify" with "add". 

Thanks Zeosa

---

