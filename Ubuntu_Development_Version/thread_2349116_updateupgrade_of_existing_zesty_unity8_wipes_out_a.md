---
title: "update/upgrade of existing zesty unity8 wipes out apps from containers"
date: 2017-01-11
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-01-11
Updated/upgraded one of my zesty installs of ubuntu (unity8) with 6 containers!! It wiped out all apps with exception of Vim.

Oh joy!.. Major breakage on the edge. :)

Regards..

---

### Post by pixelro on 2017-01-12
i think libertine now uses lxc stuff

---

### Post by pixelro on 2017-01-12
[https://launchpad.net/ubuntu/zesty/+source/libertine/+changelog](https://launchpad.net/ubuntu/zesty/+source/libertine/+changelog)

libertine (1.5+17.04.20170105.1-0ubuntu1) zesty; urgency=medium

  [ Chris Townsend ]
  * Drop support for the Puritine click package as that is Vivid only
    and a Vivid Libertine branch exists for any future fixes.
  * Only set the lxc log when a container is defined during class init.
    (LP: [#1653973]("https://launchpad.net/bugs/1653973"))
  * Bump version to 1.5 for new upstream release.

  [ Larry Price ]
  * Logic for bundling libertine as a snap built from source.
  * Catch exceptions raised during container creation.
  * Initial implementation of lxd backend. (LP: [#1580612]("https://launchpad.net/bugs/1580612"))
  * Use the libertine logger and LIBERTINE_DEBUG variable everywhere.
  * Update configure bind-mount logic given new lxd backend.
  * Use dpkg to find package name when installing local deb.
  * Create d-bus service for lxd container management.

---

### Post by ventrical on 2017-01-12
> **pixelro said:**
> i think libertine now uses lxc stuff

Yes it does... always has since 16.10 and 16.04 testing unity8.

---

### Post by ventrical on 2017-01-12
> **pixelro said:**
> [https://launchpad.net/ubuntu/zesty/+source/libertine/+changelog](https://launchpad.net/ubuntu/zesty/+source/libertine/+changelog)

libertine (1.5+17.04.20170105.1-0ubuntu1) zesty; urgency=medium

  [ Chris Townsend ]
  * Drop support for the Puritine click package as that is Vivid only
    and a Vivid Libertine branch exists for any future fixes.
  * Only set the lxc log when a container is defined during class init.
    (LP: [#1653973]("https://launchpad.net/bugs/1653973"))
  * Bump version to 1.5 for new upstream release.

  [ Larry Price ]
  * Logic for bundling libertine as a snap built from source.
  * Catch exceptions raised during container creation.
  * Initial implementation of lxd backend. (LP: [#1580612]("https://launchpad.net/bugs/1580612"))
  * Use the libertine logger and LIBERTINE_DEBUG variable everywhere.
  * Update configure bind-mount logic given new lxd backend.
  * Use dpkg to find package name when installing local deb.
  * Create d-bus service for lxd container management.

Thanks. I think it is a different bug.  I left a message on one of the links you provided.

Regards..

---

