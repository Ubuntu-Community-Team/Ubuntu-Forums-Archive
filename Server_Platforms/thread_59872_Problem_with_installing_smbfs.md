---
title: "Problem with installing smbfs"
date: 2005-08-25
forum: Server Platforms
---

### Post by G.Lindqvist on 2005-08-25
I get this error:
[HTML]root@Local-Lindq:/home/guli0300 # sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  smbfs: Depends: samba-common (= 3.0.14a-3ubuntu3~5.04ubp1) but 3.0.10-1ubuntu3 is to be installed
E: Broken packages[/HTML]

I have updated apt-get and added some extra repositories. So what more can I do?

---

### Post by G.Lindqvist on 2005-08-25
Please move this thread to  "Ubuntu Repository Support"

---

### Post by G.Lindqvist on 2005-08-26
Please isn't there anything I can do to make this work? I have serach the forum for answers, but nothing.

Need smbfs to work on my server....

---

### Post by tonym on 2005-08-26
It looks as if you have picked up a version from Backports.  Did you mean to?

Try editing /etc/apt/sources.list so you only point to the standard repositories,  use dpkg to purge smbfs then try the install again.

---

### Post by G.Lindqvist on 2005-08-26
> It looks as if you have picked up a version from Backports. Did you mean to?

Try editing /etc/apt/sources.list so you only point to the standard repositories, use dpkg to purge smbfs then try the install again. 

True, that can be the case... I will try run my backup version of sources.list.

EDIT: It was the solution for my problem. Backports are evil stuff and I needed one for Ruby on Rails. Anyway, thanks tonym. ;)

---

