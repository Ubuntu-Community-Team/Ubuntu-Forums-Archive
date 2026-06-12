---
title: "Problem trying to uninstall Fail2Ban"
date: 2006-10-09
forum: Server Platforms
---

### Post by Scrappy_D on 2006-10-09
Hi,

I've been trying to uninstall a failed package (fail2ban), and this is the output from dpkg:

 dpkg -r --force-remove-reinstreq fail2ban
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 35395 files and directories currently installed.)
Removing fail2ban ...
W: Unable to locate package python-all
E: No packages found
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1325, in ?
    main()
  File "/usr/bin/pycentral", line 1319, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 919, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 196, in get_installed_runtimes
    supported = pyversions.supported_versions()
  File "/usr/share/pycentral-data/pyversions.py", line 71, in supported_versions
    depends = [re.sub(r'\s*(\S+)[ (]?.*', r'\1', s) for s in depends]
TypeError: iteration over non-sequence
dpkg: error processing fail2ban (--remove):
 subprocess pre-removal script returned error exit status 1
W: Unable to locate package python-all
E: No packages found
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1325, in ?
    main()
  File "/usr/bin/pycentral", line 1319, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 850, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 196, in get_installed_runtimes
    supported = pyversions.supported_versions()
  File "/usr/share/pycentral-data/pyversions.py", line 71, in supported_versions
    depends = [re.sub(r'\s*(\S+)[ (]?.*', r'\1', s) for s in depends]
TypeError: iteration over non-sequence
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 fail2ban

No matter what it will not be uninstalled :(
And there is no ubuntu package named python-all that I can find anywhere ....

Anyone know how I can fix this?

---

### Post by Scrappy_D on 2006-10-10
*BUMP*

APT is now fubar'd thanks to the dodgy fail2ban package :(

To prevent anyone else having the same issue, can I suggest that if you need fail2ban that you download the tar ball and install it manually as all the required 'ubuntu' packages are not there and it will fail and cause alot of headaches ....

---

