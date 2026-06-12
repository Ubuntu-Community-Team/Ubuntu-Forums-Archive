---
title: "[SOLVED] SOS -- Saved Operating System"
date: 2008-10-05
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2008-10-05
I ask the programmers to make some code that writes a file: SOS. That file would write into the /home folder.

It would know the names and revision numbers of all software installed on the 'puter and would update itself on shutdown. It could be as simple as an ascii file. Or more complex like html, so that in the event of a catastrophic failure, the user could, after getting a new hard disk or other repair measures, open the file and start re-installing the various applications.

thanks for your time.

---

### Post by Frak on 2008-10-05
That doesn't sound hard at all really. I make look into something like this.

---

### Post by schauerlich on 2008-10-05
```
ls /usr/local/bin >> ~/sos.txt
```


Repeat for /bin, /sbin, /usr/bin, and so on.

---

### Post by MaxIBoy on 2008-10-06
Does that keep track of version numbers?

---

### Post by Mark_in_Hollywood on 2008-10-06
> **Frak said:**
> That doesn't sound hard at all really. I make look into something like this.

I wanted to add a little more of my idea. And to say thanks for the support.

The SOS file should help the end-user reconfigure his entire OS/Applications and /home folder.

I started with Breezy Badger about 3 years ago and I've had to re-install the entire OS at least 6 times. Four of those involved complete loss of data. Now I can borrow an external USB drive and copy the /home to that drive. Once I reinstall the OS, then I have to search & search & search for what else was lost.

---

### Post by klange on 2008-10-06
Assuming the user isn't the kind that makes custom modifications to files outside of their home folder, and doesn't build stuff from source (without proceeding to debianize their built sources), you can do this:
```
dpkg -l > ~/SOS
```
It's not perfect (it'll show non-purged packages that you don't have installed, but you can look at the status codes to see what's actually there), but it will give you version info:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                           Description
+++-==========================================-=================================================-======================================================
rc  915resolution                              0.5.3-0ubuntu1                                    resolution modification tool for Intel graphic chipset
ii  abiword                                    2.6.4-4ubuntu2                                    efficient, featureful word processor with collaboratio
ii  abiword-common                             2.6.4-4ubuntu2                                    efficient, featureful word processor with collaboratio
ii  abiword-help                               2.6.4-4ubuntu2                                    online help for AbiWord
ii  abiword-plugin-grammar                     2.6.4-4ubuntu2                                    grammar checking plugin for AbiWord
ii  abiword-plugin-mathview                    2.6.4-4ubuntu2                                    equation editor plugin for AbiWord
ii  acl                                        2.2.47-2                                          Access control list utilities
ii  acpi                                       1.1-1ubuntu1                                      displays information on ACPI devices
ii  acpi-support                               0.112                                             scripts for handling many ACPI events
ii  acpid                                      1.0.6-9ubuntu4                                    Utilities for using ACPI power management

```

---

### Post by LaRoza on 2008-10-06
Such a feature is planned (well, a blueprint) for sysres, [https://launchpad.net/sysres](https://launchpad.net/sysres).

---

