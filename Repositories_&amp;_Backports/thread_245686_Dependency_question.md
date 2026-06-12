---
title: "Dependency question"
date: 2006-08-28
forum: Repositories &amp; Backports
---

### Post by joostk on 2006-08-28
If I decide to compile and install some piece of software manually (eg. Postfix), because I need a newer version than the one in the dapper repository, how do I fix the problem that apt-get thinks I do not have Postfix installed when certain other programs depend on an mta (or Postfix specifically) being present, because I didn't install Postfix using apt-get?

---

### Post by tkjacobsen on 2006-08-28
You can use checkinstall ([https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)) and install with dpkg, then apt-get should see it.

---

### Post by visik7 on 2006-08-28
or you can backport postfix from edgy or sid or experimental to dapper.

---

### Post by joostk on 2006-08-28
> **visik7 said:**
> or you can backport postfix from edgy or sid or experimental to dapper.

How do I do this for one specific package like Postfix? Probably a noob question, I'm used to compiling everything myself, but I like the concept of apt-get.

---

