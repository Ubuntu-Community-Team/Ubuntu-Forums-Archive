---
title: "Authentication problems"
date: 2011-08-02
forum: Server Platforms
---

### Post by KLStringer on 2011-08-02
A few days ago I started having problems with SSH and Nagios not being able to connect while looking into the issue it was discovered that a development project's test website was no longer accessible with Apache returning a 403 error permission denied, also new user accounts can't login, only root and 2 other preexisting accounts can.

I've looked at all the permissions and such and afaik they look right, the project is using Drupal but I don't know if its part of the problem or what/how to check if it is. What would cause new user accounts to not be usable?

---

### Post by KLStringer on 2011-08-02
I'm guessing I need to figure out why new user accounts aren't usable and then to go from there. What do I need to look at the find out why the accounts can't be used?

---

### Post by schnelle02 on 2011-08-02
Are you talking about new user accounts on your website?  Are you using the LDAP module to link to active directory?

---

### Post by KLStringer on 2011-08-02
New user accounts to log into the server with. We have a SAS unit that holds recordings for our QA department. They use an account thats local to the server to log on through mapped drives and it no longer allows them to log in. We've tried resetting the password and deleting/remaking the account but we still can't access the share with anything other than root, which we don't want them to use for obvious reasons.

---

### Post by schnelle02 on 2011-08-02
Ah, I misunderstood.  I do web development on the front end so I'm not sure where to start with your problem. I assume no permission changes were made?

---

### Post by KLStringer on 2011-08-03
Yep no permissions where changed at least not by anybody that works here and looking through them everything looks right, I could be wrong. We came in one morning and it just wasn't working. 

But its more than just a problem with Apache, or Nagios. The only user that can access Samba shares through mapped drives is root. Even if I create a new user, give them all the permission to access the shares they still can't authenticate to the server.

---

### Post by KLStringer on 2011-08-03
I'm thinking that since there's 3 different issues we could start with getting Apache working correctly then work on the other two. I just don't know where to start troubleshooting it from.

---

### Post by KLStringer on 2011-08-04
Anyone know of a reputable place to hire a Linux admin for consulting?

---

