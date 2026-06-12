---
title: "AFP &amp; netatalk config.."
date: 2010-08-03
forum: Server Platforms
---

### Post by wall_e on 2010-08-03
Hi guys,

Does anybody have any idea how to stop Mac users from logging into an AFP share from different locations?

Ideally I'd like to setup netatalk so that only one connection can be made at once, if that makes sense?

I've looked at the documentation on [http://netatalk.sourceforge.net/2.1/htmldocs/](http://netatalk.sourceforge.net/2.1/htmldocs/) but not really sure how to achieve this.

At present the way I am controlling who can access my ubuntu storage is by simply using netatalk in its default config. This way it is serves up home folders which are attached to users on the ubuntu machine.

This works pretty well for me because if I want to create a 'share' I can simply create a new user in webmin.

This also means I don't have to restart the netatalk daemon.

Any ideas appreciated :)

---

