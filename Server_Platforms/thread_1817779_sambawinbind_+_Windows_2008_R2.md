---
title: "samba/winbind + Windows 2008 R2"
date: 2011-08-03
forum: Server Platforms
---

### Post by remmargorp on 2011-08-03
Intent is to use samba+winbind to authenticate Ubuntu desktop against a Windows 2008 R2 domain (seems like I was able to get it working temporarily but it stopped working after some time).


Quick overview of the issue: winbind is failing to lookup group ID's for a domain user causing the domain user to receive group errors on login and an inability to use domain groups in other configuration (sudoers, etc)


- Very basic install, boot to Ubuntu Desktop 10.04 LTS 64bit install, basic install options, perform software updates

- Following an Ubuntu AD HowTo ([https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto))

- Install kerberos, samba, winbind packages
- Make changes to krb5.conf, smb.conf, files in pam.d/ (to make the home directory and restrict login based on group membership, which works even in the half-working state but requires SID instead of text name)


After a reboot I can login as a domain account but I get the following error(s):
    groups: cannot find name for group ID #####

##### is usually a number that ranges from 10000 to 10020, based on the smb.conf line regarding idmap

I will get multiple group errors (one for each group that the user belongs to that winbind can't lookup for whatever reason, some groups can be resolved - see below)


If I log-out and then log-in as a local user I can run the following command: id username

The output returns something similar to the following:

uid=10002(username) gid=10003(domain users) groups=10003(domain users),10033,10032,10031,10030,10029,10028,10027,10026,10025,10024,10023,10022,10021(some group),10020,10019,10018(some other group),10017,10016,10015,10014,10013,10012,10011(some other other group),10010,10009,10008,10007

On a working system (Ubuntu 10.10 and when 10.04 decides to work) each group is followed by parenthesis' and the name of the group, this result clearly shows that some groups can be looked up but for some reason other groups are failing


An output of /var/log/samba/log.winbind produces the following entries (that are logged when you run the id command)

[2011/08/03 19:04:39,  1] winbindd/winbindd_ads.c:1137(lookup_groupmem)
  lsa_lookupsids call failed with NT_STATUS_PIPE_BROKEN - retrying...
[2011/08/03 19:04:39,  1] winbindd/winbindd_ads.c:1137(lookup_groupmem)
  lsa_lookupsids call failed with NT_STATUS_PIPE_BROKEN - retrying...

The above repeats for what looks to be each group that fails (based on count of entries)


If I use wbinfo I can resolve text group name to SID and SID to GID
wbinfo -n groupname (returns proper SID)
wbinfo -s SID (returns proper text group name)
wbinfo -Y SID (returns proper linux mapped group ID)

Following that process for a group that my user belongs to that is not resolving (via the id username command) will return the group ID (GID) properly (even though id username fails to lookup info for that same GID)


Version Information:

uname -a
Linux hostname 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 x86_64 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:        10.04
Codename:       lucid

wbinfo -V
Version 3.4.7

smbstatus
Samba version 3.4.7



Hopefully someone can help - I've read through tons of post/mailing-lists only to find people with same/similar issues and no responses (along the way I've run into other issues with samba/winbind only to find people with the same issue and no solution)

---

### Post by remmargorp on 2011-08-03
I believe I found the solution to my issue (hopefully this helps someone in the future)


Steps to identify issue:
- enable "log level = 10" in smb.conf and restart
- clear the logs
- issue command "id username"
- review /var/log/samba/log.winbind-dc-connect


Following the log output I can see it connect to the DC I would expect it to connect to, I can see it query some info, I can see it connect to a trusted domain that exists (looks like connect alphabetically)

When it tries to look up information for that domain it is failing to perform the look-up and stops processing other trusted domains (including the domain I need it to process, which happens to be that last in the list alphabetically)


The solution: add "allow trusted domains = no" in smb.conf and restart

This solution may not work for other users, but in this case I only need this system to authenticate/validate users/groups for the domain it is in


To validate I added the configuration line above, restarted, logged in and ran "id username", it returned with the user and all of the groups with textual group names

I removed the config line and restarted, ran "id username" and it returned only a few groups with textual group names. Added the config line - repeat and it worked as expected

---

### Post by WhiteHorse on 2011-08-04
Try this:
man group

---

### Post by remmargorp on 2011-08-04
joking?

man group isn't going to provide information for this as winbind does not use /etc/group

---

