---
title: "Ubuntu 8.04 updating problem w/ firewall"
date: 2014-10-06
forum: Server Platforms
---

### Post by stefano11 on 2014-10-06
Hi all,

i'm trying to update my old distro but i get this error with apt-get:

```
Err http://old-releases.ubuntu.com hardy/main Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy/restricted Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy/universe Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy/multiverse Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-updates/main Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-updates/restricted Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-updates/universe Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-updates/multiverse Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-security/main Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-security/restricted Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-security/universe Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-security/multiverse Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-backports/main Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-backports/restricted Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-backports/universe Packages
  301 Moved Permanently
Err http://old-releases.ubuntu.com hardy-backports/multiverse Packages
  301 Moved Permanently

```

I'm behind a firewall that require authentication from users who wants to navigate from browsers, so I've passed the required authenetication in apt.conf file:

```
Acquire::http::proxy "http://user:password@firewall_IP";
```

I've noticed that there must be the issue because if I give an incorrect password I get the same 301 error.
Am I using the correct syntax?

Thank you for support.

---

### Post by nerdtron on 2014-10-06
Ubuntu 8.04 Server has reached End-of-Life and is no longer supported. That's why you are having problems updating.
See: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by stefano11 on 2014-10-06
Hi nerdtron,

i knew that 8.04 is EOL, that's why i have in my repo file the link to old-releases.ubuntu.com/hardy.
If you are sure that this repo will not work because of the EOL, can you suggest a way to upgrade my 8.04 to a supported LTS version?

Thank you

---

### Post by stefano11 on 2014-10-06
Also I've found this: [https://help.ubuntu.com/community/EOLUpgrades/Hardy](https://help.ubuntu.com/community/EOLUpgrades/Hardy)
in which is said that even if you have an EOL distro, you can always upgrade to a later version.

---

### Post by ian-weisser on 2014-10-06
That page was for upgrading from 8.04 (EOL) to 10.04 (Desktop version also EOL)
Before 10.04 Desktop was EOL, sure you could 'always' upgrade to it...while it was supported.

The problem is that the release-upgrade application will be looking for repositories that do exist (the Server version is still supported)...but many desktop packages have been removed. So the upgrade seems likely to fail.

Is there some particular reason you _need_ to use the upgrade path? It will be difficult and frustrating.
Are you open to other alternatives to get you (and your data) to supported 12.04 or 14.04 versions of Ubuntu?

---

### Post by cariboo on 2014-10-07
One way to do the upgrade is to use:

```
sudo sed -i 's/hardy/precisec/g' /etc/apt/sources.list
```

the above command changes the repositories from hardy to precise, we use this to upgrade from the current version to the next development release. **Make sure you have good usable backups of your important data before trying this**

---

### Post by nerdtron on 2014-10-07
Please be reminded that Upgrades to another version are not 100% safe. Sometimes they succeed and sometimes they fail leaving you with more problems or worst it won't boot the OS at all.

---

### Post by stefano11 on 2014-10-08
**@ **ian-weisser:
I do want to get my server and my data to latest supported version. I read somewhere that it could be possible using the CD of the next LTS version, i.e.: upgrading the 8.04 to 10.04 with 10.04 live cd, then upgrade 10.04 to 12.04 always with 12.04 live cd then upgrade through apt-get. Is this correct? Can you give me some suggestion about it?
Or you were thinking at something else when you said "other alternatives"?

@ cariboo907:
I would consider you suggestion as last chance. I'd like do get through this as clean as possibile. Thank you.

@ nerdtron:
Thank you for your advice, but I need to get all the scurity update for my server. I think upgrade to latest version is the only way to solve this situation. Isn't it?

Thank you all

---

### Post by ian-weisser on 2014-10-08
I think the easiest solution is to:
1) Backup your data
2) Use a 14.04 Live media and do an install instead of an update.

The Live media will permit you to test your hardware with 14.04 before installing.
The installer will try to preserve your existing data (/home directory). Your backup will ensure fewer problems.
A new install is much faster than multiple updates.
Any six-year jump in versions may require significant changes in your applications, configuration,or customizations. A new install avoids the problems caused by multiple intermediate changes.

---

### Post by bab1 on 2014-10-08
> **ian-weisser said:**
> 
A new install is much faster than multiple updates.
Any six-year jump in versions may require significant changes in your applications, configuration,or customizations. A new install avoids the problems caused by multiple intermediate changes.

+1 to this.  I think the versions are s far apart that saving the personal config files that are in the users /home directory should not be done.  I would backup all the data and do a fresh install.  Then reintroduce the backed up data only to the users new home directory.

---

