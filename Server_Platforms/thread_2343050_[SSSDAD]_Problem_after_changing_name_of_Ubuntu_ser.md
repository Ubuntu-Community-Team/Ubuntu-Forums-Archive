---
title: "[SSSD/AD] Problem after changing name of Ubuntu server joined to Active Directory."
date: 2016-11-12
forum: Server Platforms
---

### Post by zaicnupagadi on 2016-11-12
Hi Guys,

New here, struggling for one day with an issue decided to ask experts ^^

So I got that Ubuntu server (16.04), server is joined to AD. As the server goes to other project we decided to change name of it, and here is the problem.

On windows I am used to - remove server from domain, change the name, rejoin. Did the same for that Ubuntu machine. After name change I have modified files /etc/hostname and /etc/hosts and rejoined with "net ads join" command - got successful notification.

kinit works well, getent also - but when trying to log in I am getting error:

pam_sss(sshd:auth): received for user TESTDOMAINUSER: 4 (System error)
Case is very similar to this one:

[http://www.linuxforums.org/forum/debian-linux/194808-sssd-kdc-reply-did-not-match-expectations.html](http://www.linuxforums.org/forum/debian-linux/194808-sssd-kdc-reply-did-not-match-expectations.html)

If I change the name back to the old one - I CAN log in with "pjarosz" user without any problem, so there is some kind of a connection with server name, but I am  - in Poland we say - "too weak between my ears" :) Need someone with bigger brain on Linux/Ubuntu Server. 

My sssd.conf looks like:

[sssd]
services = nss, pam
config_file_version = 2
domains = <OUR.DOMAIN.NAME>


debug_level = 10
[domain/<OUR.DOMAIN.NAME>]
id_provider = ad
override_homedir = /home/%d/%u
access_provider = simple
simple_allow_users = [email]pjarosz@<OUR.DOMAIN.NAME[/email]>
simple_allow_groups = <GROUP.NAME>
default_shell = /bin/bash
override_shell = /bin/bash



Any thoughs on this kindly appreciated!

-zaicnupagadi

---

### Post by darkod on 2016-11-12
Do you have the server name specified in smb.conf? Double check the smb.conf too because those are the settings used by samba to join the AD.

I agree with you, removing the object from AD, then renaming the server and joining it again should work.

One way would be also to purge (remove) completely krb5-user and sssd and reinstall them again. Maybe something gets hard coded... I have never done server renaming for AD member, so I can't help much more...

---

### Post by zaicnupagadi on 2016-11-13
Hi Darko,

All what I have added to /etc/samba/smb.conf is:

workgroup = <MY_DOMAIN_NAME>
client signing = yes
client use spnego = yes
kerberos method = secrets and keytab
realm = <MY_DOMAIN_NAME>
security = ads

So there is no name in there. Before removing that stuff I would really love to try some other ways, but as there are no other suggestions from others I think I will go that path and reply how it went.

---

