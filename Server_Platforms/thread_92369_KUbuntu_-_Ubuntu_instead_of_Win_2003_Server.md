---
title: "KUbuntu - Ubuntu instead of Win 2003 Server"
date: 2005-11-19
forum: Server Platforms
---

### Post by LinuxHawk on 2005-11-19
I am going to be starting a small business network and have the option of using Linux or Windows for the server.
I am familiar with Windows Servers and the domain structure.
I have a few questions maybe some of you can answer.

This is a small business that is growing. They currently have 12 XP-Pro PC’s in place on a workgroup that is poorly managed. I want to get them on a domain.

So I need a Linux Server that has the same capabilities as Windows Server 2000 or 2003.

Can KUbuntu be set up as an authentication server for XP PC’s and possibly also Linux workstations in the future?

I also would like to know if there are any current books concerning setting up a Linux-Windows network that anyone could recommend.

Thanks in advance…

---

### Post by LordHunter317 on 2005-11-19
Samba can function at the level of an NT4 PDC.  It cannot function at the level of an AD controller.

If you need AD, install 2K3 Server.

---

### Post by justhamade on 2005-11-19
[QUOTE=LinuxHawk]
So I need a Linux Server that has the same capabilities as Windows Server 2000 or 2003.[/QUOTE]

What you need to do some research and find out the cabilities of linux, more specifically samaba, in a windows environment.  Why do people post questions that can be answered by a google query??????

---

### Post by garyng on 2005-11-20
You need to weight what kind of features(mainly from managing perspective) you want. 

If all you want is resource sharing and the like(NT domain style), samba food the bill well. But if you want other things like SSO(feature of AD) and full integration with other stuff like IE or VPN etc. I would suggest just get the 2003 server as the effort spending in making linux work for such a small number of users(thus the license saving) may not worth it.

However, if you think of it as an excercise for future similar experiences, do go for it(linux + samba + LDAP). Though I would suggest to go with debian rather than ubuntu as the "main" section may not have all the things you need and the "universe" section really is an "as-is" where many packages are not tailored to fit with the changes of ubuntu.

---

### Post by adeh on 2005-11-20
I am currently using a debian server as a domain controller in a win XP Pro environment. Same number of users, about 12. Basic file sharing and ability to log into any computer were the only goals.

Everything works very well, the only problem is that users cannot update the user list themselves. Or, more precisely, an on-site semi-knowlegdable person cannot really be expected to handle that.

In W2k3, the graphic interface is pretty easy to deal with and you can train someone to add and delete new users. On a headless linux server, it's not so simple.

In our case, we visit all the time and manage the server for them, and MSFT fees were just ridiculous, so it works well.

As for ubuntu, if you can handle apt-get then it will work fine for whatever you most likely.

Good luck!

---

### Post by garyng on 2005-11-20
[QUOTE=adeh]I am currently using a debian server as a domain controller in a win XP Pro environment. Same number of users, about 12. Basic file sharing and ability to log into any computer were the only goals.

Everything works very well, the only problem is that users cannot update the user list themselves. Or, more precisely, an on-site semi-knowlegdable person cannot really be expected to handle that.

In W2k3, the graphic interface is pretty easy to deal with and you can train someone to add and delete new users. On a headless linux server, it's not so simple.

In our case, we visit all the time and manage the server for them, and MSFT fees were just ridiculous, so it works well.

As for ubuntu, if you can handle apt-get then it will work fine for whatever you most likely.

Good luck![/QUOTE]

Download the domain user manager from MS and with some setup on the samba, you can manage user(including rights) on any XP. And with some patches to the kernel(acl/extended attributes), the explorer can be used for access control setting too.

---

### Post by Bar2D2 on 2005-11-20
[COLOR="DarkRed"][QUOTE=LinuxHawk]So I need a Linux Server that has the same capabilities as Windows Server 2000 or 2003.[/QUOTE]

AD is a typical W2003Server feature, not avialable in any Linuz dist as far as I know.
I would say Debian still haz the best server abilities.

AD 4 linux, that would be ok :)

But why keep using WXP? Switch ws also 2 linux! ;)[/COLOR]

---

### Post by MarcDM on 2005-11-21
[QUOTE=LinuxHawk]They currently have 12 XP-Pro PC’s in place on a workgroup that is poorly managed. I want to get them on a domain.

So I need a Linux Server that has the same capabilities as Windows Server 2000 or 2003.[/QUOTE]

I can't think of any books on the topic but here's how it goes. 

Samba is responsible for Windows's Authentication, Authorization, FileSharing, WINS (Windows Internet Naming System) and Windows' user DB.

Now here's the deal. 
You can use OpenLdap to setup an Ldap server to store user information. Then have Samba talk to that for user info. Also have pam/nss on the server talk to it for the same reason. 

Using idealx's smbldap-* scripts (included on debian with samba/ldap not sure, I apt-got both), you can even have Windows People pressing ctrl-alt-delete to change passwords. 

Add/Remove users/computers can happen entirely through a web interface. I think IdealX has a Webmin Module, and worst case, you can use PhpLdapAdmin (it should be in the repos) to manage users.

In the end, you have essentially a Windows domain, complete with Domain logins, and all the other niceness that comes with Windows Domains.

What's nicer, is that now you have a box that you can layer services on top of, like an internal mail server, shared address books and calendars and such.

BTW, if you really need help with this, I can help via email and phone. Send me a private message if u want.

---

### Post by LordHunter317 on 2005-11-21
Except for SSO, which requires Kerberos.  And Windows can't use UNIX kerberos situations without a custom GINA stack.

And except for AD-level GPOs.  And several other core features that active directory provides Samba does not.

If you need Active Directory, just use it.  Samba does not provide several core features of Active Directory, and can't be integrated with anything else to really move it beyond an NT4 PDC level, from a client's perspective.

And it's really the controls you can place on your client machines and the administration tools that make AD a superior solution.

---

