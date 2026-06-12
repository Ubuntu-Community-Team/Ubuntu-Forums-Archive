---
title: "What graphical user interface works with LDAP?"
date: 2023-11-03
forum: Server Platforms
---

### Post by civilpolisen on 2023-11-03
[https://linuxgenie.net/how-to-install-openldap-on-ubuntu-22-04/](https://linuxgenie.net/how-to-install-openldap-on-ubuntu-22-04/)

We are currently running LDAP on Ubuntu 18.04 and I think it's a bad deal... We are using Fusion Directory as a graphical user interface.
We used FreeIPA since before, but has left that.

But at the other hand...
[https://packages.ubuntu.com/search?keywords=fusiondirectory](https://packages.ubuntu.com/search?keywords=fusiondirectory)

Looking at this link, it looks like Fusion Directory is very compatible with the latest versions of Ubuntu! 99 hits!
So... what happens if we upgrade the server? Will it remain helpful...? 

Is there any one out there using Fusion Directory with Ubuntu 20.04 or 22.04?

---

### Post by MAFoElffen on 2023-11-03
> **civilpolisen said:**
> We
"We" = "Commercial" Right?

---

### Post by civilpolisen on 2023-11-10
"We" refers to the company that I work for. There should be many companies (or organizations) just like ours or similar like ours. Nothing special. We work with open source on the Ubuntu platform, servers and clients.
The owner is very skilled but also well very busy. He knows almost all there is to know! But I like to solve issues on my own... or at least to try to solve!  :-)

---

### Post by TheFu on 2023-11-10
To me, it is a bit of an embarrassment that there isn't a built-in user/group LDAP capable management tool for all Linux.  Why is it easier to connect to AD than to a Linux LDAP at install time?  In a home, it should be trivial to install a POSIX LDAP server and have all the clients either "find it" or be told where it is on the LAN and that should be the end of it.  All user and password management should "just work" with LDAP on Linux.

Embarrassing that isn't the situation for all Linux distros.  FreeIPA was nearly as bad at the problem.  They took 50 F/LOSS projects, written in 50 different languages and created a monster.  LDAP - "Light-weight" ... right?  It shouldn't need 2 CPUs and 4GB of RAM to work, minimum.  Plus, FreeIPA servers only ran on RHEL-based systems.  If I wanted that, I'd have deployed a Solaris NIS+ system decades ago. Sun Microsystems gives away NIS+ clients, but retained the server.  That was one of their business decisions that was the beginning of the end of their company leadership. Sigh.  NIS "just worked" ... er ... with terrible security, but for the time, it was used everywhere by everyone except the crazy organizations that used a full directory service (pre-LDAP).

LDAP and the management of it should easily run in 384MB.  The CLI tools have existed for decades. They are stable and work, if a little ugly.  It isn't like a POSIX schema is some magical mystery either.

I'll go away now.  Bitching has ended.

Have you looked at Cockpit for LDAP management?  It is on my list to check out.

---

### Post by MAFoElffen on 2023-11-10
I asked, because of your title: "What graphical user interface works with LDAP?"

While FusionDirectory is GNU GLP2, not all tools out there are, and many, even though they have free community editions for personal use, have restrictions for commercial use, so set different boundaries on a question. Your tile was broad, then you limited it to opensource, then the further discussion talked more about admin and administration, instead of client, so... 

You already mentioned Fusion Directory

There are also:[INDENT][Apache Directory Studio]("https://directory.apache.org/studio/")
[LDAP Account Manager]("https://github.com/LDAPAccountManager/lam")
[PLA]("https://github.com/leenooks/phpLDAPadmin")
[WebMin]("https://webmin.com/docs/modules/ldap-server/")
[LDAP Admin Tool]("https://ldapbrowserlinux.com/")
[/INDENT]
This is not a complete list, but just a start... A lot of older tools, pre-18.04, that were written for QT3, never got converted for QT4. Same with the shift from Python2 to Python3.

TheFu isn't going to like this, but MS-RSAT works with Samba-AD out-of-the-box... But Windows OS requires a paid license for your console machine.[INDENT][https://wiki.samba.org/index.php/Installing_RSAT](https://wiki.samba.org/index.php/Installing_RSAT)
[https://samba.tranquil.it/doc/en/samba_config_server/samba_install_RSAT.html](https://samba.tranquil.it/doc/en/samba_config_server/samba_install_RSAT.html)
[https://www.tecmint.com/manage-samba4-ad-from-windows-via-rsat/](https://www.tecmint.com/manage-samba4-ad-from-windows-via-rsat/)[/INDENT]

If you were RHEL branch instead of Debian branch, then I would recommend FreeIPA...

If you are doing MS AD with SSSD, then some manual work comes in when you start trying to share NFS network shares and group permissions, which are still a manual config affair on the Windows AD side...

---

### Post by civilpolisen on 2023-11-15
Thank you for good reply! I'm a big fan of Steve Krug's book "Don't make me think"! My copy is from the late 90's, I believe. The content may be outdated but the title says it all! :-) 

[https://www.amazon.se/Dont-Make-Me-Think-Usability/dp/0321344758](https://www.amazon.se/Dont-Make-Me-Think-Usability/dp/0321344758)

* * * *

**TheFu:**
1. We're fully aware of FreeIPA but we're leaving the platform.
2. Thank you for mentioning Cockpit! [https://cockpit-project.org/](https://cockpit-project.org/)

        **MAFoElffen:**

1. Thank you for the long list of alternatives! That was very considerate of you, to take the time!
2. I keep forgetting why we're not using Fusion Directory on Ubuntu more recent than 18.04! 
There is an active community [FusionDirectory Community days 2023]("https://www.fusiondirectory.org/en/fusiondirectory-community-days-2023/").

3. The struggle is real! :-)
```
Ign:5 https://public.fusiondirectory.org/stretch-fusiondirectory-release stretch InRelease
Ign:6 https://public.fusiondirectory.org/stretch-schema2ldif-release stretch InRelease
Err:7 https://public.fusiondirectory.org/stretch-fusiondirectory-release stretch Release
  404  Not Found [IP: 51.159.79.236 443]
Err:8 https://public.fusiondirectory.org/stretch-schema2ldif-release stretch Release
  404  Not Found [IP: 51.159.79.236 443]
Reading package lists... Done
E: The repository 'https://public.fusiondirectory.org/stretch-fusiondirectory-release stretch Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://public.fusiondirectory.org/stretch-schema2ldif-release stretch Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details. 
```

---

### Post by stephan4 on 2024-08-27
Either you use RSAT via Windows or you learn Ansible. The beauty of Linux is the power of automatization (fancy right?!?) and not relying on GUIs.

With Ansible, I can manage 1000s of accounts.

---

### Post by QIII on 2024-08-27
Closed.  RIP.

---

