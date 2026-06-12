---
title: "Problem with Samba between ubuntu server and windows 10 client"
date: 2019-05-16
forum: Server Platforms
---

### Post by unrealbe on 2019-05-16
Hello everyone,

I have some strange behavior on my samba shares that I can't figure out how to resolve it.
First some info about** my setup:**
[B] uname -a
[/B]```
Linux linuxserver 4.15.0-50-generic #54-Ubuntu SMP Mon May 6 18:46:08 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```
**  smbd -V**
```
Version 4.7.6-Ubuntu
```

[B]The issue:
[/B]After x minutes/hours my samba shares get unresponsive in my windows 10 client. I can only reacces them after a: sudo service smbd restart
In the logs I find these error messages at the same time:
**tail -50f /var/log/samba/log.smbd**
 ```
  #16 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #17 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #18 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_process+0x718) [0x7f076a281998]
   #19 /usr/sbin/smbd(+0xcfcc) [0x55b06c1d6fcc]
   #20 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x9ed0) [0x7f07671a0ed0]
   #21 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x8357) [0x7f076719f357]
   #22 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x9d) [0x7f076719b7cd]
   #23 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #24 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #25 /usr/sbin/smbd(main+0x1d0a) [0x55b06c1d234a]
   #26 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0x7f0766dc7b97]
   #27 /usr/sbin/smbd(_start+0x2a) [0x55b06c1d245a]
[2019/05/16 12:30:07.493357,  0] ../source3/lib/dumpcore.c:318(dump_core)
  coredump is handled by helper binary specified at /proc/sys/kernel/core_pattern[2019/05/16 12:30:08.469181,  0] ../source3/locking/share_mode_lock.c:439(share_mode_data_destructor)
  store returned NT_STATUS_UNSUCCESSFUL
[2019/05/16 12:30:08.469246,  0] ../source3/lib/util.c:815(smb_panic_s3)
  PANIC (pid 9477): could not store share mode entry: NT_STATUS_UNSUCCESSFUL
[2019/05/16 12:30:08.469720,  0] ../source3/lib/util.c:926(log_stack_trace)
  BACKTRACE: 28 stack frames:
   #0 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(log_stack_trace+0x1f) [0x7f076856e9cf]
   #1 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(smb_panic_s3+0x20) [0x7f076856eaa0]
   #2 /usr/lib/x86_64-linux-gnu/libsamba-util.so.0(smb_panic+0x2f) [0x7f076a6575af]
   #3 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x1d2e52) [0x7f076a2cee52]
   #4 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(+0xb1b4) [0x7f07675bd1b4]
   #5 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(+0xae10) [0x7f07675bce10]
   #6 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(_talloc_free+0xd8) [0x7f07675b58c8]
   #7 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x164ef7) [0x7f076a260ef7]
   #8 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x167e4a) [0x7f076a263e4a]
   #9 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(create_file_default+0x1ac) [0x7f076a265d0c]
   #10 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_smb2_request_process_create+0xd40) [0x7f076a298bf0]
   #11 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_smb2_request_dispatch+0xcef) [0x7f076a290fbf]
   #12 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x195b7c) [0x7f076a291b7c]
   #13 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x9ed0) [0x7f07671a0ed0]
   #14 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x8357) [0x7f076719f357]
   #15 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x9d) [0x7f076719b7cd]
   #16 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #17 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #18 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_process+0x718) [0x7f076a281998]
   #19 /usr/sbin/smbd(+0xcfcc) [0x55b06c1d6fcc]
   #20 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x9ed0) [0x7f07671a0ed0]
   #21 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x8357) [0x7f076719f357]
   #22 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x9d) [0x7f076719b7cd]
   #23 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #24 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #25 /usr/sbin/smbd(main+0x1d0a) [0x55b06c1d234a]
   #26 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0x7f0766dc7b97]
   #27 /usr/sbin/smbd(_start+0x2a) [0x55b06c1d245a]
[2019/05/16 12:30:08.469937,  0] ../source3/lib/dumpcore.c:318(dump_core)
  coredump is handled by helper binary specified at /proc/sys/kernel/core_pattern[2019/05/16 12:30:26.801590,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections
^C
tim@linuxserver:~$ clear
tim@linuxserver:~$ tail -80f /var/log/samba/log.smbd
   #21 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x8357) [0x7f076719f357]
   #22 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x9d) [0x7f076719b7cd]
   #23 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #24 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #25 /usr/sbin/smbd(main+0x1d0a) [0x55b06c1d234a]
   #26 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0x7f0766dc7b97]
   #27 /usr/sbin/smbd(_start+0x2a) [0x55b06c1d245a]
[2019/05/16 12:30:06.533716,  0] ../source3/lib/dumpcore.c:318(dump_core)
  coredump is handled by helper binary specified at /proc/sys/kernel/core_pattern[2019/05/16 12:30:07.492664,  0] ../source3/locking/share_mode_lock.c:439(share_mode_data_destructor)
  store returned NT_STATUS_UNSUCCESSFUL
[2019/05/16 12:30:07.492741,  0] ../source3/lib/util.c:815(smb_panic_s3)
  PANIC (pid 9475): could not store share mode entry: NT_STATUS_UNSUCCESSFUL
[2019/05/16 12:30:07.493157,  0] ../source3/lib/util.c:926(log_stack_trace)
  BACKTRACE: 28 stack frames:
   #0 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(log_stack_trace+0x1f) [0x7f076856e9cf]
   #1 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(smb_panic_s3+0x20) [0x7f076856eaa0]
   #2 /usr/lib/x86_64-linux-gnu/libsamba-util.so.0(smb_panic+0x2f) [0x7f076a6575af]
   #3 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x1d2e52) [0x7f076a2cee52]
   #4 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(+0xb1b4) [0x7f07675bd1b4]
   #5 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(+0xae10) [0x7f07675bce10]
   #6 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(_talloc_free+0xd8) [0x7f07675b58c8]
   #7 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x164ef7) [0x7f076a260ef7]
   #8 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x167e4a) [0x7f076a263e4a]
   #9 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(create_file_default+0x1ac) [0x7f076a265d0c]
   #10 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_smb2_request_process_create+0xd40) [0x7f076a298bf0]
   #11 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_smb2_request_dispatch+0xcef) [0x7f076a290fbf]
   #12 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x195b7c) [0x7f076a291b7c]
   #13 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x9ed0) [0x7f07671a0ed0]
   #14 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x8357) [0x7f076719f357]
   #15 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x9d) [0x7f076719b7cd]
   #16 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #17 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #18 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_process+0x718) [0x7f076a281998]
   #19 /usr/sbin/smbd(+0xcfcc) [0x55b06c1d6fcc]
   #20 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x9ed0) [0x7f07671a0ed0]
   #21 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x8357) [0x7f076719f357]
   #22 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x9d) [0x7f076719b7cd]
   #23 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #24 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #25 /usr/sbin/smbd(main+0x1d0a) [0x55b06c1d234a]
   #26 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0x7f0766dc7b97]
   #27 /usr/sbin/smbd(_start+0x2a) [0x55b06c1d245a]
[2019/05/16 12:30:07.493357,  0] ../source3/lib/dumpcore.c:318(dump_core)
  coredump is handled by helper binary specified at /proc/sys/kernel/core_pattern[2019/05/16 12:30:08.469181,  0] ../source3/locking/share_mode_lock.c:439(share_mode_data_destructor)
  store returned NT_STATUS_UNSUCCESSFUL
[2019/05/16 12:30:08.469246,  0] ../source3/lib/util.c:815(smb_panic_s3)
  PANIC (pid 9477): could not store share mode entry: NT_STATUS_UNSUCCESSFUL
[2019/05/16 12:30:08.469720,  0] ../source3/lib/util.c:926(log_stack_trace)
  BACKTRACE: 28 stack frames:
   #0 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(log_stack_trace+0x1f) [0x7f076856e9cf]
   #1 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(smb_panic_s3+0x20) [0x7f076856eaa0]
   #2 /usr/lib/x86_64-linux-gnu/libsamba-util.so.0(smb_panic+0x2f) [0x7f076a6575af]
   #3 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x1d2e52) [0x7f076a2cee52]
   #4 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(+0xb1b4) [0x7f07675bd1b4]
   #5 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(+0xae10) [0x7f07675bce10]
   #6 /usr/lib/x86_64-linux-gnu/libtalloc.so.2(_talloc_free+0xd8) [0x7f07675b58c8]
   #7 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x164ef7) [0x7f076a260ef7]
   #8 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x167e4a) [0x7f076a263e4a]
   #9 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(create_file_default+0x1ac) [0x7f076a265d0c]
   #10 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_smb2_request_process_create+0xd40) [0x7f076a298bf0]
   #11 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_smb2_request_dispatch+0xcef) [0x7f076a290fbf]
   #12 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(+0x195b7c) [0x7f076a291b7c]
   #13 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x9ed0) [0x7f07671a0ed0]
   #14 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x8357) [0x7f076719f357]
   #15 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x9d) [0x7f076719b7cd]
   #16 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #17 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #18 /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0(smbd_process+0x718) [0x7f076a281998]
   #19 /usr/sbin/smbd(+0xcfcc) [0x55b06c1d6fcc]
   #20 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x9ed0) [0x7f07671a0ed0]
   #21 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x8357) [0x7f076719f357]
   #22 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x9d) [0x7f076719b7cd]
   #23 /usr/lib/x86_64-linux-gnu/libtevent.so.0(tevent_common_loop_wait+0x1b) [0x7f076719b9eb]
   #24 /usr/lib/x86_64-linux-gnu/libtevent.so.0(+0x82f7) [0x7f076719f2f7]
   #25 /usr/sbin/smbd(main+0x1d0a) [0x55b06c1d234a]
   #26 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0x7f0766dc7b97]
   #27 /usr/sbin/smbd(_start+0x2a) [0x55b06c1d245a]
[2019/05/16 12:30:08.469937,  0] ../source3/lib/dumpcore.c:318(dump_core)
  coredump is handled by helper binary specified at /proc/sys/kernel/core_pattern[2019/05/16 12:30:26.801590,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections

```
(last line is me restarting the service to get it working again).

I have been tinkering with my samba config to try and fix it. So far nothing helps.
My current samba config:
```
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = LinuxServer
#security = user
#security = share
map to guest = bad user
guest account = tim
dns proxy = no
create mask = 0777
directory mask = 0777
#printing = bsd
#printcap name = /dev/null
browseable = yes
lock directory = /var/lock/samba
locking = yes
strict locking = no
writable = yes
ntlm auth = true

bind interfaces only = yes
disable netbios = yes
domain master = yes
deadtime = 15
invalid users = nobody root
load printers = no
max connections = 10
preferred master = yes
printable = no
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
strict sync = no

[FileServer]
path = /media
browsable =yes
writable = yes
guest ok = yes
read only = no
public = yes
available = yes

[Dataserver]
path = /data
browsable =yes
writable = yes
guest ok = yes
read only = no
public = yes
available = yes

[Disc1]
path = /media/disc1
browsable =yes
writable = yes
guest ok = yes
read only = no
public = yes
available = yes

[Disc2]
path = /media/disc2
browsable =yes
writable = yes
guest ok = yes
read only = no
public = yes
available = yes

[Disc3]
path = /media/disc3
browsable =yes
writable = yes
guest ok = yes
read only = no
public = yes
available = yes

[Disc4]
path = /media/disc4
browsable =yes
writable = yes
guest ok = yes
read only = no
public = yes
available = yes

[Disc5]
path = /media/disc5
browsable =yes
writable = yes
guest ok = yes
read only = no
public = yes
available = yes

[Disc6]
path = /media/disc6
browsable =yes
writable = yes
guest ok = yes
read only = no
public = yes
available = yes

```

Everything in global after ntlm auth = true is something I added to try and resolve this issue.

**testparm**
```
Load smb config files from /etc/samba/smb.conf
Processing section "[FileServer]"
Processing section "[Dataserver]"
Processing section "[Disc1]"
Processing section "[Disc2]"
Processing section "[Disc3]"
Processing section "[Disc4]"
Processing section "[Disc5]"
Processing section "[Disc6]"
Loaded services file OK.
WARNING: socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
This warning is printed because you set one of the
following options: SO_SNDBUF, SO_RCVBUF, SO_SNDLOWAT,
SO_RCVLOWAT
Modern server operating systems are tuned for
high network performance in the majority of situations;
when you set 'socket options' you are overriding those
settings.
Linux in particular has an auto-tuning mechanism for
buffer sizes (SO_SNDBUF, SO_RCVBUF) that will be
disabled if you specify a socket buffer size. This can
potentially cripple your TCP/IP stack.

Getting the 'socket options' correct can make a big
difference to your performance, but getting them wrong
can degrade it by just as much. As with any other low
level setting, if you must make changes to it, make
 small changes and test the effect before making any
large changes.

Server role: ROLE_STANDALONE
```

---

### Post by Morbius1 on 2019-05-16
Why are you disconnecting your connections after 15 minutes of inactivity with this line:
> deadtime = 15

---

### Post by unrealbe on 2019-05-17
> **Morbius1 said:**
> Why are you disconnecting your connections after 15 minutes of inactivity with this line:

"Everything in global after ntlm auth = true is something I added to try and resolve this issue."

I added it to see if it would resolve the issue. It didn´t. I can remove it again if you want.

---

### Post by TheFu on 2019-05-18
I would suggest simplifying to the most basic config that works, then work on complications.  For example, start with the default config file and add 1 share.  Does that work?  Does it work well?
I don't see any errors in the samba logs on a 16.04 server here, but there isn't any Win10 here either.  I vaguely remember that Win10 changed the default SMB version, so if you only have Win10 clients, then setting the smb protocol version to the value required for win10 could help.

I'm hardly an expert.  Is this a home or business setup?  The "security" parms are commented out. Is that ok?
These settings seem conflicting:```

map to guest = bad user
guest account = tim
```

But I don't have a clue.

---

### Post by unrealbe on 2019-05-20
I removed map to guest = bad user for now, let's see if it improves anything.

---

### Post by Morbius1 on 2019-05-20
Nope. You just made things worse.

This is how this combination works:
> map to guest = bad user
guest account = tim
A "Bad User" is one in which the username and password that is passed to the Linux server ( and Windows always passes a user name and password even if you didn't supply one yourself ) does not find a corresponding match in the samba password database. Under these conditions the client user is converted to ( map to ) the guest account. The Linux default guest account is an actual user named literally "nobody". You overrode that default by specifying the guest account should be you ( guest account = tim ).

If you remove "map to guest = bad user" from smb.conf samba defaults to **map to guest = never **thereby stopping all guest access to your shares. But all your shares specify guest access so .....

How are you accessing this server from WIn10? By ip address, netbios name, or mDNS name? Try it by ip address ( \\192.168.0.100 ) or by mDNS name ( \\linuxserver.local ). Note: you will have to install avahi-daemon on Ubuntu Server for mDNS to work.

---

### Post by unrealbe on 2019-05-22
> **Morbius1 said:**
> 
How are you accessing this server from WIn10? By ip address, netbios name, or mDNS name? Try it by ip address ( \\192.168.0.100 ) or by mDNS name ( \\linuxserver.local ). Note: you will have to install avahi-daemon on Ubuntu Server for mDNS to work.

I just use the hostname (linuxserver). (\\linuxserver works fine)

I note the issue is easy to reproduce, i just need to generate a lot of activity on a share. Example unrarring a collection of about 30 .rars it will definitely happen.

---

### Post by Morbius1 on 2019-05-22
> I just use the hostname (linuxserver). (\\linuxserver works fine)
"linuxserver" in this context is not a hostname it's a netbios name. 

Microsoft deprecated netbios ( and all the associated baggage that comes with it like workgroups, name resolution, master browsers, etc... ) 20 years ago with the release of Windows 2000. It will still work but it's not optimal. For example, should another machine enter the network the whole master browser selection process needs to start over again and this disrupts the network.

That is why I wondered if accessing the server by ip address or mDNS would bypass the complexity of netbios. Win10 can do either. Windows prior to that cannot do mDNS.

---

### Post by TheFu on 2019-05-22
> **unrealbe said:**
> I removed map to guest = bad user for now, let's see if it improves anything.

Actually, I would have changed "tim" to "nobody" and left the other line alone.  It is unclear to me what Morbius was saying about it, but if you figured that out. Great.

---

### Post by unrealbe on 2019-05-22
I changed the connection in windows to use the IP. 
Same issue remains.

---

### Post by unrealbe on 2019-05-22
> **TheFu said:**
> Actually, I would have changed "tim" to "nobody" and left the other line alone.  It is unclear to me what Morbius was saying about it, but if you figured that out. Great.
I'll adapt it to this.

---

### Post by Morbius1 on 2019-05-22
> [QUOTE][IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **TheFu**                     [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13861022#post13861022")                 
                 Actually, I would have changed "tim" to  "nobody" and left the other line alone.  It is unclear to me what  Morbius was saying about it, but if you figured that out. Great.


                            I'll adapt it to this.[/QUOTE]
Nope. That will break your setup again.

An anonymous samba client user tries to connect to the samba shares on your machine.

** With "guest account = tim" that user will access your shares as "tim". If the Linux permissions on the folder being accessed allow "tim" access everything is good.

** With "guest account = nobody" - which is the default so there is no need to put it in smb.conf - the anonymous user will be "nobody" and he will not be able to access any of your shares because you specifically told samba to reject him:
```
invalid users = nobody root
```
And even if you didn't tell samba to reject him "nobody" may not have Linux permissions to access the shared folder.

---

### Post by unrealbe on 2019-05-22
> **Morbius1 said:**
> Nope. That will break your setup again.

An anonymous samba client user tries to connect to the samba shares on your machine.

** With "guest account = tim" that user will access your shares as "tim". If the Linux permissions on the folder being accessed allow "tim" access everything is good.

** With "guest account = nobody" - which is the default so there is no need to put it in smb.conf - the anonymous user will be "nobody" and he will not be able to access any of your shares because you specifically told samba to reject him:
```
invalid users = nobody root
```
And even if you didn't tell samba to reject him "nobody" may not have Linux permissions to access the shared folder.

So what you are saying is that my setup was correct?

---

### Post by Morbius1 on 2019-05-22
This whole side issue started because someone didn't understand what this meant:
> map to guest = bad user
guest account = tim
That combination is a legitimate option. The guest user on the client accesses your share and is converted to tim and I'm guessing  something like /data is owned by tim and any new file added by the guest user will save as owned by tim so everything works. There are other ways to achieve the same result but it is a legitimate option. 

I mean your Win10 client does have access to these shares so your set up works - except for these timeouts and disconnects.

Look, there are a number of inconsistencies in your smb.conf that I would not have if I set this up. For example:

** You disabled netbios but you set your server to be a domain / preferred master browser that Win10 does not need. Maybe you have older Windows in the lan.

** You have the "deadtime = 15" in there for some reason. That really needs to go.

** You really should remove the " socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536" line since that's all SambaV2 stuff.

But none of that matters. You are able to connect to and use the shares from your Win10 machine. What I'm trying to figure out is why WIn10 disconnects itself or why Samba closes the connection of the WIn10 client - I'm not sure at this point who is disconnecting itself from who here. It may be a Win10 issue for all I know. It's not happening to me but I probably don't use it the way you are.

---

### Post by unrealbe on 2019-05-23
> **Morbius1 said:**
> This whole side issue started because someone didn't understand what this meant:

That combination is a legitimate option. The guest user on the client accesses your share and is converted to tim and I'm guessing  something like /data is owned by tim and any new file added by the guest user will save as owned by tim so everything works. There are other ways to achieve the same result but it is a legitimate option. 

I mean your Win10 client does have access to these shares so your set up works - except for these timeouts and disconnects.

Look, there are a number of inconsistencies in your smb.conf that I would not have if I set this up. For example:

** You disabled netbios but you set your server to be a domain / preferred master browser that Win10 does not need. Maybe you have older Windows in the lan.

** You have the "deadtime = 15" in there for some reason. That really needs to go.

** You really should remove the " socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536" line since that's all SambaV2 stuff.

But none of that matters. You are able to connect to and use the shares from your Win10 machine. What I'm trying to figure out is why WIn10 disconnects itself or why Samba closes the connection of the WIn10 client - I'm not sure at this point who is disconnecting itself from who here. It may be a Win10 issue for all I know. It's not happening to me but I probably don't use it the way you are.

Current config:
```
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = LinuxServer
#security = user
#security = share
map to guest = bad user
guest account = tim
dns proxy = no
create mask = 0777
directory mask = 0777
#printing = bsd
#printcap name = /dev/null
browseable = yes
lock directory = /var/lock/samba
locking = yes
strict locking = no
writable = yes
ntlm auth = true

bind interfaces only = yes
disable netbios = yes
invalid users = nobody root
load printers = no
max connections = 10
preferred master = yes
printable = no
strict sync = no
```


I changed one drive to using ip, does not resolve the issue. When working with a lot of files I can immediately reproduce the issue.
Just get 50 or something rars and unrar them at the same time.

Also having the issue with doing other stuff but this has been the fastest way to have the issue.

---

### Post by Morbius1 on 2019-05-23
The next time your Win10 machine connects to this server run this command on the server to see the connection parameters and post the results:
```
sudo smbstatus
```


I'm also wondering about these 50 simultaneous operations you are performing - this is one of those things I have never done. My wonder is if each one is considered a separate connection. You have in your smb.conf a parameter - **max connections = 10** - that limits the number of connections. Is one user from one machine a connection? Or is it one user doing one thing from one machine a connection? I'm not sure. The default value for that parameter is 0 which = unlimited.

Question: You have / had some options in your smb.conf that implies that you have many clients to this machine. Is it just this server and a Win10 machine or do you have many clients and it's only the Win10 machine that is the issue?

---

### Post by unrealbe on 2019-05-23
> **Morbius1 said:**
> The next time your Win10 machine connects to this server run this command on the server to see the connection parameters and post the results:
```
sudo smbstatus
```


I'm also wondering about these 50 simultaneous operations you are performing - this is one of those things I have never done. My wonder is if each one is considered a separate connection. You have in your smb.conf a parameter - **max connections = 10** - that limits the number of connections. Is one user from one machine a connection? Or is it one user doing one thing from one machine a connection? I'm not sure. The default value for that parameter is 0 which = unlimited.

Question: You have / had some options in your smb.conf that implies that you have many clients to this machine. Is it just this server and a Win10 machine or do you have many clients and it's only the Win10 machine that is the issue?


I have only one windows 10 machine connection to the share but sometimes a laptop also on windows 10 connects. Same sort of behavior.
**max connections = 10** has been removed from my settings, does not change anything.

---

### Post by Morbius1 on 2019-05-23
If you have the time I would like to see the entire output of the smbstatus command.

---

### Post by unrealbe on 2019-05-24
> **Morbius1 said:**
> If you have the time I would like to see the entire output of the smbstatus command.

Yep I will do this during the weekend and will come back to you.

---

### Post by unrealbe on 2019-05-25
> **unrealbe said:**
> Yep I will do this during the weekend and will come back to you.

```

~$ sudo smbstatus

Samba version 4.7.6-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------
2091    tim          tim          192.168.1.55 (ipv4:192.168.1.55:53120)    SMB3_11           -                    partial(AES-128-CMAC)

Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------
Disc2        2091    192.168.1.55  Sat May 25 01:07:10 PM 2019 CEST -            -
Disc4        2091    192.168.1.55  Sat May 25 01:07:09 PM 2019 CEST -            -
Disc3        2091    192.168.1.55  Sat May 25 01:07:10 PM 2019 CEST -            -
Disc5        2091    192.168.1.55  Sat May 25 01:04:41 PM 2019 CEST -            -
Disc6        2091    192.168.1.55  Sat May 25 01:07:08 PM 2019 CEST -            -
Disc1        2091    192.168.1.55  Sat May 25 01:07:11 PM 2019 CEST -            -
Dataserver   2091    192.168.1.55  Sat May 25 01:07:08 PM 2019 CEST -            -

Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek/Tim/te classificeren   Sat May 25 13:07:03 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek/Tim/te classificeren   Sat May 25 13:07:03 2019
2091         1000       DENY_NONE  0x100080    RDONLY     NONE             /media/disc4   .   Sat May 25 13:07:09 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /data   .   Sat May 25 13:08:49 2019
2091         1000       DENY_NONE  0x100080    RDONLY     NONE             /media/disc6   .   Sat May 25 13:07:07 2019
2091         1000       DENY_NONE  0x100080    RDONLY     NONE             /media/disc3   .   Sat May 25 13:07:09 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek/Tim/te classificeren/d/Devil Childe   Sat May 25 13:07:03 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek/Tim/te classificeren/d/Devil Childe   Sat May 25 13:07:03 2019
2091         1000       DENY_NONE  0x100080    RDONLY     NONE             /media/disc1   .   Sat May 25 13:07:10 2019
2091         1000       DENY_NONE  0x100080    RDONLY     NONE             /media/disc2   .   Sat May 25 13:07:10 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek/MusicBee   Sat May 25 13:58:17 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek/MusicBee   Sat May 25 13:58:17 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek/Tim/te classificeren/strappado   Sat May 25 13:07:03 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek/Tim/te classificeren/strappado   Sat May 25 13:07:03 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek   Sat May 25 13:58:16 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   Muziek   Sat May 25 13:58:16 2019
2091         1000       DENY_NONE  0x100081    RDONLY     NONE             /media/disc5   .   Sat May 25 13:06:59 2019

```

Seems strange since I did not browse to all those subfolders manually in Muziek.

Edit I forced the problem to happen and this is the current situation (before I restart the service):
~$ sudo smbstatus

```

Samba version 4.7.6-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------

Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------

Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------

```

---

### Post by Morbius1 on 2019-05-25
> Seems strange since I did not browse to all those subfolders manually in Muziek.
That one I'm going to have to think about.

Is the connection to the server a "mapped drive" in Win10?

And do you have an application that automatically connects to that "drive" at login?

Locks don't usually survive when the client disconnects and especially when the server reboots or smbd restarts so I'm not sure why it shows all those connections.

---

### Post by unrealbe on 2019-05-25
> **Morbius1 said:**
> That one I'm going to have to think about.

Is the connection to the server a "mapped drive" in Win10?

And do you have an application that automatically connects to that "drive" at login?

Locks don't usually survive when the client disconnects and especially when the server reboots or smbd restarts so I'm not sure why it shows all those connections.
Yes mapped drives in windows, like this:
[IMG]https://i.imgur.com/gUbBcl1.png[/IMG]


                                          ```
net use
New connections will be remembered.


Status       Local     Remote                    Network

-------------------------------------------------------------------------------
OK           Q:        \\LINUXSERVER\Disc5       Microsoft Windows Network
Unavailable  T:        https://unrealbe.stackstorage.com/remote.php/webdav/
                                                Web Client Network
OK           U:        \\LINUXSERVER\Disc6       Microsoft Windows Network
OK           V:        \\LINUXSERVER\Dataserver  Microsoft Windows Network
OK           W:        \\LINUXSERVER\Disc4       Microsoft Windows Network
OK           X:        \\LINUXSERVER\Disc3       Microsoft Windows Network
OK           Y:        \\LINUXSERVER\Disc2       Microsoft Windows Network
OK           Z:        \\LINUXSERVER\Disc1       Microsoft Windows Network
The command completed successfully.

```

As far as I know nothing connects automatically besides explorer.

---

### Post by Morbius1 on 2019-05-26
I cannot reproduce your symptoms.

I took a test server that I do terrible things to for testing purposes and replaced its smb.conf with yours - after making changes to "tim" and such. I couldn't even get samba to run unless I removed the reference to the lock directory. Even after that change it ran - not very well - but it ran and never disconnected.

Did you follow a HowTo to set up this server or did you make incremental changes to the standard smb.conf over time in an effort to fix the problem you described here?

I personally don't know where to go from here. Sorry.

---

### Post by unrealbe on 2019-05-27
> **Morbius1 said:**
> I cannot reproduce your symptoms.

I took a test server that I do terrible things to for testing purposes and replaced its smb.conf with yours - after making changes to "tim" and such. I couldn't even get samba to run unless I removed the reference to the lock directory. Even after that change it ran - not very well - but it ran and never disconnected.

Did you follow a HowTo to set up this server or did you make incremental changes to the standard smb.conf over time in an effort to fix the problem you described here?

I personally don't know where to go from here. Sorry.


Did you follow a HowTo to set up this server or did you make incremental  changes to the standard smb.conf over time in an effort to fix the  problem you described here?
Definitly the second part. The thing is this used to work fine, no idea what broke it (maybe a windows update)

---

