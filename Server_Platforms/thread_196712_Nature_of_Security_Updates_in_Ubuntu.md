---
title: "Nature of Security Updates in Ubuntu?"
date: 2006-06-14
forum: Server Platforms
---

### Post by kingkevbo on 2006-06-14
Hello everyone,

I am currently putting together a web server that will house some sensitive information for the place I work.  I want to use Ubuntu for this server, especially now that there is long term support for Dapper.  I am curious as to the nature of security updates for Ubuntu, as I've never gotten a clear answer as to which packages get security updates.  In /etc/apt/sources.list there is the section that states:

> ## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


However, there is this entry in the Ubuntu Official Wiki:

[https://wiki.ubuntu.com/MOTU/Teams/Security?action=show&redirect=MOTUSecurity](https://wiki.ubuntu.com/MOTU/Teams/Security?action=show&redirect=MOTUSecurity)

This seems to indicate that there is *some* security updating going on in Universe.  I have also seen changelogs that would indicate the same thing, but I am unsure if those refer to updates during development.

Anyway, I am curious as to what is actually going on.  For maximum security, should I avoid Universe and Multiverse?  If that is the case, that makes life a bit difficult, as packages such as phpMyAdmin and rkhunter(!) are in Universe.  Will backports handle these issues?  Can anyone point me to any official word on how Ubuntu handles this?  

Thanks,

Kevin

---

### Post by 23meg on 2006-06-14
[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

You're right, Universe apps *can* get security updates, but they're not *guaranteed*. Those in Main are guaranteed to get them.

---

### Post by asimon on 2006-06-15
Also be aware that universe and multiverse packages can also be unsecure to install in the first place or may not work at all. They just don't get the developer's love main and restricted packages get.

---

### Post by kingkevbo on 2006-06-15
[QUOTE=asimon]Also be aware that universe and multiverse packages can also be unsecure to install in the first place or may not work at all. They just don't get the developer's love main and restricted packages get.[/QUOTE]

Excellent!  Thanks to everyone for the clarification.

Really, it sounds like if someone should need a package from Universe (because they *really* need it) they should track 3rd party security advisories to make sure a package hasn't been neglected (in a security sense).  It would appear that I should completely stay away from Multiverse.

Anyway, thanks again!

Kevin

---

