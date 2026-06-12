---
title: "Where to put Nagios user plugins?"
date: 2011-06-07
forum: Server Platforms
---

### Post by goofrider on 2011-06-07
I want to create my own Nagios plugins but I'm a bit uneasy to put them in /usr/lib/nagios/plugins since that violates Debian/Ubuntu file system standards that /usr should be owned and managed by apt.

Any suggestions?

---

### Post by tapi0n on 2011-06-07
Don't you have to put your plugins in */usr/local/nagios/libexec*?

Haven't tried making my own plugins and don't know much about ownership, but why would this be a violation? I did read what you say but I'm not quite sure what you mean, wouldn't this imply that for whatever program runs in /usr you wouldn't be allowed to make any changes/additions?

---

### Post by linkageless on 2011-06-07
I always put mine in plugins/contrib/ on whatever distro I'm working with, usually the package manager won't remove a subdir you've created and it keeps it slightly separate, but close to hand.

IIRC there are packages that use the contrib subdir also, but you aren't likely to cause any major problem as long as you are using nice descriptive (or at least unique) filenames.

---

### Post by linkageless on 2011-06-07
> **tapi0n said:**
> Don't you have to put your plugins in */usr/local/nagios/libexec*?

You can use plugins from anywhere on the system that the nagios daemon (or nrpe if you're using that) can read. All you would need to do is be sure to include the full path for the plugin in the command definition, or define and use another user macro (eg $USER3$=/path/to/your/plugins).

---

