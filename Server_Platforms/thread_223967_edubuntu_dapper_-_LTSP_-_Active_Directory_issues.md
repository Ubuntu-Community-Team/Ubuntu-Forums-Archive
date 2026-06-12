---
title: "edubuntu dapper - LTSP - Active Directory issues"
date: 2006-07-27
forum: Server Platforms
---

### Post by bpdoyle@gmail.com on 2006-07-27
Not sure if this is the right spot to post this question, if not please accept my apologies.

I have been trying to setup an edubuntu server that we can run a lab of diskless thin clients from with the LTSP server.  But we are a microsoft shop with Active Directory currently.  So to minimize some of the management issues with users, I just want to set the server up to authenticate logins through AD.

I currently have setup kerberos,samba and winbind, and have joined the domain.  I can login locally to the edubuntu server and it authenticates my usernames through AD fine.

I can get my thin client to boot up from the LTSP server and I can use my local login(it logs in fine), but it will not authenticate a domain user through the AD.  It just flashes a black screen and then goes back to the login screen.

I feel like I didn't correctly setup something in PAM maybe, and a module is not getting loaded by the login during LTSP, but I am not sure.

any ideas?

Thanks.

---

### Post by bpdoyle@gmail.com on 2006-07-27
just for more of a reference.

I configured my authentication by running through this winbindHOWTo from the wiki pages.
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

Everything is setup just like in this example except for the editing for the /etc/pam.d/sudo file.  When I edited that twice before, like it says, I was unable to sudo after than and was pretty much locked out of making any changes, because I left the root account disabled.  So I don't know if not editing that file is part of my problem or not.

I also have two NICs in my box with ip forwarding enable so my inside NIC for the thin client subnet, can be routed to the outside NIC via NAT. This is working fine.  When I login to the thin client with my local linuxbox user I can browse just fine and ping everything.

My LTSP configuration is bascially the default.  All I did was configure my inside IP to be 192.168.0.1, start the dhcp server, and then update my sshkeys with
ltsp-update-sshkeys

Thanks again.

---

### Post by bpdoyle@gmail.com on 2006-07-31
Still no ideas huh?

---

### Post by fnjordy on 2006-08-02
This is how I did it:

[http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication](http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication)

---

### Post by Glut on 2006-08-03
Can you post:
/etc/pam.d/common-auth, common-account
/var/log/auth.log
/etc/samba/smb.conf

Thanks.

---

### Post by dan-arwed on 2007-08-02
Hi all,

it is indeed an old thread but till today I didn't find an answer to this problem in the net... A friend of mine would like to setup exactly the specified network:

*** 1) ThinServer integrated in AD, probably via Samba+winbind+kerbeors.
Integration means "member of AD-domain" and "authenticating against AD", of course.

*** 2) Thin-Clients connected to ThinServer, any login
shouid be authenticated with credentials from the AD database.

I myself managed to integrate a samba-server into AD, which was quite straight forward. But I'm still asking myself how this is working with ThinClients. Is there any pam-module telling the clients to authenticate  via samba against AD? 

Hope to fin help here.
Best regards,

Dan

---

### Post by dan-arwed on 2007-08-02
Hmh,

I found a detailed description of various setups concerning AD + LSTP + ThinClients:

[http://math.univ-lille1.fr/~hafidi/terminal-services/index.html](http://math.univ-lille1.fr/~hafidi/terminal-services/index.html)

Seems worth to have a look at it =) 

Regards Dan

---

