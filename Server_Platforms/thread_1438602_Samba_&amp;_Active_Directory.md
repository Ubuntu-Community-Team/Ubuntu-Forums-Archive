---
title: "Samba &amp; Active Directory"
date: 2010-03-25
forum: Server Platforms
---

### Post by Rokurosv on 2010-03-25
So you've probably seen me ask around about Samba and AD, that's because we're doing a little project at work to make a file server with AD integration. Now what we've done so far is to be able configure Samba and Kerberos and to join the Ubuntu box to the AD, it shows up in computers in our AD.

We've followed this guide from Ubuntu and Samba
[http://ubuntuwiki.net/index.php/Samba,_Active_Directory_with_Winbind](http://ubuntuwiki.net/index.php/Samba,_Active_Directory_with_Winbind)

[http://wiki.samba.org/index.php/Samba_%26_Active_Directory](http://wiki.samba.org/index.php/Samba_%26_Active_Directory)

Now we've followed the first one for configuring most of the server but in the Samba Wiki guide it says that we also have to modify our Pam directory. 

With the first guide when a user tries to connect to one of our test share they get an auth pop up, even if they enter their correct username and password they get an error saying that they don't have the privileges to access the share. 

Here are a couple of our logs:

nmbd log
```
Samba name server FSLX01 is now a local master browser for workgroup DOMAIN on subnet 10.10.12.70    *****
[2010/03/24 16:16:50,  0]nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)  find_domain_master_name_query_fail:  Unable to find the Domain Master Browser name DOMAIN<1b> for the workgroup DOMAIN.  Unable to sync browse lists in this workgroup.
[2010/03/24 16:27:52,  0] nmbd/nmbd.c:71(terminate)  Got SIGTERM: going down...
[2010/03/24 16:27:54,  0] nmbd/nmbd.c:854(main)  nmbd version 3.4.0 started.  Copyright Andrew Tridgell and the Samba Team 1992-2009[2010/03/24 16:28:17,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)  *****    Samba name server FSLX01 is now a local master browser for workgroup DOMAIN on subnet 10.10.12.70    *****
[2010/03/24 16:51:35,  0] nmbd/nmbd.c:71(terminate)  Got SIGTERM: going down...
[2010/03/24 16:51:38,  0] nmbd/nmbd.c:854(main)  nmbd version 3.4.0 started.  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/03/24 16:52:01,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)  *****    Samba name server FSLX01 is now a local master browser for workgroup DOMAIN on subnet 10.10.12.70    *****
[2010/03/24 17:03:22,  0] nmbd/nmbd.c:71(terminate)  Got SIGTERM: going down...
[2010/03/24 17:04:04,  0] nmbd/nmbd.c:854(main)  nmbd version 3.4.0 started.  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/03/24 17:04:27,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)  *****    Samba name server FSLX01 is now a local master browser for workgroup DOMAIN on subnet 10.10.12.70    *****
```

winbind log

```
[2010/03/24 16:29:25,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 16:34:30,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 16:39:30,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 16:44:30,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 16:49:38,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 16:55:06,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 17:00:34,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 17:03:24,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)  Got sig[15] terminate (is_parent=1)
[2010/03/24 17:04:04,  0] winbindd/winbindd.c:1244(main)  winbindd version 3.4.0 started.  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/03/24 17:04:04,  0] param/loadparm.c:7493(lp_do_parameter)  Global parameter guest account found in service section![2010/03/24 17:04:04,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/03/24 17:04:09,  0] libsmb/cliconnect.c:996(cli_session_setup_spnego)  Kinit failed: Cannot contact any KDC for requested realm[2010/03/24 17:04:09,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 17:09:31,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 17:14:59,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 17:20:01,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 17:25:01,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 17:30:21,  1] winbindd/winbindd_util.c:303(trustdom_recv)  Could not receive trustdoms
[2010/03/24 17:35:21,  1] winbindd/winbindd_util.c:303(trustdom_recv)
```

smbd log
```
2010/03/24 16:57:28,  0] lib/util_sock.c:537(read_socket_with_timeout)
[2010/03/24 16:57:28,  0] lib/util_sock.c:1468(get_peer_addr_internal)  getpeername failed. Error was Transport endpoint is not connected  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/03/24 16:58:04,  0] lib/util_sock.c:537(read_socket_with_timeout)
[2010/03/24 16:58:04,  0] lib/util_sock.c:1468(get_peer_addr_internal)  getpeername failed. Error was Transport endpoint is not connected  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/03/24 16:58:34,  0] lib/util_sock.c:537(read_socket_with_timeout)
[2010/03/24 16:58:34,  0] lib/util_sock.c:1468(get_peer_addr_internal)  getpeername failed. Error was Transport endpoint is not connected  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/03/24 17:04:04,  0] smbd/server.c:1068(main)  smbd version 3.4.0 started.  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/03/24 17:04:04,  0] param/loadparm.c:7493(lp_do_parameter)  Global parameter guest account found in service section!
[2010/03/24 17:04:04,  0] printing/print_cups.c:103(cups_connect)  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/03/24 17:04:04,  0] printing/print_cups.c:103(cups_connect)  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/03/24 17:04:09,  0] smbd/server.c:456(smbd_open_one_socket)  smbd_open_once_socket: open_socket_in: Address already in use
[2010/03/24 17:04:09,  0] smbd/server.c:456(smbd_open_one_socket)  smbd_open_once_socket: open_socket_in: Address already in use
[2010/03/24 17:06:12,  0] param/loadparm.c:9783(widelinks_warning)  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2010/03/24 17:06:13,  1] smbd/service.c:676(make_connection_snum)  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/03/24 17:06:35,  1] smbd/service.c:676(make_connection_snum)  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/03/24 17:09:12,  0] printing/print_cups.c:103(cups_connect)  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/03/24 17:09:12,  0] printing/print_cups.c:103(cups_connect)  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/03/24 17:15:18,  0] lib/util_sock.c:537(read_socket_with_timeout)
[2010/03/24 17:15:18,  0] lib/util_sock.c:1468(get_peer_addr_internal)  getpeername failed. Error was Transport endpoint is not connected  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```

domain log

```
[2010/03/24 15:45:32,  1] rpc_client/cli_pipe.c:948(cli_pipe_validate_current_pdu)  cli_pipe_validate_current_pdu: RPC fault code DCERPC fault 0x00000721 received from host SERVER.DOMAIN.com!
[2010/03/24 15:53:45,  1] libsmb/clikrb5.c:697(ads_krb5_mk_req)  ads_krb5_mk_req: krb5_get_credentials failed for SERVER$@DOMAIN (Cannot resolve network address for KDC in requested realm)
[2010/03/24 15:53:45,  1] libsmb/cliconnect.c:745(cli_session_setup_kerberos)  cli_session_setup_kerberos: spnego_gen_negTokenTarg failed: Cannot resolve network address for KDC in requested realm
[2010/03/24 15:55:56,  0] rpc_client/cli_pipe.c:687(cli_pipe_verify_schannel)  cli_pipe_verify_schannel: auth_len 56.
[2010/03/24 15:58:21,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)  Got sig[15] terminate (is_parent=0)
[2010/03/24 15:58:23,  1] libsmb/clikrb5.c:697(ads_krb5_mk_req)  ads_krb5_mk_req: krb5_get_credentials failed for SERVER$@DOMAIN (Cannot resolve network address for KDC in requested realm)
[2010/03/24 15:58:23,  1] libsmb/cliconnect.c:745(cli_session_setup_kerberos)  cli_session_setup_kerberos: spnego_gen_negTokenTarg failed: Cannot resolve network address for KDC in requested realm
[2010/03/24 15:58:23,  0] rpc_client/cli_pipe.c:687(cli_pipe_verify_schannel)  cli_pipe_verify_schannel: auth_len 56.
[2010/03/24 16:03:27,  1] rpc_client/cli_pipe.c:948(cli_pipe_validate_current_pdu)  cli_pipe_validate_current_pdu: RPC fault code DCERPC fault 0x00000721 received from host SERVER.DOMAIN.com!
[2010/03/24 17:03:24,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)  Got sig[15] terminate (is_parent=0)
[2010/03/24 17:04:05,  0] libsmb/cliconnect.c:996(cli_session_setup_spnego)  Kinit failed: Cannot contact any KDC for requested realm
[2010/03/24 17:04:09,  0] rpc_client/cli_pipe.c:687(cli_pipe_verify_schannel)  cli_pipe_verify_schannel: auth_len 56.
[2010/03/24 17:06:24,  1] rpc_client/cli_pipe.c:948(cli_pipe_validate_current_pdu)  cli_pipe_validate_current_pdu: RPC fault code DCERPC fault 0x00000721 received from host SERVER.DOMAIN.com!
```

I've used DOMAIN instead of our domain and SERVER instead of our AD server. The config files(krb5.conf, smb.conf, nsswitch.conf) look like the Ubuntu guide with our data in it. We haven't touched the pam.d dir yet. 
We're authenticating against a server running Win Server 2008 R2, could that be an issue?

Your help regarding our little experiment will be greatly appreciated :D

Thanks for your time

---

### Post by HermanAB on 2010-03-25
Hmm, in my experience the error messages that one get are either totally useless or very specific.  in your case it says that the user doesn't have permission to access the share.  I would take it as meaning *exactly* that.

In other words, at that point, most things are actually working and you should look at the group memberships.

Here is a guide I wrote long ago which may give you some help with debugging your problem:
[http://www.aeronetworks.ca/LinuxActiveDirectory.html](http://www.aeronetworks.ca/LinuxActiveDirectory.html)

---

### Post by jrssystemsnet on 2010-03-25
> **Rokurosv said:**
> So you've probably seen me ask around about Samba and AD, that's because we're doing a little project at work to make a file server with AD integration. Now what we've done so far is to be able configure Samba and Kerberos and to join the Ubuntu box to the AD, it shows up in computers in our AD.

We've followed this guide from Ubuntu and Samba
[http://ubuntuwiki.net/index.php/Samba,_Active_Directory_with_Winbind](http://ubuntuwiki.net/index.php/Samba,_Active_Directory_with_Winbind)

Note: I wrote that myself - very recently - as documentation for a (working nicely) Ubuntu + Samba fileserver on a customer's domain. :)

The intent being not to brag, but to assure you that it's very recent documentation that produced a working Samba fileserver attached to an AD (Server 2003 schema) domain.

> Now we've followed the first one for configuring most of the server but in the Samba Wiki guide it says that we also have to modify our Pam directory.

You don't, unless you also want to use your AD credentials to allow logging into the box via SSH, FTP, or some other service that uses PAM.  You absolutely do not need it for Samba file service; I didn't configure it at all, and my boxes are working fine.

```
libsmb/cliconnect.c:996(cli_session_setup_spnego)  Kinit failed: Cannot contact any KDC for requested realm[2010/03/24 17:04:09,  1] 
```

Now, I will admit, I'm no Kerberos guru and although I wrote that how-to, I'm pretty new to joining Samba to AD... but that error message looks to me as though it tells the story.  If you can't contact a Kerberos Distribution Center, you can't authenticate with AD.

Head back to my wiki article, hit the troubleshooting section, and answer the following questions:

* can you get a Kerberos ticket?
* does wbinfo -t successfully check the trust secret?  (Hint: it doesn't; we already saw that in your logs.  But look anyway, and post results here.)
* does wbinfo -u successfully retrieve a list of your AD users? (Not without a trust relationship, it won't: but see above.)
* does the Samba server show up in your AD as a member server?

[img]http://virtual.tehinterweb.net/livejournal/Samba-Server-In-Active-Directory_Listing.png[/img]

You do NOT have to manually add the Samba server into AD from the Windows side to have it show up... if you successfully joined it to the domain as in my wiki article, it shows up there all by itself.

---

### Post by Rokurosv on 2010-03-25
Nice! A little help from the author :D

Ok so I changed a few things:
My password server was wrong and my kdc was also misspelled

now the output I get from both commands is:
wbinfo -t
checking the trust secret via RPC calls succeeded

wbinfo -u
Lists all users

wbinfo -g
Lists all groups

Now I'm getting an error when I try to use smbclient to connect to my share, I get a 
session setup failed: NT_STATUS_PIPE_DISCONNECTED
error when I do so, no matter which user I try.

Also could you please explain a little more in detail the fstab configs, I already made that change and I wanted to know why do I have to modify it.

Thanks :D

---

### Post by jrssystemsnet on 2010-03-25
> **Rokurosv said:**
> now the output I get from both commands is:
wbinfo -t
checking the trust secret via RPC calls succeeded

wbinfo -u
Lists all users

wbinfo -g
Lists all groupsAlright!  Now we're getting somewhere. :)

> Now I'm getting an error when I try to use smbclient to connect to my share, I get a 
session setup failed: NT_STATUS_PIPE_DISCONNECTED
error when I do so, no matter which user I try.

1. is Samba started?  /etc/init.d/samba status
2. do you have a firewall running?  does the firewall allow incoming traffic on ports 139 and 445?

> Also could you please explain a little more in detail the fstab configs, I already made that change and I wanted to know why do I have to modify it.You only have to modify it if you want to enable ACLs on the share, which allow you to set more complicated permissions than just "owner, group, world".  NTFS uses a very complex set of permissions which can be inherited, can apply to multiple users / groups, etc; Unix filesystems by default are much, much simpler.

Of course, the upside to Unix-style simple filesystem permissions is that they don't impose the potential performance overhead that ACLs can.  You do whichever you feel like you need / would prefer to do. :)

---

### Post by Rokurosv on 2010-03-25
* nmbd is running
 * smbd is running

My krb file

```
[logging]
default = FILE:/var/log/kerberos/log.def
kdc = FILE:/var/log/kerberos/log.kdc
admin_server = FILE:/var/log/kerberos/log.admin

[libdefaults]
default_realm = DOMAIN.COM

[realms]
BCES.COM = {
        kdc = SERVER_NAME_IN_CAPS.domain.com
        admin-server = SERVER_NAME_IN_CAPS.domain.com
        default_domain = DOMAIN.COM
}

[domain_realm]
        .domain.com = DOMAIN.COM
        domain.com = DOMAIN.COM
```
Anything special that I should be checking?

---

### Post by jrssystemsnet on 2010-03-25
Your krb.conf file is irrelevant at this point; Kerberos is working or you wouldn't be able to fetch usernames with wbinfo.  But just to confirm, trot over to one of your Windows DCs and check the Directory - does your Samba machine show up in the Computers list?

You never answered the question about a firewall, which is more likely to be relevant.

Please post the exact command (and results) from ```
you@box:~# **smbclient -U Administrator -L 127.0.0.1**
``` and we should be able to get this sorted out.

Also please show any share definitions you have in /etc/samba/smb.conf.

---

### Post by Rokurosv on 2010-03-25
The firewall doesn't block those ports, already confirmed with the person in charge of it

Here's the output from the command:
smbclient -U Administrator -L 127.0.0.1
Enter Administrator's password:
session setup failed: NT_STATUS_PIPE_DISCONNECTED

A test share define in smb.conf, currently the only share define.

```
[Test]
        comment = Test share
        path = /home/shares/test
        writeable = yes
        browseable = yes
        valid users = @DOMAIN\group_name_as_shown_in_wbinfo-g
```

---

### Post by jrssystemsnet on 2010-03-25
> **Rokurosv said:**
> The firewall doesn't block those ports, already confirmed with the person in charge of itWe're not talking about the firewall at your internet connection, we're talking about any firewall you might have running on this machine itself.  Otherwise instead of a disconnected pipe error, you'd be either succeeding, or getting this:

```
me@fileserver:~$ smbclient -U administrator -L 127.0.0.1
Enter administrator's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
```

Check /var/log/samba/log.127.0.0.1 and see if there's anything interesting in there.

---

### Post by Rokurosv on 2010-03-25
Ok rejoined the domain and now this is the output for smbclient:
```

Domain=[BCES] OS=[Unix] Server=[Samba 3.4.0]

        Sharename       Type      Comment
        ---------       ----      -------
        Test            Disk      Test share
        IPC$            IPC       IPC Service (Samba 3.4.0)
Domain=[BCES] OS=[Unix] Server=[Samba 3.4.0]

        Server               Comment
        ---------            -------
        SERVER_NAME
        HOSTNAME             Samba 3.4.0

        Workgroup            Master
        ---------            -------
        DOMAIN               HOSTNAME
```
And now I've tried accesing a share from a windows pc with the IP address like so

```
\\1.2.3.4\test 
or
\\1.2.3.4\
```

and both of em return the password popup.
Tried login in with smbclient
```
smbclient -U administrator -L 127.0.0.1
Enter administrator's password:
session setup failed: NT_STATUS_LOGON_FAILURE
```

Logging in as a the domain admin.

---

### Post by jrssystemsnet on 2010-03-25
Getting much closer.

Remove the "valid users" portion of your share definition, make sure the folder is chmodded 777, and try to browse to it again.  (Always get "access at all" working before you try to get "access to some but not others" working.)

Although actually:

> ```
smbclient -U administrator -L 127.0.0.1
Enter administrator's password:
session setup failed: NT_STATUS_LOGON_FAILURE
```

Assuming you didn't fat-finger the Administrator password, that tells us right now that something else is up.  Let's see the contents of /etc/nsswitch.conf, /etc/resolv.conf, and the Authentication portion of /etc/samba/smb.conf.

---

### Post by Rokurosv on 2010-03-25
nsswitch
```
passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

resolv.conf

```
search domain.com
nameserver ip.of.our.dns
```

Also, now I changed access in the config, removed the valid users line and chmoded to 777 the test folder, and when I try to enter from a windows pc I get a "no process at the end of the pipe error"

---

### Post by jrssystemsnet on 2010-03-25
When you say "ip.of.our.dns", is that the IP of your *Active Directory* dns provider?  Typically, this should be one of your DCs.

Forget the Windows PCs for now, stick to smbclient, and to posting *exact* commands and *exact* results tried.

---

### Post by Rokurosv on 2010-03-25
> **jrssystemsnet said:**
> When you say "ip.of.our.dns", is that the IP of your *Active Directory* dns provider?  Typically, this should be one of your DCs.

Forget the Windows PCs for now, stick to smbclient, and to posting *exact* commands and *exact* results tried.

Yes, it's the IP of our DC.

Ok I will stick to smbclient
Here I've tried with my user in the DC
```
smbclient -U ronald_erazo -L 127.0.0.1
Enter ronald_erazo's password:
session setup failed: NT_STATUS_PIPE_DISCONNECTED
```

---

### Post by jrssystemsnet on 2010-03-25
OK, look at the end of /var/log/samba/log.127.0.0.1 - anything interesting?

Similarly, look at the Event Viewer on the DC which you've configured as the admin server in krb5.conf - anything interesting?

---

### Post by Rokurosv on 2010-03-25
Here's what I found in my event viewer

```
During the previous 24 hour period, some clients attempted to perform LDAP binds that were either: 
(1) A SASL (Negotiate, Kerberos, NTLM, or Digest) LDAP bind that did not request signing (integrity validation), or 
(2) A LDAP simple bind that was performed on a cleartext (non-SSL/TLS-encrypted) connection 
 
This directory server is not currently configured to reject such binds.  The security of this directory server can be significantly enhanced by configuring the server to reject such binds.  For more details and information on how to make this configuration change to the server, please see http://go.microsoft.com/fwlink/?LinkID=87923. 
 
Summary information on the number of these binds received within the past 24 hours is below. 
 
You can enable additional logging to log an event each time a client makes such a bind, including information on which client made the bind.  To do so, please raise the setting for the "LDAP Interface Events" event logging category to level 2 or higher. 
 
Number of simple binds performed without SSL/TLS: 781 
Number of Negotiate/Kerberos/NTLM/Digest binds performed without signing: 27
```

Also when I run testparm I get a warning
```
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
```

And I could not find that log, there are various log files, but not one named log.127.0.0.1

---

### Post by jrssystemsnet on 2010-03-25
OK, so what log files *do* you have under /var/log/samba?

---

### Post by Rokurosv on 2010-03-25
log.smbd     
log.wb-BUILTIN  
log.winbindd             
log.winbindd-idmap
log.nmbd  
log.wb-DOMAIN
log.wb-HOSTNAME
log.winbindd-dc-connect

---

### Post by jrssystemsnet on 2010-03-25
Well, the first thing *that* tells me is that your Samba logging isn't Ubuntu standard configured, either.

Is this server already in use for production in any way, or is it still only being used for testing?  Because honestly, I think you'd be better off reverting it to a known state - ie, Ubuntu default - and starting over, if that's feasible.

If it were me, I'd go to my DC and delete the machine from AD, go back to the Samba machine and **apt-get remove samba** and **apt-get purge samba**, **rm -rf /etc/samba**, **rm /etc/nsswitch.conf**, **apt-get remove krb5-config**, **apt-get remove krb5-user**, **apt-get remove libkadm55**, **rm /etc/krb5.conf**, undo anything you did following the *other* walkthrough... and then start over from the top.

There's just too much "well at this point not sure what's been done" going on right now for me to be able to give much help, as things stand.  All I can tell you for absolute certain is that, if followed exactly from top to bottom on an Ubuntu Hardy server in otherwise default condition, that wiki article WILL produce a working Samba server joined to an AD 2003 domain.

---

### Post by Rokurosv on 2010-03-25
This server has not been used for anything other than our file server, which we're currently configuring. I'm using Ubuntu server 9.10 and trying to join a Windows Server 2008 R2 AD domain. Let me try to start from scratch.
Also what should a standard configured server look like? I'm guessing that the log part hints it. I installed samba at the moment of installing the server, perhaps that was the issue?

---

### Post by jrssystemsnet on 2010-03-25
An otherwise un-messed-with install of Samba on Ubuntu will produce one log file for each client machine that attempts to connect to the Samba server in /var/log/samba, so you should see log.127.0.0.1 and the like, for every IP address and/or hostname that tries to connect.  You also get the log entries that you had showed up above.

Honestly it's not really the logging I'm worried about *per se*, I just want you to get back to a known default state and work from there, because there is a WHOLE lot of stuff involved in between Samba, Kerberos, etc. and without starting from a known condition, we're liable to spin our wheels endlessly.

---

### Post by Rokurosv on 2010-03-25
Ok, reinstalled everything, purged the config files and installed everything again. 

Tried running
```
smbclient -U administrator -L 127.0.0.1
Enter administrator's password:
session setup failed: NT_STATUS_INVALID_PARAMETER
root@FSLX01:/etc/samba# smbclient -U administrator -L 127.0.0.1
Enter administrator's password:
session setup failed: NT code 0x00000721
root@FSLX01:/etc/samba# smbclient -U administrator -L 127.0.0.1
Enter administrator's password:
session setup failed: NT_STATUS_PIPE_DISCONNECTED
```


```
security = ads
        realm = BCES.COM
        password server = 10.10.12.4
        workgroup = BCES
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2
        log file = /var/log/samba/log.%m
        max log size = 1000

```

I backed up my smb.conf and modified to look like this. Still getting errors when using smbclient and now there is a log for my machine but it's empty.

---

### Post by Rokurosv on 2010-03-25
Also I tried this

```
wbinfo -K ronald_erazo
Enter ronald_erazo's password:
plaintext kerberos password authentication for [ronald_erazo] succeeded (requesting cctype: FILE)
credentials were put in: FILE:/tmp/krb5cc_0
```

and it succeeded with kerberos but when I try winbind

```
wbinfo -a ronald_erazo
Enter ronald_erazo's password:
plaintext password authentication failed
Could not authenticate user ronald_erazo with plaintext password

```

---

### Post by jrssystemsnet on 2010-03-25
> **Rokurosv said:**
> Also I tried this

```
wbinfo -K ronald_erazo
Enter ronald_erazo's password:
plaintext kerberos password authentication for [ronald_erazo] succeeded (requesting cctype: FILE)
credentials were put in: FILE:/tmp/krb5cc_0
```

and it succeeded with kerberos but when I try winbind

```
wbinfo -a ronald_erazo
Enter ronald_erazo's password:
plaintext password authentication failed
Could not authenticate user ronald_erazo with plaintext password

```

Interesting.  Is your AD schema Server 2003, or Server 2008?

---

### Post by redmk2 on 2010-03-25
> **jrssystemsnet said:**
> Interesting.  Is your AD schema Server 2003, or Server 2008?

The OP stated: *"We're authenticating against a server running Win Server 2008 R2, could that be an issue?"*.  I believe this is the issue.  it is also possible that the OP does not have the latest [COLOR="Red"]samba-common[/COLOR] package. If he is running Jaunty then he is using Samba 3.2.  The default authentication should be NTLMv2.  This is the default for Win2008 r2 and Samba 3.4

The compatible AUTH can be set in either (up or down).

---

### Post by jrssystemsnet on 2010-03-26
I'm at a bit of a loss as to why it's doing plaintext passwords, since the smb.conf apparently states:

```
        client ntlmv2 auth = yes
        encrypt passwords = yes

```

---

### Post by redmk2 on 2010-03-26
> **jrssystemsnet said:**
> I'm at a bit of a loss as to why it's doing plaintext passwords, since the smb.conf apparently states:

```
        client ntlmv2 auth = yes
        encrypt passwords = yes

```

I wonder what the client is.  Is it configured (or defaults to) plain text?

The default for NTLMv2 is: [FONT="Courier New"]client ntlmv2 auth = no [/FONT]

Quoting from [_http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html_]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")

"If enabled, only an NTLMv2 and LMv2 response (both much more secure than earlier versions) will be sent."

One last thing.  I don't see a [FONT="Courier New"]security = ADS[/FONT], therefore the default is: [FONT="Courier New"]security = user[/FONT].  Could this cause problems?

---

### Post by Rokurosv on 2010-03-26
I'm using 9.10 with both packages, samba and samba-common on version 2:3.4.0-3ubuntu5.6 as shown by aptitude. I also find it strange that even when I'm stating the use of ntlmv2 on the config it sends the passwords on plain text. Perhaps there is something wrong in the config ?

---

### Post by redmk2 on 2010-03-26
> **Rokurosv said:**
> I'm using 9.10 with both packages, samba and samba-common on version 2:3.4.0-3ubuntu5.6 as shown by aptitude. I also find it strange that even when I'm stating the use of ntlmv2 on the config it sends the passwords on plain text. Perhaps there is something wrong in the config ?

The client initiates the request.  If the client starts in plain text, then the server must respond.  In your case you have told the server to dismiss all plain test requests.  The default is more flexible.  See my post above.

---

### Post by Rokurosv on 2010-03-26
> **redmk2 said:**
> The client initiates the request.  If the client starts in plain text, then the server must respond.  In your case you have told the server to dismiss all plain test requests.  The default is more flexible.  See my post above.

Yes I have it in my smb.conf, here is the global part
```
[global]
        security = ADS
        realm = DOMAIN.COM
        password server = IP.ADDRESS
        workgroup = DOMAIN
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
```

So what you're suggesting is to try without the ntlmv2 auth option?

---

### Post by redmk2 on 2010-03-26
> **Rokurosv said:**
> Yes I have it in my smb.conf, here is the global part
```
[global]
        security = ADS
        realm = BCES.COM
        password server = 10.10.12.4
        workgroup = BCES
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
```

So what you're suggesting is to try without the ntlmv2 auth option?

You could try BOTH of these set to: 
```

[FONT="Courier New"]client ntlmv2 auth = no
encrypt passwords = no[/FONT]
```

Do you have any thoughts on why you have not configured (left at the default) the "security =" parameter.  The default is "user" not "ads".

Remember to restart the Samba services. :-)

---

### Post by fang0654 on 2010-03-26
I tried setting up Samba with AD a couple of years ago, and could never get it to work 100%. (Multiple domain AD, couldn't ever see cross-domains).  An easier alternative is using Likewise Open.  They have ubuntu packages on their website, and it only takes a couple of minutes to get Samba up and running that way.

If you are interested, I'll post step by step instructions.  I've been using it this way for a couple of years now without any issues.

---

### Post by jrssystemsnet on 2010-03-26
Well heck, if nobody else is interested, I am - I've got Samba working for what I need it to, but it's always nice to know another way. =)

Is "Likewise Open" free as in beer and/or as in speech?

---

### Post by fang0654 on 2010-03-26
It is open source, and built upon samba, winbind, krb, etc.  It actually has a slew of features, but I've just used it for handling all of the AD integration with our file servers.  If you'd like more info, their "About" page is here:

[http://www.likewise.com/products/likewise_open/index.php]("http://www.likewise.com/products/likewise_open/index.php")

Note, all the info on integration is based off of Likewise's own documentation, and my experience with it.

The steps from vanilla to full AD integration:

First, make sure your DNS server is the domain controller you want to authenticate with.  Next go to the Likewise Open download page located here:

[http://www.likewise.com/community/index.php/download/]("http://www.likewise.com/community/index.php/download/")

And download the appropriate version (32 or 64 bit) for Debian/Ubuntu.

```
wget http://www.likewise.com/bits/summer09/7724/LikewiseIdentityServiceOpen-5.3.0.7724-linux-i386-deb.sh

```

Next, make the downloaded file executable, and install it.

```

chmod +x LikewiseIdentityServiceOpen-5.3.0.7724-linux-i386-deb.sh
sudo ./LikewiseIdentityServiceOpen-5.3.0.7724-linux-i386-deb.sh

```

Accept the various GPL/BSD licenses, say yes to install, and sit back for a couple of minutes.  After it installs, type in the following to get basic authentication set up with Active Directory:

```

sudo /opt/likewise/bin/domainjoin-cli join domainName ADjoinAccount

```


You can test it out with the following:
```

su - 'DOMAIN\ADUser'

```

You should be prompted for a password, and then be logged in!

Go ahead and log back out of that user.

Now for integrating Samba.  Make sure samba is installed with:

```

sudo apt-get install samba

```

Next, create a directory named 'idmap' under /usr/lib64/samba, (/usr/lib/samba for 32 bit servers). Create a symbolic link from /usr/lib64/samba/idmap/lwicompat_v2.so to point to /opt/likewise/lib64/lwicompat_v2.so. Repeat for lwicompat_v3 and lwicompat_v4.

For 64 bit:
```

cd /usr/lib64/samba
sudo mkdir idmap
cd idmap
sudo ln -s /opt/likewise/lib64/lwicompat_v4.so

```

or for 32 bit:
```

cd /usr/lib/samba
sudo mkdir idmap
cd idmap
sudo ln -s /opt/likewise/lib/lwicompat_v4.so

```

Backup the /etc/samba/smb.conf like so:

```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.old
sudo nano /etc/samba/smb.conf

```

And replace it with the following:

```

[global]
   security = ads
   workgroup = DOMAIN
   realm = DOMAIN.COM
   idmap uid = 50-999999999
   idmap gid = 50-999999999
   idmap backend = lwicompat_v4
   template shell = /bin/bash
   winbind enum users = Yes
   winbind enum groups = Yes
   password server = domain.com 
   domain master = No
   template shell = /bin/bash
   log file = /var/log/samba/log.%m


```

Next, change the file /etc/likewise/pstore.conf to match the following:

```

#
# Likewise Password Storage (LWPS)
#

[password storage:sql-db]
    type = sqldb
    path = /opt/likewise/lib/liblwps-sqldb.so
    default = yes
[password storage:tdb]
    type = tdb
    path = /opt/likewise/lib/liblwps-tdb.so
    db path = /var/lib/samba/secrets.tdb


```

Next, put in the initial SID and machine account info into samba.  First, get it from Likewise:

```

sudo/opt/likewise/bin/lw-dump-machine-acct <dns domain>
  DomainSID                = S-1-5-21-aaaa-bbbbb-ccccc-ddddd
  DomainName               = AD
  Domain DNS Name          = AD.PLAINJOE.ORG
  HostName                 = srv3
  Machine Account Name     = srv3$
  Machine Account Password = EncryptedStringPassword

```

Then, enter in the SID:

```

sudo net setdomainsid S-1-5-21-aaaa-bbbbb-ccccc-ddddd

```

Next, enter in the Machine Account Password:

```

sudo net changesecretpw -f
Enter password: <EncryptedStringPassword>

```

Reboot, log in, and do the following to see if it all took:

```

sudo net ads testjoin

```

If you get "Join is Ok", then you should be all set up.

---

### Post by Rokurosv on 2010-03-26
Thanks fang0654 will definitely give it a read and try using Likewise.

By the way I have to say that this forum post and its contributors have been more helpful than anything I've found on the web.
Once I pull this off I'll definitely be documenting all I've learned so far :D Thanks guys. Right now I'm going to give Winbind another try and if it fails I'm going to try with Likewise.

---

### Post by phrstbrn on 2010-03-29
I'm in the middle of an integration of Karmic and AD on Win2008r2.

I found that the version of samba in Karmic is out of date.  I read somewhere on the Samba mailing list that Win2008r2 broke a lot of things in samba, which is fixed in the newer versions. (I'm at work and I can't look through the mailing lists to pull up the exact post)

I pulled the source packages from Lucid (packages.ubuntu.com) and recompiled them for Karmic (there were a few dependency issues that I had to override to get it to compile).  So far it seems to be working OK.

I'm going to guess all of this will smooth over once Lucid comes out (Karmic is older then Win2008r2).

---

### Post by Rokurosv on 2010-03-29
> **phrstbrn said:**
> I'm in the middle of an integration of Karmic and AD on Win2008r2.

I found that the version of samba in Karmic is out of date.  I read somewhere on the Samba mailing list that Win2008r2 broke a lot of things in samba, which is fixed in the newer versions. (I'm at work and I can't look through the mailing lists to pull up the exact post)

I pulled the source packages from Lucid (packages.ubuntu.com) and recompiled them for Karmic (there were a few dependency issues that I had to override to get it to compile).  So far it seems to be working OK.

I'm going to guess all of this will smooth over once Lucid comes out (Karmic is older then Win2008r2).

Thanks for letting me know, might try with newer packages, although I'd prefer downloading them from samba and compile them from there. Which version are you running

---

### Post by yesrno on 2010-05-27
Hmmm got the exact same problem here, weird thing is... On my Windows 7 I recieve the pipe error, while on an XP client it works flawlessly. Maybe that's a clue ?

---

### Post by yesrno on 2010-05-27
Ok nvm it wasn't the Windows 7 and XP difference. Only clients who are not in the domain can access the share, while clients in the domain, can not.

---

