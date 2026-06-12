---
title: "Restrict OpenLDAP searches for address book?"
date: 2008-12-01
forum: Server Platforms
---

### Post by shizakapayou on 2008-12-01
I have a fully working OpenLDAP and Samba server running on Ubuntu Server 8.04.1.  I'd like to use the LDAP directory as an internal address book, preferably allowing users to add their own contacts.

With the default slapd.conf configuration, I am able to use my directory as an address book, but a search returns everything - group names, computer names, users, anything in the directory that matches the search.  I've tried writing some rules but so far I've only succeeded in removing all access to everything, which subsequently means no one can log on.

What's the best way to approach this?  Create an address book OU somewhere with all contacts in there?  All my users are already listed under the Users OU, so I'd like to be able to use the information that's already there.  How should I go about restricting searches while keeping the domain alive?

---

