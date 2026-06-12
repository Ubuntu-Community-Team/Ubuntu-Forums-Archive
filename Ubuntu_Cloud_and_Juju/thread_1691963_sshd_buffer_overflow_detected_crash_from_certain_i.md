---
title: "sshd buffer overflow detected crash from certain ip addresses"
date: 2011-02-20
forum: Ubuntu Cloud and Juju
---

### Post by Berend de Boer on 2011-02-20
Hi All,

On Amazon EC2 sshd crashes for logins from certain IP addresses. Situation:

I've sshd setup to allow password logins, i.e. in /etc/ssh/sshd_config I have:

  PasswordAuthentication yes

I can login from some ip addresses, but not others. This is a failed attempt (same user name), with sshd started on port 1090:

```
$ /usr/sbin/sshd -d -p 1090 -f /etc/ssh/sshd_config
```The main thing is this message below:

```
*** buffer overflow detected ***: sshd: berend [priv] terminated
```Here the full details:

```
debug1: sshd version OpenSSH_5.3p1 Debian-3ubuntu5
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: rexec_argv[2]='-p'
debug1: rexec_argv[3]='1090'
debug1: rexec_argv[4]='-f'
debug1: rexec_argv[5]='/etc/ssh/sshd_config'
debug1: Bind to port 1090 on 0.0.0.0.
Server listening on 0.0.0.0 port 1090.
debug1: Bind to port 1090 on ::.
Server listening on :: port 1090.
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
debug1: inetd sockets after dupping: 3, 3
Connection from 124.198.140.142 port 58881
debug1: Client protocol version 2.0; client software version OpenSSH_5.5p1 Debian-4ubuntu5
debug1: match: OpenSSH_5.5p1 Debian-4ubuntu5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu5
debug1: permanently_set_uid: 104/65534
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user berend service ssh-connection method none
debug1: attempt 0 failures 0
debug1: PAM: initializing for "berend"
debug1: PAM: setting PAM_RHOST to "124-198-140-142.dynamic.dsl.maxnet.co.nz"
debug1: PAM: setting PAM_TTY to "ssh"
Failed none for berend from 124.198.140.142 port 58881 ssh2
debug1: userauth-request for user berend service ssh-connection method password
debug1: attempt 1 failures 0
*** buffer overflow detected ***: sshd: berend [priv] terminated
======= Backtrace: =========
/lib/tls/i686/nosegneg/libc.so.6(__fortify_fail+0x50)[0xb7501320]
/lib/tls/i686/nosegneg/libc.so.6(+0xe421a)[0xb750021a]
/lib/tls/i686/nosegneg/libc.so.6(+0xe3958)[0xb74ff958]
/lib/tls/i686/nosegneg/libc.so.6(_IO_default_xsputn+0x9e)[0xb748685e]
/lib/tls/i686/nosegneg/libc.so.6(_IO_vfprintf+0xe34)[0xb7459eb4]
/lib/tls/i686/nosegneg/libc.so.6(__vsprintf_chk+0xad)[0xb74ffa0d]
/lib/tls/i686/nosegneg/libc.so.6(__sprintf_chk+0x2d)[0xb74ff94d]
/lib/security/pam_pgsql.so(pg_execParam+0xac)[0xb78318dc]
/lib/security/pam_pgsql.so(backend_authenticate+0x69)[0xb7832199]
/lib/security/pam_pgsql.so(pam_sm_authenticate+0x1b3)[0xb782f8f3]
/lib/libpam.so.0(+0x26ad)[0xb781a6ad]
/lib/libpam.so.0(pam_authenticate+0x4d)[0xb7819ebd]
sshd: berend [priv](+0x2bcd6)[0xb7884cd6]
sshd: berend [priv](+0xd13f)[0xb786613f]
sshd: berend [priv](+0x225f2)[0xb787b5f2]
sshd: berend [priv](+0x22daa)[0xb787bdaa]
sshd: berend [priv](+0x23779)[0xb787c779]
sshd: berend [priv](main+0x2761)[0xb7864e61]
/lib/tls/i686/nosegneg/libc.so.6(__libc_start_main+0xe6)[0xb7432bd6]
sshd: berend [priv](+0x8021)[0xb7861021]
======= Memory map: ========
b6e4f000-b6e6c000 r-xp 00000000 08:01 17215334   /lib/libgcc_s.so.1
b6e6c000-b6e6d000 r--p 0001c000 08:01 17215334   /lib/libgcc_s.so.1
b6e6d000-b6e6e000 rw-p 0001d000 08:01 17215334   /lib/libgcc_s.so.1
b6e6e000-b6e72000 r-xp 00000000 08:01 17068672   /lib/libnss_pgsql.so.2.0.0
b6e72000-b6e73000 r--p 00003000 08:01 17068672   /lib/libnss_pgsql.so.2.0.0
b6e73000-b6e74000 rw-p 00004000 08:01 17068672   /lib/libnss_pgsql.so.2.0.0
b6e74000-b6e7a000 r-xp 00000000 08:01 51648832   /usr/lib/libcrack.so.2.8.1
b6e7a000-b6e7b000 r--p 00006000 08:01 51648832   /usr/lib/libcrack.so.2.8.1
b6e7b000-b6e7c000 rw-p 00007000 08:01 51648832   /usr/lib/libcrack.so.2.8.1
b6e7c000-b6e7f000 rw-p 00000000 00:00 0 
b6e88000-b6e8b000 r-xp 00000000 08:01 34566689   /lib/security/pam_cracklib.so
b6e8b000-b6e8c000 r--p 00002000 08:01 34566689   /lib/security/pam_cracklib.so
b6e8c000-b6e8d000 rw-p 00003000 08:01 34566689   /lib/security/pam_cracklib.so
b6e8d000-b6e91000 r-xp 00000000 08:01 34016968   /lib/security/pam_limits.so
b6e91000-b6e92000 r--p 00003000 08:01 34016968   /lib/security/pam_limits.so
b6e92000-b6e93000 rw-p 00004000 08:01 34016968   /lib/security/pam_limits.so
b6e93000-b6e9a000 r-xp 00000000 08:01 16813134   /lib/tls/i686/nosegneg/librt-2.11.1.so
b6e9a000-b6e9b000 r--p 00006000 08:01 16813134   /lib/tls/i686/nosegneg/librt-2.11.1.so
b6e9b000-b6e9c000 rw-p 00007000 08:01 16813134   /lib/tls/i686/nosegneg/librt-2.11.1.so
b6e9c000-b6ed3000 r-xp 00000000 08:01 17241254   /lib/libdbus-1.so.3.4.0
b6ed3000-b6ed4000 r--p 00036000 08:01 17241254   /lib/libdbus-1.so.3.4.0
b6ed4000-b6ed5000 rw-p 00037000 08:01 17241254   /lib/libdbus-1.so.3.4.0
b6ed5000-b6ed7000 r-xp 00000000 08:01 51637386   /usr/lib/libck-connector.so.0.0.0
b6ed7000-b6ed8000 ---p 00002000 08:01 51637386   /usr/lib/libck-connector.so.0.0.0
b6ed8000-b6ed9000 r--p 00002000 08:01 51637386   /usr/lib/libck-connector.so.0.0.0
b6ed9000-b6eda000 rw-p 00003000 08:01 51637386   /usr/lib/libck-connector.so.0.0.0
b6edb000-b6edd000 r-xp 00000000 08:01 34016959   /lib/security/pam_mail.so
b6edd000-b6ede000 r--p 00001000 08:01 34016959   /lib/security/pam_mail.so
b6ede000-b6edf000 rw-p 00002000 08:01 34016959   /lib/security/pam_mail.so
b6edf000-b6ee1000 r-xp 00000000 08:01 34016964   /lib/security/pam_motd.so
b6ee1000-b6ee2000 r--p 00001000 08:01 34016964   /lib/security/pam_motd.so
b6ee2000-b6ee3000 rw-p 00002000 08:01 34016964   /lib/security/pam_motd.so
b6ee3000-b6ee5000 r-xp 00000000 08:01 33597025   /lib/security/pam_ck_connector.so
b6ee5000-b6ee6000 r--p 00001000 08:01 33597025   /lib/security/pam_ck_connector.so
b6ee6000-b6ee7000 rw-p 00002000 08:01 33597025   /lib/security/pam_ck_connector.so
b6ee7000-b6eea000 r-xp 00000000 08:01 17215332   /lib/libgpg-error.so.0.4.0
b6eea000-b6eeb000 r--p 00002000 08:01 17215332   /lib/libgpg-error.so.0.4.0
b6eeb000-b6eec000 rw-p 00003000 08:01 17215332   /lib/libgpg-error.so.0.4.0
b6eec000-b6f5c000 r-xp 00000000 08:01 17031231   /lib/libgcrypt.so.11.5.2
b6f5c000-b6f5d000 r--p 00070000 08:01 17031231   /lib/libgcrypt.so.11.5.2
b6f5d000-b6f5f000 rw-p 00071000 08:01 17031231   /lib/libgcrypt.so.11.5.2
b6f5f000-b6f6e000 r-xp 00000000 08:01 50331789   /usr/lib/libtasn1.so.3.1.7
b6f6e000-b6f6f000 r--p 0000e000 08:01 50331789   /usr/lib/libtasn1.so.3.1.7
b6f6f000-b6f70000 rw-p 0000f000 08:01 50331789   /usr/lib/libtasn1.so.3.1.7
b6f70000-b7006000 r-xp 00000000 08:01 50332370   /usr/lib/libgnutls.so.26.14.12
b7006000-b700a000 r--p 00095000 08:01 50332370   /usr/lib/libgnutls.so.26.14.12
b700a000-b700b000 rw-p 00099000 08:01 50332370   /usr/lib/libgnutls.so.26.14.12
b700b000-b7021000 r-xp 00000000 08:01 50331792   /usr/lib/libsasl2.so.2.0.23
b7021000-b7022000 r--p 00015000 08:01 50331792   /usr/lib/libsasl2.so.2.0.23
b7022000-b7023000 rw-p 00016000 08:01 50331792   /usr/lib/libsasl2.so.2.0.23
b7023000-b702e000 r-xp 00000000 08:01 50332673   /usr/lib/liblber-2.4.so.2.5.4
b702e000-b702f000 r--p 0000a000 08:01 50332673   /usr/lib/liblber-2.4.so.2.5.4
b702f000-b7030000 rw-p 0000b000 08:01 50332673   /usr/lib/liblber-2.4.so.2.5.4
b7030000-b7074000 r-xp 00000000 08:01 50331818   /usr/lib/libldap_r-2.4.so.2.5.4
b7074000-b7075000 r--p 00043000 08:01 50331818   /usr/lib/libldap_r-2.4.so.2.5.4
b7075000-b7076000 rw-p 00044000 08:01 50331818   /usr/lib/libldap_r-2.4.so.2.5.4
b7076000-b7077000 rw-p 00000000 00:00 0 
b7077000-b70bb000 r-xp 00000000 08:01 33784538   /lib/i686/cmov/libssl.so.0.9.8
b70bb000-b70bc000 r--p 00044000 08:01 33784538   /lib/i686/cmov/libssl.so.0.9.8
b70bc000-b70bf000 rw-p 00045000 08:01 33784538   /lib/i686/cmov/libssl.so.0.9.8
b70bf000-b70c1000 r-xp 00000000 08:01 17215697   /lib/libpam_misc.so.0.82.0
b70c1000-b70c2000 r--p 00001000 08:01 17215697   /lib/libpam_misc.so.0.82.0
b70c2000-b70c3000 rw-p 00002000 08:01 17215697   /lib/libpam_misc.so.0.82.0
b70c3000-b70e4000 r-xp 00000000 08:01 50389190   /usr/lib/libpq.so.5.2
b70e4000-b70e5000 r--p 00020000 08:01 50389190   /usr/lib/libpq.so.5.2
b70e5000-b70e6000 rw-p 00021000 08:01 50389190   /usr/lib/libpq.so.5.2
b70e6000-b70e7000 r-xp 00000000 08:01 34016973   /lib/security/pam_nologin.so
b70e7000-b70e8000 r--p 00000000 08:01 34016973   /lib/security/pam_nologin.so
b70e8000-b70e9000 rw-p 00001000 08:01 34016973   /lib/security/pam_nologin.so
b70e9000-b70ea000 r-xp 00000000 08:01 34016949   /lib/security/pam_permit.so
b70ea000-b70eb000 r--p 00000000 08:01 34016949   /lib/security/pam_permit.so
b70eb000-b70ec000 rw-p 00001000 08:01 34016949   /lib/security/pam_permit.so
b70ec000-b70ed000 r-xp 00000000 08:01 34016974   /lib/security/pam_deny.so
b70ed000-b70ee000 r--p 00000000 08:01 34016974   /lib/security/pam_deny.so
b70ee000-b70ef000 rw-p 00001000 08:01 34016974   /lib/security/pam_deny.sodebug1: do_cleanup
Aborted
```Here is a correct login, same name, just connecting from a different ip address:

```
# /usr/sbin/sshd -d -p 1090 -f /etc/ssh/sshd_config
debug1: sshd version OpenSSH_5.3p1 Debian-3ubuntu5
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: rexec_argv[2]='-p'
debug1: rexec_argv[3]='1090'
debug1: rexec_argv[4]='-f'
debug1: rexec_argv[5]='/etc/ssh/sshd_config'
debug1: Bind to port 1090 on 0.0.0.0.
Server listening on 0.0.0.0 port 1090.
debug1: Bind to port 1090 on ::.
Server listening on :: port 1090.
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
debug1: inetd sockets after dupping: 3, 3
Connection from 50.17.251.129 port 50786
debug1: Client protocol version 2.0; client software version OpenSSH_5.3p1 Debian-3ubuntu5
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu5
debug1: permanently_set_uid: 104/65534
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user berend service ssh-connection method none
debug1: attempt 0 failures 0
Address 50.17.251.129 maps to smtp3.xplainhosting.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
debug1: PAM: initializing for "berend"
debug1: PAM: setting PAM_RHOST to "50.17.251.129"
debug1: PAM: setting PAM_TTY to "ssh"
Failed none for berend from 50.17.251.129 port 50786 ssh2
debug1: userauth-request for user berend service ssh-connection method password
debug1: attempt 1 failures 0
debug1: PAM: password authentication accepted for berend
debug1: do_pam_account: called
Accepted password for berend from 50.17.251.129 port 50786 ssh2
debug1: monitor_child_preauth: berend has been authenticated by privileged process
debug1: PAM: establishing credentials
User child is on pid 22181
debug1: SELinux support disabled
debug1: PAM: establishing credentials
debug1: permanently_set_uid: 1002/1001
debug1: Entering interactive session for SSH2.
debug1: server_init_dispatch_20
debug1: server_input_channel_open: ctype session rchan 0 win 1048576 max 16384
debug1: input_session_request
debug1: channel 0: new [server-session]
debug1: session_new: session 0
debug1: session_open: channel 0
debug1: session_open: session 0: link with channel 0
debug1: server_input_channel_open: confirm session
debug1: server_input_global_request: rtype no-more-sessions@openssh.com want_reply 0
debug1: server_input_channel_req: channel 0 request pty-req reply 1
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req pty-req
debug1: Allocating pty.
debug1: session_new: session 0
debug1: SELinux support disabled
debug1: session_pty_req: session 0 alloc /dev/pts/2
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request shell reply 1
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req shell
debug1: Setting controlling tty using TIOCSCTTY.

```I'm truly baffled what is happening here. This is also a new  development, not sure exactly when it started, but somewhere along the  Ubuntu 10.04 AMI updates, possibly in the last 2 months or so.

The crash only happens from certain ip addresses. I can always login  when using a key, crashes only happen when I request that a password is  to be typed in.

Every pointer appreciated.                 

Thanks,

Berend.

---

### Post by kim0 on 2011-02-20
Hi,
This looks like a definite bug to me, and perhaps an important one as well. Please open a bug report at 

[https://bugs.launchpad.net/ubuntu/+source/openssh/](https://bugs.launchpad.net/ubuntu/+source/openssh/)

Attach all logs and traces, and please mark it as a "security bug"

Thanks

---

