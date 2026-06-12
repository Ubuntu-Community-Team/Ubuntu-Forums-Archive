---
title: "Ubuntu 11.03 server likewise samba kerberos authentication"
date: 2011-08-24
forum: Server Platforms
---

### Post by delineator on 2011-08-24
Hello all,

I have not posted in here in a while but always find the information to be extremely helpful. Okay, my problem is that I have ESXi vmware server as host with guest win2k3 server as domain controller, Ubuntu Sever Natty Narwal as file server. Now, with my natty narwal use it as a cifs server (samba) but I have likewise open5 installed which enables me to authenticate my user logons to my domain controller. However, my problem exists with samba not being able to authenticate users against the domain controller.

Here is my /etc/samba/smb.conf file:

[global]
    workgroup = RAPPERSDELIGHT
    realm = RAPPERSDELIGHT.BIZ
    server string = %h server (Samba, Ubuntu)
    security = ADS
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap backend = lwopen
    idmap uid = 50-9999999999
    idmap gid = 50-9999999999
    winbind separator = +
    winbind enum users = Yes
    winbind enum groups = Yes
    winbind use default domain = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Audio]
    path = /media/Audio
    read only = No
    create mask = 0755
    guest ok = Yes

[Videos]
    path = /media/Videos
    read only = No
    create mask = 0755
    guest ok = Yes

Heres the samba debug log:

cat /var/log/samba/log.192.168.1.44 
[2011/08/24 00:59:15.657291,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 00:59:15.657492,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 00:59:26.362506,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/08/24 00:59:26.362598,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/08/24 00:59:32.512947,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 00:59:32.513146,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 00:59:44.363260,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/08/24 00:59:44.363372,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/08/24 01:02:10.213241,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:10.213408,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:11.209668,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:11.209747,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:12.073376,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:12.073455,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:12.432278,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:12.432355,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:12.734383,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:12.734461,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:13.280308,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:13.280539,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:13.513346,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:13.513424,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:13.991175,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:13.991340,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:14.379551,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:14.379630,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:14.728088,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:14.728167,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:15.120826,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:15.120906,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:15.470259,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:15.470344,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:15.790327,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:15.790431,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:16.136241,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:16.136318,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:16.480421,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:16.480499,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:16.850554,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:16.850630,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:17.166640,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:17.166715,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:17.463324,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:17.463401,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:17.764088,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:17.764164,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:18.105088,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:18.105165,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:18.502366,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:18.502441,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:18.850159,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:18.850235,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:19.158426,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:19.158503,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:19.643967,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:19.644058,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:20.016922,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:20.016999,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:20.436055,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:20.436133,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:20.797500,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:20.798967,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:32.380063,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/08/24 01:02:32.380196,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/08/24 01:02:38.462472,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:02:38.462756,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:02:50.387517,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/08/24 01:02:50.387658,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/08/24 01:56:18.351072,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:56:18.354927,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:56:28.124273,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 01:56:28.124364,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 01:56:42.549407,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/08/24 01:56:42.549552,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/08/24 09:09:12.191025,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 09:09:12.191201,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 09:09:21.958469,  1] libads/kerberos_verify.c:339(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password
[2011/08/24 09:09:21.958561,  1] smbd/sesssetup.c:332(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/08/24 09:09:32.130952,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/08/24 09:09:32.131128,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
RAPPERSDELIGHT\peverett@bigl:~$ 

Likewise installs winbind, kerberos, and I am not able to get any info the a wbinfo -u,-g. I do receive a ticket from KDC when I logon but if I use kinit to generate another ticket then I get this error: 

kinit [EMAIL="peverett@rappersdelight.biz"]peverett@rappersdelight.biz[/EMAIL]
Password for [EMAIL="peverett@rappersdelight.biz"]peverett@rappersdelight.biz[/EMAIL]: 
kinit: KDC reply did not match expectations while getting initial credentials

Any help would be greatly appreciated thank you.

P.S. Likewise used to work fine for samba -AD integration on Ubuntu sever 9.04!

---

