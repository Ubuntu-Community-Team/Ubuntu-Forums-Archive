---
title: "apt-get weak compared to update-manager"
date: 2009-01-07
forum: Server Platforms
---

### Post by whoop on 2009-01-07
For ubuntu server apt-get (update, upgrade, dist-upgrade) is used for keeping the ubuntu server up to date. I find this functionality weak compared to the (GUI) update manager functionality.
Maybe I am missing something but I can imagine sysadmins wanting to do the following (which I can't seem to do with apt-get functionality):

1: Partial update. Only update some packages, not all.
2: Description of update. I can't see what the update fixes
3: Install Critical/Security updates only. (comparable with partial update, but this would auto-select critical/security updates only)
4: Automatic updating (maybe only for critical/security updates at least)

Are these features implemented via some method for server editions, or would these features be unwise to implement.

---

### Post by cariboo on 2009-01-07
I use apt-cron, it emails when there are updates available, with a description and a change log. Apt-cron is available in the repositories.

Jim

---

### Post by windependence on 2009-01-07
> **whoop said:**
> For ubuntu server apt-get (update, upgrade, dist-upgrade) is used for keeping the ubuntu server up to date. I find this functionality weak compared to the (GUI) update manager functionality.
Maybe I am missing something but I can imagine sysadmins wanting to do the following (which I can't seem to do with apt-get functionality):

1: Partial update. Only update some packages, not all.
2: Description of update. I can't see what the update fixes
3: Install Critical/Security updates only. (comparable with partial update, but this would auto-select critical/security updates only)
4: Automatic updating (maybe only for critical/security updates at least)

Are these features implemented via some method for server editions, or would these features be unwise to implement.

Yes, you are missing something. Take a look at the man pages for apt-get. There are literally hundreds of options.

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

If you would like to see what it does, then turn on verbose output with the -V switch. 

ALL GUI items are just fancy front ends for some CLI tool. 

-Tim

---

### Post by whoop on 2009-01-07
I can't figure out how the command line options for apt-get could achieve most (if any) of the features I described in my post.

---

