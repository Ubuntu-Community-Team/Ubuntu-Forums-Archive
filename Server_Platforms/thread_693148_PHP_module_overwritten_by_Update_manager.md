---
title: "PHP module overwritten by Update manager"
date: 2008-02-10
forum: Server Platforms
---

### Post by Kleenux on 2008-02-10
We need to have a number of specific features in PHP, therefore we compiled our own 5.2.5 version, and installed it at the location of the "official" version (prefix /usr). Features include semaphores, shmem, gd, zlib, sockets etc...

However, Update manager presented us some security and enhancements changes that were worth the installation.

Unfortunately... while I don't see another option, by installing the suggested changes, the module libphp5.so was overwritten by update manager... and all our specific features also.


What is the best strategy in this case ?

- download again the PHP source, re-compile, re-install?

- prevent Update manager from updating PHP?

What do you do?

Thanks

---

### Post by Kleenux on 2008-02-13
Anybody minds to tell what you are doing in this case (recompilation of PHP / automatic updates policy)? Thanks

---

### Post by faulkes on 2008-02-13
> **paris-unmatch said:**
> Anybody minds to tell what you are doing in this case (recompilation of PHP / automatic updates policy)? Thanks

If you require a custom LAMP stack, my suggestion would be to do so with a full build (apache, php, mysql) with no system based installation so update manager doesn't know anything about it.

The downside is you don't get automatic updates for security fixes and new features, which is the expense in time.

Alternatively you could tell update-manager to only download the packages and not install them, that way you could select which to ignore and which you need to manaually (but using dpkg and such tools) install.

The configuration for apt (which is the basis for all the update stuff) lives in
/etc/apt/apt.conf.d, You would need to add the line

Aptitude::CmdLine:: Download-Only  (remove the space between the : and D I added because the forum interprets it as a smiley)

to the appropriate configuration file.

[B]
Before you do that, I STRONGLY suggest you read up on apt and it's associated configuration files.[/B]  See the apt and aptitude man pages.

```

man apt
man aptitude

```

Faulkes

---

