---
title: "samba4, cups, NT_STATUS_OBJECT_NAME_NOT_FOUND"
date: 2021-04-14
forum: Server Platforms
---

### Post by axelandress on 2021-04-14
Hi,

My environment: UBUNTU-server 20.10 and UBUNTU-server 20.04.2 LTS (and debian 10) all with current software.
Samba 4.12.5, cups 2.3.3. Standalone-server and/or AD member-server.... all show the same error:

If I start smbd via: service smbd start, the log in /var/log/samba/log.smbd shows:

  waiting for connections
[2021/04/14 11:44:44.017770,  3] ../../source3/param/loadparm.c:1683(lp_add_prin
ter)
  adding printer service HP_1100
[2021/04/14 11:44:44.017904,  3] ../../source3/lib/util_procid.c:53(pid_to_proci
d)
  pid_to_procid: messaging_dgm_get_unique failed: No such file or directory
[2021/04/14 11:44:44.017959,  3] ../../source3/lib/messages.c:925(send_all_fn)
  send_all_fn: messaging_send_buf to 1411 failed: NT_STATUS_OBJECT_NAME_NOT_FOUN
D

(I removed some lines before and after the error)

So good, so bad...

I can access the shares, I can print... "everything" looks good, except for this error.

I installed samba "out of the box", took the installes smb.conf, removed all comments und all ";" and saved this to /etc/samba/smb.conf
"testparm" shows no error.

Here is my /etc/samba/smb.conf:

root@server-11:/etc/samba# cat smb.conf
[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   server role = standalone server

   log file = /var/log/samba/log.%m
   max log size = 1000
   logging = file
   log level = 3     <---- only log level >= 3 shows the error.....

   panic action = /usr/share/samba/panic-action %d
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes

   server min protocol = NT1
   client min protocol = NT1
   username map = /etc/samba/UsernameMap_server-11
   ntlm auth = yes

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = no
   guest ok = no

[shared-11]
        comment = Freigabe für alle Benutzer
        path = /shared-11
        browseable = yes
        writeable = yes


In /var/log/samba/log.smbd I see the error mentioned above.

I was able to analyze, that this error has something to do with cups. If I stop cups and cups-browsed, smbd starts without error... But then I cannot print. Bad idea!

Possibly a question of order of starting daemons?

Any solution is welcome!

With regards
Axel Andreß

---

