---
title: "Ubuntu 13.10, Samba 4, Domain Admin as root."
date: 2013-10-20
forum: Server Platforms
---

### Post by Roswebnet on 2013-10-20
HI everyone,
 The new Ubuntu Server 13.10 brought the new-old (recent is 4.1.0 from samba.org) stable version of samba 4 (4.0.3) in official Ubuntu repository. Installation after few standard steps, and a corrections in definition of the BIND server goes well.
 According this tutorial:
 [http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing](http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing)
 I configured an LDAP authentication, based on simple bind method.
 
 First what I tried to do after configuration is to login as a DC user into Ubuntu server. It goes well. However, I cannot run from this user a sudo commands. E.g., When I type the *sudo su &#8211;*
 I am always getting error by which user are not in the list of the sudoers.
 
 The user is a member of the Domain Admins active directory (DOT.LAN) group. After documentation researching I found possible solution. The main idea is to add by /etc/sudoers
 
 ```
# Members of the admin group may gain root privileges
  %dot\\domain^admins ALL=(ALL) ALL
```
 
 Still the user cannot get the *sudo *rights on the Samba4 server&#8230;
  
 Why? How can I solve it? Any ideas or suggestions?
 Thank you.

---

### Post by Toxic64 on 2013-10-20
adduser <username> sudo should work.

---

### Post by Roswebnet on 2013-10-20
But It means, that I need with hands add a user in Ubuntu which are already exist in SAMBA4... Not very handy.
 
 I believe there is other solution which is more practical.

---

### Post by Toxic64 on 2013-10-20
I d have to try that... though practically on a server you'd only need admins to get entiteled to launch sudo commands (there shouldn't be that many)

---

### Post by Roswebnet on 2013-10-21
I have found the solution.

After researching sudo and sudo-ldap packages. I just took a break and start with careful reading of the sudoers manpage:
[http://manpages.ubuntu.com/manpages/raring/en/man5/sudoers.5.html](http://manpages.ubuntu.com/manpages/raring/en/man5/sudoers.5.html)

I found the relevant information:

> A user name, uid, group, gid, netgroup, nonunix_group or nonunix_gid may
     be enclosed in double quotes to avoid the need for escaping special
     characters.  [COLOR=#ff0000]Alternately, special characters may be specified in escaped
     hex mode, e.g. \x20 for space.[/COLOR]  When using double quotes, any prefix
     characters must be included inside the quotes.

     The actual nonunix_group and nonunix_gid syntax depends on the underlying
     group provider plugin (see the _group_plugin_ description below).  For
     instance, the QAS AD plugin supports the following formats:

     [COLOR=#ff0000]**·**     Group in the same domain: "%:Group Name"

     **·**     Group in any domain: "%:Group [/COLOR][EMAIL="Name@FULLY.QUALIFIED.DOMAIN"][COLOR=#ff0000]Name@FULLY.QUALIFIED.DOMAIN[/COLOR][/EMAIL][COLOR=#ff0000]"[/COLOR]

     **·**     Group SID: "%:S-1-2-34-5678901234-5678901234-5678901234-567

After some experiments I put this string in my /etc/sudoers file:

```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%Domain\x20Admins ALL=(ALL) ALL
```

It is working now great. Only users from Domain Admins (AD group) and admin (unix group) now can play as a root.

see screenshot:
[IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Screenshot%202013-10-22%2000.04.44.png[/IMG]

By the way, [EMAIL="john.doe@dot.lan"]john.doe@dot.lan[/EMAIL] will not work on putty. So the john.doe will work. However ssh [EMAIL="john.doe@DOT.LAN"]john.doe@DOT.LAN[/EMAIL] will work on server.

---

### Post by faure212 on 2013-10-25
How did you even get samba4 to work?  I tried to upgrade from 13.04 to 13.10 on 5 different machines, and in each case the upgrade failed because of problems with samba4.  The system told me to "use --fix to fix these errors" but without further instructions I was lost.
It is a shame that with each release (L)ubuntu is becoming more of a pain....

---

### Post by Roswebnet on 2013-11-02
Sorry I saw your post only now.
 
 I did not upgrade. I use clean install. If you like, I can post a tutorial in tutorial section how to setup the SAMBA 4.0.3. (Ubuntu Package).

In addition, Ubuntu does not like during upgrade handle with unofficial packages. Therefore is better, to use clean install and migrate data from old server to new one.
Don't ask me how to do this :) I know how it's happened on windows, but not on Linux.

---

