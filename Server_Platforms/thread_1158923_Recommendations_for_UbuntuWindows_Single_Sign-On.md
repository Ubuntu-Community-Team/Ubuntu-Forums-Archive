---
title: "Recommendations for Ubuntu/Windows Single Sign-On?"
date: 2009-05-14
forum: Server Platforms
---

### Post by lightnb on 2009-05-14
We have several computers on our network, some of which are Ubuntu Desktops, some are running Windows XP Pro.

We'd like to implement an elegant single sign-on solution that will allow us to use a single username/password record on the server to authenticate and authorise users on both the Windows and Ubuntu clients, for the following services:

[LIST]
[*] Operating system login
[*] Dovecot (IMAPS) authentication
[*] File Sharing
[*] Calendar Server (caldavd)
[*] Print Server
[*] A PHP/mysql based web application
[/LIST]

Which service(s) (Samba, LDAP, Kerberos, etc) would you recommend for server-based authentication, authorisation, and file sharing across both platforms? The objective is to maintain the username, password and permissions in just one place, that all of the services can share.

Thanks as always,

Nick

---

### Post by HermanAB on 2009-05-14
Go to the Samba web site and read the Official Howto Guide.  Look specifically at the Domain Controller sections.

---

### Post by lightnb on 2009-05-14
I've read through [this guide]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html#id2554970") before, and we do have a working Samba PDC that our Windows clients have joined, and can log on to successfully.

What I've been unable to find is:

1. Can Ubuntu join a Samba PDC domain and use it for login? (I've found guides on connecting linux to a "true" Active Directory server, but not a Samba PDC)

2. Is there a disadvantage to using Samba to login Linux to Linux, or an inefficiency to using smb for Linux to Linux file sharing? I was under the impression that Samba was meant for Linux to Windows (or vis-versa) relationships, and better options existed for Linux to Linux. 

3. Is Samba/ Kerberos / LDAP a "pick one" choice, or a complete package together?

4. Are there any guides (that aren't incomplete or outdated) that detail how all of these elements come together to create the solution?

I've been working on this for about two weeks now and still haven't found good documentation on how all the parts come together.

---

### Post by lightnb on 2009-05-18
Or... Does anyone know how to make an Ubuntu client use a Samba PDC as a login source?

---

### Post by andyrowe on 2009-05-19
I'm a noob to ubuntu but this tutorial [http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
was a little more readable and step by step walkthrough then the samba site how to which just kind of overwelmed me. This walk through is for a linux file server running on a MS AD domain but at the top of the page is a link to a samba as PDC. Don't know if it will help you but hope so

---

### Post by lightnb on 2009-05-19
Thanks for the tip Andy.

I'm really close now (I think), but I can't quite login yet. I've joined an 8.04 machine to the domain, and I can see a list of domain users with "wbinfo -u".

It just won't log me in. I get "Access Denied". Which is different than the usual "Login Incorrect", so I know that the user name and password are correct and being accepted.

Auth.log says:

```

May 19 10:41:46 AGtest login[4674]: PAM (login) illegal module type: account-required
May 19 10:41:46 AGtest login[4674]: PAM pam_parse: expecting return value; [...pam_winbind.so]
May 19 10:41:46 AGtest login[4674]: PAM (login) no module name supplied
May 19 10:41:46 AGtest login[4674]: PAM unable to dlopen(<*unknown module path*>)
May 19 10:41:46 AGtest login[4674]: PAM [error: <*unknown module path*>: cannot open shared object file: No such file or directory]
May 19 10:41:46 AGtest login[4674]: PAM adding faulty module: <*unknown module path*>
May 19 10:41:46 AGtest login[4674]: PAM (other) illegal module type: account-required
May 19 10:41:46 AGtest login[4674]: PAM pam_parse: expecting return value; [...pam_winbind.so]
May 19 10:41:46 AGtest login[4674]: PAM (other) no module name supplied
May 19 10:41:46 AGtest login[4674]: pam_winbind(login:auth): getting password (0x00000000)
May 19 10:41:51 AGtest login[4674]: pam_winbind(login:auth): user 'domain\username' granted access
May 19 10:41:51 AGtest login[4674]: PAM no modules loaded for `login' service
May 19 10:41:51 AGtest login[4674]: Permission denied

```

At the very bottom is says: "PAM no modules loaded for `login' service". Could this be the problem?

---

### Post by lightnb on 2009-05-19
Yay! One step forward (I hope):

I'm now getting:

**User not known to the underlying authentication module**

auth.log:
```

May 19 11:15:52 AGtest login[8341]: pam_winbind(login:auth): getting password (0x00000000)
May 19 11:15:55 AGtest login[8341]: pam_winbind(login:auth): user 'domain\username' granted access
May 19 11:15:55 AGtest login[8341]: User not known to the underlying authentication module

```

common-auth:
```
auth sufficient pam_winbind.so
auth required pam_unix.so nullok_secure use_first_pass

```

common-session
```

session required pam_unix.so
session required pam_mkhomedir.so umask=0022 skel=/etc/skel/

```

common-account
```
account         required        pam_winbind.so
```

---

### Post by lightnb on 2009-05-19
Success! (Sort of)

The key was rebooting the machine. I was avoiding a reboot, since I thought I would not be able to log back in until I got it fixed. Yet rebooting fixed it. Go figure.

Anyway, I've managed to login to the computer using domain users, and have given domain administrators sudo privileges on the local machine.

Here's are the next issues that need tackled:

1.) Home Folder Mapping

When a domain user logs in, their home folder on the local machine is ```
/home/DOMAIN/username
```

The domain user's also have a server home folder, on the server at
```
/home/username
```

When the user logs in, the user's server home folder should get mapped over their local home folder, so that anything a user saves in their home folder, including application settings, actually resides on the server. AKA roaming profiles for Linux. The trick is going to be getting the home folder to mount first, so the login logs-in against the mapped home folder. Any ideas here?

2.) Shared Credentials

Also, it still asks for a password when trying to open a samba share... cant the credentials here "auto-tie" to the login credentials, so the login to the computer also logs you in to all the samba shares as the same user, at the same time?

---

