---
title: "Ubuntu Server 12.04 ldap_bind Invalid Credentials (49)"
date: 2012-05-14
forum: Server Platforms
---

### Post by ranger12 on 2012-05-14
Hmm been doing some research on this and haven't really been able to come up with a clear answer yet. I am trying to configure Kerberos with OpenLDAP and was trying to do this at the comand line (SSH connection from the workstation):

sudo ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn=kerberos.ldif
Enter LDAP Password: 

After entering the password I get this:

ldap_bind: Invalid credentials (49)

I wonder if someone could give me some advice on what to check and where.

Thanks

---

### Post by ranger12 on 2012-05-14
Well after doing some more research I tried slappasswd to generate a new password and tried adding it with ldapmodify and than restarting the slapd daemon but to no avail. I get the same result. Must be another issue. Hmm....

---

### Post by ranger12 on 2012-05-15
Sheesh, I am beginning to think I should not even bothered to setup kerberos and ldap.:)  I managed to use an alternate syntax with ldapmodify to add the schema and an index. I now tried to use addprinc after setting it up and it gives me an error saying it was unable to decrypt the database with latest master key provided. I also restarted the server and it gives the same message on boot up and also an error message stating it cannot create the realm - "whatever" What log can I check for this? Anyone know?

$ sudo kadmin.local
[sudo] password for adam: 
Authenticating as principal root/admin@ELRANCHO.NET with password.
kadmin.local: Unable to decrypt latest master key with the provided master key
 while initializing kadmin.local interface

I either missed a memo somewhere or I just simply screwed something up. However, I look at the bright side - this is a learning process/environment and not an actual server going in some office or business. :) Just a home network/project. I'll see if I can dig up some answers somewhere.

Here is the other error on boot:

krb5kdc: cannot initialize realm ELRANCHO.NET - see log file for details

---

### Post by ranger12 on 2012-05-15
Well I discovered that I did not have logging enabled for kerberos so I did. It was useless in finding out the problem. It just reports the messages at boot - no further details. I am stumped. I have not found any info about this elsewhere on the net. Is there a way I can purge OpenLDAP and kerberos and start fresh? I have no clue at this point on diagnosing what is causing this problem.

---

### Post by ranger12 on 2012-05-15
I wonder if I should not have installed krb5-kdc package and configured if I was going to configure kerberos and OpenLDAP since there is a seperate krb5-kdc-ldap package maybe that is where I screwed up. I did install that package as well. I used the server guide for all this. I hope I am not going to have to wipe the server and reinstall Ubuntu.

---

### Post by ranger12 on 2012-05-15
Yeah I think I will just wipe the drive and start fresh. I think this issue is too deep and the docs are a little fuzzy.

---

