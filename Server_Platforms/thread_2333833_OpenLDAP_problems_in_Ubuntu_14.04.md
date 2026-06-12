---
title: "OpenLDAP problems in Ubuntu 14.04"
date: 2016-08-13
forum: Server Platforms
---

### Post by toddpedlar on 2016-08-13
Hi all -

I have tried repeatedly to set up OpenLDAP according to the online instructions (which are poor).  So, I've grabbed slapd and ldap-utils and installed them, done the dpkg-reconfigure thing to set up the server according to my local setup, and then tried to do a test ldapadd of a user.

No matter what I do, ldapadd returns a failure with the "ldap_bind: Invalid credentials (49)" message.  I am using the right credentials (that were set up when ldap was setup).

What can be going on?  This seems a trivial issue as I have done so very little.  Why aren't the credentials recognized?

Todd

---

### Post by darkod on 2016-08-13
I have never set up OpenLDAP myself, but I assume you were looking at this?
[https://help.ubuntu.com/lts/serverguide/openldap-server.html](https://help.ubuntu.com/lts/serverguide/openldap-server.html)

If not, check it out, it might have steps that might help you.

---

### Post by toddpedlar on 2016-08-15
That's exactly what I had been trying - that list - and it wasn't working.

However, I started fresh yet again, and this time, was able actually even to make migrationtools work to take my flat /etc/passwd, etc and import them into the database.

Now...

I have several clients I'd like to run on my other machines.  They all have the user disk mounted, and are ready  to bind up as clients to the server, so as to allow users to connect to these machines via ldap authentication.

Problem is, the clients give me a ldap_sasl_interactive_bind_s: Can't contact LDAP server (-1) error when I try doing a simple ldapsearch.  Actually I get the same error on the LDAP server itself, so I can't even do local queries.  

The server is running.  I can see openldap when I do a ps -ef, and I get "slapd is running" when I do /etc/init.d/slapd status.  ldap is also listening, as confirmed various ways, including doing an nmap on the client machine, where I can see ldap listening on the right port on the server..

Yet I can't bind to the LDAP server either from it itself, or from a client.  

I'm clearly doing something wrong, but the online accessible documentation isn't helping me find it.

This is very frustrating

---

