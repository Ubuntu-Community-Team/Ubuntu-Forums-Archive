---
title: "munin-node warnings"
date: 2012-05-08
forum: Server Platforms
---

### Post by georgek on 2012-05-08
I upgraded a server to precise yesterday and now I'm seeing regular log messages along the lines of:
```
Use of qw(...) as parentheses is deprecated at /etc/munin/plugins/memory line 189.
```
I've already found bug reports for munin and for debian referring to this with slightly different simple changes to the plugin to get rid of this perl warning.

Before making any changes I also checked another server I upgraded last weekend and to my surprise I don't see those messages in the logs.

I've gone through all the config files I can think of, and checked package versions, and I can't see any differences.  The only difference I can see between the boxes is that one is 32 bit and the other 64 bit.  They are running different programs of course but I can't see that any would have any effect here other than munin-node or perl.

Before I spend any more time trying to work out what is or isn't happening here, has anyone got any suggestions please?

---

