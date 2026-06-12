---
title: "LDAP password"
date: 2010-07-18
forum: Server Platforms
---

### Post by tommi88 on 2010-07-18
guys...im having problem setting up the OpenLDAP server...how do i find out what is my LDAP password???

---

### Post by saphear on 2010-07-19
hey,
i have problems with ldap myself, but perhabs I can give you a hint on that one.
As far as I've read different howto's it depends on the version.
If you have a older system you have to set the domain name as well as the ldap root-pw during installation. you can repeat that part with "dpkg-reconfigure slapd".
I followed this howto [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html) 
There you set the password in the backend.ldif file and you can change it afterwards with "slapdpasswd"

I hope that helps a little

---

### Post by tommi88 on 2010-07-19
yea...i did according to the guide that you have provided me too...but then when i want to do the frontend.ldif part,it ask me for the LDAP password and then i type in the same password as i have set in the backend.ldif part but they said invalid credentials...

---

### Post by saphear on 2010-07-19
try "slapdpasswd" before adding the frontend.ldif...I did so and it worked fine for me, although my trouble starts right after that step ;)

---

### Post by tommi88 on 2010-07-19
now im having another problem...this morning i tried doing the  backend.ldif part,it worked...but then i started all over again because i  didnt wanna waste more time figuring out what was the LDAP password...

now  when im doing the backend.ldif part again..this error came out after i  type in this line of command : "sudo ldapadd -Y EXTERNAL -H ldapi:/// -f  backend.erpserver.ldif"..

then this is the error "ldap_add:  Other (e.g., implementation specific) error (80)
                                additional info: <olcModuleLoad> handler exited with 1"

i got another error message "ldap_add: Undefined attribute type (17)
                                               additional info: dn: attribute type undefined"


what  seems to be the problem????i have been seeing the same error message  for the past few days already....

---

