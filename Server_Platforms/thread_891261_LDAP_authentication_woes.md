---
title: "LDAP authentication woes"
date: 2008-08-15
forum: Server Platforms
---

### Post by asellus on 2008-08-15
Hi hi.  Been working on this for a total of probably 4 hours or so, and I was just able to figure out how to communicate successfully with my LDAP server here at work.

Here's what I want to do:

Grant the ability to ssh into this server if one has an account on the LDAP server at the office, that way it's one less password to remember and can be changed from the windows environment on our desktops.
Grant su access to certain users via sudoers list even though they aren't a local user.
Automatically create a home directory if one does not exist already when they log into the server with a valid LDAP user.


Now, I've followed various howto's on setting this stuff up, all to no avail.  I finally started just dicking around with ldapsearch and figured out the LDAP server requires a valid login in order to grant access.  Makes sense, since Cacti will only work with LDAP Auth if the "no searching" option is chosen.  For those unfamiliar, it basically takes the attempted login credentials and matches them against the LDAP server with the provided DN syntax in the settings (in this case, <username>@my.company's.email).

So, is there a way I can have the attempted login query the LDAP server with the attempted credentials if a local user does not exist?  Then, if the LDAP server accepts the login/password provided, will allow the user to log in using a template for the home directory if it does not exist?

---

