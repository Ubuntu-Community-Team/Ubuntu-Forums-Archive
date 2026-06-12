---
title: "Samba PDC or SMBLDAP - Advantages and disadvantages"
date: 2006-02-28
forum: Server Platforms
---

### Post by linuxmad on 2006-02-28
Hi,
I am planning to set up a PDC in my small network (15) machines running Winxp Pro. I tested a few configs based in this how-to [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10), and got my PDC working. But now, i came to "know" the smbldap which i really don't know anything about, and want to know the major differences between samba and smbldap. As far as i understand Samba Pdc works like a NT4 server, while smbldap works as 2000/2003 Windows Server implementing ADirectory. Is this so?
I even tried this [http://www.majen.net/smbldap/](http://www.majen.net/smbldap/) script but, when adding my first workstation i got an error saying that "user not found".

At this point I am looking like a fool in the midlle of a brigde. Where to go??
Which one is better for me?? And a good how-to like the one found at How-to forge for Samba PDC??
Thanks
Jose

---

### Post by gpredrag on 2006-02-28
I have just achieved Samba+Ldap(+Heimdal)on Debian server (on testing server, that is. Now rolling on on production). It is same on Ubuntu.
Samba 3.x can act as NT4.0 PDC replacement in any case, or member server in Active directory.
LDAP backend doesn't make it act as W2k3 server, but it will help you to have B(ackup)D(omain)C(ontrollers)s and to centralize user management. If you plan to have only one samba DC server now AND IN FUTURE, it will make no difference for windows clients.
It can be tricky if you haven't had experience with ldap but it isn't that hard as people think.
Basicaly I have followed HOWTO from samba site.
Difference is that Ubuntu/Debian uses separate files for nss_ldap and pam_ldap, but that was clear from packages documentation. Configuration for pam_ldap was also explained in debian/ubuntu packages docs.
configure.pl mentioned in HOWTOs to configure smbldap tools is gziped in smbldap documentation for that package. You also have smbldap tools  package in ubuntu.
I actually use debian testing, and with that nss_ldap has effect on udev(!). But that also is documented in udev packages docs (wich I have found out after 2 days of bangging my head against the wall).
Anyway, happy reading.

---

### Post by linuxmad on 2006-03-01
gpredrag, thanks for your reply. 
I plan to have only one server, now and in the future, so i guess i will pass the ldap support. Still i have one doubt that concerns the users and groups policies: Are the windows groups/users policies better supported using ldap backend?? The reason I am asking this is because i will use poledit to create user policies, and after that place the file containing those policies in netlogon share. If the ldap backend makes groups/users policies easier to implement i would stick to it.
Thanks,
josé

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=linuxmad]As far as i understand Samba Pdc works like a NT4 server, while smbldap works as 2000/2003 Windows Server implementing ADirectory. Is this so?[/quote]Nope.

The only advantage SMB+LDAP gives is centralized storage of account data, so you could have UNIX accounts authenticate and use the same backend.

That's not worth it for many installations.

> Are the windows groups/users policies better supported using ldap backend?? No.  They're supported at the NT4 level period.  Which isn't likely what you want, so you should probably just buy Windows 2003 Server.

---

### Post by linuxmad on 2006-03-01
> Which isn't likely what you want, so you should probably just buy Windows 2003 Server.
... NO WAY... That's the last thing i would think. I will stick with my samba PDC and use poledit to create users and group policies.
Thanks

---

### Post by gpredrag on 2006-03-01
Just to make it clear...
Having samba PDC without LDAP doesn't force you to have only one samba server, but (pretty much) limits you to only one domain controller. You may have additional samba memeber servers (for file and print sharing) using winbind to map usernames from PDC to usernames on other servers.
But from perspective of windows clients or policies ldap/noldap makes no difference.
AD stuff is planed for samba 4 (with ldap + heimdal kerberos built in).

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=linuxmad]... NO WAY... That's the last thing i would think.[/quote]Yes way.  Policies enforced by NT4 PDC are tatooed on the registry, the changes are permament and you can lock yourself out if you're not careful.

That's ignoring all the extra functionality having an AD server gives you.

I'm not saying this as a troll, I'm being perfectly honest.  From a technical perspective, AD is the correct solution.  NT4 PDCs are obsolete, and with good cause.  This includes using Samba as one.

Obviously, if other issues trump (e.g., cost) then Samba as an NT4 PDC is a good fallback plan.  

But from a technical perspective, recommending an NT4 PDC is simply silly.

---

### Post by Ubuntu Warrior on 2006-05-18
Although LordHunter's comments rile me somewhat I must agree that NT (or Samba) PDC's are not exactly state-of-the-art. Having said that we have saved enormous amounts of money avoiding the Windows network option and have implemented an Ubuntu Samba PDC-based network (with LDAP at the backend handling directory and auth, etc.). Works like a dream and, frankly, we just don't need the added functionality of a 2003 solution.

Would really appreciate a better Samba solution but for now will make do and spend my money elsewhere. BTW we run a single-site organisation with about 250 users.

---

### Post by djdicbob on 2006-07-22
> **linuxmad said:**
> gpredrag, thanks for your reply. 
I plan to have only one server, now and in the future, so i guess i will pass the ldap support. Still i have one doubt that concerns the users and groups policies: Are the windows groups/users policies better supported using ldap backend?? The reason I am asking this is because i will use poledit to create user policies, and after that place the file containing those policies in netlogon share. If the ldap backend makes groups/users policies easier to implement i would stick to it.
Thanks,
josé

In my personal experence with group and user policies in a mixed environment (Windoze & Linux)....Once you set the policies, only make changes to file permissions from the exact OS the file is created.  Example:  A win user wants you to make his/her files viewable by another group.  If that user uses Windoze, make that Admin access level change from the WIn OS.  Likewise for GNU!

my 2 cents:)

---

### Post by Mouth on 2006-07-23
I want to be able to install/use LDAP on my Ubuntu Server so that I have a single/central addressbook that I can use for all email clients (web, desktop client, web lookup, etc.)

What would people suggest?

---

### Post by Ubuntu Warrior on 2006-09-03
I would strongly recommend using Ubuntu Dapper, OpenLDAP and Samba with smbldap stuff from idealx. This gives you the ability to run an NT-style domain with a PDC hosted on Linux. The OpenLDAP server can be used to hold the directory info and it all works like a charm. Install is not that easy though so make sure you read every word from the smbldap install support docs.

We make use of the smbldap scripts for managing accounts but would much prefer a web-based graphical tool but haven't come across any yet.

---

### Post by etcpool on 2006-09-21
smbldap-tools is now already available at ubuntu respository?

0.9.2-3

---

### Post by fnjordy on 2006-09-22
> **Mouth said:**
> I want to be able to install/use LDAP on my Ubuntu Server so that I have a single/central addressbook that I can use for all email clients (web, desktop client, web lookup, etc.)

What would people suggest?

Anything special you are looking for?  There is not much real choice, OpenLDAP is the popular one, a new directory server is available from RedHat called [RedHat DS](http://directory.fedora.redhat.com/wiki/Howto:DebianUbuntu).  A previous discussion is available on the forums:

[http://www.ubuntuforums.org/archive/index.php/t-206202.html](http://www.ubuntuforums.org/archive/index.php/t-206202.html)

As an alternative I wrote an appliance for shared addressbook using Samba 4, and a plugin for Mozilla Thunderbird to directly add entries.  You normally need to use the LDAP tools or create your own interface to add and update a LDAP server.  You can test out the VMware virtual appliance version here:

[http://developer.novell.com/wiki/index.php/HOWTO:_Mozilla_Thunderbird_Address_Book](http://developer.novell.com/wiki/index.php/HOWTO:_Mozilla_Thunderbird_Address_Book)

---

### Post by datakid on 2006-09-28
> **Mouth said:**
> I want to be able to install/use LDAP on my Ubuntu Server so that I have a single/central addressbook that I can use for all email clients (web, desktop client, web lookup, etc.)

What would people suggest?

Um, I'm not quite sure what you are asking here - what suggestion are you after?

The answer is yes, ldap can do what you want. So LDAP is a good solution??! You have to answer that one yourself :)

As for the conversation above, I think it should be made clear that samba does make a good PDC (ie, single server domain) at NT level, but I'm pretty sure you cannot use group policies. 

If you want to use group policies, you will need a Windows server (2K, 2K3) and it will have to be the PDC - you can still use samba as your BDC, but group policies are a (> Windows Server 2000) functionality, and as Samba (atm) only does (< Windows Server 2000), it cannot be used as such. 

Therefore djdicbob's last comments are probably closest to getting what you want. I cannot guarantee that it will work though - it just seems to be the best solution.

Note that you can better mimic AD by using a SAMBA/LDAP/Kerberos combo, but it is more difficult to set up, and I think that it still wouldn't give you the group policy ability you so desire.

Samba 4, currently in production, maybe at least a year away, will be able to do all things Server 2K3, including group policy (as I am lead to believe).

Hope this helps

---

