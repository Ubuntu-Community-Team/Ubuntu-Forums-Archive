---
title: "rkhunter inode change warnings"
date: 2008-01-13
forum: Server Platforms
---

### Post by ysr on 2008-01-13
I ran rkhunter this morning and got warnings about 49 suspect files. On inspecting the rkhunter.log I find that all of them are similar to the ones below (i.e. warning about inode changes). 

Apart from installing updates from time to time, I can't recall anything else of significance. Any body else with similar experience.

I guess I can run --propupd to update the rkhunter database and get rid of the messages, and the fact that it is only the inode that has changed (and not the file hash or similar) is somewhat reassuring, but would like to know what might have triggered this deluge of warnings.

```

[12:46:30] /bin/bash                                         [ Warning ]
[12:46:30] Warning: The file properties have changed:
[12:46:30]          File: /bin/bash
[12:46:30]          Current inode: 74217    Stored inode: 1775397
[12:46:30] /bin/cat                                          [ Warning ]
[12:46:30] Warning: The file properties have changed:
[12:46:30]          File: /bin/cat
[12:46:30]          Current inode: 74230    Stored inode: 1775410
[12:46:31] /bin/chmod                                        [ Warning ]
[12:46:31] Warning: The file properties have changed:
[12:46:31]          File: /bin/chmod
[12:46:31]          Current inode: 74233    Stored inode: 1775413
[12:46:31] /bin/chown                                        [ Warning ]
[12:46:31] Warning: The file properties have changed:
[12:46:31]          File: /bin/chown
[12:46:31]          Current inode: 74234    Stored inode: 1775414
...
...
...

```

---

### Post by ysr on 2008-01-20
Further to my earlier posts, I have downloaded the relevant packages and compared manually the sha1sums against those of the suspect files. I find that 46 of the 49 match perfectly against the downloaded packages.

One of the three mismatches is /bin/sh. This is supplied by the package /base/bash where the three files bash, rbash and sh are identical. However, on my system /bin/sh is a link to /bin/dash. Hence the sha1sum does not match up.

Is it the same for everybody else - i.e. /bin/sh being a link to /bin/dash. (I checked the sha1sum for /bin/dash and it is fine). 

The other two (/sbin/init and /sbin/runlevel) are supplied by multiple packages - I guess this is expected as Ubuntu uses "upstart" instead of the old init scripts, but the old style packages are still available from [http://packages.ubuntu.com](http://packages.ubuntu.com). The sha1sums for these two files match those from upstart, so no problems there.

I am about to run --propupd on rkhunter, as these look like false positives. Could somebody who is more knowledgeable about these things please let me know if they believe there is some reason I should not be running --propupd. Thanks in advance.

---

### Post by PaJoe on 2008-02-04
I found in the rkhunter FAQ 4.4, something about prelinking problems and running hashupd.sh, but it resulted in the following werrror on my kubuntu gutsy system:

[FATAL] Could not find os.dat in "/var/lib/rkhunter/db", exiting

---

