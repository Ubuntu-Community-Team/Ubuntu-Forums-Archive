---
title: "LDAP authentication"
date: 2008-10-16
forum: Server Platforms
---

### Post by Corvias on 2008-10-16
This isn't necessarily related to Ubuntu server, but this was the closest place I could think of to post this.

I have an Ubuntu box that I need multiple people with accounts on an LDAP server to log into. I've found plenty of info on setting up pam to authenticate credentials against an LDAP server, however I need to know how to control what happens afterward. Basically here's what I'm looking for:

> New user "joe" sits at the ubuntu machine
> Joe enters his credentials into the login screen
> The ubuntu box talks to the LDAP server, which successfully matches the credentials, and notifies the ubuntu box of this
*Here's the important part*
> the ubuntu box check its local passwd file to see if there is a user in there matching joe.
> If there is, then the ubuntu box logs joe in and gives him his desktop
> If joe is not in the local passwd file, then his username is added, a home directory is created for him, and he is presented with a shiny new desktop.

Is this possible? Is it also possible to log everyone who can be matched to the LDAP server, then be logged into the same local account?

---

