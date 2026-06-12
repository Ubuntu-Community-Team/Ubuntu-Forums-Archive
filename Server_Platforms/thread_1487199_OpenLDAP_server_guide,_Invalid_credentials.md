---
title: "OpenLDAP server guide, Invalid credentials"
date: 2010-05-18
forum: Server Platforms
---

### Post by cswingle on 2010-05-18
Greetings!

I'm trying to set up an OpenLDAP server on a clean install of 10.04 server (AMD64).  Following the server guide ([https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)) I get down to the "Setting up ACL" step:

$ ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W oldDatabase=hdb oldAccess

This command fails with "ldap_bind: Invalid credentials (49)"

When I replace the dn with what it seems like it should be:

$ ldapsearch -xLLL -b cn=config -D cn=admin,dc=example,dc=com -W oldDatabase=hdb  oldAccess

I get "No such object (32)"

I have a feeling this is because 10.04 no longer asks you for the admin username and password during the initial debconf (nor does dpkg-reconfigure).

I can continue through the guide using this form of the commands (which were used earlier in the Guide):

$ sudo ldapsearch -Y EXTERNAL -H ldapi:/// -b cn=config olcDatabase=hdb olcAccess

but I'm a little concerned that I'm not able to properly use the admin user to make LDAP changes to the configuration.  It also seems like the Server Guide ought to use the 'sudo ... -Y EXTERNAL' form of the commands throughout if cn=admin,cn=config isn't going to work.

Should I worry?

Thanks,

Chris

---

### Post by cswingle on 2010-05-19
Sorry to reply to myself, but apparently this is a bug in the lucid Server Guide.  Reply #6 in Bug #333733 says:

[FONT=Courier New]The ACL section needs to be updated to use the new:[/FONT]
 [FONT=Courier New]   sudo ldapsearch -c -Y EXTERNAL -H ldapi:///  -b cn=config[/FONT]
 [FONT=Courier New]format.[/FONT]


I'd add that there are other sections (like the OpenLDAP Samba section) that also should be revised to reflect the new -b cn=config command format.

Cheers,

Chris

---

### Post by fnmblot on 2010-06-01
Wow!  I can't thank you enough for posting this.  I have been pulling my hair out for 2 days over this one!!

fnmblot

---

### Post by zaphod777 on 2010-07-01
so how do you update the acl so users can change their passwords?

---

### Post by elsurexiste on 2010-07-28
Yeah, I thought about that too when I was reading... I saw a couple of ldapsearch and nothing more.

---

### Post by daarkstaar on 2010-10-07
Thanks a million cswingle, like fnmblot I've been banging my head against a wall on this!!!

It would be nice if someone could update the server guide .. hint, hint!  ;)

---

