---
title: "LDAP &quot;roaming&quot; users / PAM"
date: 2005-12-16
forum: Server Platforms
---

### Post by billybofh on 2005-12-16
Hi,

I have a central LDAP authentication system which works very well.  I'm now looking to support users with "take home" machines how-ever.  This means that :

1. They will have root/sudo access
2. They will sometimes be disconnected from our central LDAP db & network in general

Generally I can configure the machines so that they cannot su to another user by putting limits into PAM (though they could, in theory un-do that limit).  I've also set things up so that these users get a pam_mkhomedir.so created home area on their local machine and then can copy files to and from their "real" network $HOME via smb.

How-ever - if they are disconnected from the LDAP server then they still have to be able to log in and get their files - so I'm creating a matching local user which is used as a fall-through if the LDAP login is unavailable.  So far, so good.......

The thing I would like to achieve is a scheme similar to OS-X or recent-ish windows whereby when someone changes their password it is changed both locally and in LDAP.  So if a user takes their machine home, changess the local password, then reconnected to our network that the password change is sync'd up automagically.  I've searched about to try and find out if there is a nice handy package which will take care of this - but to no avail so far.

Does anyone have any suggestions?  Even a cludge would do..... :)


Billy.

---

### Post by nocturn on 2005-12-16
There is a pam_ldap cache module (don't have the link handy).
Basicly, a user that logs on using the LDAP credentials gets cached and can be used offline if I remember correctly.

---

### Post by billybofh on 2005-12-17
Ahhh - thanks!  A bit of a search turns up the "pam_ccreds.so" module.  Seems to take a bit of jigging, but it looks like the kind of thing I'm after.  Thanks for the pointer!

---

### Post by pdaoust on 2006-02-01
**billybofh**: dude, please please tell us how on earth you managed to get an LDAP authentication server working well! do you have a HOWTO I can take a look at? I'm trying to get centralised authentication working, and I can't find anything really clear or concrete on the Web.

---

### Post by nocturn on 2006-02-02
A start:

[http://people.debian.org/~torsten/ldapnss.html](http://people.debian.org/~torsten/ldapnss.html)

About LDAP with Kerberos (my setup):

[http://www.ofb.net/~jheiss/krbldap/howto.html](http://www.ofb.net/~jheiss/krbldap/howto.html)

---

### Post by billybofh on 2006-02-02
pdaoust: I used Fedora Directory server ([http://directory.fedora.redhat.com/wiki/Main_Page](http://directory.fedora.redhat.com/wiki/Main_Page)) and the made the PAM & nsswitch.conf changes as detailed in the link that nocturn gave.  Fedora Directory is *much* nicer to use than OpenLDAP....

---

