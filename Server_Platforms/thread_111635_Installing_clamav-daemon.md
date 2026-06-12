---
title: "Installing clamav-daemon"
date: 2006-01-02
forum: Server Platforms
---

### Post by mike4ubuntu on 2006-01-02
I'm trying to get clamav-daemon installed, but I'm having problems with one of the support package libraries.  Can anybody explain this:

$ sudo apt-get install clamav-daemon
Password:
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
  clamav-daemon: Depends: libclamav1 (>= 0.87.1) but 0.87-1 is to be installed
                 Depends: libgmp3 but it is not installable
E: Broken packages

---

### Post by Zelut on 2006-01-02
after you've tried that try sudo apt-get -f install  ...

---

### Post by heber on 2006-01-27
user@ubuntu:~$ sudo apt-get -f install clamav
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
  clamav: Depends: libclamav1 (>= 0.88) but 0.87.1-1~breezy1 is to be installed
          Depends: libgmp3 but it is not installable
E: Broken packages
user@ubuntu:~$

---

### Post by Akita on 2006-01-28
All depend on libgmp3 but it doesn't exist in the repository. A quick Goole search shows this to be a problem with a number of Debian packages.

---

