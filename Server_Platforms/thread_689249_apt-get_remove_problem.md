---
title: "apt-get remove problem"
date: 2008-02-06
forum: Server Platforms
---

### Post by don_c on 2008-02-06
I thought I would do a clean up of my server since I've tried a few different programs and now don't use so many.  I did dpkg -l and found the only thing I wasn't using was pure-ftpd.  I tried to do an apt-get remove pure-ftpd but I'm then told its not installed so not removed.

Since I thought dpkg -l did a list of installed packages I'm left a bit confused...

---

### Post by cdenley on 2008-02-06
I believe "dpkg -l" lists packages installed or configured. If you remove a package, it still keeps the configuration. To remove the configuration, you can do "sudo dpkg -P pkg_name". When looking at the output of "dpkg -l", the "ii" at the beginning of the line means it is installed. If there is an "rc" instead, that means it is removed but configured.

You should look at "man apt-get" to see some other ways of cleaning up your server, like "sudo apt-get autoremove".

---

### Post by don_c on 2008-02-06
Thanks for that.  It was "rc" so the dpkg -P command worked.

---

