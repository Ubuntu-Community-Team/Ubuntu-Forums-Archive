---
title: "Create AppArmor profile from existing (dmesg) log"
date: 2019-03-11
forum: Security
---

### Post by azzamite on 2019-03-11
Hello everyone

I'm running AppArmor in an embedded device which has a few limitations... and I manage to retrieve the dmesg logs back to my development PC.

At this moment I'm trying to generate app profiles for the SW that will be running there.

The [aa- tools]("https://gitlab.com/apparmor/apparmor/wikis/Profiling_with_tools") want to read the syslog messages live... but they are made in python... so there must be a way to feed them the log to create the rules... right?

---

