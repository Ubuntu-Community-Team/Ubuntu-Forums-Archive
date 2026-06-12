---
title: "What should I do with the recently rootkitHunter scan result?"
date: 2008-07-31
forum: Security
---

### Post by thewebpromoter on 2008-07-31
Hello everybody, I hope you could help me, I was quite disturbed of my rkhunter scan result that shows the following results:

$sudo rkhunter -c
*Note: there were no warnings on the previous messages.

[...]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of Exim MTA                             [ OK ]
    Checking version of GnuPG                                [ OK ]
    Checking version of OpenSSL                              [ OK ]


System checks summary
=====================

File properties checks...
    Files checked: 122
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 5 minutes and 57 seconds


What should I do? I am using Ubuntu Hardy Heron ...

Thanks.

---

### Post by pedja_portugalac on 2008-07-31
Just edit rkhunter configuration file like this:

$sudo gedit /etc/rkhunter.conf

and add this line to the file:

ALLOWDEVFILE=/dev/shm/pulse-shm-*


After it will look like this:

# Allow the specified files to be present in the /dev directory and not
# regarded as a suspicious file.  One file per line (use multiple
# ALLOWDEVFILE lines), wildcards accepted.
#
#ALLOWDEVFILE=/dev/abc
ALLOWDEVFILE=/dev/shm/pulse-shm-*

---

### Post by miegiel on 2008-07-31
it's probably a false positive
i got the same two warnings

---

