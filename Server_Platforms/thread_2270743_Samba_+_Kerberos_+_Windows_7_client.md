---
title: "Samba + Kerberos + Windows 7 client:"
date: 2015-03-25
forum: Server Platforms
---

### Post by peridian on 2015-03-25
Hi,

I have a Samba installation on Ubuntu server 14.04.2 (smb.conf file included below).  It uses Kerberos 5/openLDAP in the background to auth users.

I can successfully perform the following from any Linux client.

```

kinit username@REALM
smbclient -k -L //server.domain
smbclient -k //server.domain/share

```

I can take any action in the smbclient window and see that reflected on the file system with all the correct file/folder permissions.

---

I then have a Windows 7 Home Premium x64 client.  However, if I try to access \\server.domain\share, there is a huge delay, and then it prompts for username and password.  I enter the credentials for the same username@REALM, and get told "The specified network password is not correct."

If I try to browse to the root at \\server.domain\ it prompts almost immediately, but gives the error "Logon failure: unknown user name or bad password."

I have successfully installed "Kerberos for Windows" on the Win7 client, and it can obtain a ticket for the username.  Unfortunately, I can't then use that ticket when browsing to the share, but it proves that the credentials are correct.

Have I misconfigured Samba?  Do I need any additional services on Samba for this to be inter-operable (e.g. KCRAP)?

Regards,
Rob.

/etc/samba/smb.conf

```

[global]
        workgroup = REALM
        realm = REALM
        netbios name = HOSTNAME
        server string = Samba server
        server role = standalone
        server services = smb


        hosts allow = 10.
        dns proxy = no
        dns forwarder = 10.x.x.x


        interfaces = lo, em1
        bind interfaces only = yes


        syslog = 0
        log file = /var/log/samba/log.%m
        panic action = /usr/share/samba/panic-action %d


        kerberos method = dedicated keytab
        dedicated keytab file = /var/lib/samba/samba.keytab


        load printers = no
        printing = bsd
        printcap name = /dev/null
        disable spoolss = yes
        cups options = raw


        socket options = TCP_NODELAY


        level2 oplocks = no
        oplocks = no


[...shares...]

```

---

### Post by robsoles on 2015-03-25
Is that the actual and full content of your /etc/samba/smb.conf file?


Edit: Maybe I'm wrong; fair while since I made a few samba servers work for the people who wanted them and ages since I poked my nose in the smb.conf of my own file server so maybe they've updated so much that somehow that is enough of an smb.conf file but it must be snipped after shares *- oh, I am tired; Goodnight :)*

---

### Post by peridian on 2015-03-26
Hi,

Yes I have snipped the shares details out, as they were extensive and unnecessary for this post.  The rest is all that is in my smb.conf file; most settings for Samba are correct by default, and since this is not a domain-joined configuration, there is very little to setup.  The authentication is Kerberos, and the authorisation is the underlying file system, which is a Kerberized PAM setup.

After some more testing, the first problem turned out to be snort triggering due to what it thought was malicious activity, which was obviously incorrect so I disabled the rule.

I then temporarily dropped all firewalls between the client and the server to rule out port issues.  At first I could not find any entries in the logs for the Samba server.  Then I looked on the KDC server, and found the below:

```

Mar 26 19:38:27 kdc.server.domain krb5kdc[1711](info): TGS_REQ (6 etypes {18 17 16 23 25 26}) 10.x.x.x: ISSUE: authtime 1427392360, etypes {rep=18 tkt=18 ses=18}, host/samba.server.domain@REALM for ldap/ldap.server.domain@REALM
Mar 26 19:39:34 kdc.server.domain krb5kdc[1711](info): AS_REQ (6 etypes {18 17 16 23 25 26}) 10.x.x.x: CLIENT_NOT_FOUND: NOUSER@REALM for <unknown server>, Client not found in Kerberos database

```

It seems my credentials are not coming through correctly, even though I type them correctly in Win7.

Any ideas why Samba may be translating the username into "NOUSER"?

Regards,
Rob.

---

### Post by robsoles on 2015-03-26
no user - anonymous perhaps?

---

### Post by peridian on 2015-03-27
Well, it's looking more and more like it's a M$ annoyance.  Apparently NOUSER is being used because Samba is not able to decrypt the credentials correctly.  Whether this is because it's simply passing the credentials straight through to Kerberos expecting them to be a valid ticket already or not, I do not know.

I have set a number of registry settings (courtesy of [this thread]("http://ubuntuforums.org/showthread.php?t=1330637")) and group policy settings (courtesy of [this article]("http://support.microsoft.com/en-us/kb/977321")) but it hasn't resolved it.

Rather annoyingly, I have an old Samba installation that did all its user authentication via LDAP only (no Kerberos), and that can be browsed quite happily from the same Win7 client (because it matches the name of the local account on the client to the cn on the LDAP record; this is obviously not very secure and I had wanted to get rid of that).

I had assumed (incorrectly) that Samba was decrypting the NTLM credentials, and in this new setup would continue to do so whilst handling the connection to Kerberos, but it looks like that's not how it works.

Everybody is telling me you need Win7 Pro and setup Samba as a PDC so you can join to it.  I think this is bull.

I have installed Kerberos for Windows along with Network Identity Manager, and that can happily obtain the necessary Kerberos ticket, but unfortunately native Windows applications (i.e. Windows Exploder) won't make use of that ticket, and I cannot find an equivalent application that will.

Grrrrr.....

---

### Post by robsoles on 2015-03-27
Come to think of it, pretty sure all my old installs of Samba are as PDC and WinXP clients can 'join the domain' very happily but Windows 7 is (was last I tried at least) a total pain to attempt 'joining' but for a matter of just accessing the shares it was all fine.

Pretty sure I am using PAM because I just couldn't be bothered going to the trouble of Kerberos after some reading. Ages since I had to do anything, my old installs are surviving updates and users aren't moaning so I don't find motivation to look at them.

It just happens, also, that all the PCs running Windows 7 that I have tried accessing any of my installs with has been the 64 bit Pro version - there is a laptop here with (blech) Windows 8.x on it that browses the shares more than adequately, pretty sure it is just home edition.

[quote=peridian]Everybody is telling me you need Win7 Pro and setup Samba as a PDC so you can join to it.  I think this is bull.[/quote]Just saying: I can't reassure you that it is bull.


Edit: Probably is your Kerberos install or some fiddly config item hiding away in either system - can you describe your Kerberos setup more, I can't see how your Samba install is accessing your Kerberos install?

---

### Post by peridian on 2015-03-27
Ahh, I might take some of what I said back.  It looks like Samba does get the credentials correctly, but doesn't handle them right.

I turned Samba logging levels up to 10, and after some eye-bleeding reading through the output (dump below) I have identified what it is doing.

It seems to be taking a credential of "username@REALM" and turning it into "[SMBSERVER]\[username@REALM]@[WIN7CLIENT]" because the User-Name field gets populated with whatever I have typed in, which of course I specify the Kerberos Realm in that, otherwise it would default to a Realm named after my workstation.

I don't think Samba knows what to do with the resulting username.

Regards,
Rob.

```

[2015/03/27 11:29:31.857584,  6, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:2657(lp_file_list_changed)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Fri Mar 27 11:27:05 2015
  
[2015/03/27 11:29:31.857896,  3, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/access.c:338(allow_access)
  Allowed connection from 10.x.x.x (10.x.x.x)
[2015/03/27 11:29:31.857972, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/process.c:3475(smbd_process)
  Connection allowed from ipv4:10.x.x.x:50530 to ipv4:10.x.x.x:445
[2015/03/27 11:29:31.858265,  3, pid=18337, effective(0, 0), real(0, 0), class=locking] ../source3/smbd/oplock.c:870(init_oplocks)
  init_oplocks: initializing messages.
[2015/03/27 11:29:31.858339,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 774 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.858405,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 776 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.858470,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 778 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.858533,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 770 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.858599,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 787 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.858679,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 779 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.858752,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 15 - private_data=(nil)
[2015/03/27 11:29:31.858817,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:308(messaging_register)
  Overriding messaging pointer for type 15 - private_data=(nil)
[2015/03/27 11:29:31.858887,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:340(messaging_deregister)
  Deregistering messaging pointer for type 16 - private_data=(nil)
[2015/03/27 11:29:31.858953,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 16 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.859018,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:340(messaging_deregister)
  Deregistering messaging pointer for type 33 - private_data=0x7f8c7a4d63c0
[2015/03/27 11:29:31.859083,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 33 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.859147,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:340(messaging_deregister)
  Deregistering messaging pointer for type 1 - private_data=(nil)
[2015/03/27 11:29:31.859211,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 1 - private_data=(nil)
[2015/03/27 11:29:31.859298, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/events.c:483(event_add_idle)
  event_add_idle: idle_evt(keepalive) 0x7f8c7a4e6d70
[2015/03/27 11:29:31.859372, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/events.c:483(event_add_idle)
  event_add_idle: idle_evt(deadtime) 0x7f8c7a4e6fc0
[2015/03/27 11:29:31.859442, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/events.c:483(event_add_idle)
  event_add_idle: idle_evt(housekeeping) 0x7f8c7a4ea340
[2015/03/27 11:29:31.859635, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/util_sock.c:337(read_smb_length_return_keepalive)
  got smb length of 104
[2015/03/27 11:29:31.859740,  6, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/process.c:1793(process_smb)
  got message type 0x0 of len 0x68
[2015/03/27 11:29:31.859811,  3, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/process.c:1795(process_smb)
  Transaction 0 of length 108 (0 toread)
[2015/03/27 11:29:31.859881, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2885(smbd_smb2_first_negprot)
  smbd_smb2_first_negprot: packet length 108
[2015/03/27 11:29:31.859975, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:621(smb2_validate_sequence_number)
  smb2_validate_sequence_number: clearing id 0 (position 0) from bitmap
[2015/03/27 11:29:31.860056, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:1878(smbd_smb2_request_dispatch)
  smbd_smb2_request_dispatch: opcode[SMB2_OP_NEGPROT] mid = 0
[2015/03/27 11:29:31.860140,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.860216,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.860293,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.860417,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.860615, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/util.c:1277(set_remote_arch)
  set_remote_arch: Client arch is 'Vista'
[2015/03/27 11:29:31.860728,  6, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:2657(lp_file_list_changed)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Fri Mar 27 11:27:05 2015
  
[2015/03/27 11:29:31.860860,  3, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_negprot.c:243(smbd_smb2_request_process_negprot)
  Selected protocol SMB2_10
[2015/03/27 11:29:31.860977,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:464(make_auth_context_subsystem)
  Making default auth method list for server role = 'standalone server', encrypt passwords = yes
[2015/03/27 11:29:31.861072,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend sam
[2015/03/27 11:29:31.861141,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'sam'
[2015/03/27 11:29:31.861204,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend sam_ignoredomain
[2015/03/27 11:29:31.861279,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'sam_ignoredomain'
[2015/03/27 11:29:31.861395,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend unix
[2015/03/27 11:29:31.861463,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'unix'
[2015/03/27 11:29:31.861529,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend winbind
[2015/03/27 11:29:31.861596,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'winbind'
[2015/03/27 11:29:31.861658,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend wbc
[2015/03/27 11:29:31.861721,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'wbc'
[2015/03/27 11:29:31.861783,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend trustdomain
[2015/03/27 11:29:31.861847,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'trustdomain'
[2015/03/27 11:29:31.861909,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend ntdomain
[2015/03/27 11:29:31.861973,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'ntdomain'
[2015/03/27 11:29:31.862035,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend guest
[2015/03/27 11:29:31.862098,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'guest'
[2015/03/27 11:29:31.862161,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:351(load_auth_module)
  load_auth_module: Attempting to find an auth method to match guest
[2015/03/27 11:29:31.862232,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:376(load_auth_module)
  load_auth_module: auth method guest has a valid init
[2015/03/27 11:29:31.862301,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:351(load_auth_module)
  load_auth_module: Attempting to find an auth method to match sam
[2015/03/27 11:29:31.862379,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:376(load_auth_module)
  load_auth_module: auth method sam has a valid init
[2015/03/27 11:29:31.865838,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_spnego' registered
[2015/03/27 11:29:31.865969,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_krb5' registered
[2015/03/27 11:29:31.866041,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_krb5_sasl' registered
[2015/03/27 11:29:31.866116,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'schannel' registered
[2015/03/27 11:29:31.866187,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'spnego' registered
[2015/03/27 11:29:31.866255,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'ntlmssp' registered
[2015/03/27 11:29:31.866328,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'krb5' registered
[2015/03/27 11:29:31.866393,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'fake_gssapi_krb5' registered
[2015/03/27 11:29:31.866653,  5, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:649(gensec_start_mech)
  Starting GENSEC mechanism spnego
[2015/03/27 11:29:31.866777,  5, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:649(gensec_start_mech)
  Starting GENSEC submechanism gse_krb5
[2015/03/27 11:29:31.868645, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/krb5_wrap/krb5_samba.c:1266(smb_krb5_open_keytab)
  smb_krb5_open_keytab: resolving: FILE:/var/lib/samba/samba.keytab
[2015/03/27 11:29:31.869670,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 1536 - private_data=0x7f8c7a4eed80
[2015/03/27 11:29:31.869736, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2499(smbd_smb2_request_done_ex)
  smbd_smb2_request_done_ex: idx[1] status[NT_STATUS_OK] body[64] dyn[yes:96] at ../source3/smbd/smb2_negprot.c:387
[2015/03/27 11:29:31.869782, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:874(smb2_set_operation_credit)
  smb2_set_operation_credit: requested 31, charge 1, granted 1, current possible/max 512/512, total granted/max/low/range 1/8192/1/1
[2015/03/27 11:29:31.872376, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:3241(smbd_smb2_io_handler)
  smbd_smb2_request idx[1] of 5 vectors
[2015/03/27 11:29:31.872434, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:621(smb2_validate_sequence_number)
  smb2_validate_sequence_number: clearing id 1 (position 1) from bitmap
[2015/03/27 11:29:31.872468, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:1878(smbd_smb2_request_dispatch)
  smbd_smb2_request_dispatch: opcode[SMB2_OP_SESSSETUP] mid = 1
[2015/03/27 11:29:31.872500,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.872531,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.872562,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.872615,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.872666,  5, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:187(dbwrap_check_lock_order)
  check lock order 1 for /var/run/samba/smbXsrv_session_global.tdb
[2015/03/27 11:29:31.872700, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:133(debug_lock_order)
  lock order:  1:/var/run/samba/smbXsrv_session_global.tdb 2:<none> 3:<none>
[2015/03/27 11:29:31.872734, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:59(db_tdb_log_key)
  Locking key 021B776B
[2015/03/27 11:29:31.872772, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:143(db_tdb_fetch_locked_internal)
  Allocated locked data 0x0x7f8c7a4ebd50
[2015/03/27 11:29:31.872973, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smbXsrv_session.c:853(smbXsrv_session_global_store)
[2015/03/27 11:29:31.873005, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smbXsrv_session.c:855(smbXsrv_session_global_store)
  smbXsrv_session_global_store: key '021B776B' stored
[2015/03/27 11:29:31.873040,  1, pid=18337, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       &global_blob: struct smbXsrv_session_globalB
          version                  : SMBXSRV_VERSION_0 (0)
          seqnum                   : 0x00000001 (1)
          info                     : union smbXsrv_session_globalU(case 0)
          info0                    : *
              info0: struct smbXsrv_session_global0
                  db_rec                   : *
                  session_global_id        : 0x021b776b (35354475)
                  session_wire_id          : 0x00000000021b776b (35354475)
                  creation_time            : Fri Mar 27 11:29:32 2015 GMT
                  expiration_time          : Thu Jan  1 01:00:00 1970 BST
                  auth_session_info_seqnum : 0x00000000 (0)
                  auth_session_info        : NULL
                  connection_dialect       : 0x0210 (528)
                  signing_required         : 0x00 (0)
                  encryption_required      : 0x00 (0)
                  num_channels             : 0x00000001 (1)
                  channels: ARRAY(1)
                      channels: struct smbXsrv_channel_global0
                          server_id: struct server_id
                              pid                      : 0x00000000000047a1 (18337)
                              task_id                  : 0x00000000 (0)
                              vnn                      : 0xffffffff (4294967295)
                              unique_id                : 0x760e04c556881c25 (8506741991756274725)
                          local_address            : 'ipv4:10.x.x.x:445'
                          remote_address           : 'ipv4:10.x.x.x:50530'
                          remote_name              : '10.x.x.x'
                          auth_session_info_seqnum : 0x00000000 (0)
[2015/03/27 11:29:31.873499, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:59(db_tdb_log_key)
  Unlocking key 021B776B
[2015/03/27 11:29:31.873535,  5, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:146(dbwrap_lock_order_state_destructor)
  release lock order 1 for /var/run/samba/smbXsrv_session_global.tdb
[2015/03/27 11:29:31.873566, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:133(debug_lock_order)
  lock order:  1:<none> 2:<none> 3:<none>
[2015/03/27 11:29:31.873598, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smbXsrv_session.c:1215(smbXsrv_session_create)
[2015/03/27 11:29:31.873619, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smbXsrv_session.c:1223(smbXsrv_session_create)
  smbXsrv_session_create: global_id (0x021b776b) stored
[2015/03/27 11:29:31.873648,  1, pid=18337, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       &session_blob: struct smbXsrv_sessionB
          version                  : SMBXSRV_VERSION_0 (0)
          reserved                 : 0x00000000 (0)
          info                     : union smbXsrv_sessionU(case 0)
          info0                    : *
              info0: struct smbXsrv_session
                  table                    : *
                  db_rec                   : NULL
                  connection               : *
                  local_id                 : 0x021b776b (35354475)
                  global                   : *
                      global: struct smbXsrv_session_global0
                          db_rec                   : NULL
                          session_global_id        : 0x021b776b (35354475)
                          session_wire_id          : 0x00000000021b776b (35354475)
                          creation_time            : Fri Mar 27 11:29:32 2015 GMT
                          expiration_time          : Thu Jan  1 01:00:00 1970 BST
                          auth_session_info_seqnum : 0x00000000 (0)
                          auth_session_info        : NULL
                          connection_dialect       : 0x0210 (528)
                          signing_required         : 0x00 (0)
                          encryption_required      : 0x00 (0)
                          num_channels             : 0x00000001 (1)
                          channels: ARRAY(1)
                              channels: struct smbXsrv_channel_global0
                                  server_id: struct server_id
                                      pid                      : 0x00000000000047a1 (18337)
                                      task_id                  : 0x00000000 (0)
                                      vnn                      : 0xffffffff (4294967295)
                                      unique_id                : 0x760e04c556881c25 (8506741991756274725)
                                  local_address            : 'ipv4:10.x.x.x:445'
                                  remote_address           : 'ipv4:10.x.x.x:50530'
                                  remote_name              : '10.x.x.x'
                                  auth_session_info_seqnum : 0x00000000 (0)
                  status                   : NT_STATUS_MORE_PROCESSING_REQUIRED
                  idle_time                : Fri Mar 27 11:29:32 2015 GMT
                  nonce_high               : 0x0000000000000000 (0)
                  nonce_low                : 0x0000000000000000 (0)
                  gensec                   : NULL
                  compat                   : NULL
                  tcon_table               : *
[2015/03/27 11:29:31.874235,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:464(make_auth_context_subsystem)
  Making default auth method list for server role = 'standalone server', encrypt passwords = yes
[2015/03/27 11:29:31.874269,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:351(load_auth_module)
  load_auth_module: Attempting to find an auth method to match guest
[2015/03/27 11:29:31.874300,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:376(load_auth_module)
  load_auth_module: auth method guest has a valid init
[2015/03/27 11:29:31.874331,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:351(load_auth_module)
  load_auth_module: Attempting to find an auth method to match sam
[2015/03/27 11:29:31.874362,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:376(load_auth_module)
  load_auth_module: auth method sam has a valid init
[2015/03/27 11:29:31.874420,  5, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:649(gensec_start_mech)
  Starting GENSEC mechanism spnego
[2015/03/27 11:29:31.874459,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.874495,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.874526,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.874561,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.874592,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.874662,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
  smbd_smb2_request_pending_queue: req->current_idx = 1
      req->in.vector[0].iov_len = 0
      req->in.vector[1].iov_len = 0
      req->in.vector[2].iov_len = 64
      req->in.vector[3].iov_len = 24
      req->in.vector[4].iov_len = 74
      req->out.vector[0].iov_len = 4
      req->out.vector[1].iov_len = 0
      req->out.vector[2].iov_len = 64
      req->out.vector[3].iov_len = 8
      req->out.vector[4].iov_len = 0
[2015/03/27 11:29:31.874898,  5, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:649(gensec_start_mech)
  Starting GENSEC submechanism ntlmssp
[2015/03/27 11:29:31.874975,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/ntlmssp/ntlmssp_util.c:34(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0xe2088297
    NTLMSSP_NEGOTIATE_UNICODE
    NTLMSSP_NEGOTIATE_OEM
    NTLMSSP_REQUEST_TARGET
    NTLMSSP_NEGOTIATE_SIGN
    NTLMSSP_NEGOTIATE_LM_KEY
    NTLMSSP_NEGOTIATE_NTLM
    NTLMSSP_NEGOTIATE_ALWAYS_SIGN
    NTLMSSP_NEGOTIATE_NTLM2
    NTLMSSP_NEGOTIATE_VERSION
    NTLMSSP_NEGOTIATE_128
    NTLMSSP_NEGOTIATE_KEY_EXCH
    NTLMSSP_NEGOTIATE_56
[2015/03/27 11:29:31.875375,  1, pid=18337, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       negotiate: struct NEGOTIATE_MESSAGE
          Signature                : 'NTLMSSP'
          MessageType              : NtLmNegotiate (1)
          NegotiateFlags           : 0xe2088297 (3792208535)
                 1: NTLMSSP_NEGOTIATE_UNICODE
                 1: NTLMSSP_NEGOTIATE_OEM    
                 1: NTLMSSP_REQUEST_TARGET   
                 1: NTLMSSP_NEGOTIATE_SIGN   
                 0: NTLMSSP_NEGOTIATE_SEAL   
                 0: NTLMSSP_NEGOTIATE_DATAGRAM
                 1: NTLMSSP_NEGOTIATE_LM_KEY 
                 0: NTLMSSP_NEGOTIATE_NETWARE
                 1: NTLMSSP_NEGOTIATE_NTLM   
                 0: NTLMSSP_NEGOTIATE_NT_ONLY
                 0: NTLMSSP_ANONYMOUS        
                 0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
                 1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
                 0: NTLMSSP_TARGET_TYPE_DOMAIN
                 0: NTLMSSP_TARGET_TYPE_SERVER
                 0: NTLMSSP_TARGET_TYPE_SHARE
                 1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
                 0: NTLMSSP_NEGOTIATE_IDENTIFY
                 0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
                 0: NTLMSSP_NEGOTIATE_TARGET_INFO
                 1: NTLMSSP_NEGOTIATE_VERSION
                 1: NTLMSSP_NEGOTIATE_128    
                 1: NTLMSSP_NEGOTIATE_KEY_EXCH
                 1: NTLMSSP_NEGOTIATE_56     
          DomainNameLen            : 0x0000 (0)
          DomainNameMaxLen         : 0x0000 (0)
          DomainName               : NULL
          WorkstationLen           : 0x0000 (0)
          WorkstationMaxLen        : 0x0000 (0)
          Workstation              : NULL
          Version: struct ntlmssp_VERSION
              ProductMajorVersion      : NTLMSSP_WINDOWS_MAJOR_VERSION_6 (6)
              ProductMinorVersion      : NTLMSSP_WINDOWS_MINOR_VERSION_1 (1)
              ProductBuild             : 0x1db1 (7601)
              Reserved: ARRAY(3)
                  [0]                      : 0x00 (0)
                  [1]                      : 0x00 (0)
                  [2]                      : 0x00 (0)
              NTLMRevisionCurrent      : NTLMSSP_REVISION_W2K3 (15)
[2015/03/27 11:29:31.876045,  1, pid=18337, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       challenge: struct CHALLENGE_MESSAGE
          Signature                : 'NTLMSSP'
          MessageType              : NtLmChallenge (0x2)
          TargetNameLen            : 0x000a (10)
          TargetNameMaxLen         : 0x000a (10)
          TargetName               : *
              TargetName               : 'SMBSERVER'
          NegotiateFlags           : 0xe28a8215 (3800728085)
                 1: NTLMSSP_NEGOTIATE_UNICODE
                 0: NTLMSSP_NEGOTIATE_OEM    
                 1: NTLMSSP_REQUEST_TARGET   
                 1: NTLMSSP_NEGOTIATE_SIGN   
                 0: NTLMSSP_NEGOTIATE_SEAL   
                 0: NTLMSSP_NEGOTIATE_DATAGRAM
                 0: NTLMSSP_NEGOTIATE_LM_KEY 
                 0: NTLMSSP_NEGOTIATE_NETWARE
                 1: NTLMSSP_NEGOTIATE_NTLM   
                 0: NTLMSSP_NEGOTIATE_NT_ONLY
                 0: NTLMSSP_ANONYMOUS        
                 0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
                 1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
                 0: NTLMSSP_TARGET_TYPE_DOMAIN
                 1: NTLMSSP_TARGET_TYPE_SERVER
                 0: NTLMSSP_TARGET_TYPE_SHARE
                 1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
                 0: NTLMSSP_NEGOTIATE_IDENTIFY
                 0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
                 1: NTLMSSP_NEGOTIATE_TARGET_INFO
                 1: NTLMSSP_NEGOTIATE_VERSION
                 1: NTLMSSP_NEGOTIATE_128    
                 1: NTLMSSP_NEGOTIATE_KEY_EXCH
                 1: NTLMSSP_NEGOTIATE_56     
          ServerChallenge          : c31b4e4f3fd7dedb
          Reserved                 : 0000000000000000
          TargetInfoLen            : 0x0040 (64)
          TargetNameInfoMaxLen     : 0x0040 (64)
          TargetInfo               : *
              TargetInfo: struct AV_PAIR_LIST
                  count                    : 0x00000005 (5)
                  pair: ARRAY(5)
                      pair: struct AV_PAIR
                          AvId                     : MsvAvNbDomainName (0x2)
                          AvLen                    : 0x000a (10)
                          Value                    : union ntlmssp_AvValue(case 0x2)
                          AvNbDomainName           : 'SMBSERVER'
                      pair: struct AV_PAIR
                          AvId                     : MsvAvNbComputerName (0x1)
                          AvLen                    : 0x000a (10)
                          Value                    : union ntlmssp_AvValue(case 0x1)
                          AvNbComputerName         : 'SMBSERVER'
                      pair: struct AV_PAIR
                          AvId                     : MsvAvDnsDomainName (0x4)
                          AvLen                    : 0x0006 (6)
                          Value                    : union ntlmssp_AvValue(case 0x4)
                          AvDnsDomainName          : 'domain'
                      pair: struct AV_PAIR
                          AvId                     : MsvAvDnsComputerName (0x3)
                          AvLen                    : 0x0012 (18)
                          Value                    : union ntlmssp_AvValue(case 0x3)
                          AvDnsComputerName        : 'samba.server.domain'
                      pair: struct AV_PAIR
                          AvId                     : MsvAvEOL (0x0)
                          AvLen                    : 0x0000 (0)
                          Value                    : union ntlmssp_AvValue(case 0x0)
          Version: struct ntlmssp_VERSION
              ProductMajorVersion      : NTLMSSP_WINDOWS_MAJOR_VERSION_6 (0x6)
              ProductMinorVersion      : NTLMSSP_WINDOWS_MINOR_VERSION_1 (0x1)
              ProductBuild             : 0x0000 (0)
              Reserved                 : 000000
              NTLMRevisionCurrent      : NTLMSSP_REVISION_W2K3 (0xF)
[2015/03/27 11:29:31.877033,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.877070,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.877101,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.877131,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.877160,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.877225,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.877261, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2499(smbd_smb2_request_done_ex)
  smbd_smb2_request_done_ex: idx[1] status[NT_STATUS_MORE_PROCESSING_REQUIRED] body[8] dyn[yes:161] at ../source3/smbd/smb2_sesssetup.c:167
[2015/03/27 11:29:31.877295, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:874(smb2_set_operation_credit)
  smb2_set_operation_credit: requested 31, charge 1, granted 1, current possible/max 512/512, total granted/max/low/range 1/8192/2/1
[2015/03/27 11:29:31.879610, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:3241(smbd_smb2_io_handler)
  smbd_smb2_request idx[1] of 5 vectors
[2015/03/27 11:29:31.879668, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:621(smb2_validate_sequence_number)
  smb2_validate_sequence_number: clearing id 2 (position 2) from bitmap
[2015/03/27 11:29:31.879702, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:1878(smbd_smb2_request_dispatch)
  smbd_smb2_request_dispatch: opcode[SMB2_OP_SESSSETUP] mid = 2
[2015/03/27 11:29:31.879740,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.879773,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.879803,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.879854,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.879893,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.879925,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.879955,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.879984,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.880014,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.880070,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
  smbd_smb2_request_pending_queue: req->current_idx = 1
      req->in.vector[0].iov_len = 0
      req->in.vector[1].iov_len = 0
      req->in.vector[2].iov_len = 64
      req->in.vector[3].iov_len = 24
      req->in.vector[4].iov_len = 198
      req->out.vector[0].iov_len = 4
      req->out.vector[1].iov_len = 0
      req->out.vector[2].iov_len = 64
      req->out.vector[3].iov_len = 8
      req->out.vector[4].iov_len = 0
[2015/03/27 11:29:31.880274,  1, pid=18337, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       authenticate: struct AUTHENTICATE_MESSAGE
          Signature                : 'NTLMSSP'
          MessageType              : NtLmAuthenticate (3)
          LmChallengeResponseLen   : 0x0018 (24)
          LmChallengeResponseMaxLen: 0x0018 (24)
          LmChallengeResponse      : *
              LmChallengeResponse      : union ntlmssp_LM_RESPONSE(case 24)
              v1: struct LM_RESPONSE
                  Response                 : e81fd5fb0d5cbd3200000000000000000000000000000000
          NtChallengeResponseLen   : 0x0018 (24)
          NtChallengeResponseMaxLen: 0x0018 (24)
          NtChallengeResponse      : *
              NtChallengeResponse      : union ntlmssp_NTLM_RESPONSE(case 24)
              v1: struct NTLM_RESPONSE
                  Response                 : 94d3f25e4c204011b8dd2456a182671c7516cae624c28954
          DomainNameLen            : 0x0000 (0)
          DomainNameMaxLen         : 0x0000 (0)
          DomainName               : *
              DomainName               : ''
          UserNameLen              : 0x0014 (20)
          UserNameMaxLen           : 0x0014 (20)
          UserName                 : *
              UserName                 : 'username@REALM'
          WorkstationLen           : 0x000e (14)
          WorkstationMaxLen        : 0x000e (14)
          Workstation              : *
              Workstation              : 'WIN7CLIENT'
          EncryptedRandomSessionKeyLen: 0x0010 (16)
          EncryptedRandomSessionKeyMaxLen: 0x0010 (16)
          EncryptedRandomSessionKey: *
              EncryptedRandomSessionKey: DATA_BLOB length=16
  [0000] BC 5B 19 96 82 19 AF 61   73 49 C6 E7 1B 50 84 BE   .[.....a sI...P..
          NegotiateFlags           : 0xe2888215 (3800597013)
                 1: NTLMSSP_NEGOTIATE_UNICODE
                 0: NTLMSSP_NEGOTIATE_OEM    
                 1: NTLMSSP_REQUEST_TARGET   
                 1: NTLMSSP_NEGOTIATE_SIGN   
                 0: NTLMSSP_NEGOTIATE_SEAL   
                 0: NTLMSSP_NEGOTIATE_DATAGRAM
                 0: NTLMSSP_NEGOTIATE_LM_KEY 
                 0: NTLMSSP_NEGOTIATE_NETWARE
                 1: NTLMSSP_NEGOTIATE_NTLM   
                 0: NTLMSSP_NEGOTIATE_NT_ONLY
                 0: NTLMSSP_ANONYMOUS        
                 0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
                 1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
                 0: NTLMSSP_TARGET_TYPE_DOMAIN
                 0: NTLMSSP_TARGET_TYPE_SERVER
                 0: NTLMSSP_TARGET_TYPE_SHARE
                 1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
                 0: NTLMSSP_NEGOTIATE_IDENTIFY
                 0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
                 1: NTLMSSP_NEGOTIATE_TARGET_INFO
                 1: NTLMSSP_NEGOTIATE_VERSION
                 1: NTLMSSP_NEGOTIATE_128    
                 1: NTLMSSP_NEGOTIATE_KEY_EXCH
                 1: NTLMSSP_NEGOTIATE_56     
          Version: struct ntlmssp_VERSION
              ProductMajorVersion      : NTLMSSP_WINDOWS_MAJOR_VERSION_6 (6)
              ProductMinorVersion      : NTLMSSP_WINDOWS_MINOR_VERSION_1 (1)
              ProductBuild             : 0x1db1 (7601)
              Reserved: ARRAY(3)
                  [0]                      : 0x00 (0)
                  [1]                      : 0x00 (0)
                  [2]                      : 0x00 (0)
              NTLMRevisionCurrent      : NTLMSSP_REVISION_W2K3 (15)
[2015/03/27 11:29:31.881191,  3, pid=18337, effective(0, 0), real(0, 0)] ../auth/ntlmssp/ntlmssp_server.c:358(ntlmssp_server_preauth)
  Got user=[username@REALM] domain=[] workstation=[WIN7CLIENT] len1=24 len2=24
[2015/03/27 11:29:31.881242,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/auth_ntlmssp.c:83(auth3_set_challenge)
  auth_context challenge set by NTLMSSP callback (NTLM2)
[2015/03/27 11:29:31.881279,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/auth_ntlmssp.c:84(auth3_set_challenge)
  challenge is: 
[2015/03/27 11:29:31.881321,  5, pid=18337, effective(0, 0), real(0, 0)] ../lib/util/util.c:556(dump_data)
  [0000] 64 93 46 BB 9A 4A D0 95                            d.F..J.. 
[2015/03/27 11:29:31.881427,  3, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:4838(lp_load_ex)
  lp_load_ex: refreshing parameters
[2015/03/27 11:29:31.881500,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:1487(free_param_opts)
  Freeing parametrics:
[2015/03/27 11:29:31.881613,  3, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:750(init_globals)
  Initialising global parameters
[2015/03/27 11:29:31.881790,  3, pid=18337, effective(0, 0), real(0, 0)] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2015/03/27 11:29:31.881869,  3, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:3564(do_section)
  Processing section "[global]"
  doing parameter workgroup = REALM
  doing parameter realm = REALM
  doing parameter netbios name = SMBSERVER
  doing parameter server string = Samba server
  doing parameter server role = standalone
  doing parameter server services = smb
  doing parameter hosts allow = 10.
  doing parameter dns proxy = no
  doing parameter dns forwarder = 10.x.x.x
  doing parameter interfaces = lo, em1
  doing parameter bind interfaces only = yes
  doing parameter syslog = 0
  doing parameter log file = /var/log/samba/log.%m
  doing parameter panic action = /usr/share/samba/panic-action %d
  doing parameter log level = 10
[2015/03/27 11:29:31.882458,  5, pid=18337, effective(0, 0), real(0, 0)] ../lib/util/debug.c:334(debug_dump_status)
  INFO: Current debug levels:
    all: 10
    tdb: 10
    printdrivers: 10
    lanman: 10
    smb: 10
    rpc_parse: 10
    rpc_srv: 10
    rpc_cli: 10
    passdb: 10
    sam: 10
    auth: 10
    winbind: 10
    vfs: 10
    idmap: 10
    quota: 10
    acls: 10
    locking: 10
    msdfs: 10
    dmapi: 10
    registry: 10
    scavenger: 10
    dns: 10
    ldb: 10
  doing parameter max log size = 1024
  doing parameter kerberos method = dedicated keytab
  doing parameter dedicated keytab file = /var/lib/samba/samba.keytab
  doing parameter load printers = no
  doing parameter printing = bsd
  doing parameter printcap name = /dev/null
  doing parameter disable spoolss = yes
  doing parameter cups options = raw
  doing parameter socket options = TCP_NODELAY
  doing parameter level2 oplocks = no
  doing parameter oplocks = no
[2015/03/27 11:29:31.883452,  2, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[share]"
  doing parameter comment = Shared files.
  doing parameter path = /path/to/share
  doing parameter public = yes
  doing parameter writable = yes
  doing parameter printable = no
  doing parameter write list = @filesrw
  doing parameter create mask = 0740
  doing parameter directory mask = 0750
  doing parameter force group = filesro
[2015/03/27 11:29:31.885678,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:4877(lp_load_ex)
  pm_process() returned Yes
[2015/03/27 11:29:31.885704,  7, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:5167(lp_servicenumber)
  lp_servicenumber: couldn't find homes
[2015/03/27 11:29:31.885725,  3, pid=18337, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:1773(lp_add_ipc)
  adding IPC service
[2015/03/27 11:29:31.885753,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_util.c:115(make_user_info_map)
  Mapping user []\[username@REALM] from workstation [WIN7CLIENT]
[2015/03/27 11:29:31.885787,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_util.c:137(make_user_info_map)
  Mapped domain from [] to [SMBSERVER] for user [username@REALM] from workstation [WIN7CLIENT]
[2015/03/27 11:29:31.885807,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/user_info.c:61(make_user_info)
  attempting to make a user_info for username@REALM (username@REALM)
[2015/03/27 11:29:31.885828,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/user_info.c:72(make_user_info)
  making strings for username@REALM's user_info struct
[2015/03/27 11:29:31.885848,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/user_info.c:92(make_user_info)
  making blobs for username@REALM's user_info struct
[2015/03/27 11:29:31.885871, 10, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/user_info.c:128(make_user_info)
  made a user_info for username@REALM (username@REALM)
[2015/03/27 11:29:31.885890,  3, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:177(auth_check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user []\[username@REALM]@[WIN7CLIENT] with the new password interface
[2015/03/27 11:29:31.885909,  3, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:180(auth_check_ntlm_password)
  check_ntlm_password:  mapped user is: [SMBSERVER]\[username@REALM]@[WIN7CLIENT]
[2015/03/27 11:29:31.885927, 10, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:189(auth_check_ntlm_password)
  check_ntlm_password: auth_context challenge created by NTLMSSP callback (NTLM2)
[2015/03/27 11:29:31.885945, 10, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:191(auth_check_ntlm_password)
  challenge is: 
[2015/03/27 11:29:31.885963,  5, pid=18337, effective(0, 0), real(0, 0)] ../lib/util/util.c:556(dump_data)
  [0000] 64 93 46 BB 9A 4A D0 95                            d.F..J.. 
[2015/03/27 11:29:31.885989, 10, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_builtin.c:44(check_guest_security)
  Check auth for: [username@REALM]
[2015/03/27 11:29:31.886008, 10, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:217(auth_check_ntlm_password)
  check_ntlm_password: guest had nothing to say
[2015/03/27 11:29:31.886027, 10, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_sam.c:75(auth_samstrict_auth)
  Check auth for: [username@REALM]
[2015/03/27 11:29:31.886046,  8, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/util.c:1191(is_myname)
  is_myname("SMBSERVER") returns 1
[2015/03/27 11:29:31.886068,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.886087,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.886106,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.886124,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.886142,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.886188,  5, pid=18337, effective(0, 0), real(0, 0), class=passdb] ../source3/passdb/pdb_tdb.c:594(tdbsam_getsampwnam)
  pdb_getsampwnam (TDB): error fetching database.
   Key: USER_username@realm
[2015/03/27 11:29:31.886221,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.886242,  3, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/check_samsec.c:399(check_sam_security)
  check_sam_security: Couldn't find user 'username@REALM' in passdb.
[2015/03/27 11:29:31.886262,  5, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:229(auth_check_ntlm_password)
  check_ntlm_password: sam authentication for user [username@REALM] FAILED with error NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.886284,  2, pid=18337, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:288(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [username@REALM] -> [username@REALM] FAILED with error NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.886303,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/auth_ntlmssp.c:144(auth3_check_password)
  Checking NTLMSSP password for \username@REALM failed: NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.886324,  5, pid=18337, effective(0, 0), real(0, 0)] ../auth/ntlmssp/ntlmssp_server.c:454(ntlmssp_server_check_password)
  ../auth/ntlmssp/ntlmssp_server.c:454: Checking NTLMSSP password for \username@REALM failed: NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.886348,  2, pid=18337, effective(0, 0), real(0, 0)] ../auth/gensec/spnego.c:743(gensec_spnego_server_negTokenTarg)
  SPNEGO login failed: NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.886370,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.886390,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.886408,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.886426,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.886444,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.886478,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.886498,  5, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:187(dbwrap_check_lock_order)
  check lock order 1 for /var/run/samba/smbXsrv_session_global.tdb
[2015/03/27 11:29:31.886517, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:133(debug_lock_order)
  lock order:  1:/var/run/samba/smbXsrv_session_global.tdb 2:<none> 3:<none>
[2015/03/27 11:29:31.886537, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:59(db_tdb_log_key)
  Locking key 021B776B
[2015/03/27 11:29:31.886558, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:143(db_tdb_fetch_locked_internal)
  Allocated locked data 0x0x7f8c7a4f5110
[2015/03/27 11:29:31.886588, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:59(db_tdb_log_key)
  Unlocking key 021B776B
[2015/03/27 11:29:31.886609,  5, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:146(dbwrap_lock_order_state_destructor)
  release lock order 1 for /var/run/samba/smbXsrv_session_global.tdb
[2015/03/27 11:29:31.886627, 10, pid=18337, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:133(debug_lock_order)
  lock order:  1:<none> 2:<none> 3:<none>
[2015/03/27 11:29:31.886655, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2598(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_LOGON_FAILURE] || at ../source3/smbd/smb2_sesssetup.c:130
[2015/03/27 11:29:31.886678, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2499(smbd_smb2_request_done_ex)
  smbd_smb2_request_done_ex: idx[1] status[NT_STATUS_LOGON_FAILURE] body[8] dyn[yes:1] at ../source3/smbd/smb2_server.c:2651
[2015/03/27 11:29:31.886698, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:874(smb2_set_operation_credit)
  smb2_set_operation_credit: requested 31, charge 1, granted 1, current possible/max 512/512, total granted/max/low/range 1/8192/3/1
[2015/03/27 11:29:31.890159, 10, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:1002(smbd_server_connection_terminate_ex)
  smbd_server_connection_terminate_ex: reason[NT_STATUS_CONNECTION_RESET] at ../source3/smbd/smb2_server.c:3293
[2015/03/27 11:29:31.890202,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.890223,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.890242,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.890278,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.890301,  4, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.890320,  5, pid=18337, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.890338,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.890367,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.890390,  5, pid=18337, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:340(messaging_deregister)
  Deregistering messaging pointer for type 1536 - private_data=0x7f8c7a4eed80
[2015/03/27 11:29:31.890436,  3, pid=18337, effective(0, 0), real(0, 0)] ../source3/smbd/server_exit.c:212(exit_server_common)
  Server exit (NT_STATUS_CONNECTION_RESET)
[2015/03/27 11:29:31.895446,  6, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:2657(lp_file_list_changed)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Fri Mar 27 11:27:05 2015
  
[2015/03/27 11:29:31.895618,  3, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/access.c:338(allow_access)
  Allowed connection from 10.x.x.x (10.x.x.x)
[2015/03/27 11:29:31.895661, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/process.c:3475(smbd_process)
  Connection allowed from ipv4:10.x.x.x:50531 to ipv4:10.x.x.x:445
[2015/03/27 11:29:31.895827,  3, pid=18338, effective(0, 0), real(0, 0), class=locking] ../source3/smbd/oplock.c:870(init_oplocks)
  init_oplocks: initializing messages.
[2015/03/27 11:29:31.895870,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 774 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.895908,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 776 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.895944,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 778 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.895981,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 770 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.896019,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 787 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.896055,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 779 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.896096,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 15 - private_data=(nil)
[2015/03/27 11:29:31.896134,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:308(messaging_register)
  Overriding messaging pointer for type 15 - private_data=(nil)
[2015/03/27 11:29:31.896173,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:340(messaging_deregister)
  Deregistering messaging pointer for type 16 - private_data=(nil)
[2015/03/27 11:29:31.896211,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 16 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.896256,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:340(messaging_deregister)
  Deregistering messaging pointer for type 33 - private_data=0x7f8c7a4d63c0
[2015/03/27 11:29:31.896294,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 33 - private_data=0x7f8c7a4e5a80
[2015/03/27 11:29:31.896331,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:340(messaging_deregister)
  Deregistering messaging pointer for type 1 - private_data=(nil)
[2015/03/27 11:29:31.896368,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 1 - private_data=(nil)
[2015/03/27 11:29:31.896418, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/events.c:483(event_add_idle)
  event_add_idle: idle_evt(keepalive) 0x7f8c7a4e6d70
[2015/03/27 11:29:31.896461, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/events.c:483(event_add_idle)
  event_add_idle: idle_evt(deadtime) 0x7f8c7a4e6fc0
[2015/03/27 11:29:31.896501, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/events.c:483(event_add_idle)
  event_add_idle: idle_evt(housekeeping) 0x7f8c7a4ea340
[2015/03/27 11:29:31.896612, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/util_sock.c:337(read_smb_length_return_keepalive)
  got smb length of 104
[2015/03/27 11:29:31.896672,  6, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/process.c:1793(process_smb)
  got message type 0x0 of len 0x68
[2015/03/27 11:29:31.896713,  3, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/process.c:1795(process_smb)
  Transaction 0 of length 108 (0 toread)
[2015/03/27 11:29:31.896754, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2885(smbd_smb2_first_negprot)
  smbd_smb2_first_negprot: packet length 108
[2015/03/27 11:29:31.896808, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:621(smb2_validate_sequence_number)
  smb2_validate_sequence_number: clearing id 0 (position 0) from bitmap
[2015/03/27 11:29:31.896855, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:1878(smbd_smb2_request_dispatch)
  smbd_smb2_request_dispatch: opcode[SMB2_OP_NEGPROT] mid = 0
[2015/03/27 11:29:31.896902,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.896946,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.896990,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.897057,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.897153, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/util.c:1277(set_remote_arch)
  set_remote_arch: Client arch is 'Vista'
[2015/03/27 11:29:31.897216,  6, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:2657(lp_file_list_changed)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Fri Mar 27 11:27:05 2015
  
[2015/03/27 11:29:31.897292,  3, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_negprot.c:243(smbd_smb2_request_process_negprot)
  Selected protocol SMB2_10
[2015/03/27 11:29:31.897392,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:464(make_auth_context_subsystem)
  Making default auth method list for server role = 'standalone server', encrypt passwords = yes
[2015/03/27 11:29:31.897450,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend sam
[2015/03/27 11:29:31.897490,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'sam'
[2015/03/27 11:29:31.897534,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend sam_ignoredomain
[2015/03/27 11:29:31.897578,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'sam_ignoredomain'
[2015/03/27 11:29:31.897616,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend unix
[2015/03/27 11:29:31.897652,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'unix'
[2015/03/27 11:29:31.897690,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend winbind
[2015/03/27 11:29:31.897729,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'winbind'
[2015/03/27 11:29:31.897765,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend wbc
[2015/03/27 11:29:31.897801,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'wbc'
[2015/03/27 11:29:31.897837,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend trustdomain
[2015/03/27 11:29:31.897874,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'trustdomain'
[2015/03/27 11:29:31.897910,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend ntdomain
[2015/03/27 11:29:31.897946,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'ntdomain'
[2015/03/27 11:29:31.897982,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:48(smb_register_auth)
  Attempting to register auth backend guest
[2015/03/27 11:29:31.898018,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:60(smb_register_auth)
  Successfully added auth method 'guest'
[2015/03/27 11:29:31.898054,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:351(load_auth_module)
  load_auth_module: Attempting to find an auth method to match guest
[2015/03/27 11:29:31.898095,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:376(load_auth_module)
  load_auth_module: auth method guest has a valid init
[2015/03/27 11:29:31.898134,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:351(load_auth_module)
  load_auth_module: Attempting to find an auth method to match sam
[2015/03/27 11:29:31.898172,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:376(load_auth_module)
  load_auth_module: auth method sam has a valid init
[2015/03/27 11:29:31.900157,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_spnego' registered
[2015/03/27 11:29:31.900228,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_krb5' registered
[2015/03/27 11:29:31.900269,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_krb5_sasl' registered
[2015/03/27 11:29:31.900312,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'schannel' registered
[2015/03/27 11:29:31.900352,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'spnego' registered
[2015/03/27 11:29:31.900400,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'ntlmssp' registered
[2015/03/27 11:29:31.900442,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'krb5' registered
[2015/03/27 11:29:31.900479,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'fake_gssapi_krb5' registered
[2015/03/27 11:29:31.900628,  5, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:649(gensec_start_mech)
  Starting GENSEC mechanism spnego
[2015/03/27 11:29:31.900700,  5, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:649(gensec_start_mech)
  Starting GENSEC submechanism gse_krb5
[2015/03/27 11:29:31.901802, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/krb5_wrap/krb5_samba.c:1266(smb_krb5_open_keytab)
  smb_krb5_open_keytab: resolving: FILE:/var/lib/samba/samba.keytab
[2015/03/27 11:29:31.902550,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:293(messaging_register)
  Registering messaging pointer for type 1536 - private_data=0x7f8c7a4eed80
[2015/03/27 11:29:31.902627, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2499(smbd_smb2_request_done_ex)
  smbd_smb2_request_done_ex: idx[1] status[NT_STATUS_OK] body[64] dyn[yes:96] at ../source3/smbd/smb2_negprot.c:387
[2015/03/27 11:29:31.902682, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:874(smb2_set_operation_credit)
  smb2_set_operation_credit: requested 31, charge 1, granted 1, current possible/max 512/512, total granted/max/low/range 1/8192/1/1
[2015/03/27 11:29:31.905100, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:3241(smbd_smb2_io_handler)
  smbd_smb2_request idx[1] of 5 vectors
[2015/03/27 11:29:31.905171, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:621(smb2_validate_sequence_number)
  smb2_validate_sequence_number: clearing id 1 (position 1) from bitmap
[2015/03/27 11:29:31.905212, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:1878(smbd_smb2_request_dispatch)
  smbd_smb2_request_dispatch: opcode[SMB2_OP_SESSSETUP] mid = 1
[2015/03/27 11:29:31.905251,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.905290,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.905409,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.905502,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.905582,  5, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:187(dbwrap_check_lock_order)
  check lock order 1 for /var/run/samba/smbXsrv_session_global.tdb
[2015/03/27 11:29:31.905637, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:133(debug_lock_order)
  lock order:  1:/var/run/samba/smbXsrv_session_global.tdb 2:<none> 3:<none>
[2015/03/27 11:29:31.905695, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:59(db_tdb_log_key)
  Locking key E400ED96
[2015/03/27 11:29:31.905759, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:143(db_tdb_fetch_locked_internal)
  Allocated locked data 0x0x7f8c7a4ebd50
[2015/03/27 11:29:31.906093, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smbXsrv_session.c:853(smbXsrv_session_global_store)
[2015/03/27 11:29:31.906146, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smbXsrv_session.c:855(smbXsrv_session_global_store)
  smbXsrv_session_global_store: key 'E400ED96' stored
[2015/03/27 11:29:31.906218,  1, pid=18338, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       &global_blob: struct smbXsrv_session_globalB
          version                  : SMBXSRV_VERSION_0 (0)
          seqnum                   : 0x00000001 (1)
          info                     : union smbXsrv_session_globalU(case 0)
          info0                    : *
              info0: struct smbXsrv_session_global0
                  db_rec                   : *
                  session_global_id        : 0xe400ed96 (3825266070)
                  session_wire_id          : 0x00000000e400ed96 (3825266070)
                  creation_time            : Fri Mar 27 11:29:32 2015 GMT
                  expiration_time          : Thu Jan  1 01:00:00 1970 BST
                  auth_session_info_seqnum : 0x00000000 (0)
                  auth_session_info        : NULL
                  connection_dialect       : 0x0210 (528)
                  signing_required         : 0x00 (0)
                  encryption_required      : 0x00 (0)
                  num_channels             : 0x00000001 (1)
                  channels: ARRAY(1)
                      channels: struct smbXsrv_channel_global0
                          server_id: struct server_id
                              pid                      : 0x00000000000047a2 (18338)
                              task_id                  : 0x00000000 (0)
                              vnn                      : 0xffffffff (4294967295)
                              unique_id                : 0x14d989cceaaf0d94 (1502383463908445588)
                          local_address            : 'ipv4:10.x.x.x:445'
                          remote_address           : 'ipv4:10.x.x.x:50531'
                          remote_name              : '10.x.x.x'
                          auth_session_info_seqnum : 0x00000000 (0)
[2015/03/27 11:29:31.906965, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:59(db_tdb_log_key)
  Unlocking key E400ED96
[2015/03/27 11:29:31.907023,  5, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:146(dbwrap_lock_order_state_destructor)
  release lock order 1 for /var/run/samba/smbXsrv_session_global.tdb
[2015/03/27 11:29:31.907075, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:133(debug_lock_order)
  lock order:  1:<none> 2:<none> 3:<none>
[2015/03/27 11:29:31.907130, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smbXsrv_session.c:1215(smbXsrv_session_create)
[2015/03/27 11:29:31.907164, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smbXsrv_session.c:1223(smbXsrv_session_create)
  smbXsrv_session_create: global_id (0xe400ed96) stored
[2015/03/27 11:29:31.907215,  1, pid=18338, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       &session_blob: struct smbXsrv_sessionB
          version                  : SMBXSRV_VERSION_0 (0)
          reserved                 : 0x00000000 (0)
          info                     : union smbXsrv_sessionU(case 0)
          info0                    : *
              info0: struct smbXsrv_session
                  table                    : *
                  db_rec                   : NULL
                  connection               : *
                  local_id                 : 0xe400ed96 (3825266070)
                  global                   : *
                      global: struct smbXsrv_session_global0
                          db_rec                   : NULL
                          session_global_id        : 0xe400ed96 (3825266070)
                          session_wire_id          : 0x00000000e400ed96 (3825266070)
                          creation_time            : Fri Mar 27 11:29:32 2015 GMT
                          expiration_time          : Thu Jan  1 01:00:00 1970 BST
                          auth_session_info_seqnum : 0x00000000 (0)
                          auth_session_info        : NULL
                          connection_dialect       : 0x0210 (528)
                          signing_required         : 0x00 (0)
                          encryption_required      : 0x00 (0)
                          num_channels             : 0x00000001 (1)
                          channels: ARRAY(1)
                              channels: struct smbXsrv_channel_global0
                                  server_id: struct server_id
                                      pid                      : 0x00000000000047a2 (18338)
                                      task_id                  : 0x00000000 (0)
                                      vnn                      : 0xffffffff (4294967295)
                                      unique_id                : 0x14d989cceaaf0d94 (1502383463908445588)
                                  local_address            : 'ipv4:10.x.x.x:445'
                                  remote_address           : 'ipv4:10.x.x.x:50531'
                                  remote_name              : '10.x.x.x'
                                  auth_session_info_seqnum : 0x00000000 (0)
                  status                   : NT_STATUS_MORE_PROCESSING_REQUIRED
                  idle_time                : Fri Mar 27 11:29:32 2015 GMT
                  nonce_high               : 0x0000000000000000 (0)
                  nonce_low                : 0x0000000000000000 (0)
                  gensec                   : NULL
                  compat                   : NULL
                  tcon_table               : *
[2015/03/27 11:29:31.908215,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:464(make_auth_context_subsystem)
  Making default auth method list for server role = 'standalone server', encrypt passwords = yes
[2015/03/27 11:29:31.908275,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:351(load_auth_module)
  load_auth_module: Attempting to find an auth method to match guest
[2015/03/27 11:29:31.908328,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:376(load_auth_module)
  load_auth_module: auth method guest has a valid init
[2015/03/27 11:29:31.908379,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:351(load_auth_module)
  load_auth_module: Attempting to find an auth method to match sam
[2015/03/27 11:29:31.908431,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:376(load_auth_module)
  load_auth_module: auth method sam has a valid init
[2015/03/27 11:29:31.908530,  5, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:649(gensec_start_mech)
  Starting GENSEC mechanism spnego
[2015/03/27 11:29:31.908597,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.908658,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.908711,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.908763,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.908815,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.908933,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
  smbd_smb2_request_pending_queue: req->current_idx = 1
      req->in.vector[0].iov_len = 0
      req->in.vector[1].iov_len = 0
      req->in.vector[2].iov_len = 64
      req->in.vector[3].iov_len = 24
      req->in.vector[4].iov_len = 74
      req->out.vector[0].iov_len = 4
      req->out.vector[1].iov_len = 0
      req->out.vector[2].iov_len = 64
      req->out.vector[3].iov_len = 8
      req->out.vector[4].iov_len = 0
[2015/03/27 11:29:31.909368,  5, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/gensec_start.c:649(gensec_start_mech)
  Starting GENSEC submechanism ntlmssp
[2015/03/27 11:29:31.909519,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/ntlmssp/ntlmssp_util.c:34(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0xe2088297
    NTLMSSP_NEGOTIATE_UNICODE
    NTLMSSP_NEGOTIATE_OEM
    NTLMSSP_REQUEST_TARGET
    NTLMSSP_NEGOTIATE_SIGN
    NTLMSSP_NEGOTIATE_LM_KEY
    NTLMSSP_NEGOTIATE_NTLM
    NTLMSSP_NEGOTIATE_ALWAYS_SIGN
    NTLMSSP_NEGOTIATE_NTLM2
    NTLMSSP_NEGOTIATE_VERSION
    NTLMSSP_NEGOTIATE_128
    NTLMSSP_NEGOTIATE_KEY_EXCH
    NTLMSSP_NEGOTIATE_56
[2015/03/27 11:29:31.910195,  1, pid=18338, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       negotiate: struct NEGOTIATE_MESSAGE
          Signature                : 'NTLMSSP'
          MessageType              : NtLmNegotiate (1)
          NegotiateFlags           : 0xe2088297 (3792208535)
                 1: NTLMSSP_NEGOTIATE_UNICODE
                 1: NTLMSSP_NEGOTIATE_OEM    
                 1: NTLMSSP_REQUEST_TARGET   
                 1: NTLMSSP_NEGOTIATE_SIGN   
                 0: NTLMSSP_NEGOTIATE_SEAL   
                 0: NTLMSSP_NEGOTIATE_DATAGRAM
                 1: NTLMSSP_NEGOTIATE_LM_KEY 
                 0: NTLMSSP_NEGOTIATE_NETWARE
                 1: NTLMSSP_NEGOTIATE_NTLM   
                 0: NTLMSSP_NEGOTIATE_NT_ONLY
                 0: NTLMSSP_ANONYMOUS        
                 0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
                 1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
                 0: NTLMSSP_TARGET_TYPE_DOMAIN
                 0: NTLMSSP_TARGET_TYPE_SERVER
                 0: NTLMSSP_TARGET_TYPE_SHARE
                 1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
                 0: NTLMSSP_NEGOTIATE_IDENTIFY
                 0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
                 0: NTLMSSP_NEGOTIATE_TARGET_INFO
                 1: NTLMSSP_NEGOTIATE_VERSION
                 1: NTLMSSP_NEGOTIATE_128    
                 1: NTLMSSP_NEGOTIATE_KEY_EXCH
                 1: NTLMSSP_NEGOTIATE_56     
          DomainNameLen            : 0x0000 (0)
          DomainNameMaxLen         : 0x0000 (0)
          DomainName               : NULL
          WorkstationLen           : 0x0000 (0)
          WorkstationMaxLen        : 0x0000 (0)
          Workstation              : NULL
          Version: struct ntlmssp_VERSION
              ProductMajorVersion      : NTLMSSP_WINDOWS_MAJOR_VERSION_6 (6)
              ProductMinorVersion      : NTLMSSP_WINDOWS_MINOR_VERSION_1 (1)
              ProductBuild             : 0x1db1 (7601)
              Reserved: ARRAY(3)
                  [0]                      : 0x00 (0)
                  [1]                      : 0x00 (0)
                  [2]                      : 0x00 (0)
              NTLMRevisionCurrent      : NTLMSSP_REVISION_W2K3 (15)
[2015/03/27 11:29:31.911338,  1, pid=18338, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       challenge: struct CHALLENGE_MESSAGE
          Signature                : 'NTLMSSP'
          MessageType              : NtLmChallenge (0x2)
          TargetNameLen            : 0x000a (10)
          TargetNameMaxLen         : 0x000a (10)
          TargetName               : *
              TargetName               : 'SMBSERVER'
          NegotiateFlags           : 0xe28a8215 (3800728085)
                 1: NTLMSSP_NEGOTIATE_UNICODE
                 0: NTLMSSP_NEGOTIATE_OEM    
                 1: NTLMSSP_REQUEST_TARGET   
                 1: NTLMSSP_NEGOTIATE_SIGN   
                 0: NTLMSSP_NEGOTIATE_SEAL   
                 0: NTLMSSP_NEGOTIATE_DATAGRAM
                 0: NTLMSSP_NEGOTIATE_LM_KEY 
                 0: NTLMSSP_NEGOTIATE_NETWARE
                 1: NTLMSSP_NEGOTIATE_NTLM   
                 0: NTLMSSP_NEGOTIATE_NT_ONLY
                 0: NTLMSSP_ANONYMOUS        
                 0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
                 1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
                 0: NTLMSSP_TARGET_TYPE_DOMAIN
                 1: NTLMSSP_TARGET_TYPE_SERVER
                 0: NTLMSSP_TARGET_TYPE_SHARE
                 1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
                 0: NTLMSSP_NEGOTIATE_IDENTIFY
                 0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
                 1: NTLMSSP_NEGOTIATE_TARGET_INFO
                 1: NTLMSSP_NEGOTIATE_VERSION
                 1: NTLMSSP_NEGOTIATE_128    
                 1: NTLMSSP_NEGOTIATE_KEY_EXCH
                 1: NTLMSSP_NEGOTIATE_56     
          ServerChallenge          : 78566508696c7707
          Reserved                 : 0000000000000000
          TargetInfoLen            : 0x0040 (64)
          TargetNameInfoMaxLen     : 0x0040 (64)
          TargetInfo               : *
              TargetInfo: struct AV_PAIR_LIST
                  count                    : 0x00000005 (5)
                  pair: ARRAY(5)
                      pair: struct AV_PAIR
                          AvId                     : MsvAvNbDomainName (0x2)
                          AvLen                    : 0x000a (10)
                          Value                    : union ntlmssp_AvValue(case 0x2)
                          AvNbDomainName           : 'SMBSERVER'
                      pair: struct AV_PAIR
                          AvId                     : MsvAvNbComputerName (0x1)
                          AvLen                    : 0x000a (10)
                          Value                    : union ntlmssp_AvValue(case 0x1)
                          AvNbComputerName         : 'SMBSERVER'
                      pair: struct AV_PAIR
                          AvId                     : MsvAvDnsDomainName (0x4)
                          AvLen                    : 0x0006 (6)
                          Value                    : union ntlmssp_AvValue(case 0x4)
                          AvDnsDomainName          : 'domain'
                      pair: struct AV_PAIR
                          AvId                     : MsvAvDnsComputerName (0x3)
                          AvLen                    : 0x0012 (18)
                          Value                    : union ntlmssp_AvValue(case 0x3)
                          AvDnsComputerName        : 'samba.server.domain'
                      pair: struct AV_PAIR
                          AvId                     : MsvAvEOL (0x0)
                          AvLen                    : 0x0000 (0)
                          Value                    : union ntlmssp_AvValue(case 0x0)
          Version: struct ntlmssp_VERSION
              ProductMajorVersion      : NTLMSSP_WINDOWS_MAJOR_VERSION_6 (0x6)
              ProductMinorVersion      : NTLMSSP_WINDOWS_MINOR_VERSION_1 (0x1)
              ProductBuild             : 0x0000 (0)
              Reserved                 : 000000
              NTLMRevisionCurrent      : NTLMSSP_REVISION_W2K3 (0xF)
[2015/03/27 11:29:31.913020,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.913082,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.913134,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.913185,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.913236,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.913384,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.913455, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2499(smbd_smb2_request_done_ex)
  smbd_smb2_request_done_ex: idx[1] status[NT_STATUS_MORE_PROCESSING_REQUIRED] body[8] dyn[yes:161] at ../source3/smbd/smb2_sesssetup.c:167
[2015/03/27 11:29:31.913524, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:874(smb2_set_operation_credit)
  smb2_set_operation_credit: requested 31, charge 1, granted 1, current possible/max 512/512, total granted/max/low/range 1/8192/2/1
[2015/03/27 11:29:31.915947, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:3241(smbd_smb2_io_handler)
  smbd_smb2_request idx[1] of 5 vectors
[2015/03/27 11:29:31.916046, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:621(smb2_validate_sequence_number)
  smb2_validate_sequence_number: clearing id 2 (position 2) from bitmap
[2015/03/27 11:29:31.916104, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:1878(smbd_smb2_request_dispatch)
  smbd_smb2_request_dispatch: opcode[SMB2_OP_SESSSETUP] mid = 2
[2015/03/27 11:29:31.916169,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.916226,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.916278,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.916365,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.916431,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.916486,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.916538,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.916589,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.916640,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.916735,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
  smbd_smb2_request_pending_queue: req->current_idx = 1
      req->in.vector[0].iov_len = 0
      req->in.vector[1].iov_len = 0
      req->in.vector[2].iov_len = 64
      req->in.vector[3].iov_len = 24
      req->in.vector[4].iov_len = 198
      req->out.vector[0].iov_len = 4
      req->out.vector[1].iov_len = 0
      req->out.vector[2].iov_len = 64
      req->out.vector[3].iov_len = 8
      req->out.vector[4].iov_len = 0
[2015/03/27 11:29:31.917068,  1, pid=18338, effective(0, 0), real(0, 0)] ../librpc/ndr/ndr.c:296(ndr_print_debug)
       authenticate: struct AUTHENTICATE_MESSAGE
          Signature                : 'NTLMSSP'
          MessageType              : NtLmAuthenticate (3)
          LmChallengeResponseLen   : 0x0018 (24)
          LmChallengeResponseMaxLen: 0x0018 (24)
          LmChallengeResponse      : *
              LmChallengeResponse      : union ntlmssp_LM_RESPONSE(case 24)
              v1: struct LM_RESPONSE
                  Response                 : 46452f124a6e231300000000000000000000000000000000
          NtChallengeResponseLen   : 0x0018 (24)
          NtChallengeResponseMaxLen: 0x0018 (24)
          NtChallengeResponse      : *
              NtChallengeResponse      : union ntlmssp_NTLM_RESPONSE(case 24)
              v1: struct NTLM_RESPONSE
                  Response                 : 97c07b2fab72580f22f588b0cfd3ebedea858c5a5e5983d8
          DomainNameLen            : 0x0000 (0)
          DomainNameMaxLen         : 0x0000 (0)
          DomainName               : *
              DomainName               : ''
          UserNameLen              : 0x0014 (20)
          UserNameMaxLen           : 0x0014 (20)
          UserName                 : *
              UserName                 : 'username@REALM'
          WorkstationLen           : 0x000e (14)
          WorkstationMaxLen        : 0x000e (14)
          Workstation              : *
              Workstation              : 'WIN7CLIENT'
          EncryptedRandomSessionKeyLen: 0x0010 (16)
          EncryptedRandomSessionKeyMaxLen: 0x0010 (16)
          EncryptedRandomSessionKey: *
              EncryptedRandomSessionKey: DATA_BLOB length=16
  [0000] 80 AF CB F8 C1 BB 80 BE   A7 14 62 46 2F 70 B6 22   ........ ..bF/p."
          NegotiateFlags           : 0xe2888215 (3800597013)
                 1: NTLMSSP_NEGOTIATE_UNICODE
                 0: NTLMSSP_NEGOTIATE_OEM    
                 1: NTLMSSP_REQUEST_TARGET   
                 1: NTLMSSP_NEGOTIATE_SIGN   
                 0: NTLMSSP_NEGOTIATE_SEAL   
                 0: NTLMSSP_NEGOTIATE_DATAGRAM
                 0: NTLMSSP_NEGOTIATE_LM_KEY 
                 0: NTLMSSP_NEGOTIATE_NETWARE
                 1: NTLMSSP_NEGOTIATE_NTLM   
                 0: NTLMSSP_NEGOTIATE_NT_ONLY
                 0: NTLMSSP_ANONYMOUS        
                 0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
                 0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
                 1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
                 0: NTLMSSP_TARGET_TYPE_DOMAIN
                 0: NTLMSSP_TARGET_TYPE_SERVER
                 0: NTLMSSP_TARGET_TYPE_SHARE
                 1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
                 0: NTLMSSP_NEGOTIATE_IDENTIFY
                 0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
                 1: NTLMSSP_NEGOTIATE_TARGET_INFO
                 1: NTLMSSP_NEGOTIATE_VERSION
                 1: NTLMSSP_NEGOTIATE_128    
                 1: NTLMSSP_NEGOTIATE_KEY_EXCH
                 1: NTLMSSP_NEGOTIATE_56     
          Version: struct ntlmssp_VERSION
              ProductMajorVersion      : NTLMSSP_WINDOWS_MAJOR_VERSION_6 (6)
              ProductMinorVersion      : NTLMSSP_WINDOWS_MINOR_VERSION_1 (1)
              ProductBuild             : 0x1db1 (7601)
              Reserved: ARRAY(3)
                  [0]                      : 0x00 (0)
                  [1]                      : 0x00 (0)
                  [2]                      : 0x00 (0)
              NTLMRevisionCurrent      : NTLMSSP_REVISION_W2K3 (15)
[2015/03/27 11:29:31.917834,  3, pid=18338, effective(0, 0), real(0, 0)] ../auth/ntlmssp/ntlmssp_server.c:358(ntlmssp_server_preauth)
  Got user=[username@REALM] domain=[] workstation=[WIN7CLIENT] len1=24 len2=24
[2015/03/27 11:29:31.917867,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/auth_ntlmssp.c:83(auth3_set_challenge)
  auth_context challenge set by NTLMSSP callback (NTLM2)
[2015/03/27 11:29:31.917887,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/auth_ntlmssp.c:84(auth3_set_challenge)
  challenge is: 
[2015/03/27 11:29:31.917906,  5, pid=18338, effective(0, 0), real(0, 0)] ../lib/util/util.c:556(dump_data)
  [0000] FD 55 92 FC AA 24 6E 7A                            .U...$nz 
[2015/03/27 11:29:31.917935,  3, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:4838(lp_load_ex)
  lp_load_ex: refreshing parameters
[2015/03/27 11:29:31.917956,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:1487(free_param_opts)
  Freeing parametrics:
[2015/03/27 11:29:31.917989,  3, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:750(init_globals)
  Initialising global parameters
[2015/03/27 11:29:31.918039,  3, pid=18338, effective(0, 0), real(0, 0)] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2015/03/27 11:29:31.918065,  3, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:3564(do_section)
  Processing section "[global]"
  doing parameter workgroup = REALM
  doing parameter realm = REALM
  doing parameter netbios name = SMBSERVER
  doing parameter server string = Samba server
  doing parameter server role = standalone
  doing parameter server services = smb
  doing parameter hosts allow = 10.
  doing parameter dns proxy = no
  doing parameter dns forwarder = 10.x.x.x
  doing parameter interfaces = lo, em1
  doing parameter bind interfaces only = yes
  doing parameter syslog = 0
  doing parameter log file = /var/log/samba/log.%m
  doing parameter panic action = /usr/share/samba/panic-action %d
  doing parameter log level = 10
[2015/03/27 11:29:31.918235,  5, pid=18338, effective(0, 0), real(0, 0)] ../lib/util/debug.c:334(debug_dump_status)
  INFO: Current debug levels:
    all: 10
    tdb: 10
    printdrivers: 10
    lanman: 10
    smb: 10
    rpc_parse: 10
    rpc_srv: 10
    rpc_cli: 10
    passdb: 10
    sam: 10
    auth: 10
    winbind: 10
    vfs: 10
    idmap: 10
    quota: 10
    acls: 10
    locking: 10
    msdfs: 10
    dmapi: 10
    registry: 10
    scavenger: 10
    dns: 10
    ldb: 10
  doing parameter max log size = 1024
  doing parameter kerberos method = dedicated keytab
  doing parameter dedicated keytab file = /var/lib/samba/samba.keytab
  doing parameter load printers = no
  doing parameter printing = bsd
  doing parameter printcap name = /dev/null
  doing parameter disable spoolss = yes
  doing parameter cups options = raw
  doing parameter socket options = TCP_NODELAY
  doing parameter level2 oplocks = no
  doing parameter oplocks = no
[2015/03/27 11:29:31.918520,  2, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[share]"
  doing parameter comment = Shared files.
  doing parameter path = /path/to/share
  doing parameter public = yes
  doing parameter writable = yes
  doing parameter printable = no
  doing parameter write list = @filesrw
  doing parameter create mask = 0740
  doing parameter directory mask = 0750
  doing parameter force group = filesro
[2015/03/27 11:29:31.919370,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:4877(lp_load_ex)
  pm_process() returned Yes
[2015/03/27 11:29:31.919396,  7, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:5167(lp_servicenumber)
  lp_servicenumber: couldn't find homes
[2015/03/27 11:29:31.919416,  3, pid=18338, effective(0, 0), real(0, 0)] ../source3/param/loadparm.c:1773(lp_add_ipc)
  adding IPC service
[2015/03/27 11:29:31.919444,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_util.c:115(make_user_info_map)
  Mapping user []\[username@REALM] from workstation [WIN7CLIENT]
[2015/03/27 11:29:31.919477,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_util.c:137(make_user_info_map)
  Mapped domain from [] to [SMBSERVER] for user [username@REALM] from workstation [WIN7CLIENT]
[2015/03/27 11:29:31.919497,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/user_info.c:61(make_user_info)
  attempting to make a user_info for username@REALM (username@REALM)
[2015/03/27 11:29:31.919518,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/user_info.c:72(make_user_info)
  making strings for username@REALM's user_info struct
[2015/03/27 11:29:31.919538,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/user_info.c:92(make_user_info)
  making blobs for username@REALM's user_info struct
[2015/03/27 11:29:31.919557, 10, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/user_info.c:128(make_user_info)
  made a user_info for username@REALM (username@REALM)
[2015/03/27 11:29:31.919576,  3, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:177(auth_check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user []\[username@REALM]@[WIN7CLIENT] with the new password interface
[2015/03/27 11:29:31.919595,  3, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:180(auth_check_ntlm_password)
  check_ntlm_password:  mapped user is: [SMBSERVER]\[username@REALM]@[WIN7CLIENT]
[2015/03/27 11:29:31.919614, 10, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:189(auth_check_ntlm_password)
  check_ntlm_password: auth_context challenge created by NTLMSSP callback (NTLM2)
[2015/03/27 11:29:31.919632, 10, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:191(auth_check_ntlm_password)
  challenge is: 
[2015/03/27 11:29:31.919653,  5, pid=18338, effective(0, 0), real(0, 0)] ../lib/util/util.c:556(dump_data)
  [0000] FD 55 92 FC AA 24 6E 7A                            .U...$nz 
[2015/03/27 11:29:31.919680, 10, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_builtin.c:44(check_guest_security)
  Check auth for: [username@REALM]
[2015/03/27 11:29:31.919698, 10, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:217(auth_check_ntlm_password)
  check_ntlm_password: guest had nothing to say
[2015/03/27 11:29:31.919718, 10, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_sam.c:75(auth_samstrict_auth)
  Check auth for: [username@REALM]
[2015/03/27 11:29:31.919737,  8, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/util.c:1191(is_myname)
  is_myname("SMBSERVER") returns 1
[2015/03/27 11:29:31.919758,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.919778,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.919796,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.919814,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.919832,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.919878,  5, pid=18338, effective(0, 0), real(0, 0), class=passdb] ../source3/passdb/pdb_tdb.c:594(tdbsam_getsampwnam)
  pdb_getsampwnam (TDB): error fetching database.
   Key: USER_username@realm
[2015/03/27 11:29:31.919911,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.919932,  3, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/check_samsec.c:399(check_sam_security)
  check_sam_security: Couldn't find user 'username@REALM' in passdb.
[2015/03/27 11:29:31.919952,  5, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:229(auth_check_ntlm_password)
  check_ntlm_password: sam authentication for user [username@REALM] FAILED with error NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.919974,  2, pid=18338, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:288(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [username@REALM] -> [username@REALM] FAILED with error NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.919993,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/auth_ntlmssp.c:144(auth3_check_password)
  Checking NTLMSSP password for \username@REALM failed: NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.920013,  5, pid=18338, effective(0, 0), real(0, 0)] ../auth/ntlmssp/ntlmssp_server.c:454(ntlmssp_server_check_password)
  ../auth/ntlmssp/ntlmssp_server.c:454: Checking NTLMSSP password for \username@REALM failed: NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.920034,  2, pid=18338, effective(0, 0), real(0, 0)] ../auth/gensec/spnego.c:743(gensec_spnego_server_negTokenTarg)
  SPNEGO login failed: NT_STATUS_NO_SUCH_USER
[2015/03/27 11:29:31.920057,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:216(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.920077,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:485(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2015/03/27 11:29:31.920095,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2015/03/27 11:29:31.920113,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.920134,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.920168,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:424(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.920188,  5, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:187(dbwrap_check_lock_order)
  check lock order 1 for /var/run/samba/smbXsrv_session_global.tdb
[2015/03/27 11:29:31.920207, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:133(debug_lock_order)
  lock order:  1:/var/run/samba/smbXsrv_session_global.tdb 2:<none> 3:<none>
[2015/03/27 11:29:31.920228, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:59(db_tdb_log_key)
  Locking key E400ED96
[2015/03/27 11:29:31.920249, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:143(db_tdb_fetch_locked_internal)
  Allocated locked data 0x0x7f8c7a4ff500
[2015/03/27 11:29:31.920278, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap_tdb.c:59(db_tdb_log_key)
  Unlocking key E400ED96
[2015/03/27 11:29:31.920299,  5, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:146(dbwrap_lock_order_state_destructor)
  release lock order 1 for /var/run/samba/smbXsrv_session_global.tdb
[2015/03/27 11:29:31.920317, 10, pid=18338, effective(0, 0), real(0, 0)] ../lib/dbwrap/dbwrap.c:133(debug_lock_order)
  lock order:  1:<none> 2:<none> 3:<none>
[2015/03/27 11:29:31.920345, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2598(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_LOGON_FAILURE] || at ../source3/smbd/smb2_sesssetup.c:130
[2015/03/27 11:29:31.920368, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:2499(smbd_smb2_request_done_ex)
  smbd_smb2_request_done_ex: idx[1] status[NT_STATUS_LOGON_FAILURE] body[8] dyn[yes:1] at ../source3/smbd/smb2_server.c:2651
[2015/03/27 11:29:31.920388, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:874(smb2_set_operation_credit)
  smb2_set_operation_credit: requested 31, charge 1, granted 1, current possible/max 512/512, total granted/max/low/range 1/8192/3/1
[2015/03/27 11:29:31.922598, 10, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/smb2_server.c:1002(smbd_server_connection_terminate_ex)
  smbd_server_connection_terminate_ex: reason[NT_STATUS_CONNECTION_RESET] at ../source3/smbd/smb2_server.c:3293
[2015/03/27 11:29:31.922641,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.922663,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.922681,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.922713,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.922736,  4, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/sec_ctx.c:316(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2015/03/27 11:29:31.922755,  5, pid=18338, effective(0, 0), real(0, 0)] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2015/03/27 11:29:31.922773,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/auth/token_util.c:528(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2015/03/27 11:29:31.922802,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/uid.c:425(smbd_change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2015/03/27 11:29:31.922825,  5, pid=18338, effective(0, 0), real(0, 0)] ../source3/lib/messages.c:340(messaging_deregister)
  Deregistering messaging pointer for type 1536 - private_data=0x7f8c7a4eed80
[2015/03/27 11:29:31.922877,  3, pid=18338, effective(0, 0), real(0, 0)] ../source3/smbd/server_exit.c:212(exit_server_common)
  Server exit (NT_STATUS_CONNECTION_RESET)

```

---

### Post by robsoles on 2015-03-27
I have to go beddies now but as you've dug in that far and found that maybe you can find the mechanism mincing the credentials and have a go at making it stop.

Sorry, I don't think I've been a brilliant help - sort of off all day really; at least I bumped your thread to top of list a few times :)

---

### Post by peridian on 2015-04-19
Grrrr!  Well that took a long time to figure out.

In the end, all I had to do was add arcfour-hmac-md5:normal to the list of accepted encryption types on the KDC, and regenerate the password for the user accounts.  I had correctly followed the instructions and generated the cifs/fqdn principal with arcfour, but I had not allowed it as an accepted encryption type.  It seems that Samba cannot work with anything other than arcfour, so even if you generate the keytab with aes256, it won't work.

FYI, the domain name changing is default behaviour, it remaps the username to the local default domain setting, as set by the net command.  By default, this is the NetBios name for the Samba server, so hence it kept remapping to SMBSERV as it believed this to be the default domain.  This is expected when connected on a domain.

Regards,
Rob.

---

