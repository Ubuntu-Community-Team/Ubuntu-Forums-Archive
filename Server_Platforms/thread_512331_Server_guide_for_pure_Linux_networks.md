---
title: "Server guide for pure Linux networks"
date: 2007-07-29
forum: Server Platforms
---

### Post by sitedesign on 2007-07-29
I have been setting up Linux server for some time and find the documentation of a distribution most important, hence my choice of Ubuntu, very large community supporting others.

I have been looking for a guide on setting up Ubuntu server for a pure Ubuntu network.
For instance what would be the best for the following:
1) File sharing with permanent mounting (SSHFS, NFS, SMBFS, CIFS) - I have found issues with the samba ones.
2) Print sharing - from clients to clients via server and server to clients (Cups, LPD, Samba)
3) User management (shell, Webmin, another tool) - webmin sorts the samba users when a unix user is created but wouldn't it be much nicer to be able to change the password in one place like domain login style instead of changing the local user password and the password on the server (which both users would be considered different) - depends on the file sharing above.
4) Systems management - nice tool to management software installs and upgrades across lots of machines on the network without having to go to each one and login as the user (having to have a list of users/passwords) - I know LTSP solves some of these by removing their need, but as our workstation power requirements grow the server would become too expensive compared to a couple of power workstations.

It would be great to see more guides on this type of set-up as I have found the documentation aimed at Windows clients with a Linux server, 
Maybe if I post a question about each of the areas and get the answers together we could piece together a Guide from the posts and get it on the help site.
Let me know if anyone else has had these issues and might like to post replies to help put together this document.

---

### Post by koenn on 2007-07-29
1- for a linux only environment, I'd pick a *nix native ; samba is originally designed for compatibility with WIndows file sharing, so not necesarily your best choice. 

2- beats me, no experience here.

3- you'd probably want centralized user management and possibly a single-sign-on. Look into OpenLDAP and Kerberos - search this forum for a single-sign-on HOWTO (or Google)

4- Don't know of any. There's probably commercial sollutions out there, but you could actually do a lot with cron jobs or a script that executes apt-get update / install statements remotely, over ssh.
something like (concept)
```

for COMPUTER in $(cat list_of_computers) : do
                 ssh root@$COMPUTER apt-get -y install new_software
done

```

---

