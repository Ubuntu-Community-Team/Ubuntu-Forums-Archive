---
title: "Samba isn't honouring secondary groups"
date: 2008-08-27
forum: Server Platforms
---

### Post by RandomJon on 2008-08-27
Hi
I have a problem with samba on ubuntu 8.04 using samba 3.0.28a and authenticating via likewise open. For some reason samba doesn't respect users secondary groups for filesystem permissions.

I.e. if I run "chgrp "DOMAIN\group filename" on a folder/file and the user belongs to "DOMAIN\group" but is not his/her primary group samba won't obey the permissions set for group (rwx in this case)

Samba works if the owner is the user or if the group is the users primary group which leads me to believe the auth is working and samba just isnt respecting the groups?

NB: lwiinfo / wbinfo show all these groups / users correctly, groups correctly show the users groups and members correctly shows the members of the group.

Anyone got any ideas?

---

### Post by trainerbill on 2008-10-30
As far as I know samba 3.2.x will be supporting Windows Domain secondary groups.... It is included in Intrepid Ibex.  Hardys version is 3.0.28x.  I was hoping they would back port it to hardy since it is LTS but it doesn't look like this will be happening

Common bugs fixed in Samba 3.0.3 include:

~ o Crash bugs and change notify issues in Samba's
~ printing code.
~ o [B]Honoring secondary group membership on domain member
~ servers.[/B]
~ o TDB scalability issue surrounding the TDB_CLEAR_IF_FIRST
~ flag.
~ o Substitution errors for %[UuGg] in smb.conf.
~ o winbindd crashes when using ADS security mode.
~ o SMB signing errors.
~ o Delays in winbindd startup caused by unnecessary
~ connections to trusted domain controllers.
~ o Various small memory leaks.
~ o Winbindd failing due to expired Kerberos tickets.

---

