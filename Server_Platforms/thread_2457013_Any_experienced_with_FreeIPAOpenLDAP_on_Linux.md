---
title: "Any experienced with FreeIPA/OpenLDAP on Linux?"
date: 2021-01-24
forum: Server Platforms
---

### Post by kevdog on 2021-01-24
Looking for anyone that has had some experience using OpenLDAP or FreeIPA within Linux.  My goal is to setup a central authentication server where GID/UIDs would match across various virtualized linux instances. I've played around with OpenLDAP and have a working instance but just wondering if FreeIPA is a better solution.

---

### Post by TheFu on 2021-01-24
>  My goal is to setup a central authentication server where GID/UIDs would match across various virtualized linux instances.  that's really only possible for manually managed users - not so easy with daemon accounts, if that's your goal. Any accounts that need to work prior to networking being available can't really use LDAP, for example.

I use OpenLDAP every day for authentication into my email server.  Long ago, it was used as a 1-password system for almost everything - webapps, POSIX logins. Alas, the management system for openLDAP (Zimbra) was terrible at upgrade time, effectively forcing complete removal pre-Zimbra upgrade, then complete reinstall post-Zimbra upgrade.  Zimbra upgrades were ugly enough already that I really didn't want to risk having all users locked out from every system. After 1 upgrade, I decided not to use Zimbra in that way again.  Having hassles for 20 seconds every few months was easier than the alternative every quarter and risk of complete failure.  Newer versions of Zimbra are making inroads that force paid licenses.

I won't use any php-webapps or Java to manage DBMS or LDAP (personal hatred), so I've always used LDIF files to manage users and groups. This is a hassle.

FreeIPA has been on my list of things to install for years now. A few times every year, I'd look into the requirements for that. For about 6 months, there seemed to be an Ubuntu Server version.  FreeIPA seems to be a group of 20 F/LOSS projects cobbled together. Almost every language invented is used across those projects, it seems. Perhaps 50 different languages, since there isn't a single ruler to make them all design together towards a common goal.  IMHO, this problem is why MSFT-AD still exists. There is little desire in most enterprises to remove MS-AD, so very little work has been put into creating a viable alternative that is as fast as an openLDAP server should be.

FreeIPA just became a much more complex question (politically) with the RH changes to CentOS licensing.  To my knowledge, FreeIPA doesn't work well with non-RH servers. They are all ports. The primary target platform is whatever the current RHEL server is at the time.  Clients on all sorts of Unix/Windows work fine.  Last year, RH started a replacement project for FreeIPA. I don't know anything more about it - or even if it is still alive.

I don't have an easy, perfect, answer for my needs.
For lurkers ... [https://www.youtube.com/user/intrigano/search?query=LDAP](https://www.youtube.com/user/intrigano/search?query=LDAP)

> Four weeks, twenty papers, that&#8217;s $2 dollars. Plus tip.

---

### Post by kevdog on 2021-01-25
I'm using LDAP right now to set my GID/UIDs of a lot of my docker containers to not run them as root.  I'm looking at running FreeIPA as a docker container within an Ubuntu Host.  I don't really need all the capabilities of FreeIPA such as DNS.  I understand what you mean regarding UIDs/GIDs < 1000, however in most instances setting these UIDs/GIDs > 1000 have worked pretty well.  I agree LDIF files are cumbersome and yes I'm using Apache Directory Studio and phpLDAPadmin in some form for management (mostly) --- these must be the programs your referring to at php-webapps or JAVA.  

Although its not a requirement, it seems for easier to create a single UID/GID and have them match across systems particularly when other storage options like FreeNAS or other shares are involved.

---

