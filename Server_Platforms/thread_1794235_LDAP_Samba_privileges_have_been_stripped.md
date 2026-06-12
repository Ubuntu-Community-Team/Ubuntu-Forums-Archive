---
title: "LDAP Samba privileges have been stripped"
date: 2011-06-30
forum: Server Platforms
---

### Post by sdmike6 on 2011-06-30
At my work I have an Ubuntu 11.04 server x64, running samba for a fileshare. 

The users connect to the server using LDAP.

I was messing around with Webmin using the "Convert Unix users to Samba users."

After I did this I was no longer about to use the file share using my LDAP credentials. 

For a test I created another LDAP account and I was then able to get into the fileshare.

So my question is how do I change all of the users on the server to be able to access the fileshare again?

---

### Post by sdmike6 on 2011-06-30
First off NEVER use webmin. I uninstalled that ASAP, I don't know what I was thinking.

The problem was when the conversion took place it talked to PAM and then PAM talked to the main LDAP server and changed those users samba attributes.

---

