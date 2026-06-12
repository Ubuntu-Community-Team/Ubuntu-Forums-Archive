---
title: "unattended-upgrades blacklist"
date: 2010-06-03
forum: Security
---

### Post by rayrayyy on 2010-06-03
I've got the unattended-upgrades package installed on jaunty, and it's working fine to automatically install security upgrades.  However, I'd like to exclude any upgrades that would require a reboot...I'd rather upgrade those manually at my own leisure after evaluating if I really want to install those upgrades.  Is there a way to specify this in the /etc/apt/apt.conf.d/50unattended-upgrades file?  The blacklist section would work, but how would I know the name of every package that requires a reboot.  Can I use wildcards or regexes in the blacklist to exclude things like "linux-*" and "libc*"?

---

### Post by rayrayyy on 2010-08-05
Anyone have an answer for this?  I didn't find anything in the README or online documentation.

Today, the unattended-upgrades utility upgraded the linux-image-2.6.28-19-server package on one of my servers.  In my 50unattended-upgrades file, I have this:[INDENT]// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu jaunty-security";
        "Ubuntu jaunty-updates";
};

// List of packages to not update
Unattended-Upgrade::Package-Blacklist {
        "linux-server";
        "linux-image-server";
        "linux-restricted-modules-common";
        "linux-restricted-modules-server";
        "linux-libc-dev";
        "linux-firmware";
        "linux-generic";
        "linux-image-generic";
//      "vim";
        "libc6";
        "libc6-dev";
        "libc6-i386";
};
[/INDENT]Since the package name for some of the blacklisted packages will change, I'd like to be able to use regexes so that I can blacklist things like "linux-image-.*-server" and "linux-image-.*-generic".  Is this possible?

---

### Post by pezball on 2010-10-22
Did you manage to find any answer yet in other places?   I do not care about all packages whch require a reboot but I would like to install new kernels manually.   That is, all packages which have names beginning with **linux-image** and **linux-headers**
 
In your 50unattended-upgrades file you have blacklisted **linux-server** and **linux-image-server** and they can never ever match a package name such as **linux-image-2.6.28-19-server**
 
I am testing now with only blacklisting **linux-image** and **linux-headers**.    Awaiting the next time a new kernel update comes to see how it works.  
 
There might be a clue to how this is supposed to work in the executable /usr/bin/unattended-upgrades file.   It's a python script so it is normal text.    Somewhere in that file should be the code for dealing with blacklists, to find out if it does any partial string matching, or if the entire package name needs to be exactly as written in the 50unattended-upgrades file.

---

### Post by rayrayyy on 2010-10-25
> **pezball said:**
> Did you manage to find any answer yet in other places?   I do not care about all packages whch require a reboot but I would like to install new kernels manually.   That is, all packages which have names beginning with **linux-image** and **linux-headers**
 
In your 50unattended-upgrades file you have blacklisted **linux-server** and **linux-image-server** and they can never ever match a package name such as **linux-image-2.6.28-19-server**
 
I am testing now with only blacklisting **linux-image** and **linux-headers**.    Awaiting the next time a new kernel update comes to see how it works.  
 
There might be a clue to how this is supposed to work in the executable /usr/bin/unattended-upgrades file.   It's a python script so it is normal text.    Somewhere in that file should be the code for dealing with blacklists, to find out if it does any partial string matching, or if the entire package name needs to be exactly as written in the 50unattended-upgrades file.

No, I never did get any answers about using regexes in the unattended-upgrades blacklist.  I'm not familiar with coding in Python, so I don't really feel comfortable in changing the script.  However, that does seem like a promising lead to incorporating regexes in the blacklist.  I'll try to learn some Python and play with it if I have time.

---

### Post by rayrayyy on 2010-12-20
> **rayrayyy said:**
> No, I never did get any answers about using regexes in the unattended-upgrades blacklist.  I'm not familiar with coding in Python, so I don't really feel comfortable in changing the script.  However, that does seem like a promising lead to incorporating regexes in the blacklist.  I'll try to learn some Python and play with it if I have time.

I've implemented regexes into the blacklist, and it seems to be working.  There are 2 places where I made changes to /usr/bin/unattended-upgrades.  It's a Python script, so make sure your indentation is correct.

```
# diff /usr/bin/unattended-upgrade /usr/bin/unattended-upgrades.orig
29d28
< import re
77,80c76,78
<             for blacklist_regex in blacklist:
<                 if re.match(blacklist_regex,pkg.name):
<                     logging.debug("pkg '%s' blacklisted" % pkg.name)
<                     return False
---
>             if pkg.name in blacklist:
>                 logging.debug("pkg '%s' blacklisted" % pkg.name)
>                 return False

```

---

