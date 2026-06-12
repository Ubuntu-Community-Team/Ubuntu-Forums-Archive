---
title: "Proftpd slow"
date: 2010-03-27
forum: Server Platforms
---

### Post by gangsterkb on 2010-03-27
Hi,

I have posted this problem al on the nl ububtu forum but i don't have any respond so far.

I have bought a new server, its a nice one and far far more faster than the one i had. 
I have installed proftpd with mysql mod, every thins work but is really slow. 

Far slower than the one i had. 



```

Status:	Verbinden met 10.0.0.2:21...
Status:	Verbinding aangemaakt, welkomstbericht afwachten...
Antwoord:	220 ProFTPD 1.3.2 Server (Ubuntu) [10.0.0.2]
Commando:	USER jorrit
Antwoord:	331 Password required for jorrit
Commando:	PASS *********
Antwoord:	230 User jorrit logged in
Commando:	SYST
Antwoord:	215 UNIX Type: L8
Commando:	FEAT
Antwoord:	211-Features:
Antwoord:	 MDTM
Antwoord:	 MFMT
Antwoord:	 UTF8
Antwoord:	 MFF modify;UNIX.group;UNIX.mode;
Antwoord:	 MLST modify*;perm*;size*;type*;unique*;UNIX.group*;UNIX.mode*;UNIX.owner*;
Antwoord:	 LANG en-US*
Antwoord:	 REST STREAM
Antwoord:	 SIZE
Antwoord:	211 End
Commando:	OPTS UTF8 ON
Antwoord:	200 UTF8 set to on
Status:	Verbonden
Status:	Mappenlijst ophalen...
Commando:	PWD
Antwoord:	257 "/" is the current directory
Commando:	TYPE I
Antwoord:	200 Type set to I
Commando:	PASV
Antwoord:	227 Entering Passive Mode (10,0,0,2,221,210).
Commando:	MLSD
Antwoord:	150 Opening ASCII mode data connection for MLSD
Antwoord:	226 Transfer complete
Status:	Mappenlijst succesvol ontvangen

```
```

Mar 26 23:06:52 rootserver-desktop proftpd[3736] rootserver-desktop (10.0.0.1[10.0.0.1]): FTP session opened.
Mar 26 23:06:54 rootserver-desktop proftpd[3736] rootserver-desktop (10.0.0.1[10.0.0.1]): Preparing to chroot to directory '/var/www/jorrit'
Mar 26 23:06:54 rootserver-desktop proftpd[3736] rootserver-desktop (10.0.0.1[10.0.0.1]): USER jorrit: Login successful.
```
```

  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_delay.c
  mod_facts.c
  mod_dso.c
  mod_ident.c
  mod_auth_pam.c
  mod_readme.c
  mod_cap.c
  mod_ctrls.c
  mod_lang.c
```


Must mod_sql.c also there not stand?
Regards.

---

### Post by dudumomo on 2010-03-27
Hi
What do you mean by slow ?
Slow to upload ? Slow to download ? Slow to what ? And how slow ?

---

### Post by gangsterkb on 2010-03-27
I mean, slow to upload a list of files.
I have about 1500 files on my website, 100 MB before i did that in 10 sec.

Now it take long to make a connection. the transfer speed is on the other hand fast.
   
  If i upload a 1 GB file its goes with 50MB/s

---

### Post by gangsterkb on 2010-03-28
Nobody?

---

### Post by gangsterkb on 2010-03-30
This not going to work!

Switching to vsftpd

---

### Post by jrssystemsnet on 2010-03-30
> **gangsterkb said:**
> This not going to work!

Switching to vsftpd
If you don't like vsftpd either, try pure-ftpd - that's what I've been using for about eight years now; I like it a lot.

---

