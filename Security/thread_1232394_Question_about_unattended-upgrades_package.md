---
title: "Question about unattended-upgrades package"
date: 2009-08-05
forum: Security
---

### Post by whitemank on 2009-08-05
I've got an Ubuntu Hardy server farm on Amazon's EC2 network.  The servers are automatically brought up from images that can be several months old as server demand increases.  We're trying to figure out a way to make sure the servers are brought up with the latest security patches and are looking at unattended-upgrades as the way to do that.  

We're planning to apt-get install the unattended-upgrades package at boot time and have pieced together instructions we've found on how to do that.  

After installing the package, we edit /etc/apt/apt.conf.d/10periodic to read: 

```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "1";
APT::Periodic::Unattended-Upgrade "1";
```

And edit /etc/apt/apt.conf.d/50unattended-upgrades to read: 
```
// Automaticall upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu hardy-security";
        //"Ubuntu hardy-updates";
};

// List of packages to not update
Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
};

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. The package 'mailx'
// must be installed or anything that provides /usr/bin/mail.
Unattended-Upgrade::Mail "webmaster@oursite.com";
```

From what I can tell we do not need to explicitly add the scripts to cron as they seem to be called through the existing apt cron scripts.  Is that true?  

How do we explicitly execute the unattended-upgrade script at startup?  We don't want to wait for the cron event to happen.  I'm not clear what executable runs the update.  

Is this the best way to handle security updates in our situation?  Any words of wisdom or caution?  Thanks!

---

