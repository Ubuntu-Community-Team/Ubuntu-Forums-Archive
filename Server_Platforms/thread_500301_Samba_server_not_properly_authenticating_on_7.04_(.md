---
title: "Samba server not properly authenticating on 7.04 (feisty)"
date: 2007-07-13
forum: Server Platforms
---

### Post by ZephyrXero on 2007-07-13
I'm having trouble getting my new samba based fileserver to accept any name/password to log onto it. The problem seems to be directly related to this as Windows machines can see the computer and it's shares listed properly and I can ssh from my Linux workstation to it, but whenever a Windows machine tries to mount the shared drive it either times out or flat out rejects it.

I've tried this with three different names and passwords, multiple times so it's safe to rule a typing error out. This machine is brand new and built to replace an already existing fileserver with practically the same exact setup. The only real difference is that the old machine is running Xubuntu 6.10, and this one is running 7.04. This also should not be a problem as I just recently built a similar machine to be used as a fileserver for a client and it was running 7.04 too. The version of Samba installed is 3.0.24-2ubuntu1. The only other real difference is that the old machine is using a single hard drive, and the new one is using LVM with two drives.

Here are some of the error logs I'm getting...

/var/log/samba/log.smbd:

```

[2007/07/09 16:26:16, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
  
  [2007/07/10 09:48:11, 0] lib/util_sock.c:get_peer_addr(1229)
  getpeername failed. Error was Transport endpoint is not connected
  
 [2007/07/13 06:27:37, 5] lib/debug.c:debug_dump_status(391)
  INFO: Current debug levels:
    all: True/10
    tdb: False/0
    printdrivers: False/0
    lanman: False/0
    smb: False/0
    rpc_parse: False/0
    rpc_srv: False/0
    rpc_cli: False/0
    passdb: False/0
    sam: False/0
    auth: False/0
    winbind: False/0
    vfs: False/0
    idmap: False/0
    quota: False/0
    acls: False/0
    locking: False/0
    msdfs: False/0
    dmapi: False/0
[2007/07/13 06:27:37, 3] lib/fault.c:dump_core_setup(134)
  Maximum core file size limits now 16777216(soft) -1(hard)
[2007/07/13 06:27:37, 3] smbd/sec_ctx.c:get_current_groups(168)
  get_current_groups: user is in 1 groups: 0
[2007/07/13 06:27:37, 0] smbd/server.c:main(847)
  smbd version 3.0.24 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/07/13 06:27:37, 2] smbd/server.c:main(851)
  uid=0 gid=0 euid=0 egid=0
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  Build environment:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     Built by:    buildd@terranova
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     Built on:    Tue May 22 17:45:42 UTC 2007
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     Built using: gcc
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     Build host:  Linux terranova 2.6.15.7 #1 SMP Sat Sep 30 10:21:42 UTC 2006 i686 GNU/Linux
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SRCDIR:      /build/buildd/samba-3.0.24/source
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     BUILDDIR:    /build/buildd/samba-3.0.24/source
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
  Paths:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SBINDIR: /usr/sbin
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     BINDIR: /usr/bin
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SWATDIR: /usr/share/samba/swat
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     CONFIGFILE: /etc/samba/smb.conf
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     LOGFILEBASE: /var/log/samba
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     LMHOSTSFILE: /etc/samba/lmhosts
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     LIBDIR: /usr/lib/samba
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SHLIBEXT: so
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     LOCKDIR: /var/run/samba
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     PIDDIR: /var/run/samba
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SMB_PASSWD_FILE: /etc/samba/smbpasswd
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     PRIVATE_DIR: /etc/samba
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
   System Headers:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_ACL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_CDEFS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_FCNTL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_IOCTL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_IPC_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_MMAN_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_MOUNT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_PARAM_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_PRCTL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_QUOTA_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_RESOURCE_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_SELECT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_SHM_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_SOCKET_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_STATFS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_STATVFS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_STAT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_SYSCALL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_SYSLOG_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_SYSMACROS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_TIME_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_TYPES_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_UIO_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_UNISTD_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_UN_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_VFS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_WAIT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_XATTR_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
   Headers:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_AIO_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ALLOCA_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ARPA_INET_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ASM_TYPES_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ATTR_XATTR_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_COM_ERR_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_CTYPE_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DIRENT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DLFCN_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_EXECINFO_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FCNTL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FLOAT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GLOB_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GRP_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GSSAPI_GSSAPI_GENERIC_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GSSAPI_GSSAPI_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_INTTYPES_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LANGINFO_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LASTLOG_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LBER_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LDAP_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIMITS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LOCALE_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MEMORY_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MNTENT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NETINET_IN_SYSTM_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NETINET_IP_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NETINET_TCP_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NET_IF_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NSS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_POLL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_READLINE_HISTORY_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_READLINE_READLINE_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_RPCSVC_NIS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_RPCSVC_YPCLNT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_RPCSVC_YP_PROT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_RPC_RPC_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SECURITY_PAM_APPL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SECURITY_PAM_MODULES_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SECURITY__PAM_MACROS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SHADOW_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STDARG_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STDINT_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STDLIB_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRINGS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRING_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STROPTS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYSCALL_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYSLOG_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_TERMIOS_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_TERMIO_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UNISTD_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UTIME_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
   UTMP Options:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETUTMPX
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UTMPX_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UTMP_H
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_ADDR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_EXIT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_HOST
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_ID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_NAME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_PID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_TIME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_TV
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_TYPE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UT_UT_USER
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     PUTUTLINE_RETURNS_UTMP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_UTMP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
   HAVE_* Defines:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ADDRTYPE_IN_KRB5_ADDRESS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_AP_OPTS_USE_SUBKEY
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ASPRINTF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ASPRINTF_DECL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ATEXIT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_BACKTRACE_SYMBOLS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_BER_SCANF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_C99_VSNPRINTF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_CHMOD
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_CHOWN
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_CHROOT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_COMPILER_WILL_OPTIMIZE_OUT_FNS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_CONNECT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_CREAT64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_CRYPT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_CUPS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DECODE_KRB5_AP_REQ
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DEVICE_MAJOR_FN
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DEVICE_MINOR_FN
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DIRENT_D_OFF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DLCLOSE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DLERROR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DLOPEN
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DLSYM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_DUP2
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ENDMNTENT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ENDNETGRENT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ERRNO_DECL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_EXECL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_EXPLICIT_LARGEFILE_SUPPORT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FCHMOD
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FCHOWN
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FCNTL_LOCK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FCVT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FGETXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FLISTXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FOPEN64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FREMOVEXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FSEEKO64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FSETXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FSTAT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FSTAT64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FSYNC
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FTELLO64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FTRUNCATE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FTRUNCATE64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FTRUNCATE_EXTEND
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_FUNCTION_MACRO
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETCWD
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETDIRENTRIES
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETGRENT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETGRNAM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETGROUPLIST
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETMNTENT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETNETGRENT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETRLIMIT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETSPNAM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETTIMEOFDAY_TZ
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GETXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GLOB
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GRANTPT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GSSAPI
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_GSS_DISPLAY_STATUS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ICONV
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_IFACE_IFCONF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_IMMEDIATE_STRUCTURES
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_INITGROUPS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_INNETGR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_IPRINT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KERNEL_CHANGE_NOTIFY
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KERNEL_OPLOCKS_LINUX
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KERNEL_SHARE_MODES
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_AUTH_CON_SETUSERUSERKEY
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_C_ENCTYPE_COMPARE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_C_VERIFY_CHECKSUM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_ENCRYPT_BLOCK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_ENCRYPT_DATA
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_FREE_AP_REQ
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_FREE_DATA_CONTENTS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_FREE_KEYTAB_ENTRY_CONTENTS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_FREE_KTYPES
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_FREE_UNPARSED_NAME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_GET_PERMITTED_ENCTYPES
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_GET_RENEWED_CREDS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_KEYBLOCK_IN_CREDS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_KEYTAB_ENTRY_KEY
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_KEYUSAGE_APP_DATA_CKSUM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_KT_FREE_ENTRY
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_LOCATE_KDC
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_MK_REQ_EXTENDED
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_PRINCIPAL2SALT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_PRINC_COMPONENT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_SET_DEFAULT_TGS_KTYPES
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_SET_REAL_TIME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_STRING_TO_KEY
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_TKT_ENC_PART2
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KRB5_USE_ENCTYPE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_KV5M_KEYTAB
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LDAP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LDAP_ADD_RESULT_ENTRY
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LDAP_DN2AD_CANONICAL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LDAP_INIT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LDAP_INITIALIZE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LDAP_SET_REBIND_PROC
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LGETXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBCOM_ERR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBGSSAPI_KRB5
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBK5CRYPTO
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBKRB5
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBLBER
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBLDAP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBPAM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBREADLINE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LIBRESOLV
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LINK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LINUX_XFS_QUOTAS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LISTXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LLISTXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LLSEEK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LONGLONG
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LREMOVEXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LSEEK64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LSETXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_LSTAT64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MAGIC_IN_KRB5_ADDRESS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MAKEDEV
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MEMMOVE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MEMSET
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MKNOD
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MKTIME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MLOCK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MLOCKALL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MMAP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MUNLOCK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_MUNLOCKALL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NANOSLEEP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NATIVE_ICONV
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NEW_LIBREADLINE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NL_LANGINFO
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_NO_AIO
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_OPEN64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PATHCONF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PIPE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_POLL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_POSIX_ACLS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PRCTL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PREAD
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PREAD64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PUTUTLINE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PUTUTXLINE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PWRITE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_PWRITE64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_QUOTACTL_LINUX
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_RAND
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_RANDOM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_READDIR64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_READLINK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_REALPATH
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_REMOVEXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_RENAME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SECURE_MKSTEMP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SELECT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SENDFILE64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETBUFFER
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETENV
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETGROUPS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETLINEBUF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETLOCALE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETMNTENT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETNETGRENT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETPGID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETRESGID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETRESGID_DECL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETRESUID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETRESUID_DECL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETSID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SETXATTR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SHMGET
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SIGACTION
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SIGBLOCK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SIGPROCMASK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SIGSET
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SIG_ATOMIC_T_TYPE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SNPRINTF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SNPRINTF_DECL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SOCKLEN_T_TYPE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SRAND
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SRANDOM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STAT64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STAT_HIRES_TIMESTAMPS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STAT_ST_ATIM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STAT_ST_BLKSIZE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STAT_ST_BLOCKS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STAT_ST_CTIM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STAT_ST_MTIM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRCASECMP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRCHR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRDUP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRERROR
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRFTIME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRNDUP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRNLEN
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRPBRK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRSIGNAL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRTOUL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRUCT_DIRENT64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRUCT_FLOCK64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRUCT_STAT_ST_RDEV
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_STRUCT_TIMESPEC
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_ST_RDEV
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYMLINK
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYSCALL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYSCONF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYSLOG
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_SYS_QUOTAS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_TICKET_POINTER_IN_KRB5_AP_REQ
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_TIMEGM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UNIXSOCKET
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UPDWTMP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UPDWTMPX
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_USLEEP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UTIMBUF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UTIME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_UTIMES
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_VASPRINTF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_VASPRINTF_DECL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_VA_COPY
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_VOLATILE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_VSNPRINTF
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_VSNPRINTF_DECL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_VSYSLOG
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_WAITPID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_WORKING_AF_LOCAL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_WRFILE_KEYTAB
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_XFS_QUOTAS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE_YP_GET_DEFAULT_DOMAIN
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     HAVE__ET_LIST
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
   --with Options:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_ADS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_AUTOMOUNT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_CIFSMOUNT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_PAM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_QUOTAS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_SENDFILE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_SMBMOUNT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_SYSLOG
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_UTMP
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_WINBIND
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
   Build Options:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     COMPILER_SUPPORTS_LL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     DEFAULT_DISPLAY_CHARSET
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     DEFAULT_DOS_CHARSET
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     DEFAULT_UNIX_CHARSET
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     FHS_COMPATIBLE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     KRB5_VERIFY_CHECKSUM_ARGS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     LDAP_SET_REBIND_PROC_ARGS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     LINUX
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     LINUX_SENDFILE_API
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     PACKAGE_BUGREPORT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     PACKAGE_NAME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     PACKAGE_STRING
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     PACKAGE_TARNAME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     PACKAGE_VERSION
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     REALPATH_TAKES_NULL
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     REPLACE_GETPASS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     RETSIGTYPE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SEEKDIR_RETURNS_VOID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SIZEOF_DEV_T
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SIZEOF_INO_T
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SIZEOF_INT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SIZEOF_LONG
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SIZEOF_LONG_LONG
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SIZEOF_OFF_T
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SIZEOF_SHORT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     STAT_STATVFS64
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     STAT_ST_BLOCKSIZE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     STDC_HEADERS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     STRING_STATIC_MODULES
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SYSCONF_SC_NGROUPS_MAX
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SYSCONF_SC_NPROCESSORS_ONLN
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     SYSCONF_SC_PAGESIZE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     TIME_WITH_SYS_TIME
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     USE_SETRESUID
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_ADS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_AUTOMOUNT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_CIFSMOUNT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_PAM
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_QUOTAS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_SENDFILE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_SMBMOUNT
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_SYSLOG
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     WITH_WINBIND
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     _FILE_OFFSET_BITS
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     _GNU_SOURCE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     _LARGEFILE64_SOURCE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     _POSIX_C_SOURCE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     _POSIX_SOURCE
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     auth_script_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     charset_CP437_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     charset_CP850_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     idmap_ad_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     idmap_rid_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     offset_t
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_decl_auth
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_decl_charset
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_decl_idmap
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_decl_pdb
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_decl_rpc
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_decl_vfs
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_init_auth
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_init_charset
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_init_idmap
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_init_pdb
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_init_rpc
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     static_init_vfs
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_audit_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_cap_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_default_quota_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_expand_msdfs_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_extd_audit_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_fake_perms_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_full_audit_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_netatalk_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_readonly_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_recycle_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     vfs_shadow_copy_init
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
  Type sizes:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(char):         1
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(int):          4
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(long):         4
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(long long):    8
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(uint8):        1
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(uint16):       2
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(uint32):       4
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(short):        2
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(void*):        4
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(size_t):       4
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(off_t):        8
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(ino_t):        8
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
     sizeof(dev_t):        8
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
  
  Builtin modules:
[2007/07/13 06:27:37, 4] smbd/build_options.c:output(44)
      pdb_ldap pdb_smbpasswd pdb_tdbsam rpc_lsa rpc_reg rpc_lsa_ds rpc_wks rpc_svcctl rpc_ntsvcs rpc_net rpc_netdfs rpc_srv rpc_spoolss rpc_eventlog rpc_samr idmap_ldap idmap_tdb auth_sam auth_unix auth_winbind auth_server auth_domain auth_builtin
[2007/07/13 06:27:37, 3] param/loadparm.c:lp_load(4953)
  lp_load: refreshing parameters
[2007/07/13 06:27:37, 3] param/loadparm.c:init_globals(1418)
  Initialising global parameters
[2007/07/13 06:27:37, 3] param/params.c:pm_process(572)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2007/07/13 06:27:37, 3] param/loadparm.c:do_section(3695)
  Processing section "[global]"
  doing parameter workgroup = network
  doing parameter server string = %h server (Samba, Ubuntu)
  doing parameter dns proxy = no
  doing parameter log file = /var/log/samba/log.%m
  doing parameter max log size = 1000
  doing parameter syslog = 0
  doing parameter panic action = /usr/share/samba/panic-action %d
  doing parameter encrypt passwords = true
  doing parameter passdb backend = tdbsam
  doing parameter obey pam restrictions = yes
  doing parameter invalid users = root
  doing parameter passwd program = /usr/bin/passwd %u
  doing parameter passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
  doing parameter socket options = TCP_NODELAY
  doing parameter wins support = no
[2007/07/13 06:27:37, 2] param/loadparm.c:do_section(3712)
  Processing section "[printers]"
[2007/07/13 06:27:37, 8] param/loadparm.c:add_a_service(2503)
  add_a_service: Creating snum = 0 for printers
[2007/07/13 06:27:37, 10] param/loadparm.c:hash_a_service(2540)
  hash_a_service: creating tdb servicehash
[2007/07/13 06:27:37, 10] param/loadparm.c:hash_a_service(2550)
  hash_a_service: hashing index 0 for service name printers
  doing parameter comment = All Printers
  doing parameter browseable = no
  doing parameter path = /var/spool/samba
  doing parameter printable = yes
  doing parameter public = no
  doing parameter writable = no
  doing parameter create mode = 0700
[2007/07/13 06:27:37, 2] param/loadparm.c:do_section(3712)
  Processing section "[print$]"
[2007/07/13 06:27:37, 8] param/loadparm.c:add_a_service(2503)
  add_a_service: Creating snum = 1 for print$
[2007/07/13 06:27:37, 10] param/loadparm.c:hash_a_service(2550)
  hash_a_service: hashing index 1 for service name print$
  doing parameter comment = Printer Drivers
  doing parameter path = /var/lib/samba/printers
  doing parameter browseable = yes
  doing parameter read only = yes
  doing parameter guest ok = no
[2007/07/13 06:27:37, 2] param/loadparm.c:do_section(3712)
  Processing section "[data]"
[2007/07/13 06:27:37, 8] param/loadparm.c:add_a_service(2503)
  add_a_service: Creating snum = 2 for data
[2007/07/13 06:27:37, 10] param/loadparm.c:hash_a_service(2550)
  hash_a_service: hashing index 2 for service name data
  doing parameter path = /data
  doing parameter available = yes
  doing parameter browsable = yes
  doing parameter public = yes
  doing parameter writable = yes
[2007/07/13 06:27:37, 2] param/loadparm.c:do_section(3712)
  Processing section "[bams]"
[2007/07/13 06:27:37, 8] param/loadparm.c:add_a_service(2503)
  add_a_service: Creating snum = 3 for bams
[2007/07/13 06:27:37, 10] param/loadparm.c:hash_a_service(2550)
  hash_a_service: hashing index 3 for service name bams
  doing parameter path = /data/local/shared/BAMS
  doing parameter available = yes
  doing parameter browsable = yes
  doing parameter public = yes
  doing parameter writable = yes
[2007/07/13 06:27:37, 4] param/loadparm.c:lp_load(4984)
  pm_process() returned Yes
[2007/07/13 06:27:37, 7] param/loadparm.c:lp_servicenumber(5120)
  lp_servicenumber: couldn't find homes
[2007/07/13 06:27:37, 8] param/loadparm.c:add_a_service(2503)
  add_a_service: Creating snum = 4 for IPC$
[2007/07/13 06:27:37, 10] param/loadparm.c:hash_a_service(2550)
  hash_a_service: hashing index 4 for service name IPC$
[2007/07/13 06:27:37, 3] param/loadparm.c:lp_add_ipc(2637)
  adding IPC service
[2007/07/13 06:27:37, 10] param/loadparm.c:set_server_role(4229)
  set_server_role: role = ROLE_STANDALONE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS-2LE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS-2LE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-16LE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-16LE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS-2BE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS-2BE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-16BE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-16BE
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF8
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF8
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-8
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-8
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset ASCII
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset ASCII
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset 646
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset 646
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset ISO-8859-1
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset ISO-8859-1
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS2-HEX
[2007/07/13 06:27:37, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS2-HEX
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 5] lib/charcnv.c:charset_name(81)
  Substituting charset 'UTF-8' for LOCALE
[2007/07/13 06:27:37, 3] printing/pcap.c:pcap_cache_reload(117)
  reloading printcap cache
[2007/07/13 06:27:37, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2007/07/13 06:27:37, 3] printing/pcap.c:pcap_cache_reload(223)
  reload status: error
[2007/07/13 06:27:37, 3] printing/pcap.c:pcap_cache_reload(117)
  reloading printcap cache
[2007/07/13 06:27:37, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2007/07/13 06:27:37, 3] printing/pcap.c:pcap_cache_reload(223)
  reload status: error
[2007/07/13 06:27:37, 6] param/loadparm.c:lp_file_list_changed(3006)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Fri Jul 13 05:30:28 2007
  
[2007/07/13 06:27:37, 2] lib/interface.c:add_interface(81)
  added interface ip=192.168.1.55 bcast=192.168.1.255 nmask=255.255.255.0
[2007/07/13 06:27:37, 5] lib/util.c:init_names(286)
  Netbios name list:-
  my_netbios_names[0]="SOMETHINGELSE"
[2007/07/13 06:27:37, 3] smbd/server.c:main(877)
  loaded services
[2007/07/13 06:27:37, 0] smbd/server.c:main(881)
  standard input is not a socket, assuming -D option
[2007/07/13 06:27:37, 3] smbd/server.c:main(892)
  Becoming a daemon.
[2007/07/13 06:27:37, 8] lib/util.c:fcntl_lock(1959)
  fcntl_lock fd=6 op=13 offset=0 count=1 type=0
[2007/07/13 06:27:37, 3] lib/util.c:fcntl_lock(1972)
  fcntl_lock: lock failed at offset 0 count 1 op 13 type 0 (Resource temporarily unavailable)
[2007/07/13 06:27:37, 0] /build/buildd/samba-3.0.24/source/lib/pidfile.c:pidfile_create(104)
  ERROR: smbd is already running. File /var/run/samba/smbd.pid exists and process id 4752 is running.
[2007/07/13 06:29:20, 0] lib/util_sock.c:get_peer_addr(1229)
  getpeername failed. Error was Transport endpoint is not connected
[2007/07/13 06:33:17, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2007/07/13 06:33:17, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!

```

/var/log/samba/log.<client-hostname>:

```

[2007/07/13 05:43:43, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2007/07/13 05:43:43, 0] lib/util_sock.c:send_smb(769)
  Error writing 4 bytes to client. -1. (Connection reset by peer)

```

I really need to get this machine going soon, so any help or ideas are much appreciated...thanks!

***PS:** Usually I can just copy and paste error codes like these into Google or the forums here and find a solution, but Google actually came up with no results, and I haven't found anyone with similar problems on the boards either...*

---

### Post by ZephyrXero on 2007-07-16
no ideas.... anyone? :confused:

---

### Post by Gruelius on 2007-07-16
Well the conection is being reset by the peer so it may not be samba's fault.

Do you mind posting your smb.conf? and are the users in /etc/passwd? or just in smbusers. And finally which OS are the client pc's using?

I hate samba but once it works its all sweet :D My conf file probably wont help as i have it set to use user mode and map all users to a guest account.

---

### Post by ZephyrXero on 2007-07-16
Yes, the users are in /etc/passwd.... like I said, I can login via SSH just fine with all the accounts.

99% of the clients will be running Windows XP.

Here's my smb.conf:
```

# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = network

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[data]
path = <no need for me to post this>
available = yes
browsable = yes
public = yes
writable = yes

[bams]
path = <no need for me to post this>
available = yes
browsable = yes
public = yes
writable = yes


```

Everything's set to default for the most part. I used the Shared Folders GUI that comes with Ubuntu to set it up. Like I said, I've done this same setup a few times before, and never had this problem in the past.

Also...with the reset by peer message, I considered it could be my OpenBSD router/firewall causing problems, but my PF configuration works just fine with the current fileServer I'm replacing, and there's nothing IP specific or anything in my ruleset...

I'm completely baffled at what the problem could be.

---

### Post by codmate on 2007-07-16
Firstly I would uncomment "security = user".
This may be the default anyway - but I'm not certain.

Secondly, since you are using encrypted passwords you may need to add users to the smbpasswd file.

Use the smbpasswd command to do this (surprisingly ;) )

To add a new user to smbpasswd I believe it is:

#smbpasswd -a username password

Also have a look in samba's log file.
Check /var/log/samba/log.%m

The %m stands for the machine that is connecting.
This way you will see a log for each machine that tries to connect  :)
There should also be a general log for each of nmbd and smbd.

Hope this helps.

---

### Post by ZephyrXero on 2007-07-16
I didn't even think about smbpasswd! Yep, that fixed it :)

I guess this is something new in the latest version of Samba (or at least Ubuntu's default settings)? I used to be able to just let it use the system's usernames and passwords...

---

### Post by Gruelius on 2007-07-16
its to do with the encryption settings you have. I didnt bother wtih encryption as its a home server and security isnt that much of an issue.

---

