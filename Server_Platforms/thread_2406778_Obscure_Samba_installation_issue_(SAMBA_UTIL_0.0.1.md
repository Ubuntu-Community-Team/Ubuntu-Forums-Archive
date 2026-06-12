---
title: "Obscure Samba installation issue (SAMBA_UTIL_0.0.1 not defined in file libsamba-util)"
date: 2018-11-25
forum: Server Platforms
---

### Post by kooistpa on 2018-11-25
Hi,

I ran into a strange Samba issue after fooling around in my 18.04 Server. Everything was working good, until I decided to try using my server for Time Machine backups from my Mac. This required downloading and compiling a development Samba version - and after that, everything went wrong...

The compile etc went OK, but winbind would not start. I kept getting an relocation error. After trying a lot of things (installing other packages, copying files to other directories etc), I decided I would not use the new version, and tried reverting to an original version.

Currently, I'm still stuck on getting Samba working again. I removed/purged Samba, winbind, smbd put to no avail. I keep getting an error on libsamba-util.so.0: 

```
symbol parse_guid_string version SAMBA_UTIL_0.0.1 not defined in file libsamba-util.so.0 with link time reference
```

I get this error when starting winbind, when starting samba, or when using a Samba tool.

So what are my latest steps?
-> Removing Samba

```
[COLOR=#0000cd]sudo apt-get remove samba
[/COLOR]Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  samba
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 11.2 MB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 200660 files and directories currently installed.)
Removing samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Setting up winbind (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Job for winbind.service failed because the control process exited with error code.
See "systemctl status winbind.service" and "journalctl -xe" for details.
invoke-rc.d: initscript winbind, action "start" failed.
&#9679; winbind.service - Samba Winbind Daemon
   Loaded: loaded (/lib/systemd/system/winbind.service; disabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-11-25 20:34:07 CET; 22ms ago
     Docs: man:winbindd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 31320 ExecStart=/usr/sbin/winbindd --foreground --no-process-group $WINBINDOPTIONS (code=exited, status=127)
 Main PID: 31320 (code=exited, status=127)


Nov 25 20:34:06 Orakel systemd[1]: Starting Samba Winbind Daemon...
Nov 25 20:34:07 Orakel winbindd[31320]: [COLOR=#ff0000]/usr/sbin/winbindd: relocation error: /usr/lib/x86_64-linux-gnu/samba/libsamdb-common-samba4.so: symbol parse_guid_string version SAMBA_UTIL_0.0.1 not defined in file libsamba-util.so.0 with link time reference[/COLOR]
Nov 25 20:34:07 Orakel systemd[1]: winbind.service: Main process exited, code=exited, status=127/n/a
Nov 25 20:34:07 Orakel systemd[1]: winbind.service: Failed with result 'exit-code'.
Nov 25 20:34:07 Orakel systemd[1]: Failed to start Samba Winbind Daemon.
dpkg: error processing package winbind (--configure):
 installed winbind package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libpam-winbind:amd64:
 libpam-winbind:amd64 depends on winbind (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.4); however:
  Package winbind is not configured yet.


dpkg: error processing package libpam-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
dpkg: dependency problems prevent configuration of libnss-winbind:amd64:
 libnss-winbind:amd64 depends on winbind (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.4); however:
  Package winbind is not configured yet.


dpkg: error processing package libnss-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 winbind
 libpam-winbind:amd64
 libnss-winbind:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@Orakel:/srv/usenet$
```

Some errors here, so I tried removing winbind aftert:


```
[COLOR=#0000cd]sudo apt-get remove winbind
[/COLOR]Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libnss-winbind libpam-winbind winbind
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 2,214 kB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 200468 files and directories currently installed.)
Removing libnss-winbind:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Removing libpam-winbind:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Removing winbind (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
sudo apt-get remove winbind
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libnss-winbind libpam-winbind winbind
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 2,214 kB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 200468 files and directories currently installed.)
Removing libnss-winbind:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Removing libpam-winbind:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Removing winbind (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
paul@Orakel:/srv/usenet$
```

Looks ok, so tried removing samba again:

```
paul@Orakel:/srv/usenet$ [COLOR=#0000cd]sudo apt-get remove samba
[/COLOR]Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'samba' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paul@Orakel:/srv/usenet$
```

OK, everythings looks to be gone.
Now, reinstall:

```
[COLOR=#0000cd]sudo apt-get install  samba
[/COLOR]Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  bind9 ctdb ldb-tools ntp | chrony smbldap-tools winbind
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/854 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Selecting previously unselected package samba.
(Reading database ... 200408 files and directories currently installed.)
Preparing to unpack .../samba_2%3a4.7.6+dfsg~ubuntu-0ubuntu2.4_amd64.deb ...
Unpacking samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Processing triggers for ufw (0.35-5) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for systemd (237-3ubuntu10.9) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Samba is not being run as an AD Domain Controller.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Created symlink /etc/systemd/system/multi-user.target.wants/nmbd.service &#8594; /lib/systemd/system/nmbd.service.
Failed to preset unit: Unit file /etc/systemd/system/samba-ad-dc.service is masked.
/usr/bin/deb-systemd-helper: error: systemctl preset failed on samba-ad-dc.service: No such file or directory
Created symlink /etc/systemd/system/multi-user.target.wants/smbd.service &#8594; /lib/systemd/system/smbd.service.
Processing triggers for libc-bin (2.27-3ubuntu1) ...
paul@Orakel:/srv/usenet$
```

Looks OK. So, let's add a user first thing:

```
paul@Orakel:/srv/usenet$ sudo smbpasswd -a paul[COLOR=#ff0000]smbpasswd: relocation error: /usr/lib/x86_64-linux-gnu/samba/libsamdb-common-samba4.so: symbol parse_guid_string version SAMBA_UTIL_0.0.1 not defined in file libsamba-util.so.0 with link time reference[/COLOR]
paul@Orakel:/srv/usenet$
```

Same error as before. I keep getting this same error, from various programs. Let's check if winbind is there:

```
paul@Orakel:/srv/usenet$ [COLOR=#0000cd]sudo systemctl start {nmb,smb,winbind}.service[/COLOR]
[sudo] password for paul:
Failed to start winbind.service: Unit winbind.service is masked.
paul@Orakel:/srv/usenet$

```


Nope, something wrong there. So, I tried installing winbind again:

```
[COLOR=#0000cd]sudo apt-get install winbind
[/COLOR]Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
[COLOR=#0000cd]  libnss-winbind libpam-winbind[/COLOR]
The following NEW packages will be installed:
  winbind
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/444 kB of archives.
After this operation, 1,871 kB of additional disk space will be used.
Selecting previously unselected package winbind.
(Reading database ... 200600 files and directories currently installed.)
Preparing to unpack .../winbind_2%3a4.7.6+dfsg~ubuntu-0ubuntu2.4_amd64.deb ...
Unpacking winbind (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Processing triggers for ureadahead (0.100.0-20) ...
Setting up winbind (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Created symlink /etc/systemd/system/multi-user.target.wants/winbind.service &#8594; /lib/systemd/system/winbind.service.
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for systemd (237-3ubuntu10.9) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
```

Looks ok now. For safety, I added the 2 missing packages too...

```
paul@Orakel:/srv/usenet$ [COLOR=#0000cd]sudo apt-get install libnss-winbind libpam-winbind
[/COLOR]Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  libnss-winbind libpam-winbind
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/39.3 kB of archives.
After this operation, 343 kB of additional disk space will be used.
Selecting previously unselected package libnss-winbind:amd64.
(Reading database ... 200642 files and directories currently installed.)
Preparing to unpack .../libnss-winbind_2%3a4.7.6+dfsg~ubuntu-0ubuntu2.4_amd64.deb ...
Unpacking libnss-winbind:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Selecting previously unselected package libpam-winbind:amd64.
Preparing to unpack .../libpam-winbind_2%3a4.7.6+dfsg~ubuntu-0ubuntu2.4_amd64.deb ...
Unpacking libpam-winbind:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Setting up libnss-winbind:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Setting up libpam-winbind:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.4) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
paul@Orakel:/srv/usenet$
```

Restarting Samba, Winbind:

```
paul@Orakel:/srv/usenet$ [COLOR=#0000cd]sudo systemctl start {nmb,smb,winbind}.service
[/COLOR]Job for winbind.service failed because the control process exited with error code.
See "systemctl status winbind.service" and "journalctl -xe" for details.
paul@Orakel:/srv/usenet$ [COLOR=#0000cd]sudo systemctl status winbind.service[/COLOR]
&#9679; winbind.service - Samba Winbind Daemon
   Loaded: loaded (/lib/systemd/system/winbind.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-11-25 21:13:59 CET; 23s ago
     Docs: man:winbindd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 30047 ExecStart=/usr/sbin/winbindd --foreground --no-process-group $WINBINDOPTIONS (code=exited, status=127)
 Main PID: 30047 (code=exited, status=127)


Nov 25 21:13:59 Orakel systemd[1]: Starting Samba Winbind Daemon...
Nov 25 21:13:59 Orakel winbindd[30047]: [COLOR=#ff0000]/usr/sbin/winbindd: relocation error: /usr/lib/x86_64-linux-gnu/samba/libsamdb-common-samba4.so: symbol parse_guid_string version SAMBA_UTIL_0.0.1 not defined in file libsamba-util.so.0 with link ti[/COLOR]
Nov 25 21:13:59 Orakel systemd[1]: winbind.service: Main process exited, code=exited, status=127/n/a
Nov 25 21:13:59 Orakel systemd[1]: winbind.service: Failed with result 'exit-code'.
Nov 25 21:13:59 Orakel systemd[1]: Failed to start Samba Winbind Daemon.
```

Same error. I don't even understand the error: a file with a different file version somewhere? I've searched everywhere and cannot find any solution to this problem; and have really tried everything I can think about. 

Please advise me...

---

### Post by howefield on 2018-11-25
Thread moved to the "*Server Platforms*" forum.

---

### Post by zwaardmeester on 2019-07-14
Same problem here, on Ubuntu 18.04.2

Tried purging the following samba packages

```
sudo apt purge samba samba-common samba-libs
```


and reinstall

```
sudo apt install <ubuntu-mate-desktop**> samba
```


** change <ubuntu-mate-desktop> with the ubuntu desktop package you are one. 

This did not help.

---

### Post by zwaardmeester on 2019-07-14
OK I finally managed to solve this error. I think what happens is that by manually installing samba from source, binaries (really: libraries) are created that are incompatible with the ones from the repository. One would expect that 

```
make uninstall 
```

removes all such binaries, but this appears not to be the case. 

I removed all samba libraries by hand and then reinstalled all relevant samba packages to make the system working again (note that this method is rather rigorous and I cannot vow for any adverse side effects)

**Step 1.Remove all Samba related binaries **

I choose to remove everything because that is faster. It hopefully includes all incompatible libraries from the manual installation

```

sudo bash # become root
apt purge samba winbind
cd /usr/lib/x86_64-linux-gnu/
mkdir backup-samba # any name will do here
mv libndr* backup-samba
mv libsmbclient.so.0.5.0libnss_winbind.so.2 libnss_wins.so.2 libwbclient.so.0.15 libsamba-policy.cpython-36m-x86-64-linux-gnu.so.0.0.1 libsamba-passdb.so.0.27.2 backup-samba
mv samba backup-samba # this is a directory

```

**Step 2. Reinstall minimal / client samba stuff**
```
apt search samba | grep installed
apt --reinstall install libsmbclient libwbclient0 python-samba samba-common samba-common-bin samba-libs smbclient smbldap-tools vlc-plugin-samba
```

**Step 3. (optional) Install samba server**
```
apt install samba winbind 
```

---

