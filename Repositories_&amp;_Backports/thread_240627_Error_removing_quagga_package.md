---
title: "Error removing quagga package"
date: 2006-08-21
forum: Repositories &amp; Backports
---

### Post by soragan on 2006-08-21
I have problem removing quagga package.

# apt-get remove quagga
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  quagga
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 4157kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 26334 files and directories currently installed.)
Removing quagga ...
As requested via Debconf, the Quagga daemon will not stop.
dpkg: error processing quagga (--remove):
 subprocess pre-removal script returned error exit status 1
Loading capability module if not yet done.
Starting Quagga daemons (prio:10):.
Errors were encountered while processing:
 quagga
E: Sub-process /usr/bin/dpkg returned an error code (1)

any clue? :-k

---

### Post by Treq on 2006-09-19
Hi all, I have the same on my machine: 
----------------------
root@odin:~# apt-get --purge remove quagga
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  quagga*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4157kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88438 files and directories currently installed.)
Removing quagga ...
As requested via Debconf, the Quagga daemon will not stop.
dpkg: error processing quagga (--purge):
 subprocess pre-removal script returned error exit status 1
Loading capability module if not yet done.
Starting Quagga daemons (prio:10): zebra/usr/lib/quagga/zebra already running.
invoke-rc.d: initscript quagga, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 quagga
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@odin:~# 
----------------------

It doesn't matter if quagga is running before or not. The removal-script actually tries to start quagga again!

Does anyone know if there is a way to remove this package without this "shut down quagga first" step?

Thanks a lot!
:Kjell

---

### Post by Treq on 2006-10-04
I'll reply to myself here.
There is an error somewhere in the /var/lib/dpkg/info/quagga.prerm script, which is run before the package is removed. Or in some script that this script calls again. This script is  supposed to stop quagga and then check that this has happened before the package is removed.

There is a section in this little file that says:
-------------------------
if [ "$RET" = "false" ]; then
  db_stop
  echo "As requested via Debconf, the Quagga daemon will not stop." 1>&2
  exit 1
fi
-------------------------
This is the part that checks if the daemons have been stopped.

Basically what you can do is to:
1. Stop quagga manually: /etc/init.d/quagga stop
2. Check that the daemons are indeed not running anymore.
3. Comment out this section in the prerm-file:
-------------------------
#if [ "$RET" = "false" ]; then
#  db_stop
#  echo "As requested via Debconf, the Quagga daemon will not stop." 1>&2
#  exit 1
#fi
-------------------------
4. Remove quagga: apt-get remove --purge quagga

And that should be it. Was for me at least.

Good luck,
Treq

---

