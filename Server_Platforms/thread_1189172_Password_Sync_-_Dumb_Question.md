---
title: "Password Sync - Dumb Question?"
date: 2009-06-16
forum: Server Platforms
---

### Post by rshprd on 2009-06-16
Hopefully this is not a dumb question....  in my own defense, I've searched multiple archives and have not found anything helpful.

I have multiple 8.04LTR based servers in my network.  User accounts are duplicated on all servers as each server is providing a specific resource.

I would like to be able to change, or even allow users to change their password in one location and have that change propagate out to the other servers.  My thought was to create an internal web page with PHP to let the users change their password, but before I can get to that step, I need to figure out the actual process, if any, to propagate the change in the first place.

Thanks!
RES

---

### Post by binary10 on 2009-06-16
Unless I'm missing something with 8.04 or yousetup, but have you looked at LDAP or older still  NIS or NIS+

Then just have a one account for each user  in one place..

---

### Post by HermanAB on 2009-06-16
There are various options:
Redhat Directory Server, Novell Directory Server, NIS and Samba Domain Controller are the best known.  They are all based on LDAP.

If there is any chance of having Windows clients, then you need to use a Samba Domain Controller.  Details on the Samba web site in the Official Howto.

Hope that helps!

---

### Post by rshprd on 2009-06-16
Thanks All!   

That sadly, is what I figured was the answer.  :(  Played with LDAP a bit, so it seems I have a lot more reading to do before I can get there!  Was hoping maybe there was a simpler way.

Sometimes you just have to hear it from somebody else! :p

Thanks in any event!

---

### Post by binary10 on 2009-06-16
To be honest LDAP isn't that bad once you get into it, but unlike the previous caller I wouldn't say NIS was based on LDAP. NIS you have your flat files as source (as you'd see them normally like /etc/passwd or any data/text you want to be distributed) which each time a passwd modification is made then it updates a db (a map). The db which really you rarely need to go a touch. NIS is insecure as far as password changing goes as they end up going across the wire in clear text just when the users modify them, LDAP can be configured as different types. 

LDAP - Sure there's a bit of fiddly configuration to do, and some verbose syntax to manipulate the config.. but once you have your initial setup and perhaps a few replicas, you can start installing 'ldapscripts' and then  adding/modifying users doesn't have to be so daunting.

I've setup a few LDAP servers and shed loads of mixed styles NIS boxes in the past. NIS is simpler layout to see (a makefile + some source text files (passwd.nis)) but LDAP should give you a better expandable solution if you have other software that might use additional schemas.

Check out the 8.04 LDAP setup.
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

The usual catch outs on the configuration of the LIBNSS PAM and having mismatching lookups, aka.. ldap.conf saying dn: ou=Users,dc=nodomain and you placing people into Ou=People,dc=nodomain

---

