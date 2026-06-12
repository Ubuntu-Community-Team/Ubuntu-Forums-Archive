---
title: "XRDP failes authentication via xRDP"
date: 2019-02-04
forum: Security
---

### Post by divernick on 2019-02-04
I'm running Kubuntu 18.04.  Fresh new install over the last couple days.  I'm configured to authenticate off my OpenLDAP server successfully via the console, KDE Plasma desktop and SSH. xRDP authentication works with local users but connect via LDAP users via xRDP I get "pam_unix(xrdp-sesman:auth): authentication failure;" in the /var/log/auth.log file.  I've googled to death trying to find the solution with no luck so I'm at a loss for what to try next.  

Any guidance would be helpful.

This is the log file entries from xrdp-sesman.log for a connection attempt
> [20190204-20:12:26] [INFO ] A connection received from ::1 port 41062
[20190204-20:12:27] [INFO ] ++ created session (access granted): username divernick, ip ::ffff:10.1.1.90:7548 - socket: 12
[20190204-20:12:27] [INFO ] starting Xorg session...
[20190204-20:12:27] [DEBUG] Closed socket 11 (AF_INET6 :: port 5910)
[20190204-20:12:27] [DEBUG] Closed socket 11 (AF_INET6 :: port 6010)
[20190204-20:12:27] [DEBUG] Closed socket 11 (AF_INET6 :: port 6210)
[20190204-20:12:27] [DEBUG] Closed socket 8 (AF_INET6 ::1 port 3350)
[20190204-20:12:27] [INFO ] calling auth_start_session from pid 13252
[20190204-20:12:27] [DEBUG] Closed socket 7 (AF_INET6 ::1 port 3350)
[20190204-20:12:27] [DEBUG] Closed socket 8 (AF_INET6 ::1 port 3350)
[20190204-20:12:27] [INFO ] /usr/lib/xorg/Xorg :10 -auth .Xauthority -config xrdp/xorg.conf -noreset -nolisten tcp -logfile .xorgxrdp.%s.log
[20190204-20:12:27] [CORE ] waiting for window manager (pid 13253) to exit
[20190204-20:12:30] [CORE ] window manager (pid 13253) did exit, cleaning up session
[20190204-20:12:30] [INFO ] calling auth_stop_session and auth_end from pid 13252
[20190204-20:12:30] [DEBUG] cleanup_sockets:
[20190204-20:12:30] [DEBUG] cleanup_sockets: deleting /var/run/xrdp/sockdir/xrdp_chansrv_audio_out_socket_10
[20190204-20:12:30] [DEBUG] cleanup_sockets: deleting /var/run/xrdp/sockdir/xrdp_chansrv_audio_in_socket_10
[20190204-20:12:30] [DEBUG] cleanup_sockets: deleting /var/run/xrdp/sockdir/xrdpapi_10
[20190204-20:12:30] [INFO ] ++ terminated session:  username divernick, display :10.0, session_pid 13252, ip ::ffff:10.1.1.90:7548 - socket: 12


The following is the corresponding data from auth.log
> Feb  4 20:12:27 linuxdesktop xrdp-sesman[1104]: pam_unix(xrdp-sesman:auth): [COLOR=#ff0000]authentication failure; [/COLOR]logname= uid=0 euid=0 tty=xrdp-sesman ruser= rhost=  user=divernick
Feb  4 20:12:27 linuxdesktop xrdp-sesman[13252]: pam_unix(xrdp-sesman:session): session opened for user divernick by (uid=0)
Feb  4 20:12:27 linuxdesktop systemd-logind[876]: New session c2 of user divernick.
Feb  4 20:12:30 linuxdesktop xrdp-sesman[13252]: pam_unix(xrdp-sesman:session): session closed for user divernick
Feb  4 20:12:37 linuxdesktop systemd-logind[876]: Removed session c2.


The following is the corresponding data from xrdp.log
> [20190204-20:12:26] [DEBUG] xrdp_wm_log_msg: connecting to sesman ip 127.0.0.1 port 3350
[20190204-20:12:27] [INFO ] xrdp_wm_log_msg: sesman connect ok
[20190204-20:12:27] [DEBUG] xrdp_wm_log_msg: sending login info to session manager, please wait...
[20190204-20:12:27] [DEBUG] return value from xrdp_mm_connect 0
[20190204-20:12:27] [INFO ] xrdp_wm_log_msg: login successful for display 10
[20190204-20:12:27] [DEBUG] xrdp_wm_log_msg: started connecting
[20190204-20:12:27] [INFO ] lib_mod_log_peer: xrdp_pid=13251 connected to X11rdp_pid=13254 X11rdp_uid=1001 X11rdp_gid=1001 client_ip=::ffff:10.1.1.90 client_port=7548
[20190204-20:12:27] [DEBUG] xrdp_wm_log_msg: connected ok
[20190204-20:12:27] [DEBUG] xrdp_mm_connect_chansrv: chansrv connect successful
[20190204-20:12:27] [DEBUG] Closed socket 16 (AF_INET6 ::1 port 41062)
[20190204-20:12:27] [INFO ] The following channel is allowed: rdpdr (0)
[20190204-20:12:27] [INFO ] The following channel is allowed: rdpsnd (1)
[20190204-20:12:27] [INFO ] The following channel is allowed: cliprdr (2)
[20190204-20:12:27] [INFO ] The following channel is allowed: drdynvc (3)
[20190204-20:12:27] [DEBUG] The allow channel list now initialized for this session
[20190204-20:12:30] [DEBUG] Closed socket 18 (AF_UNIX)
[20190204-20:12:30] [DEBUG] Closed socket 12 (AF_INET6 ::ffff:10.1.1.101 port 3389)
[20190204-20:12:30] [DEBUG] xrdp_mm_module_cleanup
[20190204-20:12:30] [DEBUG] Closed socket 17 (AF_UNIX)


I have used pam-auth-update to verify enabled options which like stated above, everything works accept for LDAP users via xRDP.  Local users work vix xRDP and LDAP users work through all other means.

I've compared my nsswitch.conf and all looks like I can find through my searches.  
> # /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


# pre_auth-client-config # passwd:         compat systemd
passwd: files ldap
# pre_auth-client-config # group:          compat systemd
group: files ldap
# pre_auth-client-config # shadow:         compat
shadow: files ldap
gshadow:        files


hosts:          files mdns4_minimal [NOTFOUND=return] dns
networks:       files


protocols:      db files
services:       db files ldap
ethers:         db files
rpc:            db files


# pre_auth-client-config # netgroup:       nis
netgroup: nis



The only thing I have found with any promise is perhaps I should have sssd installed but when I do it installs but not without an error reported and post LDAP authentication no longer works at all.  I haven't been able to figure out it's install issue either.

---

