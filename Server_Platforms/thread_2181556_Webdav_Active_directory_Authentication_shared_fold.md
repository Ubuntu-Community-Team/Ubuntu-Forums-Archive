---
title: "Webdav Active directory Authentication shared folder"
date: 2013-10-18
forum: Server Platforms
---

### Post by viperce on 2013-10-18
Hi,

I am trying to setup a Linux Webdav server but need to know if the following configuration would be possible.

1. I would like the users to be authenticated through the Active directory
2. I would like only the users folders they have access to be displayed.

reason for this, we would like our staff to be able to access their data from their Android/IOS devices.

---

### Post by SeijiSensei on 2013-10-18
For (1) you can use mod_authnz_ldap to authenticate against AD:  [http://www.held-im-ruhestand.de/software/apache-ldap-active-directory-authentication](http://www.held-im-ruhestand.de/software/apache-ldap-active-directory-authentication)

For (2) I suspect the answer is either no, or that it is very difficult to implement via WebDAV.  You might be better off forwarding a port through the router and using [this method](http://chrisrisner.com/Accessing-Resources-Secured-by-Azure-Active-Directory-with-iOS-and-Android) instead.

---

