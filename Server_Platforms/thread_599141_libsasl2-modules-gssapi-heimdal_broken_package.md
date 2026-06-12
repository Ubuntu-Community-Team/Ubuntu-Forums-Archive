---
title: "libsasl2-modules-gssapi-heimdal broken package?"
date: 2007-11-01
forum: Server Platforms
---

### Post by coln_panic on 2007-11-01
I need gssapi support in sasl for use with a heimdal kerberos, but it won't install due to:

```
root@server:~# apt-get install libsasl2-modules-gssapi-heimdal 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsasl2-modules-gssapi-heimdal: Depends: libsasl2-modules (= 2.1.22.dfsg1-12) but 2.1.22.dfsg1-9ubuntu2 is to be installed
E: Broken packages
```

is it (somewhat) safe to just modify the package to accept the installed version of libsasl2-modules, or what are the proper steps to take to get this fixed?  it is a 7.10 install on i386.

thanks,
jay

---

### Post by coln_panic on 2007-11-01
i guess seeing as how i don't have that much stuff in heimdal kerberos i can probably just start over with mit since that modules will install... but i would like do it right and fix this problem.

is there a resource to look at to find where to start with something like this?  i haven't done much with ubuntu packages.

---

### Post by Despot on 2008-01-12
This is a bit late in coming, but you can work around the broken dependency by download the deb to your harddrive, and installing if from the commandline thusly:

sudo dpkg -i --ignore-depends=libsasl2-modules libsasl2-modules-gssapi-heimdal_2.1.22.dfsg1-12_amd64.deb

Then edit /var/lib/dpkg/status, and remove the libsasl2-modules from the list of dependencies for libsasl2-modules-gssapi-heimdal. For safety, I recommend duplicating the original line, commenting out the original with a "#" and then editing the duplicate.

---

