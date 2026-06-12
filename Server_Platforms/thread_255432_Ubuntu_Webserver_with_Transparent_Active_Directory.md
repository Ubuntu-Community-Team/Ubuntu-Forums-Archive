---
title: "Ubuntu Webserver with Transparent Active Directory Logon?"
date: 2006-09-11
forum: Server Platforms
---

### Post by OneSeventeen on 2006-09-11
Is it possible to have an Ubuntu webserver running Apache 2 and PHP 5 that automatically knows the username of the person browsing the site?

This will be on an internal network only on an Active Directory, with all the users under the same Domain.

Any ideas?

(I really really really don't want to install another windows server!)

---

### Post by Glut on 2006-09-12
I assume that you want authentication using NTLM, so users can be spared the pain of having to retype (or have ie remember) a password.
It apparently can be done with samba, First you will want to get NTLM working with Samba, then you want to download libpam_smb from the debian repos or compile from source, because I don't believe that it's in the Ubuntu archives. Then you want to use libapache2-mod-auth-pam to authenticate via pam. Helpful thread here: [http://ubuntuforums.org/archive/index.php/t-10491.html](http://ubuntuforums.org/archive/index.php/t-10491.html)

Alternativley there is a mod_ntlm_auth out there that, should you spend enough time compiling the thing may do it out of the box. A quick search reveals a great deal of pain has been caused on users trying to compile the thing.

If you want to ditch the passwordless authentication, single signon is easy enough with your choice of winbind, kerberos or LDAP. 

So yes, it is possible - but highly dependant on the amount of pain you wish to inflict on yourself.

---

### Post by fnjordy on 2006-09-12
SPNEGO is a lot easier if its all Firefox clients and Unix/Linux servers.  It is possible for Internet Explorer but i'm not sure its worth the effort.  The authentication requires HTTPS for security because Kerberos tabs flying about the network is apparently not safe.  In the end this makes for a slower web experience: requests are all doubled and encrypted over SSL and a very inconvenient install and upgrades of Kerberos Apache modules.

If you author your application servers correctly though, similar to gmail you only need HTTPS and the SPNEGO handshake for an initial password-less login, subsequently you can use a cookied session key.  Obviously this isn't a trivial solution either.

Read more on the mod_auth_kerb website and mailing lists:

[http://modauthkerb.sourceforge.net/](http://modauthkerb.sourceforge.net/)
[http://sourceforge.net/mailarchive/forum.php?forum_id=9893](http://sourceforge.net/mailarchive/forum.php?forum_id=9893)

---

### Post by OneSeventeen on 2006-09-12
Awesome, I'll start playing around with using PAM authentication to see if I can get this done.

I am on a Windows/IE network (hence the Active Directory), so the SPNEGO solution won't work for me, but definitely worth looking into.

---

### Post by OneSeventeen on 2006-10-09
How do I get NTLM working with Samba?

---

### Post by OneSeventeen on 2006-10-09
Okay, my first step was to get a fully functional samba server and learn a bit more about authentication.

My problem comes when I hit step 12 of [this guide](http://us4.samba.org/samba/docs/man/Samba-Guide/unixclients.html#adssdm) and I type in: ```
getent group
```and all I get in return is:> root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:demas
tty:x:5:
disk:x:6:
lp:x:7:cupsys
(etc, etc, etc)

When according to the help file, I should be getting all of my domain groups.

This also leads to not being able to view file shares.  So if I go to \\servername\username on my windows box it prompts me for a username and password, but none of the domain usernames and passwords will work.  (nor will local machine usernames/passwords)

any tips on getting this Ubuntu server up and running?

---

### Post by OneSeventeen on 2006-10-09
In an effort to continue talking to myself online, I thought I'd follow up with a solution and new problem:

The solution to my existing problem (getent passwd returns only local users), I simply told passwd to pull from "file winbind" rather than "file ldap", which was done by editing /etc/nsswitch.conf

The new problem is when I am on my windows box and type in \\servername\username it still won't authenticate me.  I've been told this is because pam needs to be set to authenticate against winbind or something like that, so I'll have to figure out how to do that without messing up my ubuntu server.

Any tips on how to do that without messing up my server would be appreciated :D

---

### Post by twistedtwig on 2006-10-10
sounds complicated :P

wish i could help but am following it with great interest, one of the things i have been thinking about learning how to do.

cheers for all the info :)

Twiggy

---

### Post by breezybob on 2006-10-11
Ihave been playing with a similar setup.

[http://www.enterprisenetworkingplanet.com/netos/article.php/3502441](http://www.enterprisenetworkingplanet.com/netos/article.php/3502441)

The above was quite useful, you will need to edit a few files in /etc/pam.d to enable pam authentication

---

