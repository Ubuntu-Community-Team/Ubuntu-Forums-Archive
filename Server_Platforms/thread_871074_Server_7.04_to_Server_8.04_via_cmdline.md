---
title: "Server 7.04 to Server 8.04 via cmdline??"
date: 2008-07-26
forum: Server Platforms
---

### Post by dfrandin on 2008-07-26
I've been trying to upgrade a 7.04 headless server to 8.04, via the "update-manager-core/do-release-upgrade" mechanism since 7.10 was current... Everytime I try this, I get the following blast of errors...
---------------------------------------------------------------
root@mrbill:/var/lib# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting '/tmp/tmplj7CS8/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 45, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1144, in open
    raise ReadError("file could not be opened successfully")
tarfile.ReadError: file could not be opened successfully
root@mrbill:/var/lib#
---------------------------------------------------------------
I've removed the "update-manager-core" via apt-get and reinstalled it countless times.. Since this happened with both 7.10 AND 8.04 upgrade attempts, I wonder if there's a bug in the 
upgrade-manager-core for 7.04.. Its extremely infeasable to do a CD upgrade, as the server is headless, and lives nearly 250 miles away.. My only comms with the server is via VPN/ssh.. Any ideas???

Dave

---

### Post by songshu on 2008-07-26
please somebody correct me if i'm wrong, but i thought that update-manager was a GUI application only.

for some reason id not understand they made the graphical version before a CLI version....so far for a server distro.

you could always do it the way Debian does it flawlessly (but not officially recommended for Ubuntu).

simply edit your sources list
and do:
apt-get update
apt-get dist-upgrade
and 
apt-get -f dist-upgrade to force in case of errors.

---

### Post by tinny on 2008-07-26
> **songshu said:**
> please somebody correct me if i'm wrong, but i thought that update-manager was a GUI application only.

for some reason id not understand they made the graphical version before a CLI version....so far for a server distro.

you could always do it the way Debian does it flawlessly (but not officially recommended for Ubuntu).

simply edit your sources list
and do:
apt-get update
apt-get dist-upgrade
and 
apt-get -f dist-upgrade to force in case of errors.

Yes, but remember to run these commands as "sudo" :)

---

### Post by dfrandin on 2008-07-27
A bit deeper search of the links on google showed me the way.. though I had to upgrade to 7.10 first, then to 8.04.. but it did seem to work.. 04

Edit: actually the previous post was how I wound up doing it..  Was a bit nail-biting on the reboots, as I don't have any way to catch the esc button at the grub screen, being the 
system is a headless server 250 miles away... All works and is now 8.04...

Dave

---

