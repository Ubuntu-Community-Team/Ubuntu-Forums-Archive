---
title: "How link 12.04's svnserve against libldap, like it was in 11.04?"
date: 2013-04-09
forum: Server Platforms
---

### Post by klausthorn on 2013-04-09
When installing subversion under "11.04 server", svnserve is linked against libldap. When doing the same under "12.04 server", it is not. Libldap is installed on both, of course.

```
ldd /usr/bin/svnserve
 ...
 libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2
 ...
```
I already submitted a bug in launchpad [1] but nothing happens there, so I have to fix the linking myself, but I do not know how to.

I compiled subversion_1.6.12dfsg-4ubuntu5.1 myself under 11.04 and 12.04. Again: under 11.04, svnserve is compiled as being linked against libldap, but not under 12.04.

Between the following two lines of commands I can intervene and change the source and the debian build rules as I like, but what shall I change?
```
dpkg-source -x subversion_1.6.12dfsg-4ubuntu5.1.dsc ; cd subversion-1.6.12dfsg
  # my chance to change stuff here #
dpkg-buildpackage -us -uc -nc 2>&1|tee dpkg.log
```

I searched through the sources and debian files which drive the build process, but did not find a good starting point or any trace of "ldap".

After the build however I find libldap being mentioned e.g. in "BUILD/config.status" (on both servers = under both versions) :
```
S["SVN_APRUTIL_EXPORT_LIBS"]="-laprutil-1 -lldap -llber  "
S["SVN_APRUTIL_LIBS"]="-laprutil-1 -lldap -llber  "
```

... so some part of the debian build system seems to pick up the ldap library. Anyone knows how this happens?

And then, sadly, only under 11.04 the library is used for linking to svnserve. Anyone knows how I can fix this or at least find the cause?

When I build the original subversion source without any debian/ubuntu stuff, ldap is hardly mentioned in the results. So I guess I want to use the debian/ubuntu build system. But if you can tell me how to link against libldap without, this is also welcome.

[1] = [https://bugs.launchpad.net/ubuntu/+source/subversion/+bug/1160896](https://bugs.launchpad.net/ubuntu/+source/subversion/+bug/1160896)

---

### Post by nicolasdiogo on 2013-04-09
sorry - i can not help you with this

*but* since this problem would be more accurately placed in a SVN maillist or forum.

just trying to help - do not shoot me down, please

---

### Post by klausthorn on 2013-04-10
Thank you, I will also contact the subversion community.

But the questions about the packaging/installation system of Ubuntu/Debian only make sense in Ubunt/Debian context, don't they?

Also, knowledge about linking a binary (svnserve) with another optional library (libldap) is also welcome and hardly subversion specific.
As I am not a C programmer, I don't know how to.

---

