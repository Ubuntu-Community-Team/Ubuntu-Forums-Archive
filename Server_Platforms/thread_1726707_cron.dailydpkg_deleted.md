---
title: "cron.daily/dpkg deleted"
date: 2011-04-11
forum: Server Platforms
---

### Post by dasherjan on 2011-04-11
I&#8217;ve been trying out Ubuntu server 10.10. Unfortunately I&#8217;ve done a boneheaded thing and deleted the file &#8220;dpkg&#8221; in the /etc/cron.daily directory. My intention was to delete ntpdate. So I could install the ntp service. 


My questions are: Is there a common backup of the dpkg file on the system? If not what should be in the file so I can recreate it? I&#8217;ve tried searching Google, the Ubuntu forums and the server guide but haven&#8217;t found anything so far. Though, I can&#8217;t image I&#8217;m the first one to do this.  :)

Any help or links would be greatly appreciated!

---

### Post by DaithiF on 2011-04-11
Hi, here are the contents of /etc/cron.daily/dpkg on my 10.10:
```
#!/bin/sh

# Backup the 7 last versions of dpkg's status file
if cd /var/backups ; then
    if ! cmp -s dpkg.status.0 /var/lib/dpkg/status ; then
            cp -p /var/lib/dpkg/status dpkg.status
            savelog -c 7 dpkg.status >/dev/null
    fi
fi

```

---

### Post by dasherjan on 2011-04-12
Thank you. I'll try it out and see if anything crazy starts to happen.   :)

---

### Post by gmargo on 2011-04-12
Just reinstall the package that the file came from:
```

$ dpkg -S /etc/cron.daily/dpkg
dpkg: /etc/cron.daily/dpkg

$ sudo aptitude reinstall dpkg
-or-
$ sudo apt-get --reinstall install dpkg

```

---

