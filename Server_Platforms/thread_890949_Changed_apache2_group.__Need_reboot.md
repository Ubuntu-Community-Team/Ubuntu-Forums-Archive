---
title: "Changed apache2 group.  Need reboot?"
date: 2008-08-15
forum: Server Platforms
---

### Post by christian.convey on 2008-08-15
I'm setting up apache2 to be a Subversion gateway, using the "libapache2-svn" package.

I'm trying to get SVN check-ins (via HTTP) to work.  One thing I've done is to modify the 'www-user' so that it's a member of the user group that is allowed to write to the SVN repository's directories.

Since running usermod, I've run "sudo apache2ctl restart", and my clients still can't check in SVN files via the HTTP interface.

Do I need to actually restart the computer, in order for my "sudo usermod -a -G svnusers www-data" to give the effect I'm looking for?

---

### Post by RealPSL on 2008-08-16
No a reboot is not required. The command ```
groups www-data
``` will show the new membership. However you should restart the process as indicated for the authentication tokens to be updated.

Another command that will show you more detail is ```
id www-data
```

---

### Post by windependence on 2008-08-16
As Realipsl has mentioned, it is very rarely necessary to reboot a *nix box, or reinstall anything either I might add. This is a Windoze mindset. Unless you are doing a kernel update there is usually always a way to make the change take effect without rebooting.

-Tim

---

