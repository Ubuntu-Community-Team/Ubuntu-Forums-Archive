---
title: "ldap authentication and auto-homedirs for desktop machines"
date: 2010-08-12
forum: Security
---

### Post by gregster on 2010-08-12
The goal:
Set up a lab full of Lucid boxes that authenticate against the main university Sun ldap server and create local, limited, homedirs if they don't already exist. 

Infrastructure:
The ldap server is freely accessible on our network and does not require authentication to do a query. Users will not be able to make changes on the ldap server from these workstations. I cannot set up homedirs of users manually - any one of 15,000 people could walk in and use one of these machines.

What I've got working so far:
Authentication works, but when I log in through GDM, after a few errors, I get nothing but a blank desktop (with wallpaper and cursor). If I log in as a local user and su to an ldapuser I get assigned a home directory at /, which explains the errors; this kind of user can't write to /. I've seen posts on this but nothing that works for me.

The problem, as I've identified it:
I'm using pam_mkhomedir to create home directories on first login, but I don't seem to have any way of telling pam_mkhomedir *where* to create the home directories. I've tried to use the nss_map_attribute in /etc/ldap.conf (like this: nss_map_attribute homeDirectory "/home/users/"uid), but my syntax is all guesswork - I can't seem to find anyone else trying to mangle a homedir this way.

The request:
I welcome all assistance, including links, but please keep in mind that I've already gone through every how-to and forum thread that I can find (and that's alot). Most either don't deal with the homedir thing at all, or if they do, they only cover nfs/smb shares.

Thanks in advance.

---

### Post by bodhi.zazen on 2010-08-12
Put a a minimal $HOME structure in /etc/skel ....

See this link :

[http://www.opinsys.fi/en/setting-up-openldap-kerberos-on-ubuntu-10-04-lucid](http://www.opinsys.fi/en/setting-up-openldap-kerberos-on-ubuntu-10-04-lucid)

As you can see, the setup can be quite involved, and thus your question broad and the answer quite long if I were to write out each and every step.

Better to ask a specific question at the point you get stuck (if you get stuck).

There is also : [https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn)

---

### Post by gregster on 2010-08-13
First, thanks for the quick response bodhi.zazen.

Second, sorry. When I re-read my post, I realize my question wasn't really clear. I'll re-phrase it:

Can anyone help me with ldap.conf syntax? (I think) I need to use nss_map_attribute to set a **local** path for home directories. I've tried
nss_map_attribute homeDirectory "/home/users/"uid 
and similar, but that doesn't work.

Does anyone have any experience with nss_map_attribute?

---

### Post by bodhi.zazen on 2010-08-13
This wiki page goes through configuration :

[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

The basic syntax (of the line in question) is

> nss_map_attribute homeDirectory msSFU30HomeDirectory

You will need to adjust the "msSFU30HomeDirectory"

---

