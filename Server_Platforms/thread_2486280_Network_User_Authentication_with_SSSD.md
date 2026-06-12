---
title: "Network User Authentication with SSSD"
date: 2023-04-25
forum: Server Platforms
---

### Post by civilpolisen on 2023-04-25
We're about to implement these things at the office.
[https://ubuntu.com/server/docs/service-sssd](https://ubuntu.com/server/docs/service-sssd)

I assume the first step is to install and to create AD, Active Directory...
[https://sssd.io/docs/quick-start.html](https://sssd.io/docs/quick-start.html)

Any helpful comments on this matter would be thankfull!

Why is there no helpful documentation, guide-lines or instructions for people using Ubuntu avalible!?

---

### Post by TheFu on 2023-04-25
> **civilpolisen said:**
>  Why is there no helpful documentation, guide-lines or instructions for people using Ubuntu avalible!?

That's a highly subjective complaint.  There's lots of documentation, whether it is useful or not depends on your Linux skill level, I suspect.  Google found these quickly:
[https://ubuntu.com/server/docs/service-ldap](https://ubuntu.com/server/docs/service-ldap)
[https://ubuntu.com/server/docs/kerberos-introduction](https://ubuntu.com/server/docs/kerberos-introduction)
[https://ubuntu.com/server/docs/service-sssd](https://ubuntu.com/server/docs/service-sssd)

There are a number of 3rd party how-to articles too.
In 20.04 and later Ubuntu Desktops, they made connecting the desktop to a MS-AD pretty easy at install time, I hear. We don't have any Microsoft in our company, so I don't know personally how easy or hard it might be.

---

### Post by civilpolisen on 2023-04-26
Thank you for the links! I'm fully aware of that my skills in the open-source businesss is quite limited! That's why I post my questions in such forum as this...!
I've always done so and it's been very helpfull for me! I remember back in 1997 when my "hunger to change the world" opened the door to the wonders of tech-forum...!

I did watch one film yesterda when the "service-ldap" -procedure was part of the content.
I'll continue today...!

* * * * * * * *
Just a notice: We don't have the need of connecting clients from other operating systems such as Microsoft and / or Apple.



* * * * * * * *
This film was very helpfull the second time, with the first link above! :-) 

**Setting up OpenLDAP Server in Ubuntu 18.04 LTS**
[https://www.youtube.com/watch?v=2r1VVJzY2Rw](https://www.youtube.com/watch?v=2r1VVJzY2Rw)

However, I have version 22.04 so... maybe that's why the film differ from my reality!?

---

### Post by civilpolisen on 2023-04-26
I include some of my work and to show these unexpected errors that seems to hunt me while the authour handle these things without getting cought!

```
jakob@sssd:~$ sudo tree /etc/ldap/slapd.d/
/etc/ldap/slapd.d/
&#9500;&#9472;&#9472; cn=config
&#9474;   &#9500;&#9472;&#9472; cn=module{0}.ldif
&#9474;   &#9500;&#9472;&#9472; cn=schema
&#9474;   &#9474;   &#9500;&#9472;&#9472; cn={0}core.ldif
&#9474;   &#9474;   &#9500;&#9472;&#9472; cn={1}cosine.ldif
&#9474;   &#9474;   &#9500;&#9472;&#9472; cn={2}nis.ldif
&#9474;   &#9474;   &#9492;&#9472;&#9472; cn={3}inetorgperson.ldif
&#9474;   &#9500;&#9472;&#9472; cn=schema.ldif
&#9474;   &#9500;&#9472;&#9472; olcDatabase={0}config.ldif
&#9474;   &#9500;&#9472;&#9472; olcDatabase={-1}frontend.ldif
&#9474;   &#9492;&#9472;&#9472; olcDatabase={1}mdb.ldif
&#9492;&#9472;&#9472; cn=config.ldif

```

```
  GNU nano 6.2  add_entries.ldif                                                                             
dn: ou=Employee,dc=practice,dc=net
objectClass: organizationUnit
ou: Employee

dn: ou=Groups,dc=practice,dc=net
objectClass: organizationalUnit
ou: Groups

dn: cn=developers,ou=Groups,dc=practice,dc=net
objectClass: posixGroup
cn: developers
gidNumber:5000

dn: uid=freddy,ou=Employee,dc=practice,dc=net
obejctClass: inetOrgPerson
objectClass: postxAccount
objectClass: shadowAccount
uid: freddy
sn: smith
givenName: Freddy
cn: Freddy Smith
displayname: Freddy Smith
uidNumber: 10000
gidNumber: 5000
userPassword: freddy123
loginShell: /bin/bash
homeDirectory: /home/freddy/
```

```
jakob@sssd:~$ ldapadd -x -D cn=admin,dc=practice,dc=net -W -f add_entries.ldif 
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)

```

```
jakob@sssd:~$ ldapsearch -x -LLL -b dc=practice,dc=net "uid=freddy" cn sn gidNumber uidNumber givenName
No such object (32)

```

So... What does "Invalid credentials (49)" and "No such object (32)" referes to!?

---

### Post by civilpolisen on 2023-04-27
**How do I configure Apache2 with the home directory of phpldapadmin?**

I've done a few tutorials that has one thing in common, they don't complete the task! At the end they fail and I try to solve.
What do I write in the root folder of Apache to make it work along with phpldapadmin?

---

### Post by TheFu on 2023-04-27
I've never used any admin webapps that use PHP.  The security risks are just too great, IMHO.  We don't use apache either.
This question is completely different and if you really want help with it, creating a new thread is strongly recommended.

Most reputable tutorials spell out exactly what needs to happen. Sometimes it is in the text, not in copy/paste commands, because your setup is different and customizations are required.  When someone is new to Ubuntu, it is best to find tutorials from websites that have "ubuntu" in the domainname part AND are for the release you are using. 

Sometimes different subsystems change from release to release. Without the history of each subsystem, it is easy to assume that nothing changes and to be burned.  Most of the time, things don't change THAT much, but between Apache 2.2 and 2.4, lots of things changed in the required settings that burned many people.  PhpWebApps are always changing, since different php versions break compatibility all the time.

For someone trusting the world and not wanting to learn all the details, there are docker instances for many server-side apps.  Sometimes there are snap packages from Canonical too.  Just be certain the provider of the package is trustworthy.  The Docker repos can be full of nefarious images, which need to be avoided.  That goes for any PPA used on any Debian-based distro and for snaps, flatpaks, and appimages too.

I didn't look to see if there's a phpldapadmin docker image ... or any other. We didn't used that to maintain users in our deployment.  Sometimes I'd wonder if it would have been easier/better to do that than what we did.  Some days I really miss NIS ... er ... except the poor security.

---

