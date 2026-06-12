---
title: "repair citadel mail"
date: 2018-03-22
forum: Server Platforms
---

### Post by asmith20002 on 2018-03-22
Hello,

This is ubuntu server 16.04. (no GUI)

For some reason my citadel is failing to load its config file. It won't startup. It was working just fine before. My system journal started flooding following warnings on endless loop to the  point that I had to disable system journal forward to wall in order to  gain access to my terminal.

This is syslog:

```
Mar 22 16:45:07 machine1000 citserver[32389]: *** Citadel server engine v9.01 (build a845b4f) ***
Mar 22 16:45:07 machine1000 citserver[32389]: Copyright (C) 1987-2015 by the Citadel development team.
Mar 22 16:45:07 machine1000 citserver[32389]: This program is distributed under the terms of the GNU General Public License.
Mar 22 16:45:07 machine1000 citserver[32389]:
Mar 22 16:45:07 machine1000 citserver[32389]: Called as: /usr/sbin/citserver
Mar 22 16:45:07 machine1000 citserver[32389]: libcitadel(unnumbered)
Mar 22 16:45:07 machine1000 citserver[32389]: Loading citadel.config
Mar 22 16:45:07 machine1000 citserver[32389]: Acquiring control record
Mar 22 16:45:07 machine1000 citserver[32389]: master_startup() started
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_fqdn is empty, but must not - check your config!
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_baseroom is empty, but must not - check your config!
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_aideroom is empty, but must not - check your config!
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_twitroom is empty, but must not - check your config!
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_nodename is empty, but must not - check your config!
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_default_cal_zone is empty, but must not - check your config!
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_smtp_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 25
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_pop3_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 110
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_imap_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 143
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_msa_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 587
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_port_number is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 504
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_smtps_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 465
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_pop3s_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 995
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_imaps_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 993
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_pftcpdict_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: -1
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_managesieve_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 2020
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_xmpp_c2s_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 5222
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_xmpp_s2s_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 5269
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_nntp_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 119
Mar 22 16:45:07 machine1000 citserver[32389]: configuration setting c_nntps_port is not -1 (disabled) or a valid TCP-Port - check your config! Default setting is: 563
Mar 22 16:45:07 machine1000 citserver[32389]: Checking directory access
Mar 22 16:45:07 machine1000 citserver[32389]: Opening databases
Mar 22 16:45:07 machine1000 citserver[32389]: bdb(): open_databases() starting
Mar 22 16:45:07 machine1000 citserver[32389]: Compiled db: Berkeley DB 5.3.28: (September  9, 2013)
Mar 22 16:45:07 machine1000 citserver[32389]:   Linked db: Berkeley DB 5.3.28: (September  9, 2013)
Mar 22 16:45:07 machine1000 citserver[32389]: Calculated dbversion: 5003028
Mar 22 16:45:07 machine1000 citserver[32389]:   Previous dbversion: 5003028
Mar 22 16:45:07 machine1000 citserver[32389]: Linked zlib: 1.2.8
Mar 22 16:45:07 machine1000 citserver[32389]: bdb(): Setting up DB environment
Mar 22 16:45:07 machine1000 citserver[32389]: dbenv->open(dbenv, /var/lib/citadel/data/, 75043, 0)
Mar 22 16:45:07 machine1000 citserver[32389]: Starting up DB
Mar 22 16:45:07 machine1000 citserver[32389]: DB: BDB2506 file cdb.00 has LSN 5548/7942053, past end of log at 1/28
Mar 22 16:45:08 machine1000 citadel[32278]: ...........
Mar 22 16:45:08 machine1000 systemd[1]: Stopped LSB: control citadel server start at boot time.

```

I don't want to uninstall to avoid any data/account loss. Is there anyway to repair it?

Thanks for your time.

---

### Post by volkswagner on 2018-03-23
Do you have a backup of your config file? Have you tried editing it? Is it corrupt?
It seems it can't read the config file or it's empty/corrupt.
Do you have a hard drive problem?

---

### Post by asmith20002 on 2018-03-24
I don't know where the config file is.

I setup another server and installed citadel there bt I can't find it's config file. I even searched for strings like c_pftcpdict_port but no file contains it. Any idea where is citadel config file?

---

### Post by #&amp;thj^% on 2018-03-24
> **asmith20002 said:**
> I don't know where the config file is.

I setup another server and installed citadel there bt I can't find it's config file. I even searched for strings like c_pftcpdict_port but no file contains it. Any idea where is citadel config file?

Have they changed since 14.04?
Used to be as follows:
Configuration Files and directories
```

**citadel.config 	/var/lib/citadel/data/citadel.config 		Citadel**
Server Base config
citadel.control 	/var/lib/citadel/data/citadel.control 		Citadel
 Server State File
refcount_adjustments.dat 	/var/lib/citadel/data/refcount_adjustments.dat * 		List of id's that where deleted cached.

public_clients 	/etc/citadel/public_clients 		Clients from which source ips are allowed to set the remote user ip?
nework/mail.alias 	/etc/citadel/mail.alias 		Email Address Aliases Database
help/ 	/usr/share/citadel-server/help/ 		The help files for the commandline client
messages/ 	/etc/citadel/messages/ 		Citadels Welcome messages and so on.
netconfigs/ 	/etc/citadel/netconfigs 

```
More Here: [http://www.citadel.org/doku.php/documentation:file_layout](http://www.citadel.org/doku.php/documentation:file_layout)

---

### Post by asmith20002 on 2018-03-24
Thanks for the reply. The file is there but it is not a text-based config. It seems to be binary. That's probably why I couldn't find those strings.

I'll try to replace the files and see what happens.

---

### Post by #&amp;thj^% on 2018-03-24
And maybe recheck with:
```
sudo dpkg-reconfigure citadel-server
```

---

### Post by asmith20002 on 2018-03-26
Replacing the config file removed most of those warnings. I also ran:
dpkg-reconfigure citadel-server


Citadel still doesn't work. and now I'm getting only two warnings and they are still on endless loop.


```
Broadcast message from systemd-journald@... (Mon 2018-03-26 12:47:06 UTC):

citserver[2846]: configuration setting c_default_cal_zone is empty, but must not - check your config!


Broadcast message from systemd-journald@... (Mon 2018-03-26 12:47:06 UTC):

citserver[2846]: citadel should not be configured to run as root! Check the value of c_ctdluid


Broadcast message from systemd-journald@... (Mon 2018-03-26 12:47:06 UTC):

citserver[2848]: configuration setting c_default_cal_zone is empty, but must not - check your config!


Broadcast message from systemd-journald@... (Mon 2018-03-26 12:47:06 UTC):

citserver[2848]: citadel should not be configured to run as root! Check the value of c_ctdluid

```

These messages are shown on endless loop with that process number increasing.
I don't know why I'm getting citadel shouldn't be run as root. There's already a 'citadel' user.

How do I set c_ctdluid?

---

