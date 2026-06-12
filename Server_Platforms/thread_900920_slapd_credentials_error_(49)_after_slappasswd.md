---
title: "slapd credentials error (49) after slappasswd"
date: 2008-08-25
forum: Server Platforms
---

### Post by 3strandchords on 2008-08-25
Hi... I'm a relative n00b, so I apologize for the lameness of the question.

I'm running ubuntu 8.04, fully updated, with OpenLDAP 2.4.9.  I'm having trouble posting records via ldapadd with the following error:
ldap_bind: Invalid credentials (49)

Here's the relevant portion of slapd.conf
```
# The base of your directory in database #1
suffix "dc=happy-filler,dc=com"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn "cn=admin,dc=happy-filler,dc=com"
rootpw MUQOZ0bhbetcetcFUutqPqXxzLHt1p
```

The rootpw value is the hash that I received out of the slappasswd process.

I'm assuming that I've done something wrong either in how I've appended the hashed password *or* in how the rootdn user is set up in slapd.conf 

Any help is appreciated...

---

### Post by 3strandchords on 2008-08-26
Ok, I caught one problem...  First off, I wasn't including the {encryption} label for the rootpw entry in slapd.conf

That, I'm sure, made a difference.  However, updating the password with slappasswd, adding the new password (with {tag}) to slapd.conf, and restarting the daemon still yields the same error.



Thoughts?

---

### Post by california-ken on 2009-02-09
I am having the same problem.  I've spent hours trying to find a solution for it.  I am running Ubintu Server 8.10 with kernel 2.6.27-7 server.

My latest try followed these steps posted in another Ubuntuforum thread:

[http://ubuntuforums.org/showthread.php?t=57118](http://ubuntuforums.org/showthread.php?t=57118)

 Re: ldap_bind: Invalid credentials (49) error
strange, this is old bug but I'm still getting error like this on ubuntu-8.04. after stuck on a few hours, finally i can fix this.

run this:
....
rm -rf /var/backups/unknown-2.4.7-6ubuntu2.ldapdb
dpkg-reconfigure slapd
/etc/init.d/slapd restart

as the instruction on [http://www.debuntu.org/ldap-server-a...-ldap-clients:](http://www.debuntu.org/ldap-server-a...-ldap-clients:) then I re-run:

ldapadd -x -W -D "cn=admin,dc=debuntu,dc=local" -f ~/people_group.ldif
ldapadd -x -W -D "cn=admin,dc=debuntu,dc=local" -f ~/group.ldif
ldapadd -x -W -D "cn=admin,dc=debuntu,dc=local" -f ~/passwd.ldif
Last edited by 4ziz; July 9th, 2008 at 08:27 PM..
4ziz is offline Report Post   	Reply With Quote

This did not solve the problem!  The slapd reconfigure routine includes setting a new LDAP admin password.  However the ldapadd statements still produce the same invalid credentials error using the new password set in the reconfigure routine.  It seems as though the reconfigure procedure is creating/modifing a slapd.conf file somewhere other the standard location of /etc/ldap.  

I hope someone can help resolve the Invalid Credentials (49) problem.  There must be 100's of references to it on the Internet.

---

