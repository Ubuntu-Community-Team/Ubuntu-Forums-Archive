---
title: "Since this security bug"
date: 2007-10-22
forum: The Cafe
---

### Post by jobbesat on 2007-10-22
on firefox:
[http://secunia.com/advisories/27311/](http://secunia.com/advisories/27311/)

when we will have on repository the firefox version 2.0.0.8

Probably inappropriate section to post to, sorry in advance

---

### Post by shad0w_walker on 2007-10-22
I didn't spot anything mentioning the vulnerability on Linux. I know that the hole would still be there but i believe from the note that it maybe a bug that was only useful on Windows.

```
NOTE: Additional fixes have been added to prevent the exploitation of a URI handling vulnerability in Microsoft Windows.
```

If I am wrong then we should see the update fairly quickly.

---

### Post by x0as on 2007-10-22
> **shad0w_walker said:**
> I didn't spot anything mentioning the vulnerability on Linux. I know that the hole would still be there but i believe from the note that it maybe a bug that was only useful on Windows.

```
NOTE: Additional fixes have been added to prevent the exploitation of a URI handling vulnerability in Microsoft Windows.
```

If I am wrong then we should see the update fairly quickly.

> 6) An error exists in the handling of "smb:" and "sftp:" URI schemes on Linux systems with gnome-vfs support. This can be exploited to read any file owned by the target user via a specially crafted page on the same server.

This is why I dont bother using the version in the repository.

---

### Post by John.Michael.Kane on 2007-10-22
This was talked about here [http://ubuntuforums.org/showthread.php?t=582702&highlight=firefox](http://ubuntuforums.org/showthread.php?t=582702&highlight=firefox)

Bug report is here [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/154393](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/154393)

---

### Post by shad0w_walker on 2007-10-22
Whoops, guess i missed that bit about the Linux vulnerability. That's what i get for quickly reading through things i guess.

---

