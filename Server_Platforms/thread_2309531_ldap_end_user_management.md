---
title: "ldap end user management"
date: 2016-01-11
forum: Server Platforms
---

### Post by Swiftjay on 2016-01-11
Hi there, I'm finally diving into the deep ending and trying to move away from ClearOS to the nitty gritty of a normal server and setting up Ldap.  With alot of follow this and learning the man page on some commands I think I can get this working with using apache directory studio for managing things like adding users and groups, no problem.

However my issue is what about the end user, how would they be able to change their passwords?  A bit of explanation of the servers purpose and maybe there are tools available to the apps I plan to use.

The server is going to run apache, php & mysql and will be doing the following:

* Running zarafa server 7.2.1 with WebApp
* Running owncloud 

Now it could be that owncloud has an option to change passwords on the interface itself if it does maybe someone with experience can tell me?  It would literally solve this concern right here and now :).

Otherwise I need to think of a way or find some web tool to allow users to change their own passwords for their ldap accounts, if anyone has had experience with owncloud or knows of tools (be it open source or perhaps paid that isn't too expensive) then I'm all open for suggestions.

---

### Post by sandyd on 2016-01-11
I've used [PWM]("https://github.com/pwm-project/pwm") for a project before.

Allows you to update the info about a user such as full name/etc, along with self registration, security questions, password expiry management, and self management.

---

